---
title: Tabella di gestione temporanea dei membri foglia
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members staging table [Master Data Services]
- database [Master Data Services], members staging table
ms.assetid: a8c953da-ec20-47dc-8656-ed5f0dfed89b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 626452bb0247b355cff7e8f1e9584e2fdc0c32c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729059"
---
# <a name="leaf-member-staging-table-master-data-services"></a>Tabella di gestione temporanea dei membri foglia (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Utilizzare la tabella di gestione temporanea dei membri foglia (stg.name_Leaf) nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] per creare, aggiornare, disattivare ed eliminare i membri foglia. Inoltre, è possibile utilizzarla per aggiornare i valori degli attributi per i membri foglia.  
  
##  <a name="TableColumns"></a>Colonne della tabella  
 Nella seguente tabella viene illustrato il motivo per cui viene utilizzato ogni campo della tabella di staging Foglia.  
  
|Nome colonna|Descrizione|Valori|  
|-----------------|-----------------|------------|  
|**ID**|Un identificatore assegnato automaticamente.|Non immettere un valore in questo campo. Se il batch non è stato elaborato, questo campo è vuoto.|  
|**ImportType**<br /><br /> Obbligatoria|Determina l'azione da effettuare quando i dati in gestione temporanea corrispondono a dati già esistenti nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|**0**: crea nuovi membri. Sostituire i dati MDS esistenti con i dati in gestione temporanea, ma solo se tali dati non sono NULL. I valori NULL vengono ignorati. Per impostare un valore dell'attributo della stringa su NULL, scegliere **~NULL~**. Per impostare un valore dell'attributo del numero su NULL, scegliere **-98765432101234567890**. Per impostare un valore dell'attributo datetime su NULL, scegliere **5555-11-22T12:34:56**.<br /><br /> **1**: crea solo i nuovi membri. Qualsiasi aggiornamento ai dati MDS esistenti avrà esito negativo.<br /><br /> **2**: creare nuovi membri. Sostituire i dati MDS esistenti con i dati in gestione temporanea. Se si importano valori NULL, i valori MDS esistenti verranno sovrascritti.<br /><br /> **3**: disattiva il membro, in base al valore del codice. Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono gestiti, ma non sono più disponibili nell'interfaccia utente. Se il membro viene utilizzato come valore di attributo basato su dominio di un altro membro, la disattivazione ha esito negativo. Vedere **ImportType5** per un'alternativa.<br /><br /> **4**: Elimina definitivamente il membro, in base al valore del codice. Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono eliminati in modo definitivo. Se il membro viene utilizzato come valore di attributo basato su dominio di un altro membro, l'eliminazione ha esito negativo. Vedere **ImportType6** per un'alternativa.<br /><br /> **5**: disattiva il membro, in base al valore del **codice** . Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono gestiti, ma non sono più disponibili nell'interfaccia utente. Se il membro viene utilizzato come valore di attributo basato su dominio di altri membri, i valori correlati verranno impostati su NULL. ImportType 5 è solo per i membri foglia.<br /><br /> **6**: Elimina definitivamente il membro, in base al valore del **codice** . Tutti gli attributi, le appartenenze a gerarchie e raccolte e le transazioni vengono eliminati in modo definitivo. Se il membro viene utilizzato come valore di attributo basato su dominio di altri membri, i valori correlati verranno impostati su NULL. ImportType 6 è solo per i membri foglia.|  
|**ImportStatus_ID**<br /><br /> Obbligatoria|Lo stato del processo di importazione.|**0**, specificato per indicare che il record è pronto per la gestione temporanea.<br /><br /> **1**, assegnato automaticamente e indica che il processo di gestione temporanea del record ha avuto esito positivo.<br /><br /> **2**, assegnato automaticamente e indica che il processo di gestione temporanea del record non è riuscito.|  
|**Batch_ID**<br /><br /> Richiesto solo dal servizio Web|Un identificatore assegnato automaticamente che raggruppa i record per la gestione temporanea. A tutti i membri nel batch viene assegnato questo identificatore, visualizzato nella colonna [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ID **dell'interfaccia utente di** .|Se il batch non è stato elaborato, questo campo è vuoto.|  
|**BatchTag**<br /><br /> Richiesto, salvo che dal servizio Web|Un nome univoco per il batch, composto da un massimo di 50 caratteri.||  
|**ErrorCode**|Visualizza un codice di errore. Per tutti i record con **ImportStatus_ID** di **2**, vedere [Errori del processo di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).||  
|**Codice**<br /><br /> Richiesto, tranne quando i codici vengono generati automaticamente per **ImportType1** o **2**. Per altre informazioni, vedere [Creazione di codice automatica &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)|Un codice univoco per il membro.||  
|**Nome**<br /><br /> Facoltativo|Nome per il membro.||  
|**NewCode**|Utilizzare solo se si sta modificando il codice membro.||  
|\<Nome attributo>|Esiste una colonna per ogni attributo dell'entità. Utilizzarlo con **ImportType** uguale a **0** o a **2**. Per gli attributi in formato libero specificare il nuovo testo o valore stringa per l'attributo. Per gli attributi basati su dominio specificare il codice del membro che sarà utilizzato come attributo. Per gli attributi di collegamento, l'URL deve iniziare con **https://**.<br /><br /> Nota: non è possibile usare la gestione temporanea per gli attributi di file.||  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica: importazione di dati da tabelle &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Visualizzare gli errori che si verificano durante la gestione temporanea &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [Errori del processo di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
  
