---
title: Uso di repository Test (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 04e58ec9c40f62932c4a711c1e96c0bd4e8162e2
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51666170"
---
# <a name="using-test-repositories-oracletosql"></a>Uso di repository test (OracleToSQL)
Gli archivi di Repository Test SSMA SSMA Tester test case e risultati dei test per un uso successivo. I dati del Repository vengono salvati nelle tabelle di SQL Server **TestCaseRepository** e **RunTestCaseResultRepository** nello schema **ssma_oracle_utilities** del **ssmatesterdb** database.  
  
I pulsanti seguenti sono disponibili nella finestra di dialogo del Repository del Test case:  
  
-   Scegliere il **Aggiorna** pulsante per aggiornare l'elenco di Test case o i risultati dei Test.  
  
-   Scegliere il **chiudere** per chiudere la finestra di dialogo del Repository del Test case.  
  
## <a name="test-cases-repository"></a>Repository di test case  
È possibile visualizzare il Repository di Test case facendo **Test case...** dal **Tester** menu. SSMA consente quindi di visualizzare il **Repository del Test case** finestra di dialogo con un elenco dei case di test salvati sulle **Test case** pagina.  
  
Nella griglia vengono visualizzate le informazioni seguenti su ogni test case:  
  
-   Nome: Nome del test case.  
  
-   Create: Il test case data di creazione.  
  
-   Modificato: Il test case data dell'ultima modifica.  
  
-   Descrizione: Il test case descrizioni.  
  
I pulsanti seguenti sono disponibili nella pagina di Test case:  
  
-   Scegliere il **Add** pulsante per eseguire la procedura guidata di Test Case e creare un nuovo test.  
  
-   Scegliere il **rimuovere** pulsante per eliminare il test selezionato dal repository. Quando un Test Case viene eliminato, vengono eliminati anche tutti i risultati dei Test correlati.  
  
-   Scegliere il **modifica** pulsante per eseguire la procedura guidata di Test Case e modificare il test selezionato.  
  
-   Fare clic sui **eseguiti** pulsante per aprire il [che esegue Test case (OracleToSQL)](https://msdn.microsoft.com/fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02) finestra di dialogo ed eseguire il test selezionato.  
  
## <a name="test-results-repository"></a>Repository dei risultati del test  
È possibile visualizzare il Repository dei risultati del Test nella **i risultati del Test** pagina della **Repository del Test case** finestra. Aprirlo facendo **i risultati dei Test...** dal **Tester** menu.  
  
È possibile usare due filtri sul **i risultati dei Test** pagina:  
  
-   Il filtro del nome del Test Case: consente di scegliere i risultati dei test dal nome del test case. Questo filtro **tutti i Test case** valore consente di visualizzare i risultati dei test per tutti i test case.  
  
-   Il filtro data di esecuzione di Test Case: risultati dei test di filtri per la data di salvataggio. Questo filtro **periodo tutti** valore consente di visualizzare i risultati dei test per una data di salvataggio.  
  
Le informazioni seguenti sui risultati dei test viene visualizzate nella griglia.  
  
-   Nome: nome di Test case.  
  
-   Salvato: Test Data del caso di salvataggio.  
  
-   Risultati: Una breve descrizione dell'esecuzione del test (descrizione comando della cella, questo visualizza un riepilogo completo dell'esecuzione del test).  
  
I pulsanti seguenti sono disponibili nella pagina dei risultati dei Test:  
  
-   Fare clic sui **View** per aprire [visualizzazione di report di Test Case &#40;OracleToSQL&#41; ](../../ssma/oracle/viewing-test-case-reports-oracletosql.md) del risultato del Test Case corrente.  
  
-   Scegliere il **eliminare** pulsante per eliminare il risultato del Test selezionato  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di Test case &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Test di oggetti di Database migrati &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
