---
title: PDOStatement::fetch | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4368e362-5bda-4da1-8462-33714683c39f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a69b1093240112a804504f8d0e636ffbdfe8439e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993064"
---
# <a name="pdostatementfetch"></a>PDOStatement::fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera una riga da un set di risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
mixed PDOStatement::fetch ([ $fetch_style[, $cursor_orientation[, $cursor_offset]]] );  
```  
  
#### <a name="parameters"></a>Parametri  
$*fetch_style*: simbolo (intero) facoltativo che specifica il formato dei dati della riga. Vedere la sezione Osservazioni per l'elenco dei valori possibili per $*fetch_style*. Il valore predefinito è PDO::FETCH_BOTH. $*fetch_style* nel metodo di recupero esegue l'override di $*fetch_style* specificato nel metodo PDO::query.  
  
$*cursor_orientation*: simbolo (intero) facoltativo che indica la riga da recuperare quando l'istruzione prepare specifica `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`. Vedere la sezione Osservazioni per l'elenco dei possibili valori per $*cursor_orientation*. Vedere [PDO::prepare](../../connect/php/pdo-prepare.md) per un esempio di uso di un cursore scorrevole.  
  
$*cursor_offset*: simbolo (intero) facoltativo che specifica la riga da recuperare quando $*cursor_orientation* è PDO::FETCH_ORI_ABS o PDO::FETCH_ORI_REL e PDO::ATTR_CURSOR è PDO::CURSOR_SCROLL.  
  
## <a name="return-value"></a>Valore restituito  
Valore misto che restituisce una riga o false.  
  
## <a name="remarks"></a>Osservazioni  
Il cursore viene spostato automaticamente in avanti quando si chiama un'operazione di recupero. Nella tabella seguente sono elencati i valori possibili di $*fetch_style*.  
  
|$*fetch_style*|Descrizione|  
|-------------------|---------------|  
|PDO::FETCH_ASSOC|Specifica una matrice indicizzata in base al nome della colonna.|  
|PDO::FETCH_BOTH|Specifica una matrice indicizzata in base al nome della colonna e all'ordine in base 0. Questa è la modalità predefinita.|  
|PDO::FETCH_BOUND|Restituisce true e assegna i valori come specificato da [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md).|  
|PDO::FETCH_CLASS|Crea un'istanza ed esegue il mapping delle colonne sulle proprietà denominate.<br /><br />Chiamare [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) prima di chiamare il recupero.|  
|PDO::FETCH_INTO|Aggiorna un'istanza della classe richiesta.<br /><br />Chiamare [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) prima di chiamare il recupero.|  
|PDO::FETCH_LAZY|Crea i nomi delle variabili durante l'accesso e crea un oggetto senza nome.|  
|PDO::FETCH_NUM|Specifica una matrice indicizzata con l'ordine in base zero della colonna.|  
|PDO::FETCH_OBJ|Specifica un oggetto senza nome con i nomi delle proprietà che eseguono il mapping sui nomi delle colonne.|  
  
Se il cursore si trova alla fine del set di risultati (l'ultima riga è stata recuperata e il cursore spostato oltre il limite del set di risultati) e se il cursore è forward-only (PDO::ATTR_CURSOR = PDO::CURSOR_FWDONLY), le successive chiamate di recupero avranno esito negativo.  
  
Se il cursore è scorrevole (PDO::ATTR_CURSOR = PDO::CURSOR_SCROLL), le chiamate di recupero sposteranno il cursore all'interno del limite del set di risultati. Nella tabella seguente sono elencati i valori possibili di $*cursor_orientation*.  
  
|$*cursor_orientation*|Descrizione|  
|--------------------------|---------------|  
|PDO::FETCH_ORI_NEXT|Recupera la riga seguente. Questa è la modalità predefinita.|  
|PDO::FETCH_ORI_PRIOR|Recupera la riga precedente.|  
|PDO::FETCH_ORI_FIRST|Recupera la prima riga.|  
|PDO::FETCH_ORI_LAST|Recupera l'ultima riga.|  
|PDO::FETCH_ORI_ABS, *num*|Recupera la riga richiesta in $*cursor_offset* in base al numero di riga.|  
|PDO::FETCH_ORI_REL, *num*|Recupera la riga richiesta in $*cursor_offset* in base alla posizione relativa rispetto alla posizione corrente.|  
  
Se il valore specificato per $*cursor_offset* o $*cursor_orientation* corrisponde a una posizione al di fuori del limite del set di risultati, il recupero avrà esito negativo.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print( "\n---------- PDO::FETCH_CLASS -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg";  
      }  
  
      function __toString() {  
         return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
      }  
   }  
  
   $stmt->setFetchMode(PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
   while ( $row = $stmt->fetch(PDO::FETCH_CLASS)) {   
      print($row . "\n");   
   }  
  
   print( "\n---------- PDO::FETCH_INTO -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
   $c_obj = new cc( '' );  
  
   $stmt->setFetchMode(PDO::FETCH_INTO, $c_obj);  
   while ( $row = $stmt->fetch(PDO::FETCH_INTO)) {   
      echo "$c_obj\n";  
   }  
  
   print( "\n---------- PDO::FETCH_ASSOC -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_ASSOC );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_NUM -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_NUM );  
   print_r ($result );  
  
   print( "\n---------- PDO::FETCH_BOTH -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_BOTH );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_LAZY -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_LAZY );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_OBJ -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_OBJ );  
   print $result->Name;  
   print( "\n \n" );  
  
   print( "\n---------- PDO::FETCH_BOUND -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->bindColumn('Name', $name);  
   $result = $stmt->fetch( PDO::FETCH_BOUND );  
   print $name;  
   print( "\n \n" );  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
