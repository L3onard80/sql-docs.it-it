---
title: Livello di isolamento della transazione del cursore | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fef68bfdb62527f7b631b8d7433e095eba4d1c88
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207148"
---
# <a name="cursor-transaction-isolation-level"></a>Livello di isolamento delle transazioni di cursore
  Il comportamento di blocco completo dei cursori si basa su un'interazione fra gli attributi di concorrenza e il livello di isolamento delle transazioni impostati dal client. I client ODBC impostano il livello di isolamento delle transazioni usando gli attributi SQL_ATTR_TXN_ISOLATION o SQL_COPT_SS_TXN_ISOLATION di [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) . Il comportamento di blocco di un ambiente di cursore specifico è determinato dalla combinazione dei comportamenti di blocco della concorrenza con le opzioni del livello di isolamento delle transazioni.  
  
 Il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta i livelli di isolamento delle transazioni del cursore seguenti:  
  
-   Read committed (SQL_TXN_READ_COMMITTED)  
  
-   Read uncommitted (SQL_TXN_READ_UNCOMMITTED)  
  
-   Repeatable read (SQL_TXN_REPEATABLE_READ)  
  
-   Serializable (SQL_TXN_SERIALIZABLE)  
  
-   Snapshot (SQL_TXN_SS_SNAPSHOT)  
  
 Si noti che l'API ODBC specifica livelli di isolamento delle transazioni aggiuntivi, che tuttavia non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono supportati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] da o dal driver ODBC di Native Client.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del cursore](cursor-properties.md)  
  
  
