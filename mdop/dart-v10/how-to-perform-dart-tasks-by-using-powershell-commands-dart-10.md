---
title: Come eseguire attività di DaRT usando i comandi di PowerShell
description: Come eseguire attività di DaRT usando i comandi di PowerShell
author: dansimp
ms.assetid: f5a5c5f9-d667-4c85-9e82-7baf0b2aec6e
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: support
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: fdf167ca81281da4e04dae10e34bad6122ec05aa
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10822596"
---
# Come eseguire attività di DaRT usando i comandi di PowerShell


Microsoft Diagnostics and Recovery Toolset (DaRT) 10 include il set di cmdlet di Windows PowerShell seguente. Gli amministratori possono usare questi cmdlet di PowerShell per eseguire varie attività del server DaRT 10 dal prompt dei comandi invece che dalla creazione guidata immagine di ripristino DaRT.

## Per amministrare il dardo usando i comandi di PowerShell


Usare i cmdlet di PowerShell descritti qui per amministrare il dardo.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Nome</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Copy-DartImage</p></td>
<td align="left"><p>Brucia una ISO in un CD, un DVD o un'unità USB.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Export-DartImage</p></td>
<td align="left"><p>Consente di convertire in un file ISO il file WIM di origine, che contiene un'immagine dardo.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>New-DartConfiguration</p></td>
<td align="left"><p>Crea un oggetto di configurazione DaRT necessario per applicare un set di strumenti DaRT a un'immagine Windows.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Set-DartImage</p></td>
<td align="left"><p>Applica un oggetto DartConfiguration a un'immagine di Windows montata. Questo include l'aggiunta di tutti i file, la configurazione e le dipendenze tra pacchetti.</p></td>
</tr>
</tbody>
</table>

 

## Argomenti correlati


[Amministrazione di DaRT 10 con PowerShell](administering-dart-10-using-powershell.md)

 

 





