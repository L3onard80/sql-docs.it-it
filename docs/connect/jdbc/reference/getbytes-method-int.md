---
title: Metodo getBytes (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getBytes (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8c2973e6-d57f-4f64-b812-350ce4098ce6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 041866ac999d8a91487d0e68e2ac77a66724ad32
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658739"
---
# <a name="getbytes-method-int"></a>Metodo getBytes (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come matrice di valori byte in base all'indice del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public byte[] getBytes(int index)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Valore **int** che specifica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Matrice di **byte** valori.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 In una versione precedente di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] è possibile usare SQLServerCallableStatement.getBytes per convertire valori tra matrici di byte e il tipo di dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **date**, **time**, **datetime2** o **datetimeoffset**. In questa versione l'utilizzo del metodo con questi tipi di dati provoca un'eccezione indicante che la conversione non è supportata.  
  
 Questo metodo getBytes viene specificato dal metodo getBytes nell'interfaccia java.sql.CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBytes &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getbytes-method-sqlservercallablestatement.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
