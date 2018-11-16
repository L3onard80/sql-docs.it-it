---
title: 'Passaggio 2: Aggiunta e configurazione di una gestione connessione file flat | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9a77dd32-d8c2-4961-ad37-2a971f9d6043
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c8ed30954131f756401f054c35992d3339dfddb5
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51638418"
---
# <a name="lesson-1-2---adding-and-configuring-a-flat-file-connection-manager"></a>Lezione 1-2 - Aggiunta e configurazione di una gestione connessione file flat
In questa attività si aggiungerà una gestione connessione file flat al pacchetto appena creato. Una gestione connessione file flat abilita un pacchetto all'estrazione di dati da un file flat. Utilizzando tale gestione connessione è possibile specificare il nome file e la posizione, le impostazioni locali e la tabella codici e il formato del file, inclusi i delimitatori di colonna, da applicare quando il pacchetto estrae i dati dal file flat. È anche possibile specificare manualmente il tipo di dati per le singole colonne o usare la finestra di dialogo **Suggerisci tipo di colonne** per eseguire automaticamente il mapping delle colonne di dati estratti ai tipi di dati di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
È necessario creare una nuova gestione connessione file flat per ogni formato di file da utilizzare. Dal momento che in questa esercitazione viene eseguita l'estrazione di dati da più file flat con lo stesso formato di dati, è necessario aggiungere e configurare una sola gestione connessione file flat al pacchetto.  
  
Per questa esercitazione si configureranno le seguenti proprietà nella gestione connessione file flat:  
  
-   **Nomi di colonne:** dal momento che il file flat non presenta nomi di colonne, con la gestione connessione file flat vengono creati nomi di colonna predefiniti. Questi nomi predefiniti non sono utili per identificare i dati rappresentati da ogni colonna. Per rendere questi nomi predefiniti più utili, è necessario modificarli in nomi che corrispondano alla tabella dei fatti in cui i dati dei file flat devono essere caricati.  
  
-   **Mapping dei dati:** i mapping dei tipi di dati specificati per la gestione connessione file flat verranno usati da tutti i componenti di origine dati dei file flat che fanno riferimento alla gestione connessione. È possibile eseguire manualmente il mapping dei tipi di dati usando la gestione connessione file flat oppure usare la finestra di dialogo **Suggerisci tipi di colonne** . In questa esercitazione verranno visualizzati i mapping suggeriti nella finestra di dialogo **Suggerisci tipi di colonne** e quindi verranno effettuati manualmente i mapping necessari nella finestra di dialogo **Editor gestione connessione file flat** .  
  
Gestione connessione file flat fornisce informazioni sulle impostazioni locali per il file di dati. Se il computer non è configurato per l'uso dell'opzione Inglese (Stati Uniti), è necessario impostare proprietà aggiuntive nella finestra di dialogo **Editor gestione connessione file flat** .  
  
### <a name="to-add-a-flat-file-connection-manager-to-the-ssis-package"></a>Per aggiungere una gestione connessione file flat al pacchetto SSIS.  
  
1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area **Gestioni connessioni** e quindi fare clic su **Nuova connessione file flat**.  
  
2.  Nella finestra di dialogo **Editor gestione connessione file flat** , per **Nome gestione connessione**, digitare **Sample Flat File Source Data**.  
  
3.  Fare clic su **Sfoglia**.  
  
