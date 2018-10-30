---
title: Configurare l'account del servizio del server di report (Gestione configurazione SSRS) | Microsoft Docs
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.assetid: f880c623-67c8-4167-b98b-ace17e800faa
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d343831a702a3301cdff7b6c18bcd39318cd6241
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50021335"
---
# <a name="configure-the-report-server-service-account-ssrs-configuration-manager"></a>Configurare l'account del servizio del server di report (Gestione configurazione SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene implementato come singolo servizio contenente un servizio Web ReportServer, [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]e un'applicazione di elaborazione in background utilizzata per l'elaborazione pianificata di report e il recapito di sottoscrizioni. In questo argomento vengono illustrate la configurazione iniziale dell'account del servizio e la modifica dell'account o della password tramite lo strumento di configurazione di Reporting Services.  
  
## <a name="initial-configuration"></a>Configurazione iniziale  
 L'account del servizio del server di report viene definito durante l'installazione. È possibile eseguire il servizio usando un account utente di domino o un account predefinito, come un **account Servizio virtuale**. Non esiste alcun account predefinito. L'account specificato nella pagina **Account di servizio** dell'Installazione guidata diventerà l'account iniziale del servizio del server di report.  
  
> [!IMPORTANT]  
>  Anche se il servizio Web ReportServer e [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] sono applicazioni [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] separate, vengono eseguiti con una sola architettura del servizio all'interno della stessa identità di processo del server di report.  
  
> [!NOTE]  
>  Gli account di servizio Windows predefiniti (Servizio locale o Servizio di rete) non sono supportati come account del servizio del server di report su un computer con funzioni di controller di dominio.  
  
## <a name="changing-the-service-account"></a>Modifica dell'account del servizio  
 Per visualizzare e riconfigurare le informazioni sull'account del servizio, usare sempre Gestione configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le informazioni sull'identità del servizio sono archiviate internamente in più percorsi. L'utilizzo dello strumento garantisce che tutti i riferimenti vengano aggiornati di conseguenza ogni volta che si modifica l'account o la password. Gestione configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] esegue le operazioni supplementari seguenti per garantire la disponibilità del server di report:  
  
