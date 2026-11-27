Accessibilità 

Linee guida di accessibilità per il Design System di IO

| Standard di riferimento: Legge Stanca (L. 4/2004) e Linee guida AgID, Standard Europeo UNI CEI EN 301 549, WCAG 2.1 / 2.2 Livello AA (e documento W3C WCAG2ICT), Apple Human Interface Guidelines e Material Design Accessibility per ecosistema Mobile Nativo (iOS / Android / React Native). |
| :---- |

1\. Colore e Contrasto

* Regola Generale: Utilizzare esclusivamente i token semantici del Design System. Non affidarsi mai al solo colore per comunicare stati, errori o azioni (associare sempre icone distintive o etichette testuali).  
* Placeholder e Sfondi Complessi: Anche il testo di placeholder nei campi di input DEVE rispettare il rapporto di contrasto minimo di 4.5:1 (sono esenti solo i logotipi e gli elementi disabilitati). Su sfondi sfumati o immagini, applicare sempre un overlay che garantisca il contrasto minimo su tutta l'area del testo.  
* Rapporti Minimi Obbligatori: 

| Tipo di Contenuto | Rapporto Minimo (AA) | Note Operative |
| :---- | :---- | :---- |
| Testo standard (sotto i 18pt / 14pt bold) | 4.5:1 | Target obbligatorio per body copy, titoli di card, label ed etichette CTA. |
| Testo grande (18pt+ / 14pt+ bold) | 3.0:1 | Intestazioni principali (H1/H2) e testi da esposizione. |
| Componenti UI e icone funzionali | 3.0:1 | Icone di stato, bordi di input, indicatori di selezione, focus e grafici. |
| Stati inattivi / disabilitati | Nessun requisito | Esenti dal requisito minimo, ma devono mantenere leggibilità sufficiente. |

2\. Tipografia, Ridimensionamento e Layout

* Altezza Dinamica e Wrapping: I contenitori dei componenti NON DEVONO avere altezze fisse. Devono espandersi verticalmente per supportare il ridimensionamento dei font di sistema (Dynamic Type su iOS e Font Scale su Android fino al 200%) senza sovrapposizioni o tagli.  
* Divieto di Troncamento: NON troncare mai titoli, etichette di pulsanti o messaggi informativi con ellissi (...) o limiti forzati di righe (numberOfLines). Il testo DEVE andare a capo naturalmente (text wrapping).  
* Orientamento: Le schermate NON DEVONO bloccare l'orientamento su Portrait o Landscape, garantendo la fruibilità anche su dispositivi fissati a supporti fisici.

3\. Touch Target e Interazione

* Dimensione Minima dell'Area di Tocco: Ogni elemento interattivo (pulsanti, link, icon button, header di accordion, pulsanti di chiusura) DEVE garantire un'area cliccabile minima di 44x44pt su iOS e 48x48dp su Android.  
* Spaziatura di Sicurezza: Se l'icona visiva è inferiore a 44pt/48dp (es. icona "X" o icona info "i"), estendere l'area sensibile tramite padding trasparente (hitSlop) mantenendo almeno 8pt/dp di distanza tra target adiacenti.  
* Prevenzione degli Errori (Azioni Critiche): Per operazioni irreversibili, transazioni finanziarie o invio di dati con valore legale, prevedere sempre una schermata di riepilogo/conferma prima dell'invio definitivo e consentire la modifica dei dati inseriti.  
  • Alternativa ai Gesti Complessi: Nessuna funzionalità DEVE dipendere esclusivamente da gesti complessi (es. drag-and-drop, swipe laterali, pinch o scuotimento del dispositivo). Prevedere sempre un'alternativa azionabile con un singolo tocco semplice (es. azioni contestuali visibili).   
* Regolazione dei Limiti di Tempo (WCAG 2.2.1): Se un flusso prevede una scadenza temporale (es. timeout di sessione o operazioni di pagamento), avvisare l'utente prima della scadenza e fornire un controllo semplice per estendere o disabilitare il limite di tempo.  
* Comportamento Prevedibile su Input (WCAG 3.2.2): La selezione di un'opzione (radio button, checkbox, dropdown) o la compilazione di un campo NON DEVE innescare cambi automatici di schermata o spostamenti improvvisi di focus senza preavviso esplicito.  
* Alternativa all'Autenticazione Biometrica (UNI CEI EN 301 549 Cap. 5.3): Quando un componente o un flusso richiede l'identificazione biometrica (es. Face ID, impronta digitale per sblocco app o autorizzazione pagamenti), DEVE sempre offrire un meccanismo alternativo accessibile non biometrico (es. inserimento PIN).

