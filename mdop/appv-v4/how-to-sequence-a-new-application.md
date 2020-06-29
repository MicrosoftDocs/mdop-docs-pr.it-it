---
title: Come sequenziare una nuova applicazione
description: Come sequenziare una nuova applicazione
author: dansimp
ms.assetid: e01e98cd-2378-478f-9739-f72c465bf79a
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: aab769256116e2635edbc4bcf55d212e3a2152f8
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10816666"
---
# <span data-ttu-id="a49a6-103">Come sequenziare una nuova applicazione</span><span class="sxs-lookup"><span data-stu-id="a49a6-103">How to Sequence a New Application</span></span>


<span data-ttu-id="a49a6-104">L'Application Virtualization (App-V) Sequencer crea applicazioni che possono essere eseguite in un ambiente virtuale.</span><span class="sxs-lookup"><span data-stu-id="a49a6-104">The Application Virtualization (App-V) Sequencer creates applications that can be run in a virtual environment.</span></span> <span data-ttu-id="a49a6-105">App-V Sequencer monitora il processo di installazione e configurazione per un'applicazione e registra le informazioni necessarie per l'esecuzione dell'applicazione in un ambiente virtuale.</span><span class="sxs-lookup"><span data-stu-id="a49a6-105">The App-V Sequencer monitors the installation and setup process for an application, and it records the information necessary for the application to run in a virtual environment.</span></span> <span data-ttu-id="a49a6-106">Puoi anche usare l'App-V Sequencer per configurare i file e le configurazioni applicabili a tutti gli utenti e i file e le configurazioni che gli utenti possono personalizzare.</span><span class="sxs-lookup"><span data-stu-id="a49a6-106">You can also use the App-V Sequencer to configure which files and configurations are applicable to all users and which files and configurations users can customize.</span></span> <span data-ttu-id="a49a6-107">Quando si sequenzia un'applicazione, è necessario salvare il pacchetto in un'unità locale del computer in cui si esegue la sequenziazione.</span><span class="sxs-lookup"><span data-stu-id="a49a6-107">When you sequence an application, you should save the package to a drive that is local to the computer you are sequencing on.</span></span>

<span data-ttu-id="a49a6-108">Un'applicazione sequenziata non interagisce con il sistema operativo perché ogni applicazione viene eseguita in un ambiente virtuale ed è isolata da altre applicazioni che potrebbero essere installate o in esecuzione nel computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="a49a6-108">A sequenced application does not interact with the operating system because each application runs in a virtual environment and is isolated from other applications that might be installed or running on the target computer.</span></span> <span data-ttu-id="a49a6-109">Questo isolamento riduce drasticamente i conflitti delle applicazioni e diminuisce la quantità necessaria di test pre-distribuzione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a49a6-109">This isolation dramatically reduces application conflicts and decreases the required amount of application pre-deployment testing.</span></span>

<span data-ttu-id="a49a6-110">Dopo aver correttamente sequenziato l'applicazione, è disponibile nella console App-V Sequencer.</span><span class="sxs-lookup"><span data-stu-id="a49a6-110">After you successfully sequence the application, it is available in the App-V Sequencer Console.</span></span> <span data-ttu-id="a49a6-111">L'uso dell'App-V Sequencer in modalità provvisoria non è supportato.</span><span class="sxs-lookup"><span data-stu-id="a49a6-111">Running the App-V sequencer in Safe Mode is not supported.</span></span>

**<span data-ttu-id="a49a6-112">Per sequenziare una nuova applicazione</span><span class="sxs-lookup"><span data-stu-id="a49a6-112">To sequence a new application</span></span>**

