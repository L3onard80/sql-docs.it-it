---
title: Oggetti origine dati (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b602695720e0d6567e44e4fbe8fd06b6d496a6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63130593"
---
# <a name="data-source-objects-ole-db"></a>Oggetti origine dati (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client usa il termine origine dati per il set di interfacce di OLE DB utilizzate per stabilire un collegamento a un archivio dati, ad [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]esempio. La creazione di un'istanza dell'oggetto origine dati del provider è la prima attività di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer di Native Client.  
  
 Ogni provider OLE DB dichiara un identificatore di classe (CLSID) per se stesso. Il CLSID per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider di OLE DB di Native Client è il GUID C/C++ CLSID_SQLNCLI10 (il simbolo SQLNCLI_CLSID verrà risolto nel ProgID corretto nel file sqlncli. h a cui si fa riferimento). Con il CLSID, il consumer usa la funzione OLE **CoCreateInstance** per produrre un'istanza dell'oggetto origine dati.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client è un server in-process. Le istanze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di Native client OLE DB oggetti provider vengono creati utilizzando la macro CLSCTX_INPROC_SERVER per indicare il contesto eseguibile.  
  
 L' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto origine dati del provider OLE DB di Native Client espone le interfacce di inizializzazione OLE DB che consentono al consumer di connettersi ai database esistenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Ogni connessione effettuata tramite il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider di OLE DB di Native Client imposta automaticamente queste opzioni:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Questo esempio usa la macro identificatore di classe per creare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un oggetto origine dati del provider OLE DB di Native client e ottenere un riferimento all'interfaccia **IDBInitialize** .  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 Con la corretta creazione di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un oggetto origine dati del provider OLE DB di Native client, l'applicazione consumer può continuare inizializzando l'origine dati e creando sessioni. Le sessioni OLE DB presentano le interfacce che consentono l'accesso ai dati e la relativa modifica.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider di OLE DB di Native client effettua la prima connessione a un'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificata di come parte di un'inizializzazione dell'origine dati completata correttamente. La connessione viene mantenuta a condizione che venga mantenuto un riferimento in una delle interfacce di inizializzazione dell'origine dati o fino a quando non viene chiamato il metodo **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Proprietà dell'origine dati &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Proprietà delle informazioni sulle origini dati](data-source-information-properties.md)  
  
-   [Proprietà di inizializzazione e di autorizzazione](initialization-and-authorization-properties.md)  
  
-   [Sessioni](sessions.md)  
  
-   [Proprietà di sessione](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Oggetti origine dati persistenti](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
