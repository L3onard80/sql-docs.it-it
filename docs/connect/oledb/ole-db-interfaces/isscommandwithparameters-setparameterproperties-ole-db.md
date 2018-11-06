---
title: 'Isscommandwithparameters:: Setparameterproperties (OLE DB) | Microsoft Docs'
description: ISSCommandWithParameters::SetParameterProperties (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 8298de4362b0c38b56d56d7cbd46822a53b4ddbb
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030048"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>ISSCommandWithParameters::SetParameterProperties (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Imposta le proprietà dei parametri per i singoli parametri in base al numero ordinale oppure imposta proprietà dei parametri bulk specificando una matrice di strutture SSPARAMPROPS.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Argomenti  
 *cParams*[in]  
 Numero di strutture SSPARAMPROPS nella matrice *rgParamProperties*. Se questo numero è zero, **ISSCommandWithParameters::SetParameterProperties** eliminerà tutte le proprietà che possono essere state specificate per i parametri nel comando.  
  
 *rgParamProperties*[in]  
 Matrice di strutture SSPARAMPROPS da impostare.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Il metodo **ISSCommandWithParameters::SetParameterProperties** restituisce gli stessi codici di errore del metodo **ICommandProperties::SetProperties** OLE DB di base.  
  
## <a name="remarks"></a>Remarks  
 L'impostazione delle proprietà del parametro con questo metodo è consentita per i singoli parametri in base al numero ordinale oppure con una sola chiamata a **ISSCommandWithParameters::SetParameterProperties** dopo che la struttura SSPARAMPROPS è stata compilata dalla matrice della proprietà.  
  
 Il metodo **SetParameterInfo** deve essere chiamato prima del metodo **ISSCommandWithParameters::SetParameterProperties**. Se si chiama `SetParameterProperties(0, NULL)`, si cancellano tutte le proprietà di parametro specificate, mentre se si chiama `SetParameterInfo(0,NULL,NULL)`, si cancellano tutte le informazioni di parametro che includono le proprietà che potrebbero essere associate a un parametro.  
  
 Se si chiama **ISSCommandWithParameters::SetParameterProperties** per specificare le proprietà per un parametro che non è del tipo DBTYPE_XML o DBTYPE_UDT viene restituito DB_E_ERRORSOCCURRED o DB_S_ERRORSOCCURRED e il campo *dwStatus* di tutte le matrici DBPROP contenute nella struttura SSPARAMPROPS per quel parametro viene contrassegnato con DBPROPSTATUS_NOTSET. È necessario attraversare la matrice DBPROP di ogni proprietà DBPROPSET contenuta nella struttura SSPARAMPROPS per individuare il parametro al quale DB_E_ERRORSOCCURRED o DB_S_ERRORSOCCURRED fa riferimento.  
  
 Se viene chiamato **ISSCommandWithParameters::SetParameterProperties** per specificare le proprietà di parametri le cui informazioni non sono state ancora impostate con **SetParameterInfo**, il provider restituisce E_UNEXPECTED con il messaggio di errore seguente:  
  
 Impossibile chiamare il metodo SetParameterProperties per i parametri specificati senza chiamare prima il metodo SetParameterInfo. È necessario impostare le informazioni sui parametri prima di impostare le proprietà dei parametri stessi.  
  
 Se la chiamata a **ISSCommandWithParameters::SetParameterProperties** contiene alcuni parametri per i quali le informazioni sono state impostate e alcuni parametri per i quali non sono state impostate, le proprietà dwStatus nella struttura DBPROPSET del set di proprietà SSPARAMPROPS verranno restituite con DBSTATUS_NOTSET.  
  
 La struttura SSPARAMPROPS viene definita nel modo seguente:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Miglioramenti apportati al motore di database a partire da [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] consentire isscommandwithparameters:: Setparameterproperties ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da isscommandwithparameters:: Setparameterproperties nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Metadata Discovery](../../oledb/features/metadata-discovery.md).  
  
|Membro|Descrizione|  
|------------|-----------------|  
|*iOrdinal*|Numero ordinale del parametro passato.|  
|*cPropertySets*|Numero di strutture DBPROPSET in *rgPropertySets*.|  
|*rgPropertySets*|Puntatore alla memoria nel quale restituire una matrice di strutture DBPROPSET.|  
  
## <a name="see-also"></a>Vedere anche  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
