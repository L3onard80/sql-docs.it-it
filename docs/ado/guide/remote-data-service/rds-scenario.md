---
title: Scenario RDS | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: a7dcad87-aaf0-4b02-9660-472f8469761c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 665afeb4be263ae0772557d2d2f30e112596f289
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922441"
---
# <a name="rds-scenario"></a>Scenario RDS
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 L'applicazione Address Book è uno scenario in cui viene illustrato come utilizzare Remote Data Service (RDS) per creare un'applicazione Web semplice e compatibile con i dati, ovvero una rubrica aziendale online. Questo scenario è utile per i programmatori Microsoft Visual Basic Scripting Edition (VBScript) e COM che desiderano apprendere come usare i controlli ActiveX in grado di riconoscere i dati con Servizi Desktop remoto e per sviluppatori di software più esperti che desiderano creare applicazioni Web incentrate sui dati.  
  
 In questo scenario si presuppone che l'utente sia in grado di utilizzare i tag di layout HTML di base, di utilizzare le tecniche di data binding DHTML e di programmare con i controlli ActiveX.  
  
 Se è stato installato l'SDK, il codice sorgente completo per l'applicazione di esempio Address Book si trova nella directory SDK in samples\dataaccess\rds\AddressBook\AddressBook.asp. Per visualizzare lo scenario di Rubrica, in Internet Explorer 4,0 o versioni successive digitare **https://*webserver*/RDS/AddressBook/AddressBook.asp** dove *webserver* è il nome assegnato al computer server Web Windows NT 4,0 o Windows 2000 che esegue Internet Information Services (IIS) e ASP.  
  
## <a name="introduction-to-address-book"></a>Introduzione alla Rubrica  
 L'applicazione di esempio Address Book fornisce una semplice rubrica online che è possibile utilizzare per pubblicare una directory ricercabile su una rete Intranet. La Rubrica è progettata in modo che un utente possa immettere una stringa di ricerca in uno o più campi per richiedere informazioni sui dipendenti. Per visualizzare le funzionalità di base di Remote Data Service, l'applicazione di esempio viene mantenuta intenzionalmente piccola, con un numero minimo di oggetti e campi di ricerca.  
  
 L'interfaccia dell'applicazione è costituita dalle parti seguenti:  
  
-   RDS non visuale **. **Oggetto di associazione dati DataControl utilizzato dal client per connettersi al database.  
  
-   Caselle di testo HTML che fungono da campi di input per i criteri di ricerca degli attributi Employee.  
  
-   Pulsanti di comando HTML per compilare query, cancellare i campi di ricerca, aggiornare il database con le informazioni sui dipendenti, annullare le modifiche in sospeso e spostarsi tra le righe di dati visualizzate nella griglia.  
  
-   Il data binding DHTML per visualizzare i dati restituiti dalle query su un database back-end (tramite **RDS. **Oggetto di associazione dati di DataControl) in una tabella.  
  
-   Routine VBScript che connettono ogni elemento precedentemente indicato e consentono loro di interagire. Il codice VBScript viene utilizzato anche per inizializzare il Servizi Desktop remoto **. Oggetto DataControl** e creazione dinamica delle intestazioni di colonna nella tabella HTML dai nomi del Servizi Desktop remoto **. Campi recordset DataControl** .  
  
 Seguire i collegamenti da Step a step per configurare ed eseguire lo scenario e per altre informazioni sul funzionamento dello scenario.  
  
 Questo scenario contiene gli argomenti seguenti.  
  
-   [Requisiti di sistema per l'applicazione Address Book](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)  
  
-   [Esecuzione dello script SQL per Address Book](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)  
  
-   [Esecuzione dell'applicazione di esempio Address Book](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)  
  
-   [Oggetto di data binding di Address Book](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)  
  
-   [Pulsanti di comando di Address Book](../../../ado/guide/remote-data-service/address-book-command-buttons.md)  
  
-   [Pulsanti di spostamento di Address Book](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti di sistema per l'applicazione Address Book](../../../ado/guide/remote-data-service/system-requirements-for-the-address-book-application.md)   
 [Microsoft ActiveX Data Objects (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Esercitazione su RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)


