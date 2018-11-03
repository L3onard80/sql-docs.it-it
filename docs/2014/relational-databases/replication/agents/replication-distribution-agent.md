---
title: Agente distribuzione repliche | Microsoft Docs
ms.custom: ''
ms.date: 29/10/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- Distribution Agent, executables
- agents [SQL Server replication], Distribution Agent
- Distribution Agent, parameter reference
- command prompt [SQL Server replication]
ms.assetid: 7b4fd480-9eaf-40dd-9a07-77301e44e2ac
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7ba109b21eb8af1f4260aee43f8a9c5f8d3a3bdb
ms.sourcegitcommit: 3a8293b769b76c5e46efcb1b688bffe126d591b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226333"
---
# <a name="replication-distribution-agent"></a>Agente distribuzione repliche
  Agente distribuzione repliche è un eseguibile che consente di spostare lo snapshot (per la replica snapshot e transazionale) e le transazioni incluse nelle tabelle del database di distribuzione (per la replica transazionale) nelle tabelle di destinazione nei Sottoscrittori.  
  
> [!NOTE]  
>  I parametri possono essere specificati in qualsiasi ordine. Quando i parametri facoltativi non vengono specificati, vengono usati i valori delle impostazioni predefinite del Registro di sistema nel computer locale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      distrib [-?]  
-Publisherserver_name[\instance_name]  
-PublisherDBpublisher_database-Subscriberserver_name[\instance_name]  
-SubscriberDBsubscriber_database   
[-AltSnapshotFolderalt_snapshot_folder_path]   
[-BcpBatchSizebcp_batch_size]  
[-CommitBatchSizecommit_batch_size]  
[-CommitBatchThresholdcommit_batch_threshold]  
[-Continuous]  
[-DefinitionFiledef_path_and_file_name]  
[-Distributordistributor]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ErrorFileerror_path_and_file_name]  
[-ExtendedEventConfigFileconfiguration_path_and_file_name]  
[-FileTransferType [0|1]]  
[-FtpAddressftp_address]  
[-FtpPasswordftp_password]   
[-FtpPortftp_port]  
[-FtpUserNameftp_user_name]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-Hostnamehost_name]  
[-KeepAliveMessageIntervalkeep_alive_message_interval_seconds]  
[-LoginTimeOutlogin_time_out_seconds]  
[-MaxBcpThreads]  
[-MaxDeliveredTransactionsnumber_of_transactions]  
[-MessageIntervalmessage_interval]  
[-OledbStreamThresholdoledb_stream_threshold]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PacketSizepacket_size]  
[-PollingIntervalpolling_interval]  
[-ProfileNameprofile_name]  
[-Publicationpublication]  
[-QueryTimeOutquery_time_out_seconds]  
[-QuotedIdentifierquoted_identifier]  
[-SkipErrorsnative_error_id [:...n]]  
[-SubscriberDatabasePathsubscriber_path]  
[-SubscriberLoginsubscriber_login]  
[-SubscriberPasswordsubscriber_password]  
[-SubscriberSecurityMode [0|1]]  
[-SubscriberType [0|1|3]]  
[-SubscriptionStreams [1|2|...64]]  
[-SubscriptionTableNamesubscription_table]  
[-SubscriptionType [0|1|2]]  
[-TransactionsPerHistory [0|1|...10000]]  
[-UseDTS]  
[-UseInprocLoader]  
[-UseOledbStreaming]  
```  
  
## <a name="arguments"></a>Argomenti  
 **-?**  
 Stampa tutti i parametri disponibili.  
  
 **-Publisher** *nome_server*[**\\***** nome_istanza*]  
 Nome del server di pubblicazione. Specificare *server_name* per l'istanza predefinita di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server. Specificare *server_name***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server.  
  
 **-PublisherDB** *publisher_database*  
 Nome del database del server di pubblicazione.  
  
 **-Subscriber** *nome_server*[**\\***nome_istanza*]  
 Nome del Sottoscrittore. Specificare *server_name* per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server. Specificare *server_name***\\***instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server.  
  
 **-SubscriberDB** *subscriber_database*  
 Nome del database Sottoscrittore.  
  
 **-AltSnapshotFolder** *alt_snapshot_folder_path*  
 Percorso della cartella che contiene lo snapshot iniziale per una sottoscrizione.  
  
 **-BcpBatchSize** *bcp_batch_size*  
 Numero di righe da inviare in un'operazione di copia bulk. Quando si esegue un'operazione **bcp in** , la dimensione del batch indica il numero di righe da inviare al server come unica transazione, nonché il numero di righe che devono essere inviate prima che l'agente di distribuzione registri un messaggio di stato **bcp** . Quando si esegue un'operazione **bcp out** , viene usata una dimensione batch fissa di **1000** .  
  
 **-CommitBatchSize** *commit_batch_size*  
 Numero di transazioni da eseguire nel Sottoscrittore prima di eseguire un'istruzione COMMIT. Il valore predefinito è 100.  
  
 **-CommitBatchThreshold**  *commit_batch_threshold*  
 Numero di comandi di replica da eseguire nel Sottoscrittore prima di eseguire un'istruzione COMMIT. Il valore predefinito è 1000.  
  
 **-Continuous**  
 Specifica se l'agente tenta di eseguire continuamente il polling delle transazioni replicate. Se specificato, l'agente esegue il polling delle transazioni replicate dall'origine in base agli intervalli di polling, anche se non vi sono transazioni in sospeso.  
  
 **-DefinitionFile** *def_path_and_file_name*  
 Percorso del file di definizione dell'agente. Un file di definizione dell'agente contiene argomenti del prompt dei comandi per l'agente. Il contenuto del file viene analizzato come file eseguibile. Utilizzare virgolette doppie (") per specificare valori dell'argomento contenenti caratteri arbitrari.  
  
 **-Distributor** *distributor*  
 Nome del database di distribuzione. Per la distribuzione (push) del server di distribuzione, per impostazione predefinita viene utilizzato il nome del server di distribuzione locale.  
  
 **-DistributorLogin** *distributor_login*  
 Nome dell'account di accesso del database di distribuzione.  
  
 **-DistributorPassword** *distributor_password*  
 Password del database di distribuzione.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del database di distribuzione. Un valore 0 indica la modalità di autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mentre un valore 1 indica la modalità di autenticazione di Windows (impostazione predefinita).  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Livello di crittografia SSL (Secure Sockets Layer) utilizzato dall'agente di distribuzione quando vengono stabilite le connessioni.  
  
|Valore di EncryptionLevel|Description|  
|---------------------------|-----------------|  
|**0**|Specifica che SSL non viene utilizzato.|  
|**1**|Specifica che SSL viene utilizzato, ma l'agente non verifica che il certificato server SSL sia firmato da un'autorità emittente attendibile.|  
|**2**|Specifica che SSL viene utilizzato e che il certificato viene verificato.|  
 
 > [!NOTE]  
 >  Un certificato SSL valido è definito con un nome di dominio completo del Server SQL. Affinché l'agente possa connettersi correttamente quando si imposta - EncryptionLevel su 2, creare un alias nel Server SQL locale. Il parametro 'Nome Alias' deve essere il nome del server e il parametro "Server" deve essere impostato per il nome completo di SQL Server.

 Per altre informazioni, vedere [Panoramica della sicurezza &#40;replica&#41;](../security/security-overview-replication.md).  
  
 **-ErrorFile** *error_path_and_file_name*  
 Percorso e nome del file degli errori generato dall'agente di distribuzione. Tale file viene generato nel punto in cui si verifica l'errore durante l'applicazione delle transazioni di replica nel Sottoscrittore. Gli errori che si verificano nel server di pubblicazione e nel server di distribuzione non vengono registrati in questo file. Il file contiene le transazioni di replica non riuscite e i relativi messaggi di errore. Se il percorso viene omesso, il file degli errori viene generato nella directory corrente dell'agente di distribuzione. Il file degli errori ha lo stesso nome dell'agente di distribuzione e ha un'estensione err. Se il nome file specificato esiste già, i messaggi di errore vengono aggiunti al file. Questo parametro può essere composto da un massimo di 256 caratteri Unicode.  
  
 **-ExtendedEventConfigFile** *configuration_path_and_file_name*  
 Consente di specificare il percorso e il nome del file di configurazione XML di eventi estesi. Il file di configurazione di eventi estesi consente di configurare sessioni e abilitare eventi per la traccia.  
  
 **-FileTransferType** [ **0**| **1**]  
 Specifica il tipo di trasferimento di file. Un valore **0** indica UNC (Universal Naming Convention), mentre un valore **1** indica FTP (File Transfer Protocol).  
  
 **-FtpAddress** *ftp_address*  
 Indirizzo di rete del servizio FTP per il database di distribuzione. Quando non è specificato, viene utilizzato **DistributorAddress** . Se **DistributorAddress** non è specificato, viene utilizzato **Distributor** .  
  
 **-FtpPassword** *ftp_password*  
 Password utente utilizzata per la connessione al servizio FTP.  
  
 **-FtpPort** *ftp_port*  
 Numero di porta del servizio FTP per il database di distribuzione. Quando non è specificato, viene utilizzato il numero di porta predefinito per il servizio FTP, ovvero 21.  
  
 **-FtpUserName**  *nome_utente_ftp*  
 Nome utente utilizzato per la connessione al servizio FTP. Quando non è specificato, viene utilizzato **anonymous** .  
  
 **-HistoryVerboseLevel** [ **0** | **1** | **2** | **3** ]  
 Specifica la quantità di cronologia registrata durante un'operazione di distribuzione. Per ridurre al minimo l'effetto della registrazione della cronologia sulle prestazioni, selezionare **1**.  
  
|Valore di HistoryVerboseLevel|Description|  
|-------------------------------|-----------------|  
|**0**|I messaggi di stato vengono scritti nella console o in un file di output. I record della cronologia non vengono registrati nel database di distribuzione.|  
|**1**|Valore predefinito. Aggiorna sempre un messaggio di cronologia precedente con lo stesso stato (avvio, avanzamento, esito positivo e così via). Se non è presente un record precedente con lo stesso stato, inserisce un nuovo record.|  
|**2**|Inserisce nuovi record della cronologia, a meno che il record sia per eventi come messaggi inattivi o messaggi di processo con esecuzione prolungata, nel qual caso aggiorna i record precedenti.|  
|**3**|Inserisce sempre nuovi record, a meno che non si tratti di record per messaggi inattivi.|  
  
 **-Hostname** *host_name*  
 Nome host utilizzato per la connessione al server di pubblicazione. Questo parametro può essere composto da un massimo di 128 caratteri Unicode.  
  
 **-KeepAliveMessageInterval** *keep_alive_message_interval_seconds*  
 Numero di secondi prima che il thread per la cronologia controlli se una delle connessioni esistenti è in attesa di una risposta dal server. Questo valore può essere ridotto per evitare che l'agente di controllo contrassegni l'agente di distribuzione come sospetto in caso di esecuzione di un batch con esecuzione prolungata. Il valore predefinito è **300** secondi.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Numero di secondi prima del timeout di accesso. Il valore predefinito è **15** secondi.  
  
 **-MaxBcpThreads** *number_of_threads*  
 Specifica il numero di operazioni di copia bulk che possono essere eseguite in parallelo. Il numero massimo di connessioni ODBC e thread presenti simultaneamente corrisponde a **MaxBcpThreads** o al numero di richieste di copia bulk presenti nella transazione di sincronizzazione nel database di distribuzione, a seconda di quale sia il valore minore. **MaxBcpThreads** deve avere un valore maggiore di **0** e non ha un limite massimo specificato a livello di codice. L'impostazione predefinita è **2** volte il numero di processori, fino a un valore massimo di **8**. Quando si applica uno snapshot generato nel server di pubblicazione usando l'opzione relativa agli snapshot simultanei, viene usato un thread, indipendentemente dal numero specificato per **MaxBcpThreads**.  
  
 **-MaxDeliveredTransactions** *number_of_transactions*  
 Numero massimo di transazioni push o pull applicate ai Sottoscrittori in una sincronizzazione. Un valore **0** indica che il numero massimo corrisponde a un numero infinito di transazioni. Nei Sottoscrittori possono venire utilizzati altri valori per abbreviare la durata di una sincronizzazione di cui viene effettuato il pull da un server di pubblicazione.  
  
> [!NOTE]  
>  Se - MaxDeliveredTransactions e - Continuous sono entrambi specificati, tramite l'agente di distribuzione viene recapitato il numero specificato di transazioni e successivamente tale agente viene arrestato (anche se è specificato -Continuous). È necessario riavviare l'agente di distribuzione dopo il completamento del processo.  
  
 **-MessageInterval**  *message_interval*  
 Intervallo di tempo utilizzato per la registrazione della cronologia. Viene registrato un evento della cronologia quando viene raggiunto uno di questi parametri:  
  
-   Il valore **TransactionsPerHistory** viene raggiunto dopo la registrazione dell'ultimo evento della cronologia.  
  
-   Il valore **MessageInterval** viene raggiunto dopo la registrazione dell'ultimo evento della cronologia.  
  
 Se nell'origine non vi sono transazioni replicate disponibili, tramite l'agente viene inviato al server di distribuzione un messaggio che segnala l'assenza di transazioni. Questa opzione specifica per quanto tempo l'agente aspetta prima di inviare un altro messaggio di assenza di transazioni. Gli agenti inviano sempre un messaggio di assenza di transazioni quando rilevano che nell'origine non vi sono transazioni disponibili dopo aver elaborato in precedenza transazioni replicate. Il valore predefinito è 60 secondi.  
  
 **-OledbStreamThreshold** *oledb_stream_threshold*  
 Viene specificata la dimensione minima, in byte, per i dati BLOB (Binary Large Object), sopra la quale i dati verranno associati come flusso. Per usare questo parametro, è necessario specificare **–UseOledbStreaming** . I possibili valori sono compresi tra 400 e 1048576 byte. Il valore predefinito è 16384 byte.  
  
 **-Output** *output_path_and_file_name*  
 Percorso del file di output dell'agente. Se non viene specificato il nome file, l'output viene inviato alla console. Se il nome file specificato esiste già, l'output viene aggiunto al file.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Specifica se l'output deve essere dettagliato. Se il livello di dettaglio è **0**, vengono stampati solo i messaggi di errore. Se il livello di dettaglio è **1**, vengono stampati tutti i messaggi di report di stato. Se il livello di dettaglio è **2** (impostazione predefinita), vengono stampati tutti i messaggi di errore e i messaggi di report di stato. Questa opzione è utile per l'esecuzione del debug.  
  
 **-PacketSize** *packet_size*  
 Dimensioni del pacchetto, in byte. Il valore predefinito è 4096 byte.  
  
 **-PollingInterval** *polling_interval*  
 Frequenza, in secondi, di esecuzione di query sul database di distribuzione per le transazioni replicate. Il valore predefinito è 5 secondi.  
  
 **-ProfileName** *profile_name*  
 Specifica un profilo agente da utilizzare per i parametri dell'agente. Se **ProfileName** è NULL, il profilo agente è disabilitato. Se **ProfileName** non viene specificato, viene utilizzato il profilo predefinito per il tipo di agente. Per altre informazioni, vedere [Profili degli agenti di replica](replication-agent-profiles.md).  
  
 **-Publication**  *pubblicazione*  
 Nome della pubblicazione. Questo parametro è valido solo se la pubblicazione è configurata in modo che sia sempre disponibile uno snapshot per le sottoscrizioni nuove o reinizializzate.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Numero di secondi prima del timeout delle query. Il valore predefinito è 1800 secondi.  
  
 **-QuotedIdentifier** *quoted_identifier*  
 Specifica il carattere dell'identificatore tra virgolette da utilizzare. Il primo carattere del valore indica il valore utilizzato dall'agente di distribuzione. Se **QuotedIdentifier** viene usato senza valore, l'agente di distribuzione usa uno spazio. Se **QuotedIdentifier** non viene usato, l'agente di distribuzione usa qualsiasi identificatore delimitato tra virgolette supportato dal Sottoscrittore.  
  
 **-SkipErrors** *id_errore_nativo* [**:***...n*]  
 Elenco delimitato da due punti che specifica i numeri di errore che devono essere ignorati dall'agente.  
  
 **-SubscriberDatabasePath** *subscriber_database_path*  
 Percorso del database Jet (file con estensione mdb) se **SubscriberType** è **2** (consente una connessione a un database Jet senza un nome origine dati (DNS, Data Source Name) ODBC).  
  
 **-SubscriberLogin** *subscriber_login*  
 Nome dell'account di accesso del Sottoscrittore. Se **SubscriberSecurityMode** è **0** (per l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ), questo parametro deve essere specificato.  
  
 **-SubscriberPassword** *subscriber_password*  
 Password del Sottoscrittore. Se **SubscriberSecurityMode** è **0** (per l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ), questo parametro deve essere specificato.  
  
 **-SubscriberSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del Sottoscrittore. Un valore **0** indica la modalità di autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mentre un valore **1** indica la modalità di autenticazione di Windows (impostazione predefinita).  
  
 **-SubscriberType** [ **0**| **1**| **3**]  
 Specifica il tipo di connessione al Sottoscrittore utilizzata dall'agente di distribuzione.  
  
|Valore di SubscriberType|Description|  
|--------------------------|-----------------|  
|**0**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|**1**|Origine dati ODBC|  
|**3**|Origine dati OLE DB|  
  
 **-SubscriptionStreams** [**0**|**1**|**2**|...**64**]  
 Numero di connessioni consentite per agente di distribuzione per l'applicazione di batch di modifiche in parallelo a un Sottoscrittore, conservando molte delle caratteristiche transazionali disponibili quando si utilizza un singolo thread. Per un server di pubblicazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è supportato un intervallo di valori da 1 a 64. Questo parametro è supportato solo quando il server di pubblicazione e il server di distribuzione sono in esecuzione in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versioni successive. Questo parametro non è supportato o deve essere uguale a 0 per le sottoscrizioni peer-to-peer o i Sottoscrittori non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Se si verifica un errore di esecuzione o di commit di una delle connessioni, tutte le connessioni interromperanno il batch corrente e l'agente utilizzerà un singolo flusso per ripetere i batch non riusciti. Prima del completamento di questa fase di tentativi, possono verificarsi inconsistenze temporanee delle transazioni nel Sottoscrittore. Al termine del commit dei batch non riusciti, viene ripristinata la consistenza delle transazioni nel Sottoscrittore.  
  
> [!IMPORTANT]  
>  Quando si specifica un valore maggiore o uguale a 2 per **-SubscriptionStreams**, l'ordine di ricezione delle transazioni nel Sottoscrittore può essere diverso dall'ordine di esecuzione di tali transazioni nel server di pubblicazione. Se questo comportamento provoca violazioni di vincoli durante la sincronizzazione, è necessario utilizzare l'opzione NOT FOR REPLICATION per disabilitare l'imposizione di vincoli durante la sincronizzazione. Per altre informazioni, vedere [Controllare il comportamento di trigger e vincoli durante la sincronizzazione &#40;programmazione Transact-SQL della replica&#41;](../control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
> [!NOTE]  
>  Subscriptionstreams non funziona per gli articoli configurati per fornire [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Per utilizzare subscriptionstreams, configurare gli articoli per fornire invece chiamate di stored procedure.  
  
 **-SubscriptionTableName** *subscription_table*  
 Nome della tabella di sottoscrizione generata o utilizzata nel Sottoscrittore specificato. Quando non viene specificato, viene usata la tabella [MSreplication_subscriptions &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/msreplication-subscriptions-transact-sql). Utilizzare questa opzione per i sistemi di gestione di database (DBMS) che non supportano nomi file lunghi.  
  
 **-SubscriptionType** [ **0**| **1**| **2**]  
 Specifica il tipo di sottoscrizione per la distribuzione. Un valore **0** indica una sottoscrizione push, un valore **1** indica una sottoscrizione pull e un valore **2** indica una sottoscrizione anonima.  
  
 **-TransactionsPerHistory** [ **0**| **1**|... **10000**]  
 Specifica l'intervallo delle transazioni per la registrazione della cronologia. Se il numero di transazioni di cui è stato eseguito il commit dopo l'ultima istanza di registrazione della cronologia è maggiore rispetto al valore di questa opzione, viene registrato un messaggio di cronologia. Il valore predefinito è 100. Un valore di **0** indica **TransactionsPerHistory**infinito. See the preceding **–MessageInterval**parameter.  
  
 **-UseDTS**  
 Deve essere specificato come parametro per una pubblicazione che consente la trasformazione dei dati.  
  
 **-UseInprocLoader**  
 Migliora le prestazioni dello snapshot iniziale facendo in modo che l'agente di distribuzione utilizzi il comando BULK INSERT in caso di applicazione dei file di snapshot al Sottoscrittore. Questo parametro è deprecato in quanto non è compatibile con il tipo di dati XML. Se non si sta eseguendo la replica di dati XML, è possibile utilizzare questo parametro. Questo parametro non può essere utilizzato con snapshot in modalità carattere o Sottoscrittori non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Se si utilizza questo parametro, l'account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nel Sottoscrittore deve disporre di autorizzazioni di lettura nella directory in cui si trovano i file di dati di snapshot, con estensione bcp. Quando questo parametro non viene utilizzato, l'agente (per i Sottoscrittori non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ) o il driver ODBC caricato dall'agente (per i Sottoscrittori [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ) legge dai file, pertanto il contesto di sicurezza dell'account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non viene utilizzato.  
  
 **-UseOledbStreaming**  
 Se specificato, consente l'associazione di dati BLOB (Binary Large Object) come flusso. Usare **-OledbStreamThreshold** per specificare la dimensione, in byte, oltre la quale verrà usato un flusso.  
  
## <a name="remarks"></a>Note  
  
> [!IMPORTANT]  
>  Se [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è stato installato per l'esecuzione con un account di sistema locale anziché un account utente di dominio (impostazione predefinita), il servizio può accedere solo al computer locale. Se l'agente di distribuzione in esecuzione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent è configurato per l'utilizzo della modalità di autenticazione di Windows durante l'accesso a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'agente di distribuzione si interrompe. L'impostazione predefinita prevede l'autenticazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per informazioni sulla modifica degli account di sicurezza, vedere [View and Modify Replication Security Settings](../security/view-and-modify-replication-security-settings.md).  
  
 Per avviare l'agente di distribuzione, eseguire **distrib.exe** dal prompt dei comandi. Per informazioni, vedere [Concetti di base relativi ai file eseguibili dell'agente di replica](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="change-history"></a>Cronologia modifiche  
  
|Contenuto aggiornato|  
|---------------------|  
|Aggiunta del parametro **-ExtendedEventConfigFile** .|  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione dell'agente di replica](replication-agent-administration.md)  
  
  
