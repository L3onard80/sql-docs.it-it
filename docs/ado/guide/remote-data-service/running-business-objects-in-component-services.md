---
title: Esecuzione di oggetti business in Servizi componenti | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87eab0ac5611b437f6e0cbe1957a4d6e8652c4b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922275"
---
# <a name="running-business-objects-in-component-services"></a>Esecuzione di oggetti business nei Servizi componenti
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Gli oggetti business possono essere file eseguibili (con estensione exe) o librerie a collegamento dinamico (con estensione dll). La configurazione utilizzata per eseguire l'oggetto business varia a seconda che l'oggetto sia un file con estensione dll o exe:  
  
-   Gli oggetti business creati come file con estensione exe possono essere chiamati tramite DCOM. Se questi oggetti business vengono utilizzati tramite Internet Information Services (IIS), sono soggetti a un ulteriore marshalling dei dati, rallentando le prestazioni del client.  
  
-   Gli oggetti business creati come file con estensione dll possono essere utilizzati tramite IIS e quindi anche tramite HTTP. Possono inoltre essere utilizzati su DCOM solo tramite Servizi componenti o tramite Microsoft Transaction Server, se si utilizza Windows NT. Le dll degli oggetti business dovranno essere registrate nel computer server IIS per accedervi tramite IIS. Per informazioni su come configurare una DLL per l'esecuzione su DCOM, vedere la sezione relativa all' [Abilitazione di una dll per l'esecuzione su DCOM](../../../ado/guide/remote-data-service/enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Quando gli oggetti business nel livello intermedio vengono implementati come componenti di Servizi componenti tramite **GetObjectContext**, **secomplete**e **SetAbort**, gli oggetti business possono utilizzare i servizi componenti (o MTS, se si utilizzano gli oggetti di contesto di Windows NT) per mantenere lo stato tra più chiamate del client. Questo scenario è possibile con DCOM, che in genere viene implementato tra client attendibili e server in una rete Intranet. In questo caso, il Servizi Desktop remoto [. L'oggetto DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) e il metodo [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) sul lato client vengono sostituiti dall'oggetto del contesto di transazione e dal metodo **CreateInstance** , forniti dall'interfaccia **ITransactionContext** e implementati da Servizi componenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


