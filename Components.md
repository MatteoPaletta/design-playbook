# **Alert**

**Scheda completa del componente Alert** del Design System IO**:** descrizione di quando usarlo, proprietà, varianti, comportamento, accessibilità, **contenuti**, esempi ed errori da evitare.

```
---
id: component-alert
name: Alert
category: Feedback & Status
version: 1.0.0
tags: [alert, feedback, notification]
last_updated: 2026-10-08
---
```

# **Descrizione** 

Il componente Alert viene utilizzato per comunicare un messaggio contestuale o di sistema rilevante per l'utente all'interno della pagina corrente. Ha lo scopo di attirare l'attenzione su informazioni importanti, variazioni di stato o condizioni che richiedono consapevolezza o un'azione correttiva senza interrompere completamente il flusso utente. Il componente adotta uno stile visivo pulito a fondo pieno tenue, privo di bordi decorativi laterali, per garantire massima leggibilità ed essenzialità visiva.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Variante Success:** Conferma di un'operazione completata con esito positivo all'interno della schermata.  
* **Variante Error:** Errori critici che bloccano il processo, oppure scadenze già superate.  
* **Variante Warning:** Avvisi su task da svolgere non bloccanti, scadenze imminenti o rischi potenziali.  
* **Variante Info:** Indicazioni contestuali, note o comunicazioni neutre.

## **Don't (Quando NON usare)**

* Non usare per la validazione dei singoli campi di testo (utilizzare la validazione inline nel campo).  
* Non usare per notifiche temporanee ad auto-scomparsa (utilizzare il componente Toast).  
* Non usare la variante Warning se la data di scadenza è già trascorsa o l'azione è interrotta (utilizzare Error).  
* Non usare più di un Alert contestuale per sezione.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

| Proprietà | Default | Descrizione |
| :---- | :---- | :---- |
| **`variant`** | `info` | Stato visivo e icona associata. Valori: `success`, `error`, `warning`, `info` (triangolo per warning, cerchio per gli altri). |
| **`layout`** | `inline` | Posizionamento nel flusso. Valori: `inline` (contestuale alla pagina/sezione) o `edgeToEdge` (avviso globale fisso in alto). |
| **`action`** | `false` | Mostra o nasconde il pulsante di azione posizionato sotto il testo del messaggio. |
| **`actionLabel`** | `"Riprova"` | Testo del pulsante di azione (valido solo se `action` è attivo). |

# **4\. Stati e Comportamenti**

## **4.1 Layout Edge-To-Edge**

Variante dedicata alle comunicazioni globali di sistema (es. manutenzioni di piattaforma). Viene posizionata fissa in cima allo schermo da bordo a bordo, mantenendo uno stacco di 8px dai contenuti sottostanti.

## **4.2 Azione e Loading**

Se presente una CTA (action: true), l'interazione mostra uno spinner al posto dell'etichetta, imposta aria-busy="true" e disabilita ulteriori tocchi fino al completamento dell'operazione.

# **5\. Accessibilità (A11y)** 

**5.1 Semantica, Screen Reader e Ordine di Lettura**

• Icona Decorativa: L'icona di stato a sinistra DEVE essere nascosta alle tecnologie assistive (accessibilityElementsHidden={true} su iOS / importantForAccessibility="no" su Android). Non deve mai ricevere il focus durante la navigazione.

• Esposizione della Variante (variant): Poiché l'icona è ignorata dagli screen reader, il componente deve comunicare semanticamente la propria natura (success, error, warning, info) tramite etichetta o prefisso annunciato dalla sintesi vocale (es. "Operazione completata:", "Errore:", "Avviso:", "Informazione:").

• Ordine di Focus (Reading Order): Gli screen reader DEVONO leggere gli elementi in ordine strettamente sequenziale dall'alto verso il basso, ignorando gli elementi opzionali disattivati:

1. Contenuto del messaggio — Ruolo: testo (Text).  
2. Pulsante di azione (solo se action: true) — Ruolo interattivo distinto (Button o Link).  
   • Comportamento della CTA (action: true):  
   ◦ Assegnare il ruolo Button per azioni contestuali o di chiusura (es. "Riprova", "Ok, ho capito\!") e il ruolo Link per navigazioni verso altre schermate o risorse esterne (es. "Scopri di più").  
   ◦ Garantire un'area di tocco minima di 44x44pt (iOS) / 48x48dp (Android). Quando l'azione è posizionata inline alla fine del testo (es. in layout: "edgeToEdge"), assicurarsi che resti chiaramente selezionabile senza interrompere la leggibilità del paragrafo.  
   • Stato di Caricamento (Loading): Quando l'azione è in corso (aria-busy="true" / accessibilityState={{ busy: true, disabled: true }}), lo screen reader deve annunciare lo stato di attesa e inibire attivazioni multiple.  
   **5.2 Annunci Dinamici e Contenuti**  
   • Etichette Esplicite: Il valore di actionLabel deve essere chiaro e autoesplicativo anche se letto fuori contesto dagli screen reader (o arricchito programmaticamente tramite accessibilityLabel in caso di etichette brevi come "Scopri di più").

# **6\. Content**

# **🚧 Banner**

Specifica tecnica e di design Machine-Readable per il componente Banner del Design System IO.

```
---
id: component-banner
name: Banner
category: Messaging & Promos
version: 1.0.0
tags: [banner, messaging, promo, communication]
last_updated: 2026-10-14
---
```

# **Intento (Il Razionale)**

Il componente Banner viene utilizzato per comunicare informazioni rilevanti, novità di prodotto, aggiornamenti promozionali o comunicazioni istituzionali di rilievo. Ha lo scopo di offrire alta visibilità a messaggi importanti integrandosi armoniosamente nella pagina o sezione. Presenta uno stile visivo distinto con supporto a diverse tonalità di colore e opzioni di interazione come pulsanti d'azione dedicati e pulsante di chiusura esplicito.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Variante Neutral:** Comunicazioni generali, avvisi informativi o aggiornamenti di servizio privi di carattere promozionale marcato.  
* **Variante Turquoise:** Messaggi in evidenza, nuove funzionalità, iniziative promozionali o comunicazioni speciali che richiedono un impatto visivo maggiore.

## **Don't (Quando NON usare)**

* Non usare per feedback immediati a seguito di un'azione utente (utilizzare Toast o Alert).  
* Non usare per segnalare errori bloccanti di sistema o validazione di form (utilizzare Alert).  
* Non abusare della variante Turquoise nella stessa schermata per evitare di saturare l'attenzione visiva dell'utente.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

| Proprietà | Default | Descrizione |
| :---- | :---- | :---- |
| **`color`** | `neutral` | Tema cromatico e stile visivo del componente. Valori: `neutral` (sfondo neutro) o `turquoise` (sfondo turchese in evidenza). |
| **`title`** | `undefined` | Titolo principale del Banner, utilizzato per catturare l'attenzione dell'utente. |
| **`content`** | `undefined` | Testo descrittivo del messaggio che fornisce i dettagli dell'avviso o della promozione. |
| **`action`** | `undefined` | Oggetto o configurazione della Call to Action principale inserita all'interno del Banner. |

| `closeButton` | `true` | Mostra o nasconde l'icona di chiusura (X) in alto a destra per permettere all'utente di ignorare il messaggio. |
| :---- | :---- | :---- |

# **4\. Stati e Comportamenti**

## **4.1 Comportamento di Chiusura**

Se closeButton: true, la selezione della X rimuove il Banner dal DOM corrente. Lo stato di rimozione può essere memorizzato per evitare di riproporre il messaggio nelle sessioni successive.

## **4.2 Spacing e Margini**

Il componente mantiene un distacco verticale costante di 24px dagli elementi circostanti nel layout della pagina.

# **5\. Accessibilità (A11y)** 

**5.1 Semantica, Screen Reader e Ordine di Lettura**

• Ordine di Focus (Reading Order): Il blocco testuale viene letto prima del pulsante di chiusura. Gli screen reader DEVONO seguire rigorosamente questa sequenza:

1. Blocco Contenuto (Titolo \[se Title \= True\] \+ Description \[se Description \= True\] \+ eventuale CTA \[se CTA \= True\]) — letti in ordine dall'alto verso il basso. Nota: se l'intero Banner è cliccabile come singolo blocco, esporre l'intero contenitore con ruolo Button/Link e un'unica accessibilityLabel combinata; se contiene una CTA interna distinta (es. "Scopri di più" o "Aggiungi documento"), mantenerla come nodo interattivo separato.  
2. Pulsante di Chiusura (solo se Close \= True) — Posizionato per ultimo nell'ordine di lettura. Deve avere ruolo Button, accessibilityLabel esplicita (es. "Chiudi banner" o "Chiudi avviso") e un'area di tocco minima di 44x44pt (iOS) / 48x48dp (Android), anche se l'icona X visiva è più piccola.  
   • Stato di Caricamento (Skeleton \= Yes): Quando il componente è nello stato Skeleton \= Yes, DEVE essere nascosto allo screen reader (oppure annunciato come "Caricamento contenuto in corso" tramite accessibilityState={{ busy: true }}) per evitare la lettura di elementi vuoti.  
   • Esposizione Stato IT-Wallet: Nelle varianti IT-Wallet \| Status, le icone di stato accanto al titolo (spunta verde, triangolo giallo, punto esclamativo rosso) non devono essere lette come caratteri isolati, ma tradotte semanticamente nel messaggio (es. "Documento verificato", "Azione richiesta", "Documento non valido").  
   **5.2 Contenuti e Localizzazione**  
   • CTA Auto-esplicative: Evitare etichette generiche isolate come "Scopri di più" o "Inizia" prive di contesto per lo screen reader: associare sempre un'accessibilityLabel descrittiva (es. "Scopri di più sulla donazione" o "Inizia la conferma dell'identità"). 

# **6\. Content**

# **Accordion**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare.

```
---
id: component-accordion
name: Accordion
category: Data Display & Structure
version: 1.0.0
tags: [accordion, collapsible, disclosure, container]
last_updated: 2026-10-08
---
```

# **Descrizione** 

Il componente Accordion consente di organizzare e strutturare contenuti complessi o secondari in sezioni ripiegabili e progressivamente visibili. Viene impiegato per ridurre l’ingombro verticale della pagina, facilitando la scansione rapida delle informazioni da parte dell'utente. Ciascun elemento si compone di un’intestazione interattiva (header) contenente un titolo descrittivo, un indicatore visivo di stato (chevron) e un pannello di contenuto espandibile all’interno del DOM (Document Object Model).

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Organizzazione dei contenuti:** Raggruppare informazioni correlate o risposte a domande frequenti (FAQ) per ottimizzare la leggibilità.  
* **Tipologia Default:** Utilizzare l’elemento `Accordion` per mostrare sezioni di testo standard e dettagli espandibili.  
* **Tipologia Credentials:** Utilizzare l'elemento `ClaimsSelector.tsx` per la gestione di credenziali o attributi utente.  
* **Gerarchia chiara:** Garantire che i titoli delle intestazioni siano sintetici, espliciti e chiaramente distinguibili rispetto al contenuto del pannello.

## **Don't (Quando NON usare)**

* Non nascondere informazioni critiche o azioni primarie necessarie al completamento immediato del flusso all'interno di un pannello collassato.  
* Non annidare un componente Accordion all'interno di un altro Accordion per evitare un sovraccarico cognitivo e complessità nel DOM (Document Object Model).  
* Non utilizzare `Accordion` standard per le credenziali quando la tipologia è credential.  
* Non rimuovere l'icona o l'indicatore di espansione per preservare l'affordance di interattività dell'intestazione.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`title`**: Testo dell'intestazione dell'accordion. Definisce l'etichetta visibile nell'header. Default: `"Titolo"`.  
* **`expanded`**: Stato di apertura del pannello. Se `true`, mostra il contenuto e ruota l'icona chevron. Default: `false`.  
* **`tipologia`**: Determina il componente React sottostante. Valori: `default` (usa `Accordion`) o `credentials` (usa `ClaimsSelector.tsx`). Default: `"default"`.  
* **`disabled`**: Disabilita l'interazione con l'header e ne modifica la resa opaca. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stati dell'Header**

L'intestazione (header) del componente gestisce i seguenti stati visivi e di interazione:

* **Default:** In configurazione collassata.  
* **Hover/Focus:** Con evidenziazione visiva di sfondo o bordo e focus-ring accessibile.  
* **Expanded:** Con pannello visibile e rotazione dello chevron pari a 180°.  
* **Disabled:** Con disabilitazione dell'interazione a livello di nodo nel DOM (Document Object Model).

## **4.2 Comportamento del testo (Text Truncation & Wrapping)**

Regole per la gestione del testo:

* **Truncation:** Il testo non deve mai essere troncato con i puntini di sospensione per evitare la perdita di informazioni critiche.  
* **Wrapping:** Quando supera la larghezza disponibile, va a capo automaticamente su più righe mantenendo un'interlinea adeguata.

## **4.3 Variante ClaimSelector**

* **`variante ClaimSelector`**: Variante specifica per la gestione di credenziali o attributi utente tramite liste interne. È direttamente associata al componente `ClaimsSelector.tsx`. A livello di governance, richiede l'uso obbligatorio di `ListItems` dedicati per la selezione degli attributi, garantendo la coerenza visiva e strutturale nel DOM (Document Object Model).

# **5\. Accessibilità (A11y)**

**5.1 Semantica, Screen Reader e Ordine di Lettura**

* Intestazione (Header) e Stato di Espansione (Status): L'intera testata cliccabile deve essere esposta come un unico nodo interattivo con ruolo Button e stato di espansione dinamico (accessibilityState={{ expanded: true/false }}), in modo che lo screen reader annunci sia il titolo sia lo stato corrente ("Espanso" per Status: Open / "Compresso" per Status: Closed).  
* Icone Decorative e Chevron: L'icona opzionale a sinistra (Has Icon: Yes) e la freccia di stato a destra (chevron) DEVONO essere nascoste alle tecnologie assistive (accessibilityElementsHidden={true} / importantForAccessibility="no"), poiché il loro significato è già veicolato dal titolo e dallo stato expanded.

  Ordine di Focus (Reading Order):  
1. Quando Status: Closed: Gli screen reader leggono esclusivamente l'intestazione (Titolo \+ stato compresso) e ignorano completamente il contenuto nascosto.  
2. Quando Status: Open: Gli screen reader seguono rigorosamente l'ordine dall'alto verso il basso:  
   a. Intestazione (Titolo \+ stato espanso, ruolo Button).  
   b. Contenuto interno: nella variante Default, il testo del messaggio (ruolo Text) seguito dall'eventuale link (Link: Yes, ruolo Link); nella variante Credential, le coppie etichetta-valore (es. "Nome: Anna") e gli eventuali pulsanti informativi "i" con accessibilityLabel esplicita (es. "Dettagli su Tipologia").  
   • Stato di Caricamento (Skeleton: Yes): Quando Skeleton: il componente non deve essere interattivo (disabled) e deve essere nascosto allo screen reader (oppure annunciato come "Caricamento in corso" tramite accessibilityState={{ busy: true }}).

**5.2 Contenuti e Localizzazione**  
• Titoli Chiari e Sintetici: Il Title dell'Accordion deve anticipare con precisione il contenuto nascosto, permettendo all'utente di decidere se espanderlo senza doverlo aprire.  
• Etichette Link Esplicite (Link: Yes): Evitare link generici come "Scopri di più" privi di contesto: associare sempre un'accessibilityLabel descrittiva legata al titolo dell'Accordion (es. "Scopri di più sulla gestione delle comunicazioni"). 

# **6\. Content**

# **Feature Info**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare.

```
---
id: component-feature-info
name: Feature Info
category: Data Display & Structure
version: 1.0.0
tags: [feature-info, note, callout, info, layout]
last_updated: 2026-11-03
---
```

# **Descrizione** 

Il componente Feature Info viene utilizzato quando serve un’informazione di approfondimento, come una nota in pagina senza associare un significato di feedback. Permette di mettere in evidenza contenuti rilevanti o contestuali all'interno del layout, migliorando la strutturazione visiva dell'interfaccia nel DOM (Document Object Model) senza interferire con i messaggi di stato o di sistema.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Informazioni di approfondimento:** Utilizzare per mostrare note o dettagli esplicativi in pagina quando non si intende comunicare un feedback di sistema (es. errore, successo, avviso).  
* **Consistenza della variante StartElement:** Quando si posizionano più elementi Feature Info in sequenza, assicurarsi che utilizzino la medesima variante StartElement.  
* **Chiarezza del testo:** Mantenere il testo del blocco essenziale e ben strutturato per una rapida scansione visiva all'interno dell'interfaccia.

## **Don't (Quando NON usare)**

* Non utilizzare Feature Info per trasmettere messaggi di stato, avvisi critici o feedback immediati all'utente.  
* Non alternare varianti diverse di StartElement (es. Icon affiancato o seguito da Pictogram) in una sequenza continua di elementi Feature Info nello stesso contenitore del DOM (Document Object Model).  
* Non inserire blocchi di testo eccessivamente lunghi o complessi che possano compromettere la leggibilità globale della pagina.

# **3\. Proprietà (Figma / Code Connect Props)**

Le seguenti proprietà controllano la resa del componente Feature Info in Figma e nel codice:

* **`text`**: Contenuto testuale principale dell'approfondimento. Default: `"Descrizione dell'approfondimento"`.  
* **`startElement`**: Definisce l'elemento visivo iniziale della nota. Valori ammessi: `Icon`, `Pictogram`, `None`. Default: `"Icon"`.  
* **`actionText`**: Etichetta per l'azione secondaria facoltativa (es. link di approfondimento). Default: `"Scopri di più"`.  
* **`showAction`**: Booleano che abilita la visibilità del link o pulsante di azione. Default: `true`.

# **4\. Stati e varianti**

## **4.1 Varianti StartElement**

Il componente può configurare l'elemento iniziale (StartElement) secondo tre modalità:

* **StartElement \= Icon:** Mostra un'icona descrittiva affiancata al testo.  
* **StartElement \= Pictogram:** Mostra un pittogramma illustrativo d'impatto visivo.  
* **StartElement \= None:** Visualizza esclusivamente il contenuto testuale e l'eventuale azione.

## **4.2 Regola per elementi multipli**

Quando più elementi Feature Info vengono posizionati di seguito all'interno della stessa sezione del DOM (Document Object Model), è obbligatorio applicare uniformemente la medesima variante di StartElement. Ad esempio, un elemento con StartElement=Icon non deve mai essere seguito da un elemento con StartElement=Pictogram.

# **5\. Accessibilità (A11y)**

5.1 Semantica, Screen Reader e Ordine di Lettura

* Gestione Elemento Laterale Sinistro: Il comportamento dello screen reader cambia in base alla variante attiva:  
  * Varianti Icon (Icon: True) e Pictogram (Pictogram: True): L'icona o il pittogramma a sinistra ha funzione puramente decorativa/di supporto visivo e DEVE essere nascosto alle tecnologie assistive (accessibilityElementsHidden={true} su iOS / importantForAccessibility="no" su Android). Non deve ricevere il focus.  
  * Variante Number list (Numberlist: True): Il numero progressivo a sinistra (es. "1.", "2.") HA valore informativo/strutturale e DEVE essere letto dallo screen reader all'interno di un contesto di elenco (List / ruolo lista).  
* Ordine di Focus (Reading Order): Gli screen reader DEVONO attraversare gli elementi in ordine strettamente sequenziale:  
* Numero dell'elenco (solo se Numberlist: True) — Annunciato per primo (es. "1.") per indicare la posizione nella sequenza.  
* Corpo del testo informativo — Ruolo: testo (Text).  
* Call to Action (solo se CTA? \= True) — Ruolo interattivo distinto (Button o Link).

5.2 Contenuti e Localizzazione

