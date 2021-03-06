---
title: Cache della libreria di cursori | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 597abe268979852d754e2e3e86ae81daa8f3fed8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019071"
---
# <a name="cursor-library-cache"></a>Cache della libreria di cursori
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Microsoft consiglia di utilizzare la funzionalità di cursore del driver.  
  
 Per ogni riga di dati nel set di risultati, la libreria di cursori memorizza nella cache i dati per ogni colonna associata, la lunghezza dei dati in ogni colonna associata e lo stato della riga. La libreria di cursori utilizza i valori nella cache per restituire i valori tramite **SQLFetch** e **SQLFetchScroll** e per costruire istruzioni ricercate per le operazioni posizionate. Per ulteriori informazioni, vedere [creazione di istruzioni ricercate](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Dati della colonna](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Lunghezza dei dati di colonna](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [Stato riga](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Percorso della cache](../../../odbc/reference/appendixes/location-of-cache.md)
