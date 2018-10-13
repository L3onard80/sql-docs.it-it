---
title: Configurazione dell'account di servizio Trusted Launchpad di SQL Server | Microsoft Docs
description: Come modificare l'account del servizio Trusted Launchpad di SQL Server usata per l'esecuzione di script esterni in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/27/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 85d96d758d2f363b3b4ec40131723ad10613b64c
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100392"
---
# <a name="sql-server-launchpad-service-configuration"></a>Configurazione del servizio Launchpad di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] è un servizio che gestisce ed esegue script esterni, analogamente al modo in cui il servizio di indicizzazione e query full-text avvia un host separato per l'elaborazione delle query full-text.

Un oggetto separato [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio viene creato per ogni istanza del motore di database a cui è stato aggiunto l'integrazione con SQL Server machine learning (R o Python).

Per altre informazioni, vedere le sezioni di Launchpad [architettura di estendibilità in servizi di SQL Server Machine Learning](../../advanced-analytics/concepts/extensibility-framework.md#launchpad) e [Panoramica sulla sicurezza per il framework di estendibilità in SQL Server Machine Learning Servizi](../../advanced-analytics/concepts/security.md#launchpad).

## <a name="account-permissions"></a>Autorizzazioni dell'account

Per impostazione predefinita, Launchpad di SQL Server è configurato per l'esecuzione **NT Service\MSSQLLaunchpad**, che viene eseguito il provisioning con tutte le autorizzazioni necessarie per eseguire gli script esterni. Rimozione delle autorizzazioni da questo account può comportare Launchpad è Impossibile avviare o accedere all'istanza di SQL Server in cui devono essere eseguiti gli script esterni.

Se si modifica l'account del servizio, assicurarsi di usare la **criteri di sicurezza locali** dell'applicazione (**tutte le app** > **strumenti di amministrazione di Windows**  >  **Criteri di sicurezza locali**).

Nella tabella seguente sono elencate le autorizzazioni necessarie per questo account.

| Impostazione di criteri di gruppo | Nome di costante |
|----------------------|---------------|
| [Regolazione limite risorse memoria per un processo](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/adjust-memory-quotas-for-a-process) | SeIncreaseQuotaPrivilege | 
| [Ignorare controllo incrociato](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/bypass-traverse-checking) | SeChangeNotifyPrivilege | 
| [Accedi come servizio](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/log-on-as-a-service) | SeServiceLogonRight | 
| [Sostituzione di token a livello di processo](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/replace-a-process-level-token) | SeAssignPrimaryTokenPrivilege | 

Per altre informazioni sulle autorizzazioni necessarie per l'esecuzione di servizi di SQL Server, vedere [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).

<a name="bkmk_ChangingConfig"></a> 

## <a name="configuration-properties"></a>Proprietà di configurazione

In genere, non vi è alcun motivo per modificare la configurazione del servizio. Le proprietà che è stato possibile modificare includono l'account del servizio, il numero di processi esterni (20 per impostazione predefinita) o la password di criteri per gli account di lavoro di reimpostazione.

1. Aprire [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md). 

  + Nella pagina iniziale, digitare **MMC** per aprire Microsoft Management Console.

  + Sul **File** > **Aggiungi/Rimuovi Snap-in**, spostare **Gestione configurazione SQL Server** da disponibile a Snap-in selezionati.

2. In Gestione configurazione SQL Server in servizi di SQL Server, fare doppio clic su Launchpad di SQL Server e selezionare **proprietà**.

  + Per modificare l'account del servizio, scegliere il **Accedi** scheda.

  + Per aumentare il numero di utenti, selezionare la **avanzate** scheda.

> [!Note]
> Nelle prime versioni di SQL Server 2016 R Services, è possibile modificare alcune proprietà del servizio modificando il [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] file di configurazione. Questo file non viene usato per la modifica delle configurazioni. Gestione configurazione SQL Server è l'approccio corretto per le modifiche alla configurazione del servizio, ad esempio l'account del servizio e il numero di utenti.

## <a name="debug-settings"></a>Impostazioni di debug

Alcune proprietà possono essere modificate solo tramite file di configurazione della finestra di avvio, che potrebbe essere utile in alcuni casi, ad esempio il debug. Il file di configurazione viene creato durante [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di installazione e per impostazione predefinita viene salvato come file di testo normale nel percorso seguente: `<instance path>\binn\rlauncher.config`

Per poter apportare modifiche a questo file è necessario essere amministratore del computer su cui è eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si decide di modificare il file, si consiglia di crearne una copia di backup prima di salvare le modifiche.

La tabella seguente elenca le impostazioni avanzate per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], con i valori consentiti. 

|**Nome impostazione**|**Tipo**|**Descrizione**|
|----|----|----|
|PROCESSO\_PULIZIA\_VIA\_ESCI|Valore intero |Si tratta di un'impostazione esclusivamente interna: non modificare questo valore. </br></br>Specifica se la cartella di lavoro temporanea creata per ogni sessione runtime esterni deve essere pulita dopo il completamento della sessione. L'impostazione è utile per il debug. </br></br>I valori supportati sono **0** (disabilitato) o **1** (abilitato). </br></br>Il valore predefinito è 1, i file di log significato sono rimossi all'uscita.|
|TRACCIA\_LIVELLO|Valore intero |Consente di configurare il livello di dettaglio di traccia di MSSQLLAUNCHPAD a scopo di debug. Ciò influisce sui file di traccia nel percorso specificato dall'impostazione LOG_DIRECTORY. </br></br>I valori supportati sono: **1** (errore), **2** (prestazioni), **3** (avviso), **4** (informazioni). </br></br>Il valore predefinito è 1, vale a dire solo avvisi di output.|

Tutte le impostazioni assumono la forma di coppie chiave-valore e ogni impostazione si trova su una riga diversa. Per modificare il livello di traccia, ad esempio, si potrebbe aggiungere la riga `Default: TRACE_LEVEL=4`.

## <a name="enforcing-password-policy"></a>Applica criteri password

Se l'organizzazione ha criteri che richiedono la modifica delle password a intervalli regolari, potrebbe essere necessario forzare il servizio Launchpad in modo da rigenerare le password crittografate gestite dal servizio per gli account di lavoro.

Per abilitare questa impostazione e forzare l'aggiornamento delle password, aprire il riquadro **Proprietà** per il servizio Launchpad in Gestione configurazione SQL Server, fare clic su **Avanzate** e modificare l'impostazione di **Reimposta password utenti esterni** scegliendo **Sì**. Quando si applica questa modifica, le password vengono rigenerate immediatamente per tutti gli account utente. Per usare lo script R dopo questa modifica, è necessario riavviare il servizio Launchpad, che rileggerà quindi le password appena generate.

Per reimpostare le password a intervalli regolari, è possibile impostare questo flag manualmente o usare uno script.

## <a name="see-also"></a>Vedere anche

[Framework di estendibilità](../concepts/extensibility-framework.md)

[Panoramica della sicurezza](../concepts/security.md)
