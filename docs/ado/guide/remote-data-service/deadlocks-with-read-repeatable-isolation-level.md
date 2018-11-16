---
title: Deadlock con livello di isolamento Repeatable Read | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a063bfa08ee0c405b52c123f0af03397751a2289
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558439"
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Deadlock con livello di isolamento di lettura ripetibile
Se un oggetto business personalizzato utilizza un livello di isolamento di lettura ripetibile per accedere a SQL Server e l'oggetto business è chiamato simultaneamente da due client che inviano una query e aggiornamento nella stessa transazione, è possibile un deadlock. Servizio dati remoto è progettato per consentire a uno dei processi di timeout per rilasciare il deadlock, ma l'aggiornamento avrà esito negativo per quel client.  
  
 Usare la [servizio cursore](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **Timeout comando** proprietà dinamica per modificare la durata del timeout.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