-   Aggiunta automatica del nuovo account al gruppo di server di report creato nel computer locale. Questo gruppo è specificato negli elenchi di controllo di accesso (ACL) utilizzati per la protezione dei file di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   Aggiornamento automatico delle autorizzazioni di accesso nell'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance used to host the report server database. Il nuovo account verrà aggiunto a **RSExecRole**.  
  
     L'account di accesso al database per l'account precedente non verrà rimosso automaticamente. Assicurarsi di rimuovere gli account non più in uso. Per altre informazioni, vedere [Amministrare un database del server di report &#40;SSRS Native Mode&#41;](../../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md) in SQL Server Books Online.  
  
     Al nuovo account del servizio vengono concesse autorizzazioni per il database solo se la connessione al database del server di report è stata configurata fin dall'inizio per l'uso dell'account del servizio. Se la connessione al database del server di report è stata configurata per l'utilizzo di un account utente di dominio o di un account di accesso al database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'aggiornamento dell'account del servizio non influisce sulle informazioni di connessione.  
  
-   Aggiornamento automatico della chiave di crittografia per includere le informazioni sul profilo del nuovo account.  
  
    > [!NOTE]  
    >  Se il server di report fa parte di una distribuzione con scalabilità orizzontale, la modifica interesserà solo il server di report che si sta aggiornando. Le chiavi di crittografia per gli altri server di report della distribuzione non sono interessate dalla modifica dell'account del servizio.  
      
## <a name="to-configure-the-report-server-service-account"></a>Per configurare l'account del servizio del server di report  
  
1.  Avviare Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e connettersi al server di report.  
  
2.  Nella pagina Account servizio selezionare l'opzione che descrive il tipo di account che si desidera utilizzare.  
  
3.  Se è stato selezionato un account utente di Windows, specificare il nuovo account e la password. Il nome dell'account non può contenere più di 20 caratteri.  
  
     Se il server di report viene distribuito in una rete che supporta l'autenticazione Kerberos, è necessario registrare il nome dell'entità servizio del server di report con l'account utente di dominio specificato. Per altre informazioni, vedere [Registrare un nome dell'entità servizio &#40;SPN&#41; per un server di report](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
4.  Fare clic su **Applica**.  
  
5.  Quando viene richiesto di eseguire il backup della chiave simmetrica, digitare un nome di file e un percorso per la copia di backup della chiave simmetrica, digitare una password per bloccare e sbloccare il file, quindi scegliere **OK**.  
  
6.  Se il server di report utilizza l'account del servizio per connettersi al database del server di report, le informazioni di connessione verranno aggiornate per l'utilizzo del nuovo account o della nuova password. L'aggiornamento delle informazioni di connessione richiede la connessione al database. Se viene visualizzata la finestra di dialogo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Database Connection** dialog box appears, enter credentials that have permission to connect to the database, and then click **OK**.  
  
7.  Quando viene richiesto di ripristinare la chiave simmetrica, digitare la password specificata al passaggio 5, quindi scegliere **OK**.  
  
8.  Controllare i messaggi di stato nel riquadro Risultati per verificare che tutte le attività siano state completate correttamente.  
  
## <a name="choosing-an-account"></a>Scelta di un account  
 Per ottenere risultati ottimali, specificare un account che dispone delle autorizzazioni necessarie per stabilire connessioni di rete, con accesso ai controller di dominio di rete e ai server o ai gateway SMTP aziendali. Nella tabella seguente vengono forniti un riepilogo degli account e alcuni consigli per utilizzarli.  
  
|Account|Spiegazione|  
|-------------|-----------------|  
|Account utente di dominio|Se si possiede un account utente di dominio di Windows che dispone delle autorizzazioni minime necessarie per operazioni sul server di report, è consigliabile utilizzarlo.<br /><br /> Un account utente di dominio rappresenta la scelta consigliata, in quanto isola il servizio del server di report dalle altre applicazioni. L'esecuzione di più applicazioni tramite un account condiviso, ad esempio Servizio di rete, aumenta il rischio di esporre il server di report al controllo da parte di utenti malintenzionati, in quanto una violazione della sicurezza di una delle applicazioni può facilmente estendersi a tutte le applicazioni eseguite utilizzando lo stesso account.<br /><br /> Si noti che se si utilizza un account utente di dominio, sarà necessario modificare periodicamente la password se l'organizzazione applica criteri di scadenza delle password. Potrebbe inoltre essere necessario registrare il servizio con l'account utente. Per altre informazioni, vedere [Registrazione di un nome dell'entità servizio &#40;SPN&#41; per un server di report](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).<br /><br /> Evitare di utilizzare un account utente locale di Windows. Gli account locali non dispongono in genere di autorizzazioni sufficienti per accedere alle risorse in altri computer. Per altre informazioni sulle limitazioni imposte alle funzionalità del server di report quando si utilizza un account locale, vedere [Considerazioni sull'utilizzo di account locali](#localaccounts) in questo argomento.|  
|**account Servizio virtuale**|L'**account Servizio virtuale** rappresenta il servizio di Windows. È un account predefinito con privilegi minimi che dispone di autorizzazioni di accesso alla rete. Tale account è consigliato se non si dispone di un account utente di dominio o se si desidera evitare le possibili interruzioni del servizio provocate dall'applicazione di criteri di scadenza delle password.|  
|**Servizio di rete**|**Servizio di rete** è un account predefinito con privilegi minimi che dispone di autorizzazioni di accesso alla rete. <br /><br /> Se si seleziona **Servizio di rete**, tentare di ridurre al minimo il numero degli altri servizi eseguiti con lo stesso account. Una violazione della sicurezza di una delle applicazioni può pregiudicare la sicurezza di tutte le altre applicazioni eseguite con lo stesso account.|  
|**Servizio locale**|**Servizio locale** è un account predefinito simile a un account utente locale di Windows autenticato. I servizi eseguiti tramite l'account **Servizio locale** possono accedere alle risorse di rete come sessione Null senza credenziali. Questo account non è adatto per scenari di distribuzione Intranet in cui il server di report deve connettersi a un database del server di report remoto o a un controller di dominio di rete per autenticare un utente prima dell'apertura di un report o dell'elaborazione di una sottoscrizione.|  
|**Sistema locale**|**Sistema locale** è un account con privilegi elevati, non necessario per l'esecuzione di un server di report. Non utilizzare questo account per le installazioni dei server di report. Scegliere piuttosto un account di dominio o l'account **Servizio di rete** .|  
  
##  <a name="localaccounts"></a> Considerazioni sull'utilizzo di account locali  
 La considerazione principale relativa all'utilizzo di account locali consiste nel determinare se il server di report dovrà accedere a server di database remoti, server della posta e controller di dominio. Se si configura il server di report per l'esecuzione come account utente locale di Windows, Servizio locale o Sistema locale occorrerà tenere conto di alcune considerazioni correlate all'impostazione di altre opzioni di configurazione e alla creazione e al recapito delle sottoscrizioni:  
  
-   Se il servizio viene eseguito utilizzando un account locale e si configura una connessione a un database del server di report remoto, il numero di opzioni disponibili in seguito risulterà limitato. In particolare, se si utilizza un database del server di report remoto, sarà necessario configurare la connessione per l'utilizzo di un account utente di dominio o di un account utente di accesso al database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che disponga dell'autorizzazione necessaria per accedere all'istanza remota di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   L'esecuzione del servizio tramite un account locale introduce anche nuovi requisiti relativi alla creazione delle sottoscrizioni. Il server di report archivia le informazioni relative agli utenti che creano le sottoscrizioni. Se un utente crea una sottoscrizione mentre è connesso con un account di dominio, il servizio del server di report tenterà di connettersi a un controller di dominio per autenticare l'utente al momento dell'elaborazione della sottoscrizione. Se il servizio viene eseguito utilizzando un account locale, la richiesta di autenticazione ha esito negativo quando viene inviata a un controller di dominio remoto dal server di report. Per ovviare a questa limitazione è possibile utilizzare un'estensione personalizzata per l'autenticazione basata su form oppure fare in modo che tutti gli utenti si connettano al server di report tramite un account utente locale.  
  
-   L'esecuzione del servizio tramite un account locale introduce anche nuovi requisiti relativi al recapito delle sottoscrizioni. Alcune estensioni di recapito includono informazioni sull'account utente nelle definizioni delle sottoscrizioni. Se si inviano report a indirizzi di posta elettronica basati su account utente di dominio e il servizio del server di report viene eseguito utilizzando un account locale, il servizio non sarà in grado di accedere a un controller di dominio remoto per risolvere l'account di posta elettronica di destinazione.  
  
-   Gli account di servizio Windows predefiniti (Servizio locale o Servizio di rete) non sono supportati come account del servizio del server di report su un computer con funzioni di controller di dominio.  
  
Per la scelta dell'approccio ottimale per la propria distribuzione, è possibile utilizzare le linee guida e i collegamenti seguenti.  
  
-   [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) nella documentazione online di SQL Server.  
  
-   [Guida alla pianificazione della sicurezza dei servizi e degli account dei servizi](https://go.microsoft.com/fwlink/?LinkId=69155) nel sito Web MSDN.  
  
## <a name="updating-an-expired-password"></a>Aggiornamento di una password scaduta  
 Se il servizio del server di report viene eseguito con un account di dominio e la password scade prima che sia possibile aggiornarla in Gestione configurazione Reporting Services, il servizio non verrà avviato se prima non si specifica una nuova password.  
  
 Se la password dell'account del servizio per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] scade, quando si tenterà di connettersi al server di report verrà restituito l'errore **rsReportServerDatabaseUnavailable** . Per risolvere l'errore è necessario reimpostare la password.  
  
## <a name="troubleshooting-service-identity-update-errors"></a>Risoluzione degli errori di aggiornamento dell'identità del servizio  
 La modifica dell'identità del servizio avvia una serie di eventi che includono il riavvio del servizio, l'aggiornamento della chiave di crittografia protetta da password, l'aggiornamento delle prenotazioni URL e, se si utilizza l'account del servizio per la connessione al database del server di report, l'aggiornamento delle informazioni di connessione al database del server di report. È possibile monitorare lo stato di tali eventi visualizzando le notifiche incluse nel riquadro Risultati nella parte inferiore della pagina. Se durante il processo si verificano errori, è possibile provare a risolverli utilizzando le tecniche seguenti:  
  
-   Se non è possibile ripristinare la chiave simmetrica, tentare di ripristinarla manualmente usando il comando **Ripristina** nella pagina Chiave di crittografia. Se il problema persiste, valutare l'opportunità di eliminare il contenuto crittografato. In questo caso, sarà necessario ricreare le informazioni di connessione all'origine dati e le sottoscrizioni, ma il resto del contenuto sarà ancora disponibile. Per altre informazioni, vedere [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
-   Se non è possibile avviare il servizio, riavviarlo manualmente utilizzando l'applicazione console Servizi in Strumenti di amministrazione.  
  
-   Quando si aggiorna l'account del servizio, possono verificarsi errori relativi alle prenotazioni URL. Ogni prenotazione URL include un descrittore di sicurezza che include a sua volta un elenco di controllo di accesso discrezionale che concede all'account del servizio l'autorizzazione necessaria per accettare richieste nell'URL. Quando si aggiorna l'account, è necessario ricreare l'URL per aggiornare l'elenco di controllo di accesso discrezionale con le nuove informazioni sull'account. Se non è possibile ricreare la prenotazione URL e si è certi della validità dell'account, provare a riavviare il computer. Se l'errore persiste, provare a utilizzare un account diverso.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare gli URL del server di report &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)
