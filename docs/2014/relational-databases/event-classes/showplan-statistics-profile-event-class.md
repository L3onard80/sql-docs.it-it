---
title: Classe di evento Showplan Statistics Profile | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan Statistics Profile event class
ms.assetid: fa9e1330-a217-491c-ad7c-2c1c4015d1bb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0dc08151d47bee9190f199e187db25a3b5dd6de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62662063"
---
# <a name="showplan-statistics-profile-event-class"></a>Showplan Statistics Profile - classe di evento
  La classe di evento Showplan Statistics Profile [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene generata quando in viene eseguita un'istruzione SQL. Le informazioni incluse sono tuttavia un sottoinsieme delle informazioni disponibili nelle classi di evento Showplan XML Statistics.  
  
 Nella classe di evento Showplan Statistics Profile vengono visualizzati i dati completi della fase di compilazione e le tracce che contengono Showplan Statistics Profile possono causare una riduzione significativa delle prestazioni. Per ridurre al minimo tale rischio, limitare l'utilizzo di questa classe di evento alle tracce che consentono di monitorare problemi specifici per brevi periodi di tempo.  
  
 Quando si include la classe di evento Showplan Statistics Profile in una traccia, è necessario selezionare la colonna di dati BinaryData. In caso contrario, le informazioni relative a questa classe di evento non verranno visualizzate nella traccia.  
  
## <a name="showplan-statistics-profile-event-class-data-columns"></a>Colonne di dati della classe di evento Showplan Statistics Profile  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|BinaryData|`image`|Costo stimato della query.|2|No|  
|ClientProcessID|`int`|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se l'ID del processo client viene fornito dal client.|9|Sì|  
|DatabaseID|`int`|ID del database specificato nell'istruzione USE *database* oppure il database predefinito se non è stata eseguita alcuna istruzione USE *database* per una determinata istanza. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]consente di visualizzare il nome del database se la colonna di dati ServerName viene acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|DatabaseName|`nvarchar`|Nome del database nel quale viene eseguita l'istruzione dell'utente.|35|Sì|  
|EventClass|`int`|Tipo di evento = 98.|27|No|  
|EventSequence|`int`|Sequenza di un determinato evento all'interno della richiesta.|51|No|  
|GroupID|`int`|ID del gruppo del carico di lavoro in cui viene generato l'evento di Traccia SQL.|66|Sì|  
|HostName|`nvarchar`|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|IntegerData|`int`|Numero stimato di righe restituite.|25|Sì|  
|IsSystem|`int`|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|LineNumber|`int`|Visualizza il numero della riga contenente l'errore.|5|Sì|  
|LoginName|`nvarchar`|Nome dell'account di accesso dell'utente (account di accesso di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente).|11|Sì|  
|LoginSID|`image`|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo sys.server_principals. Il SID è univoco per ogni account di accesso nel server.|41|No|  
|NestLevel|`int`|Valore intero che rappresenta i dati restituiti da @@NESTLEVEL.|29|Sì|  
|NTDomainName|`nvarchar`|Dominio Windows di appartenenza dell'utente.|7|Sì|  
|ObjectID|`int`|ID dell'oggetto assegnato dal sistema.|22|Sì|  
|ObjectName|`nvarchar`|Nome dell'oggetto a cui si fa riferimento.|34|Sì|  
|ObjectType|`int`|Valore che rappresenta il tipo di oggetto coinvolto nell'evento. Questo valore corrisponde alla colonna type nella tabella sys.objects. Per i valori, vedere [Colonna ObjectType per gli eventi di traccia](objecttype-trace-event-column.md).|28|Sì|  
|RequestID|`int`|ID della richiesta contenente l'istruzione.|49|Sì|  
|ServerName|`nvarchar`|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|SessionLoginName|`nvarchar`|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, SessionLoginName indica Login1 e LoginName indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|SPID|`int`|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|StartTime|`datetime`|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|TransactionID|`bigint`|ID della transazione assegnato dal sistema.|4|Sì|  
|XactSequence|`bigint`|Token usato per descrivere la transazione corrente.|50|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Guida di riferimento a operatori Showplan logici e fisici](../showplan-logical-and-physical-operators-reference.md)   
 [Classe di evento Showplan XML Statistics Profile](showplan-xml-statistics-profile-event-class.md)  
  
  
