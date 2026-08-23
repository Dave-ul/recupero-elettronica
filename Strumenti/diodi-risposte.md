---
tags: [recupero, elettronica, diodi, zener, risposte, orale]
fonte_ufficiale: "Scheda «Verifica di elettronica» — Prof. Carlo Carli, classe 4E (prima e seconda parte, domande aperte)"
libro_mirandola: "Mirandola Vol.2, Cap. 5 «I diodi», pp. 192-224"
versione_stampabile: "Strumenti/diodi-risposte.html — stessa dispensa impaginata per la cartellina"
prove: [orale, scritta]
---

# Il diodo a semiconduttore — Risposte alle domande aperte

> [!info] Dove serve
> **Orale Carli**: sono le risposte già scritte alle **D1–D23** della scheda di verifica, più la scheda di integrazione. Non vanno riscritte, vanno **ripetute a voce**. Il calendario le colloca nel ripasso del diodo — vedi [[Calendario]] e [[02 - Prova Orale Carli]].

Teoria completa: [[Diodi]] · esercizi: [[Esercizi - Diodi]] · schema per la cartellina: [[Cheat Sheet A4 visuale]].

## Indice

**Prima parte** — [[#D1 — Disegnare la struttura del diodo a semiconduttore fornendone una descrizione|D1 struttura]] · [[#D2 — Disegnare il simbolo circuitale di un diodo a semiconduttore fornendone una descrizione|D2 simbolo]] · [[#D3 — Dare la definizione di polarizzazione della giunzione PN|D3 polarizzazione]] · [[#D4 — Cosa s'intende per polarizzazione diretta?|D4 diretta]] · [[#D5 — Cosa s'intende per polarizzazione inversa?|D5 inversa]] · [[#D6 — Versi convenzionali di corrente e tensione sul simbolo|D6 versi convenzionali]] · [[#D7 — Mediante quale rappresentazione grafica si descrive il funzionamento ai morsetti del diodo?|D7 rappresentazione ai morsetti]] · [[#D8 — Disegnare la curva caratteristica, mettendo in risalto zona DIRETTA e zona INVERSA|D8 curva e zone]] · [[#D9 — Descrivere la curva caratteristica e il significato di tutte le grandezze|D9 grandezze]] · [[#D10 — Il diodo è un componente lineare? Giustificare la risposta|D10 linearità]] · [[#D11 — Espressione matematica della caratteristica a destra del breakdown, con legenda|D11 Shockley]] · [[#D12 — Perché si fa riferimento a modelli equivalenti approssimati?|D12 perché i modelli]]

**Seconda parte** — [[#D13 — I tre modelli equivalenti approssimati (A, B, C)|D13 i tre modelli]] · [[#D14 — Dare la definizione di raddrizzatore, mettendo in luce la sua importanza|D14 raddrizzatore]] · [[#D15 — Raddrizzatori a singola e a doppia semionda, con le forme d'onda|D15 semionda e onda intera]] · [[#D16 — Definizione di limitatore e suoi utilizzi|D16 limitatore]] · [[#D17 — Circuiti limitatori a bassa soglia e forme d'onda|D17 bassa soglia]] · [[#D18 — Qual è lo scopo di collegare più diodi in serie o in antiparallelo?|D18 serie e antiparallelo]] · [[#D19 — Disegnare i circuiti limitatori con diodi in serie e in antiparallelo|D19 schemi limitatori]] · [[#D20 — Simbolo e curva caratteristica del diodo Zener, zona di lavoro e impieghi|D20 Zener]] · [[#D21 — I due meccanismi che consentono il passaggio della corrente dal catodo all'anodo|D21 valanga e tunnel]] · [[#D22 — Dare la definizione di stabilizzatore o regolatore di tensione|D22 stabilizzatore]] · [[#D23 — Schema più semplice di regolatore, con le espressioni matematiche|D23 regolatore Zener]]

**Integrazione** — [[#D6★ — Che cosa rappresenta la tensione di soglia di un diodo?|D6★ tensione di soglia]] · [[#Corrispondenza fra la scheda «Verifica» (D1–D16) e queste risposte|corrispondenza con la scheda]]

---

## Prima parte · D1 – D12

### D1 — Disegnare la struttura del diodo a semiconduttore fornendone una descrizione

![[diodi-fig-01.svg]]
*Fig. 1 — Struttura interna del diodo a giunzione: un unico cristallo drogato P da un lato e N dall'altro.*

Il diodo a semiconduttore è un componente **a due terminali** costituito da un **unico cristallo di semiconduttore** (quasi sempre silicio, più raramente germanio) drogato in modo **non uniforme**:

- una metà è drogata con *impurità trivalenti* (accettori: boro, gallio, indio) e diventa una **regione di tipo P**, in cui i portatori di carica maggioritari sono le **lacune** (cariche positive) e i minoritari sono gli elettroni;
- l'altra metà è drogata con *impurità pentavalenti* (donatori: fosforo, arsenico, antimonio) e diventa una **regione di tipo N**, in cui i maggioritari sono gli **elettroni liberi** e i minoritari le lacune.

La superficie di separazione fra le due regioni è la **giunzione PN**. Non si tratta di due pezzi incollati, ma di un unico reticolo cristallino continuo: solo così la giunzione funziona.

**Cosa succede subito dopo la formazione della giunzione.** Per la forte differenza di concentrazione, gli elettroni della zona N **diffondono** verso la zona P e le lacune della zona P verso la zona N, ricombinandosi a coppie. Nella fascia a cavallo della giunzione spariscono quindi i portatori mobili e restano scoperti gli **ioni fissi** del reticolo: ioni negativi dalla parte P (accettori che hanno acquistato un elettrone) e ioni positivi dalla parte N (donatori che ne hanno perso uno).

Si forma così la **regione di svuotamento** (o zona di carica spaziale, o regione di deplezione), praticamente priva di cariche mobili, sede di un **campo elettrico interno** diretto da N verso P. A questo campo corrisponde una **barriera di potenziale** $V_0$ pari a circa **0,6 ÷ 0,7 V** nel silicio e **0,2 ÷ 0,3 V** nel germanio, che si oppone a un'ulteriore diffusione: il sistema raggiunge l'equilibrio e, in assenza di tensioni esterne, **la corrente complessiva è nulla**.

I due terminali metallici sono saldati alle estremità del cristallo con **contatti ohmici** (non raddrizzanti): il terminale collegato alla regione P si chiama **anodo (A)**, quello collegato alla regione N **catodo (K)**. Sul contenitore reale il catodo è individuato da un **anello** stampigliato.

### D2 — Disegnare il simbolo circuitale di un diodo a semiconduttore fornendone una descrizione

![[diodi-fig-02.svg]]
*Fig. 2 — Simbolo circuitale del diodo a semiconduttore.*

Il simbolo è formato da **due elementi**:

- un **triangolo pieno**, collegato al terminale di **anodo**, cioè alla regione P;
- una **barretta trasversale** appoggiata al vertice del triangolo, collegata al terminale di **catodo**, cioè alla regione N.

Il simbolo è **mnemonico**, cioè ricorda il funzionamento del componente: il triangolo va letto come una **freccia** e indica il verso in cui la **corrente convenzionale** può attraversare il diodo, cioè **dall'anodo al catodo**; la barretta va letta come una **parete** che sbarra il passaggio nel verso opposto (dal catodo all'anodo).

Il diodo è quindi un **componente polarizzato**: non è simmetrico e non può essere inserito in un circuito in un verso qualsiasi. Invertire anodo e catodo non è un errore trascurabile, cambia completamente il funzionamento del circuito.

### D3 — Dare la definizione di polarizzazione della giunzione PN

**Polarizzare una giunzione PN significa applicare dall'esterno una tensione continua ai suoi terminali**, alterando in questo modo la condizione di equilibrio in cui la giunzione si trova quando è isolata.

La tensione esterna si sovrappone alla barriera di potenziale interna $V_0$ e, a seconda del **segno con cui viene applicata**, può **abbassarla** o **innalzarla**, modificando di conseguenza la larghezza della regione di svuotamento e la corrente che attraversa il dispositivo. Si distinguono perciò due modi di polarizzare la giunzione, che danno luogo a comportamenti opposti:

- **polarizzazione diretta** (potenziale maggiore sulla zona P);
- **polarizzazione inversa** (potenziale maggiore sulla zona N).

La polarizzazione è dunque il modo in cui si «predispone» il diodo a lavorare: è ciò che stabilisce il **punto di lavoro** del componente sulla sua curva caratteristica.

### D4 — Cosa s'intende per polarizzazione diretta?

![[diodi-fig-03.svg]]
*Fig. 3 — Le due polarizzazioni a confronto: circuiti e comportamento della giunzione.*

Si ha **polarizzazione diretta** quando il generatore esterno è collegato con il **polo positivo alla regione P (anodo)** e il **polo negativo alla regione N (catodo)**, cioè quando $V_A > V_K$ e quindi $V_D > 0$.

**Effetti sulla giunzione:**

- il campo elettrico prodotto dal generatore è **opposto** a quello interno della giunzione, quindi la **barriera di potenziale si abbassa** (diventa $V_0 - V$);
- di conseguenza la **regione di svuotamento si restringe** e diventa meno «isolante»;
- i **portatori maggioritari** (lacune dalla P, elettroni dalla N) hanno energia sufficiente per attraversare la giunzione e si stabilisce una **corrente diretta $I_D$ di valore elevato**, dell'ordine dei mA o degli A, sostenuta dal generatore.

Finché la tensione applicata resta **al di sotto della tensione di soglia $V_\gamma$** ($\approx 0{,}7\ \text{V}$ per il silicio) la barriera non è ancora sufficientemente abbattuta e la corrente è praticamente trascurabile. Superata $V_\gamma$, la corrente **cresce in modo esponenziale** mentre la tensione ai capi del diodo rimane quasi bloccata attorno a 0,7 V: il diodo si comporta **quasi come un corto circuito**, cioè come un **interruttore chiuso**. Si dice che il diodo è **ON**, in conduzione.

> [!warning] Attenzione pratica
> Poiché in conduzione il diodo non limita la corrente, è **sempre necessaria una resistenza di limitazione $R$ in serie**, altrimenti la corrente cresce fino a distruggere il componente per effetto Joule.

### D5 — Cosa s'intende per polarizzazione inversa?

Si ha **polarizzazione inversa** quando il generatore esterno è collegato con il **polo positivo alla regione N (catodo)** e il **polo negativo alla regione P (anodo)**, cioè quando $V_A < V_K$ e quindi $V_D < 0$ (vedi Fig. 3, a destra).

**Effetti sulla giunzione:**

- il campo elettrico esterno è **concorde** con quello interno, quindi la **barriera di potenziale si innalza** (diventa $V_0 + V$);
- la **regione di svuotamento si allarga**, perché il generatore richiama verso l'esterno i portatori maggioritari, allontanandoli dalla giunzione;
- i maggioritari **non riescono più ad attraversare** la giunzione: la corrente dovuta a essi si annulla.

Rimane una piccolissima corrente, la **corrente inversa di saturazione $I_S$**, dovuta ai **portatori minoritari** generati termicamente nelle due regioni: per loro il campo della giunzione non è un ostacolo ma un aiuto. $I_S$ ha valori dell'ordine dei **nA** (silicio) o dei µA (germanio), è **praticamente indipendente dal valore della tensione inversa** ma **fortemente dipendente dalla temperatura** (raddoppia circa ogni 10 °C di aumento).

In pratica, in polarizzazione inversa il diodo si comporta **come un circuito aperto**, cioè come un **interruttore aperto**: si dice che è **OFF**, interdetto. Questo vale però solo fino a un valore limite di tensione: superata la **tensione di breakdown $V_{BR}$**, la corrente inversa cresce bruscamente e, se non è limitata dall'esterno, distrugge il componente.

### D6 — Versi convenzionali di corrente e tensione sul simbolo

> Domanda per esteso: «Considerando il simbolo di un diodo al silicio, mettere in luce il verso che si usa per convenzione per i versi della corrente e della tensione nel simbolo stesso».

![[diodi-fig-04.svg]]
*Fig. 4 — Versi convenzionali positivi di corrente e tensione sul simbolo del diodo.*

Sul simbolo si adotta la **convenzione degli utilizzatori** (il diodo è un componente passivo che assorbe potenza), cioè si scelgono i versi positivi in modo che **la corrente entri dal morsetto a potenziale maggiore**:

- **Corrente $I_D$**: si assume positiva quando **entra dall'anodo ed esce dal catodo**, cioè quando ha lo stesso verso indicato dal triangolo del simbolo (da A verso K).
- **Tensione $V_D$**: si assume positiva quando il **+ è sull'anodo** e il **– sul catodo**; formalmente $V_D = V_A - V_K$.

Questa scelta è comodissima perché rende **coerente il segno con lo stato di funzionamento**:

- polarizzazione **diretta** → $V_D > 0$ e $I_D > 0$ → il punto di lavoro sta nel **primo quadrante** del piano V–I;
- polarizzazione **inversa** → $V_D < 0$ e $I_D < 0$ (piccolissima, pari a $-I_S$) → punto di lavoro nel **terzo quadrante**.

Se dai calcoli risulta un valore **negativo** di $I_D$ in un circuito in cui si era ipotizzata la conduzione, significa che **l'ipotesi era sbagliata** e che in realtà il diodo è interdetto.

### D7 — Mediante quale rappresentazione grafica si descrive il funzionamento ai morsetti del diodo?

Il funzionamento ai morsetti si descrive mediante la **curva caratteristica tensione–corrente** (detta anche **caratteristica statica** o **caratteristica V–I**), cioè il grafico della funzione

$$I_D = f(V_D)$$

tracciato sul **piano cartesiano V–I**, con la tensione $V_D$ sull'asse delle ascisse e la corrente $I_D$ sull'asse delle ordinate.

Il grande vantaggio di questa rappresentazione è che descrive **completamente il comportamento esterno del componente**: per usare il diodo in un circuito non serve conoscere che cosa succede fisicamente dentro la giunzione, basta sapere quale corrente circola per ogni valore di tensione applicata. È la stessa logica del «**modello a scatola nera**»: si guarda solo ciò che accade ai due morsetti.

La curva è ricavabile sperimentalmente punto per punto (alimentando il diodo e misurando V e I) oppure si trova già tracciata nel **data sheet** del costruttore; è inoltre lo strumento su cui si esegue l'**analisi grafica con la retta di carico**, per determinare il punto di lavoro Q del diodo in un circuito.

### D8 — Disegnare la curva caratteristica, mettendo in risalto zona DIRETTA e zona INVERSA

![[diodi-fig-05.svg]]
*Fig. 5 — Curva caratteristica del diodo: zona diretta (rosso), zona inversa e zona di breakdown (blu).*

La curva si sviluppa in **due quadranti**, coerentemente con i versi convenzionali della domanda D6:

- **Zona di polarizzazione diretta — I quadrante** ($V_D > 0$, $I_D > 0$). Per tensioni comprese fra 0 e $V_\gamma$ la corrente è ancora trascurabile; in corrispondenza del **ginocchio** la curva «si alza» e da lì in poi diventa quasi **verticale**: piccolissime variazioni di tensione producono grandissime variazioni di corrente. È la zona in cui il diodo **conduce**.
- **Zona di polarizzazione inversa — III quadrante** ($V_D < 0$, $I_D < 0$). La curva è praticamente **orizzontale e schiacciata sull'asse delle tensioni**, a un valore costante e minuscolo pari a $-I_S$. È la zona in cui il diodo è **interdetto**.
- **Zona di breakdown** — parte terminale del III quadrante. Raggiunta la tensione $-V_{BR}$ la curva **precipita verso il basso**: la corrente inversa aumenta bruscamente in modulo pur restando la tensione quasi costante.

> [!note] Osservazione sui grafici reali
> Le scale dei due semiassi **non sono le stesse**. In diretta si usano mA o A e frazioni di volt; in inversa nA o µA e decine o centinaia di volt. Senza questo accorgimento la parte inversa della curva sarebbe indistinguibile dall'asse.

### D9 — Descrivere la curva caratteristica e il significato di tutte le grandezze

La curva mostra, per ogni valore di tensione applicata ai morsetti, la corrente che percorre il diodo. Percorrendola da destra verso sinistra si incontrano **quattro tratti**: conduzione diretta, ginocchio, interdizione inversa, breakdown. Le grandezze che vi compaiono sono:

| Grandezza | Nome | Significato | Valori tipici (Si) |
|---|---|---|---|
| $V_D$ | tensione ai morsetti | differenza di potenziale anodo–catodo; ascissa della curva | — |
| $I_D$ | corrente nel diodo | corrente che attraversa il componente da A a K; ordinata della curva | — |
| $V_\gamma$ | tensione di soglia (cut-in, di ginocchio) | tensione oltre la quale il diodo entra in piena conduzione | 0,6 ÷ 0,7 V (0,2 ÷ 0,3 V nel Ge) |
| $I_S$ | corrente inversa di saturazione | corrente dei portatori minoritari in polarizzazione inversa; costante rispetto a V, raddoppia ogni ≈10 °C | nA ÷ µA |
| $V_{BR}$ | tensione di breakdown (di rottura) | tensione inversa oltre la quale la corrente cresce bruscamente | 50 ÷ 1000 V |
| $r_D$ | resistenza differenziale (dinamica) | $r_D = \Delta V_D / \Delta I_D$ — inverso della pendenza nel punto di lavoro; misura quanto il tratto di conduzione si discosta dalla verticale | 1 ÷ 20 Ω |
| $Q$ | punto di lavoro | coppia $(V_{DQ}, I_{DQ})$ in cui il diodo lavora effettivamente nel circuito | — |

**Descrizione tratto per tratto:**

- $0 < V_D < V_\gamma$ — la barriera di potenziale non è ancora abbattuta: la corrente esiste ma è così piccola da essere trascurabile alla scala del grafico. Il diodo è ancora praticamente interdetto.
- $V_D \approx V_\gamma$ — *ginocchio*: è la zona di transizione in cui la curva cambia rapidamente pendenza.
- $V_D > V_\gamma$ — la corrente cresce con legge **esponenziale**; la caratteristica è quasi verticale e la tensione ai capi del diodo resta «inchiodata» attorno a 0,7 V qualunque sia la corrente. Questa proprietà è alla base dell'uso del diodo come riferimento di tensione grossolano e dei modelli approssimati.
- $-V_{BR} < V_D < 0$ — corrente costante e pari a $-I_S$: il diodo blocca.
- $V_D \le -V_{BR}$ — breakdown: la corrente inversa aumenta rapidissimamente. Per un diodo raddrizzatore normale è una condizione **distruttiva**; per il diodo Zener, invece, è la **zona di lavoro voluta**.

### D10 — Il diodo è un componente lineare? Giustificare la risposta

**No: il diodo è un componente NON lineare** (e per di più **unidirezionale**, cioè polarizzato).

**Giustificazione.** Un bipolo si dice lineare quando la sua caratteristica V–I è una **retta passante per l'origine**, cioè quando vale la legge di Ohm con resistenza costante ($V = R \cdot I$ con $R$ costante). Nel diodo questo non accade per tre motivi:

1. **La caratteristica non è una retta ma un'esponenziale.** Il legame fra tensione e corrente è $I_D = I_S\left(e^{V_D/(\eta V_T)} - 1\right)$: il rapporto $V_D / I_D$ **cambia da punto a punto**, quindi non esiste una «resistenza del diodo» unica. Si può parlare solo di resistenza statica ($V_{DQ}/I_{DQ}$) o differenziale ($\Delta V / \Delta I$), entrambe valide soltanto nell'intorno di un preciso punto di lavoro.
2. **Il comportamento dipende dal verso della tensione.** Applicando +5 V si ottiene una corrente di parecchi mA, applicando −5 V si ottengono pochi nA: il componente **non è simmetrico**, mentre un resistore lineare dà correnti uguali e opposte per tensioni uguali e opposte.
3. **Non valgono i principi che definiscono la linearità**, cioè l'omogeneità (raddoppiando la tensione **non** raddoppia la corrente) e la **sovrapposizione degli effetti**. Di conseguenza **non si possono applicare direttamente i teoremi delle reti lineari** (sovrapposizione, Thévenin, Norton) ai circuiti che contengono diodi.

È proprio la non linearità a rendere utile il diodo: raddrizzare, limitare, rivelare, stabilizzare sono tutte operazioni che un componente lineare **non potrebbe mai svolgere**. Il prezzo da pagare è la difficoltà di calcolo, che si aggira con l'analisi grafica (retta di carico) o con i **modelli lineari a tratti** delle domande D12 e D13.

### D11 — Espressione matematica della caratteristica a destra del breakdown, con legenda

Per tutti i valori di tensione **a destra di $-V_{BR}$** (cioè escludendo la zona di rottura) la caratteristica è descritta dall'**equazione di Shockley**:

$$I_D = I_S\left(e^{\frac{V_D}{\eta\,V_T}} - 1\right) \qquad \text{con}\quad V_T = \frac{kT}{q} \approx 26\ \text{mV} \ \text{a}\ T = 300\ \text{K}$$

**Legenda delle grandezze:**

- $I_D$ — corrente che attraversa il diodo, in ampere [A]; positiva se entrante nell'anodo.
- $V_D$ — tensione applicata ai morsetti del diodo, in volt [V]; positiva in polarizzazione diretta, negativa in inversa.
- $I_S$ — **corrente inversa di saturazione** [A]. Dipende dal materiale, dal drogaggio, dall'area della giunzione e fortemente dalla temperatura; è dell'ordine dei nA nel silicio.
- $\eta$ (in alcuni testi $n$) — **coefficiente di emissione** o fattore di idealità, numero puro compreso fra **1 e 2**. Vale circa 2 per i diodi al silicio a basse correnti e tende a 1 alle correnti elevate e per il germanio; tiene conto degli scostamenti del diodo reale dal comportamento ideale.
- $V_T$ — **tensione (o potenziale) termico** [V]: $V_T = kT/q$. A temperatura ambiente ($T \approx 300\ \text{K}$, cioè 27 °C) vale **circa 26 mV**.
- $k$ — costante di Boltzmann, $k = 1{,}38 \cdot 10^{-23}\ \text{J/K}$.
- $T$ — temperatura **assoluta** della giunzione, in kelvin [K].
- $q$ — carica elementare dell'elettrone, $q = 1{,}602 \cdot 10^{-19}\ \text{C}$.

**Verifica del modello nei due casi.**

- **Polarizzazione diretta**: se $V_D > 0$ e $V_D \gg V_T$, l'esponenziale diventa molto maggiore di 1 e si ha $I_D \approx I_S\,e^{V_D/(\eta V_T)}$: la corrente cresce esponenzialmente, come mostra il ramo del primo quadrante.
- **Polarizzazione inversa**: se $V_D < 0$ e $|V_D| \gg V_T$, l'esponenziale tende a 0 e resta $I_D \approx -I_S$: corrente costante e negativa, indipendente dalla tensione. Da qui il nome «corrente di saturazione».

> [!note] Perché «a destra della tensione di breakdown»
> L'equazione di Shockley descrive i soli fenomeni di diffusione dei portatori attraverso la giunzione e **non contiene alcun termine capace di descrivere la valanga o l'effetto tunnel**. Per $V_D \le -V_{BR}$ essa continuerebbe a prevedere una corrente pari a $-I_S$, in totale contrasto con la realtà: perciò la sua validità si ferma a destra del breakdown.

### D12 — Perché si fa riferimento a modelli equivalenti approssimati?

Perché usare l'equazione esatta è, nella pratica progettuale, **scomodo, spesso impossibile e quasi sempre inutile**. Le ragioni sono cinque:

1. **Difficoltà matematica.** L'equazione di Shockley è **trascendente**: inserendola nelle equazioni di Kirchhoff di un circuito si ottiene un sistema con un'incognita che compare sia come esponente sia fuori dall'esponenziale, **non risolvibile per via algebrica**. Servirebbero metodi iterativi o numerici, del tutto sproporzionati a un normale calcolo di circuito.
2. **Impossibilità di usare i teoremi delle reti lineari.** Finché in rete c'è un elemento non lineare non si possono applicare sovrapposizione degli effetti, Thévenin, Norton. **Linearizzando il diodo a tratti**, ogni tratto diventa una rete lineare e tutti gli strumenti già noti tornano utilizzabili.
3. **Incertezza sui parametri.** $I_S$ e $\eta$ **non sono noti con precisione**, variano con la temperatura, con l'invecchiamento e **da esemplare a esemplare** dello stesso tipo (tolleranze di costruzione). Un calcolo «esatto» basato su dati incerti dà un risultato apparentemente preciso ma in realtà falso.
4. **Nella maggior parte dei circuiti serve solo sapere se il diodo conduce o no.** In un raddrizzatore, in un limitatore, in un circuito logico a diodi, l'informazione utile è lo stato ON/OFF; la forma esatta del ginocchio è irrilevante.
5. **L'errore introdotto è accettabile.** Quando le tensioni in gioco sono molto maggiori di $V_\gamma$ (per esempio 12 V rispetto a 0,7 V) e le resistenze di circuito sono molto maggiori di $r_D$ (kΩ rispetto a pochi Ω), l'approssimazione comporta un errore **di pochi punti percentuali**, ampiamente entro le tolleranze dei componenti reali.

In sintesi: i modelli approssimati **sostituiscono al diodo un insieme di componenti lineari ideali** (interruttore, generatore, resistore), rendendo il calcolo rapido, eseguibile a mano e sufficientemente accurato. Si sceglie di volta in volta il modello meno complicato che garantisce la precisione richiesta.

---

## Seconda parte · D13 – D23

### D13 — I tre modelli equivalenti approssimati (A, B, C)

> Domanda per esteso: «Disegnare e descrivere i tre modelli equivalenti approssimati di un diodo reale (Modello A, B, C), in polarizzazione diretta e inversa, con la curva caratteristica, sottolineando da quali considerazioni dipende la scelta».

![[diodi-fig-06.svg]]
*Fig. 6 — I tre modelli equivalenti approssimati e le rispettive caratteristiche linearizzate.*

Tutti e tre i modelli sostituiscono al diodo reale una **rete di componenti lineari ideali**, diversa a seconda che il diodo sia in conduzione o interdetto. **In polarizzazione inversa tutti e tre coincidono**: il diodo è un **interruttore aperto** (si trascura $I_S$, che è dell'ordine dei nA).

**Modello A — interruttore + generatore $V_\gamma$ + resistore $r_D$** (il più completo).
In conduzione il diodo è rappresentato da un interruttore chiuso in serie a un generatore di tensione costante $V_\gamma \approx 0{,}7\ \text{V}$ e a una resistenza $r_D$ (resistenza differenziale, tipicamente 1 ÷ 20 Ω). La tensione ai suoi capi vale $V_D = V_\gamma + r_D I_D$: cresce, sia pur di poco, al crescere della corrente. La caratteristica è una **semiretta inclinata** che parte da $V_\gamma$ con pendenza $1/r_D$. È il modello che meglio riproduce il diodo reale.

**Modello B — interruttore + generatore $V_\gamma$** (il più usato).
Si trascura $r_D$: in conduzione il diodo è un interruttore chiuso in serie al solo generatore $V_\gamma$, quindi $V_D = V_\gamma = \text{costante}$ qualunque sia la corrente. La caratteristica è una **semiretta verticale** a partire da $V_\gamma$. È il compromesso migliore fra semplicità e precisione ed è quello normalmente adottato nell'analisi dei circuiti.

**Modello C — diodo ideale** (il più semplice).
Si trascurano sia $r_D$ sia $V_\gamma$: il diodo diventa un **puro interruttore comandato dalla tensione**, chiuso (corto circuito, $V_D = 0$) quando è polarizzato direttamente, aperto (circuito aperto, $I_D = 0$) quando è polarizzato inversamente. La caratteristica **coincide con i due semiassi positivi**. Serve per l'analisi qualitativa rapida e per capire il funzionamento logico di un circuito.

| Modello | Conduzione | Interdizione | $V_D$ in conduzione | Precisione |
|---|---|---|---|---|
| **A** | interruttore chiuso + $V_\gamma$ + $r_D$ | interruttore aperto | $V_\gamma + r_D I_D$ | alta |
| **B** | interruttore chiuso + $V_\gamma$ | interruttore aperto | $V_\gamma \approx 0{,}7\ \text{V}$ | media (la più usata) |
| **C** | interruttore chiuso | interruttore aperto | 0 V | bassa (qualitativa) |

**Da quali considerazioni dipende la scelta del modello:**

- **Rapporto fra le tensioni in gioco e $V_\gamma$.** Se la tensione di alimentazione è molto maggiore di 0,7 V (per esempio 24 V), i 0,7 V sono un errore inferiore al 3 % e si può usare il **modello C**. Se invece si lavora con segnali di pochi volt o con frazioni di volt, $V_\gamma$ è determinante e occorre almeno il **modello B**.
- **Rapporto fra $r_D$ e le resistenze del circuito.** Se le resistenze esterne sono dell'ordine dei kΩ, $r_D$ (pochi ohm) è del tutto trascurabile e il modello B basta; se invece le resistenze in gioco sono confrontabili con $r_D$ (circuiti a bassa impedenza, forti correnti) serve il **modello A**.
- **Precisione richiesta e scopo dell'analisi.** Per un dimensionamento di massima o per capire il funzionamento è sufficiente il modello più semplice; per un calcolo di progetto, per la valutazione della potenza dissipata o della caduta effettiva serve il modello più accurato.
- **Dati realmente disponibili.** Se il data sheet non fornisce $r_D$, usare il modello A darebbe una falsa precisione.

> [!tip] Regola pratica
> Si sceglie sempre il **modello più semplice che garantisce l'accuratezza richiesta**. Complicare il modello oltre il necessario aumenta i calcoli senza migliorare davvero il risultato, perché l'incertezza sui componenti reali resta comunque dominante.

### D14 — Dare la definizione di raddrizzatore, mettendo in luce la sua importanza

**Definizione.** Il **raddrizzatore** è un circuito che, sfruttando l'unidirezionalità del diodo, **converte una tensione alternata** (bidirezionale, che cambia periodicamente di segno e ha valor medio nullo) **in una tensione unidirezionale**, cioè di un solo segno, «pulsante», dotata di un **valor medio diverso da zero**.

Il raddrizzatore da solo **non produce ancora una tensione continua**: l'uscita è unidirezionale ma variabile nel tempo. Per ottenere la continua occorrono gli stadi successivi (filtro e stabilizzatore).

**Importanza.**

- È il **primo stadio attivo di ogni alimentatore in corrente continua**. La catena tipica è: **trasformatore → raddrizzatore → filtro (condensatore) → stabilizzatore → carico**.
- Risolve un problema fondamentale: l'energia elettrica viene **distribuita in alternata** (perché è facile trasformarla e trasportarla), mentre **quasi tutta l'elettronica funziona in continua** (semiconduttori, circuiti integrati, microprocessori). Il raddrizzatore è il ponte fra i due mondi.
- È presente in **praticamente ogni apparecchio alimentato dalla rete**: alimentatori di PC, caricabatterie, alimentatori a spina, televisori.
- Trova impiego anche in applicazioni non di alimentazione: **rivelatore d'inviluppo** nei ricevitori AM, circuiti di misura del valor medio, saldatrici, processi galvanici.

### D15 — Raddrizzatori a singola e a doppia semionda, con le forme d'onda

![[diodi-fig-07.svg]]
*Fig. 7 — Raddrizzatore a singola semionda e a doppia semionda a ponte, con le rispettive forme d'onda.*

**1) Raddrizzatore a singola semionda (a una semionda).**
È costituito da **un solo diodo in serie al carico $R_L$**, alimentato dal secondario del trasformatore.

- **Semionda positiva**: il diodo è polarizzato direttamente, conduce e si comporta quasi da corto circuito. Il segnale passa al carico: $v_o = v_i - V_\gamma$.
- **Semionda negativa**: il diodo è polarizzato inversamente, è interdetto e non passa corrente: $v_o = 0$. L'intera tensione d'ingresso si ritrova ai capi del diodo, che deve quindi sopportare una tensione inversa di picco pari a $V_{max}$ (parametro **PIV**, *Peak Inverse Voltage*).

$$V_{o,med} = \frac{V_{max}}{\pi} \approx 0{,}318 \cdot V_{max} \qquad f_{ripple} = f_{rete} = 50\ \text{Hz}$$

Vantaggi: semplicissimo ed economico. Svantaggi: metà del tempo l'uscita è nulla, il valor medio è basso, il ripple è grande e alla frequenza di rete, quindi il filtraggio richiede condensatori molto grandi; il trasformatore è sfruttato male.

**2) Raddrizzatore a doppia semionda (a onda intera).** Esistono due realizzazioni:

- **A ponte di Graetz** (schema disegnato): **quattro diodi** disposti a rombo. In ogni semionda conducono **due diodi opposti** in serie mentre gli altri due sono interdetti, e la corrente attraversa il carico **sempre nello stesso verso**. Anche la semionda negativa viene quindi «ribaltata» verso l'alto. La caduta sui diodi è $2V_\gamma \approx 1{,}4\ \text{V}$ perché ce ne sono due in serie. Non richiede trasformatore a presa centrale.
- **Con trasformatore a presa centrale**: due soli diodi e un secondario con presa centrale a massa; ogni diodo lavora su una metà dell'avvolgimento. La caduta è di un solo $V_\gamma$, ma serve un trasformatore speciale e ogni diodo deve sopportare una tensione inversa doppia.

$$V_{o,med} = \frac{2V_{max}}{\pi} \approx 0{,}637 \cdot V_{max} \qquad f_{ripple} = 2 f_{rete} = 100\ \text{Hz}$$

**Vantaggi della doppia semionda:** valor medio doppio; migliore rendimento e migliore sfruttamento del trasformatore; ripple di frequenza doppia e ampiezza minore, quindi **filtraggio molto più facile** (bastano condensatori più piccoli). Per questi motivi è la soluzione praticamente sempre adottata negli alimentatori.

### D16 — Definizione di limitatore e suoi utilizzi

**Definizione.** Il **limitatore** (in inglese *clipper*, «tosatore») è un circuito che **impedisce alla tensione di uscita di superare uno o due livelli di soglia prefissati**, «tagliando» le parti della forma d'onda che eccedono tali livelli e lasciando invece **inalterata** la porzione di segnale compresa entro le soglie.

In altre parole, il limitatore **non modifica la forma del segnale nella zona di funzionamento normale**, ma interviene solo quando l'ampiezza diventa eccessiva. Può essere **unilaterale** (limita solo i valori positivi o solo i negativi) o **bilaterale/simmetrico** (limita entrambi).

**Utilizzi.**

- **Protezione degli ingressi** di circuiti, strumenti di misura, amplificatori, porte logiche e ingressi di microcontrollori da **sovratensioni** accidentali, che li danneggerebbero irreparabilmente. È l'impiego più importante.
- **Sagomatura delle forme d'onda** (*wave shaping*): tagliando le creste di una sinusoide di grande ampiezza si ottiene una forma d'onda **quasi rettangolare**, utile per generare segnali di clock o di sincronismo.
- **Eliminazione dei disturbi impulsivi** (rumore, spike) che superano una certa ampiezza, senza alterare il segnale utile.
- **Selezione di ampiezza**: lasciare passare solo le porzioni di segnale al di sotto o al di sopra di un livello.
- **Adattamento della dinamica** del segnale al campo di ingresso ammesso da un convertitore analogico-digitale (ADC), evitando di eccedere il fondo scala.
- **Protezione da scariche elettrostatiche (ESD)** nei circuiti integrati, dove i diodi di clamp sono integrati su ogni pin.

### D17 — Circuiti limitatori a bassa soglia e forme d'onda

![[diodi-fig-08.svg]]
*Fig. 8 — Limitatore a bassa soglia con un solo diodo verso massa, e relative forme d'onda.*

Si chiamano **limitatori a bassa soglia** i limitatori in cui **la soglia di taglio è fissata unicamente dalla tensione di soglia $V_\gamma$ dei diodi**, senza ricorrere a generatori di polarizzazione ausiliari in serie ai diodi. La soglia risulta perciò «bassa», dell'ordine di **0,7 V** (o di un suo multiplo, se i diodi sono più d'uno in serie).

**Struttura del circuito.** È formato da:

- una **resistenza $R$ in serie** fra ingresso e uscita, che ha la doppia funzione di limitare la corrente nel diodo e di «assorbire» la differenza fra tensione d'ingresso e tensione limitata;
- un **diodo (o gruppo di diodi) collegato in parallelo all'uscita, verso massa**, che costituisce l'elemento limitatore vero e proprio.

**Funzionamento (riferito allo schema disegnato).**

- **Finché $v_i < V_\gamma$**: il diodo è polarizzato direttamente ma non oltre la soglia, quindi è **interdetto** e si comporta da circuito aperto. Nel ramo di $R$ non circola corrente (l'uscita si suppone a vuoto o su carico ad alta impedenza), quindi **non c'è caduta su $R$** e risulta $v_o = v_i$: il segnale passa **inalterato**.
- **Quando $v_i$ tende a superare $V_\gamma$**: il diodo entra **in conduzione** e, per il modello equivalente, si comporta come un generatore di tensione costante $V_\gamma$. L'uscita resta perciò **bloccata (clampata) a $v_o \approx V_\gamma \approx 0{,}7\ \text{V}$**, per quanto grande diventi l'ingresso. Tutta la **tensione in eccesso $(v_i - V_\gamma)$ cade sulla resistenza $R$**, che percorre una corrente $I = (v_i - V_\gamma)/R$.
- **Semionde negative**: il diodo è polarizzato inversamente, resta interdetto e l'uscita segue integralmente l'ingresso. Con un solo diodo la limitazione è dunque **unilaterale** (soltanto sulle creste positive); invertendo il diodo si limitano invece le sole creste negative.

La forma d'onda risultante ha quindi le **creste positive «tosate» a un livello piatto pari a $V_\gamma$**, mentre le semionde negative restano sinusoidali.

### D18 — Qual è lo scopo di collegare più diodi in serie o in antiparallelo?

**Diodi in serie — scopo: alzare il valore della soglia di limitazione.**
Poiché i diodi in serie sono attraversati dalla stessa corrente e le loro cadute di tensione si sommano, con **n diodi in serie** il gruppo entra in conduzione solo quando la tensione applicata supera $n \cdot V_\gamma$. Si ottiene così il livello di taglio desiderato **senza dover ricorrere a generatori di polarizzazione ausiliari**, che complicherebbero il circuito e richiederebbero un'alimentazione in più:

| Numero di diodi in serie | Soglia di limitazione |
|---|---|
| 1 | ≈ 0,7 V |
| 2 | ≈ 1,4 V |
| 3 | ≈ 2,1 V |
| n | ≈ n · 0,7 V |

Lo svantaggio è che la soglia risulta **quantizzata a multipli di 0,7 V**: non si può ottenere un valore intermedio qualsiasi.

**Diodi in antiparallelo — scopo: rendere la limitazione simmetrica.**
Collegando due diodi **in parallelo ma con verso opposto** (l'anodo dell'uno sul catodo dell'altro), per ogni polarità della tensione ce n'è sempre uno polarizzato direttamente. Il risultato è che l'uscita viene limitata **sia sulle semionde positive sia su quelle negative**, a $\pm V_\gamma$: si ottiene una limitazione **bilaterale e simmetrica**, adatta a proteggere un ingresso da sovratensioni di entrambi i segni.

Le due tecniche si **combinano**: mettendo in antiparallelo due *gruppi* di n diodi in serie si ottiene una limitazione simmetrica a $\pm n V_\gamma$ (per esempio ±1,4 V con due diodi per ramo).

### D19 — Disegnare i circuiti limitatori con diodi in serie e in antiparallelo

![[diodi-fig-09.svg]]
*Fig. 9 — Limitatore con diodi in serie (soglia più alta) e limitatore con diodi in antiparallelo (taglio simmetrico).*

![[diodi-fig-10.svg]]
*Fig. 10 — Effetto del limitatore in antiparallelo su una sinusoide di ampiezza molto maggiore della soglia: sagomatura in onda quasi quadra.*

### D20 — Simbolo e curva caratteristica del diodo Zener, zona di lavoro e impieghi

![[diodi-fig-11.svg]]
*Fig. 11 — Simbolo del diodo Zener, polarizzazione di lavoro e curva caratteristica con la zona di funzionamento evidenziata.*

**Simbolo.** È quello del diodo normale, ma con la **barretta del catodo ripiegata alle due estremità** in modo da ricordare la lettera **Z** (una piega verso l'alto e una verso il basso). Serve proprio a distinguerlo a colpo d'occhio dal diodo raddrizzatore.

**Curva caratteristica.**

- **In polarizzazione diretta** lo Zener si comporta **esattamente come un diodo normale**: conduce oltre $V_\gamma \approx 0{,}7\ \text{V}$. In questo modo però **non viene mai usato**.
- **In polarizzazione inversa** presenta un **ginocchio molto netto e ben definito** in corrispondenza della tensione $V_Z$ (tensione di Zener). Superata $V_Z$ la caratteristica diventa **quasi verticale**.

**Zona di funzionamento.** Il diodo Zener **lavora nella zona di breakdown inversa**, cioè nel **terzo quadrante, oltre il ginocchio**. È la sua caratteristica distintiva: mentre in un diodo comune il breakdown è una condizione distruttiva da evitare, lo Zener è **costruito appositamente** (con drogaggi elevati e adeguata dissipazione) per **lavorare stabilmente in quella zona senza danneggiarsi**, a patto che la corrente sia limitata dall'esterno.

In quel tratto la **tensione ai suoi capi rimane praticamente costante e pari a $V_Z$** anche se la corrente varia moltissimo. La corrente di lavoro deve però restare compresa fra due limiti:

- $I_{ZK}$ (corrente di ginocchio, *knee*): corrente **minima** necessaria perché il punto di lavoro sia oltre il ginocchio e la tensione sia effettivamente stabile. Sotto $I_{ZK}$ lo Zener «esce» dalla zona di regolazione.
- $I_{ZM}$: corrente **massima** ammessa, fissata dalla potenza massima dissipabile: $I_{ZM} = P_{Zmax}/V_Z$. Oltre questo valore il componente si distrugge per surriscaldamento.

La pendenza (non perfettamente verticale) del tratto è descritta dalla **resistenza differenziale $r_Z$**, di pochi ohm: è il parametro che dice di quanto la tensione varia realmente al variare della corrente ($\Delta V_Z = r_Z \Delta I_Z$). Tanto più $r_Z$ è piccola, tanto migliore è lo Zener.

**Impiego del diodo Zener.**

- **Stabilizzatore/regolatore di tensione** (impiego principale): fornisce al carico una tensione costante indipendentemente dalle variazioni dell'ingresso e del carico (vedi D22 e D23).
- **Riferimento di tensione** di precisione per amplificatori, comparatori, convertitori A/D e alimentatori stabilizzati più complessi.
- **Limitatore e protezione da sovratensioni**: posto in parallelo a un ingresso, taglia tutto ciò che supera $V_Z$. Due Zener in antiparallelo (o back-to-back) danno una limitazione simmetrica a valori scelti a piacere.
- **Traslatore di livello**: inserito in serie a un ramo, sposta il livello continuo di un segnale di una quantità fissa $V_Z$.
- **Sagomatura di forme d'onda** a soglie elevate (mentre i diodi comuni permettono soglie solo a multipli di 0,7 V, gli Zener si trovano in tutta la gamma da ≈2,4 V a oltre 100 V).

### D21 — I due meccanismi che consentono il passaggio della corrente dal catodo all'anodo

Il passaggio di corrente **dal catodo all'anodo** significa passaggio di corrente **in senso inverso**, cioè nel verso normalmente bloccato dal diodo. Ciò avviene **nella zona di breakdown**, ed è reso possibile da **due meccanismi fisici distinti**:

**1) Effetto valanga (moltiplicazione a valanga, *avalanche breakdown*).**
Quando la tensione inversa è elevata, il campo elettrico nella regione di svuotamento diventa molto intenso. I pochi **portatori minoritari** che l'attraversano vengono **accelerati** e acquistano un'energia cinetica tale che, urtando contro gli atomi del reticolo cristallino, riescono a **rompere i legami covalenti** e a liberare nuove **coppie elettrone–lacuna** (ionizzazione per urto). I nuovi portatori vengono a loro volta accelerati e ne liberano altri, in un **processo a catena, «a valanga»**, che moltiplica rapidissimamente la corrente inversa.

- Prevale nei diodi con **drogaggio relativamente basso**, in cui la regione di svuotamento è larga e i portatori hanno spazio per accelerare.
- È il meccanismo dominante per tensioni di rottura **superiori a circa 6 V**.
- Ha **coefficiente di temperatura positivo**: all'aumentare della temperatura $V_{BR}$ aumenta (le vibrazioni del reticolo ostacolano l'accelerazione dei portatori).

**2) Effetto Zener (effetto tunnel, *Zener breakdown*).**
Quando entrambe le regioni sono **drogate molto pesantemente**, la regione di svuotamento risulta **estremamente sottile** e già per tensioni inverse modeste il campo elettrico raggiunge valori enormi (oltre $10^8\ \text{V/m}$). Un campo così intenso è in grado di **strappare direttamente gli elettroni dai legami covalenti** degli atomi di silicio, facendoli passare per **effetto tunnel** dalla banda di valenza della zona P alla banda di conduzione della zona N, **senza bisogno di urti né di accelerazione**.

- Prevale nei diodi **fortemente drogati**, con regione di svuotamento sottilissima.
- È il meccanismo dominante per tensioni di rottura **inferiori a circa 5 V**.
- Ha **coefficiente di temperatura negativo**: all'aumentare della temperatura $V_Z$ diminuisce.

> [!important] Osservazioni importanti
> - Nella zona intermedia, **fra circa 5 e 6 V**, i due meccanismi **coesistono** e i loro coefficienti di temperatura, essendo di segno opposto, **si compensano**: per questo gli Zener attorno a **5,6 V** sono i più **stabili in temperatura** e vengono preferiti come riferimenti di precisione.
> - In entrambi i casi il fenomeno è di per sé **reversibile e non distruttivo**: il diodo si danneggia solo se la **potenza dissipata** supera il valore massimo, cioè se la corrente non viene limitata da una resistenza esterna.
> - Nell'uso corrente tutti i diodi che lavorano in questa zona vengono chiamati «Zener», anche quando il meccanismo effettivo è la valanga.

### D22 — Dare la definizione di stabilizzatore o regolatore di tensione

**Definizione.** Lo **stabilizzatore** (o **regolatore**) **di tensione** è un circuito che, posto fra la sorgente e il carico, **mantiene la tensione di uscita costante al valore voluto**, indipendentemente dalle variazioni delle grandezze che tenderebbero a farla cambiare, e cioè:

- le **variazioni della tensione d'ingresso** — dovute alle fluttuazioni della tensione di rete e al ripple residuo lasciato dal filtro. La capacità di reiezione si misura con la **regolazione di linea**: $S_V = \Delta V_o / \Delta V_i$;
- le **variazioni della corrente assorbita dal carico** — dovute al fatto che l'apparecchio alimentato non richiede sempre la stessa corrente. Si misura con la **regolazione di carico**: $R_o = \Delta V_o / \Delta I_L$;
- le **variazioni di temperatura** — misurate dal coefficiente termico $S_T = \Delta V_o / \Delta T$.

**Idealmente** tutti e tre questi coefficienti dovrebbero valere zero: la tensione d'uscita non dovrebbe dipendere né da $V_i$, né da $I_L$, né da $T$.

**Collocazione e importanza.** Lo stabilizzatore è l'**ultimo stadio dell'alimentatore**: *trasformatore → raddrizzatore → filtro → **stabilizzatore** → carico*. Il raddrizzatore e il filtro da soli forniscono una tensione ancora affetta da ripple e dipendente dal carico; è lo stabilizzatore a trasformarla in una **vera tensione continua**, pulita e costante. È indispensabile perché i circuiti elettronici moderni (in particolare i circuiti integrati e i microprocessori) richiedono alimentazioni entro tolleranze molto strette, spesso di pochi punti percentuali.

### D23 — Schema più semplice di regolatore, con le espressioni matematiche

![[diodi-fig-12.svg]]
*Fig. 12 — Regolatore di tensione a diodo Zener: lo schema più semplice possibile.*

**Struttura.** Il regolatore più semplice è formato da due soli componenti: una **resistenza di zavorra $R_S$ in serie** e un **diodo Zener in parallelo al carico**, polarizzato inversamente (catodo verso il polo positivo). È detto **regolatore parallelo** (*shunt regulator*).

**Relazioni fondamentali.**

$$V_o = V_Z \quad \text{(finché lo Zener lavora in breakdown)}$$

$$I_S = \frac{V_i - V_Z}{R_S} \qquad I_L = \frac{V_Z}{R_L} \qquad I_Z = I_S - I_L$$

($I_S$ è la corrente totale erogata attraverso $R_S$, $I_L$ quella assorbita dal carico, $I_Z$ quella nello Zener — 1° principio di Kirchhoff al nodo.)

$$V_i = R_S I_S + V_Z \qquad \text{(2° principio di Kirchhoff alla maglia d'ingresso)}$$

$$P_Z = V_Z I_Z \le P_{Zmax}$$

**Condizione di funzionamento corretto.** La regolazione è garantita solo se, in **tutte** le condizioni di lavoro, la corrente nello Zener resta compresa fra i due limiti:

$$I_{ZK} \le I_Z \le I_{ZM} \qquad \text{con} \quad I_{ZM} = \frac{P_{Zmax}}{V_Z}$$

Da questa condizione si ricava l'intervallo entro cui deve cadere $R_S$, considerando i due casi peggiori:

$$R_{S,max} = \frac{V_{i,min} - V_Z}{I_{ZK} + I_{L,max}} \quad \text{(ingresso minimo, carico massimo)}$$

$$R_{S,min} = \frac{V_{i,max} - V_Z}{I_{ZM} + I_{L,min}} \quad \text{(ingresso massimo, carico minimo)}$$

**Descrizione del funzionamento — perché stabilizza.** Lo Zener, lavorando nel tratto quasi verticale della sua caratteristica inversa, **impone la propria tensione $V_Z$** al nodo di uscita. Il circuito reagisce così alle due possibili perturbazioni:

- **Se aumenta la tensione d'ingresso $V_i$**: aumenta la corrente totale $I_S$. Ma poiché l'uscita resta bloccata a $V_Z$, la corrente nel carico $I_L$ non cambia: **tutto l'incremento va nello Zener** ($I_Z$ aumenta). Di conseguenza aumenta la caduta su $R_S$, che **assorbe interamente l'eccesso di tensione**, e l'uscita resta costante.
- **Se aumenta la corrente richiesta dal carico $I_L$** (cioè diminuisce $R_L$): lo Zener **cede parte della propria corrente al carico**, cioè $I_Z$ diminuisce esattamente di quanto $I_L$ aumenta. La somma $I_S = I_Z + I_L$ resta praticamente invariata, la caduta su $R_S$ non cambia e l'uscita resta a $V_Z$.

Lo Zener si comporta quindi come un **«serbatoio» di corrente in parallelo al carico**: assorbe ciò che al carico non serve, restituisce ciò che al carico occorre in più.

**Limiti di questo schema.** La stabilizzazione non è perfetta, perché la resistenza differenziale $r_Z$ non è nulla: una variazione di corrente produce comunque una piccola variazione di uscita, $\Delta V_o = r_Z \Delta I_Z$. Inoltre il **rendimento è basso** (la potenza dissipata da $R_S$ e dallo Zener è sempre presente, anche a vuoto, quando lo Zener assorbe tutta la corrente) ed è adatto solo a **correnti di carico modeste** e poco variabili. Per prestazioni migliori si ricorre a regolatori con **transistor di potenza** (regolatori serie, a controreazione) o a **regolatori integrati** della serie 78xx/79xx, che usano comunque uno Zener interno come riferimento di tensione.

---

## Integrazione · Scheda «Verifica di elettronica»

### D6★ — Che cosa rappresenta la tensione di soglia di un diodo?

La **tensione di soglia $V_\gamma$** (detta anche tensione di ginocchio, di *cut-in* o di accensione) è il **valore di tensione diretta al di sotto del quale la corrente nel diodo è trascurabile e oltre il quale il diodo entra in piena conduzione**.

Dal punto di vista fisico rappresenta la **tensione necessaria per abbattere la barriera di potenziale** della giunzione PN e permettere ai portatori maggioritari di attraversarla in gran numero; il suo valore è quindi legato al **materiale semiconduttore** impiegato.

Dal punto di vista grafico corrisponde alla **posizione del ginocchio** della curva caratteristica, cioè al punto in cui la curva cambia bruscamente pendenza e diventa quasi verticale (Fig. 5).

Dal punto di vista circuitale è il parametro che compare nei **modelli equivalenti B e A** come generatore di tensione costante, e rappresenta la **caduta di tensione fissa** ai capi del diodo in conduzione.

| Materiale / tipo | $V_\gamma$ tipica |
|---|---|
| Germanio | 0,2 ÷ 0,3 V |
| Silicio | 0,6 ÷ 0,7 V |
| Schottky | 0,2 ÷ 0,4 V |
| LED (rosso → blu) | 1,6 ÷ 3,4 V |

### Corrispondenza fra la scheda «Verifica» (D1–D16) e queste risposte

| Scheda «Verifica» | Argomento | Vedi risposta |
|---|---|---|
| D1 | Struttura del diodo | D1 |
| D2 | Simbolo circuitale | D2 |
| D3 | Zone di polarizzazione sulla caratteristica | D8 |
| D4 | Grandezze dell'equazione a destra del breakdown | D11 |
| D5 | Motivi dei modelli approssimati | D12 |
| D6 | Tensione di soglia | D6★ (qui sopra) |
| D7 | Modello interruttore + generatore + resistore | D13 — Modello A |
| D8 | Raddrizzatore a semionda e suo utilizzo | D14 e D15 |
| D9 | Funzione del limitatore | D16 |
| D10 | Usi del limitatore | D16 |
| D11 | Limitatore con diodi in serie e suo scopo | D18 e D19 |
| D12 | Limitatore con diodi in antiparallelo e suo scopo | D18 e D19 |
| D13 | Funzione del diodo Zener | D20 |
| D14 | Cosa consente l'impiego dello Zener come stabilizzatore | D20 e D21 |
| D15 | Funzione dello stabilizzatore/regolatore | D22 |
| D16 | Schema del regolatore con relazioni | D23 |

---

Dispensa di studio — Il diodo a semiconduttore · Cap. 5, pp. 192–224 · Classe 4E.
Le conoscenze qui raccolte sono il presupposto per lo studio dei transistor BJT e MOSFET: [[BJT]], [[MOSFET]].
