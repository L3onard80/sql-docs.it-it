---
title: Utilizzo di progettazione query e Progettazione viste con dati internazionali (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], international data
- queries [SQL Server], international data
- languages [SQL Server], Query and View Designer
- international considerations [SQL Server], Query and View Designer
- Criteria pane
- View Designer, international data
- Query Designer [SQL Server], international data
- localized information in Query and View Designer [SQL Server]
- global considerations [SQL Server], Query and View Designer
- SQL pane [Visual Database Tools]
- multiple language support [SQL Server], Query and View Designer
ms.assetid: 4b51c56f-f902-4e72-b919-e36127369b63
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 673ad13ff5688fb17eaa4b975644256f072a3aef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63204624"
---
# <a name="use-the-query-and-view-designer-with-international-data-visual-database-tools"></a>Utilizzazione di Progettazione query e Progettazione viste con dati internazionali (Visual Database Tools)
  È possibile utilizzare [Progettazione query e Progettazione viste](visual-database-tools.md) con dati in qualsiasi lingua e in qualsiasi versione del sistema operativo Windows. Le seguenti indicazioni evidenziano le differenze esistenti e forniscono informazioni sulla gestione di dati in applicazioni internazionali.  
  
## <a name="localized-information-in-the-criteria-and-sql-panes"></a>Informazioni localizzate nei riquadri Criteri e SQL  
 Se si utilizza il riquadro Criteri per creare una query, è possibile immettere le informazioni nel formato corrispondente alle impostazioni internazionali di Windows configurate nel computer. Se ad esempio si stanno cercando dei dati, è possibile immettere i dati nelle colonne dei criteri utilizzando il formato desiderato, con le seguenti eccezioni:  
  
-   I formati di dati long non sono supportati.  
  
-   I simboli di valuta non dovrebbero essere immessi nel riquadro Criteri.  
  
-   I simboli di valuta non verranno visualizzati nel riquadro Risultati.  
  
    > [!NOTE]  
    >  Nel riquadro Risultati è possibile immettere il simbolo di valuta che corrisponde alle impostazioni internazionali di Windows del computer in uso, ma verrà rimosso e non sarà visualizzato.  
  
-   L'operatore meno unario viene sempre visualizzato a sinistra del numero (ad esempio, -1) indipendentemente dalle impostazioni internazionali.  
  
 Al contrario, i dati e le parole chiave nel riquadro SQL devono sempre essere in formato ANSI (Stati Uniti). Quando, ad esempio, in Progettazione query e Progettazione viste viene compilata una query, viene inserito il formato ANSI di tutte le parole chiave SQL quali SELECT e FROM. Se si aggiungono elementi all'istruzione nel riquadro SQL, assicurarsi di utilizzare il formato ANSI standard per gli elementi.  
  
 Quando si immettono dati utilizzando un formato locale specifico nel riquadro Criteri, in Progettazione query e Progettazione viste tali dati vengono automaticamente convertiti in formato ANSI nel riquadro SQL. Se ad esempio le impostazioni internazionali sono configurate su Tedesco (standard), è possibile immettere i dati nel riquadro Criteri in un formato quale "31.12.96". La data tuttavia verrà visualizzata nel riquadro SQL con il formato data e ora ANSI, ovvero come `{ ts '1996-12-31 00:00:00' }.` Se si immettono dati direttamente nel riquadro SQL, è necessario usare il formato ANSI.  
  
## <a name="sort-order"></a>Ordinamento  
 Il criterio di ordinamento dei dati nella query è determinato dal database. Le opzioni impostate nella finestra di dialogo Impostazioni internazionali di Windows non influiscono sui criteri di ordinamento delle query. In ciascuna query, tuttavia, è possibile fare in modo che le righe vengano restituite in un particolare ordine.  
  
## <a name="using-double-byte-characters"></a>Utilizzo di caratteri a byte doppio  
 È possibile utilizzare caratteri DBCS per valori letterali o nomi di oggetti di database quali nomi di tabelle e visualizzazioni o alias. È inoltre possibile utilizzare caratteri DBCS per i nomi dei parametri e i caratteri dei marcatori dei parametri. Non è invece possibile utilizzare caratteri DBCS in elementi del linguaggio SQL quali i nomi delle funzioni o le parole chiave SQL.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
