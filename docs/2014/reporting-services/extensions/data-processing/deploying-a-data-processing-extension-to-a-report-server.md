---
title: "Procedura: Distribuire un'estensione per l'elaborazione dati in un server di report | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- assemblies [Reporting Services], data processing extension deployments
ms.assetid: e00dface-70f8-434b-9763-8ebee18737d2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0f593b2488d9bb7226edad1f8d98a244f4df191
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164077"
---
# <a name="how-to-deploy-a-data-processing-extension-to-a-report-server"></a>Procedura: Distribuzione di un'estensione per l'elaborazione dati in un server di report
  I server di report utilizzano le estensioni per l'elaborazione dati per il recupero e l'elaborazione di dati nei report visualizzabili. È necessario distribuire l'assembly dell'estensione per l'elaborazione dati in un server di report come assembly privato. È inoltre necessario creare una voce nel file di configurazione del server di report, ovvero RSReportServer.config.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-deploy-a-data-processing-extension-assembly"></a>Per distribuire un assembly dell'estensione per l'elaborazione dati  
  
1.  Copiare l'assembly dal percorso di gestione temporanea nella directory bin del server di report in cui si desidera utilizzare l'estensione per l'elaborazione dati. Il percorso predefinito della directory bin del server di report è %Programmi%\Microsoft SQL Server\MSRS10_50.\<*NomeIstanza*>\Reporting Services\ReportServer\bin.  
  
    > [!NOTE]  
    >  Con questo passaggio viene evitato l'aggiornamento a un'istanza di SQL Server più recente. Per altre informazioni, vedere [Upgrade and migrate Reporting Services](../../install-windows/upgrade-and-migrate-reporting-services.md).  
  
2.  Dopo aver copiato il file di assembly, aprire il file RSReportServer.config che si trova nella directory ReportServer. È necessario immettere una voce nel file di configurazione per il file di assembly dell'estensione per l'elaborazione dati. È possibile aprire il file di configurazione in Visual Studio o in un semplice editor di testo, ad esempio Blocco note.  
  
3.  Individuare l'elemento `Data` nel file RSReportServer.config. È necessario immettere una voce per l'estensione per l'elaborazione dati appena creata nel percorso seguente:  
  
    ```  
    <Extensions>  
       <Data>  
          <Your extension configuration information goes here>  
       </Data>  
    </Extensions>  
    ```  
  
4.  Aggiungere una voce per l'estensione per l'elaborazione dati. La voce deve includere un elemento `Extension` con valori per `Name` e `Type` e può essere simile a quanto riportato di seguito:  
  
    ```  
    <Extension Name="ExtensionName" Type="CompanyName.ExtensionName.MyConnectionClass, MyExtensionAssembly" />  
    ```  
  
     Il valore per `Name` è il nome univoco dell'estensione per l'elaborazione dati. Il valore per `Type` è un elenco delimitato da virgole che include una voce per lo spazio dei nomi completo della classe che implementa le interfacce <xref:Microsoft.ReportingServices.Interfaces.IExtension> e <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, seguito dal nome dell'assembly, senza l'estensione dll. Per impostazione predefinita, le estensioni per l'elaborazione dati sono visibili. Per nascondere un'estensione dalle interfacce utente, come Gestione report, aggiungere un attributo `Visible` all'elemento `Extension` e impostarlo su `false`.  
  
5.  Aggiungere un gruppo di codice per l'assembly personalizzato che conceda l'autorizzazione `FullTrust` per l'estensione. A questo scopo, aggiungere il gruppo di codice al file rssrvpolicy.config che per impostazione predefinita si trova nel percorso %Programmi%\Microsoft SQL Server\\<MSRS10_50.\<*Nome istanza*>\Reporting Services\ReportServer. Il gruppo di codice può essere simile a quanto riportato di seguito:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="MyExtensionCodeGroup"  
       Description="Code group for my data processing extension">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.<Instance Name>\Reporting Services\ReportServer\bin\MyExtensionAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 L'appartenenza URL è solo una delle diverse condizioni di appartenenza selezionabili per l'estensione per l'elaborazione dati. Per altre informazioni sulla sicurezza dall'accesso di codice in [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vedere [Sviluppo sicuro &#40;Reporting Services&#41;](../secure-development/secure-development-reporting-services.md).  
  
## <a name="verifying-the-deployment"></a>Verifica della distribuzione  
 È possibile verificare se l'estensione per l'elaborazione dati è stata distribuita correttamente nel server di report tramite il metodo <xref:ReportService2010.ReportingService2010.ListExtensions%2A> del servizio Web. È inoltre possibile aprire Gestione report e verificare che l'estensione sia inclusa nell'elenco delle origini dati disponibili. Per altre informazioni su Gestione report e sulle origini dati, vedere [Creare, modificare ed eliminare origini dati condivise &#40;SSRS&#41;](../../report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di un'estensione per l'elaborazione dati](deploying-a-data-processing-extension.md)   
 [Estensioni di Reporting Services](../reporting-services-extensions.md)   
 [Implementazione di un'estensione per l'elaborazione dati](implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  
