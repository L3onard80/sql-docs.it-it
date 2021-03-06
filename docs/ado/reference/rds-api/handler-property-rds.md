---
title: Proprietà Handler (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a7423879b8263d87575d913c4863143faf3573e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963993"
---
# <a name="handler-property-rds"></a>Proprietà Handler (Servizi Desktop remoto)
Indica il nome di un programma di personalizzazione sul lato server (gestore) che estende la funzionalità di [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)ed eventuali parametri usati dal *gestore*.  
  
 **Si applica a:** [oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Variabile oggetto che rappresenta un Servizi Desktop remoto [. Oggetto DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *Stringa*  
 Valore **stringa** che contiene il nome del gestore e qualsiasi parametro, tutti separati da virgole (ad esempio, `"handlerName,parm1,parm2,...,parm` *N*`"`).  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà supporta la [personalizzazione](../../../ado/guide/remote-data-service/datafactory-customization.md), una funzionalità che richiede l'impostazione della proprietà [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) su **adUseClient**.  
  
 Il nome del gestore e i relativi parametri, se presenti, sono separati da virgole (","). Si otterrà un comportamento imprevedibile se un punto e virgola (";") viene visualizzato in qualsiasi punto all'interno della *stringa*. È possibile scrivere un gestore personalizzato, purché supporti l'interfaccia **IDataFactoryHandler** .  
  
 Il nome del gestore predefinito è **MSDFMAP. Il gestore**e il relativo parametro predefinito sono un file di personalizzazione denominato **MSDFMAP. INI**. Utilizzare questa proprietà per richiamare file di personalizzazione alternativi creati dall'amministratore del server.  
  
 L'alternativa all'impostazione della proprietà **handler** consiste nel specificare un gestore e i parametri nella proprietà [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) . ovvero "**handler =**_handlerName, parametro1, parametro2,...;_".  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Handler (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [Personalizzazione di datafactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


