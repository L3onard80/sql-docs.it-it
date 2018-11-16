---
title: sys.dm_qn_subscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_qn_subscriptions
- dm_qn_subscriptions_TSQL
- sys.dm_qn_subscriptions
- sys.dm_qn_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_qn_subscriptions dynamic management view
ms.assetid: a3040ce6-f5af-48fc-8835-c418912f830c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0157288c21e7b4f9b5d0b06bbf698369a216bf07
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657250"
---
# <a name="query-notifications---sysdmqnsubscriptions"></a>Eseguire una query notifiche - DM qn_subscriptions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle sottoscrizioni di notifica delle query attive nel server. È possibile utilizzare questa vista per individuare le sottoscrizioni attive nel server o in un database specificato oppure per individuare un'entità server specificata.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID di una sottoscrizione.|  
|**database_id**|**int**|ID del database in cui la query di notifica viene eseguita. In questo database vengono archiviate le informazioni relative alla sottoscrizione.|  
|**sid**|**varbinary(85)**|ID di sicurezza (SID) dell'entità server che ha creato la sottoscrizione e di cui è proprietaria.|  
|**object_id**|**int**|ID della tabella interna in cui sono archiviate le informazioni sui parametri di sottoscrizione.|  
|**created**|**datetime**|Data e ora di creazione della sottoscrizione.|  
|**timeout**|**int**|Timeout in secondi per la sottoscrizione. La notifica verrà contrassegnata per l'esecuzione non appena è trascorso l'intervallo di tempo specificato.<br /><br /> Nota: Il tempo di esecuzione effettiva potrebbe essere maggiore del timeout specificato. Se, tuttavia, si verifica una modifica che invalida la sottoscrizione dopo il timeout specificato ma prima dell'esecuzione della sottoscrizione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fa sì che l'esecuzione si verifichi in corrispondenza dell'ora in cui viene apportata la modifica.|  
|**status**|**int**|Indica lo stato della sottoscrizione. Per un elenco dei codici, vedere la tabella in Note.|  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|On|Tipo|  
|----------|--------|--------|----------|  
|**sys.dm_qn_subscriptions**|**sys.databases**|**database_id**|Molti-a-uno|  
|**sys.dm_qn_subscriptions**|**sys.internal_tables**|**object_id**|Molti-a-uno|  
  
## <a name="remarks"></a>Note  
 Il codice di stato 0 indica uno stato non definito.  
  
 I codici di stato seguenti indicano che è stata attivata una sottoscrizione a causa di una modifica:  
  
|codice|Stato minore|Info|  
|----------|------------------|----------|  
|65798|La sottoscrizione è stata attivata perché i dati sono stati modificati|sottoscrizione attivata dall'inserimento|  
|65799|La sottoscrizione è stata attivata perché i dati sono stati modificati|DELETE|  
|65800|La sottoscrizione è stata attivata perché i dati sono stati modificati|Update|  
|65801|La sottoscrizione è stata attivata perché i dati sono stati modificati|Merge|  
|65802|La sottoscrizione è stata attivata perché i dati sono stati modificati|troncamento di tabella|  
|66048|La sottoscrizione è stata attivata perché il timeout è scaduto|modalità informazioni non definita|  
|66315|La sottoscrizione è stata attivata perché un oggetto è stato modificato|oggetto o utente eliminato|  
|66316|La sottoscrizione è stata attivata perché un oggetto è stato modificato|oggetto modificato|  
|66565|La sottoscrizione è stata attivata perché il database è stato scollegato o eliminato|server o db riavviato|  
|66571|La sottoscrizione è stata attivata perché il database è stato scollegato o eliminato|oggetto o utente eliminato|  
|66572|La sottoscrizione è stata attivata perché il database è stato scollegato o eliminato|oggetto modificato|  
|67341|la sottoscrizione è stata attivata a causa di mancanza di risorse sul server|la sottoscrizione è stata attivata a causa di mancanza di risorse sul server|  
  
 I codici di stato seguenti indicano che non è stato possibile creare una sottoscrizione:  
  
