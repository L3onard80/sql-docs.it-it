---
title: Espressioni logiche (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- logical operators [SQL Server], XQuery
- effective Boolean value [XQuery]
- logical expressions [XQuery]
- EBV
- expressions [XQuery], logical
ms.assetid: de94cd2e-2d48-49fb-9ebd-a2d90c79bf62
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fd6417c10be286164b9d56a0c2587dfd63a1de23
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51670339"
---
# <a name="logical-expressions-xquery"></a>Espressioni logiche (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery supporta l'operatore logico **e** e **o** operatori.  
  
```  
expression1 and expression2  
expression1 or expression2  
```  
  
 Le espressioni di prova `expression1,``expression2`, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] può comportare una sequenza vuota, una sequenza di uno o più nodi o un singolo valore booleano. In base al risultato, il valore booleano effettivo viene determinato nel modo seguente:  
  
-   Se l'espressione di prova restituisce una sequenza vuota, il risultato dell'espressione è False.  
  
-   Se l'espressione di prova restituisce un singolo valore booleano, il risultato dell'espressione è tale valore.  
  
-   Se l'espressione di prova restituisce una sequenza costituita da uno o più nodi, il risultato dell'espressione è True.  
  
-   Negli altri casi, viene restituito un errore statico.  
  
 L'operatore logico **e** e **o** operatore viene quindi applicato ai valori booleani risultanti delle espressioni con la semantica logica standard.  
  
 La query recupera dal catalogo prodotti la versione piccola delle foto con angolazione frontale, corrispondenti all'elemento <`Picture`>, relative a un modello di prodotto specifico. Si noti che, per ogni documento di descrizione del prodotto, nel catalogo è possibile archiviare uno o più foto del prodotto con attributi diversi, ad esempio le dimensioni e l'angolazione.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $F in /PD:ProductDescription/PD:Picture[PD:Size="small"   
                                                 and PD:Angle="front"]  
     return   
         $F   
    ') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 Risultato:  
  
```  
<PD:Picture   
  xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  <PD:Angle>front</PD:Angle>  
  <PD:Size>small</PD:Size>  
  <PD:ProductPhotoID>31</PD:ProductPhotoID>  
</PD:Picture>  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni XQuery](../xquery/xquery-expressions.md)  
  
  
