---
title: Importazione ed esportazione delle informazioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 12537c9d-31e4-40b0-a411-cb343abbe96a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9045ee53e6e3e08222c99ddffa2935040a314b16
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51031938"
---
# <a name="importing-and-exporting-knowledge"></a>Importazione ed esportazione delle informazioni
  È possibile creare le Knowledge Base e i domini direttamente nell'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] oppure è possibile importare le informazioni in una Knowledge Base o esportarle da essa. Nell'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] è possibile utilizzare un file di dati per le operazioni di importazione ed esportazione o un file di Excel per le operazioni di importazione. Il file di dati utilizzato è un file crittografato creato da [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) con un'estensione DQS. I file creati da Microsoft Excel potranno presentare l'estensione xlsx, xls o csv. Queste operazioni offrono una maggiore flessibilità nella compilazione e nella condivisione delle informazioni utilizzate per eseguire la pulizia dei dati e la corrispondenza.  
  
> [!IMPORTANT]  
>  È possibile esportare contemporaneamente *tutte* le Knowledge Base del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] in un file di backup DQS con estensione DQSB eseguendo il file DQSInstaller.exe dal prompt dei comandi. Analogamente, è possibile importare contemporaneamente *tutte* le Knowledge Base da un file di backup DQS con estensione DQSB nel [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] eseguendo il file DQSInstaller.exe dal prompt dei comandi. Per informazioni su questa operazione, vedere [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](install-windows/export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md) nella Guida all'installazione di DQS.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 È possibile eseguire le operazioni di importazione ed esportazione seguenti:  
  
|||  
|-|-|  
|Esportare un dominio di una Knowledge Base in un file di dati DQS|[Esportare un dominio in un file DQS](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md)|  
|Importare un dominio da un file di dati DQS in una Knowledge Base esistente|[Importare un dominio da un file DQS](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md)|  
|Esportare un'intera Knowledge Base in un file di dati DQS|[Esportare una Knowledge Base in un file DQS](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)|  
|Importare un'intera Knowledge Base in un file di dati DQS|[Importare una Knowledge Base da un file DQS](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md)|  
|Importare i valori da un file di Excel in un dominio|[Import Values from an Excel File into a Domain](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)|  
|Importare i domini da un file di Excel in una Knowledge Base|[Importare i domini da un file di Excel in Individuazione informazioni](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md)|  
|Importare le informazioni raccolte durante la pulizia in una Knowledge Base|[Importare i valori di un progetto di pulizia in un dominio](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md)|  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Compilazione di una Knowledge Base eseguendo l'individuazione delle informazioni e gestendo queste ultime in modo interattivo|[Compilazione di una Knowledge Base](../../2014/data-quality-services/building-a-knowledge-base.md)|  
|Creazione di un singolo dominio e aggiunta di informazioni al dominio.|[Gestione di un dominio](../../2014/data-quality-services/managing-a-domain.md)|  
|Creazione di un dominio composito e aggiunta di informazioni al dominio.|[Gestione di un dominio composito](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
