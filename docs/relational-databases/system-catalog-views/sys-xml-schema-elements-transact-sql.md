---
title: sys. xml_schema_elements (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_elements
- sys.xml_schema_elements_TSQL
- xml_schema_elements
- xml_schema_elements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_elements catalog view
ms.assetid: 190ed0cd-0c5e-4607-9db4-9e77cacf17d7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d43f30f15502a41882190dcdd19984d9ec042d4a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037389"
---
# <a name="sysxml_schema_elements-transact-sql"></a>sys.xml_schema_elements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni componente XML Schema che è un tipo, **symbol_space** di **E**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate>**|**--**|Eredita le colonne da [sys. xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_default_fixed**|**bit**|1 = Il valore predefinito è un valore fisso. Questo valore non può essere sostituito in un'istanza XML.<br /><br /> 0 = Il valore predefinito non è un valore fisso per l'elemento (impostazione predefinita).|  
|**is_abstract**|**bit**|1 = L'elemento è di tipo abstract e non può essere utilizzato in un documento dell'istanza. Un membro del gruppo di sostituzione dell'elemento deve essere incluso nel documento dell'istanza.<br /><br /> 0 = L'elemento non è abstract (impostazione predefinita).|  
|**is_nillable**|**bit**|1 = L'elemento ammette valori Null.<br /><br /> 0 = L'elemento non ammette valori Null (predefinito)|  
|**must_be_qualified**|**bit**|1 = L'elemento deve essere qualificato come spazio dei nomi in modo esplicito.<br /><br /> 0 = L'elemento può essere qualificato come spazio dei nomi in modo implicito (predefinito)|  
|**is_extension_blocked**|**bit**|1 = La sostituzione con un'istanza di un tipo di estensione è bloccata.<br /><br /> 0 = La sostituzione con il tipo di estensione è consentita (predefinito)|  
|**is_restriction_blocked**|**bit**|1 = La sostituzione con un'istanza di un tipo di restrizione è bloccata.<br /><br /> 0 = La sostituzione con il tipo di restrizione è consentita (predefinito)|  
|**is_substitution_blocked**|**bit**|1 = L'istanza di un gruppo di sostituzione non può essere utilizzata.<br /><br /> 0 = La sostituzione con un gruppo di sostituzione è consentita (predefinito)|  
|**is_final_extension**|**bit**|1 = La sostituzione con un'istanza di un tipo di estensione non è consentita.<br /><br /> 0 = La sostituzione in un'istanza di un tipo di estensione è consentita (predefinito)|  
|**is_final_restriction**|**bit**|1 = La sostituzione con un'istanza di un tipo di restrizione non è consentita.<br /><br /> 0 = La sostituzione in un'istanza di un tipo di restrizione è consentita (predefinito)|  
|**default_value**|**nvarchar (4000)**|Valore predefinito dell'elemento. È NULL se non viene specificato un valore predefinito.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML Schema &#40;viste del catalogo&#41; di sistema di tipo XML &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
