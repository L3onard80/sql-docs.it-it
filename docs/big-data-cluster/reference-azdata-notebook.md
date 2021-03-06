---
title: Informazioni di riferimento su azdata notebook
titleSuffix: SQL Server big data clusters
description: Articolo di riferimento per i comandi azdata notebook.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0a866dcca1debba47abf2e2e241d00151b8641ff
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "74820968"
---
# <a name="azdata-notebook"></a>azdata notebook

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L'articolo seguente offre informazioni di riferimento sui comandi `notebook` dello strumento `azdata`. Per altre informazioni su altri comandi `azdata`, vedere [Informazioni di riferimento su azdata](reference-azdata.md)

## <a name="commands"></a>Comandi:
|     |     |
| --- | --- |
[azdata notebook view](#azdata-notebook-view) | Visualizza un notebook.  Opzione per arrestare subito un errore di esecuzione della cella.
[azdata notebook run](#azdata-notebook-run) | Esegue un notebook.  L'esecuzione viene arrestata al primo errore.
## <a name="azdata-notebook-view"></a>azdata notebook view
Questo comando può acquisire un file notebook e convertire il Markdown, il codice e l'output nel formato del terminale a colori.
```bash
azdata notebook view --path -p 
                     [--continue-on-error -c]
```
### <a name="examples"></a>Esempi
Visualizzare il notebook.  Vengono visualizzate tutte le celle.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb'
```
Visualizzare il notebook.  Vengono visualizzate tutte le celle, a meno che nell'output non venga rilevata una cella con errore.  In questo caso, l'output viene arrestato.
```bash
azdata notebook view --path '/home/me/notebooks/demo_notebook.ipynb' --stop-on-error
```
### <a name="required-parameters"></a>Parametri obbligatori
#### `--path -p`
Percorso del notebook da visualizzare.
### <a name="optional-parameters"></a>Parametri facoltativi
#### `--continue-on-error -c`
Continua a visualizzare celle aggiuntive, ignorando eventuali errori di cella rilevati nell'output del notebook.  Il comportamento predefinito è arrestare il processo in caso di errore.  In questo modo, infatti, è più facile esaminare la prima cella in cui è stato rilevato un errore.
### <a name="global-arguments"></a>Argomenti globali
#### `--debug`
Aumenta il livello di dettaglio della registrazione per mostrare tutti i log di debug.
#### `--help -h`
Visualizza questo messaggio della guida ed esce.
#### `--output -o`
Formato di output.  Valori consentiti: json, jsonc, table, tsv.  Valore predefinito: json.
#### `--query -q`
Stringa di query JMESPath. Per altre informazioni ed esempi, vedere [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Aumenta il livello di dettaglio della registrazione. Usare --debug per log di debug completi.
## <a name="azdata-notebook-run"></a>azdata notebook run
Questo comando crea una directory temporanea ed esegue al suo interno il notebook specificato come directory di lavoro.
```bash
azdata notebook run --path -p 
                    [--output-path]  
                    [--output-html]  
                    [--arguments -a]  
                    [--interactive -i]  
                    [--clear -c]  
                    [--timeout -t]
```
### <a name="examples"></a>Esempi
Eseguire un notebook.
```bash
azdata notebook run --path '/home/me/notebooks/demo_notebook.ipynb'
```
### <a name="required-parameters"></a>Parametri obbligatori
#### `--path -p`
Percorso di file del notebook da eseguire.
### <a name="optional-parameters"></a>Parametri facoltativi
#### `--output-path`
Percorso di directory da usare per l'output del notebook.  Il notebook con i dati di output e i file prodotti dal notebook vengono generati in relazione a questa directory.
#### `--output-html`
Flag facoltativo che indica se convertire ulteriormente il notebook di output in formato HTML.  Crea un secondo file di output.
#### `--arguments -a`
Elenco facoltativo di argomenti del notebook da inserire nell'esecuzione del notebook.  Codificati come dizionario JSON.  Esempio: '{"name":"value", "name2":"value2"}'
#### `--interactive -i`
Consente di eseguire un notebook in modalità interattiva.
#### `--clear -c`
In modalità interattiva cancellare il contenuto del riquadro della console prima di eseguire il rendering di una cella.
#### `--timeout -t`
Secondi di attesa per il completamento dell'esecuzione. Il valore-1 indica un'attesa infinita.
`600`
### <a name="global-arguments"></a>Argomenti globali
#### `--debug`
Aumenta il livello di dettaglio della registrazione per mostrare tutti i log di debug.
#### `--help -h`
Visualizza questo messaggio della guida ed esce.
#### `--output -o`
Formato di output.  Valori consentiti: json, jsonc, table, tsv.  Valore predefinito: json.
#### `--query -q`
Stringa di query JMESPath. Per altre informazioni ed esempi, vedere [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Aumenta il livello di dettaglio della registrazione. Usare --debug per log di debug completi.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su altri comandi `azdata`, vedere [Informazioni di riferimento su azdata](reference-azdata.md). Per altre informazioni su come installare lo strumento `azdata`, vedere [Installare azdata per gestire i cluster Big Data di SQL Server 2019](deploy-install-azdata.md).
