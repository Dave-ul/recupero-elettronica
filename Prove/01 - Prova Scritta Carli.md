---
tags: [recupero, elettronica, prova-scritta, carli]
fonte: "MAJORANA — Lettera di giudizio sospeso (Secondo Periodo), 09/06/2026"
docente: Prof. Carlo Carli
tipologia: Scritta
---

# 01 — Prova Scritta (Prof. Carli)

> [!info] Dove serve
> È la **prova scritta** di teoria del docente Carlo Carli. La LETTERA dice **«esercizi»**, quindi è la prova più "computazionale": dati e circuiti forniti, da risolvere in un tempo limitato. Ma leggi prima il callout qui sotto.

> [!warning] Ricalibratura del formato — 2026-07-28
> Le **verifiche scritte vere** del Prof. Carli entrate nel vault (tre fogli fotografati, 39 domande — vedi [[04 - Verifica tipo Carli — Diodi]]) sono **interamente a domande aperte con disegni: zero esercizi numerici**.
>
> Sono verifiche **in corso d'anno**, non la prova di recupero: dicono **come Carli interroga**, non cosa entrerà nel recupero. Ma la conseguenza pratica è netta — **prepararsi solo ai conti è un rischio**. Per ogni argomento della scritta devi saper anche *definire, descrivere e disegnare*, non solo calcolare.
>
> Ciò che resta valido: sullo **scope** comanda la LETTERA (AC, filtri 1° ordine, BJT, JFET a canale N, MOSFET a canale N ad arricchimento), e su quegli argomenti i conti servono davvero. Le sezioni «Pattern» ed «Errori classici» di questo file **non** sono state toccate.

---

## Cosa chiede la lettera

Dalla lettera di giudizio sospeso, **verbatim**, la riga che riguarda questa prova:

> **PROVA SCRITTA**: **esercizi** sui circuiti in **corrente alternata**, sui **filtri passivi del primo ordine**, sui transistor **BJT**, sui transistor **JFET a canale N** e sui transistor **MOSFET a canale N ad arricchimento**.

> [!danger] Correzione 2026-07-28 — questa citazione era sbagliata, e in modo che cambia cosa studi
> La versione precedente riportava, come «dalla lettera», *«Circuiti in corrente alternata, filtri passivi del primo ordine, transistor BJT / JFET / MOSFET, **diodi**»*. La LETTERA **non** mette i diodi in questa prova: li mette **nell'orale** (e nella pratica Protti). Era una fusione delle due prove, che per giunta perdeva i qualificatori «**a canale N**» e «**ad arricchimento**» — cioè proprio i limiti che ti risparmiano JFET a canale P e MOSFET depletion.
>
> Testo riletto dal PDF originale della LETTERA il 2026-07-28. Vedi [[00 - Fonti e note]] §1 e [[00 - Audit e correzioni]], Fase Studio — Lotto 1.
>
> **I diodi restano utili anche qui**, ma per una ragione diversa: sono il **prerequisito** di BJT e MOSFET — e sul suo stesso foglio di verifica Carli scrive *«queste conoscenze serviranno allo studio dei transistori BJT e transistor MOSFET»*.

In forma scritta, questo si traduce tipicamente in:

- Calcolo di **modulo e argomento** di impedenze
- Analisi di circuiti RC/RL/RLC con il **metodo simbolico**
- Calcolo di **potenze** (attiva, reattiva, apparente), **fattore di potenza**, **rifasamento**
- Calcolo della **frequenza di taglio** e del guadagno di **filtri** RC e RL del primo ordine
- Analisi di **circuiti a diodo** (raddrizzatori, limitatori, zener) — **non** in LETTERA per questa prova: qui come prerequisito di BJT/MOSFET e perché la pratica Protti li chiede. Il banco vero è [[04 - Verifica tipo Carli — Diodi]]
- **Polarizzazione e punti di lavoro** di transistor BJT/MOSFET
- Eventuale calcolo di **guadagno** in piccoli segnali di un amplificatore

---

## Checklist argomenti

