---
title: SQLSetPos (driver di database desktop) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d35a282acf3b672113ec71b534b4087aa3549285
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905459"
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (driver di database desktop)
Sono supportate la semantica del modello bulk per le chiamate **SQLSetPos** con l'argomento *IRow* uguale a 0.  
  
 SQL_LOCK_NO_CHANGE è supportato per *Flock*. SQL_LOCK_EXCLUSIVE e SQL_LOCK_UNLOCK non sono supportati.  
  
 **SQLSetPos** supporta i join aggiornabili. Per ulteriori informazioni, vedere la *Guida per programmatori Microsoft Jet motore di database*.
