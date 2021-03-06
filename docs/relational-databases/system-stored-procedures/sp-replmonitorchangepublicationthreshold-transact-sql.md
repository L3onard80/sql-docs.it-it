---
title: sp_replmonitorchangepublicationthreshold (T-SQL)
description: Viene descritta la sp_replmonitorchangepublicationthreshold stored procedure che modifica la metrica di soglia di monitoraggio per una pubblicazione.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords:
- sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
author: stevestein
ms.author: sstein
ms.openlocfilehash: fdcf5a9dcd462562886c7815b500c43145b749a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "75322228"
---
# <a name="sp_replmonitorchangepublicationthreshold-transact-sql"></a>sp_replmonitorchangepublicationthreshold (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Modifica la metrica del valore soglia di monitoraggio di una pubblicazione. Questa stored procedure, utilizzata per il monitoraggio della replica, viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replmonitorchangepublicationthreshold [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @metric_id = ] metric_id ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'   
    [ , [ @value = ] value ]   
    [ , [ @shouldalert = ] shouldalert ]   
    [ , [ @mode = ] mode ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publisher = ] 'publisher'`Nome del server di pubblicazione. *Publisher* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @publisher_db = ] 'publisher_db'`Nome del database pubblicato. *publisher_db* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @publication = ] 'publication'`Nome della pubblicazione per cui si desidera modificare gli attributi della soglia di monitoraggio. *Publication* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @publication_type = ] publication_type`Se il tipo di pubblicazione. *publication_type* è di **tipo int**. i possibili valori sono i seguenti.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**0**|Pubblicazione transazionale.|  
|**1**|Pubblicazione snapshot.|  
|**2**|Pubblicazione di tipo merge.|  
|NULL (predefinito)|La replica cerca di determinare il tipo di pubblicazione.|  
  
`[ @metric_id = ] metric_id`ID della metrica della soglia della pubblicazione da modificare. *metric_id* è di **tipo int**e il valore predefinito è null. i possibili valori sono i seguenti.  
  
|valore|Nome della metrica|  
|-----------|-----------------|  
|**1**|**scadenza** : monitora la scadenza imminente delle sottoscrizioni di pubblicazioni transazionali.|  
|**2**|**latenza** : esegue il monitoraggio delle prestazioni delle sottoscrizioni di pubblicazioni transazionali.|  
|**4**|**mergeexpiration** : monitora la scadenza imminente delle sottoscrizioni di pubblicazioni di tipo merge.|  
|**5**|**mergeslowrunduration** : esegue il monitoraggio della durata delle sincronizzazioni di tipo merge su connessioni remote a larghezza di banda ridotta.|  
|**6**|**mergefastrunduration** : esegue il monitoraggio della durata delle sincronizzazioni di tipo merge su connessioni LAN (Local Area Network) a larghezza di banda elevata.|  
|**7**|**mergefastrunspeed** : esegue il monitoraggio della velocità di sincronizzazione delle sincronizzazioni di tipo merge su connessioni LAN a larghezza di banda elevata.|  
|**8**|**mergeslowrunspeed** : esegue il monitoraggio della velocità di sincronizzazione delle sincronizzazioni di tipo merge su connessioni remote a larghezza di banda ridotta.|  
  
 È necessario specificare *metric_id* o *thresholdmetricname*. Se viene specificato *thresholdmetricname* , *METRIC_ID* deve essere null.  
  
`[ @thresholdmetricname = ] 'thresholdmetricname'`Nome della metrica della soglia della pubblicazione da modificare. *thresholdmetricname* è di **tipo sysname**e il valore predefinito è null. È necessario specificare *thresholdmetricname* o *metric_id*. Se *metric_id* è specificato, *THRESHOLDMETRICNAME* deve essere null.  
  
`[ @value = ] value`Nuovo valore della metrica della soglia della pubblicazione. *value* è di **tipo int**e il valore predefinito è null. Se **null**, il valore della metrica non viene aggiornato.  
  
`[ @shouldalert = ] shouldalert`Indica se viene generato un avviso quando viene raggiunta una metrica della soglia della pubblicazione. *ShouldAlert* è di **bit**e il valore predefinito è null. Il valore **1** indica che viene generato un avviso e il valore **0** indica che non viene generato un avviso.  
  
`[ @mode = ] mode`Indica se la metrica della soglia della pubblicazione è abilitata. *mode* è di tipo **tinyint**e il valore predefinito è **1**. Il valore **1** indica che il monitoraggio di questa metrica è abilitato e il valore **2** indica che il monitoraggio di questa metrica è disabilitato.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replmonitorchangepublicationthreshold** viene utilizzato con tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del database **db_owner** o **replmonitor** nel database di distribuzione possono eseguire **sp_replmonitorchangepublicationthreshold**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
