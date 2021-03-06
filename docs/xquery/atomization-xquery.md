---
title: Atomizzazione (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, atomization
- atomization [XQuery]
ms.assetid: e3d7cf2f-c6fb-43c2-8538-4470a6375af5
author: rothja
ms.author: jroth
ms.openlocfilehash: e034e6464e395c1516eed874ed1c0cff2c32238f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985704"
---
# <a name="atomization-xquery"></a>Atomizzazione (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Per atomizzazione si intende il processo di estrazione del valore tipizzato di un elemento. In determinate circostanze, il processo è implicito. Alcuni operatori XQuery, ad esempio gli operatori aritmetici e di confronto, dipendono da tale processo. Ad esempio, quando si applicano operatori aritmetici direttamente ai nodi, il valore tipizzato di un nodo viene innanzitutto recuperato richiamando in modo implicito la [funzione dati](../xquery/data-accessor-functions-data-xquery.md). Tale funzione passa il valore atomico come operando all'operatore aritmetico.  
  
 Ad esempio, la query seguente restituisce il numero totale di attributi LaborHours. In questo caso, **Data ()** viene applicato in modo implicito ai nodi attributo.  
  
```  
declare @x xml  
set @x='<ROOT><Location LID="1" SetupTime="1.1" LaborHours="3.3" />  
<Location LID="2" SetupTime="1.0" LaborHours="5" />  
<Location LID="3" SetupTime="2.1" LaborHours="4" />  
</ROOT>'  
-- data() implicitly applied to the attribute node sequence.  
SELECT @x.query('sum(/ROOT/Location/@LaborHours)')  
```  
  
 Sebbene non sia obbligatorio, è anche possibile specificare in modo esplicito la funzione **Data ()** :  
  
```  
SELECT @x.query('sum(data(ROOT/Location/@LaborHours))')  
```  
  
 Un altro esempio di atomizzazione implicita riguarda l'utilizzo di operatori aritmetici. L' **+** operatore richiede valori atomici e i **dati ()** vengono applicati in modo implicito per recuperare il valore atomico dell'attributo LaborHours. La query viene specificata sulla colonna Instructions del tipo **XML** nella tabella ProductModel. La query seguente restituisce tre volte l'attributo LaborHours. Dalla query si noti quanto segue:  
  
-   Nella costruzione dell'attributo OrignialLaborHours, l'atomizzazione viene applicata in modo implicito alla sequenza singleton restituita da (`$WC/@LaborHours`). Il valore tipizzato dell'attributo LaborHours viene assegnato a OrignialLaborHours.  
  
-   Nella costruzione dell'attributo UpdatedLaborHoursV1, l'operatore aritmetico richiede valori atomici. Pertanto, **Data ()** viene applicato in modo implicito all'attributo LaborHours restituito da (`$WC/@LaborHours`). Successivamente, viene aggiunto il valore atomico 1. La costruzione dell'attributo UpdatedLaborHoursV2 Mostra l'applicazione esplicita dei **dati ()**, ma non è obbligatoria.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in /AWMI:root/AWMI:Location[1]  
        return  
            <WC OriginalLaborHours = "{ $WC/@LaborHours }"  
                UpdatedLaborHoursV1 = "{ $WC/@LaborHours + 1 }"   
                UpdatedLaborHoursV2 = "{ data($WC/@LaborHours) + 1 }" >  
            </WC>') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Risultato:  
  
```  
<WC OriginalLaborHours="2.5"   
    UpdatedLaborHoursV1="3.5"   
    UpdatedLaborHoursV2="3.5" />  
```  
  
 L'atomizzazione restituisce un'istanza di tipo semplice, un set vuoto o un errore di tipo statico.  
  
 L'atomizzazione si verifica anche nei parametri delle espressioni di confronto passati alle funzioni, ai valori restituiti dalle funzioni, alle espressioni **cast ()** e alle espressioni di ordinamento passate nella clausola ORDER BY.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su XQuery](../xquery/xquery-basics.md)   
 [Espressioni di confronto &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)   
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
