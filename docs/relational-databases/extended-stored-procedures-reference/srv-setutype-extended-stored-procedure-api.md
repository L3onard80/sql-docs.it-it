---
title: srv_setutype (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- srv_setutype
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 033d575a0f34428558e3ef56968ac1a705613d14
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803459"
---
# <a name="srvsetutype-extended-stored-procedure-api"></a>srv_setutype (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Imposta il tipo di dati definito dall'utente per una colonna di una riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *column*  
 Indica quale colonna impostare. Le colonne sono numerate a partire da 1.  
  
 *user_type*  
 Specifica il codice del tipo di dati definito dall'utente.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL. Restituisce FAIL se la colonna non esiste.  
  
## <a name="remarks"></a>Remarks  
 In una colonna sono presenti due tipi di dati: il tipo di dati effettivo e il tipo di dati definito dall'utente. Il tipo di dati definito dall'utente è usato da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per archiviare il tipo di dati definito dall'utente effettivo della colonna, se presente, e informazioni di descrizione della colonna, ad esempio il supporto di valori Null e l'aggiornabilità.  
  
 La funzione **srv_setutype** può essere chiamata in qualsiasi momento in cui *column* è stato definito con **srv_describe** e prima che sia stata inviata l'ultima riga.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_describe &#40;API Stored procedure estesa&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
