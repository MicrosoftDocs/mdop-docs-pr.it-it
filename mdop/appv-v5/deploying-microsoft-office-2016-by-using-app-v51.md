---
title: Distribuzione di Microsoft Office 2016 con App-V
description: Distribuzione di Microsoft Office 2016 con App-V
author: dansimp
ms.assetid: e0f4876-da99-4b89-977e-2fb6e89ea3d3
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop, appcompat, virtualization
ms.mktglfcycl: deploy
ms.sitesec: library
ms.prod: w10
ms.date: 04/19/2017
ms.openlocfilehash: b47fd46c8dc368bbce819b24f18fa30328fbbaf0
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10805854"
---
# Distribuzione di Microsoft Office 2016 con App-V


Usare le informazioni in questo articolo per usare Microsoft Application Virtualization (App-V) 5,1 o versioni successive per offrire Microsoft Office 2016 come applicazione virtualizzata ai computer dell'organizzazione. Per informazioni sull'uso di App-V per consegnare Office 2013, vedere [distribuzione di Microsoft office 2013 tramite App-v](deploying-microsoft-office-2013-by-using-app-v51.md). Per informazioni sull'uso di App-V per consegnare Office 2010, vedere [distribuzione di Microsoft office 2010 tramite App-v](deploying-microsoft-office-2010-by-using-app-v51.md).

Questo argomento contiene le sezioni seguenti:

