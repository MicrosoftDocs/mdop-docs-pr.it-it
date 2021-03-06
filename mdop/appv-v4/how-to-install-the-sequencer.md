---
title: Come installare Sequencer
description: Come installare Sequencer
author: dansimp
ms.assetid: 2cd16427-a0ba-4870-82d1-3e3c79e1959b
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 75a0f987fcc76d1ed92631085a4364ae6e06c9ce
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10817266"
---
# Come installare Sequencer


Microsoft Application Virtualization (App-V) Sequencer monitora e registra il processo di installazione e configurazione per le applicazioni in modo che l'applicazione possa essere eseguita come applicazione virtuale. È necessario installare il sequencer in un computer in cui è installato solo il sistema operativo. In alternativa, è possibile installare il sequencer in un computer che gestisce un ambiente virtuale, ad esempio Microsoft Virtual PC. Questo metodo è utile perché è più semplice mantenere un ambiente di sequenziazione pulito che può essere riutilizzato con una configurazione aggiuntiva minima.

È necessario disporre di diritti amministrativi nel computer in uso per sequenziare l'applicazione e il computer deve essere connesso alla rete. Il computer non deve eseguire alcuna versione del client Application Virtualization (App-V). La creazione di un'applicazione virtuale tramite il sequencer è molto intensiva delle risorse, quindi è importante installare il sequencer in un computer che soddisfi o superi i requisiti consigliati. Per altre informazioni sui requisiti di sistema, vedere [requisiti hardware e software sequencer](sequencer-hardware-and-software-requirements.md).

**Per installare Microsoft Application Virtualization Sequencer**

1.  Copiare i file di installazione di Microsoft Application Virtualization Sequencer nel computer in cui si vuole installarlo.

2.  Per avviare l'installazione guidata di Microsoft Application Virtualization Sequencer, selezionare **setup.exe**. Se il **pacchetto ridistribuibile Microsoft Visual C++ SP1 (x86)** non viene rilevato prima dell'installazione, **setup.exe** lo installerà.

3.  Nella pagina di **benvenuto** fare clic su **Avanti**.

4.  Per accettare le condizioni del contratto di licenza nella pagina **contratto** di licenza, selezionare **Accetto i termini del contratto di licenza**. Fai clic su **Avanti**.

5.  Nella pagina **cartella di destinazione** , per accettare la cartella di installazione predefinita, fare clic su **Avanti**. Per specificare una cartella di destinazione diversa, fare clic su **Cambia** e specificare la cartella di installazione che verrà usata per l'installazione. Fai clic su **Avanti**.

6.  Nella pagina **pronto per l'installazione del programma** , per avviare l'installazione, fare clic su **Installa**.

7.  Nella pagina **completamento guidata InstallShield** , per chiudere l'installazione guidata e aprire il sequencer, fare clic su **fine**. Per chiudere l'installazione guidata senza aprire il sequencer, deselezionare **Avvia il programma** e fare clic su **fine**.

## Argomenti correlati


[Configurazione di Application Virtualization Sequencer](configuring-the-application-virtualization-sequencer.md)

 

 





