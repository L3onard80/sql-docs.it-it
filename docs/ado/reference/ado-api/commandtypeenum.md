---
title: CommandTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a2de155d9c4a61246245b2c7f9c3c73a535994a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919681"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
Specifica la modalità di interpretazione di un argomento di comando.  
  
 È importante convalidare i valori *commandString* forniti dall'utente per evitare che gli utenti dell'applicazione possano inserire comandi potenzialmente pericolosi per l'esecuzione di ADO.  
  
|Costante|valore|Descrizione|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|Non specifica l'argomento tipo di comando.|  
|**adCmdText**|1|Restituisce [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) come definizione testuale di un comando o di una chiamata stored procedure.|  
|**adCmdTable**|2|Restituisce **CommandText** come nome di tabella le cui colonne vengono tutte restituite da una query SQL generata internamente.|  
|**adCmdStoredProc**|4|Restituisce **CommandText** come nome stored procedure.|  
|**adCmdUnknown**|8|Default. Indica che il tipo di comando nella proprietà **CommandText** non è noto.<br /><br /> Quando il tipo di comando non è noto, ADO effettuerà diversi tentativi di interpretare **CommandText**.<br /><br /> -   **CommandText** viene interpretato come definizione testuale di un comando o di una chiamata stored procedure. Questo comportamento è identico a quello di **adCmdText**.<br />-   **CommandText** è il nome di un stored procedure. Questo comportamento è identico a quello di **adCmdStoredProc**.<br />-   **CommandText** viene interpretato come il nome di una tabella. Tutte le colonne vengono restituite da una query SQL generata internamente. Questo comportamento è identico a quello di **adCmdTable**.|  
|**adCmdFile**|256|Restituisce **CommandText** come nome file di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)archiviato in modo permanente. Utilizzato con **Recordset.** [Apre](../../../ado/reference/ado-api/open-method-ado-recordset.md) o [esegue](../../../ado/reference/ado-api/requery-method.md) nuovamente la query.|  
|**adCmdTableDirect**|512|Restituisce **CommandText** come nome di tabella le cui colonne vengono restituite. Utilizzato con **Recordset. Open** o solo la **riesecuzione della query** . Per utilizzare il metodo [Seek](../../../ado/reference/ado-api/seek-method.md) , il **Recordset** deve essere aperto con **adCmdTableDirect**.<br /><br /> Questo valore non può essere combinato con il valore di [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) **adAsyncExecute**.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 Pacchetto: **com. ms. wfc. Data**  
  
|Costante|  
|--------------|  
|AdoEnums. CommandType. Unspecified|  
|AdoEnums. CommandType. TEXT|  
|AdoEnums. CommandType. TABLE|  
|AdoEnums. CommandType. STOREDPROC|  
|AdoEnums. CommandType. UNKNOWN|  
|AdoEnums. CommandType. FILE|  
|AdoEnums. CommandType. TABLEDIRECT|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Proprietà CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Metodo Execute (Command - ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Metodo Execute (Connection - ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Metodo Open (Recordset - ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Metodo Requery](../../../ado/reference/ado-api/requery-method.md)||
