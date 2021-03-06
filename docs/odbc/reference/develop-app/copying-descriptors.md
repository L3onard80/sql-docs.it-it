---
title: Copia di descrittori | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d41cd744d39113c556c4ee8bc17411b7992e596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002147"
---
# <a name="copying-descriptors"></a>Copia di descrittori
La funzione **SQLCopyDesc** viene chiamata per copiare i campi di un descrittore in un altro descrittore. I campi possono essere copiati solo in un descrittore dell'applicazione o in un oggetto dpi, ma non in un IRD. I campi possono essere copiati da qualsiasi tipo di descrittore. Vengono copiati solo i campi definiti per i descrittori di origine e di destinazione. **SQLCopyDesc** non copia il campo SQL_DESC_ALLOC_TYPE perché non è possibile modificare il tipo di allocazione di un descrittore. I campi copiati sovrascrivono i campi esistenti.  
  
 Un'istruzione ARD su un handle di istruzione può fungere da APD in un altro handle di istruzione. Questo consente a un'applicazione di copiare le righe tra le tabelle senza copiare i dati a livello di applicazione. A tale scopo, un descrittore di riga che descrive una riga recuperata di una tabella viene riutilizzato come descrittore di parametro per un parametro in un'istruzione INSERT. Per la riuscita dell'operazione, il tipo di informazioni di SQL_MAX_CONCURRENT_ACTIVITIES deve essere maggiore di 1.
