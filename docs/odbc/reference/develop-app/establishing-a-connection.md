---
title: Stabilire una connessione | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- SQLBrowseConnect function [ODBC], establishing a connection
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- SQLConnect function [ODBC], establishing a connection
- SQLDriverConnect function [ODBC], making a connection
- ODBC drivers [ODBC], connection functions
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7ef6f3d50382d810dd9df246c4d857d9467674f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "76941030"
---
# <a name="establishing-a-connection"></a>Istituzione di una connessione
Dopo aver allocato gli handle di ambiente e di connessione e aver impostato gli attributi di connessione, l'applicazione è pronta per la connessione all'origine dati o al driver. Per eseguire questa operazione, l'applicazione può usare tre diverse funzioni: **SQLConnect** (livello di conformità dell'interfaccia Core), **SQLDriverConnect** (Core) e **SQLBrowseConnect** (livello 1). Ognuno dei tre è progettato per essere utilizzato in uno scenario diverso. Prima della connessione, l'applicazione può determinare quali di queste funzioni sono supportate con la parola chiave **ConnectFunctions** restituita da **SQLDrivers**.  
  
> [!NOTE]  
>  Alcuni driver limitano il numero di connessioni attive supportate. Un'applicazione chiama **SQLGetInfo** con l'opzione SQL_MAX_DRIVER_CONNECTIONS per determinare il numero di connessioni attive supportate da un determinato driver.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Origine dati predefinita](../../../odbc/reference/develop-app/default-data-source.md)  
  
-   [Connessione con SQLConnect](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)  
  
-   [Stringhe di connessione](../../../odbc/reference/develop-app/connection-strings.md)  
  
-   [Connessione con SQLDriverConnect](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)  
  
-   [Connessione con SQLBrowseConnect](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)