### 🟢 Circuiti in CA — già pronto
- [ ] [[Segnali sinusoidali e fasori]] — rappresentazione complessa, modulo/argomento
- [ ] [[Impedenza dei bipoli R, L, C]] — calcolo di $\bar{Z}$, parallelo con coniugato
- [ ] [[Il metodo simbolico]] — procedimento a tre passi (entra → risolvi → esci)
- [ ] [[Le potenze in alternata]] — $P$, $Q$, $S$, $\cos\varphi$, rifasamento
- [ ] [[Reti RLC e risonanza]] — $\omega_0$, $Q$, $B$, condizioni di risonanza serie/parallelo
- [ ] [[Filtri passivi del primo ordine]] — RC/RL passa-basso e passa-alto, Bode

> [!check] Stato: COMPLETO
> Tutti gli appunti necessari per la parte CA/filtri sono già in `Argomenti/`. Gli esercizi tipo sono in `Esercizi/`.

### 🟡 Diodi — da preparare
- [ ] [[Diodi]] — giunzione p-n, polarizzazione diretta/inversa, curve V-I
- [ ] [[Diodi#Zener]] — stabilizzazione, potenza dissipata
- [ ] Circuiti raddrizzatori (mezza onda, ponte di Graetz)
- [ ] [[Esercizi - Diodi]]

### 🟡 Transistor BJT — da preparare
- [ ] [[BJT]] — struttura NPN/PNP, regioni di funzionamento
- [ ] [[BJT#Polarizzazione]] — reti $V_{BB}$/$R_B$, partitore di polarizzazione
- [ ] Calcolo del **punto di lavoro** ($I_C$, $V_{CE}$) in continua
- [ ] Distinguere zona attiva, saturazione, interdizione
- [ ] [[Esercizi - BJT]]

### 🟡 MOSFET — cenni
- [ ] [[BJT#MOSFET]] — enhancement/depletion, threshold, $K$, $V_{GS}$
- [ ] Polarizzazione base del MOSFET
- [ ] Lettura delle curve caratteristiche

### ⚪ JFET — solo domanda orale
> [!tip] Per la prova scritta il JFET è raramente chiesto
> Il JFET è un'estensione concettuale del MOSFET; se la prova scritta non lo prevede, lo trovi eventualmente all'[[02 - Prova Orale Carli|orale]] (definizione e confronto).

---

## Esercizi tipo scritta — come affrontarli

### Pattern 1 — "Calcola modulo e argomento di $\bar{V}_R$"

**Schema:**
1. Disegna il circuito, identifica il partitore o la maglia.
2. Converti i componenti in impedenze complesse: $\omega = 2\pi f$, $L \to j\omega L$, $C \to -j/(\omega C)$.
3. Se c'è un parallelo, **moltiplica per il coniugato** per portare il denominatore reale.
4. Separa parte reale e parte immaginaria.
5. Calcola modulo: $\sqrt{a^2 + b^2}$.
6. Calcola argomento con l'**attenzione al quadrante**: $\arctan(b/a)$ + correzione $+180°$ se $a < 0$, $+360°$ se vuoi angolo positivo.

> [!success] Controllo finale
> Verifica con il segno della reattanza: se il parallelo è dominato da C, l'uscita è **in ritardo** sulla tensione di ingresso (fase negativa). È un controllo gratuito che smaschera immediatamente un segno sbagliato.

### Pattern 2 — "Calcola $P$, $Q$, $S$ e rifasa"

**Schema:**
1. Calcola $\bar{Z} = R + jX$, poi $|Z|$ e $\varphi$.
2. Calcola $I = V/|Z|$.
3. $P = R I^2$, $Q = X I^2$ (con segno!), $S = |Z| I^2$.
4. **Controllo triangolo**: verifica che $S = \sqrt{P^2 + Q^2}$.
5. Per rifasare: applica direttamente
   $$C_{rifas} = \frac{P(\tan\varphi - \tan\varphi')}{\omega V^2}$$
   con $\varphi' = \arccos(\cos\varphi_{\text{nuovo}})$.

### Pattern 3 — "Frequenza di taglio di un filtro RC"

**Schema:**
1. Scrivi la funzione di trasferimento $H(j\omega) = V_{out}/V_{in}$.
2. Porta nella forma canonica passa-basso o passa-alto.
3. Identifica $\omega_t = 1/\tau$ con $\tau = RC$ (passa-basso/alto RC) oppure $\tau = L/R$ (passa-alto/basso RL).
4. La frequenza di taglio è $f_t = \omega_t/(2\pi)$.
5. Per il guadagno in banda passante: $|H(j\cdot 0)|$ o $|H(j\cdot\infty)|$ a seconda del tipo.

### Pattern 4 — "Punto di lavoro di un BJT"

**Schema:**
1. Identifica la rete di polarizzazione (la parte in DC).
2. Spegni il segnale: tutte le C → aperto, tutti i generatori AC → spenti.
3. Applica Kirchhoff alla maglia di polarizzazione per calcolare $I_B$.
4. Usa $\beta$ (o $h_{FE}$) per ottenere $I_C = \beta I_B$.
5. Calcola $V_{CE}$ dalla maglia di uscita.
6. **Verifica la zona**: $V_{CE}$ deve essere circa metà di $V_{CC}$ in saturazione, e in zona attiva deve valere $V_{BE} \approx 0{,}7\ \text{V}$ (silicio).

### Pattern 5 — "Raddrizzatore a ponte"

**Schema:**
1. Disegna il ponte di Graetz: 4 diodi, due rami in antiparallelo.
2. Tensione in uscita (al primario senza filtro): è una doppia semionda rettificata con $|V_{out,p}| = V_{in,p} - 2 V_D$.
3. Tensione media con filtro $C$: $V_{DC} \approx V_{in,p}(1 - 1/(2 f RC))$ — da ricordare a memoria.
4. Ripple picco-picco: $V_{ripple} = I_{load}/(f C)$.

---

## Errori classici da evitare

> [!danger] I 5 errori più frequenti nelle prove scritte di Carli
>
> 1. **Confondere segno di $Q$**: $Q = V I \sin\varphi$ porta il **segno di $\varphi$**. Molti scrivono $Q = +X I^2$ per un circuito RC; è **negativo**, perché $X < 0$.
> 2. **Dimenticare la correzione di quadrante in $\arctan$**: un vettore $a < 0$, $b > 0$ richiede $+180°$; diversi studenti scrivono $\arctan(b/a)$ e basta, sbagliando di 180°.
> 3. **Scambiare BJT PNP/NPN nelle formule $\beta$**: in PNP le tensioni sono misurate con polarità opposte; usare le formule "alla NPN" dà segni invertiti.
> 4. **Dimenticare di cortocircuitare le C in continua**: $X_C = 1/(\omega C) \to \infty$ per $\omega \to 0$, ma in DC la C è un **circuito aperto**. Per la polarizzazione non si deve fare il limite — va proprio aperta.
> 5. **Frequenza di taglio in f Hz o in $\omega$ rad/s?**: $\omega_t = 1/\tau$ è in **rad/s**. Se ti chiedono $f_t$ devi dividere per $2\pi$. Trappola delle calcolatrici scientifiche: numero di pulsanti diversi, pulsante "RAD" e pulsante "Hz" non sono interscambiabili.

---

## Materiale portare alla prova

- Calcolatrice scientifica (con funzioni complesse o con tasti $\angle$ / $\to$Rect / $\to$Polar)
- Penne, matita, gomma
- Squadra e righello
- Foglio bianco per le bozze

> [!warning] Niente formulario
> Le prove scritte Carli sono "a libri chiusi": non portare libri o appunti. Le formule chiave (impedenze, potenze, transistor, diodi) le devi ricordare.

---

## Quando sei pronto, prova a fare (in ordine di difficoltà)

1. Esercizi 1–3 di [[Esercizi - Impedenza dei bipoli R, L, C]] (impedenze in serie/parallelo)
2. Esercizio 9 di [[Esercizi - Il metodo simbolico]] (partitore RC)
3. Esercizi di [[Esercizi - Le potenze in alternata]] (potenze + rifasamento)
4. Esercizio base di [[Esercizi - Filtri passivi del primo ordine]] (frequenza di taglio RC)
5. Esercizio introduttivo di [[Esercizi - Diodi]] (raddrizzatore a semionda)
6. Esercizio di [[Esercizi - BJT]] (calcolo del punto di lavoro in partitore)

> [!success] Traguardo
> Quando svolgi **tutti e 6** in meno di 90 minuti ciascuno, sei pronto per la prova scritta. Se sbagli ancora sui segni del rifasamento o sui quadranti, torna sui prerequisiti e rifalli.
