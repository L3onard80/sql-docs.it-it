---
title: DELETE (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bc78718c813ef1aa599c1ab299c634d018bc88d6
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144547"
---
# <a name="delete-dmx"></a>DELETE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Cancella un modello di data mining, una struttura di data mining o una struttura di data mining e tutti i modelli di data mining associati, a seconda delle clausole DMX (Data Mining Extensions) utilizzate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DELETE FROM [MINING MODEL] <model>[.CONTENT]  
DELETE FROM [MINING STRUCTURE] <structure>[.CONTENT]|[.CASES]  
```  
  
## <a name="arguments"></a>Argomenti  
 *model*  
 Identificatore del modello.  
  
 *struttura*  
 Identificatore della struttura.  
  
## <a name="remarks"></a>Note  
 Se non si specifica **modello di data MINING** oppure **struttura di data MINING**, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cerca il tipo di oggetto in base al nome ed elabora l'oggetto corretto. Se il server contiene una struttura di data mining e un modello di data mining con lo stesso nome, verrà restituito un errore.  
  
 Nella tabella seguente sono descritti i risultati ottenuti utilizzando le diverse forme della sintassi.  
  
|.|Risultato|  
|---------------|------------|  
|DELETE FROM MINING STRUCTURE*\<struttura >*<br /><br /> o Gestione configurazione<br /><br /> DELETE FROM MINING STRUCTURE*\<struttura >*. CONTENUTO|Esegue ProcessClear nella struttura di data mining. Viene cancellato tutto il contenuto della struttura di data mining e dei modelli di data mining associati.|  
|DELETE FROM MINING STRUCTURE*\<struttura >*. CASE|Esegue ProcessClearStructureOnly nella struttura di data mining. Viene cancellato tutto il contenuto della struttura di data mining, lasciando invariati i modelli di data mining associati. Dopo la cancellazione della struttura di data mining non è possibile eseguire il drill-through sui modelli di data mining associati.|  
|Elimina dal modello di data MINING*\<modello >*<br /><br /> o Gestione configurazione<br /><br /> Elimina dal modello di data MINING*\<modello >*. CONTENUTO|Esegue ProcessClear sul modello di data mining, ma lascia invariati i valori dello stato. I valori di stato sono i possibili stati di una colonna. Per la colonna del genere, ad esempio, i valori di stato sono maschio e femmina.|  
  
 Per altre informazioni sui tipi di elaborazione, vedere [elemento di tipo &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso tutto il contenuto dal modello NB_Sample.  
  
```  
DELETE FROM NB_Sample.CONTENT  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le estensioni di Data Mining di dati &#40;DMX&#41; istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Le estensioni di Data Mining di dati &#40;DMX&#41; istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
