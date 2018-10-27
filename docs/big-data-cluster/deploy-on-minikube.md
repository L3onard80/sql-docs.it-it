---
title: Configurare Minikube per le distribuzioni di cluster di SQL Server 2019 dei big Data | Microsoft Docs
description: Informazioni su come configurare Minikube per le distribuzioni di cluster (anteprima) dei big data 2019 di SQL Server in un singolo computer.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 71523efb55fd1bc41927b38d2e91abc9833c73b0
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050783"
---
# <a name="configure-minikube-for-sql-server-2019-big-data-cluster-deployments"></a>Configurare Minikube per le distribuzioni di cluster di SQL Server 2019 dei big Data

Questo articolo descrive come configurare **minikube** in un unico computer per le distribuzioni di cluster (anteprima) di SQL Server 2019 dei big Data. Minikube è uno strumento che rende più semplice eseguire Kubernetes in un singolo computer, ad esempio un portatile o un desktop. Minikube esegue un cluster Kubernetes a nodo singolo all'interno di una macchina virtuale sul computer portatile per gli utenti che desiderano provare Kubernetes o svilupparlo quotidiane. 

## <a name="prerequisites"></a>Prerequisiti

- Per eseguire un cluster di Minikube per SQL Server 2019 CTP 2.0 in una configurazione del cluster SQL dei big data, è consigliabile che il computer dispone di almeno 32 GB di RAM.

   > [!TIP] 
   > Se nel computer è solo il valore minimo consigliato di memoria, quindi configurare la distribuzione del cluster per avere solo 1 istanza di calcolo del pool, 1 istanza del pool di dati e istanza del pool di archiviazione di 1. Questa configurazione deve essere utilizzata solo per gli ambienti di valutazione in cui non è importante la durabilità e disponibilità dei dati. Vedere le [documentazione sulla distribuzione](deployment-guidance.md#define-environment-variables) per altre informazioni sulle variabili di ambiente da impostare per configurare il numero di repliche per i pool di dati, di calcolo di pool e i pool di archiviazione.

- La virtualizzazione VT-x o AMD-v deve essere abilitata nel BIOS del computer.

## <a name="install-dependencies"></a>Installare le dipendenze

1. Se non è già installato, installare git localmente nel [Windows](https://git-for-windows.github.io/), [Linux o Mac](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

1. Installare [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Instalovat Python 3:
   - Se pip non è presente, quindi scaricare [get-clspip.py](https://bootstrap.pypa.io/get-pip.py) ed eseguire `python get-pip.py`.
   - Installare le richieste del pacchetto usando `python -m pip install requests`.

1. Se si dispone già di un hypervisor installato, installarne uno adesso.
   - Per OS X, installare [driver xhyve](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads), o [VMware Fusion](https://www.vmware.com/products/fusion).
   - Per Linux, installare [VirtualBox](https://www.virtualbox.org/wiki/Downloads) oppure [KVM](http://www.linux-kvm.org/).
   - Per Windows, installare [VirtualBox](https://www.virtualbox.org/wiki/Downloads) oppure [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Se non è un commutatore esterno configurato in hyper-v, quindi crearne uno che abbia accesso alla rete esterna.  Vedere come [crea commutatore esterno in hyper-v per minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Installare Minikube

Installare Minikube seguendo le istruzioni per la [v0.28.2 versione](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Il cluster di big data di SQL Server 2019 CTP 2.0 funziona solo con versione v0.24.1 e versioni successive.

## <a name="create-a-minikube-cluster"></a>Creare un cluster di Minikube

Il comando seguente crea un cluster di minikube in una macchina virtuale di Hyper-V con 8 CPU, 28 GB di memoria e dimensioni del disco da 100 GB. Le dimensioni del disco non sono lo spazio riservato.  Raggiunge tale dimensione sul disco in base alle esigenze.  È consigliabile non modificare il disco di spazio su un valore minore di 100 GB come si è verificato un problema con questo test. Questa specifica anche il commutatore hyper-v con accesso esterno in modo esplicito.

Modificare i parametri, ad esempio **-memoria** in base alle esigenze a seconda dell'hardware disponibile e che si usa hypervisor.  Assicurarsi che il **: hyper-v** valore del parametro di commutatore virtuale corrispondente al nome usato durante la creazione del commutatore virtuale.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Se si usa Minikube con VirtualBox il comando dovrebbe essere simile al seguente:

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Disabilitare i checkpoint automatici con Hyper-V

In Windows 10, è abilitato un checkpoint automatico in una macchina virtuale. Eseguire il comando seguente in PowerShell per disabilitare il checkpoint automatico nella macchina virtuale.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Passaggi successivi

I passaggi descritti in questo articolo è configurato un cluster di Minikube. Il passaggio successivo consiste nel distribuire il cluster di big data di SQL Server 2019. Per istruzioni, vedere l'articolo seguente:

[Distribuire SQL Server 2019 CTP 2.0 in Kubernetes](deployment-guidance.md#deploy)
