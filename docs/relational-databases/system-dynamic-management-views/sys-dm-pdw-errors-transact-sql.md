---
title: sys.dm_pdw_errors (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 944eac31-5691-432b-b9f5-f1e11c05191f
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8868a654d46842acea95d087ec54831b210ba16a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51672920"
---
# <a name="sysdmpdwerrors-transact-sql"></a>sys.dm_pdw_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti gli errori rilevati durante l'esecuzione di una richiesta o una query.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar(36)**|Chiave per questa visualizzazione.<br /><br /> Id numerico univoco associato all'errore.|Deve essere univoco tra tutti gli errori di query nel sistema.|  
|origine|**nvarchar(64)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|Tipo|**nvarchar(4000)**|Tipo di errore che si è verificato.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|create_time|**datetime**|Ora in cui si è verificato l'errore.|Minore o uguale all'ora corrente.|  
|pwd_node_id|**int**|Identificatore del nodo specifico interessato, se presente. Per altre informazioni su ID di nodo, vedere [sys.dm_pdw_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).||  
|session_id|**nvarchar(32)**|Identificatore della sessione interessata, se presente. Per altre informazioni su ID di sessione, vedere [DM pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|request_id|**nvarchar(32)**|Identificatore della richiesta interessata, se presente. Per altre informazioni sugli ID richiesta, vedere [DM pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).||  
|spid|**int**|SPID della sessione SQL Server interessato, se presente.||  
|thread_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|dettagli|**nvarchar(4000)**|Contiene la descrizione di testo di errore completo.||  
  
 Per informazioni sul numero massimo di righe mantenuto da questa vista, vedere la sezione i valori massimi vista di sistema nel [valori minimi e massimi (SQL Server PDW)](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
