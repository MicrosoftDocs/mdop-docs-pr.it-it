---
title: Usare l'ambiente di test
description: Usare l'ambiente di test
author: dansimp
ms.assetid: 86295084-b39e-4040-bb3f-15c3c1e99b1a
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 1264d9fe6f922a7e61bcd069581c7bd5e39b7787
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10818236"
---
# Usare l'ambiente di test


Se si usa un'unità organizzativa testing (OU) per testare gli oggetti Criteri di gruppo prima della distribuzione nell'ambiente di produzione, è necessario disporre delle autorizzazioni necessarie per accedere all'unità organizzativa di test. L'uso di un'unità organizzativa di test è facoltativo.

**Per usare un'unità organizzativa di test**

1.  Durante l'estrazione del GPO per la modifica, nella **console Gestione criteri di gruppo**fare clic su **oggetti Criteri di gruppo** nella foresta e nel dominio in cui si gestiscono i GPO.

2.  Fare clic sulla copia estratta dell'oggetto Criteri di controllo da testare. Il nome verrà preceduto da **\ [Estratto \]**. Se non è elencato, fare clic su **azione**e quindi su **Aggiorna**. Ordinare i nomi in ordine alfabetico e **\ [Estratto \]** i GPO verranno in genere visualizzati nella parte superiore dell'elenco.

3.  Trascinare e rilasciare il GPO nell'unità organizzativa di test.

4.  Fare clic su **OK** nella finestra di dialogo in cui viene chiesto se creare un collegamento al GPO nell'UO di test.

### Considerazioni aggiuntive

-   Al termine del test, il controllo nel GPO Elimina automaticamente il collegamento alla copia Estratto del GPO.

### Riferimenti aggiuntivi

-   [Modifica di un oggetto Criteri di gruppo](editing-a-gpo-agpm30ops.md)

 

 





