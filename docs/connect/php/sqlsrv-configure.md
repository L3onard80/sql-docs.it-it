---
title: sqlsrv_configure | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_configure
apitype: NA
helpviewer_keywords:
- sqlsrv_configure
- API Reference, sqlsrv_configure
ms.assetid: 9393f975-a4ef-4c50-b4dd-14892fc55cc9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98c3848ad344fcbb964d1b3a5e9ec1a6afe8703f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618690"
---
# <a name="sqlsrvconfigure"></a>sqlsrv_configure
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Modifica le impostazioni delle opzioni di registrazione e gestione degli errori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_configure( string $setting, mixed $value )  
```  
  
#### <a name="parameters"></a>Parametri  
*$setting*: nome dell'impostazione da configurare. Vedere la tabella seguente per un elenco di impostazioni.  
  
*$value*: valore da applicare all'impostazione specificata nel parametro *$setting* . I valori possibili per questo parametro dipendono dall'impostazione specificata. Nella tabella seguente sono elencate le combinazioni possibili:  
  
|Impostazione|Valori possibili per il parametro $value (equivalente Integer tra parentesi)|Valore predefinito|  
|-----------|------------------------------------------------------------------------------|-----------------|  
|ClientBufferMaxKBSize<sup>1</sup>|Numero non negativo fino al limite di memoria PHP.<br /><br />Lo zero e i numeri negativi non sono consentiti.|10240 KB|  
|LogSeverity<sup>2</sup>|SQLSRV_LOG_SEVERITY_ALL (-1)<br /><br />SQLSRV_LOG_SEVERITY_ERROR (1)<br /><br />SQLSRV_LOG_SEVERITY_NOTICE (4)<br /><br />SQLSRV_LOG_SEVERITY_WARNING (2)|SQLSRV_LOG_SEVERITY_ERROR (1)|  
|LogSubsystems<sup>2</sup>|SQLSRV_LOG_SYSTEM_ALL (-1)<br /><br />SQLSRV_LOG_SYSTEM_CONN (2)<br /><br />SQLSRV_LOG_SYSTEM_INIT (1)<br /><br />SQLSRV_LOG_SYSTEM_OFF (0)<br /><br />SQLSRV_LOG_SYSTEM_STMT (4)<br /><br />SQLSRV_LOG_SYSTEM_UTIL (8)|SQLSRV_LOG_SYSTEM_OFF (0)|  
|WarningsReturnAsErrors<sup>3</sup>|**true** (1) o **false** (0)|**true** (1)|  
  
## <a name="return-value"></a>Valore restituito  
Se viene eseguita una chiamata a **sqlsrv_configure** con un'impostazione o un valore non supportato, la funzione restituisce **false**. In caso contrario, la funzione restituisce **true**.  
  
## <a name="remarks"></a>Remarks  
(1) Per altre informazioni sulle query lato client, vedere [Tipi di cursore &#40;driver SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md).  
  
(2) Per altre informazioni sull'attività di registrazione, vedere [Attività di registrazione](../../connect/php/logging-activity.md).  
  
(3) Per altre informazioni sulla configurazione della gestione degli errori e degli avvisi, vedere [Procedura: Configurare la gestione degli errori e degli avvisi usando il driver SQLSRV](../../connect/php/how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver.md).  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md) 
  
