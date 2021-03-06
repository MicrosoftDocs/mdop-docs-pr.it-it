---
title: Guida dettagliata per Gestione avanzata Criteri di gruppo Microsoft 2.5
description: Guida dettagliata per Gestione avanzata Criteri di gruppo Microsoft 2.5
author: dansimp
ms.assetid: 454298c9-0fab-497a-9808-c0246a4c8db5
ms.reviewer: ''
manager: dansimp
ms.author: dansimp
ms.pagetype: mdop
ms.mktglfcycl: manage
ms.sitesec: library
ms.prod: w10
ms.date: 08/30/2016
ms.openlocfilehash: 67925e417e4fb1f5398dfd030f366936f1d36909
ms.sourcegitcommit: 354664bc527d93f80687cd2eba70d1eea024c7c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "10820195"
---
# Guida dettagliata per Gestione avanzata Criteri di gruppo Microsoft 2.5


Questa guida dettagliata illustra le tecniche avanzate per la gestione dei criteri di gruppo tramite la console Gestione criteri di gruppo e la gestione avanzata Criteri di gruppo di Microsoft. Advanced Group Policy Management aumenta le funzionalità di GPMC, fornendo:

-   Ruoli standard per la delega delle autorizzazioni per la gestione degli oggetti Criteri di gruppo (GPO) in più amministratori di criteri di gruppo.

-   Un archivio per consentire agli amministratori dei criteri di gruppo di creare e modificare i GPO offline prima di distribuirli in un ambiente di produzione.

-   Possibilità di eseguire il rollback a qualsiasi versione precedente di un oggetto Criteri di controllo.

-   Funzionalità check-in/check-out per gli oggetti Criteri di gruppo per garantire che gli amministratori dei criteri di raggruppamento non sovrascrivano inavvertitamente il lavoro dell'altro.

## Panoramica degli scenari Advanced Group Policy Management


Per questo scenario, si utilizzerà un account utente distinto per ogni ruolo in Advanced Group Policy Management per dimostrare in che modo i criteri di gruppo possono essere gestiti in un ambiente con più amministratori di criteri di gruppo con livelli di autorizzazione diversi. In particolare, verranno eseguite le attività seguenti:

-   L'uso di un account membro del gruppo Domain Admins consente di installare Advanced Group Policy Management e assegnare il ruolo di amministratore Advanced Group Policy Management a un account o un gruppo.

-   Uso degli account a cui assegnare i ruoli di Advanced Group Policy Management, installare client Advanced Group Policy Management.

-   Usando un account con il ruolo amministratore Advanced Group Policy Management, configura Advanced Group Policy Management e delega l'accesso a GPO assegnando ruoli ad altri account.

-   L'uso di un account con il ruolo di Editor richiede la creazione di un oggetto Criteri di tipo, che viene quindi approvato usando un account con il ruolo di approvazione. Con l'account dell'editor, controlla l'oggetto Criteri di ricerca dall'archivio, modifica il GPO, controlla l'oggetto Criteri di ricerca nell'archivio e Richiedi la distribuzione.

-   Usando un account con il ruolo di approvazione, esaminare l'oggetto Criteri di controllo e distribuirlo nell'ambiente di produzione.

-   Usando un account con il ruolo di editor, crea un modello di GPO e usalo come punto di partenza per creare un nuovo GPO.

-   Uso di un account con il ruolo Approvatore, eliminare e ripristinare un oggetto Criteri di stato.

![processo di sviluppo degli oggetti Criteri di gruppo](images/ab77a1f3-f430-4e7d-be58-ee8f9bd1140e.gif)

## Requisiti


I computer in cui si vuole installare Advanced Group Policy Management devono soddisfare i requisiti seguenti ed è necessario creare account per l'uso in questo scenario.

### Requisiti del server Advanced Group Policy Management

Advanced Group Policy Management Server 2.5 richiede WindowsVista® (versione a 32 bit) senza i Service Pack installati o Windows Server® 2003 (versione a 32 bit), nonché la console GPMC. È inoltre necessario essere un membro del gruppo Domain Admins per installare Advanced Group Policy Management Server.

È consigliabile installare Advanced Group Policy Management Server in un server membro o controller di dominio con la versione più recente di GPMC disponibile e supportata da Advanced Group Policy Management. Advanced Group Policy Management usa la GPMC per eseguire il backup e il ripristino degli oggetti Criteri di stato e le versioni più recenti di GPMC includono ulteriori impostazioni dei criteri non disponibili nelle versioni precedenti. Se la versione di GPMC nel server Advanced Group Policy Management è precedente alla versione nei computer usati dagli amministratori per gestire i criteri di gruppo, il server Advanced Group Policy Management non sarà in grado di archiviare le impostazioni dei criteri non disponibili nella versione precedente di GPMC.

