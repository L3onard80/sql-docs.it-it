---
title: Panoramica di SQL Server in Linux
description: Questo articolo descrive la modalità di esecuzione di SQL Server in Linux e spiega come ottenere altre informazioni.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: 31904a43dba642c73620a66bcf4abaa066b5ef82
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "73531277"
---
# <a name="sql-server-on-linux"></a>SQL Server in Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: moniker range="= sql-server-2017 || = sqlallproducts-allversions"
A partire da SQL Server 2017, è possibile eseguire SQL Server in Linux. Si tratta dello stesso motore di database di SQL Server, con molte funzionalità e molti servizi simili indipendentemente dal sistema operativo.
::: moniker-end

::: moniker range=">= sql-server-ver15 || >= sql-server-linux-ver15"
SQL Server 2019 può essere eseguito in Linux. Si tratta dello stesso motore di database di SQL Server, con molte funzionalità e molti servizi simili indipendentemente dal sistema operativo. Per altre informazioni su questa versione, vedere [Novità di SQL Server 2019 per Linux](sql-server-linux-whats-new-2019.md).
::: moniker-end

::: moniker range="= sql-server-2017"
> [!TIP]
> [SQL Server 2019](sql-server-linux-overview.md?view=sql-server-ver15) è disponibile. Per informazioni sulle novità per Linux nella versione più recente, vedere [Novità di SQL Server 2019 per Linux](sql-server-linux-whats-new-2019.md?view=sql-server-ver15).
::: moniker-end

::: moniker range="= sql-server-linux-2017"
> [!TIP]
> [SQL Server 2019](sql-server-linux-overview.md?view=sql-server-linux-ver15) è disponibile. Per informazioni sulle novità per Linux nella versione più recente, vedere [Novità di SQL Server 2019 per Linux](sql-server-linux-whats-new-2019.md?view=sql-server-linux-ver15).
::: moniker-end

::: moniker range="= sqlallproducts-allversions"
> [!TIP]
> SQL Server 2019 è disponibile. Per informazioni sulle novità per Linux nella versione più recente, vedere [Novità di SQL Server 2019 per Linux](sql-server-linux-whats-new-2019.md).
::: moniker-end

## <a name="install"></a>Installazione

Per iniziare, installare SQL Server in Linux usando una delle guide di avvio rapido seguenti:

- [Eseguire l'installazione in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Eseguire l'installazione in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Eseguire l'installazione in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Esecuzione in Docker](quickstart-install-connect-docker.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

> [!NOTE]
> Anche Docker può essere eseguito in più piattaforme. Ciò significa che è possibile eseguire l'immagine Docker in Linux, Mac e Windows.

## <a name="connect"></a>Connessione

Dopo l'installazione, connettersi all'istanza di SQL Server nel computer Linux. È possibile connettersi in locale o in remoto con un'ampia gamma di strumenti e driver. Le guide di avvio rapido illustrano come usare lo strumento da riga di comando [sqlcmd](sql-server-linux-setup-tools.md). Gli altri strumenti disponibili sono:

| Strumento | Esercitazione |
|-----|-----|
| Visual Studio Code (VS Code) | [Usare VS Code con SQL Server in Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Usare SSMS in Windows per la connessione a SQL Server in Linux](sql-server-linux-manage-ssms.md) |
| SQL Server Data Tools (SSDT) | [Usare SSDT con SQL Server in Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Esplora

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

Il motore di database sottostante di SQL Server 2017 è lo stesso in tutte le piattaforme supportate, incluso Linux. Molte funzioni e funzionalità esistenti, quindi, funzionano allo stesso modo in Linux. Quest'area della documentazione espone alcune di queste funzionalità dalla prospettiva di Linux, oltre a richiamare aree che in Linux presentano requisiti specifici.

Se si ha già familiarità con SQL Server, rivedere le [Note sulla versione](sql-server-linux-release-notes.md) per alcune linee guida generali e per informazioni sui problemi noti di questa versione. Vedere quindi le [novità di SQL Server in Linux](sql-server-linux-whats-new.md) e le [novità di SQL Server 2017 nel complesso](../sql-server/what-s-new-in-sql-server-2017.md).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15"

Il motore di database sottostante a [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] è lo stesso in tutte le piattaforme supportate, incluso Linux. Molte funzioni e funzionalità esistenti, quindi, funzionano allo stesso modo in Linux. Quest'area della documentazione espone alcune di queste funzionalità dalla prospettiva di Linux, oltre a richiamare aree che in Linux presentano requisiti specifici.

Se si ha già familiarità con SQL Server in Linux, rivedere le [Note sulla versione](sql-server-linux-release-notes-2019.md) per alcune linee guida generali e per informazioni sui problemi noti di questa versione. Vedere quindi le [novità di SQL Server 2019 in Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

::: moniker-end

<!--SQL Server All Versions-->
::: moniker range="=sqlallproducts-allversions"

Il motore di database sottostante a SQL Server 2017 e [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] è lo stesso in tutte le piattaforme supportate, incluso Linux. Molte funzioni e funzionalità esistenti, quindi, funzionano allo stesso modo in Linux. Quest'area della documentazione espone alcune di queste funzionalità dalla prospettiva di Linux, oltre a richiamare aree che in Linux presentano requisiti specifici.

Se si ha già familiarità con SQL Server in Linux, rivedere le note sulla versione:

- [Note sulla versione di SQL Server 2017](sql-server-linux-release-notes.md)
- [Note sulla versione di SQL Server 2019](sql-server-linux-release-notes-2019.md)

Vedere quindi le novità:

- [Novità di SQL Server 2017](sql-server-linux-whats-new.md)
- [Novità di SQL Server 2019 in Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sql-server-on-linux)

::: moniker-end

> [!TIP]
> Per le risposte alle domande frequenti, vedere [Domande frequenti su SQL Server in Linux](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
