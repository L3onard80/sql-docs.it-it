---
title: syssubscriptions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions system table
ms.assetid: 106c1707-e0e0-49b4-ba50-25380c40fab2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 251dbb143c1b5aa150cc094ce67943dd0139ee6d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72305020"
---
# <a name="syssubscriptions-transact-sql"></a>syssubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni sottoscrizione nel database. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|ID univoco di un articolo.|  
|**srvid**|**smallint**|ID del Sottoscrittore.|  
|**dest_db**|**sysname**|Nome del database di destinazione.|  
|**stato**|**tinyint**|Stato della sottoscrizione:<br /><br /> **0** = inattivo.<br /><br /> **1** = sottoscritto.<br /><br /> **2** = attivo.|  
|**sync_type**|**tinyint**|Tipo di sincronizzazione iniziale:<br /><br /> **1** = automatico.<br /><br /> **2** = nessuna|  
|**login_name**|**sysname**|Nome dell'account di accesso utilizzato quando si aggiunge la sottoscrizione.|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> 0 = Push: l'agente di distribuzione viene eseguito nel server di distribuzione.<br /><br /> 1 = Pull: l'agente di distribuzione viene eseguito nel Sottoscrittore.|  
|**distribution_jobid**|**binario (16)**|ID del processo dell'agente di distribuzione.|  
|**timestamp**|**timestamp**|Il timestamp.|  
|**update_mode**|**tinyint**|Modalità di aggiornamento:<br /><br /> **0** = sola lettura.<br /><br /> **1** = aggiornamento immediato.|  
|**loopback_detection**|**bit**|Si applica alle sottoscrizioni che fanno parte di una topologia di replica transazionale bidirezionale. Il rilevamento di loopback determina se l'agente di distribuzione deve inviare nuovamente al Sottoscrittore le transazioni provenienti dal Sottoscrittore:<br /><br /> **0** = restituisce.<br /><br /> **1** = non viene restituito.|  
|**queued_reinit**|**bit**|Specifica se l'articolo è contrassegnato per l'inizializzazione o la reinizializzazione. Il valore **1** indica che l'articolo sottoscritto è contrassegnato per l'inizializzazione o la reinizializzazione.|  
|**nosync_type**|**tinyint**|Tipo di inizializzazione della sottoscrizione:<br /><br /> **0** = automatico (snapshot)<br /><br /> **1** = solo supporto replica<br /><br /> **2** = inizializzazione con backup<br /><br /> **3** = inizializzazione dal numero di sequenza del file di log (LSN)<br /><br /> Per ulteriori informazioni, vedere il ** \@parametro sync_type** di [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).|  
|**srvname**|**sysname**|Nome del Sottoscrittore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
