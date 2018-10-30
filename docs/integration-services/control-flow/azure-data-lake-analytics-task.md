---
title: Attività Azure Data Lake Analytics | Microsoft Docs
description: È possibile inviare processi U-SQL al servizio Azure Data Lake Analytics con l'attività Azure Data Lake Analytics.
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: a43a9d8d3b5ecf3f9d28f46db0b354891b40b183
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906081"
---
# <a name="azure-data-lake-analytics-task"></a>Attività Azure Data Lake Analytics

È possibile inviare processi U-SQL al servizio Azure Data Lake Analytics con l'attività Azure Data Lake Analytics. Questa attività è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Per informazioni generali, vedere [Azure Data Lake Analytics](https://azure.microsoft.com/services/data-lake-analytics/).

## <a name="configure-the-task"></a>Configurare l'attività

Per aggiungere un'attività Data Lake Analytics a un pacchetto, trascinarla dalla casella degli strumenti SSIS al canvas di progettazione. Fare quindi doppio clic sull'attività o fare clic con il pulsante destro del mouse sull'attività e scegliere **Modifica**. Verrà visualizzata la finestra di dialogo dell'**editor attività di Azure Data Lake Analytics**. È possibile impostare le proprietà tramite Progettazione SSIS o a livello di codice.

## <a name="general-page-configuration"></a>Configurazione della pagina Generale

Usare la pagina **Generale** per configurare l'attività e fornire lo script U-SQL inviato dall'attività. Per altre informazioni sul linguaggio U-SQL, vedere la [U-SQL language reference](https://msdn.microsoft.com/azure/data-lake-analytics/u-sql/u-sql-language-reference) (Guida di riferimento al linguaggio U-SQL).

### <a name="basic-configuration"></a>Configurazione di base

Specificare il nome e la descrizione dell'attività.

### <a name="u-sql-configuration"></a>Configurazione di U-SQL

La configurazione di U-SQL ha due impostazioni: **SourceType** e le opzioni dinamiche basate sul valore di **SourceType**. 

**SourceType** specifica l'origine dello script U-SQL. Lo script viene inviato a un account di Data Lake Analytics durante l'esecuzione del pacchetto SSIS. Le opzioni per questa proprietà sono:

|valore|Descrizione|  
|-----------|-----------------|  
|**DirectInput**|Specifica lo script U-SQL tramite l'editor inline. Selezionando questo valore, verrà visualizzata l'opzione dinamica **USQLStatement**.|  
|**FileConnection**|Specifica un file con estensione usql locale che contiene lo script U-SQL. Selezionando questa opzione, verrà visualizzata l'opzione dinamica **FileConnection**.|  
|**Variabile**|Specifica una variabile SSIS che contiene lo script U-SQL. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **SourceVariable**.|

**SourceType Dynamic Options** (Opzioni dinamiche per SourceType) specifica il contenuto dello script per la query U-SQL. 

|SourceType|Opzioni dinamiche|  
|-----------|-----------------|  
|**SourceType = DirectInput**|Digitare la query U-SQL da inviare direttamente nella casella di opzione oppure fare clic sul pulsante Sfoglia (...) per digitare la query U-SQL nella finestra di dialogo **Enter U-SQL Query** (Immettere la query U-SQL).|  
|**SourceType = FileConnection**|Selezionare una gestione connessione file esistente o selezionare <**Nuova connessione**> per creare una nuova connessione file. Per informazioni correlate, vedere [Gestione connessione file](../../integration-services/connection-manager/file-connection-manager.md) ed [Editor gestione connessione File](../../integration-services/connection-manager/file-connection-manager-editor.md).|  
|**SourceType = Variable**|Selezionare una variabile esistente oppure selezionare \<**Nuova variabile**> per creare una nuova variabile. Per informazioni correlate, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) e [Aggiungi variabile](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5).|


### <a name="job-configuration"></a>Configurazione del processo
La configurazione del processo specifica le proprietà di invio dei processi U-SQL.

- **AzureDataLakeAnalyticsConnection:** specifica l'account di Data Lake Analytics a cui viene inviato lo script U-SQL. Consente di scegliere una connessione da un elenco di gestioni connessione definite. Per creare una nuova connessione, selezionare <**Nuova connessione**>. Per informazioni correlate, vedere [Gestione connessione di Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md).

