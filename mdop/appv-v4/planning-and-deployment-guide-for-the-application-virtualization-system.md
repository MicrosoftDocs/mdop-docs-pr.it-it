---
title: Guida alla pianificazione e alla distribuzione per il sistema di virtualizzazione delle applicazioni
description: Guida alla pianificazione e alla distribuzione per il sistema di virtualizzazione delle applicazioni
author: dansimp
ms.assetid: 6c012e33-9ac6-4cd8-84ff-54f40973833f
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 10bcac26fddae2f0e5826dbd7335adda06d3987e
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10815956"
---
# <span data-ttu-id="77921-103">Guida alla pianificazione e alla distribuzione per il sistema di virtualizzazione delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="77921-103">Planning and Deployment Guide for the Application Virtualization System</span></span>


<span data-ttu-id="77921-104">Microsoft Application Virtualization Management offre la possibilità di rendere le applicazioni disponibili per i computer degli utenti finali senza dover installare le applicazioni direttamente in tali computer.</span><span class="sxs-lookup"><span data-stu-id="77921-104">Microsoft Application Virtualization Management provides the capability to make applications available to end user computers without having to install the applications directly on those computers.</span></span> <span data-ttu-id="77921-105">Ciò viene reso possibile tramite un processo noto come *sequenziamento dell'applicazione*, che consente l'esecuzione di ogni applicazione nel proprio ambiente virtuale autonomo nel computer client.</span><span class="sxs-lookup"><span data-stu-id="77921-105">This is made possible through a process known as *sequencing the application*, which enables each application to run in its own self-contained virtual environment on the client computer.</span></span> <span data-ttu-id="77921-106">Le applicazioni sequenziate vengono isolate l'una dall'altra, eliminando i conflitti tra applicazioni, ma possono comunque interagire con il computer client.</span><span class="sxs-lookup"><span data-stu-id="77921-106">The sequenced applications are isolated from one another, eliminating application conflicts, yet can still interact with the client computer.</span></span>

<span data-ttu-id="77921-107">Application Virtualization Client è il componente del sistema di virtualizzazione dell'applicazione che consente all'utente finale di interagire con le applicazioni dopo che sono state pubblicate nel computer.</span><span class="sxs-lookup"><span data-stu-id="77921-107">The Application Virtualization Client is the Application Virtualization system component that enables the end user to interact with the applications after they have been published to the computer.</span></span> <span data-ttu-id="77921-108">Il client gestisce l'ambiente virtuale in cui vengono eseguite le applicazioni virtualizzate in ogni computer.</span><span class="sxs-lookup"><span data-stu-id="77921-108">The client manages the virtual environment in which the virtualized applications run on each computer.</span></span> <span data-ttu-id="77921-109">Dopo l'installazione del client in un computer, le applicazioni devono essere messe a disposizione del computer tramite un processo noto come *pubblicazione*, che consente all'utente finale di eseguire le applicazioni virtuali.</span><span class="sxs-lookup"><span data-stu-id="77921-109">After the client has been installed on a computer, the applications must be made available to the computer through a process known as *publishing*, which enables the end user to run the virtual applications.</span></span> <span data-ttu-id="77921-110">Il processo di pubblicazione colloca le icone e i tasti di scelta rapida dell'applicazione virtuale nel computer, in genere nel desktop di Windows o nel menu **Start** , e inserisce anche le informazioni di associazione per la definizione del pacchetto e il tipo di file nel computer.</span><span class="sxs-lookup"><span data-stu-id="77921-110">The publishing process places the virtual application icons and shortcuts on the computer—typically on the Windows desktop or on the **Start** menu—and also places the package definition and file type association information on the computer.</span></span> <span data-ttu-id="77921-111">La pubblicazione rende inoltre disponibile il contenuto del pacchetto dell'applicazione per il computer dell'utente finale.</span><span class="sxs-lookup"><span data-stu-id="77921-111">Publishing also makes the application package content available to the end user’s computer.</span></span>

<span data-ttu-id="77921-112">Il contenuto del pacchetto dell'applicazione virtuale può essere inserito in uno o più server di virtualizzazione dell'applicazione in modo che possa essere trasmesso ai client su richiesta e memorizzato nella cache localmente.</span><span class="sxs-lookup"><span data-stu-id="77921-112">The virtual application package content can be placed on one or more Application Virtualization servers so that it can be streamed down to the clients on demand and cached locally.</span></span> <span data-ttu-id="77921-113">I server di file e i server Web possono essere usati anche come server di streaming oppure il contenuto può essere posizionato direttamente nel computer dell'utente finale, ad esempio se si usa un sistema di distribuzione del software elettronico, come Microsoft endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="77921-113">File servers and Web servers can also be used as streaming servers, or the content can be placed directly on the end user’s computer—for example, if you are using an electronic software distribution system, such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="77921-114">In un'implementazione multiserver, il mantenimento del contenuto del pacchetto e la sua conservazione aggiornata in tutti i server di flusso richiedono una soluzione di gestione dei pacchetti completa.</span><span class="sxs-lookup"><span data-stu-id="77921-114">In a multi-server implementation, maintaining the package content and keeping it up to date on all the streaming servers requires a comprehensive package management solution.</span></span> <span data-ttu-id="77921-115">A seconda delle dimensioni dell'organizzazione, potrebbe essere necessario disporre di molte applicazioni virtuali accessibili per gli utenti finali dislocati in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="77921-115">Depending on the size of your organization, you might need to have many virtual applications accessible to end users located all over the world.</span></span> <span data-ttu-id="77921-116">La gestione dei pacchetti per garantire che le applicazioni giuste siano disponibili per tutti gli utenti dove e quando è necessario accedervi è quindi un requisito essenziale.</span><span class="sxs-lookup"><span data-stu-id="77921-116">Managing the packages to ensure that the right applications are available to all users where and when they need access to them is therefore an essential requirement.</span></span>

