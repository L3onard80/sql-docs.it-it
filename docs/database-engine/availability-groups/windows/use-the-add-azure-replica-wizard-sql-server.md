---
title: Usare la procedura guidata Aggiungi replica Azure (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a2f46a7451fa246065ae11b3771e22b7c609f4f
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602961"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Utilizzare la procedura guidata Aggiungi replica Azure (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La procedura guidata Aggiungi replica Azure consente di creare una nuova macchina virtuale di Azure in un ambiente IT ibrido e di configurarla come replica secondaria per un gruppo di disponibilità Always On nuovo o esistente.  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
     [Security](#Security)  
  
-   **Per aggiungere una replica mediante:**  [Procedura guidata Aggiungi replica Azure (SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 Se non è mai stata aggiunta una replica di disponibilità a un gruppo di disponibilità, vedere le sezioni "Istanze del server" e "Repliche e gruppi di disponibilità" in [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario essere connessi all'istanza del server che ospita la replica primaria corrente.  
  
-   È necessario utilizzare un ambiente IT ibrido in cui nella subnet locale sia presente una VPN da sito a sito con Windows Azure. Per altre informazioni, vedere [Creare una rete virtuale con una connessione VPN da sito a sito usando il portale di Azure classico](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Il gruppo di disponibilità deve contenere le repliche di disponibilità locali.  
  
-   I client nel listener del gruppo di disponibilità devono avere la connettività a Internet se desiderano mantenere la connettività con il listener quando viene eseguito il failover del gruppo di disponibilità in una replica di Windows Azure.  
  
-   **Prerequisiti per l'utilizzo della sincronizzazione dei dati iniziale completa** È necessario specificare una condivisione di rete affinché la procedura guidata possa creare e accedere ai backup. Per la replica primaria, all'account usato per avviare il [!INCLUDE[ssDE](../../../includes/ssde-md.md)] devono essere associate le autorizzazioni del file system in lettura e scrittura per una condivisione di rete. Per le repliche secondarie, all'account deve essere associata l'autorizzazione di lettura per la condivisione di rete.  
  
     Se non è possibile usare la procedura guidata per eseguire la sincronizzazione dei dati iniziale completa, sarà necessario preparare i database secondari manualmente. Tale operazione può essere eseguita prima o dopo l'esecuzione della procedura guidata. Per altre informazioni, vedere [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Vedere [Security](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)  
  
##  <a name="SSMSProcedure"></a> Utilizzo della procedura guidata Aggiungi replica Azure (SQL Server Management Studio)  
 La procedura guidata Aggiungi replica Azure può essere avviata dalla [Pagina Specifica repliche](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md). Questa pagina può essere visualizzata in due modi:  
  
-   [Usare la Creazione guidata gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Usare la procedura guidata Aggiungi replica a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 Dopo aver avviato la procedura guidata Aggiungi replica Azure effettuare i passaggi seguenti:  
  
1.  Scaricare innanzitutto un certificato di gestione per la sottoscrizione di Windows Azure. Fare clic su **Download** per aprire la pagina di accesso.  
  
2.  Accedere a Microsoft Azure con il proprio account Microsoft o aziendale. L'account Microsoft o aziendale è nel formato di un indirizzo di posta elettronica, ad esempio HYPERLINK "mailto:patc@contoso.com" patc@contoso.com. Per altre informazioni sulle credenziali di Azure, vedere [Microsoft Account for Organizations FAQ](https://technet.microsoft.com/jj592903) (Domande frequenti sull'account Microsoft per le organizzazioni) e [Troubleshooting sign-in problems with your organizational account](https://support.microsoft.com/kb/2756852)(Risoluzione dei problemi di accesso con l'account dell'organizzazione).  
  
3.  Connettersi quindi alla sottoscrizione facendo clic su **Connetti**. Una volta connessi, gli elenchi a discesa vengono popolati con i parametri di Microsoft Azure, ad esempio **Rete virtuale** e **Subnet rete virtuale**.  
  
4.  Specificare le impostazioni per la macchina virtuale Windows Azure che ospiterà la nuova replica secondaria:  
  
     Immagine  
     Nome dell'immagine di SQL Server da utilizzare per la macchina virtuale Windows Azure  
  
     Dimensioni VM  
     Dimensioni della macchina virtuale Windows Azure  
  
     Nome VM  
     Nome DNS della macchina virtuale Windows Azure  
  
     Nome utente VM  
     Nome utente dell'amministratore predefinito della macchina virtuale Windows Azure  
  
     Password amministratore VM (e Conferma password)  
     Password dell'amministratore predefinito della macchina virtuale Windows Azure  
  
     Rete virtuale  
     Rete virtuale in cui posizionare la macchina virtuale Windows Azure  
  
     Subnet rete virtuale  
     Subnet della rete virtuale in cui posizionare la macchina virtuale Windows Azure  
  
     Dominio  
     Dominio Active Directory (AD) a cui aggiungere la macchina virtuale Windows Azure  
  
     Nome utente di dominio  
     Nome utente di Active Directory utilizzato per aggiungere la macchina virtuale Windows Azure al dominio  
  
     Password  
     Password utilizzata per aggiungere la macchina virtuale Windows Azure al dominio  
  
5.  Fare clic su **OK** per eseguire il commit delle impostazioni e chiudere la procedura guidata Aggiungi replica Azure.  
  
6.  Continuare con il resto dei passaggi di configurazione della [Pagina Specifica repliche](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) come per qualsiasi nuova replica.  
  
     Dopo avere completato la Creazione guidata gruppo di disponibilità o la procedura guidata Aggiungi replica a gruppo di disponibilità, il processo di configurazione esegue tutte le operazioni in Microsoft Azure per creare la nuova macchina virtuale, aggiungerla al dominio di Active Directory, aggiungerla al cluster di Windows, abilitare la Disponibilità elevata Always On e aggiungere la nuova replica al gruppo di disponibilità.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Aggiungere una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Prerequisiti, restrizioni e raccomandazioni per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [Aggiungere una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
