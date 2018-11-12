---
title: Analitica di Python nel database per sviluppatori SQL | Microsoft Docs
description: Informazioni su come incorporare codice Python in stored procedure SQL Server e funzioni T-SQL.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8c992cbda06d158bec0b76d6d46d71157a08cf3e
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51032988"
---
# <a name="tutorial-in-database-python-analytics-for-sql-developers"></a>Tutorial: Analitica di In-Database Python per gli sviluppatori SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questa esercitazione per programmatori SQL indicazioni, informazioni sull'integrazione di Python tramite la creazione e distribuzione di una macchina basata su Python e imparando a usare soluzioni una [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) database in SQL Server. 

Questa esercitazione presenta funzioni di Python usate in un flusso di lavoro di modellazione dati. Passaggi includono l'esplorazione dei dati, creazione e training di un modello di classificazione binaria e la distribuzione del modello. Si userà i dati di esempio dei Taxi di New York City e Commission Limosine, e il modello che si compilerà consente di stimare se una corsa è probabile che risulterà in un suggerimento basato sull'ora del giorno, distanza percorsa e località di partenza. Tutto il codice Python usato in questa esercitazione viene eseguito il wrapping nelle stored procedure da creare ed eseguire in Management Studio.

> [!NOTE]
> Questa esercitazione è disponibile in R e Python. Per la versione di R, vedere [analitica nel database per gli sviluppatori di R](sqldev-in-database-r-for-sql-developers.md).

## <a name="overview"></a>Panoramica

Il processo di creazione di una soluzione di apprendimento è complessa può includere più strumenti e il coordinamento di esperti in materia in diverse fasi:

+ acquisizione e pulizia dei dati
+ esaminando i dati e creazione di funzionalità utili per la modellazione
+ set di training e il modello di ottimizzazione
+ distribuzione nell'ambiente di produzione

Sviluppo e test del codice effettivo è opportuno usare un ambiente di sviluppo dedicato. Tuttavia, dopo che lo script è stato testato completamente, è possibile distribuire facilmente venga [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Wrapping di codice esterni nelle stored procedure è il meccanismo principale per il codice operatività in SQL Server.

Se si è un programmatore SQL familiarità con Python o sviluppatori Python per SQL, questa esercitazione in più parti introduce un flusso di lavoro tipico per condurre analitica nel database con SQL Server e Python. 

+ [Lezione 1: Esplorare e visualizzare i dati usando Python](sqldev-py3-explore-and-visualize-the-data.md)

+ [Lezione 2: Creare una data funzionalità usando funzioni SQL personalizzate](sqldev-py4-create-data-features-using-t-sql.md)

+ [Lezione 3: Eseguire il training e salvataggio di un modello Python con T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

+ [Lezione 4: Stimare i possibili risultati usando un modello Python in una stored procedure](sqldev-py6-operationalize-the-model.md)

Dopo aver salvato il modello al database, è possibile chiamare il modello per le stime da [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzando stored procedure.

## <a name="prerequisites"></a>Prerequisiti

+ [Servizi SQL Server 2017 Machine Learning con Python](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [Autorizzazioni](../security/user-permission.md)

+ [Database di esempio dei Taxi di NYC](demo-data-nyctaxi-in-sql.md)

Tutte le attività possono essere eseguite usando [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Questa esercitazione presuppone la conoscenza delle operazioni di base dei database, ad esempio la creazione di tabelle e database, l'importazione di dati e la scrittura di query SQL. Presuppone che una conoscenza di Python. Di conseguenza, viene fornito tutto il codice Python. 

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esplorare e visualizzare i dati usando Python](sqldev-py3-explore-and-visualize-the-data.md)
