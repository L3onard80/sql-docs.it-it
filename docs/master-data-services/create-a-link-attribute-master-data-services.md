---
title: Creare un attributo di collegamento
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating link attributes
- creating link attributes [Master Data Services]
ms.assetid: e6658e9c-5b08-4b8d-b556-17ec2dd041d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 929e363228b30889e163519786d802dd4caee049
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728493"
---
# <a name="create-a-link-attribute-master-data-services"></a>Creare un attributo di collegamento (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] creare un attributo per il collegamento quando si deve immettere un collegamento ipertestuale come valore di attributo, ad esempio `https://www.contoso.com`.  
  
> [!NOTE]  
>  Quando gli utenti immettono un valore per un attributo di collegamento, la stringa deve iniziare con **https://**. In caso contrario viene visualizzato un errore.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario che sia presente un'entità perché ne venga creato l'attributo. Per altre informazioni, vedere [creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## <a name="attribute-information"></a>Informazioni sugli attributi  
 Per ogni indice creato, viene aggiunta alla griglia una riga con sette colonne. La tabella seguente descrive le colonne.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|Stato|Stato dell'attributo.<br /><br /> Quando si fa clic su Salva, viene visualizzata l' ![icona di aggiornamento dell'immagine di stato](../master-data-services/media/mds-statusicon-updating.png "Icona per lo stato di aggiornamento") , che indica che l'attributo è in fase di aggiornamento.<br /><br /> Se si verificano errori durante la creazione o la modifica di un attributo, viene visualizzata l'immagine ![icona di stato errore](../master-data-services/media/mds-statusicon-error.png "Icona per lo stato di errore") .<br /><br /> In caso contrario, lo stato è OK e viene visualizzata l'immagine ![icona di stato OK](../master-data-services/media/mds-statusicon-ok.png "Icona per lo stato OK") .|  
|Nome|Nome dell'attributo.|  
|Nome visualizzato|Nome visualizzato dell'attributo.|  
|Descrizione|Descrizione dell'attributo.|  
|Larghezza in pixel visualizzazione|Larghezza dell'attributo.|  
|Tipo e proprietà|Informazioni sul tipo e sul tipo di dati dell'attributo.|  
|Abilita rilevamento modifiche|Specifica se l'attributo è abilitato per il rilevamento delle modifiche e visualizza tra parentesi il numero del gruppo.|  
  
 Quando si fa clic su un attributo vengono visualizzate le informazioni seguenti.  
  
-   **Creato da**: nome dell'utente che ha creato l'attributo.  
  
-   Il **: data e ora di creazione**dell'attributo.  
  
-   **Aggiornato da**: nome dell'ultimo utente che ha aggiornato l'attributo.  
  
-   **Il: data**e ora dell'ultimo aggiornamento dell'attributo.  
  
### <a name="to-create-a-link-attribute"></a>Per creare un attributo di collegamento  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modello** selezionare un modello dalla griglia e quindi fare clic su **entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga dell'entità per la quale si vuole creare un attributo.  
  
4.  Fare clic su **Attributi**.  
  
5.  Nella pagina **Gestisci attributi** eseguire una di queste operazioni, quindi fare clic su **Aggiungi**.  
  
    -   Se l'attributo è per i membri foglia, selezionare **Foglia** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per i membri consolidati, selezionare **Consolidato** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per le raccolte, selezionare **Raccolta** nella casella di riepilogo **Tipo di membro** .  
  
6.  Nella casella **Nome** digitare un nome per l'attributo. Per un elenco di parole che non vanno usate come nomi di attributo, vedere [Parole riservate &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
7.  Facoltativamente, digitare un nome visualizzato e specificare una descrizione per l'attributo nella casella **Descrizione** .  
  
8.  Nella casella **Larghezza in pixel visualizzazione** digitare la larghezza della colonna attributo da visualizzare nella griglia **Esplora** .  
  
9. Nell'elenco **Tipo di attributo** selezionare **Formato libero**.  
  
10. Nell'elenco **Tipo di dati** selezionare **Collegamento**.  
  
11. Nella casella **Lunghezza** digitare il numero massimo di caratteri consentiti.  
  
12. Facoltativamente, selezionare **Abilita rilevamento modifiche** per tenere traccia delle modifiche a gruppi di attributi. Per altre informazioni, vedere [Aggiungere attributi ad un gruppo rilevamento modifiche &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Fare clic su **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Modificare il nome di un attributo e il tipo di dati &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Creare un attributo di file &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
