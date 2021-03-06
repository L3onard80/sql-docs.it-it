---
title: Oggetto View (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6bc26e8d59c29bd7b1b0fbdd0a3a4fdb39f8fee1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964840"
---
# <a name="view-object-adox"></a>Oggetto View (ADOX)
Rappresenta un set filtrato di record o una tabella virtuale. Quando viene utilizzato insieme all'oggetto [comando](../../../ado/reference/ado-api/command-object-ado.md) ADO, l'oggetto **View** può essere utilizzato per aggiungere, eliminare o modificare le visualizzazioni.  
  
## <a name="remarks"></a>Osservazioni  
 Una vista è una tabella virtuale, creata da altre tabelle o viste di database. L'oggetto **visualizzazione** consente di creare una visualizzazione senza dover essere a conoscenza o utilizzare la sintassi "Create View" del provider.  
  
 Con le proprietà di un oggetto **visualizzazione** , è possibile:  
  
-   Identificare la vista con la proprietà [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Specificare l'oggetto **comando** ADO che può essere utilizzato per aggiungere, eliminare o modificare viste con la proprietà [Command](../../../ado/reference/adox-api/command-property-adox.md) .  
  
-   Restituisce informazioni sulla data con le proprietà [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) e [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) .  
  
 Questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto View](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di raccolte views e Fields (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Esempio di metodo Append views (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Raccolta views, esempio di proprietà CommandText (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Esempio di metodo Delete views (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Raccolta Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