In particolare, se il server Advanced Group Policy Management esegue Windows Server2003 e la versione di GPMC che lo ha accompagnato e i computer degli amministratori dei criteri di gruppo eseguono WindowsVista e la versione di GPMC che l'ha accompagnata, è comunque possibile gestire la maggior parte delle impostazioni dei criteri. Tuttavia, le impostazioni dei criteri della GPMC in Windows Vista che non sono disponibili in GPMC in Windows Server 2003, ad esempio quelle correlate al reindirizzamento delle cartelle, alla rete wireless (IEEE 802,11) e alle stampanti distribuite, non possono essere archiviate dal server Advanced Group Policy Management, anche se gli amministratori possono configurarli usando Advanced Group Policy Management nei propri computer.

Se è necessario installare Advanced Group Policy Management in un computer con una versione precedente di GPMC che gli amministratori dei criteri di gruppo sono in esecuzione, vedere il riferimento alle impostazioni dei criteri di gruppo per informazioni dettagliate sulle impostazioni dei criteri disponibili con i sistemi operativi. Per scaricare il riferimento alle impostazioni dei criteri di gruppo, vedere <https://go.microsoft.com/fwlink/?LinkID=106147> .

**Nota**  Non è possibile eseguire la migrazione degli archivi da un server Advanced Group Policy Management o da un server GPOVault con Windows Server2003 a un server Advanced Group Policy che esegue WindowsVista.

Per Windows Server2003, se il server GPOVault è installato nel computer in cui si vuole installare Advanced Group Policy Management, è consigliabile non disinstallare il server GPOVault prima di iniziare l'installazione. L'installazione di Advanced Group Policy Management consente di disinstallare GPOVault server e trasferire automaticamente i dati di archivio di GPOVault esistenti in un archivio Advanced Group Policy Management.

 

### Requisiti client Advanced Group Policy Management

Advanced Group Policy Management Client 2.5 richiede WindowsVista (versione a 32 bit) senza i Service Pack installati o Windows Server2003 (versione a 32 bit), nonché la console GPMC. Il client Advanced Group Policy Management può essere installato in un computer che utilizza Advanced Management Server.

### Requisiti per lo scenario

Prima di iniziare questo scenario, creare quattro account utente. Durante lo scenario, verrà assegnato uno dei ruoli di Advanced Group Policy Management seguenti a ognuno di questi account: amministratore Advanced Group Policy Management (controllo completo), approvatore, editor e revisore. Questi account devono essere in grado di inviare e ricevere messaggi di posta elettronica. Assegnare l'autorizzazione **collegamento GPO** agli account con l'amministratore di Advanced Group Policy Management, l'approvatore e i ruoli di editor facoltativi.

**Nota** 
 L'autorizzazione **collegamento GPO** viene assegnata ai membri di amministratori di dominio e amministratori aziendali per impostazione predefinita. Per assegnare l'autorizzazione **collegamento GPO** ad altri utenti o gruppi, ad esempio account con il ruolo di amministratore o approvatore della gestione avanzata, fare clic sul nodo per il dominio e quindi fare clic sulla scheda **delega** , selezionare **Collega oggetti Criteri**di gruppo, fare clic su **Aggiungi**e selezionare gli utenti o i gruppi a cui assegnare l'autorizzazione.

 

Per questo scenario, è possibile eseguire azioni con account diversi. È possibile accedere con ogni account come indicato oppure usare il comando **Esegui come** per avviare la GPMC con l'account indicato.

**Nota**  Per usare il comando **Esegui come** con GPMC in Windows Server2003, fare clic sul pulsante **Start**, scegliere **strumenti di amministrazione**, fare clic con il pulsante destro del mouse su **Gestione criteri di gruppo**e scegliere Esegui con **nome**. Fare clic **sull'utente seguente** e immettere le credenziali per un account.

Per usare il comando **Esegui come** con GPMC in Windows Vista, fare clic sul pulsante **Start** , scegliere **Esegui**e digitare **runas/user:** <em> nel NomeDominio omeutente </em> **"mmc%windir%\\system32\\gpmc.msc"** e fare clic su **OK**. Quando richiesto, digitare la password per l'account.

 

## Procedura per l'installazione e la configurazione di Advanced Group Policy


Per installare e configurare Advanced Group Policy Management, è necessario completare la procedura seguente.