* Nessuna Dipendenza da Feedback Semantici: Poiché il Feature info fornisce approfondimenti neutri senza connotazione di stato (a differenza dell'Alert), non aggiungere prefissi di gravità ("Avviso:", "Errore:").  
* Etichette CTA Auto-esplicative (CTA? \= True): Evitare che lo screen reader legga formule generiche isolate come "Scopri di più". Associare sempre un'accessibilityLabel contestuale legata al servizio o all'argomento descritto nel testo (es. "Scopri di più su \[Nome servizio\]", come indicato nelle specifiche di lettura). 

# **6\. Content**

# **List Item Info**

Specifica tecnica e di design Machine-Readable per il componente List Item Info del Design System IO.

```
---
id: component-list-item-info
name: List Item Info
category: Information
version: 1.0.0
tags: [list-item, info, ui]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente List Item Info viene utilizzato per presentare dati e informazioni di sola lettura o con piccole azioni contestuali, basandosi sulla coppia Label/Value, badge opzionali e pulsanti d'azione rapidi come "Modifica".

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Struttura Label/Value e Azioni:** Utilizzare la variante informativa per mostrare informazioni chiare tramite coppia Label/Value, affiancate eventualmente da badge di stato/numerici o da pulsanti d'azione rapida come "Modifica".  
* **Separatori e Padding:** Inserire i divider esclusivamente dal 2° al penultimo elemento della lista ed utilizzare l'icona Chevron List Item a destra per bilanciare la spaziatura interna (padding).

## **Don't (Quando NON usare)**

* Non utilizzare il componente per scenari di navigazione o selezioni complesse.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`label`:** Stringa. Etichetta o titolo del dato informativo descritto nell'elemento. Default: `undefined`.  
* **`value`:** Stringa / ReactNode. Valore associato alla label per comporre la coppia informativa Label/Value. Default: `undefined`.  
* **`badge`:** ReactNode. Badge opzionale per mostrare stato o conteggi numerici affiancati all'informazione. Default: `undefined`.  
* **`actionButton`:** ReactNode. Pulsante d'azione rapida opzionale (es. "Modifica"). Default: `undefined`.  
* **`state`:** Enum ("Default"). Stato visivo dell'elemento. Valore supportato: Default. Default: `Default`.  
* **`showDivider`:** Booleano. Determina la presenza del separatore dal 2° elemento al penultimo del gruppo. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stato Default**

Rappresenta la modalità visiva standard a riposo del componente. Viene utilizzata per la consultazione della coppia essenziale Label/Value e per consentire l'accesso immediato alle eventuali azioni rapide correlate (es. "Modifica").

## **4.2 Varianti con Badge e CTA**

Configurazioni avanzate che arricchiscono la struttura informativa base con elementi contestuali o d'azione:

* **Variante con Badge:** Integra badge numerici o di stato affiancati alla coppia Label/Value per evidenziare contatori, notifiche o condizioni operative.  
* **Variante con CTA:** Dispone di un pulsante d'azione rapida (es. "Modifica") per consentire l'aggiornamento contestuale o l'interazione diretta con il dato visualizzato.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM:** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Transactional**

Specifica tecnica e di design Machine-Readable per il componente List Item Transactional del Design System IO.

```
---
id: component-list-item-transactional
name: List Item Transactional
category: Transactional
version: 1.0.0
tags: [list-item, transaction, ui, payment]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente List Item Transactional viene utilizzato per rappresentare visivamente transazioni finanziarie e movimenti di pagamento. È ottimizzato per mostrare in modo immediato l'esito della transazione, l'importo economico, le etichette descrittive e gli indicatori di stato (es. FALLITA), sfruttando una griglia a 16 colonne per massimizzare l'efficienza dello spazio orizzontale.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Rappresentazione di Transazioni:** Utilizzare per mostrare dati relativi a pagamenti, storici transazioni e movimenti finanziari con indicazione chiara dell'importo e dell'esito.  
* **Separatori e Padding:** Inserire i divider esclusivamente dal 2° al penultimo elemento della lista ed utilizzare l'icona Chevron List Item a destra per bilanciare la spaziatura interna (padding).

## **Don't (Quando NON usare)**

* Non utilizzare per elementi di lista puramente informativi o di semplice configurazione/impostazione privi di rilevanza transazionale o finanziaria.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`label`:** Stringa. Titolo o ente associato alla transazione. Default: `undefined`.  
* **`description`:** Stringa. Descrizione o dettaglio aggiuntivo del movimento. Default: `undefined`.  
* **`amount`:** Stringa. Importo valuta associato alla transazione (es. "00,00 €"). Default: `undefined`.  
* **`statusBadge`:** ReactNode / Stringa. Badge di stato per evidenziare l'esito della transazione (es. "FALLITA"). Default: `undefined`.  
* **`showChevron`:** Booleano. Determina la presenza dell'icona di navigazione a freccia (\>). Default: `false`.  
* **`gridColumns`:** Numero (16). Impostazione del layout a 16 colonne per l'ottimizzazione degli spazi orizzontali. Default: `16`.

# **4\. Stati e varianti**

## **4.1 Stato Default**

Visualizzazione standard del movimento transazionale con Label, Description e l'importo della transazione. Può includere la freccia di navigazione per accedere ai dettagli.

## **4.2 Varianti con Stato ed Errore**

Varianti che mostrano chiaramente l'esito del pagamento o stato speciale:

* **Variante Transazione Fallita:** Include l'etichetta/badge esplicito "FALLITA" affiancato alla descrizione per segnalare un errore nel flusso di pagamento.  
* **Variante Navigabile:** Integra il simbolo di avanzamento chevron (\>) sul margine destro per indicare che la riga è interattiva e porta al dettaglio della transazione.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM:** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Navigazione**

Specifica tecnica e di design Machine-Readable per il componente List Item Navigazione del Design System IO.

```
---
id: component-list-item-navigation
name: List Item Navigazione
category: Navigation
version: 1.0.0
tags: [list-item, navigation, ui, chevron]
last_updated: 2026-11-10
---
```

**1\. Descrizione**  
Il componente List Item Navigazione viene utilizzato per guidare l'utente verso sezioni di dettaglio o flussi specifici all'interno dell'applicazione. Integra un'icona Chevron List Item sul margine destro per bilanciare visivamente il padding e segnalare l'interattività dell'elemento. Gli elementi disabilitati non sono mai visibili nella lista, mentre i divisori (divider) separano gli elementi a partire dal secondo fino al penultimo per garantire l'ordine visivo dell'elenco.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Navigazione e Flussi:** Utilizzare per consentire l'accesso a dettagli, sotto-pagine o configurazioni interattive.  
* **Separatori e Padding:** Inserire i divider esclusivamente dal 2° al penultimo elemento della lista ed utilizzare l'icona Chevron List Item a destra per bilanciare la spaziatura interna (padding).

## **Don't (Quando NON usare)**

* Non mostrare mai i list item disabilitati nella lista (gli elementi non disponibili o disattivati devono essere completamente nascosti dall'elenco).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`label`:** Stringa. Titolo o voce principale di navigazione. Default: `undefined`.  
* **`description`:** Stringa. Testo di supporto o sottotitolo opzionale. Default: `undefined`.  
* **`leftElement`:** ReactNode. Elemento visivo opzionale a sinistra (Icona, Avatar o Data). Default: `undefined`.  
* **`topElement`:** ReactNode. Elemento opzionale posizionato in alto (Badge "NOVITÀ" o Data). Default: `undefined`.  
* **`showChevron`:** Booleano. Icona Chevron List Item posizionata a destra per bilanciare il padding e indicare l'azione di avanzamento. Default: `true`.  
* **`showDivider`:** Booleano. Determina la presenza della linea di separazione (applicata dal 2° al penultimo elemento). Default: `true`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Stato visivo primario attivo del list item navigabile. Presenta l'etichetta principale, l'eventuale descrizione e l'icona Chevron List Item a destra per bilanciare il padding di riga.

## **4.2 Varianti con Left Element e Top Element**

Le varianti di navigazione supportano diversi arricchimenti visivi:

* **Variante con Icona o Avatar:** Integra un elemento grafico a sinistra (Icon / Avatar) per caratterizzare visivamente la destinazione.  
* **Variante con Badge o Data:** Include un elemento superiore (Badge "NOVITÀ" o indicazione della data) sopra il titolo.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM:** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Link**

Specifica tecnica e di design Machine-Readable per il componente List Item Link del Design System IO.

```
---
id: component-list-item-link
name: List Item Link
category: Navigation
version: 1.0.0
tags: [list-item, navigation, link, ui, external-link]
last_updated: 2026-11-10
---
```

**1\. Descrizione**  
Il componente List Item Link viene utilizzato per indirizzare l'utente verso risorse esterne, documenti legali o servizi terzi all'interno dell'applicazione. A differenza del List Item Navigazione, integra un'icona di invio/link esterno o icone contestuali specifiche sul margine per indicare chiaramente che l'azione porterà a una destinazione esterna o a un collegamento diretto. I divisori separano le varie voci della lista per garantire la leggibilità e l'ordine visivo dell'elenco.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Collegamenti Esterni e Risorse:** Utilizzare per reindirizzare a pagine web esterne, documenti ufficiali (es. Informativa sulla Privacy) o azioni dirette di supporto e uscita.  
* **Iconografia Contestuale:** Associare l'icona adeguata all'azione (es. spunta/documento per Privacy, freccia/uscita per Esci da IO, cestino per Elimina) per chiarire immediatamente il tipo di risorsa.

## **Don't (Quando NON usare)**

* Non utilizzare per la navigazione interna gerarchica a sotto-pagine dell'app (in quel caso utilizzare List Item Navigazione con Chevron).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`label`:** Stringa. Titolo o testo del collegamento (es. "Informativa sulla Privacy", "Richiedi assistenza", "Esci da IO", "Elimina"). Default: `undefined`.  
* **`description`:** Stringa. Testo esplicativo o sottotitolo opzionale di supporto al link. Default: `undefined`.  
* **`leftIcon`:** ReactNode. Icona opzionale a sinistra dell'etichetta (es. segno di spunta, freccia di uscita, cestino). Default: `undefined`.  
* **`isExternal`:** Booleano. Se impostato su true, mostra l'icona di collegamento esterno sul margine destro. Default: `true`.  
* **`destructive`:** Booleano. Definisce se l'azione collegata è distruttiva (es. "Elimina"), applicando la variazione cromatica d'allerta. Default: `false`.  
* **`showDivider`:** Booleano. Determina la presenza della linea di separazione (applicata dal 2° al penultimo elemento). Default: `true`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Stato visivo primario del link. Presenta l'etichetta e l'eventuale icona identificativa (es. Informativa sulla Privacy, Richiedi assistenza).

## **4.2 Varianti di Azione Diretto / Distruttiva**

Il componente prevede varianti per diverse categorie di azione:

* **Variante Standard / Informativa:** Per link a documenti o pagine informative (es. "Informativa sulla Privacy", "Richiedi assistenza").  
* **Variante Uscita / Logout:** Include l'icona di direzione/uscita (es. "Esci da IO") per indicare la disconnessione o chiusura sessione.  
* **Variante Distruttiva:** Utilizzata per azioni irreversibili o di rimozione (es. "Elimina").

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM:** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Message**

Specifica tecnica e di design Machine-Readable per il componente List Item Message del Design System IO.

```
---
id: component-list-item-message
name: List Item Message
category: Messages
version: 1.0.0
tags: [list-item, message, communication, ui, io-app]
last_updated: 2026-11-10
---
```

**1\. Descrizione**  
Il componente List Item Message viene utilizzato per visualizzare i messaggi e le comunicazioni ricevute all'interno dell'applicazione IO. Rappresenta una riga elenco strutturata che mostra l'avatar o logo dell'ente mittente (con eventuale supporto a Double Avatar), il nome dell'organizzazione, il nome del servizio e il titolo/anteprima del messaggio, oltre all'orario/data di invio. È progettato per garantire un layout coerente sia nelle visualizzazioni standard (Default, Selected, Pressed, Skeleton) sia nei risultati di ricerca (Search result).

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Elenchi di Messaggi e Notifiche:** Utilizzare per elencare le comunicazioni in arrivo nella sezione Messaggi dell'app IO.  
* **Struttura del Testo e Troncamento:** Il nome dell'organizzazione (Organization name) deve occupare al massimo 1 riga con troncamento tramite punti di sospensione (...). La combinazione di Service name e Title/Anteprima deve occupare al massimo 2 righe complessive, anch'essa troncata con ....  
* **Gestione Avatar e Fallback:** Gestire l'avatar principale dell'ente (o la combinazione Double Avatar); in caso di assenza dell'immagine personalizzata dell'ente/servizio, eseguire il fallback automatico sul logo predefinito dell'organizzazione.  
* **Layout, Dynamic Type e Griglia:** Utilizzare la griglia a 16 colonne per la disposizione degli elementi. Supportare il Dynamic Type garantendo un incremento massimo della dimensione del testo pari a x1.5 per preservare la struttura visiva.  
* **Evidenziatura Risultati di Ricerca (Search result):** Nei risultati di ricerca, applicare la logica di evidenziatura con colore turchese solo ed esclusivamente se il termine cercato è presente nel testo di preview/anteprima.

## **Don't (Quando NON usare)**

* Non utilizzare per la navigazione generica a schede o impostazioni di profilo (per cui va usato List Item Navigazione o List Item Link).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`organizationName`:** Stringa. Nome dell'ente/organizzazione (es. "Nome Ente"). Max 1 riga con troncamento (...). Default: `undefined`.  
* **`serviceName`:** Stringa. Nome del servizio specifico associato al messaggio. Parte integrante delle max 2 righe di anteprima. Default: `undefined`.  
* **`titlePreview`:** Stringa. Titolo o testo di anteprima del messaggio. Max 2 righe complessive (in combinazione con serviceName) con troncamento (...). Default: `undefined`.  
* **`timestamp`:** Stringa. Orario o data di invio (es. "09:15"). Default: `undefined`.  
* **`avatarVariant`:** Enum ("single" \| "double"). Definisce la modalità avatar (singolo o Double Avatar). In assenza di asset custom, si applica il fallback al logo organizzazione. Default: `"single"`.  
* **`state`:** Enum ("default" \| "selected" \| "pressed" \| "skeleton" \| "search-result"). Stato visivo ed interattivo dell'elemento. Default: `"default"`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Rappresenta le variazioni di stato dell'interfaccia del messaggio:

* **Default:** Stato di base del messaggio letto o da leggere.  
* **Selected & Pressed:** Stati di selezione visiva o pressione/interazione attiva sulla riga.

**Skeleton:** Stato di caricamento visivo (placeholder) durante il recupero dei dati.

## **4.2 Varianti di Azione Diretto / Distruttiva**

Le varianti del componente si articolano principalmente in base agli avatar e alla ricerca:

* **Variante Avatar Singolo / Double Avatar:** Mostra l'avatar o i loghi sovrapposti dell'ente e del servizio. Se l'immagine specifica non è disponibile, viene utilizzato il logo dell'organizzazione come fallback.  
* **Variante Search Result:** Visualizzazione ottimizzata per la ricerca. Evidenzia con colore turchese le parole chiave inserite dall'utente, a condizione che tali parole compaiano all'interno della preview del messaggio.  
* **Layout Grid & Scaling:** Tutte le varianti adottano la griglia a 16 colonne e supportano il riscalamento del testo via Dynamic Type con un limite massimo pari a x1.5.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM:** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Header**

Specifica tecnica e di design Machine-Readable per il componente List Item Header del Design System IO.

```
---
id: component-list-item-header
name: List Item Header
category: Headers
version: 1.0.0
tags: [list-item, header, section, title, ui, io-app]
last_updated: 2026-11-10
---
```

**1\. Descrizione**  
Il componente List Item Header viene utilizzato per intestare e separare logicamente sezioni o gruppi di elementi all'interno di elenchi nell'applicazione IO. Consente di strutturare la gerarchia visiva mediante etichette di testo (Label text), badge informativi di stato/notifica, elementi di azione rapida (Action) e icone informative secondarie ("i"). È progettato per garantire un'organizzazione chiara dei contenuti e una distinzione immediata delle differenti categorie visive.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Separazione di Sezioni in Elenchi:** Utilizzare per raggruppare e contestualizzare visivamente elementi correlati all'interno di liste complesse o pagine di impostazioni nell'app IO.  
* **Integrazione di Badge e Azioni:** Inserire badge per evidenziare lo stato della sezione (es. novità o conteggi) e azioni (Action) per offrire comandi rapidi contestuali alla sezione.  
* **Chiarezza del Testo dell'Etichetta:** Utilizzare etichette sintetiche e descrittive (Label text) che definiscano chiaramente il contenuto del gruppo sottostante.  
* **Uso dell'Icona Informativa:** Affiancare l'icona "i" al testo dell'intestazione esclusivamente quando è necessario fornire un aiuto o dettagli contestuali aggiuntivi sulla sezione.  
* **Allineamento e Layout:** Mantenere un layout coerente con i margini e le guide del Design System per garantire l'allineamento visivo con i List Item sottostanti.

## **Don't (Quando NON usare)**

* Non utilizzare come singolo elemento di lista interattivo principale o naviga-riga; per la navigazione a singola riga usare i componenti List Item dedicati.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`labelText`:** Stringa. Testo principale dell'intestazione (Label text). Default: `"Label text"`.  
* **`showBadge`:** Booleano. Controlla la visibilità del badge informativo (BADGE) affiancato all'etichetta. Default: `false`.  
* **`badgeText`:** Stringa. Testo visualizzato all'interno del badge. Default: `"BADGE"`.  
* **`showAction`:** Booleano. Determina la presenza del comando d'azione rapida (Action) a destra. Default: `false`.  
* **`actionLabel`:** Stringa. Etichetta del pulsante/comando d'azione (Action). Default: `"Action"`.  
* **`showInfoIcon`:** Booleano. Controlla la visualizzazione dell'icona informativa ("i") affiancata. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Definisce le configurazioni di stato visivo del componente List Item Header:

* **Standard Label:** Visualizzazione di base con solo il testo dell'etichetta (Label text).  
* **Header con Badge / Action / Info:** Stato arricchito da badge informativo, elemento d'azione rapida o icona informativa "i".

**Skeleton:** Stato di caricamento visivo (placeholder) durante il recupero dei dati.

## **4.2 Varianti di Azione Diretto / Distruttiva**

Le varianti del componente si articolano in base agli elementi accessori inclusi:

* **Variante Testo \+ Badge:** Integra un badge visivo accanto all'etichetta di testo.  
* **Variante Testo \+ Action:** Include un'azione contestuale (Action) allineata a destra per l'interazione diretta con la sezione.  
* **Variante Testo \+ Info:** Incontra l'icona di supporto ("i") per attivare suggerimenti o tooltip informativi.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM (Document Object Model):** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Radio**

Specifica tecnica e di design Machine-Readable per il componente List Item Radio del Design System IO.

```
---
id: component-list-item-radio
name: List Item Radio
category: List Items
version: 1.0.0
tags: [list-item, radio, selection, single-select, ui, io-app]
last_updated: 2026-11-10
---
```

**1\. Descrizione**  
Il componente List Item Radio consente all'utente di effettuare una selezione singola ed esclusiva all'interno di una lista di opzioni nell'applicazione IO. È composto da un pulsante radio (Radio button), un titolo principale (Title), una descrizione di supporto opzionale (Description) e, nelle varianti avanzate, un importo monetario o valore aggiuntivo allineato (Amount). È ideato per garantire chiarezza nelle scelte mutually exclusive ed esperienza utente uniforme in contesti quali selezioni di pagamento, impostazioni o configurazioni rapide.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Selezione Singola Esclusiva:** Utilizzare all'interno di gruppi di opzioni in cui l'utente può selezionare un solo elemento alla volta (mutually exclusive).  
* **Uso dei Separatori (Divider):** Nei gruppi di List Item Radio, applicare i divider separatori a partire dal 2° elemento fino al penultimo elemento del gruppo, lasciando il primo e l'ultimo elemento privi di separatori estesi esterni.  
* **Chiarezza del Testo:** Definire titoli chiari e sinteti accompagnati da descrizioni esplicative per facilitare la scelta rapida ed informata.  
* **Integrazione di Importi (Amount):** Utilizzare la variante con Amount per mostrare in modo evidenziato valori economici, tariffe o commissioni associate alla singola scelta.  
* **Area di Interazione (Touch Target):** Garantire che l'intera superficie del List Item Radio sia cliccabile/focalizzabile per facilitare la selezione da dispositivi mobili.

## **Don't (Quando NON usare)**

* Non utilizzare per selezioni multiple (in tal caso utilizzare List Item Checkbox) o per azioni immediate di navigazione/comando senza stato di selezione memorizzato.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`titleText`:** Stringa. Titolo principale dell'opzione (es. "Usa configurazione rapida"). Default: `"Title"`.  
* **`showDescription`:** Booleano. Controlla la visibilità del testo descrittivo secondario sottostante il titolo. Default: `true`.  
* **`descriptionText`:** Stringa. Testo descrittivo di approfondimento dell'opzione. Default: `"Description text"`.  
* **`selected`:** Booleano. Definisce lo stato di selezione del radio button (Selected / Unselected). Default: `false`.  
* **`showAmount`:** Booleano. Determina la presenza dell'importo o valore monetario (es. "2,50 €"). Default: `false`.  
* **`amountText`:** Stringa. Valore testuale o monetario da visualizzare. Default: `"0,00 €"`.  
* **`showDivider`:** Booleano. Gestisce la presenza del separatore inferiore (applicato dal 2° al penultimo elemento del gruppo). Default: `true`.  
* **`disabled`:** Booleano. Disabilita l'interazione e modifica lo stato visivo. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Definisce le configurazioni di stato visivo del componente List Item Header:

* **Selected / Unselected:** Stato selezionato (radio attivato) o non selezionato (radio vuoto).  
* **Default / Pressed / Focused:** Stati di interazione visiva durante la navigazione o la pressione dell'elemento.  
* **Disabled:** Stato disabilitato non interattivo.

**Skeleton:** Stato di caricamento visivo (placeholder) durante il recupero dei dati.

## **4.2 Varianti di Azione**

Le varianti del componente si articolano in base agli elementi accessori inclusi:

* **Standard Radio (Title \+ Description):** Variante di base composta da titolo e descrizione esplicativa.  
* **Radio con Amount (Title \+ Description \+ Amount):** Variante arricchita con valore/importo affiancato.  
* **Simple Radio (Title unicamente):** Variante essenziale senza descrizione secondaria né importo.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM (Document Object Model (Modello a Oggetti del Documento)):** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Checkbox**

Specifica tecnica e di design Machine-Readable per il componente List Item Checkbox del Design System IO.

```
---
id: component-list-item-checkbox
name: List Item Checkbox
category: List Items
version: 1.0.0
tags: [list-item, checkbox, selection, multi-select, ui, io-app]
last_updated: 2026-11-10
---
```

**1\. Descrizione**  
Il componente List Item Checkbox consente all'utente di selezionare una o più opzioni indipendenti all'interno di una lista nell'applicazione IO. È composto da una casella di spunta (Checkbox), un titolo principale (Title), una descrizione di supporto opzionale (Description) ed eventualmente da un indicatore o valore aggiuntivo. È ideato per gestire selezioni multiple, configurazioni di preferenze e attivazioni/disattivazioni di servizi (es. notifiche e comunicazioni) mantenendo un layout chiaro, coerente e accessibile.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Selezione Multipla Indipendente:** Utilizzare all'interno di un checkbox group per permettere all'utente di selezionare zero, una o più opzioni non mutually exclusive (es. preferenze di notifica).  
* **Uso dei Separatori (Divider):** Per comporre un gruppo di due o più checkbox group, impiegare i divider utilizzati a partire dal 2° elemento al penultimo.  
* **Chiarezza del Testo:** Accompagnare l'etichetta principale con una descrizione esplicativa per chiarire l'impatto della selezione (es. attivazione comunicazioni dai servizi).  
* **Stato Iniziale Chiaro:** Definire chiaramente lo stato predefinito (Checked / Unchecked) per riflettere le impostazioni correnti dell'utente.  
* **Area di Interazione Ampliata:** Rendere l'intera superficie dell'elemento di lista cliccabile per facilitare il tocco da dispositivi mobili.

## **Don't (Quando NON usare)**

* Non utilizzare per selezioni singole ed esclusive (in tal caso usare List Item Radio) o per azionare comandi di navigazione diretti senza memoria di stato.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`titleText`:** Stringa. Titolo principale dell'opzione (es. "Usa configurazione rapida"). Default: `"Title"`.  
* **`showDescription`:** Booleano. Controlla la visibilità del testo descrittivo secondario sottostante il titolo. Default: `true`.  
* **`descriptionText`:** Stringa. Testo descrittivo di approfondimento dell'opzione. Default: `"Description text"`.  
* **`checked`:** Booleano/Enum. Definisce lo stato della casella di spunta (Checked / Unchecked / Indeterminate). Default: `false`.  
* **`indeterminate`:** Booleano. Gestisce lo stato indeterminato/parziale della selezione nei gruppi nidificati. Default: `false`.  
* **`showDivider`:** Booleano. Gestisce la presenza del separatore inferiore (da applicare dal 2° al penultimo elemento del checkbox group). Default: `true`.  
* **`disabled`:** Booleano. Disabilita l'interazione e modifica lo stato visivo. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Definisce le configurazioni di stato visivo del componente List Item Checkbox:

* **Checked / Unchecked / Indeterminate:** Stato selezionato (spunta attiva), non selezionato (vuoto) o indeterminato (trattino di selezione parziale).  
* **Default / Pressed / Focused:** Stati di interazione visiva durante la navigazione o la pressione dell'elemento.  
* **Disabled:** Stato disabilitato non interattivo.

**Skeleton:** Stato di caricamento visivo (placeholder) durante il recupero dei dati.

## **4.2 Varianti di Azione**

Le varianti del componente si articolano in base agli elementi accessori inclusi:

* **Standard Checkbox (Title \+ Description):** Variante standard composta da titolo e descrizione esplicativa secondaria.  
* **Simple Checkbox (Title unicamente):** Variante essenziale priva di descrizione secondaria.  
* **Checkbox Group:** Composizione di più list item checkbox integrati in sequenza con divider interni.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM (Document Object Model (Modello a Oggetti del Documento)):** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **List Item Switch**

Specifica tecnica e di design Machine-Readable per il componente List Item Switch del Design System IO.

```
---
id: component-list-item-switch
name: List Item Switch
category: List Items
version: 1.0.0
tags: [list-item, switch, toggle, selection, ui, io-app]
last_updated: 2026-11-10
---
```

**1\. Descrizione**  
Il componente List Item Switch consente all'utente di attivare o disattivare immediatamente uno stato binario (On/Off) o una funzionalità all'interno dell'applicazione IO. È composto da un controllo di commutazione (Switch), un titolo principale (Title), una descrizione di supporto opzionale (Description) ed eventualmente da un link o azione secondaria (es. "Scopri di più"). È progettato per gestire impostazioni immediate, preferenze di notifica e abilitazione di opzioni di servizio garantendo un feedback visivo istantaneo e un'elevata accessibilità.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Attivazione Immediata:** Utilizzare per variazioni di stato binario (On/Off) che producono un effetto immediato senza richiedere un salvataggio o una conferma esplicita.  
* **Uso dei Separatori (Divider):** Per comporre un toggle group di due o più elementi, applicare i divider interni dal 2° al penultimo elemento del gruppo.  
* **Chiarezza dell'Impatto:** Accompagnare l'etichetta con un testo descrittivo o una CTA informativa (es. "Scopri di più") per chiarire l'effetto della commutazione.  
* **Stato Iniziale Coerente:** Rappresentare in modo chiaro e trasparente lo stato corrente del sistema (On / Off / Loading).  
* **Area di Interazione Ampliata:** Rendere l'intera superficie dell'elemento di lista cliccabile per facilitare il tocco da dispositivi mobili.

## **Don't (Quando NON usare)**

* Non utilizzare per la scelta tra opzioni esclusive in un modulo (usare List Item Radio) o per conferme differite da un pulsante "Salva".

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`titleText`:** Stringa. Titolo principale dell'opzione (es. "Usa configurazione rapida"). Default: `"Title"`.  
* **`showDescription`:** Booleano. Controlla la visibilità del testo descrittivo secondario. Default: `true`.  
* **`descriptionText`:** Stringa. Testo descrittivo di approfondimento. Default: `"Description text"`.  
* **`checked`:** Booleano. Stato del controllo switch (true \= On / false \= Off). Default: `false`.  
* **`showActionLink`:** Booleano. Controlla la presenza del link o della CTA secondaria (es. "Scopri di più"). Default: `false`.  
* **`showDivider`:** Booleano. Gestisce la presenza del separatore inferiore (da applicare dal 2° al penultimo elemento del checkbox group). Default: `true`.  
* **`disabled`:** Booleano. Disabilita l'interazione e modifica lo stato visivo. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Definisce le configurazioni di stato visivo e di interazione del componente List Item Switch:

* **Checked / Unchecked:** Stato attivo (attiva la funzionalità) o disattivo (disattiva la funzionalità).  
* **Default / Focused / Loading (ATTENDI):** Stati d'interazione; lo stato Loading mostra la dicitura "ATTENDI" o l'indicatore durante il passaggio di stato.  
* **Disabled:** Stato disabilitato non interattivo.

**Validation / Hint Text:** Stato informativo o di errore immediato (es. "\! Seleziona per continuare").

## **4.2 Varianti di Azione**

Le varianti del componente si articolano in base al contesto d'uso e ai controlli integrati:

* **Standard Switch (Title \+ Description):** Composizione standard con etichetta principale e spiegazione dettagliata.  
* **Switch con Action Link:** Variante che include un link di approfondimento secondario ("Scopri di più").  
* **Toggle Group:** Insieme di più componenti List Item Switch in sequenza con divider interni posizionati dal 2° al penultimo elemento.

# **5\. Accessibilità (A11y) 🟠**

### **List Item — Specifiche di Accessibilità**

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * Il gruppo di list item deve essere inserito in un contenitore di lista semantico (role="list" / \<ul\>) e ciascuna riga deve essere esposta come elemento di lista (role="listitem" / \<li\>). Ciò consente allo screen reader di annunciare l'indice e il totale degli elementi (es. *"Elemento 1 di 5"*).

* **Gerarchia interna e Naming**:  
  * **Variante Navigazione (intera riga cliccabile)**: Assegnare il ruolo interattivo unificato di link (\<a\>) o pulsante (\<button\>) all'intero elemento di riga per evitare fermate di focus frammentate.  
  * **Accessible Name unificato**: Il nome accessibile deve aggregare in una sola lettura logica il titolo/valore principale, la descrizione secondaria, l'eventuale data e i badge (es. *"Notifiche push, Consenti anteprime e promemoria"* oppure *"Novità, \[Titolo\], \[Descrizione\]"*).  
  * **Chevron e icone illustrative**: La freccia di navigazione destra (chevron) e le icone a sinistra con scopo puramente visivo devono essere nascoste alle tecnologie assistive (aria-hidden="true" / accessible={false}). Le linee divisorie (divider) tra gli elementi sono elementi grafici di separazione e vanno escluse dal flusso di lettura.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con ellissi (...) devono obbligatoriamente mantenere disponibile per lo screen reader l'intera stringa non troncata tramite l'albero di accessibilità o label completa.

* **Elementi interattivi interni e Controlli annidati**:  
  * **Variante Informativa con CTA**: Nelle righe con azioni secondarie dedicate (pulsante testuale "Modifica", icona "Copia", icona info "i", eliminazione/cestino), la riga di testo rimane statica e solo il comando specifico riceve il focus.  
  * **Divieto di controlli annidati**: È vietato inserire pulsanti o link all'interno di una riga che è a sua volta un link o pulsante (nessun comando interattivo annidato in un altro comando).  
  * **Controlli Icon-only**: I pulsanti composti da sola icona (es. copia, info) devono avere un'etichetta accessibile contestualizzata (es. aria-label="Copia codice fiscale", non un generico "Copia").

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, descrizioni, label di supporto, testi di badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della riga.  
  * Icone funzionali (copia, info, eliminazione, errore, chevron) e bordi grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*).

* **Non dipendenza dal colore**:  
  * **Cosa fare**: Nelle varianti con stato di errore o avviso, associare sempre al testo rosso un'icona semantica dedicata (es. icona esclamativa) e rendere esplicita la criticità tramite testo o label accessibile. Nelle varianti con badge (es. "NOVITÀ"), trasmettere lo stato attraverso testo leggibile e non solo con il colore del badge.  
  *   
  * **Cosa evitare**: Non affidarsi unicamente alla tinta del testo o dello sfondo per comunicare stati di selezione, errore o interattività.  
  * 

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile governato dal token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo):  
  * Nella variante Navigazione circonda l'intera superficie della riga.  
  * Nella variante Informativa con CTA circonda unicamente il singolo elemento interattivo interno ("Modifica", icona copia, icona info).  
* **Touch Target**: Minimo garantito $44\times 44px$. Per la riga navigabile l'area coincide con l'intera riga; per i comandi interni (icone copia, info o pulsanti testuali) è obbligatorio estendere l'area di tocco interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Sposta il focus da un list item interattivo al successivo (o da una CTA interna alla successiva), escludendo i testi statici e le frecce decorative dal percorso di tabulazione.  
  * Invio / Spazio: Attiva l'azione se il target è un componente di tipo pulsante (es. CTA "Modifica" o riga d'azione).  
  * Invio: Esegue la navigazione verso il dettaglio se il target è un link.

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo) — Navigazione** | role="listitem" con elemento interattivo interno  | *"\[Titolo\], \[Descrizione\], \[Badge se presente\], elemento X di Y, pulsante / link"*.  |
| **Elemento statico (già a schermo) — Informativo con CTA** | role="listitem" statico con comando interno focalizzabile  | *"\[Etichetta\], \[Valore\], \[Azione con nome accessibile es. 'Modifica \[Etichetta\]'\], pulsante"*.  |
| **Stato Errore (Navigazione)** | Testo esplicito e indicatore accessibile  | *"\[Titolo\], Errore: \[Descrizione\], elemento X di Y, pulsante / link"*.  |
| **Caricamento / Skeleton** | aria-busy="true" sull'elemento o lista  | Segnala lista o elemento in fase di caricamento ed evita interazioni e letture parziali.  |
| **Disabilitato** | Nascosto dal layout (da regola DS) o aria-disabled="true"  | Elemento non visibile e non esposto; se visibile per eccezione, segnalato come disattivato. |

* **A11y \- DOM (Document Object Model (Modello a Oggetti del Documento)):** Nodo elemento di lista (\<li\> o accessibilityRole="none") incapsulato rigorosamente all'interno di un contenitore elenco semantico (\<ul\> / \<ol\>); se l'intera riga è navigabile, il nodo interattivo primario (\<a\> o \<button\>) costituisce il wrapper del contenuto con nome accessibile unificato, mantenendo nascoste le icone ausiliarie/chevron (aria-hidden="true") ed evitando l'annidamento errato di controlli interattivi all'interno di altri pulsanti.

# **6\. Content**

# **Module Payment Notice**

Specifica tecnica e di design Machine-Readable per il componente Module Payment Notice del Design System IO.

