---
title: MSmerge_identity_range_allocations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
author: stevestein
ms.author: sstein
ms.openlocfilehash: de0325925bb1ad1626987361435056ff21a26be6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68072651"
---
# <a name="msmerge_identity_range_allocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La tabella **MSmerge_identity_range_allocations** viene utilizzata per tenere traccia della cronologia delle assegnazioni degli intervalli di valori Identity, per gli autori e i sottoscrittori, per gli articoli pubblicati. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|ID del server di pubblicazione.|  
|**publisher_db**|**nvarchar(128)**|Nome del database di pubblicazione.|  
|**pubblicazione**|**nvarchar(128)**|Nome della pubblicazione.|  
|**articolo**|**nvarchar(128)**|Nome dell'articolo.|  
|**subscriber**|**nvarchar(128)**|Nome del Sottoscrittore.|  
|**subscriber_db**|**nvarchar(128)**|Nome del database di sottoscrizione.|  
|**is_pub_range**|**bit**|Indica se l'intervallo di valori Identity è assegnato a un server di pubblicazione.|  
|**ranges_allocated**|**tinyint**|Numero di intervalli di valori Identity assegnati.|  
|**range_begin**|**numerico (38)**|Valore iniziale dell'intervallo.|  
|**range_end**|**numerico (38)**|Valore finale dell'intervallo.|  
|**next_range_begin**|**numerico (38)**|Valore iniziale dell'intervallo successivo da assegnare.|  
|**next_range_end**|**numerico (38)**|Valore finale dell'intervallo successivo da assegnare.|  
|**max_used**|**numerico (38)**|Valore Identity più alto utilizzato.|  
|**time_of_allocation**|**datetime**|Ora in cui è stata eseguita l'assegnazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
