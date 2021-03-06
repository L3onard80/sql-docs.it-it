---
title: Uso delle estensioni Visual C++ | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ [ADO], using VC++ extensions
- ADO, Visual C++
ms.assetid: ff759185-df41-4507-8d12-0921894ffbd9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a9d60695bd033bfc83e3a091490f27f9432782c0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926459"
---
# <a name="visual-c-extensions"></a>Estensioni Visual C++
## <a name="the-iadorecordbinding-interface"></a>Interfaccia IADORecordBinding
 Le estensioni Microsoft Visual C++ per ADO associate, o bind, i campi di un oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) alle variabili C/C++. Ogni volta che la riga corrente del **Recordset** associato viene modificata, tutti i campi associati nel **Recordset** vengono copiati nelle variabili C/C++. Se necessario, i dati copiati vengono convertiti nel tipo di dati dichiarato della variabile C/C++.

 Il metodo **BindToRecordset** dell'interfaccia **IADORecordBinding** associa i campi alle variabili C/C++. Il metodo **AddNew** aggiunge una nuova riga al **Recordset**associato. Il metodo **Update** compila i campi in nuove righe del **Recordset**o aggiorna i campi nelle righe esistenti, con il valore delle variabili C/C++.

 L'interfaccia **IADORecordBinding** viene implementata dall'oggetto **Recordset** . L'implementazione non viene codificata manualmente.