- **JobName:** specifica il nome del processo U-SQL. 
- **AnalyticsUnits:** specifica il numero di unità di analisi del processo U-SQL.
- **Priority:** specifica la priorità del processo U-SQL. È possibile impostare questa proprietà su un valore compreso tra 0 e 1000. A un numero minore corrisponde una priorità più alta.
- **RuntimeVersion:** specifica la versione di runtime di Data Lake Analytics del processo U-SQL. Per impostazione predefinita, l'opzione è impostata su "default". In genere non è necessario modificare questa proprietà.
- **Synchronous:** valore booleano che specifica se l'attività attende o meno il completamento dell'esecuzione del processo. Se il valore è impostato su true, l'attività viene contrassegnata come **riuscita**dopo il completamento del processo. Se il valore è impostato su false, l'attività verrà contrassegnata come **riuscita**al termine della fase di preparazione del processo.

  |valore|Descrizione|
  |-----------|-----------------|
  |True|Il risultato dell'attività è basato sul risultato dell'esecuzione del processo U-SQL. Il processo ha esito positivo > l'attività ha esito positivo. Il processo ha esito negativo > l'attività ha esito negativo. L'attività ha esito positivo o negativo > l'attività viene completata.|
  |False|Il risultato dell'attività è basato sul risultato della preparazione e dell'invio del processo U-SQL. L'invio del processo ha esito positivo e supera la fase di preparazione > l'attività ha esito positivo. L'invio del processo ha esito negativo o il processo non supera la fase di preparazione > l'attività ha esito negativo. L'attività ha esito positivo o negativo > l'attività viene completata.|

- **TimeOut:** specifica il timeout in secondi per l'esecuzione del processo. In caso di timeout, il processo viene annullato e contrassegnato come non riuscito. Questa proprietà non è disponibile se **Synchronous** è impostato su false.

## <a name="parameter-mapping-page-configuration"></a>Configurazione della pagina Mapping parametri

Usare la pagina **Mapping parametri** della finestra di dialogo dell'**editor dell'attività Azure Data Lake Analytics** per mappare variabili a parametri (variabili U-SQL) nello script U-SQL.

- **Nome variabile:** dopo aver aggiunto un mapping dei parametri, selezionando **Aggiungi**, selezionare una variabile di sistema o definita dall'utente nell'elenco. In alternativa, è possibile selezionare <**Nuova variabile**> per aggiungere una nuova variabile usando la finestra di dialogo **Aggiungi variabile**. Per informazioni correlate, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  

- **Nome parametro:** specificare un nome di parametro/variabile nello script U-SQL. Assicurarsi che il nome del parametro inizi con il simbolo \@, ad esempio \@Param1. 

Ecco un esempio di come passare i parametri per lo script U-SQL.

**Script U-SQL di esempio**
```
@searchlog =
    EXTRACT UserId          int,
            Start           DateTime,
            Region          string,
            Query           string,
            Duration        int,
            Urls            string,
            ClickedUrls     string
    FROM @in
    USING Extractors.Tsv(nullEscape:"#NULL#");

@rs1 =
    SELECT Start, Region, Duration
    FROM @searchlog
WHERE Region == "en-gb";

@rs1 =
    SELECT Start, Region, Duration
    FROM @rs1
    WHERE Start <= DateTime.Parse("2012/02/19");

OUTPUT @rs1   
    TO @out
      USING Outputters.Tsv(quoting:false, dateTimeFormat:null);
```

Si noti che i percorsi di input e output sono definiti nei parametri **\@in** e **\@out**. I valori dei parametri **\@in** e **\@out** nello script U-SQL vengono passati in modo dinamico dalla configurazione del mapping dei parametri.

|Nome variabile|Nome parametro|
|-------------|--------------|
|Utente: Variabile1|\@in|
|Utente: Variabile2|\@out| 

## <a name="expression-page-configuration"></a>Configurazione della pagina Espressioni

Tutte le proprietà nella configurazione della pagina Generale possono essere assegnate come espressione di proprietà per consentire l'aggiornamento dinamico della proprietà in fase di esecuzione. Per altre informazioni, vedere [Usare le espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md).

## <a name="see-also"></a>Vedere anche
- [Gestione connessioni di Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)
- [Attività File system di Azure Data Lake Store](../../integration-services/control-flow/azure-data-lake-store-file-system-task.md)
- [Gestione connessioni di Azure Data Lake Store](../../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