```
---
id: component-module-payment-notice
name: Module Payment Notice
category: Modules
version: 1.0.0
tags: [module, payment-notice, tari, payment, ui, io-app]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente Module Payment Notice visualizza un avviso di pagamento (es. "Tari 2023 \- Rata Unica") all'interno dell'applicazione IO. È composto da un'intestazione con il codice avviso, una descrizione del tributo o servizio, l'importo da saldare (es. "171,00 €"), un indicatore d'azione o chevron (\>) e un badge visivo di stato (Default, PAGATO, ERRORE, SCADUTO, REVOCATO, IN CORSO o Skeleton). È progettato per offrire un riepilogo immediato e chiaro dello stato di ciascun avviso di pagamento dell'utente.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Riepilogo Avviso di Pagamento:** Utilizzare per mostrare la sintesi di un tributo o avviso di pagamento (es. Tari) con relativo importo e stato corrente.  
* **Feedback Visivo di Stato:** Associare sempre un badge di stato testuale ed esplicito (PAGATO, ERRORE, SCADUTO, REVOCATO, IN CORSO) per comunicare la situazione del pagamento.  
* **Chiarezza degli Importi e Codici:** Mostrare chiaramente il codice avviso e l'importo aggiornato da pagare.  
* **Area Cliccabile Intera:** Rendere l'intero modulo un'unica area d'interazione per accedere al dettaglio dell'avviso o completare il pagamento.

## **Don't (Quando NON usare)**

* Non utilizzare per semplici interruttori di stato On/Off (usare List Item Switch) o per opzioni di scelta esclusive in un modulo.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`noticeCode`:** Stringa. Codice identificativo dell'avviso di pagamento.  
* **`titleText`:** Stringa. Titolo dell'avviso o tributo (es. "Tari 2023 \- Rata Unica").  
* **`amount`:** Stringa. Importo dell'avviso di pagamento (es. "171,00 €").  
* **`status`:** Enum. Stato dell'avviso di pagamento (Default, Paid/PAGATO, Error/ERRORE, Expired/SCADUTO, Revoked/REVOCATO, In progress/IN CORSO, Skeleton).  
* **`showChevron`:** Booleano. Controlla la visibilità dell'indicatore di navigazione/azione (\>). Default: `true`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Definisce le configurazioni di stato visivo e di avviso del componente Module Payment Notice:

* **Default:** Stato standard dell'avviso di pagamento in attesa di azione dell'utente.  
* **Paid (PAGATO):** Stato di pagamento completato con successo.  
* **Error (ERRORE):** Stato di errore temporaneo o problema riscontrato nell'avviso.  
* **Expired (SCADUTO):** Stato in cui il termine ultimo di pagamento è trascorso.  
* **Revoked (REVOCATO):** Stato di avviso anullato o revocato dall'ente creditore.  
* **In progress (IN CORSO):** Stato di pagamento in fase di elaborazione o transazione avviata.

**Skeleton:** Stato di caricamento segnaposto delle informazioni del modulo.

## **4.2 Varianti di Azione**

Le varianti del componente variano in base allo stato del pagamento (PAGATO, ERRORE, SCADUTO, REVOCATO, IN CORSO, Default e Skeleton) e alla visualizzazione dell'indicatore di navigazione:

* **Modulo Avviso Standard:** Mostra codice avviso, descrizione del tributo (es. Tari 2023 \- Rata Unica), importo e stato dell'avviso.  
* **Varianti di Stato Badge:** PAGATO, ERRORE, SCADUTO, REVOCATO, IN CORSO.  
* **Variante Skeleton:** Struttura di caricamento visivo usata durante il recupero dei dati dell'avviso.

# **5\. Accessibilità (A11y) 🟠**

### **Module — Specifiche di Accessibilità**

**A11y \- DOM**: role="button" o role="link" sull'intero contenitore per moduli a interazione unificata (Navigation, Payment, Attachment, CGN), oppure contenitore neutro con comando interno dedicato (\<button\> / accessibilityRole="button") per varianti con CTA specifica (Checkout).

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * **Modulo interattivo a blocco unico** (Navigation, Payment Notice, Attachment, CGN, Credential): l'intera card costituisce un singolo elemento interattivo (pulsante / \<button\> se attiva un'azione o modale, link / \<a\> se naviga verso una nuova schermata o URL). Evita fermate di focus frammentate all'interno del modulo.  
  * **Modulo con azione dedicata** (Checkout module): se l'interazione è limitata alla sola CTA (es. "Modifica"), il modulo agisce da raggruppamento statico e il focus si posiziona unicamente sul pulsante dell'azione.  
* **Gerarchia interna**:  
  * **Titoli**: Esposti sempre come intestazione semantica (header / \<h2\>–\<h3\>) per preservare la navigazione gerarchica dell'interfaccia.  
  * **Accessible Name unificato**: Aggregare i contenuti testuali in un'unica stringa ordinata: Titolo principale \+ Descrizione/Codice \+ Importo o Data \+ Badge di stato (es. *"Tari 2023 \- Rata Unica, 171,00 €, Scaduto, pulsante"* oppure *"PayPal, email utente, Modifica, pulsante"*).  
  * **Icone e Chevron**: Chevron destra, icone logo/servizio e icone di formato (es. PDF) devono essere escluse dallo screen reader (aria-hidden="true" / accessible={false}) se il significato è già comunicato dal testo. Se un'icona trasmette un'informazione univoca non presente nel testo (es. punto esclamativo di errore isolato), assegnare una label programmatica esplicita.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con puntini di sospensione (...) devono garantire la lettura dell'intera stringa non troncata allo screen reader tramite etichetta accessibile dedicata.  
* **Elementi interattivi interni**:  
  * Evitare l'annidamento di elementi interattivi (nessun pulsante secondario dentro una card già interamente cliccabile).  
  * Differenziare semanticamente le azioni: usare il componente pulsante per aprire sheet/modali e il componente link per aperture di schermate o documenti PDF esterni.

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, codici, importi, badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della card.  
  * Icone informative, bordi e componenti grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*), escludendo codici colore arbitrari.  
* **Non dipendenza dal colore**:  
  * **Cosa fare**: Negli stati degli avvisi (Payment Notices), associare sempre un'etichetta testuale chiara o un'icona specifica alla variazione di colore:  
    * *Stati rossi (temporanei e risolvibili, es. "ERRORE")*: identificati da badge testuale e icona di pericolo/esclamativa.  
    * *Stati grigi (permanenti non risolvibili, es. "SCADUTO", "REVOCATO")*: identificati da dicitura testuale esplicita.  
    * *Stati verdi o neutri ("PAGATO", "IN CORSO", "NOVITÀ", "DEFAULT")*: accompagnati sempre dal relativo testo di stato.  
  * **Cosa evitare**: Non affidarsi unicamente al cambio cromatico del testo o della card per comunicare l'esito del pagamento, lo stato della pratica o l'interattività.  
    

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile obbligatorio su tutti i moduli o comandi focalizzabili tramite token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo circostante). È vietato sopprimere il contorno di focus.  
* **Touch Target**: Minimo garantito $44\times 44px$. Per i moduli a blocco unico l'area coincide con l'intera superficie della card; per controlli specifici isolati (es. pulsante "Modifica" o icona info) estendere l'area interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Raggiunge solo i controlli azionabili (l'intero modulo o la specifica CTA interna), escludendo i testi statici non interattivi.  
  * Invio / Spazio: Attiva l'azione o apre il pannello modale se il controllo è un pulsante (\<button\>).  
  * Invio: Esegue la navigazione verso il dettaglio o il download del documento se il controllo è un link (\<a\>).

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo)** | Nessun attributo live  | Letto come blocco unico ordinato: *"\[Titolo\], \[Importo/Codice\], \[Badge di stato se presente\], pulsante / link"*.  |
| **Comparsa improvvisa / dinamica** | role="alert" (urgente) o role="status" (normale) | *"\[Titolo modulo\] \- \[Importo/Stato aggiornato\]"*.  |
| **Caricamento / Azione in corso** | aria-busy="true" \+ blocco interazione | Segnala componente in elaborazione, impedendo invii o tocchi doppi.  |
| **Stato Skeleton (in caricamento)** | aria-busy="true" sul contenitore  | Segnala modulo in caricamento ed evita letture frammentate dei segnaposto visivi.  |
| **Disabilitato (es. Modulo non attivo)** | aria-disabled="true"  | *"\[Titolo\], non disponibile, pulsante disabilitato"* (visibile ma non attivabile). |

* **A11y \- DOM:** Contenitore a card o regione semantica (\<article\> o \<section\> su Web, \<View\> strutturata su mobile nativo); se l'intero modulo è cliccabile (es. navigazione a dettaglio o selezione provider), l'involucro primario è costituito da un elemento interattivo nativo (\<button\> o \<a\>) con nome accessibile unificato ricavato via aria-labelledby che concatena titolo, descrizione e importo/badge di stato. I nodi ausiliari e le icone grafiche sono contrassegnati come decorativi (aria-hidden="true" / accessible={false}), mentre negli stati di transizione o caricamento il nodo radice espone programmaticamente aria-busy="true" e aria-disabled="true" per inibire interazioni multiple nel DOM.

# **6\. Content**

# **Module Attachment**

Specifica tecnica e di design Machine-Readable per il componente Module Attachment del Design System IO.

```
---
id: component-module-attachment
name: Module Attachment
category: Modules
version: 1.0.0
tags: [module, attachment, pdf, document, ui, io-app]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente Module Attachment permette di visualizzare un allegato o documento digitale (es. "Verbale di accertamento per la violazione n. 12345.pdf") all'interno dell'applicazione IO. È composto da un'icona di formato (es. PDF), il titolo del file, la data dell'allegato (es. "18 maggio 2022"), un indicatore d'azione o chevron (\>) e supporta diversi stati visivi (Default, Disabled, Skeleton). È progettato per garantire un'accesso immediato ai documenti allegati e alle relative informazioni.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Riepilogo Documento Allegato:** Utilizzare per mostrare la sintesi di un file allegato (es. verbale, ricevuta, documento PDF) indicandone nome, formato e data.  
* **Regole di Spacing:** Applicare 16 px di spaziatura tra l'elemento e il contenuto del layout, 8 px di spazio verticale tra un Attachment Module e l'altro in una lista, e 24 px di margine dall'alto quando inserito all'interno di una bottom sheet per distanziarlo opportunamente dal titolo.  
* **Chiara Identificazione del Formato:** Indicare sempre in modo esplicito il formato del file (es. PDF) e la data di riferimento del documento.  
* **Area Cliccabile Intera:** Rendere l'intero modulo un'area d'interazione unica per l'apertura o il download del documento allegato.

## **Don't (Quando NON usare)**

* Non utilizzare per la gestione di avvisi di pagamento completi (usare Module Payment Notice) o per l'inserimento di azioni di input del modulo.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`fileName`:** Stringa. Nome del file o titolo dell'allegato (es. "Verbale di accertamento per la violazione n. 12345.pdf").  
* **`fileType`:** Stringa. Formato del documento (es. "PDF").  
* **`dateText`:** Stringa. Data dell'allegato (es. "18 maggio 2022").  
* **`state`:** Enum. Stato del modulo allegato (Default, Disabled, Skeleton). Default: `Default`.  
* **`showChevron`:** Booleano. Controlla la visibilità dell'indicatore di navigazione/azione (\>). Default: `true`.

# **4\. Stati e varianti**

## **4.1 Stato Default e Pressed**

Definisce le configurazioni di stato visivo del componente Module Attachment:

* **Default:** Stato standard del modulo allegato, cliccabile e attivo.  
* **Disabled:** Stato disabilitato non interattivo (modulo visibile ma non attivabile dall'utente).  
* **Skeleton:** Stato di caricamento segnaposto delle informazioni dell'allegato.

## **4.2 Varianti di Azione**

Le varianti del componente dipendono dallo stato dell'allegato (Default, Disabled, Skeleton) e dalla visualizzazione dell'indicatore chevron:

* **Modulo Attachment Standard:** Mostra nome file, formato PDF, data e freccia d'interazione (\>).  
* **Variante Disabilitata:** Stile depotenziato/opacizzato che inibisce l'interazione dell'utente.  
* **Variante Skeleton:** Struttura visuale di caricamento usata prima del recupero del file.

# **5\. Accessibilità (A11y) 🟠**

### **Module — Specifiche di Accessibilità**

**A11y \- DOM**: role="button" o role="link" sull'intero contenitore per moduli a interazione unificata (Navigation, Payment, Attachment, CGN), oppure contenitore neutro con comando interno dedicato (\<button\> / accessibilityRole="button") per varianti con CTA specifica (Checkout).

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * **Modulo interattivo a blocco unico** (Navigation, Payment Notice, Attachment, CGN, Credential): l'intera card costituisce un singolo elemento interattivo (pulsante / \<button\> se attiva un'azione o modale, link / \<a\> se naviga verso una nuova schermata o URL). Evita fermate di focus frammentate all'interno del modulo.  
  * **Modulo con azione dedicata** (Checkout module): se l'interazione è limitata alla sola CTA (es. "Modifica"), il modulo agisce da raggruppamento statico e il focus si posiziona unicamente sul pulsante dell'azione.  
* **Gerarchia interna**:  
  * **Titoli**: Esposti sempre come intestazione semantica (header / \<h2\>–\<h3\>) per preservare la navigazione gerarchica dell'interfaccia.  
  * **Accessible Name unificato**: Aggregare i contenuti testuali in un'unica stringa ordinata: Titolo principale \+ Descrizione/Codice \+ Importo o Data \+ Badge di stato (es. *"Tari 2023 \- Rata Unica, 171,00 €, Scaduto, pulsante"* oppure *"PayPal, email utente, Modifica, pulsante"*).  
  * **Icone e Chevron**: Chevron destra, icone logo/servizio e icone di formato (es. PDF) devono essere escluse dallo screen reader (aria-hidden="true" / accessible={false}) se il significato è già comunicato dal testo. Se un'icona trasmette un'informazione univoca non presente nel testo (es. punto esclamativo di errore isolato), assegnare una label programmatica esplicita.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con puntini di sospensione (...) devono garantire la lettura dell'intera stringa non troncata allo screen reader tramite etichetta accessibile dedicata.  
* **Elementi interattivi interni**:  
  * Evitare l'annidamento di elementi interattivi (nessun pulsante secondario dentro una card già interamente cliccabile).  
  * Differenziare semanticamente le azioni: usare il componente pulsante per aprire sheet/modali e il componente link per aperture di schermate o documenti PDF esterni.

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, codici, importi, badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della card.  
  * Icone informative, bordi e componenti grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*), escludendo codici colore arbitrari.  
* **Non dipendenza dal colore**:  
  * **Cosa fare**: Negli stati degli avvisi (Payment Notices), associare sempre un'etichetta testuale chiara o un'icona specifica alla variazione di colore:  
    * *Stati rossi (temporanei e risolvibili, es. "ERRORE")*: identificati da badge testuale e icona di pericolo/esclamativa.  
    * *Stati grigi (permanenti non risolvibili, es. "SCADUTO", "REVOCATO")*: identificati da dicitura testuale esplicita.  
    * *Stati verdi o neutri ("PAGATO", "IN CORSO", "NOVITÀ", "DEFAULT")*: accompagnati sempre dal relativo testo di stato.  
  * **Cosa evitare**: Non affidarsi unicamente al cambio cromatico del testo o della card per comunicare l'esito del pagamento, lo stato della pratica o l'interattività.  
    

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile obbligatorio su tutti i moduli o comandi focalizzabili tramite token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo circostante). È vietato sopprimere il contorno di focus.  
* **Touch Target**: Minimo garantito $44\times 44px$. Per i moduli a blocco unico l'area coincide con l'intera superficie della card; per controlli specifici isolati (es. pulsante "Modifica" o icona info) estendere l'area interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Raggiunge solo i controlli azionabili (l'intero modulo o la specifica CTA interna), escludendo i testi statici non interattivi.  
  * Invio / Spazio: Attiva l'azione o apre il pannello modale se il controllo è un pulsante (\<button\>).  
  * Invio: Esegue la navigazione verso il dettaglio o il download del documento se il controllo è un link (\<a\>).

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo)** | Nessun attributo live  | Letto come blocco unico ordinato: *"\[Titolo\], \[Importo/Codice\], \[Badge di stato se presente\], pulsante / link"*.  |
| **Comparsa improvvisa / dinamica** | role="alert" (urgente) o role="status" (normale) | *"\[Titolo modulo\] \- \[Importo/Stato aggiornato\]"*.  |
| **Caricamento / Azione in corso** | aria-busy="true" \+ blocco interazione | Segnala componente in elaborazione, impedendo invii o tocchi doppi.  |
| **Stato Skeleton (in caricamento)** | aria-busy="true" sul contenitore  | Segnala modulo in caricamento ed evita letture frammentate dei segnaposto visivi.  |
| **Disabilitato (es. Modulo non attivo)** | aria-disabled="true"  | *"\[Titolo\], non disponibile, pulsante disabilitato"* (visibile ma non attivabile). |

* **A11y \- DOM:** Contenitore a card o regione semantica (\<article\> o \<section\> su Web, \<View\> strutturata su mobile nativo); se l'intero modulo è cliccabile (es. navigazione a dettaglio o selezione provider), l'involucro primario è costituito da un elemento interattivo nativo (\<button\> o \<a\>) con nome accessibile unificato ricavato via aria-labelledby che concatena titolo, descrizione e importo/badge di stato. I nodi ausiliari e le icone grafiche sono contrassegnati come decorativi (aria-hidden="true" / accessible={false}), mentre negli stati di transizione o caricamento il nodo radice espone programmaticamente aria-busy="true" e aria-disabled="true" per inibire interazioni multiple nel DOM.

# **6\. Content**

# **Module Checkout**

Specifica tecnica e di design Machine-Readable per il componente Module Checkout del Design System IO.

```
---
id: component-module-checkout
name: Module Checkout
category: Modules
version: 1.0.0
tags: [module, checkout, payment, paypal, ui, io-app]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente Module Checkout permette di visualizzare e gestire il metodo di pagamento selezionato dall'utente (es. PayPal) all'interno del flusso di cassa e di pagamento dell'applicazione IO. È composto dal logo o nome del provider di pagamento (es. "PayPal"), un'etichetta/dettaglio informativo come l'account mascherato (es. "arien\_c\*\*\*\*\*\*@\*\*hoo.it"), e un'azione dedicata espressa tramite il pulsante "Modifica". Supporta diversi stati visivi e d'interazione (Default, Pressed, Skeleton) ed è progettato per garantire la massima trasparenza e chiarezza prima del completamento di una transazione.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Riepilogo Metodo di Pagamento:** Utilizzare nei flussi di checkout per mostrare il metodo di pagamento attualmente scelto dall'utente (es. PayPal con account mascherato).  
* **Azione Dedicata (Modifica):** Includere sempre il pulsante o controllo esplicito "Modifica" per consentire il cambio o l'aggiornamento rapido del metodo di pagamento senza interrompere il flusso dell'utente.  
* **Protezione dei Dati Sensibili:** Mascherare opportunamente le informazioni personali dell'account (es. email parzialmente oscurata "arien\_c\*\*\*\*\*\*@\*\*hoo.it") per garantire la privacy visiva.  
* **Gestione Stati di Caricamento:** Mostrare lo stato Skeleton durante il recupero dei dati del metodo di pagamento salvato.

## **Don't (Quando NON usare)**

* Non utilizzare per mostrare allegati di documenti (usare Module Attachment), avvisi di pagamento completi (usare Module Payment Notice) o all'esterno dei contesti di cassa e pagamento.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente Module Checkout è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`providerName`:** Stringa. Nome del provider di pagamento (es. "PayPal").  
* **`accountDetails`:** Stringa. Informazione mascherata dell'account o carta (es. "arien\_c\*\*\*\*\*\*@\*\*hoo.it").  
* **`actionLabel`:** Stringa. Testo dell'azione secondaria/dedicata. Default: `"Modifica"`.  
* **`state`:** Enum. Stato visivo ed interattivo del modulo (Default, Pressed, Skeleton). Default: `Default`.  
* **`onActionPress`:** Funzione callback attivata al click o tap sul pulsante "Modifica".

# **4\. Stati e varianti**

## **4.1 Stati (Default, Pressed, Skeleton)**

Definisce le configurazioni degli stati visivi del componente Module Checkout:

* **Default:** Stato visivo standard con provider (es. PayPal), account mascherato (es. arien\_c\*\*\*\*\*\*@\*\*hoo.it) e pulsante "Modifica" attivo.  
* **Pressed:** Stato di feedback visivo che si attiva durante l'interazione o la pressione sul pulsante "Modifica" o sull'area interattiva.  
* **Skeleton:** Stato di caricamento segnaposto mostrato durante il recupero dei dati del metodo di pagamento da rete.

## **4.2 Varianti di Azione**

Le varianti e le configurazioni principali del componente dipendono dalle informazioni esposte e dallo stato del modulo:

* **Modulo Checkout con Provider E-wallet:** Mostra il nome del servizio (es. PayPal), l'indirizzo email o dati identificativi mascherati e l'azione "Modifica".  
* **Stato Interattivo Pressed:** Evidenzia l'interazione in corso sull'azione di modifica.  
* **Variante Skeleton:** Struttura di placeholder animata o statica usata prima del caricamento completo del metodo di pagamento.

# **5\. Accessibilità (A11y) 🟠**

### **Module — Specifiche di Accessibilità**

**A11y \- DOM**: role="button" o role="link" sull'intero contenitore per moduli a interazione unificata (Navigation, Payment, Attachment, CGN), oppure contenitore neutro con comando interno dedicato (\<button\> / accessibilityRole="button") per varianti con CTA specifica (Checkout).

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * **Modulo interattivo a blocco unico** (Navigation, Payment Notice, Attachment, CGN, Credential): l'intera card costituisce un singolo elemento interattivo (pulsante / \<button\> se attiva un'azione o modale, link / \<a\> se naviga verso una nuova schermata o URL). Evita fermate di focus frammentate all'interno del modulo.  
  * **Modulo con azione dedicata** (Checkout module): se l'interazione è limitata alla sola CTA (es. "Modifica"), il modulo agisce da raggruppamento statico e il focus si posiziona unicamente sul pulsante dell'azione.  
* **Gerarchia interna**:  
  * **Titoli**: Esposti sempre come intestazione semantica (header / \<h2\>–\<h3\>) per preservare la navigazione gerarchica dell'interfaccia.  
  * **Accessible Name unificato**: Aggregare i contenuti testuali in un'unica stringa ordinata: Titolo principale \+ Descrizione/Codice \+ Importo o Data \+ Badge di stato (es. *"Tari 2023 \- Rata Unica, 171,00 €, Scaduto, pulsante"* oppure *"PayPal, email utente, Modifica, pulsante"*).  
  * **Icone e Chevron**: Chevron destra, icone logo/servizio e icone di formato (es. PDF) devono essere escluse dallo screen reader (aria-hidden="true" / accessible={false}) se il significato è già comunicato dal testo. Se un'icona trasmette un'informazione univoca non presente nel testo (es. punto esclamativo di errore isolato), assegnare una label programmatica esplicita.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con puntini di sospensione (...) devono garantire la lettura dell'intera stringa non troncata allo screen reader tramite etichetta accessibile dedicata.  
* **Elementi interattivi interni**:  
  * Evitare l'annidamento di elementi interattivi (nessun pulsante secondario dentro una card già interamente cliccabile).  
  * Differenziare semanticamente le azioni: usare il componente pulsante per aprire sheet/modali e il componente link per aperture di schermate o documenti PDF esterni.

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, codici, importi, badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della card.  
  * Icone informative, bordi e componenti grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*), escludendo codici colore arbitrari.  
* **Non dipendenza dal colore**:  
  * **Cosa fare**: Negli stati degli avvisi (Payment Notices), associare sempre un'etichetta testuale chiara o un'icona specifica alla variazione di colore:  
    * *Stati rossi (temporanei e risolvibili, es. "ERRORE")*: identificati da badge testuale e icona di pericolo/esclamativa.  
    * *Stati grigi (permanenti non risolvibili, es. "SCADUTO", "REVOCATO")*: identificati da dicitura testuale esplicita.  
    * *Stati verdi o neutri ("PAGATO", "IN CORSO", "NOVITÀ", "DEFAULT")*: accompagnati sempre dal relativo testo di stato.  
  * **Cosa evitare**: Non affidarsi unicamente al cambio cromatico del testo o della card per comunicare l'esito del pagamento, lo stato della pratica o l'interattività.  
    

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile obbligatorio su tutti i moduli o comandi focalizzabili tramite token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo circostante). È vietato sopprimere il contorno di focus.  
* **Touch Target**: Minimo garantito $44\times 44px$. Per i moduli a blocco unico l'area coincide con l'intera superficie della card; per controlli specifici isolati (es. pulsante "Modifica" o icona info) estendere l'area interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Raggiunge solo i controlli azionabili (l'intero modulo o la specifica CTA interna), escludendo i testi statici non interattivi.  
  * Invio / Spazio: Attiva l'azione o apre il pannello modale se il controllo è un pulsante (\<button\>).  
  * Invio: Esegue la navigazione verso il dettaglio o il download del documento se il controllo è un link (\<a\>).

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo)** | Nessun attributo live  | Letto come blocco unico ordinato: *"\[Titolo\], \[Importo/Codice\], \[Badge di stato se presente\], pulsante / link"*.  |
| **Comparsa improvvisa / dinamica** | role="alert" (urgente) o role="status" (normale) | *"\[Titolo modulo\] \- \[Importo/Stato aggiornato\]"*.  |
| **Caricamento / Azione in corso** | aria-busy="true" \+ blocco interazione | Segnala componente in elaborazione, impedendo invii o tocchi doppi.  |
| **Stato Skeleton (in caricamento)** | aria-busy="true" sul contenitore  | Segnala modulo in caricamento ed evita letture frammentate dei segnaposto visivi.  |
| **Disabilitato (es. Modulo non attivo)** | aria-disabled="true"  | *"\[Titolo\], non disponibile, pulsante disabilitato"* (visibile ma non attivabile). |

* **A11y \- DOM:** Contenitore a card o regione semantica (\<article\> o \<section\> su Web, \<View\> strutturata su mobile nativo); se l'intero modulo è cliccabile (es. navigazione a dettaglio o selezione provider), l'involucro primario è costituito da un elemento interattivo nativo (\<button\> o \<a\>) con nome accessibile unificato ricavato via aria-labelledby che concatena titolo, descrizione e importo/badge di stato. I nodi ausiliari e le icone grafiche sono contrassegnati come decorativi (aria-hidden="true" / accessible={false}), mentre negli stati di transizione o caricamento il nodo radice espone programmaticamente aria-busy="true" e aria-disabled="true" per inibire interazioni multiple nel DOM.

# **6\. Content**

# **Module Navigation**

Specifica tecnica e di design Machine-Readable per il componente Module Navigation del Design System IO.

```
---
id: component-module-navigation
name: Module Navigation
category: Modules
version: 1.0.0
tags: [module, navigation, spid, cie, identity, ui, io-app]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente Module Navigation permette di visualizzare un blocco interattivo orientato alla navigazione e alla selezione di opzioni primarie (es. metodi di autenticazione come SPID o CIE) all'interno dell'applicazione IO. È composto da un titolo/provider (es. "SPID"), una descrizione o sottotitolo esplicativo (es. "Usa credenziali e app (o SMS)"), un eventuale badge informativo (es. "IN ARRIVO") e un indicatore visivo di direzione (chevron "\>"). Si distingue strutturalmente dal "List item navigation" in quanto quest'ultimo è progettato come riga sequenziale all'interno di elenchi e liste dati stese, mentre il Module Navigation si presenta come una card/modulo autonomo a blocco unico con spaziatura e gerarchia visiva dedicata. Supporta diversi stati (Active/Default, Pressed, Skeleton) ed è ottimizzato per facilitare le scelte di navigazione di alto livello.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Selezione Opzioni Principali di Navigazione:** Utilizzare nei contesti di scelta ad alto livello (es. selezione del provider di identità digitale SPID o CIE) in cui ogni opzione richiede una rilevanza visiva a scheda/modulo autonomo.  
* **Navigazione Guidata con Indicatori:** Includere sempre la chevron visiva ("\>") e descrizioni sintetiche per chiarire l'azione di atterraggio prima dell'interazione.  
* **Gestione di Badge di Stato:** Utilizzare etichette o badge interni (es. "IN ARRIVO") per comunicare la disponibilità o lo stato del servizio integrato nel modulo.  
* **Stati di Caricamento:** Mostrare la variante Skeleton durante il caricamento asincrono delle opzioni di navigazione dinamiche.