|codice|Stato minore|Info|  
|----------|------------------|----------|  
|132609|La creazione della sottoscrizione non è riuscita perché l'istruzione non è supportata|query troppo complessa|  
|132610|La creazione della sottoscrizione non è riuscita perché l'istruzione non è supportata|istruzione non valida per la sottoscrizione|  
|132611|La creazione della sottoscrizione non è riuscita perché l'istruzione non è supportata|opzioni impostate non valide per la sottoscrizione|  
|132612|La creazione della sottoscrizione non è riuscita perché l'istruzione non è supportata|livello di isolamento non valido|  
|132622|La creazione della sottoscrizione non è riuscita perché l'istruzione non è supportata|utilizzato internamente|  
|132623|La creazione della sottoscrizione non è riuscita perché l'istruzione non è supportata|superato il limite di modelli per tabella|  
  
 I codici di stato seguenti vengono utilizzati internamente e vengono classificati come modalità di controllo di termine e inizializzazione:  
  
|codice|Stato minore|Info|  
|----------|------------------|----------|  
|198656|Utilizzato internamente: modalità di controllo di termine e inizializzazione|modalità informazioni non definita|  
|198928|La sottoscrizione è stata eliminata|la sottoscrizione è stata attivata perché è stato collegato il database|  
|198929|La sottoscrizione è stata eliminata|la sottoscrizione è stata attivata perché l'utente è stato eliminato|  
|198930|La sottoscrizione è stata eliminata|la sottoscrizione è stata eliminata a causa di una nuova sottoscrizione|  
|198931|La sottoscrizione è stata eliminata|la sottoscrizione è stata terminata|  
|199168|La sottoscrizione è attiva|modalità informazioni non definita|  
|199424|La sottoscrizione è stata inizializzata ma non è ancora attiva|modalità informazioni non definita|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE nel server.  
  
> [!NOTE]  
>  Se l'utente non dispone dell'autorizzazione VIEW SERVER STATE, questa vista restituisce informazioni sulle sottoscrizioni di proprietà dell'utente corrente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-return-active-query-notification-subscriptions-for-the-current-user"></a>A. Restituzione delle sottoscrizioni di notifica delle query attive per l'utente corrente  
 Nell'esempio seguente vengono restituite le sottoscrizioni di notifica delle query attive per l'utente corrente. Se l'utente dispone delle autorizzazioni VIEW SERVER STATE, vengono restituite tutte le sottoscrizioni attive nel server.  
  
```  
SELECT id, database_id, sid, object_id, created, timeout, status  
FROM sys.dm_qn_subscriptions;  
GO  
```  
  
### <a name="b-returning-active-query-notification-subscriptions-for-a-specified-user"></a>B. Restituzione delle sottoscrizioni di notifica delle query attive per un utente specificato  
 Nell'esempio seguente vengono restituite le sottoscrizioni di notifica delle query attive per l'account di accesso `Ruth0`.  
  
```  
SELECT id, database_id, sid, object_id, created, timeout, status  
FROM sys.dm_qn_subscriptions  
WHERE sid = SUSER_SID('Ruth0');  
GO  
```  
  
### <a name="c-returning-internal-table-metadata-for-query-notification-subscriptions"></a>C. Restituzione dei metadati delle tabelle interne per le sottoscrizioni di notifica delle query  
 Nell'esempio seguente vengono restituiti i metadati delle tabelle interne per le sottoscrizioni di notifica delle query.  
  
```  
SELECT qn.id AS query_subscription_id  
    ,it.name AS internal_table_name  
    ,it.object_id AS internal_table_id  
FROM sys.internal_tables AS it  
JOIN sys.dm_qn_subscriptions AS qn ON it.object_id = qn.object_id  
WHERE it.internal_type_desc = 'QUERY_NOTIFICATION';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative alle notifiche delle query &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/92eb22d8-33f3-4c17-b32e-e23acdfbd8f4)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)  
  
  
