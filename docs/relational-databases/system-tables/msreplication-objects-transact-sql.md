---
title: MSreplication_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 058e1948fa79ed2ba250a4f4d504f95201d1e254
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079086"
---
# <a name="msreplication_objects-transact-sql"></a>MSreplication_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La tabella **MSreplication_objects** contiene una riga per ogni oggetto associato alla replica nel database del Sottoscrittore. Questa tabella è archiviata nel database di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Nome del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**pubblicazione**|**sysname**|Nome della pubblicazione.|  
|**object_name**|**sysname**|Nome dell'oggetto .|  
|**object_type**|**carattere (2)**|Tipo di oggetto:<br /><br /> **u** = tabella.<br /><br /> **t** = trigger.<br /><br /> **p** = stored procedure.|  
|**articolo**|**sysname**|Nome dell'articolo a cui è associato l'oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
