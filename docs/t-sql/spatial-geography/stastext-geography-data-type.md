---
title: STAsText (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STAsText (geography Data Type)
- STAsText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STAsText method
ms.assetid: d3d2635d-ca6c-4205-9d6c-eb939ee314fd
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 9050e529cd851d5b6785e3e167c1c081a2079dd5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68042506"
---
# <a name="stastext-geography-data-type"></a>STAsText (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una rappresentazione WKT (Well-Known Text) OGC (Open Geospatial Consortium) di un'istanza **geography**. Il testo non conterrà alcun valore Z (innalzamento) o M (misura) appartenente all'istanza.  
  
 Questo metodo con tipo di dati **geography** supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STAsText ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **nvarchar(max)**  
  
 Tipo CLR restituito: **SqlChars**  
  
## <a name="remarks"></a>Osservazioni  
 Il tipo OGC di un'istanza **geography** può essere determinato richiamando [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], il set di possibili risultati restituito nel server è stato esteso alle istanze **FullGlobe**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene usato `STAsText()` per creare un'istanza `LineString``geography` da (-122.360, 47.656) a (-122.343, 47.656) dal testo. e viene restituito il risultato in formato testo.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
