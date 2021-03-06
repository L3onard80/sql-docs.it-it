---
title: Viste del catalogo FILESTREAM e FileTable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- FileTables [SQL Server], catalog views
ms.assetid: 2c83a4a7-720b-4435-a3b5-788c29f56949
author: stevestein
ms.author: sstein
ms.openlocfilehash: 04fc26296d7c499982c75296089decfb57bd9ab4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016602"
---
# <a name="filestream-and-filetable-catalog-views-transact-sql"></a>Viste del catalogo Filestream e FileTable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritte le viste del catalogo correlate alla caratteristica FileTable.  
  
## <a name="filestream-and-filetable-catalog-views-transact-sql"></a>Viste del catalogo FILESTREAM e FileTable (Transact-SQL)
 [sys.database_filestream_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)  
 Consente di visualizzare informazioni sul livello di accesso non transazionale a dati FILESTREAM in tabelle FileTable abilitato. Contiene una riga per ogni database nell'istanza di SQL Server.  
  
 [sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)  
 Contiene un elenco degli oggetti definiti dal sistema correlati a tabelle FileTable. Contiene una riga per ogni oggetto definito dal sistema.  
  
 [sys.filetables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)  
 Restituisce una riga per ogni tabella FileTable. Eredita da **sys. Tables**.  

## <a name="see-also"></a>Vedere anche
[Filestream](../../relational-databases/blob/filestream-sql-server.md)
<br>[Tabelle FileTable](../../relational-databases/blob/filetables-sql-server.md)
<br>[DMV per FILESTREAM e tabelle FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
<br>[Stored procedure di sistema per Filestream e tabelle FileTable (Transact-SQL)](../system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)
  
  
