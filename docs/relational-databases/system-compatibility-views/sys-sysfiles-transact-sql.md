---
title: sys. sysfiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysfiles
- sys.sysfiles_TSQL
- sys.sysfiles
- sysfiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysfiles system table
- sys.sysfiles compatibility view
ms.assetid: 3b47f38d-1cff-404d-89d3-9342c451c802
author: rothja
ms.author: jroth
ms.openlocfilehash: 2a3554e254be0623e36719fe76b2d811908a939d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053473"
---
# <a name="syssysfiles-transact-sql"></a>sys.sysfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni file di un database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Numero di identificazione del file, univoco per ogni database.|  
|**GroupID**|**smallint**|Numero di identificazione del filegroup.|  
|**dimensioni**|**int**|Dimensioni del file in pagine da 8 KB.|  
|**MaxSize**|**int**|Dimensioni massime del file espresse in pagine da 8 KB.<br /><br /> 0 = Nessun aumento.<br /><br /> -1 = La dimensione del file aumenterà finché il disco è pieno.<br /><br /> 268435456 = La dimensione del file di log aumenterà fino al valore massimo di 2 TB.<br /><br /> Nota: i database aggiornati con una dimensione di file di log illimitata segnaleranno-1 per le dimensioni massime del file di log.|  
|**growth**|**int**|Aumento delle dimensioni del database. Può essere il numero di pagine o la percentuale di dimensioni del file, a seconda del valore dello **stato**.<br /><br /> 0 = Nessun aumento.|  
|**stato**|**int**|Bit di stato per il valore di **crescita** in megabyte (MB) o KILOBYTE (KB).<br /><br /> 0x2 = File del disco.<br /><br /> 0x40 = File di log.<br /><br /> 0x100000 = Aumento. Questo valore indica una percentuale e non il numero di pagine.|  
|**prestazioni**|**int**|Riservato.|  
|**nome**|**sysname**|Nome logico del file.|  
|**filename**|**nvarchar(260)**|Nome del dispositivo fisico, incluso il percorso completo del file.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste di compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
