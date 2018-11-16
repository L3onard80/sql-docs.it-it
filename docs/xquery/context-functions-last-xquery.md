---
title: Funzione (XQuery) Last | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- last function [XQuery]
- fn:last function
ms.assetid: dc92086e-3b01-4b0b-9f54-3bbf306cf7ae
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7220b0fe10f88ec9ba78d31a8507d12eba7aafff
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674070"
---
# <a name="context-functions---last-xquery"></a>Funzioni di contesto - last (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero di elementi della sequenza da elaborare. In particolare, restituisce l'indice di valori interi dell'ultimo elemento della sequenza. Il valore di indice del primo elemento della sequenza è 1.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:last() as xs:integer  
```  
  
## <a name="remarks"></a>Note  
 In SQL Server **fn:last()** può essere usato solo nel contesto di un predicato dipendente dal contesto. In particolare, può essere utilizzata solo tra parentesi (`[ ]`).  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-using-the-last-xquery-function-to-retrieve-the-last-two-manufacturing-steps"></a>A. Utilizzo della funzione XQuery last() per recuperare le ultime due fasi di produzione  
 La query seguente recupera le ultime due fasi di produzione relative a un modello di prodotto specifico. Il valore, il numero di fasi di produzione, restituiti dai **Last** funzione viene utilizzata nella query seguente per recuperare le ultime due fasi di produzione.  
  
```  
SELECT ProductModelID, Instructions.query('   
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  <LastTwoManuSteps>  
   <Last-1Step>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[(last()-1)]/text() }  
   </Last-1Step>  
   <LastStep>   
     { (/AWMI:root/AWMI:Location)[1]/AWMI:step[last()]/text() }  
   </LastStep>  
  </LastTwoManuSteps>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Nella query precedente, il **Last** funzionare in /`/AWMI:root//AWMI:Location)[1]/AWMI:step[last()]` restituisce il numero di fasi di produzione. Tale valore viene utilizzato per recuperare l'ultima fase di produzione nel centro di lavorazione.  
  
 Risultato:  
  
```  
ProductModelID Result    
-------------- -------------------------------------  
7      <LastTwoManuSteps>  
         <Last-1Step>  
            When finished, inspect the forms for defects per   
            Inspection Specification .  
         </Last-1Step>  
         <LastStep>Remove the frames from the tool and place them   
            in the Completed or Rejected bin as appropriate.  
         </LastStep>  
       </LastTwoManuSteps>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
