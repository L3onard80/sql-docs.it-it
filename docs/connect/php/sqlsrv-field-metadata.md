---
title: sqlsrv_field_metadata | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_field_metadata
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_field_metadata
- sqlsrv_field_metadata
ms.assetid: c02f6942-0484-4567-a78e-fe8aa2053536
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ef4bd58d352216cd4c64fe6c18a9ffd6dd3b13a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "76939567"
---
# <a name="sqlsrv_field_metadata"></a>sqlsrv_field_metadata
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera i metadati per i campi di un'istruzione preparata. Per informazioni sulla preparazione di un'istruzione, vedere [sqlsrv_query](../../connect/php/sqlsrv-query.md) o [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md). Si noti che **sqlsrv_field_metadata** può essere chiamato in qualsiasi istruzione preparata, pre-esecuzione o post-esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_field_metadata( resource $stmt)  
```  
  
#### <a name="parameters"></a>Parametri  
*$stmt*: risorsa di istruzione per la quale sono richiesti i metadati del campo.  
  
## <a name="return-value"></a>Valore restituito  
Una **matrice** di matrici oppure **false**. La matrice è costituita da una singola matrice per ogni campo nel set di risultati. Ogni matrice secondaria include le chiavi elencate nella tabella seguente. Se si verifica un errore durante il recupero dei metadati del campo, viene restituito **false** .  
  
|Chiave|Descrizione|  
|-------|---------------|  
|Nome|Nome della colonna a cui corrisponde il campo.|  
|Type|Valore numerico che corrisponde a un tipo SQL.|  
|Dimensione|Numero di caratteri per i campi di tipo carattere (char(n), varchar(n), nchar(n), nvarchar(n), XML). Numero di byte per i campi di tipo binario (binary(n), varbinary(n), tipo definito dall'utente). **NULL** per altri tipi di dati di SQL Server.|  
|Precision|Precisione per i tipi di precisione delle variabili (real, numeric, decimal, datetime2, datetimeoffset e time). **NULL** per altri tipi di dati di SQL Server.|  
|Scalabilità|Scala per i tipi di scala delle variabili (numeric, decimal, datetime2, datetimeoffset e time). **NULL** per altri tipi di dati di SQL Server.|  
|Nullable|Valore enumerato che indica se la colonna è nullable (**SQLSRV_NULLABLE_YES**), non è nullable (**SQLSRV_NULLABLE_NO**) o non è noto se la colonna è nullable (**SQLSRV_NULLABLE_UNKNOWN**).|  
  
Nella tabella seguente vengono fornite altre informazioni sulle chiavi di ogni matrice secondaria (per informazioni sui tipi, vedere la documentazione di SQL Server):  
  
|Tipo di dati di SQL Server 2008|Type|Precisione min/max|Scala min/max|Dimensione|  
|-----------------------------|--------|----------------------|------------------|--------|  
|bigint|SQL_BIGINT (-5)|||8|  
|BINARY|SQL_BINARY (-2)|||0 < *n* < 8000 <sup>1</sup>|  
|bit|SQL_BIT (-7)||||  
|char|SQL_CHAR (1)|||0 < *n* < 8000 <sup>1</sup>|  
|Data|SQL_TYPE_DATE (91)|10/10|0/0||  
|Datetime|SQL_TYPE_TIMESTAMP (93)|23/23|3/3||  
|datetime2|SQL_TYPE_TIMESTAMP (93)|19/27|0/7||  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET (-155)|26/34|0/7||  
|decimal|SQL_DECIMAL (3)|1/38|0/valore precisione||  
|float|SQL_FLOAT (6)|4/8|||  
|image|SQL_LONGVARBINARY (-4)|||2 GB|  
|INT|SQL_INTEGER (4)||||  
|money|SQL_DECIMAL (3)|19/19|4/4||  
|NCHAR|SQL_WCHAR (-8)|||0 < *n* < 4000 <sup>1</sup>|  
|ntext|SQL_WLONGVARCHAR (-10)|||1 GB|  
|NUMERIC|SQL_NUMERIC (2)|1/38|0/valore precisione||  
|NVARCHAR|SQL_WVARCHAR (-9)|||0 < *n* < 4000 <sup>1</sup>|  
|real|SQL_REAL (7)|4/4|||  
|smalldatetime|SQL_TYPE_TIMESTAMP (93)|16/16|0/0||  
|SMALLINT|SQL_SMALLINT (5)|||2 byte|  
|Smallmoney|SQL_DECIMAL (3)|10/10|4/4||  
|sql_variant|SQL_SS_VARIANT (-150)|||Variabile|  
|text|SQL_LONGVARCHAR (-1)|||2 GB|  
|time|SQL_SS_TIME2 (-154)|8/16|0/7||  
|timestamp|SQL_BINARY (-2)|||8 byte|  
|TINYINT|SQL_TINYINT (-6)|||1 byte|  
|udt|SQL_SS_UDT (-151)|||Variabile|  
|UNIQUEIDENTIFIER|SQL_GUID (-11)|||16|  
|varbinary|SQL_VARBINARY (-3)|||0 < *n* < 8000 <sup>1</sup>|  
|varchar|SQL_VARCHAR (12)|||0 < *n* < 8000 <sup>1</sup>|  
|Xml|SQL_SS_XML (-152)|||0|  
  
(1) Zero (0) indica che la dimensione massima è consentita.  
  
La chiave nullable può essere yes o no.  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene creata una risorsa di istruzione, quindi vengono recuperati e visualizzati i metadati dei campi. Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) siano installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```
<?php
/* Connect to the local server using Windows Authentication and
specify the AdventureWorks database as the database in use. */
$serverName = "(local)";
$connectionInfo = array("Database"=>"AdventureWorks");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect.\n";
    die( print_r( sqlsrv_errors(), true));
}

