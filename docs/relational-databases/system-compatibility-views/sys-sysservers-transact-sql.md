---
title: sys.sysservers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
author: rothja
ms.author: jroth
ms.openlocfilehash: 333be9cb6c86c1db3801ac50159610c6d19d1611
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68941105"
---
# <a name="syssysservers-transact-sql"></a>sys.sysservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni server accessibile come origine dati OLE DB da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**srvid**|**smallint**|ID del server remoto (solo per uso locale).|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**srvname**|**sysname**|Nome del server.|  
|**srvproduct**|**sysname**|Nome del prodotto del server remoto.|  
|**ProviderName**|**nvarchar(128)**|Nome del provider OLE DB per l'accesso al server.|  
|**DataSource**|**nvarchar(4000)**|Valore dell'origine dei dati OLE DB.|  
|**percorso**|**nvarchar(4000)**|Valore della posizione di OLE DB.|  
|**ProviderString**|**nvarchar(4000)**|Valore stringa del provider OLE DB.|  
|**schemadate**|**datetime**|Data dell'ultimo aggiornamento della riga.|  
|**topologyx**|**int**|Non usato.|  
|**topologia**|**int**|Non usato.|  
|**Catalogo**|**sysname**|Catalogo utilizzato quando viene stabilita una connessione a un provider OLE DB.|  
|**srvcollation**|**sysname**|Regole di confronto del server.|  
|**ConnectTimeout**|**int**|Impostazione del timeout per la connessione al server.|  
|**QueryTimeout**|**int**|Impostazione del timeout per le query eseguite sul server.|  
|**srvnetname**|**carattere (30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**IsRemote**|**bit**|1 = Server remoto.<br /><br /> 0 = Server collegato.|  
|**RPC**|**bit**|1 = **sp_serveroption\@RPC** è impostata su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@RPC** è impostata su **false** o **off**.|  
|**pub**|**bit**|1 = **sp_serveroption\@pubblicazione** è impostata su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@pubblicazione** è impostata su **false** o **off**.|  
|**Sub**|**bit**|1 = **sp_serveroption\@Sub** impostato su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@Sub** impostato su **false** o **off**.|  
|**dist**|**bit**|1 = **sp_serveroption\@dist** è impostata su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@dist** è impostata su **false** o **off**.|  
|**dpub**|**bit**|1 = **sp_serveroption\@dpub** impostato su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@dpub** è impostato su **false** o **off**.|  
|**RpcOut**|**bit**|1 = **sp_serveroption\@RPC out** impostata su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@RPC out** è impostata su **false** o **off**.|  
|**DataAccess**|**bit**|1 = **sp_serveroption\@accesso ai dati** impostato su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@l'accesso ai dati** è impostato su **false** o **off**.|  
|**collationcompatible**|**bit**|1 = **sp_serveroption\@la compatibilità delle regole di confronto** è impostata su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@la compatibilità delle regole di confronto** è impostata su **false** o **off**.|  
|**sistema**|**bit**|1 = **sp_serveroption\@sistema** impostato su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@sistema** è impostato su **false** o **off**.|  
|**useremotecollation**|**bit**|1 = **sp_serveroption\@regole di confronto remote** impostate su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@regole di confronto remote** impostate su **false** o **off**.|  
|**LazySchemaValidation**|**bit**|1 = **sp_serveroption\@convalida dello schema lazy** impostata su **true** o **on**.<br /><br /> 0 = **sp_serveroption\@la convalida dello schema lazy** è impostata su **false** o **off**.|  
|**confronto**|**sysname**|Regole di confronto del server impostate **per\@sp_serveroption nome delle regole di confronto**.|  
|**nonsqlsub**|bit|0 = il server è un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> 1 = il server non è un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste di compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
