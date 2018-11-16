---
title: Eseguire un file script di Reporting Services | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: tools
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: da90014c17b0540a8bee4e691835361068227565
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51814154"
---
# <a name="run-a-reporting-services-script-file"></a>Eseguire un file script di Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] - I file script vengono eseguiti dal prompt dei comandi usando l'ambiente di script di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (RS.exe). RS.exe dispone di molti argomenti del prompt dei comandi disponibili per l'utilizzo. Per altre informazioni sulle opzioni del prompt dei comandi, vedere [Utilità RS.exe &#40;SSRS&#41;](../../reporting-services/tools/rs-exe-utility-ssrs.md). Per altri esempi di script, vedere [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="sample-command-lines"></a>Esempi di righe di comando  
  
-   Eseguire Script.rss nell'ambiente di script che definisce il server di report di destinazione. Per impostazione predefinita, viene applicata l'autenticazione di Windows:  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica un nome utente e una password per l'autenticazione delle chiamate al servizio Web:  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica un timeout del server di 30 secondi:  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -l 30  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica una variabile globale degli script denominata *report*.  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -v report="Company Sales"  
    ```  
  
-   Eseguire Script.rss nell'ambiente di script che specifica che le operazioni del servizio Web nel file script vengono eseguite come batch.  
  
    ```  
    rs –i Script.rss -s https://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
