---
title: Finestra Cronologia
description: Finestra Cronologia
author: dansimp
ms.assetid: 114f50a4-508d-4589-b006-6cd05cffe6b7
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 06/16/2016
ms.openlocfilehash: 81911b5103c76e267d806fb7cd8acf55811440c9
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820796"
---
# Finestra Cronologia


La cronologia di un oggetto Criteri di gruppo può essere visualizzata facendo doppio clic su un GPO oppure facendo clic con il pulsante destro del mouse su un GPO e quindi scegliendo **cronologia**. Viene visualizzata anche nella console di **gestione di criteri di gruppo** come scheda per ogni oggetto.

La cronologia fornisce un record di eventi nella durata dell'oggetto Criteri di stato selezionato. Nella finestra **cronologia** è possibile ottenere un report delle impostazioni in una versione dell'oggetto Criteri di gruppo, confrontare più versioni di un oggetto Criteri di gruppo o eseguire il rollback a una versione precedente di un oggetto Criteri di gruppo.

## Filtrare gli eventi nella finestra cronologia


Le schede nella finestra **cronologia** filtrano gli Stati nella cronologia del GPO.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Schede</th>
<th align="left">Filtro</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Tutti gli Stati</strong></p></td>
<td align="left"><p>Visualizzare tutti gli Stati nella cronologia del GPO.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Versioni esclusive</strong></p></td>
<td align="left"><p>Visualizza solo le versioni univoche dell'oggetto Criteri di controllo archiviate nell'archivio. La versione distribuita nell'ambiente di produzione, i tasti di scelta rapida per le versioni esclusive e gli Stati informativi vengono omessi dall'elenco.</p></td>
</tr>
</tbody>
</table>



## Informazioni sugli eventi


Le informazioni vengono fornite per ogni stato nella cronologia del GPO.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Attributo GPO</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Modifica data</strong></p></td>
<td align="left"><p>Indicatore di data e ora di quando <strong> </strong> è stata eseguita l'azione nella colonna stato.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Stato</strong></p></td>
<td align="left"><p>Uno stato nella cronologia del GPO.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Modificato da</strong></p></td>
<td align="left"><p>La persona che ha eseguito l'accesso o ha distribuito l'oggetto Criteri di controllo.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Comment</strong></p></td>
<td align="left"><p>Un commento immesso dalla persona che ha effettuato l'accesso o ha distribuito un GPO al momento della modifica di questa versione. Utile per identificare le specifiche della versione in caso di necessità di eseguire il rollback a una versione precedente.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Cancellabile</strong></p></td>
<td align="left"><p>Se questa versione del GPO può essere eliminata se il numero di versioni univoche di ogni oggetto Criteri di controllo conservati nell'archivio è limitato.</p>
<div class="alert">
<strong>Nota</strong><br/><p>Per modificare la versione di un oggetto Criteri di cancellabile, è possibile fare clic con il pulsante destro del mouse su di esso e quindi fare clic su non <strong> consentire l'eliminazione </strong> o <strong> consentire l'eliminazione </strong> .</p>
</div>
<div>

</div></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Versione computer</strong></p></td>
<td align="left"><p>Versione generata automaticamente della parte di configurazione del computer dell'oggetto Criteri di controllo.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Versione utente</strong></p></td>
<td align="left"><p>Versione generata automaticamente della parte di configurazione utente dell'oggetto Criteri di controllo.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Stato GPO</strong></p></td>
<td align="left"><p>La configurazione del computer e la configurazione dell'utente possono essere gestite separatamente. Questo stato Mostra le parti del GPO abilitate.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Filtro WMI</strong></p></td>
<td align="left"><p>Visualizzare i filtri WMI applicati a questo oggetto Criteri di stato. I filtri WMI vengono gestiti nella <strong> cartella filtri WMI </strong> per il dominio nell'albero della console di GPMC.</p></td>
</tr>
</tbody>
</table>



## Rapporti


I pulsanti **Impostazioni** e **differenze** consentono di visualizzare i report sulle impostazioni GPO per la versione o le versioni degli oggetti selezionati. Facendo clic con il pulsante destro del mouse su versioni GPO è disponibile l'opzione per visualizzare anche i report basati su XML.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Button</th>
<th align="left">Effetto</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Impostazioni</strong></p></td>
<td align="left"><p>Generare un report basato su HTML che visualizzi le impostazioni nella versione selezionata del GPO.</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Differenze</strong></p></td>
<td align="left"><p>Generare un report basato su HTML che confronti le impostazioni in più versioni selezionate dell'oggetto Criteri di gruppo.</p></td>
</tr>
</tbody>
</table>



### Chiave per i report differenze

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Simbolo</th>
<th align="left">Significato</th>
<th align="left">Colore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Nessuno</p></td>
<td align="left"><p>L'elemento esiste con impostazioni identiche in entrambi i GPO</p></td>
<td align="left"><p>Varia in base al livello</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>[#]</strong></p></td>
<td align="left"><p>L'elemento è presente in entrambi i GPO, ma con le impostazioni modificate</p></td>
<td align="left"><p>Blu</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>[-]</strong></p></td>
<td align="left"><p>L'elemento esiste solo nel primo GPO</p></td>
<td align="left"><p>Rosso</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>[+]</strong></p></td>
<td align="left"><p>L'elemento esiste solo nel secondo GPO</p></td>
<td align="left"><p>Verde</p></td>
</tr>
</tbody>
</table>



-   Per gli elementi con impostazioni modificate, le impostazioni modificate vengono identificate quando l'elemento viene espanso. Il valore dell'attributo in ogni oggetto Criteri di ricerca viene visualizzato nello stesso ordine in cui vengono visualizzati i GPO nel report.

-   Alcune modifiche alle impostazioni possono comportare la segnalazione di un elemento come due elementi diversi (uno presente solo nel primo GPO, uno presente solo nel secondo), anziché un elemento modificato.

### Riferimenti aggiuntivi

-   [Scheda Contenuto](contents-tab-agpm30ops.md)









