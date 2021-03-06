---
title: 'Funzione SQL: Variable () (XQuery) | Microsoft Docs'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:variable() function
- sql:variable function
ms.assetid: 6e2e5063-c1cf-4b5a-b642-234921e3f4f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 56a8c53a22fefec7fbda4c2ac7476ae46d664199
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946000"
---
# <a name="xquery-extension-functions---sqlvariable"></a>Funzioni per estensioni XQuery - sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Espone in un'espressione XQuery una variabile che contiene un valore SQL relazionale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>Osservazioni  
 Come descritto nell'argomento [associazione di dati relazionali all'interno di codice XML](../t-sql/xml/binding-relational-data-inside-xml-data.md), è possibile utilizzare questa funzione quando si utilizzano [i metodi con tipo di dati XML](../t-sql/xml/xml-data-type-methods.md) per esporre un valore relazionale all'interno di XQuery.  
  
 Il [metodo query ()](../t-sql/xml/query-method-xml-data-type.md) , ad esempio, viene utilizzato per specificare una query su un'istanza XML archiviata in una variabile o in una colonna con tipo di dati **XML** . A volte è necessario creare query in grado di utilizzare anche valori contenuti in un parametro o in una variabile [!INCLUDE[tsql](../includes/tsql-md.md)], per mettere insieme dati relazionali e XML. A tale scopo, usare la funzione **SQL: Variable** .  
  
 Il valore SQL verrà mappato a un valore XQuery corrispondente e il relativo tipo sarà un tipo di base XQuery equivalente al tipo SQL corrispondente.  
  
 È possibile fare riferimento a un'istanza **XML** solo nel contesto dell'espressione di origine di un'istruzione XML-DML insert. in caso contrario, non è possibile fare riferimento a valori di tipo **XML** o di un tipo di Common Language Runtime (CLR) definito dall'utente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>R. Utilizzo della funzione sql:variable() per convertire in XML il valore di una variabile Transact-SQL  
 Nell'esempio seguente viene costruita un'istanza XML costituita da:  
  
-   Un valore (`ProductID`) ottenuto da una colonna non XML. La [funzione SQL: Column ()](../xquery/xquery-extension-functions-sql-column.md) viene utilizzata per associare questo valore nel codice XML.  
  
-   Un valore (`ListPrice`) ottenuto da una colonna non XML di un'altra tabella. La funzione `sql:column()` viene utilizzata anche in questo caso per associare tale valore nell'istanza XML.  
  
-   Un valore (`DiscountPrice`) ottenuto da una variabile [!INCLUDE[tsql](../includes/tsql-md.md)]. Il metodo `sql:variable()` viene utilizzato per associare tale valore nell'istanza XML.  
  
-   Valore (`ProductModelName`) da una colonna di tipo **XML** , per rendere la query più interessante.  
  
 Query:  
  
```sql
DECLARE @price money  
  
SET @price=2500.00  
SELECT ProductID, Production.ProductModel.ProductModelID,CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
       <Product   
           ProductID="{ sql:column("Production.Product.ProductID") }"  
           ProductModelID= "{ sql:column("Production.Product.ProductModelID") }"  
           ProductModelName="{/pd:ProductDescription[1]/@ProductModelName }"  
           ListPrice="{ sql:column("Production.Product.ListPrice") }"  
           DiscountPrice="{ sql:variable("@price") }"  
        />')   
FROM Production.Product   
JOIN Production.ProductModel  
ON Production.Product.ProductModelID = Production.ProductModel.ProductModelID  
WHERE ProductID=771  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Gli elementi XQuery utilizzati nel metodo `query()` costruiscono l'istanza XML.  
  
-   La `namespace` parola chiave viene usata per definire un prefisso dello spazio dei nomi nel [prologo XQuery](../xquery/modules-and-prologs-xquery-prolog.md). Tale prefisso viene creato perché il valore dell'attributo `ProductModelName` viene recuperato dalla colonna di tipo xml `CatalogDescription xml`, a cui è associato uno schema.  
  
 Risultato:  
  
```xml
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di estensione di SQL Server XQuery](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Creare istanze di dati XML](../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio XML di manipolazione dei dati &#40;XML DML&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
