---
title: Panoramica dell'installazione di SQL Server Servicing | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6a9fd19b-2367-4908-b638-363b1e929e1e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b8e9532c9d3ecbc32942e6a70d82f5837856a329
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093586"
---
# <a name="overview-of-sql-server-servicing-installation"></a>Panoramica sull'installazione dei servizi SQL Server
  È possibile applicare un aggiornamento a qualsiasi componente installato di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite un aggiornamento dei servizi di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Se il livello di versione di un componente esistente di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] è successivo rispetto a quello dell'aggiornamento, il programma di installazione lo escluderà dall'aggiornamento. Per altre informazioni sull'applicazione di un aggiornamento del servizio, vedere [Install SQL Server 2014 Servicing](../../database-engine/install-windows/install-sql-server-servicing-updates.md)Updates.  
  
 Quando si installano aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , è necessario tenere conto delle considerazioni seguenti:  
  
-   Tutte le funzionalità appartenenti a una determinata istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere aggiornate contemporaneamente. Se ad esempio si aggiorna il [!INCLUDE[ssDE](../../includes/ssde-md.md)]e nella stessa istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sono installati anche [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sarà necessario aggiornare anche tali componenti. È necessario aggiornare sempre le caratteristiche condivise, ad esempio gli strumenti di gestione, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], con l'aggiornamento più recente. Le istanze o i componenti non selezionati nell'albero delle funzionalità non verranno aggiornati.  
  
-   Per impostazione predefinita [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , i file di log degli aggiornamenti vengono salvati in\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]% Program\\files% \120\Setup Bootstrap\LOG.  
  
-   Tramite l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è ora possibile integrare un aggiornamento con il supporto originale in modo da eseguire il supporto in questione e l'aggiornamento contemporaneamente. Per ulteriori informazioni, vedere Novità [dell'installazione di SQL Server](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md).  
  
-   Prima di eseguire un aggiornamento dei servizi di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , è consigliabile eseguire il backup dei dati.  
  
-   Gli aggiornamenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update. È consigliabile cercare regolarmente i nuovi aggiornamenti per mantenere l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aggiornata e sicura. 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SP1 viene fornito come installazione completa di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Anziché fornire il Service Pack nel pacchetto eseguibile della patch standard da applicare alle istanze di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RTM, per questa versione viene fornito un pacchetto di installazione costituito da due file. Quando eseguito, tramite il pacchetto verrà installata una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con SP1 preinstallato.  
  
## <a name="requirements-and-known-issues"></a>Requisiti e problemi noti  
 I requisiti di spazio su disco consigliati corrispondono a circa 2,5 volte la dimensione del pacchetto e vengono utilizzati per installare, scaricare ed estrarre il pacchetto. Al termine dell'installazione di un Service Pack, è possibile rimuovere il pacchetto scaricato. Qualsiasi file temporaneo viene rimosso automaticamente.  
  
 **Esaminare i problemi noti:** Per ulteriori informazioni sui problemi noti della versione corrente, vedere l'argomento relativo alle note sulla versione corrispondente qui: [SQL Server note sulla versione](https://msdn.microsoft.com/f617a0af-92dd-47aa-82c3-f51b1346bcd8).  
  
## <a name="installation-overview"></a>Panoramica sull'installazione  
 In questa sezione viene descritta l'installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per gli aggiornamenti cumulativi e i Service Pack, con le istruzioni per eseguire le operazioni seguenti:  
  
-   Preparazione per l'installazione degli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   Installazione degli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   Riavvio di servizi e applicazioni  
  
### <a name="prepare-for-a-includesscurrentincludessscurrent-mdmd-update-installation"></a>Preparare l'installazione di un aggiornamento di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Prima di installare gli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , è opportuno effettuare le operazioni indicate di seguito:  
  
