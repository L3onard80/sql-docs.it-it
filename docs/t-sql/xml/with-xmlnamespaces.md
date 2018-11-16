---
title: WITH XMLNAMESPACES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WITH_XMLNAMESPACES_TSQL
- WITH XMLNAMESPACES
dev_langs:
- TSQL
helpviewer_keywords:
- adding XML namespaces
- XML namespace declarations [SQL Server]
- clauses [SQL Server], WITH XMLNAMESPACES
- WITH XMLNAMESPACES clause
- declaring XML namespaces
ms.assetid: 3b32662b-566f-454d-b7ca-e247002a9a0b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6123d5e5b5944af3a3495e74541a454a035e91bb
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51695219"
---
# <a name="with-xmlnamespaces"></a>WITH XMLNAMESPACES
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Dichiara uno o più spazi dei nomi XML.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WITH XMLNAMESPACES ( <XML namespace declaration item>  
[ { , <XML namespace declaration item> }...] )   
  
<XML namespace declaration item> ::=  
<xml_namespace_uri> AS <xml_namespace_prefix>  
| <XML default namespace declaration item>  
<xml_namespace_uri> ::= <character string literal>  
```  
  
```  
  
<xml_namespace_prefix> ::= <identifier>  
```  
  
```  
  
<XML default namespace declaration item> ::=  
DEFAULT <xml_namespace_uri>  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *xml_namespace_uri*  
 URI (Uniform Resource Identifier) che identifica lo spazio dei nomi XML da dichiarare. *xml_namespace_uri* è una stringa SQL.  
  
 *xml_namespace_prefix*  
 Specifica un prefisso da mappare e associare al valore dell'URI dello spazio dei nomi in *xml_namespace_uri*. *xml_namespace_prefix* deve essere un identificatore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="remarks"></a>Remarks  
 Se si utilizza la clausola WITH XMLNAMESPACES in un'istruzione che include inoltre un'espressione di tabella comune, è necessario che la clausola WITH XMLNAMESPACES preceda tale espressione.  
  
 Di seguito sono riportate le regole sintattiche generali in caso di utilizzo della clausola WITH XMLNAMESPACES:  
  
-   Ogni dichiarazione di spazio dei nomi XML deve contenere almeno un elemento di dichiarazione dello spazio dei nomi XML predefinito.  
  
-   Ogni prefisso dello spazio dei nomi XML utilizzato deve essere un nome privo di due punti (NCName) in cui il carattere due punti (:) non fa parte del nome.  
  
-   Non è possibile definire un prefisso di spazio dei nomi due volte.  
  
-   I prefissi degli spazi dei nomi XML e gli URI fanno distinzione tra maiuscole e minuscole.  
  
-   Non è possibile dichiarare il prefisso di spazio dei nomi XML `xmlns`.  
  
-   Il prefisso di spazio dei nomi XML `xml` non può essere sovrascritto da uno spazio dei nomi diverso dall'URI dello spazio dei nomi `'https://www.w3.org/XML/1998/namespace'`. A questo URI non può essere assegnato un prefisso diverso.  
  
-   Il prefisso di spazio dei nomi XML `xsi` non può essere dichiarato nuovamente se la direttiva ELEMENTS XSINIL è utilizzata nella query.  
  
-   I valori stringa dell'URI sono codificati in base alla tabella codici delle regole di confronto del database corrente e vengono convertite internamente in Unicode.  
  
-   Gli spazi vuoti dell'URI dello spazio dei nomi XML verranno compressi in base alle regole XSD di compressione degli spazi vuoti usate per **xs:anyURI**. Non viene eseguita alcuna operazione di sostituzione con entità o sostituzione con caratteri nei valori di URI dello spazio dei nomi XML.  
  
-   Nell'URI dello spazio dei nomi XML verrà controllato se sono inclusi caratteri XML 1.0 non validi. Se il controllo ha esito positivo, verrà generato un errore, ad esempio U+0007.  
  
-   In seguito alla compressione di tutti gli spazi vuoti, l'URI dello spazio dei nomi XML non può essere una stringa di lunghezza zero. In caso contrario viene generato un errore per segnalare che un URI dello spazio dei nomi vuoto non è valido.  
  
-   La parola chiave XMLNAMESPACES è riservata nel contesto della clausola WITH.  
  
## <a name="examples"></a>Esempi  
 Per alcuni esempi, vedere [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
