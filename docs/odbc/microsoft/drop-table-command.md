---
title: Comando DROP TABLE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 278950bac7589b8a6b02d894c8133a699c3bd1ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071802"
---
# <a name="drop-table-command"></a>DROP TABLE (comando)
Rimuove una tabella dal database specificato con l'origine dati e la Elimina dal disco.  
  
 Il driver ODBC Visual FoxPro supporta la sintassi nativa del linguaggio Visual FoxPro per questo comando. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Impostazioni  
 *TableName*  
 Specifica la tabella da rimuovere dal database specificato con l'origine dati e da eliminare dal disco.  
  
 *FileName*  
 Specifica una tabella gratuita da eliminare dal disco.  
  
 ?  
 Consente di visualizzare la finestra di dialogo Rimuovi dalla quale è possibile scegliere una tabella da rimuovere dal database specificato con l'origine dati e da eliminare dal disco.  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene eseguita l'eliminazione della tabella, vengono rimossi anche tutti gli indici primari, i valori predefiniti e le regole di convalida associati alla tabella. DROP TABLE influiscono anche sulle altre tabelle del database specificato con l'origine dati se tali tabelle presentano regole o relazioni associate alla tabella da rimuovere. Le regole e le relazioni non sono più valide quando la tabella viene rimossa dal database.  
  
## <a name="driver-remarks"></a>Osservazioni del driver  
 Quando l'applicazione invia l'istruzione ODBC SQL DROP TABLE all'origine dati, il driver ODBC Visual FoxPro converte il comando nel comando TABLE di Visual FoxProDROP usando la sintassi illustrata nella tabella seguente.  
  
|Sintassi ODBC|Origine dati|Sintassi di Visual FoxPro|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *-base-nome-tabella*|Database (file con estensione DBC)|Rimuovi tabella *TableName* Delete|  
||Directory delle tabelle gratuite (file con estensione dbf)|Cancella *dbfName*<br /><br /> Cancella *cdxName*<br /><br /> Cancella *fptName*|
