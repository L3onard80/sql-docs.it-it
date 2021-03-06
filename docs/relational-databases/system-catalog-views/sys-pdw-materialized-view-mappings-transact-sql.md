---
title: sys. pdw_materialized_view_mappings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: d548291653b589d973c9c21813690a61a0fdb7ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729822"
---
# <a name="syspdw_materialized_view_mappings-transact-sql"></a>sys. pdw_materialized_view_mappings (Transact-SQL)  

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Associa la vista materializzata ai nomi di oggetto interni per object_id.

Le colonne physical_name e object_id formano la chiave per questa vista del catalogo.
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|physical_name |**nvarchar (36)**|Nome fisico per la vista materializzata.|  
|object_id  |**int**|ID oggetto per la vista materializzata. Vedere [sys. Objects (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql?view=azure-sqldw-latest).| 

## <a name="permissions"></a>Autorizzazioni

È richiesta l'autorizzazione VIEW DATABASE STATE.
  
## <a name="see-also"></a>Vedere anche

[Ottimizzazione delle prestazioni con vista materializzata](/azure/sql-data-warehouse/performance-tuning-materialized-views)   
[Crea vista MATERIALIZZAta come SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[MODIFICARE la vista MATERIALIZZAta &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[SPIEGA &#40;&#41;Transact-SQL](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys. pdw_materialized_view_column_distribution_properties &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys. pdw_materialized_view_distribution_properties &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;&#41;Transact-SQL](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse e Parallel data warehouse viste del catalogo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Visualizzazioni di sistema supportate in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Istruzioni T-SQL supportate in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements) 
