---
title: SQL Server, Database Replica | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SQLServer:Database Replica
- performance counters [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], performance counters
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3bcb9137498f43dd746b80ce8ba23ce1c4207fa6
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033148"
---
# <a name="sql-server-database-replica"></a>SQL Server, replica di database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'oggetto prestazioni **SQLServer:Database Replica** contiene contatori delle prestazioni che forniscono informazioni sui database secondari di un gruppo di disponibilità Always On in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Questo oggetto è valido solo su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita una replica secondaria.  
  
|Nome contatore|Descrizione|Contenuto in...|  
|------------------|-----------------|--------------|  
|**Byte file ricevuti/sec**|Quantità di dati FILESTREAM ricevuti dalla replica secondaria per il database secondario nell'ultimo secondo.|Replica secondaria|  
|**Coda log in attesa di applicazione**|Numero di blocchi di log in attesa di essere applicati alla replica del database.|Replica secondaria|
|**Coda log pronti per l'applicazione**|Numero di blocchi di log in attesa e pronti per essere applicati alla replica del database.|Replica secondaria| 
|**Byte log ricevuti/sec**|Quantità di record del log ricevuti dalla replica secondaria per il database nell'ultimo secondo.|Replica secondaria|  
|**Log rimanente per il rollback**|La quantità di log in KB che deve ancora completare la fase di rollback.|Replica secondaria|  
|**Coda invii log**|Quantità di record di log nei file di log del database primario che non sono stati inviati alla replica secondaria (in KB). Questo valore viene inviato alla replica secondaria dalla replica primaria. Le dimensioni della coda non includono file FILESTREAM inviati a un database secondario.|Replica secondaria|  
|**Transazioni di scrittura con mirroring/sec**|Numero di transazioni che sono state scritte nel database primario e il cui commit viene eseguito solo quando il log è stato inviato al database secondario nell'ultimo secondo.|Replica primaria|  
|**Coda di recupero**|Quantità di record del log nei file di log della replica secondaria che non sono ancora stati sottoposti a rollforward.|Replica secondaria|  
|**Blocchi rollforward/sec**|Numero di volte in cui il thread fase di rollforward viene bloccato nei blocchi utilizzati dai lettori del database.|Replica secondaria|  
|**Byte rollforward rimanenti**|Quantità di log in KB che deve essere ripetuta per completare la fase di ripristino.|Replica secondaria|  
|**Byte di cui è stato eseguito il rollforward/sec**|Quantità di record del log sottoposti a rollforward nel database secondario nell'ultimo secondo.|Replica secondaria|  
|**Totale log per cui è necessario il rollback**|Kilobyte di log totali che devono essere annullati.|Replica secondaria|  
|**Ritardo transazioni**|Periodo di attesa in millisecondi dell'acknowledgement per un commit senza terminazione.|Replica primaria|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, replica di disponibilità](../../relational-databases/performance-monitor/sql-server-availability-replica.md)   
 [SQL Server, oggetto di database](../../relational-databases/performance-monitor/sql-server-databases-object.md)   
 [Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
