---
title: sp_help_spatial_geometry_histogram (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_histogram
- sp_help_spatial_geometry_histogram_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_histogram
ms.assetid: 036aaf61-df3e-40f7-aa4e-62983c5a37bd
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c29562bbdaeff69084547c3505fc84def3a0c668
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51663235"
---
# <a name="sphelpspatialgeometryhistogram-transact-sql"></a>sp_help_spatial_geometry_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Semplifica l'impostazione delle chiavi dei parametri di griglia e del rettangolo di selezione per un indice spaziale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_spatial_geometry_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @xmin = ] 'minx' ]   
     [ , [ @ymin = ] 'miny' ]   
     [ ,.[ @xmax = ] 'maxx' ]  
     [ , [ @ymax = ] 'maxy' ]  
     [ , [ @sample = ] 'sample' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@tabname =**] **'***tabname***'**  
 Nome qualificato o non qualificato della tabella per cui è stato specificato l'indice spaziale.  
  
 Le virgolette sono necessarie solo se viene specificata una tabella qualificata. Nel caso di un nome completo, ovvero contenente un nome di database, il nome del database deve corrispondere a quello del database corrente. *TabName* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@colname =** ] **'***colname***'**  
 Nome della colonna spaziale specificata. *colname* è un **sysname**, non prevede alcun valore predefinito.  
  
 [  **@resolution =** ] **'***risoluzione***'**  
 Risoluzione del rettangolo di selezione. I valori validi sono compresi tra 10 e 5000. *risoluzione* è un **tinyint**, non prevede alcun valore predefinito.  
  
 [  **@xmin =** ] **'***xmin***'**  
 Proprietà del valore minimo di X del rettangolo di selezione. *xmin* è un **float**, non prevede alcun valore predefinito.  
  
 [  **@ymin =** ] **'***ymin***'**  
 Proprietà del valore minimo di Y del rettangolo di selezione. *ymin* è un **float**, non prevede alcun valore predefinito.  
  
 [  **@xmax =** ] **'***xmax***'**  
 Proprietà del valore massimo di X del rettangolo di selezione. *xmax* è un **float**, non prevede alcun valore predefinito.  
  
 [  **@ymax =** ] **'***ymax***'**  
 Proprietà del valore massimo di Y del rettangolo di selezione. *ymax* è un **float**, non prevede alcun valore predefinito.  
  
 [  **@sample =** ] **'***esempio***'**  
 Percentuale della tabella utilizzata. I valori validi sono da 0 a 100. *campione* è un **float**. Il valore predefinito è 100.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Viene restituito un valore di tabella. Nella griglia seguente viene descritto il contenuto delle colonne della tabella.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Rappresenta l'ID univoco di ciascuna cella. Il conteggio inizia da 1.|  
|**cella**|**geometry**|Poligono rettangolare che rappresenta ciascuna cella. La forma della cella è identica alla forma della cella utilizzata per l'indicizzazione spaziale.|  
|**row_count**|**bigint**|Indica il numero di oggetti spaziali che toccano o contengono la cella.|  
  
## <a name="permissions"></a>Permissions  
 Utente deve essere un membro del **pubblica** ruolo. È necessario disporre dell'autorizzazione READ ACCESS per il server e l'oggetto.  
  
## <a name="remarks"></a>Note  
 Nella scheda spaziale di SSMS viene illustrata una rappresentazione grafica dei risultati. È possibile eseguire una query sui risultati rispetto alla finestra spaziale per ottenere un numero approssimativo di risultati. Gli oggetti nella tabella potrebbero riguardare più di una cella, pertanto la somma delle celle potrebbe essere maggiore del numero di oggetti effettivi.  
  
 È possibile che una riga aggiuntiva venga aggiunta al set di risultati contenente il numero di oggetti esterni al rettangolo di selezione o che toccano il bordo dello stesso. Il **cellid** di questa riga è 0 e il **cella** di questa riga contiene una **LineString** che rappresenta il rettangolo di selezione. Questa riga rappresenta l'intero spazio esterno al rettangolo di selezione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente crea una tabella di esempio e quindi chiama **sp_help_spatial_geometry_histogram** sulla tabella.  
  
 `USE AdventureWorksDW2012`  
  
 `GO`  
  
 `-- Set database compatibility for circular arc segments`  
  
 `ALTER DATABASE AdventureWorksDW2012`  
  
 `SET COMPATIBILITY_LEVEL = 110;`  
  
 `GO`  
  
 `-- Create table to execute sp_help_spatial_geometry_histogram on`  
  
 `CREATE TABLE TownSites`  
  
 `(`  
  
 `Location geometry NULL,`  
  
 `SiteName nvarchar(50) NULL`  
  
 `)`  
  
 `GO`  
  
 `-- Insert site data into table`  
  
 `DECLARE @g geometry;`  
  
 `SET @g = geometry::Parse('POINT(0 0)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Booth Map';`  
  
 `SET @g = geometry::Parse('POLYGON((1 1, 1 2, 2 2, 2 1, 1 1))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Town Hall';`  
  
 `SET @g = geometry::Parse('CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-1 0, 0 -1, 1 0),(1 0, 1 2, -1 0)))');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Park';`  
  
 `SET @g = geometry::Parse('CIRCULARSTRING(1 5, 2 2, 5 1)');`  
  
 `INSERT INTO TownSites(Location, SiteName)`  
  
 `SELECT @g, N'Main Road';`  
  
 `-- Call proc to see data within bounding box`  
  
 `EXEC sp_help_spatial_geometry_histogram @tabname = TownSites, @colname = Location, @resolution = 64, @xmin = -2, @ymin = -2, @xmax = 3, @ymax = 3, @sample = 100;`  
  
 `GO`  
  
 `DROP TABLE TownSites;`  
  
 `GO`  
  
## <a name="see-also"></a>Vedere anche  
 [Indice spaziale Stored procedure &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
