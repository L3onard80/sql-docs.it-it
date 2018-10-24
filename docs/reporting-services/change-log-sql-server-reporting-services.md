---
title: Log delle modifiche per SQL Server Reporting Services (SSRS) 2017 e versioni successive | Microsoft Docs
ms.date: 08/31/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: casualoak
ms.author: edugonz
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 2fa40e17381622862ea2a5b5e6fac594f6a42f6a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728776"
---
# <a name="change-log-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Log delle modifiche per SQL Server Reporting Services (SSRS) 2017 e versioni successive

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)] 

Questo articolo descrive le modifiche apportate in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. 

## <a name="sql-server-2017-reporting-services"></a>SQL Server 2017 Reporting Services 

### <a name="version-140600906-released-september-12-2018"></a>Versione 14.0.600.906, data di rilascio: 12 settembre 2018

È stato risolto il bug seguente:

- Il cookie di autenticazione personalizzata non restituisce le informazioni cookie corrette

### <a name="version-140600892-released-august-31-2018"></a>Versione 14.0.600.892, data di rilascio: 31 agosto 2018

Sono stati corretti i bug seguenti:

- La presenza di una casella di testo all'interno di un rettangolo impedisce l'ingrandimento in verticale quando rc:Toolbar=False e contiene testo lungo 
- La dimensione del testo non viene ridimensionata se pageHeight è minore di 0,5 in 
- Deadlock nel database di catalogo SSRS quando viene usato con CRM 
- Le intestazioni di colonna con allineamento verticale non vengono visualizzate correttamente quando si scorre verso il basso nel report 
- Per gli utenti aggiunti al ruolo SCOM Reporting verrà bloccato l'accesso al portale Web SSRS 
- I caratteri thai non vengono esportati correttamente in PDF 
- Modifica del comportamento del ruolo browser 
- rc:Toolbar=false non funziona nell'edizione Express 
- Barra di scorrimento verticale mancante nell'area dei messaggi di richiesta per i parametri 
- Aggiornamento del runtime per i report per dispositivi mobili 

### <a name="version-140600744-released-april-25-2018"></a>Versione 14.0.600.744, data di rilascio: 25 aprile 2018 

Sono stati corretti i bug seguenti:

- La pagina Sottoscrizione guidata dai dati non visualizza l'opzione di recapito dopo la creazione
- Se si esegue l'aggiornamento da SSRS 2012 a SSRS 2017, RSManagement genererà un'eccezione a intervalli di pochi secondi
- Non è possibile modificare i valori predefiniti per i parametri multivalore in IE11
- Le pianificazioni sono vuote quando viene eseguita una pianificazione condivisa

### <a name="version-140600689-released-february-28-2018"></a>Versione 14.0.600.689, data di rilascio: 28 febbraio 2018

Sono stati corretti i bug seguenti:

- La visibilità di Parametro report in un report collegato viene ripristinata dopo la modifica delle relative proprietà
- Il parametro URL rc:Toolbar=false non funziona nell'edizione Express
- In presenza di espressioni nella casella di testo con la proprietà CanGrow impostata su false, i valori non vengono visualizzati
- Aggiunta del collegamento "Ulteriori informazioni" per il codice Product Key nel programma di installazione
- Il portale Web con autenticazione basata su form personalizzata ignora il cookie di scadenza variabile
- L'esportazione in Word crea altezze di righe non uniformi se il contenuto della riga è vuoto

### <a name="version-140600594-released-january-9-2018"></a>Versione 14.0.600.594, data di rilascio: 9 gennaio 2018

Aggiornamenti per la sicurezza

### <a name="version-140600490-released-november-1-2017"></a>Versione 14.0.600.490, data di rilascio: 1 novembre 2017

È stato risolto il bug seguente:

- Problemi risolti con l'aggiornamento dello SKU

### <a name="version-140600451-released-september-30-2017"></a>Versione 14.0.600.451, data di rilascio: 30 settembre 2017 

Versione iniziale

## <a name="next-steps"></a>Passaggi successivi

[Novità di Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)   

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
