---
title: Visualizzare l'attività dei processi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e1ce3fe6aec1612eff8d9560801119894de15e16
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51702981"
---
# <a name="view-job-activity"></a>Visualizza attività processi
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In questo argomento viene illustrato come visualizzare lo stato di runtime dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
All'avvio di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene creata una nuova sessione e la tabella **sysjobactivity** del database **msdb** viene popolata con tutti i processi definiti esistenti. In questa tabella sono registrati l'attività e lo stato dei processi correnti. Per visualizzare lo stato corrente dei processi è possibile utilizzare Monitoraggio attività processo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Se il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene interrotto in modo imprevisto, per verificare quali processi erano in esecuzione al momento dell'interruzione è possibile fare riferimento alla tabella **sysjobactivity** .  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per visualizzare l'attività del processo utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>Per visualizzare l'attività del processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)], quindi espandere questa istanza.  
  
2.  Espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse su **Monitoraggio attività processi** e scegliere **Visualizza attività processi**.  
  
4.  In **Monitoraggio attività processo**è possibile visualizzare i dettagli relativi a ogni processo definito nel server.  
  
5.  Fare clic con il pulsante destro del mouse su un processo per avviarlo, arrestarlo, attivarlo o disabilitarlo, aggiornarne lo stato visualizzato in Monitoraggio attività processo, eliminarlo o visualizzarne la cronologia o le proprietà.  Per avviare, arrestare, attivare o disabilitare o aggiornare più processi, selezionare più righe in Monitoraggio attività processo e fare clic con il pulsante destro del mouse.  
  
6.  Per aggiornare Monitoraggio attività processo fare clic su **Aggiorna**. Per visualizzare un numero inferiore di righe, fare clic su **Filtro** e specificare i parametri del filtro.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-view-job-activity"></a>Per visualizzare l'attività del processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_help_jobactivity (Transact-SQL)](https://msdn.microsoft.com/d344864f-b4d3-46b1-8933-b81dec71f511).  
  