4\. Semantica, Screen Reader e Ordine di Lettura

* Ordine di Focus (Reading Order): La navigazione tramite scorrimento (swipe) con VoiceOver e TalkBack DEVE seguire un ordine logico e sequenziale dall'alto verso il basso e da sinistra a destra, rispecchiando la gerarchia visiva.  
* Ruoli e Stati Nativi: Dichiarare sempre il ruolo semantico corretto (Button, Link, Header, Text, Checkbox, Radio) e gli stati dinamici tramite accessibilityState (selected, disabled, checked, busy, expanded).  
* Gestione delle Modali e Bottom Sheet: Quando una modale o un bottom sheet è aperto, DEVE intrappolare il focus al proprio interno (accessibilityViewIsModal={true}), impedendo allo screen reader di leggere gli elementi sottostanti. Alla chiusura, il focus deve tornare all'elemento che ha attivato la modale.  
* Annunci Dinamici: Quando compaiono messaggi di errore, conferme o cambi di stato dinamici senza spostamento di focus, attivare un annuncio vocale automatico tramite AccessibilityInfo.announceForAccessibility.  
* Gerarchia dei Titoli: Ogni schermata deve avere un titolo principale esposto con ruolo header (accessibilityRole="header") per consentire la navigazione rapida per intestazioni.  
* Distinzione tra Nome e Descrizione (Label vs Hint): Separare sempre il nome dell'elemento (accessibilityLabel, breve e identificativo dello scopo) dalle istruzioni aggiuntive (accessibilityHint, es. formato richiesto o effetto dell'azione), rispettando la sequenza nativa dello screen reader (Nome \-\> Ruolo \-\> Stato \-\> Hint).   
* Coerenza dei Componenti e dell'Aiuto (WCAG 3.2.4, 3.2.6): Componenti con la stessa funzione (es. pulsanti di chiusura, ricerca, filtri) e punti di accesso all'assistenza (FAQ, supporto) DEVONO mantenere la stessa posizione relativa e la stessa accessibilityLabel in tutte le schermate dell'app.  
* Privacy dei Dati Mascherati (UNI CEI EN 301 549 Cap. 4): Per garantire la privacy degli utenti che utilizzano tecnologie assistive, i campi di input sensibili o mascherati (es. PIN CIE, password, codici segreti) NON DEVONO mai esporre i caratteri in chiaro né farli pronunciare ad alta voce dallo screen reader.

 

5\. Immagini, Icone e Testi

* Classificazione delle Immagini e Icone:   
  * Decorative / Ridondanti: Icone di stato affiancate da testo esplicito o illustrazioni grafiche DEVONO essere nascoste alle tecnologie assistive (accessibilityElementsHidden={true} su iOS / importantForAccessibility="no" su Android).  
  * Funzionali (senza testo): Icone cliccabili (es. chiudi, condividi, info) DEVONO avere una accessibilityLabel che descrive l'azione (es. "Chiudi avviso"), non la forma dell'icona ("X").  
  * Informative / Complesse: Devono avere una descrizione sintetica che trasmetta il significato del dato (es. stato di un grafico).  
* Link e CTA Auto-esplicativi: Evitare etichette generiche isolate come "Scopri di più" o "Inizia". Se il testo visibile è breve, arricchire programmaticamente la accessibilityLabel includendo il contesto (es. "Scopri di più sulla manutenzione").  
* Form e Input: Ogni campo di testo deve avere una label visibile e associata programmaticamente (mai affidarsi al solo placeholder). Gli errori di validazione devono essere mostrati inline sotto al campo e annunciati dallo screen reader.  
* Lingua: Dichiarare la lingua principale dell'app e applicare accessibilityLanguage sulle singole parole o frasi in lingua straniera per garantire una pronuncia corretta.  
* Autocompilazione nei Form: Sui campi relativi a dati personali o codici (email, telefono, nome, indirizzo, codici OTP), configurare sempre gli attributi nativi di completamento automatico (textContentType su iOS e autoComplete su Android) per ridurre il carico cognitivo e motorio.  
* Avviso di Navigazione Esterna: Quando un link o una CTA apre una risorsa esterna all'app (es. browser di sistema o portale web esterno), informare anticipatamente l'utente includendo l'avviso nella accessibilityLabel (es. "Consulta il bando, apre nel browser esterno").   
* Divieto di Immagini di Testo e Riferimenti Sensoriali: NON utilizzare mai immagini contenenti testo (che non si adattano al Dynamic Type). Nelle istruzioni testuali, NON fare riferimento a caratteristiche sensoriali o spaziali (es. scrivere "Seleziona il pulsante Chiudi" anziché "Premi la X rossa in alto a destra").  
* Link a Documenti Scaricabili: Quando un link o un pulsante apre o scarica un documento (es. ricevute o avvisi), includere sempre il formato e il peso del file nell'etichetta accessibile (es. "Scarica ricevuta, PDF, 1,5 MB").  
* Zero Inserimento Ridondante e Autenticazione Accessibile (WCAG 3.3.7, 3.3.8): Nei form multi-step, pre-compilare automaticamente i dati già forniti dall'utente nello stesso flusso. Nei flussi di accesso e verifica (es. codici OTP, password), abilitare sempre il copia-incolla e l'autocompilazione di sistema senza blocchi cognitivi.  
* Contenuti Multimediali: Eventuali contenuti video o audio integrati nell'app DEVONO prevedere sottotitoli sincronizzati (captions) e una trascrizione testuale alternativa. 

