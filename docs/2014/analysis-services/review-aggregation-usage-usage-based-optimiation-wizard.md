---
title: Esaminare l'utilizzo delle aggregazioni (procedura guidata basata basata sull'utilizzo) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a58f7f8620924d4f707fe61c45ae87e19737471f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070166"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a>Controlla utilizzo aggregazioni (Ottimizzazione guidata basata sulle statistiche di utilizzo)
  Utilizzare la pagina **Controlla utilizzo aggregazioni** per configurare le impostazioni di utilizzo delle aggregazioni.  
  
## <a name="options"></a>Opzioni  
 **Default**  
 Selezionare per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo su Predefinito. Con questa impostazione, la progettazione applica una regola predefinita in base al tipo di attributo e di dimensione.  
  
 **Completo**  
 Selezionare per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo in Completa. Con questa impostazione, ogni aggregazione per il cubo deve includere questo attributo o un attributo correlato che è a un livello inferiore nella catena dell'attributo. Evitare l'impostazione di utilizzo aggregazioni Completa quando un attributo contiene molti membri. Se specificata per più attributi o attributi che hanno molti membri, questa impostazione potrebbe impedire la progettazione delle aggregazioni a causa delle dimensioni eccessive.  
  
 **Nessuno**  
 Selezionare per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo in Nessuna. Con questa impostazione nessuna aggregazione del cubo deve includere questo attributo.  
  
 **Unrestricted**  
 Selezionare per impostare l'impostazione di utilizzo delle aggregazioni per l'attributo su Senza restrizioni. Con questa impostazione non sono inserite restrizioni nella progettazione delle aggregazioni. Tuttavia, l'attributo ancora deve essere valutato per stabilire se è idoneo.  
  
 **Imposta come predefinito per tutti**  
 Selezionare per impostare le impostazioni  di utilizzo delle aggregazioni per tutti gli attributi su Predefinito.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida sensibile al contesto della progettazione guidata aggregazioni](aggregation-design-wizard-f1-help.md)   
 [Procedure guidate di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
