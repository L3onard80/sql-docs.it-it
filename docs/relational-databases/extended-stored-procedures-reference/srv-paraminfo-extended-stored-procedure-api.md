---
title: srv_paraminfo (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paraminfo
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
ms.openlocfilehash: 85efd235861522754cbcdc209d6cf28558907d76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68058768"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a>srv_paraminfo (API Stored procedure estesa)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce informazioni su un parametro. Questa funzione sostituisce le funzioni seguenti: [srv_paramtype](../../relational-databases/extended-stored-procedures-reference/srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](../../relational-databases/extended-stored-procedures-reference/srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](../../relational-databases/extended-stored-procedures-reference/srv-parammaxlen-extended-stored-procedure-api.md) e [srv_paramdata](../../relational-databases/extended-stored-procedures-reference/srv-paramdata-extended-stored-procedure-api.md). **srv_paraminfo** supporta i tipi di dati nei [tipi di dati](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md) e i dati di lunghezza zero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Handle per una connessione client.  
  
 *n*  
 Numero ordinale del parametro da impostare. Il primo parametro è 1.  
  
 *pbType*  
 Tipo di dati del parametro.  
  
 *pcbMaxLen*  
 Indicatore di misura relativo alla lunghezza massima del parametro.  
  
 *pcbActualLen*  
 Indicatore di misura relativo alla lunghezza effettiva del parametro. Il valore 0 (\**pcbActualLen* == 0) indica dati di lunghezza zero se **pfNull* è impostato su FALSE.  
  
 *pbData*  
 Puntatore al buffer per i dati di parametro. Se *pbData* non è NULL, l'API Stored procedure estesa scrive \**pcbActualLen* byte di dati in \**pbData*. Se *pbData* è NULL, non viene scritto alcun dato in \**pbData* ma la funzione restituisce \**pbType*, \**pcbMaxLen*, \**pcbActualLen* e **pfNull*. La memoria per questo buffer deve essere gestita dall'applicazione.  
  
 *pfNull*  
 Puntatore a un flag null. **pfNull* è impostato su true se il valore del parametro è null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Se le informazioni sul parametro vengono ottenute correttamente, viene restituito SUCCEED; in caso contrario, FAIL. Restituisce FAIL se non esiste una stored procedure remota corrente o se non è presente nessun parametro *n* della stored procedure remota.  
  
## <a name="remarks"></a>Osservazioni  
 **Nota sulla sicurezza** È necessario esaminare accuratamente il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento per i programmatori delle stored procedure estese](../../relational-databases/extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
  
  
