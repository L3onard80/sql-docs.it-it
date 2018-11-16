---
title: 'Pdostatement:: ErrorCode | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5bbe2c3bc3aa3b75a32e5567ee4e1891b303e52
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604751"
---
# <a name="pdostatementerrorcode"></a>PDOStatement::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera il valore SQLSTATE dell'operazione più recente per l'oggetto istruzione del database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
string PDOStatement::errorCode();  
```  
  
## <a name="return-value"></a>Valore restituito  
Restituisce un valore SQLSTATE di cinque caratteri sotto forma di stringa oppure NULL se non esiste alcuna operazione nell'handle di istruzione.  
  
## <a name="remarks"></a>Remarks  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
In questo esempio viene illustrata una query SQL che contiene un errore.  Viene quindi visualizzato il codice di errore.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print $stmt->errorCode();  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
