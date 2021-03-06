---
title: Comando DELETE TAG | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 576e7e10d9d6f5c7e8616f57bde2dfed05503eae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68112076"
---
# <a name="delete-tag-command"></a>DELETE TAG (comando)
Rimuove un tag o tag da un file di indice composto (con estensione CDX).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Argomenti  
 *TagName1* DI *CDXFileName1*[, *TagName2*[of *CDXFileName2*]]...  
 Specifica un tag da rimuovere da un file di indice composto. È possibile eliminare più tag con un TAG DELETE includendo un elenco di nomi di tag separati da virgole. Se nei file di indice aperti sono presenti due o più tag con lo stesso nome, è possibile rimuovere un tag da un file di indice specifico includendo *CDXFileName*.  
  
 ALL [di *CDXFileName*]  
 Rimuove ogni tag da un file di indice composto. Se la tabella corrente include un file di indice composto strutturale, tutti i tag vengono rimossi dal file di indice, il file di indice viene eliminato dal disco e il flag nell'intestazione della tabella che indica la presenza di un file di indice composto strutturale associato viene rimosso. Utilizzare ALL con di *CDXFileName* per rimuovere tutti i tag da un file di indice composto aperto diverso dal file di indice composto strutturale.  
  
## <a name="remarks"></a>Osservazioni  
 I file di indice composti creati con INDEX contengono tag corrispondenti alle voci di indice. Il TAG DELETE viene usato per rimuovere tag o tag da file di indice composti aperti. È possibile eliminare solo i tag dai file di indice composti aperti nell'area di lavoro corrente. Se si rimuovono tutti i tag da un file di indice composto, il file viene eliminato dal disco.  
  
 Visual FoxPro cerca innanzitutto un tag nel file di indice composto strutturale (se ne è aperto uno). Se il tag non è presente nel file di indice composto strutturale, Visual FoxPro Cerca il tag negli altri file di indice composti aperti.  
  
## <a name="see-also"></a>Vedere anche  
 [INDEX (comando)](../../odbc/microsoft/index-command.md)
