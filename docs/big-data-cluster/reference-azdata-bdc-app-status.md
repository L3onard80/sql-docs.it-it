---
title: informazioni di riferimento sullo stato dell'app BDC azdata
titleSuffix: SQL Server big data clusters
description: Articolo di riferimento per i comandi di stato dell'app BDC azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7ebf442b3bf87960d081bfe4b0867cdd082ec22a
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158096"
---
# <a name="azdata-bdc-app-status"></a>stato dell'app BDC azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Questo articolo è un articolo di riferimento per **azdata**. 

## <a name="commands"></a>Comandi:
|     |     |
| --- | --- |
[visualizzazione dello stato dell'app BDC azdata](#azdata-bdc-app-status-show) | Stato del servizio app.
## <a name="azdata-bdc-app-status-show"></a>visualizzazione dello stato dell'app BDC azdata
Stato del servizio app.
```bash
azdata bdc app status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Esempi
Ottenere lo stato del servizio app.
```bash
azdata bdc app status show
```
Ottenere lo stato del servizio app con tutte le istanze.
```bash
azdata bdc app status show --all
```
Ottenere lo stato della risorsa appproxy all'interno del servizio app.
```bash
azdata bdc app status show --resource appproxy
```
### <a name="optional-parameters"></a>Parametri facoltativi
#### `--resource -r`
Ottenere questa risorsa in questo servizio.
#### `--all -a`
Mostra tutte le istanze di ogni risorsa all'interno del servizio.
### <a name="global-arguments"></a>Argomenti globali
#### `--debug`
Aumenta il livello di dettaglio della registrazione per mostrare tutti i log di debug.
#### `--help -h`
Visualizza questo messaggio della guida ed esce.
#### `--output -o`
Formato di output.  Valori consentiti: json, jsonc, table, tsv.  Valore predefinito: json.
#### `--query -q`
Stringa di query JMESPath. Per altre informazioni ed esempi, vedere [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Aumenta il livello di dettaglio della registrazione. Usare --debug per i log di debug completi.

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni su altri comandi **azdata**, vedere [Informazioni di riferimento su azdata](reference-azdata.md). 

- Per altre informazioni su come installare lo strumento **azdata**, vedere [Installare azdata per gestire i cluster Big Data di SQL Server 2019](deploy-install-azdata.md).
