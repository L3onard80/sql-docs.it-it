---
title: DrilldownLevelTop (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 461c91d7261b42b5828e2c515a89e8203f40e357
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68049271"
---
# <a name="drilldownleveltop-mdx"></a>DrilldownLevelTop (MDX)


  Esegue il drill-down, fino al livello immediatamente inferiore, dei membri di livello più alto di un set al livello specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DrilldownLevelTop(<Set_Expression>, <Count> [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Conteggio*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Numeric_Expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
 *Include_Calc_Members*  
 Parola chiave per l'aggiunta di membri calcolati ai risultati del drill-down.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificata un'espressione numerica, la funzione **DrilldownLevelTop** Ordina in ordine decrescente gli elementi figlio di ogni membro nel set specificato in base al valore dell'espressione numerica, valutato sul set di membri figlio. Se non viene specificata un'espressione numerica, la funzione dispone in ordine decrescente i membri figlio di ogni membro nel set specificato in base ai valori delle celle rappresentate dal set di membri figlio, come determinato dal contesto della query.  
  
 Dopo l'ordinamento, la funzione **DrilldownLevelTop** restituisce un set contenente i membri padre e il numero di membri figlio, specificato in *Count,* con il valore massimo.  
  
 La funzione **DrilldownLevelTop** è simile alla funzione [DrilldownLevel](../mdx/drilldownlevel-mdx.md) , ma anziché includere tutti gli elementi figlio per ogni membro al livello specificato, la funzione **DrilldownLevelTop** restituisce il numero più alto di membri figlio.  
  
 Eseguendo una query sulla proprietà XMLA MdpropMdxDrillFunctions è possibile verificare il livello di supporto fornito dal server per le funzioni di drill-through. per informazioni dettagliate, vedere [Proprietà XMLA supportate &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce i primi tre membri figlio del livello Product Category in base alla misura predefinita. Nel cubo di esempio Adventure Work i primi tre membri figlio per Accessories sono Bike Racks, Bike Stands e Bottles and Cages. Nella finestra Query MDX di Management Studio è possibile passare a Products | Product Categories | Members | All Products | Accessories per visualizzare l'elenco completo. È possibile incrementare l'argomento Count per restituire più membri.  
  
```  
SELECT DrilldownLevelTop   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene illustrato l'uso del flag di **INCLUDE_CALC_MEMBERS** , usato per includere i membri calcolati nel livello di drill-down. La misura [Reseller Order Count] è inclusa nell'istruzione **DrilldownLevelTop** per garantire che i valori restituiti siano ordinati in base a tale misura.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELTOP(  
  [Product].[Product Categories].children ,  
  2,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DrilldownLevel &#40;&#41;MDX](../mdx/drilldownlevel-mdx.md)   
 [Guida di riferimento alle funzioni MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
