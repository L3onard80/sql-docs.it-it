---
title: Modalità di conversione di FOR JSON dei tipi di dati SQL Server in tipi di dati JSON (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/07/2016
ms.prod: sql
ms.reviewer: douglasl
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR JSON, data type conversion
ms.assetid: da356f06-efd0-4ea3-8157-77395bf790d7
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 80bf0fa78d101f853b04793c1084a69a6f6bdd00
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51661179"
---
# <a name="how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server"></a>Modalità di conversione di FOR JSON dei tipi di dati SQL Server in tipi di dati JSON (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  La clausola **FOR JSON** usa le regole seguenti per convertire i tipi di dati SQL Server in tipi JSON nell'output JSON.  
  
|Category|Tipo di dati di SQL Server|Tipo di dati JSON|  
|--------------|--------------|---------------|  
|Tipi stringa e carattere|char, nchar, varchar, nvarchar|string|  
|Tipi numerici|int, bigint, float, decimal, numeric|number|  
|Tipo bit|bit|Booleano (true o false)|  
|Tipi data e ora|date, datetime, datetime2, time, datetimeoffset|string|  
|Tipi binari|varbinary, binary, image, timestamp, rowversion|Stringa con codifica BASE64|  
|Tipi CLR|geometry, geography, altri tipi CLR|Non supportato. Questi tipi restituiscono un errore.<br /><br /> Nell'istruzione SELECT usare CAST o CONVERT, oppure una proprietà o un metodo CLR, per convertire i dati di origine in un tipo di dati SQL Server convertibile correttamente in un tipo JSON. Usare ad esempio **STAsText()** per il tipo geometry o **ToString()** per qualsiasi tipo CLR. Il tipo del valore di output JSON è quindi derivato dal tipo restituito della conversione che si usa nell'istruzione SELECT.|  
|Altri tipi|uniqueidentifier, money|string|  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Altre informazioni su JSON in SQL Server e nel database SQL di Azure  
  
### <a name="microsoft-blog-posts"></a>Post del blog Microsoft  
  
Per soluzioni specifiche, casi d'uso e indicazioni, vedere questi [post del blog sul supporto JSON integrato](https://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/) in SQL Server e nel database SQL di Azure.  

### <a name="microsoft-videos"></a>Video Microsoft

Per un'introduzione visiva al supporto JSON predefinito in SQL Server e nel database SQL di Azure, vedere i video seguenti:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support) (SQL Server 2016 e supporto JSON)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database) (Uso di JSON in SQL Server 2016 e nel database SQL di Azure)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds) (JSON come ponte tra NoSQL e gli ambienti relazionali)
  
## <a name="see-also"></a>Vedere anche  
 [Formattare i risultati delle query in formato JSON con FOR JSON &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)  
  
  