<span data-ttu-id="77921-117">La guida alla pianificazione e distribuzione di Application Virtualization offre informazioni utili per comprendere meglio e distribuire l'applicazione Microsoft Application Virtualization e i relativi componenti.</span><span class="sxs-lookup"><span data-stu-id="77921-117">The Application Virtualization Planning and Deployment Guide provides information to help you better understand and deploy the Microsoft Application Virtualization application and its components.</span></span> <span data-ttu-id="77921-118">Vengono inoltre fornite procedure dettagliate per l'implementazione degli scenari di distribuzione principali.</span><span class="sxs-lookup"><span data-stu-id="77921-118">It also provides step-by-step procedures for implementing the key deployment scenarios.</span></span>

## <span data-ttu-id="77921-119">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="77921-119">In This Section</span></span>


<a href="" id="planning-for-application-virtualization-system-deployment"></a>[<span data-ttu-id="77921-120">Pianificazione della distribuzione del sistema Application Virtualization</span><span class="sxs-lookup"><span data-stu-id="77921-120">Planning for Application Virtualization System Deployment</span></span>](planning-for-application-virtualization-system-deployment.md)  
<span data-ttu-id="77921-121">Fornisce le indicazioni necessarie per pianificare l'implementazione e la distribuzione del sistema di virtualizzazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="77921-121">Provides the guidance necessary to plan the implementation and deployment of your Application Virtualization system.</span></span>

<a href="" id="application-virtualization-deployment-and-upgrade-considerations"></a>[<span data-ttu-id="77921-122">Considerazioni sull'aggiornamento e la distribuzione di Application Virtualization</span><span class="sxs-lookup"><span data-stu-id="77921-122">Application Virtualization Deployment and Upgrade Considerations</span></span>](application-virtualization-deployment-and-upgrade-considerations.md)  
<span data-ttu-id="77921-123">Fornisce informazioni sui requisiti hardware e software per installare i vari componenti di virtualizzazione delle applicazioni, nonché le informazioni sull'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="77921-123">Provides information about hardware and software requirements for installing the various Application Virtualization components, as well as upgrade information.</span></span>

<a href="" id="electronic-software-distribution-based-scenario"></a>[<span data-ttu-id="77921-124">Scenario basato sulla distribuzione elettronica del software</span><span class="sxs-lookup"><span data-stu-id="77921-124">Electronic Software Distribution-Based Scenario</span></span>](electronic-software-distribution-based-scenario.md)  
<span data-ttu-id="77921-125">Fornisce informazioni sulla distribuzione della virtualizzazione delle applicazioni tramite un sistema ESD (Electronic Software Distribution).</span><span class="sxs-lookup"><span data-stu-id="77921-125">Provides information about deploying Application Virtualization using an electronic software distribution (ESD) system.</span></span>

<a href="" id="application-virtualization-server-based-scenario"></a>[<span data-ttu-id="77921-126">Scenario basato su Application Virtualization Server</span><span class="sxs-lookup"><span data-stu-id="77921-126">Application Virtualization Server-Based Scenario</span></span>](application-virtualization-server-based-scenario.md)  
<span data-ttu-id="77921-127">Fornisce informazioni sulla distribuzione della virtualizzazione delle applicazioni con Application Virtualization Management Server.</span><span class="sxs-lookup"><span data-stu-id="77921-127">Provides information about deploying Application Virtualization using the Application Virtualization Management Server.</span></span>

<a href="" id="stand-alone-delivery-scenario-for-application-virtualization-clients"></a>[<span data-ttu-id="77921-128">Scenario di recapito autonomo per i Application Virtualization Client</span><span class="sxs-lookup"><span data-stu-id="77921-128">Stand-Alone Delivery Scenario for Application Virtualization Clients</span></span>](stand-alone-delivery-scenario-for-application-virtualization-clients.md)  
<span data-ttu-id="77921-129">Descrive come distribuire la virtualizzazione delle applicazioni in una modalità autonoma, senza l'uso di ESD o risorse basate su server.</span><span class="sxs-lookup"><span data-stu-id="77921-129">Describes how to deploy Application Virtualization in a stand-alone mode, without the use of ESD or server-based resources.</span></span>

<a href="" id="application-virtualization-reference"></a>[<span data-ttu-id="77921-130">Riferimento per Application Virtualization</span><span class="sxs-lookup"><span data-stu-id="77921-130">Application Virtualization Reference</span></span>](application-virtualization-reference.md)  
<span data-ttu-id="77921-131">Contiene materiale dettagliato di riferimento tecnico relativo all'installazione e alla gestione dei componenti di sistema.</span><span class="sxs-lookup"><span data-stu-id="77921-131">Contains detailed technical reference material related to installing and managing system components.</span></span>

 

 




