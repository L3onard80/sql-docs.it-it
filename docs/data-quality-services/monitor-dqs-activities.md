---
title: Monitorare le attività DQS
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.administration.activitymonitoring.f1
helpviewer_keywords:
- monitoring activity
- activity monitoring
ms.assetid: 1d4c76f3-0d7b-498e-b792-4db4a0349814
author: swinarko
ms.author: sawinark
ms.openlocfilehash: d9926eb251d109eb8ed9529a4ae739e8a1915b07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "75245460"
---
# <a name="monitor-dqs-activities"></a>Monitorare le attività DQS

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In questo argomento viene descritto come monitorare a livello centrale le attività seguenti in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS): individuazione delle informazioni, gestione del dominio, criteri di corrispondenza, pulizia dei dati, corrispondenza dei dati e pulizia SSIS.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Solo gli utenti con il ruolo dqs_administrator nel database DQS_Main possono terminare un'attività o arrestare un processo all'interno di un'attività.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
  
-   Per visualizzare le attività DQS è necessario disporre del ruolo dqs_kb_editor o dqs_kb_operator nel database DQS_MAIN.  
  
-   Per terminare un'attività o arrestare un processo all'interno di un'attività nonché visualizzare le attività DQS, è necessario disporre del ruolo dqs_administrator nel database DQS_MAIN.  
  
##  <a name="View"></a>Visualizzare le attività DQS  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Eseguire l'applicazione Data Quality Client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Monitoraggio attività**. Verrà visualizzata la schermata Monitoraggio attività.  
  
     ![Schermata Monitoraggio attività](../data-quality-services/media/dqs-activitymonitoring.gif "Schermata Monitoraggio attività")  
  
3.  Nella schermata Monitoraggio attività vengono visualizzate le informazioni su ogni attività in una griglia di attività. Nella griglia di attività vengono visualizzate le informazioni seguenti su ciascuna attività DQS:  
  
     **ID**: valore intero. Numero univoco dell'attività generato dal sistema per il monitoraggio delle attività.  
  
     **Nome**: nome della Knowledge base o del progetto Data Quality utilizzato per questa attività.  
  
     **Attivo**: indica se l'attività è attualmente attiva o meno. I valori possibili sono i seguenti:  
  
    -   **Attivo**: l'attività è attualmente in esecuzione.  
  
    -   **Terminato**: l'attività è stata completata.  
  
    -   **Terminato**: l'attività è stata terminata utilizzando la schermata Monitoraggio attività dall'amministratore DQS o l'attività è stata annullata dall'utente durante l'esecuzione nella rispettiva area [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]di funzionalità in.  
  
     **Tipo**: indica il tipo di attività. **Sub Type** indica il flusso di lavoro specifico eseguito per un tipo di attività. Vengono monitorati i tipi di attività seguenti:  
  
    -   Sottotipi di **Gestione informazioni** :  
  
        -   **Individuazione informazioni**  
  
        -   **Gestione del dominio**  
  
        -   **Criteri di corrispondenza**  
  
    -   Sottotipi di **progetto DQ** :  
  
        -   **Pulizia**  
  
        -   **Corrispondenza**  
  
    -   Sottotipi di **pulizia SSIS** :  
  
        -   **Pulizia**  
  
     **Current status**: indica lo stato corrente di un'attività. Lo stato dell'attività è determinato dall'ultimo processo di calcolo. Possono essere presenti diversi processi di calcolo in un'attività, ad esempio l'esecuzione ripetuta del processo di individuazione all'interno dell'attività di individuazione delle informazioni. Lo stato può pertanto cambiare diverse volte nel corso dell'attività.  
  
     **Lo stato corrente** può avere i valori seguenti:  
  
    -   **In esecuzione**: il processo di calcolo è in esecuzione.  
  
    -   **Succeeded**: questo stato viene impostato prima dell'esecuzione di un processo di calcolo e di nuovo dopo che un processo di calcolo termina correttamente.  
  
    -   **Non riuscito**: il processo di calcolo non è riuscito.  
  
    -   **Arrestato**: il processo di calcolo è stato arrestato.  
  
     **DQKB**: nome della Knowledge base utilizzata per l'attività.  
  
     **Utente**: nome dell'utente che ha avviato l'attività o ultimo utente che ha eseguito l'attività (in caso contrario).  
  
     **Ora di inizio attività**: data e ora di inizio dell'attività  
  
     **Tempo trascorso**: tempo trascorso dall'avvio dell'attività. Il valore viene visualizzato nella notazione HH:MM:SS.  
  
     **Ora di fine attività**: data e ora di fine dell'attività.  
  
