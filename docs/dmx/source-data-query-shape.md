---
title: SHAPE (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: c928d4c96917479f8c37415d5ebe2db9b7f9eb98
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938111"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;query&gt; dei dati di origine-forma
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Consente di combinare query da più origini dei dati in una singola tabella gerarchica, ovvero una tabella con tabelle nidificate, che diventa la tabella dei case per il modello di data mining.  
  
 La sintassi completa del comando **Shape** è documentata nel software [!INCLUDE[msCoName](../includes/msconame-md.md)] Development Kit (SDK) di Data Access Components (MDAC).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argomenti  
 *query master*  
 Query che restituisce la tabella padre.  
  
 *query tabella figlio*  
 Query che restituisce la tabella nidificata.  
  
 *colonna master*  
 Colonna della tabella padre utilizzata per identificare le righe figlio tra i risultati di una query che restituisce una tabella figlio.  
  
 *colonna figlio*  
 Colonna della tabella figlio utilizzata per identificare le righe padre tra i risultati di una query che restituisce la tabella padre.  
  
 *Nome tabella colonne*  
 Nome della colonna appena aggiunta nella tabella padre per creare la tabella figlio.  
  
## <a name="remarks"></a>Osservazioni  
 Le query devono essere ordinate in base alla colonna che definisce la correlazione tra la tabella padre e la tabella figlio.  
  
## <a name="examples"></a>Esempi  
 Per eseguire il training di un modello contenente una tabella nidificata, è possibile utilizzare l'esempio seguente all'interno di un'istruzione [INSERT INTO &#40;&#41;DMX](../dmx/insert-into-dmx.md) . Le due tabelle all'interno dell'istruzione **Shape** sono correlate tramite la colonna **OrderNumber** .  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Vedere anche  
 [&#60;query sui dati di origine&#62;](../dmx/source-data-query.md)   
 [Le estensioni di data mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Le estensioni di data mining &#40;DMX&#41; le istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX&#41; &#40;di Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
