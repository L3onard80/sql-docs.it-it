---
title: Panoramica di Common Language Runtime (CLR)
description: SQL Server e Istanza gestita di database SQL di Azure consentono di implementare alcune funzionalità utilizzando i linguaggi .NET utilizzando l'integrazione nativa Common Language Runtime (CLR) come SQL Server moduli lato server (procedure, funzioni e trigger).
ms.custom: seo-lt-2019
ms.date: 06/20/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
author: rothja
ms.author: jroth
ms.openlocfilehash: 3ae939be30262130bc1caed2a96201eacb0e22f9
ms.sourcegitcommit: 10ab8d797a51926e92aec977422b1ee87b46286d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544955"
---
# <a name="common-language-runtime-integration"></a>Integrazione di Common Language Runtime
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index) consentono di implementare alcune funzionalità utilizzando i linguaggi .NET utilizzando l'integrazione nativa Common Language Runtime (CLR) come SQL Server moduli lato server (procedure, funzioni e trigger). CLR fornisce codice gestito con servizi quali l'integrazione tra linguaggi diversi, la sicurezza da accesso di codice, la gestione della durata degli oggetti e il supporto per il debug e il profiling. Grazie all'integrazione con Common Language Runtime, gli sviluppatori di applicazioni e gli utenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hanno ora la possibilità di scrivere stored procedure, trigger, tipi definiti dall'utente, funzioni definite dall'utente (scalari e con valori di tabella) e funzioni di aggregazione definite dall'utente utilizzando qualsiasi linguaggio di .NET Framework, inclusi [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include la versione preinstallata di 4 di .NET Framework.  

> [!WARNING]
>  CLR usa la Sicurezza dall'accesso di codice (CAS, Code Access Security) in .NET Framework, non più supportata come limite di sicurezza. Un assembly CLR creato con `PERMISSION_SET = SAFE` potrebbe essere in grado di accedere alle risorse di sistema esterne, chiamare codice non gestito e acquisire privilegi sysadmin. A partire da [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)], viene introdotta un'opzione `sp_configure` denominata `clr strict security` per migliorare la sicurezza degli assembly CLR. `clr strict security` è abilitata per impostazione predefinita e considera gli assembly CLR `SAFE` e `EXTERNAL_ACCESS` come se fossero contrassegnati `UNSAFE`. È possibile disabilitare l'opzione `clr strict security` per la compatibilità con le versioni precedenti, ma questa operazione è sconsigliata. Microsoft consiglia che tutti gli assembly siano firmati con un certificato o una chiave asimmetrica con un account di accesso corrispondente che disponga dell'autorizzazione `UNSAFE ASSEMBLY` nel database master. Per altre informazioni, vedere [CLR strict security](../../database-engine/configure-windows/clr-strict-security.md). Gli amministratori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono anche aggiungere assembly a un elenco di assembly, considerato attendibile dal motore di database. Per altre, vedere [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md).

È inoltre possibile guardare questo video di 6 minuti in cui viene illustrato come utilizzare CLR in Istanza gestita di database SQL di Azure:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Its-just-SQL-CLR-in-Azure-SQL-Database-Managed-Instance/player?WT.mc_id=dataexposed-c9-niner]



## <a name="when-to-use-clr-modules"></a>Quando usare i moduli CLR?

L'integrazione con CLR consente di implementare funzionalità complesse disponibili in .NET Framework, ad esempio espressioni regolari, codice per l'accesso a risorse esterne (server, servizi Web, database), crittografia personalizzata e così via. Di seguito sono elencati alcuni dei vantaggi dell'integrazione con CLR sul lato server:
  
-   **Un modello di programmazione migliore.** I linguaggi .NET Framework sono sotto molti aspetti più completi di Transact-SQL, in quanto offrono costrutti e funzionalità precedentemente non disponibili per gli sviluppatori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile inoltre sfruttare la potenza della libreria .NET Framework che fornisce una vasta gamma di classi, utilizzabili in modo rapido ed efficiente per risolvere i problemi di programmazione.  
  
-   **Miglioramento della sicurezza e della protezione.** Il codice gestito è in esecuzione in un ambiente CLR, ospitato dal motore di database. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lo utilizza per fornire un'alternativa più sicura alle stored procedure estese disponibili in versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Possibilità di definire tipi di dati e funzioni di aggregazione.** I tipi definiti dall'utente e le funzioni di aggregazione definite dall'utente sono due nuovi oggetti di database gestiti che espandono le capacità di archiviazione ed esecuzione di query di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Sviluppo semplificato attraverso un ambiente standardizzato.** Lo sviluppo di database è integrato nelle versioni future dell'ambiente di sviluppo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio .NET. Gli sviluppatori utilizzano per lo sviluppo e il debug degli script e degli oggetti di database gli stessi strumenti impiegati per scrivere componenti e servizi .NET Framework di livello intermedio o di livello client.  
  
-   **Possibilità di prestazioni e scalabilità migliori.** In molte situazioni, i modelli di compilazione ed esecuzione del linguaggio .NET Framework consentono di ottenere prestazioni migliori rispetto a Transact-SQL.  
  
 Nella tabella seguente sono elencati gli argomenti inclusi in questa sezione.  
  
 [Panoramica dell'integrazione con CLR](../../relational-databases/clr-integration/clr-integration-overview.md)  
 Vengono descritti i tipi di oggetti che è possibile compilare utilizzando l'integrazione con CLR e vengono esaminati i requisiti per la compilazione di oggetti di database tramite questa integrazione.  
  
 [Novità dell'integrazione con CLR](../../relational-databases/clr-integration/clr-integration-what-s-new.md)  
 Vengono descritte le nuove caratteristiche di questa versione.  
  
 [Architettura dell'integrazione con CLR](https://msdn.microsoft.com/library/05e4b872-3d21-46de-b4d5-739b5f2a0cf9)  
 Vengono illustrati gli obiettivi di progettazione dell'integrazione con CLR.  
  
 [Abilitazione dell'integrazione con CLR](../../relational-databases/clr-integration/clr-integration-enabling.md)  
 Viene illustrato come abilitare l'integrazione con CLR.  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione del .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] solo)   
 [Prestazioni dell'integrazione con CLR](../../relational-databases/clr-integration/clr-integration-architecture-performance.md)  
  
  
