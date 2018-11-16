---
title: Gestione del Server di SQL Server Analysis Services | Microsoft Docs
ms.date: 11/15/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 41c689b2dfb122b94204cfbb8d52f9f8e9a1a8fb
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700439"
---
# <a name="sql-server-analysis-services-server-management"></a>Gestione del server SQL Server Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Per Azure Analysis Services, vedere [gestire Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-manage).

  Un'istanza del server di Analysis Services è una copia del **msmdsrv.exe** eseguibile che viene eseguito come servizio di sistema operativo. Ogni istanza è completamente indipendente dalle altre istanze nello stesso server, disponendo di impostazioni proprie di configurazione, autorizzazioni, porte, account di avvio, archiviazione di file e proprietà della modalità server.  
  
 Ogni istanza viene eseguita come servizio Windows, Msmdsrv.exe, nel contesto di sicurezza di un account di accesso definito.  
  
-   Il nome del servizio dell'istanza predefinita è MSSQLServerOLAPService.  
  
-   Il nome del servizio di ogni istanza denominata di è MSOLAP$ InstanceName.  
  
> [!NOTE]  
>  Se sono installate più istanze, il programma di installazione installa anche un servizio redirector, integrato con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizio Browser. Il servizio redirector è responsabile dell'indirizzamento dei client all'istanza denominata appropriata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser viene sempre eseguito nel contesto di sicurezza dell'account Servizio locale, un account utente limitato utilizzato da Windows per servizi che non accedono a risorse esterne al computer locale.  
  
 L'espressione a più istanze indica la possibilità di scalabilità verticale mediante l'installazione di più istanze del server nello stesso hardware. Per Analysis Services in particolare, indica inoltre la possibilità di supportare modalità server diverse disponendo di più istanze nello stesso server, ciascuna configurata per l'esecuzione in una modalità specifica.  
  
 La modalità server è una proprietà del server che determina quale architettura di archiviazione e memoria viene utilizzata per tale istanza. Un server in esecuzione in modalità multidimensionale utilizza il livello di gestione delle risorse compilato per database di cubi multidimensionali e modelli di data mining. Al contrario, la modalità server tabulare usa il motore di analisi in memoria VertiPaq e la compressione dati per aggregare i dati quando richiesti.  
  
 Le differenze nell'architettura di archiviazione e memoria significano che una sola istanza di Analysis Services eseguirà database tabulari o database multidimensionali, ma non entrambi. La proprietà della modalità server determina quale tipo di database viene eseguito nell'istanza.  
  
 La modalità server viene impostata durante l'installazione quando si specifica il tipo di database che verrà eseguito nel server. Per supportare tutte le modalità disponibili, è possibile installare più istanze di Analysis Services, ciascuna distribuita in una modalità server corrispondente ai progetti che vengono compilati.  
  
 In generale, la maggior parte delle attività amministrative da eseguire non variano a seconda della modalità. Un amministratore di sistema di Analysis Services può utilizzare le stesse routine e gli stessi script per gestire qualsiasi istanza di Analysis Services nella rete, indipendentemente dalla modalità di installazione.  
  
> [!NOTE]  
>  L'eccezione è [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint. L'amministrazione server di una distribuzione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] è sempre all'interno del contesto di una farm SharePoint. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] si differenzia dalle altre modalità server perché è sempre a istanza singola ed è sempre gestito da Amministrazione centrale SharePoint o dallo strumento di configurazione [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Benché sia possibile, non è consigliabile connettersi a [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint in SQL Server Management Studio o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. In una farm SharePoint è presente un'infrastruttura mediante la quale viene sincronizzato lo stato del server e controllata la disponibilità del server. L'utilizzo di altri strumenti può interferire con queste operazioni. Per altre informazioni sulle [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Amministrazione server, vedere [Power Pivot per SharePoint ](../../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md).  
  
## <a name="common-server-management-topics"></a>Argomenti relativi alla gestione di server comune  
  
|Collegamento|Descrizione dell'attività|  
|----------|----------------------|  
|[Configurazione successiva all'installazione](../../analysis-services/instances/post-install-configuration-analysis-services.md)|Descrive le attività necessarie e facoltative per completare o modificare un'installazione di Analysis Services.|  
|[Connettersi ad Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)|Descrive le proprietà delle stringhe di connessione, le librerie client, le metodologie di autenticazione e le procedure per stabilire o cancellare le connessioni.|  
|[Monitorare un'istanza di Analysis Services](../../analysis-services/instances/monitor-an-analysis-services-instance.md)|Vengono descritti strumenti e tecniche per monitorare un'istanza del server, incluso il modo di utilizzare Performance Monitor e SQL Server Profiler.|  
|[Disponibilità elevata e scalabilità](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)|Descrive le tecniche usate più di frequente per garantire ai database di Analysis Services disponibilità elevata e scalabilità. |  
|[Scenari di globalizzazione per Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md)|Illustra il supporto per la lingua e le regole di confronto, i passaggi per modificare entrambe le proprietà e i suggerimenti per l'impostazione e il test dei comportamenti della lingua e delle regole di confronto.|  
|[Registrare le operazioni in Analysis Services](../../analysis-services/instances/log-operations-in-analysis-services.md)|Descrive i log e illustra come configurarli.|  
  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto tra soluzioni tabulari e multidimensionali ](../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
