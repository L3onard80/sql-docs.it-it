---
title: sys.dm_repl_traninfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_repl_traninfo
- dm_repl_traninfo
- sys.dm_repl_traninfo_TSQL
- dm_repl_traninfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_repl_traninfo dynamic management view
ms.assetid: 5abe2605-0506-46ec-82b5-6ec08428ba13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9aa68c8c0dbc702b7f0db3e3186c7ddb56266dbc
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664967"
---
# <a name="sysdmrepltraninfo-transact-sql"></a>sys.dm_repl_traninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su ogni transazione replicata o di acquisizione dati delle modifiche.  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**fp2p_pub_exists**|**tinyint**|Indica se la transazione si trova in un database pubblicato tramite la replica transazionale peer-to-peer. Se è true, il valore è 1; altrimenti è 0.|  
|**db_ver**|**int**|Versione del database.|  
|**comp_range_address**|**varbinary(8)**|Definisce un intervallo di rollback parziale che deve essere ignorato.|  
|**textinfo_address**|**varbinary(8)**|Indirizzo in memoria della struttura di informazioni in formato testo nella cache.|  
|**fsinfo_address**|**varbinary(8)**|Indirizzo in memoria della struttura di informazioni in formato filestream nella cache.|  
|**begin_lsn**|**nvarchar(64)**|Numero di sequenza del file di log (LSN) corrispondente al record di log iniziale per la transazione.|  
|**commit_lsn**|**nvarchar(64)**|LSN del record di log del commit per la transazione.|  
|**dbid**|**smallint**|ID del database.|  
|**rows**|**int**|ID del comando replicato nella transazione.|  
|**xdesid**|**nvarchar(64)**|ID della transazione.|  
|**artcache_table_address**|**varbinary(8)**|Indirizzo in memoria dell'ultima struttura della tabella di articoli nella cache utilizzata per la transazione.|  
|**server**|**nvarchar(514)**|Nome del server.|  
|**server_len_in_bytes**|**smallint**|Lunghezza in caratteri, espressa in byte, del nome del server.|  
|**database**|**nvarchar(514)**|Nome del database.|  
|**db_len_in_bytes**|**smallint**|Lunghezza in caratteri, espressa in byte, del nome del database.|  
|**originator**|**nvarchar(514)**|Nome del server in cui ha origine la transazione.|  
|**originator_len_in_bytes**|**smallint**|Lunghezza in caratteri, espressa in byte, del server in cui ha origine la transazione.|  
|**orig_db**|**nvarchar(514)**|Nome del database in cui ha origine la transazione.|  
|**orig_db_len_in_bytes**|**smallint**|Lunghezza in caratteri, espressa in byte, del database in cui ha origine la transazione.|  
|**cmds_in_tran**|**int**|Numero di comandi replicati nella transazione corrente. Questo numero viene utilizzato per determinare quando è necessario eseguire il commit di una transazione logica.|  
|**is_boundedupdate_singleton**|**tinyint**|Specifica se l'aggiornamento di una colonna univoca interessa solo una singola riga.|  
|**begin_update_lsn**|**nvarchar(64)**|LSN utilizzato nell'aggiornamento di una colonna univoca.|  
|**delete_lsn**|**nvarchar(64)**|LSN da eliminare come parte di un aggiornamento.|  
|**last_end_lsn**|**nvarchar(64)**|Ultimo LSN in una transazione logica.|  
|**fcomplete**|**tinyint**|Specifica se il comando è un aggiornamento parziale.|  
|**fcompensated**|**tinyint**|Specifica se la transazione è interessata da un rollback parziale.|  
|**fprocessingtext**|**tinyint**|Specifica se la transazione include una colonna di dati di tipo binario di grandi dimensioni.|  
|**max_cmds_in_tran**|**int**|Numero massimo di comandi una transazione logica, come specificato dall'agente di lettura log.|  
|**begin_time**|**datetime**|Ora di inizio della transazione.|  
|**commit_time**|**datetime**|Ora in cui è stato eseguito il commit della transazione.|  
|**session_id**|**int**|ID della sessione di analisi del log relativo all'acquisizione dei dati delle modifiche. Questa colonna è associata ai **session_id** colonna nelle [DM cdc_logscan_sessions](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md).|  
|**session_phase**|**int**|Numero che indica la fase in cui si trovava la sessione quando si è verificato l'errore. Questa colonna è associata ai **phase_number** colonna nelle [DM cdc_errors](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-errors.md).|  
|**is_known_cdc_tran**|**bit**|Indica che la transazione è controllata dall'acquisizione dei dati delle modifiche.<br /><br /> 0 = Transazione di replica della transazione.<br /><br /> 1 = Transazione di acquisizione dati delle modifiche.|  
|**error_count**|**int**|Numero di errori.|  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione VIEW DATABASE STATE per il database di pubblicazione o il database abilitato per l'acquisizione dei dati delle modifiche.  
  
## <a name="remarks"></a>Note  
 Vengono restituite informazioni solo per gli oggetti di database replicati o per le tabelle abilitate per l'acquisizione dei dati delle modifiche caricati nella cache dell'articolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative alle repliche &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)   
 [Viste a gestione dinamica correlate a Change Data Capture &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/2a771d7d-693a-4f56-9227-02cd00e0e200)  
  
  

