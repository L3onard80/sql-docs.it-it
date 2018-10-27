---
title: Le impostazioni di conversione (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f551cf6e-1575-4206-9cca-975b5b43a6b8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4ff1a1a9f5b8ba216a2d14d186f2ade20e5eb3dc
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100112"
---
# <a name="conversion-settings-mysqltosql"></a>Impostazioni di conversione (MySQLToSQL)
Il **'Impostazioni'** scheda consente all'utente di impostare le impostazioni a livello di nodo. La scheda sarà disponibile a livello dei nodi della Metabase seguenti:  
  
-   Nodo del database  
  
-   Categoria di funzioni  
  
-   Nodo della funzione  
  
-   Categoria di tabelle  
  
-   Nodo della tabella  
  
## <a name="specifications"></a>Specifiche:  
Il **impostazioni** scheda ha due impostazioni utente, una visualizzazione dei.:  
  
1.  Conversione (funzione)  
  
2.  Conversione della tabella  
  
Queste impostazioni saranno disponibili in base al tipo di nodo della Metabase. Ad esempio, conversione di funzioni correlate impostazione non sarà disponibile in corrispondenza del nodo di tabella  
  
> [!NOTE]  
> -   Le modifiche apportate dall'utente verranno salvate nell'area di lavoro di progetto come file separato delle preferenze.  
> -   L'estensione del file saranno **ccprefs**.  
  
1.  **Impostazione di conversione (funzione):**  
  
    1.  Questa scheda contiene **'Forzare la conversione di funzione'** opzione. L'opzione può avere uno dei quattro valori seguenti:  
  
        -   Convertire in base alle impostazioni di progetto [ereditate]  
  
        -   Sempre la conversione a una funzione  
  
        -   Sempre la conversione a una routine  
  
        -   Convertire in base alle impostazioni di progetto  
  
    2.  Basato sulle impostazioni, la funzione verrà convertita in una funzione o a una stored procedure.  
  
    3.  Le impostazioni apportate dall'utente vengono salvate nel file di preferenze propagate fa clic sul pulsante **applica** pulsante.  
  
2.  **Impostazione di conversione di tabella:**  
  
    1.  Questa scheda contiene **'La generazione delle colonne ausiliario sopprimere ROWID'** opzione. L'opzione può avere uno dei quattro valori seguenti:  
  
        -   Convertire in base alle impostazioni di progetto [ereditate]  
  
        -   Sì  
  
        -   no  
  
        -   Convertire in base alle impostazioni di progetto  
  
    2.  Se **'Sì'**, questa impostazione impedisce la creazione della creazione di colonne ausiliario ROWID nelle tabelle di destinazione.  
  
    3.  Le impostazioni apportate dall'utente vengono salvate nel file di preferenze propagate fa clic sul pulsante **applica** pulsante.  
  
## <a name="see-also"></a>Vedere anche  
[Impostazioni progetto (conversione) (MySQL a SQL)](http://msdn.microsoft.com/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
