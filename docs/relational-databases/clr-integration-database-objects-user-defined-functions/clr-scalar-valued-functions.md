---
title: Funzioni a valori scalari CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
ms.openlocfilehash: ac063fa59d22308cb90206816555eea8474acca6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68009778"
---
# <a name="clr-scalar-valued-functions"></a>Funzioni a valori scalari CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Una funzione a valori scalari restituisce un valore singolo, come una stringa un Integer o un valore di bit. È possibile creare funzioni a valori scalari definite dall'utente nel codice gestito utilizzando qualsiasi linguaggio di programmazione di .NET Framework. Queste funzioni sono accessibili a [!INCLUDE[tsql](../../includes/tsql-md.md)] o ad altro codice gestito. Per informazioni sui vantaggi dell'integrazione con CLR e sulla scelta tra codice gestito [!INCLUDE[tsql](../../includes/tsql-md.md)]e, vedere [Cenni preliminari sull'integrazione con CLR](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>Requisiti per le funzioni a valori scalari CLR  
 Le funzioni a valori scalari di .NET Framework vengono implementate come metodi in una classe di un assembly .NET Framework. I parametri di input e il tipo restituiti da un SVF possono essere uno qualsiasi dei tipi di dati scalari supportati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]da, ad eccezione di **varchar**, **char**, **rowversion**, **Text**, **ntext**, **Image**, **timestamp**, **Table**o **Cursor**. Le funzioni a valori scalari devono assicurare una corrispondenza tra il tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il tipo dati restituito del metodo di implementazione. Per ulteriori informazioni sulle conversioni di tipi, vedere [mapping dei dati dei parametri CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
 Quando si implementa un .NET Framework SVF in una lingua .NET Framework, è possibile specificare l'attributo personalizzato **SqlFunction** per includere informazioni aggiuntive sulla funzione. L'attributo **SqlFunction** indica se la funzione accede o modifica i dati, se è deterministica, e se la funzione prevede operazioni a virgola mobile.  
  
 Le funzioni definite dall'utente a valori scalari possono essere deterministiche o non deterministiche. Una funzione deterministica restituisce sempre lo stesso risultato quando viene chiamata con un set specifico di parametri di input. Una funzione non deterministica può restituire risultati diversi quando viene chiamata con un set specifico di parametri di input.  
  
> [!NOTE]  
>  Non contrassegnare una funzione come deterministica se non produce sempre gli stessi valori di output, dati gli stessi valori di input e lo stesso stato del database. Una funzione non propriamente deterministica ma contrassegnata come tale può causare danni a viste indicizzate e colonne calcolate. Per contrassegnare una funzione come deterministica, impostare la proprietà **Deterministic** su true.  
  
### <a name="table-valued-parameters"></a>Parametri con valori di tabella  
 I parametri con valori di tabella, ovvero tipi di tabella definiti dall'utente passati in una procedura o in una funzione, consentono di passare in modo efficiente più righe di dati al server. Pur essendo caratterizzati da funzionalità simili alle matrici di parametri, i parametri con valori di tabella offrono più flessibilità e una maggiore integrazione con [!INCLUDE[tsql](../../includes/tsql-md.md)] Consentono inoltre di ottenere prestazioni potenzialmente migliori. I parametri con valori di tabella consentono inoltre di ridurre il numero di round trip al server. Anziché inviare più richieste al server, ad esempio con un elenco di parametri scalari, è possibile inviare i dati al server sotto forma di parametro con valori di tabella. Un tipo di tabella definito dall'utente non può essere passato come parametro con valori di tabella a una stored procedure gestita o a una funzione in esecuzione nel processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], né può essere restituito dalle stesse. Per altre informazioni su TVP, vedere [usare i parametri con valori di tabella &#40;motore di database&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="example-of-a-clr-scalar-valued-function"></a>Esempio di una funzione a valori scalari CLR  
 Di seguito è riportata una semplice funzione a valori scalari che accede ai dati e restituisce un valore integer:  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 La prima riga di codice fa riferimento a **Microsoft. SqlServer. Server** per accedere agli attributi e a **System. Data. SqlClient** per accedere allo spazio dei nomi ADO.NET. Questo spazio dei nomi contiene **SqlClient**, il .NET Framework provider di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]per.  
  
 Successivamente, la funzione riceve l'attributo personalizzato **SqlFunction** , disponibile nello spazio dei nomi **Microsoft. SqlServer. Server** . L'attributo personalizzato indica se la funzione definita dall'utente utilizza il provider in-process per leggere dati nel server. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non consente alle Funzioni definite dall'utente di aggiornare, inserire o eliminare dati. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono ottimizzare l'esecuzione di una UDF che non utilizza il provider in-process. Questo è indicato impostando **DataAccessKind** su **DataAccessKind. None**. Sulla riga successiva il metodo di destinazione è un metodo statico pubblico (condiviso in Visual Basic .NET).  
  
 La classe **SqlContext** , che si trova nello spazio dei nomi **Microsoft. SqlServer. Server** , può quindi accedere a un oggetto **SqlCommand** con una connessione all' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza già configurata. Anche se non viene usato in questo caso, il contesto di transazione corrente è disponibile anche tramite il Application Programming Interface **System. Transactions** (API).  
  
 La maggior parte delle righe di codice nel corpo della funzione deve essere familiare agli sviluppatori che hanno scritto applicazioni client che utilizzano i tipi disponibili nello spazio dei nomi **System. Data. SqlClient** .  
  
 [C#]  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 [Visual Basic]  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 Il testo del comando appropriato viene specificato inizializzando l'oggetto **SqlCommand** . Nell'esempio precedente viene conteggiato il numero di righe nella tabella **SalesOrderHeader**. Viene quindi chiamato il metodo **ExecuteScalar** dell'oggetto **cmd** . Viene restituito un valore di tipo **int** in base alla query. Infine, il numero di ordini viene restituito al chiamante.  
  
 Se questo codice viene salvato in un file chiamato FirstUdf.cs, può essere compilato come assembly nel modo seguente:  
  
 [C#]  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 [Visual Basic]  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  
  `/t:library` indica che è necessario generare una libreria anziché un file eseguibile. I file eseguibili non possono essere registrati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Visual C++ oggetti di database compilati con **/CLR: pure** non sono supportati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]per l'esecuzione in. Questo tipo di oggetti di database include, ad esempio, funzioni a valori scalari.  
  
 Di seguito sono riportate la query [!INCLUDE[tsql](../../includes/tsql-md.md)] e una chiamata di esempio per registrare l'assembly e la funzione definita dall'utente.  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 Si noti che il nome della funzione esposto in [!INCLUDE[tsql](../../includes/tsql-md.md)] non dovere corrispondere al nome del metodo statico pubblico di destinazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping dei dati dei parametri CLR](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [Panoramica degli attributi personalizzati dell'integrazione con CLR](https://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)   
 [Funzioni definite dall'utente](../../relational-databases/user-defined-functions/user-defined-functions.md)   
 [Accesso ai dati da oggetti di database CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
