---
title: sys. sp_cdc_disable_table (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_disable_table
- sp_cdc_disable_table
- sys.sp_cdc_disable_table_TSQL
- sp_cdc_disable_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_table
- sys.sp_cdc_disable_table
- change data capture [SQL Server], disabling tables
ms.assetid: da2156c0-504e-4d76-b9a0-4448becf9bda
author: rothja
ms.author: jroth
ms.openlocfilehash: 693c449679433b733cfc3a45e2bbedf3f1d92185
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106514"
---
# <a name="syssp_cdc_disable_table-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Disabilita Change Data Capture per la tabella di origine e l'istanza di acquisizione specificate nel database corrente. Change Data Capture non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @source_schema = ] 'source\_schema'`Nome dello schema in cui è contenuta la tabella di origine. *source_schema* è di **tipo sysname**e non prevede alcun valore predefinito e non può essere null.  
  
 *source_schema* deve esistere nel database corrente.  
  
`[ @source_name = ] 'source\_name'`Nome della tabella di origine da cui Change Data Capture deve essere disabilitato. *source_name* è di **tipo sysname**e non prevede alcun valore predefinito e non può essere null.  
  
 *source_name* deve esistere nel database corrente.  
  
`[ @capture_instance = ] 'capture\_instance' | 'all'`Nome dell'istanza di acquisizione da disabilitare per la tabella di origine specificata. *capture_instance* è di **tipo sysname** e non può essere null.  
  
 Quando si specifica ' all', tutte le istanze di acquisizione definite per *source_name* sono disabilitate.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sys. sp_cdc_disable_table** Elimina la tabella delle modifiche Change Data Capture e le funzioni di sistema associate alla tabella di origine e all'istanza di acquisizione specificate. Elimina tutte le righe associate all'istanza di acquisizione specificata dalle tabelle di sistema Change Data Capture e imposta la colonna **is_tracked_by_cdc** per la voce della tabella nella vista del catalogo [sys. Tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) su 0.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del database **db_owner** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene disabilitata l'acquisizione dei dati delle modifiche per la tabella `HumanResources.Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_table   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee',  
    @capture_instance = N'HumanResources_Employee';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys. sp_cdc_enable_table &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
