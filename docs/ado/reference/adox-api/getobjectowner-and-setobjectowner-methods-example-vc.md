---
title: Esempio di metodi GetObjectOwner e SetObjectOwner (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SetObjectOwner method [ADOX], VC++ example
- GetObjectOwner method [ADOX], VC++ example
ms.assetid: f5f2aa4b-d790-458f-9e70-1643e3e203b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c16536becfcea826d9cb6e6ea251517d40ad3ded
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "76934642"
---
# <a name="getobjectowner-and-setobjectowner-methods-example-vc"></a>Esempio dei metodi GetObjectOwner e SetObjectOwner (VC++)
Questo esempio illustra i metodi [GetObjectOwner](../../../ado/reference/adox-api/getobjectowner-method-adox.md) e [SetObjectOwner](../../../ado/reference/adox-api/setobjectowner-method.md) . Questo codice presuppone l'esistenza dell'accounting del gruppo (vedere l'esempio relativo ai [gruppi e agli utenti Append, ChangePassword Methods (VC + +)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vc.md) per vedere come aggiungere questo gruppo al sistema). Il proprietario della tabella Categories è impostato su Accounting.  
  
```  
// BeginOwnersCpp.cpp  
// compile with: /EHsc  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define and initialize ADOX object pointers. These are in the ADODB namespace.  
   _TablePtr m_pTable = NULL;  
   _CatalogPtr m_pCatalog = NULL;  
  
   try {  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));  
      TESTHR(hr = m_pTable.CreateInstance(__uuidof(Table)));  
  
      // Open the Catalog.  
      m_pCatalog->PutActiveConnection("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';jet oledb:system database='c:\\system.mdw'");  
  
      // Print the original owner of Categories  
      _bstr_t strOwner = m_pCatalog->GetObjectOwner("Categories", adPermObjTable);  
      cout << "Owner of Categories: " << strOwner << "\n" << endl;  
  
      //Create and append new group with a string.  
      m_pCatalog->Groups->Append("Accounting");  
  
      //Set the owner of Categories to Accounting.  
      m_pCatalog->SetObjectOwner("Categories", adPermObjTable, "Accounting");  
  
      _variant_t vIndex;  
      // List the owners of all tables and columns in the catalog.  
      for ( long iIndex = 0 ; iIndex < m_pCatalog->Tables->Count ; iIndex++ ) {  
         vIndex = iIndex;  
         m_pTable = m_pCatalog->Tables->GetItem(vIndex);  
         cout << "Table: " << m_pTable->Name << endl;  
         cout << "   Owner: " << m_pCatalog->GetObjectOwner(m_pTable->Name, adPermObjTable) << endl;  
      }  
  
      // Restore the original owner of Categories  
      m_pCatalog->SetObjectOwner("Categories", adPermObjTable, strOwner);  
  
      // Delete Accounting  
      m_pCatalog->Groups->Delete("Accounting");  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
  
   catch(...) {  
      cout << "Error occurred in include files...." << endl;  
   }  
   ::CoUninitialize();  
}  
```
