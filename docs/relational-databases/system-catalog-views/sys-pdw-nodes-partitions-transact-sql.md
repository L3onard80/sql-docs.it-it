---
title: sys. pdw_nodes_partitions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d0fc42e1ce8d15498caf89582b66549f4e083130
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72305233"
---
# <a name="syspdw_nodes_partitions-transact-sql"></a>sys. pdw_nodes_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni partizione di tutte le tabelle e la maggior parte dei tipi di indici in un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] database. Tutte le tabelle e gli indici contengono almeno una partizione, indipendentemente dal fatto che siano partizionati in modo esplicito.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|partition_id|**bigint**|ID della partizione. Valore univoco all'interno di un database.|  
|object_id|**int**|ID dell'oggetto a cui appartiene la partizione. Ogni tabella o vista è costituita da almeno una partizione.|  
|index_id|**int**|ID dell'indice all'interno dell'oggetto a cui appartiene la partizione.|  
|partition_number|**int**|Numero di partizione in base 1 all'interno dell'indice o heap di appartenenza. Per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], il valore di questa colonna è 1.|  
|hobt_id|**bigint**|ID del heap o albero B dati (HoBT) che contiene le righe per la partizione.|  
|rows|**bigint**|Numero approssimativo di righe nella partizione. |  
|data_compression|**int**|Indica lo stato di compressione per ogni partizione:<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|**nvarchar (60)**|Indica lo stato di compressione per ogni partizione. I valori possibili sono NONE, ROW e PAGE.|  
|pdw_node_id|**int**|Identificatore univoco di un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nodo.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione `CONTROL SERVER`.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>Esempio A: visualizzare le righe in ogni partizione all'interno di ogni distribuzione 

**Si applica a:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
Per visualizzare il numero di righe in ogni partizione all'interno di ogni distribuzione, utilizzare [DBCC PDW_SHOWPARTITIONSTATS (SQL Server PDW)](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md) .

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>Esempio B: usa le viste di sistema per visualizzare le righe in ogni partizione di ogni distribuzione di una tabella

**Si applica a:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
Questa query restituisce il numero di righe in ogni partizione di ogni distribuzione della tabella `myTable`.  
 
```sql  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel data warehouse viste del catalogo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

