---
title: sp_deletetracertokenhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
author: stevestein
ms.author: sstein
ms.openlocfilehash: cf591964e5dfef0536c79b0b35e5918d4f46d972
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771136"
---
# <a name="sp_deletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Rimuove i record dei token di traccia dalla [MStracer_tokens &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) e MStracer_history &#40;le tabelle di sistema [transact-SQL&#41;](../../relational-databases/system-tables/mstracer-history-transact-sql.md) . Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di distribuzione del server di distribuzione.

![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Sintassi

```
sp_deletetracertokenhistory [ @publication = ] 'publication'
    [ , [ @tracer_id = ] tracer_id ]
    [ , [ @cutoff_date = ] cutoff_date ]
    [ , [ @publisher = ] 'publisher' ]
    [ , [ @publisher_db = ] 'publisher_db' ]
```

## <a name="arguments"></a>Argomenti

`@publication= 'publication'`  
Nome della pubblicazione in cui è stato inserito il token di traccia. Il tipo di dati è **sysname**. Questo parametro è obbligatorio.

`[ @tracer_id= ] tracer_id`  
ID del token di traccia da eliminare. Il tipo di dati è **int**. Il valore predefinito è *null*. Se *null*, vengono eliminati tutti i token di traccia appartenenti alla pubblicazione.

`[ @cutoff_date= ] cutoff_date`  
Token di traccia inseriti nella pubblicazione prima dell'eliminazione di questa data. Il tipo di dati è **DateTime**. Il valore predefinito è *null*.

`[ @publisher= ] 'publisher'`  
Nome del server di pubblicazione. Il tipo di dati è **sysname**. Il valore predefinito è *null*.

> [!NOTE]
> Questo parametro deve essere specificato solo per i server [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di pubblicazione non o quando viene eseguito il stored procedure dal database di distribuzione.

`[ @publisher_db= ] 'publisher_db'`  
Nome del database di pubblicazione. Il tipo di dati è **sysname**. Il valore predefinito è NULL. Questo parametro viene ignorato se la stored procedure viene eseguita nel server di pubblicazione.

> [!NOTE]
> Questo parametro deve essere specificato quando si esegue il stored procedure dal database di distribuzione.

## <a name="return-code-values"></a>Valori del codice restituito

**0** (esito positivo) o **1** (esito negativo)

## <a name="remarks"></a>Osservazioni

**sp_deletetracertokenhistory** viene utilizzata nella replica transazionale.  

Si verifica un errore se si specificano entrambi i parametri *tracer_id* e *cutoff_date*.

Se non si esegue **sp_deletetracertokenhistory** per eliminare i metadati del token di traccia, le informazioni verranno eliminate quando si verifica la pulizia periodica della cronologia pianificata.

È possibile determinare gli ID del token di traccia eseguendo [sp_helptracertokens &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) o eseguendo una query sulla tabella di sistema [MStracer_tokens &#40;transact-SQL&#41;](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) .

## <a name="permissions"></a>Autorizzazioni

Solo il personale seguente ha l'autorità per eseguire **sp_deletetracertokenhistory**:

- Membri dei ruoli **replmonitor** nel database di distribuzione
- Membri del ruolo predefinito del server **sysadmin** .
- Membri del ruolo predefinito del database **db_owner** nel database di pubblicazione.
- **Db_owner** del database predefinito.

## <a name="see-also"></a>Vedere anche

[Misurare la latenza e convalidare le connessioni per la replica transazionale](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

[sp_helptracertokenhistory &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)
