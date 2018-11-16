---
title: PDOStatement::closeCursor | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9aa14dfba76af243ee91c044c89993ca6cfec05
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606151"
---
# <a name="pdostatementclosecursor"></a>PDOStatement::closeCursor
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Chiude il cursore, consentendo all'istruzione di essere eseguita nuovamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## <a name="return-value"></a>Valore restituito  
Restituisce true in caso di esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Remarks  
closeCursor ha effetto quando l'opzione di connessione MultipleActiveResultSets è impostata su false.  Per altre informazioni sull'opzione di connessione MultipleActiveResultSets, vedere [Procedura: Disabilitare più set di risultati attivi (MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).  
  
Anziché chiamare closeCursor, è anche possibile limitarsi a impostare l'handle di istruzione su Null.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
