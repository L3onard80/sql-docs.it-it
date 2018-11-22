---
title: 'Lezione 2: Aggiungere cicli con SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed4b198ab8f0582f3e01cfaca957af4f72e343e2
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51641218"
---
# <a name="lesson-2-adding-looping-with-ssis"></a>Lezione 2: Aggiungere cicli con SSIS
Nella [Lezione 1: Creare un progetto e un pacchetto di base con SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md) è stato creato un pacchetto che ha estratto i dati da un'unica origine file flat, ha trasformato i dati usando la trasformazione Ricerca e infine ha caricato i dati in una copia della tabella dei fatti **FactCurrencyRate** del database di esempio **AdventureWorksDW2012**.  
  
Tuttavia, per un processo di estrazione, trasformazione e caricamento (ETL, Extract, Transform and Loading) raramente viene usato un unico file flat. In genere durante un processo ETL i dati vengono estratti da più origini file flat. L'estrazione dei dati da più origini richiede un flusso di controllo iterativo. Una delle caratteristiche più attese di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste nella possibilità di aggiungere facilmente iterazioni o cicli ai pacchetti.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offre due tipi di contenitori per eseguire i cicli di pacchetti: il contenitore Ciclo Foreach e il contenitore Ciclo For. Nel contenitore Ciclo Foreach viene usato un enumeratore per eseguire il ciclo mentre nel contenitore Ciclo For viene usata in genere un'espressione di variabili. Questa lezione prevede l'uso del contenitore Ciclo Foreach.  
  
Il contenitore Ciclo Foreach consente a un pacchetto di ripetere il flusso di controllo per ogni membro di un enumeratore specificato. Il contenitore Ciclo Foreach consente di enumerare:  
  
-   Righe di un recordset ADO  
  
-   Informazioni sullo schema ADO .NET  
  
-   Strutture di file e directory  
  
-   Variabili utente, di sistema e del pacchetto  
  
-   Oggetti enumerabili contenuti in una variabile  
  
-   Elementi di una raccolta  
  
-   Nodi in un'espressione XPATH  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Oggetti SMO (Management Objects)  
  
In questa lezione verranno illustrate le procedure per modificare il pacchetto ETL semplice creato nella lezione 1 usando il contenitore Ciclo Foreach. Verranno inoltre impostate le variabili del pacchetto definite dall'utente in modo che nel pacchetto creato nell'esercitazione sia possibile scorrere tutti i file flat contenuti nella cartella. Se non è stata completata la lezione precedente, è possibile copiare il pacchetto della lezione 1 completato incluso nell'esercitazione.  
  
In questa lezione verrà modificato solo il flusso di controllo, non il flusso di dati.  
  
> [!IMPORTANT]  
> Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e sulla distribuzione di **AdventureWorksDW2012**, vedere [Esempi di Reporting Services su CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto della lezione 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Passaggio 2: Aggiunta e configurazione del contenitore Ciclo Foreach](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Passaggio 3: Modifica della gestione connessione file flat](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Passaggio 4: Test del pacchetto creato nell'esercitazione della lezione 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
[Passaggio 1: Copia del pacchetto della lezione 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>Vedere anche  
[Contenitore Ciclo For](../integration-services/control-flow/for-loop-container.md)  
  
  
  
