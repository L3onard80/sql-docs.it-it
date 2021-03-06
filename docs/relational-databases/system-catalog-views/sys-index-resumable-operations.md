---
title: sys. index_resumable_operations (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.index_resumable_operations_TSQL
- sys.indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes
- sys.index_resumable_operations
ms.assetid: ''
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d33b78710605841e4559f9c402a18210e25b2daa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73980308"
---
# <a name="sysindex_resumable_operations-transact-sql"></a>sys. index_resumable_operations (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]
**sys. index_resumable_operations** è una vista di sistema che monitora e controlla lo stato di esecuzione corrente per la ricompilazione o la creazione di indici ripristinabili.  
**Si applica a**: SQL Server (2017 e versioni successive) e al database SQL di Azure
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui appartiene l'indice (non nullable).|  
|**index_id**|**int**|ID dell'indice (non nullable). **index_id** è univoco solo all'interno dell'oggetto.|
|**nome**|**sysname**|Nome dell'indice. il **nome** è univoco solo all'interno dell'oggetto.|  
|**sql_text**|**nvarchar(max)**|Testo dell'istruzione T-SQL DDL|
|**last_max_dop**|**smallint**|Ultimo MAX_DOP usato (valore predefinito = 0)|
|**partition_number**|**int**|Numero di partizione all'interno dell'indice o dell'heap proprietario. Per le tabelle e gli indici non partizionati oppure nel caso in cui tutte le partizioni vengano ricompilate, il valore di questa colonna è NULL.|
|**state**|**tinyint**|Stato operativo per l'indice ripristinabile:<br /><br />0 = in esecuzione<br /><br />1 = sospensione|
|**state_desc**|**nvarchar (60)**|Descrizione dello stato operativo per l'indice ripristinabile (in esecuzione o in pausa)|  
|**start_time**|**datetime**|Ora di inizio dell'operazione sugli indici (non nullable)|
|**last_pause_time**|**DataTime**| Ora dell'ultima pausa dell'operazione sugli indici (Nullable). NULL se l'operazione è in esecuzione e non è mai stata sospesa.|
|**total_execution_time**|**int**|Tempo di esecuzione totale dall'ora di inizio in minuti (non nullable)|
|**percent_complete**|**reale**|Stato dell'operazione di indice completato in% (non nullable).|
|**page_count**|**bigint**|Numero totale di pagine di indice allocate dall'operazione di compilazione dell'indice per i nuovi indici di mapping e non nullable.

## <a name="permissions"></a>Autorizzazioni

[!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  

## <a name="example"></a>Esempio

 Elencare tutte le operazioni di creazione o ricompilazione di indici ripristinabili in stato di sospensione.

```sql
SELECT * FROM  sys.index_resumable_operations WHERE STATE = 1;  
```

## <a name="see-also"></a>Vedere anche

- [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)
- [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)
- [Viste del catalogo](catalog-views-transact-sql.md)
- [Viste del catalogo oggetti](object-catalog-views-transact-sql.md)
- [sys.indexes](sys-xml-indexes-transact-sql.md)
- [sys.index_columns](sys-index-columns-transact-sql.md)
- [sys.xml_indexes](sys-xml-indexes-transact-sql.md)
- [sys.objects](sys-index-columns-transact-sql.md)
- [sys.key_constraints](sys-key-constraints-transact-sql.md)
- [sys.filegroups](sys-filegroups-transact-sql.md)
- [sys.partition_schemes](sys-partition-schemes-transact-sql.md)
- [Domande frequenti sull'esecuzione di query sul catalogo di sistema di SQL Server](querying-the-sql-server-system-catalog-faq.md)
