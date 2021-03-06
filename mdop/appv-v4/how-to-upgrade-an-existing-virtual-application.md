---
title: Come eseguire l'aggiornamento di un'applicazione virtuale esistente
description: Come eseguire l'aggiornamento di un'applicazione virtuale esistente
author: dansimp
ms.assetid: ec531576-2423-4c2c-9b9f-da74174a6858
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 71fb096c103a0bcb9913d4eea33b1259a33a54ee
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10816446"
---
# Come eseguire l'aggiornamento di un'applicazione virtuale esistente


Puoi aggiornare un'applicazione virtuale esistente a una nuova versione usando l'Application Virtualization (App-V) Sequencer. Il processo di aggiornamento è simile alla creazione di una nuova applicazione virtuale. È necessario aprire l'applicazione virtuale esistente per un aggiornamento, apportare gli aggiornamenti necessari e quindi salvare l'applicazione virtuale aggiornata in una nuova posizione nella directory radice del pacchetto.

Puoi anche usare la console dell'App-V Sequencer per apportare modifiche a un'applicazione virtuale esistente senza eseguire un aggiornamento. Tuttavia, non puoi apportare modifiche al file System dell'applicazione virtuale usando questo metodo perché l'App-V Sequencer non decodifica effettivamente il file SFT associato. Ad esempio, è possibile aprire un'applicazione virtuale esistente nella console dell'App-V Sequencer selezionando **Apri** dal menu **file** . È possibile aggiornare il **nome del pacchetto** e i **Commenti**associati ed è possibile apportare modifiche al file system virtuale e al registro di sistema virtuale. È anche possibile creare un file di Windows Installer.

Usare la procedura seguente per aggiornare un'applicazione virtuale esistente.

**Per aggiornare un'applicazione virtuale esistente**

1.  Per avviare la console App-v sequencer, nel computer in cui è in uso App-v sequencer selezionare **Avvia** / **programmi** / **Microsoft**Application Virtualization / **sequencer**.

2.  Per aprire l'applicazione virtuale esistente, nella console App-V selezionare **file** / **aperto per l'aggiornamento del pacchetto**. Usare la finestra di dialogo **Apri per l'aggiornamento del pacchetto** per individuare il file di SPRJ associato che si vuole aprire per l'aggiornamento.

3.  Per specificare la posizione in cui il pacchetto verrà decodificato, fare clic su **Sfoglia per cartella** e specificare il Q:\\. Questa è la posizione in cui verrà creata la directory radice del pacchetto come specificato nel file SFT associato. Quando si crea la versione aggiornata del pacchetto, questa verrà contrassegnata con un'aggiunta sequenziale al nome della directory, ad esempio "**.1**" verrà aggiunto al nome della directory presente nell'unità Q:\\.

4.  Per aprire la sequenziazione guidata, selezionare **strumenti** / **sequenziazione guidata**. Nella pagina **informazioni pacchetto** , facoltativamente, specificare il nuovo **nome del pacchetto** e aggiungere commenti facoltativi che verranno associati all'applicazione virtuale aggiornata. Fai clic su **Avanti**.

5.  Per iniziare il monitoraggio della nuova installazione nella pagina di **installazione di monitor** , fare clic su **Avvia monitoraggio**. Dopo aver completato il caricamento dell'ambiente virtuale, installare la versione aggiornata dell'applicazione o applicare gli aggiornamenti all'applicazione esistente. Dopo aver completato l'aggiornamento dell'applicazione virtuale, fare clic su **Interrompi monitoraggio**e quindi su **Avanti**.

6.  Nella pagina file **aggiuntivi da associare a Virtual File System (VFS)** , per specificare altri file da aggiungere al file system virtuale (VFS), fare clic su **Aggiungi**. Passare al file che si vuole aggiungere e fare clic su **Apri**. Per cancellare i file esistenti aggiunti, fare clic su **Reimposta**e quindi su **Avanti**.

7.  Nella pagina **Configura applicazioni** configurare i tasti di scelta rapida e le associazioni di tipi di file che verranno associati all'applicazione virtuale aggiornata. Selezionare l'elemento che si vuole aggiornare e quindi fare clic su **modifica posizioni**. Specificare le configurazioni nella finestra di dialogo **posizioni di scelta rapida** e quindi fare clic su **Avanti**.

8.  Nella pagina **Avvia applicazioni** , per avviare l'applicazione per verificare che il pacchetto sia ottimizzato per lo streaming, selezionare il pacchetto e fare clic su **Avvia**. Questo passaggio è utile per configurare l'esecuzione iniziale dell'applicazione nei computer di destinazione e per accettare eventuali contratti di licenza associati prima che il pacchetto venga reso disponibile ai client. Se sono presenti più applicazioni associate al pacchetto, è possibile selezionare **Avvia tutto** per aprire tutte le applicazioni. Per sequenziare la nuova versione dell'applicazione virtuale, fare clic su **Avanti**.

9.  Per completare e chiudere la sequenziazione guidata, nella pagina **Sequence Package** fare clic su **fine**.

10. Dopo aver aggiornato correttamente l'applicazione virtuale, per salvare il pacchetto, nel menu **file** della console App-V Sequencer selezionare **Salva**. È possibile accedere all'applicazione virtuale nella directory specificata nel passaggio 3.

## Argomenti correlati


[Application Virtualization Sequencer](application-virtualization-sequencer.md)

[Come eseguire l'aggiornamento di un'applicazione virtuale con la riga di comando](how-to-upgrade-a-virtual-application-by-using-the-command-line.md)

 

 





