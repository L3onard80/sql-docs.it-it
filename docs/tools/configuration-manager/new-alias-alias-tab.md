---
title: Nuovo alias (scheda Alias)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: d691369d3df437cb8312d66f521eb48c20212ca8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "75306436"
---
# <a name="new-alias-alias-tab"></a>Nuovo alias (scheda Alias)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Un alias rappresenta un nome alternativo che può essere utilizzato per stabilire una connessione. L'alias incapsula gli elementi necessari di una stringa di connessione e li espone con un nome scelto dall'utente. La pagina **Alias** della finestra di dialogo **Nuovo alias** consente di specificare gli elementi della stringa di connessione per un alias. Per modificare la stringa di connessione di un alias esistente, vedere [Proprietà &#60;Alias&#62; &#40;scheda Alias&#41;](../../tools/configuration-manager/alias-properties-alias-tab.md).  
  
 Non è necessario completare tutti i valori nella griglia **Proprietà** . Le combinazioni valide variano a seconda del protocollo selezionato. Per esempi di combinazioni valide, vedere gli argomenti elencati di seguito.  
  
 **Nome alias**  
 Nome o alias che si desidera utilizzare per fare riferimento alla connessione.  
  
 **Nome pipe** / **Numero porta**  
 Elementi aggiuntivi della stringa di connessione. Il nome di questa casella varia a seconda del protocollo selezionato.  
  
 **Protocollo**  
 Protocollo utilizzato per la connessione.  
  
 **Server**  
 Nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui si esegue la connessione.  
  
## <a name="when-to-use-an-alias"></a>Situazioni in cui utilizzare un alias  
 Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si connette a un'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mediante il protocollo **Shared Memory** e a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un altro computer mediante **TCP/IP** o **Named Pipes**. Creare un alias quando si utilizza TCP/IP o Named Pipes e si desidera fornire una stringa di connessione personalizzata o quando si desidera utilizzare un nome diverso da quello del server per la connessione.  
  
### <a name="examples"></a>Esempi  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in attesa sulla porta TCP/IP 1433 predefinita, pertanto si desidera creare una stringa di connessione con un numero di porta diverso.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in attesa sulla porta named pipe predefinita, pertanto si desidera creare una stringa di connessione con un nome di pipe diverso.  
  
-   Un'applicazione prevede di connettersi a un database nel server denominato `ACCT`, ma tale database è stato consolidato come istanza denominata `ACCT` nel server `CENTRAL`. Non è semplice modificare l'applicazione. Creare un alias denominato `ACCT`, con una stringa di connessione che punta a `CENTRAL\ACCT`.  
  
## <a name="creating-a-valid-connection-string"></a>Creazione di una stringa di connessione valida  
 Per una descrizione ed esempi di combinazioni valide di proprietà di alias, vedere gli argomenti seguenti:  
  
-   [Creazione di una stringa di connessione valida mediante il protocollo di memoria condivisa](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [Creazione di una stringa di connessione valida con TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [Creazione di una stringa di connessione valida tramite named pipe](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
