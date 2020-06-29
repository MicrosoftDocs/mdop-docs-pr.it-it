---
title: Eseguire il rollback a una versione precedente di un oggetto Criteri di gruppo
description: Eseguire il rollback a una versione precedente di un oggetto Criteri di gruppo
author: dansimp
ms.assetid: 06ce9251-95e0-46d0-99c2-b9a0690e5891
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 1146a8ecaf25796b9ac105ba46ea7f27b06fc8aa
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820275"
---
# <span data-ttu-id="81a64-103">Eseguire il rollback a una versione precedente di un oggetto Criteri di gruppo</span><span class="sxs-lookup"><span data-stu-id="81a64-103">Roll Back to an Earlier Version of a GPO</span></span>


<span data-ttu-id="81a64-104">Un responsabile approvazione può eseguire il rollback delle modifiche apportate a un oggetto Criteri di gruppo ridistribuendo una versione precedente del GPO dalla cronologia.</span><span class="sxs-lookup"><span data-stu-id="81a64-104">An Approver can roll back changes to a Group Policy Object (GPO) by redeploying an earlier version of the GPO from its history.</span></span> <span data-ttu-id="81a64-105">La distribuzione di una versione precedente di un oggetto Criteri di controllo sovrascrive la versione del GPO attualmente in produzione.</span><span class="sxs-lookup"><span data-stu-id="81a64-105">Deploying an earlier version of a GPO overwrites the version of the GPO currently in production.</span></span>

<span data-ttu-id="81a64-106">Per completare questa procedura è necessario un account utente con l'approvatore o l'amministratore della gestione avanzata Criteri di gruppo (controllo completo) o le autorizzazioni necessarie in Advanced Group Policy Management per il completamento.</span><span class="sxs-lookup"><span data-stu-id="81a64-106">A user account with the Approver or AGPM Administrator (Full Control) role or necessary permissions in Advanced Group Policy Management (AGPM) is required to complete this procedure.</span></span> <span data-ttu-id="81a64-107">Esaminare i dettagli in "considerazioni aggiuntive" in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="81a64-107">Review the details in "Additional considerations" in this topic.</span></span>

**<span data-ttu-id="81a64-108">Per distribuire una versione precedente di un GPO nell'ambiente di produzione del dominio</span><span class="sxs-lookup"><span data-stu-id="81a64-108">To deploy an earlier version of a GPO to the production environment of the domain</span></span>**

1.  <span data-ttu-id="81a64-109">Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.</span><span class="sxs-lookup"><span data-stu-id="81a64-109">In the **Group Policy Management Console** tree, click **Change Control** in the forest and domain in which you want to manage GPOs.</span></span>

2.  <span data-ttu-id="81a64-110">Nella scheda **contenuto** fare clic sulla scheda **controllati** per visualizzare gli oggetti Criteri di controllo controllati.</span><span class="sxs-lookup"><span data-stu-id="81a64-110">On the **Contents** tab, click the **Controlled** tab to display the controlled GPOs.</span></span>

3.  <span data-ttu-id="81a64-111">Fare doppio clic sul GPO da distribuire per visualizzarne la **cronologia**.</span><span class="sxs-lookup"><span data-stu-id="81a64-111">Double-click the GPO to be deployed to display its **History**.</span></span>

4.  <span data-ttu-id="81a64-112">Fare clic con il pulsante destro del mouse sulla versione da distribuire, scegliere **Distribuisci**e quindi fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="81a64-112">Right-click the version to be deployed, click **Deploy**, and then click **Yes**.</span></span>

5.  <span data-ttu-id="81a64-113">Quando la finestra di **stato** indica che lo stato di avanzamento complessivo è stato completato, fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="81a64-113">When the **Progress** window indicates that overall progress is complete, click **Close**.</span></span> <span data-ttu-id="81a64-114">Nella finestra **cronologia** fare clic su **Chiudi**.</span><span class="sxs-lookup"><span data-stu-id="81a64-114">In the **History** window, click **Close**.</span></span>

<span data-ttu-id="81a64-115">**Nota**  Per verificare che la versione ridistribuita corrisponda alla versione progettata, esaminare un report di differenza per le due versioni.</span><span class="sxs-lookup"><span data-stu-id="81a64-115">**Note** To verify that the version that has been redeployed matches the version intended, examine a difference report for the two versions.</span></span> <span data-ttu-id="81a64-116">Nella finestra **cronologia** per l'oggetto Criteri di ricerca evidenziare le due versioni, quindi fare clic con il pulsante destro del mouse e scegliere **differenza** e report **HTML** o **report XML**.</span><span class="sxs-lookup"><span data-stu-id="81a64-116">In the **History** window for the GPO, highlight the two versions, and then right-click and select **Difference** and either **HTML Report** or **XML Report**.</span></span>

 

### <span data-ttu-id="81a64-117">Considerazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="81a64-117">Additional considerations</span></span>

-   <span data-ttu-id="81a64-118">Per impostazione predefinita, per eseguire questa procedura è necessario essere un approvatore o un amministratore Advanced Group Policy Management (controllo completo).</span><span class="sxs-lookup"><span data-stu-id="81a64-118">By default, you must be an Approver or an AGPM Administrator (Full Control) to perform this procedure.</span></span> <span data-ttu-id="81a64-119">In particolare, devi avere il **contenuto dell'elenco** e distribuire le autorizzazioni **GPO** per l'oggetto Criteri di ricerca.</span><span class="sxs-lookup"><span data-stu-id="81a64-119">Specifically, you must have **List Contents** and **Deploy GPO** permissions for the GPO.</span></span>

### <span data-ttu-id="81a64-120">Riferimenti aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="81a64-120">Additional references</span></span>

-   [<span data-ttu-id="81a64-121">Attività del responsabile approvazione</span><span class="sxs-lookup"><span data-stu-id="81a64-121">Performing Approver Tasks</span></span>](performing-approver-tasks-agpm40.md)

 

 




