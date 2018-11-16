---
title: La connessione a un database SQL di Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c4caaa9ca14fd2f8eb396ef2c2869ba30bd48420
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602211"
---
# <a name="connecting-to-an-azure-sql-database"></a>Connessione a un database SQL di Azure

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

In questo argomento vengono illustrati i problemi dell'uso di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] per la connessione a [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]. Per altre informazioni sulla connessione a [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], vedere:  
  
- [Database SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)  
  
- [Procedura: Connettersi a SQL Azure mediante JDBC](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)  

- [Connessione tramite autenticazione di Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>Dettagli

Quando ci si connette a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], è necessario connettersi al database master per chiamare **SQLServerDatabaseMetaData.getCatalogs**.  
[!INCLUDE[ssAzure](../../includes/ssazure_md.md)] non supporta la restituzione dell'intero set di cataloghi da un database utente. **SQLServerDatabaseMetaData.getCatalogs** utilizzare la vista sys. Databases per ottenere i cataloghi. Fare riferimento alla trattazione delle autorizzazioni in [Sys. Databases (Database SQL Azure)](https://go.microsoft.com/fwlink/?LinkId=217396) comprendere **SQLServerDatabaseMetaData.getCatalogs** comportamento su una [!INCLUDE[ssAzure](../../includes/ssazure_md.md)].  
  
## <a name="connections-dropped"></a>Connessioni eliminate

Durante la connessione a [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], è possibile che le connessioni inattive siano terminate da un componente di rete, ad esempio un firewall, dopo un periodo di inattività. In questo contesto esistono due tipi di inattività:  

- Inattività a livello TCP, in cui le connessioni possono essere eliminate da un certo numero di dispositivi di rete.  

- Inattività in SQL Azure Gateway, in cui potrebbero verificarsi messaggi TCP **keepalive** (rendendo la connessione non inattiva da una prospettiva TCP), ma in cui non è stata rilevata una query attiva da 30 minuti. In questo scenario il gateway determinerà che la connessione TDS è inattiva da 30 minuti e la terminerà.  
  
Per evitare l'eliminazione di connessioni inattive da un componente di rete, è consigliabile impostare le seguenti impostazioni del Registro di sistema, o le relative equivalenti non Windows, nel sistema operativo in cui viene caricato il driver:  
  
|Impostazione del Registro di sistema|Valore consigliato|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ sistema \ CurrentControlSet \ Services \ Tcpip \ parametri \ parametro KeepAliveTime della connessione|30000|  
|HKEY_LOCAL_MACHINE \ sistema \ CurrentControlSet \ Services \ Tcpip \ parametri \ parametro KeepAliveInterval della connessione|1000|  
|HKEY_LOCAL_MACHINE \ sistema \ CurrentControlSet \ Services \ Tcpip \ parametri \ TcpMaxDataRetransmissions|10|  
  
Riavviare il computer per attivare le impostazioni del Registro di sistema.  

A tale scopo, durante l'esecuzione di Windows Azure creare un'attività di avvio per aggiungere le chiavi del Registro di sistema.  Ad esempio, aggiungere l'attività di avvio al file di definizione del servizio:  

```xml
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```

Successivamente, aggiungere il file AddKeepAlive.cmd al progetto in uso. Impostare l'impostazione "Copia nella directory di output" su Copia sempre. Di seguito è riportato un esempio di file AddKeepAlive.cmd:  

```bat
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on SQL Azure  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```

## <a name="appending-the-server-name-to-the-userid-in-the-connection-string"></a>Accodamento del nome del server all'ID utente nella stringa di connessione  

Prima della versione 4.0 di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], durante la connessione a [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] veniva richiesto l'accodamento del nome del server all'ID utente nella stringa di connessione. Ad esempio, user@servername. A partire dalla versione 4.0 di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] l'accodamento di @servername all'ID utente nella stringa di connessione non è più necessario.  
  
## <a name="using-encryption-requires-setting-hostnameincertificate"></a>Impostazione di hostNameInCertificate obbligatoria per l'utilizzo della crittografia

Quando ci si connette a un [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], è necessario specificare **hostNameInCertificate** se si specifica **crittografare = true**. (Se è il nome del server nella stringa di connessione *shortName*. *domainName*, impostare il **hostNameInCertificate** proprietà \*. *domainName*.)  
  
Ad esempio  

```java
jdbc:sqlserver://abcd.int.mscds.com;databaseName= myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate= *.int.mscds.com;  
```

## <a name="see-also"></a>Vedere anche

[Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
