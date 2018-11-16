---
title: Visualizzare un elenco di database in un'istanza di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- current databases
- databases currently on server [SQL Server]
- database list [SQL Server]
- viewing database list
- displaying database list
- databases [SQL Server], viewing
- servers [SQL Server], databases listed on
- listing databases
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 15a9659ce024aceb016d0140893e401500e0fe6d
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2018
ms.locfileid: "51557878"
---
# <a name="view-a-list-of-databases-on-an-instance-of-sql-server"></a>Visualizzare un elenco di database in un'istanza di SQL Server
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In questo argomento si illustra come visualizzare un elenco di database in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per visualizzare un elenco di database in un'istanza di SQL Server utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Se il chiamante di **sys.databases** non è il proprietario del database e il database non è **master** o **tempdb**, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono ALTER ANY DATABASE o VIEW ANY DATABASE a livello di server oppure l'autorizzazione CREATE DATABASE nel database **master** . Il database a cui è connesso il chiamante può essere sempre visualizzato in **sys.databases**.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a>Per visualizzare un elenco di database in un'istanza di SQL Server  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espandere questa istanza.  
  
2.  Per visualizzare un elenco di tutti i database dell'istanza, espandere **Database**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a>Per visualizzare un elenco di database in un'istanza di SQL Server  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. In questo esempio viene restituito un elenco di database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nell'elenco sono inclusi i nomi dei database, i relativi ID di database, nonché le date di creazione dei database.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di database e file &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  
