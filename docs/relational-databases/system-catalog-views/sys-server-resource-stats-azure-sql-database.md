---
title: sys. server_resource_stats (database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.service: sql-database
ms.reviewer: carlrab, edmaca
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||=sqlallproducts-allversions
ms.openlocfilehash: 72e363b05e8f14dda535abd70e4218c949c42c91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133065"
---
# <a name="sysserver_resource_stats-azure-sql-database"></a>sys. server_resource_stats (database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Restituisce l'utilizzo della CPU, l'i/o e i dati di archiviazione per un Istanza gestita SQL di Azure. I dati vengono raccolti e aggregati per intervalli di cinque minuti. Una riga viene segnalata ogni 15 secondi. I dati restituiti includono l'utilizzo della CPU, le dimensioni di archiviazione, l'utilizzo di IO e lo SKU dell'istanza gestita. I dati cronologici vengono mantenuti per circa 14 giorni.

La vista **sys. server_resource_stats** ha definizioni diverse a seconda della versione dell'istanza gestita di SQL Azure a cui è associato il database. Prendere in considerazione queste differenze e le eventuali modifiche richieste dall'applicazione durante l'aggiornamento a una nuova versione del server.
 
  
 La tabella seguente descrive le colonne disponibili in un server v12:  
  
|Colonne|Tipo di dati|Descrizione|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime2**|Ora UTC che indica l'inizio dell'intervallo di Reporting di quindici secondi|  
|end_time|**datetime**|Ora UTC che indica la fine dell'intervallo di Reporting di quindici secondi|
|resource_type|Nvarchar (128)|Tipo di risorsa per cui vengono fornite le metriche|
|resource_name|nvarchar(128)|Nome della risorsa.|
|sku|nvarchar(128)|Istanza gestita livello di servizio dell'istanza. Di seguito sono indicati i valori possibili: <br><ul><li>Utilizzo generico</li></ul><ul><li>Business Critical</li></ul>|
|hardware_generation|nvarchar(128)|Identificatore di generazione hardware: come gen 4 o gen 5|
|virtual_core_count|INT|Rappresenta il numero di core virtuali per istanza (8, 16 o 24 in anteprima pubblica)|
|avg_cpu_percent|Decimal (5, 2)|Utilizzo medio del calcolo in percentuale del limite del livello di servizio Istanza gestita utilizzato dall'istanza. Viene calcolato come somma del tempo di CPU di tutti i pool di risorse per tutti i database nell'istanza e diviso per il tempo di CPU disponibile per tale livello nell'intervallo specificato.|
|reserved_storage_mb|bigint|Archiviazione riservata per istanza (quantità di spazio di archiviazione acquistata dal cliente per l'istanza gestita)|
|storage_space_used_mb|Decimal (18, 2)|Archiviazione usata da tutti i file di database dell'istanza gestita (inclusi i database utente e di sistema)|
|io_request|bigint|Numero totale di operazioni fisiche di i/o nell'intervallo|
|io_bytes_read|bigint|Numero di byte fisici letti nell'intervallo|
|io_bytes_written|bigint|Numero di byte fisici scritti nell'intervallo|

 
> [!TIP]  
>  Per ulteriori informazioni sui limiti e sui livelli di servizio, vedere gli argomenti [istanza gestita livelli di servizio](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tiers).  
    
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni per la connessione al database **Master** .  
  
## <a name="remarks"></a>Osservazioni  
 I dati restituiti da **sys. server_resource_stats** vengono espressi come il totale utilizzato in byte o megabyte (indicati in nomi di colonna) diversi da avg_cpu, espresso come percentuale dei limiti massimi consentiti per il livello di servizio o il livello di prestazioni in esecuzione.  
 
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i database che hanno una media di almeno l'80% di utilizzo del calcolo nell'ultima settimana.  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT resource_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.server_resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY resource_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>Vedere anche  
 [Livelli di servizio Istanza gestita](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tiers)
