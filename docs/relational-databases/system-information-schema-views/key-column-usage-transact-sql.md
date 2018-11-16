---
title: KEY_COLUMN_USAGE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- KEY_COLUMN_USAGE_TSQL
- KEY_COLUMN_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.KEY_COLUMN_USAGE view
- KEY_COLUMN_USAGE view
ms.assetid: ec1e18c2-63a1-4d2b-ba9a-c13857403782
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 11e1d28357b1a16b7b683bf2296e97e3a207887b
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660050"
---
# <a name="keycolumnusage-transact-sql"></a>KEY_COLUMN_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni colonna vincolata come chiave nel database corrente. Questa vista degli schemi delle informazioni restituisce informazioni sugli oggetti per i quali l'utente dispone di autorizzazioni.  
  
 Per recuperare informazioni da queste viste, specificare il nome completo di **INFORMATION_SCHEMA. * * * view_name*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Qualificatore del vincolo.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che contiene il vincolo.<br /><br /> **\*\* Importanti \* \***  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**CONSTRAINT_NAME**|**nvarchar (** 128 **)**|Nome del vincolo.|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Qualificatore della tabella.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che contiene la tabella.<br /><br /> **\*\* Importanti \* \***  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|Nome della tabella.|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|Nome colonna.|  
|**ORDINAL_POSITION**|**int**|Posizione ordinale della colonna.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste degli schemi delle informazioni &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Sys. Foreign_Keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)   
 [Sys. key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
  
