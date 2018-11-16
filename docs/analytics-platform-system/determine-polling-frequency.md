---
title: Determinare la frequenza di polling - sistema di piattaforma Analitica | Microsoft Docs
description: Questo articolo illustra come determinare la frequenza di polling per gli avvisi di sistema di piattaforma Analitica appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6b838766e7a6d6bfb9a68bb832cd7a8feb3c9960
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696619"
---
# <a name="determine-polling-frequency"></a>Determinare la frequenza di Polling
Questo articolo illustra come determinare la frequenza di polling per gli avvisi di sistema di piattaforma Analitica appliance.  
  
## <a name="to-determine-the-polling-frequency"></a>Per determinare la frequenza di Polling  
Poiché PDW attualmente non supporta notifiche proattive quando si verificano avvisi, la soluzione di monitoraggio deve eseguire continuamente il polling dell'appliance DLL.  Internamente, PDW esegue il polling di componenti a intervalli diversi:  
  
-   Cluster: 60 secondi  
  
-   Heartbeat-60 secondi  
  
-   Tutti gli altri componenti, ovvero cinque minuti  
  
-   Contatori delle prestazioni: tre secondi  
  
Un intervallo comune per eseguire il polling per gli avvisi, che viene usato anche da System Center, è **ogni 15 minuti**.  Ovviamente, è possibile eseguire query più o meno frequente, ma non è consigliabile eseguire il polling inferiore a ogni sei ore.  
  
Polling più frequente è accettabile, ma il polling troppo frequentemente può creare confusione il [sys.dm_pdw_nodes_exec_requests](https://msdn.microsoft.com/library/ms177648(v=sql11).aspx) DMV.  Polling troppo frequentemente può rendere difficile per gli utenti per la diagnosi delle prestazioni delle query problemi quando le distribuisce rapidamente all'esterno della visualizzazione.  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Monitoraggio dell'Appliance &#40;sistema di piattaforma Analitica&#41;](appliance-monitoring.md)  
  
