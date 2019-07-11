---
title: Mapping di SQLError | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 452ee7b5e2c9e38aaf0fb81969228f5c5e7b5559
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793066"
---
# <a name="sqlerror-mapping"></a>Mapping di SQLError
Quando un'applicazione chiama **SQLError** tramite un database ODBC *3.x* driver, la chiamata a  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 viene eseguito il mapping a  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 con il *HandleType* impostata sul valore SQL_HANDLE_ENV, SQL_HANDLE_DBC o SQL_HANDLE_STMT, come necessario, argomento e il *gestire* argomento impostato sul valore in *henv*, *hdbc*, o *hstmt*, nel modo appropriato. Il *RecNumber* argomento è determinato da Gestione Driver.