## **Don't (Quando NON usare)**

* Non utilizzare all'interno di liste dense o elenchi continui di impostazioni (usare il componente List Item Navigation).   
* Non utilizzare per riepiloghi di pagamento (usare Module Checkout) o allegati (usare Module Attachment).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente Module Navigation è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`title`:** Stringa. Titolo principale della voce di navigazione (es. "SPID").  
* **`description`:** Stringa. Sottotitolo o descrizione operativa esplicativa (es. "Usa credenziali e app (o SMS)").  
* **`badgeText`:** Stringa opzionale. Testo del badge di stato visibile nel modulo (es. "IN ARRIVO").  
* **`showChevron`:** Boolean. Indica la presenza dell'icona chevron ("\>") di puntamento. Default: `true`.  
* **`state`:** Enum. Stato visivo ed interattivo del modulo (Active/Default, Pressed, Skeleton). Default: `Active`.

# **4\. Stati e varianti**

## **4.1 Stati (Active, Pressed, Skeleton)**

Definisce le configurazioni degli stati visivi del componente Module Navigation:

* **Active (Default):** Stato interattivo standard pronto alla selezione, con titolo, descrizione, eventuale badge e chevron visibile.  
* **Pressed:** Stato di feedback visivo (background evidenziato) durante la pressione dell'utente sull'intera superficie della card.  
* **Skeleton:** Stato di caricamento con segnaposto animato per simulare la struttura del modulo prima della resa dei dati.

## **4.2 Varianti di Azione**

Le varianti del componente Module Navigation si articolano principalmente in base allo stato informativo ed alla presenza di elementi ausiliari:

* **Modulo di Navigazione Standard (es. SPID):** Comprende titolo principale, descrizione estesa ed indicatore chevron di proseguimento.  
* **Modulo con Badge Informativo:** Integra un badge visivo (es. "IN ARRIVO") affiancato alle informazioni primarie.  
* **Variante Skeleton:** Struttura di layout temporanea per mantenere le proporzioni durante il caricamento.

# **5\. Accessibilità (A11y) 🟠**

### **Module — Specifiche di Accessibilità**

**A11y \- DOM**: role="button" o role="link" sull'intero contenitore per moduli a interazione unificata (Navigation, Payment, Attachment, CGN), oppure contenitore neutro con comando interno dedicato (\<button\> / accessibilityRole="button") per varianti con CTA specifica (Checkout).

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * **Modulo interattivo a blocco unico** (Navigation, Payment Notice, Attachment, CGN, Credential): l'intera card costituisce un singolo elemento interattivo (pulsante / \<button\> se attiva un'azione o modale, link / \<a\> se naviga verso una nuova schermata o URL). Evita fermate di focus frammentate all'interno del modulo.  
  * **Modulo con azione dedicata** (Checkout module): se l'interazione è limitata alla sola CTA (es. "Modifica"), il modulo agisce da raggruppamento statico e il focus si posiziona unicamente sul pulsante dell'azione.  
* **Gerarchia interna**:  
  * **Titoli**: Esposti sempre come intestazione semantica (header / \<h2\>–\<h3\>) per preservare la navigazione gerarchica dell'interfaccia.  
  * **Accessible Name unificato**: Aggregare i contenuti testuali in un'unica stringa ordinata: Titolo principale \+ Descrizione/Codice \+ Importo o Data \+ Badge di stato (es. *"Tari 2023 \- Rata Unica, 171,00 €, Scaduto, pulsante"* oppure *"PayPal, email utente, Modifica, pulsante"*).  
  * **Icone e Chevron**: Chevron destra, icone logo/servizio e icone di formato (es. PDF) devono essere escluse dallo screen reader (aria-hidden="true" / accessible={false}) se il significato è già comunicato dal testo. Se un'icona trasmette un'informazione univoca non presente nel testo (es. punto esclamativo di errore isolato), assegnare una label programmatica esplicita.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con puntini di sospensione (...) devono garantire la lettura dell'intera stringa non troncata allo screen reader tramite etichetta accessibile dedicata.  
* **Elementi interattivi interni**:  
  * Evitare l'annidamento di elementi interattivi (nessun pulsante secondario dentro una card già interamente cliccabile).  
  * Differenziare semanticamente le azioni: usare il componente pulsante per aprire sheet/modali e il componente link per aperture di schermate o documenti PDF esterni.

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, codici, importi, badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della card.  
  * Icone informative, bordi e componenti grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*), escludendo codici colore arbitrari.  
* **Non dipendenza dal colore**:  
  * **Cosa fare**: Negli stati degli avvisi (Payment Notices), associare sempre un'etichetta testuale chiara o un'icona specifica alla variazione di colore:  
    * *Stati rossi (temporanei e risolvibili, es. "ERRORE")*: identificati da badge testuale e icona di pericolo/esclamativa.  
    * *Stati grigi (permanenti non risolvibili, es. "SCADUTO", "REVOCATO")*: identificati da dicitura testuale esplicita.  
    * *Stati verdi o neutri ("PAGATO", "IN CORSO", "NOVITÀ", "DEFAULT")*: accompagnati sempre dal relativo testo di stato.  
  * **Cosa evitare**: Non affidarsi unicamente al cambio cromatico del testo o della card per comunicare l'esito del pagamento, lo stato della pratica o l'interattività.  
    

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile obbligatorio su tutti i moduli o comandi focalizzabili tramite token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo circostante). È vietato sopprimere il contorno di focus.  
* **Touch Target**: Minimo garantito $44\times 44px$. Per i moduli a blocco unico l'area coincide con l'intera superficie della card; per controlli specifici isolati (es. pulsante "Modifica" o icona info) estendere l'area interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Raggiunge solo i controlli azionabili (l'intero modulo o la specifica CTA interna), escludendo i testi statici non interattivi.  
  * Invio / Spazio: Attiva l'azione o apre il pannello modale se il controllo è un pulsante (\<button\>).  
  * Invio: Esegue la navigazione verso il dettaglio o il download del documento se il controllo è un link (\<a\>).

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo)** | Nessun attributo live  | Letto come blocco unico ordinato: *"\[Titolo\], \[Importo/Codice\], \[Badge di stato se presente\], pulsante / link"*.  |
| **Comparsa improvvisa / dinamica** | role="alert" (urgente) o role="status" (normale) | *"\[Titolo modulo\] \- \[Importo/Stato aggiornato\]"*.  |
| **Caricamento / Azione in corso** | aria-busy="true" \+ blocco interazione | Segnala componente in elaborazione, impedendo invii o tocchi doppi.  |
| **Stato Skeleton (in caricamento)** | aria-busy="true" sul contenitore  | Segnala modulo in caricamento ed evita letture frammentate dei segnaposto visivi.  |
| **Disabilitato (es. Modulo non attivo)** | aria-disabled="true"  | *"\[Titolo\], non disponibile, pulsante disabilitato"* (visibile ma non attivabile). |

* **A11y \- DOM:** Contenitore a card o regione semantica (\<article\> o \<section\> su Web, \<View\> strutturata su mobile nativo); se l'intero modulo è cliccabile (es. navigazione a dettaglio o selezione provider), l'involucro primario è costituito da un elemento interattivo nativo (\<button\> o \<a\>) con nome accessibile unificato ricavato via aria-labelledby che concatena titolo, descrizione e importo/badge di stato. I nodi ausiliari e le icone grafiche sono contrassegnati come decorativi (aria-hidden="true" / accessible={false}), mentre negli stati di transizione o caricamento il nodo radice espone programmaticamente aria-busy="true" e aria-disabled="true" per inibire interazioni multiple nel DOM.

# **6\. Content**

# **Module Credential**

Specifica tecnica e di design Machine-Readable per il componente Module Credential del Design System IO.

