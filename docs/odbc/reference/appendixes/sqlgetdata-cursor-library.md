---
title: SQLGetData (libreria di cursori) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5962882de08712dcff75790de7c58d69f965a3bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086378"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Microsoft consiglia di utilizzare la funzionalità di cursore del driver.  
  
 In questo argomento viene illustrato l'utilizzo della funzione **SQLGetData** nella libreria di cursori. Per informazioni generali su **SQLGetData**, vedere [funzione SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md).  
  
 La libreria di cursori implementa **SQLGetData** costruendo prima un'istruzione **Select** con una clausola **where** che enumera i valori archiviati nella cache per ogni colonna associata nella riga corrente. Viene quindi eseguita l'istruzione **Select** per riselezionare la riga e viene chiamato **SQLGetData** nel driver per recuperare i dati dall'origine dati, anziché dalla cache.  
  
> [!CAUTION]  
>  La clausola **where** costruita dalla libreria di cursori per identificare la riga corrente può non essere in grado di identificare le righe, identificare una riga diversa o identificare più di una riga. Per ulteriori informazioni, vedere [creazione di istruzioni ricercate](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 Se l'attributo SQL_ATTR_USE_BOOKMARKS Statement è impostato su SQL_UB_VARIABLE, è possibile chiamare **SQLGetData** sulla colonna 0 per restituire i dati dei segnalibri.  
  
 Le chiamate a **SQLGetData** sono soggette alle restrizioni seguenti:  
  
-   Impossibile chiamare **SQLGetData** per i cursori di sola trasmissione.  
  
-   **SQLGetData** può essere chiamato solo quando vengono soddisfatte le condizioni seguenti: un'istruzione **SELECT** ha generato il set di risultati. l'istruzione **Select** non contiene un join, una clausola **Union** o una clausola **Group by** ; e qualsiasi colonna che utilizza un alias o un'espressione nell'elenco di selezione non è associata a **SQLBindCol**.  
  
-   Se il driver supporta una sola istruzione attiva, la libreria di cursori Recupera il resto del set di risultati prima di eseguire l'istruzione **Select** e di chiamare **SQLGetData**.
