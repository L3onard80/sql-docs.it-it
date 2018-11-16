---
title: Sys. change_tracking_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- change_tracking_databases
- sys.change_tracking_databases_TSQL
- sys.change_tracking_databases
- change_tracking_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.change_tracking_databases
- change tracking [SQL Server], sys.change_tracking_databases
ms.assetid: bb233baa-2991-4904-a0eb-3772b81121a4
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 984f9f2796edf1012e852d014e94ed6f6a6f7d57
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667272"
---
# <a name="change-tracking-catalog-views---syschangetrackingdatabases"></a>Modificare viste del catalogo di rilevamento - Sys. change_tracking_databases
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni database con il rilevamento delle modifiche abilitato.  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database. È univoco all'interno dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_auto_cleanup_on|**bit**|Indica se i dati di rilevamento delle modifiche vengono rimossi automaticamente una volta trascorso il periodo di memorizzazione configurato:<br /><br /> 0 = Off<br /><br /> 1 = On|  
|retention_period|**int**|Se si utilizza la rimozione automatica, il periodo di memorizzazione specifica per quanto tempo i dati di rilevamento delle modifiche verranno conservati nel database.|  
|retention_period_units_desc|**nvarchar(60)**|Specifica la descrizione del periodo memorizzazione:<br /><br /> Minutes<br /><br /> Ore<br /><br /> Giorni|  
|retention_period_units|**tinyint**|Unità di tempo relativa al periodo di memorizzazione:<br /><br /> 1 = Minuti<br /><br /> 2 = Ore<br /><br /> 3 = Giorni|  
  
## <a name="permissions"></a>Permissions  
 Gli stessi controlli dell'autorizzazione vengono effettuati per sys.change_tracking_databases, così come per sys.databases. Se il chiamante di sys.change_tracking_databases non è il proprietario del database, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono ALTER ANY DATABASE o VIEW ANY DATABASE a livello di server, oppure l'autorizzazione CREATE DATABASE nel database master o corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di rilevamento delle modifiche &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
