---
title: Copiare lo stato di un facet della gestione basata su criteri in un file XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3cae39c440c86348763b20ae04c70b3ce2ecc181
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127103"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Copiare lo stato di un facet della gestione basata su criteri in un file XML
  In questo argomento verrà descritto come copiare lo stato di un facet della gestione basata su criteri in un file XML in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per copiare lo stato di un facet in un file XML tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Le procedure descritte in questo argomento richiedono l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>Per copiare lo stato di un facet in un file XML  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], su un oggetto istanza, su un database o su un oggetto di database, quindi scegliere **Facet**.  
  
2.  Nel **Visualizza facet -**_object_name_ la finestra di dialogo, fare clic su **Esporta stato corrente come criteri**.  
  
3.  Nella finestra di dialogo **Esporta come criterio** digitare il percorso e il nome del file oppure usare il pulsante Sfoglia (**...**) per trovare il file, quindi digitare il nome del file XML. Per ulteriori informazioni sulle opzioni disponibili in questa finestra di dialogo, vedere [Export As Policy Dialog Box](export-as-policy-dialog-box.md).  
  
4.  Al termine, fare clic su **OK**.  
  
  
