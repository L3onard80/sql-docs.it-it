---
title: sys.dm_exec_query_statistics_xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: e5cb0bdbbbb535293835a0114061d8ca322ec8a8
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51675100"
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Restituisce il piano di esecuzione per le richieste in elaborazione delle query. Utilizzare questa DMV per recuperare i file XML dello showplan con le statistiche temporanee. 

## <a name="syntax"></a>Sintassi

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>Argomenti 
*session_id*  
 L'id di sessione è in esecuzione batch per essere cercato. *session_id* viene **smallint**. *session_id* può essere ottenuto dagli oggetti a gestione dinamica seguenti:  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>Tabella restituita
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|ID della sessione. Non ammette i valori NULL.|
|request_id|**int**|ID della richiesta. Non ammette i valori NULL.|
|sql_handle|**varbinary(64)**|Mappa hash del testo SQL della richiesta. Ammette valori Null.|
|plan_handle|**varbinary(64)**|Mappa hash del piano di query. Ammette valori Null.|
|query_plan|**xml**|Showplan XML con parziale delle statistiche. Ammette valori Null.|

## <a name="remarks"></a>Note
Questa funzione di sistema è disponibile a partire [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1.

Questa funzione di sistema funziona in entrambe **standard** e **leggero** infrastruttura di analisi delle statistiche di esecuzione di query.  
  
**Standard** profilatura infrastruttura delle statistiche possono essere abilitate utilizzando:
  -  [SET STATISTICS XML SU](../../t-sql/statements/set-statistics-xml-transact-sql.md)
  -  [SET STATISTICS PROFILE IN](../../t-sql/statements/set-statistics-profile-transact-sql.md)
  -  il `query_post_execution_showplan` degli eventi esteso.  
  
**Lightweight** sono disponibile in infrastruttura di analisi statistiche [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e possono essere abilitati:
  -  Con trace flag a livello globale 7412.
  -  Usando il [ *query_thread_profile* ](https://support.microsoft.com/kb/3170113) degli eventi esteso.
  
> [!NOTE]
> Dopo aver abilitato dal flag di traccia 7412, verrà abilitata a qualsiasi utente dell'infrastruttura anziché standard per la profilatura, ad esempio la vista DMV di analisi le statistiche di esecuzione query profilatura lightweight [DM exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md).
> Tuttavia, la profilatura standard viene ancora usato per SET STATISTICS XML, *Includi piano effettivo* azione nel [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)], e `query_post_execution_showplan` xEvent.

> [!IMPORTANT]
> Nel benchmark TPC-C, ad esempio i test di carico di lavoro, l'abilitazione dell'infrastruttura di profilatura leggera delle statistiche aggiunge un sovraccarico di 1,5 o 2 percento. Al contrario, l'infrastruttura di profilatura delle statistiche standard è possibile aggiungere fino al 90% di sovraccarico per lo stesso scenario di carico di lavoro.

## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione `VIEW SERVER STATE` per il server.  

## <a name="examples"></a>Esempi  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. Esaminare le statistiche di piano e di esecuzione dinamico delle query per un batch in esecuzione  
 Le seguenti query di esempio **exec_requests** per trovare la query specifica e copiare il `session_id` dall'output.  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 Quindi, per ottenere le statistiche di piano e l'esecuzione di query in tempo reale, usare l'insieme copiato `session_id` con funzione di sistema **DM exec_query_statistics_xml**.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 O combinato per tutte le richieste in esecuzione.  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>Vedere anche
  [Flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

