---
title: Aggiornare gli strumenti di gestione di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- management tools, upgrading
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 332c513c7c7d76956fc5647d7e4cb96eeac633d7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "67934707"
---
# <a name="upgrade-sql-server-management-tools"></a>Aggiornare gli strumenti di gestione di SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supporta l'aggiornamento da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive. Questo articolo fornisce informazioni sul supporto e sul comportamento dell'aggiornamento degli strumenti e dei componenti di gestione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Posta elettronica database, Piani di manutenzione, XPStar e XPWeb.  
  
> [!IMPORTANT]  
>  Per le installazioni locali, è necessario eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come amministratore. Se si esegue il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio che dispone di autorizzazioni di lettura ed esecuzione per tale condivisione remota.  
  
## <a name="known-upgrade-issues"></a>Problemi di aggiornamento noti  
Prima di eseguire l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], considerare i problemi indicati di seguito.  
  
### <a name="for-all-upgrade-scenarios"></a>Per tutti gli scenari di aggiornamento:  
  
- Tutti i server TSX devono essere aggiornati prima dell'aggiornamento del server MSX. Per altre informazioni su MSX/TSX in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md).  
  
-   Tutti i componenti inclusi in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere aggiornati simultaneamente. I numeri di versione dei componenti del [!INCLUDE[ssDE](../../includes/ssde-md.md)], di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]e di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] devono essere identici in un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   È possibile aggiungere componenti a un'installazione esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel momento in cui si esegue l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per altre informazioni, vedere [Eseguire l'aggiornamento a SQL Server 2016 usando l'Installazione guidata &#40;Programma di installazione&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gli strumenti client ad esempio [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], [!INCLUDE[ssDE](../../includes/ssde-md.md)] Ottimizzazione guidata, sqlcmd e osql, non vengono aggiornati a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Gli strumenti client vengono invece eseguiti in modalità affiancata con gli strumenti delle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] supporta l'importazione delle impostazioni dalle versioni precedenti degli strumenti client di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Durante l'aggiornamento, l'autenticazione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà aggiornata dall'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'autenticazione di Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] L'autenticazione non è supportata in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   I dati per processi e avvisi verranno mantenuti durante l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Se nell'istanza da aggiornare viene utilizzato SQLMail, le stored procedure estese associate saranno supportate e attivate in seguito all'aggiornamento. In caso contrario, saranno disattivate.  
  
-   Posta elettronica database, anche noto come SQLiMail, verrà aggiornato con il componente [!INCLUDE[ssDE](../../includes/ssde-md.md)] di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per impostazione predefinita, Posta elettronica database verrà utilizzato in seguito all'aggiornamento. Qualsiasi aggiornamento dello schema deve essere riconciliato con uno script di aggiornamento in seguito all'aggiornamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Backward Compatibility_deleted](https://msdn.microsoft.com/library/15d9117e-e2fa-4985-99ea-66a117c1e9fd)   
 [Eseguire l'aggiornamento a SQL Server usando l'Installazione guidata &#40;programma di installazione&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
