# **Guidelines: fondamenta del design system di IO**

> **Cosa c'è qui:** le regole generali di UX, di accessibilità e dei contenuti (voce, tono, stile, messaggi di errore) e come applicarli.   
> **Cosa NON c'è qui:** la scelta dei componenti e le regole di scrittura di ogni componente (`components.md`), i pattern e gli anti-pattern (`patterns.md`).

---

## **1\. Gestione Anatomia, Token e Spaziature (Spacing)**

**Token Semantici e Code Connect**   
I token cromatici e le specifiche anatomiche sono governati nativamente all'interno di Figma Code Connect e della codebase. I componenti devono attenersi rigorosamente alla codebase come regola assoluta non interpretabile: è vietato inventare o definire valori assoluti (HEX) nei file di documentazione.  
**Spaziature a livello di Template**  
Le regole di spaziatura esterna (margini e padding verso elementi contigui) non appartengono al singolo componente, ma sono gestite dai template UI contenitori (es. layout di pagina, liste o array di card).  
---

## **2\. User experience**

Linee guida fondamentali per la progettazione dell'interfaccia dell'app IO, volte a garantire un'esperienza fluida, accessibile e a ridurre il carico cognitivo dei cittadini.

### **2.1 Gerarchia Visiva e Carico Cognitivo**

* **Progressive Disclosure:** mostra immediatamente solo le informazioni e le azioni essenziali, nascondendo opzioni avanzate o secondarie dietro interazioni specifiche.  
* **Costruzione della gerarchia:** usa la spaziatura, il raggruppamento degli elementi (Legge della Prossimità) e i pesi tipografici per guidare la scansione visiva, non affidarti esclusivamente al colore.  
* **Minimizzare il carico mnemonico:** rendi visibili opzioni, azioni e informazioni chiave. I dettagli del servizio o della transazione devono essere sempre richiamabili o visibili nel contesto d'uso.  
* **Uso dei Key Template:** fai sempre riferimento ai key template del Design System come punto di partenza per la progettazione di qualsiasi nuova schermata.

### **2.2 Visibilità dello Stato e Feedback**

* **Feedback immediato:** ogni interazione diretta (tap, click, swipe) deve essere seguita da un feedback istantaneo (es. stato Pressed, transizione o spinner di caricamento).  
* **Gestione delle attese:** per caricamenti asincroni, privilegiare l'uso di Skeleton rispetto a schermate vuote:  
  * **Skeleton di componente:** per singoli componenti o sezioni quando sono presenti dati in pagina forniti da API.  
  * **Pagina di loading generale:** quando l'intera schermata è in fase di caricamento iniziale e nessun dato strutturale è disponibile.  
* **Visibilità dello stato del sistema:** mantieni l'utente informato sullo stato attuale delle operazioni entro tempi ragionevoli, specialmente durante transazioni economiche o invii di moduli ufficiali.

Stati dell'interfaccia nel contesto d'uso:

* **Default:** stato iniziale del componente.  
* **Active / Pressed:** interazione o selezione attiva.  
* **Disabled:** componente disabilitato e privo di interattività.  
* **Saved:** stato confermato o salvato.  
  * **Skeleton:** fase di caricamento del contenuto.

### **2.3 Controllo Utente e Prevenzione degli Errori**

* **Vie d'uscita chiare:** fornisci sempre un'uscita di sicurezza facilmente individuabile per abbandonare azioni avviate per sbaglio.  
* **Prevenzione attiva degli errori:** usa elementi strutturati per evitare sviste (es. convalida nei campi di testo, helper text, opzioni predefinite).  
* **Frizioni intenzionali:** richiedi una conferma esplicita prima di completare azioni irreversibili o distruttive.  
* **Controllo e libertà dell'utente:** fornisci funzioni come "annulla" o "torna indietro" e la modifica facile dei dati prima dell'invio.  
* **Diagnosi degli errori:** messaggi in linguaggio chiaro e mai tecnico, affiancati da un codice errore copiabile per l'assistenza.

### **2.4 Flessibilità, Efficienza e Consistenza**

* **Acceleratori per utenti esperti:** prevedi scorciatoie e gesture veloci per velocizzare le operazioni frequenti.  
* **Personalizzazione:** consenti di configurare preferenze di notifica e servizi preferiti in Home Page.  
* **Consistenza interna:** mantieni identici i pattern interattivi e il comportamento dei componenti in tutta l'app.  
* **Standard di settore (Legge di Jakob):** sfrutta modelli mentali e interazioni standard dei sistemi operativi mobile (iOS e Android).

