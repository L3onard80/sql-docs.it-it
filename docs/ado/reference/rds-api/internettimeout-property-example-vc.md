---
title: Esempio di Proprietà InternetTimeout (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- InternetTimeout property [ADO], VC++ example
ms.assetid: 88b6d05c-d4eb-4ab1-bbe2-95d146237f94
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7596f9728f7a51a5d28a3c1a19943efff783ac62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963996"
---
# <a name="internettimeout-property-example-vc"></a>Esempio della proprietà InternetTimeout (VC++)
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 In questo esempio viene illustrata la proprietà [InternetTimeout](../../../ado/reference/rds-api/internettimeout-property-rds.md) , presente negli oggetti [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) e [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) . In questo caso, la proprietà **InternetTimeout** viene illustrata sull'oggetto **DataControl** e il timeout è impostato su 20 secondi.  
  
```cpp
// BeginInternetTimeoutCpp  
#import "c:\Program Files\Common Files\System\ADO\msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
#import "C:\Program Files\Common Files\System\MSADC\msadco.dll"  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
void InternetTimeOutX(void);  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//    Main Function                                     //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void main()  
{  
    if(FAILED(::CoInitialize(NULL)))  
        return;  
  
    InternetTimeOutX();  
  
    ::CoUninitialize();  
}  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//         InternetTimeOutX Function                    //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void InternetTimeOutX(void)   
{  
    HRESULT hr = S_OK;  
  
    // Define ADO object pointers.  
    // Initialize pointers on define.  
    // These are in the ADODB::  namespace.  
    _RecordsetPtr  pRst = NULL;  
  
    //Define RDS object pointers  
    RDS::IBindMgrPtr dc ;  
  
    try  
    {  
        TESTHR(dc.CreateInstance(__uuidof(RDS::DataControl)));  
        dc->Server = "https://MyServer";  
        dc->Connect = "Data Source='AuthorDatabase'";  
        dc->SQL = "SELECT * FROM Authors";  
  
        // Wait at least 20 seconds.  
        dc->InternetTimeout = 20000;  
        dc->Refresh();  
  
        // Use another Recordset as a convenience  
        pRst = dc->GetRecordset();  
        while(!(pRst->EndOfFile))  
        {  
            printf("%s %s",(LPSTR) (_bstr_t) pRst->Fields->  
                GetItem("au_fname")->Value,  
               (LPSTR) (_bstr_t) pRst->Fields->  
                GetItem("au_lname")->Value);  
  
            pRst->MoveNext();  
        }  
        pRst->Close();  
    }  
  
    catch (_com_error &e)  
    {  
        PrintProviderError(pRst->GetActiveConnection());  
        PrintComError(e);  
    }  
}  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//     PrintProviderError Function                      //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void PrintProviderError(_ConnectionPtr pConnection)  
{  
    // Print Provider Errors from Connection object.  
    // pErr is a record object in the Connection's Error collection.  
    ErrorPtr  pErr  = NULL;  
  
    if( (pConnection->Errors->Count) > 0)  
    {  
        long nCount = pConnection->Errors->Count;  
        // Collection ranges from 0 to nCount -1.  
        for(long i = 0; i < nCount; i++)  
        {  
            pErr = pConnection->Errors->GetItem(i);  
            printf("\t Error number: %x\t%s", pErr->Number,   
                pErr->Description);  
        }  
    }  
}  
  
//////////////////////////////////////////////////////////  
//                                                      //  
//     PrintComError Function                           //  
//                                                      //  
//////////////////////////////////////////////////////////  
  
void PrintComError(_com_error &e)  
{  
    _bstr_t bstrSource(e.Source());  
    _bstr_t bstrDescription(e.Description());  
  
    // Print Com errors.    
    printf("Error\n");  
    printf("\tCode = %08lx\n", e.Error());  
    printf("\tCode meaning = %s\n", e.ErrorMessage());  
    printf("\tSource = %s\n", (LPCSTR) bstrSource);  
    printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
// EndInternetTimeoutCpp  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà InternetTimeout (Servizi Desktop remoto)](../../../ado/reference/rds-api/internettimeout-property-rds.md)


