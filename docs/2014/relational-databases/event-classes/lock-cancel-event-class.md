---
title: Classe di evento Lock:Cancel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Cancel event class
ms.assetid: d9203e58-40ba-4712-a918-2c34a5d396d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 909db99964faaf2fc3aec8196db929bf61fc7c09
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63023491"
---
# <a name="lockcancel-event-class"></a>Classe di evento Lock:Cancel
  La classe di evento **Lock:Cancel** indica che l'acquisizione di un blocco su una risorsa è stata annullata, ad esempio a causa dell'annullamento di una query.  
  
## <a name="lockcancel-event-class-data-columns"></a>Colonne di dati della classe di evento Lock:Cancel  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|`nvarchar`|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|**BinaryData**|`image`|Identificatore della risorsa blocco.|2|Sì|  
|**ClientProcessID**|`int`|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se tramite il client viene indicato l'ID del processo client.|9|Sì|  
|**DatabaseID**|`int`|ID del database in cui è stato acquisito il blocco. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]consente di visualizzare il nome del database se la colonna di dati **ServerName** viene acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**DatabaseName**|`nvarchar`|Nome del database in cui è stata tentata l'acquisizione del blocco.|35|Sì|  
|**Duration**|`bigint`|Quantità di tempo (in microsecondi) dalla richiesta all'annullamento del blocco.|13|Sì|  
|**EndTime**|`datetime`|Ora di fine dell'evento.|15|Sì|  
|**EventClass**|`int`|Tipo di evento = 26.|27|No|  
|**EventSequence**|`int`|Sequenza di un determinato evento all'interno della richiesta.|51|No|  
|**GroupID**|`int`|ID del gruppo del carico di lavoro in cui viene generato l'evento di Traccia SQL.|66|Sì|  
|**Nome host**|`nvarchar`|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|**IntegerData2**|`int`|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|55|Sì|  
|**IsSystem**|`int`|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|**LoginName**|`nvarchar`|Nome dell'account di accesso dell'utente (account di accesso di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente).|11|Sì|  
|**LoginSid**|`image`|ID di sicurezza (SID) dell'utente connesso. È possibile trovare queste informazioni nella vista del catalogo **sys. server_principals** . Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**Mode**|`int`|Modalità di blocco risultante dopo l'annullamento.<br /><br /> 0=NULL - Compatibile con tutte le altre modalità di blocco (LCK_M_NL)<br /><br /> 1=Blocco di stabilità dello schema (LCK_M_SCH_S)<br /><br /> 1=Blocco di modifica dello schema (LCK_M_SCH_M)<br /><br /> 3=Blocco condiviso (LCK_M_S)<br /><br /> 4=Blocco di aggiornamento (LCK_M_U)<br /><br /> 5=Blocco esclusivo (LCK_M_X)<br /><br /> 6=Blocco condiviso preventivo (LCK_M_IS)<br /><br /> 7=Blocco di aggiornamento preventivo (LCK_M_IU)<br /><br /> 8=Blocco esclusivo preventivo (LCK_M_IX)<br /><br /> 9=Condiviso-Preventivo-Aggiornamento (LCK_M_SIU)<br /><br /> 10=Condiviso-Preventivo-Esclusivo (LCK_M_SIX)<br /><br /> 10=Aggiornamento-Preventivo-Esclusivo (LCK_M_SIX)<br /><br /> 12=Blocco aggiornamenti bulk (LCK_M_BU)<br /><br /> 13=Intervalli di chiavi-Condiviso/Condiviso (LCK_M_RS_S)<br /><br /> 14=Intervalli di chiavi-Condiviso/Aggiornamento (LCK_M_RS_U)<br /><br /> 15=Intervalli di chiavi-Inserimento-NULL (LCK_M_RI_NL)<br /><br /> 16=Intervalli di chiavi-Inserimento-Condiviso (LCK_M_RI_S)<br /><br /> 17=Intervalli di chiavi-Inserimento-Aggiornamento (LCK_M_RI_U)<br /><br /> 18=Intervalli di chiavi-Inserimento-Esclusivo (LCK_M_RI_X)<br /><br /> 19=Intervalli di chiavi-Esclusivo-Condiviso (LCK_M_RX_S)<br /><br /> 20=Intervalli di chiavi-Esclusivo-Aggiornamento (LCK_M_RX_U)<br /><br /> 21=Intervalli di chiavi-Esclusivo-Esclusivo (LCK_M_RX_X)|32|Sì|  
|**NTDomainName**|`nvarchar`|Dominio Windows di appartenenza dell'utente.|7|Sì|  
|**NTUserName**|`nvarchar`|Nome utente di Windows.|6|Sì|  
|**ObjectID**|`int`|ID dell'oggetto sul quale è stato annullato il blocco, se disponibile e applicabile.|22|Sì|  
|**ObjectID2**|`bigint`|ID dell'entità o dell'oggetto correlato, se disponibile e applicabile.|56|Sì|  
|**OwnerID**|`int`|1=TRANSACTION<br /><br /> 2=CURSOR<br /><br /> 3=SESSION<br /><br /> 4=SHARED_TRANSACTION_WORKSPACE<br /><br /> 5=EXCLUSIVE_TRANSACTION_WORKSPACE|58|Sì|  
|**RequestID**|`int`|ID della richiesta contenente l'istruzione.|49|Sì|  
|**ServerName**|`nvarchar`|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|**SessionLoginName**|`nvarchar`|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|**SPID**|`int`|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|**StartTime**|`datetime`|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**TextData**|`ntext`|Valore di testo che dipende dal tipo di blocco acquisito. Si tratta dello stesso valore della colonna **resource_description** in **sys. dm_tran_locks**.|1|Sì|  
|**ID transazione**|`bigint`|ID della transazione assegnato dal sistema.|4|Sì|  
|**Tipo**|`int`|1=NULL_RESOURCE<br /><br /> 2=DATABASE<br /><br /> 3=FILE<br /><br /> 5=OBJECT<br /><br /> 6=PAGE<br /><br /> 7=KEY<br /><br /> 8=EXTENT<br /><br /> 9=RID<br /><br /> 10=APPLICATION<br /><br /> 11=METADATA<br /><br /> 12=AUTONAMEDB<br /><br /> 13=HOBT<br /><br /> 14=ALLOCATION_UNIT|57|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
  
