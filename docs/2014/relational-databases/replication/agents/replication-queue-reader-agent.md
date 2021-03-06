---
title: Agente di lettura coda repliche | Microsoft Docs
ms.custom: ''
ms.date: 10/29/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], Queue Reader Agent
- command prompt [SQL Server replication]
- Queue Reader Agent, parameter reference
- Queue Reader Agent, executables
ms.assetid: 8e227793-11f6-47c6-99dc-ffc282f5d4bf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d92a15ae855c5521319abd252b1f5a7efc2bf300
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63191671"
---
# <a name="replication-queue-reader-agent"></a>Agente di lettura coda repliche
  Il agente di lettura coda di replica è un eseguibile che consente di leggere [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i messaggi archiviati [!INCLUDE[msCoName](../../../includes/msconame-md.md)] in una coda o in una coda di messaggi e quindi di applicare tali messaggi al server di pubblicazione. L'agente di lettura coda viene utilizzato con le pubblicazioni snapshot e transazionali che consentono l'aggiornamento in coda.  
  
> [!NOTE]  
>  I parametri possono essere specificati in qualsiasi ordine. Quando i parametri facoltativi non vengono specificati, vengono utilizzati i valori predefiniti basati sul profilo agente predefinito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      qrdrsvc [-?]  
[-Continuous]  
[-DefinitionFiledefinition_file]  
[-Distributorserver_name[\instance_name]]  
[-DistributionDBdistribution_database]  
[-DistributorLogindistributor_login]  
[-DistributorPassworddistributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-HistoryVerboseLevel [0|1|2|3]]  
[-LoginTimeOutlogin_time_out_seconds]  
[-Outputoutput_path_and_file_name]  
[-OutputVerboseLevel [0|1|2]]  
[-PollingIntervalpolling_interval]  
[-PublisherFailoverPartnerserver_name[\instance_name] ]  
[-ProfileNameagent_profile_name]  
[-QueryTimeOutquery_time_out_seconds]  
[-ResolverState [1|2|3]]  
```  
  
## <a name="arguments"></a>Argomenti  
 **-?**  
 Visualizza le informazioni sull'utilizzo.  
  
 **-Continuo**  
 Specifica se l'agente tenta di elaborare continuamente le transazioni in coda. Se è specificato, l'agente continua l'esecuzione anche se non vi sono transazioni in coda in sospeso in alcuno dei Sottoscrittori.  
  
 **-DefinitionFile** _def_path_and_file_name_  
 Percorso del file di definizione dell'agente. Un file di definizione dell'agente contiene argomenti della riga di comando per l'agente. Il contenuto del file viene analizzato come file eseguibile. Utilizzare virgolette doppie (") per specificare valori dell'argomento contenenti caratteri arbitrari.  
  
 **-** _Server_name_database di**\\**distribuzione [_instance_name_]  
 Nome del database di distribuzione. Specificare *server_name* per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server. Specificare *server_name*\\*instance_name* per un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in tale server. Se non specificato, per impostazione predefinita viene utilizzato il nome dell'istanza predefinita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nel computer locale.  
  
 **-DistributionDB** _distribution_database_  
 Database di distribuzione.  
  
 **-DistributorLogin** _distributor_login_  
 Nome dell'account di accesso del database di distribuzione.  
  
 **-DistributorPassword** _distributor_password_  
 Password del database di distribuzione.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Specifica la modalità di sicurezza del database di distribuzione. Il valore **0** indica [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la modalità di autenticazione (impostazione predefinita), mentre un valore **1** indica la modalità di autenticazione di Windows.  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Livello di crittografia SSL (Secure Sockets Layer) utilizzato dall'agente di lettura coda quando vengono stabilite le connessioni.  
  
|Valore di EncryptionLevel|Descrizione|  
|---------------------------|-----------------|  
|**0**|Specifica che SSL non viene utilizzato.|  
|**1**|Specifica che SSL viene utilizzato, ma l'agente non verifica che il certificato server SSL sia firmato da un'autorità emittente attendibile.|  
|**2**|Specifica che SSL viene utilizzato e che il certificato viene verificato.|  

 > [!NOTE]  
 >  Un certificato SSL valido è definito con un nome di dominio completo del Server SQL. Affinché l'agente possa connettersi correttamente quando si imposta - EncryptionLevel su 2, creare un alias nel Server SQL locale. Il parametro 'Nome alias' deve corrispondere al nome del server e il parametro 'Server' deve essere impostato sul nome completo dell'istanza di SQL Server.
  
 Per ulteriori informazioni, vedere [replica di SQL Server sicurezza](../security/view-and-modify-replication-security-settings.md).  
  
 **-HistoryVerboseLevel più elevato** [ **0**| **1**| **2**| **3**]  
 Specifica la quantità di cronologia registrata durante un'operazione dell'agente di lettura coda. Per ridurre al minimo l'effetto della registrazione della cronologia sulle prestazioni, selezionare **1**.  
  
|Valore di HistoryVerboseLevel|Descrizione|  
|-------------------------------|-----------------|  
|**0**|Nessuna registrazione della cronologia (opzione non consigliata).|  
|**1**|Default. Aggiorna sempre un messaggio di cronologia precedente con lo stesso stato (avvio, avanzamento, esito positivo e così via). Se non è presente un record precedente con lo stesso stato, inserisce un nuovo record.|  
|**2**|Inserisce nuovi record della cronologia, inclusi record per messaggi inattivi o messaggi di processo con esecuzione prolungata.|  
|**3**|Inserisce nuovi record della cronologia che includono informazioni aggiuntive che potrebbero essere utili per la risoluzione dei problemi.|  
  
 **-LoginTimeOut** _login_time_out_seconds_  
 Numero di secondi prima del timeout dell'accesso. Il valore predefinito è 15 secondi.  
  
 **-Output** _output_path_and_file_name_  
 Percorso del file di output dell'agente. Se non viene specificato il nome file, l'output viene inviato alla console. Se il nome file specificato esiste già, l'output viene aggiunto al file.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2**]  
 Specifica se l'output deve essere dettagliato. Se il livello di dettaglio è **0**, vengono stampati solo i messaggi di errore. Se il livello di dettaglio è **1**, vengono stampati tutti i messaggi di report di stato. Se il livello di dettaglio è **2** (impostazione predefinita), vengono stampati tutti i messaggi di errore e i messaggi di report di stato. Questa opzione è utile per l'esecuzione del debug.  
  
 **-PollingInterval** _polling_interval_  
 Rilevante solo per sottoscrizioni aggiornabili che utilizzano code basate su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Specifica la frequenza, in secondi, di polling della coda [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per le transazioni in coda in sospeso. Il valore può essere compreso tra 0 e 240 secondi. Il valore predefinito è 5 secondi.  
  
 **-PublisherFailoverPartner** _server_name_[**\\**_instance_name_]  
 Specifica l'istanza del partner di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che partecipa in una sessione di mirroring del database con il database di pubblicazione. Per altre informazioni, vedere [Mirroring e replica del database &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-Profilename** _agent_profile_name_  
 Nome di un profilo agente utilizzato per fornire un set di valori predefiniti all'agente. Per altre informazioni, vedere [Profili degli agenti di replica](replication-agent-profiles.md).  
  
 **-QueryTimeOut** _query_time_out_seconds_  
 Numero di secondi prima del timeout della query. Il valore predefinito è 1800 secondi.  
  
 **-ResolverState** [ **1**| **2**| **3**]  
 Specifica in che modo vengono risolti i conflitti degli aggiornamenti in coda. Un valore **1** indica che il conflitto viene vinto dal server di pubblicazione e che verrà eseguito il rollback della transazione in coda in conflitto corrente nel server di pubblicazione e nel Sottoscrittore di aggiornamento di origine. L'elaborazione delle transazioni in coda successive continuerà. Un valore **2** indica che il conflitto viene vinto dal Sottoscrittore e che la transazione in coda sostituirà i valori nel server di pubblicazione. Un valore **3** indica che qualsiasi conflitto comporterà la reinizializzazione del Sottoscrittore. Il conflitto viene vinto dal server di pubblicazione, l'elaborazione delle transazioni in coda successive verrà interrotta e la sottoscrizione verrà reinizializzata. L'impostazione predefinita è **1** per le pubblicazioni transazionali e **3** per le pubblicazioni snapshot.  
  
## <a name="remarks"></a>Osservazioni  
 Per avviare l'agente di lettura coda, eseguire **qrdrsvc.exe** dal prompt dei comandi. Per informazioni, vedere [File eseguibili dell'Agente di replica](../concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione dell'agente di replica](replication-agent-administration.md)  
  
  
