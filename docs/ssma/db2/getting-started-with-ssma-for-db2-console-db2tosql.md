---
title: Introduzione con SSMA per la console DB2 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f245c017-023e-4880-8721-8908d339525e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: fbb0a90d9cfd628e9251a55de3df8b66a22f1ef7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67989666"
---
# <a name="getting-started-with-ssma--for-db2-console-db2tosql"></a>Introduzione con SSMA per la console DB2 (DB2ToSQL)
In questa sezione viene descritta la procedura per avviare e iniziare a usare l'applicazione console DB2. Sono inoltre elencate le convenzioni usate in una tipica finestra di output della console di SSMA.  
  
## <a name="launching-ssma-console"></a>Avvio della console SSMA  
Per avviare l'applicazione console SSMA, attenersi alla procedura seguente:  
  
1.  Passare a **Start** e puntare a **tutti i programmi**.  
  
2.  Fare clic sul collegamento del ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prompt dei comandi Migration Assistant per DB2** .  
  
    Viene visualizzato il menu di utilizzo della console `(/? Help)`SSMA e, che consente di iniziare a usare l'applicazione console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedura per l'uso della console di SSMA  
Dopo che la console è stata avviata correttamente nel sistema Windows, è possibile utilizzare la procedura seguente per lavorare su di essa:  
  
1.  Configurare la console SSMA tramite i file di script. Per ulteriori informazioni su questa sezione, vedere [creazione di file di Script &#40;DB2ToSQL&#41;](../../ssma/db2/creating-script-files-db2tosql.md) .  
  
2.  [Creazione di file di valori di variabile &#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
  
3.  [Creazione dei file di connessione del server &#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
  
4.  [Esecuzione della console SSMA &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md) in base alle esigenze del progetto  
  
Altre funzionalità:  
  
1.  [Gestione delle password](https://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) e esportazione/importazione in altre macchine Windows  
  
2.  [Generazione di report](https://msdn.microsoft.com/69ef5fd9-190d-4c58-8199-b3f77d5e1883) per visualizzare i report di output XML dettagliati per la valutazione/conversion e la migrazione dei dati. È anche possibile generare report di errore dettagliati per i comandi di aggiornamento e sincronizzazione.  
  
## <a name="ssma-console-output-conventions"></a>Convenzioni di output della console SSMA  
Quando si eseguono i comandi e le opzioni di script di SSMA, il programma console Visualizza i risultati e i messaggi (informazioni, errore e così via) per l'utente nella console o, se necessario, reindirizza a un file di output XML. Ogni tipo di messaggio nell'output è identificato da un colore univoco. Ad esempio, il messaggio di testo in colore bianco denota i comandi del file di script; quello in verde rappresenta una richiesta per l'input dell'utente e così via.  
  
![SSMAConsoleOutput_Oracle](../../ssma/db2/media/ssmaconsoleoutput_oracle.jpg "SSMAConsoleOutput_Oracle")  
  
Interpretazione dei colori dell'output della console nella tabella seguente:  
  
|Colore|Descrizione|  
|---------|---------------|  
|Rosso|Errore irreversibile durante l'esecuzione|  
|Grigio|Indicatore di data e ora, messaggio all'utente|  
|Bianco|Comandi file script, tipo di messaggio|  
|Giallo|Avviso|  
|Green|Richiedi input utente|  
|azzurro|Inizio, fine e risultato di un'operazione|  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per DB2](https://msdn.microsoft.com/79fbe8ea-471b-407a-be2a-4100d9b57c61)  
  
