---
title: Funzionalità del driver OLE DB per SQL Server | Microsoft Docs
description: 'Funzionalità del driver OLE DB per SQL Server '
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: fa0fcda394142cd8ac2b3df5b91f5f8c4ad25739
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840909"
---
# <a name="ole-db-driver-for-sql-server-features"></a>Funzionalità del driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Oltre a esporre le funzionalità di Windows (in precedenza Microsoft) Data Access Components (WDAC), il driver OLE DB per SQL Server implementa anche molte altre funzionalità che consentono di esporre le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione    
 [Uso del mirroring del database](../../oledb/features/using-database-mirroring.md)  
 Viene descritto in che modo il driver OLE DB per SQL Server supporta l'uso di database con mirroring, cioè la capacità di mantenere una copia, o mirror, di un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un server di standby.  
  
 [Esecuzione di operazioni asincrone](../../oledb/features/performing-asynchronous-operations.md)  
 Si illustra in che modo il driver OLE DB per SQL Server supporta le operazioni asincrone, ovvero la capacità di restituzione immediata senza blocchi sul thread chiamante.  
  
 [Uso di MARS &#40;Multiple Active Result Set&#41;](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta multiple active result set (MARS). che consente di eseguire e ricevere più set di risultati utilizzando una sola connessione al database.  
  
 [Uso di tipi di dati XML](../../oledb/features/using-xml-data-types.md)  
 Si illustra in che modo il driver OLE DB per SQL Server supporta i dati XML, ovvero un tipo di dati basato su XML che è possibile usare come tipo di colonna, tipo di variabile, tipo di parametro o tipo restituito dalla funzione.  
  
 [Uso dei tipi definiti dall'utente](../../oledb/features/using-user-defined-types.md)  
 Si illustra in che modo il driver OLE DB per SQL Server supporta i tipi definiti dall'utente (UDT) che estendono il sistema dei tipi SQL consentendo di archiviare oggetti e strutture dei dati personalizzate in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Uso di tipi valore di grandi dimensioni](../../oledb/features/using-large-value-types.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta i tipi di dati valori di grandi dimensioni, ovvero sono tipi di dati large object (LOB).  
  
 [Modifica delle password a livello di codice](../../oledb/features/changing-passwords-programmatically.md)  
 Si illustra in che modo il driver OLE DB per SQL Server supporta la gestione delle password scadute per consentirne la modifica sul client senza il coinvolgimento dell'amministratore.  
  
 [Uso dell'isolamento dello snapshot](../../oledb/features/working-with-snapshot-isolation.md)  
 Si illustra in che modo il driver OLE DB per SQL Server supporta il miglioramento del controllo delle versioni delle righe che comporta a sua volta un miglioramento delle prestazioni del database evitando le situazioni di blocco in lettura/scrittura.  
  
 [Uso delle notifiche delle query](../../oledb/features/working-with-query-notifications.md)  
 Viene descritto come il Driver OLE DB per SQL Server supporta la notifica di tipo consumer nella modifica di set di righe.  
  
 [Esecuzione di operazioni di copia bulk](../../oledb/features/performing-bulk-copy-operations.md)  
 Si illustra in che modo il driver OLE DB per SQL Server supporta operazioni di copia bulk che consentono il trasferimento di grandi quantità di dati all'interno o all'esterno di una tabella o vista di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Uso della crittografia senza convalida](../../oledb/features/using-encryption-without-validation.md)  
 Illustra come usare il Driver OLE DB per SQL Server per crittografare i dati inviati al server senza la convalida del certificato.  
  
 [Parametri con valori di tabella &#40;driver OLE DB per SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 Descrive i Driver OLE DB per il supporto di SQL Server per i parametri con valori di tabella.  
  
 [Tipi CLR definiti dall'utente di grandi dimensioni](../../oledb/features/large-clr-user-defined-types.md)  
 Si illustra il supporto dei tipi CRL definiti dall'utente di grandi dimensioni.  
  
 [Supporto FILESTREAM](../../oledb/features/filestream-support.md)  
 Descrive i Driver OLE DB per il supporto di SQL Server per la caratteristica FILESTREAM avanzata.  
  
 [Supporto per nomi SPN nelle connessioni client](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 Si illustra in che modo il supporto per i nomi SPN (nome dell'entità servizio) è stato esteso per consentire l'autenticazione reciproca in tutti i protocolli.  
  
 [Supporto per colonne di tipo sparse nel driver OLE DB per SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 Descrive i Driver OLE DB per il supporto di SQL Server per le colonne di tipo sparse.  
  
 [Miglioramenti relativi a data e ora](../../oledb/features/date-and-time-improvements.md)  
 Viene descritto il supporto aggiunto per Driver OLE DB per SQL Server per i tipi di dati data e ora.  
  
 [Individuazione dei metadati](../../oledb/features/metadata-discovery.md)  
 Si illustrano i miglioramenti apportati all'individuazione dei metadati in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Supporto UTF-16 nel driver OLE DB per SQL Server](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 Si illustra una modifica nel comportamento introdotta in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Se si specifica un buffer a lunghezza fissa quando si esegue l'associazione di un risultato della colonna o di un parametro di output e se il carattere **wchar** scritto nel buffer prima del carattere di terminazione è un punto di codice surrogato elevato in una coppia di surrogati, nonché se il carattere **wchar** successivo è un punto di codice surrogato basso, nel driver OLE DB per SQL Server il punto di codice surrogato elevato non viene aggiunto al buffer.  
  
 [Driver OLE DB per il supporto di SQL Server per il ripristino di emergenza a disponibilità elevata](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 Illustra come configurare l'applicazione per sfruttare le funzionalità di ripristino di emergenza a disponibilità elevata aggiunte in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Accesso alle informazioni di diagnostica nel log degli eventi estesi](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 Illustra i miglioramenti apportati al driver OLE DB per SQL Server e alla traccia dei dati, che consente l'accesso alle informazioni di diagnostica nel buffer circolare e nel registro XEvents.  
  
 [Driver OLE DB per il supporto SQL Server per LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 Descrive i Driver OLE DB per il supporto di SQL Server per la funzionalità di Local DB.  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per SQL Server](../../oledb/oledb-driver-for-sql-server.md)      
 [Procedure relative a OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [Installazione del driver OLE DB per SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  
