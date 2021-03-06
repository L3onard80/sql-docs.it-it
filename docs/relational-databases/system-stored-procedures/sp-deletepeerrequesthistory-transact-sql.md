---
title: sp_deletepeerrequesthistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletepeerrequesthistory
- sp_deletepeerrequesthistory_TSQL
helpviewer_keywords:
- sp_deletepeerrequesthistory
ms.assetid: 63a4ec6e-ce79-4bf1-9d37-5ac88f8d6beb
author: stevestein
ms.author: sstein
ms.openlocfilehash: e1af3aad1f66f3de7dd2fce44990718980018d3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111938"
---
# <a name="sp_deletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina la cronologia correlata a una richiesta di stato della pubblicazione, che include la cronologia delle richieste ([MSpeer_request &#40;Transact-sql&#41;](../../relational-databases/system-tables/mspeer-request-transact-sql.md)) e la cronologia delle risposte ([MSpeer_response &#40;transact-SQL&#41;](../../relational-databases/system-tables/mspeer-response-transact-sql.md)). Questa stored procedure viene eseguita nel database di pubblicazione in un server di pubblicazione che partecipa a una topologia di replica peer-to-peer. Per altre informazioni, vedere [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publication = ] 'publication'`Nome della pubblicazione per cui è stata effettuata la richiesta di stato. *Publication* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @request_id = ] request_id`Specifica una singola richiesta di stato in modo che tutte le risposte a questa richiesta verranno eliminate. *request_id* è di **tipo int**e il valore predefinito è null.  
  
`[ @cutoff_date = ] cutoff_date`Specifica una data di taglio, prima della quale vengono eliminati tutti i record di risposta precedenti. *cutoff_date* è di tipo **DateTime**e il valore predefinito è null.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_deletepeerrequesthistory** viene utilizzata in una topologia di replica transazionale peer-to-peer. Per altre informazioni, vedere [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 Quando si esegue **sp_deletepeerrequesthistory**, è necessario specificare *request_id* o *cutoff_date* .  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** o del ruolo predefinito del database **db_owner** possono eseguire **sp_deletepeerrequesthistory**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_helppeerrequests &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [sp_helppeerresponses &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [sp_requestpeerresponse &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  
