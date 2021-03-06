---
title: Finestra di dialogo Controllo immediato
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
f1_keywords:
- vs.debug.quickwatch
helpviewer_keywords:
- QuickWatch Dialog [Transact-SQL]
ms.assetid: d6bbb373-1452-41f2-bdc5-86ae689c3dc0
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9cfd48c59a928481be28d03d970fb399ea10b720
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "75253020"
---
# <a name="transact-sql-debugger---quickwatch-dialog-box"></a>Debugger Transact-SQL - Finestra di dialogo Controllo immediato

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Utilizzare la finestra di dialogo **Controllo immediato** per visualizzare rapidamente il tipo di dati e il valore di un'espressione [!INCLUDE[tsql](../../includes/tsql-md.md)] , ad esempio una variabile o un parametro, quando si esegue il debug di codice [!INCLUDE[tsql](../../includes/tsql-md.md)] . Per controllare più espressioni, è anche possibile aggiungere l'espressione a una finestra **Espressione di controllo** .  

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="task-list"></a>Elenco attività

 **Per accedere alla finestra di dialogo Controllo immediato**  
  
-   Scegliere **Controllo immediato** dal menu **Debug**.  
  
 **Per visualizzare le informazioni relative a un'espressione**  
  
1.  Nella casella di riepilogo **Espressione** digitare o selezionare l'espressione desiderata. Sono supportate le espressioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti:  
  
    -   Variabili.  
  
    -   Parametri.  
  
    -   Funzioni di sistema il cui nome inizia con @@.  
  
    -   Espressioni compilate applicando operatori a uno o più parametri, variabili o funzioni di sistema, ad esempio @@IntegerCounter + 1 o FirstName + LastName.  
  
    -   Istruzioni Transact-SQL tramite cui viene restituito un solo valore, ad esempio SELECT CharacterCol FROM MyTable WHERE PrimaryKey = 1.  
  
2.  Fare clic su **Rivaluta**.  
  
 **Per aggiungere un'espressione di controllo immediato a una finestra Espressione di controllo**  
  
-   Fare clic su **Aggiungi espressione di controllo**.  
  
 **Per modificare il valore di un'espressione di controllo immediato**  
  
-   Fare clic con il pulsante destro del mouse sull'espressione e scegliere **Modifica valore**.  
  
## <a name="options"></a>Opzioni  
 **Elenco di espressioni**  
 Consente di visualizzare l'espressione selezionata. L'elenco a discesa contiene un set di espressioni che è possibile selezionare per visualizzarle. Le espressioni incluse nell'elenco sono quelle disponibili nell'ambito del frame dello stack corrente selezionato nella finestra **Stack di chiamate** . Per visualizzare un'espressione diversa, immettere l'espressione o selezionarla nell'elenco. Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] supporta le espressioni seguenti: variabili, parametri e le funzioni di sistema i cui nomi iniziano con @@.  
  
 **Griglia Valore**  
 Consente di visualizzare le proprietà dell'espressione attualmente controllata.  
  
 **Nome**  
 Espressione [!INCLUDE[tsql](../../includes/tsql-md.md)] controllata.  
  
 **Valore**  
 Consente di visualizzare il valore assegnato all'espressione. Quando l'espressione non è associata ad alcun valore, viene visualizzato uno spazio vuoto.  
  
 Se la lunghezza di un'espressione è maggiore della larghezza della colonna **Valore** , il valore completo verrà visualizzato in una descrizione comandi quando si sposta il puntatore sulla cella **Valore** per l'espressione.  
  
 Un'icona di lente di ingrandimento in una cella **Valore** indica che è disponibile il visualizzatore del debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] . Nell'elenco è possibile specificare **Visualizzatore testo**, **Visualizzatore XML**o **Visualizzatore HTML**. Per avviare un visualizzatore del debugger, fare clic sull'icona di lente di ingrandimento. Tramite il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] viene visualizzata una finestra di dialogo contenente dati in un formato appropriato per il tipo di dati.  
  
 **Tipo**  
 Consente di visualizzare il tipo di dati dell'espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Informazioni del debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [finestra Espressioni di controllo](../../relational-databases/scripting/transact-sql-debugger-watch-window.md)   
 [finestra Variabili locali](../../relational-databases/scripting/transact-sql-debugger-locals-window.md)   
 [Finestra Stack di chiamate](../../relational-databases/scripting/transact-sql-debugger-call-stack-window.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
