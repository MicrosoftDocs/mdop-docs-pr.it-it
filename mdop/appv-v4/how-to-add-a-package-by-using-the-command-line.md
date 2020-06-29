---
title: Come aggiungere un pacchetto con la riga di comando
description: Come aggiungere un pacchetto con la riga di comando
author: dansimp
ms.assetid: e75af49e-811a-407a-a7f0-6de8562b9188
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: ab418017a075300f308d4ef4c6eceb4f623a05c7
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10821406"
---
# <span data-ttu-id="0a435-103">Come aggiungere un pacchetto con la riga di comando</span><span class="sxs-lookup"><span data-stu-id="0a435-103">How to Add a Package by Using the Command Line</span></span>


<span data-ttu-id="0a435-104">Le procedure seguenti elencano i passaggi necessari per aggiungere un pacchetto di applicazione virtuale al client Application Virtualization (App-V) in un computer specifico.</span><span class="sxs-lookup"><span data-stu-id="0a435-104">The following procedures list the steps that are necessary to add a virtual application package to the Application Virtualization (App-V) Client on a specific computer.</span></span>

**<span data-ttu-id="0a435-105">Per aggiungere un pacchetto di applicazione virtuale per un utente specifico</span><span class="sxs-lookup"><span data-stu-id="0a435-105">To add a virtual application package for a specific user</span></span>**

-   <span data-ttu-id="0a435-106">Eseguire il comando seguente sotto l'account utente della persona che deve ottenere il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="0a435-106">Run the following command under the user account of the person who is to get the package.</span></span> <span data-ttu-id="0a435-107">Il comando aggiunge e pubblica il pacchetto per l'utente.</span><span class="sxs-lookup"><span data-stu-id="0a435-107">The command adds and publishes the package for that user.</span></span>

    `SFTMIME ADD PACKAGE:”name” /MANIFEST <manifest-path>`

**<span data-ttu-id="0a435-108">Per aggiungere un pacchetto di applicazione virtuale per tutti gli utenti</span><span class="sxs-lookup"><span data-stu-id="0a435-108">To add a virtual application package for all users</span></span>**

-   <span data-ttu-id="0a435-109">Eseguire il comando seguente in un account con diritti di amministratore.</span><span class="sxs-lookup"><span data-stu-id="0a435-109">Run the following command under an account that has administrator rights.</span></span> <span data-ttu-id="0a435-110">Il pacchetto viene aggiunto e pubblicato per tutti gli utenti nel computer.</span><span class="sxs-lookup"><span data-stu-id="0a435-110">The package is added and published for all users on the computer.</span></span>

    `SFTMIME ADD PACKAGE:”name” /MANIFEST <manifest-path> /GLOBAL`

**<span data-ttu-id="0a435-111">Per aggiungere un pacchetto usando un sistema di distribuzione elettronica del software</span><span class="sxs-lookup"><span data-stu-id="0a435-111">To add a package using an electronic software distribution system</span></span>**

1.  <span data-ttu-id="0a435-112">Se si usa un sistema di distribuzione del software elettronico che esegue i comandi sotto l'account di **sistema** del computer, il pacchetto viene pubblicato solo per l'account, a meno che non si usi l'opzione/Global.</span><span class="sxs-lookup"><span data-stu-id="0a435-112">If you are using an electronic software distribution system that runs the commands under the computer’s **SYSTEM** account, the package is published for that account only, unless you use the /GLOBAL switch.</span></span> <span data-ttu-id="0a435-113">Eseguire il comando seguente per aggiungere e pubblicare il pacchetto per tutti gli utenti nel computer:</span><span class="sxs-lookup"><span data-stu-id="0a435-113">Run the following command to add and publish the package for all users on the computer:</span></span>

    `SFTMIME ADD PACKAGE:”name” /MANIFEST <manifest-path> /GLOBAL`

2.  

    <span data-ttu-id="0a435-114">Se si vuole aggiungere il pacchetto solo per utenti specifici, eseguire il comando **Aggiungi pacchetto** e quindi pubblicare esplicitamente il pacchetto per ogni utente eseguendo il comando **pubblica pacchetto** seguente sotto l'account utente di ogni persona:</span><span class="sxs-lookup"><span data-stu-id="0a435-114">If you want to add the package for specific users only, run the **ADD PACKAGE** command, and then explicitly publish the package for each user by running the following **PUBLISH PACKAGE** command under each person’s user account:</span></span>

    `SFTMIME ADD PACKAGE:”name” /MANIFEST <manifest-path>`

    `SFTMIME PUBLISH PACKAGE:”name” /MANIFEST <manifest-path>`

    <span data-ttu-id="0a435-115">La pubblicazione del pacchetto senza il parametro globale concede all'utente l'accesso alle applicazioni nel pacchetto e pubblica i tipi di file e i tasti di scelta rapida elencati nel manifesto nel profilo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0a435-115">Publishing the package without the GLOBAL parameter grants the user access to the applications in the package and publishes the file types and shortcuts that are listed in the manifest to the user’s profile.</span></span> <span data-ttu-id="0a435-116">Le autorizzazioni necessarie sono "Manage tipo di file Associations" (**ManageTypes**) e "Publish Shortcuts" (**PublishShortcut**).</span><span class="sxs-lookup"><span data-stu-id="0a435-116">Permissions required are “Manage file type associations” (**ManageTypes**) and “Publish shortcuts” (**PublishShortcut**).</span></span>

## <span data-ttu-id="0a435-117">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="0a435-117">Related topics</span></span>


[<span data-ttu-id="0a435-118">Come eliminare tutte le applicazioni virtuali usando la riga di comando</span><span class="sxs-lookup"><span data-stu-id="0a435-118">How to Delete All Virtual Applications by Using the Command Line</span></span>](how-to-delete-all-virtual-applications-by-using-the-command-line.md)

[<span data-ttu-id="0a435-119">Come rimuovere un pacchetto con la riga di comando</span><span class="sxs-lookup"><span data-stu-id="0a435-119">How to Remove a Package by Using the Command Line</span></span>](how-to-remove-a-package-by-using-the-command-line.md)

 

 





