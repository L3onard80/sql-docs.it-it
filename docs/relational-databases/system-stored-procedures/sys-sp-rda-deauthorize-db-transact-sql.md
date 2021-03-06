---
title: sys. sp_rda_deauthorize_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_deauthorize_db
- sys.sp_rda_deauthorize_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_deauthorize_db stored procedure
ms.assetid: 2e362e15-2cd5-4856-9f0b-54df56b0866b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6aeb27d4fb452a4ed5b7f45086f601eacb4f0339
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905116"
---
# <a name="syssp_rda_deauthorize_db-transact-sql"></a>sys. sp_rda_deauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Rimuove la connessione autenticata tra un database locale abilitato per l'estensione e il database di Azure remoto. Eseguire **sp_rda_deauthorize_db** quando il database remoto non è raggiungibile o è in uno stato incoerente e si desidera modificare il comportamento della query per tutte le tabelle abilitate per l'estensione nel database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_rda_deauthorize_db   
```  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
  
## <a name="remarks"></a>Osservazioni  
 Dopo l'esecuzione di **sp_rda_deauthorize_db** , tutte le query sulle tabelle e i database abilitati per l'estensione hanno esito negativo. Ovvero la modalità query è impostata su DISABLEd. Per uscire da questa modalità, eseguire una delle operazioni seguenti.  
  
-   Eseguire [sys. sp_rda_reauthorize_db &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) per riconnettersi al database di Azure remoto. Questa operazione Reimposta automaticamente la modalità di query su LOCAL_AND_REMOTE, che rappresenta il comportamento predefinito per Stretch Database. Ovvero le query restituiscono i risultati dai dati locali e remoti.  
  
-   Eseguire [sys. sp_rda_set_query_mode &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) con l'argomento LOCAL_ONLY per consentire l'esecuzione delle query solo sui dati locali.  
  
## <a name="see-also"></a>Vedere anche  
 [sys. sp_rda_set_query_mode &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)   
 [sys. sp_rda_reauthorize_db &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
