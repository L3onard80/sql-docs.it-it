---
title: srv_sendmsg (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_sendmsg
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
author: rothja
ms.author: jroth
ms.openlocfilehash: 62fa2db01ff17008a0b6a7cd4e5fd0a2bce71189
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67910910"
---
# <a name="srv_sendmsg-extended-stored-procedure-api"></a>srv_sendmsg (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Invia un messaggio al client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client, in questo caso l'handle che ha ricevuto la richiesta del linguaggio. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *MsgType*  
 SRV_MSG_INFO o SRV_MSG_ERROR, a seconda che il server invii un messaggio informativo o un messaggio di errore.  
  
 *msgnum*  
 Numero di messaggio a 4 byte.  
  
 *classe*  
 Specifica la gravità dell'errore. Un livello di gravità minore o uguale a 10 è considerato un messaggio informativo.  
  
 *state*  
 Fornisce il numero di contesto dell'errore per il messaggio corrente. Il numero di contesto dell'errore fornisce informazioni sul contesto dell'errore. I numeri di contesto validi sono compresi tra 0 e 255.  
  
 *rpcname*  
 Attualmente non supportato.  
  
 *rpcnamelen*  
 Attualmente non supportato.  
  
 *LineNum*  
 Numero di riga nel batch di comandi del linguaggio a cui è applicato il messaggio. I numeri di riga partono da 1. Se *linenum* non si applica al messaggio, viene impostato su 0.  
  
 *Messaggio*  
 Puntatore alla stringa di caratteri da inviare al client.  
  
 *msglen*  
 Specifica la lunghezza, espressa in byte, di *message*. Se *message* è con terminazione Null, impostare *msglen* su SRV_NULLTERM.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione invia messaggi informativi o di errore al client. Viene chiamata una volta per ogni messaggio da inviare.  
  
 I messaggi possono essere inviati al client con **srv_sendmsg** in qualsiasi ordine prima o dopo l'invio di tutte le righe, se presenti, con **srv_sendrow**. Tutti i messaggi, se presenti, devono essere inviati al client prima dell'invio dello stato di completamento con **srv_senddone**.  
  
 Per inviare i messaggi in Unicode, usare **srv_wsendmsg** anziché **srv_sendmsg**.  
  
 Per ulteriori informazioni [, vedere dati Unicode e tabelle codici del server](../../relational-databases/extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
