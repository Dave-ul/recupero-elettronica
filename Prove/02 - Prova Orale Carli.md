---
tags: [recupero, elettronica, prova-orale, carli]
fonte: "MAJORANA — Lettera di giudizio sospeso (Secondo Periodo), 09/06/2026"
docente: Prof. Carlo Carli
tipologia: Orale
---

# 02 — Prova Orale (Prof. Carli)

> [!info] Dove serve
> È la **prova orale** di teoria del docente Carlo Carli. Non ci sono esercizi da risolvere davanti al foglio: ci sono **definizioni, teoremi, dimostrazioni rapide**, domande di ragionamento e analisi di schemi "a voce".

---

## Cosa chiede la lettera

Dalla lettera di giudizio sospeso, **verbatim**, la riga che riguarda questa prova:

> **PROVA ORALE**: domande sul **diodo**, sui **circuiti in corrente alternata** e sui **filtri passivi del primo ordine**.

> [!warning] Correzione 2026-07-28 — questa citazione era sbagliata
> La versione precedente riportava, sempre come «dalla lettera», *«Circuiti in corrente alternata, filtri passivi del primo ordine, transistor BJT / JFET / MOSFET, diodi»*: una **fusione delle due prove**, che aggiungeva all'orale i transistor (che la LETTERA mette **nella scritta**) e perdeva i qualificatori «a canale N» e «ad arricchimento». Testo riletto dal PDF originale della LETTERA. Vedi [[00 - Fonti e note]] §1 e [[00 - Audit e correzioni]], Fase Studio — Lotto 1.
>
> **Cosa cambia per te**: il **diodo** è l'unico componente che la LETTERA nomina esplicitamente per l'orale — ed è anche l'unico argomento su cui hai le **domande vere** del docente ([[04 - Verifica tipo Carli — Diodi]]). BJT/JFET/MOSFET restano confronti naturali che Carli può chiedere, ma non sono capitoli d'esame **di questa prova**.

All'orale la lista si traduce in domande di tipo:

- "Cos'è il metodo simbolico e quando **non** si può usare?"
- "Dimostra / spiega perché $\bar{Z}_C = -j/(\omega C)$"
- "Perché il condensatore è un cortocircuito alle alte frequenze?"
- "Che differenza c'è tra BJT e MOSFET?"
- "Cos'è il JFET e come si distingue dal MOSFET a canale n?"
- "Spiega la curva caratteristica del diodo e la zona di breakdown (Zener)"
- "Che cos'è un filtro passa-banda e come si realizza?"

---

## I tre livelli di domanda orale

> [!tip] Strategia per studiare l'orale
> Le domande dell'orale si dividono in tre fasce di difficoltà, e ti conviene prepararle tutte e tre — l'orale non è mai "solo definizioni":

| Livello | Tipo | Esempio |
|---|---|---|
| 🟢 **Definizione** | Saper enunciare | "Cos'è l'impedenza?" |
| 🟡 **Spiegazione** | Perché funziona | "Perché $\omega L$ è la reattanza induttiva?" |
| 🔴 **Confronto / analisi** | Collegare concetti | "BJT vs MOSFET: vantaggi e svantaggi" |

> Le 🟢 e 🟡 valgono almeno 6-7; le 🔴 fanno la differenza tra il 7 e il 9.

---

## Quesiti tipo — Guida rapida

### 🟢 Definizioni da sapere a memoria

