---
title: Editor attività Invia messaggi (pagina posta) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d80ca8e475bf9c2b56c11118a44e5282573f280d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055825"
---
# <a name="send-mail-task-editor-mail-page"></a>Editor attività Invia messaggi (pagina Messaggio)
  Usare la pagina **Messaggio** della finestra di dialogo **Editor attività Invia messaggi** per specificare i destinatari, il tipo di messaggio e la priorità relativi a un messaggio. È inoltre possibile allegare file al messaggio. Il testo del messaggio può essere una stringa specificata, una connessione a un file che contiene il testo o il nome di una variabile che contiene il testo.  
  
 Per ulteriori informazioni su questa attività, vedere [Send Mail Task](control-flow/send-mail-task.md).  
  
## <a name="options"></a>Opzioni  
 **SMTPConnection**  
 Selezionare una gestione connessione SMTP nell'elenco oppure fare clic su ** \<nuova connessione... >** per creare una nuova gestione connessione.  
  
> [!IMPORTANT]  
>  La gestione connessione SMTP supporta solo l'autenticazione anonima e l'autenticazione di Windows. Non supporta l'autenticazione di base.  
  
 **Argomenti correlati:** [gestione connessione SMTP](connection-manager/smtp-connection-manager.md)  
  
 **Da**  
 Consente di specificare l'indirizzo di posta elettronica del mittente.  
  
 **A**  
 Consente di specificare gli indirizzi di posta elettronica dei destinatari, separati da punti e virgola.  
  
 **CC**  
 Consente di specificare gli indirizzi di posta elettronica, separati da punti e virgola, di altri destinatari che riceveranno copie del messaggio.  
  
 **Ccn**  
 Consente di specificare gli indirizzi di posta elettronica, separati da punti e virgola, di destinatari in copia nascosta che riceveranno copie del messaggio.  
  
 **Oggetto**  
 Consente di specificare l'oggetto del messaggio di posta elettronica.  
  
 **MessageSourceType**  
 Consente di selezionare il tipo di origine del messaggio. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**Input diretto**|Consente di impostare l'origine sul testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
|**Connessione file**|Consente di impostare l'origine sul file contenente il testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
|**Variabile**|Consente di impostare l'origine su una variabile contenente il testo del messaggio. Selezionando questo valore, verrà visualizzata l'opzione dinamica **MessageSource**.|  
  
 **Priorità**  
 Consente di impostare il livello di priorità del messaggio.  
  
 **Allegati**  
 Consente di specificare i nomi file degli allegati del messaggio di posta elettronica, separati dal carattere di barra verticale (|).  
  
> [!NOTE]  
>  Le righe A, Cc e Ccn sono limitate a 256 caratteri, in conformità con gli standard Internet.  
  
## <a name="messagesourcetype-dynamic-options"></a>Opzioni dinamiche MessageSourceType  
  
### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Input diretto  
 **MessageSource**  
 Digitare il testo del messaggio oppure fare clic sul pulsante Sfoglia (...), quindi digitare il messaggio nella finestra di dialogo **Origine messaggio**.  
  
### <a name="messagesourcetype--file-connection"></a>MessageSourceType = Connessione file  
 **MessageSource**  
 Selezionare una gestione connessione file nell'elenco oppure crearne una nuova facendo clic su \<**Nuova connessione**.  
  
 **Argomenti correlati:** [gestione connessione file](connection-manager/file-connection-manager.md), [Editor gestione connessione file](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="messagesourcetype--variable"></a>MessageSourceType = Variabile  
 **MessageSource**  
 Selezionare una variabile nell'elenco oppure fare clic \<su **nuova variabile...**> per creare una nuova variabile.  
  
 **Argomenti correlati:** [Integration Services &#40;variabili di&#41; SSIS](integration-services-ssis-variables.md), [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Invia messaggi &#40;pagina generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  
