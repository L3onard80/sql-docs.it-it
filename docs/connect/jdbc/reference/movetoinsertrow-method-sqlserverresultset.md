---
title: Metodo moveToInsertRow (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToInsertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3c54bfe-d5b7-4f6e-ae6c-3e8954e5b1c9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cea6bc026cecccdb362b8aef422f3f38ab8ef22
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677169"
---
# <a name="movetoinsertrow-method-sqlserverresultset"></a>Metodo moveToInsertRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sposta il cursore nella riga di inserimento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void moveToInsertRow()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo moveToInsertRow viene specificato dal metodo moveToInsertRow nell'interfaccia ResultSet.  
  
 La posizione corrente del cursore viene memorizzata mentre il cursore viene posizionato sulla riga di inserimento. La riga di inserimento è una riga speciale associata a un set di risultati aggiornabile. Si tratta essenzialmente di un buffer in cui è possibile costruire una nuova riga chiamando i metodi di aggiornamento prima di aggiungere la riga al set di risultati.  
  
 È possibile chiamare solo i metodi updater, getter e [insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md) quando il cursore si trova sulla riga di inserimento. È necessario assegnare un valore a tutte le colonne di un set di risultati ogni volta che questo viene chiamato e prima di chiamare il metodo insertRow. Un metodo di aggiornamento deve essere chiamato prima che uno di richiamo possa essere chiamato su un valore della colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
