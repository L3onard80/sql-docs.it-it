---
title: sp_invalidate_textptr (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_invalidate_textptr_TSQL
- sp_invalidate_textptr
dev_langs:
- TSQL
helpviewer_keywords:
- sp_invalidate_textptr
ms.assetid: dd9920e1-7064-4c05-93d8-9303103fa1d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81df88f6e451d71dc5778e49162db97def7ed27d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68113190"
---
# <a name="sp_invalidate_textptr-transact-sql"></a>sp_invalidate_textptr (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene invalidato il puntatore di testo all'interno di righe specificato oppure tutti i puntatori di testo all'interno di righe nella transazione. **sp_invalidate_textptr** può essere utilizzato solo in puntatori di testo all'interno di righe. Questi puntatori si trovano nelle tabelle in cui è abilitata l'opzione **text in row** .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_invalidate_textptr [ [ @TextPtrValue = ] textptr_value ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @TextPtrValue = ] textptr_value`Puntatore di testo all'interno di righe che deve essere invalidato. *textptr_value* è di tipo **varbinary (** 16 **)** e il valore predefinito è null. Se è NULL, **sp_invalidate_textptr** invalida tutti i puntatori di testo all'interno di righe nella transazione.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="remarks"></a>Osservazioni  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta un massimo di 1.024 puntatori di testo all'interno di righe validi attivi per ogni transazione di un database. In una transazione che si estende su più database, tuttavia, possono essere inclusi 1.024 puntatori di testo all'interno di righe in ogni database. **sp_invalidate_textptr** possibile utilizzare per invalidare i puntatori di testo all'interno di righe e, pertanto, spazio libero per ulteriori puntatori di testo all'interno di righe.  
  
 Per altre informazioni sull'opzione text in row, vedere [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di motore di database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_tableoption &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)   
 [TEXTPTR &#40;&#41;Transact-SQL](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)   
 [TEXTVALID &#40;&#41;Transact-SQL](../../t-sql/functions/text-and-image-functions-textvalid-transact-sql.md)  
  
  
