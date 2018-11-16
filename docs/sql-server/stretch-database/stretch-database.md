---
title: Stretch Database | Microsoft Docs
ms.custom: ''
ms.date: 06/27/2016
ms.prod: sql
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database
ms.assetid: ce6db775-21a5-40bc-95a1-f560376d4ee2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ae4e7fc1879a530f2a97f41276d9d0d4237ba471
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701993"
---
# <a name="stretch-database"></a>Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Stretch Database migra i dati ad accesso sporadico in modo trasparente e sicuro nel cloud di Microsoft Azure.  
  
 Per una guida introduttiva su Stretch Database, vedere [Avviare la procedura guidata Abilitare il database per Stretch](../../sql-server/stretch-database/get-started-by-running-the-enable-database-for-stretch-wizard.md).  
  
## <a name="what-are-the-benefits-of-stretch-database"></a>Quali sono i vantaggi di Stretch Database?  
 Stretch Database offre i vantaggi seguenti:  
  
 **Offre disponibilità conveniente per i dati ad accesso sporadico**  
 Consente di estendere i dati transazionali ad accesso frequente e sporadico in modo dinamico da SQL Server a Microsoft Azure con SQL Server Stretch Database. A differenza della tipica archiviazione dei dati ad accesso sporadico, i dati sono sempre online e disponibili per eseguire query. È possibile fornire sequenze temporali di durata maggiore per la conservazione dei dati senza ridurre lo spazio per le tabelle di grandi dimensioni come la cronologia degli ordini cliente. È possibile trarre vantaggio dal basso costo di Azure invece di aggiornare la costosa archiviazione locale. Scegliere il piano tariffario e configurare le impostazioni nel portale di Azure per mantenere il controllo su prezzo e costi. Scalare in verticale o in orizzontale in base alle esigenze. Per informazioni dettagliate, vedere [Prezzi di SQL Server Stretch Database](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
 **Non richiede modifiche a query o applicazioni**  
 Consente di accedere direttamente ai dati di SQL Server a prescindere che si trovino in locale o che siano stati estesi al cloud.  Impostare i criteri che determinano le posizioni di archiviazione dei dati e SQL Server gestisce il trasferimento dei dati in background. L'intera tabella è sempre online e disponibile per le query. Stretch Database non richiede modifiche alle query o alle applicazioni esistenti: il percorso dei dati è completamente disponibile per l'applicazione.  
  
 **Semplifica la manutenzione dei dati locali**  
 Consente di ridurre la manutenzione e l’archiviazione locale dei dati. I backup dei dati in locale vengono eseguiti più velocemente e terminano all'interno della finestra di manutenzione. Esegue in automatico il backup della parte dei dati nel cloud. Le esigenze di archiviazione locale vengono notevolmente ridotte. L’archiviazione di Azure può consentire un risparmio dell’80% rispetto all’aggiunta di unità SSD locali.  
  
 **Protegge i dati anche durante la migrazione**  
 Consente di estendere in massima tranquillità e in modo sicure le applicazioni più importanti nel cloud. La Crittografia sempre attiva di SQL Server offre la crittografia dei dati in movimento. La sicurezza a livello di riga e altre funzionalità avanzate per la sicurezza di SQL Server funzionano anche con Stretch Database per proteggere i dati.  
  
## <a name="what-does-stretch-database-do"></a>Funzionalità di Stretch Database  
 Dopo l'abilitazione di Stretch Database per un'istanza di SQL Server e di un database e dopo la selezione di almeno una tabella, Stretch Database avvia automaticamente la migrazione dei dati ad accesso sporadico in Azure.  
  
-   Se i dati ad accesso sporadico vengono archiviati in una tabella separata, è possibile eseguire la migrazione dell'intera tabella.  
  
-   Se la tabella contiene dati usati più di frequente e dati usati meno di frequente, è possibile specificare una funzione di filtro per selezionare le righe di cui eseguire la migrazione.

**Non è necessario modificare le query e le applicazioni client esistenti.** Si continua ad avere accesso trasparente ai dati locali e remoti, anche durante la migrazione dei dati. Potrebbe essere riscontrata una leggera latenza per le query remote, che si verifica solo quando si esegue una query dei dati ad accesso sporadico.

**Stretch Database assicura che nessun dato venga perso** se si verifica un errore durante la migrazione. Estensione database vanta anche una logica di riesecuzione per gestire i problemi di connessione che possono verificarsi durante la migrazione. Una DMV fornisce lo stato della migrazione.

**È possibile sospendere la migrazione dei dati** per risolvere i problemi nel server locale o per ottimizzare la larghezza di banda di rete disponibile.  
  
 ![Panoramica di Estensione database](../../sql-server/stretch-database/media/stretch-overview.png "Panoramica di Estensione database")  
  
## <a name="is-stretch-database-for-you"></a>Idoneità di Stretch Database per il sistema usato  
 Se è possibile impostare le seguenti istruzioni, Stretch Database può aiutare a soddisfare i requisiti e a risolvere i problemi.  
  
|Responsabili delle decisioni|DBA|  
|--------------------------------|---------------------|  
|È necessario mantenere i dati transazionali per molto tempo.|Le dimensioni delle tabelle sono fuori controllo.|  
|Alcune volte è necessario eseguire query dei dati ad accesso sporadico.|Gli utenti sostengono che desiderano accedere ai dati ad accesso sporadico, che usano solo raramente.|  
|Si dispone di applicazioni, incluse applicazioni meno recenti, che non si intende aggiornare.|È necessario continuare ad aggiungere spazio di archiviazione.|  
|Si desidera trovare un modo per risparmiare denaro sull'archiviazione.|Non è possibile eseguire il backup o il ripristino di tabelle di dimensioni così grandi secondo quanto previsto dal contratto di servizio.|  
  
## <a name="what-kind-of-databases-and-tables-are-candidates-for-stretch-database"></a>Tipologie di database e tabelle idonee per Stretch Database  
 Stretch Database è ideale per i database transazionali che contengono grandi quantità di dati ad accesso sporadico, in genere archiviati in un numero ridotto di tabelle. Queste tabelle possono contenere più di un miliardo di righe.  
  
 Se si usa la funzionalità della tabella temporale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], usare Stretch Database per migrare tutta o una parte della tabella di cronologia associata per un'archiviazione conveniente in Azure. Per altre informazioni, vedere [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md).  
  
 Per identificare i database e le tabelle Estensione database, usare Stretch Database Advisor, una funzionalità SQL Server 2016 Upgrade Advisor. Per altre informazioni, vedere [Identificare i database e le tabelle per Estensione database eseguendo Stretch Database Advisor](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md). Per altre informazioni sui potenziali problemi che causano il blocco, vedere [Limitazioni per Stretch Database](../../sql-server/stretch-database/limitations-for-stretch-database.md).  

