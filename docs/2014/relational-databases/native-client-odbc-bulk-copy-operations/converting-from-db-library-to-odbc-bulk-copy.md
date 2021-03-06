---
title: Conversione dalla copia bulk DB-Library a ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9694a5f54d740e298b9c6af4ab3169a3eb8ab14
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067627"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>Conversione della copia bulk da DB-Library a ODBC
  La conversione di un programma di copia bulk DB-Library in ODBC è semplice perché le funzioni di copia [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bulk supportate dal driver ODBC di Native Client sono simili alle funzioni di copia bulk DB-Library, con le eccezioni seguenti:  
  
-   Nelle applicazioni DB-Library un puntatore a una struttura DBPROCESS viene passato come primo parametro delle funzioni di copia bulk. Nelle applicazioni ODBC il puntatore DBPROCESS viene sostituito da un handle di connessione ODBC.  
  
-   Le applicazioni DB-Library chiamano **BCP_SETL** prima della connessione per abilitare le operazioni di copia bulk in un DBPROCESS. Le applicazioni ODBC chiamano invece [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) prima della connessione per abilitare le operazioni bulk su un handle di connessione:  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC di Native client non supporta i gestori di messaggi e di errori di DB-Library. è necessario chiamare **SQLGetDiagRec** per ottenere gli errori e i messaggi generati dalle funzioni di copia bulk ODBC. Le versioni ODBC delle funzioni di copia bulk restituiscono i codici restituiti standard di copia bulk SUCCEED o FAILED, non codici restituiti di tipo ODBC, come SQL_SUCCESS o SQL_ERROR.  
  
-   I valori specificati per il parametro DB-Library [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* vengono interpretati in modo diverso rispetto al parametro ODBC **bcp_bind**_cbData_ .  
  
    |Condizione indicata|Valore *VARLEN* DB-Library|Valore ODBC *cbData*|  
    |-------------------------|--------------------------------|-------------------------|  
    |Valori Null forniti|0|-1 (SQL_NULL_DATA)|  
    |Dati variabili forniti|-1|-10 (SQL_VARLEN_DATA)|  
    |Carattere di lunghezza zero o stringa binaria|ND|0|  
  
     In DB-Library, un valore *varlen* pari a-1 indica che vengono forniti dati a lunghezza variabile, che in ODBC *cbData* viene interpretato per indicare che vengono forniti solo valori null. Modificare le specifiche *VARLEN* DB-Library di-1 in SQL_VARLEN_DATA e tutte le specifiche *varlen* da 0 a SQL_NULL_DATA.  
  
-   Il_file\__ **Colfmt BCP\_** di DB-Library e ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData* presentano lo stesso problema dei parametri **bcp_bind**_varlen_ e *cbData* indicati in precedenza. Modificare le specifiche di *FILE_COLLEN* DB-Library di-1 per SQL_VARLEN_DATA ed eventuali specifiche di *file_collen* da 0 a SQL_NULL_DATA.  
  
-   Il parametro *iValue* della funzione ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) è un puntatore void. In DB-Library *iValue* è un numero intero. Eseguire il cast dei valori per ODBC *iValue* a void *.  
  
-   L'opzione **BCP_CONTROL** BCPMAXERRS specifica il numero di righe singole che possono avere errori prima che un'operazione di copia bulk abbia esito negativo. Il valore predefinito per BCPMAXERRS è 0 (fail al primo errore) nella versione DB-Library di **bcp_control** e 10 nella versione ODBC. Le applicazioni DB-Library che dipendono dal valore predefinito 0 per terminare un'operazione di copia bulk devono essere modificate per chiamare il **BCP_CONTROL** ODBC per impostare BCPMAXERRS su 0.  
  
-   La funzione ODBC **bcp_control** supporta le seguenti opzioni non supportate dalla versione DB-Library di **bcp_control**:  
  
    -   BCPODBC  
  
         Se impostato su TRUE, specifica che i valori **DateTime** e **smalldatetime** salvati in formato carattere avranno il prefisso e il suffisso della sequenza di escape del timestamp ODBC. Si applica solo alle operazioni BCP_OUT.  
  
         Con BCPODBC impostato su FALSE, un valore **DateTime** convertito in una stringa di caratteri viene restituito come:  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Con BCPODBC impostato su TRUE, lo stesso valore **DateTime** viene restituito come:  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   BCPKEEPIDENTITY  
  
         Quando è impostato su TRUE, specifica che le funzioni di copia bulk inseriscono i valori dei dati forniti per le colonne con vincoli di identità. Se questa impostazione non è disponibile, per le righe inserite vengono generati nuovi valori Identity.  
  
    -   BCPHINTS  
  
         Specifica le varie ottimizzazioni della copia bulk. Questa opzione non può essere utilizzata nella versione 6.5 o nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   BCPFILECP  
  
         Specifica la tabella codici del file di copia bulk.  
  
    -   BCPUNICODEFILE  
  
         Specifica che un file di copia bulk in modalità carattere è un file Unicode.  
  
-   La funzione ODBC **bcp_colfmt** non supporta l'indicatore *file_type* di SQLCHAR perché è in conflitto con il typedef ODBC SQLCHAR. Usare SQLCHARACTER invece per **bcp_colfmt**.  
  
-   Nelle versioni ODBC delle funzioni di copia bulk il formato per l'utilizzo dei valori **DateTime** e **smalldatetime** nelle stringhe di caratteri è il formato ODBC aaaa-mm-gg hh: mm: SS. sss; i valori **smalldatetime** utilizzano il formato ODBC yyyy-mm-gg hh: mm: SS.  
  
     Le versioni DB-Library delle funzioni di copia bulk accettano valori **DateTime** e **smalldatetime** nelle stringhe di caratteri utilizzando diversi formati:  
  
    -   Il formato predefinito è *mmm gg aaaa hh: Mmxx* dove *XX* è AM o PM.  
  
    -   stringhe di caratteri **DateTime** e **smalldatetime** in qualsiasi formato supportato dalla funzione **DBConvert** di DB-Library.  
  
    -   Quando la casella **Usa impostazioni internazionali** è selezionata nella scheda **Opzioni** DB-Library dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rete client, le funzioni di copia bulk DB-Library accettano anche le date nel formato di data regionale definito per le impostazioni locali del registro di sistema del computer client.  
  
     Le funzioni di copia bulk DB-Library non accettano i formati ODBC **DateTime** e **smalldatetime** .  
  
     Se l'attributo dell'istruzione SQL_SOPT_SS_REGIONALIZE è impostato su SQL_RE_ON, le funzioni di copia bulk ODBC accettano il formato di data locale definito per le impostazioni locali del Registro di sistema del computer client.  
  
-   Quando si esegue l'output dei valori **Money** in formato carattere, le funzioni di copia bulk ODBC forniscono quattro cifre di precisione e nessun separatore virgola; Le versioni DB-Library forniscono solo due cifre di precisione e includono i separatori di virgole.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni di copia bulk &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)   
 [Funzioni di copia bulk](../native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
