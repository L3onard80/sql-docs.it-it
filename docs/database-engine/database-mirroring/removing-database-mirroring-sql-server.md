---
title: Rimozione di mirroring del database (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ae494ae5b12cf99e836869f65c055803dd9666e6
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68025265"
---
# <a name="removing-database-mirroring-sql-server"></a>Rimozione di mirroring del database (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il proprietario del database può arrestare manualmente una sessione di mirroring del database in qualsiasi momento in uno dei partner.  
  
## <a name="impact-of-removing-mirroring"></a>Impatto della rimozione del mirroring  
 Quando il mirroring viene rimosso, si verificano le situazioni seguenti:  
  
-   La relazione, se presente, tra i partner e tra ogni partner e il server di controllo del mirroring viene interrotta in modo permanente.  
  
     Se al momento dell'interruzione della sessione è in corso la comunicazione tra i partner, la relazione viene immediatamente arrestata in entrambi i computer. Se i partner non stanno comunicando, ovvero il database è in stato DISCONNECTED al momento dell'arresto, la relazione viene immediatamente interrotta nel partner in cui è stato arrestato il mirroring. Quando l'altro partner tenta di riconnettersi, individua che la sessione di mirroring del database è stata terminata.  
  
-   Le informazioni sulla sessione di mirroring vengono eliminate, diversamente da ciò che si verifica nel caso di sospensione di una sessione. Il mirroring viene rimosso sia nel database principale, sia nel database mirror. In **sys.databases** la colonna **mirroring_state** e tutte le altre colonne di mirroring vengono impostate su NULL. Per altre informazioni, vedere [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md).  
  
-   Viene mantenuta ogni istanza del server partner con una copia distinta del database.  
  
-   Il database mirror viene lasciato nello stato RESTORING (vedere la colonna **state** di **sys.databases**), poiché è stato creato tramite RESTORE WITH NORECOVERY. A questo punto, è possibile eliminare il database mirror precedente o recuperarlo tramite WITH RECOVERY. Il database recuperato presenterà alcune divergenze rispetto al database principale precedente, in quanto tramite il recupero viene avviato un nuovo fork di recupero.  
  
> [!NOTE]  
>  Per proseguire il mirroring dopo avere arrestato una sessione, è necessario stabilire una nuova sessione di mirroring del database. Se dopo l'arresto del mirroring è stato creato un backup del log, è necessario applicarlo al database mirror prima di riavviare il mirroring.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
 **Per rimuovere il mirroring del database**  
  
-   [Rimuovere il mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
 **Per avviare il mirroring del database**  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/database-mirroring-establish-session-windows-authentication.md)  
  
  
## <a name="see-also"></a>Vedere anche  
 [Mirroring del database di ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Sospensione e ripresa del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/pausing-and-resuming-database-mirroring-sql-server.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  
