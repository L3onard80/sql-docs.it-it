---
title: Attributi (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- free-form attributes [Master Data Services]
- attributes [Master Data Services], about attributes
- attributes [Master Data Services], file attributes
- file attributes [Master Data Services]
- attributes [Master Data Services], free-form attributes
- attributes [Master Data Services]
ms.assetid: 95ecb75f-c559-41c3-933c-40ae60a4c2fd
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 88f1f0909e667db38c3b9b5d13bf11a2262b405b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480152"
---
# <a name="attributes-master-data-services"></a>Attributi (Master Data Services)
  Gli attributi sono oggetti contenuti in entità [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . I valori dell'attributo descrivono i membri dell'entità. Un attributo può essere utilizzato per descrivere un membro foglia, un membro consolidato o una raccolta.  
  
## <a name="how-attributes-relate-to-other-model-objects"></a>Correlazione tra attributi e altri oggetti modello  
 Un attributo può essere considerato come una colonna in una tabella entità. Un valore di attributo è il valore utilizzato per descrivere un membro specifico.  
  
 ![Entità Master Data Services rappresentata come tabella](../../2014/master-data-services/media/mds-conc-entity-table.gif "Entità Master Data Services rappresentata come tabella")  
  
 Quando si crea un'entità che contiene molti attributi, è possibile organizzare gli attributi in gruppi di attributi. Per altre informazioni, vedere [Gruppi di attributi &#40;Master Data Services&#41;](attribute-groups-master-data-services.md).  
  
## <a name="required-attributes"></a>Attributi obbligatori  
 Quando si crea un'entità, gli attributi Name e Code vengono creati automaticamente. L'attributo Code richiede un valore che deve essere univoco all'interno dell'entità. Gli attributi Name e Code non possono essere rimossi.  
  
## <a name="attribute-types"></a>Tipi di attributo  
 Sono disponibili tre tipi di attributi:  
  
-   Attributi in formato libero che consentono l'immissione in formato libero di testo, numeri, date o collegamenti.  
  
-   Attributi basati su dominio, che vengono popolati dalle entità. Per altre informazioni, vedere [Attributi basati su dominio &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md).  
  
-   Attributi di file che vengono utilizzati per archiviare file, documenti o immagini. Gli attributi di file hanno lo scopo di favorire la coerenza dei dati richiedendo che i file abbiano un'estensione specifica. Non è possibile garantire che gli attributi di file impediscano ad un utente malintenzionato di caricare un file di tipo diverso.  
  
### <a name="numeric-free-form-attributes"></a>Attributi numerici in formato libero  
 Per i valori di attributi numerici in formato libero è necessaria una gestione particolare poiché tali valori sono limitati al tipo di valore **SqlDouble** .  
  
 Per impostazione predefinita, un valore **SqlDouble** contiene 15 cifre decimali di precisione, anche se internamente viene gestito un massimo di 17 cifre. La precisione di un numero a virgola mobile ha diverse conseguenze:  
  
-   Due numeri a virgola mobile apparentemente uguali per una particolare precisione potrebbero non risultare uguali, in quanto le relative cifre meno significative sono diverse.  
  
-   Un'operazione matematica o di confronto che utilizza un numero a virgola mobile potrebbe non produrre lo stesso risultato se viene utilizzato un numero decimale, perché il numero a virgola mobile potrebbe non avere un'esatta approssimazione al numero decimale.  
  
-   È possibile che un valore non esegua un *round trip* se è interessato un numero a virgola mobile. Si dice che un valore esegue un roundtrip se un'operazione converte un numero a virgola mobile originale in un altro formato, un'operazione inversa trasforma di nuovo il formato convertito in un numero a virgola mobile e il numero a virgola mobile finale è uguale al numero a virgola mobile originale. Il round trip potrebbe non riuscire perché una o più cifre meno significative vengono perse o modificate in una conversione.  
  
## <a name="attribute-examples"></a>Esempi di attributo  
 Nell'esempio seguente l'entità dispone degli attributi Name, Code, Subcategory, StandardCost, ListPrice e FilePhoto. Tali attributi descrivono i membri. Ogni membro viene rappresentato da una singola riga di valori di attributo.  
  
 ![Tabella dell'entità relativa al prodotto biciclette](../../2014/master-data-services/media/mds-conc-entity-table-w-data.gif "Tabella dell'entità relativa al prodotto biciclette")  
  
 Nell'esempio seguente l'entità Product include:  
  
-   Gli attributi in formato libero Name, Code, StandardCost e ListPrice.  
  
-   L'attributo basato su dominio Subcategory.  
  
-   L'attributo di file FilePhoto.  
  
 Subcategory è un'entità utilizzata come attributo basato su dominio di Product. Category è un'entità utilizzata come attributo basato su dominio di Subcategory. Come l'entità Product, le entità Category e Subcategory includono ciascuna gli attributi predefiniti Name e Code.  
  
 ![Struttura ad albero dell'entità relativa al prodotto](../../2014/master-data-services/media/mds-conc-entity-ui.gif "Struttura ad albero dell'entità relativa al prodotto")  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare un nuovo attributo di testo in formato libero.|[Creare un attributo di testo &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)|  
|Creare un nuovo attributo numerico in formato libero.|[Creare un attributo numerico &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)|  
|Creare un nuovo attributo di collegamento in formato libero.|[Creare un attributo di collegamento &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-link-attribute-master-data-services.md)|  
|Creare un nuovo attributo di file.|[Creare un attributo di file &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)|  
|Creare un nuovo attributo basato su dominio.|[Creare un attributo basato su dominio &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Modificare il nome di un attributo esistente.|[Modificare il nome di un attributo &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)|  
|Aggiungere attributi ad un gruppo rilevamento modifiche|[Aggiungere attributi a un gruppo di Rilevamento modifiche &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Eliminare un attributo esistente.|[Eliminare un attributo &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-master-data-services.md)|  
|Modificare l'ordine degli attributi.|[Modificare l'ordine degli attributi](../../2014/master-data-services/change-the-order-of-attributes.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Attributi basati su dominio &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [Gruppi di attributi &#40;Master Data Services&#41;](attribute-groups-master-data-services.md)  
  
-   [Membri &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)  
  
-   [Autorizzazioni foglia &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md)  
  
-   [Autorizzazioni consolidate &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
