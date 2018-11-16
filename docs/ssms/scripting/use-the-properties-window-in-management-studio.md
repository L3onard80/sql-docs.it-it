---
title: Usare la finestra Proprietà in Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 040d2e81b8b45f8f7c6f3003a7522c63dbcef568
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696199"
---
# <a name="use-the-properties-window-in-management-studio"></a>Utilizzo della finestra Proprietà in Management Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Nella finestra Proprietà è indicato lo stato di un elemento in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ad esempio una connessione o un operatore Showplan, e vengono riportate informazioni su oggetti di database come ad esempio tabelle, visualizzazioni e finestre di progettazione.  
  
 È possibile utilizzare la finestra Proprietà per visualizzare le proprietà della connessione corrente. In questa finestra molte proprietà solo di sola lettura ma è possibile modificarle altrove in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. La proprietà Database di una query, ad esempio, è di sola lettura nella finestra Proprietà ma può essere modificata sulla barra degli strumenti.  
  
### <a name="to-view-properties-using-the-properties-window"></a>Per visualizzare le proprietà utilizzando la finestra Proprietà  
  
1.  Se la finestra Proprietà non è visibile, scegliere **Finestra Proprietà** dal menu **Visualizza** oppure premere F4.  
  
2.  Impostare lo stato attivo sull'oggetto che si desidera visualizzare.  
  
3.  Cercare una proprietà specifica nella finestra Proprietà.  
  
### <a name="to-view-connection-properties-of-a-query-window"></a>Per visualizzare le proprietà di connessione di una finestra di query  
  
1.  Se la finestra Proprietà non è visibile, scegliere **Finestra Proprietà** dal menu **Visualizza** oppure premere F4.  
  
2.  Nella finestra Proprietà è possibile vedere tutte le proprietà di connessione.  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a>Per visualizzare le proprietà di un operatore Showplan  
  
1.  Scegliere **Includi piano di esecuzione effettivo** dal menu **Query**.  
  
2.  Nell'editor di query SQL digitare ed eseguire una query.  
  
3.  Se la finestra Proprietà non è visibile, scegliere **Finestra Proprietà** dal menu **Visualizza** oppure premere F4.  
  
4.  Nella scheda **Piano di esecuzione** dell'editor di query SQL fare clic sulle icone degli operatori per visualizzare informazioni sugli operatori nella finestra Proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra Proprietà &#40;Management Studio&#41;](https://msdn.microsoft.com/library/6a9a1389-df8d-4cfc-928b-eccbf884a22d)  
  
  
