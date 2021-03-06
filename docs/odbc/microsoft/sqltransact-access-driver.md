---
title: SQLTransact (driver di accesso) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f4d4b3d8d417591bd72dde22240c81a91d80f990
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948976"
---
# <a name="sqltransact-access-driver"></a>SQLTransact (driver Access)
> [!NOTE]  
>  In questo argomento vengono fornite informazioni specifiche del driver di accesso. Per informazioni generali su questa funzione, vedere l'argomento appropriato in informazioni di [riferimento sulle API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Quando si utilizza il driver Microsoft Access, SQL_COMMIT e SQL_ROLLBACK sono supportati per l'argomento *ftype* in una chiamata a **SQLTransact**.  
  
 Se si verifica un errore durante il processo di commit, è possibile ripristinare il database interessato utilizzando l'opzione Ripristina database nell'installazione del driver Microsoft Access o tramite l'utilizzo della parola chiave REPAIR_DB nella funzione **SQLConfigDataSource** .