### **2.5 Esempi di progettazione (Do & Don't)**

|  Fai così (Do) |  Non così (Don't) |
| ----- | ----- |
| Mostra solo i dati essenziali e nascondi le opzioni secondarie (Progressive Disclosure). | Sovraccaricare la schermata con tutte le informazioni contemporaneamente. |
| Fornisci feedback immediato a ogni tap o swipe (stato Pressed, loader, transizione). | Lasciare l'utente senza riscontro visivo dopo un'interazione. |
| Usa Skeleton per il caricamento dei contenuti di componente. | Mostrare schermate completamente vuote durante le chiamate asincrone. |
| Richiedi una conferma esplicita prima di eseguire azioni irreversibili. | Eliminare dati o metodi di pagamento con un singolo tocco senza conferma. |
| Fornisci sempre un'uscita di sicurezza evidente (es. icona Exit o pulsante Chiudi). | Bloccare l'utente all'interno di un flusso senza possibilità di annullare. |
| Mantieni i pattern interattivi uniformi in tutta l'applicazione. | Usare lo stesso gesto (es. swipe) con significati diversi in varie sezioni. |

### **2.6 Documentazione e Guida**

* **Aiuto contestuale e accessibile:** sebbene il sistema debba essere intuitivo, fornisci supporto contestuale (tooltip, FAQ nell'help contestuale, articoli del Centro Assistenza) conciso e focalizzato sui compiti dell'utente.

---

## **3\. Contenuti**

Regole di scrittura valide per tutta l'interfaccia. Le regole di scrittura dei singoli componenti sono in components.md.

**Testi reali:** progetta sempre con testi reali e definitivi, scritti secondo questa sezione o components.md. Mai testo segnaposto.

**Il testo fa parte del design**: se non entra nel layout, riscrivi il testo o rivedi il layout. Non troncarlo e non rimpicciolirlo.

### **3.1 Personalità e tono di voce**

La personalità di IO non cambia mai. Il tono si adatta al contesto, al messaggio e allo stato emotivo di chi legge.

| Tratto | Cosa significa in pratica |
| ----- | ----- |
| **Utile** | Semplifica la vita delle persone con servizi basati sui loro bisogni e facili da usare. |
| **Innovativa** | Rende immediate e piacevoli anche le esperienze di solito considerate macchinose; supera i pregiudizi verso la Pubblica Amministrazione. |
| **Affidabile** | Dà informazioni ufficiali, sicure e coerenti. Fa quello che promette e non lascia nessuno indietro. |
| **Ampia e accessibile** | Si rivolge a tutte e tutti; abbatte barriere fisiche, cognitive e culturali. |
| **Facilitatrice** | Aiuta a capire le complessità senza nasconderle; spiega il perché delle scelte e permette a chi vuole di approfondire. |

Il tono è sempre:

* **Chiaro e trasparente**: parole comuni, niente termini tecnici, burocratici o settoriali. Va dritto al punto e privilegia l'azione.  
* **Autorevole, con empatia**: informazioni precise che generano fiducia. Guida senza imporre.  
* **Informale**: umano e quotidiano, positivo senza eccedere nell'entusiasmo. Non banalizza le complessità.  
* **Rispettoso e ampio**: niente pregiudizi, inglesismi o espressioni legate a una sola cultura.

#### 

Come dosare il tono:

| Situazione | Esempio di contesto | Enfatizza | Esempio |
| ----- | ----- | ----- | ----- |
| **Neutra** | La persona si informa su un nuovo servizio | Chiarezza, trasparenza, informalità | Paga su IO con PayPal\! Abbina il tuo conto PayPal e paga gli avvisi pagoPA più facilmente. |
| **Positiva** | Un pagamento è andato a buon fine | Positività (puoi far conoscere nuove funzioni), informalità | Conto PayPal abbinato\! Dai uno sguardo alle impostazioni del tuo nuovo metodo e inizia subito a usarlo. |
| **Negativa** | La persona è arrabbiata, impaziente o in ansia | Trasparenza (se c'è un problema, non nasconderlo), guida e rispetto verso la soluzione | Purtroppo, in questo momento non riusciamo ad aiutarti. Sappiamo che c'è un problema e siamo al lavoro per risolverlo. |

### **3.2 Come ci rivolgiamo alle persone**

| Persona | Quando |  Fai così (DO) | Non così (Don’t) |
| ----- | ----- | ----- | ----- |
| **Tu** (2ª singolare) | Sempre, nei testi e nelle CTA. Non esplicitare il soggetto. | Contribuisci a migliorare l’app IO | I cittadini possono contribuire allo sviluppo dell'app |
| **Io** (1ª singolare) | Solo nelle CTA con valore legale (accettare condizioni, consenso al trattamento dei dati) e nelle domande delle FAQ. | Comprendo e accetto i termini e le condizioni del servizio. | DIchiara che comprendi e accetti i termini e le condizioni del servizio. |
| **Noi** (1ª plurale) | Quando parla il team  | Per richiedere assistenza, scrivici: ti risponderemo il prima possibile. | IO ti aiuto |
| **Terza persona** | Solo quando ti riferisci al prodotto. | IO è l'unico punto di accesso ai servizi pubblici, direttamente dal tuo dispositivo | Il cittadino può accedere ai serizi pubblici tramite IO |

* **Mai** la terza persona di cortesia (*lei*).  
* **Mai** parlare di "utenti" o "cittadini" nei testi: dai del tu.

### **3.3 Chiarezza e struttura delle frasi**

**Struttura**

* **Una frase, un concetto**.  
* Ordine: soggetto, verbo, complemento. Evita subordinate, incisi e gerundi.  
* Lunghezza: cerca di restare al massimo in 20 parole per frase. Oltre, dividi il periodo.  
* Piramide invertita: prima le informazioni essenziali, poi i dettagli.  
* **Prima il beneficio, poi come ottenerlo**.

**Forma**

* **Voce attiva**, mai passiva.  
* Frasi affermative: trasforma le negazioni in affermazioni, dove possibile. Mai doppie negazioni.  
* **Niente forme impersonali o astratte**.  
* Più verbi, meno sostantivi: al centro del testo c'è l'azione.  
* **Aggettivi e avverbi**: solo se aggiungono valore.  
* Tempo presente. Futuro semplice, passato prossimo e congiuntivo solo se necessari. Niente altri tempi composti.

**Parole**

* Linguaggio quotidiano: niente termini burocratici o tecnici. Se non esiste un equivalente comune, spiega il significato.  
* Parole familiari, concrete, precise e brevi, non rare, astratte o giri di parole.  
* Niente latinismi, inglesismi e parole straniere.  
* Solo informazioni necessarie: chiediti se la persona ne ha davvero bisogno, e proprio in quel momento.

**Leggibilità**

* Ogni testo deve avere indicativamente un **indice GULPEASE di 60**, cioè essere comprensibile per chi ha la licenza media. L'indice considera la lunghezza delle parole e delle frasi.

Esempi:

| Regola | Fai così (Do) | Non così (Don't) |
| ----- | ----- | ----- |
| **Prima il beneficio** | Aggiungi il tuo metodo di pagamento e impostalo come preferito. | I metodi di pagamento possono essere aggiunti in questa sezione, successivamente potrai scegliere di inserirlo come metodo preferito. |
| **Voce attiva** | Invia la richiesta entro la scadenza. | Le richieste devono essere inoltrate entro e non oltre il termine stabilito. |
| **Niente forme impersonali** | Al momento il servizio non è disponibile. | Si rende noto che il servizio è stato sospeso temporaneamente. |
| **Tempo presente** | In questa pagina puoi aggiungere PayPal come metodo di pagamento. | In questa pagina potrai aggiungere PayPal come metodo di pagamento. |
| **Linguaggio quotidiano** | Adottiamo misure di sicurezza per proteggere i tuoi dati. | Adottiamo misure di sicurezza per proteggere i tuoi dati e, ove possibile, li pseudonimizziamo. |
| **Linguaggio quotidiano** | Per aggiornare l'app, vai nello store del tuo dispositivo. | Al fine di garantire l'ottimale funzionamento dell'app IO, si rende necessario procedere all'aggiornamento della versione software tramite l'interfaccia del marketplace digitale. |
| **Niente inglesismi** | riscontro, risposta, valutazione | feedback |
| **Niente inglesismi** | richiesta di assistenza | ticket |
| **Niente inglesismi** | codice QR | QR code |

### **3.4 Stile e punteggiatura**

#### **Maiuscole**

Usale:

* a inizio frase, nelle sigle e nei nomi di persona;  
* nei nomi delle istituzioni;  
* nei nomi dei prodotti e dei servizi di IO;  
* quando ti riferisci a sezioni dell'app.

Non usarle:

* con la capitalizzazione all'inglese, nemmeno nei titoli;  
* su parole intere per dare enfasi: sono più difficili da leggere e alcuni screen reader le leggono come se "urlassero".

**Eccezioni:** IO è sempre tutto in maiuscolo.

|  Fai così (Do) | Non così (Don't) |
| ----- | ----- |
| CGN, 3DS | cgn, 3ds |
| Dipartimento per le Politiche Giovanili e il Servizio Civile Universale | Dipartimento per le politiche giovanili e il servizio civile universale |
| Vai al Portafoglio | Vai al portafoglio |
| L'app IO | L'App IO |
| Il programma Cashback è terminato | Il programma Cashback è TERMINATO |

#### **Accenti**

* Usa gli accenti corretti, mai apici o apostrofi al loro posto.  
* Scrivi **È**, mai E'.   
* **Perché** ha sempre l'accento acuto: mai "perchè".

#### **Punteggiatura**

| Segno | Regola |
| ----- | ----- |
| **Punto** | Alla fine di ogni frase e nelle notifiche push. Mai in titoli, intestazioni, etichette, voci di menu. |
| **Virgola** | Per separare elementi di un elenco, una parola o una frase introduttiva, periodi lunghi. Se non serve, evitala. |
| **Punto esclamativo** | Con parsimonia: solo per una novità o qualcosa a cui dare enfasi. |
| **Parentesi** | Da evitare: molte persone ignorano il testo tra parentesi. Se serve dividi la frase in due. |
| **Punto e virgola** | Solo alla fine delle voci di un elenco introdotto dai due punti. |
| **Virgolette** | Usale **singole** (' '), non doppie: i testi vivono in file JSON o Markdown, dove le doppie fanno parte della sintassi. Usale per citare una sottosezione dell'app o l'etichetta di un pulsante nel testo: Vai al Portafoglio e seleziona 'I tuoi metodi'. |

#### **D eufonica**

Solo quando si incontrano due vocali uguali.

#### **Articoli**

* **Usali** negli elementi conversazionali: titoli, sottotitoli, descrizioni.  
* Nelle CTA usali quando rendono il testo naturale e completo; togli quelli superflui che allungano il testo.

#### **Acronimi e abbreviazioni**

* La prima volta scrivi il termine per esteso e l'acronimo tra parentesi; poi usa solo l'acronimo.  
* **Mai il punto dopo un acronimo:** lo screen reader potrebbe leggerlo come una parola troncata ("Avvicina la carta al POS." viene letto "…al POSIZIONE").  
* Evita abbreviazioni come p.es.: la chiarezza vale più della brevità.

#### **Elenchi puntati e numerati**

* **Puntati** se gli elementi non sono in sequenza; **numerati** se lo sono.  
* Dopo una frase con i due punti: ogni voce inizia con la minuscola e termina con il punto e virgola; l'ultima termina con il punto.  
* Voci coerenti per lunghezza e formulazione.

#### **Grassetto, corsivo, sottolineato**

* **Grassetto:** solo nei testi lunghi e densi, per far risaltare le parole chiave: azioni, CTA, nomi di elementi dell'interfaccia. Con moderazione. Mai nelle schede servizio. Per la leggibilità, dividi anche il testo in paragrafi.  
* **Corsivo:** mai, nemmeno nelle schede servizio.  
* **Sottolineato:** solo per i link.

#### **Emoji**

**Mai**, né nei testi a schermo né negli alt text: il significato è ambiguo e non aggiungono informazioni. *(Vale solo dentro l'app, non per i social.)*

### **3.5 Numeri, date, valute e altri formati**

| Elemento | Regola | Fai così |  Non così |
| ----- | ----- | ----- | ----- |
| **Numeri** | Sempre in cifre, mai in lettere | Hai ancora 5 settimane per usare la tua Carta Giovani Nazionale. | Hai ancora cinque settimane… |
| **Ordinali** | Per esteso. Mai numeri romani, salvo per le leggi | …a partire dal quinto giorno dopo l'acquisto. | …dal V giorno… · …dal 5° giorno… |
| **Date** | Giorno in numeri e mese per esteso, poi anno. Se manca spazio gg/mm/aaaa. Mesi e giorni della settimana con la minuscola | 1 febbraio 2022 · 01/02/2022 | 1 Febbraio 2022 · 01-02-2022 |
| **Riferimenti temporali** | Sempre precisi, con una data. Niente "domani", "ieri": cambiano con il fuso orario e con il momento della lettura | Hai un avviso che scade il 17/11/2022. Accedi per pagarlo. | Hai un avviso che scade domani. |
| **Valute** | Importo, spazio unificatore (non separabile), simbolo | Hai pagato 124,51 € per 'TARI 2021' | Hai pagato € 124,51… |
| **Indirizzi** | Riga 1: destinatario. Riga 2: via e numero civico. Riga 3: CAP, città, provincia tra parentesi. Virgola solo dopo il numero civico | Maria Bianchi / Via Roma 56, / 20900 Monza (MB) | Maria Bianchi 56, Via Roma / Monza \- Monza Brianza 20900 |
| **Riferimenti normativi** | Nome della norma per esteso, con link alla Gazzetta Ufficiale. Niente abbreviazioni (DL, Art., d.lgs.) | La legge nr. 234 del 30 dicembre 2021 ha stabilito la fine del programma Cashback. | …dalla legge n.234 del 30 dicembre 2021 (art.1, commi 637-644). |
| **URL** | Mai "https" o "www" | Vai su ioitalia.it | Vai su www\.ioitalia.it |
| **Percorsi nell'app** | Usa \> tra i passaggi, senza virgolette, con i nomi aggiornati all'ultima versione dell'app | Nella sezione Profilo \> Preferenze \> Gestione servizi puoi attivare l'inoltro dei messaggi. | Vai a Profilo, Preferenze, Gestione servizi per attivare… |

### **3.6 Linguaggio ampio**

Parti da due elementi: **parole semplici e comprensibili** e **nessuna frase o tono discriminatorio**, derivato da stereotipi o pregiudizi.

**Regola di partenza:** non usare mai termini sessisti, abilisti o razzisti. Neutralità di genere

**Neutralità di genere**

L'italiano non ha il neutro. Applica queste strategie in ordine di preferenza:

1. **Parola collettiva o neutra**.  
2. **Perifrasi**.  
3. **Maschile plurale**, solo se la perifrasi non è possibile. Mai il maschile singolare.

Entrambi i generi, se non è possibile una delle soluzioni precedenti e se lo spazio lo permette (es. le cittadine e i cittadini).

| Strategia | Fai così (Do) | Non così (Don't) |
| ----- | ----- | ----- |
| **Parola neutra** | la cittadinanza | il cittadino |
| **Parola neutra** | il corpo docente | il docente |
| **Parola neutra** | le persone | l'utente |
| **Perifrasi** | Ti diamo il benvenuto | Benvenuto |
| **Perifrasi** | Ti invitiamo a pagare gli avvisi entro 10 giorni dalla ricezione. | I cittadini sono invitati a pagare gli avvisi entro 10 giorni dalla ricezione. |
| **Maschile plurale** | Abbiamo progettato l'app insieme ai cittadini, partendo dalle loro esigenze. | Abbiamo progettato l'app insieme al cittadino, partendo dalle sue esigenze. |

**Identità di genere e orientamento sessuale**

* **Fai riferimento al genere solo se serve.** Nei moduli, chiediti a cosa serve il dato prima di chiederlo.  
* **Se serve, offri opzioni ampie.**  
* **Non dare per scontato che una relazione sia eterosessuale.** Niente termini discriminatori verso la comunità LGBTQI+ e niente stereotipi di genere.

**Disabilità**

* Fai riferimento alla disabilità solo se serve.  
* Le persone hanno una disabilità, non sono la loro disabilità.   
* Le barriere dipendono da spazi, servizi e regole, non dalla persona.

#### **Neurodivergenze**

Le persone neurodivergenti (per esempio con autismo, ADHD, dislessia, disprassia, sindrome di Tourette) elaborano le informazioni in modo diverso dalla media. Contenuti chiari riducono stress, confusione e frustrazione.

* Frasi brevi e dirette, senza gergo né linguaggio figurato.  
* Informazioni in ordine logico e prevedibile, con elenchi puntati o numerati.