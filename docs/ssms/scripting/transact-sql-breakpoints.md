---
title: Punti di interruzione Transact-SQL
titleSuffix: T-SQL debugger
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 12/04/2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1c31101eb201a55dffd100fb9365f7c29826fb5d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "75243398"
---
# <a name="transact-sql-breakpoints"></a>Punti di interruzione Transact-SQL

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

I punti di interruzione specificano la sospensione dell'esecuzione del debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] in un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] specifica, per consentire le visualizzazione dello stato degli elementi di codice in tale punto.

[!INCLUDE[ssms-old-versions](../../includes/ssms-old-versions.md)]

## <a name="breakpoints"></a>Punti di interruzione

Quando si esegue il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] , è possibile attivare o attivare un punto di interruzione per istruzioni specifiche. Quando viene raggiunta un'istruzione con un punto di interruzione, il debugger sospende l'esecuzione per consentire la visualizzazione di informazioni di debug, ad esempio i valori presenti in variabili e parametri.

È possibile gestire i punti di interruzione singolarmente nella finestra dell'editor o collettivamente tramite la finestra **Punti di interruzione** . È possibile modificare i punti di interruzione per specificare elementi quali condizioni specifiche in presenza delle quali l'esecuzione deve essere sospesa oppure le azioni in caso di esecuzione del punto di interruzione.

## <a name="breakpoint-tasks"></a>Attività correlate ai punti di interruzione  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene decritto come specificare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] in corrispondenza della quale il debugger deve sospendere l'esecuzione.|[Attivare/disattivare un punto di interruzione](../../relational-databases/scripting/toggle-a-breakpoint.md)|  
|Viene descritto come disattivare temporaneamente un punto di interruzione e riattivarlo in un secondo momento. Viene inoltre descritto come eliminare un punto di interruzione.|[Abilitare, disabilitare ed eliminare punti di interruzione](../../relational-databases/scripting/enable-disable-and-delete-breakpoints.md)|  
|Viene descritto come specificare una condizione che definisce se l'interruzione nel punto deve avvenire in base alla valutazione di un'espressione Transact-SQL specificata.|[Impostare una condizione del punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-condition.md)|  
|Viene descritto come specificare un numero di passaggi che determina l'interruzione solo quando l'istruzione contenente il punto di interruzione è stata eseguita un determinato numero di volte.|[Specificare un numero di passaggi](../../relational-databases/scripting/specify-a-hit-count.md)|  
|Viene descritto come specificare un filtro che determina l'interruzione in corrispondenza del punto impostato solo per processi o thread specificati.|[Specificare un filtro per un punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-filter.md)|  
|Viene descritto come specificare un'azione **Quando raggiunto** , ovvero un'operazione personalizzata eseguita quando viene eseguita l'istruzione del punto di interruzione. Ne è un esempio la visualizzazione di un messaggio.|[Specificare un'azione del punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-action.md)|  
|Viene descritto come modificare la posizione di un punto di interruzione.|[Modificare la posizione di un punto di interruzione](../../relational-databases/scripting/edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni del debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)  
  
  
