---
title: SQLFetch (libreria di cursori) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2cb829f065421a13d3c7df06c670808bc3d9d77c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064429"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Microsoft consiglia di utilizzare la funzionalità di cursore del driver.  
  
 In questo argomento viene illustrato l'utilizzo della funzione **SQLFetch** nella libreria di cursori. Per informazioni generali su **SQLFetch**, vedere [funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Quando si utilizza la libreria di cursori, le chiamate a **SQLFetch** non possono essere combinate con chiamate a **SQLFetchScroll** o **SQLExtendedFetch**.  
  
 Se **SQLFetch** viene chiamato con SQL_ATTR_ROW_ARRAY_SIZE impostato su un valore maggiore di 1, la libreria di cursori passerà la chiamata al driver. Se il driver è ODBC 2. driver *x* , le dimensioni del set di righe verranno ignorate e la chiamata a **SQLFetch** restituirà una singola riga di dati.  
  
 Se la libreria di cursori viene utilizzata con ODBC 2. il driver *x* , un offset di binding (come definito dall'attributo dell'istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR) non viene usato quando viene chiamato **SQLFetch** .  
  
 Quando viene caricata la libreria di cursori, un'applicazione non può chiamare **SQLFetch** per recuperare le colonne dei segnalibri. La libreria di cursori passa la chiamata a **SQLFetch** tramite al driver, ma la funzione chiama per abilitare i segnalibri e associare la colonna del segnalibro intercettata dalla libreria di cursori.
