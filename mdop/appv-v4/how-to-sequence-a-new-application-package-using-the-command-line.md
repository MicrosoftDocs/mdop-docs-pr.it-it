---
title: Come sequenziare un nuovo pacchetto di applicazione usando la riga di comando
description: Come sequenziare un nuovo pacchetto di applicazione usando la riga di comando
author: dansimp
ms.assetid: de72912b-d9e7-45b5-a601-12528f1a4cac
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 2dd638a7e4765cedbf1d8050626fb8cc54b2ce8b
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10816676"
---
# <span data-ttu-id="9cbef-103">Come sequenziare un nuovo pacchetto di applicazione usando la riga di comando</span><span class="sxs-lookup"><span data-stu-id="9cbef-103">How to Sequence a New Application Package Using the Command Line</span></span>


<span data-ttu-id="9cbef-104">Puoi usare una riga di comando per sequenziare una nuova applicazione.</span><span class="sxs-lookup"><span data-stu-id="9cbef-104">You can use a command line to sequence a new application.</span></span> <span data-ttu-id="9cbef-105">L'uso di una riga di comando è utile quando è necessario creare un numero elevato di applicazioni virtuali o quando è necessario creare applicazioni sequenziate su base periodica.</span><span class="sxs-lookup"><span data-stu-id="9cbef-105">Using a command line is useful when you have to create a large number of virtual applications or when you need to create sequenced applications on a recurring basis.</span></span>

**<span data-ttu-id="9cbef-106">Importante</span><span class="sxs-lookup"><span data-stu-id="9cbef-106">Important</span></span>**  
<span data-ttu-id="9cbef-107">La sequenziazione della riga di comando consente solo la sequenziazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="9cbef-107">Command-line sequencing allows for default sequencing only.</span></span> <span data-ttu-id="9cbef-108">Se è necessario modificare le impostazioni di installazione predefinite per l'applicazione che si sta sequenziando, è necessario modificare manualmente l'applicazione virtuale o aggiornare l'applicazione virtuale tramite Application Virtualization (App-V) Sequencer.</span><span class="sxs-lookup"><span data-stu-id="9cbef-108">If you need to change default installation settings for the application you are sequencing, you must either manually modify the virtual application or update the virtual application by using the Application Virtualization (App-V) Sequencer.</span></span> <span data-ttu-id="9cbef-109">Per altre informazioni sull'aggiornamento di un'applicazione virtuale tramite App-V Sequencer, vedere [come aggiornare un'applicazione virtuale esistente](how-to-upgrade-an-existing-virtual-application.md).</span><span class="sxs-lookup"><span data-stu-id="9cbef-109">For more information about updating a virtual application by using the App-V Sequencer, see [How to Upgrade an Existing Virtual Application](how-to-upgrade-an-existing-virtual-application.md).</span></span>



<span data-ttu-id="9cbef-110">Usare la procedura seguente per creare un'applicazione virtuale tramite la riga di comando.</span><span class="sxs-lookup"><span data-stu-id="9cbef-110">Use the following procedure to create a virtual application by using the command line.</span></span>

**<span data-ttu-id="9cbef-111">Per sequenziare un'applicazione usando la riga di comando</span><span class="sxs-lookup"><span data-stu-id="9cbef-111">To sequence an application by using the command line</span></span>**

1.  <span data-ttu-id="9cbef-112">Nel computer in cui è in esecuzione l'App-V Sequencer aprire il prompt dei comandi selezionando **Start**, **Esegui**e quindi digitare **cmd**.</span><span class="sxs-lookup"><span data-stu-id="9cbef-112">On the computer that is running the App-V Sequencer, open the command prompt by selecting **Start**, **Run**, and then type **cmd**.</span></span> <span data-ttu-id="9cbef-113">Fai clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="9cbef-113">Click **OK**.</span></span>

2.  <span data-ttu-id="9cbef-114">Usare il prompt dei comandi per specificare la posizione in cui è installato l'App-V Sequencer.</span><span class="sxs-lookup"><span data-stu-id="9cbef-114">Use the command prompt to specify the location of where the App-V Sequencer is installed.</span></span> <span data-ttu-id="9cbef-115">Ad esempio, al prompt dei comandi digitare quanto segue: **CD C:\\Programmi \\Programmi\\microsoft Application Virtualization Sequencer**.</span><span class="sxs-lookup"><span data-stu-id="9cbef-115">For example, at the command prompt, you could type the following: **cd C:\\Program Files\\Microsoft Application Virtualization Sequencer**.</span></span>

3.  <span data-ttu-id="9cbef-116">Al prompt dei comandi digitare il comando seguente, sostituendo il testo tra virgolette con i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="9cbef-116">At the command prompt, type the following command, replacing the text in quotation marks with your values:</span></span>

    `SFTSequencer /INSTALLPACKAGE:"pathtoMSI" /INSTALLPATH:"pathtopackageroot" /OUTPUTFILE:"pathtodestinationSPRJ"`

    **<span data-ttu-id="9cbef-117">Nota</span><span class="sxs-lookup"><span data-stu-id="9cbef-117">Note</span></span>**  
    <span data-ttu-id="9cbef-118">Puoi specificare parametri aggiuntivi usando la riga di comando, a seconda della complessità dell'applicazione che stai sequenziando.</span><span class="sxs-lookup"><span data-stu-id="9cbef-118">You can specify additional parameters by using the command line, depending on the complexity of the application you are sequencing.</span></span> <span data-ttu-id="9cbef-119">Per un elenco completo dei parametri disponibili per l'uso con l'App-V Sequencer, vedi la [riga di comando Application Virtualization Sequencer](application-virtualization-sequencer-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="9cbef-119">For a complete list of parameters that are available for use with the App-V Sequencer, see [Application Virtualization Sequencer Command Line](application-virtualization-sequencer-command-line.md).</span></span>



~~~
Use the value descriptions in the following table to help you determine the actual text you will use in the preceding command.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Value</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><em>pathtoMSI</em></p></td>
<td align="left"><p>Specifies the Windows Installer or a batch file that will be used to install an application so that it can be sequenced.</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>pathtopackageroot</em></p></td>
<td align="left"><p>Specifies the package root directory.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>pathtodestinationSPRJ</em></p></td>
<td align="left"><p>Specifies the path and file name of the SPRJ file that will be created.</p></td>
</tr>
</tbody>
</table>
~~~



4. <span data-ttu-id="9cbef-120">Premere **invio**.</span><span class="sxs-lookup"><span data-stu-id="9cbef-120">Press **Enter**.</span></span>

## <span data-ttu-id="9cbef-121">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="9cbef-121">Related topics</span></span>


[<span data-ttu-id="9cbef-122">Come gestire le applicazioni virtuali usando la riga di comando</span><span class="sxs-lookup"><span data-stu-id="9cbef-122">How to Manage Virtual Applications Using the Command Line</span></span>](how-to-manage-virtual-applications-using-the-command-line.md)








