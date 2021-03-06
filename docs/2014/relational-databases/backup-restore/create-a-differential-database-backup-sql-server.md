---
title: Creare un backup differenziale di database (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full differential backups [SQL Server]
- database backups [SQL Server], full differential backups
- backing up databases [SQL Server], full differential backups
- backups [SQL Server], creating
ms.assetid: 70f49794-b217-4519-9f2a-76ed61fa9f99
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4be1c196adbe21635c1339da3d5ec7ca519001fc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62876600"
---
# <a name="create-a-differential-database-backup-sql-server"></a>Creazione di un backup differenziale del database (SQL Server)
  In questo argomento viene descritto come creare un backup differenziale del database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Prerequisiti](#Prerequisites)  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per creare un backup differenziale del database utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Non è possibile utilizzare l'istruzione BACKUP in una transazione esplicita o implicita.  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   Per creare un backup differenziale del database, è necessario che sia disponibile un backup completo precedente del database. Se non è mai stato creato un backup del database selezionato, eseguire un backup completo prima di creare backup differenziali. Per altre informazioni, vedere [Creare un backup completo del database &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).  
  
###  <a name="Recommendations"></a> Raccomandazioni  
  
-   A causa dell'aumento delle dimensioni dei backup differenziali, il ripristino di un backup di questo tipo può comportare un notevole aumento del tempo necessario per il ripristino di un database. È consigliabile pertanto eseguire un nuovo backup completo a intervalli prestabiliti per creare una nuova base differenziale per i dati. È ad esempio possibile eseguire un backup completo settimanale dell'intero database, ovvero un backup completo del database, seguito da una serie regolare di backup differenziali del database nell'arco della settimana.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Le autorizzazioni BACKUP DATABASE e BACKUP LOG vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** e dei ruoli predefiniti del database **db_owner** e **db_backupoperator** .  
  
 Eventuali problemi correlati alla proprietà e alle autorizzazioni sul file fisico del dispositivo di backup possono interferire con l'operazione di backup. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia possibile leggere e scrivere sul dispositivo e che l'account utilizzato per eseguire il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponga delle autorizzazioni di scrittura. Le autorizzazioni di accesso ai file, tuttavia, non vengono controllate dalla stored procedure [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)che aggiunge una voce per un dispositivo di backup nelle tabelle di sistema. Di conseguenza, i problemi relativi all'accesso e alla proprietà del file fisico del dispositivo di backup potrebbero emergere solo in fase di accesso alla risorsa fisica durante un tentativo di backup o ripristino.  
  
##  <a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-create-a-differential-database-backup"></a>Per creare un backup differenziale del database  
  
1.  Dopo aver stabilito la connessione all'istanza appropriata del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server per espanderne l'albero.  
  
2.  Espandere **Database**e, a seconda del database, selezionare un database utente o espandere **Database di sistema** e selezionare un database di sistema.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**e quindi fare clic su **Backup**. Verrà visualizzata la finestra di dialogo **Backup database** .  
  
4.  Verificare il nome del database nella casella di riepilogo **Database** . È possibile selezionare facoltativamente un database diverso nell'elenco.  
  
     È possibile eseguire un backup differenziale per qualsiasi modello di recupero (con registrazione completa, con registrazione minima delle operazioni bulk o con registrazione minima).  
  
5.  Nella casella di riepilogo **Tipo di backup** selezionare **Differenziale**.  
  
    > [!IMPORTANT]  
    >  Quando è selezionata l'opzione **differenziale** , verificare che la casella di controllo **copia solo backup** sia deselezionata.  
  
6.  In **Componente di cui eseguire il backup**fare clic su **Database**.  
  
7.  Accettare il nome predefinito del set di backup indicato nella casella di testo **Nome** oppure immettere un nome diverso per il set di backup.  
  
8.  Facoltativamente, immettere una descrizione del set di backup nella casella di testo **Descrizione** .  
  
9. Specificare la scadenza del set di backup:  
  
    -   Per impostare la scadenza del set di backup dopo un numero di giorni specifico, fare clic su **Dopo** (opzione predefinita) e immettere il numero di giorni dopo la creazione del set trascorsi i quali il set scadrà. È possibile impostare un valore compreso nell'intervallo da 0 a 99999 giorni. L'impostazione del valore 0 giorni indica che il set di backup non ha scadenza.  
  
         Il valore predefinito viene impostato nell'opzione **Periodo di memorizzazione predefinito supporti di backup (giorni)** della finestra di dialogo **Proprietà server** (pagina**Impostazioni database** ). Per accedere alla pagina, fare clic con il pulsante destro del mouse sul nome del server in Esplora oggetti e scegliere Proprietà, quindi selezionare la pagina **Impostazioni database** .  
  
    -   Per impostare una data di scadenza specifica per il set di backup, fare clic su **Il**e immettere la data di scadenza del set.  
  
10. Fare clic su **Disco** o su **Nastro**per selezionare il tipo di destinazione del backup. Per selezionare il percorso per un massimo di 64 unità disco o nastro contenenti un singolo set di supporti, fare clic su **Aggiungi**. I percorsi selezionati vengono visualizzati nella casella di riepilogo **Backup su** .  
  
     Per rimuovere una destinazione di backup, selezionarla e fare clic su **Rimuovi**. Per visualizzare il contenuto di una destinazione di backup, selezionarla e fare clic su **Contenuto**.  
  
11. Per visualizzare o selezionare le opzioni avanzate, fare clic su **Opzioni** nel riquadro **Selezione pagina** .  
  
12. Selezionare un'opzione **Sovrascrivi supporti** facendo clic su una delle opzioni seguenti:  
  
    -   **Esegui backup nel set di supporti esistente**  
  
         Per questa opzione, fare clic su **Accoda al set di backup esistente** o **Sovrascrivi tutti i set di backup esistenti**. Facoltativamente, selezionare la casella di controllo **Controlla nome set di supporti e scadenza set di backup** e, sempre facoltativamente, immettere un nome nella casella di testo **Nome set di supporti** . Se non si specifica un nome, verrà creato un set di supporti con nome vuoto. Se si specifica un nome, il supporto (nastro o disco) verrà controllato per verificare che il nome effettivo corrisponda al nome specificato.  
  
         Se non si specifica il nome del set di supporti e si seleziona la casella di controllo per il controllo del nome, in caso di esito positivo anche il nome dei supporti nei supporti risulterà vuoto.  
  
    -   **Esegui backup in un nuovo set di supporti e cancella tutti i set di backup esistenti**  
  
         Per questa opzione, immettere un nome nella casella di testo **Nome nuovo set di supporti** e, facoltativamente, aggiungere una descrizione per il set di supporti nella casella di testo **Descrizione nuovo set di supporti** .  
  
13. Nella sezione **Affidabilità** selezionare facoltativamente una delle opzioni seguenti:  
  
    -   **Verifica backup al termine**.  
  
    -   **Esegui checksum prima della scrittura nei supporti**e, facoltativamente, **Continua in caso di errori checksum**. Per informazioni sui checksum, vedere [Possibili errori relativi ai supporti durante il backup e il ripristino &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md).  
  
14. Se si esegue il backup su un'unità nastro, come specificato nella sezione **Destinazione** della pagina **Generale** , l'opzione **Scarica nastro al termine del backup** sarà attiva. Se si seleziona questa opzione, verrà inoltre attivata l'opzione **Riavvolgi il nastro prima di scaricarlo** .  
  
    > [!NOTE]  
    >  Le opzioni presenti nella sezione **Log delle transazioni** sono attive solo in caso di backup di un log delle transazioni, come specificato nella sezione **Tipo backup** nella pagina **Generale** .  
  
15. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] e versioni successive supporta la [compressione dei backup](backup-compression-sql-server.md). Per impostazione predefinita, la compressione di un backup dipende dal valore dell'opzione di configurazione del server **Valore predefinito di compressione backup**. Tuttavia, indipendentemente dall'impostazione predefinita a livello di server corrente, è possibile comprimere un backup selezionando **Comprimi backup**ed è possibile impedire la compressione selezionando **Non comprimere il backup**.  
  
     **Per visualizzare l'impostazione predefinita corrente della compressione dei backup**  
  
    -   [Visualizzare o configurare l'opzione di configurazione del server backup compression default](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
    > [!NOTE]  
    >  In alternativa, è possibile creare backup differenziali del database tramite Creazione guidata piano di manutenzione.  
  
##  <a name="TsqlProcedure"></a> Con Transact-SQL  
  
#### <a name="to-create-a-differential-database-backup"></a>Per creare un backup differenziale del database  
  
1.  Per creare il backup differenziale del database, eseguire l'istruzione BACKUP DATABASE specificando:  
  
    -   Il nome del database di cui eseguire il backup.  
  
    -   Il dispositivo di backup in cui archiviare il backup completo del database.  
  
    -   Clausola DIFFERENTIAL per specificare che viene effettuato il backup solo delle parti del database modificate dopo l'ultimo backup completo del database stesso.  
  
     La sintassi richiesta è la seguente:  
  
     BACKUP DATABASE *database_name* TO <backup_device> WITH DIFFERENTIAL  
  
###  <a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio vengono creati un backup completo e un backup differenziale del database `MyAdvWorks` .  
  
```sql  
-- Create a full database backup first.  
BACKUP DATABASE MyAdvWorks   
   TO MyAdvWorks_1   
   WITH INIT;  
GO  
-- Time elapses.  
-- Create a differential database backup, appending the backup  
-- to the backup device containing the full database backup.  
BACKUP DATABASE MyAdvWorks  
   TO MyAdvWorks_1  
   WITH DIFFERENTIAL;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Backup differenziali &#40;SQL Server&#41;](differential-backups-sql-server.md)   
 [Creare un backup completo del database &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)   
 [Backup di file e filegroup &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Ripristinare un backup differenziale del database &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md)   
 [Ripristinare un backup del log delle transazioni &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [Piani di manutenzione](../maintenance-plans/maintenance-plans.md)   
 [Backup completi del file &#40;SQL Server&#41;](full-file-backups-sql-server.md)  
  
  
