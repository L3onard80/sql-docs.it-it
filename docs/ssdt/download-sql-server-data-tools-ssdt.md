---
title: Scaricare SQL Server Data Tools (SSDT)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssdt
ms.topic: conceptual
keywords: installare ssdt, scaricare ssdt, versione più recente di ssdt
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 02/20/2020
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: f6a7628d324236a8fbbe7afa5b80c746f95fec13
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "80271487"
---
# <a name="download-sql-server-data-tools-ssdt-for-visual-studio"></a>Scaricare SQL Server Data Tools per Visual Studio (SSDT)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

**SQL Server Data Tools (SSDT)** è uno strumento di sviluppo moderno che consente di compilare database relazionali SQL Server, database SQL di Azure, modelli di dati di Analysis Services (AS), pacchetti di Integration Services (IS) e report di Reporting Services (RS). Con SSDT è possibile progettare e distribuire qualsiasi tipo di contenuto SQL Server con la stessa facilità con la quale si sviluppa un'applicazione in Visual Studio.

## <a name="ssdt-for-visual-studio-2019"></a>SSDT per Visual Studio 2019

### <a name="changes-in-ssdt-for-visual-studio-2019"></a>Modifiche in SSDT per Visual Studio 2019

La funzionalità di base di SSDT per la creazione di progetti di database è rimasta parte integrante di Visual Studio.

Con Visual Studio 2019, le funzionalità necessarie per abilitare i progetti di Analysis Services, Integration Services e Reporting Services sono state spostate nelle rispettive estensioni di Visual Studio.

> [!NOTE]
> Non è disponibile alcun programma di installazione autonomo SSDT per Visual Studio 2019.

### <a name="install-ssdt-with-visual-studio-2019"></a>Installare SSDT con Visual Studio 2019

Se [Visual Studio 2019](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019) è già installato, è possibile modificare l'elenco dei carichi di lavoro per includere SSDT.

* Per i progetti di database SQL, selezionare **SQL Server Data Tools** in **Elaborazione ed archiviazione dati**.

   ![Carico di lavoro Elaborazione ed archiviazione dati](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload-2019.png)

