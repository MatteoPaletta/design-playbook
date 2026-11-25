# Error & Feedback Handling

```
---
id: pattern-error-feedback
name: Error & Feedback Handling
category: Feedback & Status
tags: [pattern, error, feedback, validation, toast, alert, operation-result]
last_updated: 2026-11-16
---
```

# 1\. Descrizione

Questo pattern definisce come il sistema comunica all'utente l'esito di un'azione, i cambiamenti di stato o il verificarsi di un problema all'interno dell'interfaccia. L'obiettivo principale è rassicurare l'utente tramite un riscontro visivo o testuale immediato, riducendo il carico cognitivo e guidandolo chiaramente verso una soluzione in caso di errore, garantendo al contempo che qualsiasi elemento dinamico inserito nel DOM (Document Object Model) sia correttamente accessibile e gestito.

# 2\. Regole d'Uso (Governance)

## Principii Generali

* **DO:** Fornire sempre un riscontro chiaro all’utente sull’esito di ciascuna operazione, chiamata al backend o interrogazione API.

## Validazione e Campi

* **DO:** Utilizzare segnalazioni circoscritte per errori di digitazione o validazione localizzati su singoli campi.  
* **DO:** Validare il singolo campo e il relativo messaggio di errore solo quando l'utente toglie il focus dal campo.  
* **DO:** Validare un form multi-input esclusivamente dopo che l'utente ha premuto il pulsante di conferma/invio (es. "Continua").  
* **DON'T:** NON usare avvisi generici per validare un singolo punto di inserimento (usa la validazione inline per correzioni immediate. Esempio: in un modulo d'iscrizione, se l'utente inserisce un'email non valida (es. priva del simbolo "@"), mostra subito un messaggio d'errore sotto il campo di testo al momento del cambio di focus (blur), aggiornando il DOM (Document Object Model) in modo multimodale (testo di aiuto rosso \+ icona d'avviso) e annunciandolo allo screen reader via role="alert", senza bloccare la compilazione degli altri campi.  
* **DON'T:** Validare un form multi-campo prematuramente durante la digitazione, generando ansia e messaggi di errore prima che l'utente abbia terminato l'inserimento.

## Feedback Asincrono e Notifiche

* **DO:** Utilizzare avvisi contestuali nella pagina per comunicare variazioni di stato o condizioni che richiedono attenzione all'interno di una specifica sezione, senza interrompere la navigazione globale.  
* **DO:** Utilizzare notifiche temporanee e non bloccanti per feedback asincroni (es. salvataggio in background completato o piccoli errori di rete non bloccanti).  
* **DON'T:** Non usare messaggi temporanei per comunicazioni critiche o errori bloccanti: l'utente non fa in tempo a leggerli o a intraprendere l'azione necessaria.  
* **DON'T:** Non mostrare più di un alert o snackbar alla volta.

## Stati di Caricamento e Interazione

* **DO:** Fornire un feedback istantaneo a ogni interazione diretta (tap, click, swipe) tramite cambi di stato (es. Pressed), transizioni o loader.  
* **DO:** Utilizzare la variante Skeleton dei componenti durante l'attesa di dati asincroni.  
* **DON'T:** Non mostrare schermate vuote durante il caricamento o il passaggio a un’altra schermata.

## Gestione degli Errori Bloccanti e Schermate di Esito

* **DO:** Utilizzare schermate di esito dedicate (OK/KO page) per comunicare l'esito finale e definitivo di un flusso ad alto impatto (es. operazione conclusa o fallita), occupando l'intero focus della pagina.  
* **DO:** Utilizzare il componente Missing items per segnalare il mancato caricamento di porzioni di schermate o contenuto (per esempio, il mancato caricamento delle credenziali nella sezione Portafoglio).  
* **DON'T:** Non sovrapporre più di una Call to Action primaria all'interno di una schermata di esito se l'azione richiesta è univoca e conclusiva.

## Accessibilità e Assistive Technology

* **DO:** Garantire che tutti gli avvisi o i messaggi di stato siano annunciati correttamente dagli screen reader tramite gli attributi ARIA appropriati (es. role="alert" o role="status").  
* **DO:** Portare il focus della tastiera sul primo errore o sull'avviso principale in caso di errori bloccanti multipli.  
* DON’T: escludere immagini decorative

# 5\. Content

# 6\. Criteri di Valutazione AI

Griglia di controllo per verifiche e design critique automatizzate da parte di agenti AI:

