---
title: SQLDriverConnect (driver ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6fd8f3be1213a91195cd74a8b723629e2c5833f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053895"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (driver ODBC Visual FoxPro)
> [!NOTE]  
>  Questo argomento contiene informazioni specifiche del driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in informazioni di [riferimento sulle API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità API ODBC: livello 1  
  
 Consente di connettersi a un'origine dati esistente, che può essere un [database](../../odbc/microsoft/visual-foxpro-terminology.md) o una directory di [tabelle gratuite](../../odbc/microsoft/visual-foxpro-terminology.md). Le parole chiave degli attributi ODBC UID e PWD vengono ignorate. Nella tabella seguente sono elencate le parole chiave aggiuntive per gli attributi supportati.  
  
|Parola chiave dell'attributo ODBC|Valore attributo|  
|----------------------------|---------------------|  
|DSN||  
|UID|Ignorato dal driver ODBC Visual FoxPro ma non genera un errore.|  
|PWD|Ignorato dal driver ODBC Visual FoxPro ma non genera un errore.|  
|Driver|Nome e percorso del driver ODBC Visual FoxPro. implementato da Gestione driver.|  
  
|Parola chiave dell'attributo del driver ODBC Visual FoxPro|Valore attributo|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|"Sì" o "No"|  
|Fascicola|"Machine" o un'altra sequenza di ordinamento. Per un elenco delle sequenze di confronto supportate, vedere [SET COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Descrizione||  
|Esclusivo|"Sì" o "No"|  
|SourceDB|Percorso completo di una directory contenente zero o più [tabelle gratuite](../../odbc/microsoft/visual-foxpro-terminology.md)oppure il percorso assoluto e il nome file per un [database](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|"DBC" o "DBF"|  
|Versione||  
  
 Se il nome dell'origine dati non è specificato, gestione driver richiede all'utente le informazioni (a seconda dell'impostazione dell'argomento *fDriverCompletion* ) e continua. Se sono necessarie ulteriori informazioni, il driver ODBC Visual FoxPro Visualizza la finestra di dialogo di richiesta.  
  
 Per ulteriori informazioni, vedere [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) in *ODBC Programmer ' s Reference*.
