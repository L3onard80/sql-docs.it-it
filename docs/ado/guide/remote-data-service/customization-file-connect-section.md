---
title: Sezione connessione file di personalizzazione | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connect section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1de3710590cf49de30ff8e79a6ff829b124c42dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922801"
---
# <a name="customization-file-connect-section"></a>Sezione sulla connessione del file di personalizzazione
Il comportamento predefinito del gestore è negare tutte le connessioni. La sezione **Connect** specifica le eccezioni al comportamento. Se, ad esempio, tutte le sezioni di **connessione** sono assenti o vuote, per impostazione predefinita non è possibile effettuare alcuna connessione.  
  
 La sezione **Connect** può contenere:  
  
-   Una voce di accesso predefinita che specifica le operazioni di lettura e scrittura predefinite consentite in questa connessione. Se nella sezione non è presente alcuna voce di accesso predefinita, la sezione verrà ignorata.  
  
-   Nuova stringa di connessione che sostituisce la stringa di connessione del client.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
 Una voce di accesso predefinita è nel formato seguente:  
  
```console
  
Access=  
accessRight  
  
```  
  
 Una voce della stringa di connessione di sostituzione è nel formato seguente:  
  
```console
  
Connect=  
connectionString  
  
```  
  
## <a name="remarks"></a>Osservazioni  
  
|Parte|Descrizione|  
|----------|-----------------|  
|**Connettere**|Stringa letterale che indica che si tratta di una voce della stringa di connessione.|  
|**_connectionString_**|Stringa che sostituisce l'intera stringa di connessione del client.|  
|**Accedere**|Stringa letterale che indica che si tratta di una voce di accesso.|  
|**_accessRight_**|Uno dei seguenti diritti di accesso:<br /><br /> -   **NoAccess** : l'utente non può accedere all'origine dati.<br />-   **ReadOnly** -l'utente può leggere l'origine dati.<br />-   **ReadWrite** -l'utente può leggere o scrivere nell'origine dati.|  
  
 Se si desidera consentire qualsiasi connessione (in effetti, disabilitando il comportamento predefinito del gestore), impostare la voce di accesso nella sezione **Connetti predefinito** su `Access=ReadWrite`ed eliminare o impostare come commento qualsiasi altra sezione dell' _identificatore_ di **connessione** .  
  
## <a name="see-also"></a>Vedere anche  
 [Sezione log file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Sezione SQL del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Sezione utenti del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di datafactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni client obbligatorie](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sul file di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)



