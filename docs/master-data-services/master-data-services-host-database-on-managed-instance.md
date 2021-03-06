---
title: Ospitare un database in un'istanza gestita
description: Questo articolo descrive come configurare un database Master Data Services (MDS) in un'istanza gestita.
ms.custom: ''
ms.date: 07/01/2019
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19519697-c219-44a8-9339-ee1b02545445
author: v-redu
ms.author: lle
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b4bb1a89e997486e88b6d4ca48a9a550d1c552b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729025"
---
# <a name="host-an-mds-database-on-a-managed-instance"></a>Ospitare un database MDS in un'istanza gestita

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Questo articolo illustra come configurare un database di Master Data Services (MDS) in un'istanza gestita.
  
## <a name="preparation"></a>Operazioni preliminari

Per preparare, è necessario creare e configurare un'istanza gestita di database SQL di Azure e configurare il computer dell'applicazione Web.

### <a name="create-and-configure-the-database"></a>Creare e configurare il database

1. Creare un'istanza gestita di database SQL di Azure con una rete virtuale. Per informazioni dettagliate, vedere [Guida introduttiva: creare un'istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started) .

1. Configurare una connessione da punto a sito. Per istruzioni, vedere [configurare una connessione da punto a sito a una VNet usando l'autenticazione del certificato di Azure nativo: portale di Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) .

1. Configurare Azure Active Directory autenticazione con istanza gestita di database SQL. Per informazioni dettagliate, vedere [configurare e gestire Azure Active Directory autenticazione con SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure) .

### <a name="configure-web-application-machine"></a>Configurare il computer dell'applicazione Web

1. Installare un certificato di connessione da punto a sito e una VPN per assicurarsi che il computer possa accedere all'istanza gestita di database SQL. Per istruzioni, vedere [configurare una connessione da punto a sito a una VNet usando l'autenticazione del certificato nativa di Azure: portale di Azure](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) .

1. Installare i ruoli e le funzionalità seguenti:
   - Ruoli:
     - Internet Information Services
     - Strumenti di gestione Web
     - Console di gestione IIS
     - Servizi Web
     - Sviluppo di applicazioni
     - Estendibilità .NET 3.5
     - Estendibilità .NET 4.5
     - ASP.NET 3.5
     - ASP.NET 4.5
     - Estensioni ISAPI
     - Filtri ISAPI
     - Funzionalità HTTP comuni
     - Documento predefinito
     - Esplorazione directory
     - Errori HTTP
     - Contenuto statico
     - Integrità e diagnostica
     - Registrazione HTTP
     - Monitoraggio richieste
     - Prestazioni
     - Compressione contenuto statico
     - Security
     - Filtro richieste
     - Autenticazione di Windows
       > [!NOTE]
       > Non installare la pubblicazione WebDAV

   - Caratteristiche:
     - .NET Framework 3.5 (inclusi .NET 2.0 e 3.0)
     - .NET Framework 4.5 Advanced Services
     - ASP.NET 4.5
     - WCF Services
     - Attivazione HTTP (obbligatoria)
     - Condivisione porta TCP
     - Servizio Attivazione processo Windows
     - Modello di processo
     - Ambiente .NET
     - API di configurazione
     - Compressione contenuto dinamico

## <a name="install-and-configure-an-mds-web-application"></a>Installare e configurare un'applicazione Web MDS

Quindi, installare e configurare [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].

### <a name="install-sql-server-2019"></a>Installare SQL Server 2019

Utilizzare l'installazione guidata di SQL Server o un prompt dei comandi per [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]installare.

1. Aprire `Setup.exe`e seguire i passaggi dell'installazione guidata.

