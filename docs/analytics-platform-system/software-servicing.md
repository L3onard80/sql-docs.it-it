---
title: Manutenzione software - sistema di piattaforma Analitica | Microsoft Docs
description: Software di manutenzione nel sistema di piattaforma Analitica (AP).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 444d7f29e7f65da7e5d98dde310b2c1f8ad8dd4b
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700210"
---
# <a name="software-servicing-in-analytics-platform-system"></a>Manutenzione software nel sistema di piattaforma Analitica
Questa sezione vengono riepilogati i requisiti per le Appliance di sistema di piattaforma Analitica, inclusi gli hotfix WSUS e il sistema di piattaforma Analitica di manutenzione software.  
  
## <a name="Basics"></a>Nozioni di base di manutenzione software  
**Windows Server Update Services:** l'appliance del sistema di piattaforma Analitica può essere configurato per ricevere gli aggiornamenti da Windows Server Update Services (WSUS). Questi aggiornamenti includono importanti modifiche al software di appliance. Dopo averli configurati, molti aggiornamenti verranno installati automaticamente e non richiedono interventi di gestione. In genere, vengono configurati gli aggiornamenti WSUS durante la [configurare Windows Server Update Services &#40;WSUS&#41; &#40;sistema di piattaforma Analitica&#41; ](configure-windows-server-update-services-wsus.md) passaggio eseguito durante la nuova configurazione del dispositivo. In caso contrario, questo passaggio di configurazione può essere eseguito in un secondo momento. Per informazioni su WSUS, vedere la [sito Web WSUS Guida](https://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Gli aggiornamenti rapidi:** , inoltre, potrebbe essere necessario applicare aggiornamenti rapidi di sistema di piattaforma Analitica. Oggetto *hotfix* è un aggiornamento software che viene creato per un cliente specifico risolvere un problema con il software di sistema di piattaforma Analitica. Ciascun aggiornamento rapido è un file eseguibile che consente di installare la correzione del problema specifico del cliente. Ciascun aggiornamento rapido contiene anche un accumulo di tutti gli aggiornamenti software rilasciati in precedenza per Windows, SQL Server e il sistema di piattaforma Analitica. Se è necessario installare un hotfix, il supporto Microsoft fornirà all'utente di aggiornamento rapido e istruzioni.  
  
**Ambito degli aggiornamenti:** applicare un hotfix o service pack al sistema di piattaforma Analitica necessario rendere l'intero dispositivo offline.  
  
**Adattatore di destinazione di SSIS e strumenti Client:** quando si applica un aggiornamento rapido che include le modifiche al MSI di adattatore di destinazione SSIS o file MSI di strumenti Client, i file MSI verranno aggiornati nel **C:\PDWINST\ClientTools** Directory nel nodo di controllo. L'hotfix non viene automaticamente installato i componenti dal file MSI aggiornati. Per aggiornare tali componenti, il cliente deve disinstallare le versioni precedenti dei componenti e installare le nuove versioni dei file MSI aggiornati. Quando si disinstalla un aggiornamento rapido che include le modifiche dell'Adapter MSI destinazione SSIS o file MSI di strumenti Client, i file MSI per tali componenti verranno annullate le versioni precedenti. Per ripristinare tali componenti a una versione precedente, il cliente deve disinstallare le versioni esistenti (più recente) dei componenti e reinstallare le versioni precedenti dei file MSI ripristinati.  
  
## <a name="software-servicing-topics"></a>Negli argomenti di manutenzione software  
Gli argomenti seguenti descrivono come gestire software di manutenzione nell'appliance:  
  
-   [Scaricare e applicare gli aggiornamenti di Microsoft &#40;sistema di piattaforma Analitica&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Disinstallare gli aggiornamenti di Microsoft &#40;sistema di piattaforma Analitica&#41;](uninstall-microsoft-updates.md)  
  
-   [Applicare gli hotfix del sistema di piattaforma Analitica &#40;sistema di piattaforma Analitica&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Disinstallare gli aggiornamenti rapidi del sistema di piattaforma Analitica &#40;sistema di piattaforma Analitica&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