-   **Eseguire il backup [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dei database di sistema** di: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prima di installare gli aggiornamenti `master`, `msdb`eseguire il `model` backup dei database di, e. L'installazione di un aggiornamento di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] implica la modifica di tali database, rendendoli incompatibili con le versioni precedenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Se si decide di reinstallare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] senza questi aggiornamenti, saranno necessari i backup di tali database.  
  
     È inoltre consigliabile eseguire il backup dei database utente esistenti.  
  
    > [!IMPORTANT]  
    >  Prima di applicare gli aggiornamenti alle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che fanno parte di una topologia di replica, è necessario eseguire il backup dei database replicati e dei database di sistema.  
  
-   **Eseguire il backup [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dei database, del file di configurazione e del repository** : prima di aggiornare [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]un'istanza di, è necessario eseguire il backup degli elementi seguenti:  
  
    -   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]database. Per impostazione predefinita, questi file\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vengono installati in c:\Programmi \MSAS12. \<InstanceId> \OLAP\Data\\. Per l'installazione di Wow, il percorso predefinito è C:\ProgramFiles (x86 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) \ \MSAS12. \<InstanceId> \OLAP\Data\\.  
  
    -   Impostazione della configurazione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nel file di configurazione msmdsrv.ini. Per impostazione predefinita, questo file\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]si trova nella cartella c:\Programmi \MSAS12. \<InstanceId> directory \OLAP\Config\.  
  
    -   Database contenente il repository di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (facoltativo). Questo passaggio è necessario solo se [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è stato configurato per l'utilizzo con la libreria DSO (Decision Support Objects).  
  
    > [!NOTE]  
    >  Se non si esegue il backup dei database, del file di configurazione e del repository di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , non sarà possibile ripristinare la versione precedente di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dopo l'installazione di una versione aggiornata.  
  
-   **Verificare che lo spazio disponibile nei database di sistema sia sufficiente** . se l'opzione di aumento automatico delle dimensioni `master` non `msdb` è selezionata per i database di sistema e, i database devono avere almeno 500 KB di spazio libero. Per verificare che i database dispongano di spazio sufficiente, eseguire la stored procedure di sistema `sp_spaceused` nei database `master` e `msdb`. Se la quantità di spazio non allocato in uno dei due database è inferiore a 500 KB, aumentare la dimensione del database.  
  
-   **Arrestare i servizi e le applicazioni** : per evitare un possibile riavvio del sistema, arrestare tutte le applicazioni e i servizi che effettuano connessioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle istanze di da aggiornare, prima [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] di installare gli aggiornamenti. Questi sono [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Per altre informazioni, vedere [Avviare, arrestare, sospendere, riprendere, riavviare i servizi SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
    > [!NOTE]  
    >  Non è possibile arrestare i servizi in un ambiente con cluster di failover. Per ulteriori informazioni, vedere la sezione relativa all'installazione nei cluster di failover più avanti in questo argomento.  
  
-   Per eliminare la necessità di riavviare il computer dopo l'installazione degli aggiornamenti, verrà visualizzato un elenco dei processi che bloccano i file necessari. Se durante l'installazione degli aggiornamenti è necessario arrestare un determinato servizio, al termine dell'installazione tale servizio verrà riavviato automaticamente.  
  
-   Se vengono rilevati file bloccati durante l'installazione, potrebbe essere necessario riavviare il computer al termine dell'installazione. Se necessario, verrà richiesto di riavviare il computer.  
  
### <a name="install-includesscurrentincludessscurrent-mdmd-updates"></a>Installare gli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 In questa sezione viene descritto il processo di installazione.  
  
> [!IMPORTANT]  
>  Gli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] devono essere installati con un account che dispone di privilegi amministrativi nel computer in cui verranno installati. Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.  
  
#### <a name="starting-a-includesscurrentincludessscurrent-mdmd-update"></a>Avvio di un aggiornamento di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Per installare un aggiornamento di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , eseguire il file di pacchetto autoestraente.  
  
 Pacchetto di aggiornamento cumulativo (CU) \<: SQLServer2014>-KBXXXXXX-*PPP*. exe  
  
 Pacchetto di Service Pack (PCU) \<: SQLServer2014 \<>SPX>-KBxxxxxx-PPP-lll. exe  
  
-   x indica il numero di Service Pack.  
  
-   PPP indica la piattaforma specifica.  
  
-   LLL indica l'abbreviazione per la lingua di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ad esempio LLL per la lingua inglese è ENU.  
  
 Per informazioni sull'applicazione di aggiornamenti ai componenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] che fanno parte di un cluster di failover, vedere la sezione relativa all'installazione del cluster di failover. Per ulteriori informazioni su come eseguire un'installazione di aggiornamento in modalità automatica, vedere [Install SQL Server 2014 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
####  <a name="Slipstream"></a>Aggiornamenti del prodotto [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nell'installazione  
 La funzionalità di aggiornamento del prodotto è una funzionalità del programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Integra gli aggiornamenti più recenti del pacchetto con l'installazione del prodotto principale, in modo che il prodotto principale e i relativi aggiornamenti applicabili vengano installati contemporaneamente. Con la funzionalità di aggiornamento del prodotto è inoltre possibile cercare aggiornamenti applicabili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update, Windows Server Update Services (WSUS), una cartella locale o una condivisione di rete.  Dopo avere individuato le versioni più recenti degli aggiornamenti applicabili, questi vengono scaricati e integrati dal programma di installazione con il processo di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrente. Tramite l'aggiornamento del prodotto è possibile includere un aggiornamento cumulativo, un Service Pack o un Service Pack con aggiornamento cumulativo. La funzionalità di aggiornamento del prodotto è un'estensione dal punto di vista funzionale dell'installazione integrata che era disponibile in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="updating-a-prepared-image-of-includessnoversionincludesssnoversion-mdmd"></a>Aggiornamento di un'immagine preparata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 È possibile applicare un aggiornamento a un'istanza predisposta non configurata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza completare la configurazione dell'istanza predisposta. I diversi metodi per l'applicazione di un aggiornamento a un'istanza predisposta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono spiegati di seguito:  
  
-   Aggiornamento di un'istanza precedentemente predisposta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
     Gli aggiornamenti a un'istanza predisposta possono essere applicati prima della configurazione. Il pacchetto di aggiornamento rileva che l'istanza è in stato predisposto e applica la patch all'istanza predisposta, senza completare la configurazione.  
  
-   Aggiornamenti a un'istanza predisposta tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update:  
  
     È possibile applicare aggiornamenti a un'istanza predisposta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update. Il pacchetto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update rileva che l'istanza è in stato predisposto e applica la patch all'istanza predisposta, senza completare la configurazione.  
  
 Se si aggiorna un'immagine preparata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sarà necessario specificare il parametro InstanceID. Per altre informazioni e per la sintassi di esempio, vedere [Installazione degli aggiornamenti dal prompt dei comandi](../../database-engine/install-windows/installing-updates-from-the-command-prompt.md).  
  
## <a name="updating-a-completed-image-of-includessnoversionincludesssnoversion-mdmd"></a>Aggiornamento di un'immagine completata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 L'aggiornamento di un'istanza completata e configurata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] segue gli stessi processi di qualsiasi altra istanza installata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="rebuilding-a-includesscurrentincludessscurrent-mdmd-failover-cluster-node"></a>Ricompilazione di un nodo del cluster di failover di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Se è necessario ricompilare un nodo nel cluster di failover dopo l'applicazione degli aggiornamenti, effettuare le operazioni seguenti:  
  
1.  Ricompilare il nodo nel cluster di failover. Per altre informazioni sulla ricompilazione di un nodo, vedere [Recuperare da un errore dell'istanza del cluster di failover](../failover-clusters/windows/recover-from-failover-cluster-instance-failure.md).  
  
2.  Eseguire il programma di installazione originale di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per installare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nel nodo del cluster di failover.  
  
3.  Eseguire il programma di installazione degli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sul nodo appena aggiunto.  
  
## <a name="restart-services-and-applications"></a>Riavvio di servizi e applicazioni  
 Al termine dell'installazione potrebbe essere necessario riavviare il computer. Dopo il riavvio del sistema oppure al termine del programma di installazione se non viene richiesto di riavviare il sistema, usare il nodo **Servizi** del Pannello di controllo per riavviare i servizi arrestati prima dell'applicazione degli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Sono inclusi servizi quali Distributed Transaction Coordinator e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Search o i servizi equivalenti specifici dell'istanza.  
  
 Riavviare le applicazioni chiuse prima di eseguire il programma di installazione degli aggiornamenti di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Subito dopo il completamento dell'installazione, è inoltre consigliabile eseguire un altro backup dei database `master`, `msdb` e `model` aggiornati.  
  
## <a name="uninstalling-updates-from-includesscurrentincludessscurrent-mdmd"></a>Disinstallazione di aggiornamenti da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 È possibile disinstallare gli aggiornamenti cumulativi o i Service Pack di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] da **Programmi e funzionalità** nel Pannello di controllo. Per visualizzare l'elenco di aggiornamenti installati, aprire Aggiornamenti installati facendo clic sul pulsante **Start** , **Pannello di controllo**, **Programmi**, quindi scegliendo **Visualizza aggiornamenti installati**in **Programmi e funzionalità**. Ogni aggiornamento cumulativo è elencato separatamente. Tuttavia, quando si installa un Service Pack più recente degli aggiornamenti cumulativi, le voci relative agli aggiornamenti cumulativi vengono nascoste e diventano disponibili solo se si disinstalla il Service Pack.  
  
 Per disinstallare Service Pack e aggiornamenti, è necessario iniziare dall'aggiornamento o dal Service Pack applicato più di recente all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e procedere a ritroso. In ciascuno dei seguenti esempi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] termina con l'aggiornamento cumulativo 1 dopo aver completato la disinstallazione degli altri Service Pack o aggiornamenti.  
  
-   Nelle istanze di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] con aggiornamento cumulativo 1 e SP1 installati, disinstallare il SP1.  
  
-   Nelle istanze di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] con aggiornamento cumulativo 1, SP1 e aggiornamento cumulativo 2 installati, disinstallare prima l'aggiornamento cumulativo 2 e quindi il SP1.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare SQL Server 2014 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Installare gli aggiornamenti di manutenzione di SQL Server 2014](../../database-engine/install-windows/install-sql-server-servicing-updates.md)   
 [Convalidare un'installazione di SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)   
 [Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