4.  Nella finestra di dialogo **Apri** individuare il file SampleCurrencyData.txt nel computer.  
  
    I dati di esempio sono inclusi nei pacchetti di lezioni di [!INCLUDE[ssIS](../includes/ssis-md.md)] . Per scaricare i dati di esempio e i pacchetti di lezioni, effettuare le operazioni seguenti.  
  
    1.  Passare alla pagina relativa agli [esempi di prodotti di Integration Services](https://go.microsoft.com/fwlink/?LinkId=275027)  
  
    2.  Fare clic sulla scheda **DOWNLOADS** .  
  
    3.  Fare clic sul file SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
5.  Deselezionare i nomi di colonna nella prima casella di controllo della riga di dati.  
  
### <a name="to-set-locale-sensitive-properties"></a>Per impostare le proprietà dipendenti dalle impostazioni locali  
  
1.  Nella finestra di dialogo **Editor gestione connessione file flat** fare clic su **Generale**.  
  
2.  Impostare **Impostazioni locali** su Inglese (Stati Uniti) e **Tabella codici** su 1252.  
  
### <a name="to-rename-columns-in-the-flat-file-connection-manager"></a>Per rinominare le colonne nella gestione connessione file flat  
  
1.  Nella finestra di dialogo **Editor gestione connessione file flat** fare clic su **Avanzate**.  
  
2.  Nel riquadro delle proprietà apportare le seguenti modifiche:  
  
    -   Modificare la proprietà nome **Colonna 0** in **AverageRate**.  
  
    -   Modificare la proprietà nome **Colonna 1** in **CurrencyID**.  
  
    -   Modificare la proprietà nome **Colonna 2** in **CurrencyDate**.  
  
    -   Modificare la proprietà nome **Colonna 3** in **EndOfDayRate**.  
  
    > [!NOTE]  
    > Per impostazione predefinita, le quattro colonne sono inizialmente impostate su un tipo di dati stringa [DT_STR] con un valore **OutputColumnWidth** di 50.  
  
### <a name="to-remap-column-data-types"></a>Per modificare il mapping dei tipi di dati di colonna  
  
1.  Nella finestra di dialogo **Editor gestione connessione file flat** fare clic su **Suggerisci tipi**.  
  
    [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] indica automaticamente i tipi di dati più appropriati in base alle prime 200 righe di dati. È inoltre possibile modificare le opzioni suggerite in modo da campionare più o meno dati, specificare il tipo di dati predefinito per numeri interi o dati booleani oppure aggiungere spazi come spaziatura interna nelle colonne stringa.  
  
    Per il momento non apportare modifiche alle opzioni nella finestra di dialogo **Suggerisci tipi di colonne** e fare clic su **OK** in modo che [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggerisca i tipi di dati per le colonne. In questo modo verrà nuovamente visualizzato il riquadro **Avanzate** della finestra di dialogo **Editor gestione connessione file flat** in cui è possibile visualizzare i tipi di dati delle colonne suggeriti da [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Se si fa clic su **Annulla**non verranno indicati suggerimenti relativi ai metadati delle colonne e verrà usato il tipo di dati string predefinito, ovvero DT_STR.  
  
    In questa esercitazione, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suggerisce i tipi di dati mostrati nella seconda colonna della tabella seguente per i dati ricavati dal file SampleCurrencyData.txt. Tuttavia, i tipi di dati necessari per le colonne nella destinazione, che verranno definiti in una fase successiva, sono mostrati nell'ultima colonna della tabella che segue.  
  
    |Colonna file flat|Tipo suggerito|Colonna di destinazione|Tipo destinazione|  
    |--------------------|------------------|----------------------|--------------------|  
    |AverageRate|float [DT_R4]|FactCurrencyRate.AverageRate|FLOAT|  
    |CurrencyID|string [DT_STR]|DimCurrency.CurrencyAlternateKey|nchar(3)|  
    |CurrencyDate|date [DT_DATE]|DimDate.FullDateAlternateKey|Data|  
    |EndOfDayRate|float [DT_R4]|FactCurrencyRate.EndOfDayRate|FLOAT|  
  
    Il tipo di dati suggerito per la colonna **CurrencyID** non è compatibile con il tipo di dati del campo della tabella di destinazione. Dal momento che il tipo di dati di `DimCurrency.CurrencyAlternateKey` è nchar (3), **CurrencyID** deve essere modificato da stringa [DT_STR] in stringa Unicode [DT_WSTR]. Il campo `DimDate.FullDateAlternateKey` viene anche definito come tipo di dati relativo alla data, quindi **CurrencyDate** deve essere modificato da date [DT_Date] in database date [DT_DBDATE].  
  
2.  Nell'elenco selezionare la colonna CurrencyID e nel riquadro delle proprietà modificare il tipo di dati della colonna **CurrencyID** da string [DT_STR] in Unicode string [DT_WSTR].  
  
3.  Nel riquadro delle proprietà modificare il tipo di dati della colonna **CurrencyDate** da date [DT_DATE] a database date [DT_DBDATE].  
  
4.  Fare clic su **OK**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 3: Aggiunta e configurazione di una gestione connessione OLE DB](../integration-services/lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
## <a name="see-also"></a>Vedere anche  
[Gestione connessione file flat](../integration-services/connection-manager/flat-file-connection-manager.md)  
[Tipi di dati di Integration Services](../integration-services/data-flow/integration-services-data-types.md)  
  
  
  
