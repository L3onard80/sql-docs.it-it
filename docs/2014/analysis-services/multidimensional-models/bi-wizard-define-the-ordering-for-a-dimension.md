---
title: Definire l'ordinamento per una dimensione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05e75eb726d67e992a0a9320be8d23bbc547bedb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076855"
---
# <a name="define-the-ordering-for-a-dimension"></a>Definire l'ordinamento di una dimensione
  L'aggiunta della funzionalità avanzata di ordinamento degli attributi a un cubo o una dimensione consente di specificare come verranno ordinati i membri di un attributo. I membri possono essere ordinati in base al nome o alla chiave dell'attributo oppure in base al nome o alla chiave di un altro attributo (tramite una relazione tra attributi). Per impostazione predefinita, i membri vengono ordinati in base al nome. Questa funzionalità avanzata modifica l'impostazione delle proprietà `OrderBy` e `OrderByAttributeID` degli attributi in una dimensione.  
  
 Per aggiungere la funzionalità di ordinamento degli attributi, usare Configurazione guidata funzionalità di Business Intelligence e quindi selezionare l'opzione **Impostazione ordinamento attributi** nella pagina **Scelta funzionalità avanzata** . Questa procedura guidata consente di eseguire in modo semplificato i passaggi relativi alla selezione di una dimensione alla quale si desidera applicare l'ordinamento degli attributi e all'impostazione della modalità di ordinamento degli attributi per la dimensione selezionata.  
  
## <a name="selecting-a-dimension"></a>Selezione di una dimensione  
 Nella prima pagina **Impostazione ordinamento attributi** della procedura guidata specificare la dimensione alla quale si desidera applicare l'ordinamento degli attributi. L'aggiunta della funzionalità avanzata dell'ordinamento degli attributi alla dimensione selezionata implica modifiche alla dimensione. Tali modifiche verranno ereditate da tutti i cubi che includono la dimensione selezionata.  
  
## <a name="specifying-ordering"></a>Impostazione dell'ordinamento  
 Nella seconda pagina **Impostazione ordinamento attributi** della procedura guidata specificare la modalità di ordinamento di tutti gli attributi nella dimensione.  
  
 Nella colonna **Attributo di ordinamento** è possibile modificare l'attributo usato per l'ordinamento. Se l'attributo che si desidera utilizzare per ordinare i membri non è presente nell'elenco, scorrere l'elenco verso il basso, quindi selezionare ** \<nuovo attributo... >** per aprire la finestra di dialogo **Seleziona colonna** , in cui è possibile selezionare una colonna in una tabella delle dimensioni. La selezione di una colonna tramite la finestra di dialogo **Seleziona colonna** consente di creare un attributo aggiuntivo in base al quale ordinare i membri di un attributo.  
  
 Nella colonna **Criteri** è quindi possibile selezionare se ordinare i membri dell'attributo in base alla **chiave** oppure al **nome**.  
  
  
