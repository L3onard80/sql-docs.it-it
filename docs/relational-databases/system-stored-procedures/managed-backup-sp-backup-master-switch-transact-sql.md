---
title: sp_backup_master_switch (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
- sp_ backup_master_switch_TSQL
- smart_admin.sp_backup_master_switch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
ms.assetid: 1ed2b2b2-c897-41cc-bed5-1c6bc47b9dd2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a575a83d0e41dfb39dae33040d367188c4ce2200
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50099672"
---
# <a name="managedbackupspbackupmasterswitch-transact-sql"></a>sp_backup_master_switch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Sospende o riprende il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 Utilizzare questa stored procedure per sospendere temporaneamente e riprendere il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Ciò assicura che tutte le impostazioni di configurazione vengano conservate e mantenute quando riprendono le operazioni. Quando il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] viene sospeso, il periodo di conservazione non viene applicato. Ciò significa che non sono presenti controlli per determinare se i file devono essere eliminati dall'archiviazione o se sono presenti file di backup danneggiati o un'interruzione nella catena di log.  
  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
EXEC managed_backup.sp_backup_master_switch   
                     [@new_state = ] { 0 | 1}  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @state  
 Imposta lo stato del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Il @state parametro è **BIT**. Quando è impostato su un valore pari a 0, le operazioni vengono sospese e quando è impostato su un valore pari a 1, le operazioni riprendono.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="security"></a>Sicurezza  
 Vengono descritti i problemi di sicurezza relativi all'istruzione. Includere le autorizzazioni come sottosezione (titolo H3). Provare a includere altre sottosezioni per il concatenamento di proprietà e il controllo, se appropriate.  
  
### <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** autorizzazioni, e **EXECUTE** autorizzazioni sul **sp_delete BackupHistory**stored procedure.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente può essere utilizzato per sospendere il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nell'istanza in cui viene eseguito:  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
 L'esempio seguente può essere utilizzato per riprendere il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=1;  
Go  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Backup gestito di SQL Server in Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
