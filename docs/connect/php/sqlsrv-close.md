---
title: sqlsrv_close | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_close
apitype: NA
helpviewer_keywords:
- sqlsrv_close
- API Reference, sqlsrv_close
ms.assetid: 6ac6209c-a134-4f8f-b88b-8eefaa1cbc7f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b56cb6975f7fd7a4367912dcd5101271b611336
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806719"
---
# <a name="sqlsrvclose"></a>sqlsrv_close
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Chiude la connessione specificata e rilascia le risorse associate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_close( resource $conn )  
```  
  
#### <a name="parameters"></a>Parametri  
*$conn*: connessione da chiudere.  
  
## <a name="return-value"></a>Valore restituito  
Valore booleano **true** a meno che la funzione non venga chiamata con un parametro non valido. Se la funzione viene chiamata con un parametro non valido, viene restituito **false** .  
  
> [!NOTE]  
> **Null** è un parametro valido per questa funzione. Permette alla funzione di essere chiamata più volte in uno script. Ad esempio, se si chiude una connessione in una condizione di errore e la si chiude nuovamente alla fine dello script, la seconda chiamata a **sqlsrv_close** restituirà **true** perché la prima chiamata a **sqlsrv_close** (nella condizione di errore) imposta la risorsa di connessione su **null**.  
  
## <a name="example"></a>Esempio  
L'esempio seguente chiude una connessione. Nell'esempio si presuppone che SQL Server sia installato nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nella console.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection here.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
echo "Connection closed.\n";  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
  