| Domanda | Risposta sintetica | Dove ripassarla |
|---|---|---|
| Cos'è un **fasore**? | Un vettore (o numero complesso) che rappresenta una sinusoide isofrequenziale | [[Segnali sinusoidali e fasori#Il fasore]] |
| Cos'è l'**impedenza**? | Il rapporto $\bar{Z} = \bar{V}/\bar{I}$; generalizza la resistenza. | [[Impedenza dei bipoli R, L, C#Definizione]] |
| Cos'è il **metodo simbolico**? | Tecnica per analizzare reti AC sostituendo le sinusoidi con i fasori corrispondenti | [[Il metodo simbolico]] |
| Cos'è la **potenza attiva / reattiva / apparente**? | $P = VI\cos\varphi$, $Q = VI\sin\varphi$, $S = VI$ | [[Le potenze in alternata]] |
| Cos'è la **risonanza**? | Condizione in cui $X_L + X_C = 0$; la rete è puramente resistiva | [[Reti RLC e risonanza]] |
| Cos'è un **filtro passa-basso / passa-alto**? | Rete che seleziona frequenze basse/alte sopra/sotto una $f_t$ | [[Filtri passivi del primo ordine]] |
| Cos'è un **diodo a giunzione**? | Componente a semiconduttore con due terminali (anodo, catodo) che conduce in un solo verso | [[Diodi]] |
| Cos'è un **BJT**? | Transistor a giunzione bipolare (NPN o PNP), pilotato in corrente dalla base | [[BJT]] |
| Cos'è un **MOSFET**? | Transistor a effetto di campo con gate isolato (ossido), pilotato in tensione | [[BJT#MOSFET]] |
| Cos'è un **JFET**? | FET a giunzione, gate direttamente connesso al canale tramite giunzione p-n | [[BJT#JFET]] |

### 🟡 Spiegazioni da saper fare

> [!question] "Perché $\bar{Z}_C = -j/(\omega C)$? Cosa vuol dire quel $-j$?"
>
> Perché l'impedenza nasce da $\bar{I} = j\omega C \bar{V}$, quindi $\bar{Z}_C = \bar{V}/\bar{I} = 1/(j\omega C) = -j/(\omega C)$. Il $-j$ significa che la **corrente è in anticipo di 90° sulla tensione**, cioè la tensione è **in ritardo** di 90° sulla corrente.
>
> Vedi: [[Segnali sinusoidali e fasori#Moltiplicare per j]] e [[Impedenza dei bipoli R, L, C#Condensatore]].

> [!question] "Perché il metodo simbolico richiede eccitazioni isofrequenziali?"
>
> Perché il fasore ha senso solo tra sinusoidi che ruotano alla stessa velocità. Se due generatori hanno frequenze diverse, i loro vettori ruoterebbero a velocità diverse, l'angolo tra loro cambierebbe di continuo, e la rappresentazione perderebbe significato.
>
> Vedi: [[Il metodo simbolico#Limiti]].

> [!question] "Perché in un transistor BJT la corrente di base controlla la corrente di collettore?"
>
> Perché la struttura NPN è fatta di tre regioni di semiconduttore alternate. Una piccola corrente $I_B$ che attraversa la giunzione B-E controlla il "passaggio" di portatori tra emettitore e collettore; il fattore $\beta = h_{FE}$ è il guadagno di corrente, tipicamente 100–300.
>
> Vedi: [[BJT#Struttura]].

> [!question] "Perché il MOSFET scalda meno del BJT?"
>
> Perché il gate del MOSFET è isolato da uno strato di ossido, quindi **non assorbe corrente continua** (corrente di gate ≈ 0). Nel BJT invece serve sempre una $I_B$ per mandare il transistor in zona attiva. Il MOSFET scalda meno perché non c'è la potenza $V_{BE} \cdot I_B$.
>
> Vedi: [[BJT#MOSFET]].

> [!question] "Perché il fattore di potenza è $\cos\varphi$?"
>
> Perché $\varphi$ è l'angolo di sfasamento tra tensione e corrente. Dal triangolo delle potenze la potenza **utile** (attiva) è il **cateto orizzontale** del triangolo, l'ipotenusa è la potenza apparente, e il rapporto è $\cos\varphi$ = $\frac{\text{cateto}}{\text{ipotenusa}}$.
>
> Vedi: [[Le potenze in alternata#Triangolo delle potenze]].

### 🔴 Confronti e analisi

> [!danger] "BJT vs MOSFET: quando si sceglie l'uno o l'altro?"
>
> **BJT**: pilotaggio in corrente; $\beta \cdot I_B = I_C$. Veloce, robusta nelle commutazioni, ben modellizzata in elettronica analogica (amplificatori a basso rumore).
>
> **MOSFET**: pilotaggio in tensione; $V_{GS}$ controlla $I_D$. Bassissima potenza di pilotaggio, facile da integrare, dominante nell'elettronica digitale (CMOS) e di potenza.
>
> **Regola pratica ITIS**: amplificatori a piccolo segnale → BJT; integrati digitali, alimentatori switching → MOSFET.

> [!danger] "JFET vs MOSFET: stessa struttura concettuale, ma…"
>
> Il JFET ha il gate connesso al canale tramite una **giunzione p-n** che va polarizzata **in inversa**; questo preclude di avere $V_{GS}$ positiva. Il MOSFET ha il gate **isolato da uno strato di ossido**: $V_{GS}$ può essere positivo, negativo, o nullo; curve molto più flessibili.
>
> Vedi: [[BJT#JFET]].

> [!danger] "Diodo vs Zener: stessa struttura, comportamento opposto"
>
> Il diodo a giunzione in polarizzazione **diretta** conduce (sopra la soglia ~0,7 V), in **inversa** non conduce (fino al breakdown).
> Il diodo **Zener** è progettato per lavorare esattamente nella zona di **breakdown** (tensione Zener $V_Z$ caratteristica del componente, tipicamente 3–200 V) e **mantenere una tensione costante** ai suoi capi anche con correnti variabili: da qui il suo uso come **stabilizzatore di tensione**.
>
> Vedi: [[Diodi#4. Il diodo Zener]]. *(Link corretto il 2026-07-28: puntava a `#Zener`, un'intestazione che non esiste.)*

---

## 🔷 Diodi — il banco di ripasso vero

> [!important] Qui non si studia: qui si smista
> Il **diodo** è l'unico componente che la LETTERA nomina per questa prova, ed è l'unico argomento del vault su cui esistono le **domande vere del docente**: 39 domande aperte da due compiti dati alla classe 4E, trascritte e risposte in **[[04 - Verifica tipo Carli — Diodi]]**.
>
> Le risposte stanno **là**, la teoria sta in **[[Diodi]]**. Questa tabella serve a una cosa sola: dirti **quali domande valgono il 6 e quali fanno il 9**, con la scala 🟢/🟡/🔴 usata in tutto questo file.

### 🟢 Definizioni — vanno sapute a memoria, sono il 6

| Cosa ti chiede | Domande | Dove ripassarla |
|---|---|---|
| Struttura del diodo (zone P/N, anodo, catodo) — **con disegno** | A-D1 · B-D1 | [[Diodi#1. La giunzione p-n: perché esiste il diodo]] |
| Simbolo circuitale — **con disegno** | A-D2 · B-D2 | idem (FIGURA 5) |
| Definizione di polarizzazione della giunzione PN | B-D3 | [[Diodi#2. Polarizzazione diretta e inversa]] |
| Cosa s'intende per polarizzazione diretta / inversa | B-D4 · B-D5 | idem (FIGURA 6) |
| Versi convenzionali di $I_D$ e $V_D$ nel simbolo | B-D6 | [[Diodi#La curva completa e i versi convenzionali (FIGURA 7, p. 197)]] |
| Con quale rappresentazione grafica si descrive il diodo ai morsetti | B-D7 | idem |
| Che cosa rappresenta la **tensione di soglia** (risposta: $\approx 0{,}6$ V) | A-D6 | idem, box «0,6 V o 0,7 V?» |
| Funzione di un limitatore · definizione e utilizzi | A-D9 · A-D10 · C-D16 | [[Diodi#6. Limitatori di tensione (clipper)]] |
| Definizione di raddrizzatore e sua importanza | C-D14 | [[Diodi#5. Il raddrizzatore]] |
| Funzione del diodo Zener | A-D13 | [[Diodi#4. Il diodo Zener]] |
| Definizione di stabilizzatore / regolatore di tensione | A-D15 · C-D22 | [[Diodi#Stabilizzatore di tensione con Zener]] |

### 🟡 Spiegazioni — è qui che si costruisce il 7-8

| Cosa ti chiede | Domande | Dove ripassarla |
|---|---|---|
| Curva caratteristica con le **due zone** diretta e inversa, disegnate ed etichettate | A-D3 · B-D8 | [[Diodi#3. La curva V-I: la «spezzata» di carico]] |
| Descrizione della curva e significato di **tutte** le grandezze | B-D9 | idem |
| Espressione di Shockley con la **legenda completa** | A-D4 · B-D11 | [[Diodi#L'equazione di Shockley e la sua legenda (form. 5.1, p. 198)]] |
| Modello equivalente interruttore + generatore + resistore | A-D7 | [[Diodi#I tre modelli approssimati (nomenclatura del libro)]] |
| Raddrizzatore a semionda: schema + utilizzo principale | A-D8 | [[Diodi#Raddrizzatore a semionda]] |
| Raddrizzatori a singola **e** doppia semionda + forme d'onda | C-D15 | [[Diodi#Raddrizzatore a ponte (Graetz)]] |
| I **quattro** limitatori a bassa soglia + forme d'onda | C-D17 | [[Diodi#I quattro limitatori a bassa soglia (FIGURA 24, p. 211)]] |
| Limitatore con diodi in serie / in antiparallelo — schemi | A-D11 · A-D12 · C-D19 | [[Diodi#Alzare la soglia: diodi in serie, antiparallelo, generatore]] |
| Simbolo e curva dello Zener, zona di funzionamento, impiego | C-D20 | [[Diodi#4. Il diodo Zener]] |
| Cosa consente l'impiego dello Zener come stabilizzatore | A-D14 | [[Diodi#Stabilizzatore di tensione con Zener]] |
| Schema del regolatore **con le relazioni** (5.10, 5.11) | A-D16 · C-D23 | idem (FIGURA 33/34) |

### 🔴 Confronti e giustificazioni — sono queste a fare il 9

| Cosa ti chiede | Domande | Perché è 🔴 |
|---|---|---|
| Perché si ricorre a **modelli approssimati** per il diodo reale | A-D5 · B-D12 | non è una definizione: devi dire che il diodo **non è lineare**, che quindi saltano Ohm/sovrapposizione/Thévenin, e che la linearizzazione a tratti li ripristina |
| «Il diodo è un componente lineare?» — **giustificare** | B-D10 | la risposta è una riga, la giustificazione è tutto il punto: retta per l'origine vs $\Delta I$ diversissimi a parità di $\Delta V$ |
| I **tre** modelli a confronto (inversa, diretta, curva) + da cosa dipende la scelta | C-D13 | tabella 3×3 da disegnare **e** un criterio da enunciare: precisione richiesta vs peso dei conti |
| Scopo di collegare più diodi **in serie o in antiparallelo** | C-D18 | due circuiti diversi in una domanda sola: $n \cdot 0{,}7$ V da un lato, $\pm 0{,}7$ V dall'altro — ed è la **trappola** della parola «in serie» |
| I **due meccanismi** di breakdown | C-D21 | effetto **Zener** ($V_Z<5$ V, campo che rompe i legami) vs effetto **valanga** ($V_Z>6$ V, urti e moltiplicazione) — vedi [[Diodi#I due meccanismi di breakdown: effetto Zener ed effetto valanga (p. 220)]] |

> [!tip] Il conto che conta
> **21 domande su 39 iniziano con «Disegnare».** All'orale il foglio bianco te lo danno: la checklist di cosa deve comparire in ciascuno dei 15 disegni è in [[04 - Verifica tipo Carli — Diodi]] §4.

---

## "Dimostra / spiega" — i passaggi chiave

> [!warning] Questi li devi saper rifare a voce senza leggere
> L'orale Carli tende a chiederti di **spiegare a parole** un passaggio che hai fatto in forma scritta. Memorizza la sequenza, non solo il risultato.

1. **Come si ricava $\bar{V} = j\omega L \bar{I}$ nell'induttore?**
   - Legge fisica: $v(t) = L \cdot di/dt$
   - Se $i(t) = I \sin(\omega t + \varphi)$, allora $v(t) = L\omega I \cos(\omega t + \varphi) = L\omega I \sin(\omega t + \varphi + \pi/2)$
   - In fasori: $\bar{V} = L \cdot (j\omega) \bar{I} = j\omega L \bar{I}$ (la derivata = moltiplicazione per $j\omega$)

2. **Come si dimostra che la somma di potenze non è $P + Q = S$?**
   - $S^2 = (V I)^2 = P^2 + Q^2$ — Pitagora sul triangolo
   - $P + Q \ne S$ in generale (è la somma di due cateti, non il quadrato dell'ipotenusa)
   - W, VAR, VA sono la stessa unità (Watt) ma sono convenzioni diverse, hanno proprio lo scopo di ricordarti che NON vanno sommate come numeri

3. **Perché la frequenza di taglio di un RC passa-basso è $\omega_t = 1/(RC)$?**
   - $\bar{V}_{out}/\bar{V}_{in} = \frac{1/(j\omega C)}{R + 1/(j\omega C)} = \frac{1}{1 + j\omega RC}$
   - Quando $\omega RC = 1$, il modulo è $1/\sqrt{2}$ — la definizione operativa di $f_t$
   - Quindi $\omega_t = 1/(RC)$

---

## Errori dialettici all'orale

> [!danger] Le trappole lessicali
>
> 1. **"frequenza" vs "pulsazione"**: $f$ è in **Hz**, $\omega$ in **rad/s**. Scambiarli in una dimostrazione fa crollare tutto.
> 2. **"impedenza" vs "reattanza"**: l'impedenza è il **numero complesso** $\bar{Z} = R + jX$. La reattanza è solo la **parte immaginaria** $X$.
> 3. **"filtro passa-basso" vs "filtro soppressore di banda"**: il primo taglia le **alte** freq., il secondo ne **toglie una specifica** (notch).
> 4. **"AND" vs "OR" nelle definizioni di zona BJT**: zona attiva = giunzione B-E **ON** + giunzione B-C **inversa**; saturazione = **entrambe ON**; interdizione = **entrambe OFF**.
> 5. **Dire "il transistor amplifica in tensione"**: potrebbe, ma il primario modo di funzionamento è l'**amplificazione di corrente** (con la piccola $I_B$ che comanda la grande $I_C$).

---

## Checklist finale

### Circuiti CA
- [ ] Fasori e rappresentazione complessa
- [ ] Impedenze di R, L, C e valori limite
- [ ] Metodo simbolico, limiti (regime + isofrequenza)
- [ ] Potenze e triangolo
- [ ] Rifasamento — senso industriale
- [ ] Risonanza serie e parallelo
- [ ] Filtri RC/RL — passa basso, passa alto
- [ ] L'oscilloscopio [[L'oscilloscopio]] (per ricollegarti alla pratica)

### Componenti
- [ ] Diodo a giunzione: curva V-I
- [ ] Diodo Zener: tensione di breakdown
- [ ] BJT: struttura, regioni, $\beta$
- [ ] MOSFET: enhancement vs depletion
- [ ] JFET: cenni, differenza dal MOSFET

### Collegamento teoria-pratica
- [ ] Sai indicare quale grandezza è misurabile in laboratorio (oscilloscopio)
- [ ] Sai indicare cosa cambia in continua vs in alternata

---

## Esercizi di preparazione all'orale

Non è "svolgere esercizi", è **spiegare a voce** mentre li svolgi. prova a farlo da solo, possibilmente registra la tua spiegazione e riascoltala.

1. Spiega a voce l'[[Esercizi - Il metodo simbolico#Esercizio 9]] come se parlassi con uno che non l'ha mai visto.
2. Spiega la curva $V$-$I$ del diodo: cosa succede a tensioni negative? E positive?
3. Spiega perché in un MOSFET enhancement a canale n con $V_{GS} < V_{th}$ non scorre $I_D$.
4. Spiega il rifasamento di un carico RL partendo solo dalla $X_L$.

> [!success] Traguardo
> Riesci a spiegare **tutte e 4** in meno di 5 minuti ciascuna, senza leggere appunti? Sei pronto per la prova orale Carli.
