---
title: FILE_IDEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILE_IDEX
- FILE_IDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILE_IDEX function
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_IDEX
ms.assetid: 7532fea5-ee5e-4edd-b98b-111a7ba56c8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 59b44b3356a0f71074543eb35107040ff8c47982
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68071497"
---
# <a name="file_idex-transact-sql"></a>FILE_IDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Questa funzione restituisce il numero di identificazione (ID) del file per il nome logico specificato del file di dati, file di log o file full-text nel database corrente. 
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
FILE_IDEX ( file_name )  
```  
  
## <a name="arguments"></a>Argomenti  
 *file_name*  
Un'espressione di tipo **sysname** che restituisce il valore di ID di file 'FILE_IDEX' per il nome del file. 
  
## <a name="return-types"></a>Tipi restituiti  
**int**  
  
**NULL** in caso di errore  
  
## <a name="remarks"></a>Osservazioni  
*file_name* corrisponde al nome di file logico visualizzato nella colonna **name** dalla vista del catalogo [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md) o [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).  
  
Usare `FILE_IDEX` in un elenco SELECT, una clausola WHERE o in qualsiasi posizione che supporti l'uso di un'espressione. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-retrieving-the-file-id-of-a-specified-file"></a>R. Recupero dell'ID file di un file specificato  
L'esempio seguente restituisce l'ID per il file `AdventureWorks_Data`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX('AdventureWorks2012_Data') AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
### <a name="b-retrieving-the-file-id-when-the-file-name-is-not-known"></a>B. Recupero dell'ID file di un nome file non noto  
Questo esempio restituisce l'ID del file di log `AdventureWorks`. Il frammento di codice Transact-SQL (T-SQL) consente di selezionare il nome file logico dalla vista del catalogo `sys.database_files`, in cui il tipo di file è uguale a `1` (log).  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX((SELECT TOP (1) name FROM sys.database_files WHERE type = 1)) AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
2  
```  
  
### <a name="c-retrieving-the-file-id-of-a-full-text-catalog-file"></a>C. Recupero dell'ID file di un file del catalogo full-text  
Questo esempio restituisce l'ID di un file full-text. Il frammento di codice T-SQL consente di selezionare il nome file logico dalla vista del catalogo `sys.database_files`, in cui il tipo di file è uguale a `4` (full-text). Se non esiste un catalogo full-text, il codice restituisce 'NULL'.
  
```sql  
SELECT FILE_IDEX((SELECT name FROM sys.master_files WHERE type = 4))  
AS 'File_ID';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni per i metadati &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
