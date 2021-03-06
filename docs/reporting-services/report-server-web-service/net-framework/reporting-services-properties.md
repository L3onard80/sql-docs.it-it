---
title: Proprietà di Reporting Services | Microsoft Docs
description: Un server di report definisce proprietà di sistema globali e proprietà di singoli elementi. Le applicazioni possono aggiungere proprietà definite dall'utente a proprietà di sistema e di elemento.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7240bf3e987c5817489035d94879817f5f39569b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "79509712"
---
# <a name="reporting-services-properties"></a>Proprietà di Reporting Services
  Il server di report definisce un set di proprietà di sistema globali del server di report e un set di proprietà degli elementi associate a un singolo elemento archiviato nel database del server di report. Le proprietà definite dal server di report non possono essere eliminate e in alcuni casi sono di sola lettura. Un'applicazione consente di estendere le proprietà di sistema e degli elementi aggiungendo a queste proprietà ulteriori proprietà definite dall'utente.  
  
 I metodi del servizio Web seguenti consentono di recuperare e di impostare le proprietà di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Metodo|Azione|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Restituisce i valori di una o più proprietà di un elemento nel database del server di report.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Restituisce una o più proprietà di sistema.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Imposta una o più proprietà di un elemento nel database del server di report.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Imposta una o più proprietà di sistema.|  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Proprietà degli elementi del server di report](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Vengono descritte le proprietà specifiche degli elementi in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Proprietà di sistema del server di report](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Vengono descritte le proprietà di sistema in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
