---
title: Tipi di cursori (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], types
ms.assetid: 7cc01544-e814-403b-bbfe-a2750bf921bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 00c89272d121898b6ac5af75022344acf1dceb28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923850"
---
# <a name="types-of-cursors-ado"></a>Tipi di cursori (ADO)
Come regola generale, l'applicazione deve usare il cursore più semplice che fornisce l'accesso ai dati necessari. Ogni ulteriore caratteristica del cursore oltre le nozioni di base (di sola lettura, statica, a scorrimento, senza buffer) presenta una memoria del client, un carico di rete o le prestazioni. In molti casi, le opzioni predefinite del cursore generano un cursore più complesso rispetto a quello effettivamente necessario per l'applicazione.  
  
 La scelta del tipo di cursore dipende dalla modalità di utilizzo del set di risultati da parte dell'applicazione, nonché da diverse considerazioni sulla progettazione, incluse le dimensioni del set di risultati, la percentuale dei dati che è probabile utilizzare, la sensibilità alle modifiche dei dati e le prestazioni dell'applicazione requisiti.  
  
 Nella maggior parte dei casi, la scelta del cursore dipende dal fatto che sia necessario modificare o semplicemente visualizzare i dati:  
  
-   Se è sufficiente scorrere un set di risultati, ma non modificare i dati, usare un cursore [statico](../../../ado/guide/data/static-cursors.md) o di [sola trasmissione](../../../ado/guide/data/forward-only-cursors.md) .  
  
-   Se si dispone di un set di risultati di grandi dimensioni ed è necessario selezionare solo poche righe, utilizzare un cursore [Keyset](../../../ado/guide/data/keyset-cursors.md) .  
  
-   Se si desidera sincronizzare un set di risultati con aggiunte, modifiche ed eliminazioni recenti da parte di tutti gli utenti simultanei, utilizzare un cursore [dinamico](../../../ado/guide/data/dynamic-cursors.md) .  
  
 Anche se ogni tipo di cursore sembra essere distinto, tenere presente che questi tipi di cursore non sono molto diversi come il risultato delle caratteristiche e delle opzioni sovrapposte.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Cursori forward-only](../../../ado/guide/data/forward-only-cursors.md)  
  
-   [Cursori statici](../../../ado/guide/data/static-cursors.md)  
  
-   [Cursori keyset](../../../ado/guide/data/keyset-cursors.md)  
  
-   [Cursori dinamici](../../../ado/guide/data/dynamic-cursors.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori di sola trasmissione](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursori statici](../../../ado/guide/data/static-cursors.md)   
 [Cursori keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Cursori dinamici](../../../ado/guide/data/dynamic-cursors.md)
