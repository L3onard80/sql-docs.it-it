---
title: Proprietà ErrorControl (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 436c26aa6fffcfc364b47cbfbc8cf3c32e145849
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217579"
---
# <a name="errorcontrol-property-sqlservice-class"></a>Proprietà ErrorControl (classe SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ottiene o imposta la gravità dell'errore se il servizio non viene avviato durante l'avvio del computer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>Parti  
 *object*  
 Oggetto della [classe SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore string che specifica la gravità dell'errore riportato se il servizio non viene avviato durante l'avvio del computer. Nella tabella seguente sono illustrati i possibili valori.  
  
 Ignore  
 L'utente non viene notificato.  
  
 Normale  
 L'utente viene notificato.  
  
 Severe  
 Il sistema viene riavviato con l'ultima configurazione valida nota.  
  
 Critico  
 Il sistema tenta un riavvio con una configurazione valida.  
  
 Unknown  
 La gravità è sconosciuta.  
  
## <a name="remarks"></a>Note  
 Il valore indica l'azione intrapresa dal programma di avvio in caso di errore. Tutti gli errori vengono registrati dal computer.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvio e arresto di servizi](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
