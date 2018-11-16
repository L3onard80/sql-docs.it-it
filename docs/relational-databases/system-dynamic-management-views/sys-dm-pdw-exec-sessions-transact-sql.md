---
title: sys.dm_pdw_exec_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: dade699d433ce2b7ab95d3f09f370adedc8bcf2e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664060"
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>sys.dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutte le sessioni attualmente o recentemente aperte nell'appliance. Elenca una riga per ogni sessione.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|Id della query corrente o dell'ultima query eseguita (se la sessione viene terminata e la query è stata in esecuzione al momento della terminazione). Chiave per questa visualizzazione.|Deve essere univoco in tutte le sessioni nel sistema.|  
|status|**nvarchar(10)**|Per le sessioni correnti, indica se la sessione è attualmente attivo o inattivo. Per le sessioni precedenti, la sessione potrebbe mostrare lo stato chiuso o terminato (se la sessione è stata chiusa forzatamente).|'ACTIVE', 'CLOSED', 'IDLE', 'TERMINATE'|  
|request_id|**nvarchar(32)**|L'id della query corrente o ultima esecuzione della query.|Deve essere univoco tra tutte le richieste nel sistema. Null se non è stato eseguito.|  
|security_id|**varbinary(85)**|ID di sicurezza dell'entità che esegue la sessione.||  
|login_name|**nvarchar(128)**|Il nome di accesso dell'entità che esegue la sessione.|Qualsiasi stringa conforme alle convenzioni di denominazione utente.|  
|login_time|**datetime**|Data e ora in cui l'utente connesso e questa sessione è stata creata.|Valido **datetime** prima dell'ora corrente.|  
|query_count|**int**|Acquisisce il numero di query/richiesteQuesta sessione è stata eseguita dopo la creazione.|Maggiore o uguale a 0.|  
|is_transactional|**bit**|Acquisisce se una sessione è attualmente in una transazione oppure No.|0 per commit automatico, 1 per transazionale.|  
|client_id|**nvarchar(255)**|Consente di acquisire informazioni sul client per la sessione.|Qualsiasi stringa valida.|  
|APP_NAME|**nvarchar(255)**|Consente di acquisire le informazioni sul nome dell'applicazione se lo si desidera impostare come parte del processo di connessione.|Qualsiasi stringa valida.|  
|sql_spid|**int**|Il numero di id dello SPID Desiderato. Uso di `session_id` questa sessione. Usare la `sql_spid` colonna da aggiungere al **sys.dm_pdw_nodes_exec_sessions**.<br /><br /> **\*\* Avviso \* \***  questa colonna contiene SPID chiuso.||  
  
 Per informazioni sul numero massimo di righe mantenuto da questa vista, vedere la sezione i valori massimi vista di sistema nel [valori minimi e massimi (SQL Server PDW)](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9) argomento.  
  
## <a name="permissions"></a>Permissions  
 È necessaria l'autorizzazione `VIEW SERVER STATE`.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
