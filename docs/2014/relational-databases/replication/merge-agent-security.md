---
title: Sicurezza agente di merge | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.MA.f1
helpviewer_keywords:
- Merge Agent Security dialog box
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: af3d3490957114d6ba7731b49435dc7e90122f90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62932488"
---
# <a name="merge-agent-security"></a>Sicurezza agente di merge
  La finestra di dialogo **agente di merge sicurezza** consente di specificare l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] account di Windows con cui viene eseguito il agente di merge. L'agente di merge viene eseguito nel server di distribuzione per le sottoscrizioni push e nel Sottoscrittore per le sottoscrizioni pull. L'account di Windows viene definito anche account del *processo*, perché il processo dell'agente viene eseguito con questo account. Le opzioni aggiuntive disponibili in questa finestra di dialogo dipendono dalla modalità con cui si accede a tale finestra di dialogo:  
  
-   Se si accede alla finestra di dialogo dalla Creazione guidata nuova sottoscrizione, è inoltre possibile specificare il contesto in cui l'agente di merge stabilisce le connessioni al Sottoscrittore (per le sottoscrizioni push) o ai server di pubblicazione e di distribuzione (per le sottoscrizioni pull). La connessione può essere effettuata utilizzando l'account di Windows o nel contesto di un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account specificato.  
  
-   Se si accede alla finestra di dialogo dalla finestra di dialogo **Proprietà sottoscrizione** , specificare il contesto in cui l'agente di merge stabilisce le connessioni facendo clic sul pulsante delle proprietà (**...**) nella riga **Connessione al Sottoscrittore** o **Connessione al server di pubblicazione** della finestra di dialogo. Per altre informazioni sull'accesso alla finestra di dialogo **Proprietà sottoscrizione**, vedere [Visualizzare e modificare le proprietà delle sottoscrizioni push](view-and-modify-push-subscription-properties.md) e [Visualizzare e modificare le proprietà delle sottoscrizioni pull](view-and-modify-pull-subscription-properties.md).  
  
 Tutti gli account devono essere validi e per ogni account deve essere stata specificata la password corretta. Gli account e le password vengono convalidati solo dopo l'avvio dell'esecuzione di un agente.  
  
## <a name="options"></a>Opzioni  
 **Account processo**  
 Consente di immettere l'account di Windows con cui viene eseguito l'agente di merge.  
  
-   Per le sottoscrizioni push, l'account deve:  
  
    -   Essere almeno un membro del ruolo predefinito del database **db_owner** nel database di distribuzione.  
  
    -   Essere un membro del ruolo PAL.  
  
    -   Essere un account di accesso associato a un utente nel database di pubblicazione.  
  
    -   Disporre delle autorizzazioni di lettura per la condivisione snapshot.  
  
-   Per le sottoscrizioni pull, l'account deve essere almeno un membro del ruolo predefinito del database **db_owner** nel database di sottoscrizione.  
  
 Sono necessarie autorizzazioni aggiuntive nel caso in cui l'account di processo sia rappresentato durante l'attivazione delle connessioni. Vedere le sezioni **Connetti al server di pubblicazione e al server di distribuzione** e **Connetti al Sottoscrittore** riportate di seguito.  
  
 Non è possibile specificare l' **account del processo** per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]le sottoscrizioni pull di, perché il agente di merge non [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]viene eseguito nelle istanze di.  
  
 **Password** e **Conferma password**  
 Immettere la password per l'account di Windows.  
  
 **Connettersi al server di pubblicazione e al server di distribuzione**  
 Per le sottoscrizioni push, le connessioni al server di pubblicazione e al server di distribuzione vengono sempre stabilite tramite la rappresentazione dell'account specificato nella casella di testo **Account processo** .  
  
 Per le sottoscrizioni pull, scegliere se l'agente di merge deve stabilire le connessioni al server di pubblicazione e al server di distribuzione tramite la rappresentazione dell'account specificato nella casella di testo **Account processo** oppure utilizzando un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si seleziona l'opzione per l'utilizzo di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , immettere un account di accesso e una password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di scegliere di rappresentare l'account di Windows anziché di utilizzare un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 L'account di Windows o l'account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzato per la connessione deve:  
  
-   Essere un membro del ruolo PAL.  
  
-   Essere un account di accesso associato a un utente nel database di pubblicazione.  
  
-   Essere un account di accesso associato a un utente nel database di distribuzione (l'utente può essere l'utente Guest).  
  
-   Disporre delle autorizzazioni di lettura per la condivisione snapshot.  
  
 **Connetti al Sottoscrittore**  
 Per le sottoscrizioni pull, le connessioni al Sottoscrittore vengono sempre stabilite tramite la rappresentazione dell'account specificato nella casella di testo **Account processo** .  
  
 Per le sottoscrizioni push, scegliere se l'agente di merge deve stabilire le connessioni al server di pubblicazione e al server di distribuzione tramite la rappresentazione dell'account specificato nella casella di testo **Account processo** oppure utilizzando un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si seleziona l'opzione per l'utilizzo di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , immettere un account di accesso e una password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  È consigliabile scegliere di rappresentare l'account di Windows anziché di utilizzare un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 L'account di Windows o l'account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzato per la connessione deve essere almeno un membro del ruolo del database predefinito **db_owner** nel database di sottoscrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire gli account di accesso e le password nella replica](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Modello di sicurezza dell'agente di replica](security/replication-agent-security-model.md)   
 [Panoramica degli agenti di replica](agents/replication-agents-overview.md)   
 [Replication Security Best Practices](security/replication-security-best-practices.md)   
 [Sottoscrizione delle pubblicazioni](subscribe-to-publications.md)  
  
  