2. Nella pagina [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Selezione funzionalità **selezionare** in **Funzionalità condivise**.
Questa azione consente di installare:
   - [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]
   - Assembly
   - Uno snap-in di Windows PowerShell
   - Cartelle e file per servizi e applicazioni Web.

   ![MDS-SQLServer2019-config-MI-SQLFeatureSelection](../master-data-services/media/mds-sqlserver2019-config-mi-sqlfeatureselection.png "MDS-SQLServer2019-config-MI_SQLFeatureSelection")  

### <a name="set-up-the-database-and-website"></a>Configurare il database e il sito Web

1. Connettere la rete virtuale di Azure per assicurarsi che sia possibile connettersi all'istanza gestita.

   ![MDS-SQLServer2019-config-MI-P2SVPNConnect](../master-data-services/media/mds-sqlserver2019-config-mi-p2svpnconnect.png "MDS-SQLServer2019-config-MI_P2SVPNConnect")

1. Aprire [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] e quindi selezionare **Configurazione database** nel riquadro sinistro.

1. Selezionare **Crea database** per aprire la **procedura guidata Crea database**. Selezionare **Avanti**.

1. Nella pagina **server database** completare il campo **istanza SQL Server** , quindi scegliere il **tipo di autenticazione**. Selezionare **Test connessione** per confermare che è possibile utilizzare le credenziali per connettersi al database tramite il tipo di autenticazione scelto. Selezionare **Avanti**.

   > [!NOTE]
   > - Un'istanza di SQL Server ha `xxxxxxx.xxxxxxx.database.windows.net`un aspetto simile a.
   > - Per un'istanza gestita, scegliere tra i tipi di autenticazione **"SQL Server account"** e **"utente corrente – Active Directory integrata"** .
   > - Se si seleziona **utente corrente-Active Directory integrato** come tipo di autenticazione, il campo **nome utente** è di sola lettura e visualizza l'account utente di Windows attualmente connesso. Se si esegue SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in una macchina virtuale (VM) di Azure, il campo **nome utente** Visualizza il nome della macchina virtuale e il nome utente per l'account amministratore locale nella macchina virtuale.

   L'autenticazione deve contenere la regola **"sysadmin"** per le istanze gestite.

   ![MDS-SQLServer2019-config-MI-CreateDBConnect](../master-data-services/media/mds-sqlserver2019-config-mi-createdbconnect.png "MDS-SQLServer2019-config-MI_CreateDBConnect")  

1. Digitare un nome nel campo **Nome database** . Facoltativamente, per selezionare le regole di confronto di Windows, deselezionare la casella di controllo **SQL Server regole di confronto predefinite** e selezionare una o più delle opzioni disponibili. Ad esempio, con **distinzione tra maiuscole**e minuscole. Selezionare **Avanti**.

   ![MDS-SQLServer2019-config-MI-CreatedDBName](../master-data-services/media/mds-sqlserver2019-config-mi-createddbname.png "MDS-SQLServer2019-config-MI_CreatedDBName")

1. Nel campo **nome utente** specificare l'account di Windows dell'utente con privilegi avanzati predefinito per [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. Un utente con privilegi avanzati ha accesso a tutte le aree funzionali e può aggiungere, eliminare e aggiornare tutti i modelli.

   ![MDS-SQLServer2019-config-MI-CreateDBUserName](../master-data-services/media/mds-sqlserver2019-config-mi-createdbusername.png "MDS-SQLServer2019-config-MI_createDBUserName")

1. Selezionare **Avanti** per visualizzare un riepilogo delle impostazioni per il [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] database. Fare di nuovo clic su **Avanti** per creare il database. Verrà visualizzata la pagina **stato e fine** .

1. Dopo aver creato e configurato il database, selezionare **fine**.

   Per ulteriori informazioni sulle impostazioni della **procedura guidata Crea database**, vedere [creazione guidata database &#40;[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Configuration Manager&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).

1. Nella pagina **Configurazione database** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]scegliere **Seleziona database**.

1. Selezionare **Connetti**, scegliere il [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] database e quindi fare clic su **OK**.

   ![MDS-SQLServer2019-config-MI-connectDBName](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_connectDBName")

1. In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]selezionare **configurazione Web** nel riquadro sinistro.

1. Nella casella di riepilogo **sito** Web scegliere **sito Web predefinito**, quindi selezionare **Crea** per creare un'applicazione Web.

   ![MDS-SQLServer2019-config-MI-webconfiguration](../master-data-services/media/mds-sqlserver2019-config-mi-webconfiguration.png "MDS-SQLServer2019-config-MI_WebConfiguration")

   > [!NOTE]
   > Se si seleziona **sito Web predefinito**, sarà necessario creare un'applicazione Web separatamente. Se si sceglie **Crea nuovo sito Web** nella casella di riepilogo, l'applicazione viene creata automaticamente.

1. Nella sezione **pool di applicazioni** immettere un nome utente diverso, immettere la password e quindi fare clic su **OK**.

   ![MDS-SQLServer2019-config-MI-CreateWebApplication](../master-data-services/media/mds-sqlserver2019-config-mi-createwebapplication.png "MDS-SQLServer2019-config-MI_CreateWebApplication")

   > [!NOTE]
   > Assicurarsi che l'utente possa accedere al database con l'autenticazione integrata di Active Directory creata di recente. In alternativa, è possibile modificare la connessione in `web.config` un secondo momento.

   Per ulteriori informazioni sulla finestra di dialogo **Crea applicazione Web** , vedere finestra di [dialogo crea applicazione web [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] &#40;Configuration Manager&#41;](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).

1. Nel riquadro **configurazione Web** della finestra **dell'applicazione Web** Selezionare l'applicazione creata e quindi scegliere **Seleziona** nella sezione **associare l'applicazione al database** .

1. Selezionare **Connetti** e scegliere il [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] database che si desidera associare all'applicazione Web. Selezionare **OK**.

   È stata completata la configurazione del sito Web. Nella pagina **configurazione Web** è ora visualizzato il sito Web selezionato, l'applicazione Web creata e il [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] database associato all'applicazione.

   ![MDS-SQLServer2019-config-MI-WebConfigSelectDB](../master-data-services/media/mds-sqlserver2019-config-mi-webconfigselectdb.png "MDS-SQLServer2019-config-MI_WebConfigSelectDB")

1. Selezionare **Applica**. Verrà visualizzato il messaggio **Configurazione completata** . Selezionare **OK** nella finestra di messaggio per avviare l'applicazione Web. L'indirizzo del sito `http://server name/web application/`Web è.

## <a name="configure-authentication"></a>Configurare l'autenticazione

Per connettere il database dell'istanza gestita all'applicazione Web, è necessario modificare l'altro tipo di autenticazione.

Trovare il `web.config` file in `C:\Program Files\Microsoft SQL Server\150\Master Data Services\WebApplication`. Modificare connectionString per modificare l'altro tipo di autenticazione per la connessione al database dell'istanza gestita.

Il tipo di autenticazione predefinito `Active Directory Integrated` è come illustrato nella stringa di connessione di esempio seguente:

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Integrated&quot;" />
   ```

MDS supporta inoltre l'autenticazione Active Directory password e l'autenticazione SQL Server, come illustrato nelle stringhe di connessione di esempio seguenti:

- Autenticazione della password di Active Directory

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Password&quot; ; UID=bob@contoso.onmicrosoft.com; PWD=MyPassWord!" />
   ```

- Gli account di accesso di Autenticazione

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;User ID=UserName;Password=MyPassword!;" />
   ```

## <a name="upgrade-includessmdsshort_mdincludesssmdsshort-mdmd-and-sql-database-version"></a>Aggiornamento [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] e versione del database SQL

### <a name="upgrade-includessmdsshort_mdincludesssmdsshort-mdmd"></a>Aggiornamento[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]

Installare l' **aggiornamento cumulativo di SQL Server 2019**. [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]verranno aggiornate automaticamente.

### <a name="upgrade-sql-server"></a>Eseguire l'aggiornamento di SQL Server

È possibile che venga ricevuto l' `The client version is incompatible with the database version` errore: dopo l'installazione di **SQL Server 2019 aggiornamento cumulativo**.
![MDS-SQLServer2019-config-MI-UpgradeDBPage](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbpage.png "MDS-SQLServer2019-config-MI_UpgradeDBPage")

Per risolvere il problema, è necessario aggiornare la versione del database:

1. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Aprire e quindi selezionare **Configurazione database** nel riquadro sinistro.

1. Nella pagina **Configurazione database** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]scegliere **Seleziona database**.

1. Scegliere il [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] database associato all'applicazione Web. Selezionare **Connetti**e quindi fare clic su **OK**.

   ![MDS-SQLServer2019-config-MI-ConnectDBName](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_ConnectDBName")

1. Seleziona **Aggiorna database...** .

   ![MDS-SQLServer2019-config-MI-SelectUpgradeDB](../master-data-services/media/mds-sqlserver2019-config-mi-selectupgradedb.png "MDS-SQLServer2019-config-MI_SelectUpgradeDB")

1. In aggiornamento guidato database selezionare **Avanti** nella pagina **iniziale** e nella pagina **Verifica aggiornamento** .

   ![MDS-SQLServer2019-config-MI-UpgradeDBWizard](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbwizard.png "MDS-SQLServer2019-config-MI_UpgradeDBWizard")

1. Selezionare **fine** al termine di tutte le attività.

## <a name="see-also"></a>Vedere anche

- [Database Master Data Services](../master-data-services/master-data-services-database.md)
- [Applicazione Web Gestione dati master](../master-data-services/master-data-manager-web-application.md)
- [Pagina di configurazione del database &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)
- [Novità di Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)
