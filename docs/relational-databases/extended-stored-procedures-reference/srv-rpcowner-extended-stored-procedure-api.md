---
title: srv_rpcowner (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_rpcowner
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f6ec4e8f0edb68f7a316ae695359f617e1b6b1dc
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677810"
---
# <a name="srvrpcowner-extended-stored-procedure-api"></a>srv_rpcowner (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce il componente proprietario per la stored procedure remota corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *len*  
 Puntatore a una variabile di tipo integer che riceve la lunghezza del nome del proprietario. Il parametro *len* può essere NULL. In tal caso, non viene restituita la lunghezza del componente proprietario.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Puntatore DBCHAR al componente proprietario con terminazione Null per la stored procedure remota corrente. Se non è presente alcuna stored procedure remota corrente, viene restituito NULL e *len* viene impostato su -1.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione restituisce solo il componente proprietario della stored procedure remota. Non include gli identificatori facoltativi per il nome, il nome della stored procedure remota e il numero della stored procedure remota.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
