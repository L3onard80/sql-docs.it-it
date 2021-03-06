---
title: RENAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2019
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 0907cfd9-33a6-4fa6-91da-7d6679fee878
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 624131beece632cffd13bde3d6ad378f67b3a340
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68141266"
---
# <a name="rename-transact-sql"></a>RENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Rinomina una tabella creata dall'utente in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Rinomina una tabella o un database creato dall'utente in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].

> [!NOTE]
> Per rinominare un database in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], usare [ALTER DATABASE (Azure SQL Data Warehouse](alter-database-transact-sql.md?view=aps-pdw-2016-au7). Per rinominare un database nel database SQL di Azure, usare l'istruzione [ALTER DATABASE (database SQL di Azure)](alter-database-transact-sql.md?view=azuresqldb-mi-current). Per rinominare un database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], usare la stored procedure [sp_renamedb](../../relational-databases/system-stored-procedures/sp-renamedb-transact-sql.md).

## <a name="syntax"></a>Sintassi

```
-- Syntax for Azure SQL Data Warehouse

-- Rename a table.
RENAME OBJECT [::] [ [ database_name . [schema_name ] ] . ] | [schema_name . ] ] table_name TO new_table_name
[;]

```

```
-- Syntax for Analytics Platform System

-- Rename a table
RENAME OBJECT [::] [ [ database_name . [ schema_name ] . ] | [ schema_name . ] ] table_name TO new_table_name
[;]

-- Rename a database
RENAME DATABASE [::] database_name TO new_database_name
[;]
```

## <a name="arguments"></a>Argomenti

RENAME OBJECT [::] [ [*database_name* . [ *schema_name* ]. ] | [ *schema_name*. ] ]*table_name* TO *new_table_name*
**SI APPLICA A:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Modifica il nome di una tabella definita dall'utente. Specificare la tabella da rinominare con un nome in una, due o tre parti. Specificare il nome *new_table_name* della nuova tabella come nome in una parte.

RENAME DATABASE [::] [ *database_name* TO *new_database_name*
**SI APPLICA A:** [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Modifica il nome di un database definito dall'utente da *database_name* a *new_database_name*. Non è possibile rinominare un database con uno di questi nomi di database riservati di [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]:

- master
- model
- msdb
- tempdb
- pdwtempdb1
- pdwtempdb2
- DWConfiguration
- DWDiagnostics
- DWQueue

## <a name="permissions"></a>Autorizzazioni

Per eseguire questo comando, è necessaria questa autorizzazione:

- Autorizzazione **ALTER** per la tabella

## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni

### <a name="cannot-rename-an-external-table-indexes-or-views"></a>Non è possibile rinominare tabelle, indici e viste esterne

Non è possibile rinominare tabelle, indici o viste esterne. Anziché rinominare la tabella, l'indice o la vista esterna, è possibile rilasciarla e quindi ricrearla con il nuovo nome.

### <a name="cannot-rename-a-table-in-use"></a>Non è possibile rinominare una tabella in uso

Non è possibile rinominare una tabella o un database mentre è in uso. Per la ridenominazione di una tabella è necessario un blocco esclusivo su di essa. Se la tabella è in uso, può essere necessario terminare le sessioni che la usano. Per terminare una sessione, è possibile usare il comando KILL. Usare KILL con cautela, poiché quando una sessione viene terminata, viene eseguito il rollback di tutte le operazioni di cui non è stato eseguito il commit. Le sessioni in SQL Data Warehouse sono caratterizzate dal prefisso 'SID'. Quando si richiama il comando KILL, includere il prefisso 'SID' e il numero della sessione. Questo esempio visualizza un elenco di sessioni attive o inattive e quindi termina la sessione 'SID1234'.

### <a name="views-are-not-updated"></a>Le viste non vengono aggiornate

Quando si rinomina un database, tutte le viste che usano il nome precedente non sono più valide. Questo comportamento vale per le viste sia all'interno che all'esterno del database. Se ad esempio il database delle vendite viene rinominato, le viste che contengono `SELECT * FROM Sales.dbo.table1` non sono più valide. Per risolvere questo problema, è possibile evitare di usare nomi in tre parti nelle viste o aggiornare le viste in modo che facciano riferimento al nuovo nome del database.

Quando si rinomina una tabella, le viste non vengono aggiornate in modo che facciano riferimento al nuovo nome di tabella. Tutte le viste, all'interno o all'esterno del database, che fanno riferimento al nome di tabella precedente non sono più valide. Per risolvere questo problema, è possibile aggiornare ogni vista in modo che faccia riferimento al nuovo nome della tabella.

## <a name="locking"></a>Blocco

La ridenominazione di una tabella acquisisce un blocco condiviso per l'oggetto DATABASE, un blocco condiviso per l'oggetto SCHEMA e un blocco esclusivo per la tabella.

## <a name="examples"></a>Esempi

### <a name="a-rename-a-database"></a>R. Rinominare un database

**SI APPLICA A:** solo [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Questo esempio rinomina il database definito dall'utente AdWorks in AdWorks2.

```sql
-- Rename the user defined database AdWorks
RENAME DATABASE AdWorks to AdWorks2;

```

 Quando si rinomina una tabella, tutti gli oggetti e tutte le proprietà associate alla tabella vengono aggiornati in modo che facciano riferimento al nuovo nome della tabella. Vengono aggiornati, ad esempio, le definizioni di tabella, gli indici, i vincoli e le autorizzazioni. Le viste non vengono aggiornate.

### <a name="b-rename-a-table"></a>B. Rinominare una tabella

**SI APPLICA A:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Questo esempio rinomina la tabella Customer in Customer1.

```sql
-- Rename the customer table
RENAME OBJECT Customer TO Customer1;

RENAME OBJECT mydb.dbo.Customer TO Customer1;
```

Quando si rinomina una tabella, tutti gli oggetti e tutte le proprietà associate alla tabella vengono aggiornati in modo che facciano riferimento al nuovo nome della tabella. Vengono aggiornati, ad esempio, le definizioni di tabella, gli indici, i vincoli e le autorizzazioni. Le viste non vengono aggiornate.

### <a name="c-move-a-table-to-a-different-schema"></a>C. Spostare una tabella in un altro schema

**SI APPLICA A:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Se si intende spostare l'oggetto in un altro schema, usare [ALTER SCHEMA](../../t-sql/statements/alter-schema-transact-sql.md). L'istruzione seguente, ad esempio, sposta l'elemento tabella dallo schema product allo schema dbo.

```sql
ALTER SCHEMA dbo TRANSFER OBJECT::product.item;
```

### <a name="d-terminate-sessions-before-renaming-a-table"></a>D. Terminare le sessioni prima di rinominare una tabella

**SI APPLICA A:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

È importante ricordare che non è possibile rinominare una tabella mentre è in uso. La ridenominazione di una tabella richiede un blocco esclusivo su di essa. Se la tabella è in uso, può essere necessario terminare le sessioni che la usano. Per terminare una sessione, è possibile usare il comando KILL. Usare KILL con cautela, poiché quando una sessione viene terminata, viene eseguito il rollback di tutte le operazioni di cui non è stato eseguito il commit. Le sessioni in SQL Data Warehouse sono caratterizzate dal prefisso 'SID'. Quando si richiama il comando KILL, è necessario includere il prefisso 'SID' e il numero della sessione. Questo esempio visualizza un elenco di sessioni attive o inattive e quindi termina la sessione 'SID1234'.

```sql
-- View a list of the current sessions
SELECT session_id, login_name, status
FROM sys.dm_pdw_exec_sessions
WHERE status='Active' OR status='Idle';

-- Terminate a session using the session_id.
KILL 'SID1234';
```