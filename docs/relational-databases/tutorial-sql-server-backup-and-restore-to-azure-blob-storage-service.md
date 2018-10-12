---
title: 'Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione Blob di Azure| Microsoft Docs'
ms.custom: ''
ms.date: 04/09/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a33c2bd47bae8bede7fa71e1654627c123e7cdbc
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874319"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Esercitazione: Backup e ripristino di SQL Server nel servizio di archiviazione Blob di Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Questa esercitazione contiene nozioni utili sulla scrittura di backup nel servizio Archiviazione BLOB di Azure e sul ripristino dallo stesso.  Questa esercitazione illustra come creare un contenitore BLOB di Azure e le credenziali per l'accesso all'account di archiviazione, la scrittura di un backup nel servizio BLOB e l'esecuzione di un ripristino semplice.
  
### <a name="prerequisites"></a>Prerequisites  
Per completare l'esercitazione è necessario conoscere i concetti di backup e ripristino di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e la sintassi T-SQL. Per usare questa esercitazione, sono necessari un account di archiviazione di Azure, SQL Server Management Studio (SSMS), l'accesso a un server che esegue SQL Server e un database AdventureWorks. Inoltre, l'account utente usato per eseguire i comandi BACKUP e RESTORE deve essere incluso nel ruolo del database **db_backup operator** con autorizzazioni **Modifica qualsiasi credenziale**. 

