---
title: srv_paramset (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramset
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a91a80ea94b4ac4be9747f3327b843a5cbba4ed4
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032508"
---
# <a name="srvparamset-extended-stored-procedure-api"></a>srv_paramset (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Imposta il valore di un parametro restituito di chiamata a una stored procedure remota. Questa funzione è stata sostituita dalla funzione **srv_paramsetoutput**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la chiamata alla stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *n*  
 Indica il numero del parametro da impostare. Il primo parametro è 1.  
  
 *data*  
 Puntatore al valore dei dati da inviare di nuovo al client come parametro restituito della stored procedure remota.  
  
 *len*  
 Specifica la lunghezza effettiva dei dati da restituire. Se il tipo di dati del parametro ha una lunghezza costante e non consente valori Null (ad esempio, *srvbit* o *srvint1*), *len* viene ignorato.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED se il valore del parametro è stato impostato correttamente; in caso contrario, FAIL. Restituisce FAIL se non esiste una stored procedure remota corrente, se non è presente il parametro *n* della stored procedure remota, se il parametro non è un parametro restituito o se l'argomento *len* non è valido.  
  
 Se *len* è 0, restituisce NULL. L'impostazione di *len* su 0 è l'unico modo per restituire NULL al client.  
  
 Questa funzione restituisce i valori seguenti, se il parametro è uno dei tipi di dati di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
|Nuovi tipi di dati|Lunghezza dei dati restituiti|  
|--------------------|------------------------|  
|**BITN**|**NULL:** *len* = 0, data = IG, RET = 0<br /><br /> **ZERO:** N/D<br /><br /> **>=255:** N/D<br /><br /> **<255:** N/D|  
|**BIGVARCHAR**|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|**BIGCHAR**|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|**BIGBINARY**|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|**BIGVARBINARY**|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|NCHAR|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|NVARCHAR|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|**NTEXT**|**NULL:** *len* = IG, data = IG, RET = 0<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = IG, data = IG, RET = 0<br /><br /> **\<255:** *len* = IG, data = IG, RET = 0|  
|RET = valore restituito di srv_paramset||  
|IG = il valore verrà ignorato||  
|valid = qualsiasi puntatore valido ai dati||  
  
## <a name="remarks"></a>Remarks  
 I parametri contengono i dati passati tra i client e l'applicazione con stored procedure remote. Il client può specificare determinati parametri come parametri restituiti. Questi parametri restituiti possono contenere valori che l'applicazione del server Open Data Services passa nuovamente al client. L'utilizzo di parametri restituiti è analogo al passaggio di parametri per riferimento.  
  
 Non è possibile impostare il valore restituito per un parametro non richiamato come parametro restituito. È possibile usare **srv_paramstatus** per determinare la modalità di richiamo del parametro.  
  
 Questa funzione imposta il valore restituito per un parametro ma non lo invia effettivamente al client. Tutti i parametri restituiti, indipendentemente dal fatto che i relativi valori restituiti siano stati impostati con **srv_paramset**, vengono inviati automaticamente al client quando **srv_senddone** viene chiamato con il flag di stato SRV_DONE_FINAL impostato.  
  
 Quando viene effettuata una chiamata a una stored procedure remota con parametri, tali parametri possono essere passati per nome o per posizione (senza nome). Se invece viene effettuata con alcuni parametri passati per nome e altri passati per posizione, si verifica un errore. Il gestore SRV_RPC viene comunque chiamato, ma risulta che non sono presenti parametri e **srv_rpcparams** restituisce 0.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_paramsetoutput &#40;API Stored procedure estesa&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