## <a name="binding-entries"></a>Voci di binding
 Le estensioni Visual C++ per i campi di mapping ADO di un oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) a variabili C/C++. La definizione di un mapping tra un campo e una variabile è detta *voce di associazione*. Le macro forniscono voci di binding per dati numerici, a lunghezza fissa e a lunghezza variabile. Le voci di binding e le variabili C/C++ vengono dichiarate in una classe derivata dalla classe Visual C++ Extensions, **CADORecordBinding**. La classe **CADORecordBinding** è definita internamente dalle macro della voce di associazione.

 ADO esegue internamente il mapping dei parametri in queste macro a una struttura OLE DB **DBBINDING** e crea un oggetto **funzione di accesso** OLE DB per gestire lo spostamento e la conversione dei dati tra campi e variabili. OLE DB definisce i dati come composti da tre parti: un *buffer* in cui sono archiviati i dati; *stato* che indica se un campo è stato archiviato correttamente nel buffer o in che modo è necessario ripristinare la variabile nel campo; e la *lunghezza* dei dati. Per ulteriori informazioni, vedere [recupero e impostazione dei dati (OLE DB) nella Guida](https://msdn.microsoft.com/4369708b-c9fb-4d48-a321-bf949b41a369)di riferimento per i programmatori di OLE DB.

## <a name="header-file"></a>File di intestazione
 Includere il file seguente nell'applicazione per usare le estensioni Visual C++ per ADO:

```cpp
#include <icrsint.h>
```

## <a name="binding-recordset-fields"></a>Binding di campi recordset

#### <a name="to-bind-recordset-fields-to-cc-variables"></a>Per associare campi recordset a variabili C/C++

1.  Creare una classe derivata dalla classe **CADORecordBinding** .

2.  Specificare le voci di binding e le variabili C/C++ corrispondenti nella classe derivata. Racchiudere le voci di binding tra **BEGIN_ADO_BINDING** e **END_ADO_BINDING** macro. Non terminare le macro con virgole o punti e virgola. I delimitatori appropriati vengono specificati automaticamente da ogni macro.

     Specificare una voce di binding per ogni campo di cui eseguire il mapping a una variabile C/C++. Usare un membro appropriato da **ADO_FIXED_LENGTH_ENTRY**, **ADO_NUMERIC_ENTRY**o **ADO_VARIABLE_LENGTH_ENTRY** famiglia di macro.

3.  Nell'applicazione creare un'istanza della classe derivata da **CADORecordBinding**. Ottenere l'interfaccia **IADORecordBinding** dal **Recordset**. Chiamare quindi il metodo **BindToRecordset** per associare i campi del **Recordset** alle variabili C/C++.

 Per ulteriori informazioni, vedere l' [esempio Visual C++ Extensions](../../../ado/guide/appendixes/visual-c-extensions-example.md).

## <a name="interface-methods"></a>Metodi di interfaccia
 L'interfaccia **IADORecordBinding** ha tre metodi: **BindToRecordset**, **AddNew**e **Update**. L'unico argomento per ogni metodo è un puntatore a un'istanza della classe derivata da **CADORecordBinding**. Pertanto, i metodi **AddNew** e **Update** non possono specificare i parametri del metodo ADO omonimi.

## <a name="syntax"></a>Sintassi
 Il metodo **BindToRecordset** associa i campi **Recordset** alle variabili C/C++.

```cpp
BindToRecordset(CADORecordBinding *binding)
```

 Il metodo **AddNew** richiama il suo omonimo, il metodo ADO [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) , per aggiungere una nuova riga al **Recordset**.

```cpp
AddNew(CADORecordBinding *binding)
```

 Il metodo **Update** richiama l'omonimo metodo di [aggiornamento](../../../ado/reference/ado-api/update-method.md) ADO, per aggiornare il **Recordset**.

```cpp
Update(CADORecordBinding *binding)
```

## <a name="binding-entry-macros"></a>Macro di immissione di associazione
 Le macro di immissione delle associazioni definiscono l'associazione di un campo del **Recordset** e una variabile. Una macro iniziale e finale delimita il set di voci di associazione.

 Le famiglie di macro sono fornite per i dati a lunghezza fissa, ad esempio **addate** o **adBoolean**; dati numerici, ad esempio **adTinyInt**, **adInteger**o **adDouble**; e dati a lunghezza variabile, ad esempio **adChar**, **adVarChar** o **adVarBinary**. Anche tutti i tipi numerici, ad eccezione di **adVarNumeric**, sono tipi a lunghezza fissa. Ogni famiglia ha insiemi diversi di parametri, in modo che sia possibile escludere le informazioni di binding che non sono di alcun interesse.

 Per ulteriori informazioni, vedere [Appendice A: tipi di dati](https://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6)di OLE DB Programmer ' s Reference.

### <a name="begin-binding-entries"></a>Inizio binding voci
 **BEGIN_ADO_BINDING**(*classe*)

### <a name="fixed-length-data"></a>Dati a lunghezza fissa
 **ADO_FIXED_LENGTH_ENTRY**(*ordinale, tipo di dati, buffer, stato, modifica*)

 **ADO_FIXED_LENGTH_ENTRY2**(*ordinale, DataType, buffer, Modify*)

### <a name="numeric-data"></a>Dati numerici
 **ADO_NUMERIC_ENTRY**(*ordinale, tipo di dati, buffer, precisione, scala, stato, modifica*)

 **ADO_NUMERIC_ENTRY2**(*ordinale, tipo di dati, buffer, precisione, scala, modifica*)

### <a name="variable-length-data"></a>Dati a lunghezza variabile
 **ADO_VARIABLE_LENGTH_ENTRY**(*ordinale, tipo di dati, buffer, dimensioni, stato, lunghezza, modifica*)

 **ADO_VARIABLE_LENGTH_ENTRY2**(*ordinale, tipo di dati, buffer, dimensioni, stato, modifica*)

 **ADO_VARIABLE_LENGTH_ENTRY3**(*ordinale, tipo di dati, buffer, dimensioni, lunghezza, modifica*)

 **ADO_VARIABLE_LENGTH_ENTRY4**(*ordinale, tipo di dati, buffer, dimensioni, modifica*)

### <a name="end-binding-entries"></a>Termina voci di binding
 **END_ADO_BINDING**()

|Parametro|Descrizione|
|---------------|-----------------|
|*Classe*|Classe in cui sono definite le voci di associazione e le variabili C/C++.|
|*Ordinal*|Numero ordinale, conteggio da uno, del campo **Recordset** corrispondente alla variabile C/C++.|
|*DataType*|Tipo di dati ADO equivalente della variabile C/C++ (vedere [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) per un elenco di tipi di dati validi). Se necessario, il valore del campo **Recordset** verrà convertito in questo tipo di dati.|
|*Buffer*|Nome della variabile C/C++ in cui verrà archiviato il campo del **Recordset** .|
|*Dimensione*|Dimensione massima, in byte, del *buffer*. Se il *buffer* contiene una stringa a lunghezza variabile, consentire lo spazio per uno zero di terminazione.|
|*Status*|Nome di una variabile che indicherà se il contenuto del *buffer* è valido e se la conversione del campo nel *tipo* di dati è stata eseguita correttamente.<br /><br /> I due valori più importanti per questa variabile sono **adFldOK**, il che significa che la conversione è stata eseguita correttamente. e **adFldNull**, che indica che il valore del campo è una variante di tipo VT_NULL e non è semplicemente vuota.<br /><br /> I valori possibili per *lo stato* sono elencati nella tabella seguente, "valori di stato".|
|*Modifica*|Flag booleano; Se TRUE, indica che ADO è autorizzato ad aggiornare il campo **Recordset** corrispondente con il valore contenuto nel *buffer*.<br /><br /> Impostare il parametro booleano *Modify* su true per abilitare ADO per aggiornare il campo associato e false se si desidera esaminare il campo senza modificarlo.|
|*Precision*|Numero di cifre che possono essere rappresentate in una variabile numerica.|
|*Scalabilità*|Numero di posizioni decimali in una variabile numerica.|
|*Length*|Nome di una variabile a quattro byte che conterrà la lunghezza effettiva dei dati nel *buffer*.|

## <a name="status-values"></a>Valori di stato
 Il valore della variabile di *stato* indica se un campo è stato copiato correttamente in una variabile.

 Quando si impostano i dati, *lo stato* può essere impostato su **adFldNull** per indicare che il campo **Recordset** deve essere impostato su null.

|Costante|valore|Descrizione|
|--------------|-----------|-----------------|
|**adFldOK**|0|È stato restituito un valore di campo non null.|
|**adFldBadAccessor**|1|Binding non valido.|
|**adFldCantConvertValue**|2|Non è stato possibile convertire il valore per motivi diversi dalla non corrispondenza di segno o dall'overflow dei dati.|
|**adFldNull**|3|Quando si recupera un campo, indica che è stato restituito un valore null.<br /><br /> Quando si imposta un campo, indica che il campo deve essere impostato su **null** quando il campo non può codificare **null** (ad esempio, una matrice di caratteri o un Integer).|
|**adFldTruncated**|4|I dati a lunghezza variabile o le cifre numeriche sono stati troncati.|
|**adFldSignMismatch**|5|Il valore è firmato e il tipo di dati della variabile è senza segno.|
|**adFldDataOverFlow**|6|Il valore è maggiore di quello che può essere archiviato nel tipo di dati della variabile.|
|**adFldCantCreate**|7|Il tipo di colonna e il campo sconosciuti sono già aperti.|
|**adFldUnavailable**|8|Non è stato possibile determinare il valore del campo, ad esempio in un nuovo campo non assegnato senza alcun valore predefinito.|
|**adFldPermissionDenied**|9|Quando si esegue l'aggiornamento, non sono disponibili autorizzazioni per la scrittura di dati.|
|**adFldIntegrityViolation**|10|Quando si esegue l'aggiornamento, il valore del campo viola l'integrità della colonna.|
|**adFldSchemaViolation**|11|Quando si esegue l'aggiornamento, il valore del campo viola lo schema della colonna.|
|**adFldBadStatus**|12|Durante l'aggiornamento, parametro di stato non valido.|
|**adFldDefault**|13|Quando si esegue l'aggiornamento, viene utilizzato un valore predefinito.|

## <a name="see-also"></a>Vedere anche
 [Esempio di estensioni Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) estensioni [Visual C++ estensioni](../../../ado/guide/appendixes/visual-c-extensions-header.md)
