---
title: Partizioni (finestra di dialogo Ripristina Database) (Analysis Services - dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.restoredbdialog.partitions.f1
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ef5ec59980d267a8ead0f69aedb12c6eca5508dc
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51639868"
---
# <a name="partitions-restore-database-dialog-box-analysis-services---multidimensional-data"></a>Partizioni (finestra di dialogo Ripristina Database) (Analysis Services - Dati multidimensionali)
  Usare la pagina **Partizioni** della finestra di dialogo **Ripristina database** di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per specificare il percorso di ripristino delle partizioni locali, nel caso in cui debbano essere ripristinate partizioni remote e i file di backup remoto da usare per eseguire questa operazione.  
  
> [!IMPORTANT]  
>  Per ogni file di backup, l'utente che esegue il comando di ripristino deve disporre delle autorizzazioni per leggere dal percorso di backup specificato per ogni file. Per ripristinare un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] non installato nel server, l'utente deve inoltre essere un membro del ruolo del server per l'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] specifica. Per sovrascrivere un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , l'utente deve avere uno dei ruoli seguenti: deve essere un membro del ruolo del server per l'istanza [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] o un membro di un ruolo del database con autorizzazioni Controllo completo (amministratore) per il database da ripristinare.  
  
> [!NOTE]  
>  Dopo avere ripristinato un database esistente, l'utente che ha effettuato l'operazione potrebbe perdere l'accesso al database ripristinato. Può verificarsi questa perdita di accesso se, al momento dell’esecuzione del backup, l'utente non era un membro del ruolo del server o non era un membro del ruolo del database con autorizzazioni Controllo completo (amministratore).  
  
 **Per visualizzare la pagina partizioni nella finestra di dialogo Ripristina Database**  
  
-   In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]fare clic con il pulsante destro del mouse sulla cartella **Database** di un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] o su un database in **Esplora oggetti**, scegliere **Ripristina**e quindi, in **Selezione pagina**, fare clic su **Partizioni**.  
  
## <a name="options"></a>Opzioni  
 **Script**  
 Crea uno script di ripristino basato sulle opzioni selezionate nella finestra di dialogo. Lo script di ripristino è scritto in ASSL ( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Scripting Language).  
  
 Facendo clic sull'icona **Script** lo script di ripristino viene inviato in una nuova finestra Query, per impostazione predefinita.  
  
 Facendo clic sulla freccia **Script** viene visualizzato un menu che consente di scegliere dove inviare lo script di ripristino:  
  
-   A una nuova finestra Query (impostazione predefinita).  
  
-   A un file.  
  
-   Negli Appunti.  
  
-   A un processo.  
  
 **Ripristina nei percorsi originali**  
 Selezionare questa opzione per ripristinare le partizioni locali incluse nel file di backup nei rispettivi percorsi originali.  
  
 **Seleziona percorsi diversi**  
 Selezionare questa opzione per specificare percorsi diversi in cui ripristinare le partizioni locali.  
  
> [!NOTE]  
>  È possibile cambiare la cartella di ripristino di una partizione locale solo se è stato specificato un percorso diverso da quello predefinito per tale partizione nel cubo.  
  
 La griglia seguente, attivata se l'opzione è selezionata, viene utilizzata per specificare una cartella di ripristino per ogni partizione locale:  
  
|colonna|Description|  
|------------|-----------------|  
|**Cube**|Visualizza il nome del cubo contenente la partizione locale.|  
|**Gruppo di misure**|Visualizza il nome del gruppo di misure contenente la partizione locale.|  
|**Partizione**|Visualizza il nome della partizione locale.|  
|**Dimensioni (MB)**|Visualizza le dimensioni (in megabyte) della partizione locale.|  
|**Cartella originale**|Visualizza il nome della cartella originale in cui era archiviata la partizione locale.|  
|**Cartella ripristino**|Consente di digitare il nome della cartella di ripristino per la partizione locale. È inoltre possibile fare clic sul pulsante con i puntini di sospensione (**...**) per visualizzare la finestra di dialogo **Cerca cartella remota** e selezionare il percorso della cartella da usare. Per altre informazioni sulla finestra di dialogo **Cerca cartella remota**, vedere [Finestra di dialogo Cerca cartella remota &#40;Analysis Services - Dati multidimensionali&#41;](browse-for-remote-folder-dialog-box-analysis-services-multidimensional-data.md).|  
  
 **Ripristinare le partizioni remote**  
 Selezionare questa opzione per ripristinare partizioni remote archiviate in file di backup remoti.  
  
> [!NOTE]  
>  Questa opzione è attivata solo se il file di backup contiene riferimenti alle partizioni remote.  
  
 La griglia seguente, attivata se l'opzione è selezionata, viene utilizzata per specificare una cartella di ripristino per ogni partizione locale:  
  
|colonna|Description|  
|------------|-----------------|  
|**Server**|Visualizza il nome dell'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] che gestisce la partizione remota.|  
|**Data Source**|Visualizza il nome dell'origine dei dati nel file di backup che rappresenta il database contenente la partizione remota.|  
|**File di backup**|Consente di digitare il nome e il percorso completo del file di backup remoto da usare. È inoltre possibile fare clic sul pulsante con i puntini di sospensione (**...**) per visualizzare la finestra di dialogo **Individua file di database** e selezionare il percorso e il nome del file di backup remoto da usare. Per altre informazioni sulla finestra di dialogo **Trova file di database**, vedere [Finestra di dialogo Individua file di database &#40;Analysis Services - Dati multidimensionali&#41;](locate-database-files-dialog-box-analysis-services-multidimensional-data.md).|  
|**...**|Fare clic su questo pulsante per visualizzare la finestra di dialogo **Partizioni remote - Impostazioni avanzate** e modificare le opzioni avanzate, ad esempio la stringa di connessione all'origine dati, per il ripristino della partizione remota. Per altre informazioni sulla finestra di dialogo **Partizioni remote - Impostazioni avanzate**, vedere [Finestra di dialogo Partizioni remote – Impostazioni avanzate &#40;Analysis Services - Dati multidimensionali&#41;](remote-partitions-advanced-settings-dialog-analysis-services-multidimensional-data.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Ripristina Database &#40;Analysis Services - Dati multidimensionali&#41;](restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Generale &#40;dialogo Ripristina Database&#41; &#40;Analysis Services - dati multidimensionali&#41;](general-restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Backup e ripristino di database di Analysis Services](multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
  
