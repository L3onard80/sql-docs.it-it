---
title: sp_helpfilegroup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fe9798b6a9f560621eba9806e25081f72e316c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122539"
---
# <a name="sp_helpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce i nomi e gli attributi dei filegroup associati al database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @filegroupname = ] 'name'`Nome logico di qualsiasi filegroup nel database corrente. *Name* è di **tipo sysname**e il valore predefinito è null. Se *nome* non è specificato, vengono elencati tutti i filegroup nel database corrente e viene visualizzato solo il primo set di risultati visualizzato nella sezione set di risultati.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**GroupName**|**sysname**|Nome del filegroup|  
|**GroupID**|**smallint**|Identificatore numerico del filegroup.|  
|**FileCount**|**int**|Numero di file del filegroup.|  
  
 Se si specifica *Name* , viene restituita una riga per ogni file nel filegroup.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Nome logico del file nel filegroup.|  
|**fileid**|**smallint**|Identificatore numerico del file.|  
|**filename**|**nchar (260)**|Nome fisico del file che include il percorso di directory.|  
|**dimensioni**|**nvarchar (15)**|Dimensione del file in kilobyte.|  
|**MaxSize**|**nvarchar (15)**|Dimensione massima del file.<br /><br /> Valore massimo fino a cui possono aumentare le dimensioni del file. Se questo campo include il valore UNLIMITED, le dimensioni del file possono aumentare fino a riempire il disco.|  
|**growth**|**nvarchar (15)**|Incremento per l'aumento delle dimensioni del file. Indica la quantità di spazio aggiunta al file ogni volta che è necessario spazio aggiuntivo.<br /><br /> 0 = la dimensione del file è fissa e non aumenterà.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>R. Restituzione di tutti i filegroup in un database  
 Nell'esempio seguente vengono restituite le informazioni sui filegroup nel database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>B. Restituzione di tutti i file in un filegroup  
 Nell'esempio seguente vengono restituite le informazioni relative a tutti i file nel filegroup `PRIMARY` nel database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di motore di database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. master_files &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys. filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Filegroup e file di database](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