##  <a name="Filter"></a>Filtrare le informazioni sull'attività DQS  
 È possibile utilizzare il riquadro dei filtri (**Filtra per**, **Valore**, **Da data**e **A data**) nella schermata Monitoraggio attività per filtrare e visualizzare le attività necessarie in base a un determinato criterio di filtro. Per filtrare i record dell'attività:  
  
1.  Decidere il criterio di filtro: specificare se si desidera filtrare i record dell'attività in base a un valore di una delle colonne nella griglia di attività (basato su valori) o in base a un intervallo di date oppure in base a entrambi i criteri.  
  
    1.  **Filtro basato su valori**: selezionare un criterio di filtro nell'elenco **Filtra per** , quindi selezionare il valore appropriato per filtrare in base all'elenco **valore** . Dopo aver selezionato un'opzione nell'elenco **Filtra per** , l'elenco **Valore** viene aggiornato con i valori possibili. È possibile applicare un filtro in base ai campi seguenti nei record dell'attività: **Attivo**, **Tipo**, **Sottotipo**, **Stato corrente**, **DQKB**e **Utente**.  
  
    2.  **Filtro basato sull'intervallo di date**: **selezionare le date** appropriate nei controlli data di inizio **e data** . Per impostazione predefinita, la data visualizzata in **Da data** precede di due giorni la data corrente e la data visualizzata in **A data** è la data corrente. Il filtro non viene applicato in base alle date di *inizio* e di *fine* , ma in base all'intervallo. Questo significa che verranno visualizzate tutte le attività in esecuzione durante l'intervallo di date selezionato.  
  
2.  Fare clic sull'icona **Aggiorna l'elenco di attività** per applicare il filtro e visualizzare solo le attività DQS filtrate.  
  
##  <a name="ActivityDetails"></a>Visualizza dettagli attività DQS  
 È possibile visualizzare le informazioni dettagliate di un'attività DQS, ad esempio le fasi dell'attività e le informazioni sul profiler, nella schermata Monitoraggio attività. A tale scopo, procedere come indicato di seguito:  
  
1.  Selezionare un'attività DQS nella griglia di attività (nel riquadro superiore).  
  
2.  Nel riquadro inferiore vengono visualizzati i dettagli dell'attività selezionata nelle 2 schede seguenti:  
  
    -   **Passaggi attività**: Visualizza una griglia dei processi di calcolo (fasi attività) associati all'attività selezionata. In questa scheda possono essere visualizzati diversi passaggi di attività per un'attività. Questo problema può verificarsi se lo stesso passaggio dell'attività all'interno dell'attività è stato eseguito più volte dall'utente. Ad esempio, nel caso in cui la fase dell'attività è stata arrestata e avviata di nuovo. Nella griglia in questa scheda vengono visualizzate le informazioni seguenti per ogni fase associata all'attività: **Tipo**, **Stato corrente**, **Ora di inizio**, **Tempo trascorso**e **Ora di fine**.  
  
    -   **Profiler**: Visualizza le informazioni di profilatura per le attività correnti e storiche. Per le attività correnti, contiene informazioni parziali ma coerenti. Le informazioni di profiling di un'attività vengono esportate in un file di Excel quando si esportano i dettagli dell'attività corrispondenti in un file di Excel. Le informazioni sono disponibili nei fogli **Profiler - Origine** e **Profiler - Campi** del file di Excel esportato.  
  
##  <a name="Export"></a>Esporta dettagli attività DQS  
 È possibile esportare in un file di Excel le proprietà, i processi e le informazioni di profiling di un'attività presenti nella schermata Monitoraggio attività. A tale scopo, procedere come indicato di seguito:  
  
1.  Selezionare un'attività nella griglia di attività (nel riquadro superiore).  
  
