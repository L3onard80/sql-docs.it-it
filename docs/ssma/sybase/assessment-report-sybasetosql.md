---
title: Report di valutazione (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: af24f2c4-5e86-4135-a4f3-a24faaeeefe7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c6d83e81253430f243fcaed55b66f6d0de6299ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083498"
---
# <a name="assessment-report-sybasetosql"></a>Report di valutazione (SybaseToSQL)
La finestra report di valutazione Mostra i risultati della conversione degli oggetti di database [!INCLUDE[tsql](../../includes/tsql-md.md)] nella sintassi e consente inoltre di stimare la complessità e il costo dei progetti di migrazione.  
  
Per accedere al report di valutazione, selezionare gli oggetti da convertire in Esplora metadati di origine, fare clic con il pulsante destro del mouse su **database**e quindi scegliere **Crea report**.  
  
## <a name="options"></a>Opzioni  
**Statistiche di conversione**  
Mostra le statistiche di conversione per tipo di istruzione. Questo riquadro è visibile solo quando si seleziona un oggetto gruppo, ad esempio uno schema, o un oggetto senza codice nel riquadro sinistro.  
  
**Oggetti per categoria**  
Mostra le statistiche di conversione per tipo di oggetto. Questo riquadro è visibile solo quando si seleziona un oggetto gruppo, ad esempio uno schema, o un oggetto senza codice nel riquadro sinistro.  
  
**Statistiche**  
Mostra le statistiche di conversione per l'oggetto selezionato. Questo riquadro è visibile solo quando si seleziona un singolo oggetto con codice nel riquadro sinistro. Potrebbe essere necessario espandere **statistiche** per visualizzare questo riquadro.  
  
**Navigazione origine**  
Mostra il codice dell'ambiente del servizio app per l'oggetto selezionato ed evidenzia il codice che [!INCLUDE[tsql](../../includes/tsql-md.md)]non è stato convertito in. Questo riquadro è visibile solo quando si seleziona un singolo oggetto con codice nel riquadro sinistro.  
  
Per impostare o cancellare i segnalibri, fare clic sui numeri di riga. Utilizzare i pulsanti nella parte superiore del riquadro per spostarsi nel codice.  
  
**Navigazione di destinazione**  
Mostra il codice risultante [!INCLUDE[tsql](../../includes/tsql-md.md)] della conversione per l'oggetto selezionato e i messaggi di errore per il codice che non è stato convertito. Questo riquadro è visibile solo quando si seleziona un singolo oggetto con codice nel riquadro sinistro.  
  
Per impostare o cancellare i segnalibri, fare clic sui numeri di riga. Utilizzare i pulsanti nella parte superiore del riquadro per spostarsi nel codice.  
  
**riquadro Messaggi**  
Mostra gli errori, gli avvisi e i messaggi informativi generati durante la creazione del report di valutazione. I messaggi sono raggruppati per numero. Per visualizzare il codice che ha causato l'errore, fare clic su **errore**, **avviso**o **informazioni**, espandere la categoria di messaggi e quindi fare clic su un messaggio.  
  
