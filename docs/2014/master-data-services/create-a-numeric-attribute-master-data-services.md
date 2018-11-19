---
title: Creare un attributo numerico (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating number attributes
- creating number attributes [Master Data Services]
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a3aee9b1bbe939c3790d2849c829a706425aa1b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072631"
---
# <a name="create-a-numeric-attribute-master-data-services"></a>Creare un attributo numerico (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]creare un attributo numerico quando si vuole che gli utenti immettano un numero come valore di attributo.  
  
> [!NOTE]  
>  Gli attributi numerici presentano limitazioni. Per altre informazioni, vedere [Attributes &#40;Master Data Services&#41;](attributes-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
-   È necessario che sia presente un'entità perché ne venga creato l'attributo. Per altre informazioni, vedere [Creare un'entità &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-numeric-attribute"></a>Per creare un attributo numerico  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Vista modelli** scegliere **Gestisci** dalla barra dei menu, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestione entità** selezionare un modello dall'elenco **Modello** .  
  
4.  Selezionare la riga relativa all'entità per la quale si desidera creare un attributo.  
  
5.  Fare clic su **Modifica entità selezionata**.  
  
6.  Nella pagina **Modifica entità** :  
  
    -   Se l'attributo è per membri foglia, nel riquadro **Attributi membro foglia** fare clic su **Aggiungi attributo foglia**.  
  
    -   Se l'attributo è per membri consolidati, nel riquadro **Attributi membro consolidati** fare clic su **Aggiungi attributo consolidato**.  
  
    -   Se l'attributo è per raccolte, nel riquadro **Attributi raccolta** fare clic su **Aggiungi attributo raccolta**.  
  
7.  Nella pagina **Aggiungi attributo** selezionare l'opzione **Formato libero** .  
  
8.  Nella casella **Nome** digitare un nome per l'attributo. Per un elenco di parole che non vanno usate come nomi di attributo, vedere [Parole riservate &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).  
  
9. Nella casella **Larghezza in pixel visualizzazione** digitare la larghezza della colonna attributo da visualizzare nella griglia **Esplora** .  
  
10. Nell'elenco **Tipo di dati** selezionare **Numero**.  
  
11. Nella casella **Decimali** digitare il numero di cifre che è possibile immettere dopo un separatore decimale.  
  
12. Dal **maschera di Input** elencare, selezionare un formato per i numeri negativi.  
  
13. Facoltativamente, selezionare **Abilita rilevamento modifiche** per tenere traccia delle modifiche a gruppi di attributi. Per altre informazioni, vedere [Aggiungere attributi ad un gruppo rilevamento modifiche &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) .  
  
14. Fare clic su **Salva attributo**.  
  
15. Nella pagina **Gestione entità** , fare clic su **Salva entità**.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi &#40;Master Data Services&#41;](attributes-master-data-services.md)   
 [Modificare un nome di attributo &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Creare un attributo di File &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