1.  <span data-ttu-id="a49a6-113">Devi creare l'unità di virtualizzazione dell'applicazione per sequenziare una nuova applicazione virtuale.</span><span class="sxs-lookup"><span data-stu-id="a49a6-113">You must create the Application Virtualization drive to sequence a new virtual application.</span></span> <span data-ttu-id="a49a6-114">Per creare l'unità di virtualizzazione dell'applicazione, eseguire il mapping dell'unità Q:\\ a una posizione che può essere usata per salvare i file durante la sequenziazione di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a49a6-114">To create the Application Virtualization drive, map the Q:\\ drive to a location that can be used to save files while you are sequencing an application.</span></span> <span data-ttu-id="a49a6-115">È quindi necessario creare singole directory per ogni applicazione che si prevede di sequenziare nell'unità Q:\\.</span><span class="sxs-lookup"><span data-stu-id="a49a6-115">You must then create individual directories for each application you plan to sequence on the Q:\\ drive.</span></span> <span data-ttu-id="a49a6-116">È possibile creare le cartelle di destinazione dell'applicazione virtuale prima di sequenziare un'applicazione oppure crearla nel passaggio 5 di questa procedura.</span><span class="sxs-lookup"><span data-stu-id="a49a6-116">You can create the virtual application target folders before you sequence an application, or you can create it in step 5 of this procedure.</span></span>

2.  <span data-ttu-id="a49a6-117">Per avviare la console App-v sequencer, nel computer in cui è in uso l'app-v sequencer selezionare **Avvia**  /  **programmi**  /  **Microsoft**Application Virtualization  /  **sequencer**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-117">To start the App-V Sequencer Console, on the computer that is running the App-V Sequencer, select **Start** / **Programs** / **Microsoft Application Virtualization** / **Microsoft Application Virtualization Sequencer**.</span></span> <span data-ttu-id="a49a6-118">Per avviare la **sequenziazione guidata**, selezionare **file**  /  **nuovo pacchetto**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-118">To start the **Sequencing Wizard**, select **File** / **New Package**.</span></span>

3.  <span data-ttu-id="a49a6-119">Nella pagina **informazioni pacchetto** specificare il nome del **pacchetto** che verrà assegnato all'applicazione virtuale.</span><span class="sxs-lookup"><span data-stu-id="a49a6-119">On the **Package Information** page, specify the **Package Name** that will be assigned to the virtual application.</span></span> <span data-ttu-id="a49a6-120">Il nome del pacchetto è necessario per la generazione del file di Windows Installer associato.</span><span class="sxs-lookup"><span data-stu-id="a49a6-120">The package name is required for generating the associated Windows Installer file.</span></span> <span data-ttu-id="a49a6-121">Dovresti anche aggiungere un commento facoltativo che verrà assegnato al pacchetto e che fornisce informazioni dettagliate sull'applicazione virtuale.</span><span class="sxs-lookup"><span data-stu-id="a49a6-121">You should also add an optional comment that will be assigned to the package and that provides detailed information about the virtual application.</span></span> <span data-ttu-id="a49a6-122">Per visualizzare la pagina **Opzioni avanzate** , selezionare **Mostra opzioni di monitoraggio avanzate**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-122">To display the **Advanced Options** page, select **Show Advanced Monitoring Options**.</span></span> <span data-ttu-id="a49a6-123">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-123">Click **Next**.</span></span>

    **<span data-ttu-id="a49a6-124">Nota</span><span class="sxs-lookup"><span data-stu-id="a49a6-124">Note</span></span>**  
    <span data-ttu-id="a49a6-125">Per visualizzare la pagina **Opzioni avanzate** , è necessario selezionare **Mostra opzioni di monitoraggio avanzate**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-125">To display the **Advanced Options** page, you must select **Show Advanced Monitoring Options**.</span></span> <span data-ttu-id="a49a6-126">Se non è necessaria la pagina **Opzioni avanzate** , passare al passaggio 4.</span><span class="sxs-lookup"><span data-stu-id="a49a6-126">If you do not require the **Advanced Options** page, skip to step 4.</span></span>