6\. Movimento e Animazioni

* Rispetto di Reduce Motion: Verificare sempre la preferenza di sistema dell'utente tramite AccessibilityInfo.isReduceMotionEnabled. Quando attiva, sostituire transizioni complesse, effetti parallasse o illustrazioni animate (es. onboarding, schermate di successo) con dissolvenze statiche o frame fissi.  
* Limite di Lampeggiamento: Nessun elemento visivo o animazione DEVE lampeggiare o cambiare colore più di 3 volte al secondo, per prevenire crisi fotosensibili.  
* Animazioni Automatiche: Eventuali animazioni che partono in automatico e durano più di 5 secondi DEVONO prevedere un controllo per metterle in pausa, fermarle o nasconderle.  
* Controllo dell'Audio (WCAG 1.4.2): Nessun suono o traccia audio DEVE avviarsi automaticamente all'apertura di una schermata. Qualsiasi contenuto audio di durata superiore a 3 secondi deve offrire un controllo immediato per metterlo in pausa o silenziarlo senza abbassare il volume dello screen reader.

7\. Checklist di Validazione (Agent & Designer)

Prima dell'approvazione di un componente o di una schermata, verificare che:

- [ ] Tutti i testi rispettino il contrasto 4.5:1 (3.0:1 per testi grandi e icone) tramite token semantici.  
- [ ] Nessun testo venga troncato con ellissi al 200% di ingrandimento font di sistema.  
- [ ] Tutti i target interattivi misurino almeno 44x44pt (iOS) / 48x48dp (Android).  
- [ ] Le icone decorative siano nascoste allo screen reader e le icone funzionali abbiano una accessibilityLabel chiara.  
- [ ] L'ordine di lettura dello screen reader segua fedelmente il flusso visivo dall'alto verso il basso.  
- [ ] Gli stati dinamici (expanded, busy, disabled, selected) e gli annunci di errore siano esposti programmaticamente.  
- [ ] Le modali isolino il focus dal contenuto sottostante.  
- [ ] Le animazioni rispettano la preferenza di sistema Reduce Motion e non superano i 3 lampeggiamenti al secondo.  
- [ ] I gesti complessi (swipe, drag-and-drop) hanno un'alternativa a tocco singolo.  
- [ ] I campi di input personali supportano l'autocompilazione nativa e i link esterni avvisano dell'uscita dall'app.   
- [ ] Nome accessibile (accessibilityLabel) e descrizione aggiuntiva (accessibilityHint) sono separati correttamente senza istruzioni verbose nel nome.  
- [ ] Le istruzioni non si basano su posizione visiva, colore o forma ("in alto a destra", "icona rossa") e non esistono immagini di testo.  
- [ ] I link a documenti dichiarano formato e dimensione del file.  
- [ ] I flussi di inserimento dati evitano la ridigitazione (WCAG 3.3.7) e supportano sempre copia-incolla e autofill nei passaggi di autenticazione (WCAG 3.3.8).   
- [ ] Verifica Strumentale (Automatica \+ Manuale): Oltre ai controlli su Figma (Stark / Contrast Checker), testare il componente compilato su dispositivo reale o simulatore tramite Accessibility Inspector \+ VoiceOver su iOS e Accessibility Scanner \+ TalkBack su Android, verificando navigazione sequenziale (flick), attivazione (doppio tocco) ed esplorazione al tatto.

