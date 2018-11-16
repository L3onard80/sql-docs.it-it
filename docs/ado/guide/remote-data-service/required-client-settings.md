---
title: Le impostazioni Client necessarie | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cec3e79e3d37f064cb742588519a374737e01319
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558218"
---
# <a name="required-client-settings"></a>Impostazioni obbligatorie dei client
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più incluse nel sistema operativo Windows (vedere Windows 8 e [indicazioni sulla compatibilità di Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) per altri dettagli). I componenti client di servizi desktop remoto verranno rimosso in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che usano servizi desktop remoto devono eseguire la migrazione a [di WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Specificare le impostazioni seguenti per usare una classe personalizzata **DataFactory** gestore.  
  
-   Specificare "Provider = Remote MS" nel [connessione ADO (Object)](../../../ado/reference/ado-api/connection-object-ado.md) oggetto [Provider di proprietà (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) proprietà o i **connessione** stringa di connessione dell'oggetto "**Provider**= "parola chiave.  
  
-   Impostare il [proprietà CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient**.  
  
-   Specificare il nome del gestore da utilizzare nel [oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto **gestore** proprietà o i [Recordset ADO (Object)](../../../ado/reference/ado-api/recordset-object-ado.md) stringa di connessione dell'oggetto " **Gestore**= "parola chiave. (Non è possibile impostare il gestore di **connessione** oggetto stringa di connessione.)  
  
 Servizi Desktop remoto fornisce un gestore predefinito nel server denominato **MSDFMAP. Gestore**. (Il file di personalizzazione predefinito denominato MSDFMAP. INI).  
  
 **Esempio**  
  
 Si supponga che le sezioni seguenti **MSDFMAP. INI** e il nome dell'origine dati AdvWorks, sono stati definiti in precedenza:  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 I seguenti frammenti di codice sono scritti in Visual Basic:  
  
## <a name="rdsdatacontrol-version"></a>SERVIZI DESKTOP REMOTO. Versione DataControl  
  
```vb
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "https://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Versione del recordset  
  
```vb
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Specificare il [proprietà del gestore (Servizi Desktop remoto)](../../../ado/reference/rds-api/handler-property-rds.md) proprietà o una parola chiave; il [Provider di proprietà (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) proprietà o una parola chiave; e il *CustomerById* e  *CustomerDatabase* gli identificatori. Quindi aprire il **Recordset** oggetto  
  
 RS. Aprire "CustomerByID (4)", "gestore = MSDFMAP. Gestore;"& _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sezione sulla connessione del File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Sezione SQL del File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Sezione UserList del File personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni Client richieste](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sul file di personalizzazione.](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