4.  <span data-ttu-id="a49a6-127">Nella pagina **Opzioni avanzate** per specificare le dimensioni del **blocco** per l'applicazione virtuale, selezionare le dimensioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="a49a6-127">On the **Advanced Options** page, to specify the **Block Size** for the virtual application, select the size you want.</span></span> <span data-ttu-id="a49a6-128">La dimensione del blocco determina il modo in cui verrà suddiviso il file **. SFT** per lo streaming del pacchetto in rete per i computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="a49a6-128">The block size determines how the **.sft** file will be divided for streaming the package across the network to target computers.</span></span> <span data-ttu-id="a49a6-129">Per consentire a Microsoft Update di aggiornare l'applicazione man mano che viene sequenziata; Selezionare **Consenti l'esecuzione di Microsoft Update durante il monitoraggio**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-129">To allow Microsoft Update to update the application as it is being sequenced; select **Allow Microsoft Update to run during monitoring**.</span></span> <span data-ttu-id="a49a6-130">Se si seleziona questa opzione, gli aggiornamenti di Microsoft possono essere installati durante la fase di monitoraggio e sarà necessario accettare gli aggiornamenti associati per l'installazione.</span><span class="sxs-lookup"><span data-stu-id="a49a6-130">If you select this option, Microsoft Updates are allowed to be installed during the monitoring phase and you will need to accept the associated updates for them to be installed.</span></span> <span data-ttu-id="a49a6-131">Per rimappare i file dll (Dynamic Link Library) supportati in modo che usino uno spazio di RAM contiguo, selezionare **rebase dll**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-131">To remap the supported dynamic link library (.dll) files so that they use a contiguous space of RAM, select **Rebase DLLs**.</span></span> <span data-ttu-id="a49a6-132">Se si seleziona questa opzione, è possibile risparmiare memoria e migliorare le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="a49a6-132">Selecting this option can conserve memory and help improve performance.</span></span> <span data-ttu-id="a49a6-133">Molte applicazioni non supportano questa opzione, ma è utile in ambienti con RAM limitata, ad esempio in scenari Terminal Server.</span><span class="sxs-lookup"><span data-stu-id="a49a6-133">Many applications do not support this option, but it is useful in environments with limited RAM such as in Terminal Server scenarios.</span></span> <span data-ttu-id="a49a6-134">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-134">Click **Next**.</span></span>

5.  <span data-ttu-id="a49a6-135">Nella pagina di **installazione di monitor** , per monitorare l'installazione di un'applicazione, fare clic su **Avvia monitoraggio**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-135">On the **Monitor Installation** page, to monitor the installation of an application, click **Begin Monitoring**.</span></span> <span data-ttu-id="a49a6-136">Dopo aver fatto clic su **Avvia monitoraggio**, specificare la directory nell'unità Q:\\ in cui verrà installata l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a49a6-136">After you click **Begin Monitoring**, specify the directory on the Q:\\ drive where the application will be installed.</span></span> <span data-ttu-id="a49a6-137">Per installare l'applicazione in una cartella che non è stata creata, fare clic su **Crea nuova cartella**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-137">To install the application to a folder that has not been created, click **Make New Folder**.</span></span> <span data-ttu-id="a49a6-138">È necessario installare ogni applicazione sequenziata in una directory separata.</span><span class="sxs-lookup"><span data-stu-id="a49a6-138">You must install each application that you sequence into a separate directory.</span></span>

    **<span data-ttu-id="a49a6-139">Importante</span><span class="sxs-lookup"><span data-stu-id="a49a6-139">Important</span></span>**  
    <span data-ttu-id="a49a6-140">Il nome della cartella specificato non deve contenere più di 8 caratteri.</span><span class="sxs-lookup"><span data-stu-id="a49a6-140">The folder name you specify must not be longer than 8 characters.</span></span>



~~~
Wait for the virtual environment to load, and then install the application so that the App-V Sequencer can monitor the process. When you have completed the installation, click **Stop Monitoring** and then click **Next**.
~~~

