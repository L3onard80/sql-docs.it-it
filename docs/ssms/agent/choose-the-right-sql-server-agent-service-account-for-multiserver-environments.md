---
title: Scegliere l'account del servizio Agent per ambienti multiserver
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ecbf0a9d692092d61b3d10ae54f6d25afb4d7ba8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "75242502"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>Scegliere l'account di servizio SQL Server Agent adatto ad ambienti multiserver

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

L'account di Windows scelto per il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent può influenzare il comportamento di un ambiente multiserver, come illustrato di seguito:  
  
-   Se si esegue il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent con un account che non appartiene al gruppo Administrators locale di Windows, è possibile che l'integrazione dei server di destinazione nei server master abbia esito negativo. In questo caso, verrà visualizzato il messaggio di errore seguente:  
  
    "Operazione di integrazione non riuscita."  
  
    Per risolvere il problema, riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
-   Quando il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene eseguito con l'account di sistema locale, le operazioni tra server master e server di destinazione sono supportate solo se entrambi risiedono nello stesso computer. Se si utilizza questa configurazione, quando si integrano i server di destinazione in un server master, verrà visualizzato il seguente messaggio:  
  
    "Verifica che l'account di avvio dell'agente per *<target_server_computer_name>* disponga dei diritti per l'accesso come server di destinazione".  
  
    Questo messaggio può essere ignorato. L'operazione di integrazione verrà completata correttamente.  
  
Per informazioni su come selezionare l'account di avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, vedere [Selezionare un account per il servizio SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md).  
  