* \[Pattern\] Il tipo di messaggio scelto è adeguato al livello di interruzione richiesto (es. notifica temporanea per asincrono/temporaneo, schermata di esito per bloccante/conclusivo)? \[Sì/No\]  
* \[Pattern \- Flow\] In caso di validazione di un form a più campi, l'errore generale viene segnalato solo dopo il tentativo di invio (tap sulla CTA primaria)? \[Sì/No\]  
* \[Content\] Il titolo del messaggio di errore esplicita il problema in modo preciso e NON utilizza la stringa generica "Si è verificato un errore"? \[Sì/No\]  
* \[Content\] Il corpo del testo offre una via di risoluzione ed è privo di codici tecnici (es. "404", "Null")? \[Sì/No\]  
* \[A11y\] I nuovi avvisi a schermo vengono iniettati nel DOM (Document Object Model) con il corretto role="alert" o role="status" per guidare lo Screen Reader? \[Sì/No\]  
* \[A11y\] L'errore è comunicato in modo multi-modale (testo \+ icona) senza affidarsi solo al colore? \[Sì/No\]  
* \[A11y\] L'errore viene comunicato annunciandolo allo screen reader via role="alert", senza bloccare la compilazione degli altri campi? \[Sì/No\]

# **Wizard & Multi-step Flow**

```
---
id: pattern-wizard-multistep
name: Wizard & Multi-step Flow
category: Navigation & Workflows
tags: [pattern, wizard, multi-step, form, progress-indicator, navigation, accessibility]
last_updated: 2026-11-18
---
```

# **1\. Descrizione**

Il pattern Wizard & Multi-step guida l'utente attraverso un processo complesso o articolato suddividendolo in una sequenza di passaggi logici e lineari. Riduce il carico cognitivo focalizzando l'attenzione su una singola sotto-attività alla volta, mostrando in modo chiaro l'avanzamento complessivo e consentendo di rivedere o modificare i dati inseriti. È particolarmente indicato per flussi di creazione e configurazione, adesione o inserimento dati lungo, e garantisce che ogni aggiornamento dinamico apportato all'interfaccia o al DOM (Modello a Oggetti del Documento) sia perfettamente accessibile e tracciabile.

# **2\. Regole d'Uso (Governance)**

## **Struttura e Sequenza dei Passaggi**

* **DO:** Suddividere il processo in un numero contenuto di passaggi chiari e sequenziali (idealmente tra 3 e 5 passaggi) organizzati secondo un ordine logico.  
* **DON'T:** Non creare wizard eccessivamente lunghi (oltre 7-8 step) o con un solo passaggio, per evitare disorientamento o sovrastrutture inutili.

**Navigazione e Indicatore di Progresso**

* **DO:** Mostrare sempre un indicatore di progresso visibile e aggiornato (es. "Passaggio X di Y") con etichette descrittive per ciascuno step.  
* **DO:** Fornire controlli di navigazione espliciti ed etichettati chiaramente per andare avanti ("Continua") e per tornare indietro ("Indietro").  
* **DON'T:** Non nascondere il pulsante per tornare al passaggio precedente   
* **DON’T:** Non azzerare i dati già inseriti quando l'utente retrocede nel flusso.

## **Validazione e Gestione Errori**

* ## **DO:** Validare la completezza dei dati obbligatori di ogni singolo step al momento dell’avanzamento allo step successivo.

* ## **DO:** Validare la correttezza dei singoli campi al cambio di focus (blur) del campo.

* **DO:** Fornire un riepilogo finale prima dell'invio definitivo per permettere la verifica complessiva e la correzione puntuale dei dati.  
* **DON'T:** Non consentire il passaggio allo step successivo se il passaggio corrente contiene errori di validazione non risolti.

## **Persistenza e Salvataggio dello Stato**

* **DO:** Preservare lo stato dei campi compresi i dati immessi tra le varie schermate e salvare automaticamente i progressi ad ogni avanzamento di step.  
* **DON'T:** Non abbandonare la sessione utente cancellando l'input in caso di chiusura accidentale o navigazione a ritroso.  
* **DO:** Richiedere una conferma esplicita tramite una finestra modale prima di uscire o interrompere il wizard.  
* **DO:** Chiedere sempre una conferma esplicita mediante modale prima di completare o inviare il wizard.

# **3\. Stati e Comportamenti**

* **Stato Iniziale / Primo Step:** L'utente viene introdotto al flusso con l'indicazione chiara dell'obiettivo e del numero totale di passaggi.  
* **Stato Intermedio / In Corso:** L'indicatore di progresso evidenzia lo step attivo, contrassegna come completati quelli precedenti e rende disabilitati o non selezionabili gli step futuri non ancora raggiunti.  
* **Stato di Transizione:** Durante il passaggio tra uno step e l'altro o la chiamata a servizi asincroni, viene visualizzato un loader o uno stato Skeleton per evitare clic multipli e garantire un riscontro visivo immediato.  
* **Stato di Rivedi / Riepilogo:** Schermata finale prima dell'invio che mostra tutti i dati inseriti con la possibilità di accedere direttamente alla modifica dei singoli passaggi.  
* **Stato Completato (OK / KO Page):** Schermata conclusiva di esito che conferma l'operazione eseguita con successo o segnala l'errore bloccante definitivo fornendo azioni di recupero.

