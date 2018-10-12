---
title: Visualizzazione di un log di controllo di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b05de4a591964336b9d54ff3319086f818d6231f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650239"
---
# <a name="view-a-sql-server-audit-log"></a>Visualizzazione di un log di controllo di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questo argomento descrive come visualizzare un log di controllo di SQL Server in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per visualizzare un log di controllo di SQL Server mediante:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È richiesta l'autorizzazione **CONTROL SERVER** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>Per visualizzare un log di controllo di SQL Server  
  
1.  In Esplora oggetti espandere la cartella **Sicurezza** .  
  
2.  Espandere la cartella **Controlli** .  
  
3.  Fare clic con il pulsante destro del mouse sul log di controllo da visualizzare e selezionare **Visualizza log di controllo**. Si aprirà la finestra di dialogo **Visualizzatore file di log** _nome\_server_. Per altre informazioni, vedere [Log File Viewer F1 Help](../../../relational-databases/logs/log-file-viewer-f1-help.md).  
  
4.  Al termine, fare clic su **Chiudi**.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] consiglia di visualizzare il log di controllo usando il Visualizzatore file di log. Tuttavia, se si sta creando un sistema di monitoraggio automatizzato, è possibile leggere direttamente le informazioni nel file di controllo usando la funzione [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). La lettura diretta del file restituisce i dati in un formato leggermente diverso (non elaborato). Per altre informazioni, vedere **sys.fn_get_audit_file** .  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Audit &#40;Database Engine&#41;](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md)   
 [Scrittura di eventi di controllo di SQL Server nel registro di sicurezza](../../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md)  
  
  
