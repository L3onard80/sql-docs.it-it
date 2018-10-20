---
title: Estensione di SQL Server Agent di Studio dei dati di Azure | Microsoft Docs
description: Estensione di SQL Server Agent (anteprima) per Azure Data Studio
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 1ad136bb5bda8534d722b3b89d6731db5b704cb6
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356212"
---
# <a name="sql-server-agent-extension-preview"></a>Estensione di SQL Server Agent (anteprima)

L'estensione di SQL Server Agent (anteprima) è un'estensione per la gestione e risoluzione dei problemi di configurazione e i processi di SQL Agent. Questa estensione è attualmente in anteprima.

Azioni principali includono:
- Processi di elenco SQL Server Agent configurati in un Server SQL
- Visualizza cronologia processi con i risultati dell'esecuzione processo
- Controllo processo base per avviare e arrestare i processi

## <a name="install-the-sql-server-agent-extension"></a>Installare l'estensione di SQL Server Agent

1. Per aprire la gestione delle estensioni e accedere alle estensioni disponibili, selezionare l'icona delle estensioni o scegliere **Estensioni** dal menu **Visualizza**.
2. Selezionare un'estensione disponibile per visualizzare i dettagli.

   ![Installare l'agente](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Selezionare l'estensione desiderata e scegliere **Installa**.
2. Selezionare **Ricarica** per abilitare l'estensione (richiesto solo la prima volta in cui l'estensione viene installata).
1. Passare al dashboard di gestione facendo clic con il tasto destro del mouse sul server o sul database e selezionando **Gestisci**.
2. Le estensioni installate vengono visualizzate come schede nel dashboard di gestione:

   ![Agente di visualizzazione](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Visualizza processi

Quando ci si connette all'estensione di SQL Server Agent, il primo oggetto visualizzato è un elenco di tutti i processi dell'agente.

   ![Visualizza processi](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su SQL Server Agent, [controllare la documentazione.](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017)


