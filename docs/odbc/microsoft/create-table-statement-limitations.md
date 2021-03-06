---
title: Limitazioni dell'istruzione CREATE TABLE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db5d2cb8decde9828acd3005551717ac9f6cef32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096588"
---
# <a name="create-table-statement-limitations"></a>Limitazioni dell'istruzione CREATE TABLE
Quando si usa Microsoft Access, Microsoft Excel o Paradoxdriver e la lunghezza di una colonna di tipo text o Binary non è specificata (oppure è specificata come 0), la lunghezza della colonna verrà impostata su 255.  
  
 Quando si usa il driver dBASE e la lunghezza di una colonna di testo o binaria non è specificata (oppure è specificata come 0), la lunghezza della colonna verrà impostata su 254.  
  
 È supportato un massimo di 255 colonne.  
  
 Quando il driver Microsoft Excel viene usato in un'origine dati MicrosoftExcel 5,0, 7,0 o 97, non è possibile creare un foglio di lavoro con lo stesso nome di un foglio di lavoro che è stato eliminato in precedenza. Quando si utilizza il driver Microsoft Excel per accedere a un foglio di lavoro versione 5,0, 7,0 o 97, un'istruzione DROP TABLE Cancella il foglio di lavoro, ma non elimina il nome del foglio di lavoro.  
  
 Quando si utilizza il driver Paradox, non è possibile aggiungere le colonne dopo che è stato definito un indice in una tabella. Se la prima colonna dell'elenco di argomenti di un'istruzione CREATE TABLE crea un indice, non è possibile includere una seconda colonna nell'elenco di argomenti.
