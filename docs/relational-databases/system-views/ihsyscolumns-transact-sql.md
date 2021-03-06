---
title: IHsyscolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: a432685809676f997049940ea5aa1ce43dc38a60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029631"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La vista **IHsyscolumns** espone le informazioni sulle colonne per gli articoli pubblicati da un server di pubblicazione non SQL Server. Questa vista è archiviata in DistributionDatabase.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**nome**|**sysname**|Nome della colonna o del parametro della procedura.|  
|**ID**|**int**|ID di oggetto della tabella a cui appartiene la colonna o ID della stored procedure a cui è associato il parametro.|  
|**xtype**|**tinyint**|Tipo di archiviazione fisica da [sys. systypes &#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|ID del tipo di dati esteso definito dall'utente.|  
|**lunghezza**|**bigint**|Lunghezza massima di archiviazione fisica da [sys. systypes &#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**int**|ID di colonna o di parametro.|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**riservati**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|ID del valore predefinito della colonna.|  
|**dominio**|**int**|ID della regola o vincolo CHECK per la colonna.|  
|**number**|**int**|Numero della sottoprocedura quando la procedura è raggruppata (**0** per le voci non di procedura).|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|Offset nella riga in cui appare la colonna.|  
|**CollationID**|**int**|ID delle regole di confronto della colonna. NULL per colonne non di tipo carattere.|  
|**linguaggio**|**int**|Identificatore di lingua per la colonna.|  
|**stato**|**int**|Mappa di bit utilizzata per descrivere una proprietà della colonna o del parametro:<br /><br /> **0x08** = la colonna consente valori null.<br /><br /> **0x10** = il riempimento ANSI era attivo quando sono state aggiunte colonne **varchar** o **varbinary** . Gli spazi vuoti finali vengono conservati per **varchar** e gli zeri finali vengono conservati per le colonne **varbinary** .<br /><br /> **0x40** = il parametro è un parametro di output.<br /><br /> **0x80** = la colonna è una colonna Identity.|  
|**tipo**|**int**|Tipo di archiviazione fisica da [sys. systypes &#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**Tipo di utente**|**tinyint**|ID del tipo di dati definito dall'utente da [sys. systypes &#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**int**|Livello di precisione della colonna|  
|**scala**|**int**|Scala della colonna.|  
|**IsComputed**|**int**|Flag che indica se si tratta di una colonna calcolata:<br /><br /> **0** = non calcolata.<br /><br /> **1** = calcolato.|  
|**isoutparam**|**int**|Indica se il parametro della procedura è un parametro di output:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**IsNullable**|**int**|Indica se la colonna ammette valori Null:<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**confronto**|**int**|Nome delle regole di confronto della colonna. NULL per colonne non di tipo carattere.|  
|**tdscollation**|**int**|Nome delle regole di confronto della colonna quando restituite in un flusso di dati tabulare (TDS, Tabular Data Stream).|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste di replica &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
