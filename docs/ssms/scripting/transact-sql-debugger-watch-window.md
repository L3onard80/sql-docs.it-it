---
title: Finestra Espressioni di controllo | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- Watch Window [Transact-SQL]
ms.assetid: 23f3baa4-14c2-4262-92f7-3f43fcfa0436
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a80ab78dc6a061abd5b975cc1f4afb0836f95b3d
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643260"
---
# <a name="transact-sql-debugger---watch-window"></a>Debugger Transact-SQL - Finestra Espressioni di controllo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Nella finestra **Espressione di controllo** vengono visualizzate informazioni sulle espressioni selezionate. Sono disponibili fino a quattro finestre di visualizzazione delle espressioni di controllo: **Espressione di controllo 1**, **Espressione di controllo 2, Espressione di controllo 3**ed **Espressione di controllo 4**. Le espressioni vengono valutate nell'ambito del frame dello stack di chiamate corrente selezionato nella finestra **Stack di chiamate** . Per controllare variabili ed espressioni, è necessario utilizzare la modalità di debug.  
  
## <a name="task-list"></a>Elenco attività  
 **Per accedere alle finestre Espressione di controllo**  
  
-   Scegliere **Finestre** dal menu **Debug**, fare clic su **Espressione di controllo**, quindi su **Espressione di controllo 1**, **Espressione di controllo 2, Espressione di controllo 3**o **Espressione di controllo 4**.  
  
 **Per modificare il valore di un'espressione**  
  
-   Fare clic con il pulsante destro del mouse sull'espressione e scegliere **Modifica valore**.  
  
## <a name="columns"></a>Colonne  
 **Nome**  
 Espressioni elencate dal debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] . Sono supportate le espressioni seguenti:  
  
-   Variabili.  
  
-   Parametri.  
  
-   Funzioni di sistema il cui nome inizia con @@.  
  
-   Espressioni compilate applicando operatori a uno o più parametri, variabili o funzioni di sistema, ad esempio @@IntegerCounter + 1 o FirstName + LastName.  
  
-   Istruzioni Transact-SQL tramite cui viene restituito un solo valore, ad esempio SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.  
  
 **Value**  
 Consente di visualizzare il valore restituito dopo che il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] valuta l'espressione specificata in **Nome**.  
  
 Se la lunghezza di un'espressione è maggiore della larghezza della colonna **Valore** , il valore completo verrà visualizzato in una descrizione comandi quando si sposta il puntatore sulla cella **Valore** per l'espressione.  
  
 Un'icona di lente di ingrandimento in una cella **Valore** indica che è disponibile il visualizzatore del debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] . Nell'elenco è possibile specificare **Visualizzatore testo**, **Visualizzatore XML**o **Visualizzatore HTML**. Per avviare un visualizzatore del debugger, fare clic sull'icona di lente di ingrandimento. Nel debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] verrà visualizzata una finestra di dialogo contenente dati in un formato appropriato per il tipo di dati.  
  
 **Tipo**  
 Consente di visualizzare il tipo di dati dell'espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Informazioni del debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [finestra Variabili locali](../../relational-databases/scripting/transact-sql-debugger-locals-window.md)   
 [Finestra Stack di chiamate](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Finestra di dialogo Controllo immediato](../../relational-databases/scripting/transact-sql-debugger-quickwatch-dialog-box.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
