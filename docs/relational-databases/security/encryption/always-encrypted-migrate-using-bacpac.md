---
title: Esportare e importare database usando Always Encrypted | Microsoft Docs
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1f2f44a6cf1172b779160d4ee17e584c7a7b2452
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "73595806"
---
# <a name="export-and-import-databases-using-always-encrypted"></a>Esportare e importare database usando Always Encrypted 
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Questo articolo descrive come esportare e importare database contenenti colonne protette con [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md).

Quando si esporta un database, tutti i dati archiviati in colonne crittografate vengono recuperati dal database in formato crittografato (ciphertext) e inseriti nel file [BACPAC](../../data-tier-applications/data-tier-applications.md) risultante. Il file BACPAC risultante contiene anche i metadati per le chiavi di Always Encrypted.

Quando si importa il file BACPAC in un database, i dati crittografati del file BACPAC vengono caricati nel database e i metadati delle chiavi di Always Encrypted vengono ricreati. 

Se si usa un'applicazione configurata per eseguire query in colonne crittografate archiviate nel database di origine (quello esportato), non sono necessarie operazioni particolari per consentire all'applicazione di eseguire query sui dati crittografati nel database di destinazione, perché le chiavi presenti in entrambi i database sono le stesse.

Per informazioni dettagliate su come esportare e importare un database, vedere:
- [Esportazione di un'applicazione livello dati](../../data-tier-applications/export-a-data-tier-application.md)
- [Importare un file BACPAC per creare un nuovo database utente](../../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)
- [Esportare un database SQL di Azure in un file BACPAC](https://docs.microsoft.com/azure/sql-database/sql-database-export)
- [Importare un file BACPAC in un database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-import)
- [SqlPackage.exe](../../../tools/sqlpackage.md)

## <a name="permissions-for-migrating-databases-with-encrypted-columns"></a>Autorizzazioni per la migrazione di database con colonne crittografate

Sono necessarie le autorizzazioni *ALTER ANY COLUMN MASTER KEY* e *ALTER ANY COLUMN ENCRYPTION KEY* per il database di origine. Per il database di destinazione sono necessarie le autorizzazioni *ALTER ANY COLUMN MASTER KEY*, *ALTER ANY COLUMN ENCRYPTION KEY*, *VIEW ANY COLUMN MASTER KEY DEFINITION* e *VIEW ANY COLUMN ENCRYPTION DEFINITION*

Non è invece necessario avere i diritti di accesso alle chiavi master della colonna configurate per le colonne crittografate, poiché durante le operazioni di esportazione e importazione i dati rimangono crittografati.

## <a name="next-steps"></a>Passaggi successivi
- [Sviluppare applicazioni usando Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>Vedere anche
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Eseguire il backup e il ripristino di database usando Always Encrypted](always-encrypted-migrate-using-backup-restore.md)
- [Eseguire la migrazione di dati da o verso colonne usando Always Encrypted con l'Importazione/Esportazione guidata SQL Server](always-encrypted-migrate-using-import-export-wizard.md)
- [Caricamento bulk di dati crittografati in colonne tramite Always Encrypted](migrate-sensitive-data-protected-by-always-encrypted.md)