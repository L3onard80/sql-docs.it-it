---
title: Comando INSERT-SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 884a33339db10ee8e07d8b432d1765720d45734a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019454"
---
# <a name="insert---sql-command"></a>INSERT (comando SQL)
Accoda un record alla fine di una tabella che contiene i valori di campo specificati.  
  
 Il driver ODBC Visual FoxPro supporta la sintassi nativa del linguaggio Visual FoxPro per questo comando. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>Argomenti  
 Inserisci in *dbf_name*  
 Specifica il nome della tabella a cui viene accodato il nuovo record. *dbf_name* possibile includere un percorso e può essere un'espressione del nome.  
  
 Se la tabella specificata non è aperta, viene aperta esclusivamente in una nuova area di lavoro e il nuovo record viene aggiunto alla tabella. La nuova area di lavoro non è selezionata. l'area di lavoro corrente rimane selezionata.  
  
 Se la tabella specificata è aperta, INSERT Accoda il nuovo record alla tabella. Se la tabella è aperta in un'area di lavoro diversa dall'area di lavoro corrente, non viene selezionata dopo l'aggiunta del record; l'area di lavoro corrente rimane selezionata.  
  
 [( *fname1*[, *fname2*[,...]])]  
 Specifica nel nuovo record i nomi dei campi in cui vengono inseriti i valori.  
  
 VALORI ( *eExpression1*[, *eExpression2*[,...]])  
 Specifica i valori dei campi inseriti nel nuovo record. Se si omettono i nomi dei campi, è necessario specificare i valori dei campi nell'ordine definito dalla struttura della tabella.  
  
## <a name="remarks"></a>Osservazioni  
 Il nuovo record contiene i dati elencati nella clausola VALUEs.  
  
## <a name="driver-remarks"></a>Osservazioni del driver  
 Quando l'applicazione invia l'istruzione SQL ODBC INSERT all'origine dati, il driver ODBC Visual FoxPro converte il comando nel comando Visual FoxProINSERT senza conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [Comando CREATE TABLE-SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT (comando SQL)](../../odbc/microsoft/select-sql-command.md)
