---
title: sys. dm_pdw_os_performance_counters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8f275d48131ef7011307f39f38d37a8bfff4ea18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899320"
---
# <a name="sysdm_pdw_os_performance_counters-transact-sql"></a>sys. dm_pdw_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene informazioni sui contatori delle prestazioni di Windows per i [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]nodi in.  
  
|Nome colonna|Tipo di dati|Descrizione|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ID del nodo che contiene il contatore.<br /><br /> pdw_node_id e counter_name formano la chiave per questa visualizzazione.|Vedere node_id in [sys. dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|counter_name|**nvarchar(255)**|Nome del contatore delle prestazioni di Windows.||  
|counter_category|**nvarchar(255)**|Nome della categoria del contatore delle prestazioni di Windows.||  
|nome_istanza|**nvarchar(255)**|Nome dell'istanza specifica del contatore.||  
|counter_value|**Decimali (38, 10)**|Valore corrente del contatore.||  
|last_update_time|**Datetime2 (3)**|Timestamp dell'ultima volta in cui il valore è stato aggiornato.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel data warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