-   [Informazioni da conoscere prima di iniziare](#bkmk-before-you-start)

-   [Creazione di un pacchetto di Office 2016 per App-V con lo strumento di distribuzione di Office](#bkmk-create-office-pkg)

-   [Pubblicazione del pacchetto di Office per App-V 5,1](#bkmk-pub-pkg-office)

-   [Personalizzazione e gestione dei pacchetti di Office App-V](#bkmk-custmz-manage-office-pkgs)

## <a href="" id="bkmk-before-you-start"></a>Informazioni da conoscere prima di iniziare


Prima di distribuire Office 2016 tramite App-V, esaminare le informazioni di pianificazione seguenti.

### <a href="" id="bkmk-supp-vers-coexist"></a>Versioni di Office supportate e coesistenza di Office

Usare la tabella seguente per ottenere informazioni sulle versioni supportate di Office e sull'utilizzo di versioni coesistenti di Office.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Informazioni da rivedere</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="planning-for-using-app-v-with-office.md#bkmk-office-vers-supp-appv" data-raw-source="[Supported versions of Microsoft Office](planning-for-using-app-v-with-office.md#bkmk-office-vers-supp-appv)">Versioni supportate di Microsoft Office</a></p></td>
<td align="left"><ul>
<li><p>Versioni supportate di Office</p></li>
<li><p>Tipi di distribuzione supportati, ad esempio desktop, Personal Virtual Desktop Infrastructure (VDI), pool VDI)</p></li>
<li><p>Opzioni di gestione licenze di Office</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p><a href="planning-for-using-app-v-with-office.md#bkmk-plan-coexisting" data-raw-source="[Planning for Using App-V with coexisting versions of Office](planning-for-using-app-v-with-office.md#bkmk-plan-coexisting)">Pianificazione dell'uso di App-V con le versioni coesistenti di Office</a></p></td>
<td align="left"><p>Considerazioni per l'installazione di versioni diverse di Office nello stesso computer</p></td>
</tr>
</tbody>
</table>



### <a href="" id="bkmk-pkg-pub-reqs"></a>Requisiti per l'imballaggio, la pubblicazione e la distribuzione

Prima di distribuire Office tramite App-V, esaminare i requisiti seguenti.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Attività</th>
<th align="left">Requisito</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Imballaggio</p></td>
<td align="left">
<ul>
<li><p>Tutte le applicazioni di Office che si desidera distribuire agli utenti devono essere in un unico pacchetto.</p></li>
<li><p>In App-V 5,1 e versioni successive è necessario usare lo strumento di distribuzione di Office per creare pacchetti. Non è possibile usare il sequencer.</p></li>
<li><p>Se si distribuisce Microsoft Visio 2016 e Microsoft Project 2016 insieme a Office, è necessario includerli nello stesso pacchetto con Office. Per altre informazioni, vedere <a href="#bkmk-deploy-visio-project" data-raw-source="[Deploying Visio 2016 and Project 2016 with Office](#bkmk-deploy-visio-project)"> distribuzione di Visio 2016 e Project 2016 con Office </a> .</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>Pubblicazione</p></td>
<td align="left"><ul>
<li><p>È possibile pubblicare un solo pacchetto di Office in ogni computer client.</p></li>
<li><p>È necessario pubblicare il pacchetto di Office a livello globale. Non è possibile pubblicare l'utente.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td align="left"><p>Distribuire uno dei prodotti seguenti in un computer condiviso, ad esempio tramite Servizi Desktop remoto:</p>
<ul>
<li><p>App Microsoft 365 per le aziende</p></li>
<li><p>Visio Pro per Office 365</p></li>
<li><p>Project Pro per Office 365</p></li>
</ul></td>
<td align="left"><p>È necessario abilitare l' <a href="https://technet.microsoft.com/library/dn782860.aspx" data-raw-source="[shared computer activation](https://technet.microsoft.com/library/dn782860.aspx)"> attivazione di computer condivisi </a> .</p>
</td>
</tr>
</tbody>
</table>



### Esclusione di applicazioni di Office da un pacchetto

La tabella seguente descrive i metodi consigliati per l'esclusione di specifiche applicazioni di Office da un pacchetto.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Attività</th>
<th align="left">Dettagli</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Usa l' <strong> </strong> impostazione ExcludeApp quando crei il pacchetto usando lo strumento di distribuzione di Office.</p></td>
<td align="left"><ul>
<li><p>Consente di escludere specifiche applicazioni di Office dal pacchetto quando lo strumento di distribuzione di Office crea il pacchetto. Ad esempio, puoi usare questa impostazione per creare un pacchetto che contiene solo Microsoft Word.</p></li>
<li><p>Per altre informazioni, Vedi <a href="https://technet.microsoft.com/library/jj219426.aspx#bkmk-excludeappelement" data-raw-source="[ExcludeApp element](https://technet.microsoft.com/library/jj219426.aspx#bkmk-excludeappelement)"> elemento ExcludeApp </a> .</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>Modificare il file di DeploymentConfig.xml</p></td>
<td align="left"><ul>
<li><p>Modificare il file DeploymentConfig.xml dopo la creazione del pacchetto. Questo file contiene le impostazioni predefinite del pacchetto per tutti gli utenti in un computer in cui è in uso App-V client.</p></li>
<li><p>Per altre informazioni, vedere <a href="#bkmk-disable-office-apps" data-raw-source="[Disabling Office 2016 applications](#bkmk-disable-office-apps)"> disabilitare le applicazioni di Office 2016 </a> .</p></li>
</ul></td>
</tr>
</tbody>
</table>



## <a href="" id="bkmk-create-office-pkg"></a>Creazione di un pacchetto di Office 2016 per App-V con lo strumento di distribuzione di Office


Completare la procedura seguente per creare un pacchetto di Office 2016 per App-V 5,1 o versioni successive.

>**Important** &nbsp; Importante &nbsp; In App-V 5,1 e versioni successive è necessario usare lo strumento di distribuzione di Office per creare un pacchetto. Non è possibile usare il sequencer per creare pacchetti.

### Rivedere i prerequisiti per l'uso dello strumento di distribuzione di Office

Il computer in cui si sta installando lo strumento di distribuzione di Office deve avere:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Prerequisiti</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Software prerequisito</p></td>
<td align="left"><p>.NET Framework 4</p></td>
</tr>
<tr class="even">
<td align="left"><p>Sistemi operativi supportati</p></td>
<td align="left"><ul>
<li><p>versione di Windows 10 a 64 bit</p></li>
<li><p>versione a 64 bit di Windows 8 o 8,1</p></li>
<li><p>versione di Windows 7 a 64 bit</p></li>
</ul></td>
</tr>
</tbody>
</table>


>**Nota**  In questo argomento il termine "Office 2016 App-V Package" si riferisce alla licenza per gli abbonamenti.


### Creare pacchetti di Office 2016 App-V usando lo strumento di distribuzione di Office

Puoi creare pacchetti di Office 2016 App-V usando lo strumento di distribuzione di Office. Le istruzioni seguenti spiegano come creare un pacchetto di Office 2016 App-V con licenze per l'abbonamento.

Creare pacchetti di Office 2016 App-V in computer Windows a 64 bit. Una volta creato, il pacchetto di Office 2016 App-V verrà eseguito in computer con Windows 7, Windows 8,1 e Windows 10 a 32 bit e 64 bit.

### Scaricare lo strumento di distribuzione di Office

I pacchetti App-V di Office 2016 vengono creati con lo strumento di distribuzione di Office, che genera un pacchetto di Office 2016 App-V. Il pacchetto non può essere creato o modificato tramite App-V Sequencer. Per iniziare la creazione del pacchetto:

1.  Scaricare lo [strumento di distribuzione di Office 2016 per l'esecuzione a](https://www.microsoft.com/download/details.aspx?id=49117)portata di clic.

> **Importante** È necessario usare lo strumento di distribuzione di Office 2016 per creare pacchetti di Office 2016 App-V.
> 2. Eseguire il file con estensione exe ed estrarne le caratteristiche nella posizione desiderata. Per semplificare la procedura, è possibile creare una cartella di rete condivisa in cui verranno salvate le caratteristiche.

    Example: \\\\Server\\Office2016

3. Verificare che esistano un setup.exe e un file di configuration.xml e che si trovino nella posizione specificata.

### Scaricare le applicazioni di Office 2016

Dopo aver scaricato lo strumento di distribuzione di Office, è possibile usarlo per ottenere le più recenti applicazioni di Office 2016. Dopo aver ottenuto le applicazioni di Office, è possibile creare il pacchetto App-V di Office 2016.

Il file XML incluso nello strumento di distribuzione di Office specifica i dettagli del prodotto, ad esempio le lingue e le applicazioni di Office incluse.

1. **Personalizzare il file di configurazione XML di esempio:** Usare il file di configurazione XML di esempio scaricato con lo strumento di distribuzione di Office per personalizzare le applicazioni di Office:

   1. Aprire il file XML di esempio in blocco note o nell'editor di testo preferito.

   2. Con l'esempio configuration.xml file aperto e pronto per la modifica, è possibile specificare i prodotti, le lingue e il percorso in cui si salvano le applicazioni di Office 2016. Di seguito è riportato un esempio di base del file configuration.xml:

      ```xml
      <Configuration>
         <Add SourcePath= ”\\Server\Office2016” OfficeClientEdition="32" >
          <Product ID="O365ProPlusRetail ">
            <Language ID="en-us" />
          </Product>
          <Product ID="VisioProRetail">
            <Language ID="en-us" />
          </Product>
        </Add>
      </Configuration>
      ```

      >**Nota**  La configurazione XML è un file XML di esempio. Il file include righe commentate. Puoi "rimuovere il commento" da queste righe per personalizzare le impostazioni aggiuntive con il file. Per rimuovere il commento da queste righe, Rimuovi "<! --"dall'inizio della riga e"--> "dalla fine della riga.

      Il file di configurazione XML precedente specifica che Office 2016 ProPlus 32 bit Edition, incluso Visio ProPlus, verrà scaricato in inglese in \\\\server\\Office 2016, che rappresenta il percorso in cui verranno salvate le applicazioni di Office. Si noti che l'ID prodotto delle applicazioni non influirà sulla licenza finale di Office. I pacchetti App-V di Office 2016 con varie licenze possono essere creati dalle stesse applicazioni specificando le licenze in una fase successiva. Nella tabella seguente sono riepilogati gli attributi e gli elementi personalizzabili del file XML:

      <table>
      <colgroup>
      <col width="33%" />
      <col width="33%" />
      <col width="33%" />
      </colgroup>
      <thead>
      <tr class="header">
      <th align="left">Input</th>
      <th align="left">Descrizione</th>
      <th align="left">Esempio</th>
      </tr>
      </thead>
      <tbody>
      <tr class="odd">
      <td align="left"><p>Elemento Add</p></td>
      <td align="left"><p>Specifica i prodotti e le lingue da includere nel pacchetto.</p></td>
      <td align="left"><p>N/D</p></td>
      </tr>
      <tr class="even">
      <td align="left"><p>OfficeClientEdition (attributo dell'elemento Add)</p></td>
      <td align="left"><p>Specifica l'edizione del prodotto Office 2016 da usare: 32 bit o 64 bit. L'operazione non riesce se <strong> OfficeClientEdition </strong> non è impostato su un valore valido.</p></td>
      <td align="left"><p><strong>OfficeClientEdition </strong> = &quot; 32&quot;</p>
      <p><strong>OfficeClientEdition </strong> = &quot; 64&quot;</p></td>
      </tr>
      <tr class="odd">
      <td align="left"><p>Elemento Product</p></td>
      <td align="left"><p>Specifica l'applicazione. Project 2016 e Visio 2016 devono essere specificati qui come prodotto aggiunto da includere nelle applicazioni.

      Per altre informazioni sugli ID prodotto, vedere <a href="https://support.microsoft.com/kb/2842297" data-raw-source="[Product IDs that are supported by the Office Deployment Tool for Click-to-Run](https://support.microsoft.com/kb/2842297)"> ID prodotto supportati dallo strumento di distribuzione di Office per l'esecuzione a portata di clic</a>
      </p></td>
      <td align="left"><p><code>Product ID =&quot;O365ProPlusRetail &quot;</code></p>
      <p><code>Product ID =&quot;VisioProRetail&quot;</code></p>
      <p><code>Product ID =&quot;ProjectProRetail&quot;</code></p>
      </td>
      </tr>
      <tr class="even">
      <td align="left"><p>Elemento Language</p></td>
      <td align="left"><p>Specifica la lingua supportata nelle applicazioni</p></td>
      <td align="left"><p><code>Language ID=&quot;en-us&quot;</code></p></td>
      </tr>
      <tr class="odd">
      <td align="left"><p>Version (attributo dell'elemento Add)</p></td>
      <td align="left"><p>Facoltativo. Specifica una compilazione da usare per il pacchetto</p>
      <p>Impostazione predefinita per la build più recente annunciata (come definito in v32.CAB all'origine di Office).</p></td>
      <td align="left"><p><code>16.1.2.3</code></p></td>
      </tr>
      <tr class="even">
      <td align="left"><p>SourcePath (attributo dell'elemento Add)</p></td>
      <td align="left"><p>Specifica la posizione in cui verranno salvate le applicazioni.</p></td>
      <td align="left"><p><code>Sourcepath = &quot;\Server\Office2016”</code></p></td>
      </tr>
      <tr class="even">
      <td align="left"><p>Branch (attributo dell'elemento Add)</p></td>
      <td align="left"><p>Facoltativo. Specifica la filiale di aggiornamento per il prodotto che si vuole scaricare o installare. </p><p>Per altre informazioni su come aggiornare i rami, vedere Panoramica dei rami di aggiornamento per le app Microsoft 365 per le aziende.</p></td>
      <td align="left"><p><code>Branch = &quot;Business&quot;</code></p></td>
      </tr>
      </tbody>
      </table>

      Dopo aver modificato il file configuration.xml per specificare il prodotto desiderato, le lingue e anche la posizione in cui verranno salvate le applicazioni di Office 2016, è possibile salvare il file di configurazione, ad esempio come Customconfig.xml.

2. **Scaricare le applicazioni nella posizione specificata:** Usare un prompt dei comandi con privilegi elevati e un sistema operativo di 64 bit per scaricare le applicazioni di Office 2016 che verranno in seguito convertite in un pacchetto di App-V. Di seguito è riportato un esempio di comando con una descrizione dei dettagli:

   ``` syntax
   \\server\Office2016\setup.exe /download \\server\Office2016\Customconfig.xml
   ```

   Nell'esempio:

   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <tbody>
   <tr class="odd">
   <td align="left"><p><strong>\server\Office2016</strong></p></td>
   <td align="left"><p>è il percorso di condivisione di rete che contiene lo strumento di distribuzione di Office e il file Configuration.xml personalizzato Customconfig.xml.</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>Setup.exe</strong></p></td>
   <td align="left"><p>è lo strumento di distribuzione di Office.</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>/Download</strong></p></td>
   <td align="left"><p>Scarica le applicazioni di Office 2016 specificate nel file customConfig.xml. Questi bit possono essere convertiti in seguito in un pacchetto di Office 2016 App-V con contratti multilicenza.</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>\server\Office2016\Customconfig.xml</strong></p></td>
   <td align="left"><p>passa il file di configurazione XML necessario per completare il processo di download, in questo esempio customconfig.xml. Dopo aver usato il comando Scarica, le applicazioni di Office devono essere trovate nella posizione specificata nel file XML di configurazione, in questo esempio \Server\Office2016.</p></td>
   </tr>
   </tbody>
   </table>



### Convertire le applicazioni di Office in un pacchetto App-V

Dopo aver scaricato le applicazioni di Office 2016 tramite lo strumento di distribuzione di Office, usare lo strumento di distribuzione di Office per convertirle in un pacchetto di Office 2016 App-V. Completare i passaggi che corrispondono al modello di licenza.

**Riepilogo delle operazioni che è necessario eseguire:**

-   Creare i pacchetti App-V di Office 2016 nei computer Windows a 64 bit. Il pacchetto verrà tuttavia eseguito in computer con Windows 7, Windows 8 o 8,1 e Windows 10 a 32 bit e 64 bit.

-   Creare un pacchetto di Office App-V per il pacchetto di licenze di sottoscrizione usando lo strumento di distribuzione di Office e quindi modificare il file di configurazione di CustomConfig.xml.

    Nella tabella seguente sono riepilogati i valori che è necessario immettere nel file CustomConfig.xml per il modello di licenza in uso. I passaggi descritti nelle sezioni che seguono la tabella specificano le voci esatte che è necessario apportare.

>**Note** &nbsp; Nota &nbsp; Puoi usare lo strumento di distribuzione di Office per creare pacchetti App-V per le app Microsoft 365 per le aziende. La creazione di pacchetti per le versioni con contratto multilicenza di Office Professional Plus o Office standard non è supportata.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">ID prodotto</th>
<th align="left">Licenze per gli abbonamenti</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>Office 2016</strong></p></td>
<td align="left"><p>O365ProPlusRetail</p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>Office 2016 con Visio 2016</strong></p></td>
<td align="left"><p>O365ProPlusRetail</p>
<p>VisioProRetail</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>Office 2016 con Visio 2016 e Project 2016</strong></p></td>
<td align="left"><p>O365ProPlusRetail</p>
<p>VisioProRetail</p>
<p>ProjectProRetail</p></td>
</tr>
</tbody>
</table>



**Come convertire le applicazioni di Office in un pacchetto App-V**

1. In blocco note riaprire il file CustomConfig.xml e apportare le modifiche seguenti al file:

   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <thead>
   <tr class="header">
   <th align="left">Parametro</th>
   <th align="left">Informazioni su come modificare il valore in</th>
   </tr>
   </thead>
   <tbody>
   <tr class="odd">
   <td align="left"><p>SourcePath</p></td>
   <td align="left"><p>Selezionare le applicazioni di Office scaricate in precedenza.</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p>ProductID</p></td>
   <td align="left"><p>Specificare le licenze per gli abbonamenti, come illustrato nell'esempio seguente:</p>
   <pre class="syntax" space="preserve"><code>&lt;Configuration&gt;
      &lt;Add SourcePath= &quot;\server\Office 2016&quot; OfficeClientEdition=&quot;32&quot; &gt;
       &lt;Product ID=&quot;O365ProPlusRetail&quot;&gt;
         &lt;Language ID=&quot;en-us&quot; /&gt;
       &lt;/Product&gt;
       &lt;Product ID=&quot;VisioProRetail&quot;&gt;
         &lt;Language ID=&quot;en-us&quot; /&gt;
       &lt;/Product&gt;
     &lt;/Add&gt;
   &lt;/Configuration&gt; </code></pre>
   <p>In questo esempio sono state apportate le modifiche seguenti per creare un pacchetto con licenze di sottoscrizione:</p>
   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <tbody>
   <tr class="odd">
   <td align="left"><p><strong>SourcePath</strong></p></td>
   <td align="left"><p>è il percorso, che è stato modificato in modo che punti alle applicazioni di Office scaricate in precedenza.</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>ID prodotto</strong></p></td>
   <td align="left"><p>per Office è stato modificato in <code>O365ProPlusRetail</code> .</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>ID prodotto</strong></p></td>
   <td align="left"><p>per Visio è stato modificato in <code>VisioProRetail</code> .</p></td>
   </tr>
   </tbody>
   </table>
   <p></p>
   <tr class="odd">
   <td align="left"><p>ExcludeApp (facoltativo)</p></td>
   <td align="left"><p>Consente di specificare le applicazioni di Office che non si desidera includere nel pacchetto App-V creato dallo strumento di distribuzione di Office. Ad esempio, è possibile escludere Access e InfoPath.</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p>PACKAGEGUID (facoltativo)</p></td>
   <td align="left"><p>Per impostazione predefinita, tutti i pacchetti App-V creati dallo strumento di distribuzione di Office condividono lo stesso ID pacchetto App-V. Puoi usare PACKAGEGUID per specificare un ID pacchetto diverso per ogni pacchetto, che ti permette di pubblicare più pacchetti App-V, creati dallo strumento di distribuzione di Office e di gestirli usando App-V Server.</p>
   <p>Un esempio di quando usare questo parametro è creare pacchetti diversi per utenti diversi. Ad esempio, è possibile creare un pacchetto con solo Office 2016 per alcuni utenti e creare un altro pacchetto con Office 2016 e Visio 2016 per un altro gruppo di utenti.</p>

   &gt;<strong>Nota </strong> anche se usi ID pacchetto univoci, puoi comunque distribuire solo un pacchetto di App-V in un singolo dispositivo.
   </td>
   </tr>
   </tbody>
   </table>


2. Usare il comando/Packager per convertire le applicazioni di Office in un pacchetto di Office 2016 App-V.

   Ad esempio:

   ``` syntax
   \\server\Office2016\setup.exe /packager \\server\Office2016\Customconfig.xml  \\server\share\Office2016AppV
   ```

   Nell'esempio:

   <table>
   <colgroup>
   <col width="50%" />
   <col width="50%" />
   </colgroup>
   <tbody>
   <tr class="odd">
   <td align="left"><p><strong>\server\Office2016</strong></p></td>
   <td align="left"><p>è il percorso di condivisione di rete che contiene lo strumento di distribuzione di Office e il file Configuration.xml personalizzato Customconfig.xml.</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>Setup.exe</strong></p></td>
   <td align="left"><p>è lo strumento di distribuzione di Office.</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>/packager</strong></p></td>
   <td align="left"><p>Crea il pacchetto App-V di Office 2016 con il tipo di licenza specificato nel file customConfig.xml.</p></td>
   </tr>
   <tr class="even">
   <td align="left"><p><strong>\server\Office2016\Customconfig.xml</strong></p></td>
   <td align="left"><p>passa il file XML di configurazione (in questo caso customConfig) che è stato preparato per la fase di assemblaggio.</p></td>
   </tr>
   <tr class="odd">
   <td align="left"><p><strong>\server\share\Office 2016AppV</strong></p></td>
   <td align="left"><p>Specifica la posizione del pacchetto di Office App-V appena creato.</p></td>
   </tr>
   </tbody>
   </table>



~~~
After you run the **/packager** command, the following folders appear up in the directory where you specified the package should be saved:

-   **App-V Packages** – contains an Office 2016 App-V package and two deployment configuration files.

-   **WorkingDir**

**Note** To troubleshoot any issues, see the log files in the %temp% directory (default).
~~~



3. Verificare che il pacchetto Office 2016 App-V funzioni correttamente:

   1.  Pubblicare il pacchetto App-V di Office 2016, creato globalmente, in un computer di test e verificare che vengano visualizzati i tasti di scelta rapida di Office 2016.

   2.  Avviare alcune applicazioni di Office 2016, ad esempio Excel o Word, per verificare che il pacchetto funzioni come previsto.

## <a href="" id="bkmk-pub-pkg-office"></a>Pubblicazione del pacchetto di Office per App-V


Usare le informazioni seguenti per pubblicare un pacchetto di Office.

### Metodi per la pubblicazione di pacchetti di Office App-V

Distribuire il pacchetto App-V per Office 2016 usando gli stessi metodi usati per qualsiasi altro pacchetto:

-   System Center Configuration Manager

-   App-V Server

-   Autonomo tramite i comandi di PowerShell

### Prerequisiti e requisiti per la pubblicazione

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Prerequisito o requisito</th>
<th align="left">Dettagli</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Abilitare gli script di PowerShell nei client App-V</p></td>
<td align="left"><p>Per pubblicare i pacchetti di Office 2016, è necessario eseguire uno script.</p>
<p>Gli script di pacchetto sono disabilitati per impostazione predefinita nei client App-V. Per abilitare gli script, eseguire il comando di PowerShell seguente:</p>
<pre class="syntax" space="preserve"><code>Set-AppvClientConfiguration –EnablePackageScripts 1</code></pre></td>
</tr>
<tr class="even">
<td align="left"><p>Pubblicare il pacchetto Office 2016 globalmente</p></td>
<td align="left"><p>I punti di estensione nel pacchetto di Office App-V richiedono l'installazione a livello di computer.</p>
<p>Quando si pubblica a livello di computer, non sono necessarie azioni prerequisitive o ridistribuibili e il pacchetto Office 2016 consente a livello globale le proprie applicazioni di funzionare come Office installato nativamente, eliminando la necessità per gli amministratori di personalizzare i pacchetti.</p></td>
</tr>
</tbody>
</table>



### Come pubblicare un pacchetto di Office

Eseguire il comando seguente per pubblicare un pacchetto di Office a livello globale:

-   `Add-AppvClientPackage <Path_to_AppV_Package> | Publish-AppvClientPackage –global`

-   Dalla console di gestione Web in App-V Server è possibile aggiungere le autorizzazioni a un gruppo di computer anziché a un gruppo di utenti per consentire la pubblicazione globale dei pacchetti nei computer del gruppo corrispondente.

## <a href="" id="bkmk-custmz-manage-office-pkgs"></a>Personalizzazione e gestione dei pacchetti di Office App-V


Per gestire i pacchetti di Office App-V, USA le stesse operazioni che vuoi per qualsiasi altro pacchetto, ma esistono alcune eccezioni, come descritto nelle sezioni seguenti.

-   [Attivazione dei plug-in di Office tramite i gruppi di connessioni](#bkmk-enable-office-plugins)

-   [Disabilitazione delle applicazioni di Office 2016](#bkmk-disable-office-apps)

-   [Disabilitazione di tasti di scelta rapida di Office 2016](#bkmk-disable-shortcuts)

-   [Gestione degli aggiornamenti del pacchetto di Office 2016](#bkmk-manage-office-pkg-upgrd)

-   [Distribuzione di Visio 2016 e Project 2016 con Office](#bkmk-deploy-visio-project)

### <a href="" id="bkmk-enable-office-plugins"></a>Attivazione dei plug-in di Office tramite i gruppi di connessioni

Usare la procedura descritta in questa sezione per abilitare i plug-in di Office con il pacchetto di Office. Per usare i plug-in di Office, devi usare app-V Sequencer per creare un pacchetto distinto che contiene solo i plug-in. Non è possibile usare lo strumento di distribuzione di Office per creare il pacchetto plug-in. Viene quindi creato un gruppo di connessioni contenente il pacchetto di Office e il pacchetto plug-in, come descritto nella procedura seguente.

**Per abilitare i plug-in per i pacchetti di Office App-V**

1.  Aggiungere un gruppo di connessioni tramite App-V Server, System Center Configuration Manager o un cmdlet di PowerShell.

2.  Sequenziare i plug-in usando l'App-V Sequencer. Assicurarsi che Office 2016 sia installato nel computer usato per sequenziare il plug-in. È consigliabile usare le app Microsoft 365 per le aziende (non virtuali) nel computer di sequenziazione quando si sequenziano i plug-in di Office 2016.

3.  Crea un pacchetto di App-V che include i plug-in desiderati.

4.  Aggiungere un gruppo di connessioni tramite App-V Server, System Center Configuration Manager o un cmdlet di PowerShell.

5.  Aggiungere il pacchetto App-V di Office 2016 e il pacchetto plug-in sequenziato al gruppo di connessioni creato.

    >**Importante** L'ordine dei pacchetti nel gruppo di connessioni determina l'ordine in cui il contenuto del pacchetto viene Unito. Nel file del descrittore del gruppo di connessioni aggiungere prima il pacchetto Office 2016 App-V e quindi aggiungere il pacchetto App-V plug-in.



6.  Assicurarsi che entrambi i pacchetti vengano pubblicati nel computer di destinazione e che il pacchetto di plug-in venga pubblicato globalmente in modo che corrisponda alle impostazioni globali del pacchetto pubblicato App-V di Office 2016.

7.  Verificare che il file di configurazione della distribuzione del pacchetto di plug-in abbia le stesse impostazioni del pacchetto di Office 2016 App-V.

    Poiché il pacchetto App-V di Office 2016 è integrato con il sistema operativo, le impostazioni del pacchetto plug-in dovrebbero corrispondere. È possibile eseguire una ricerca nel file di configurazione della distribuzione per "modalità COM" e verificare che il pacchetto plug-in disponga di tale valore impostato come "Integrated" e che sia "InProcessEnabled" che "OutOfProcessEnabled" corrispondano alle impostazioni del pacchetto di App-V di Office 2016 pubblicato.

8.  Aprire il file di configurazione della distribuzione e impostare il valore per **gli oggetti Enabled** su **false**.

9.  Se sono state apportate modifiche al file di configurazione della distribuzione dopo la sequenziazione, verificare che il pacchetto di plug-in venga pubblicato con il file.

10. Verificare che il gruppo di connessioni creato sia abilitato nel computer desiderato. Il gruppo di connessioni creato sarà probabilmente "pend" Se il pacchetto App-V di Office 2016 è in uso quando il gruppo di connessioni è abilitato. In questo caso, è necessario riavviare il file per abilitare il gruppo di connessioni.

11. Dopo aver correttamente pubblicato entrambi i pacchetti e aver abilitato il gruppo di connessioni, avviare l'applicazione di Office 2016 di destinazione e verificare che il plug-in pubblicato e aggiunto al gruppo di connessioni funzioni come previsto.

### <a href="" id="bkmk-disable-office-apps"></a>Disabilitazione delle applicazioni di Office 2016

Potrebbe essere necessario disabilitare applicazioni specifiche nel pacchetto di Office App-V. Ad esempio, puoi disabilitare Access, ma lascia tutte le altre applicazioni principali di Office disponibili. Quando si disattiva un'applicazione, l'utente finale non vedrà più il collegamento per l'applicazione. Non è necessario ripetere la sequenza dell'applicazione. Quando si modifica il file di configurazione della distribuzione dopo la pubblicazione del pacchetto di Office 2016 App-V, si salvano le modifiche, si aggiunge il pacchetto App-V di Office 2016 e lo si ripubblica con il nuovo file di configurazione della distribuzione per applicare le nuove impostazioni alle applicazioni di pacchetto di Office 2016 App-V.

>**Nota** Per escludere specifiche applicazioni di Office, ad esempio Access e InfoPath, quando si crea il pacchetto App-V con lo strumento di distribuzione di Office, usare l'impostazione **ExcludeApp** .


**Per disabilitare un'applicazione di Office 2016**

1.  Aprire un file di configurazione della distribuzione con un editor di testo, ad esempio **blocco note** , e cercare "applicazioni".

2.  Cercare l'applicazione di Office che si vuole disabilitare, ad esempio Access 2016.

3.  Cambiare il valore di "Enabled" da "true" a "false".

4.  Salvare il file di configurazione della distribuzione.

5.  Aggiungere il pacchetto App-V di Office 2016 con il nuovo file di configurazione della distribuzione.

    ```xml
    <Application Id="[{AppVPackageRoot}]\office16\lync.exe" Enabled="true">
      <VisualElements>
        <Name>Lync 2016</Name>
        <Icon />
        <Description />
      </VisualElements>
    </Application>
    <Application Id="[(AppVPackageRoot}]\office16\MSACCESS.EXE" Enabled="true">
      <VisualElements>
        <Name>Access 2016</Name>
        <Icon />
        <Description />
      </VisualElements>
    </Application>
    ```

6.  Aggiungere di nuovo il pacchetto Office 2016 App-V e ripubblicarlo con il nuovo file di configurazione della distribuzione per applicare le nuove impostazioni alle applicazioni di pacchetto di Office 2016 App-V.

### <a href="" id="bkmk-disable-shortcuts"></a>Disabilitazione di tasti di scelta rapida di Office 2016

Potrebbe essere necessario disabilitare i tasti di scelta rapida per alcune applicazioni di Office invece di depubblicare o rimuovere il pacchetto. L'esempio seguente mostra come disabilitare i tasti di scelta rapida per Microsoft Access.

**Per disabilitare i collegamenti per le applicazioni di Office 2016**

1.  Aprire un file di configurazione della distribuzione in blocco note e cercare "tasti di scelta rapida".

2.  Per disabilitare alcuni tasti di scelta rapida, eliminare o impostare come commento i tasti di scelta rapida specifici che non si desidera. È necessario conservare il sottosistema presente e abilitato. Ad esempio, nell'esempio seguente elimina i tasti di scelta rapida di Microsoft Access, mantenendo &lt; intatto il collegamento &gt; &lt; di/Shortcut &gt; per disabilitare il collegamento a Microsoft Access.

    ``` syntax
    Shortcuts

    -->
     <Shortcuts Enabled="true">
      <Extensions>
        <Extension Category="AppV.Shortcut">
          <Shortcut>
           <File>[{Common Programs}]\Microsoft Office 2016\Access 2016.lnk</File>
           <Target>[{AppvPackageRoot}])office16\MSACCESS.EXE</Target>
           <Icon>[{Windows}]\Installer\{90150000-000F-0000-0000-000000FF1CE)\accicons.exe.Ø.ico</Icon>
           <Arguments />
           <WorkingDirectory />
           <AppuserModelId>Microsoft.Office.MSACCESS.EXE.15</AppUserModelId>
           <AppUserModelExcludeFromShowInNewInstall>true</AppUserModelExcludeFromShowInNewInstall>
           <Description>Build a professional app quickly to manage data.</Description>
           <ShowCommand>l</ShowCommand>
           <ApplicationId>[{AppVPackageRoot}]\office16\MSACCESS.EXE</ApplicationId>
        </Shortcut>
    ```

3.  Salvare il file di configurazione della distribuzione.

4.  Ripubblicare il pacchetto di Office 2016 App-V con il nuovo file di configurazione della distribuzione.

Molte altre impostazioni possono essere modificate modificando la configurazione della distribuzione per i pacchetti App-V, ad esempio le associazioni di tipi di file, il file system virtuale e altro ancora. Per altre informazioni su come usare i file di configurazione della distribuzione per modificare le impostazioni del pacchetto App-V, vedere la sezione risorse aggiuntive alla fine del documento.

### <a href="" id="bkmk-manage-office-pkg-upgrd"></a>Gestione degli aggiornamenti del pacchetto di Office 2016

Per aggiornare un pacchetto di Office 2016, usare lo strumento di distribuzione di Office. Per aggiornare un pacchetto di Office 2016 distribuito in precedenza, eseguire la procedura seguente.

**Come aggiornare un pacchetto di Office 2016 distribuito in precedenza**

1. Creare un nuovo pacchetto di Office 2016 tramite lo strumento di distribuzione di Office che usa il più recente software applicativo di Office 2016. I bit più recenti di Office 2016 possono essere sempre ottenuti attraverso la fase di download della creazione di un pacchetto di Office 2016 App-V. Il pacchetto di Office 2016 appena creato includerà gli aggiornamenti più recenti e un nuovo ID versione. Tutti i pacchetti creati con lo strumento di distribuzione di Office hanno lo stesso lignaggio.

   > **Nota** I pacchetti di Office App-V hanno due ID versione:
   > <ul>
   > <li>Un ID versione del pacchetto di Office 2016 App-V univoco in tutti i pacchetti creati con lo strumento di distribuzione di Office.</li>
   > <li>Un secondo ID versione del pacchetto App-V, x. x.x. x, ad esempio, nel manifesto di AppX che verrà modificato solo se è presente una nuova versione di Office. Ad esempio, se è disponibile una nuova versione di Office 2016 con gli aggiornamenti e viene creato un pacchetto tramite lo strumento di distribuzione di Office per incorporare questi aggiornamenti, l'ID versione x. X.x. x verrà modificato in modo che la versione di Office sia cambiata. Il server App-V utilizzerà l'ID versione x. X.x. x per distinguere questo pacchetto e riconoscerà che contiene nuovi aggiornamenti al pacchetto pubblicato in precedenza e, di conseguenza, lo pubblicherà come aggiornamento al pacchetto di Office 2016 esistente.</li>
   > </ul>


2. Pubblicare globalmente i pacchetti di Office 2016 App-V appena creati nei computer in cui si desidera applicare i nuovi aggiornamenti. Dato che il nuovo pacchetto ha lo stesso lignaggio del pacchetto di Office 2016 App-V più vecchio, la pubblicazione del nuovo pacchetto con gli aggiornamenti consentirà di applicare solo le nuove modifiche al vecchio pacchetto e quindi sarà veloce.

3. Gli aggiornamenti verranno applicati allo stesso modo dei pacchetti App-V pubblicati a livello globale. Dato che le applicazioni saranno probabilmente in uso, gli aggiornamenti potrebbero essere ritardati finché non viene riavviato il computer.


### <a href="" id="bkmk-deploy-visio-project"></a>Distribuzione di Visio 2016 e Project 2016 con Office

La tabella seguente descrive i requisiti e le opzioni per la distribuzione di Visio 2016 e Project 2016 con Office.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Attività</th>
<th align="left">Dettagli</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Come si impacca e pubblica Visio 2016 e Project 2016 con Office?</p></td>
<td align="left"><p>È necessario includere Visio 2016 e Project 2016 nello stesso pacchetto con Office.</p>
<p>Se non si sta distribuendo Office, è possibile creare un pacchetto che contiene Visio e/o Project, purché si seguano i requisiti di creazione di pacchetti, pubblicazioni e distribuzione descritti in questo argomento.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Come è possibile distribuire Visio 2016 e Project 2016 a utenti specifici?</p></td>
<td align="left"><p>Usare uno dei metodi seguenti:</p>
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Se vuoi...</th>
<th align="left">... quindi usa questo metodo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Creare due pacchetti diversi e distribuirli a un gruppo di utenti diverso</p></td>
<td align="left"><p>Creare e distribuire i pacchetti seguenti:</p>
<ul>
<li><p>Pacchetto che contiene solo la distribuzione di Office in computer i cui utenti necessitano solo di Office.</p></li>
<li><p>Pacchetto che contiene Office, Visio e Project-deploy per i computer i cui utenti hanno bisogno di tutte e tre le applicazioni.</p></li>
</ul></td>
</tr>
<tr class="even">
<td align="left"><p>Se si vuole solo un pacchetto per l'intera organizzazione o se si hanno utenti che condividono computer:</p></td>
<td align="left"><p>Segue questa procedura:</p>
<ol>
<li><p>Creare un pacchetto che contiene Office, Visio e Project.</p></li>
<li><p>Distribuire il pacchetto a tutti gli utenti.</p></li>
<li><p>Usare <a href="https://technet.microsoft.com/library/dd723678.aspx" data-raw-source="[Microsoft AppLocker](https://technet.microsoft.com/library/dd723678.aspx)"> Microsoft AppLocker </a> per impedire a utenti specifici di usare Visio e Project.</p></li>
</ol></td>
</tr>
</tbody>
</table>
<p> </p></td>
</tr>
</tbody>
</table>


## Risorse aggiuntive


[Distribuzione di Microsoft Office 2013 tramite App-V](deploying-microsoft-office-2013-by-using-app-v.md)

[Distribuzione di Microsoft Office 2010 con App-V](deploying-microsoft-office-2010-by-using-app-v.md)

[Strumento di distribuzione di Office 2016 per l'esecuzione a portata di clic](https://www.microsoft.com/download/details.aspx?id=49117)

**Gruppi di connessioni**

[Distribuzione di gruppi di connessioni in Microsoft App-V v5](https://go.microsoft.com/fwlink/p/?LinkId=330683)

[Gestione dei gruppi di connessione](managing-connection-groups.md)

**Configurazione dinamica**

[Informazioni sulla configurazione dinamica di App-V 5.1](about-app-v-51-dynamic-configuration.md)





