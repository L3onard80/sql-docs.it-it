---
title: Eventi registrati da un pacchetto di Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package [Integration Services], events
- events [Integration Services], package
ms.assetid: 55a0951a-46f3-4f0f-9972-74cec9cc26b7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ef709a48f0c5c162e971cebbdf5d49c4417250ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62889840"
---
# <a name="events-logged-by-an-integration-services-package"></a>Eventi registrati da un pacchetto di Integration Services
  Un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] registra diversi messaggi di eventi nel registro eventi applicazioni di Windows. nel registro eventi applicazioni di Windows.  
  
 In questo argomento vengono fornite informazioni sui messaggi di evento comuni registrati da un pacchetto nel registro eventi applicazioni. Alcuni di questi messaggi vengono registrati per impostazione predefinita, anche se per il pacchetto non è stata abilitata la funzione di registrazione. Altri messaggi, invece, vengono registrati solo se tale funzione è stata abilitata. L'origine eventi per i messaggi è SQLISPackage, indipendentemente dal fatto che la registrazione avvenga per impostazione predefinita o perché è stata abilitata la funzione di registrazione.  
  
 Per informazioni generali sull'esecuzione dei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vedere [Esecuzione di progetti e pacchetti](../packages/run-integration-services-ssis-packages.md).  
  
 Per informazioni sulla risoluzione dei problemi relativi all'esecuzione dei pacchetti, vedere [Strumenti per la risoluzione dei problemi relativi all'esecuzione dei pacchetti](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="messages-about-the-status-of-the-package"></a>Messaggi relativi allo stato del pacchetto  
 Durante l'esecuzione, un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] di norma registra vari messaggi relativi al proprio stato e avanzamento. Tali messaggi sono elencati nella tabella seguente.  
  
> [!NOTE]  
>  I messaggi indicati nella tabella vengono registrati anche se non è stata abilitata la funzione di registrazione per il pacchetto.  
  
|ID evento|Nome simbolico|Text|Note|  
|--------------|-------------------|----------|-----------|  
|12288|DTS_MSG_PACKAGESTART|Esecuzione del pacchetto "" avviata|L'esecuzione del pacchetto è stata avviata.|  
|12289|DTS_MSG_PACKAGESUCCESS|Esecuzione del pacchetto "" completata.|Il pacchetto è stato eseguito correttamente e non è più in esecuzione.|  
|12290|DTS_MSG_PACKAGECANCEL|Il pacchetto "%1!s!" è stato annullato.|Il pacchetto non è più in esecuzione in quanto è stato annullato.|  
|12291|DTS_MSG_PACKAGEFAILURE|Esecuzione del pacchetto "" non riuscita.|L'esecuzione del pacchetto non è riuscita ed è stata arrestata.|  
  
 Per impostazione predefinita, in una nuova installazione, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene configurato in modo da non registrare alcuni eventi correlati all'esecuzione dei pacchetti nel registro eventi delle applicazioni. Questa impostazione impedisce la generazione di un numero eccessivo di voci del log eventi quando si usa la funzionalità Agente di raccolta dati della versione corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Gli eventi non registrati includono EventID 12288, che indica che il pacchetto è stato avviato ed EventID 12289 che indica che il pacchetto è stato completato. Per inserire questi due eventi nel registro eventi dell'applicazione, aprire il Registro di sistema per la modifica. Nel Registro di sistema individuare il nodo HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS e modificare il valore di DWORD dell'impostazione LogPackageExecutionToEventLog da 0 a 1. Tuttavia, nell'installazione di un aggiornamento [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è configurato per registrare questi due eventi. Per disabilitare la registrazione, modificare il valore dell'impostazione LogPackageExecutionToEventLog da 1 a 0.  
  
## <a name="messages-associated-with-package-logging"></a>Messaggi associati alla registrazione dei pacchetti  
 Se è stata abilitata la funzione di registrazione per il pacchetto, il registro eventi applicazioni è una delle destinazioni supportate dalle caratteristiche di registrazione facoltative nei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Per altre informazioni, vedere [registrazione di Integration Services &#40;SSIS&#41;](integration-services-ssis-logging.md).  
  
 Se è stata abilitata la funzione di registrazione per il pacchetto e il percorso del log è il registro eventi dell'applicazione, vengono registrate le voci che riguardano le informazioni seguenti:  
  
-   Messaggi relativi alle fasi di esecuzione del pacchetto.  
  
-   Messaggi relativi a eventi specifici che si verificano durante l'esecuzione del pacchetto.  
  
### <a name="messages-about-the-stages-of-package-execution"></a>Messaggi relativi alle fasi di esecuzione del pacchetto  
  
|ID evento|Nome simbolico|Text|Note|  
|--------------|-------------------|----------|-----------|  
|12544|DTS_MSG_EVENTLOGENTRY|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Quando si configura la funzione di registrazione per il pacchetto nel registro eventi applicazioni, vari messaggi utilizzano questo formato generico.|  
|12556|DTS_MSG_EVENTLOGENTRY_PACKAGESTART|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Il pacchetto è stato avviato.|  
|12547|DTS_MSG_EVENTLOGENTRY_PREVALIDATE|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|La convalida dell'oggetto sta per iniziare.|  
|12548|DTS_MSG_EVENTLOGENTRY_POSTVALIDATE|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|La convalida dell'oggetto è stata completata.|  
|12552|DTS_MSG_EVENTLOGENTRY_PROGRESS|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Questo messaggio generico segnala lo stato di avanzamento del pacchetto.|  
|12546|DTS_MSG_EVENTLOGENTRY_POSTEXECUTE|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Le operazioni previste per l'oggetto sono state completate.|  
|12557|DTS_MSG_EVENTLOGENTRY_PACKAGEEND|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|L'esecuzione del pacchetto è completata.|  
  
### <a name="messages-about-events-that-occur"></a>Messaggi relativi agli eventi  
 Nella tabella seguente sono elencati solo alcuni dei messaggi restituiti in seguito a eventi. Per un elenco più completo dei messaggi di errore, di avviso e informativi usati da [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vedere [Guida di riferimento ai messaggi e agli errori di Integration Services](../integration-services-error-and-message-reference.md).  
  
|ID evento|Nome simbolico|Text|Note|  
|--------------|-------------------|----------|-----------|  
|12251|DTS_MSG_EVENTLOGENTRY_TASKFAILED|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Impossibile eseguire l'attività.|  
|12250|DTS_MSG_EVENTLOGENTRY_ERROR|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Questo messaggio segnala un errore.|  
|12249|DTS_MSG_EVENTLOGENTRY_WARNING|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Questo messaggio segnala un avviso.|  
|12258|DTS_MSG_EVENTLOGENTRY_INFORMATION|Nome evento: %1%r Messaggio: %9%r Operatore: %2%r Nome origine: %3%r ID origine: %4%r ID esecuzione: %5%r Ora inizio: %6%r Ora fine: %7%r Codice dati: %8|Questo messaggio segnala informazioni non associate a un errore o a un avviso.|  
  
## <a name="related-tasks"></a>Attività correlate  
 Per informazioni su come visualizzare le voci di log in tempo reale, vedere [Visualizzare le voci di log nella finestra Registra eventi](../view-log-entries-in-the-log-events-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi registrati dal servizio Integration Services](../service/events-logged-by-the-integration-services-service.md)  
  
  
