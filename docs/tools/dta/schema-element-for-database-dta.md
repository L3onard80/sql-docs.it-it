---
title: Elemento schema per Database (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1cfa944f7b86a0333c28832858e5b2c57d218531
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51292937"
---
# <a name="schema-element-for-database-dta"></a>Elemento Schema per Database (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Specifica lo schema del database che si desidera ottimizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta per l'elemento **Database** specificato nell'elemento **Server** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Database per Server &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**Elementi figlio**|[Elemento Name per Schema &#40;DTA&#41;](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [Elemento Table per Schema &#40;DTA&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Elemento Server &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
