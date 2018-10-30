---
title: Disponibilità elevata in SQL Server Reporting Services | Microsoft Docs
ms.date: 10/05/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 42fb4216a0322a0d3f077f237b2ece3cdef7958b
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50030760"
---
# <a name="high-availability-in-sql-server-reporting-services"></a>Disponibilità elevata in SQL Server Reporting Services

Un server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è un server senza stato (stateless) in cui vengono archiviati dati dell'applicazione, contenuto, proprietà e informazioni sulla sessione in due database relazionali di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In questa situazione, il modo più efficiente per garantire la disponibilità delle funzionalità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste nell'esecuzione delle operazioni seguenti:  
  
-   Utilizzare le caratteristiche a disponibilità elevata del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] per ottimizzare il tempo di attività dei database del server di report. Se si configura un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] per l'esecuzione in un cluster di failover, è possibile selezionarla quando si crea un database del server di report.  
  
-   Utilizzare, per quanto possibile, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] con i database di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e per le origini dati. Per altre informazioni, vedere [Reporting Services con i gruppi di disponibilità AlwaysOn](../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).  
  
-   Configurare più server di report in modo che vengano eseguiti in una distribuzione con scalabilità orizzontale, in cui tutti i server condividono un unico database del server di report. La distribuzione di più istanze del server di report, preferibilmente in server diversi, con scalabilità orizzontale consente di non interrompere il servizio ininterrotto nel caso in cui una delle istanze del server di report si arresti.  
  
 Una distribuzione con scalabilità orizzontale consente di condividere un database. Se uno server di report si arresta, gli altri server nella stessa distribuzione continueranno a funzionare.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non riesce a interagire con i cluster. Di per sé, una distribuzione con scalabilità orizzontale non fornisce il bilanciamento carico e non rileva i carichi di elaborazione su un server di report né invia le nuove richieste di elaborazione al server meno occupato. Tale distribuzione inoltre non reindirizza le richieste di elaborazione che non state completate in modo corretto. Per ottenere il bilanciamento del carico, è necessario configurarlo per i server Web che ospitano i server di report e configurare quindi i server di report in una distribuzione con scalabilità orizzontale in modo che condividano lo stesso database del server di report.  
  
 Il servizio Web ReportServer e il servizio Windows sono strettamente integrati e vengono eseguiti insieme come una sola istanza del server di report. Non è possibile configurare separatamente la disponibilità per uno dei due servizi.  

Altre domande? [Visitare il forum su Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
