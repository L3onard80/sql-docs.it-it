---
title: sys. dm_exec_cached_plan_dependent_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plan_dependent_objects
- dm_exec_cached_plan_dependent_objects_TSQL
- sys.dm_exec_cached_plan_dependent_objects_TSQL
- dm_exec_cached_plan_dependent_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cached_plan_dependent_objects dynamic management function
ms.assetid: 9b6cf5f7-b267-44fb-aac8-f49c9aa10cc1
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ca4499645846dacc762d8d3bf130ccc44a7f3155
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097903"
---
# <a name="sysdm_exec_cached_plan_dependent_objects-transact-sql"></a>sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni piano di esecuzione [!INCLUDE[tsql](../../includes/tsql-md.md)] o CLR (Common Language Runtime) e ogni cursore associato a un piano.  
  
## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_exec_cached_plan_dependent_objects(plan_handle)  
```  
  
## <a name="arguments"></a>Argomenti  
*plan_handle*  
Token che identifica in modo univoco un piano di esecuzione della query per un batch eseguito e il cui piano risiede nella cache dei piani. *plan_handle* è di tipo **varbinary (64)**.   

Il *plan_handle* può essere ottenuto dagli oggetti a gestione dinamica seguenti:  
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys. dm_exec_procedure_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys. dm_exec_trigger_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**usecounts**|**int**|Numero di volte in cui è stato utilizzato il contesto di esecuzione o il cursore.<br /><br /> La colonna non ammette i valori Null.|  
|**memory_object_address**|**varbinary (8)**|Indirizzo di memoria del contesto di esecuzione o del cursore.<br /><br /> La colonna non ammette i valori Null.|  
|**cacheobjtype**|**nvarchar(50)**|Tipo di oggetto Plan Cache. La colonna non ammette i valori Null. Valori possibili:<br /><br /> Piano eseguibile<br /><br /> Funzione CLR compilata<br /><br /> Procedura CLR compilata<br /><br /> Cursore|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione `VIEW SERVER STATE` per il server.  
  
## <a name="physical-joins"></a>Join fisici  
 ![Diagramma delle relazioni](../../relational-databases/system-dynamic-management-views/media/dm-dependent-objects.gif "Diagramma delle relazioni")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|Da|A|Attivato|Relazione|  
|----------|--------|--------|------------------|  
|**dm_exec_cached_plan_dependent_objects**|**dm_os_memory_objects**|**memory_object_address**|Uno-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys. syscacheobjects &#40;&#41;Transact-SQL](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)  
  
  
