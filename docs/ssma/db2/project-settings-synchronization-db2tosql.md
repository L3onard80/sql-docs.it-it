---
title: Impostazioni progetto (sincronizzazione) (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a5629a72-8c17-46a4-bb4d-19d51a0b98a2
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 38b3da74ce30799a01f28f3961a4fa0461d7543f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060168"
---
# <a name="project-settingssynchronization-db2tosql"></a>Impostazioni progetto (sincronizzazione) (DB2ToSQL)
La pagina sincronizzazione della finestra di dialogo **Impostazioni progetto** contiene impostazioni che consentono di personalizzare il modo in cui SSMA carica e aggiorna gli oggetti di database, ad esempio tabelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e stored procedure, in.  
  
Le opzioni predefinite delle azioni specificano le impostazioni predefinite per l'aggiornamento degli oggetti dal database DB2 e la sincronizzazione degli oggetti con il database SQL Server. Per ulteriori informazioni, vedere [Refresh from Database &#40;DB2ToSQL&#41;](../../ssma/db2/refresh-from-database-db2tosql.md).  
  
È possibile accedere a due diverse pagine di sincronizzazione che contengono le stesse impostazioni:  
  
-   Per specificare le impostazioni per tutti i progetti SSMA futuri, scegliere **Impostazioni progetto predefinite**dal menu **strumenti** , quindi fare clic su **Sincronizza** nella parte inferiore del riquadro sinistro.  
  
-   Per specificare le impostazioni per il progetto corrente, scegliere **Impostazioni progetto**dal menu **strumenti** , quindi fare clic su **Sincronizza** nella parte inferiore del riquadro sinistro.  
  
## <a name="miscellaneous-options"></a>Opzioni varie  
**Tenta**  
Specifica il numero di tentativi che SSMA deve eseguire quando carica gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in. Gli oggetti che non vengono caricati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel tentativo corrente verranno ritentati fino a quando SSMA non raggiunge il numero massimo di tentativi nel processo di sincronizzazione corrente. Il valore predefinito impostato è **2**  
  
## <a name="synchronization-for-db2-options"></a>Sincronizzazione per le opzioni DB2  
**Azione per la modifica di oggetti locali e remoti**  
Consente di specificare l'impostazione predefinita nella finestra di dialogo di sincronizzazione quando la definizione dell'oggetto viene modificata in SSMA e nel server di database. Il valore predefinito impostato è **Aggiorna da database**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA caricherà le definizioni del database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
**Azione per la modifica di un oggetto locale**  
Consente di specificare l'impostazione predefinita nella finestra di dialogo di sincronizzazione quando l'oggetto viene modificato in SSMA. Il valore predefinito impostato è **Skip**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA caricherà le definizioni del database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
**Azione per la modifica di un oggetto remoto**  
Consente di specificare l'impostazione predefinita nella finestra di dialogo di sincronizzazione in caso di modifica degli oggetti nel server di database. Il valore predefinito impostato è **Aggiorna da database**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA caricherà le definizioni del database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
**Azione quando mancano i metadati degli oggetti locali**  
Specifica l'impostazione predefinita nella finestra di dialogo di sincronizzazione quando mancano i metadati locali. Il valore predefinito impostato è **Aggiorna da database**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA caricherà le definizioni del database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
## <a name="synchronization-for-sql-server-options"></a>Sincronizzazione per le opzioni di SQL Server  
**Azione per la modifica di oggetti locali e remoti**  
Consente di specificare l'impostazione predefinita nella finestra di dialogo di sincronizzazione quando la definizione dell'oggetto viene modificata in SSMA e nel server di database. Il valore predefinito impostato è **Scrivi nel database**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA caricherà le definizioni del database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Scrivi nel database**, SSMA aggiornerà gli oggetti nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
**Azione per la modifica di un oggetto locale**  
Consente di specificare l'impostazione predefinita nella finestra di dialogo di sincronizzazione quando l'oggetto viene modificato in SSMA. Il valore predefinito impostato è **Scrivi nel database**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA caricherà le definizioni del database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Scrivi nel database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
**Azione per la modifica di un oggetto remoto**  
Consente di specificare l'impostazione predefinita nella finestra di dialogo di sincronizzazione in caso di modifica degli oggetti nel server di database.  Il valore predefinito impostato è **Aggiorna da database**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA caricherà le definizioni del database nei metadati quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Scrivi nel database**, SSMA aggiornerà l'oggetto nel database in base al contenuto dei metadati SSMA quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
**Azione quando mancano i metadati degli oggetti locali**  
Specifica l'impostazione predefinita nella finestra di dialogo di sincronizzazione quando mancano i metadati locali. Il valore predefinito impostato è **Aggiorna da database**.  
  
-   Se si seleziona **Aggiorna da database**, SSMA seleziona l'opzione **Aggiorna da database** quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Scrivi nel database**, SSMA eliminerà l'oggetto dal database quando viene soddisfatta la condizione.  
  
-   Se si seleziona **Ignora**, SSMA non eseguirà alcuna azione di aggiornamento.  
  
