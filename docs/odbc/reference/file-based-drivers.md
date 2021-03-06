---
title: Driver basati su file | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 803da51c8507faa47f92b295d3749f00317bc413
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915379"
---
# <a name="file-based-drivers"></a>Driver basati su file
I driver basati su file vengono usati con origini dati, ad esempio dBASE, che non forniscono un motore di database autonomo per il driver da usare. Questi driver accedono direttamente ai dati fisici e devono implementare un motore di database per l'elaborazione di istruzioni SQL. Come procedura standard, i motori di database nei driver basati su file implementano il subset di ODBC SQL definito dal livello di conformità SQL minimo. per un elenco delle istruzioni SQL in questo livello di conformità, vedere [Appendice C: grammatica SQL](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Nel confronto di driver basati su file e DBMS, i driver basati su file sono più difficili da scrivere a causa del componente del motore di database, meno complicati da configurare perché non ci sono parti di rete e meno potenti perché poche persone hanno il tempo di scrivere il database motori potenti come quelli prodotti dalle società di database.  
  
 Nella figura seguente sono illustrate due diverse configurazioni di driver basati su file, una in cui i dati risiedono localmente e l'altro in cui si trovano in una rete file server.  
  
 ![Due configurazioni di driver basati su file&#45;](../../odbc/reference/media/pr06.gif "pr06")
