---
title: Ripristinare un'installazione di SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 90c11b28-892b-44d6-978e-0eee48c75b7d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0d9486134e0a9103239853d8378e29aea688c7fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67046662"
---
# <a name="drop-a-sql-server-2014-installation"></a>Rimuovere un'installazione di SQL Server 2014
  L'operazione di ripristino può essere utilizzata negli scenari seguenti:  
  
-   Ripristino di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] danneggiata dopo averla installata.  
  
-   Ripristino di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se l'operazione di aggiornamento è stata annullata o non è riuscita dopo il mapping del nome dell'istanza all'istanza appena aggiornata.  
  
    -   Se nel log di riepilogo viene visualizzato il messaggio seguente, è possibile ripristinare l'istanza di aggiornamento non riuscita.  
  
         "Aggiornamento di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non riuscito. Per continuare, individuare la causa dell'errore, correggere il problema, quindi ripristinare l'installazione."  
  
    -   Se nel log di riepilogo viene visualizzato il messaggio seguente, è necessario disinstallare e reinstallare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non è possibile ripristinare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
         "Aggiornamento di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non riuscito. Per continuare, individuare la causa dell'errore e correggere il problema."  
  
 Quando si ripristina un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Vengono sostituiti tutti i file mancanti o danneggiati.  
  
-   Vengono sostituite tutte le chiavi del Registro di sistema mancanti o danneggiate.  
  
-   Tutti i valori di configurazione mancanti o non validi vengono impostati su valori predefiniti.  
  
 Prima di continuare, per i cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rivedere le informazioni importanti seguenti:  
  
-   Il ripristino deve essere eseguito sui nodi di cluster singoli.  
  
-   Per ripristinare un nodo del cluster di failover dopo un'operazione di preparazione non riuscita, usare **Rimuovi nodo**, quindi eseguire nuovamente la procedura di preparazione. Per altre informazioni, vedere [Aggiungere o rimuovere nodi in un cluster di failover di SQL Server &#40;programma di installazione&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### <a name="to-repair-a-failed-installation-of-includessnoversionincludesssnoversion-mdmd-from-the-installation-center"></a>Per ripristinare un'installazione non riuscita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dal Centro installazione  
  
1.  Avviare il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (file setup.exe) dai supporti di installazione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Dopo la verifica del sistema e dei prerequisiti, nel programma di installazione verrà visualizzata la pagina Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  Fare clic su **Manutenzione** nell'area di navigazione a sinistra, quindi fare clic su **Ripristina** per avviare l'operazione di ripristino.  
  
    > [!TIP]  
    >  Se Centro installazione è stato avviato utilizzando il menu Start, a questo punto sarà necessario fornire il percorso del supporto di installazione.  
  
4.  Verranno eseguite la regola di supporto dell'installazione e le routine dei file per garantire che nel sistema siano installati i prerequisiti e che il computer passi le regole di convalida dell'installazione. Fare clic su **OK** o **Installa** per continuare.  
  
5.  Nella pagina Seleziona istanza selezionare l'istanza da ripristinare, quindi fare clic su **Avanti** per continuare.  
  
6.  Verranno eseguite le regole di ripristino per convalidare l'operazione. Scegliere **Avanti**per continuare.  
  
7.  La pagina Ripristino indica che l'operazione può essere eseguita. Per continuare fare clic su **Ripristina**.  
  
8.  Nella pagina Stato del ripristino viene mostrato lo stato dell'operazione di ripristino. Nella pagina Operazione completata è indicato che l'operazione è stata completata.  
  
### <a name="to-repair-a-failed-installation-of-includessnoversionincludesssnoversion-mdmd-using-command-prompt"></a>Per ripristinare un'installazione non riuscita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il prompt dei comandi  
  
1.  Al prompt dei comandi eseguire il comando seguente:  
  
    ```  
    Setup.exe /q /ACTION=Repair /INSTANCENAME=instancename  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e leggere i file di log del programma di installazione di SQL Server](view-and-read-sql-server-setup-log-files.md)   
 [Procedure per l'installazione](../../sql-server/install/installation-how-to-topics.md)  
  
  
