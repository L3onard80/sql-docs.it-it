---
title: sys. http_endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.http_endpoints
- http_endpoints
- sys.http_endpoints_TSQL
- http_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.http_endpoints catalog view
ms.assetid: 16f59695-ecd9-457e-8874-055af63f8ea7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 41ca717399a3cd86f2137de6ae474d89e3eb819e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122727"
---
# <a name="syshttp_endpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni endpoint creato nel server, che utilizza il protocollo HTTP.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**< colonne ereditate>**||Eredita le colonne da [sys. endpoints &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**sito**|**nvarchar(128)**|Nome del computer host per il sito, come specificato nell'opzione SITE =.|  
|**url_path**|**nvarchar(4000)**|Parte del percorso dell'URL per l'endpoint HTTP, come specificato nell'opzione PATH=.|  
|**is_clear_port_enabled**|**bit**|1 = Porta non protetta abilitata con l'opzione PORT = CLEAR.|  
|**clear_port**|**int**|Numero di porta specificato nell'opzione CLEAR PORT =.<br /><br /> NULL = Non specificata.|  
|**is_ssl_port_enabled**|**bit**|1 = Porta SSL abilitata con l'opzione PORT = SSL.|  
|**ssl_port**|**int**|Valore del numero di porta specificato nell'opzione SSL PORT =.<br /><br /> NULL = Non specificata.|  
|**is_anonymous_enabled**|**bit**|1 = Accesso anonimo abilitato con l'opzione AUTHENTICATION = ANONYMOUS.|  
|**is_basic_auth_enabled**|**bit**|1 = Autenticazione di base abilitata con l'opzione AUTHENTICATION = BASIC.|  
|**is_digest_auth_enabled**|**bit**|1 = Autenticazione digest abilitata con l'opzione AUTHENTICATION = DIGEST.|  
|**is_kerberos_auth_enabled**|**bit**|1 = Autenticazione integrata abilitata con l'opzione AUTHENTICATION = KERBEROS.|  
|**is_ntlm_auth_enabled**|**bit**|1 = Autenticazione integrata abilitata con l'opzione AUTHENTICATION = NTLM.|  
|**is_integrated_auth_enabled**|**bit**|1 = Autenticazione integrata abilitata con l'opzione AUTHENTICATION = INTEGRATED.|  
|**authorization_realm**|**nvarchar(128)**|Hint restituito al client nell'ambito della richiesta di autenticazione HTTP DIGEST. Valore dell'opzione AUTH REALM.<br /><br /> NULL se non specificato o se l'autenticazione DIGEST non è abilitata.|  
|**default_logon_domain**|**nvarchar(128)**|Dominio di accesso predefinito se si abilita l'autenticazione BASIC. Valore dell'opzione DEFAULT LOGON DOMAIN.<br /><br /> NULL se non specificato o se l'autenticazione BASIC non è abilitata.|  
|**is_compression_enabled**|**bit**|1 = Opzione COMPRESSION = ENABLED impostata.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo degli endpoint &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
