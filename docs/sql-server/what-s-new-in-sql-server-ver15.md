---
title: Novità di SQL Server 2019 | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.prod: sql-server-2018
ms.reviewer: ''
ms.technology:
- server-general
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 015a6d65f1d225ab5a8752352d41fd2201f871b5
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461116"
---
# <a name="whats-new-in-sql-server-2019"></a>Novità di SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] si basa sulle versioni precedenti per sviluppare SQL Server come piattaforma provvista di scelte per linguaggi di sviluppo, tipi di dati, sistemi operativi ed elaborazione locale o nel cloud. Questo articolo riepiloga le novità di SQL Server 2019. Per altre informazioni e problemi noti, vedere le [Note sulla versione di SQL Server 2019](sql-server-ver15-release-notes.md).

**Per provare SQL Server 2019**
- [![Download da Evaluation Center](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=862101) [Scaricare SQL Server 2019 per l'installazione in Windows](http://go.microsoft.com/fwlink/?LinkID=862101)
- Installazione in Linux per [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) e [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Esecuzione in SQL Server 2019 in Docker](../linux/quickstart-install-connect-docker.md).

## <a name="ctp-20"></a>CTP 2.0 

Community Technology Preview (CTP) 2.0 è la prima versione pubblica di [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]. Di seguito sono descritte le funzionalità aggiunte o migliorate in [!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)] CTP 2.0.

- [Cluster Big Data](#bigdatacluster)
  - Distribuire un cluster Big Data con contenitori SQL e Spark Linux in Kubernetes
  - Accedere ai Big Data da HDFS
  - Eseguire l'analisi avanzata e l'apprendimento automatico con Spark
  - Usare lo streaming Spark per i dati dei pool di dati SQL
  - Usare Azure Data Studio per eseguire volumi Query che offrono un'esperienza di tipo notebook

- [Motore di database](#databaseengine)
  - Supporto UTF-8
  - L'istruzione di creazione indici online ripristinabili consente di ripristinare la creazione di indici dopo l'interruzione
  - Compilazione e ricompilazione degli indici columnstore cluster online
  - Always Encrypted con enclave sicuri
  - Elaborazione di query intelligenti
  - Estensione di programmabilità per il linguaggio Java
  - Funzionalità SQL Graph
  - Impostazione di configurazione con ambito database per operazioni DDL online e ripristinabili
  - Gruppi di disponibilità Always On - Reindirizzamento della connessione di replica secondaria
  - Individuazione e classificazione dei dati - Integrata in modo nativo in SQL Server
  - Supporto esteso per i dispositivi con memoria persistente
  - Supporto delle statistiche columnstore in `DBCC CLONEDATABASE`
  - Nuove opzioni aggiunte a `sp_estimate_data_compression_savings`
  - Cluster di failover di SQL Server Machine Learning Services
  - Infrastruttura leggera di profilatura query abilitata per impostazione predefinita
  - Nuovi connettori PolyBase
  - La nuova funzione di sistema `sys.dm_db_page_info` restituisce informazioni sulla pagina

- [SQL Server in Linux](#sqllinux)
  - Supporto della replica
  - Supporto di Microsoft Distributed Transaction Coordinator (MSDTC)
  - Gruppo di disponibilità AlwaysOn in contenitori Docker con Kubernetes
  - Supporto OpenLDAP per provider AD di terze parti
  - Machine Learning in Linux
  - Nuovo registro contenitori
  - Nuove immagini del contenitore basate su RHEL
  - Notifica dell'utilizzo elevato della memoria

- [Master Data Services](#mds)
  - Controlli Silverlight sostituiti

- [Security](#security)
  - Gestione dei certificati in Gestione configurazione SQL Server

- [Strumenti](#tools)
  - SQL Server Management Studio (SSMS) 18.0 (anteprima)
  - Azure Data Studio

Continuare a leggere per altri dettagli su queste funzionalità.

## <a id="bigdatacluster"></a>Cluster Big Data

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] I [cluster Big Data](../big-data-cluster/big-data-cluster-overview.md) rendono disponibili nuovi scenari come i seguenti:

- Distribuire un cluster Big Data con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e contenitori Spark Linux in Kubernetes
- Accedere ai Big Data da HDFS
- Eseguire l'analisi avanzata e l'apprendimento automatico con Spark
- Usare lo streaming Spark per i dati dei pool di dati SQL
- Eseguire volumi Query che offrono un'esperienza di tipo notebook in [**Azure Data Studio**](../sql-operations-studio/what-is.md).
  
[!INCLUDE [Big Data Clusters preview](../includes/big-data-cluster-preview-note.md)]

## Motore di database <a id="databaseengine"></a>

CTP 2.0 introduce o migliora le nuove funzionalità seguenti per [!INCLUDE[ssdeNoVersion](../includes/ssdenoversion_md.md)].

### <a name="database-compatibility-level"></a>Livello di compatibilità del database

È stata aggiunto il livello **COMPATIBILITY_LEVEL 150** del database. Per attivarlo per un database utente specifico, eseguire:

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

### <a name="utf-8-support"></a>Supporto UTF-8

Supporto completo per la codifica dei caratteri di grande diffusione UTF-8 come codifica di importazione o esportazione o come regola di confronto di livello database o colonna per i dati di testo. La codifica UTF-8 è consentita nei tipi di dati `CHAR` e `VARCHAR` ed è abilitata quando si crea o si modifica la regola di confronto di un oggetto convertendola in una regola di confronto con il suffisso `UTF8`. 

Ad esempio da `LATIN1_GENERAL_100_CI_AS_SC` a `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. UTF-8 è disponibile solo per le regole di confronto di Windows che supportano i caratteri supplementari. Questa funzionalità è stata introdotta in SQL Server 2012. `NCHAR` e `NVARCHAR` consentono solo la codifica UTF-16 e rimangono invariati.

A seconda del set di caratteri in uso, questa funzionalità può offrire importanti risparmi di risorse di archiviazione. Se ad esempio si cambia il tipo di dati di una colonna esistente e contenente stringhe ASCII da `NCHAR(10)` a `CHAR(10)` usando una regola di confronto con supporto di UTF-8, i requisiti di risorse di archiviazione vengono ridotti quasi del 50%. Questa riduzione deriva dal fatto che `NCHAR(10)` richiede 22 byte per l'archiviazione, mentre `CHAR(10)` richiede solo 12 byte per la stessa stringa Unicode.

### <a name="resumable-online-index-create"></a>Creazione di indici online ripristinabili

- Con la **creazione di indici online ripristinabili** un'operazione di creazione indice può essere sospesa e ripresa in seguito dal punto in cui è stata interrotta, anziché riavviarla dall'inizio.

  La creazione di indici online ripristinabili supporta gli scenari seguenti:
  - Ripristino di un'operazione di creazione indice dopo un errore di creazione indice, ad esempio in seguito a un failover del database o all'esaurimento dello spazio su disco.
  - Sospensione temporanea di un'operazione di creazione indice e ripresa in un secondo momento, per consentire di liberare temporaneamente risorse di sistema in base alle esigenze e quindi riprendere l'esecuzione.
  - Creazione di indici di grandi dimensioni senza usare grandi quantità spazio di registro, senza un'esecuzione prolungata che blocca altre attività di manutenzione e con la possibilità di troncare il log.

  In caso di un errore di creazione indice, senza questa funzionalità la creazione indice online va eseguita di nuovo e l'operazione deve essere riavviata dall'inizio.

In questa versione, la funzionalità ripristinabile viene estesa con l'aggiunta di questa funzionalità alla [ricompilazione dell'indice online ripristinabile](http://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/), già disponibile.

È anche possibile impostare questa funzionalità come valore predefinito per un database specifico usando l'[impostazione predefinita con ambito database per le operazioni DDL online e ripristinabili](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

Per altre informazioni, vedere [Creazione di indici online ripristinabili](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

### <a name="build-and-rebuild-clustered-columnstore-indexes-online"></a>Compilare e ricompilare gli indici columnstore cluster online

È possibile convertire le tabelle rowstore al formato columnstore. Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la creazione di indici columnstore cluster (CCI) era un processo offline la cui esecuzione richiedeva la sospensione di tutte le modifiche. Con [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] e [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] è possibile creare o ricreare indici columnstore cluster online. Il carico di lavoro non viene bloccato e tutte le modifiche apportate ai dati sottostanti vengono aggiunte in modo trasparente nella tabella columnstore di destinazione. Di seguito sono elencati alcuni esempi di nuove istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] che è possibile usare:

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted con enclave sicuri

Espansione di Always Encrypted con crittografia sul posto e calcoli avanzati. Le espansioni provengono dall'abilitazione di calcoli sui dati di testo non crittografato all'interno di un enclave sicuro sul lato server.

Le operazioni di crittografia includono la crittografia delle colonne e la rotazione delle chiavi di crittografia della colonna. Queste operazioni possono ora essere trasmesse usando [!INCLUDE[tsql](../includes/tsql-md.md)] e non richiedono lo spostamento dei dati fuori dal database. Gli enclave sicuri rendono disponibile Always Encrypted per una vasta gamma di scenari, che dispongono di entrambi i requisiti seguenti:  

- L'esigenza di proteggere i dati sensibili da utenti con privilegi elevati ma non provvisti delle autorizzazioni necessarie, quali amministratori di database, amministratori di sistema, operatori cloud o istanze di malware.
- L'esigenza di supportare calcoli avanzati sui dati protetti all'interno del sistema di database.

Per informazioni dettagliate, vedere [Always Encrypted con enclave sicuri](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Always Encrypted con enclave sicuri è disponibile solo nel sistema operativo Windows.

### <a name="intelligent-query-processing"></a>Elaborazione di query intelligenti

- Il **feedback delle concessioni di memoria in modalità riga** estende la funzionalità di feedback delle concessioni di memoria, adattando le dimensioni delle concessioni di memoria introdotte in [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] sia per gli operatori in modalità batch che per quelli in modalità riga.  Per una condizione di concessione di memoria di dimensioni eccessive, se la memoria concessa supera di oltre due volte la quantità di memoria realmente usata, il feedback delle concessioni di memoria ricalcola la concessione. Le esecuzioni consecutive richiederanno quindi una quantità di memoria inferiore. Per le concessioni di memoria di dimensioni insufficienti che generano distribuzioni su disco, il feedback delle concessioni di memoria attiva il ricalcolo della concessione di memoria. Le esecuzioni consecutive richiederanno quindi una quantità di memoria superiore. Questa funzionalità è abilitata per impostazione predefinita nel livello di compatibilità del database 150.

- **Approximate COUNT DISTINCT** restituisce il numero approssimativo di valori univoci non Null in un gruppo. Questa funzione è progettata per l'uso in scenari Big Data. È ottimizzata per le query in cui sono vere tutte le condizioni seguenti:
   - Accede a set di dati costituiti da milioni di righe.
   - Definisce l'aggregazione di una o più colonne con un numero elevato di valori distinti.
   - La velocità di risposta è più importante della precisione assoluta.
      - `APPROX_COUNT_DISTINCT` restituisce i risultati con un'approssimazione alla risposta precisa pari al 2%.
      - La risposta approssimata viene restituita in una frazione minima del tempo necessario per la risposta esatta.

- La **modalità batch per rowstore** non richiede più un indice columnstore per l'elaborazione di una query in modalità batch. La modalità batch consente agli operatori di query di funzionare su un set di righe, anziché su una sola riga alla volta. Questa funzionalità è abilitata per impostazione predefinita nel livello di compatibilità del database 150. La modalità batch migliora la velocità delle query che accedono a tabelle rowstore quando sono soddisfatte le condizioni seguenti:
   - La query usa operatori analitici, ad esempio operatori di join o di aggregazione.
   - La query implica un numero di righe non inferiore a 100.000.
   - La query è associata alla CPU anziché all'input/output di dati.
   - La creazione e l'uso di un indice columnstore può comportare uno degli svantaggi seguenti:
      - Aggiunge un sovraccarico eccessivo alla query.
      - Non è implementabile perché l'applicazione dipende da una funzionalità non ancora supportata con gli indici columnstore.

- **La compilazione posticipata delle variabili di tabella** migliora la qualità del piano e le prestazioni generali per le query che fanno riferimento a variabili di tabella. Durante l'ottimizzazione e la compilazione iniziale, questa funzionalità propagherà le stime della cardinalità basate sui conteggi effettivi delle righe di variabili di tabella.  Queste informazioni accurate sui conteggi di righe verranno usate per l'ottimizzazione delle operazioni del piano downstream. Questa funzionalità è abilitata per impostazione predefinita nel livello di compatibilità del database 150.

Per usare la funzionalità di elaborazione di query intelligenti impostare l'opzione del database `COMPATIBILITY_LEVEL = 150`.

### <a id="programmability"></a> Estensioni di programmabilità per il linguaggio Java

- **Estensione per il linguaggio Java (anteprima)**: usare l'estensione per il linguaggio Java per eseguire il codice Java in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] questa estensione viene installata quando si aggiunge la funzionalità "Machine Learning Services (in-database)" all'istanza di SQL Server.

### <a id="sqlgraph"></a> Funzionalità SQL Graph

- **Il supporto delle corrispondenze in `MERGE` DML** consente di specificare relazioni grafo in un'unica istruzione anziché in istruzioni `INSERT`, `UPDATE` o `DELETE` separate. È possibile unire i dati grafo correnti da tabelle nodi o tabelle archi a nuovi dati usando i predicati `MATCH` nell'istruzione `MERGE`. Questa funzionalità abilita gli scenari `UPSERT` nelle tabelle bordi. Ora gli utenti possono usare un'istruzione merge singola per inserire un nuovo bordo o aggiornarne uno esistente tra due nodi.

- Sono stati introdotti i **vincoli di bordo** per le tabelle bordi in SQL Graph. Le tabelle bordi possono connettere qualsiasi nodo a qualsiasi altro nodo del database. Con l'introduzione di vincoli di bordo, è ora possibile applicare determinate restrizioni a questo comportamento. Il nuovo vincolo `CONNECTION` consente di specificare il tipo di nodi ai quali può connettersi una tabella bordi nello schema.

### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations"></a>Impostazione predefinita con ambito database per operazioni DDL online e ripristinabili 

- L'**impostazione predefinita con ambito database per operazioni DDL online e ripristinabili** supporta un'impostazione di funzionamento predefinita per le operazioni indice `ONLINE` e `RESUMABLE` a livello del database, anziché definire tali opzioni per ogni singola istruzione DDL dell'indice, quali le operazioni di creazione o ricompilazione dell'indice.

- Impostare questi valori predefiniti usando le opzioni di configurazione con ambito database `ELEVATE_ONLINE` e `ELEVATE_RESUMABLE`. Entrambe le opzioni fanno sì che il motore del database imposti automaticamente le operazioni dell'indice supportate per l'esecuzione online o ripristinabili. È possibile abilitare i comportamenti seguenti tramite queste opzioni:

  - L'opzione `FAIL_UNSUPPORTED` autorizza tutte le operazioni sugli indici online o ripristinabili e non consente le operazioni sugli indici online o ripristinabili non supportate.
  - L'opzione `WHEN_SUPPPORTED` consente le operazioni online o ripristinabili supportate ed esegue le operazioni sugli indici non supportate non in linea o in modo non ripristinabile.
  - L'opzione `OFF` supporta il comportamento corrente di esecuzione di tutte le operazioni sugli indici come offline e non ripristinabili, salvo diversa indicazione esplicita nell'istruzione DDL.

Per eseguire l'override dell'impostazione predefinita, includere l'opzione ONLINE o l'opzione RESUMABLE nei comandi di creazione e ricompilazione dell'indice.  

Senza questa funzionalità è necessario specificare le opzioni online e ripristinabili direttamente nell'istruzione DDL dell'indice, ad esempio nell'istruzione di creazione e ricompilazione dell'indice.

Altre informazioni: per altre informazioni sulle operazioni ripristinabili, vedere [Creazione di indici online ripristinabili](http://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/).

### <a id="ha"></a>Gruppi di disponibilità AlwaysOn - Più repliche sincrone 

- **Fino a cinque repliche sincrone**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] aumenta il numero massimo di repliche sincrone fino a 5. Il numero massimo era 3 in [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. È possibile configurare questo gruppo di 5 repliche per il failover automatico all'interno del gruppo. Sono presenti 1 replica primaria e 4 repliche secondarie sincrone.

- **Reindirizzamento della connessione di replica da secondaria a primaria**: consente di orientare le connessioni dell'applicazione client alla replica primaria, indipendentemente dal server di destinazione specificato nella stringa di connessione. Questa funzionalità consente il reindirizzamento della connessione senza un listener. Usare il reindirizzamento della connessione di replica da secondaria a primaria se si verificano le condizioni seguenti:

  - La tecnologia cluster non offre una funzionalità listener.
  - È implementata una configurazione con più subnet in cui il reindirizzamento diventa complesso.
  - Scenari di scalabilità in lettura o ripristino di emergenza in cui il tipo di cluster è `NONE`.

Per informazioni dettagliate, vedere [Secondary to primary replica read/write connection redirection (Always On Availability Groups)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) (Reindirizzamento connessione in lettura/scrittura dalla replica secondaria alla primaria (Gruppi di disponibilità AlwaysOn)).

### <a name="data-discovery-and-classification"></a>Individuazione e classificazione dei dati

Funzionalità avanzate di individuazione e classificazione dei dati incorporate a livello nativo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La classificazione e l'assegnazione di etichette ai dati più sensibili offre i vantaggi seguenti:
- Contribuisce a soddisfare i requisiti in materia di privacy e di conformità alle normative.
- Supporta scenari di sicurezza quali il monitoraggio (controllo) e gli avvisi in caso di accesso anomalo ai dati sensibili.
- Semplifica l'identificazione della posizione dei dati sensibili nell'organizzazione, in modo che gli amministratori possano adottare le misure necessarie per la protezione del database.

Per altre informazioni, vedere [Individuazione dati e classificazione SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

Anche il [controllo](../relational-databases/security/auditing/sql-server-audit-database-engine.md) è stato migliorato e il log di controllo ora include un nuovo campo denominato `data_sensitivity_information`, che registra le classificazioni (etichette punteggio) di riservatezza dei dati effettivi restituiti dalla query. Per dettagli ed esempi vedere [ADD SENSITIVITY CLASSIFICATION](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>Non sono state apportate modifiche alle modalità di abilitazione del controllo. È stato aggiunto ai record di controllo un nuovo campo `data_sensitivity_information`, che registra le classificazioni (etichette punteggio) di riservatezza dei dati effettivi restituiti dalla query. Vedere [Controllo dell'accesso ai dati sensibili](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification#subheading-3).

### <a name="expanded-support-for-persistent-memory-devices"></a>Supporto esteso per i dispositivi con memoria persistente

Qualsiasi file [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] inserito in un dispositivo con memoria persistente può ora essere eseguito in modalità *con riconoscimento*. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] accede direttamente al dispositivo, ignorando lo stack di archiviazione del sistema operativo e usando operazioni memcpy efficienti. Questa modalità migliora le prestazioni poiché consente input/output a bassa latenza su tali dispositivi.
    - Esempi di file [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] includono:
        - File di database
        - File di log delle transazioni
        - File del checkpoint OLTP in memoria
    - La memoria persistente è anche detta memoria della classe di archiviazione.
    - La memoria persistente è talvolta denominata in modo informale *pmem* in siti Web non Microsoft.

> [!NOTE]
> Per questa versione di anteprima il riconoscimento dei file nei dispositivi con memoria persistente è disponibile solo per Linux. SQL Server in Windows supporta i dispositivi con memoria persistente a partire da SQL Server 2016.

### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase"></a>Supporto delle statistiche columnstore in DBCC CLONEDATABASE

`DBCC CLONEDATABASE` crea una copia di un database con il solo schema, che include tutti gli elementi necessari per la risoluzione dei problemi di prestazioni delle query senza copiare i dati.  Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] il comando non copiava le statistiche necessarie per rilevare con precisione i problemi delle query dell'indice columnstore e per acquisire queste informazioni erano necessari passaggi manuali. Ora in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] DBCC CLONEDATABASE acquisisce automaticamente i BLOB di statistiche per gli indici columnstore. Di conseguenza non sono necessari passaggi manuali.

### <a name="new-options-added-to-spestimatedatacompressionsavings"></a>Nuove opzioni aggiunte a sp_estimate_data_compression_savings

`sp_estimate_data_compression_savings` restituisce le dimensioni correnti degli oggetti richiesti e stima le dimensioni dell'oggetto per lo stato di compressione richiesto.  Questa procedura supporta attualmente tre opzioni: `NONE`, `ROW` e `PAGE`. SQL Server 2019 introduce due nuove opzioni: `COLUMNSTORE` e `COLUMNSTORE_ARCHIVE`. Le nuove opzioni consentono di stimare il risparmio di spazio ottenibile con la creazione di un indice columnstore sulla tabella usando la compressione del columnstore standard o archivio.

### <a id="ml"></a> Cluster di failover di SQL Server Machine Learning Services e modellazione basata sulle partizioni

- **Modellazione basata sulle partizioni**: elabora gli script esterni per le singole partizioni dei dati usando i nuovi parametri aggiunti a `sp_execute_external_script`. Questa funzionalità supporta il training di molti modelli di dimensioni ridotte (un modello per ogni partizione dei dati) invece del training di un solo modello di grandi dimensioni.

- **Cluster di failover di Windows Server**: è possibile configurare la disponibilità elevata per Machine Learning Services in un cluster di failover di Windows Server.

Per informazioni dettagliate, vedere [What's new in SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) (Novità di SQL Server Machine Learning Services).

### <a name="lightweight-query-profiling-infrastructure-enabled-by-default"></a>Infrastruttura leggera di profilatura query abilitata per impostazione predefinita

L'infrastruttura leggera di profilatura query (LWP) restituisce dati sulle prestazioni delle query in modo più efficiente rispetto alle tecnologie di profilatura standard. Ora la profilatura leggera è abilitata per impostazione predefinita. È stata introdotta in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1. La profilatura leggera offre un meccanismo per la raccolta di statistiche sull'esecuzione query con un sovraccarico previsto pari al 2% della capacità della CPU, rispetto a un sovraccarico che può raggiungere il 75% della capacità della CPU per il meccanismo di profilatura query standard. Nelle versioni precedenti, questa funzionalità era OFF per impostazione predefinita. Gli amministratori di database potevano abilitarla con il [flag di traccia 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md). 

Per altre informazioni sulla profilatura leggera, vedere [Developers Choice: Query progress – anytime, anywhere](http://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) (Scelta degli sviluppatori: Stato query ovunque e in qualsiasi momento).

### <a id="polybase"></a>Nuovi connettori PolyBase

- **Nuovi connettori per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata e MongoDB**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] presentazione di nuovi connettori a dati esterni per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata e MongoDB.

### <a name="new-sysdmdbpageinfo-system-function-returns-page-information"></a>La nuova funzione di sistema sys.dm_db_page_info restituisce informazioni sulla pagina

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` restituisce informazioni su una pagina di un database. La funzione restituisce una riga che contiene le informazioni di intestazione della pagina, tra cui `object_id`, `index_id` e `partition_id`. Questa funzione sostituisce l'uso di `DBCC PAGE` nella maggior parte dei casi.  

Per facilitare la risoluzione dei problemi associati alle attese correlate alla pagina è stata anche aggiunta a `sys.dm_exec_requests` e `sys.sysprocesses` la nuova colonna page_resource. La nuova colonna consente di unire `sys.dm_db_page_info` a queste viste tramite un'altra nuova funzione di sistema: `sys.fn_PageResCracker`. Vedere come esempio lo script seguente:

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

## <a id="sqllinux"></a> SQL Server in Linux

- **Supporto della replica**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] supporta la replica di SQL Server in Linux. Una macchina virtuale Linux con SQL Agent può essere un'entità di pubblicazione, di distribuzione o un sottoscrittore. 

  Creare i seguenti tipi di pubblicazioni:
  - Transazionale
  - Snapshot
  - Merge

  Configurare la replica [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oppure usare le [stored procedure di replica](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Supporto di Microsoft Distributed Transaction Coordinator (MSDTC)**: SQL Server 2019 in Linux supporta Microsoft Distributed Transaction Coordinator (MSDTC). Per informazioni dettagliate, vedere [Come configurare Microsoft Distributed Transaction Coordinator (MSDTC) in Linux](../linux/sql-server-linux-configure-msdtc.md).

- **Gruppo di disponibilità AlwaysOn in contenitori Docker con Kubernetes**: Kubernetes può orchestrare i contenitori che eseguono istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per restituire un set di database a disponibilità elevata con Gruppi di disponibilità Always On di SQL Server. Un operatore Kubernetes distribuisce un elemento StatefulSet che include un contenitore con **mssql-server** e un monitoraggio di integrità.

- **Supporto OpenLDAP per provider AD di terze parti**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] in Linux è supportato OpenLDAP, che consente ai fornitori di terze parti di accedere a Active Directory.

- **Machine Learning in Linux**: SQL Server 2019 Machine Learning Services (In-Database) è ora supportato in Linux. Il supporto include la stored procedure `sp_execute_external_script`. Per istruzioni relative all'installazione di Machine Learning Services in Linux, vedere [Installare SQL Server 2019 Machine Learning Services (R, Python, Java) in Linux](../linux/sql-server-linux-setup-machine-learning.md).

- **Nuovo registro contenitori**: tutte le immagini del contenitore per [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] e per [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] si trovano ora nel Registro contenitori Microsoft. Il Registro contenitori Microsoft è il registro contenitori ufficiale per la distribuzione di contenitori prodotto Microsoft. Ora vengono anche pubblicate le immagini certificate basate su RHEL.

  - Registro contenitori Microsoft: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Immagini del contenitore certificate basate su RHEL: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

## <a id="mds"></a> Master Data Services (MDS)

- **Controlli Silverlight sostituiti con HTML**: il portale Master Data Services (MDS) non è più dipendente da Silverlight. Tutti i componenti Silverlight precedenti sono stati sostituiti con controlli HTML.

## <a id="security"></a>Security

- **Gestione dei certificati in Gestione configurazione SQL Server**: i certificati SSL/TLS sono molto usati per garantire l'accesso alle istanze di SQL Server. La gestione dei certificati è ora integrata in Gestione configurazione SQL Server e questo semplifica varie attività comuni, ad esempio:

  - Visualizzazione e convalida di certificati installati in un'istanza [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 
  - Visualizzazione di certificati prossimi alla scadenza.
  - Distribuzione di certificati tra computer appartenenti a gruppi di disponibilità AlwaysOn (dal nodo che contiene la replica primaria).
  - Distribuzione di certificati tra computer appartenenti a un'istanza del cluster di failover (dal nodo attivo).

  > [!NOTE]
  > L'utente deve avere autorizzazioni amministratore per tutti i nodi del cluster.

## <a id="tools"></a>Strumenti

- [**Azure Data Studio**](../azure-data-studio/what-is.md): rilasciato in precedenza con il nome di anteprima di SQL Operations Studio, Azure Data Studio è uno strumento desktop leggero, moderno, open source e multipiattaforma per le attività più comuni di sviluppo e amministrazione di dati. Con Azure Data Studio è possibile connettersi a SQL Server in locale e nel cloud su Windows, macOS e Linux. Con Azure Data Studio è possibile:

  - Modificare ed eseguire query in un ambiente di sviluppo moderno, con esecuzione rapida di Intellisense, frammenti di codice e integrazione del controllo codice sorgente.  
  - Visualizzare rapidamente i dati con la funzionalità predefinita di creazione grafici dai set di risultati.  
  - Creare dashboard personalizzati per i server e i database mediante widget personalizzabili.  
  - Gestire facilmente l'ambiente nel suo complesso, grazie al terminale incorporato.  
  - Analizzare i dati con un'esperienza di tipo notebook integrata basata su Jupyter.  
  - Migliorare l'esperienza con estensioni e temi personalizzati.  
  - Esplorare le risorse di Azure con un browser incorporato degli abbonamenti e delle risorse.
  - La soluzione supporta gli scenari che usano il cluster Big Data di SQL Server.


- [**SQL Server Management Studio (SSMS) 18.0 (anteprima)**](../ssms/sql-server-management-studio-ssms.md)

  - Supporto di [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].
  - Supporto di Always Encrypted con enclave sicuri.
  - File di download di dimensioni più piccole.
  - Ora basato su Visual Studio 2017 Isolated Shell.
  - Per l'elenco completo, vedere il [log delle modifiche SSMS](../ssms/sql-server-management-studio-changelog-ssms.md).

## <a name="other-services"></a>Altri servizi

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 non introduce nuove funzionalità per i servizi seguenti:

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="next-steps"></a>Passaggi successivi

- [Note sulla versione di SQL Server 2019](sql-server-ver15-release-notes.md)

- [Microsoft SQL Server 2019: White paper tecnico](https://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Pubblicato in settembre 2018. Valido per Microsoft SQL Server 2019 CTP 2.0 per Windows, Linux e i contenitori Docker.


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
