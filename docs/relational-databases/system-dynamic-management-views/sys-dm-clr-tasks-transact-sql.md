---
title: sys. dm_clr_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 00b37550b9a5d121d395f94d4810a4a093c3125d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265999"
---
# <a name="sysdm_clr_tasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per tutte le attività CLR (Common Language Runtime) in esecuzione. Un batch [!INCLUDE[tsql](../../includes/tsql-md.md)] contenente un riferimento a una routine CLR crea un'attività distinta per l'esecuzione di tutto il codice gestito nel batch. La stessa attività CLR viene utilizzata da più istruzioni nel batch che richiedono l'esecuzione del codice gestito. L'attività CLR è responsabile del mantenimento di oggetti e stato relativi all'esecuzione del codice gestito, nonché delle transizioni tra l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e CLR.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary (8)**|Indirizzo dell'attività CLR.|  
|**sos_task_address**|**varbinary (8)**|Indirizzo dell'attività batch [!INCLUDE[tsql](../../includes/tsql-md.md)] sottostante.|  
|**appdomain_address**|**varbinary (8)**|Indirizzo del dominio applicazione in cui è in esecuzione l'attività.|  
|**state**|**nvarchar(128)**|Stato corrente dell'attività.|  
|**abort_state**|**nvarchar(128)**|Stato corrente dell'interruzione se l'attività è stata annullata. Durante l'interruzione delle attività si possono verificare più stati.|  
|**tipo**|**nvarchar(128)**|Tipo di attività.|  
|**affinity_count**|**int**|Affinità dell'attività.|  
|**forced_yield_count**|**int**|Numero di volte che l'attività è obbligata a restituire il controllo.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]è richiesta `VIEW SERVER STATE` l'autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l' **amministratore del server** o un account **amministratore Azure Active Directory** .   
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative a Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

