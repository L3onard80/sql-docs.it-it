---
title: sys. sp_xtp_merge_checkpoint_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/28/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_merge_checkpoint_files_TSQL
- sys.sp_xtp_merge_checkpoint_files
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_merge_checkpoint_files
ms.assetid: da04df2a-f7a1-41e7-a1ef-2d5d68919892
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73638d41c7a24a37c068d365771b4d0469a174d5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041020"
---
# <a name="syssp_xtp_merge_checkpoint_files-transact-sql"></a>sys.sp_xtp_merge_checkpoint_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  **sys. sp_xtp_merge_checkpoint_files** unisce tutti i file di dati e differenziali nell'intervallo di transazioni specificato.  
  
 Per altre informazioni, vedere [creazione e gestione dell'archiviazione per gli oggetti con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
||  
|-|  
|**Nota**: questo stored procedure è deprecato in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Non è più necessario e non può essere usato, a partire [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]da.|  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_xtp_merge_checkpoint_files database_name, @transaction_lower_bound, @transaction_upper_bound  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database in cui richiamare l'unione. Se il database non include tabelle in memoria, questa stored procedure restituisce un errore utente. Se il database è offline, restituisce un errore.  
  
 *lower_bound_Tid*  
 Limite inferiore (BigInt) delle transazioni per un file di dati, come illustrato in [sys. dm_db_xtp_checkpoint_files &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md) corrispondenti al file del checkpoint iniziale dell'Unione. Viene generato un errore per un valore transactionId non valido.  
  
 *upper_bound_Tid*  
 Limite superiore (BigInt) delle transazioni per un file di dati, come illustrato in [sys. dm_db_xtp_checkpoint_files &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md). Viene generato un errore per un valore transactionId non valido.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 nessuno  
  
## <a name="cursors-returned"></a>Cursori restituiti  
 nessuno  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesto il ruolo predefinito del server sysadmin e il ruolo predefinito del database db_owner.  
  
## <a name="remarks"></a>Osservazioni  
 Unisce tutti i dati e i file differenziali nell'intervallo valido per produrre un singolo dato e un file differenziale. Questa stored procedure non rispetta i criteri di unione.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
