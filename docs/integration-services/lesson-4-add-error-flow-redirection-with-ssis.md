---
title: 'Lezione 4: Aggiungere il reindirizzamento del flusso errato con SSIS | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 94a34901743b462ea4fd8a4f36d381b789c360f2
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51637878"
---
# <a name="lesson-4-add-error-flow-redirection-with-ssis"></a>Lezione 4: Aggiungere il reindirizzamento del flusso errato tramite SSIS
Per gestire gli errori che si verificano durante il processo di trasformazione, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consente di decidere sulla base dei singoli componenti e delle singole colonne come gestire i dati che non possono essere trasformati. È possibile scegliere di ignorare un errore in alcune colonne, reindirizzare l'intera riga con esito negativo o interrompere l'esecuzione del componente. Per impostazione predefinita, tutti i componenti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sono configurati in modo da interrompersi quando si verificano errori. L'arresto di un componente determina l'arresto del pacchetto e di conseguenza di tutte le elaborazioni successive.  
  
Anziché arrestare l'esecuzione del pacchetto a causa degli errori, è consigliabile configurare e gestire potenziali errori di elaborazione nel momento stesso in cui si verificano durante la trasformazione. Sebbene sia possibile decidere di ignorare gli errori in modo da garantire l'esecuzione dei pacchetti, è talvolta opportuno reindirizzare la riga con esito negativo a un altro percorso di elaborazione in cui i dati e gli errori possono essere mantenuti e quindi essere esaminati e rielaborati in un momento successivo.  
  
In questa lezione verrà creata una copia del pacchetto sviluppato in [Lezione 3: Aggiungere la registrazione tramite SSIS](../integration-services/lesson-3-add-logging-with-ssis.md). L'utilizzo di questo nuovo pacchetto consentirà di creare una versione danneggiata di uno dei file di dati di esempio. Durante l'esecuzione del pacchetto, il file danneggiato forzerà la generazione di un errore di elaborazione.  
  
Per gestire i dati dell'errore verrà aggiunta e configurata una destinazione file flat che consente di scrivere in un file tutte le righe che non riescono a individuare un valore di ricerca nella trasformazione Lookup Currency Key.  
  
Prima che i dati dell'errore vengano scritti nel file, si includerà un componente script che usa uno script per ottenere le descrizioni degli errori. La trasformazione Lookup Currency Key verrà quindi riconfigurata in modo che i dati che non possono essere elaborati vengano reindirizzati alla trasformazione Script.  
  
> [!IMPORTANT]  
> Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e sulla distribuzione di **AdventureWorksDW2012**, vedere la pagina relativa agli [ esempi del prodotto Reporting Services su CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910)  
  
## <a name="tasks-in-lesson"></a>Argomenti della lezione  
In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto della lezione 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Passaggio 2: Creazione di un file danneggiato](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Passaggio 3: Aggiunta del reindirizzamento del flusso degli errori](../integration-services/lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Passaggio 4: Aggiunta di una destinazione file flat](../integration-services/lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Passaggio 5: Test del pacchetto creato nella lezione 4 dell'esercitazione](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
[Passaggio 1: Copia del pacchetto della lezione 3](../integration-services/lesson-4-1-copying-the-lesson-3-package.md)  
  
  
  
