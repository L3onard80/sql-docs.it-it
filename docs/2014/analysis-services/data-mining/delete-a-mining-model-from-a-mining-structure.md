---
title: Eliminare un modello di data mining da una struttura di data mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], mining models
- deleting mining models
- removing mining models
- mining models [Analysis Services], deleting
ms.assetid: 9ab1506b-856e-4762-a663-5adf15ac71e3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d4e32a40946eb9e513ad22cd837773187843151
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084775"
---
# <a name="delete-a-mining-model-from-a-mining-structure"></a>Eliminare un modello di data mining da una struttura di data mining
  È possibile eliminare i modelli di data mining usando Progettazione modelli di data mining, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]o istruzioni DMX.  
  
### <a name="delete-a-mining-model-using-sql-server-data-tools"></a>Eliminare un modello di data mining utilizzando SQL Server Data Tools  
  
1.  Selezionare la scheda **Modelli di data mining** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sul modello da eliminare e quindi scegliere **Elimina**.  
  
     Verrà visualizzata la finestra di dialogo **Elimina oggetti** .  
  
3.  Fare clic su **OK**.  
  
### <a name="delete-a-mining-model-using-sql-server-management-studio"></a>Eliminare un modello di data mining utilizzando SQL Server Management Studio  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenente il modello.  
  
2.  Espandere **Strutture di data mining**e quindi espandere **Modelli di data mining**.  
  
3.  Fare clic con il pulsante destro del mouse sul modello che si vuole eliminare e scegliere **Elimina**.  
  
     L'eliminazione del modello non comporta l'eliminazione dei dati di training, ma solo dei metadati e degli schemi creati durante il training del modello.  
  
### <a name="delete-a-mining-model-using-dmx"></a>Eliminare un modello di data mining tramite DMX  
  
-   [ELIMINA MODELLO DI DATA MINING &#40;DMX&#41;](/sql/dmx/drop-mining-model-dmx)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative al modello di data mining](mining-model-tasks-and-how-tos.md)  
  
  
