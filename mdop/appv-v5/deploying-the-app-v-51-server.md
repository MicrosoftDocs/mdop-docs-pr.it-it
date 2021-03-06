---
title: Distribuzione del server App-V 5.1
description: Distribuzione del server App-V 5.1
author: dansimp
ms.assetid: 987b61dc-00d6-49ba-8f1b-92d7b948e702
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 2bcff2a3211ea3e2f666aff1d6f2ad919509aa3a
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10805823"
---
# Distribuzione del server App-V 5.1

È possibile installare le caratteristiche del server Microsoft Application Virtualization (App-V) 5,1 usando configurazioni di distribuzione diverse, descritte in questo argomento. Prima di installare le funzionalità del server, esaminare la sezione server delle [considerazioni sulla sicurezza di App-V 5,1](app-v-51-security-considerations.md).

Per informazioni sulla distribuzione di App-V Server, vedere [informazioni su App-v 5,1](about-app-v-51.md#bkmk-migrate-to-51).

> [!IMPORTANT]
> Prima di installare e configurare i server App-V 5,1, è necessario specificare una porta in cui verranno ospitati tutti i componenti. Devi anche aggiungere le regole del firewall associate per consentire alle richieste in arrivo di accedere alle porte specificate. Il programma di installazione non modifica le impostazioni del firewall.

## <a href="" id="---------app-v-5-1-server-overview"></a> Panoramica del server App-V 5,1

Il server App-V 5,1 è costituito da cinque componenti. Ogni componente offre uno scopo diverso nell'ambiente App-V 5,1. Ognuno dei cinque componenti è brevemente descritto qui:

- Server di gestione: offre funzionalità di gestione complessive per l'infrastruttura App-V 5,1.
- Database di gestione: consente di semplificare le predistribuzioni di database per la gestione di App-V 5,1.
- Publishing Server: offre funzionalità di hosting e flusso per le applicazioni virtuali.
- Reporting Server: offre app-V 5,1 Reporting Services.
- Database delle relazioni: consente di semplificare le predistribuzioni di database per la creazione di report in App-V 5,1.

## <a href="" id="---------app-v-5-1-stand-alone-deployment"></a> Implementazione autonoma di App-V 5,1

La distribuzione autonoma di App-V 5,1 offre una buona topologia per una distribuzione di piccole dimensioni o un ambiente di test. Quando si usa questo tipo di implementazione, tutti i componenti del server vengono distribuiti in un singolo computer. I servizi e i database associati verranno confrontati per le risorse nel computer che esegue i componenti dell'App-V 5,1. Di conseguenza, non è consigliabile usare questa topologia per distribuzioni più grandi.

[Come distribuire il server App-V 5.1](how-to-deploy-the-app-v-51-server.md)

[Come distribuire il server App-V 5.1 con uno script](how-to-deploy-the-app-v-51-server-using-a-script.md)

## <a href="" id="---------app-v-5-1-server-distributed-deployment"></a> Implementazione distribuita del server App-V 5,1

La topologia di distribuzione distribuita può supportare una grande base client App-V 5,1 e consente di gestire e ridimensionare più facilmente l'ambiente. Quando si usa questo tipo di distribuzione, i componenti del server App-V 5,1 vengono distribuiti in più computer, in base alla struttura e ai requisiti dell'organizzazione.

[Come installare i database di gestione e creazione di report in computer distinti dai servizi di gestione e creazione di report](how-to-install-the-management-and-reporting-databases-on-separate-computers-from-the-management-and-reporting-services51.md)

[Come installare il server di gestione in un computer autonomo e connetterlo al database](how-to-install-the-management-server-on-a-standalone-computer-and-connect-it-to-the-database51.md)

[Come distribuire il server App-V 5.1 con uno script](how-to-deploy-the-app-v-51-server-using-a-script.md)

[Come installare il server di pubblicazione in un computer remoto](how-to-install-the-publishing-server-on-a-remote-computer51.md)

[Come installare il server di gestione in un computer autonomo e connetterlo al database](how-to-install-the-management-server-on-a-standalone-computer-and-connect-it-to-the-database51.md)

## Uso di una soluzione ESD (Enterprise Software Distribution) e di un'app-V 5,1

Puoi anche distribuire i client e i pacchetti App-V 5,1 usando un ESD senza dover distribuire App-V 5,1. Le funzionalità complete per l'integrazione variano a seconda dell'ESD usato.

> [!NOTE]
> Il server di report e il database di report di App-V 5,1 possono comunque essere distribuiti insieme all'ESD per raccogliere i dati dei report dai client App-V 5,1. Tuttavia, gli altri tre componenti del server non devono essere distribuiti perché si scontrano con la funzionalità ESD.

[Distribuzione di pacchetti App-V 5.1 usando una soluzione di distribuzione elettronica del software](deploying-app-v-51-packages-by-using-electronic-software-distribution--esd-.md)

## <a href="" id="---------app-v-5-1-server-logs"></a> Log del server App-V 5,1

Puoi usare le informazioni sul log di App-V 5,1 per risolvere i problemi relativi all'installazione e agli eventi operativi del server durante l'uso di App-V 5,1. Le informazioni del log correlate al server possono essere esaminate con il **Visualizzatore eventi**. Nella riga seguente viene visualizzato il percorso specifico per gli eventi correlati al server:

**Visualizzatore eventi \ \ applicazioni e registri Servizi \ \ Microsoft \ \ App V**

I registri di configurazione associati vengono salvati nella directory seguente:

**Temp**

In App-V 5,0 SP3 alcuni registri sono stati consolidati e spostati. Vedere [informazioni su App-V 5,0 SP3](about-app-v-50-sp3.md#bkmk-event-logs-moved).

## <a href="" id="---------app-v-5-1-reporting"></a> Creazione di report in App-V 5,1

La creazione di report in App-V 5,1 consente ai client App-V 5,1 di raccogliere dati e quindi di inviarli di nuovo per essere archiviati in un repository centrale. Puoi usare queste informazioni per ottenere una migliore visualizzazione dell'utilizzo dell'applicazione virtuale all'interno dell'organizzazione. L'elenco seguente mostra alcuni tipi di informazioni raccolte dal client App-V 5,1:

- Informazioni sul computer in cui viene eseguito il client App-V 5,1.
- Informazioni sui pacchetti virtualizzati in uno specifico computer in cui viene eseguito il client App-V 5,1.
- Informazioni sul pacchetto aperto e Shutdown per un utente specifico.

Le informazioni di report verranno mantenute fino a quando non vengono inviate correttamente al database del server di report. Dopo che i dati sono presenti nel database, è possibile usare Microsoft SQL Server Reporting Services per generare i report necessari.

Se si vogliono recuperare le informazioni del report, è necessario usare Microsoft SQL Server Reporting Services (SSRS), disponibile in Microsoft SQL. SSRS non viene installato quando si installa il server di report App-V 5,1 e deve essere distribuito separatamente per generare i report associati.

Usare il collegamento seguente per altre informazioni [sulla creazione di report di App-V 5,1](about-app-v-51-reporting.md).

[Come abilitare la creazione di report nel client App-V 5.1 con PowerShell](how-to-enable-reporting-on-the-app-v-51-client-by-using-powershell.md)

## Altre risorse per l'App-V Server

[Distribuzione di App-V 5.1](deploying-app-v-51.md)
