---
title: Record di diagnostica | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 90133b4a18876c52b9b6b6bffbe4c8c02c953e07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039884"
---
# <a name="diagnostic-records"></a>Record di diagnostica
Associate a ogni handle di ambiente, connessione, istruzione e descrittore sono *record di diagnostica*. Questi record contengono informazioni di diagnostica sull'ultima funzione chiamata che ha utilizzato un particolare handle. I record vengono sostituiti solo quando un'altra funzione viene chiamata usando tale handle. Non esiste un limite al numero di record di diagnostica che possono essere archiviati in qualsiasi momento.  
  
 Esistono due tipi di record di diagnostica: un *record di intestazione* e zero o più *record di stato*. Il record di intestazione è il record 0; i record di stato sono record 1 e versioni successive. I record di diagnostica sono composti da un numero di campi distinti, diversi per il record di intestazione e i record di stato. Inoltre, i componenti ODBC possono definire i propri campi dei record di diagnostica.  
  
 Sebbene i record di diagnostica possano essere considerati come strutture, non è necessario che siano effettivamente strutture. il modo in cui un driver archivia le informazioni di diagnostica è specifico del driver.  
  
 I campi nei record di diagnostica vengono recuperati con **SQLGetDiagField**. I campi SQLSTATE, numero di errore nativo e messaggio di diagnostica dei record di stato possono essere recuperati in una singola chiamata con **SQLGetDiagRec**.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Record di intestazione](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Record di stato](../../../odbc/reference/develop-app/status-records.md)
