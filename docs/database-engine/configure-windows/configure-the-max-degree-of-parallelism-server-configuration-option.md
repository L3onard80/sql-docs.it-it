---
title: Configurare l'opzione di configurazione del server max degree of parallelism | Microsoft Docs
ms.custom: ''
ms.date: 02/12/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
- MaxDop
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 94f8c87e0b996be0b9485cbe5a43038e33420fe0
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "79288725"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a>Configurare l'opzione di configurazione del server max degree of parallelism
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Questo argomento illustra come configurare l'opzione di configurazione del server **max degree of parallelism (MAXDOP)** in SQL Server usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Quando un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguita in un computer con più microprocessori o CPU, viene automaticamente rilevato il grado di parallelismo, ovvero il numero di processori usati per eseguire una singola istruzione per l'esecuzione di ogni piano parallelo. È possibile utilizzare l'opzione **max degree of parallelism** per limitare il numero di processori da utilizzare nell'esecuzione di piani paralleli. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valuta i piani di esecuzione parallela per query, operazioni DDL (Data Definition Language) sugli indici, inserimento parallelo, modifica colonna online, raccolta di statistiche parallela e popolamento dei cursori statici e gestiti da keyset.

> [!NOTE]
> [!INCLUDE [sssqlv15-md](../../includes/sssqlv15-md.md)] presenta raccomandazioni automatiche per l'impostazione dell'opzione di configurazione del server MAXDOP durante il processo di installazione. L'interfaccia utente del programma di installazione consente di accettare le impostazioni consigliate o di immettere valori personalizzati. Per altre informazioni, vedere [Pagina Configurazione del motore di database - MaxDOP](../../sql-server/install/instance-configuration.md#maxdop).

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se l'opzione affinity mask non è impostata sul valore predefinito, il numero di processori disponibili per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in sistemi SMP (multiprocessori simmetrici, Symmetric Multiprocessor) potrebbe risultare ridotto.  

-   Il limite del **massimo grado di parallelismo (MAXDOP)** è impostato per [attività](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md). Non è un limite per [richiesta](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) o per query. Ciò significa che durante l'esecuzione di query parallele una singola richiesta può generare più attività che vengono assegnate a un'utilità di pianificazione. Per altre informazioni, vedere [Guida sull'architettura dei thread e delle attività](../../relational-databases/thread-and-task-architecture-guide.md). 
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Raccomandazioni  
  
-   Questa opzione è avanzata e la relativa modifica è riservata ad amministratori di database esperti o a professionisti dotati di certificazione per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Per consentire al server di determinare il grado massimo di parallelismo, impostare questa opzione su 0, cioè il valore predefinito. L'impostazione di grado massimo di parallelismo su 0 consente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di utilizzare tutti i processori disponibili fino a un massimo di 64. Per eliminare la generazione di piani paralleli, impostare **max degree of parallelism** su 1. Impostare il valore su un numero compreso tra 1 e 32.767 per specificare il numero massimo di core del processore che può essere utilizzato per l'esecuzione di una singola query. Se il valore è maggiore di quello dei processori disponibili, viene utilizzato il numero effettivo di processori disponibili. Se il computer dispone di un unico processore, il valore di **max degree of parallelism** verrà ignorato.  
  
-   È possibile sostituire il valore di max degree of parallelism nelle query specificando l'hint per la query MAXDOP nell'istruzione per la query. Per altre informazioni, vedere [Hint per la query &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
-   Le operazioni tramite cui viene creato o ricompilato un indice o eliminato un indice cluster possono richiedere un elevato utilizzo di risorse. È possibile sostituire il valore di max degree of parallelism per le operazioni sugli indici specificando l'opzione per gli indici MAXDOP nell'istruzione per l'indice. Il valore MAXDOP viene applicato all'istruzione al momento dell'esecuzione e non viene archiviato nei metadati dell'indice. Per altre informazioni, vedere [Configurazione di operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
-   Oltre al parallelismo delle query e delle operazioni sugli indici, questa opzione controlla anche il parallelismo dei controlli DBCC CHECKTABLE, DBCC CHECKDB e DBCC CHECKFILEGROUP. È possibile disabilitare i piani di esecuzione parallela per queste istruzioni utilizzando il flag di traccia 2528. Per altre informazioni, vedere [Flag di traccia &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md).

> [!TIP]
> Per eseguire questa operazione a livello di query, usare l'**hint per la query** [MAXDOP](../../t-sql/queries/hints-transact-sql-query.md).     
> Per eseguire questa operazione a livello di database, usare la **configurazione con ambito database** [MAXDOP](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).      
> Per eseguire questa operazione a livello di carico di lavoro, usare l'**opzione di configurazione del gruppo di carico di lavoro di Resource Governor** [MAX_DOP](../../t-sql/statements/create-workload-group-transact-sql.md).      

###  <a name="guidelines"></a><a name="Guidelines"></a> Linee guida  
A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], se, all'avvio del servizio, [!INCLUDE[ssde_md](../../includes/ssde_md.md)] rileva più di otto core fisici per ogni nodo o socket NUMA all'avvio, vengono creati automaticamente nodi soft-NUMA per impostazione predefinita. [!INCLUDE[ssde_md](../../includes/ssde_md.md)] inserisce processori logici dello stesso core fisico in nodi soft-NUMA diversi. Le raccomandazioni contenute nella tabella seguente consentono di mantenere tutti i thread di lavoro di una query parallela nello stesso nodo soft-NUMA. Questo comportamento permette di migliorare le prestazioni delle query e la distribuzione dei thread di lavoro tra i nodi NUMA per il carico di lavoro. Per altre informazioni, vedere [Soft-NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md).

A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], usare le linee guida seguenti quando si configura il valore di configurazione del server **max degree of parallelism**:

||||
|----------------|-----------------|-----------------|
|Server con un singolo nodo NUMA|Minore o uguale a 8 processori logici|Mantenere MAXDOP uguale o inferiore al numero di processori logici|
|Server con un singolo nodo NUMA|Più di 8 processori logici|Mantenere MAXDOP su 8|
|Server con più nodi NUMA|Minore o uguale a 16 processori logici per nodo NUMA|Mantenere MAXDOP uguale o inferiore al numero di processori logici per nodo NUMA|
|Server con più nodi NUMA|Più di 16 processori logici per nodo NUMA|Impostare per MAXDOP su un valore pari alla metà del numero di processori logici per nodo NUMA senza superare il valore MAX di 16|
  
> [!NOTE]
> Per nodo NUMA nella tabella precedente si intendono i nodi soft-NUMA creati automaticamente da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e versioni successive oppure i nodi NUMA basati su hardware se soft-NUMA è stato disabilitato.   
>  Usare le stesse linee guida quando si configura l'opzione max degree of parallelism per gruppi di carico di lavoro di Resource Governor. Per altre informazioni, vedere [CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md).
  
A partire da [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] e fino a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], usare le linee guida seguenti quando si configura il valore di configurazione del server **max degree of parallelism**:

