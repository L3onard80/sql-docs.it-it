---
title: Usare kubectl per monitorare un cluster di big data di SQL Server | Microsoft Docs
description: Questo articolo forniscono i comandi di kubectl utile per il monitoraggio e risoluzione dei problemi relativi a un cluster di big data di SQL Server 2019 (anteprima).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/15/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: a47726e86bd1f10cda4db55bec6eac995344da38
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356595"
---
# <a name="kubectl-commands-for-monitoring-and-troubleshooting-sql-server-big-data-clusters"></a>Comandi di Kubectl per il monitoraggio e risoluzione dei problemi dei cluster di SQL Server i big Data

Questo articolo descrive alcuni comandi utili di Kubernetes che è possibile usare per monitorare e risolvere i problemi di un cluster di big data di SQL Server 2019 (anteprima). Questo articolo illustra le attività comuni, ad esempio la copia dei file in o da un contenitore in esecuzione uno dei servizi cluster di big data di SQL Server. Viene inoltre illustrato come visualizzare i dettagli di un pod o altri elementi di Kubernetes che si trovano nel cluster di big data.

## <a name="kubectl-command-examples"></a>Esempi di comando di Kubectl

Eseguire il comando seguente **kubectl** comandi sul computer client Linux (bash) o Windows (cmd o PS). Richiedono precedente autenticazione nel cluster e un contesto del cluster da eseguire. Per un cluster servizio contenitore di AZURE creato in precedenza, ad esempio, è possibile eseguire `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` per scaricare il file di configurazione del cluster Kubernetes e impostare il contesto del cluster.

## <a name="get-status-of-pods"></a>Ottenere lo stato dei POD

È possibile usare il `kubectl get pods` comando per ottenere lo stato dei POD nel cluster per tutti gli spazi dei nomi o per lo spazio dei nomi del cluster di big data. Le sezioni seguenti mostrano esempi di entrambi.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Mostra lo stato di tutti i POD nel cluster Kubernetes

Eseguire il comando seguente per ottenere tutti i POD e i relativi stati, tra cui i POD che fanno parte dello spazio dei nomi che SQL Server vengono creati i POD del cluster di big data in:

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Mostra lo stato di tutti i POD nel cluster di big data di SQL Server

Usare il `-n` parametro per specificare uno spazio dei nomi specifico. Si noti che SQL Server in un nuovo spazio dei nomi creato in fase di bootstrap del cluster vengono creati i POD del cluster di big data basata sul nome del cluster specificato nella `mssqlctl create cluster <cluster_name>` comando.

```bash
kubectl get pods -n <namespace_name>
```

Ad esempio, il comando seguente mostra lo stato dei POD in un cluster di big data denominato `big_data_cluster`:

```bash
kubectl get pods -n big_data_cluster
```

## <a name="get-pod-details"></a>Ottenere i dettagli di pod

Eseguire il comando seguente per ottenere una descrizione dettagliata di un pod specifico nell'output di formato json. Include informazioni dettagliate, ad esempio il nodo corrente di Kubernetes che il pod viene inserito in, i contenitori in esecuzione all'interno di pod e l'immagine usata per avviare i contenitori. Inoltre, Mostra altri dettagli, ad esempio etichette, stato e salvati in modo permanente le attestazioni di volumi che sono associate i pod.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

L'esempio seguente mostra i dettagli per il `mssql-data-pool-master-0` pod in un cluster di big data denominato `big_data_cluster`:

```bash
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="get-status-of-services"></a>Ottenere lo stato dei servizi

Eseguire il comando seguente per ottenere i dettagli per i servizi cluster di big data. Questi dettagli includono il tipo e gli indirizzi IP associati con le porte e i rispettivi servizi. Si noti che i servizi cluster di SQL Server i big data vengono creati in un nuovo spazio dei nomi creato in fase di bootstrap del cluster in base al nome del cluster specificato nella `mssqlctl create cluster <cluster_name>` comando.

```bash
kubectl get svc -n <namespace_name>
```

L'esempio seguente mostra lo stato per i servizi in un cluster di big data denominato `big_data_cluster`:

```bash
kubectl get svc -n big_data_cluster
```

## <a name="get-service-details"></a>Ottenere i dettagli del servizio

Eseguire questo comando per ottenere una descrizione dettagliata di un servizio in formato json output. Che include i dettagli come etichette, selettore, indirizzo IP, external-IP (se il servizio è di tipo LoadBalancer), porta e così via.
```
kubectl describe pod  <pod_name> -n <namespace_name>
```

Esempio:
```
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="run-commands-in-a-container"></a>Eseguire i comandi in un contenitore

Se gli strumenti esistenti o dell'infrastruttura non consentono di eseguire una determinata attività senza effettivamente in corso nel contesto del contenitore, è possibile accedere al contenitore usando `kubectl exec` comando. Ad esempio, si potrebbe essere necessario verificare se esiste un file specifico, o potrebbe essere necessario riavviare i servizi nel contenitore. 

