---
title: Impostazioni di sistema (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- Master Data Services, system settings
- system settings [Master Data Services]
ms.assetid: 83075cdf-f059-4646-8ba2-19be8202f130
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a411290435a10e351c05e9dd1350bde597dbe449
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289249"
---
# <a name="system-settings-master-data-services"></a>Impostazioni di sistema (Master Data Services)
  Per tutte le applicazioni Web e tutti i servizi Web associati a un database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è possibile configurare impostazioni di sistema.  
  
 Molte di queste impostazioni possono essere configurate in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] nella pagina **Database** . Altre possono essere configurate nella tabella Impostazioni sistema (mdm.tblSystemSetting) nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Le impostazioni possono essere raggruppate nelle categorie seguenti:  
  
-   [Impostazioni generali](#General)  
  
-   [Impostazioni di gestione delle versioni](#Versions)  
  
-   [Impostazioni di gestione temporanea](#Staging)  
  
-   [Impostazioni di Esplora risorse](#Explorer)  
  
-   [Impostazioni del componente aggiuntivo per Excel](#xls)  
  
-   [Impostazioni delle regole business](#BusinessRules)  
  
-   [Impostazioni di notifica](#Notifications)  
  
-   [Impostazioni di sicurezza](#Security)  
  
-   [Non utilizzato](#NotUsed)  
  
##  <a name="General"></a>Impostazioni generali  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
|**Timeout della connessione del database**|**DatabaseConnectionTimeOut**|Numero di secondi consentiti dal database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] per l'esecuzione di una connessione. Se la connessione non viene eseguita entro tale intervallo di tempo, verrà annullata e verrà visualizzato un errore. Il valore predefinito è **60** secondi (1 minuto).|  
|**Timeout del comando di database**|**DatabaseCommandTimeOut**|Numero di secondi consentiti dal database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] per l'esecuzione di un comando. Se il comando non viene eseguito entro tale intervallo di tempo, verrà annullato e verrà visualizzato un errore. Il valore predefinito è **3600** secondi (60 minuti).|  
|**Timeout servizio Web**|**ServerTimeOut**|Numero di secondi consentiti da ASP.NET per l'esecuzione di una richiesta di pagina di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Se la richiesta non viene eseguita entro tale intervallo di tempo, verrà annullata e verrà visualizzato un errore. Il valore predefinito è **120000** secondi (2000 minuti).|  
|**Timeout client**|**ClientTimeOut**|Numero di secondi di inattività prima che [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] torni alla home page. Il valore predefinito è **300** secondi (5 minuti).|  
|**Numero di righe per batch**|**RowsPerBatch**|Numero di record che il servizio Web deve recuperare in ogni batch. Il valore predefinito è **50**.|  
||**ApplicationName**|Testo visualizzato nei registri eventi. Il valore predefinito è **MDM**.|  
||**SiteTitle**|Testo visualizzato nella barra del titolo del Web browser di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Il valore predefinito è **Gestione dati master**.|  
  
##  <a name="Versions"></a>Impostazioni di gestione delle versioni  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
|**Copia solo versioni con commit**|**CopyOnlyCommittedVersion**|In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]determina se gli utenti possono copiare le versioni dei modelli con stato **Commit eseguito**oppure le versioni con qualsiasi stato. Il valore predefinito è **Sì** o **1**per indicare che gli utenti possono copiare solo le versioni con stato **Commit eseguito** . Sostituire con **No** o **2** per consentire agli utenti di copiare tutte le versioni.|  
  
 Per altre informazioni, vedere [Versioni &#40;Master Data Services&#41;](versions-master-data-services.md).  
  
##  <a name="Staging"></a>Impostazioni di gestione temporanea  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
|**Registra tutte le transazioni di staging**|**StagingTransactionLogging**|Questa impostazione è valida solo per Microsoft SQL Server 2008 R2. Determina se registrare o meno le transazioni quando i record di gestione temporanea vengono caricati nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Il valore predefinito è **Disattivato** o **2**. Sostituire con **Attivato** o **1** per abilitare la registrazione.|  
|**Intervallo batch di gestione temporanea**|**StagingBatchInterval**|Nell'area funzionale [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Integration Management** functional area, the number of seconds after you select **Start Batches** that your batch is processed. Il valore predefinito è **60** secondi (1 minuto).|  
  
 Per altre informazioni, vedere [Importazione dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="Explorer"></a>Impostazioni di Esplora risorse  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
|**Numero di membri nella gerarchia per impostazione predefinita**|**HierarchyChildNodeLimit**|Nell'area funzionale Esplora[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ** di ** indica il numero massimo di membri visualizzati in ogni nodo della gerarchia prima che venga visualizzato **...ulteriori nodi...**. Fare clic su **...ulteriori nodi...** per visualizzare il gruppo di membri successivo. Il valore predefinito è **50**.|  
|**Mostra i nomi nella gerarchia per impostazione predefinita**|**ShowNamesInHierarchy**|Nell'area funzionale Esplora[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ** di ** determina l'impostazione predefinita selezionata quando vengono visualizzate le gerarchie.<br /><br /> Il valore predefinito è **Sì** o **1**, che indica la visualizzazione del nome e del codice di ogni membro. Sostituire con **No** o **2** per visualizzare solo il codice.|  
|**Numero di attributi basati su dominio nell'elenco**|**DBAListRowLimit**|Nell'area funzionale [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer**, numero di attributi visualizzati in un elenco quando si fa doppio clic su un valore di attributo basato su dominio nella griglia. Il valore predefinito è **50**. Se sono presenti più di 50 membri, viene visualizzata una finestra di dialogo in cui eseguire ricerche.|  
||**GridFilterDefaultFuzzySimilarityLevel**|Nell'area funzionale Esplora[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ** di **, livello di somiglianza utilizzato quando si utilizzano i criteri del filtro **Corrisponde a**. Il valore predefinito è **0.3**. Impostare il valore più prossimo a **1** per restituire una corrispondenza che più si avvicini ai criteri di ricerca. Impostare su **1** per una corrispondenza esatta.|  
  
##  <a name="xls"></a>Impostazioni del componente aggiuntivo per Excel  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
|Mostrare il testo del componente aggiuntivo per Excel sulla home page del sito Web|ShowAddInText|Sulla home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , mostrare un collegamento con cui gli utenti possono scaricare [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|  
|Percorso di installazione del componente aggiuntivo per Excel sulla home page del sito Web|AddInURL|Sulla home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , se viene visualizzato il collegamento a [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] , percorso a cui vengono indirizzati gli utenti quando fanno clic sul collegamento.|  
  
##  <a name="BusinessRules"></a>Impostazioni delle regole business  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
|**Numero in base a cui incrementare le nuove regole business**|**BusinessRuleDefaultPriorityIncrement**|Nell'area funzionale Amministrazione sistema[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ** di **, numero in base a cui viene incrementata la priorità di ogni nuova regola business. Il valore predefinito è **10**.|  
|**Numero di membri a cui applicare le regole business**|**BusinessRuleRealtimeMemberCount**|Nell'area funzionale Esplora[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ** di **, il numero massimo di membri nella griglia a cui applicare regole business. Nel [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], numero massimo di membri nel foglio di lavoro attivo a cui applicare le regole di business. Il valore predefinito è **10000**.|  
  
 Per altre informazioni, vedere [Regole di business &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md).  
  
##  <a name="Notifications"></a>Impostazioni di notifica  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
|**URL Gestione dati master per le notifiche**|**MDMRootURL**|URL per l'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , usato nel collegamento presente nelle notifiche tramite posta elettronica, ad esempio http://constoso/mds.|  
|**Intervallo posta elettronica di notifica**|**NotificationInterval**|Frequenza, in secondi, con cui vengono inviate le notifiche tramite posta elettronica. Il valore predefinito è **120** secondi (2 minuti).|  
|**Numero di notifiche in un singolo messaggio di posta elettronica**|**NotificationsPerEmail**|Numero massimo di problemi di convalida che saranno elencati in un singolo messaggio di posta elettronica di notifica. Eventuali ulteriori problemi non vengono inclusi nel messaggio di posta elettronica, ma sono disponibili in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].|  
|**Formato di posta elettronica predefinito**|**EmailFormat**|Formato per tutte le notifiche tramite posta elettronica. Il valore predefinito è **HTML** o **1**. L'impostazione del database **2** indica **Testo**.<br /><br /> Nota: è possibile eseguire l'override di questa impostazione per un singolo utente in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], modificando e salvando il valore di **Formato posta elettronica** nella scheda **Generale** dell'utente.|  
|**Espressione regolare per l'indirizzo di posta elettronica**|**EmailRegExPattern**|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Nell'area funzionale **autorizzazioni utenti e gruppi** , l'espressione regolare usata per convalidare l'indirizzo di posta elettronica immesso nella scheda **generale** di un utente. Per ulteriori informazioni sulle espressioni regolari, vedere [elementi del linguaggio di espressioni regolari](https://go.microsoft.com/fwlink/?LinkId=164401) in MSDN Library.|  
|**Account Posta elettronica database**|**EmailProfilePrincipalAccount**|Visualizza l'account di posta del database da utilizzare per l'invio delle notifiche tramite posta elettronica. Il profilo predefinito è **mds_email_user**.|  
|**Profilo Posta elettronica database**|**DatabaseMailProfile**|Profilo di posta del database da utilizzare per l'invio delle notifiche tramite posta elettronica. Il valore predefinito è vuoto.|  
||**ValidationIssueHTML**|In formato HTML, testo ricevuto dagli utenti di messaggi di posta elettronica quando la convalida di una regola business ha esito negativo.|  
||**ValidationIssueText**|In formato testo normale, testo ricevuto dagli utenti di messaggi di posta elettronica quando la convalida di una regola business ha esito negativo.|  
||**VersionStatusChangeText**|In formato testo normale, testo ricevuto dagli utenti di messaggi di posta elettronica quando viene modificato lo stato di una versione. Solo gli utenti con l'autorizzazione **Update** per l'intero modello ricevono questo messaggio di posta elettronica.|  
||**VersionStatusChangeHTML**|In formato HTML, testo ricevuto dagli utenti di messaggi di posta elettronica quando viene modificato lo stato di una versione. Solo gli utenti con l'autorizzazione **Update** per l'intero modello ricevono questo messaggio di posta elettronica.|  
  
 Per altre informazioni, vedere [Notifiche &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md).  
  
##  <a name="Security"></a>Impostazioni di sicurezza  
  
|Impostazione di Gestione configurazione|Impostazione di sistema|Descrizione|  
|-----------------------------------|--------------------|-----------------|  
||**SecurityMemberProcessInterval**|Nell'area funzionale Autorizzazioni utenti e gruppi[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ** di **, frequenza in secondi con cui vengono applicate le autorizzazioni di utenti e gruppi impostate in **Membri gerarchia**. Il valore predefinito è **3600** secondi (60 minuti).|  
  
 Per altre informazioni, vedere [Applicare immediatamente autorizzazioni membri &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="NotUsed"></a>Non utilizzato  
 Le seguenti impostazioni nella tabella Impostazioni sistema non vengono utilizzate.  
  
-   **SecurityMode**  
  
-   **MDSHubName**  
  
-   **ApplicationLogging**  
  
-   **ReportServer**  
  
-   **ReportDirectory**  
  
-   **BusinessRuleEngineIterationLimit**  
  
-   **BusinessRuleExtensibility**  
  
-   **AttributeExplorerMarkAllActionMemberCount**  
  
## <a name="see-also"></a>Vedere anche  
 [&#40;di sicurezza degli oggetti di database Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
