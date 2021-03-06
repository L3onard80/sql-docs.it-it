---
title: sp_pdw_database_encryption (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 47d7aca62ddbf2637b54d77171a08817b842555c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008907"
---
# <a name="sp_pdw_database_encryption-sql-data-warehouse"></a>sp_pdw_database_encryption (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Usare **sp_pdw_database_encryption** per abilitare Transparent Data Encryption in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] per un'appliance. Quando **sp_pdw_database_encryption** impostato su 1, utilizzare l'istruzione **ALTER database** per crittografare un database tramite Transparent Data Encryption.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Parametri  
`[ @enabled = ] enabled`Determina se la crittografia trasparente dei dati è abilitata. *Enabled* è di **tipo int**. i possibili valori sono i seguenti:  
  
-   0 = Disabilitato  
  
-   1 = Attivato  
  
 L'esecuzione di **sp_pdw_database_encryption** senza parametri restituisce lo stato corrente di Transparent Data Encryption nell'appliance come set di risultati scalari: 0 per Disabled o 1 per Enabled.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Quando Transparent Data Encryption viene abilitato utilizzando **sp_pdw_database_encryption**, il database tempdb viene eliminato, ricreato e crittografato. Per questo motivo, non è possibile abilitare la funzionalità Transparent Data Encryption in un'appliance mentre sono presenti altre sessioni attive che usano tempdb. L'abilitazione o la disabilitazione di Transparent Data Encryption in un'appliance è un'azione che modifica lo stato dell'appliance, nella maggior parte dei casi dovrebbe essere eseguita una volta nella durata dell'appliance e deve essere eseguita quando non è presente traffico nell'appliance.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del database **sysadmin** o all'autorizzazione **Control Server** .  
  
## <a name="example"></a>Esempio  
 L'esempio seguente abilita Transparent Data Encryption nell'appliance.  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
