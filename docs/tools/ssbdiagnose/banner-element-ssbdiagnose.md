---
title: Banner (ssbdiagnose) elemento | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 26882b39f9f3dfdd8b565b02794ade0bf7cb65c0
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291498"
---
# <a name="banner-element-ssbdiagnose"></a>Elemento Banner (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Identifica l'utilità che ha generato il file di output XML di **ssbdiagnose** .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|attribute|Descrizione|  
|---------------|-----------------|  
|**title**|Identifica l'utilità che ha generato il file di output XML di **ssbdiagnose** .|  
|**product**|Identifica il prodotto che ha generato il file di output XML di **ssbdiagnose** .|  
|**version**|Identifica la versione dell'utilità che ha generato il file XML di output.|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Una volta per ogni file di output XML di **ssbdiagnose** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Elementi figlio**|Nessuna.|  
  
## <a name="example"></a>Esempio  
 Di seguito viene riportato un esempio di un elemento Banner.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
