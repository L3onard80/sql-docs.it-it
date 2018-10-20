---
title: Terminale integrato di Studio di Azure Data | Microsoft Docs
description: Scopri il terminale integrato in Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 91adc56e93a7dc1b065b77169ad18fd977231d9f
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49355982"
---
# <a name="integrated-terminal"></a>Terminale integrato

In [!INCLUDE[name-sos](../includes/name-sos-short.md)] è possibile aprire un terminale integrato, avviato inizialmente dalla radice dell'area di lavoro. Ciò risulta utile poiché elimina la necessità di passare da una finestra all'altra o di modificare lo stato di un terminale esistente per eseguire un'attività rapida dalla riga di comando.

Per aprire il terminale:

* Premere **Ctrl+`** con il carattere apice inverso.
* Selezionare il comando **Terminale integrato** |  dal menu **Visualizza**.
* Dal **riquadro comandi** (**CTRL+MAIUSC+P**) scegliere il comando **Visualizza: Attiva/Disattiva terminale integrato**.

![Terminale](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> È comunque possibile aprire una shell esterna con il **comando Apri nel prompt dei comandi di Esplora risorse** (**Apri nel terminale** in Mac o Linux) se si preferisce lavorare all'esterno di [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="managing-multiple-terminals"></a>Gestione di più terminali

È possibile creare più terminali aperti in diverse posizioni e spostarsi facilmente tra di essi È possibile infatti aggiungere più istanze del terminale facendo clic sull'icona "+" (più) in alto a destra del pannello **TERMINALE** o premendo **Ctrl+Maiusc+`**. Ogni istanza creata aggiunge un'altra voce nell'elenco a discesa in alto a destra, il quale può essere usato per selezionare i vari terminali.

![Più terminali](media/integrated-terminal/terminal-multiple-instances.png)

Per rimuovere le istanze create premere l'icona del cestino.

