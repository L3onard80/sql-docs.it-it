---
title: sp_helpextendedproc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpextendedproc
- sp_helpextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpextendedproc
ms.assetid: 7e1f017e-c898-4225-b375-6a73ef9aac7b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3dcbe6d187b56b0b15ae829eeecf1811b02dfee7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67943501"
---
# <a name="sp_helpextendedproc-transact-sql"></a>sp_helpextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza le stored procedure estese definite e il nome della libreria a collegamento dinamico (DLL) a cui appartiene la procedura (funzione).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Usare invece l' [integrazione con CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpextendedproc [ [@funcname = ] 'procedure' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @funcname = ] 'procedure'`Nome del stored procedure esteso per il quale vengono restituite informazioni. la *routine* è di **tipo sysname**e il valore predefinito è null.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**nome**|**sysname**|Nome della stored procedure estesa.|  
|**Libreria dll**|**nvarchar(255)**|Nome della DLL.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene specificata la *procedura* , **sp_helpextendedproc** segnala la stored procedure estesa specificata. Quando questo parametro non viene specificato, **sp_helpextendedproc** restituisce tutti i nomi di stored procedure estesi e i nomi delle dll a cui appartiene ogni stored procedure estesa.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'autorizzazione per l'esecuzione di **sp_helpextendedproc** viene concessa a **public**.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-reporting-help-on-all-extended-stored-procedures"></a>R. Restituzione di informazioni su tutte le stored procedure estese  
 Nell'esempio seguente vengono restituite informazioni su tutte le stored procedure estese.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc;  
GO  
```  
  
### <a name="b-reporting-help-on-a-single-extended-stored-procedure"></a>B. Restituzione di informazioni su una sola stored procedure estesa  
 Nell'esempio seguente viene riportato un `xp_cmdshell` report sulla stored procedure estesa.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc xp_cmdshell;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addextendedproc &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
