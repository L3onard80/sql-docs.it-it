---
title: Proprietà DefaultDatabase | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c78dfdc476dc9dcf599fcfe7cb87bd5e1a39d281
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919159"
---
# <a name="defaultdatabase-property"></a>Proprietà DefaultDatabase
Indica il database predefinito per un oggetto [Connection](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta o restituisce un valore **stringa** che restituisce il nome di un database disponibile dal provider.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare la proprietà **DefaultDatabase** per impostare o restituire il nome del database predefinito in un oggetto **connessione** specifico.  
  
 Se è presente un database predefinito, le stringhe SQL possono utilizzare una sintassi non qualificata per accedere agli oggetti in tale database. Per accedere agli oggetti in un database diverso da quello specificato nella proprietà **DefaultDatabase** , è necessario qualificare i nomi degli oggetti con il nome del database desiderato. Al momento della connessione, il provider scriverà le informazioni predefinite sul database nella proprietà **DefaultDatabase** . Alcuni provider consentono un solo database per connessione, nel qual caso non è possibile modificare la proprietà **DefaultDatabase** .  
  
 Alcune origini dati e i provider potrebbero non supportare questa funzionalità e possono restituire un errore o una stringa vuota.  
  
> [!NOTE]
>  **Utilizzo servizio dati remoto** Questa proprietà non è disponibile in un oggetto **connessione** sul lato client.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà provider e DefaultDatabase (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Esempio delle proprietà Provider e DefaultDatabase (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