> [!TIP]
> Se vengono usati spesso più terminali, è possibile aggiungere tasti di scelta rapida per i comandi `focusNext`, `focusPrevious` e `kill` descritti nella [sezione Tasti di scelta rapida](#key-bindings) per spostarsi da un terminale all'altro usando solo la tastiera.

## <a name="configuration"></a>Configurazione

L'impostazione predefinita della shell usata è `$SHELL` in Linux e macOS, PowerShell in Windows 10 e cmd.exe nelle versioni precedenti di Windows. L'impostazione può essere ignorata manualmente impostando `terminal.integrated.shell.*` nelle [impostazioni](settings.md). Gli argomenti possono essere passati alla shell del terminale in Linux e macOS usando l'impostazione `terminal.integrated.shellArgs.*`.

### <a name="windows"></a>Windows

Configurare correttamente la shell in Windows corrisponde ad individuare il file eseguibile corretto e aggiornare l'impostazione. Di seguito un elenco di file eseguibili di shell comuni e i percorsi predefiniti:

```json
// 64-bit cmd if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\cmd.exe"
// 64-bit PowerShell if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\WindowsPowerShell\\v1.0\\powershell.exe"
// Git Bash
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe"
// Bash on Ubuntu (on Windows)
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\bash.exe"
```

> [!NOTE]
> Per essere utilizzato come un terminale integrato, il file eseguibile della shell deve essere un'applicazione console in modo che `stdin/stdout/stderr` possano essere reindirizzati.

> [!TIP]
> La shell del terminale integrato viene eseguita con le autorizzazioni di [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Se è necessario eseguire un comando della shell con autorizzazioni elevate (amministratore) o diverse, è possibile usare le utilità della piattaforma, ad esempio `runas.exe`, all'interno di un terminale.

### <a name="shell-arguments"></a>Argomenti della shell

Quando viene avviata, è possibile passare argomenti alla shell.

Ad esempio, per eseguire bash come una shell di account di accesso (viene eseguito `.bash_profile`), passare l'argomento `-l` (tra virgolette doppie):

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>Impostazioni di visualizzazione del terminale

È possibile personalizzare il carattere e l'altezza della riga nel terminale integrato con le seguenti impostazioni:

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>Tasti di scelta rapida del terminale

Il comando **Visualizza: Attiva/Disattiva terminale integrato** è associato a **Ctrl+`** e mostra/nasconde rapidamente il pannello del terminale integrato.

Di seguito sono elencati i tasti di scelta rapida per spostarsi rapidamente nel terminale integrato:

Key|Comando
---|---
**CTRL+`**|Mostra terminale integrato
**CTRL+MAIUSC+`**|Crea un nuovo terminale
**CTRL+freccia su**|Scorre verso l'alto
**CTRL+freccia giù**|Scorre verso il basso
**CTRL+PGSU**|Scorre di una pagina verso l'alto
**CTRL+PGGIÙ**|Scorre di una pagina verso il basso
**CTRL+Home**|Scorre fino all'inizio
**CTRL + fine**|Scorrere verso il basso
**CTRL+K**|Cancella il contenuto del terminale

Sono disponibili altri comandi e possono essere associati ai tasti di scelta rapida che preferite.

Sono:

* `workbench.action.terminal.focus`: Imposta lo stato attivo del terminale. Corrisponde all'attivazione/disattivazione ma imposta lo stato attivo del terminale anziché nasconderlo, quando è visibile.
* `workbench.action.terminal.focusNext`: Mostra l'istanza di terminale successiva.
* `workbench.action.terminal.focusPrevious`: Mostra l'istanza di terminale precedente.
* `workbench.action.terminal.kill`: Rimuove l'istanza di terminale corrente.
* `workbench.action.terminal.runSelectedText`: Esegue il testo selezionato nell'istanza di terminale.
* `workbench.action.terminal.runActiveFile`: Esegue il file attivo nell'istanza di terminale.

### <a name="run-selected-text"></a>Eseguire il testo selezionato

Per usare il comando `runSelectedText`, selezionare il testo in un editor ed eseguire il comando **Terminale: Esegui testo selezionato nel terminale attivo** tramite il **riquadro comandi** (**CTRL+MAIUSC+P**). Il terminale tenta di eseguire il testo selezionato:

![Eseguire il testo selezionato](media/integrated-terminal/terminal_run_selected.png)

Se non è selezionato alcun testo nell'editor attivo, viene eseguita nel terminale la riga su cui si trova il cursore.

### <a name="copy--paste"></a>Copia e Incolla

I tasti di scelta rapida per copiare e incollare seguono gli standard di piattaforma:

* Linux: **Ctrl + Maiusc + C** e **Ctrl + MAIUSC + V**
* Mac: **Cmd + C** e **Cmd + V**
* Windows: **Ctrl + C** e **Ctrl + V**

### <a name="find"></a>Trova

Il terminale integrato dispone di una funzionalità di ricerca di base attivabile tramite **Ctrl+F**.

Se si desidera che **Ctrl+F** venga eseguito sulla shell anziché come ricerca in Linux e Windows, è necessario rimuovere il tasto di scelta rapida:

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>Rinominare le sessioni del terminale

Le sessioni del terminale integrato possono essere rinominate ora utilizzando il comando **Terminale: Rinomina** (`workbench.action.terminal.rename`). Il nuovo nome viene visualizzato in terminal selezione elenco a discesa.

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>Utilizzo forzato di tasti di scelta rapida per il passaggio tra i terminali

Mentre il terminale integrato è attivo, molti tasti di scelta rapida non funzioneranno perché tali sequenze sono utilizzati dal terminale stesso. L'impostazione `terminal.integrated.commandsToSkipShell` può essere utilizzata per risolvere il problema. Contiene una matrice di nomi di comando con tasti di scelta rapida ignorare l'elaborazione, la shell e invece essere elaborati dal [!INCLUDE[name-sos](../includes/name-sos-short.md)] sistema di associazione della chiave. Per impostazione predefinita, questo include tutti i tasti di scelta rapida del terminale più una selezione di alcuni dei più comuni tasti di scelta rapida.

