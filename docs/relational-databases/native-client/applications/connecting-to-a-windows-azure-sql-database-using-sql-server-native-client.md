---
title: Connessione a un Database SQL di Windows Azure utilizza SQL Server Native Client | Documenti di Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 92184be8a4195ce5b246cd957ba675fcb2fe43a6
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51665211"
---
# <a name="connecting-to-a-windows-azure-sql-database-using-sql-server-native-client"></a>Connessione a un database SQL di Windows Azure utilizzando SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Per un esempio che illustra come connettersi a un [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, vedere [Development: procedure (Windows Azure, SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Problemi noti correlati alla connessione a un database SQL  
 Di seguito sono elencati i problemi noti che si verificano durante la connessione a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:  
  
-   Una connessione effettuata con **SQLBrowseConnect** può essere respinta qualora **SQLBrowseConnect** viene utilizzato in più fasi.  Ad esempio, se il nome del driver viene inviato nella prima chiamata, il server e le credenziali (utente e password) inviati nella seconda chiamata, la connessione e l'impostazione di un linguaggio e di un nome di database hanno luogo nella terza chiamata.  Durante la terza chiamata [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client emetterà un'istruzione USE per modificare i database. Poiché l'istruzione USE non è supportata in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], viene generato l'errore seguente:  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
