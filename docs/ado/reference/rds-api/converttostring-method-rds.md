---
title: Esempio di metodo ConvertToString (Servizi Desktop remoto) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 426fd1fdcd3931981037b346b048de816e8596d0
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600291"
---
# <a name="converttostring-method-rds"></a>Metodo ConvertToString (Servizi Desktop remoto)
Converte un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) a una stringa MIME che rappresenta i dati del recordset.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Data factory*  
 Una variabile oggetto che rappresenta un' [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto.  
  
 *Recordset*  
 Una variabile oggetto che rappresenta un **Recordset** oggetto.  
  
## <a name="remarks"></a>Note  
 Con i file ASP, usare **ConvertToString** per incorporare le **Recordset** in una pagina HTML generata nel server per il trasporto in un computer client.  
  
 **ConvertToString** carica innanzitutto il **Recordset** nel servizio del cursore nelle tabelle e quindi genera un flusso in formato MIME.  
  
 Sul client, il servizio dati remoto può convertire la stringa MIME nuovamente in completamente funzionante **Recordset**. Funziona anche per la gestione di meno di 400 righe di dati con non più di larghezza 1024 byte per riga. È consigliabile non utilizzarlo per lo streaming dei dati BLOB e di set di risultati di grandi dimensioni tramite HTTP. Nessuna compressione in transito viene eseguita su stringa, in modo molto grandi set di dati richiederà molto tempo al trasporto su HTTP rispetto al formato wire ottimizzato viene definiti e distribuiti dal servizio dati remoto come il formato di protocollo di trasporto nativi.  
  
> [!NOTE]
>  Se si usa Active Server Pages per incorporare la stringa MIME risultante in una pagina HTML client, tenere presente che le versioni precedenti alla versione 2.0 di VBScript limitano la dimensione della stringa di 32 KB. Se questo limite viene superato, viene restituito un errore. Mantenere relativamente ridotto nell'ambito della query quando si usa incorporamento MIME tramite file ASP. Per risolvere questo problema, scaricare la versione più recente di VBScript dal sito Web di Microsoft Windows Script Technologies.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo ConvertToString (VB)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [Esempio di metodo ConvertToString (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


