---
title: Sintassi della gerarchia di oggetti (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], hierarchy syntax
ms.assetid: 7ed8df86-9fd2-4e09-96bc-5381fec85f65
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3405621d604e6450756520f6d93b66a51d4d66c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67941981"
---
# <a name="object-hierarchy-syntax-transact-sql"></a>Sintassi della gerarchia degli oggetti (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Il parametro *PropertyName* di sp_OAGetProperty e sp_OASetProperty e il parametro *methodname* di sp_OAMethod supportano una sintassi della gerarchia degli oggetti simile a quella [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]di. Quando viene adottata questa sintassi speciale, i parametri sopraindicati seguono il seguente formato generale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
'TraversedObject.PropertyOrMethod'  
```  
  
## <a name="arguments"></a>Argomenti  
 *TraversedObject*  
 È un oggetto OLE nella gerarchia sotto il *objecttoken* specificato nell'stored procedure. Utilizzare la sintassi di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] per specificare una serie di raccolte, proprietà oggetto e metodi che restituiscono oggetti. I vari identificatori di oggetti della serie devono essere separati da un punto (.).  
  
 Un elemento della serie potrebbe essere il nome di una raccolta. Per specificare una raccolta, utilizzare la seguente sintassi:  
  
 Raccolta ("*Item*")  
  
 Le virgolette doppie (") sono obbligatorie. La sintassi di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] con il punto esclamativo (!) non è supportata per le raccolte.  
  
 *PropertyOrMethod*  
 Nome di una proprietà o di un metodo di *TraversedObject*.  
  
 Per specificare tutti i parametri indice o metodo tramite i parametri di sp_OAGetProperty, sp_OASetProperty o sp_OAMethod (compreso il supporto per i parametri di output di sp_OAMethod), utilizzare la sintassi seguente:  
  
 *PropertyOrMethod*  
  
 Per specificare tutti i parametri indice o metodo tra parentesi e ignorare di conseguenza tutti i parametri indice o metodo di sp_OAGetProperty, sp_OASetProperty o sp_OAMethod, utilizzare la sintassi seguente:  
  
 *PropertyOrMethod*([ *parameterName*: =] "*Parameter*" [,...])  
  
 Le virgolette doppie (") sono obbligatorie. Tutti i parametri denominati devono essere specificati dopo tutti i parametri posizionali.  
  
## <a name="remarks"></a>Osservazioni  
 Se *TraversedObject* non è specificato, *PropertyOrMethod* è obbligatorio.  
  
 Se *PropertyOrMethod* non è specificato, *TraversedObject* viene restituito come parametro di output del token dell'oggetto dal stored procedure di automazione OLE. Se viene specificato *PropertyOrMethod* , viene chiamato il metodo o la proprietà di *TraversedObject* e il valore della proprietà o il valore restituito del metodo viene restituito come parametro di output dalla stored procedure di automazione OLE.  
  
 Se un elemento nell'elenco *TraversedObject* non restituisce un oggetto OLE, viene generato un errore.  
  
 Per ulteriori informazioni sulla sintassi degli oggetti OLE di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], consultare la documentazione di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
 Per ulteriori informazioni sui codici restituiti HRESULT, vedere [sp_OACreate &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nei seguenti esempi di sintassi della gerarchica degli oggetti viene utilizzato un oggetto SQL-DMO SQLServer.  
  
```  
-- Get the AdventureWorks2012 Person.Address Table object.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address")',  
   @table OUT  
  
-- Get the Rows property of the AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").Rows',  
   @rows OUT  
  
-- Call the CheckTable method to validate the   
-- AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAMethod @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").CheckTable',  
   @checkoutput OUT  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Script di esempio di automazione OLE](../../relational-databases/stored-procedures/ole-automation-sample-script.md)   
 [Stored procedure di automazione &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
  
  
