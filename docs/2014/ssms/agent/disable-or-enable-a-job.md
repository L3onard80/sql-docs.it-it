---
title: Disabilitare o abilitare un processo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1fa9a2700bd2f6a9ce2b074b1633182fc30c9aa7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211411"
---
# <a name="disable-or-enable-a-job"></a>Abilitare o disabilitare un processo
  In questo argomento viene descritto come disabilitare un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Quando si disabilita un processo, questo non viene eliminato e, se necessario, può essere abilitato nuovamente.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per disabilitare o abilitare un processo utilizzando:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implementazione della sicurezza di SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Con SQL Server Management Studio  
  
#### <a name="to-disable-or-enable-a-job"></a>Per disabilitare o abilitare un processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del, quindi [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]espandere l'istanza.  
  
2.  Espandere **SQL Server Agent**.  
  
3.  Espandere **Processi**e fare clic con il pulsante destro del mouse sul processo da disabilitare o abilitare.  
  
4.  Per disabilitare un processo fare clic su **Disabilita**. Per abilitare un processo fare clic su **Abilita**.  
  
##  <a name="TSQL"></a> Con Transact-SQL  
  
#### <a name="to-disable-or-enable-a-job"></a>Per disabilitare o abilitare un processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- changes the name, description, and enables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 1 ;  
    GO  
    ```  
  
 Per ulteriori informazioni, vedere [sp_update_job &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).  
  
  
