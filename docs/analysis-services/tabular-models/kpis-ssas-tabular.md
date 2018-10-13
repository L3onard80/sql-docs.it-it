---
title: Gli indicatori KPI | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8c718c3f8501a56b9ba02062e9457ca0cd67ad56
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906431"
---
# <a name="kpis"></a>KPI
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  In un modello tabulare un indicatore di prestazioni chiave ( *KPI* ) viene usato per misurare le prestazioni di un valore, definito da una misura di *base* , rispetto a un valore di *destinazione* , definito anch'esso da una misura o da un valore assoluto. Questo articolo fornisce agli autori di modelli tabulari una conoscenza di base degli indicatori KPI in un modello tabulare.  
  
##  <a name="bkmk_benefits"></a> Vantaggi  
 Nella terminologia aziendale un indicatore KPI rappresenta una misurazione quantificabile per la valutazione degli obiettivi aziendali e viene stimato con una frequenza spesso elevata. Il reparto vendite di un'organizzazione può ad esempio utilizzare un indicatore KPI per misurare il profitto lordo mensile rispetto al profitto lordo previsto. Il reparto contabilità può misurare le spese mensili rispetto ai ricavi per valutare i costi, mentre un reparto risorse umane può misurare l'avvicendamento trimestrale dei dipendenti. Ognuno di questi rappresenta un esempio di utilizzo di un indicatore KPI. I professionisti aziendali utilizzano spesso gli indicatori di prestazioni chiave raggruppati in una scorecard aziendale per ottenere un riepilogo cronologico immediato e accurato del successo aziendale o per identificare le tendenze.  
  
 Un indicatore KPI di un modello tabulare include gli elementi seguenti:  
  
 **Valore di base**  
 Un valore di base è definito da una misura che restituisce un valore. Tale valore può essere, ad esempio, un'aggregazione di vendite effettive oppure una misura calcolata, quale il profitto per un dato periodo.  
  
 **Valore di destinazione**  
 Un valore di destinazione viene definito da una misura che restituisce un valore o da un valore assoluto. Ad esempio, un valore di destinazione potrebbe essere l'importo di aumento delle vendite o dei profitti che i responsabili di un'organizzazione desiderano ottenere.  
  
 **Soglie di stato**  
 Una soglia di stato viene definita dall'intervallo tra una soglia minima e massima o da un valore fisso. La soglia di stato viene visualizzata con un diagramma per consentire agli utenti di determinare facilmente lo stato del valore di base rispetto al valore di destinazione.  
  
##  <a name="bkmk_example"></a> Esempio  
 Il responsabile vendite di Adventure Works desidera creare una tabella pivot da utilizzare per visualizzare rapidamente se i dipendenti addetti alle vendite soddisfano o meno le rispettive quote di vendite per un determinato periodo (anno). Nella tabella pivot dovranno essere visualizzati, per ogni dipendente, l'importo in dollari delle vendite effettive, l'importo in dollari della quota di vendite e un semplice grafico con l'indicazione dello stato, ovvero se la quota di vendite di ognuno è inferiore, uguale o superiore a quella definita. Desidera inoltre poter sezionare i dati per anno.  
  
 A tale scopo, il responsabile vendite supporta lo sviluppatore di soluzioni di Business Intelligence dell'organizzazione aggiungendo un indicatore KPI delle vendite al modello tabulare di AdventureWorks. Il responsabile vendite utilizzerà quindi Excel per connettersi al modello tabulare Adventure Works come origine dati e creare una tabella pivot con i campi (misure e KPI) e i filtri dei dati da analizzare se la forza vendita soddisfa le rispettive quote.  
  
 Nel modello viene creata una misura nella colonna SalesAmount della tabella FactResellerSales che indica l'importo in dollari delle vendite effettive per ogni dipendente addetto alle vendite. Tale misura definirà il valore di base dell'indicatore KPI.  
  
 Viene creata la misura Sales con la formula seguente:  
  
```  
Sales:=Sum(FactResellerSales[SalesAmount])  
```  
  
 Nella colonna SalesAmountQuota della tabella FactSalesQuota è definita una quota vendite per ogni dipendente. I valori in questa colonna verranno utilizzati come misura di destinazione (valore) nell'indicatore KPI.  
  
 La misura SalesAmountQuota viene creata con la formula seguente:  
  
```  
Target SalesAmountQuota:=Sum(FactSalesQuota[SalesAmountQuota])  
```  
  
> [!NOTE]  
>  Tra la colonna EmployeeKey nella tabella FactSalesQuota e la colonna EmployeeKey nella tabella DimEmployees esiste una relazione, che risulta necessaria per rappresentare nella tabella FactSalesQuota ogni dipendente addetto alle vendite incluso nella tabella DimEmployees.  
  
 Dopo aver creato le misure da utilizzare come valore di base e valore di destinazione dell'indicatore KPI, la misura Sales verrà estesa a un nuovo KPI vendite. Nel KPI vendite la misura di destinazione SalesAmountQuota viene definita come valore di destinazione. La soglia di stato viene definita come intervallo sotto forma di percentuale, la cui destinazione è pari al 100%, a indicare che le vendite effettive definite dalla misura Sales hanno soddisfatto l'importo della quota definito nella misura di destinazione SalesAmountQuota. Le percentuali minima e massima sono definite sulla barra di stato e viene selezionato un tipo di grafico.  
  
 A questo punto il responsabile vendite può creare una tabella pivot aggiungendo il valore di base, il valore di destinazione e lo stato dell'indicatore KPI al campo Valori. La colonna Employees viene aggiunta al campo RowLabel e la colonna CalendarYear viene aggiunta come filtro dei dati.  
  
 Il responsabile vendite può quindi sezionare per anno l'importo delle vendite effettive, l'importo della quota di vendite e lo stato per ogni dipendente addetto alle vendite. Può inoltre analizzare le tendenze di vendita negli anni per determinare se è necessario o meno modificare la quota di vendite per un dipendente.  
  
##  <a name="bkmk_create"></a> Create and edit KPIs  
 Per creare gli indicatori di prestazioni chiave in Progettazione modelli, verrà utilizzata la finestra di dialogo relativa al KPI. Dal momento che gli indicatori KPI devono essere associati a una misura, un indicatore KPI viene creato estendendo una misura che restituisce un valore di base, quindi creando una misura che restituisce un valore di destinazione, oppure immettendo un valore assoluto. Dopo aver definito la misura di base (valore) e il valore di destinazione, è possibile definire i parametri della soglia di stato tra i valori di base e di destinazione. Lo stato viene visualizzato in formato grafico tramite icone, barre, grafici o colori selezionabili. I valori di base e di destinazione, nonché lo stato, possono essere aggiunti a un report o a una tabella pivot come valori che possono essere sezionati rispetto ad altri campi dati.  
  
 Per visualizzare la finestra di dialogo dell'indicatore KPI, nella griglia delle misure per una tabella fare clic con il pulsante destro del mouse su una misura che verrà utilizzata come valore di base, quindi fare clic su **Crea KPI**. Dopo che una misura è stata estesa a un indicatore KPI come valore di base, verrà visualizzata un'icona insieme al nome della misura nella griglia delle misure che identifica la misura come associata a un indicatore KPI.  
  
##  <a name="bkmk_related_tasks"></a> Attività correlate  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Creare e gestire indicatori KPI](../../analysis-services/tabular-models/create-and-manage-kpis-ssas-tabular.md)|Viene descritto come creare un indicatore KPI con una misura di base, una misura di destinazione e soglie di stato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Misure](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [Prospettive](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)  
  
  