Usare il `kubectl exec` comando, usare la sintassi seguente:

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

Le due sezioni seguenti forniscono due esempi di esecuzione di un comando in un contenitore specifico.

### <a id="restartsql"></a> Accedere a un contenitore specifico e riavviare il processo di SQL Server

Nell'esempio seguente viene illustrato come riavviare il processo di SQL Server nel `mssql-server` contenitore nel `mssql-master-pool-0` pod:

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> Accedere a un contenitore specifico e riavviare i servizi in un contenitore
 
Nell'esempio seguente viene illustrato come riavviare tutti i servizi gestiti da **supervisord**: 

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a> Copiare i file

Se è necessario copiare i file dal contenitore nel computer locale, usare `kubectl cp` comando con la sintassi seguente:

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

Analogamente, è possibile usare `kubectl cp` per copiare i file dal computer locale in un contenitore specifico.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a> Copiare i file da un contenitore

Nell'esempio seguente copia i file di log di SQL Server dal contenitore per il `~/temp/sqlserverlogs` percorso nel computer locale (in questo esempio il computer locale è un client Linux):
 
```bash
kubectl cp mssql-master-pool-0:/var/opt/mssql/log -c mssql-server -n big_data_cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> Copiare i file nel contenitore

L'esempio seguente copia il **AdventureWorks2016CTP3.bak** file dal computer locale al contenitore di istanza master di SQL Server (`mssql-server`) nella `mssql-master-pool-0` pod. Il file viene copiato il `/tmp` directory nel contenitore. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n big_data_cluster
```

## <a id="forcedelete"></a> Eliminazione forzata un pod
 
Non è consigliabile forzare l'eliminazione un pod. Ma per il test di disponibilità, resilienza o la persistenza dei dati, è possibile eliminare un pod per simulare un errore di pod con il `kubectl delete pods` comando.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

L'esempio seguente elimina il pod del pool di archiviazione, `mssql-storage-pool-default-0`:

```bash
kubectl delete pods mssql-storage-pool-default-0 -n big_data_cluster --grace-period=0 --force
```

## <a id="getip"></a> Ottenere l'indirizzo IP di pod
 
Per la risoluzione dei problemi, potrebbe essere necessario ottenere l'indirizzo IP del nodo di che un pod in esecuzione. Per ottenere l'indirizzo IP, usare il `kubectl get pods` comando con la sintassi seguente:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

L'esempio seguente ottiene l'indirizzo IP del nodo di `mssql-master-pool-0` pod è in esecuzione in:

```bash
kubectl get pods mssql-master-pool-0 -o yaml -n big_data_cluster | grep hostIP
```

## <a name="start-the-kubernetes-dashboard"></a>Avviare il dashboard di Kubernetes

È possibile avviare il dashboard di Kubernetes per altre informazioni sul cluster. Le sezioni seguenti illustrano come avviare il dashboard per Kubernetes nel servizio contenitore di AZURE e per eseguire il bootstrap utilizzando kubeadm Kubernetes.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Avviare il dashboard di quando il cluster è in esecuzione nel servizio contenitore di AZURE

Per avviare il dashboard di Kubernetes eseguire:
 
```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Se viene visualizzato l'errore seguente: *non è possibile restare in ascolto sulla porta 8001: tutti i listener non è riuscito a creare con i seguenti errori: non è possibile creare listener: errore ascolto tcp4 127.0.0.1:8001: > associare: un solo utilizzo di ogni indirizzo del socket (protocollo di rete indirizzo/porta) di norma è consentita. Non è possibile creare listener: errore ascolto tcp6: indirizzo [[:: 1]]: 8001: mancante nella porta > risolvere l'errore: Impossibile rimanere in ascolto su una delle porte di richiesta: [{8001 9090}]*, assicurarsi che non è stato avviato il dashboard già da un'altra finestra.

Quando si avvia il dashboard nel browser, è possibile ottenere gli avvisi di autorizzazione a causa di RBAC viene abilitata per impostazione predefinita nei cluster servizio contenitore di AZURE e l'account di servizio utilizzato dal dashboard non dispone delle autorizzazioni sufficienti per accedere a tutte le risorse (ad esempio,  *non è consentito il Pod: utente "system: serviceaccount:kube-system: kubernetes-dashboard" non è possibile elencare i POD nello spazio dei nomi "default"*). Eseguire il comando seguente per concedere le autorizzazioni necessarie per `kubernetes-dashboard`e quindi riavviare il dashboard:

```
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Avviare il dashboard di quando viene avviato un cluster Kubernetes automaticamente usando kubeadm

Per altre istruzioni su come distribuire e configurare il dashboard del cluster Kubernetes, vedere [la documentazione di Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Per avviare il dashboard di Kubernetes, eseguire questo comando:

```
kubectl proxy
```

## <a name="next-steps"></a>Passaggi successivi

Per il monitoraggio e risoluzione dei problemi che è specifica di SQL Server i cluster di big data, vedere la [portale di amministrazione cluster](cluster-admin-portal.md).