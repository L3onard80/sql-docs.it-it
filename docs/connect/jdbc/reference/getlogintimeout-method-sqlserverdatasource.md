---
title: Metodo getLoginTimeout (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26a7c8e0cc876c8d13e9beb621354cead2f6296c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708579"
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>Metodo getLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il numero di secondi di attesa di questo oggetto [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) durante il tentativo di stabilire una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** che rappresenta il numero di secondi di attesa.  
  
## <a name="remarks"></a>Remarks  
 Se l'applicazione non specifica in modo esplicito un valore di timeout, questo metodo restituisce un valore predefinito di 15 secondi.  
  
 Questo metodo getLoginTimeout viene specificato dal metodo getLoginTimeout nell'interfaccia javax.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
