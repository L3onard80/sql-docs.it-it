---
title: Requisiti del database
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a06d5b8ebc22e5456e8f2989766f2f829d637cd0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728142"
---
# <a name="database-requirements-master-data-services"></a>Requisiti del database (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Tutti i dati master vengono archiviati in un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Nel computer che ospita il database deve essere in esecuzione un' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]istanza di.  
  
 Utilizzare [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] per creare e configurare il database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] in un computer locale o remoto. Se si sposta il database da un ambiente a un altro, è possibile gestire le informazioni in un nuovo ambiente associando il servizio Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] e [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] al database nella nuova posizione.  
  
> [!NOTE]  
>  Tutti i computer in cui si installano componenti di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] devono essere dotati di licenza appropriata. Per ulteriori informazioni, fare riferimento al Contratto di licenza.  
  
## <a name="requirements"></a>Requisiti  
 Prima di creare un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , assicurarsi che vengano soddisfatti i requisiti seguenti.  
  
### <a name="sql-server-edition"></a>Edizione di SQL Server  
 Il database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] può essere ospitato nelle seguenti edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]Enterprise (64 bit) x64  
  
-   
  [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] Developer (64-bit) x64  
  
-   
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence (64-bit) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]Enterprise (64 bit) x64  
  
-   
  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer (64-bit) x64  
  
-   
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence (64-bit) x64  
  
-   
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise (64 bit) x64 - Aggiornamento solo da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise  
  
-   
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer (64-bit) x64  
  
-   Microsoft SQL Server 2008 R2 Enterprise (64 bit) x64  
  
-   Microsoft SQL Server 2008 R2 Developer (64 bit) x64  
  
 Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md). 
  
### <a name="operating-system"></a>Sistema operativo  
 Per informazioni sui sistemi operativi Windows supportati e sugli altri requisiti per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], vedere [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="accounts-and-permissions"></a>Account e autorizzazioni  
  
|Type|Descrizione|  
|----------|-----------------|  
|Account utente|Per ospitare il database [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile usare un account di Windows o un account di [!INCLUDE[ssDE](../../includes/ssde-md.md)] per connettersi all'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . È necessario che l'account utente appartenga al ruolo server **sysadmin** nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Per altre informazioni sul ruolo **sysadmin** , vedere [Ruoli a livello di server](../../relational-databases/security/authentication-access/server-level-roles.md).|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]account amministratore|Quando si crea un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , è necessario specificare un account utente di dominio con il ruolo di amministratore di sistema di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Per tutte le applicazioni Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] associate a questo database, tale utente può aggiornare i modelli e i dati in tutte le aree funzionali. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md).|  
  
### <a name="database-backup"></a>Backup del database  
 In base alla procedura consigliata, eseguire il backup dell'intero database quotidianamente in un momento di bassa attività ed eseguire il backup dei log delle transazioni con maggiore frequenza a seconda delle necessità dell'ambiente. Per altre informazioni sui backup di database, vedere [Panoramica del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installa Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
 [Creazione di un database di Master Data Services](../../master-data-services/install-windows/create-a-master-data-services-database.md)   
 [Database Master Data Services](../../master-data-services/master-data-services-database.md)   
 [Finestra di dialogo Connetti a un database di Master Data Services](../../master-data-services/connect-to-a-master-data-services-database-dialog-box.md)   
 [Creazione guidata database &#40;Gestione configurazione Master Data Services&#41;](../../master-data-services/create-database-wizard-master-data-services-configuration-manager.md)  
  
  
