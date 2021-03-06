---
title: Membri di SQLServerStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 828cbaa9-ea7a-4986-95c3-5ba0d7d01d83
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72eededd01cd61d6845cc92bbdfbfd073668dd76
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "67970359"
---
# <a name="sqlserverstatement-members"></a>Membri di SQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Nelle tabelle seguenti sono elencati i membri esposti dalla classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="constructors"></a>Costruttori  
 No.  
  
## <a name="fields"></a>Campi  
 No.  
  
## <a name="inherited-fields"></a>Campi ereditati  
  
|Nome|Descrizione|  
|----------|-----------------|  
|java.sql.Statement|CLOSE_ALL_RESULTS, CLOSE_CURRENT_RESULT, EXECUTE_FAILED, KEEP_CURRENT_RESULT, NO_GENERATED_KEYS, RETURN_GENERATED_KEYS, SUCCESS_NO_INFO|  
  
## <a name="methods"></a>Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[addBatch](../../../connect/jdbc/reference/addbatch-method-sqlserverstatement.md)|Aggiunge il comando SQL specificato all'elenco corrente di comandi per questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md)|Annulla l'istruzione SQL attualmente in esecuzione tramite questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[clearBatch](../../../connect/jdbc/reference/clearbatch-method-sqlserverstatement.md)|Svuota l'elenco corrente di comandi SQL per questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverstatement.md)|Cancella tutti gli avvisi segnalati in questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverstatement.md)|Rilascia immediatamente le risorse JDBC e di database di questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) invece di attendere il rilascio automatico.|  
|[execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)|Esegue l'istruzione SQL specificata, che può restituire più risultati.|  
|[executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)|Invia al database un batch di comandi da eseguire. Se tutti i comandi vengono eseguiti correttamente, restituisce una matrice di conteggi aggiornamenti.|  
|[executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)|Esegue l'istruzione SQL specificata e restituisce un solo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[executeUpdate](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)|Esegue l'istruzione SQL specificata, che può essere un'istruzione INSERT, UPDATE, MERGE o DELETE, oppure un'istruzione SQL che non restituisce nulla, quale un'istruzione SQL DDL.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverstatement.md)|Recupera l'oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) che ha generato questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverstatement.md)|Recupera la direzione per il recupero di righe da tabelle di database che rappresenta l'impostazione predefinita per i set di risultati generati da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverstatement.md)|Recupera il numero di righe del set di risultati che rappresenta la dimensione di recupero predefinita per gli oggetti del set di risultati generati da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getGeneratedKeys](../../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)|Recupera le chiavi generate automaticamente create come risultato dell'esecuzione di questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getMaxFieldSize](../../../connect/jdbc/reference/getmaxfieldsize-method-sqlserverstatement.md)|Recupera il numero massimo di byte che possono essere restituiti per i valori di colonna binaria o di tipo carattere in un oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) generato da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getMaxRows](../../../connect/jdbc/reference/getmaxrows-method-sqlserverstatement.md)|Recupera il numero massimo di righe che possono essere contenute da un oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) generato da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getMoreResults](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)|Passa al risultato successivo di questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getQueryTimeout](../../../connect/jdbc/reference/getquerytimeout-method-sqlserverstatement.md)|Recupera il numero di secondi di attesa di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] prima dell'esecuzione di questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)|Recupera la modalità di memorizzazione delle risposte nel buffer per questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md)|Recupera il risultato corrente come oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getResultSetConcurrency](../../../connect/jdbc/reference/getresultsetconcurrency-method-sqlserverstatement.md)|Recupera la concorrenza dei set di risultati per gli oggetti [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) generati da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResultSetHoldability](../../../connect/jdbc/reference/getresultsetholdability-method-sqlserverstatement.md)|Recupera la trattenibilità del set di risultati per gli oggetti [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) generati da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getResultSetType](../../../connect/jdbc/reference/getresultsettype-method-sqlserverstatement.md)|Recupera il tipo di set di risultati per gli oggetti [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) generati da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[getUpdateCount](../../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md)|Recupera il risultato corrente come conteggio aggiornamenti.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverstatement.md)|Recupera il primo avviso segnalato dalle chiamate a questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverstatement.md)|Indica se questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) è stato chiuso.|  
|[isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md)|Restituisce un valore che indica se è possibile aggiungere un'istruzione al pool di istruzioni fornito dall'utente.|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)|Indica se questo oggetto istruzione è un wrapper per l'interfaccia specificata.|  
|[setCursorName](../../../connect/jdbc/reference/setcursorname-method-sqlserverstatement.md)|Imposta il nome del cursore SQL sulla stringa specificata, che sarà utilizzata dai metodi Execute successivi.|  
|[setEscapeProcessing](../../../connect/jdbc/reference/setescapeprocessing-method-sqlserverstatement.md)|Imposta la modalità di elaborazione di escape.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md)|Fornisce al driver JDBC un hint per la direzione da utilizzare per l'elaborazione delle righe del set di risultati.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverstatement.md)|Fornisce al driver JDBC un hint per il numero di righe che devono essere recuperate dal database, qualora siano necessarie più righe.|  
|[setMaxFieldSize](../../../connect/jdbc/reference/setmaxfieldsize-method-sqlserverstatement.md)|Imposta sul numero di byte specificato il limite per il numero massimo di byte in una colonna [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) che archivia valori di tipo carattere o binari.|  
|[setMaxRows](../../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md)|Imposta sul numero specificato il numero massimo di righe che un oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) può contenere.|  
|[setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md)|Richiede che un'istruzione sia o meno inserita in un pool.|  
|[setQueryTimeout](../../../connect/jdbc/reference/setquerytimeout-method-sqlserverstatement.md)|Imposta il numero di secondi durante i quali il driver rimarrà in attesa dell'esecuzione di un oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) sul numero di secondi specificato.|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)|Imposta la modalità di memorizzazione delle risposte nel buffer per questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) su un valore String **full** o **adaptive** senza distinzione tra maiuscole e minuscole.|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)|Restituisce un oggetto che implementa l'interfaccia specificata per consentire l'accesso ai metodi specifici di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