* Per i progetti di Analysis Services, Integration Services o Reporting Services, è possibile installare le [estensioni](https://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions) appropriate da *Strumenti > Estensioni e aggiornamenti* o dal [Marketplace](https://marketplace.visualstudio.com/search?term=services&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance).

Se Visual Studio 2019 non è installato, è possibile scaricare e installare [Visual Studio 2019 Community](https://visualstudio.microsoft.com/downloads/). 

* Per i progetti di database SQL, selezionare **SQL Server Data Tools** in **Elaborazione ed archiviazione dati** nell'elenco dei carichi di lavoro durante l'installazione.

* Per i progetti di Analysis Services, Integration Services o Reporting Services, è possibile installare le [estensioni](https://docs.microsoft.com/visualstudio/ide/finding-and-using-visual-studio-extensions) appropriate da *Strumenti > Estensioni e aggiornamenti* o dal [Marketplace](https://marketplace.visualstudio.com/search?term=services&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance).

## <a name="ssdt-for-visual-studio-2017"></a>SQL Server Data Tools (SSDT) per Visual Studio 2017

### <a name="changes-in-ssdt-for-visual-studio-2017"></a>Modifiche in SSDT per Visual Studio 2017

A partire da Visual Studio 2017, la funzionalità di creazione di progetti di database è stata integrata nell'installazione di Visual Studio. Non è necessario installare il programma di installazione autonomo di SSDT per l'esperienza principale di SSDT.

Per creare progetti di Analysis Services, Integration Services o Reporting Services è ora ancora necessario il programma di installazione autonomo di SSDT.

### <a name="install-ssdt-with-visual-studio-2017"></a>Installare SSDT con Visual Studio 2017

Per installare SSDT durante l'[installazione di Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), selezionare il carico di lavoro **Elaborazione ed archiviazione dati** e quindi selezionare **SQL Server Data Tools**.

Se Visual Studio è già installato, è possibile [modificare l'elenco dei carichi di lavoro](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) per includere SSDT.

![Carico di lavoro Elaborazione ed archiviazione dati](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload-2017.png)

### <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installare Analysis Services, Integration Services e Reporting Services

Per installare il supporto di progetti di Analysis Services, Integration Services e Reporting Services, eseguire il [programma di installazione SSDT autonomo](#ssdt-for-vs-2017-standalone-installer).

Il programma di installazione elenca le istanze di Visual Studio disponibili per l'aggiunta degli strumenti SSDT. Se Visual Studio non è già installato, selezionando **Install a new SQL Server Data Tools instance** (Installa una nuova istanza di SQL Server Data Tools) è possibile installare SSDT con una versione minima di Visual Studio. Per un'esperienza ottimale, tuttavia, è consigliabile usare SSDT con [la versione più recente di Visual Studio](https://www.visualstudio.com/downloads).

![Selezionare AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)

## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT per Visual Studio 2017 (programma di installazione autonomo)

[![download](../ssdt/media/download.png) Download di SSDT per Visual Studio 2017 (15.9.4)](https://go.microsoft.com/fwlink/?linkid=2124518 )

> [!IMPORTANT]
> * Prima di installare SSDT per Visual Studio 2017 (15.9.4), disinstallare le estensioni *Progetti di Analysis Services* e *Progetti di Reporting Services*, se già installate, e chiudere tutte le istanze di Visual Studio.
> * È stato rimosso il componente della posta in arrivo Origine Power Query per SQL Server 2017. È stato annunciato Origine Power Query per SQL Server 2017 e 2019 come componente predefinito. È possibile scaricarlo [qui](https://www.microsoft.com/download/details.aspx?id=100619).
> * È stato rimosso il componente della posta in arrivo Microsoft Connector per Oracle per SQL Server 2019. È stato annunciato Microsoft Connector per Oracle per SQL Server 2019 come componente predefinito. È possibile scaricarlo [qui](https://www.microsoft.com/download/details.aspx?id=58228).

### <a name="release-notes"></a>Note sulla versione

Per un elenco completo delle modifiche, vedere [Note sulla versione per SQL Server Data Tools (SSDT)](release-notes-ssdt.md).

### <a name="system-requirements"></a>Requisiti di sistema

SSDT per Visual Studio 2017 ha gli stessi [requisiti di sistema](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) di Visual Studio.

### <a name="available-languages---ssdt-for-vs-2017"></a>Lingue disponibili - SSDT per VS 2017

Questa versione di **SSDT per VS 2017** può essere installata nelle lingue seguenti:

* [Cinese semplificato]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x804)
* [Cinese tradizionale]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x404)
* [Inglese (Stati Uniti)]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x409)
* [Francese]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x40c)
* [Tedesco]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x407)
* [Italiano]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x410)
* [Giapponese]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x411)
* [Coreano]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x412)
* [Portoghese (Brasile)]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x416)
* [Russo]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x419)
* [Spagnolo]( https://go.microsoft.com/fwlink/?linkid=2124518&clcid=0x40a)

### <a name="considerations-and-limitations"></a>Considerazioni e limiti

* Non è possibile installare la versione community offline

* Per aggiornare SSDT, è necessario seguire lo stesso percorso usato per installare SSDT. Ad esempio, se SSDT è stato aggiunto usando le estensioni VSIX, è necessario eseguire l'aggiornamento tramite le estensioni VSIX. Se SSDT è stato installato tramite un'installazione distinta, è necessario eseguire l'aggiornamento usando tale metodo.

## <a name="offline-install"></a>Eseguire l'installazione offline

Per installare SSDT quando non si è connessi a Internet, seguire la procedura descritta in questa sezione. Per altre informazioni, vedere [Creare un'installazione di rete di Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio).

Per prima cosa, completare la procedura seguente mentre si è **online**:

1. [Scaricare il programma di installazione autonomo di SSDT](#ssdt-for-vs-2017-standalone-installer).

2. [Scaricare vs_sql.exe](https://aka.ms/vs/15/release/vs_sql.exe).

3. Mentre si è ancora online, eseguire uno dei comandi seguenti per scaricare tutti i file necessari per l'installazione offline. L'uso dell'opzione `--layout` è fondamentale, in quanto scarica i file effettivi per l'installazione offline. Sostituire `<filepath>` con il tracciato di layout effettivo in cui salvare i file.
   1. Per una lingua specifica, passare le impostazioni locali: `vs_sql.exe --layout c:\<filepath> --lang en-us` (una sola lingua corrisponde a circa 1 GB).
   1. Per tutte le lingue, omettere l'argomento `--lang`: `vs_sql.exe --layout c:\<filepath>` (tutte le lingue corrispondono a circa 3,9 GB).

Dopo aver completato questa procedura, i passaggi seguenti possono essere eseguiti **offline**:

1. Eseguire `vs_setup.exe --NoWeb` per installare la shell di Visual Studio 2017 e il progetto di dati di SQL Server.

2. Dalla cartella dei layout eseguire `SSDT-Setup-ENU.exe /install` e selezionare SSIS/SSRS/SSAS.
   * Per un'installazione automatica, eseguire `SSDT-Setup-ENU.exe /INSTALLALL[:vsinstances] /passive`.

Per le opzioni disponibili, eseguire `SSDT-Setup-ENU.exe /help`

> [!NOTE]
> Se si usa una versione completa di Visual Studio 2017, creare una cartella offline solo per SSDT e quindi eseguire `SSDT-Setup-ENU.exe` da questa nuova cartella (non aggiungere SSDT a un altro layout offline di Visual Studio 2017). Se si aggiunge il layout SSDT a un layout offline di Visual Studio esistente, i componenti di runtime necessari (exe) non vengono creati in tale layout.

## <a name="supported-sql-versions"></a>Versioni di SQL supportate

|Modelli di progetto|Piattaforme SQL supportate|
|-------------------|--------------------|
|Database relazionali| SQL Server 2005\* - SQL Server 2017<br> (usare SSDT 17.x o SSDT per Visual Studio 2017 per la connessione a [SQL Server in Linux](../linux/sql-server-linux-overview.md))<br /><br />database SQL di Azure<br /><br />Azure SQL Data Warehouse (supporta solo query, i progetti di database non sono ancora supportati)<br /><br /> \* Il supporto per SQL Server 2005 è deprecato<br /><br /> e si consiglia di passare a una versione di SQL supportata ufficialmente|
|Modelli di Analysis Services<br /><br />Report di Reporting Services | SQL Server 2008 - SQL Server 2017|
|pacchetti di Integration Services| SQL Server 2012 - SQL Server 2019 |

## <a name="dacfx"></a>DacFx

SSDT per Visual Studio 2015 e 2017 usano entrambi DacFx 17.4.1: [Download del framework applicazione livello dati (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).

## <a name="previous-versions"></a>Versioni precedenti

Per scaricare e installare SSDT per Visual Studio 2015 o una versione precedente di SSDT, vedere [Versioni precedenti di SQL Server Data Tools (SSDT e SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo l'installazione di SSDT, eseguire queste esercitazioni per imparare a creare database, pacchetti, modelli di dati e report mediante SSDT.

* [Sviluppo di database offline orientato ai progetti](project-oriented-offline-database-development.md)

* [Esercitazione SSIS: Creare un pacchetto ETL semplice](../integration-services/ssis-how-to-create-an-etl-package.md)

* [Esercitazioni su Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services-tutorials-ssas)

* [Creare un report tabella semplice (esercitazione su SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="see-also"></a>Vedere anche

* [Forum MSDN di SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt) 

* [Blog del Team di SSDT](https://blogs.msdn.com/b/ssdt/)

* [Riferimento all'API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)

* [Scaricare SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
