---
title: Dati spaziali (SQL Server) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ce6471d2a8f8adc5a04356d1b075437011f036d2
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018716"
---
# <a name="spatial-data-sql-server"></a>Dati spaziali (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  I dati spaziali rappresentano informazioni sulla posizione fisica e sulla forma di oggetti geometrici. Questi oggetti possono essere posizioni dei punti oppure oggetti più complessi ad esempio paesi, strade o laghi.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta due tipi di dati spaziali: il tipo di dati **geometry** e il tipo di dati **geography** .  
  
-   Il tipo **geometry** rappresenta i dati in un sistema di coordinate euclideo (piano).  
  
-   Il tipo **geography** rappresenta i dati in un sistema di coordinate terrestri.  
  
 Entrambi i tipi di dati sono implementati come tipi di dati Common Language Runtime (CLR) .NET in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Per una descrizione dettagliata ed esempi delle nuove funzionalità spaziali di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], scaricare il white paper [New Spatial Features in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407)(Nuove funzionalità spaziali in SQL Server 2012).  
  
##  <a name="reltasks"></a> Attività correlate  
 [Creazione, costruzione e query di istanze geometry](../../relational-databases/spatial/create-construct-and-query-geometry-instances.md)  
 Vengono descritti i metodi da utilizzare con le istanze del tipo di dati geometry.  
  
 [Creare, Costruire e Istanze geografiche di Query](../../relational-databases/spatial/create-construct-and-query-geography-instances.md)  
 Vengono descritti i metodi che è possibile utilizzare con istanze del tipo di dati geography.  
  
 [Query dei dati spaziali per Nearest Neighbor](../../relational-databases/spatial/query-spatial-data-for-nearest-neighbor.md)  
 Viene descritto il modello di query utilizzato per trovare gli oggetti spaziali più vicini a un oggetto spaziale specifico.  
  
 [Creazione, modifica ed eliminazione di indici spaziali](../../relational-databases/spatial/create-modify-and-drop-spatial-indexes.md)  
 Fornisce informazioni sulla creazione, la modifica e il rilascio di un indice spaziale.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)  
 Sono stati introdotti i tipi di dati spaziali.  
  
-   [Punto](../../relational-databases/spatial/point.md)  
  
-   [LineString](../../relational-databases/spatial/linestring.md)  
  
-   [CircularString](../../relational-databases/spatial/circularstring.md)  
  
-   [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
  
-   [Poligono](../../relational-databases/spatial/polygon.md)  
  
-   [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  
  
-   [MultiPoint](../../relational-databases/spatial/multipoint.md)  
  
-   [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
  
-   [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
  
-   [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  
  
 [Panoramica degli indici spaziali](../../relational-databases/spatial/spatial-indexes-overview.md)  
 Sono stati introdotti indici spaziali e vengono descritti gli schemi a mosaico.  
  
  
