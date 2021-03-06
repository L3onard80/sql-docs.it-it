---
title: Migrazione di dati Oracle in SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Data Migration, Client-Side Migration
- Oracle Data Migration,Server-Side Migration
ms.assetid: e23c5268-41ed-4e55-9fe7-a11376202a13
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: c37f9c8e39a8a9dd87eabecba445b5ce7cef9028
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264685"
---
# <a name="migrating-oracle-data-into-sql-server-oracletosql"></a>Migrazione di dati Oracle a SQL Server (OracleToSQL)
Una volta sincronizzati correttamente gli oggetti convertiti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]con, è possibile eseguire la migrazione dei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dati da Oracle a.  
  
> [!IMPORTANT]  
> Se il motore usato è il motore di migrazione dei dati lato server, prima di poter eseguire la migrazione dei dati, è necessario installare SSMA per Oracle Extension Pack e i provider Oracle nel computer che esegue SSMA. È inoltre necessario che il servizio SQL Server Agent sia in esecuzione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti server (OracleToSQL)](https://msdn.microsoft.com/33070e5f-4e39-4b70-ae81-b8af6e4983c5) .  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima di eseguire la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrazione dei dati a, rivedere le opzioni di migrazione del progetto nella finestra di dialogo **Impostazioni progetto** .  
  
-   Utilizzando questa finestra di dialogo è possibile impostare opzioni quali le dimensioni del batch di migrazione, il blocco della tabella, il controllo dei vincoli, la gestione dei valori null e la gestione dei valori Identity. Per ulteriori informazioni sulle impostazioni di migrazione del progetto, vedere [Impostazioni progetto (migrazione) (OracleToSQL)](https://msdn.microsoft.com/fcd6b988-633b-4b2b-9f36-6368b5e86b60).  
  
-   Il **motore di migrazione** nella finestra di dialogo **Impostazioni progetto** consente all'utente di eseguire il processo di migrazione utilizzando due tipi di motori di migrazione dei dati:  
  
    1.  Motore di migrazione dati lato client  
  
    2.  Motore di migrazione dei dati lato server  
  
**Migrazione dei dati sul lato client:**  
  
-   Per avviare la migrazione dei dati sul lato client, selezionare l'opzione **motore di migrazione dati lato client** nella finestra di dialogo **Impostazioni progetto** .  
  
-   In **Impostazioni progetto**viene impostata l'opzione **motore di migrazione dati lato client** .  
  
    > [!NOTE]  
    > Il **motore di migrazione dei dati lato client** si trova all'interno dell'applicazione SSMA e pertanto non dipende dalla disponibilità del pacchetto di estensione.  
  
**Migrazione dei dati lato server:**  
  
-   Durante la migrazione dei dati sul lato server, il motore risiede nel database di destinazione. Viene installato tramite il pacchetto di estensione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti server in SQL Server](installing-ssma-components-on-sql-server-oracletosql.md)  
  
-   Per avviare la migrazione sul lato server, selezionare l'opzione **motore di migrazione dei dati sul lato server** nella finestra di dialogo **Impostazioni progetto** .  
  
## <a name="migrating-data-to-sql-server"></a>Migrazione dei dati a SQL Server  
La migrazione dei dati è un'operazione di caricamento bulk che consente di spostare righe di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da tabelle Oracle in tabelle nelle transazioni. Il numero di righe caricate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in in ogni transazione viene configurato nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, assicurarsi che il riquadro di output sia visibile. In caso contrario, scegliere **output**dal menu **Visualizza** .  
  
**Per eseguire la migrazione dei dati**  
  
1.  Verificare quanto segue:  
  
    -   I provider Oracle sono installati nel computer che esegue SSMA.  
  
    -   Gli oggetti convertiti sono stati sincronizzati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il database.  
  
2.  In Esplora metadati Oracle selezionare gli oggetti che contengono i dati di cui si desidera eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per tutti gli schemi, selezionare la casella di controllo accanto agli **schemi**.  
  
    -   Per eseguire la migrazione dei dati o omettere singole tabelle, espandere innanzitutto lo schema, espandere **tabelle**, quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
3.  Per eseguire la migrazione dei dati, si verificano due casi:  
  
    **Migrazione dei dati sul lato client:**  
  
    -   Per eseguire la **migrazione dei dati lato client**, selezionare l'opzione **motore di migrazione dati lato client** nella finestra di dialogo **Impostazioni progetto** .  
  
    **Migrazione dei dati lato server:**  
  
    -   Prima di eseguire la migrazione dei dati sul lato server, verificare quanto segue:  
  
        1.  SSMA per Oracle Extension Pack è installato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
        2.  Il servizio SQL Server Agent è in esecuzione nell'istanza di SQL Server.  
  
    -   Per eseguire la **migrazione dei dati sul lato server**, selezionare l'opzione **motore di migrazione dei dati sul lato server** nella finestra di dialogo **Impostazioni progetto** .  
  
4.  Fare clic con il pulsante destro del mouse su **schemi** in Oracle Metadata Explorer, quindi scegliere **Migrate data**. È inoltre possibile eseguire la migrazione dei dati per singoli oggetti o categorie di oggetti: fare clic con il pulsante destro del mouse sull'oggetto o la relativa cartella padre. Selezionare l'opzione **Migrate data** .  
  
    > [!NOTE]  
    > Se il pacchetto di estensione SSMA per Oracle non è installato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e il **motore di migrazione dei dati lato server** è selezionato, durante la migrazione dei dati nel database di destinazione si verifica l'errore seguente: "i componenti di migrazione dei dati di SSMA non sono stati trovati in SQL Server, non sarà possibile eseguire la migrazione dei dati sul lato server. Verificare se il pacchetto di estensione è installato correttamente. Fare clic su **Annulla** per terminare la migrazione dei dati.  
  
5.  Nella finestra di dialogo **Connetti a Oracle** immettere le credenziali di connessione, quindi fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a Oracle, vedere [connettersi a oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)  
  
    Per la connessione al database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di destinazione, immettere le credenziali di connessione nella finestra di dialogo **Connetti a SQL Server** e fare clic su **Connetti**. Per altre informazioni sulla connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [connettersi a SQL Server](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    I messaggi verranno visualizzati nel riquadro di **output** . Al termine della migrazione, viene visualizzato il **report migrazione dei dati** . Se non è stata eseguita la migrazione di dati, fare clic sulla riga che contiene gli errori, quindi fare clic su **Dettagli**. Al termine del report, fare clic su **Chiudi**. Per ulteriori informazioni sul report di migrazione dei dati, vedere [report sulla migrazione dei dati (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Quando si usa SQL Express Edition come database di destinazione, è consentita solo la migrazione dei dati lato client e la migrazione dei dati sul lato server non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