```
---
id: component-module-credential
name: Module Credential
category: Modules
version: 1.0.0
tags: [module, credential, identity, digital-identity, spid, cie, ui, io-app]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente Module Credential permette di visualizzare un blocco interattivo orientato alla presentazione ed alla gestione delle credenziali e delle identità digitali dell'utente (es. attributi e servizi legati all'Identità Digitale) all'interno dell'applicazione IO. È composto da un titolo/provider o nome della credenziale (es. "Identità Digitale"), una descrizione esplicativa o attributo associato, un eventuale badge informativo di stato (es. "BADGE") e un indicatore visivo di direzione (chevron "\>"). Si distingue strutturalmente dal "List item navigation" in quanto quest'ultimo è progettato come semplice riga sequenziale all'interno di elenchi stesi di opzioni o impostazioni generiche, mentre il Module Credential è una card/modulo autonomo focalizzato sul dominio specifico delle credenziali utente, caratterizzato da una spaziatura interna/esterna dedicata (con regola di spaziatura fissa a 8 px) e da una gerarchia visiva ed informativa a blocco unico. Supporta diversi stati interattivi ed è ottimizzato per garantire l'accesso immediato alle opzioni legate alle credenziali personali.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Gestione e Selezione Credenziali:** Utilizzare nei contesti dedicati all'Identità Digitale o alla gestione delle credenziali utente (es. SPID, CIE o altri provider di identità) in cui l'opzione richiede un contenitore autonomo e ben delineato.  
* **Applicazione Spaziatura Standard (8 px):** Rispettare rigorosamente la regola di spaziatura dedicata di 8 px (margin/padding) per il Module Credential, al fine di garantire coerenza visiva e separazione ottimale rispetto agli altri elementi del layout.  
* **Indicatori Visivi e Badge di Credenziale:** Includere la chevron visiva ("\>") per l'azione di dettaglio ed eventuali badge di stato (es. "BADGE") per segnalare condizioni specifiche della credenziale.  
* **Stati di Caricamento:** Utilizzare la variante Skeleton durante il recupero o la verifica asincrona dei dati relativi alla credenziale.

## **Don't (Quando NON usare)**

* Non utilizzare al posto del componente List Item Navigation all'interno di liste dense di impostazioni generali. Non utilizzare per moduli di pagamento (usare Module Checkout) o per la fruizione di allegati documenti (usare Module Attachment).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente Module Credential è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`title`:** Stringa. Titolo principale o nome della credenziale (es. "Module Credential" o "Identità Digitale").  
* **`description`:** Stringa opzionale. Descrizione esplicativa o stato associato alla credenziale.  
* **`badgeText`:** Stringa opzionale. Testo dell'etichetta o badge di stato visibile nel modulo (es. "BADGE").  
* **`showChevron`:** Boolean. Indica la presenza dell'icona chevron ("\>") di puntamento. Default: `true`.  
* **`state`:** Enum. Stato visivo ed interattivo del modulo (Active/Default, Pressed, Skeleton). Default: `Active`.

# **4\. Stati e varianti**

## **4.1 Stati (Active, Pressed, Skeleton)**

Definisce le configurazioni degli stati visivi del componente Module Credential:

* **Active (Default):** Stato interattivo standard pronto alla selezione, con titolo, descrizione, eventuale badge e chevron visibile.  
* **Pressed:** Stato di feedback visivo (background evidenziato) durante la pressione dell'utente sull'intera superficie della card.  
* **Skeleton:** Stato di caricamento con segnaposto animato per simulare la struttura del modulo prima della resa dei dati.

## **4.2 Varianti di Azione**

Le varianti del componente Module Credential si articolano principalmente in base alle informazioni della credenziale ed alla presenza di badge ed indicatori:

* **Modulo Credenziale Standard (es. Identità Digitale):** Comprende titolo principale, descrizione ed indicatore chevron di proseguimento ("\>").  
* **Modulo Credenziale con Badge:** Integra un badge informativo (es. "BADGE") affiancato al titolo o ai dettagli della credenziale.  
* **Variante Skeleton:** Struttura di layout temporanea per mantenere le proporzioni durante il caricamento.

# **5\. Accessibilità (A11y) 🟠**

### **Module — Specifiche di Accessibilità**

**A11y \- DOM (Document Object Model)**: role="button" o role="link" sull'intero contenitore per moduli a interazione unificata (Navigation, Payment, Attachment, CGN), oppure contenitore neutro con comando interno dedicato (\<button\> / accessibilityRole="button") per varianti con CTA specifica (Checkout).

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * **Modulo interattivo a blocco unico** (Navigation, Payment Notice, Attachment, CGN, Credential): l'intera card costituisce un singolo elemento interattivo (pulsante / \<button\> se attiva un'azione o modale, link / \<a\> se naviga verso una nuova schermata o URL). Evita fermate di focus frammentate all'interno del modulo.  
  * **Modulo con azione dedicata** (Checkout module): se l'interazione è limitata alla sola CTA (es. "Modifica"), il modulo agisce da raggruppamento statico e il focus si posiziona unicamente sul pulsante dell'azione.  
* **Gerarchia interna**:  
  * **Titoli**: Esposti sempre come intestazione semantica (header / \<h2\>–\<h3\>) per preservare la navigazione gerarchica dell'interfaccia.  
  * **Accessible Name unificato**: Aggregare i contenuti testuali in un'unica stringa ordinata: Titolo principale \+ Descrizione/Codice \+ Importo o Data \+ Badge di stato (es. *"Tari 2023 \- Rata Unica, 171,00 €, Scaduto, pulsante"* oppure *"PayPal, email utente, Modifica, pulsante"*).  
  * **Icone e Chevron**: Chevron destra, icone logo/servizio e icone di formato (es. PDF) devono essere escluse dallo screen reader (aria-hidden="true" / accessible={false}) se il significato è già comunicato dal testo. Se un'icona trasmette un'informazione univoca non presente nel testo (es. punto esclamativo di errore isolato), assegnare una label programmatica esplicita.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con puntini di sospensione (...) devono garantire la lettura dell'intera stringa non troncata allo screen reader tramite etichetta accessibile dedicata.  
* **Elementi interattivi interni**:  
  * Evitare l'annidamento di elementi interattivi (nessun pulsante secondario dentro una card già interamente cliccabile).  
  * Differenziare semanticamente le azioni: usare il componente pulsante per aprire sheet/modali e il componente link per aperture di schermate o documenti PDF esterni.

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, codici, importi, badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della card.  
  * Icone informative, bordi e componenti grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*), escludendo codici colore arbitrari.  
* **Non dipendenza dal colore**:  
  * **Cosa fare**: Negli stati degli avvisi (Payment Notices), associare sempre un'etichetta testuale chiara o un'icona specifica alla variazione di colore:  
    * *Stati rossi (temporanei e risolvibili, es. "ERRORE")*: identificati da badge testuale e icona di pericolo/esclamativa.  
    * *Stati grigi (permanenti non risolvibili, es. "SCADUTO", "REVOCATO")*: identificati da dicitura testuale esplicita.  
    * *Stati verdi o neutri ("PAGATO", "IN CORSO", "NOVITÀ", "DEFAULT")*: accompagnati sempre dal relativo testo di stato.  
  * **Cosa evitare**: Non affidarsi unicamente al cambio cromatico del testo o della card per comunicare l'esito del pagamento, lo stato della pratica o l'interattività.  
    

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile obbligatorio su tutti i moduli o comandi focalizzabili tramite token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo circostante). È vietato sopprimere il contorno di focus.  
* **Touch Target**: Minimo garantito $44\times 44px$. Per i moduli a blocco unico l'area coincide con l'intera superficie della card; per controlli specifici isolati (es. pulsante "Modifica" o icona info) estendere l'area interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Raggiunge solo i controlli azionabili (l'intero modulo o la specifica CTA interna), escludendo i testi statici non interattivi.  
  * Invio / Spazio: Attiva l'azione o apre il pannello modale se il controllo è un pulsante (\<button\>).  
  * Invio: Esegue la navigazione verso il dettaglio o il download del documento se il controllo è un link (\<a\>).

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo)** | Nessun attributo live  | Letto come blocco unico ordinato: *"\[Titolo\], \[Importo/Codice\], \[Badge di stato se presente\], pulsante / link"*.  |
| **Comparsa improvvisa / dinamica** | role="alert" (urgente) o role="status" (normale) | *"\[Titolo modulo\] \- \[Importo/Stato aggiornato\]"*.  |
| **Caricamento / Azione in corso** | aria-busy="true" \+ blocco interazione | Segnala componente in elaborazione, impedendo invii o tocchi doppi.  |
| **Stato Skeleton (in caricamento)** | aria-busy="true" sul contenitore  | Segnala modulo in caricamento ed evita letture frammentate dei segnaposto visivi.  |
| **Disabilitato (es. Modulo non attivo)** | aria-disabled="true"  | *"\[Titolo\], non disponibile, pulsante disabilitato"* (visibile ma non attivabile). |

* **A11y \- DOM (Document Object Model):** Contenitore a card o regione semantica (\<article\> o \<section\> su Web, \<View\> strutturata su mobile nativo); se l'intero modulo è cliccabile (es. navigazione a dettaglio o selezione provider), l'involucro primario è costituito da un elemento interattivo nativo (\<button\> o \<a\>) con nome accessibile unificato ricavato via aria-labelledby che concatena titolo, descrizione e importo/badge di stato. I nodi ausiliari e le icone grafiche sono contrassegnati come decorativi (aria-hidden="true" / accessible={false}), mentre negli stati di transizione o caricamento il nodo radice espone programmaticamente aria-busy="true" e aria-disabled="true" per inibire interazioni multiple nel DOM (Document Object Model).

# **6\. Content**

# **Module CGN Discount**

Specifica tecnica e di design Machine-Readable per il componente Module CGN Discount del Design System IO.

```
---
id: component-module-cgn-discount
name: Module CGN Discount
category: Modules
version: 1.0.0
tags: [module, cgn, discount, carta-giovani-nazionale, operator, deal, ui, io-app]
last_updated: 2026-11-10
---
```

# **1\. Descrizione**

Il componente Module CGN Discount è progettato specificamente per la gestione e la rappresentazione delle proposte e delle offerte dei singoli operatori aderenti alla Carta Giovani Nazionale (CGN) all'interno dell'applicazione IO. Si presenta come un modulo/card autonomo interattivo che raccoglie il nome dell'operatore o titolo dell'offerta, una descrizione o dettaglio dell'opportunità, un badge dello sconto applicato opzionale (es. "-25%") e un indicatore visivo di direzione (chevron "\>"). Supporta inoltre la variante speciale "Novità", caratterizzata da una colorazione viola distintiva e da un badge dedicato. Rispettando l'architettura a moduli del Design System, garantisce una composizione in pagina coerente mediante una regola di spaziatura fissa di 8 px (margin/padding) per la separazione visiva dagli altri elementi del layout.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Rappresentazione Offerte Carta Giovani Nazionale (CGN):** Utilizzare nelle schermate dedicate all'esposizione delle promozioni e degli sconti dei singoli operatori partner della CGN nell'app IO.  
* **Applicazione Spaziatura Standard (8 px):** Rispettare rigorosamente la regola di spaziatura dedicata di 8 px per la composizione del layout in pagina, garantendo il corretto respiro visivo del modulo.  
* **Gestione Badge ed Evidenze Opzionali:** Includere il badge del valore dello sconto (es. "-25%") quando pertinente e utilizzare la variante Novità (colorazione viola) per evidenziare nuove convenzioni o promozioni appena lanciate.  
* **Stati di Caricamento:** Utilizzare la variante Skeleton durante il recupero o la verifica asincrona dei dati relativi alla credenziale.

## **Don't (Quando NON usare)**

* Non utilizzare per la gestione dell'identità o credenziali generali dell'utente (usare Module Credential). Non utilizzare per pagamenti (usare Module Checkout) o per la lista di allegati e documenti generici (usare Module Attachment).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente Module Credential è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`title`:** Stringa. Nome dell'operatore o titolo della promozione CGN.  
* **`description`:** Stringa opzionale. Descrizione dettagliata dell'offerta o termini della promozione.  
* **`discountBadgeText`:** Stringa opzionale. Etichetta visiva dello sconto applicato (es. "-25%"). Non è un elemento obbligatorio.  
* **`isNew`:** Boolean. Abilita la variante "Novità" con colorazione viola e badge dedicato. Default: `false`.  
* **`showChevron`:** Boolean. Mostra l'indicatore visivo chevron ("\>") a destra del modulo. Default: `true`.  
* **`state`:** Enum. Stato visivo ed interattivo del modulo (Active/Default, Pressed, Skeleton). Default: `Active`.

# **4\. Stati e varianti**

## **4.1 Stati (Active, Pressed, Skeleton)**

Definisce le configurazioni degli stati visivi del componente Module Credential:

* **Active (Default):** Stato interattivo standard pronto alla selezione, con titolo, descrizione, eventuale badge e chevron visibile.  
* **Pressed:** Stato di feedback visivo (background evidenziato) durante la pressione dell'utente sull'intera superficie della card.  
* **Skeleton:** Stato di caricamento con segnaposto animato per simulare la struttura del modulo prima della resa dei dati.

## **4.2 Varianti di Azione**

Le varianti del componente Module Credential si articolano principalmente in base alle informazioni della credenziale ed alla presenza di badge ed indicatori:

* **Modulo CGN Discount Default:** Configurazione standard contenente titolo operatore, testo descrittivo, eventuale badge sconto e chevron di navigazione.  
* **Variante Novità (Viola):** Variante speciale ad alto impatto visivo con tema cromatico viola e badge dedicato "NOVITÀ" affiancato alle informazioni dello sconto.  
* **Variante Skeleton:** Struttura di layout temporanea per mantenere le proporzioni durante il caricamento.

# **5\. Accessibilità (A11y) 🟠**

### **Module — Specifiche di Accessibilità**

**A11y \- DOM (Document Object Model)**: role="button" o role="link" sull'intero contenitore per moduli a interazione unificata (Navigation, Payment, Attachment, CGN), oppure contenitore neutro con comando interno dedicato (\<button\> / accessibilityRole="button") per varianti con CTA specifica (Checkout).

#### **1\. Ruolo e Struttura Semantica**

* **Ruolo del contenitore**:  
  * **Modulo interattivo a blocco unico** (Navigation, Payment Notice, Attachment, CGN, Credential): l'intera card costituisce un singolo elemento interattivo (pulsante / \<button\> se attiva un'azione o modale, link / \<a\> se naviga verso una nuova schermata o URL). Evita fermate di focus frammentate all'interno del modulo.  
  * **Modulo con azione dedicata** (Checkout module): se l'interazione è limitata alla sola CTA (es. "Modifica"), il modulo agisce da raggruppamento statico e il focus si posiziona unicamente sul pulsante dell'azione.  
* **Gerarchia interna**:  
  * **Titoli**: Esposti sempre come intestazione semantica (header / \<h2\>–\<h3\>) per preservare la navigazione gerarchica dell'interfaccia.  
  * **Accessible Name unificato**: Aggregare i contenuti testuali in un'unica stringa ordinata: Titolo principale \+ Descrizione/Codice \+ Importo o Data \+ Badge di stato (es. *"Tari 2023 \- Rata Unica, 171,00 €, Scaduto, pulsante"* oppure *"PayPal, email utente, Modifica, pulsante"*).  
  * **Icone e Chevron**: Chevron destra, icone logo/servizio e icone di formato (es. PDF) devono essere escluse dallo screen reader (aria-hidden="true" / accessible={false}) se il significato è già comunicato dal testo. Se un'icona trasmette un'informazione univoca non presente nel testo (es. punto esclamativo di errore isolato), assegnare una label programmatica esplicita.  
  * **Testi lunghi**: I testi dinamici che superano le due righe e vengono troncati visivamente con puntini di sospensione (...) devono garantire la lettura dell'intera stringa non troncata allo screen reader tramite etichetta accessibile dedicata.  
* **Elementi interattivi interni**:  
  * Evitare l'annidamento di elementi interattivi (nessun pulsante secondario dentro una card già interamente cliccabile).  
  * Differenziare semanticamente le azioni: usare il componente pulsante per aprire sheet/modali e il componente link per aperture di schermate o documenti PDF esterni.

#### **2\. Contrasto e Riconoscibilità Visiva**

* **Rapporti minimi**:  
  * Testi (titoli, codici, importi, badge e CTA): $\geq 4.5:1$ rispetto allo sfondo della card.  
  * Icone informative, bordi e componenti grafici: $\geq 3.0:1$ rispetto allo sfondo.  
  * Utilizzare unicamente i token semantici del Design System (es. color.text.\*, color.background.\*, color.action.\*), escludendo codici colore arbitrari.  
* **Non dipendenza dal colore**:  
  * **Cosa fare**: Negli stati degli avvisi (Payment Notices), associare sempre un'etichetta testuale chiara o un'icona specifica alla variazione di colore:  
    * *Stati rossi (temporanei e risolvibili, es. "ERRORE")*: identificati da badge testuale e icona di pericolo/esclamativa.  
    * *Stati grigi (permanenti non risolvibili, es. "SCADUTO", "REVOCATO")*: identificati da dicitura testuale esplicita.  
    * *Stati verdi o neutri ("PAGATO", "IN CORSO", "NOVITÀ", "DEFAULT")*: accompagnati sempre dal relativo testo di stato.  
  * **Cosa evitare**: Non affidarsi unicamente al cambio cromatico del testo o della card per comunicare l'esito del pagamento, lo stato della pratica o l'interattività.  
    

#### **3\. Interazione, Focus e Tastiera**

* **Focus ring**: Indicatore visibile obbligatorio su tutti i moduli o comandi focalizzabili tramite token semantico color.border.focus.outer (spessore $\geq 2px$ e contrasto $\geq 3.0:1$ rispetto allo sfondo circostante). È vietato sopprimere il contorno di focus.  
* **Touch Target**: Minimo garantito $44\times 44px$. Per i moduli a blocco unico l'area coincide con l'intera superficie della card; per controlli specifici isolati (es. pulsante "Modifica" o icona info) estendere l'area interattiva tramite padding trasparente.  
* **Mappa Tasti & Gesti essenziale**:  
  * Tab / Shift \+ Tab: Raggiunge solo i controlli azionabili (l'intero modulo o la specifica CTA interna), escludendo i testi statici non interattivi.  
  * Invio / Spazio: Attiva l'azione o apre il pannello modale se il controllo è un pulsante (\<button\>).  
  * Invio: Esegue la navigazione verso il dettaglio o il download del documento se il controllo è un link (\<a\>).

#### **4\. Comportamento Screen Reader (Stati)**

| Scenario / Stato UI | Proprietà Tecnica | Cosa deve sentire l'utente |
| :---- | :---- | :---- |
| **Elemento statico (già a schermo)** | Nessun attributo live  | Letto come blocco unico ordinato: *"\[Titolo\], \[Importo/Codice\], \[Badge di stato se presente\], pulsante / link"*.  |
| **Comparsa improvvisa / dinamica** | role="alert" (urgente) o role="status" (normale) | *"\[Titolo modulo\] \- \[Importo/Stato aggiornato\]"*.  |
| **Caricamento / Azione in corso** | aria-busy="true" \+ blocco interazione | Segnala componente in elaborazione, impedendo invii o tocchi doppi.  |
| **Stato Skeleton (in caricamento)** | aria-busy="true" sul contenitore  | Segnala modulo in caricamento ed evita letture frammentate dei segnaposto visivi.  |
| **Disabilitato (es. Modulo non attivo)** | aria-disabled="true"  | *"\[Titolo\], non disponibile, pulsante disabilitato"* (visibile ma non attivabile). |

* **A11y \- DOM (Document Object Model):** Contenitore a card o regione semantica (\<article\> o \<section\> su Web, \<View\> strutturata su mobile nativo); se l'intero modulo è cliccabile (es. navigazione a dettaglio o selezione provider), l'involucro primario è costituito da un elemento interattivo nativo (\<button\> o \<a\>) con nome accessibile unificato ricavato via aria-labelledby che concatena titolo, descrizione e importo/badge di stato. I nodi ausiliari e le icone grafiche sono contrassegnati come decorativi (aria-hidden="true" / accessible={false}), mentre negli stati di transizione o caricamento il nodo radice espone programmaticamente aria-busy="true" e aria-disabled="true" per inibire interazioni multiple nel DOM (Document Object Model).

# **6\. Content**

# **Markdown**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare per il rendering di testo formattato dinamico e blocchi di contenuti.

```
---
id: component-markdown
name: Markdown
category: Data Display & Structure
version: 1.0.0
tags: [markdown, text-block, rich-text, formatting, service-detail]
last_updated: 2026-11-03
---
```

# **Descrizione** 

Il componente `Markdown` consente di formattare ed erogare testo arricchito in modo dinamico all’interno dell’interfaccia utente. È progettato per interpretare sintassi di formattazione leggera e trasformarla in elementi tipografici strutturati all’interno del DOM (Document Object Model). Permette l’integrazione di titoli di pagina, sottotitoli, paragrafi di testo esteso, elementi in grassetto, corsivo, link e liste puntate. Viene comunemente impiegato nelle schede di dettaglio servizio e nei blocchi informativi testuali (es. servizi Bollo Auto di ACI) per presentare elenchi di funzionalità, conferme di pagamento o avvisi di scadenza.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Strutturazione di contenuti dinamici:** Utilizzare il componente per interpretare blocchi di testo formattati con titoli, sottotitoli e paragrafi strutturati.  
* **Formattazione testuale avanzata:** Applicare stile grassetto, corsivo e collegamenti ipertestuali (link) all'interno di paragrafi estesi per dare la giusta gerarchia e risalto alle informazioni.  
* **Liste puntate funzionali:** Impiegare elenchi puntati per schematizzare azioni utente o funzionalità di servizio (ad esempio: "ricevere un promemoria", "pagare il Bollo Auto").  
* **Dettagli di servizio:** Utilizzare nei dettagli di servizio e comunicazioni istituzionali che richiedono testo formattato descrittivo.

## **Don't (Quando NON usare)**

* Non utilizzare il componente Markdown per la resa di singoli campi di input o etichette semplici che non necessitano di formattazione ricca.  
* Non sovraccaricare il testo con combinazioni eccessive di grassetti, corsivi e link nella stessa riga per evitare confusione visiva.  
* Non inserire codice HTML non sicuro all'interno della stringa Markdown per prevenire problemi di rendering nel DOM (Document Object Model).  
* Non alterare manualmente la spaziatura verticale tra paragrafi e titoli in modo disallineato rispetto alle linee guida di sistema.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice per la gestione dei blocchi di testo:

* **`content`**: Stringa di testo in sintassi Markdown da renderizzare nel DOM (Document Object Model). Supporta titoli, sottotitoli, paragrafi, grassetto, corsivo, link ed elenchi. Default: `""`.  
* **`variant`**: Definisce il contesto d'uso del blocco di testo. Valori: `default` (blocco di testo libero standard con titolo e paragrafo) o `service-detail` (struttura informativa specifica con elenchi ed evidenze per schede servizio). Default: `"default"`.  
* **`truncation`**: Se impostata su `true`, limita la lunghezza del blocco di testo inserendo puntini di sospensione o un'interruzione graduale. Default: `false`.  
* **`isInteractive`**: Determina se i collegamenti ipertestuali (link) all'interno del contenuto Markdown sono cliccabili ed eseguibili dall'utente. Default: `true`.

# **4\. Stati e varianti**

## **4.1 Stati Tipografici ed Elementi Supportati**

Il componente Markdown gestisce i seguenti elementi e stati di formattazione nel DOM (Document Object Model / Modello a Oggetti del Documento):

* **Titolo della pagina (Heading 1):** Elemento principale di intestazione per identificare la sezione o la scheda.  
* **Sottotitolo della pagina (Heading 2):** Elemento per suddividere concettualmente i blocchi di testo secondari.  
* **Stili di testo (Bold, Italic, Link):** Gestione inline di enfasi forte (grassetto), enfasi leggera (corsivo) e collegamenti esterni cliccabili.  
* **Liste puntate (Unordered List):** Elenco con contrassegno visivo per la presentazione sintetica di punti chiave.

## **4.2 Varianti del componente**

Di seguito sono elencate le principali varianti supportate per la strutturazione dei contenuti all'interno del DOM (Document Object Model / Modello a Oggetti del Documento):

* **Titolo:** Variante dedicata alla resa di un titolo principale isolato, utilizzata per definire la gerarchia visiva primaria della pagina o del blocco informativo nel DOM (Document Object Model / Modello a Oggetti del Documento).  
* **Intestazione:** Variante per intestazioni di livello secondario o di sezione, utile per contrassegnare l'inizio di una specifica macro-area all'interno del DOM (Document Object Model / Modello a Oggetti del Documento).  
* **Paragrafo con sottotitolo:** Struttura composta da un sottotitolo gerarchico seguito da uno o più blocchi di testo descrittivo esteso, per organizzare sezioni informative dettagliate nel DOM (Document Object Model / Modello a Oggetti del Documento).  
* **Paragrafo senza sottotitolo:** Blocco di testo continuo privo di intestazione introduttiva, impiegato per descrizioni dirette o contenuti testuali lineari nel DOM (Document Object Model / Modello a Oggetti del Documento).

## **4.3 Comportamento del testo (Text Truncation & Wrapping)**

Regole per la gestione del testo:

* **Truncation:** Il testo non deve mai essere troncato con i puntini di sospensione per evitare la perdita di informazioni critiche.  
* **Wrapping:** Quando supera la larghezza disponibile, va a capo automaticamente su più righe mantenendo un'interlinea adeguata.

## **4.4 Variante Dettaglio Servizio (Service Detail)**

* **`variante Service Detail`**: Variante ottimizzata per schede informative di servizio (ad es. Bollo Auto ACI). Gestisce layout con paragrafi introduttivi, riferimenti ad enti esterni e liste puntate di azioni disponibili per l'utente. Garantisce la corretta resa dei nodi di testo all'interno della struttura del DOM (Document Object Model / Modello a Oggetti del Documento).

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Missing items**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare per il rendering di uno stato di errore/vuoto (empty state) con eventuale Call to Action (CTA) per ricaricare la pagina.

```
---
id: component-missing-items
name: Missing items
category: Advice & Banners
version: 1.0.0
tags: [missing-items, empty-state, banner-error-state, pagamenti, cta, reload]
last_updated: 2026-11-17
---
```

# **Descrizione** 

Il componente `Missing items` (collegato a livello di codice a `BannerErrorState.tsx`) rappresenta uno stato di feedback/errore locale (empty state) utilizzato principalmente all’interno della sezione Pagamenti dell'app (es. nel caricamento dei metodi di pagamento o delle ricevute pagoPA). Informa l’utente che il caricamento dei dati è fallito o che la lista di elementi non è temporaneamente disponibile, offrendo contestualmente un'azione di ripristino o di retry (es. "Prova di nuovo"). Il componente viene renderizzato all'interno del DOM (Document Object Model / Modello a Oggetti del Documento) garantendo la continuità visiva della schermata ed evitando l'uso di schermate d'errore a tutto schermo (KO State) quando l'interruzione riguarda un singolo blocco di contenuto.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Gestione errori localizzati nei Pagamenti:** Utilizzare il componente per notificare il fallimento del caricamento di specifiche sezioni della vista Pagamenti (es. "Metodi di pagamento" o "Ricevute pagoPA") all'interno del DOM (Document Object Model / Modello a Oggetti del Documento).  
* **Azione di ripristino (Retry):** Fornire sempre una Call to Action (CTA) chiara (es. "Prova di nuovo") per permettere all'utente di ricaricare il blocco di contenuti senza dover aggiornare l'intera pagina o riavviare l'applicazione.  
* **Feedback contestuale chiaro:** Associare all'errore un testo descrittivo sintetico e inequivocabile sul problema riscontrato (es. "Il caricamento dei metodi è fallito.").  
* **Mantenimento della struttura di pagina:** Impiegare il componente all'interno di container o card esistenti per preservare il layout e la gerarchia informativa complessiva del DOM (Document Object Model / Modello a Oggetti del Documento).

## **Don't (Quando NON usare)**

* Non utilizzare il componente per errori bloccanti di intera applicazione o di processo critico; in tali casi utilizzare schermate dedicate di KO State o modali full-screen.  
* Non omettere la stringa di spiegazione dell'errore lasciando soltanto il pulsante di ricaricamento.  
* Non impiegare il componente per conferme d'ordine o esiti positivi (OK State).  
* Non inserire codice o tag HTML non sicuri all'interno dei testi di spiegazione per prevenire alterazioni non gestite nel rendering del DOM (Document Object Model / Modello a Oggetti del Documento).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nei file di progettazione Figma e nel componente Code Connect (`BannerErrorState.tsx`):

* **`label`**: Stringa di testo contenente il messaggio d'errore principale renderizzato nel DOM (Document Object Model / Modello a Oggetti del Documento) (es. "Il caricamento dei metodi è fallito."). Default: `"Il caricamento dei dati è fallito."`.  
* **`ctaLabel`**: Stringa contenente il testo dell'azione di retry (es. "Prova di nuovo"). Se non definita o vuota, l'azione di ricaricamento viene nascosta dal DOM (Document Object Model / Modello a Oggetti del Documento). Default: `"Prova di nuovo"`.  
* **`onRetry`**: Funzione di callback scatenata al tap/click sulla CTA per avviare il ricarico asincrono dei dati. Default: `undefined`.  
* **`icon`**: Specifica l'icona di avviso/errore da mostrare accanto al testo informativo per rafforzare visivamente lo stato di errore. Default: `"warning/error"`.

# **4\. Stati e varianti**

## **4.1 Stati Tipografici ed Elementi Supportati**

Il componente gestisce i seguenti elementi e stati di formattazione nel DOM (Document Object Model / Modello a Oggetti del Documento):

* **Stato Default Error:** Visualizzazione del testo informativo di errore affiancato dall'icona rappresentativa all'interno del nodo DOM (Document Object Model / Modello a Oggetti del Documento).  
* **Stato con CTA di Ricarico:** Presenza del pulsante d'azione interattivo (variante text/link o button solid a seconda del contesto di layout nei Pagamenti) per consentire il retry rapido.  
* **Stato Loading/Retrying:** Durante l'esecuzione di `onRetry`, la CTA o l'intero blocco nel DOM (Document Object Model / Modello a Oggetti del Documento) può mostrare uno spinner temporaneo di caricamento in attesa della risposta di rete.  
* **Stato Nascosto (Resolved):** Al buon esito del ricaricamento dati, il componente si smonta dal DOM (Document Object Model / Modello a Oggetti del Documento) lasciando il posto ai contenuti caricati con successo.

## **4.2 Varianti del componente**

Di seguito sono descritte le principali varianti supportate per la gestione dell'empty state d'errore all'interno della sezione Pagamenti nel DOM (Document Object Model / Modello a Oggetti del Documento):

* **Standard (Con CTA):** Variante principale impiegata nei blocchi Metodi di pagamento e Ricevute pagoPA, che include la spiegazione dell'errore e la CTA "Prova di nuovo".  
* **Informative (Senza CTA):** Variante puramente informativa utilizzata quando il recupero delle informazioni non è immediatamente eseguibile dall'utente e non richiede un'azione di retry diretta.  
* **Compact / Inline:** Layout ridotto destinato a contenitori stretti o elementi di lista in cui la visualizzazione spaziale deve integrarsi in maniera fluida senza rompere il flusso della pagina nel DOM (Document Object Model / Modello a Oggetti del Documento).

## **4.3 Comportamento del testo (Text Truncation & Wrapping)**

Regole per la gestione del testo e del layout del componente nel DOM (Document Object Model / Modello a Oggetti del Documento):

* **Truncation:** Il testo non deve mai essere troncato con i puntini di sospensione per evitare la perdita di informazioni critiche.  
* **Wrapping:** Quando supera la larghezza disponibile, va a capo automaticamente su più righe mantenendo un'interlinea adeguata.

## **4.4 Variante per la Sezione Pagamenti**

* **`variante Pagamenti Error State`**: Variante specifica configurata per i blocchi card e liste della sezione Pagamenti (es. caricamento fallito dei metodi di pagamento o delle ricevute). Garantisce l'integrazione nativa del feedback visivo d'errore e della relativa CTA nel DOM (Document Object Model / Modello a Oggetti del Documento), senza disorientare l'utente o nascondere gli altri elementi operativi della pagina.

# **5\. Accessibilità (A11y)**

**5.1 Semantica, Screen Reader e Ordine di Lettura**

* Icona Decorativa: L'icona triangolare di avviso posizionata sopra il testo DEVE essere nascosta alle tecnologie assistive (accessibilityElementsHidden={true} su iOS / importantForAccessibility="no" su Android), poiché il messaggio testuale esprime già chiaramente la natura dell'errore. Non deve ricevere il focus.  
* Ordine di Focus (Reading Order): Gli screen reader DEVONO attraversare gli elementi interni in ordine strettamente sequenziale dall'alto verso il basso:  
1. Messaggio di stato/errore (es. "Il caricamento dei metodi è fallito.") — Ruolo: testo (Text).  
2. Call to Action (es. "Prova di nuovo") — Ruolo interattivo distinto: Button.  
   1. Stato di Ricaricamento (Loading): Quando l'utente attiva la CTA "Prova di nuovo" e parte il tentativo di ricaricamento, esporre lo stato di attesa tramite accessibilityState={{ busy: true, disabled: true }} (o annunciare "Caricamento in corso" tramite AccessibilityInfo.announceForAccessibility) inibendo tocchi multipli.  
   2. Esito del Ricaricamento (Annuncio Dinamico): Se il nuovo tentativo fallisce nuovamente o carica i dati con successo, comunicare l'esito allo screen reader tramite AccessibilityInfo.announceForAccessibility senza far perdere l'orientamento all'utente.

**5.2 Contenuti e Disambiguazione di Contesto**

* Etichette CTA Contestuali (Label in Name \- WCAG 2.5.3): Quando il componente Missing items viene utilizzato più volte nella stessa schermata (es. per sezioni diverse come "Metodi di pagamento" e "Ricevute pagoPA"), l'etichetta visiva può restare sintetica ("Prova di nuovo"), ma la accessibilityLabel del pulsante DEVE essere arricchita programmaticamente con il contesto della sezione (es. "Prova di nuovo a caricare i metodi di pagamento"), mantenendo il testo visibile all'interno del nome accessibile.  
* Messaggi Chiari e Specifici: Il testo del messaggio deve indicare con precisione quale contenuto o sezione non è stato caricato, evitando messaggi generici come "Errore" o "Qualcosa è andato storto" 

# **6\. Content**

# **Search Input**

Quando usarlo, proprietà, varianti, comportamento ed errori da evitare per il componente Search Input (searchbar).

```
---
id: component-search-input
name: Search Input
category: Inputs & Controls
version: 1.0.0
tags: [search, searchbar, input, text-field, filter]
last_updated: 2026-11-03
---
```

# **Descrizione** 

Il componente Search Input (searchbar) consente agli utenti di inserire parole chiave per individuare rapidamente contenuti, messaggi o dati all'interno dell'applicazione. Si compone di un campo di testo per l'inserimento dei termini di ricerca, un'icona d'indicazione (lente di ingrandimento o freccia indietro), un pulsante di cancellazione rapida del testo ("X") e un'azione esplicita di annullamento ("Annulla") per uscire dallo stato di ricerca. Il componente garantisce la corretta sincronizzazione visiva ed interattiva all'interno del DOM (Document Object Model).

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Comportamento di Ricerca:** Mantenere il comportamento di ricerca coerente seguendo la logica as-is.  
* **Visualizzazione Icona di Cancellazione (X):** Mostrare l'icona "X" esclusivamente quando nel campo di ricerca è presente almeno un carattere digitato dall'utente.  
* **Azione dell'Icona di Cancellazione (X):** Utilizzare l'icona "X" per cancellare immediatamente l'intera chiave di ricerca digitata, sia durante la fase di digitazione (typing) sia a digitazione completata.  
* **Azione del Pulsante Annulla:** Configurare il pulsante o l'azione "Annulla" per interrompere la sessione di ricerca e riportare l'utente alla pagina o vista di provenienza.

## **Don't (Quando NON usare)**

* Non mostrare l'icona di cancellazione "X" quando il campo di testo è completamente vuoto o privo di caratteri inseriti dall'utente.  
* Non utilizzare il pulsante "Annulla" come semplice pulizia del testo, ma esclusivamente per abbandonare la ricerca e tornare al contesto precedente.  
* Non alterare o deviare dalle logiche di ricerca consolidate nel modello as-is dell'applicazione.

# **3\. Proprietà (Figma / Code Connect Props)**

Il comportamento e l'aspetto visivo del componente Search Input sono controllati dalle seguenti proprietà:

* **`placeholder`**: Definisce il testo guida mostrato quando il campo di ricerca è vuoto. Default: `"Cerca nei messaggi"` o `"Inserisci testo"`.  
* **`value`**: Rappresenta la stringa di testo inserita dall'utente nel campo di input.  
* **`showClearButton`**: Valore booleano che controlla la visibilità dell'icona di cancellazione "X". Impostato automaticamente su `true` quando `value` contiene uno o più caratteri.  
* **`showCancelButton`**: Valore booleano che determina la presenza e visualizzazione dell'azione "Annulla" accanto al campo di input.  
* **`disabled`**: Disabilita l'interazione con il campo di input e ne rende opaco l'aspetto visivo nel DOM (Document Object Model). Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stati dell'Header**

Il componente Search Input supporta i seguenti stati visivi e di interazione:

* **Empty / Idle:** Campo di ricerca privo di testo con placeholder visibile e nessuna icona "X" di cancellazione.  
* **Typing / Inserimento:** Stato attivo durante la digitazione con cursore visibile, icona "X" attiva per la pulizia del testo e risultati parziali.  
* **Completed / Inserito:** Testo di ricerca completo immesso nel campo con icona "X" mantenuta per permettere un ripristino rapido.  
* **Focused:** Stato di selezione attiva del campo con evidenziazione del bordo o focus-ring conforme alle specifiche visive.

## **4.2 Variante Search Input New Page**

La variante Search Input New Page viene utilizzata per gestire la ricerca all'interno di una pagina interamente dedicata. Presenta un'icona di freccia indietro ("←") per la navigazione al posto dell'icona standard di ingrandimento e gestisce le transizioni di stato all'interno del DOM (Document Object Model) durante l'esperienza di ricerca:

* **Empty / Idle:** Mostra l'icona della freccia indietro ("←") e il testo guida di placeholder, senza l'icona "X" di cancellazione.  
* **Typing / Inserimento:** Stato attivo durante la digitazione con cursore e icona "X" visibili per la pulizia immediata del testo immesso.  
* **Completed / Inserito:** Testo di ricerca completo con l'icona "X" per consentire il ripristino o la modifica rapida dei termini cercati.

# **5\. Accessibilità (A11y)**

**5.1 Contrasto, Ridimensionamento e Spaziatura Minima**

* Contrasto del Placeholder e dei Testi: Sia il testo digitato sia il testo di placeholder (es. "Cerca nei messaggi", "Inserisci testo") DEVONO rispettare il rapporto di contrasto minimo di 4.5:1 rispetto allo sfondo del campo (evitare token grigi con contrasto inferiore a 4.5:1). Le icone funzionali (lente di ingrandimento, icona "X", freccia indietro) devono garantire almeno 3.0:1.

* Touch Target e Spaziatura Minima tra Controlli:  
  * L'area del campo di input, il pulsante di cancellazione ("X"), il pulsante "Annulla" (variante Searchbar in page) e il pulsante Indietro (variante Searchbar in new page) DEVONO garantire ciascuno un'area di tocco minima di 44x44pt (iOS) / 48x48dp (Android).  
  * Garantire una distanza minima di sicurezza di almeno 8pt/dp tra i target adiacenti (in particolare tra il pulsante "X" interno al campo e l'azione esterna "Annulla", e tra la freccia Indietro e il bordo sinistro del campo) per evitare attivazioni accidentali.

**5.2 Semantica, Screen Reader e Ordine di Lettura**

* Ruolo e Etichetta del Campo (Search): Il campo di input deve essere esposto nativamente come campo di ricerca (accessibilityRole="search" / searchbox) con una accessibilityLabel esplicita (es. "Cerca nei messaggi"), anche quando il placeholder scompare durante la digitazione.  
* Icona Lente Decorativa: L'icona della lente di ingrandimento interna a sinistra DEVE essere nascosta allo screen reader (accessibilityElementsHidden={true} / importantForAccessibility="no") poiché ridondante rispetto al ruolo e all'etichetta del campo.  
* Pulsante di Cancellazione ("X"):  
  * Nascosto all'albero di accessibilità quando il campo è vuoto.  
  * Quando visibile (almeno 1 carattere digitato), deve avere ruolo Button e accessibilityLabel esplicita ("Cancella testo di ricerca" o "Svuota campo di ricerca"), annunciando all'attivazione che il campo è stato svuotato e mantenendo il focus sul campo di testo.  
* Ordine di Focus (Reading Order):  
  * Variante Searchbar in page: 1\. Campo di ricerca \-\> 2\. Pulsante "X" (se presente) \-\> 3\. Pulsante "Annulla" (ruolo Button, accessibilityLabel: "Annulla ricerca e torna indietro").  
  * Variante Searchbar in new page: 1\. Pulsante Indietro (ruolo Button, accessibilityLabel: "Torna indietro") \-\> 2\. Campo di ricerca \-\> 3\. Pulsante "X" (se presente).

**5.3 Comportamento Tastiera e Feedback Risultati**

* Azione Tastiera Virtuale: Impostare il tasto di conferma della tastiera di sistema su "Cerca" (returnKeyType="search") per consentire l'avvio della ricerca senza dover toccare altri elementi.  
* Annuncio Risultati Dinamici: Quando la digitazione filtra dinamicamente una lista sottostante, annunciare in modo non invasivo l'esito tramite AccessibilityInfo.announceForAccessibility (es. "3 risultati trovati" oppure "Nessun risultato trovato"). 

# **6\. Content**

# **Tab Navigation**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare.

```
---
id: component-tab-navigation
name: Tab Navigation
category: Navigation
version: 1.0.0
tags: [tab navigation, tab single item, tab, navigation, container]
last_updated: 2026-11-03
---
```

# **Descrizione**

Il componente Tab Navigation consente di organizzare la navigazione tra viste o sezioni correlate all'interno della stessa schermata, permettendo all'utente di passare rapidamente da un sotto-insieme di contenuti all'altro senza modificare il contesto generale della pagina. Ciascun elemento componente ("Tab Item") agisce come nodo interattivo all'interno del DOM (Document Object Model). A differenza dei filtri a chip, la Tab Navigation rappresenta una struttura di navigazione mutuamente esclusiva ed esaustiva: vi deve sempre necessariamente essere un unico elemento "attivo" (selezionato) alla volta.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Parola singola e breve:** Prediligere sempre per ciascuna etichetta (Label) del Tab Item una singola parola breve e descrittiva per garantire la massima scansionabilità e prevenire problemi di spazio visivo.  
* **Elemento attivo obbligatorio:** Garantire che ci sia sempre necessariamente un unico elemento Tab Item nello stato "Selected" (attivo) in ogni momento.  
* **Contenuti omogenei:** Utilizzare le Tab per alternare tra viste dello stesso livello gerarchico e concettualmente correlate.  
* **Coerenza visiva dell'icona:** Utilizzare la variante di icona "Filled" esclusivamente quando lo stato del Tab Item è "Selected", se disponibile nella libreria di icone.  
* **Numero massimo raccomandato di Tab Item:** Limitare il numero di elementi a un massimo di 4-5 tab per gruppo per garantire una buona leggibilità e prevenire un eccessivo scorrimento orizzontale o problemi di layout nel DOM (Document Object Model).  
* **Numero minimo di Tab Item:** Prevedere sempre almeno 2 elementi Tab Item per gruppo, poiché un numero inferiore non giustificherebbe la presenza di una struttura di navigazione a tab tra viste alternative nel DOM (Document Object Model).

## **Don't (Quando NON usare)**

* Non utilizzare la Tab Navigation per attività di filtraggio dinamico multi-selezione o deselezionabile (per cui vanno invece usati i Chip di filtro).  
* Non lasciare la Tab Navigation in uno stato senza alcun elemento selezionato.  
* Non inserire etichette multilinea o frasi lunghe all'interno dei Tab Item.  
* Non mescolare stili di icone disomogenei all'interno della stessa barra di navigazione a tab nel DOM (Document Object Model).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice (formattate esclusivamente via bullet points):

* **`label`**: Testo esplicativo del Tab Item. Deve prediligere una parola singola e breve. Default: "Label".  
* **`selected`**: Stato di selezione del Tab Item. Se true, attiva lo stato visivo evidenziato e sostituisce l'icona con la variante "Filled" (se presente). Default: false.  
* **`icon`**: Icona opzionale integrata nel Tab Item. Se lo stato è "Selected" e l'icona possiede una variante "Filled", viene mostrata quest'ultima. Default: null / none.  
* **`badgeCount`**: Indicatore numerico opzionale per mostrare notifica o conteggio elementi associati al tab. Default: null.  
* **`disabled`**: Disabilita l'interazione con il Tab Item e modifica la resa visiva a livello di nodo nel DOM (Document Object Model). Default: false.

# **4\. Stati e varianti**

## **4.1 Stati del Tab Item**

* **Default (Unselected):** Stato a riposo non attivo. Visualizza il testo con contrasto standard e l'icona in variante linea/outlined.  
* **Hover / Focus:** Evidenziazione visiva di interazione con focus-ring accessibile sul nodo del DOM (Document Object Model).  
* **Selected (Active):** Stato attivo e selezionato. Visualizza l'indicatore di selezione (bordo/sfondo evidenziato) e mostra l'icona in variante "Filled" (se disponibile).  
* **Disabled:** Disabilitazione visiva e di interazione dell'elemento nel DOM (Document Object Model).

## **4.2 Comportamento e Regole di Selezione**

* **Mutua Esclusività:** La selezione di un Tab Item deseleziona automaticamente il tab precedentemente attivo.  
* **Persistenza dell'Elemento Attivo:** Non è possibile deselezionare un tab attivo senza selezionarne un altro (nessuno stato "all unselected").  
* **Text Truncation & Wrapping:** Le etichette dei tab devono consistere in parole brevi. Se lo spazio della vista è ridotto, il testo non va a capo ma viene gestito con scorrimento orizzontale della barra di tab.

## **4.3 Varianti di Layout e Icone**

* **Tab Item solo Testo:** Variante composta da sola etichetta testuale (parola singola e breve).  
* **Tab Item Testo \+ Icona:** Variante composta da etichetta testuale e icona; l'icona commuta alla versione "Filled" solo quando lo stato è "Selected".  
* **Tab Item con Badge:** Variante che include un conteggio o punto di notifica visivo.

# **5\. Accessibilità (A11y)**

**5.1 Touch Target, Ridimensionamento e Contrasto**

* Area di Tocco e Spaziatura Minima: Ogni singola tab (Tab single element) DEVE garantire un'area cliccabile minima di 44pt di altezza su iOS / 48dp su Android, mantenendo una spaziatura minima di almeno 8pt/dp tra una pillola e l'altra all'interno del Tab group per evitare selezioni accidentali.  
* Contrasto e Distinzione dello Stato (Contrast: No / Yes):  
  * Garantire un rapporto di contrasto minimo di 4.5:1 per il testo della label in entrambi gli stati (Selected: Yes e Selected: No) e su entrambe le varianti di sfondo (Contrast: No e Contrast: Yes).  
  * La tab selezionata (Selected: Yes) NON DEVE affidarsi solo al cambio di colore, ma distinguersi tramite riempimento/bordo della pillola e, se attiva l'icona (Show Icon: True), tramite cambio di stile dell'icona (es. outline \-\> filled).  
  * Gli elementi in stato Disabled: Yes devono mantenere una leggibilità visiva sufficiente pur essendo esclusi dall'interazione.

**5.2 Semantica, Screen Reader e Ordine di Lettura**

* Ruolo del Contenitore e delle Singole Tab:  
  * Il contenitore Tab group deve essere esposto come gruppo di schede (accessibilityRole="tablist" su React Native / Android).  
  * Ogni Tab single element deve essere esposta come singolo nodo interattivo con ruolo tab (o button) e stato esplicito: accessibilityState={{ selected: true/false, disabled: true/false }}.  
* Icona Opzionale Decorativa (Show Icon: True): L'icona interna alla pillola a sinistra della label DEVE essere nascosta alle tecnologie assistive (accessibilityElementsHidden={true} / importantForAccessibility="no") poiché ridondante rispetto al testo della tab.  
* Ordine di Focus (Reading Order) e Annuncio di Posizione:  
  * Gli screen reader DEVONO navigare le tab in ordine sequenziale da sinistra a destra (1 \-\> 2 \-\> 3 \-\> ...).  
  * Lo screen reader deve annunciare nell'ordine: Etichetta della tab (es. "Inquadra"), Ruolo ("scheda" / "pulsante"), Stato ("selezionato" / "non selezionato" / "non disponibile") e posizione relativa nel gruppo (es. "1 di 3").  
  * Nelle varianti scorrevoli (N.Elements: 3+), lo swipe dello screen reader verso le tab parzialmente fuori schermo deve far scorrere automaticamente il contenitore per portare la tab focalizzata completamente in vista (Focus Not Obscured \- WCAG 2.4.11).

**5.3 Contenuti e Localizzazione**

* Etichette Brevi e Univoche: Utilizzare etichette sintetiche (1-2 parole) che descrivano chiaramente la vista o la modalità attivata (es. "Inquadra", "Carica", "Digita"), tenendo conto dell'espansione del testo fino al 30-50% in fase di traduzione.  
* Cambio di Contenuto Prevedibile: La selezione di una tab deve aggiornare esclusivamente il pannello/contenuto associato nella schermata corrente senza provocare cambi improvvisi di contesto o navigazioni inattese. 

# **6\. Content**

# **Text Input**

Linee guida sull'uso, governance, proprietà, varianti e comportamenti dei campi di inserimento testo.

```
---
id: component-text-input
name: Text Input
category: Inputs & Forms
version: 1.0.0
tags: [text-input, form, input, password, validation, haptics]
last_updated: 2026-11-03
---
```

# **Descrizione** 

Il componente Text Input consente all'utente di inserire ed modificare valori di testo lineari all'interno di una maschera d'inserimento o form. Supporta diverse modalità visive, varianti funzionali con gestione di maschere (es. Codice avviso), campi protetti per password con opzione di visibilità e contatori di caratteri espliciti (es. 0/18). Risulta pienamente integrato con l'albero del DOM (Document Object Model) per la gestione dinamica degli stati di validazione e il controllo del focus.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Obbligatorietà di Default:** I campi nei form sono considerati obbligatori di default.  
* **Campi Opzionali:** Segnalare chiaramente i campi non obbligatori aggiungendo il placeholder o la dicitura "(facoltativo)" nell'etichetta/label.  
* **Validazione Singola Input:** Mostrare il feedback di errore o successo al momento dell'evento di blur (perdita del focus dall'elemento nel DOM (Document Object Model)).  
* **Validazione Form Multi-Input:** Scatenare la validazione e la visualizzazione degli errori complessivi esclusivamente sull'evento di tap/click sul pulsante di conferma del form.  
* **Feedback Aptico:** Utilizzare il feedback haptic (iOS notificationSuccess/notificationError) per rafforzare l'esito delle azioni in modo opzionale.

## **Don't (Quando NON usare)**

* Non inserire avvisi o messaggi generali del tipo "Tutti i campi sono obbligatori" all'inizio o all'interno del form.  
* Non validare un form con più campi contestualmente all'interazione su ciascun singolo input prima dell'invio.  
* Non omettere l'indicazione del limite di caratteri (es. 0/18) nei campi con restrizione di lunghezza.  
* Non utilizzare maschere di formattazione non coerenti con il dato richiesto (es. spaziatura "0000 0017 8484 2692 50" vs "0000 001784842692 50").

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`label`**: Etichetta del campo (es. "Codice avviso"). Default: `"Codice avviso"`.  
* **`helperText`**: Testo d'aiuto posizionato al di sotto dell'input. Default: `"Helper text"`.  
* **`counter`**: Contatore di caratteri nel formato corrente/massimo (es. "0/18"). Default: `"0/18"`.  
* **`type`**: Tipo di input inserito. Valori: `text`, `password`. Default: `"text"`.  
* **`hapticFeedback`**: Attiva il feedback tattile/aptico all'interazione o validazione (es. Success / Error). Default: `false`.

# **4\. Stati e varianti**

## **4.1 Stati dell'Header**

Gli stati del componente sono riflessi strutturalmente nel DOM (Document Object Model) ed includono:

* **Default/Inattivo:** Campo vuoto o precompilato pronto per l'interazione.  
* **Focus/Active:** Campo in corso di digitazione con cursore attivo.  
* **Errore/Validation:** Bordo/icona di avviso identificativa ("\!") e messaggio relativo nel testo di supporto.  
* **Successo:** Stato di input valido con opzione di riscontro visivo o feedback aptico (Feedback Success).

## **4.2 Comportamento del testo (Text Truncation & Wrapping)**

Regole per la gestione del testo:

* **Truncation:** Il testo non deve mai essere troncato con i puntini di sospensione per evitare la perdita di informazioni critiche.  
* **Wrapping:** Quando supera la larghezza disponibile, va a capo automaticamente su più righe mantenendo un'interlinea adeguata.

## **4.3 Variante Password e Maschere**

* **Variante Password:** Nasconde i caratteri sostituendoli con elementi oscurati ("............"), offrendo l'icona “Icon Eye” per mostrare/nascondere il contenuto in chiaro nel DOM (Document Object Model).  
* **Maschera di Formattazione:** Consente la formattazione automatica dei caratteri inseriti (es. "0000 001784842692 50" o "0000 0017 8484 2692 50") per facilitare la lettura e la verifica.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Toast Notification**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare.

```
---
id: component-toast-notification
name: Toast Notification
category: Feedback & Status
version: 1.0.0
tags: [toast, notification, feedback, status, alert, snackbar]
last_updated: 2026-11-03
---
```

# **Descrizione** 

Il componente Toast Notification fornisce un messaggio di feedback temporaneo e non interruttivo in risposta a un'azione svolta dall'utente o a un evento di sistema. Viene visualizzato in sovrapposizione all'interfaccia principale senza bloccare l'operatività dell'utente e scompare automaticamente dopo un intervallo temporale predefinito oppure tramite interazione manuale. Il componente viene inserito nel DOM (Document Object Model / Modello a Oggetti del Documento) dinamicamente per garantire una comunicazione immediata e contestuale dello stato di avanzamento o di errore.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Feedback temporaneo:** Comunicare l'esito di un'azione asincrona o di background (es. salvataggio completato, invio dati, errore di connessione).  
* **Posizionamento corretto:** Fissare la notifica a 24 px dal margine superiore della viewport o direttamente sotto eventuali elementi di navigazione o header di tipo sticky.  
* **Contrasto elevato:** Utilizzare uno stroke perimetrale a contrasto per preservare la leggibilità e la distinzione visiva in caso di sovrapposizione con componenti di tipo Alert o sfondi complessi.  
* **Criteri di annullamento:** Consentire l'eliminazione rapida manuale tramite gesto di swipe da destra verso sinistra o tramite l'interazione con l'azione o icona di chiusura.

## **Don't (Quando NON usare)**

* Non utilizzare Toast Notification per messaggi critici o bloccanti che richiedono un’azione confermativa o immediata ed esplicita da parte dell'utente; in questi casi, fare riferimento al componente Alert o ai componenti di modale bloccante (Dialog/Modal).  
* Non accumulare nel DOM (Document Object Model / Modello a Oggetti del Documento) più di 3 notifiche contemporaneamente per evitare l'affollamento della viewport.  
* Non includere testi lunghi o contenuti complessi che richiedono uno scorrimento all'interno del pannello di notifica.  
* Non rimuovere l'indicatore visivo di stato o il contorno a contrasto necessario per la separazione visiva.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`message`**: Testo descrittivo contenuto all'interno della notifica. Default: `"Messaggio"`.  
* **`status`**: Definisce lo stato e lo stile visivo. Valori: `success`, `error`, `warning`, `info`, `neutral`. Default: `"neutral"`.  
* **`duration`**: Tempo di permanenza in millisecondi prima della scomparsa automatica dal DOM (Document Object Model / Modello a Oggetti del Documento). Default: `4000`.  
* **`hapticFeedback`**: Tipo di risposta aptica attivata su dispositivi mobili supportati. Valori: `notificationSuccess`, `notificationError`, `notificationWarning`, `impactMedium`. Default: `null`.

# **4\. Stati e varianti**

## **4.1 Varianti di Status**

Il componente Toast Notification supporta 5 varianti cromatiche e funzionali di stato per comunicare contestualmente il tipo di aggiornamento:

* **Success:** Indica il buon fine di un'operazione o di un processo asincrono. Associata a feedback aptico iOS `notificationSuccess`.  
* **Error:** Segnala un errore critico o il fallimento dell'operazione. Associata a feedback aptico iOS `notificationError`.  
* **Warning:** Evidenzia un avviso non bloccante o una situazione che richiede attenzione. Associata a feedback aptico iOS `notificationWarning`.  
* **Info:** Fornisce un'informazione di servizio neutrale o di aggiornamento generale senza carattere di urgenza.  
* **Neutral:** Notifica generica priva di connotazione di stato, utilizzata per comunicazioni standard o interazioni generiche. Associata a feedback aptico iOS `impactMedium`.

## **4.2 Posizionamento e Sovrapposizione**

Il componente adotta un layout rigoroso per garantire la massima visibilità:

* **Offset dall'alto:** La notifica viene posizionata ad una distanza fissa di 24 px rispetto al bordo superiore della viewport oppure subito al di sotto di header ed elementi sticky presenti nell'interfaccia.  
* **Stroke a contrasto:** Per impedire problemi di leggibilità o di confondibilità visiva qualora la notifica vada a sovrapporsi ad un componente Alert o a uno sfondo ad alto contrasto, il contenitore integra uno stroke perimetrale di separazione.

* ## **4.3 Interazione di Swipe e Eliminazione**

* **Gesto di Swipe:** Su tutti i dispositivi touch, l'utente può scorrere la notifica da destra verso sinistra per rimuoverla ed eliminarla immediatamente dal DOM (Document Object Model / Modello a Oggetti del Documento) prima dello scadere del timer automatico.

## **4.4 Gestione della Lettura Prioritaria per Screen Reader**

* **Priorità di Annuncio:** L'inserimento della notifica nel DOM (Document Object Model / Modello a Oggetti del Documento) fa scattare l'interruzione immediata o l'accodamento dell'annuncio dello screen reader in base alla gravità dello stato, garantendo che gli avvisi critici vengano letti prioritariamente.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Bottom Sheet**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare.

```
---
id: component-bottom-sheet
name: Bottom Sheet
category: Overlay & Navigation
version: 1.0.0
tags: [bottom-sheet, overlay, modal, navigation, container]
last_updated: 2026-11-03
---
```

# **Descrizione** 

Il componente Bottom Sheet consiste in un pannello ancorato alla parte inferiore dello schermo che si sovrappone al contenuto principale dell'applicazione. Viene utilizzato per presentare contenuti contestuali, opzioni di navigazione o brevi approfondimenti senza costringere l'utente a cambiare pagina. All'interno dell'albero del DOM (Document Object Model), viene renderizzato come un livello sovrapposto (overlay) per garantire una gestione flessibile della gerarchia visiva e dell'interazione.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Variante Editoriale:** Utilizzare per mostrare brevi approfondimenti ed elementi informativi direttamente all'interno della pagina corrente, senza interrompere drasticamente il flusso operativo e senza richiedere azioni obbligatorie da parte dell'utente.  
* **Variante Navigazionale:** Utilizzare per opzioni di disambiguazione, scelta rapida o selezione di percorsi alternativi in mobilità.  
* **Contenuti sintetici:** Includere informazioni essenziali e azioni chiare per evitare uno scorrimento eccessivo all'interno del pannello.  
* **Adattabilità mobile:** Privilegiare l'uso su dispositivi mobili per facilitare l'interazione con una sola mano nell'interfaccia utente.

## **Don't (Quando NON usare)**

* Non utilizzare il Bottom Sheet per processi complessi e multi-step che richiedono un'ampia compilazione di dati o una navigazione profonda nel DOM (Document Object Model).  
* Non sovrapporre più Bottom Sheet contemporaneamente per evitare confusione nell'albero dei componenti e nella gestione degli stati.  
* Non sostituire le modali critiche di confermazione o errore bloccante con un Bottom Sheet di tipo editoriale.  
* Non nascondere le opzioni di chiusura esplicita qualora il contenuto richieda un'azione consapevole.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Bottom Sheet nelle librerie di design e nel codice sono definite come segue:

* **`title`**: Testo dell'intestazione principale del Bottom Sheet. Definisce il titolo del pannello visibile in alto. Default: `"Titolo del Bottom sheet"`.  
* **`variant`**: Determina lo scopo funzionale del componente. Valori possibili: `editorial` (per approfondimenti e testo) oppure `navigation` (per liste di opzioni o azioni di disambiguazione). Default: `"editorial"`.  
* **`isOpen`**: Stato booleano di visibilità. Se `true`, il pannello viene renderizzato nel DOM (Document Object Model) ed è visibile a schermo. Default: `false`.  
* **`showOverlay`**: Controlla la presenza dello sfondo scuro (backdrop) dietro al pannello per bloccare le interazioni esterne. Default: `true`.  
* **`dismissible`**: Abilita la chiusura rapida tramite interazione con l'overlay o gesture di scorrimento verso il basso. Default: `true`.

# **4\. Stati e varianti**

## **4.1 Stati dell'Header**

Il componente gestisce comportamenti dinamici, risposte responsive ed eventi di chiusura standardizzati:

## **4.1 Regole di Chiusura**

* **Tap sull'overlay:** Se la proprietà dismissible è attiva, toccare l'area di sfondo oscurata determina l'immediata smontatura o occultamento del componente nel DOM (Document Object Model).  
* **Gesture di Swipe Down:** L'utente può trascinare il pannello verso il basso per chiuderlo. Il comportamento rispetta le convenzioni native del sistema operativo (es. trascinamento tramite drag handle su iOS o gesture standard su Android).  
* 4.2 Regole Responsive e Adattamento

## **4.2 Comportamento del testo (Text Truncation & Wrapping)**

* **Dispositivi Mobile:** Il Bottom Sheet occupa il 100% della larghezza della viewport, aderendo ai margini inferiori dello schermo.  
* **Dispositivi Desktop / Tablet:** Per evitare un'estensione eccessiva e poco leggibile del testo, la larghezza del pannello viene limitata (max-width) e il componente viene centrato o trasformato visivamente in una modale ancorata nel DOM (Document Object Model).

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Full screen modal**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare.

```
---
id: component-full-screen-modal
name: Full Screen Modal
category: Overlay & Navigation
version: 1.0.0
tags: [full-screen-modal, overlay, modal, flow, form, navigation, container]
last_updated: 2026-11-03
---
```

# **Descrizione** 

Il componente Full Screen Modal (Modale a schermo intero) è un elemento contenitore di primo livello che copre interamente la viewport del dispositivo. Viene utilizzato per focalizzare l'attenzione dell'utente su flussi operativi complessi, form articolati, procedure multi-step o configurazioni estese, isolando temporaneamente l'utente dal contesto dell'applicazione sottostante. A differenza del Bottom Sheet (che si aggancia alla parte inferiore dello schermo per interazioni rapide o contenuti informativi brevi), la Full Screen Modal trasforma temporaneamente l'interfaccia in uno spazio di lavoro dedicato. All'interno dell'albero del DOM (Document Object Model), la modale a schermo intero viene renderizzata come un livello sovrapposto (overlay) globale con z-index elevato per bloccare l'interazione con l'interfaccia sottostante.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Flussi di inserimento dati complessi:** Utilizzare per la compilazione di form estesi, wizard guidati o procedure multi-step che richiedono grande spazio verticale e orizzontale.  
* **Isolamento del task:** Impiegare quando occorre evitare distrazioni visive dall'interfaccia sottostante e garantire che l'utente porti a termine o annulli esplicitamente il flusso in corso.  
* **Gestione di tabelle ed editor estesi:** Utilizzare per la modifica di dati complessi, anteprime di documenti a schermo intero o editor di configurazione.  
* **Esperienza cross-device omogenea:** Adottare quando è necessario mantenere un layout coerente sia su dispositivi mobile sia su desktop per task operativi importanti.  
* **Flussi di navigazione browser in-app:** Utilizzare per la gestione di flussi browser in-app, garantendo un'esperienza integrata e protetta senza abbandonare app IO.

## **Don't (Quando NON usare)**

* Non utilizzare la Full Screen Modal per brevi conferme, avvisi informativi semplici o azioni rapide (utilizzare modali standard o toast notification).  
* Non utilizzare per contenuti di consultazione rapida o approfondimenti editoriali veloci (per i quali è preferibile il Bottom Sheet su mobile o un drawer/popover su desktop).  
* Non nidificare una Full Screen Modal all'interno di un'altra modale nel DOM (Document Object Model) per evitare confusione nella gerarchia degli stati e nella gestione dei punti di ripristino.  
* Non omettere i pulsanti espliciti di chiusura (es. icona "X" o pulsante "Annulla") per consentire all'utente di abbandonare il flusso in qualsiasi momento.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Full Screen Modal nelle librerie di design e nel codice sono definite come segue:

* **`title`**: Stringa di testo visualizzata nell'header fisso della modale per identificare il flusso corrente. Default: `"Titolo Modale"`.  
* **`variant`**: Definisce la struttura funzionale del layout. Valori possibili: `default` (contenuto fisso o scorrevole singolo), `stepper` (per wizard a più passaggi con indicatore di progresso) oppure `split-view` (con pannello laterale di riepilogo). Default: `"default"`.  
* **`isOpen`**: Stato booleano di visibilità. Quando impostato su `true`, il componente viene renderizzato a schermo intero nel DOM (Document Object Model). Default: `false`.  
* **`stickyHeader`**: Se impostato su `true`, l'intestazione contenente titolo e pulsante di chiusura rimane bloccata in alto durante lo scorrimento del contenuto. Default: `true`.  
* **`stickyFooter`**: Se impostato su `true`, la barra delle azioni principali (es. "Salva", "Conferma", "Indietro") rimane fissa nella parte inferiore della viewport. Default: `true`.  
* **`preventUnsavedChanges`**: Se `true`, tenta di intercettare l'azione di chiusura per mostrare un dialogo di conferma in presenza di dati non salvati nel form. Default: `true`.

# **4\. Stati e varianti**

## **4.1 Struttura e Layout degli Stati**

La Full Screen Modal gestisce differenti stati visivi e configurazioni di layout in base alla fase del flusso lavorativo:

* **Stato Default (Single-page Form):** Presenta un header fisso con il titolo e l'azione di chiusura, un corpo centrale scorrevole e un footer fisso contenente le azioni primarie e secondarie.  
* **Stato Multi-step / Stepper:** Visualizza nell'header una barra di avanzamento o un indicatore numerato di passaggi per guidare l'utente attraverso le varie fasi del processo operativo.  
* **Stato Caricamento / Processing:** Disabilita temporaneamente i pulsanti di azione nel footer e mostra uno spinner o uno skeleton loader nel corpo centrale durante il salvataggio dei dati nel DOM (Document Object Model).

## **4.2 Regole di Chiusura ed Interazione**

* **Pulsante di Chiusura Esplicito:** La presenza dell'icona di chiusura (X) nell'header o del pulsante "Annulla" nel footer consente di distruggere l'istanza del componente nel DOM (Document Object Model).  
* **Gestione Modifiche Non Salvate:** Qualora l'utente abbia modificato i dati all'interno del form, il tentativo di chiusura innesca una richiesta di conferma “dialog” bloccante prima della rimozione dal DOM (Document Object Model).

## **4.3 Adattamento Responsive e Comportamento del Testo**

* **Dispositivi Mobile e Desktop:** A differenza del Bottom Sheet, la Full Screen Modal occupa sempre il 100% della larghezza e dell'altezza della viewport su tutti i breakpoint, garantendo la massima area di lavoro disponibile.  
* **Gestione del Testo e dei Form:** I titoli lunghi nell'header vengono troncati con punti di sospensione (ellipsis), mentre i campi di testo e i contenuti nel corpo della modale utilizzano l'andata a capo automatica (word-wrap) garantendo una leggibilità ottimale.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Button sticky bottom**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione delle azioni fisse in basso (sticky bottom/footer actions).

```
---
id: component-button-sticky-bottom
name: Button Sticky Bottom
category: Overlay & Navigation
version: 1.0.0
tags: [button-sticky-bottom, footer-actions, sticky-footer, primary-action, secondary-action, tertiary-action, overlay, navigation]
last_updated: 2026-11-10
---
```

# **Descrizione** 

Il componente Button Sticky Bottom (o Footer Actions) è una barra di azioni ancorata in modo permanente alla parte inferiore della viewport o del contenitore dell'interfaccia. Garantisce che le azioni principali di proseguimento, salvataggio o conferma rimangano costantemente visibili ed accessibili all'utente, indipendentemente dallo scorrimento dei contenuti retrostanti. A livello dell'albero del DOM (Document Object Model), viene posizionato come elemento con riposizionamento fisso/sticky e z-index elevato per sovrapporsi al contenuto scorrevole senza ostruire la leggibilità.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Flussi di compilazione e form lunghi:** Utilizzare nei flussi a schermata singola o multi-step in cui la chiamata all'azione primaria deve rimanere costantemente raggiungibile durante lo scorrimento.  
* **Gerarchia chiara delle azioni:** Disporre fino a un massimo di tre azioni distinte (Primary, Secondary, Tertiary) strutturate secondo il livello di importanza dell'operazione.  
* **Integrazione con tastiera virtuale:** Utilizzare nei layout mobile garantendo che l'area delle azioni si adatti correttamente al sollevamento della tastiera su schermo.  
* **Disposizione adattiva (Inline / Stacked):** Utilizzare il layout affiancato (Inline) solo su desktop per ottimizzare lo spazio verticale occupato e massimizzare l'area visibile dei contenuti. Su schermi mobile, adottare la disposizione impilata (Stacked) a tutta larghezza per garantire aree di tocco (touch target) sufficientemente ampie, evitare la sovrapposizione o il troncamento del testo e mantenere un'elevata leggibilità delle azioni.

## **Don't (Quando NON usare)**

* Non affollare la barra inferiore con più di 3 azioni contemporaneamente per evitare sovraccarico cognitivo e problemi di spaziatura visiva.  
* Non nascondere l'azione primaria (Primary) durante lo scorrimento se il completamento della schermata dipende direttamente da essa.  
* Non sovrapporre la barra sticky bottom ad altri elementi di navigazione fissi (come Bottom Navigation Bar) senza un opportuno offset di sicurezza nel DOM (Document Object Model).  
* Non utilizzare lo stile Primary per più di un pulsante all'interno del medesimo footer sticky.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Button Sticky Bottom nelle librerie di design e nel codice sono definite come segue:

* **`layout`**: Modalità di disposizione dei pulsanti nel footer. Valori possibili: `stacked` (pulsanti disposti uno sopra l'altro) o `inline` (pulsanti disposti uno fianco all'altro). Default: `"stacked"`.  
* **`primaryAction`**: Oggetto contenente etichetta e gestore evento dell'azione principale (pulsante Primary). Default: visibile.  
* **`secondaryAction`**: Oggetto facoltativo per l'azione secondaria (pulsante Secondary). Default: `null`.  
* **`tertiaryAction`**: Oggetto facoltativo per l'azione terziaria (pulsante Tertiary). Default: `null`.  
* **`buttonSize`**: Dimensione dei pulsanti all'interno del contenitore. Valori possibili: `default` o `medium`. Default: `"default"`.  
* **`isSticky`**: Stato booleano per attivare o disattivare il posizionamento fisso in basso nell'albero del DOM (Document Object Model). Default: `true`.

# **4\. Stati e varianti**

## **4.1 Struttura e Layout degli Stati**

Il componente supporta tre configurazioni principali del layout in base al numero di azioni e alla modalità di affiancamento:

* **Single Action (Primary):** Visualizza un unico pulsante ad alta priorità (Primary) a tutta larghezza per confermare o completare l'operazione corrente.  
* **Dual Action (Primary \+ Secondary):** Presenta l'azione principale (Primary) e una di supporto (Secondary). Può essere disposta verticalmente (Stacked) oppure affiancata (Inline / Medium).  
* **Triple Action (Primary \+ Secondary \+ Tertiary):** Combina un'azione principale, una secondaria e una terziaria disposte in ordine di importanza gerarchica.

## **4.2 Regole di Chiusura ed Interazione**

* **Ancoraggio alla viewport:** Il contenitore rimane bloccato nella parte inferiore dello schermo tramite posizionamento sticky/fixed nel DOM (Document Object Model).  
* **Interazione con la tastiera di sistema:** Alla comparsa della tastiera virtuale mobile, l'area delle azioni viene posizionata subito al di sopra di essa per mantenere accessibile l'invio del form.

## **4.3 Adattamento Responsive e Comportamento del Testo**

* **Layout Mobile vs Desktop:** Su schermi di ridotte dimensioni è raccomandata la configurazione Stacked a tutta larghezza, mentre su schermi più ampi è preferibile l'organizzazione Inline.  
* **Comportamento dei testi:** Le etichette dei pulsanti devono rimanere concise. In caso di ridimensionamento, il testo non deve andare a capo in modo anomalo né essere troncato.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Camera view**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione del componente di acquisizione visiva e scansione (Camera View).

```
---
id: component-camera-view
name: Camera View
category: Media & Input
version: 1.0.0
tags: [camera-view, scan, capture, overlay, dismiss-button, framing-guide, mobile-camera]
last_updated: 2026-11-10
---
```

# **Descrizione** 

Il componente Camera View gestisce l'interfaccia a schermo intero per l'acquisizione di immagini, documenti o la scansione di codici via fotocamera. Integra un livello overlay contenente i controlli principali di chiusura (pulsante "X"), un titolo o istruzione guida (es. "Inquadra") ed elementi visivi di delimitazione del frame di scansione. A livello dell'albero del DOM (Document Object Model / Modello a Oggetti del Documento), il viewfinder viene integrato tramite uno stream video locale sovrapposto dagli elementi di interfaccia ad alto z-index per facilitare l'inquadratura in tempo reale.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Scansione di codici o documenti:** Utilizzare nei flussi che richiedono la lettura automatica di codice QR/barcode o l'acquisizione guidata di documenti d'identità e ricevute.  
* **Controlli essenziali visibili:** Mantenere sempre visibile l'azione di chiusura/annullamento ("X") e un'istruzione chiara (es. "Inquadra") sovrapposte allo stream video.  
* **Gestione dei permessi:** Mostrare stati di caricamento o di richiesta permessi prima di inizializzare lo stream hardware della fotocamera.  
* **Indicatori d'inquadratura:** Fornire guide visive (angoli di rilevamento o bounding box) per guidare l'utente nel posizionamento del soggetto.

## **Don't (Quando NON usare)**

* Non ostruire l'area centrale del viewfinder con elementi grafici o barre opache che impediscano la visione del soggetto da inquadrare.  
* Non omettere il pulsante di chiusura esplicito ("X") per prevenire contesti di blocco dell'interfaccia o impossibilità di uscire dal flusso di fotocamera.  
* Non sovraccaricare l'overlay della fotocamera con azioni secondarie non pertinenti all'attività primaria di scansione o scatto.  
* Non inizializzare lo stream video senza verificare la presenza dei permessi di sistema nel DOM (Document Object Model / Modello a Oggetti del Documento).

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Camera View nelle librerie di design e nel codice sono definite come segue:

* **`title`**: Etichetta testuale di guida visibile nell'overlay superiore. Default: `"Inquadra"`.  
* **`showDismissButton`**: Booleano per controllare la visibilità del pulsante di chiusura ("X"). Default: `true`.  
* **`facingMode`**: Seleziona la fotocamera da attivare. Valori possibili: `"environment"` (posteriore) o `"user"` (frontale). Default: `"environment"`.  
* **`flashControl`**: Abilita il pulsante per l'attivazione/disattivazione del flash o torcia integrata. Default: `false`.  
* **`scanOverlayType`**: Definisce la maschera visiva di inquadratura. Valori: `"qr_code"`, `"document"`, `"none"`. Default: `"qr_code"`.  
* **`onDismiss`**: Callback invocata quando l'utente seleziona il pulsante di chiusura ("X").

# **4\. Stati e varianti**

## **4.1 Struttura e Layout degli Stati**

Il componente supporta diverse configurazioni di stato e modalità di interazione durante il ciclo di vita della fotocamera:

* **Active Viewfinder (Scansione attiva):** Stream video funzionante a pieno schermo con maschera di inquadratura e controlli sovrapposti.  
* **Permission Requested / Denied:** Stato visualizzato in mancanza dei permessi di accesso alla fotocamera, con indicazioni per abilitarla.  
* **Processing State:** Fase di elaborazione immediata al rilevamento del codice o all'acquisizione del frame.

## **4.2 Regole di Chiusura ed Interazione**

* **Gestione Chiusura:** La pressione del pulsante "X" interrompe immediatamente lo stream video nel DOM (Document Object Model / Modello a Oggetti del Documento) e rilascia le risorse hardware della fotocamera.  
* **Focus e Tap-to-Focus:** L'interazione con l'area video consente di ricalibrare la messa a fuoco e l'esposizione sul punto selezionato dall'utente.

## **4.3 Adattamento Responsive e Comportamento del Testo**

* **Adattamento Fullscreen:** L'area del viewfinder si adatta alla dimensione dello schermo mantenendo il rapporto d'aspetto dello stream senza distorsioni visive.  
* **Posizionamento Header Overlay:** Gli elementi di controllo superiori ("X" e titolo "Inquadra") rispettano le safe-area superiori dei dispositivi per evitare sovrapposizioni con la barra di stato.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Carousel**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione delle sequenze di schede e contenuti scorrevoli orizzontalmente (Carousel / Card Carousel).

```
---
id: component-carousel
name: Carousel
category: Layout & Navigation
version: 1.0.0
tags: [carousel, card-carousel, horizontal-scroll, slideshow, accessibility, image-rotator, swiper]
last_updated: 2026-11-10
---
```

# **Descrizione**

Il componente Carousel (o Card Carousel) è un contenitore di layout per lo scorrimento orizzontale di elementi omogenei (come schede di servizio, enti in evidenza o comunicazioni) all'interno di uno spazio verticale contenuto. All'interno dell'albero del DOM (Document Object Model), viene strutturato come una regione logica formata da una sequenza di diapositive/schede affiancate, gestita tramite proprietà di scroll-snapping o controlli d'interazione espliciti. Consente di presentare molteplici contenuti correlati riducendo l'ingombro iniziale della schermata e mantenendo al contempo un'elevata densità informativa.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Raggruppamento di schede omogenee:** Utilizzare per mostrare elementi visivi della stessa natura, quali Service Cards, Institution Cards o comunicazioni in evidenza.  
* **Ottimizzazione dello spazio verticale:** Utilizzare per consentire l'esplorazione di opzioni secondarie o in evidenza senza forzare un prolungato scorrimento verticale della pagina.  
* **Contenuti opzionali ed esplorativi:** Adottare quando gli elementi all'interno del carousel non sono bloccanti per l'esperienza dell'utente o per il completamento del flusso primario.  
* **Controlli visibili ed espliciti:** Fornire sempre indicatori visivi di paginazione/progressione e pulsanti prev/next o scorciatoie di navigazione visibili ed accessibili nel DOM (Document Object Model).

## **Don't (Quando NON usare)**

* Non utilizzare per la presentazione di molti documenti o dati critici: il componente non funziona in modo efficiente ed è sconsigliato in presenza di un numero elevato di elementi.  
* Non fare affidamento esclusivo sul carousel per trasmettere informazioni fondamentali o passaggi obbligatori di un flusso.  
* Non attivare l'avanzamento automatico (auto-play) privo di controlli manuali di pausa o senza fermare la rotazione quando il componente riceve il focus nel DOM (Document Object Model).  
* Non nascondere elementi interattivi al di fuori dell'area visibile senza un corretto trattamento della visibilità e della sequenza di focus.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Carousel nelle librerie di design e nel codice sono definite come segue:

* **`itemType`**: Tipo di scheda o contenuto ospitato nel carosello. Valori possibili: `serviceCard`, `institutionCard`, `messageCard` o `custom`. Default: `"serviceCard"`.  
* **`loop`**: Indicatore booleano per consentire lo scorrimento infinito/ciclico delle schede. Default: `false`.  
* **`showControls`**: Determina la visibilità dei pulsanti di avanzamento (Previous / Next). Default: `true`.  
* **`showIndicators`**: Mostra i pallini (dots) o gli indicatori numerici di paginazione. Default: `true`.  
* **`autoPlay`**: Stato booleano per l'avanzamento temporizzato automatico delle diapositive. Default: `false`.  
* **`visibleItemsCount`**: Numero di elementi o porzioni di schede visibili contemporaneamente nello viewport del contenitore nel DOM (Document Object Model). Default: `1.2` (per suggerire lo scorrimento orizzontale su mobile).

# **4\. Stati e varianti**

## **4.1 Configurazione delle Schede e del Layout**

Il componente si adatta ai diversi tipi di contenuti e layout strutturali disponibili nel Design System:

* **Service Card Carousel:** Contiene schede di servizio standard con nome servizio ed ente erogatore (Service name, Organization name).  
* **Featured Institutions Carousel:** Ospita schede di enti ed istituzioni in evidenza con logo ed etichetta identificativa.  
* **Message / Communication Carousel:** Presenta messaggi o avvisi in un unico punto informativo.

## **4.2 Comportamento Dinamico e Interazione**

* **Default:** Stato iniziale del contenitore scorrevole pronto per l'interazione da parte dell'utente.  
* **Scrolling / Swiping:** Stato attivo durante il movimento orizzontale condotto tramite gesti touch o trascinamento sul DOM (Document Object Model).  
* **Focused / Paused:** Stato assunto quando l'utente posiziona il puntatore o il focus da tastiera sul componente, arrestando l'eventuale rotazione automatica.  
* **Skeleton Loading:** Stato di caricamento tramite strutture Skeleton applicato alle schede in attesa della risposta delle API.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Guided Tour**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione dei percorsi guidati e dell'onboarding passo-passo (Guided Tour / Product Tour / Walkthrough).

```
---
id: component-guided-tour
name: Guided Tour
category: Navigation & Onboarding
version: 1.0.0
tags: [guided-tour, onboarding, walkthrough, product-tour, step-by-step, tooltip, modal, progress-bar, accessibility]
last_updated: 2026-11-10
---
```

# **Descrizione**

Il componente Guided Tour (o Product Tour / Walkthrough) è un motivo d'interazione ed elemento d'interfaccia orientato all'onboarding che guida l'utente attraverso le funzionalità chiave, i flussi di lavoro o le novità di un'applicazione. All'interno dell'albero del DOM (Document Object Model), il Guided Tour viene gestito tramite l'ancoraggio dinamico di finestre di dialogo contestuali (popover/tooltip) o sovrapposizioni modali (modal overlay) sugli elementi dell'interfaccia interessati. Il componente permette di mostrare sequenze ordinate di passaggi guidati (da 4 a 6 step al massimo), evidenziando visivamente i componenti di destinazione tramite faretti o mascherate di sfondo (spotlight / dark overlay) e offrendo controlli espliciti per la progressione, il salto del percorso e la chiusura rapida.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Introduzione a nuove interfacce e funzionalità:** Utilizzare per orientare l'utente al primo accesso (first-time onboarding) o per evidenziare funzionalità complesse e non immediatamente intuitive.  
* **Percorsi brevi e focalizzati sugli obiettivi:** Mantenere il tour conciso (ideale tra 4 e 6 passaggi), orientando l'utente al raggiungimento del primo valore o risultato concreto ("aha moment").  
* **Scelta di adesione e controllo totale (Opt-in e Skip):** Fornire sempre pulsanti visibili ed espliciti per saltare (Skip) o interrompere (Exit/Close) la visita in qualsiasi momento senza vincoli.  
* **Indicatori di avanzamento chiari:** Includere sempre una barra di progresso visibile o l'indicatore numerico dei passaggi (es. Step 2 di 4\) per comunicare chiaramente la durata stimata del percorso.  
* **Rilancio su richiesta (Relaunch Hub):** Permettere di riavviare il tour su richiesta tramite un menu di aiuto o impostazioni per gli utenti che desiderano consultarlo in seguito.

## **Don't (Quando NON usare)**

* Non forzare percorsi obbligatori senza possibilità di chiusura o salto (no-escape), creando frustrazione e rischio di abbandono dell'applicazione.  
* Non sovraccaricare il tour con un numero eccessivo di passaggi (\> 6 passaggi) o spiegazioni ovvie di elementi comuni di UI (es. "Questo è il pulsante Salva").  
* Non bloccare azioni operative prioritarie per gli utenti esperti o per chi ha già familiarità con l'interfaccia.  
* Non lanciare tour automatici senza contesto o fuori tempo mentre l'utente sta eseguendo compiti ad alta concentrazione.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Guided Tour nelle librerie di design e nel codice sono definite come segue:

* **`tourType`**: Determina la modalità visiva del passaggio. Valori possibili: `modal` (schermata di benvenuto/overview), `tooltip` (ancorato ad elementi del DOM (Document Object Model)) o `slideout`. Default: `"tooltip"`.  
* **`currentStep`**: Indice numerico dell'attuale passaggio visibile nel tour (es. 1, 2, 3). Default: `1`.  
* **`totalSteps`**: Numero complessivo di passaggi configurati per il tour. Default: `4`.  
* **`showProgressBar`**: Indicatore booleano per visualizzare la barra o i pallini di avanzamento. Default: `true`.  
* **`allowSkip`**: Abilita la presenza del pulsante visibile per saltare l'intero tour. Default: `true`.  
* **`spotlightOverlay`**: Attiva uno sfondo scuro semitrasparente che mette in evidenza l'elemento target ancorato nel DOM (Document Object Model). Default: `true`.  
* **`targetElement`**: Riferimento o selettore dell'elemento target agganciato nell'albero del DOM (Document Object Model). Default: `null`.

# **4\. Stati e varianti**

## **4.1 Configurazione dei Passaggi e delle Varianti Visive**

Il componente supporta diverse tipologie di visualizzazione strutturale:

* **Welcome Modal (First-look):** Finestra modale d'apertura ad alto impatto per salutare l'utente, presentare il valore generale e chiedere l'avvio volontario del tour.  
* **In-Context Tooltip (Contextual Step):** Fumetto/tooltip ancorato a una specifica funzionalità dell'interfaccia con puntatore rivolto all'elemento evidenziato nel DOM (Document Object Model).  
* **Completion Card (Final CTA):** Passaggio finale che sintetizza il completamento e reindirizza l'utente verso l'azione principale con un pulsante d'azione chiaro.

## **4.2 Comportamento Dinamico e Interazione**

* **Initial / Triggered:** Stato in cui il tour viene attivato automaticamente o su richiesta dell'utente.  
* **Active Step:** Stato corrente del passaggio in cui il focus viene mantenuto sull'elemento ancorato e sui controlli di navigazione (Successivo / Indietro).

**Dismissed / Skipped:** Stato assunto a seguito dell'interruzione o del salto manuale, che rimuove gli elementi del tour dal DOM (Document Object Model) e ripristina la normale navigazione.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Header**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione e la gestione delle testate di navigazione (Header di 1° livello e Service Header).

```
---
id: component-header
name: Header
category: Navigation & Layout
version: 1.0.0
tags: [header, navigation, service-header, sticky, tab-navigation, accessibility]
last_updated: 2026-11-10
---
```

# **Descrizione**

Il componente Header funge da elemento strutturale e di orientamento primario per le applicazioni e i servizi digitali. Posizionato nella parte superiore dell'albero del DOM (Document Object Model), definisce la gerarchia visiva, fornisce il contesto della pagina corrente e integra controlli essenziali di navigazione ed azione. Il componente supporta due varianti strutturali principali: l'Header di 1° livello, utilizzato per le sezioni principali dell'applicazione con supporto ad azioni secondarie e navigazione a schede, e il Service Header, progettato a larghezza intera (full-width) per presentare le informazioni del servizio e dell'ente erogatore con spaziatura dedicata.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Utilizzare l'Header di 1° livello nelle viste principali:** Impiegare l'Header di 1° livello per definire il titolo di sezione principale (stile H2), limitando il numero di azioni rapide ad un massimo di 3 elementi visibili nel DOM (Document Object Model).  
* **Mantenere il posizionamento Sticky:** Configurare l'Header di 1° livello come elemento fisso (sticky) durante lo scorrimento della pagina per garantire la persistenza dei controlli di navigazione.  
* **Abilitare il ridimensionamento dinamico (Resize on scroll):** Predisporre la riduzione della dimensione del titolo da H2 a H4 durante lo scorrimento verso il basso per ottimizzare lo spazio verticale della viewport.  
* **Utilizzare il Service Header a larghezza intera:** Applicare il Service Header a tutta larghezza (full-width) rispettando rigorosamente il layout di spaziatura con 8px nella parte superiore e 16px nella parte inferiore.  
* **Integrazione della Tab Navigation:** Includere la navigazione a schede (Tab navigation) direttamente all'interno dell'Header di 1° livello quando si organizzano sotto-sezioni correlate della pagina.

## **Don't (Quando NON usare)**

* Non inserire più di 3 azioni principali all'interno dell'Header di 1° livello per evitare il sovraccarico visivo del DOM (Document Object Model).  
* Non alterare le distanze di spaziatura predefinite nel Service Header (8px sopra, 16px sotto) per mantenere la coerenza visiva dell'applicazione.  
* Non disabilitare il ridimensionamento dinamico del titolo su dispositivi mobili o durante lo scorrimento per non limitare l'area di lavoro dell'utente.  
* Non combinare impropriamente elementi di primo e secondo livello all'interno di una struttura di testata unica non conforme alla gerarchia di design.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Header nelle librerie di design e nel codice sono definite come segue:

* **`headerType`**: Definisce la variante strutturale dell'header. Valori possibili: `first-level` (Header di 1° livello con azioni e tab) o `service-header` (Service Header full-width con dettagli dell'ente). Default: `"first-level"`.  
* **`isSticky`**: Determina se l'header rimane ancorato in cima alla finestra d'interfaccia (DOM (Document Object Model)) durante lo scorrimento. Default: `true`.  
* **`titleStyle`**: Specifica la dimensione e lo stile del titolo visibile (es. H2 di base o H4 compresso a seguito di scorrimento). Default: `"H2"`.  
* **`maxActions`**: Imposta il numero massimo di pulsanti o azioni rapide inseribili nell'Header di 1° livello (massimo 3). Default: `3`.  
* **`hasTabNavigation`**: Indicatore booleano per includere la barra di navigazione a schede come elemento integrato di pagina. Default: `false`.  
* **`fullWidth`**: Forza il layout del componente a coprire l'intera larghezza del contenitore (applicato di default al Service Header). Default: `true`.  
* **`spacingTop`**: Spaziatura superiore applicata al Service Header (valore fisso a 8px). Default: `"8px"`.  
* **`spacingBottom`**: Spaziatura inferiore applicata al Service Header (valore fisso a 16px). Default: `"16px"`.

# **4\. Stati e varianti**

## **4.1 Varianti di Header**

Il componente Header è strutturato in due varianti principali:

* **Header di 1° livello:** Destinato alle sezioni principali dell'applicazione. Include fino a 3 azioni secondarie, supporto al posizionamento sticky, ridimensionamento del titolo (H2 a H4) e integrazione con tab navigation come elemento di pagina.  
* **Service Header:** Variante a larghezza intera (full-width) pensata per mettere in risalto il nome del servizio e dell'ente erogatore, con margini di spaziatura dedicati (8px superiore, 16px inferiore).

## **4.2 Stati e Comportamenti Dinamici**

* **Default (Default State):** Stato iniziale visualizzato all'apertura della pagina con titolo in stile H2 e layout standard completo.  
* **Scrolled / Compressed State:** Stato assunto durante lo scorrimento della pagina (sticky). Il titolo subisce un resize riducendosi a stile H4 e riducendo l'ingombro verticale nel DOM (Document Object Model).  
* **Tab Navigation Active:** Stato in cui l'Header mostra e gestisce le schede di navigazione attive per consentire il cambio contestuale della vista.

5\. Accessibilità

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Message Details Header**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione e la gestione del componente Message Details Header nelle comunicazioni digitali.

```
---
id: component-message-details-header
name: Message Details Header
category: Navigation & Layout
version: 1.0.0
tags: [message-details-header, header, full-width, legal-value, notification]
last_updated: 2026-11-10
---
```

# **Descrizione**

Il componente Message Details Header funge da modulo di testata dedicato alla visualizzazione dei dettagli di una comunicazione o notifica digitale. Posizionato esclusivamente nella parte superiore del corpo del messaggio a tutta larghezza (full-width), definisce il contesto informativo principale presentando l'ente o mittente, l'oggetto/titolo della comunicazione, la data e ora di invio/ricezione, l'eventuale canale erogatore e lo stato del valore legale. Il componente permette di strutturare chiaramente le informazioni chiave del messaggio all'interno del DOM (Document Object Model (Modello a Oggetti del Documento)), garantendo immediatezza visiva e tracciabilità formale.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Utilizzo esclusivo Full-Width:** Utilizzare il componente sempre a larghezza intera (full-width) rispetto al contenitore principale della pagina o del messaggio.  
* **Posizionamento in testa al messaggio:** Collocare l'header rigorosamente come primo modulo visivo nel corpo del messaggio, prima di qualsiasi contenuto narrativo o allegato.  
* **Inclusione dei metadati chiave:** Garantire sempre la presenza delle informazioni fondamentali: nome del mittente/ente, oggetto del messaggio, data/ora e indicatore di valore legale se pertinente.  
* **Chiara indicazione del valore legale:** Mostrare in modo visibile il badge o la dicitura "VALORE LEGALE" per messaggi inviati tramite canali certificati (es. Send \- Servizio Notifiche Digitali).  
* **Mantenere l'allineamento visivo:** Garantire una gerarchia chiara e leggibile dei testi e dei badge all'interno della struttura del DOM (Document Object Model (Modello a Oggetti del Documento)).

## **Don't (Quando NON usare)**

* Non utilizzare il componente all'interno di colonne ridotte o contenitori parziali che ne compromettano il layout full-width.  
* Non collocare il modulo al di sotto del testo principale o in posizione intermedia all'interno del messaggio.  
* Non omettere i metadati essenziali come l'ente erogatore/mittente e la data/ora di invio.  
* Non alterare l'aspetto o la dicitura del valore legale quando la notifica possiede rilevanza giuridica o amministrativa.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Header nelle librerie di design e nel codice sono definite come segue:

* **`senderName`**: Stringa che definisce il nome dell'ente o organizzazione mittente (es. "Comune di Controguerra"). Default: `""`.  
* **`subject`**: Titolo o argomento principale della comunicazione (es. "Carta d'Identità Elettronica \- Richiesta di firma"). Default: `""`.  
* **`timestamp`**: Indicazione temporale formattata contenente data e ora del messaggio (es. "12 maggio 2023, 12:34"). Default: `""`.  
* **`hasLegalValue`**: Valore booleano che indica se la comunicazione possiede valore legale formalizzato. Default: `true`.  
* **`serviceProvider`**: Canale o piattaforma utilizzata per l'invio (es. "Send \- Servizio Notifiche Digitali" o "Novità e aggiornamenti"). Default: `""`.  
* **`fullWidth`**: Forza il layout a coprire l'intera larghezza del contenitore madre. Default: `true`.  
* **`variant`**: Identifica la variante visiva e contestuale (es. `"default"`, `"legal-notice"`). Default: `"default"`.

# **4\. Stati e varianti**

## **4.1 Varianti del Componente**

Il componente Message Details Header presenta le seguenti varianti principali:

* **Default Header:** Variante standard full-width per messaggi di servizio e comunicazioni ordinarie dell'ente (es. notizie, aggiornamenti).  
* **Legal Notice Header:** Variante avanzata contenente l'indicatore esplicito "VALORE LEGALE" ed eventuale specifica dell'erogatore tramite piattaforma ufficiale (es. Send \- Servizio Notifiche Digitali).

## **4.2 Stati e Comportamenti Dinamici**

* **Stato Default (Standard Display):** Visualizzazione standard di tutti i metadati e dell'oggetto all'apertura del messaggio nel DOM (Document Object Model (Modello a Oggetti del Documento)).  
* **Stato con Valore Legale Attivo:** Mostra in evidenza la targhetta visiva dedicata al valore giuridico della notifica.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Message Footer**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione e la gestione del componente Message Footer nelle comunicazioni digitali.

```
---
id: component-message-footer
name: Message Footer
category: Navigation & Layout
version: 1.0.0
tags: [message-footer, footer, layout, actions, list-item-action]
last_updated: 2026-11-10
---
```

# **Descrizione**

Il componente Message Footer costituisce il modulo di chiusura situato in fondo all'interfaccia di una comunicazione o notifica digitale. Rappresenta la sezione finale della visualizzazione all'interno del DOM (Document Object Model (Modello a Oggetti del Documento)) e raccoglie le azioni secondarie o correlate disponibili per l'utente (es. "Archivia il messaggio", "Contatta il mittente", "Mostra altri dati", "Segnala un problema"). Ha lo scopo di offrire un accesso rapido ed ordinato alle operazioni contestuali, integrando eventuali avvisi o CTA di sistema tramite elementi dedicati.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Posizionamento standard:** Posizionarsi sempre come ultimo elemento all'interno della schermata nel DOM (Document Object Model (Modello a Oggetti del Documento)).  
* **Distanziamento superiore:** Garantire una spaziatura verticale di esattamente 24 px rispetto all'elemento immediatamente superiore.  
* **Utilizzo delle icone nei List Item Action:** Tutti i List Item Action contenuti nello slot del footer devono obbligatoriamente includere un'icona identificativa.  
* **Ordinamento rigoroso delle azioni:** Posizionare prima tutti i List Item Action con variant=primary e successivamente tutti quelli con variant=danger (es. segnalazione problemi).  
* **Tag con CTA in Fase 1:** Come regola per il messaggio nel footer, in fase 1 si utilizza l'elemento Alert come default per il tag contenente una Call To Action (CTA).

## **Don't (Quando NON usare)**

* Non configurare mai il componente come elemento sticky o fisso alla finestra durante lo scorrimento.  
* Non collocare il componente in una posizione intermedia o diversa dal termine del contenuto nel DOM (Document Object Model (Modello a Oggetti del Documento)).  
* Non inserire elementi List Item Action privi di icona.  
* Non invertire l'ordine delle azioni mettendo elementi con variant=danger prima di quelli con variant=primary.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Header nelle librerie di design e nel codice sono definite come segue:

* **`actionsSlot`**: Slot contenente l'insieme degli elementi List Item Action forniti all'interfaccia. Default: `[]`.  
* **`alertDefaultTag`**: Componente Alert utilizzato di default per la gestione del tag con CTA (Fase 1). Default: `true`.  
* **`topSpacing`**: Valore numerico della spaziatura superiore rispetto al contenuto che lo precede (espresso in px). Default: `24`.  
* **`isSticky`**: Proprietà booleana che forza la sovrapposizione fissa. Deve essere sempre disabilitata. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Varianti del Componente**

Il componente Message Details Header presenta le seguenti varianti principali:

* **Standard Actions Footer:** Struttura base che include la sequenza dei List Item Action dotati di icona, ordinati per variant=primary e successivamente variant=danger.  
* **Footer con Alert CTA (Fase 1):** Variante che integra nella parte superiore dell'area footer l'elemento Alert di default come tag per messaggi con Call To Action.

## **4.2 Stati e Comportamenti Dinamici**

* **Stato di caricamento e rendering nel DOM:** I List Item Action vengono inseriti sequenzialmente nell'albero del DOM (Document Object Model (Modello a Oggetti del Documento)), mantenendo fisso l'offset superiore di 24 px.  
* **Interazione con le Azioni:** Ogni List Item Action gestisce lo stato di hover, focus e pressione in modo indipendente per consentire l'avvio delle funzioni correlate (es. apertura di dialoghi o invio di segnalazioni).

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Navbar**

Linee guida complete, proprietà, varianti, comportamenti e regole d'uso per l'integrazione e la gestione del componente Navbar nelle comunicazioni e nell'interfaccia dell'applicazione.

```
---
id: component-navbar
name: Navbar
category: Navigation & Layout
version: 1.0.0
tags: [navbar, navigation, layout, actions, bottom-bar]
last_updated: 2026-11-10
---
```

# **Descrizione**

Il componente Navbar costituisce l'elemento centrale per la navigazione principale all'interno dell'applicazione. Garantisce l'accesso rapido ed immediato alle sezioni chiave dell'interfaccia (es. Messaggi, Portafoglio, Inquadra, Pagamenti, Servizi), offrendo una struttura persistente e intuitiva per l'orientamento dell'utente all'interno della gerarchia delle funzioni.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Dynamic type e padding 8 px:** Dimensione della label variabile da 10px a un massimo di 12px, con un padding interno di 8 px e la troncatura della parola tramite puntini di sospensione in caso di copy esteso.  
* **Colore:** Utilizzo del colore Grey 850 per icone e label nello stato non selezionato al fine di garantire i requisiti fondamentali di accessibilità e contrasto visivo.  
* **Elevation a fine pagina:** L'ombra scompare dinamicamente per indicare visivamente la fine della pagina o il raggiungimento del fondo del contenuto durante lo scorrimento.

## **Don't (Quando NON usare)**

* Non applicare l'effetto di ombra (elevation) ad altri elementi sovrapposti all'esterno dei criteri stabiliti dallo Z Index della Navbar.  
* Non utilizzare colori differenti da Grey 850 per icone e testi negli stati non selezionati per evitare problemi di contrasto e accessibilità.  
* Non superare la dimensione massima di 12px o scendere sotto i 10px per le etichette di testo (label).  
* Non permettere al testo delle etichette di andare su più righe senza applicare la troncatura.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà che controllano il componente Navbar nelle librerie di design e nel codice sono definite come segue:

* **`items`**: Lista degli elementi di navigazione contenuti nella bar (icone \+ label). Default: `[]`.  
* **`selectedIndex`**: Indice dell'elemento di navigazione attualmente attivo. Default: `0`.  
* **`elevation`**: Proprietà booleana o stato che determina la presenza dell'ombra in base allo scorrimento. Default: `true`.  
* **`padding`**: Valore del padding interno applicato agli elementi della Navbar. Default: `8px`.

# **4\. Stati e varianti**

## **4.1 Varianti del Componente**

Il componente Navbar presenta le seguenti varianti e stati principali:

* **Stato Selezionato:** L'elemento attivo evidenzia l'icona e la label con il colore di accento/primario dell'applicazione per indicare chiaramente la sezione corrente.  
* **Stato Non Selezionato:** Gli elementi inattivi utilizzano il colore Grey 850 sia per l'icona che per la label, assicurando il rispetto dei contrasti e dei requisiti d'accessibilità.

## **4.2 Stati e Comportamenti Dinamici**

* **Interazioni e Scorrimento:** Al tocco di un elemento viene attivato lo stato selezionato e avviata la navigazione. Durante lo scorrimento della pagina viene mostrata l'ombra di elevazione, che scompare automaticamente al raggiungimento del fondo del contenuto.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Operation result**

Quando usarlo, proprietà, varianti, comportamento, accessibilità ed errori da evitare per l'esito delle operazioni.

```
---
id: component-operation-result
name: Operation result
category: Feedback & Status
version: 1.0.0
tags: [operation-result, empty-state, feedback, status, confirm]
last_updated: 2026-11-10
---
```

# **Descrizione** 

Il componente Operation result fornisce un feedback visivo immediato e chiaro all'utente sull'esito di un azione o sullo stato del sistema. Viene utilizzato per comunicare lo stato vuoto di una sezione (Empty state), il successo di una transazione o procedura (OK state) oppure la presenza di errori/problemi temporanei (KO state). Strutturalmente si compone di un elemento grafico/iconico descrittivo, un titolo esplicativo, un testo di supporto, e fino a due azioni primarie e secondarie espresse tramite pulsanti di CTA (Call To Action) integrate nel DOM (Document Object Model).

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Chiara comunicazione di stato:** Utilizzare il componente per confermare l'esito di operazioni ad alto impatto (pagamenti, invio moduli) o per informare l'utente su sezioni prive di contenuti.  
* **Varianti dedicate:** Adottare lo stato OK per transazioni completate con successo, lo stato KO per errori bloccanti o temporanei, e lo stato Empty per guide visive o contenuti vuoti.  
* **Azioni chiare:** Fornire azioni di chiusura o navigazione esplicite ("Ok, chiudi", "Indietro") per facilitare il prosieguo dell'esperienza utente.  
* **Unica CTA:** Utilizzare **1 sola CTA Primary** quando l'azione richiesta è univoca, diretta, focalizzata e conclusiva (es. chiusura di un flusso bloccante o presa visione di un esito senza alternative immediate).   
* **Due CTA:** Utilizzare la combinazione **2 CTA (Primary \+ Secondary)** quando l'utente si trova di fronte a un bivio decisionale o a un'operazione che richiede un'alternativa di navigazione (es. l'azione principale di conferma/proseguimento affiancata da un'azione secondaria di ritorno, annullamento o consultazione come "Indietro" o "Annulla").

## **Don't (Quando NON usare)**

* Non utilizzare lo stato OK in presenza di errori parziali o avvisi di cui l'utente debba farsi carico immediatamente.  
* Non omettere i pulsanti di azione quando l'utente necessita di chiudere la schermata o ritornare al flusso precedente.  
* Non generare sovraccarico informativo all'interno del messaggio descrittivo principale.  
* Non posizionare elementi interattivi complessi all'interno del layout del componente per mantenere pulita la struttura del DOM (Document Object Model).

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`state`**: Determina la variante visiva e contestuale. Valori: `empty`, `ok`, `ko`. Default: `"ok"`.  
* **`title`**: Titolo principale dell'esito. Definisce la riga d'intestazione dell'esito. Default: `"Titolo"`.  
* **`description`**: Testo esplicativo o secondario fornito a supporto del messaggio principale.  
* **`primaryActionLabel`**: Etichetta dell'azione primaria (es. "Ok, chiudi", "Primary").  
* **`secondaryActionLabel`**: Etichetta dell'azione secondaria (es. "Indietro", "Secondary").

# **4\. Stati e varianti**

## **4.1 Empty State**

La variante Empty State descrive l'assenza di contenuti in una specifica sezione (es. archivi o elenchi vuoti):

* **Titolo:** "Il tuo archivio è vuoto".  
* **Descrizione:** "Premi a lungo uno o più messaggi per archiviarli.".  
* **Azioni correlate:** Pulsanti d'azione configurabili ("Primary", "Secondary") integrate nel DOM (Document Object Model).

## **4.2 OK State (Esito Positivo)**

La variante OK State conferma il corretto completamento di una procedura o transazione:

* **Titolo:** "Il pagamento è andato a buon fine".  
* **Descrizione:** "È tutto a posto, puoi tornare alle tue operazioni".

* ## **4.3 KO State (Esito Negativo)**

* **Titolo e Descrizione:** "C'è un problema temporaneo, riprova." con indicazione dell'azione correttiva ("Premi a lungo uno o più messaggi per archiviarli.").  
* **Azioni di Chiusura e Navigazione:** Pulsanti dedicati per la gestione dell'esito visibili nell'interfaccia ("Ok, chiudi", "Indietro").

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Payment card**

Quando usarlo, proprietà, varianti, comportamento ed errori da evitare per le carte e metodi di pagamento.

```
---
id: component-payment-card
name: Payment card
category: Payment & Wallet
version: 1.0.0
tags: [payment-card, wallet, paypal, visa, bancomat-pay, card-detail]
last_updated: 2026-11-10
---
```

# **Descrizione** 

Il componente Payment card permette di visualizzare e gestire i metodi di pagamento registrati dall'utente (come carte di credito/debito Visa, account PayPal, BANCOMAT Pay o altri istituti bancari). Visualizza in modo chiaro le informazioni identificative del metodo (es. ultime 4 cifre della carta, email associata all'account, data di scadenza e stato di validità/scadenza). Viene utilizzato sia in modalità compatta/estesa all'interno di elenchi e selezioni di pagamento, sia nella vista di dettaglio per configurazioni avanzate (impostazioni, preferiti e rimozione del metodo) integrate nel DOM (Modello a Oggetti del Documento).

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Chiara identificazione del metodo:** Utilizzare il componente per mostrare chiaramente i dati identificativi del metodo di pagamento (circuito, ultime 4 cifre o email dell'account) e la data di scadenza.  
* **Gestione dello stato:** Mostrare chiaramente i badge di stato come "SCADUTA" o indicatori di attenzione quando il metodo necessita di aggiornamento o non è utilizzabile.  
* **Impostazione metodo preferito:** Fornire nella schermata di dettaglio l'opzione "Usa come preferito" per selezionare automaticamente il metodo durante i pagamenti in-app pagoPA.  
* **Rimozione sicura:** Includere l'azione "Rimuovi metodo" nella vista di dettaglio per permettere all'utente di disassociare facilmente il wallet.

## **Don't (Quando NON usare)**

* Non mostrare il numero completo della carta di credito per ragioni di sicurezza e conformità privacy, limitando l'esposizione alle sole ultime 4 cifre.  
* Non nascondere lo stato di carta scaduta ("SCADUTA"), evitando che l'utente tenti un pagamento con un metodo non valido.  
* Non alterare i loghi e i marchi dei circuiti di pagamento (Visa, PayPal, BANCOMAT Pay) rispettando la Brand Governance dei rispettivi fornitori.  
* Non sovraccaricare la variante Small con informazioni secondarie non necessarie durante la fase di selezione rapida.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`type`**: Specifica la tipologia del metodo di pagamento. Valori: `visa`, `paypal`, `bancomat_pay`, `generic_bank`.  
* **`size`**: Dimensione del layout nel DOM (Modello a Oggetti del Documento). Valori: `small` (vista compattata/elenco), `medium` (carta standard), `detail` (vista completa di configurazione).  
* **`accountIdentifier`**: Identificativo visualizzato (es. "\*\*\*\* 9900" oppure "anna\_v\*\*\*\*\*\*\*\*@\*\*hoo.it").  
* **`expirationDate`**: Data di scadenza nel formato MM/YY (es. "02/24").  
* **`isExpired`**: Booleano che indica se la carta è scaduta. Default: `false`.  
* **`isFavorite`**: Booleano per impostare la carta come metodo preferito per i pagamenti in-app pagoPA. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Payment Card Small**

Variante compatta utilizzata principalmente in liste di selezione veloce o in spazi di layout ridotti:

* **Elementi visivi:** Logo del circuito/banca (Visa, PayPal, BANCOMAT Pay, Generic bank) affiancato dalle ultime cifre numeriche o dal nome identificativo.  
* **Stati di attenzione:** Presenza di badge d'avviso (icona punto esclamativo) per segnalare la necessità di verificare il metodo.

## **4.2 Payment Card Standard & Scaduta**

Variante standard usata per la consultazione principale dei metodi di pagamento salvati:

* **Informazioni estese:** Mostra l'identificativo (es. Visa .... 9900 o l'email mascherata dell'account PayPal) e la data di scadenza (es. "Valida fino al 02/24").  
* **Stato SCADUTA:** Visualizza l'etichetta esplicita "SCADUTA" in evidenza quando il metodo ha superato la data di validità.

## **4.3 Payment Card Detail**

* **Intestazione e Dettagli:** Include pulsante di ritorno ("←"), logo del metodo, identificativo mascherato ed esplicita indicazione di validità ("Valida fino al 02/24").  
* **Opzioni di Configurazione:** Sezione "Impostazioni" con toggle "Usa come preferito" (con descrizione contestuale per i pagamenti in app pagoPA) e pulsante d'azione "Rimuovi metodo" integrate nel DOM (Modello a Oggetti del Documento).

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Text block**

Quando usarlo, proprietà, varianti, comportamento ed errori da evitare per il componente Text block.

```
---
id: component-text-block
name: Text block
category: Content & Display
version: 1.0.0
tags: [text-block, typography, content, privacy, terms]
last_updated: 2026-11-10
---
```

# **Descrizione** 

Il componente Text block è un elemento strutturale di layout utilizzato per presentare blocco di testo informativo, titoli di pagina e note legali o informative all'interno dell'interfaccia. Supporta titoli strutturati su diversi livelli di gerarchia (Heading), testo di corpo del paragrafo e collegamenti ipertestuali a documenti o informative di supporto. Il componente si adatta automaticamente e in modo fluido alla larghezza del dispositivo all'interno del DOM (Modello a Oggetti del Documento).

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Strutturazione del contenuto:** Utilizzare il componente per organizzare gerarchicamente sezioni di testo, titoli di pagina e testo descrittivo continuo.  
* **Layout reattivo:** Assicurarsi che il blocco si adatti alla larghezza del dispositivo occupando lo spazio orizzontale disponibile nel DOM (Modello a Oggetti del Documento).  
* **Note legali e informative:** Inserire riferimenti e link all'Informativa Privacy e ai Termini e Condizioni d'uso nella parte conclusiva del blocco di testo.

## **Don't (Quando NON usare)**

* Non utilizzare rigide dimensioni fisse in pixel che impediscano l'adattamento automatico alla larghezza dello schermo del dispositivo nel DOM (Modello a Oggetti del Documento).  
* Non saltare livelli della gerarchia visiva dei titoli per garantire la corretta leggibilità e struttura logica.  
* Non inserire azioni primarie o elementi complessi interattivi all'interno del blocco di solo testo.

# **3\. Proprietà (Figma / Code Connect Props)**

L'interfaccia del componente è controllata dalle seguenti proprietà esposte nella libreria Figma e nel codice:

* **`title`**: Stringa opzionale per l'intestazione del blocco ("Titolo della pagina").  
* **`bodyText`**: Testo principale del paragrafo (es. "Lorem ipsum dolor sit amet...").  
* **`fullWidth`**: Booleano che determina se il componente si estende al 100% della larghezza del dispositivo nel DOM (Modello a Oggetti del Documento). Default: `true`.  
* **`showLegalFooter`**: Booleano per includere o meno la sezione informativa con i link alla Privacy e ai Termini e Condizioni. Default: `false`.

# **4\. Stati e varianti**

## **4.1 Text Block Standard**

Variante principale utilizzata per la presentazione di contenuti testuali standard:

* **Titolo della pagina:** Intestazione visibile in evidenza per contestualizzare la sezione.  
* **Corpo del testo:** Uno o più paragrafi descrittivi che si adattano fluidamente alla larghezza del contenitore nel DOM (Modello a Oggetti del Documento).

## **4.2 Text Block con Note Legali**

Variante estesa che include piè di pagina informativo con collegamenti ipertestuali:

* **Testo di chiusura:** "Per maggiori informazioni, leggi l'informativa Privacy e i Termini e Condizioni d'uso".  
* **Link d'azione:** Iperlink collegati direttamente alle rispettive sezioni legali.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Timeline**

Quando usarlo, proprietà, varianti, comportamento ed errori da evitare per il componente Timeline.

```
---
id: component-timeline
name: Timeline
category: Content & Display
version: 1.0.0
tags: [timeline, status, history, tracking, bottomsheet]
last_updated: 2026-11-10
---
```

# **Descrizione** 

Il componente Timeline è un elemento visivo e di layout utilizzato per rappresentare in ordine cronologico una sequenza di eventi, stati o fasi di un processo (es. lo stato di avanzamento di una notifica). Si compone di elementi di tracciamento (Timeline Dot) e singoli elementi della lista (Timeline List Item) che riportano date, titoli di stato e orari. Il componente si renderizza dinamicamente nel DOM (Document Object Model) adattandosi al contenitore, inclusi elementi di overlay come le bottomsheet.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Tracciamento cronologico di processi:** Utilizzare la Timeline per mostrare la progressione di uno stato o storico eventi (es. "Invio in corso", "Depositata", "Consegnata", "Perfezionata per decorrenza termini", "Avvenuto accesso").  
* **Integrazione in componenti di overlay:** Inserire la Timeline all'interno di bottomsheet o modali per dettagli sullo stato del servizio.  
* **Rappresentazione chiara di date e orari:** Visualizzare chiaramente il giorno, il mese (es. "23 MAG") e l'orario (es. "09:30") per ciascuna voce nel DOM (Document Object Model).

## **Don't (Quando NON usare)**

* Non utilizzare la Timeline per elencare elementi privi di un'ordinazione temporale o di stato Sequenziale.  
* Non alterare l'ordine logico di lettura visiva degli elementi di tracciamento rispetto alla struttura del DOM (Document Object Model).  
* Non omissione delle etichette temporali (data/ora) quando il tracciamento richiede precisione cronologica.

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà principali che configurano il componente nel codice e nei moduli di design sono:

* **`items`**: Array di oggetti appartenenti a `Timeline List Item` contenenti data, ora e titolo dello stato.  
* **`statusDot`**: Configurazione visiva del nodo grafico (Timeline Dot) per ciascun elemento, indicante lo stato completato, attivo o in attesa.  
* **`showDisclaimer`**: Booleano per mostrare un messaggio informativo aggiuntivo al termine della lista (es. avviso per accedere alla versione web per maggiori dettagli). Default: `false`.  
* **`containerType`**: Stringa che definisce l'ambiente di resa nel DOM (Document Object Model) ("standard", "bottomsheet"). Default: `"standard"`.

# **4\. Stati e varianti**

## **4.1 Text Block Standard**

Lista cronologica completa presentata all'interno del flusso di pagina standard nel DOM (Document Object Model):

* **Timeline List Item:** Singolo blocco contenente giorno, mese, descrizione dello stato e orario dell'evento.  
* **Timeline Dot:** Indicatore grafico dello stato relativo a ciascun passaggio del processo.

## **4.2 Text Block con Note Legali**

Configurazione integrata in un pannello bottomsheet di tracciamento (es. "Stato della notifica"):

* **Intestazione del pannello:** Titolo dedicato della bottomsheet (es. "Stato della notifica") con pulsante di chiusura.  
* **Nota informativa ed elemento di azione:** Avviso descrittivo finale con bottone di reindirizzamento (es. "Accedi a SEND").

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Stepper**

Quando usarlo, proprietà, varianti, comportamento ed errori da evitare per il componente Stepper.

```
---
id: component-stepper
name: Stepper
category: Content & Display
version: 1.0.0
tags: [stepper, workflow, wizard, process]
last_updated: 2026-11-24
---
```

# **1\. Descrizione**

Il componente Stepper è un elemento visivo e di navigazione che guida l'utente attraverso un processo o workflow suddiviso in una sequenza di passaggi o fasi logiche (es. flussi di checkout, onboarding o configurazione). Mostra in modo chiaro la progressione del task, indicando lo step attivo, quelli completati e quelli futuri. Renderizzato dinamicamente all'interno del DOM (Document Object Model), lo Stepper facilita la comprensione della struttura del processo e riduce il carico cognitivo dell'utente.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Suddivisione di processi complessi:** Utilizzare lo Stepper per guidare l'utente in workflow strutturati (es. registrazioni, procedure guidate, acquisti) organizzati da 3 a 5 passaggi sequenziali.  
* **Navigazione e persistenza dei dati:** Consentire all'utente di tornare agli step precedenti senza perdita delle informazioni inserite nei form.  
* **Etichette brevi ed esplicite:** Nome dei passaggi sintetico ed orientato all'azione (es. "Dati", "Pagamento", "Riepilogo") chiaramente renderizzato nel DOM (Document Object Model).

## **Don't (Quando NON usare)**

* Non utilizzare lo Stepper per processi semplici costituiti da meno di 3 passaggi o per form estremamente brevi.  
* Non eccedere i 5-6 passaggi complessivi per non sovraccaricare l'utente e prevenire l'abbandono del flusso.  
* Non annidare Stepper all'interno di altri Stepper o utilizzare più istanze nella medesima vista del DOM (Document Object Model).

# **3\. Proprietà (Figma / Code Connect Props)**

Le proprietà principali che configurano il componente nel codice e nei moduli di design sono:

* **`steps`**: Array di oggetti che definiscono ciascun passaggio (titolo, sottotitolo opzionale, stato ed eventuale contenuto) iniettati nel DOM (Document Object Model).  
* **`orientation`**: Disposizione visiva del componente ("horizontal" per desktop/wizard estesi, "vertical" per mobile o pannelli laterali). Default: `"horizontal"`.  
* **`isNonLinear`**: Booleano che consente la navigazione libera tra gli step non consecutivi senza vincolo di dipendenza stringente. Default: `false`.  
* **`currentStep`**: Indice numerico relativo allo step attualmente attivo ed evidenziato nella schermata.

# **4\. Stati e varianti**

## **4.1 Text Block Standard**

Disposizione e comportamento del componente nel DOM (Document Object Model):

* **Horizontal Stepper:** Ideale per schermi di dimensioni medio-grandi; dispone etichette ed indicatori numerati lungo un asse orizzontale collegato da linee di avanzamento.  
* **Vertical Stepper:** Ottimizzato per dispositivi mobile o layout stretti; sviluppa lo step-by-step verticalmente integrando direttamente i contenuti ed i form al sotto di ciascun nodo.  
* **Linear Flow:** Obbliga il completamento sequenziale dei singoli passaggi prima di abilitare lo step successivo.  
* **Non-Linear Flow:** Permette la selezione e l'accesso diretto a qualsiasi step del flusso in modo flessibile.

## **4.2 Stati dei singoli Step**

* **Upcoming (Futuro):** Passaggio non ancora raggiunto, visivamente disabilitato o neutro.  
* **Current (Attivo):** Passaggio in corso d'opera, in risalto cromatico e focalizzato nel DOM (Document Object Model).  
* **Completed (Completato):** Passaggio concluso con successo, contrassegnato da icona di spunta (checkmark) e cliccabile per eventuale modifica.  
* **Error (Errore):** Passaggio che contiene campi non validi o errori bloccanti, evidenziato da apposita icona di avviso e messaggio esplicativo.

# **5\. Accessibilità (A11y)**

# **6\. Content**

# **Loading Page**

# **1\. Descrizione**

La **Loading Page** gestisce l'attesa durante operazioni asincrone bloccanti a schermo intero (es. generazione o presentazione di una credenziale digitale, verifica pagamenti), quando nessun dato strutturale della schermata successiva è ancora disponibile

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Caricamento iniziale:** Utilizza quando l'intera schermata è in fase di elaborazione o caricamento iniziale e l'utente deve attendere il completamento prima di poter interagire con i dati.  
* **Transizione:** Inserisci una dissolvenza della pagina al completamento dell'operazione.  
* **Cambio di schermata:** Utilizza per il passaggio a una nuova sezione o schermata nei casi in cui sia richiesto il caricamento completo del contenuto.

## **Don't (Quando NON usare)**

* **Caricamento parziale:** Non utilizzare quando la struttura della pagina è già nota e si stanno caricando solo singole sezioni o liste di dati (in quel caso usare la variante **Skeleton** dei singoli componenti).  
* **Spinner isolato:** Non mostrare uno spinner isolato privo di spiegazione testuale su cosa il sistema sta facendo.  
* **Operazioni locali o di sezione:** Non usare se si deve caricare soltanto una porzione specifica dello schermo o rimanere in attesa di dati localizzati.

# **Criteri di Valutazione AI**

| Criterio | Descrizione | Esito |
| :---- | :---- | :---- |
| **\[Content \- Tone of Voice\]** | Il titolo esplicita chiaramente l'operazione in corso ed usa un tono empatico e diretto? | \[Sì/No\] |
| **\[A11y \- Dynamic Updates\]** | Lo stato di caricamento è comunicato correttamente alle tecnologie assistive tramite region aria-live? | \[Sì/No\] |
| **\[UX \- Feedback\]** | Viene fornita una stima temporale o una rassicurazione visiva sull'attesa? | \[Sì/No\] |

# **OK/KO page (Schermate di Esito)**

# **1\. Descrizione**

Il key template **OK/KO page** definisce il layout e il comportamento delle schermate di esito a schermo intero (conclusivo e bloccante) per flussi ad alto impatto (es. completamento dell'attivazione di una credenziale digitale o fallimento bloccante dell'operazione). Comunica all'utente il successo definitivo dell'operazione oppure l'impossibilità di procedere a causa di un errore non risolvibile inline, fornendo indicazioni chiare sui passi successivi o sulle azioni di recupero. Garantisce che qualsiasi modifica apportata al DOM (Document Object Model) sia tempestivamente annunciata alle tecnologie assistive.

# **2\. Regole d'Uso (Governance)**

## **Do (Quando usare)**

* **Esito Conclusivo:** Utilizzare per confermare l'avvenuto completamento di un flusso dispositiva ad alto impatto (OK Page) o un fallimento critico/bloccante non gestibile tramite componenti inline (KO Page).  
* **Singola CTA Primaria:** Fornire un'unica Call to Action primaria chiara per chiudere la schermata o per avviare il tentativo di riprova (es. "Riprova" o "Ok, chiudi").  
* **Informazioni di Supporto:** Nelle schermate KO, mostrare sempre dettagli utili per l'assistenza (es. codice errore esplicito ed eventuali contatti dell'Issuer/Auth Source) riducendo la necessità di supporto esterno.

## **Don't (Quando NON usare)**

* **Feedback Asincrono Non Bloccante:** Non utilizzare per errori minori, validazioni di campi o notifiche temporanee in background (utilizzare notifiche snackbar/banner contextual inline).  
* **Messaggi Generici:** Non utilizzare mai messaggi opachi o generici come "Si è verificato un errore" senza esplicitare la causa e le azioni correttive possibili.  
* **Sovrapposizione di CTA Primarie:** Non inserire più di un'azione primaria nella stessa schermata di esito.

# **3\. Stati e Comportamenti**

* **Stato OK (Success):** Mostra un pittogramma/icona di successo visivamente distinta, un titolo rassicurante e sintetico (es. "Il pagamento è andato a buon fine"), eventuale testo esplicativo e una CTA di chiusura ("Ok, chiudi" o "Fatto\!").  
* **Stato KO (Error/Failure):** Presenta un'icona di errore, un titolo trasparente del problema, la descrizione della causa, la CTA di riprova ("Riprova") e azioni secondarie/link di supporto ("Contatta l'assistenza", "Vai alle domande frequenti", codice errore per eventuale segnalazione).  
* **Gestione dell'azione "Annulla" o indietro:** Il tap sulla CTA "Riprova" ripete l'autenticazione o la richiesta di sblocco, mentre l'uscita o la chiusura riporta l'utente direttamente alla schermata principale/entry page preservando la coerenza dello stato del sistema nel DOM (Document Object Model).

# **4\. Criteri di Valutazione AI**

| Criterio | Descrizione | Esito |
| :---- | :---- | :---- |
| **\[Template \- Pattern Fit\]** | La schermata di esito è riservata ad un processo conclusivo o ad un errore bloccante a schermo intero? \[Sì/No\] | \[Sì/No\] |
| **\[Content \- Clarity\]** | Il titolo chiarisce perfettamente l'esito senza ricorrere a formattazioni generiche e la descrizione offre una via di risoluzione ed eventuale codice di errore? \[Sì/No\] | \[Sì/No\] |
| **\[A11y \- Focus Management\]** | All'iniezione della schermata di esito nel DOM (Document Object Model), il focus viene impostato sul titolo principale \<h1\> ed annunciato dallo Screen Reader tramite role="alert" o role="status"? \[Sì/No\] | \[Sì/No\] |

Non entriamo troppo nel dettaglio. Spieghiamo come si generano le diverse credenziali (pattern, indicatore cromatico, tag, logo). Non definiamo una a una le tipologie, ma elenchiamo solo i diversi tipi di documenti presenti.