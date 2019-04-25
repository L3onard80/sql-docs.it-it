---
title: dbo.sysjobstepslogs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobstepslogs_TSQL
- sysjobstepslogs_TSQL
- sysjobstepslogs
- dbo.sysjobstepslogs
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobstepslogs system table
ms.assetid: 128c25db-0b71-449d-bfb2-38b8abcf24a0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 537f40f96b70478833105d84960830469703565b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470766"
---
# <a name="dbosysjobstepslogs-transact-sql"></a>dbo.sysjobstepslogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene il log dei passaggi del processo per tutti i passaggi dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent configurati per la scrittura del relativo output in una tabella. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**log_id**|**int**|ID del log dei passaggi del processo.|  
|**log**|**nvarchar(max)**|Contenuto del log dei passaggi del processo.|  
|**date_created**|**datetime**|Data e ora di creazione del log dei passaggi del processo.|  
|**date_modified**|**datetime**|Data e ora dell'ultima modifica del log dei passaggi del processo.|  
|**log_size**|**int**|Dimensioni in byte del log dei passaggi del processo.|  
|**step_uid**|**uniqueidentifier**|ID univoco del passaggio del processo.|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)  
  
  