||||
|----------------|-----------------|-----------------|
|Server con un singolo nodo NUMA|Minore o uguale a 8 processori logici|Mantenere MAXDOP uguale o inferiore al numero di processori logici|
|Server con un singolo nodo NUMA|Più di 8 processori logici|Mantenere MAXDOP su 8|
|Server con più nodi NUMA|Minore o uguale a 8 processori logici per nodo NUMA|Mantenere MAXDOP uguale o inferiore al numero di processori logici per nodo NUMA|
|Server con più nodi NUMA|Più di 8 processori logici per nodo NUMA|Mantenere MAXDOP su 8|
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 Le autorizzazioni di esecuzione per **sp_configure** senza alcun parametro o solo con il primo parametro vengono assegnate per impostazione predefinita a tutti gli utenti. Per eseguire **sp_configure** con entrambi i parametri per la modifica di un'opzione di configurazione o per l'esecuzione dell'istruzione RECONFIGURE, a un utente deve essere concessa l'autorizzazione a livello di server ALTER SETTINGS. L'autorizzazione ALTER SETTINGS è assegnata implicitamente ai ruoli predefiniti del server **sysadmin** e **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Per configurare l'opzione max degree of parallelism  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del mouse su un server e scegliere **Proprietà**.  
  
2.  Fare clic sul nodo **Avanzate** .  
  
3.  Nella casella **Max Degree of Parallelism** selezionare il numero massimo di processori da utilizzare nell'esecuzione di piani paralleli.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Con Transact-SQL  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>Per configurare l'opzione max degree of parallelism  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si illustra come utilizzare [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) per configurare l'opzione `max degree of parallelism` su `16`.  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 16;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)sia installato il servizio WMI.  
  
##  <a name="follow-up-after-you-configure-the-max-degree-of-parallelism-option"></a><a name="FollowUp"></a> Completamento: Dopo la configurazione dell'opzione max degree of parallelism  
 L'impostazione diventa effettiva immediatamente senza dover riavviare il server.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)      
 [Indicazioni e linee guida per l'opzione di configurazione "max degree of parallelism" in SQL Server](https://support.microsoft.com/help/2806535)     
 [Opzione di configurazione del server affinity mask](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Guida sull'architettura di elaborazione delle query](../../relational-databases/query-processing-architecture-guide.md#DOP)       
 [Guida sull'architettura dei thread e delle attività](../../relational-databases/thread-and-task-architecture-guide.md)    
 [Configurazione di operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md)    
 [Hint di query &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)     
 [Impostare le opzioni di indice](../../relational-databases/indexes/set-index-options.md)     