- Ottenere un [account Azure](https://azure.microsoft.com/offers/ms-azr-0044p/) gratuito.
- Creare un [account di archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-quickstart-create-account?tabs=portal).
- Installare [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Scaricare i [database di esempio AdventureWorks2016](https://docs.microsoft.com/sql/samples/adventureworks-install-configure).
- Assegnare l'account utente al ruolo [db_backupoperator](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles) e concedere le autorizzazioni [Modifica qualsiasi credenziale](https://docs.microsoft.com/sql/t-sql/statements/alter-credential-transact-sql). 


## <a name="create-azure-blob-container"></a>Creare un contenitore BLOB di Azure
Un contenitore fornisce un raggruppamento di un set di BLOB. Tutti i BLOB devono essere inclusi in un contenitore. Un account può contenere un numero illimitato di contenitori, tuttavia ne deve contenere almeno uno. In un contenitore è possibile archiviare un numero illimitato di BLOB. 

Per creare un contenitore, seguire questa procedura:

1. Aprire il portale di Azure. 
1. Passare all'account di archiviazione. 
   1. Selezionare l'account di archiviazione e scorrere verso il basso fino a **Servizi BLOB**.
   1. Selezionare **BLOB** e quindi selezionare +**Contenitore** per aggiungere un nuovo contenitore. 
   1. Immettere il nome del contenitore e prendere nota del nome specificato. Queste informazioni vengono usate nell'URL (percorso del file di backup) nelle istruzioni T-SQL più avanti in questa esercitazione. 
   1. Fare clic su **OK**. 
    
    ![Nuovo contenitore](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/new-container.png)


  >[!NOTE]
  >L'autenticazione per l'account di archiviazione è obbligatoria per il backup e il ripristino di SQL Server anche se si sceglie di creare un contenitore pubblico. È anche possibile creare un contenitore a livello di programmazione tramite le API REST. Per altre informazioni, vedere [Create container](https://docs.microsoft.com/rest/api/storageservices/Create-Container) (Crea contenitore)


## <a name="create-a-sql-server-credential"></a>Creare le credenziali di SQL Server
Una credenziale di SQL Server è un oggetto utilizzato per archiviare le informazioni di autenticazione necessarie per connettersi a una risorsa all'esterno di SQL Server. In questo caso, nei processi di backup e ripristino di SQL Server le credenziali vengono usate per l'autenticazione per il servizio Archiviazione BLOB di Azure. Nelle credenziali vengono archiviati il nome dell'account di archiviazione e i relativi valori della **chiave di accesso** . Una volta create, le credenziali devono essere specificate nell'opzione WITH CREDENTIAL durante l'esecuzione delle istruzioni BACKUP/RESTORE. Per altre informazioni sulle credenziali, vedere [Credenziali](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/credentials-database-engine). 

  >[!IMPORTANT]
  >I requisiti per la creazione delle credenziali di SQL Server descritti di seguito sono specifici per i processi di backup di SQL Server ([Backup di SQL Server nell'URL](backup-restore/sql-server-backup-to-url.md)e [Backup gestito di SQL Server in Microsoft Azure](backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server usa il nome dell'account di archiviazione e le informazioni sulla chiave di accesso per accedere all'archiviazione di Azure per scrivere e leggere i backup.

### <a name="access-keys"></a>Chiavi di accesso
Dato che il portale di Azure è ancora aperto, salvare le chiavi di accesso necessarie per la creazione delle credenziali. 

1. Passare ad **Account di archiviazione** nel portale di Azure. 
1. Scorrere verso il basso fino a **Impostazioni** e selezionare **Chiavi di accesso**. 
1. Salvare sia la chiave che la stringa di connessione per usarle più avanti in questa esercitazione. 

   ![Chiavi di accesso](media/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service/access-keys.png)

### <a name="create-a-sql-server-credential"></a>Creare le credenziali di SQL Server
Usare la chiave di accesso salvata per creare le credenziali di SQL Server seguendo questa procedura. 

1. Connettersi all'istanza di SQL Server usando SQL Server Management Studio. 
1. Selezionare il database **AdventureWorks2016** e aprire una finestra **Nuova query**. 
1. Copiare, incollare ed eseguire l'esempio seguente nella finestra Query modificandolo in base alle esigenze: 

  ```sql
  CREATE CREDENTIAL mycredential   
  WITH IDENTITY= 'msftutorialstorage', -- this is the name of the storage account you specified when creating a storage account   
  SECRET = '<storage account access key>' -- this should be either the Primary or Secondary Access Key for the storage account 
  ```
1. Eseguire l'istruzione per creare le credenziali. 

## <a name="backup-database-to-the-windows-azure-blob-storage-service"></a>Creare una copia di backup del database nel servizio Archiviazione BLOB di Azure
In questa lezione verrà usata un'istruzione T-SQL per eseguire un backup completo del database nel servizio Archiviazione BLOB di Azure. 

1. Connettersi all'istanza di SQL Server usando SQL Server Management Studio. 
1. Selezionare il database **AdventureWorks2016** e aprire una finestra **Nuova query**. 
1. Copiare e incollare l'esempio seguente nella finestra Query modificandolo se necessario: 

 ```sql
 BACKUP DATABASE [AdventureWorks2016] 
 TO URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/ 
 WITH CREDENTIAL = 'mycredential';
 /* name of the credential you created in the previous step */ 
 GO
 ```
1. Eseguire l'istruzione per eseguire un backup su URL del database AdventureWorks2016. 

 
## <a name="restore-database-from-windows-azure-blob-storage-service"></a>Ripristinare il database dal servizio Archiviazione BLOB di Azure
In questa sezione verrà usata un'istruzione T-SQL per ripristinare il backup di database completo. 

1. Connettersi all'istanza di SQL Server usando SQL Server Management Studio. 
1. Aprire una finestra **Nuova query**. 
1. Copiare e incollare l'esempio seguente nella finestra Query modificandolo se necessario: 

 ```sql
 RESTORE DATABASE AdventureWorks2016 
 FROM URL = 'https://msftutorialstorage.blob.core.windows.net/sql-backup/AdventureWorks2016.bak' 
 WITH CREDENTIAL = 'mycredential',
 STATS = 5 -- use this to see monitor the progress
 GO
 ``` 

## <a name="see-also"></a>Vedere anche 
Di seguito sono indicate alcune letture suggerite per comprendere i concetti e le procedure consigliate quando si usa il servizio Archiviazione BLOB di Azure per i backup di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   [Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)   
-   [Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell'URL](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
