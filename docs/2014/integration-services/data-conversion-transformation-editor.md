---
title: Editor trasformazione Conversione dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5346c808c7d724ae630bb3dd25016a9977af363e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66060047"
---
# <a name="data-conversion-transformation-editor"></a>Editor trasformazione Conversione dati
  Usare la finestra di dialogo **Editor trasformazione Conversione dati** per selezionare le colonne da convertire e i tipi di dati in cui convertire la colonna e impostare gli attributi di conversione.  
  
> [!NOTE]  
>  La `FastParse` proprietà delle colonne di output della trasformazione Conversione dati non è disponibile nell' **Editor trasformazione Conversione dati**, ma può essere impostata tramite il **Editor avanzato**. Per altre informazioni su questa proprietà, vedere la sezione relativa alla trasformazione Conversione dati in [Proprietà personalizzate delle trasformazioni](data-flow/transformations/transformation-custom-properties.md).  
  
 Per sapere di più sulla trasformazione conversione dati, vedere [Trasformazione Conversione dati](data-flow/transformations/data-conversion-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Consente di selezionare le colonne da convertire utilizzando le caselle di controllo. Le selezioni effettuate determinano l'aggiunta delle colonne di input nella tabella sottostante.  
  
 **Colonna di input**  
 Consente di selezionare le colonne da convertire nell'elenco delle colonne di input disponibili. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo descritte in precedenza.  
  
 **Alias di output**  
 Consente di digitare un alias per ogni nuova colonna. L'impostazione predefinita è `Copy of` seguita dal nome della colonna di input. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
 **Tipo di dati**  
 Consente di selezionare un tipo di dati disponibile nell'elenco. Per altre informazioni, vedere [Tipi di dati di Integration Services](data-flow/integration-services-data-types.md).  
  
 **Length**  
 Consente di selezionare la lunghezza della colonna per dati di tipo stringa.  
  
 **Precision**  
 Consente di impostare la precisione per dati numerici.  
  
 **Scalabilità**  
 Consente di impostare la scala per dati numerici.  
  
 **Tabella codici**  
 Consente di selezionare la tabella codici appropriata per le colonne di tipo DT_STR.  
  
 **Configurare l'output degli errori**  
 Consente di indicare come gestire gli errori tramite la finestra di dialogo [Configura output errori](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Conversione di dati in un tipo di dati diverso utilizzando la trasformazione Conversione dati](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
