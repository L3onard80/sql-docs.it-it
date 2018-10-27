---
title: Drill-through sulle strutture di Data Mining | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6d2ea3d80496f84330802640ff99d951fd2416bb
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146487"
---
# <a name="drillthrough-on-mining-structures"></a>Drill-through sulle strutture di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Il termine*drill-through* indica la possibilità di eseguire query su un modello o una struttura di data mining e di ottenere dati dettagliati non esposti nel modello.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] offre due diverse opzioni per il drill-through dei dati del case. È possibile eseguire il drill-through dei dati utilizzati per compilare il modello di data mining o dei dati di origine nella struttura di data mining.  
  
## <a name="drillthrough-to-model-cases-vs-drillthrough-to-structure"></a>Drill-through nei case del modello e drill-through nella struttura  
 Il drill-through nei **case del modello** è utile per trovare dettagli aggiuntivi su regole, schemi o cluster in un modello.  
  
 Al contrario, il **drill-through dei dati della struttura** consente l'accesso a informazioni non disponibili nel modello. Ad esempio, se si dispone delle autorizzazioni appropriate, è possibile risalire alle righe di dati utilizzate per il training del modello e a quelle utilizzate per il test.  
  
 È possibile visualizzare gli attributi dei dati non utilizzati nell'analisi, a condizione che siano stati inclusi nella definizione della struttura. Ad esempio, le strutture di data mining supportano spesso molti tipi diversi di modelli ed è possibile che alcune colonne della struttura siano state escluse da un modello perché il tipo di dati era incompatibile o i dati non erano utili per l'analisi. Non è ad esempio consigliabile utilizzare le informazioni di contatto del cliente in un modello di clustering, anche se i dati sono stati inclusi nella struttura, tuttavia abilitando il drill-through è possibile accedere a queste informazioni senza eseguire query separate sull'origine dati.  
  
## <a name="enabling-drillthrough-to-structure-data"></a>Abilitazione del drill-through per i dati della struttura  
 Per utilizzare il drill-through per la struttura di data mining, è necessario soddisfare le condizioni seguenti:  
  
-   È anche necessario abilitare il drill-through per il modello. Per impostazione predefinita, entrambi i tipi di drill-through sono disabilitati. Per abilitare il drill-through nella Creazione guidata modello di data mining, selezionare l'opzione per abilitare il drill-through per i case del modello nell'ultima pagina della procedura guidata. È anche possibile abilitare in seguito il drill-through per un modello modificando la proprietà **AllowDrillthrough** .  
  
-   Se si crea la struttura di data mining utilizzando DMX, utilizzare la clausola WITH DRILLTHROUGH. Per altre informazioni, vedere [CREATE MINING STRUCTURE &#40;DMX&#41;](../../dmx/create-mining-structure-dmx.md).  
  
-   Il drill-through consiste nel recupero delle informazioni sui case di training memorizzati nella cache durante l'elaborazione della struttura di data mining. Pertanto, se i dati memorizzati nella cache sono stati cancellati dopo l'elaborazione della struttura impostando la proprietà <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> su **ClearAfterProcessing**, il drill-through non funzionerà. Per abilitare il drill-through per le colonne della struttura, è necessario impostare la proprietà <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> su **KeepTrainingCases** e rielaborare la struttura.  
  
-   Verificare che la proprietà [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) sia impostata su **True**sia per il modello sia per la struttura di data mining. È inoltre necessario essere membro di un ruolo che disponga delle autorizzazioni di drill-through sia per la struttura sia per il modello.  
  
## <a name="security-issues-for-drillthrough"></a>Problemi di sicurezza correlati al drill-through  
 Le autorizzazioni di drill-through vengono impostate separatamente per la struttura e per il modello. L'autorizzazione del modello consente di eseguire il drill-through dal modello, anche se non si dispone di autorizzazioni sulla struttura. Le autorizzazioni di drill-through per la struttura consentono di includere colonne della struttura nelle query di drill-through dal modello usando la funzione [StructureColumn &#40;DMX&#41;](../../dmx/structurecolumn-dmx.md).  
  
 Per altre informazioni su come creare ruoli e assegnare autorizzazioni in Analysis Services, vedere [Progettazione ruoli &#40;Analysis Services - Dati multidimensionali&#41;](http://msdn.microsoft.com/library/e8ba42db-0565-4d68-b3ab-0c63d8d07192).  
  
> [!NOTE]  
>  Se si abilita il drill-through per la struttura e per il modello di data mining, qualsiasi utente che sia un membro di un ruolo che dispone delle autorizzazioni di drill-through per il modello di data mining può anche visualizzare le colonne della struttura di data mining, anche se tali colonne non sono incluse nel modello di data mining. Pertanto, per proteggere i dati sensibili, è necessario configurare la vista origine dati per mascherare le informazioni personali e consentire l'accesso drill-through alla struttura di data mining solo quando necessario.  
  
## <a name="related-tasks"></a>Attività correlate  
 Per ulteriori informazioni su come utilizzare il drill-through con i modelli di data mining, vedere gli argomenti seguenti:  
  
|||  
|-|-|  
|Utilizzo del drill-through per la struttura dai visualizzatori del modello di data mining|[Usare il drill-through dai visualizzatori modello](../../analysis-services/data-mining/use-drillthrough-from-the-model-viewers.md)|  
|Per tipi di modelli specifici, vedere gli esempi di query drill-through.|[Query di data mining](../../analysis-services/data-mining/data-mining-queries.md)|  
|Ottenere informazioni sulle autorizzazioni applicabili a strutture e modelli di data mining specifici.|[Concedere le autorizzazioni per le strutture e i modelli di data mining &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Drill-through sui modelli di data mining](../../analysis-services/data-mining/drillthrough-on-mining-models.md)  
  
  
