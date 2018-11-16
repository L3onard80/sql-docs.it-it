---
title: Interpretazione dei risultati di unit test di SQL Server | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: fde3c95b-2f68-483d-a197-0f7161b72fa3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0576454d646f5e738e153f7937cb717f8b26fc3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51658940"
---
# <a name="interpreting-sql-server-unit-test-results"></a>Interpretazione dei risultati di unit test di SQL Server
Quando si esegue uno unit test di SQL Server, i risultati del test vengono generati automaticamente, salvati su disco e riepilogati nella finestra **Risultati del test**. Non appena si avvia un'esecuzione di test, viene visualizzata la finestra **Risultati test** con lo stato dell'esecuzione di test. Nella visualizzazione sono inclusi i test in esecuzione e quelli completati.  
  
Per visualizzare informazioni dettagliate su un risultato di test, fare doppio clic su nella finestra **Risultati test** per visualizzare la pagina **Visualizza dettagli risultati test**. Per ulteriori informazioni, fare doppio clic su un risultato di test.  
  
Per altre informazioni su come modificare la visualizzazione della finestra **Risultati del test**, vedere [Procedura: Aggiungere o rimuovere colonne nelle finestre dei test (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182508(VS.100).aspx) o [Procedura: Aggiungere o rimuovere colonne nelle finestre dei test (Visual Studio 2012)](https://msdn.microsoft.com/library/ms182508.aspx).  
  
## <a name="storing-test-results"></a>Archiviazione di risultati di test  
I risultati di unit test vengono archiviati automaticamente sul disco rigido in file con estensione trx. Un file trx è un file XML contenente i dettagli di un'esecuzione di test. È possibile caricare i file trx dalle esecuzioni di test precedenti per verificare i risultati di tali esecuzioni di test o per rieseguire i test precedenti. Per altre informazioni, vedere [Procedura: Eseguire nuovamente un test (Visual Studio 2010)](https://msdn.microsoft.com/library/ms182472(VS.100).aspx).  
  
> [!NOTE]  
> Non è possibile eseguire unit test in modalità remota.  
  
Se il team sta usando un progetto team di Visual Studio Team Foundation Server per semplificare la gestione del lavoro, è anche possibile pubblicare i dati di test in un database di SQL Server noto come archivio operativo.  
  
Per altre informazioni su come salvare i risultati di test, riutilizzarli e condividerli con il team, vedere [Procedura: Salvare e aprire risultati dei test in Visual Studio 2010](https://msdn.microsoft.com/library/ms404662(VS.100).aspx) o [Procedura: Salvare e aprire risultati dei test in Visual Studio 2012](https://msdn.microsoft.com/library/ms404662.aspx).  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di unit test di SQL Server](../ssdt/running-sql-server-unit-tests.md)  
  
