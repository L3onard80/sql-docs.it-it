---
title: Eliminare un attributo
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], deleting
- deleting attributes [Master Data Services]
ms.assetid: ec3e66f7-0e35-43d7-a80d-64899948ebfe
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2d48e8c51f8151f8626e971f928a245ba6776c3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728336"
---
# <a name="delete-an-attribute-master-data-services"></a>Eliminare un attributo (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile eliminare un attributo quando si vuole eliminarlo in modo permanente insieme a tutti i valori associati.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-an-attribute"></a>Per eliminare un attributo  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modello** selezionare un modello dalla griglia e quindi fare clic su **entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga dell'entità per la quale si vuole creare un attributo.  
  
4.  Fare clic su **Attributi**.  
  
5.  Nella pagina **Gestisci attributi** eseguire una delle operazioni seguenti.  
  
    -   Se l'attributo è per i membri foglia, selezionare **Foglia** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per i membri consolidati, selezionare **Consolidato** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per le raccolte, selezionare **Raccolta** nella casella di riepilogo **Tipo di membro** .  
  
6.  Selezionare la riga per l'attributo che si vuole eliminare.  
  
    > [!NOTE]  
    >  Gli attributi Nome e Codice non possono essere eliminati.  
  
7.  Scegliere **Elimina**.  
  
8.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Attributi basati su dominio &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)   
 [Creare un attributo di testo &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