2.  Fare clic sull'icona **Esportare l'attività selezionata in Excel** . In alternativa, fare clic con il pulsante destro del mouse su un'attività nella griglia di attività, quindi scegliere **Esporta attività** nel menu di scelta rapida.  
  
3.  Viene richiesto di specificare un nome e un percorso per il file di Excel da salvare. Il file di Excel esportato contiene i fogli seguenti:  
  
    |Nome foglio|Descrizione|  
    |----------------|-----------------|  
    |Attività|Contiene le informazioni (colonne) sull'attività come riportato nella griglia di attività.|  
    |Processi|Contiene le informazioni (colonne) sui processi nell'attività come riportato nella scheda **Fasi attività** .|  
    |Profiler - Origine|Per il sottotipo **Pulizia** contiene le informazioni seguenti sull'attività: Record, Record corretti, Record con correzione e Record non validi.<br /><br /> Per i sottotipi **Individuazione informazioni**, **Gestione dominio**, **Criteri di corrispondenza**e **Corrispondenza** contiene le informazioni seguenti sull'attività: Record, Valori totali, Nuovi valori, Valori univoci e Nuovi valori univoci.|  
    |Profiler - Campi|Per i sottotipi **Pulizia** e **Pulizia SSIS** contiene le informazioni seguenti sull'attività: Campo, Dominio, Valori con correzione, Valori consigliati, Completezza e Accuratezza.<br /><br /> Per i sottotipi **Individuazione informazioni**, **Gestione dominio**, **Criteri di corrispondenza**e **Corrispondenza** contiene le informazioni seguenti sull'attività: Campo, Dominio, Nuovo, Univoco, Valido nel dominio e Completezza.|  
  
##  <a name="Terminate"></a>Termina un'attività DQS  
 Gli amministratori DQS (ruolo dqs_administrator) possono terminare un'attività in esecuzione (attiva) non di tipo **Pulizia SSIS**. Quando viene terminata un'attività, vengono arrestati tutti i processi in esecuzione nell'attività e viene rimosso tutto ciò che è correlato all'attività. Questa operazione non può essere annullata. Terminare un'attività nella schermata Monitoraggio attività equivale ad annullare la rispettiva attività facendo clic su **Annulla** durante l'esecuzione nell'area funzionale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Per terminare un'attività:  
  
1.  Selezionare un'attività in esecuzione nella griglia di attività (nel riquadro superiore).  
  
2.  Fare clic sull'icona **Termina l'attività selezionata** . In alternativa, fare clic con il pulsante destro del mouse sull'attività nella griglia di attività, quindi scegliere **Termina attività** nel menu di scelta rapida.  
  
3.  Verrà visualizzato un messaggio per confermare l'azione. Fare clic su **Sì**.  
  
##  <a name="Stop"></a>Arrestare un processo nell'attività DQS  
 Gli amministratori DQS (ruolo dqs_administrator) possono arrestare un processo in esecuzione (attivo) in un'attività non di tipo **Pulizia SSIS**. Arrestare un processo nella schermata Monitoraggio attività equivale ad arrestare il processo all'interno della rispettiva attività nell'area funzionale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Ad esempio, è possibile arrestare il processo di pulizia computerizzato all'interno di un'attività di pulizia o arrestare il processo di corrispondenza all'interno di un'attività corrispondente. Un processo arrestato non può essere riavviato dalla schermata Monitoraggio attività. È necessario riavviare il processo dall'area funzionale corrispondente nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. In tal caso, viene aggiunta una riga aggiuntiva alla griglia processi nella scheda **fasi attività** . Lo stato del processo arrestato continua a essere visualizzato come **arrestato**. Per arrestare un processo:  
  
1.  Selezionare un processo in esecuzione nella griglia Dettagli attività (nel riquadro inferiore).  
  
2.  Fare clic sull'icona **Arresta il processo selezionato** . In alternativa, fare clic con il pulsante destro del mouse sul processo nella griglia Dettagli attività, quindi scegliere **Arresta processo** nel menu di scelta rapida.  
  
3.  Verrà visualizzato un messaggio per confermare l'azione. Fare clic su **Sì**.  
  
  
