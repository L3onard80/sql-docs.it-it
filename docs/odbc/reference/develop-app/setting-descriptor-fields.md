---
title: Impostazione di campi del descrittore | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34c4a6e3d98b6711c77fb50d7156207de148881a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094251"
---
# <a name="setting-descriptor-fields"></a>Configurazione dei campi del descrittore
Per modificare i campi di un descrittore, un'applicazione può chiamare **SQLSetDescField**. Alcuni campi sono di sola lettura e non possono essere impostati. (Vedere la descrizione della funzione [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) ).  
  
 I campi del record del descrittore sono impostati con un numero di record (*RecNumber*) di 1 o superiore, mentre i campi di intestazione del descrittore sono impostati con un numero di record pari a 0. Un numero di record pari a 0 viene utilizzato anche per impostare i campi dei segnalibri, in base alla convenzione che i segnalibri sono contenuti nella colonna 0. Questo potrebbe lasciare l'impressione che i campi dei segnalibri siano contenuti all'interno dell'intestazione del descrittore, ma questo non è il caso. I campi segnalibro sono distinti dai campi di intestazione.  
  
 Quando si impostano i campi singolarmente, l'applicazione deve seguire la sequenza definita in [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). L'impostazione di alcuni campi determina l'impostazione di altri campi da parte del driver. In questo modo si garantisce che il descrittore sia sempre pronto per l'utilizzo dopo che l'applicazione ha specificato un tipo di dati. Quando l'applicazione imposta il campo SQL_DESC_TYPE, il driver verifica che altri campi che specificano il tipo siano validi e coerenti.  
  
 Se una chiamata di funzione che imposta un campo del descrittore ha esito negativo, il contenuto del campo del descrittore non è definito dopo la chiamata di funzione non riuscita.
