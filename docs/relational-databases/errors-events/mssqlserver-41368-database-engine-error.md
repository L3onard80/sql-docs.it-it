---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
robots: noindex,nofollow
ms.openlocfilehash: 66c836c80db24b951bbf4e53d77c975eea6e4832
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68123156"
---
# <a name="mssqlserver_41368"></a>MSSQLSERVER_41368
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41368|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|Testo del messaggio|L'accesso alle tabelle con ottimizzazione per la memoria utilizzando il livello di isolamento READ COMMITTED è supportato solo per transazioni in modalità autocommit. Non è invece supportato con le transazioni implicite o esplicite. Specificare un livello di isolamento supportato per la tabella con ottimizzazione per la memoria utilizzando un hint di tabella, ad esempio WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Spiegazione  
L'accesso alle tabelle ottimizzate per la memoria utilizzando il livello di isolamento READ COMMITTED è supportato solo per transazioni in modalità autocommit. Per altre informazioni, vedere [Transazioni con tabelle e procedure in memoria](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md).  
  
Quando si accede a una tabella ottimizzata per la memoria da una transazione esplicita avviata tramite un'istruzione BEGIN TRANSACTION o da una transazione implicita, se l'opzione IMPLICIT_TRANSACTIONS è impostata su ON, il livello di isolamento READ COMMITTED non è supportato.  
  
## <a name="user-action"></a>Azione dell'utente  
Quando si accede a una tabella ottimizzata per la memoria da una transazione esplicita o implicita READ COMMITTED, utilizzare l'istruzione SNAPSHOT per accedere alla tabella. A questo scopo, è possibile usare l'hint di tabella WITH (SNAPSHOT) (per altre informazioni, vedere [Transazioni con tabelle e procedure in memoria](~/relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)) o impostare l'opzione MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT del database su ON (per altre informazioni, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql.md)).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
