---
title: sp_helpreplicationoption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationoption
- sp_helpreplicationoption_TSQL
helpviewer_keywords:
- sp_helpreplicationoption
ms.assetid: ef988dbc-dd0b-4132-80ab-81eebec1cffe
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1003a1a33565da9b48135123d83c4ea6551debeb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771478"
---
# <a name="sp_helpreplicationoption-transact-sql"></a>sp_helpreplicationoption (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Visualizza i tipi di opzioni di replica attivate per un server. Questa stored procedure viene eseguita in qualsiasi database di qualsiasi server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpreplicationoption [ [ @optname =] 'option_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @optname = ] 'option_name'`Nome dell'opzione di replica per cui eseguire una query. *option_name* è di **tipo sysname**e il valore predefinito è null.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**transazionale**|Viene restituito un set di risultati quando è attivata la replica transazionale.|  
|**merge**|Viene restituito un set di risultati quando è attivata la replica di tipo merge.|  
|NULL (predefinito)|Non viene restituito un set di risultati.|  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|Nome dell'opzione di replica. I possibili valori sono i seguenti:<br /><br /> **transazionale**<br /><br /> **merge**|  
|**valore**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**major_version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**minor_version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Revisione**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**install_failures**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpreplicationoption** viene utilizzato per ottenere informazioni sulle opzioni di replica abilitate in un determinato server. Per ottenere informazioni su un database specifico, utilizzare **sp_helpreplicationdboption**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione vengono assegnate per impostazione predefinita al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
