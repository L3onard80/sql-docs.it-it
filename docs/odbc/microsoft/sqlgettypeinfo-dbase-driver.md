---
title: SQLGetTypeInfo (driver dBASE) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 43319f7f23741a1533321c9369077d42a2484395
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898744"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (driver dBASE)
> [!NOTE]  
>  In questo argomento vengono fornite informazioni specifiche del driver dBASE. Per informazioni generali su questa funzione, vedere l'argomento appropriato in informazioni di [riferimento sulle API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Il nome del tipo (TYPE_NAME) restituito nella tabella prodotta da **SQLGetTypeInfo** sarà il nome usato più di frequente dall'origine dati.  
  
 SQL_ALL_EXCEPT_LIKE verrà restituito nella colonna RICERCAbile per i tipi di dati byte, Counter, Double, Single, Long e short. Per ottenere la funzionalità LIKE, è possibile convertire il valore in un carattere usando le funzioni di conversione canoniche ODBC, quindi eseguire il confronto.
