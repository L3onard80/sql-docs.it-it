---
title: MSpeer_lsns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_lsns
- MSpeer_lsns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_lsns system table
ms.assetid: 0ba33907-601b-4c3d-8099-2663f680a161
author: stevestein
ms.author: sstein
ms.openlocfilehash: c0d31de11ed7d41ecca409589f3daa25c85f1146
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085768"
---
# <a name="mspeer_lsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La tabella **Mspeer_lsns** viene utilizzata per eseguire il mapping di ogni transazione a una sottoscrizione in una topologia di replica peer-to-peer. Questa tabella è archiviata in tutti i database di pubblicazione in una topologia di replica peer-to-peer e nel database di sottoscrizione di tutti i Sottoscrittori di una pubblicazione peer-to-peer. Per ulteriori informazioni su questo tipo di topologia di replica transazionale, vedere [replica transazionale peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md). Questa tabella è archiviata nel database di pubblicazione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**ID**|**int**|Identifica un LSN peer-to-peer.|  
|**last_updated**|**datetime**|Data e ora in cui è stato eseguito l'ultimo **aggiornamento della riga** .|  
|**Creatore**|**sysname**|Nome del server di pubblicazione che ha avviato la transazione.|  
|**originator_db**|**sysname**|Nome del database in cui è stata avviata la transazione.|  
|**originator_publication**|**sysname**|Nome della pubblicazione in cui è stata avviata la transazione.|  
|**originator_publication_id**|**int**|ID della pubblicazione in cui è stata avviata la transazione.|  
|**originator_db_version**|**int**|Identifica il numero di versione del database di origine.|  
|**originator_lsn**|**int**|Identifica l'LSN nella pubblicazione di origine.|  
|**originator_version**|**int**|Identifica il numero di versione del server di pubblicazione.|  
|**originator_id**|**smallint**|Identifica ogni nodo nella topologia per consentire il rilevamento dei conflitti. Per altre informazioni, vedere [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