## **4\. Accessibilità**

* **DO:** Strutturare la navigazione del wizard garantendo il supporto completo alle tecnologie assistive e agli screen reader mediante regioni aria-live e attributi ARIA appropriati (es. aria-current="step" sull'indicatore di progresso).  
* **DO:** Spostare automaticamente il focus della tastiera all'inizio della nuova schermata o sul primo elemento interattivo/errore al cambio di passaggio, aggiornando dinamicamente il DOM (Modello a Oggetti del Documento).  
* **DO:** Assicurare che i testi, le etichette degli step e le istruzioni non presentino troncamenti e mantengano un contrasto cromatico sufficiente conforme alle linee guida WCAG.  
* **DON'T:** Non affidarsi esclusivamente a elementi visivi o cromatici per comunicare lo step corrente o lo stato di avanzamento senza corrispondenti alternative testuali accessibili.

# **5\. Content**

# **6\. Criteri di Valutazione AI**

Griglia di controllo per verifiche e design critique automatizzate da parte di agenti AI su flussi Wizard & Multi-step:

* \[Pattern \- Flow\] Il processo è suddiviso in un numero ridotto di step logici sequenziali con un indicatore di progresso sempre visibile e aggiornato? \[Sì/No\]  
* \[Pattern \- Navigation\] La navigazione permette di tornare indietro senza perdere i dati già inseriti e senza resettare i campi? \[Sì/No\]  
* \[Pattern \- Validation\] La validazione blocca l'avanzamento allo step successivo solo in presenza di errori nel passaggio corrente e fornisce messaggi chiari e contestuali? \[Sì/No\]  
* \[Content\] Tutte le etichette dei passaggi e le istruzioni di navigazione sono esplicite, comprensibili e prive di troncamenti? \[Sì/No\]  
* \[A11y\] Gli aggiornamenti di stato e il cambio di passaggio iniettati nel DOM (Modello a Oggetti del Documento) vengono annunciati correttamente dallo Screen Reader tramite aria-live o aria-current="step"? \[Sì/No\]  
* \[A11y\] Il focus della tastiera viene riposizionato correttamente all'inizio di ciascun nuovo passaggio? \[Sì/No\]  
* \[A11y\] È stata prevista una schermata di riepilogo o di conferma finale prima dell'invio definitivo del flusso? \[Sì/No\]

# **Navigation & Page Hierarchy**

```
---
id: pattern-navigation-hierarchy
name: Navigation & Page Hierarchy
category: Navigation & Architecture
tags: [pattern, navigation, hierarchy, information-architecture, wayfinding, accessibility]
last_updated: 2026-11-18
---
```

# **1\. Descrizione**

Il pattern Navigation & Page Hierarchy definisce la struttura informativa, semantica e visiva che permette all'utente di orientarsi all'interno dell'applicazione, comprendere la propria posizione corrente e navigare in modo intuitivo tra i diversi livelli di profondità dell'interfaccia. Stabilisce l'organizzazione logica di intestazioni, landmark, breadcrumb, menu di navigazione e livelli sequenziali. Una gerarchia ben strutturata garantisce una fruibilità ottimale sia visivamente sia attraverso tecnologie assistive, assicurando che l'albero della struttura nel DOM (Document Object Model) rispecchi fedelmente l'organizzazione concettuale del contenuto.

# **2\. Regole d'Uso (Governance)**

## **Struttura e Sequenza dei Passaggi**

* **DO:** Organizzare i contenuti secondo una gerarchia sequenziale e nidificata di titoli (\<h1\> fino a \<h6\>), mantenendo un unico \<h1\> principale per pagina per definire il contesto primario.  
* **DON'T:** Non saltare livelli di intestazione (es. passare da \<h1\> a \<h3\> senza \<h2\>)  
* **DON’T**: Non usare un titolo grande (come un \<h1\> o un \<h2\>) per motivi stilistici o se quel testo non è un vero titolo di sezione.

**Navigazione e Indicatore di Progresso**

* **DO:** Fornire sempre un sistema di wayfinding coerente (es. breadcrumb) e landmark ARIA espliciti (\<nav\>, \<main\>, \<header\>, \<footer\>, \<aside\>) per identificare le macro-aree di pagina.  
* **DO:** Indicare chiaramente l'elemento attivo nel menu di navigazione utilizzando l'attributo aria-current="page" nel DOM (Document Object Model).  
* **DON'T:** Non modificare l'ordine visivo del layout in modo discordante rispetto all'ordine degli elementi nel DOM (Document Object Model) per prevenire disorientamento nella navigazione via tastiera.  
* **DON'T:** Non basare la comprensione della struttura gerarchica unicamente sul colore o sulla dimensione del font senza opportuni tag semantici.

## **Validazione e Gestione Errori**

* ## **DO:** Gestire correttamente il cambio di pagina o sezione nelle Single Page Application (SPA) riposizionando programmaticamente il focus della tastiera sull'intestazione principale \<h1\>.

* ## **DO:** Includere un link di salto rapido al contenuto primario ("Skip to main content") come primo elemento interattivo della pagina nel DOM (Document Object Model).

* **DO:** Mantenere la profondità dell'albero di navigazione entro 3-4 livelli per evitare una complessità eccessiva della struttura informativa.  
* **DON'T:** Non nascondere elementi di navigazione critici dietro menu a comparsa.

## **Persistenza e Salvataggio dello Stato**

* **DO:** Assicurarsi che l'indirizzo web (URL) cambi e si aggiorni sempre in base a quello che l'utente sta vedendo nella pagina.  
* **DON'T:** Non aggiornare la gerarchia o l'albero dei contenuti nel DOM (Document Object Model) in seguito ad azioni utente senza aggiornare il titolo del documento (\<title\>) o notificare gli screen reader tramite regiolive ARIA.  
* **DO:** Preservare la posizione di scorrimento (scroll position) o la sezione attiva quando l'utente naviga a ritroso verso pagine o sezioni precedentemente consultate.  
* **DON'T:** Non generare collegamenti o modifiche dinamiche all'albero di navigazione che alterino inaspettatamente la struttura della pagina attiva senza un'interazione esplicita dell'utente.

# **3\. Stati e Comportamenti**

* **DO:** Utilizzare sempre Auto-Layout dinamico per comporre le schermate.  
* **DO:** Utilizzare sempre i breakpoint definiti in Figma: nei layout mobile/tablet la navigazione si trasforma in un componente overlay/drawer, preservando la corrispondenza sequenziale degli elementi nel DOM (Document Object Model).  
* **DO:** Progettare sempre le schermate e i flussi dedicati a tutti gli stati di errore prevedibili.

## **4\. Accessibilità**

* **DO:** Definire sempre l’ordine di lettura dei componenti in pagina.  
* **DO:** Strutturare sempre i frame rispettando rigorosamente l'ordine visivo e di lettura da tastiera, specificando le etichette ARIA (aria-label o aria-labelledby) per identificare visivamente e semanticamente i diversi blocchi di navigazione.  
* **DO:** Disegnare lo stato di Focus Visible con uno stile ad alto contrasto cromatico e specificare le regole di gestione del focus per i componenti dinamici nel DOM (Document Object Model) all'interno delle annotazioni di handoff.

# **5\. Content**

# **6\. Criteri di Valutazione AI**

Griglia di controllo per verifiche e design critique automatizzate da parte di agenti AI su flussi Wizard & Multi-step:

* \[Pattern \- Structure\] La pagina segue un'alberatura gerarchica sequenziale di intestazioni (\<h1\>-\<h6\>) senza salti di livello e con un solo \<h1\> primario? \[Sì/No\]  
* \[Pattern \- Wayfinding\] Sono presenti elementi di wayfinding coerenti (breadcrumb, landmark \<nav\>, indicatore di pagina corrente aria-current="page")? \[Sì/No\]  
* \[Pattern \- Focus Management\] Al cambio di pagina/sezione, il focus della tastiera viene riposizionato correttamente sull'intestazione principale \<h1\> o all'inizio del contenuto principale? \[Sì/No\]  
* \[Content\] Le etichette dei menu e dei percorsi di navigazione sono brevi, descrittive e coerenti tra le varie sezioni dell'applicazione? \[Sì/No\]  
* \[A11y\] L'albero semantico nel DOM (Document Object Model) utilizza correttamente i landmark HTML5 (\<header\>, \<nav\>, \<main\>, \<footer\>) e i relativi attributi ARIA? \[Sì/No\]  
* \[A11y\] È presente un link di salto rapido al contenuto primario ("Skip to main content") perfettamente funzionante da tastiera? \[Sì/No\]  
* \[A11y\] L'ordine visivo degli elementi corrisponde esattamente all'ordine di lettura nel DOM (Document Object Model)? \[Sì/No\]