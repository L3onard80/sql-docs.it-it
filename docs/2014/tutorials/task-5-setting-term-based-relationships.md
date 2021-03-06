---
title: 'Attività 5: impostazione delle relazioni basate su termini | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0e9a6a1a96d208077e70c0cf1835cff6e34650dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489114"
---
# <a name="task-5-setting-term-based-relationships"></a>Attività 5: Impostazione delle relazioni basate su termini
  In questa attività vengono definite alcune relazioni basate su termini per i valori per il dominio **Supplier Name** . Una relazione basata su termini consente di effettuare una correzione a un termine che fa parte di un valore in un dominio, consentendo in questo modo a più valori identici ad eccezione dell'ortografia di una parte in comune tra essi di essere considerati sinonimi identici. Ad esempio, **Inc.** può essere corretto in **incorporato**. Queste relazioni vengono utilizzate da DQS nei processi di individuazione delle informazioni, di pulizia o di corrispondenza. Per altri dettagli, vedere [creare relazioni basate su termini](https://msdn.microsoft.com/library/hh510404.aspx) .  
  
1.  Selezionare **Supplier Name** nell' **elenco di domini**.  
  
2.  Passare alla scheda **relazioni basate su termini** nel riquadro di destra.  
  
3.  Fare clic sul pulsante **Aggiungi nuova relazione** sulla barra degli strumenti per aggiungere una relazione alla tabella.  
  
4.  Digitare **Co.** per il campo **valore** e **società** per il campo **Correggi in** .  
  
5.  Ripetere i due passaggi precedenti per i valori seguenti:  
  
    |valore|Correggi in|  
    |-----------|----------------|  
    |Corp.|Corporation|  
    |Inc.|Incorporated|  
  
     ![Relazioni basate su termini](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Relazioni basate su termini")  
  
## <a name="next-step"></a>passaggio successivo  
 [Attività 6: Impostazione di sinonimi](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
