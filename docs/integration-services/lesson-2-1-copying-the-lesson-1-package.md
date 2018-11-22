---
title: 'Passaggio 1: Copia del pacchetto della lezione 1 | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b7638d36f78853612c312880cd9698625af1ffe3
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51640478"
---
# <a name="lesson-2-1---copying-the-lesson-1-package"></a>Lezione 2-1 - Copia del pacchetto della lezione 1
In questa attività si procederà alla creazione di una copia del pacchetto della lezione 1, denominato Lesson 1.dtsx. Se non è stata completata la lezione 1, è possibile aggiungere al progetto il pacchetto completo della lezione 1 incluso nell'esercitazione e quindi copiarlo. Questa nuova copia verrà usata per tutto il seguito della lezione 2.  
  
### <a name="to-create-the-lesson-2-package"></a>Per creare il pacchetto della lezione 2  
  
1.  Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools non è già aperto, fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server 2012**, quindi selezionare **SQL Server Data Tools**.  
  
2.  Scegliere **Apri** dal menu **File**, fare clic su **Progetto/Soluzione**, selezionare la cartella **SSIS Tutorial** , fare clic su **Apri**e quindi fare doppio clic su **SSIS Tutorial.sln**.  
  
3.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Lesson 1.dtsx**e quindi scegliere **Copia**.  
  
4.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Pacchetti SSIS** e quindi scegliere **Incolla**.  
  
    Per impostazione predefinita, il pacchetto copiato verrà denominato Lesson 2.dtsx.  
  
5.  In Esplora soluzioni fare doppio clic su **Lesson 2.dtsx** per aprire il pacchetto  
  
6.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area di progettazione **Flusso di controllo** e scegliere **Proprietà**.  
  
7.  Nella finestra Proprietà aggiornare la proprietà **Name** impostandola su **Lesson 2**.  
  
8.  Fare clic sulla casella relativa alla proprietà **ID**, fare clic sulla freccia a discesa, quindi scegliere **\<Genera nuovo ID\>**.  
  
### <a name="to-add-the-completed-lesson-1-package"></a>Per aggiungere il pacchetto della lezione 1 completato  
  
1.  Aprire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools e il progetto SSIS Tutorial.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse su **Pacchetti SSIS**e scegliere **Aggiungi pacchetto esistente**.  
  
3.  Nella finestra di dialogo **Aggiungi copia del pacchetto esistente** in **Posizione pacchetto**selezionare **File system**.  
  
4.  Fare clic sul pulsante **(…)** , passare a **Lesson 1.dtsx** nel computer e quindi fare clic su **Apri**.  
  
    Per scaricare tutti i pacchetti di lezioni di questa esercitazione, effettuare le operazioni seguenti.  
  
    1.  Passare alla pagina degli [esempi del prodotto di Integration Services](https://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Fare clic sulla scheda **DOWNLOADS** .  
  
    3.  Fare clic sul file SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Copiare e incollare il pacchetto della lezione 1, come illustrato nei passaggi 3-8 della procedura precedente.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 2: Aggiunta e configurazione del contenitore Ciclo Foreach](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