[Passaggio 1: installare Advanced Group Policy Management Server](#bkmk-config1)

[Passaggio 2: installare il client Advanced Group Policy Management](#bkmk-config2)

[Passaggio 3: configurare una connessione al server Advanced Group Policy Management](#bkmk-config3)

[Passaggio 4: configurare la notifica tramite posta elettronica](#bkmk-config4)

[Passaggio 5: delega dell'accesso](#bkmk-config5)

### <a href="" id="bkmk-config1"></a>Passaggio 1: installare Advanced Group Policy Management Server

In questo passaggio verrà installato il server Advanced Group Policy Management nel server membro o controller di dominio che eseguirà il servizio Advanced Group Policy Management e si configurerà l'archivio. Tutte le operazioni Advanced Group Policy Management vengono gestite tramite questo servizio Windows e vengono eseguite con le credenziali del servizio. L'archivio gestito da un server Advanced Group Policy Management può essere ospitato in tale server o in un altro server della stessa foresta.

**Per installare Advanced Group Policy Management Server nel computer in cui è ospitato il servizio Advanced Group Policy Management**

1.  Accedere con un account membro del gruppo Domain Admins.

2.  Avviare il CD di Microsoft Desktop Optimization Pack e seguire le istruzioni visualizzate per selezionare **Gestione criteri di gruppo avanzati-server**.

3.  Nella finestra di dialogo **Introduzione** fare clic su **Avanti**.

4.  Nella finestra di dialogo **condizioni di licenza software Microsoft** accettare i termini e fare clic su **Avanti**.

5.  Nella finestra di dialogo **percorso applicazione** selezionare una posizione in cui installare il server Advanced Group Policy Management. Il computer in cui è installato il server Advanced Group Policy Management ospita il servizio Advanced Group Policy Management e gestisce l'archivio. Fai clic su **Avanti**.

6.  Nella finestra di dialogo **percorso di archiviazione** selezionare un percorso per l'archivio relativo al server Advanced Group Policy Management. Il percorso di archiviazione può puntare a una cartella nel server Advanced Group Policy Management o altrove, ma è necessario selezionare una posizione con spazio sufficiente per archiviare tutti i GPO e i dati della cronologia gestiti da questo server Advanced Group Policy Management. Fai clic su **Avanti**.

7.  Nella finestra di dialogo **account del servizio Advanced Group Policy Management** selezionare un account del servizio in cui verrà eseguito il servizio Advanced Group Policy Management e quindi fare clic su **Avanti**.

8.  Nella finestra di dialogo **proprietario archivio** selezionare un account o un gruppo a cui assegnare inizialmente il ruolo amministratore Advanced Group Policy Management (controllo completo). Questo amministratore della gestione avanzata Criteri di amministrazione può assegnare i ruoli e le autorizzazioni di Advanced Group Policy ad altri amministratori di criteri di gruppo, incluso il ruolo di amministratore Advanced Per questo scenario, selezionare l'account da usare nel ruolo amministratore Advanced Group Policy Management. Fai clic su **Avanti**.

9.  Fare clic su **Installa**e quindi su **fine** per uscire dalla configurazione guidata.

    **Attenzione**  Non modificare le impostazioni per il servizio Advanced Group Policy Management tramite strumenti e **Servizi** **amministrativi** nel sistema operativo. Questa operazione può impedire l'avvio del servizio Advanced Group Policy Management. Per informazioni su come modificare le impostazioni per il servizio, vedere la guida per la gestione avanzata dei criteri di gruppo.

     

### <a href="" id="bkmk-config2"></a>Passaggio 2: installare il client Advanced Group Policy Management

Ogni amministratore dei criteri di gruppo, tutti gli utenti che creano, modifica, distribuisce, esamina o Elimina GPO, deve avere installato client Advanced Group Policy Management in computer che usano per gestire i GPO. Per questo scenario, è possibile installare il client Advanced Group Policy in almeno un computer. Non è necessario installare il client Advanced Group Policy Management nei computer degli utenti finali che non eseguono l'amministrazione dei criteri di gruppo.

**Per installare il client Advanced Group Policy Management nel computer di un amministratore di criteri di gruppo**

1.  Avviare il CD di Microsoft Desktop Optimization Pack e seguire le istruzioni visualizzate per selezionare **Gestione criteri di gruppo avanzati-client**.

2.  Nella finestra di dialogo **Introduzione** fare clic su **Avanti**.

3.  Nella finestra di dialogo **condizioni di licenza software Microsoft** accettare i termini e fare clic su **Avanti**.

4.  Nella finestra di dialogo **percorso applicazione** selezionare una posizione in cui installare client Advanced Group Policy Management. Fai clic su **Avanti**.

5.  Nella finestra di dialogo **server Advanced Group Policy Management** Digitare il nome completo del computer e la porta per il server Advanced Group Policy Management a cui connettersi. La porta predefinita per il servizio Advanced Group Policy Management è 4600. Fai clic su **Avanti**.

6.  Fare clic su **Installa**e quindi su **fine** per uscire dalla configurazione guidata.

### <a href="" id="bkmk-config3"></a>Passaggio 3: configurare una connessione al server Advanced Group Policy Management

La Advanced Group Policy Management archivia tutte le versioni di ogni oggetto Criteri di gruppo (GPO) controllato, un GPO per cui Advanced Group Policy Management fornisce il controllo delle modifiche, in un archivio centrale, quindi gli amministratori dei criteri di gruppo possono visualizzare e modificare i GPO offline senza influire immediatamente sulla versione distribuita di ogni oggetto.

In questo passaggio si configura una connessione al server Advanced Group Policy Management e si assicura che tutti gli amministratori di criteri di gruppo si connettano allo stesso server Advanced Group Policy Management Per informazioni sulla configurazione di più server Advanced Group Policy Management, vedere Guida per la gestione avanzata di criteri di gruppo.

**Per configurare una connessione al server Advanced Group Policy Management per tutti gli amministratori dei criteri di gruppo**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con l'account utente selezionato come proprietario dell'archivio. Questo utente ha il ruolo di amministratore Advanced Group Policy Management (controllo completo).

2.  Fare clic sul pulsante **Start**, scegliere **strumenti di amministrazione**e **Gestione criteri di gruppo** per aprire la **console Gestione criteri di gruppo**.

3.  Nell'albero della **console di gestione di criteri di gruppo** modificare un oggetto Criteri di gruppo applicato a tutti gli amministratori dei criteri di raggruppamento.

4.  Nella finestra **Editor oggetti Criteri di gruppo** fare clic **su configurazione utente**, **modelli amministrativi**e **componenti di Windows**.

5.  Se **Advanced Group Policy Management** non è elencato in **componenti di Windows**:

    1.  Fare clic con il pulsante destro del mouse su **modelli amministrativi** e scegliere **Aggiungi/Rimuovi modelli**.

    2.  Fare clic su **Aggiungi**, selezionare **Advanced Group Policy Management. admx** o **Advanced Group Policy Management. adm**, fare clic su **Apri**e quindi su **Chiudi**.

6.  In **componenti di Windows**fare doppio clic su **Advanced Group Policy Management**.

7.  Nel riquadro dei dettagli fare doppio clic su **server Advanced Group Policy Management (tutti i domini)**.

8.  Nella finestra delle **proprietà del server Advanced Group Policy Management (tutti i domini)** selezionare **abilitato** e digitare il nome completo del computer e la porta, ad esempio server.contoso.com:4600, per il server che ospita l'archivio. La porta utilizzata dal servizio Advanced Group Policy Management è la porta 4600.

9.  Fare clic su **OK**e quindi chiudere la finestra **Editor oggetti Criteri di gruppo** . Quando i criteri di gruppo vengono aggiornati, la connessione del server Advanced Group Policy Management viene configurata per ogni amministratore di criteri di gruppo

### <a href="" id="bkmk-config4"></a>Passaggio 4: configurare la notifica tramite posta elettronica

In qualità di amministratore Advanced Group Policy Management (controllo completo), è possibile designare gli indirizzi di posta elettronica degli approvatori e degli amministratori della gestione avanzata dati a cui viene inviato un messaggio di posta elettronica contenente una richiesta quando un editor tenta di creare, distribuire o eliminare un oggetto Criteri di gruppo. Puoi anche determinare l'alias da cui vengono inviati questi messaggi.

**Per configurare la notifica tramite posta elettronica per Advanced Group Policy Management**

1.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

2.  Nel riquadro dei dettagli fare clic sulla scheda **delega del dominio** .

3.  Nel campo **da** Digitare l'alias di posta elettronica per Advanced Group Policy Management da cui inviare le notifiche.

4.  Nel campo **a** Digitare l'indirizzo di posta elettronica per l'account utente a cui si vuole assegnare il ruolo di approvatore.

5.  Nel campo **server SMTP** Digitare un server di posta SMTP valido.

6.  Nei campi **nome utente** e **password** digitare le credenziali di un utente con accesso al servizio SMTP.

7.  Fai clic su **Applica**.

### <a href="" id="bkmk-config5"></a>Passaggio 5: delega dell'accesso

In qualità di amministratore Advanced Group Policy Management (controllo completo) deleghi l'accesso a livello di dominio a GPO, assegnando ruoli all'account di ogni amministratore di criteri di gruppo.

**Nota**  È anche possibile delegare l'accesso a livello di GPO invece che a livello di dominio. Per informazioni dettagliate, vedere Guida per la gestione avanzata di criteri di gruppo.

 

**Importante**  Devi limitare l'appartenenza al gruppo proprietari creatori di criteri di gruppo, in modo che non possa essere usato per eludere la gestione di Access a GPO per Advanced Group Policy Management. Nella console di **gestione di criteri di gruppo**fare clic su **oggetti Criteri di gruppo** nella foresta e nel dominio in cui si vogliono gestire gli oggetti GPO, fare clic su **delega**e quindi configurare le impostazioni in modo che soddisfino le esigenze dell'organizzazione.

 

**Per delegare l'accesso a tutti i GPO in un dominio**

1.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

2.  Nella scheda **delega del dominio** fare clic sul pulsante **Avanzate** .

3.  Nella finestra di dialogo **autorizzazioni** :

    1.  Fare clic sull'account utente di un amministratore di criteri di gruppo e quindi selezionare la casella di controllo **approvatore** per assegnare il ruolo all'account. Deselezionare la casella di controllo **Editor** . Questo ruolo include il ruolo di revisore.

    2.  Fare clic sull'account utente di un altro amministratore di criteri di gruppo e quindi selezionare la casella di controllo **Editor** per assegnare il ruolo all'account. Questo ruolo include il ruolo di revisore.

    3.  Fare clic su un terzo account e quindi selezionare la casella di controllo **revisore** per assegnare solo il ruolo di revisore all'account di tale amministratore dei criteri di gruppo. Deselezionare la casella di controllo **Editor** .

    4.  Fare clic sul pulsante **Avanzate** .

4.  Nella finestra di dialogo **impostazioni di sicurezza avanzate** :

    1.  Selezionare un amministratore di criteri di gruppo e quindi fare clic su **modifica**.

    2.  In **applica**a selezionare **questo oggetto e gli oggetti annidati**e quindi fare clic su **OK** nella finestra di dialogo **immissione** delle **autorizzazioni** .

    3.  Ripetere l'impostazione per ogni amministratore di criteri di gruppo.

5.  Nella finestra di dialogo **impostazioni di sicurezza avanzate** fare clic su **OK**.

6.  Nella finestra di dialogo **autorizzazioni** fare clic su **OK**.

## Procedura per la gestione dei GPO


È necessario completare la procedura seguente per creare, modificare, rivedere e distribuire GPO tramite Advanced Group Policy Management. Verrà inoltre creato un modello, eliminato un oggetto Criteri di stato e il ripristino di un oggetto Criteri di stato eliminato.

[Passaggio 1: creare un oggetto Criteri di stato](#bkmk-manage1)

[Passaggio 2: modificare un oggetto Criteri di stato](#bkmk-manage2)

[Passaggio 3: rivedere e distribuire un GPO](#bkmk-manage3)

[Passaggio 4: usare un modello per creare un GPO](#bkmk-manage4)

[Passaggio 5: eliminare e ripristinare un GPO](#bkmk-manage5)

### <a href="" id="bkmk-manage1"></a>Passaggio 1: creare un oggetto Criteri di stato

In un ambiente con più amministratori di criteri di gruppo, coloro che hanno il ruolo di editor possono richiedere la creazione di nuovi GPO, ma tale richiesta deve essere approvata da un utente con il ruolo di approvatore perché la creazione di un nuovo GPO ha un impatto sull'ambiente di produzione.

In questo passaggio si utilizzerà un account con il ruolo di editor per richiedere la creazione di un nuovo oggetto Criteri di stato. Usando un account con il ruolo di approvatore, approvare la richiesta e completare la creazione di un GPO.

**Per richiedere la creazione di un nuovo GPO gestito tramite Advanced Group Policy Management**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con un account utente a cui è stato assegnato il ruolo di editor in Advanced Group Policy Management.

2.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

3.  Fare clic con il pulsante destro del mouse sul nodo **Cambia controllo** e quindi scegliere **nuovo GPO controllato**.

4.  Nella finestra di dialogo **nuovo GPO controllato** :

    1.  Per ricevere una copia della richiesta, digitare l'indirizzo di posta elettronica nel campo **CC** .

    2.  Digitare **MioGPO** come nome per il nuovo oggetto Criteri di stato.

    3.  Digitare un commento per il nuovo oggetto Criteri di ricerca.

    4.  Fare clic su **Crea Live** in modo che il nuovo GPO venga distribuito nell'ambiente di produzione immediatamente dopo l'approvazione.

    5.  Fai clic su **Invia**.

5.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Il nuovo GPO viene visualizzato nella scheda **in sospeso** .

**Per approvare la richiesta in sospeso per creare un oggetto Criteri di stato**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con un account utente a cui è stato assegnato il ruolo di responsabile approvazione in Advanced Group Policy Management.

2.  Aprire la posta in arrivo per l'account e notare che è stato ricevuto un messaggio di posta elettronica dall'alias Advanced Group Policy Management con la richiesta dell'editor per creare un oggetto Criteri di ricerca.

3.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

4.  Nella scheda **contenuto** fare clic sulla scheda **in sospeso** per visualizzare gli oggetti Criteri di stato in sospeso.

5.  Fare clic con il pulsante destro del mouse su **MioGPO**e quindi scegliere **approva**.

6.  Fare clic su **Sì** per confermare l'approvazione della creazione dell'oggetto Criteri di stato. Il GPO viene spostato nella scheda **controllato** .

### <a href="" id="bkmk-manage2"></a>Passaggio 2: modificare un oggetto Criteri di stato

Puoi usare i GPO per configurare le impostazioni di computer o utenti e distribuirle a molti computer o utenti. In questo passaggio si usa un account con il ruolo di editor per estrarre un oggetto Criteri di ricerca dall'archivio, modificare l'oggetto Criteri di stato offline, controllare l'oggetto Criteri di controllo modificato nell'archivio e richiedere la distribuzione del GPO all'ambiente di produzione. Per questo scenario, devi configurare un'impostazione nell'oggetto Criteri di ricerca per richiedere che la password abbia almeno otto caratteri di lunghezza.

**Per controllare l'oggetto Criteri di ricerca dall'archivio per la modifica**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con un account utente a cui è stato assegnato il ruolo di editor in Advanced Group Policy Management.

2.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

3.  Nella scheda **contenuto** del riquadro dei dettagli fare clic sulla scheda **controllati** per visualizzare gli oggetti Criteri di controllo controllati.

4.  Fare clic con il pulsante destro del mouse su **MioGPO**e quindi scegliere **Estrai**.

5.  Digitare un commento da visualizzare nella **cronologia** del GPO mentre è estratto e quindi fare clic su **OK**.

6.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Nella scheda **controllato** lo stato dell'oggetto Criteri di controllo viene identificato come **Estratto**.

**Per modificare l'oggetto Criteri di stato offline e configurare la lunghezza minima della password**

1.  Nella scheda **controllo** , fare clic con il pulsante destro del mouse su **MioGPO**e quindi scegliere **modifica** per aprire la finestra **Editor oggetti Criteri di gruppo** e apportare modifiche a una copia offline dell'oggetto. Per questo scenario, configurare la lunghezza minima della password:

    1.  In **Configurazione computer**fare doppio clic su **impostazioni di Windows**, fare doppio clic su **impostazioni di sicurezza**, fare doppio clic su criteri **account**e quindi fare doppio clic su **criteri password**.

    2.  Nel riquadro dei dettagli fare doppio clic su **lunghezza minima password**.

    3.  Nella finestra Proprietà selezionare la casella di controllo **Definisci l'impostazione del criterio** , impostare il numero di caratteri su **8**e quindi fare clic su **OK**.

2.  Chiudere la finestra **Editor oggetti Criteri di gruppo** .

**Per controllare l'oggetto Criteri di ricerca nell'archivio**

1.  Nella scheda **controllato** fare clic con il pulsante destro del mouse su **MioGPO** e quindi scegliere **Archivia**.

2.  Digitare un commento e quindi fare clic su **OK**.

3.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Nella scheda **controllato** lo stato dell'oggetto Criteri di controllo viene identificato come **archiviato**.

**Per richiedere la distribuzione del GPO all'ambiente di produzione**

1.  Nella scheda **controllato** fare clic con il pulsante destro del mouse su **MioGPO** e quindi scegliere **Distribuisci**.

2.  Poiché questo account non è un approvatore o un amministratore della Advanced Group Policy Management, è necessario inviare una richiesta di distribuzione. Per ricevere una copia della richiesta, digitare l'indirizzo di posta elettronica nel campo **CC** . Digitare un commento da visualizzare nella **cronologia** del GPO e quindi fare clic su **Invia**.

3.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. **MioGPO** viene visualizzato nell'elenco dei GPO nella scheda **in sospeso** .

### <a href="" id="bkmk-manage3"></a>Passaggio 3: rivedere e distribuire un GPO

In questo passaggio si funge da approvatore, si creano report e si analizzano le impostazioni e le modifiche apportate alle impostazioni nell'oggetto Criteri di stato per determinare se è necessario approvarle. Dopo aver valutato l'oggetto Criteri di gruppo, è necessario distribuirlo nell'ambiente di produzione e collegarlo a un dominio o a un'unità organizzativa in modo che abbia effetto quando i criteri di raggruppamento vengono aggiornati per i computer di tale dominio o OU.

**Per rivedere le impostazioni nel GPO**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con un account utente a cui è stato assegnato il ruolo di responsabile approvazione in Advanced Group Policy Management. Qualsiasi amministratore di criteri di gruppo con il ruolo revisore, incluso in tutti gli altri ruoli, può rivedere le impostazioni di un oggetto Criteri di controllo.

2.  Aprire la posta in arrivo per l'account e tenere presente che è stato ricevuto un messaggio di posta elettronica dall'alias Advanced Group Policy Management con una richiesta dell'editor per distribuire un oggetto Criteri di ricerca.

3.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

4.  Nella scheda **contenuto** del riquadro dei dettagli fare clic sulla scheda **in sospeso** .

5.  Fare doppio clic su **MioGPO** per visualizzarne la cronologia.

6.  Esaminare le impostazioni della versione più recente di MioGPO:

    1.  Nella finestra **cronologia** fare clic con il pulsante destro del mouse sulla versione del GPO con il timestamp più recente, scegliere **Impostazioni**e quindi fare clic su **report HTML** per visualizzare un riepilogo delle impostazioni del GPO.

    2.  Nel Web browser fare clic su **Mostra tutto** per visualizzare tutte le impostazioni nel GPO.

    3.  Chiudi il browser.

7.  Confrontare la versione più recente di MioGPO con la prima versione archiviata:

    1.  Nella finestra **cronologia** fare clic sulla versione del GPO con il timestamp più recente. Premere **CTRL** e fare clic sulla versione più recente del GPO con uno stato di **check-in**.

    2.  Fare clic sul pulsante **differenze** . La sezione criteri **account/criteri password** è evidenziata in verde e preceduta da **\ [+ \]**, che indica che questa impostazione è configurata solo nella seconda versione dell'oggetto Criteri di gruppo.

    3.  Fare clic su **criteri account/password**. L'impostazione **lunghezza minima password** viene evidenziata anche in verde e preceduta da **\ [+ \]**, che indica che è configurata solo nella seconda versione del GPO.

    4.  Chiudere il Web browser.

**Per distribuire il GPO nell'ambiente di produzione**

1.  Nella scheda **in sospeso** fare clic con il pulsante destro del mouse su **MioGPO** e quindi scegliere **approva**.

2.  Digitare un commento da includere nella cronologia del GPO.

3.  Fai clic su **Sì**. Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Il GPO viene distribuito nell'ambiente di produzione.

**Per collegare l'oggetto Criteri di gruppo a un dominio o un'unità organizzativa**

1.  In GPMC fare clic con il pulsante destro del mouse sul dominio o un'unità organizzativa a cui applicare il GPO configurato e quindi scegliere **collega un oggetto Criteri**di campo esistente.

2.  Nella finestra di dialogo **Seleziona GPO** fare clic su **MioGPO**e quindi su **OK**.

### <a href="" id="bkmk-manage4"></a>Passaggio 4: usare un modello per creare un GPO

In questo passaggio si usa un account con il ruolo di editor per creare un modello, una versione statica non modificabile di un oggetto Criteri di ricerca da usare come punto di partenza per la creazione di nuovi GPO e quindi creare un nuovo GPO basato su tale modello. I modelli sono utili per creare rapidamente più oggetti Criteri di gruppo che includono molte delle stesse impostazioni.

**Per creare un modello basato su un oggetto Criteri di lavoro esistente**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con un account utente a cui è stato assegnato il ruolo di editor in Advanced Group Policy Management.

2.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

3.  Nella scheda **contenuto** del riquadro dei dettagli fare clic sulla scheda **controllato** .

4.  Fare clic con il pulsante destro del mouse su **MioGPO**e quindi scegliere **Salva come modello** per creare un modello che incorpora tutte le impostazioni attualmente in MioGPO.

5.  Digitare **MyTemplate** come nome per il modello e un commento e quindi fare clic su **OK**.

6.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Il nuovo modello viene visualizzato nella scheda **modelli** .

**Per richiedere la creazione di un nuovo GPO gestito tramite Advanced Group Policy Management**

1.  Fare clic sulla scheda **controllato** .

2.  Fare clic con il pulsante destro del mouse sul nodo **Cambia controllo** e quindi scegliere **nuovo GPO controllato**.

3.  Nella finestra di dialogo **nuovo GPO controllato** :

    1.  Per ricevere una copia della richiesta, digitare l'indirizzo di posta elettronica nel campo **CC** .

    2.  Digitare **MioaltroGPO** come nome per il nuovo oggetto Criteri di stato.

    3.  Digitare un commento per il nuovo oggetto Criteri di ricerca.

    4.  Fare clic su **Crea Live**, in modo che il nuovo GPO venga distribuito nell'ambiente di produzione immediatamente dopo l'approvazione.

    5.  Per **da modello GPO**selezionare **MyTemplate**.

    6.  Fai clic su **Invia**.

4.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Il nuovo GPO viene visualizzato nella scheda **in sospeso** .

Usare un account a cui è stato assegnato il ruolo di approvatore per approvare la richiesta in sospeso per creare il GPO come nel [passaggio 1: creare un oggetto Criteri](#bkmk-manage1)di stato. MyTemplate incorpora tutte le impostazioni configurate in MioGPO. Poiché MioaltroGPO è stato creato con MyTemplate, contiene inizialmente tutte le impostazioni contenute in MioGPO nel momento in cui è stato creato MyTemplate. Puoi confermare questa operazione generando un report differenza per confrontare MioaltroGPO con MyTemplate.

**Per controllare l'oggetto Criteri di ricerca dall'archivio per la modifica**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con un account utente a cui è stato assegnato il ruolo di editor in Advanced Group Policy Management.

2.  Fare clic con il pulsante destro del mouse su **MioaltroGPO**e quindi scegliere **Estrai**.

3.  Digitare un commento da visualizzare nella cronologia del GPO mentre è estratto e quindi fare clic su **OK**.

4.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Nella scheda **controllato** lo stato dell'oggetto Criteri di controllo viene identificato come **Estratto**.

**Per modificare l'oggetto Criteri di stato offline e configurare la durata del blocco dell'account**

1.  Nella scheda **controllo** , fare clic con il pulsante destro del mouse su **MioaltroGPO**e quindi scegliere **modifica** per aprire la finestra **Editor oggetti Criteri di gruppo** e apportare modifiche a una copia offline dell'oggetto. Per questo scenario, configurare la lunghezza minima della password:

    1.  In **Configurazione computer**fare doppio clic su **impostazioni di Windows**, fare doppio clic su **impostazioni di sicurezza**, fare doppio clic su criteri **account**e quindi fare doppio clic su **criteri di blocco account**.

    2.  Nel riquadro dei dettagli fare doppio clic sulla **durata del blocco dell'account**.

    3.  Nella finestra Proprietà selezionare la casella di controllo **Definisci questa impostazione**, impostare la durata su **30** minuti e quindi fare clic su **OK**.

2.  Chiudere la finestra **Editor oggetti Criteri di gruppo** .

Selezionare MioaltroGPO nell'archivio e richiedere la distribuzione come per MioGPO nel [passaggio 2: modificare un oggetto Criteri](#bkmk-manage2)di ricerca. Puoi confrontare MioaltroGPO a MioGPO o a MyTemplate usando i report differenze. Tutti gli account che includono il ruolo di revisore (amministratore della gestione avanzata Criteri di amministrazione \ [controllo completo \], approvatore, editor o revisore) possono generare report.

**Per confrontare un oggetto Criteri di confronto a un altro GPO e a un modello**

1.  Per confrontare MioGPO e MioaltroGPO:

    1.  Nella scheda **controllata** fare clic su **MioGPO**. Premere **CTRL** e quindi fare clic su **MioaltroGPO**.

    2.  Fare clic con il pulsante destro del mouse su **MioaltroGPO**, scegliere **differenze**e fare clic su **report HTML**.

2.  Per confrontare MioaltroGPO e MyTemplate:

    1.  Nella scheda **controllata** fare clic su **MioaltroGPO**.

    2.  Fare clic con il pulsante destro del mouse su **MioaltroGPO**, scegliere **differenze**e fare clic su **modello**.

    3.  Selezionare **MyTemplate** e **report HTML**e quindi fare clic su **OK**.

### <a href="" id="bkmk-manage5"></a>Passaggio 5: eliminare e ripristinare un GPO

In questo passaggio si funge da approvatore per eliminare un oggetto Criteri di stato.

**Per eliminare un oggetto Criteri di stato**

1.  In un computer in cui è stato installato il client Advanced Group Policy Management, accedere con un account utente a cui è stato assegnato il ruolo di responsabile approvazione.

2.  Nell'albero della **console di gestione di criteri di gruppo** fare clic su **Cambia controllo** nella foresta e nel dominio in cui si vuole gestire gli oggetti GPO.

3.  Nella scheda **contenuto** fare clic sulla scheda **controllati** per visualizzare gli oggetti Criteri di controllo controllati.

4.  Fare clic con il pulsante destro del mouse su **MioGPO**e quindi scegliere **Elimina**. Fare clic su **Elimina GPO da archiviazione e produzione** per eliminare sia la versione nell'archivio che la versione distribuita del GPO nell'ambiente di produzione.

5.  Digitare un commento da visualizzare in audit trail per il GPO e quindi fare clic su **OK**.

6.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. Il GPO viene rimosso dalla scheda **controllato** e viene visualizzato nella scheda **Cestino** , in cui può essere ripristinato o distrutto.

Occasionalmente potresti scoprire dopo l'eliminazione di un GPO che è ancora necessario. In questo passaggio si funge da approvatore per ripristinare un oggetto Criteri di stato eliminato.

**Per ripristinare un oggetto Criteri di stato eliminato**

1.  Nella scheda **contenuto** fare clic sulla scheda **Cestino** per visualizzare i GPO eliminati.

2.  Fare clic con il pulsante destro del mouse su **MioGPO**e quindi scegliere **Ripristina**.

3.  Digitare un commento da visualizzare nella cronologia del GPO e quindi fare clic su **OK**.

4.  Quando la finestra **stato Advanced Group Policy Management** indica che lo stato di avanzamento complessivo è completato, fare clic su **Chiudi**. L'oggetto Criteri di controllo viene rimosso dalla scheda **Cestino** e viene visualizzato nella scheda **controllati** .

    **Nota**  Il ripristino di un GPO nell'archivio non viene automaticamente ridistribuito nell'ambiente di produzione. Per restituire il GPO all'ambiente di produzione, distribuire il GPO come nel [passaggio 3: rivedere e distribuire un oggetto Criteri di controllo](#bkmk-manage3).

     

Dopo la modifica e la distribuzione di un oggetto Criteri di ricerca, potresti scoprire che le recenti modifiche apportate al GPO causano un problema. In questo passaggio si funge da approvatore per eseguire il rollback a una versione precedente dell'oggetto Criteri di controllo. È possibile eseguire il rollback a qualsiasi versione nella cronologia del GPO. È possibile usare i commenti e le etichette per identificare le versioni valide note e quando sono state apportate modifiche specifiche.

**Per eseguire il rollback a una versione precedente di un oggetto Criteri di controllo**

1.  Nella scheda **contenuto** fare clic sulla scheda **controllati** per visualizzare gli oggetti Criteri di controllo controllati.

2.  Fare doppio clic su **MioGPO** per visualizzarne la cronologia.

3.  Fare clic con il pulsante destro del mouse sulla versione da distribuire, scegliere **Distribuisci**e quindi fare clic su **Sì**.

4.  Quando la finestra di **stato** indica che lo stato di avanzamento complessivo è stato completato, fare clic su **Chiudi**. Nella finestra **cronologia** fare clic su **Chiudi**.

    **Nota**  Per verificare che la versione ridistribuita sia la versione progettata, esaminare un report di differenza per le due versioni. Nella finestra **cronologia** del GPO selezionare le due versioni, fare clic con il pulsante destro del mouse su di esse, scegliere **differenza**e quindi fare clic su **report HTML** o **report XML**.

     

 

 





