---
title: Supporto dei tipi di parametri con valori di tabella OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69f7994848d02d6e5e0036aaf132e6294f8d5d90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761629"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Supporto del tipo di parametro con valori di tabella OLE DB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In questo argomento viene descritto il supporto del tipo OLE DB per i parametri con valori di tabella.  
  
## <a name="table-valued-parameter-rowset-object"></a>Oggetto set di righe di parametri con valori di tabella  
 È possibile creare un oggetto set di righe specifico per i parametri con valori di tabella. Per creare l'oggetto set di righe di parametri con valori di tabella, utilizzare ITableDefinitionWithConstraints:: CreateTableWithConstraints o IOpenRowset:: OpenRowset. A questo scopo, impostare il membro *eKind* del parametro *pTableID* su DBKIND_GUID_NAME e specificare CLSID_ROWSET_INMEMORY come membro *guid*. Il nome del tipo di server per il parametro con valori di tabella deve essere specificato nel membro *pwszName* di *pTableID* quando si usa IOpenRowset:: OPENROWSET. L'oggetto set di righe di parametri con valori di tabella si comporta come un normale oggetto del provider OLE DB di SQL Server Native Client.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a>DBTYPE_TABLE  
 Un nuovo tipo, DBTYPE_TABLE, rappresenta un tipo di tabella. Tale tipo specifica i parametri con valori di tabella nelle varie interfacce OLE DB in cui è richiesto un oggetto DBTYPE.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 Il formato di DBTYPE_TABLE è identico a quello di DBTYPE_IUNKNOWN. Si tratta di un puntatore a un oggetto nel buffer di dati. Per una specifica completa nelle associazioni, il consumer inserisce dati nel buffer DBOBJECT, con *iid* impostato su una delle interfacce dell'oggetto set di righe (IID_IRowset). Se non viene specificato alcun oggetto DBOBJECT nelle associazioni, si presuppone che l'oggetto sia IID_IRowset.  
  
 Le conversioni da e verso DBTYPE_TABLE per altri tipi non sono supportate. IConvertType::CanConvert restituisce S_FALSE per la conversione non supportata per tutte le richieste diverse dalla conversione da DBTYPE_TABLE a DBTYPE_TABLE. In questa situazione si presuppone l'uso di DBCONVERTFLAGS_PARAMETER sull'oggetto Command.  
  
## <a name="methods"></a>Metodi  
 Per informazioni sui metodi di OLE DB che supportano i parametri con valori di tabella, vedere [OLE DB supporto dei tipi di parametro con valori di tabella &#40;&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Proprietà  
 Per informazioni sulle proprietà di OLE DB che supportano i parametri con valori di tabella, vedere [OLE DB tipo di parametro con valori di tabella supporto di &#40;proprietà&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri con valori di tabella &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Usare parametri con valori di tabella &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
