---
title: DROP SENSITIVITY CLASSIFICATION (Transact-SQL) | Microsoft Docs
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- DROP SENSITIVITY CLASSIFICATION
- DROP_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SENSITIVITY CLASSIFICATION statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8926d9f39722bac3d70bc10aba6970ff32a5bb17
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703369"
---
# <a name="drop-sensitivity-classification-transact-sql"></a>DROP SENSITIVITY CLASSIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Elimina i metadati di classificazione della riservatezza da una o più colonne di database.

## <a name="syntax"></a>Sintassi

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    <object_name> [, ...n ]

<object_name> ::=
{
    [schema_name.]table_name.column_name
}
```  

## <a name="arguments"></a>Argomenti  

*object_name* ([schema_name.]table_name.column_name)

Si tratta del nome della colonna del database da cui rimuovere la classificazione. Attualmente è supportata solo la classificazione delle colonne.
    - *schema_name* (facoltativo): si tratta del nome dello schema a cui appartiene la colonna classificata.
    - *Table_name*: si tratta del nome della tabella a cui appartiene la colonna classificata.
    - *column_name*: si tratta del nome della colonna da cui eliminare la classificazione.

## <a name="remarks"></a>Remarks  

- È possibile eliminare più classificazioni di oggetti usando una sola istruzione ‘DROP SENSITIVITY CLASSIFICATION’.

## <a name="permissions"></a>Permissions  

È necessaria l'autorizzazione ALTER ANY SENSITIVITY CLASSIFICATION. L'autorizzazione ALTER ANY SENSITIVITY CLASSIFICATION è implicita nell'autorizzazione del database ALTER o nell'autorizzazione del server CONTROL SERVER.


## <a name="examples"></a>Esempi  


### <a name="a-dropping-classification-from-a-single-column"></a>A. Eliminazione della classificazione da una singola colonna

Nell'esempio seguente la classificazione viene rimossa dalla colonna `dbo.sales.price`.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price
```

### <a name="b-dropping-classification-from-multiple-columns"></a>B. Eliminazione della classificazione da più colonne

Nell'esempio seguente la classificazione viene rimossa dalle colonne `dbo.sales.price`, `dbo.sales.discount` e `SalesLT.Customer.Phone`.  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price, dbo.sales.discount, SalesLT.Customer.Phone  
```

## <a name="see-also"></a>Vedere anche  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[Introduzione a SQL Information Protection](https://aka.ms/sqlip)
