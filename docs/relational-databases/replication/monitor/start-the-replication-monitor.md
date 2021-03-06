---
title: Avviare Monitoraggio replica | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 13f31de587e0cacaea6d0b137949084165914597
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287870"
---
# <a name="start-the-replication-monitor"></a>Avvio di Monitoraggio replica
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  È possibile avviare Monitoraggio replica da [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] in qualsiasi istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]oppure dal prompt dei comandi. Dopo l'avvio di Monitoraggio replica, aggiungere uno o più server di pubblicazione da monitorare. Per altre informazioni, vedere [Aggiungere e rimuovere server di pubblicazione da Monitoraggio replica](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>Per avviare Monitoraggio replica da SQL Server Management Studio  
  
1.  Connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Replica** o una delle relative sottocartelle e quindi scegliere **Avvia Monitoraggio replica**.  

### <a name="to-start-replication-monitor-from-the-command-prompt"></a>Per avviare Monitoraggio replica dal prompt dei comandi  
  
1.  Al prompt dei comandi passare alla directory di installazione degli strumenti. Il percorso predefinito è [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\ .  
  
2.  Eseguire sqlmonitor.exe.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
