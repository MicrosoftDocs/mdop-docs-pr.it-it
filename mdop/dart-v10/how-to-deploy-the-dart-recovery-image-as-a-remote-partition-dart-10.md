---
title: Come distribuire l'immagine di ripristino di DaRT come partizione remota
description: Come distribuire l'immagine di ripristino di DaRT come partizione remota
author: dansimp
ms.assetid: 06a5e250-b992-4f6a-ad74-e7715f9e96e7
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: support
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: 3cdb1313a64bacd652a5253c09f36fa792d0fa3c
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10804696"
---
# Come distribuire l'immagine di ripristino di DaRT come partizione remota


Dopo aver eseguito la creazione guidata immagine di ripristino di Microsoft Diagnostics and Recovery Toolset (DaRT) 10 e aver creato l'immagine di ripristino, è possibile estrarre il file Boot. wim dal file di immagine ISO e distribuirlo come partizione remota nella rete.

**Per distribuire il dardo 10 come partizione remota**

1.  Estrarre il file Boot. wim dal file di immagine ISO DaRT.

    1.  Montare il file di immagine ISO creato nella finestra di dialogo **Crea immagine di avvio** usando il metodo preferito della società per il montaggio di un'immagine.

    2.  Aprire il file di immagine ISO e copiare il file Boot. wim dalla cartella \\sources nell'immagine montata in una posizione nel computer o in un'unità esterna.

        **Nota**  Se si è masterizzato un CD o un DVD dell'immagine di ripristino, è possibile aprire i file nel CD o nel DVD e copiare il file Boot. wim dalla cartella \\sources. In questo modo è possibile ignorare la necessità di montare l'immagine.

         

2.  Distribuire il file Boot. wim in un server WDS a cui è possibile accedere dai computer degli utenti finali dell'organizzazione.

3.  Configurare il server WDS per usare il file Boot. wim per DaRT seguendo le procedure di distribuzione di WDS standard.

Per altre informazioni su come distribuire il dardo come partizione remota, vedere [procedura dettagliata: distribuire un'immagine usando la](https://go.microsoft.com/fwlink/?LinkId=212108) [Guida introduttiva di servizi di distribuzione](https://go.microsoft.com/fwlink/?LinkId=212106)di PXE e Windows.

## Argomenti correlati


[Creazione dell'immagine di ripristino di DaRT 10](creating-the-dart-10-recovery-image.md)

[Distribuzione dell'immagine di ripristino di DaRT](deploying-the-dart-recovery-image-dart-10.md)

[Pianificazione di DaRT 10](planning-for-dart-10.md)

 

 





