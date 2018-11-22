---
title: "Passaggio 4: Test del pacchetto creato nella lezione 2 dell'esercitazione | Microsoft Docs"
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5f612768d1e4cd6bff6be8204b38c0a99e1eb285
ms.sourcegitcommit: 7e828cd92749899f4e1e45ef858ceb9a88ba4b6a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51629514"
---
# <a name="lesson-2-4---testing-the-lesson-2-tutorial-package"></a>Lezione 2-4 - Test del pacchetto creato nella lezione 2 dell'esercitazione
Dopo aver configurato il contenitore Ciclo Foreach e la gestione connessione file flat, il pacchetto creato nella lezione 2 consente di eseguire un'iterazione dell'insieme di 14 file flat contenuti nella cartella Sample Data. Ogni volta che viene trovato un nome di file corrispondente ai criteri specificati, il contenitore Ciclo Foreach popola la variabile definita dall'utente con il nome del file. Tale variabile aggiorna di conseguenza la proprietà ConnectionString della gestione connessione file flat e viene stabilita una connessione al nuovo file flat. Il contenitore Ciclo Foreach quindi esegue l'attività del flusso di dati non modificati sui dati del nuovo file flat prima di connettersi al file successivo contenuto nella cartella.  
  
Utilizzare la procedura seguente per verificare la funzionalità relativa ai cicli aggiunta al pacchetto.  
  
> [!NOTE]  
> Se si esegue il pacchetto della lezione 1, sarà necessario eliminare i record da dbo.NewFactCurrencyRate in AdventureWorksDW2012 prima di eseguire il pacchetto di questa lezione. In caso contrario, il pacchetto non verrà eseguito correttamente e verranno generati errori indicanti una violazione del vincolo di chiave primaria. Verranno restituiti gli stessi errori se si esegue il pacchetto selezionando Debug/Avvia debug (o premendo F5) perché verranno eseguite entrambe le lezioni 1 e 2. Tramite la lezione 2 si tenterà di inserire record già inseriti nella lezione 1.  
  
## <a name="checking-the-package-layout"></a>Verifica del layout del pacchetto  
Prima di testare il pacchetto, è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 2 contengano gli oggetti visualizzati nei diagrammi seguenti. Il flusso di dati deve essere identico a quello nella lezione 1.  
  
**Flusso di controllo**  
  
![Flusso di controllo nel pacchetto](../integration-services/media/task4lesson2control.gif "Flusso di controllo nel pacchetto")  
  
**Flusso di dati**  
  
![Flusso di dati nel pacchetto](../integration-services/media/task9lesson1data.gif "Flusso di dati nel pacchetto")  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a>Per testare il pacchetto creato nella lezione 2 dell'esercitazione  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Lesson 2.dtsx** e scegliere **Esegui pacchetto**.  
  
    Il pacchetto verrà eseguito. È possibile verificare lo stato di ogni ciclo nella finestra Output o facendo clic sulla scheda **Stato** . Ad esempio, viene evidenziato che sono state aggiunte 1097 righe alla tabella di destinazione dal file Currency_VEB.txt.  
  
2.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 5: Aggiungere configurazioni del pacchetto SSIS per il modello di distribuzione del pacchetto](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di progetti e pacchetti](~/integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
  