6. <span data-ttu-id="a49a6-141">Nella pagina file **aggiuntivi da associare a Virtual File System (VFS)** , per specificare altri file da aggiungere al file system virtuale (VFS), fare clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-141">On the **Additional Files to Map to Virtual File System (VFS)** page, to specify additional files to be added to the Virtual File System (VFS), click **Add**.</span></span> <span data-ttu-id="a49a6-142">Passare al file che si vuole aggiungere e fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-142">Browse to the file you want to add, and click **Open**.</span></span> <span data-ttu-id="a49a6-143">Per cancellare i file esistenti aggiunti, fare clic su **Reimposta** e quindi su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-143">To clear existing files that have been added, click **Reset** and then click **Next**.</span></span>

7. <span data-ttu-id="a49a6-144">Nella pagina **Configura applicazioni** configurare i tasti di scelta rapida e le associazioni di tipi di file che verranno associati all'applicazione virtuale.</span><span class="sxs-lookup"><span data-stu-id="a49a6-144">On the **Configure Applications** page, configure the shortcuts and file type associations that will be associated with the virtual application.</span></span> <span data-ttu-id="a49a6-145">Selezionare l'elemento che si vuole aggiornare e quindi fare clic su **modifica posizioni**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-145">Select the element you want to update, and then click **Edit Locations**.</span></span> <span data-ttu-id="a49a6-146">Specificare le configurazioni nella finestra di dialogo **posizioni di scelta rapida** .</span><span class="sxs-lookup"><span data-stu-id="a49a6-146">Specify the configurations in the **Shortcut Locations** dialog box.</span></span> <span data-ttu-id="a49a6-147">Fare clic su **OK** e quindi su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-147">Click **OK** and then click **Next**.</span></span>

8. <span data-ttu-id="a49a6-148">Nella pagina **Avvia applicazioni** , per avviare l'applicazione per verificare che il pacchetto sia ottimizzato per lo streaming, selezionare il pacchetto e fare clic su **Avvia**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-148">On the **Launch Applications** page, to start the application to ensure that the package is optimized for streaming, select the package and click **Launch**.</span></span> <span data-ttu-id="a49a6-149">Questo passaggio è utile per configurare l'esecuzione iniziale dell'applicazione nei computer di destinazione e per accettare eventuali contratti di licenza associati prima che il pacchetto venga reso disponibile ai client.</span><span class="sxs-lookup"><span data-stu-id="a49a6-149">This step is useful for configuring how the application initially runs on target computers and for accepting any associated license agreements before the package is made available to clients.</span></span> <span data-ttu-id="a49a6-150">Se sono presenti più applicazioni associate al pacchetto, è possibile selezionare **Avvia tutto** per aprire tutte le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="a49a6-150">If there are multiple applications associated with this package, you can select **Launch All** to open all of the applications.</span></span> <span data-ttu-id="a49a6-151">Per sequenziare il pacchetto, fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-151">To sequence the package, click **Next**.</span></span>

9. <span data-ttu-id="a49a6-152">Nella pagina **Sequence Package** , per chiudere la procedura guidata, fare clic su **fine**.</span><span class="sxs-lookup"><span data-stu-id="a49a6-152">On the **Sequence Package** page, to close the wizard, click **Finish**.</span></span>

10. <span data-ttu-id="a49a6-153">Dopo aver creato il pacchetto, per salvare il pacchetto, nella console App-V Sequencer selezionare **File**  /  **Salva** file e specificare il nome e il percorso in cui verrà salvato il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="a49a6-153">After you have successfully created the package, to save the package, in the App-V Sequencer Console, select **File** / **Save** and specify the name and the location where the package will be saved.</span></span>

## <span data-ttu-id="a49a6-154">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="a49a6-154">Related topics</span></span>


[<span data-ttu-id="a49a6-155">Attività per Application Virtualization Sequencer</span><span class="sxs-lookup"><span data-stu-id="a49a6-155">Tasks for the Application Virtualization Sequencer</span></span>](tasks-for-the-application-virtualization-sequencer.md)








