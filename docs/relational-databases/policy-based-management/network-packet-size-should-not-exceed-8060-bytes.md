---
title: Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b74d7122f6247d4aebfb4046cfe80cbce11897d7
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668690"
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Valore massimo per le dimensioni del pacchetto di rete impostato su 8060 byte
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Se il valore specificato per sp_configure ''network packet size' o se le dimensioni del pacchetto di rete di qualsiasi utente connesso sono maggiori di 8060 byte, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue operazioni di allocazione della memoria diverse. In questo caso, può verificarsi un aumento dello spazio degli indirizzi virtuali dei processi non riservato per il pool di buffer.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Le dimensioni del pacchetto di rete non devono superare 8060 byte.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Articolo 903002 della Microsoft Knowledge Base](https://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