/* Prepare the statement. */
$tsql = "SELECT ReviewerName, Comments FROM Production.ProductReview";
$stmt = sqlsrv_prepare( $conn, $tsql);
  
/* Get and display field metadata. */
foreach( sqlsrv_field_metadata( $stmt) as $fieldMetadata) {
    foreach( $fieldMetadata as $name => $value) {
        echo "$name: $value\n";
    }  
    echo "\n";
}  
  
/* Note: sqlsrv_field_metadata can be called on any statement
resource, pre- or post-execution. */
  
/* Free statement and connection resources. */
sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);
?>
```

## <a name="sensitivity-data-classification-metadata"></a>Metadati di classificazione dei dati di riservatezza

Nella versione 5.8.0 è stata introdotta la nuova opzione `DataClassification` per consentire agli utenti di accedere ai [metadati di classificazione dei dati di riservatezza](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-ver15&tabs=t-sql#subheading-4) in Microsoft SQL Server 2019 usando `sqlsrv_field_metadata`, che richiede Microsoft ODBC Driver 17.4.2 o versione successiva.

Per impostazione predefinita l'opzione `DataClassification` è `false`, ma se è impostata su `true` la matrice restituita da `sqlsrv_field_metadata` viene popolata con i metadati di classificazione dei dati di riservatezza, se esistenti. 

Ad esempio prendere in considerazione una tabella Patients:

```
CREATE TABLE Patients 
      [PatientId] int identity,
      [SSN] char(11),
      [FirstName] nvarchar(50),
      [LastName] nvarchar(50),
      [BirthDate] date)
```

È possibile classificare le colonne SSN e BirthDate come illustrato di seguito:

```
ADD SENSITIVITY CLASSIFICATION TO [Patients].SSN WITH (LABEL = 'Highly Confidential - secure privacy', INFORMATION_TYPE = 'Credentials')
ADD SENSITIVITY CLASSIFICATION TO [Patients].BirthDate WITH (LABEL = 'Confidential Personal Data', INFORMATION_TYPE = 'Birthdays')
```

Per accedere ai metadati, chiamare `sqlsrv_field_metadata` come illustrato nel frammento di codice seguente:

```
$tableName = 'Patients';
$tsql = "SELECT * FROM $tableName";
$stmt = sqlsrv_prepare($conn, $tsql, array(), array('DataClassification' => true));
if (sqlsrv_execute($stmt)) {
    $fieldmeta = sqlsrv_field_metadata($stmt);

    foreach ($fieldmeta as $f) {
        if (count($f['Data Classification']) > 0) {
            echo $f['Name'] . ": \n";
            print_r($f['Data Classification']); 
        }
    }
}
```

L'output sarà:

```
SSN: 
Array
(
    [0] => Array
        (
            [Label] => Array
                (
                    [name] => Highly Confidential - secure privacy
                    [id] => 
                )

            [Information Type] => Array
                (
                    [name] => Credentials
                    [id] => 
                )

        )

)
BirthDate: 
Array
(
    [0] => Array
        (
            [Label] => Array
                (
                    [name] => Confidential Personal Data
                    [id] => 
                )

            [Information Type] => Array
                (
                    [name] => Birthdays
                    [id] => 
                )

        )

)
```

Se si usa `sqlsrv_query` anziché `sqlsrv_prepare` il frammento di codice precedente può essere modificato come nell'esempio seguente:

```
$tableName = 'Patients';
$tsql = "SELECT * FROM $tableName";
$stmt = sqlsrv_query($conn, $tsql, array(), array('DataClassification' => true));
$fieldmeta = sqlsrv_field_metadata($stmt);

foreach ($fieldmeta as $f) {
    $jstr = json_encode($f);
    echo $jstr . PHP_EOL;
}
```

Come si può notare nella rappresentazione JSON seguente i metadati di classificazione dei dati vengono visualizzati se associati alle colonne:

```
{"Name":"PatientId","Type":4,"Size":null,"Precision":10,"Scale":null,"Nullable":0,"Data Classification":[]}
{"Name":"SSN","Type":1,"Size":11,"Precision":null,"Scale":null,"Nullable":1,"Data Classification":[{"Label":{"name":"Highly Confidential - secure privacy","id":""},"Information Type":{"name":"Credentials","id":""}}]}
{"Name":"FirstName","Type":-9,"Size":50,"Precision":null,"Scale":null,"Nullable":1,"Data Classification":[]}
{"Name":"LastName","Type":-9,"Size":50,"Precision":null,"Scale":null,"Nullable":1,"Data Classification":[]}
{"Name":"BirthDate","Type":91,"Size":null,"Precision":10,"Scale":0,"Nullable":1,"Data Classification":[{"Label":{"name":"Confidential Personal Data","id":""},"Information Type":{"name":"Birthdays","id":""}}]}
```

## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  

[Costanti &#40;driver Microsoft per PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
  
