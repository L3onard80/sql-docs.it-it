---
title: sp_helplanguage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d46e178fc1872a84bb573f16629803c59f2fb6c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122507"
---
# <a name="sp_helplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni su una lingua alternativa specifica o su tutte le lingue in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @language = ] 'language'`Nome della lingua alternativa per la quale visualizzare le informazioni. *Language* è di **tipo sysname**e il valore predefinito è null. Se viene specificata la *lingua* , vengono restituite informazioni sulla lingua specificata. Se la lingua non è specificata, vengono restituite informazioni su tutte le lingue nella vista di compatibilità **sys. syslanguages** .  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|Numero di identificazione della lingua.|  
|**DateFormat**|**nchar (3)**|Formato della data.|  
|**DATEFIRST**|**tinyint**|Primo giorno della settimana: 1 per lunedì, 2 per martedì e così via fino a 7 per domenica.|  
|**aggiornamento**|**int**|Versione dell'ultimo aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la lingua specificata.|  
|**nome**|**sysname**|Nome della lingua.|  
|**alias**|**sysname**|Nome alternativo per la lingua.|  
|**mesi**|**nvarchar (372)**|Nomi dei mesi.|  
|**shortmonths**|**nvarchar (132)**|Nomi brevi dei mesi.|  
|**giorni**|**nvarchar (217)**|Nomi dei giorni.|  
|**LCID**|**int**|ID delle impostazioni locali di Windows relative alla lingua.|  
|**msglangid**|**smallint**|ID del gruppo di messaggi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-information-about-a-single-language"></a>R. Restituzione di informazioni su una sola lingua  
 Nell'esempio seguente vengono visualizzate informazioni sulla lingua alternativa `French`.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. Restituzione di informazioni su tutte le lingue  
 Nell'esempio seguente vengono visualizzate informazioni su tutte le lingue alternative installate.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di motore di database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
