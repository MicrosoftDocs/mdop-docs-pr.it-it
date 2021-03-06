---
title: UNPUBLISH PACKAGE
description: UNPUBLISH PACKAGE
author: dansimp
ms.assetid: 1651427c-72a5-4701-bb57-71e14a7a3803
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 7704fb3ed03be4864a837767d9e890d28b63f175
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10815135"
---
# UNPUBLISH PACKAGE


Consente di rimuovere i tasti di scelta rapida e i tipi di file per un intero pacchetto.

`SFTMIME UNPUBLISH PACKAGE:package-name [/CLEAR] [/GLOBAL]                 [/LOG log-pathname | /CONSOLE | /GUI]`

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Parametro</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>PACCHETTO: &lt; nome pacchetto&gt;</p></td>
<td align="left"><p>Nome del pacchetto.</p></td>
</tr>
<tr class="even">
<td align="left"><p>/CLEAR</p></td>
<td align="left"><p>Se presente, verranno rimosse anche le impostazioni utente. Per altre informazioni, vedere la nota importante più avanti in questo argomento.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>/GLOBAL</p></td>
<td align="left"><p>Se presente, il pacchetto sarà non pubblicato per tutti gli utenti di questo computer.</p></td>
</tr>
<tr class="even">
<td align="left"><p>/LOG</p></td>
<td align="left"><p>Se specificato, l'output viene registrato nel nome del percorso specificato.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>/CONSOLE</p></td>
<td align="left"><p>Se specificato, l'output viene presentato nella finestra della console attiva (impostazione predefinita).</p></td>
</tr>
<tr class="even">
<td align="left"><p>/GUI</p></td>
<td align="left"><p>Se specificato, l'output viene presentato in una finestra di dialogo di Windows.</p></td>
</tr>
</tbody>
</table>

 

Per la versione 4.6 è stata aggiunta l'opzione seguente.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>/LOGU</p></td>
<td align="left"><p>Se specificato, l'output viene registrato nel nome del percorso specificato in formato UNICODE.</p></td>
</tr>
</tbody>
</table>

 

**Importante**  Prima di poter eseguire il comando **UNPUBLISH PACKAGE** , il pacchetto deve essere già stato aggiunto al client Application Virtualization.

Per usare il pacchetto **globale**, l'annullamento della **pubblicazione** deve essere eseguito come amministratore locale. in caso contrario, è necessaria solo l'autorizzazione **ClearApp** .

L'uso di **UNPUBLISH PACKAGE** with **Global** rimuove tutti i tipi di file globali e i tasti di scelta rapida per il pacchetto. **Clear** non è applicabile.

L'uso di **UNPUBLISH PACKAGE** without **Global** rimuove i tasti di scelta rapida e i tipi di file per il pacchetto e, se **Clear** è impostato, rimuove anche le impostazioni utente e arresta i carichi in background nel contesto dell'utente.

**UNPUBLISH PACKAGE** funziona con le applicazioni dello stesso nome del pacchetto o GUID usato come ID di origine per il pacchetto di **aggiunta**, **modifica**e **pubblicazione**.

Annulla **pubblicazione pacchetto** Cancella sempre tutte le impostazioni utente, i collegamenti e i tipi di file indipendentemente dall'uso dell'opzione/Clear.

 

## Argomenti correlati


[Informazioni di riferimento sui comandi di SFTMIME](sftmime--command-reference.md)

 

 





