---
title: Descrittori e driver di database desktop | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0096dad8fbb4cf9847385759702e39ac074c4c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68112053"
---
# <a name="descriptors-and-desktop-database-drivers"></a>Descrittori e driver di database desktop
Un descrittore è una struttura di dati che include informazioni sui parametri dinamici o sui dati della colonna. **SQLGetDescField** può essere usato per recuperare i descrittori supportati elencati di seguito. I descrittori di parametri di implementazione (dpi) non vengono popolati automaticamente perché **SQLDescribeParam** non è supportato. Non sono inoltre supportati i campi di descrizione che non sono disponibili tramite Jet, ad esempio SQL_DESC_BASE_TABLE_NAME.  
  
 Per ulteriori informazioni sui campi di descrizione supportati da Jet, vedere *Microsoft jet motore di database Programmer ' s Guide*.  
  
 Per ulteriori informazioni sui descrittori, vedere gli argomenti in "descrittori" in *ODBC Programmer ' s Reference*.  
  
|Campi del descrittore|Livello di supporto|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Supportato|  
|SQL_DESC_ARRAY_SIZE|Supportato solo per ARD|  
|SQL_DESC_ARRAY_STATUS_PTR|Supportato|  
|SQL_DESC_BIND_OFFSET_PTR|Supportato|  
|SQL_DESC_BIND_TYPE|Supportato|  
|SQL_DESC_COUNT|Supportato|  
|SQL_DESC_ROWS_PROCESSED_PTR|Supportato solo per ARD|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Supportato|  
|SQL_DESC_BASE_COLUMN_NAME|Supportato (nuovo)|  
|SQL_DESC_BASE_TABLE_NAME|Supportato (nuovo)|  
|SQL_DESC_CASE_SENSITIVE|Sempre FALSE|  
|SQL_DESC_CATALOG_NAME|Non supportate|  
|SQL_DESC_CONCISE_TYPE|Supportato|  
|SQL_DESC_DATA_PTR|Supportato|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Supportato|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Supportato per i tipi di intervallo C|  
|SQL_DESC_DISPLAY_SIZE|Supportato|  
|SQL_DESC_FIXED_PREC_SCALE|Supportato (TRUE per Money)|  
|SQL_DESC_INDICATOR_PTR|Supportato|  
|SQL_DESC_LABEL|Supportato|  
|SQL_DESC_LENGTH|Supportato|  
|SQL_DESC_LITERAL_PREFIX|Supportato|  
|SQL_DESC_LITERAL_SUFFIX|Supportato|  
|SQL_DESC_LOCAL_TYPE_NAME|Non supportato (restituisce una stringa vuota)|  
|SQL_DESC_NAME|Supportato|  
|SQL_DESC_NULLABLE|Supportato<br /><br /> **Nota** Non supportato nelle versioni precedenti a Jet 4,0|  
|SQL_DESC_NUM_PREC_RADIX|Supportato|  
|SQL_DESC_OCTET_LENGTH|Supportato|  
|SQL_DESC_OCTET_LENGTH_PTR|Supportato|  
|SQL_DESC_PARAMETER_TYPE|Solo parametri di input|  
|SQL_DESC_PRECISION|Supportato|  
|SQL_DESC_SCALE|Supportato|  
|SQL_DESC_SCHEMA_NAME|Non supportate|  
|SQL_DESC_SEARCHABLE|Supportato|  
|SQL_DESC_TABLE_NAME|Non supportate|  
|SQL_DESC_TYPE|Supportato|  
|SQL_DESC_TYPE_NAME|Supportato|  
|SQL_DESC_UNNAMED|Supportato|  
|SQL_DESC_UNSIGNED|Supportato|  
|SQL_DESC_UPDATABLE|Supportato|