## <a name="test-drive-stretch-database"></a>Test drive di Stretch Database  
 **Test drive di Stretch Database con il database di esempio AdventureWorks.** Per ottenere il database di esempio AdventureWorks, è necessario scaricare almeno il file di database e il file di script ed esempi da [qui](https://www.microsoft.com/download/details.aspx?id=49502). Dopo aver ripristinato il database di esempio in un'istanza di SQL Server 2016, decomprimere il file di esempi e aprire il file degli esempi di Estensione database dalla cartella Stretch DB. Eseguire gli script in questo file per controllare lo spazio usato dai dati prima e dopo aver abilitato Stretch Database, per tenere traccia dello stato della migrazione dei dati e per verificare di poter continuare a eseguire query sui dati esistenti e inserire nuovi dati sia durante sia dopo la migrazione dei dati.  
  
## <a name="next-step"></a>Passaggio successivo  
 **Identificare i database e le tabelle candidati per Stretch Database.** Per identificare i database e le tabelle candidati per Estensione database, scaricare SQL Server 2016 Upgrade Advisor ed eseguire Stretch Database Advisor. Stretch Database Advisor identifica anche i problemi di blocco. Per altre informazioni, vedere [Identificare i database e le tabelle per Estensione database eseguendo Stretch Database Advisor](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md).  
  
  
