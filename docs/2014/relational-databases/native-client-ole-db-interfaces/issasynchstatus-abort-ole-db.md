---
title: 'ISSAsynchStatus:: Abort (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b61f5e3e44f9584fc3f93efb521585e3173b6c1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62638717"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
  Annulla un'operazione di esecuzione asincrona.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Abort(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hChapter*[in]  
 Handle del capitolo per il quale interrompere l'operazione. Se l'oggetto chiamato non è un oggetto set di righe o l'operazione non è valida per un capitolo, il chiamante deve impostare *hChapter* su DB_NULL_HCHAPTER.  
  
 *eOperation*[in]  
 Operazione da interrompere. Deve corrispondere al valore seguente:  
  
 DBASYNCHOP_OPEN: la richiesta di annullamento si applica all'apertura o al popolamento asincrono di un set di righe o all'inizializzazione asincrona di un oggetto origine dati.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 S_OK  
 La richiesta di annullare l'operazione asincrona è stata elaborata. Questo non garantisce che l'operazione stessa sia stata annullata. Per determinare se è stata effettivamente annullata, il consumer deve chiamare [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) e verificare DB_E_CANCELED. È tuttavia possibile che non venga restituito nella chiamata successiva.  
  
 DB_E_CANTCANCEL  
 Non è stato possibile annullare l'operazione asincrona.  
  
 DB_E_CANCELED  
 La richiesta di interrompere l'operazione asincrona è stata annullata durante le notifiche. L'operazione viene ancora eseguita in modo asincrono.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider.  
  
 E_INVALIDARG  
 Il parametro *hChapter* non è DB_NULL_HCHAPTER o *eOperation* non è DBASYNCH_OPEN.  
  
 E_UNEXPECTED  
 **ISSAsynchStatus:: Abort** è stato chiamato su un oggetto origine dati su cui **IDBInitialize:: Initialize** non è stato chiamato oppure non è stato completato.  
  
 **ISSAsynchStatus:: Abort** è stato chiamato su un oggetto origine dati su cui **IDBInitialize:: Initialize** è stato chiamato ma successivamente annullato prima dell'inizializzazione o si è verificato un timeout. L'oggetto origine dati non è ancora inizializzato.  
  
 **ISSAsynchStatus:: Abort** è stato chiamato su un set di righe su cui è stato precedentemente chiamato **ITransaction:: commit** o **ITransaction:: Abort** e il set di righe non è sopravvissuto al commit o all'interruzione ed è in uno stato non valido.  
  
 **ISSAsynchStatus:: Abort** è stato chiamato su un set di righe annullato in modo asincrono nella fase di inizializzazione. Il set di righe si trova in uno stato non valido.  
  
## <a name="remarks"></a>Osservazioni  
 L'interruzione dell'inizializzazione di un set di righe o di un oggetto origine dati potrebbe lasciare il set di righe o l'oggetto origine dati in uno stato non valido e determinare la restituzione di E_UNEXPECTED da parte di tutti i metodi ad eccezione di **IUnknown**. Quando ciò accade, l'unica azione possibile per il consumer consiste nel rilasciare il set di righe o l'oggetto origine dati.  
  
 Se si chiama **ISSAsynchStatus::Abort** e si passa un valore per *eOperation* diverso da DBASYNCHOP_OPEN, viene restituito S_OK. Questo non implica che l'operazione sia stata completata o annullata.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni asincrone](../native-client/features/performing-asynchronous-operations.md)  
  
  
