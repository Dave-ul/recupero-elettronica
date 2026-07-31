---
tags: [recupero, elettronica, transistor, jfet, amplificatore, vcr, p-channel]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) — Cap. 7 «Gli amplificatori a transistor», §3 «I transistor FET e gli amplificatori a FET», parte JFET pp. 358-365 (struttura, pinch-off, caratteristiche d'uscita del 2N3819 in FIG. 42 a p. 362). Conversione folio Cap. 7: pag. stampata = 2·PDF + 122."
prove: [scritta, orale, pratica]
---

# JFET — Struttura, regioni, polarizzazione, amplificatori

> [!info] Dove serve
> **Scritta Carli** (LETTERA): esercizi su transistor JFET a canale n (polarizzazione + amplificazione). **Orale Carli** (LETTERA): NON cita JFET — solo «diodo, circuiti AC, filtri 1° ordine». I confronti BJT/MOSFET/JFET all'orale sono **estensione naturale** ma non testualmente richiesti. **Pratica Protti**: identificazione pin, misura $I_{DSS}$ e $V_P$, transcaratteristica (rientrano in «tutto il programma svolto nell'anno» del registro elettronico).

Prerequisiti: [[Impedenza dei bipoli R, L, C]], [[Diodi]] (la giunzione gate-canale del JFET è proprio una giunzione p-n), [[MOSFET]] (la forma delle equazioni è molto simile), [[Amplificatori a BJT]] (modello per piccoli segnali).

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §10**.

## 1. Cos'è un JFET n-channel

Il **JFET** (Junction FET) ha il **gate connesso al canale tramite una giunzione p-n** che, durante il funzionamento normale, è **polarizzata inversamente**.

Terminali:
- **Gate (G)** — collegato a una regione che forma la giunzione inversa col canale.
- **Source (S)** e **Drain (D)** — come nel MOSFET.
- $V_{GS}$ può andare **solo** da $V_{GS(off)} \le V_{GS} \le 0{,}3\text{ V}$ (per JFET n-channel) — **NON** positivo.

> [!warning] Limite di pilotaggio
> A $V_{GS} > 0{,}3\text{ V}$ circa, la giunzione gate-canale entra in diretta → conduce corrente di gate incontrollata → il pilotaggio si "rompe". **Non si pilota mai un JFET n con $V_{GS} > 0$.**

---

## 2. Equazioni e curve caratteristiche (§§ 9 e 10 approfondiscono i grafici)

Equazione di progetto (regione di saturazione / pinch-off):

$$I_D = I_{DSS} \cdot \left(1 - \frac{V_{GS}}{V_P}\right)^2$$

Parametri del dispositivo:
- $V_P$ = tensione di **pinch-off** (negativa nei JFET n-channel; tipicamente $-2\text{ V} \div -8\text{ V}$).
- $I_{DSS}$ = corrente di drain con $V_{GS}=0$ (la corrente massima; tipicamente 1–20 mA).

Curve tipiche:
- $V_{GS} = 0$ → $I_D = I_{DSS}$ (conduzione massima).
- $V_{GS} = V_P$ → $I_D = 0$ (cutoff).
- Tra i due valori: andamento parabolico (analogo al MOSFET enhancement, ma con $V_{GS} \le 0$).

---

## 3. Regioni di funzionamento

| Regione | Condizione | Comportamento |
|---|---|---|
| **Cutoff** | $V_{GS} \le V_P$ | $I_D = 0$ |
| **Triodo (resistiva)** | $V_{GS} > V_P$ e $V_{DS}$ piccolo ($V_{DS} < V_{GS} - V_P$) | $R_{DS}$ controllata da $V_{GS}$ |
| **Saturazione (pinch-off)** | $V_{GS} > V_P$ e $V_{DS} \ge V_{GS} - V_P$ | $I_D \approx \text{cost}$, data da $V_{GS}$ |
| **Breakdown** | $V_{DS} > V_{BR}$ (tipicamente 20–50 V) | Guasto, corrente incontrollata |

---

## 4. Polarizzazione

A differenza del MOSFET (dove la $V_{GS}$ può essere fissata direttamente da un partitore), nel JFET n $V_{GS}$ **deve essere $\le 0$** → la polarizzazione standard è la **autopolarizzazione con $R_S$**.

### Schema classico

```
V_DD
 │
 R_D
 │
 ├──── V_out (sul drain)
 │
 D
 │
 │
 S ──┬── R_S ── GND
     │
     (R_G dal source al gate, opzionale)
     │
     Gate
```

Quasi sempre si aggiunge $R_G$ dal gate verso massa per dare un riferimento DC al gate. Poiché la corrente di gate è ≈ 0 (giunzione inversa), $R_G$ non è percorsa da corrente → $V_G = 0$ e quindi:

$$V_{GS} = V_G - V_S = 0 - I_D R_S = - I_D R_S$$

### Calcolo del punto di lavoro

$$I_D = I_{DSS} \cdot \left(1 - \frac{V_{GS}}{V_P}\right)^2 = I_{DSS} \cdot \left(1 + \frac{I_D R_S}{V_P}\right)^2$$

(perché $V_P<0$ e $V_{GS}=-I_D R_S<0$; il "$+$" è corretto dopo la sostituzione).

Anche qui è un'**equazione di 2° grado** in $I_D$. La radice valida è quella **più piccola** (per garantire $V_{GS}>V_P$ in saturazione).

### Retta di carico

$$V_{DS} = V_{DD} - I_D (R_D + R_S)$$

Verifica: $V_{DS} \ge V_{GS} - V_P$ per essere in saturazione (pinch-off).

> [!danger] **Se $\Delta < 0$ nel 2° grado: la polarizzazione è FISICAMENTE IMPOSSIBILE**
> Il 2° grado dell'autopolarizzazione ($I_D R_S + V_{GS} = 0$ + parabolica di Shockley) può dare discriminante **negativo**. Significa che non esiste alcun punto di lavoro in saturazione: il JFET, con quei valori di $R_S$, $I_{DSS}$, $V_P$, o resta bloccato in zona triodo (sotto pinch-off) o oscilla tra cutoff e massima corrente. Soluzione pratica:
> 1. **Riduci $R_S$** finché $\Delta \geq 0$ (tipicamente serve $R_S \le |V_P|/(2 I_{DSS})$).
> 2. **Cambia JFET** con $V_P$ più negativo (JFET "meno sensibile").
> 3. Usa **degenerazione di source** (vedi §13) — ma attenzione: questo non risolve il problema del $\Delta$, lo mitiga solo tramite partitore.
> Alla Carli scritta, se vedi $\Delta < 0$, scrivi: "con questi valori il JFET non può lavorare in saturazione autonoma" + motivazione + alternativa proposta. È un **7/8 garantito** in molte griglie di correzione.

---

## 5. Esempio numerico (costruito)

**Dati:** $V_{DD}=15\text{ V}$, $R_D=2{,}2\text{ k}\Omega$, $R_S=220\text{ }\Omega$, $I_{DSS}=8\text{ mA}$, $V_P=-4\text{ V}$.

**Svolgimento:**

1. **Gate:** $V_G = 0$ (corrente di gate ≈ 0, $R_G$ verso massa).

2. **Source:** $V_{GS} = 0 - I_D R_S = -0{,}22 \cdot I_D$ (con $I_D$ in mA).

3. **Equazione parabolica** del JFET (con $V_P = -4$, $V_{GS} < 0$):
   $$I_D = 8 \cdot \left(1 - \frac{-0{,}22 I_D}{-4}\right)^2 = 8 \cdot \left(1 - 0{,}055 I_D\right)^2$$

4. **Espansione:**
   $$I_D = 8 \cdot \left(1 - 0{,}11 I_D + 0{,}003025 I_D^2\right) = 8 - 0{,}88 I_D + 0{,}0242 I_D^2$$

5. **Equazione di 2° grado:**
   $$0{,}0242 I_D^2 - 1{,}88 I_D + 8 = 0$$

6. **Radici:**
   $$\Delta = 1{,}88^2 - 4 \cdot 0{,}0242 \cdot 8 = 3{,}534 - 0{,}774 = 2{,}76$$
   $$I_D = \frac{1{,}88 \pm \sqrt{2{,}76}}{0{,}0484} = \frac{1{,}88 \pm 1{,}66}{0{,}0484}$$

   - $I_{D1} = 3{,}54/0{,}0484 \approx 73{,}1\text{ mA}$ → sopra $I_{DSS}=8\text{ mA}$: **SCARTATA** (fisicamente impossibile).
   - $I_{D2} = 0{,}22/0{,}0484 \approx 4{,}55\text{ mA}$ → $V_{GS} \approx -1{,}0\text{ V}$, sopra $V_P=-4\text{ V}$: ✅ **ACCETTATA**.

7. **Tensione $V_{DS}$:**
   $$V_{DS} = 15 - 4{,}55 \cdot (2{,}2 + 0{,}22) = 15 - 11{,}0 \approx 4{,}0\text{ V}$$

8. **Verifica pinch-off**: serve $V_{DS} > V_{GS} - V_P$.
   $V_{GS} - V_P = -1{,}0 - (-4) = 3{,}0\text{ V}$. $V_{DS} = 4{,}0 > 3{,}0$ → ✅ **in saturazione**.

> [!check] Risultato
> $I_D \approx 4{,}55\text{ mA}$, $V_{DS} \approx 4{,}0\text{ V}$, $V_{GS} \approx -1{,}0\text{ V}$, **in saturazione**.

### 5.1 Cosa succede se $R_S$ è troppo grande?

Con $R_S = 1\text{ k}\Omega$ e gli stessi altri parametri:

- $V_{GS} = -I_D \cdot R_S = -I_D$
- $I_D = 8 \cdot (1 - I_D/(-4))^2 = 8 \cdot (1 - I_D/4)^2$
- $\Rightarrow 0{,}5 I_D^2 - 5 I_D + 8 = 0 \Rightarrow \Delta = 9 \Rightarrow I_D = 2\text{ mA}$ (radice valida, $V_{GS}=-2\text{ V}$)

→ Esiste ancora soluzione, ma il JFET è molto "schiacciato" vicino alla zona triodo. In laboratorio si misura una $V_{DS}$ vicina al ginocchio della caratteristica.

> [!warning] Quando la polarizzazione diventa "borderline"
> Il discriminante dell'equazione di 2° grado è **sempre positivo** (per la struttura stessa dell'equazione di autopolarizzazione). Tuttavia, per valori di $R_S$ molto grandi (es. $R_S \cdot I_{DSS} \approx |V_P|$), la soluzione valida ha $V_{GS}$ vicino a $V_P$: il JFET resta in pinch-off ma **molto vicino al cutoff**. In questa zona, piccole variazioni di $V_{DD}$ o di $I_{DSS}$ (per temperatura o per tolleranza del componente) provocano grandi salti di $I_D$: la polarizzazione è **instabile**. Per evitare il problema, in laboratorio si aggiunge un partitore al source ($R_1, R_2$ in serie a $R_S$), così $V_{GS}$ è fissata direttamente dal partitore e non più solo dalla caduta su $R_S$.

---

## 6. Quesiti tipo — Guida rapida (teoria)

> [!question] JFET vs MOSFET enhancement: chi ha il pilotaggio "più pulito"?
> Il **MOSFET enhancement**: gate isolato dall'ossido → corrente di pilotaggio ≈ 0, e $V_{GS}$ può essere **positivo o negativo**.
> Il **JFET**: gate connesso tramite giunzione → deve stare in inversa, quindi $V_{GS} \le 0$.

> [!question] Perché un JFET n non può avere $V_{GS} > 0$?
> Perché la giunzione gate-canale andrebbe in diretta, e la corrente di gate crescerebbe distruggendo il pilotaggio. Il JFET n si pilota solo con $V_{GS}$ tra $V_P$ (negativo) e 0.

> [!question] Dove si usa un JFET oggi?
> Principalmente in:
> - **Amplificatori a basso rumore all'ingresso** (pre-amp di strumentazione, audio Hi-Fi, stadio RF).
> - **Interruttore analogico** in elettronica di precisione (commutazione di piccoli segnali con alta impedenza OFF).
> - **Resistenza controllata in tensione (VCR)** in AGC, compressori audio, mixer.
> NON si usa in logica digitale: è più lento e difficile da integrare rispetto al MOSFET.

> [!question] Forma della curva $I_D(V_{GS})$ in saturazione del JFET?
> $I_D = I_{DSS} \cdot (1 - V_{GS}/V_P)^2$ → parabolica (analoga a quella del MOSFET enhancement, ma con parametri diversi: $V_P<0$ e la curva ha il picco a $V_{GS}=0$, non a $V_{GS}>V_{th}$).

> [!question] Come si polarizza un JFET n in pratica?
> Quasi sempre con **autopolarizzazione**: $R_S$ tra source e massa, $R_G$ tra source e gate (per dare $V_G = V_S$... o meglio $V_G=0$ con $R_G$ a massa), $R_D$ tra $V_{DD}$ e drain. La $V_{GS}$ negativa nasce "automaticamente" dalla caduta su $R_S$.

> [!question] Quando si preferisce il JFET al BJT in uno stadio di ingresso?
> Quando serve un'**alta impedenza di ingresso**: il JFET ha $Z_{in} \approx 10^{10}\text{ }\Omega$ (grazie alla giunzione gate-canale inversa), il BJT ha $Z_{in} \approx \beta \cdot r_\pi \approx \text{k}\Omega\text{―M}\Omega$. Esempio tipico: pre-amp per microfoni a condensatore, pickups piezo, strumentazione.

> [!question] Cosa significa "transconduttanza" $g_m$?
> È la **pendenza della transcaratteristica**: $g_m = \Delta I_D / \Delta V_{GS}$. Misura "quanto $I_D$ cambia per unità di variazione di $V_{GS}$". È il parametro principale del JFET usato come amplificatore. (Vedi §10.)

---

## 7. Confronto sintetico MOSFET vs JFET

| Caratteristica | MOSFET enhancement n | JFET n |
|---|---|---|
| Gate | Isolato (ossido) | Giunzione p-n (inversa) |
| Corrente di gate | ~0 (leakage) | Piccola (µA inversa) |
| $V_{GS}$ può essere positivo? | **Sì** | **No** |
| A $V_{GS}=0$ | Non conduce ($I_D = 0$) | Conduce ($I_D = I_{DSS}$) |
| Pilotaggio tipico | CMOS, switching di potenza, amplificatori | Amplificatori a basso rumore, switches analogici |
| Equazione di design | $I_D = K (V_{GS} - V_{th})^2$ | $I_D = I_{DSS} (1 - V_{GS}/V_P)^2$ |

> [!tip] Convenzione
> La formula parabolica è la stessa forma; cambia solo il parametro di "riferimento": $V_{th}>0$ per il MOSFET enhancement, $V_P<0$ per il JFET n.

---

## 8. Da qui in poi

- Prerequisiti: [[Impedenza dei bipoli R, L, C]], [[Diodi]], [[MOSFET]]
- Confronto (sezione di [[BJT]]): BJT vs MOSFET vs JFET
- Esercizi: [[Esercizi - JFET]]
- Riferimenti libro: Mirandola Vol.2, **Cap. 7 §3 «I transistor FET», parte JFET pp. 358-365** (struttura del JFET a canale N, condizione di pinch-off, caratteristiche d'uscita del 2N3819 in FIG. 42 a p. 362)
- Riferimenti online: https://www.edutecnica.it/elettronica/jfet/jfet.htm

---

# ⤵ NUOVI CAPITOLI — Approfondimenti richiesti dalla lettera di giudizio sospeso ⤵

> [!info] Nota di percorso
> Le sezioni che seguono (9–20) approfondiscono tutti i sottoargomenti del JFET che la lettera di giudizio sospeso menziona (anche vagamente). Sequenza consigliata: leggere 9 e 10 (curve e $g_m$), poi 11–13 (amplificatori), poi 14–15 (VCR e switch), poi 16–17 (P-channel e piedinature), infine 18–20 (misure lab, temperatura, confronto BJT).

---

## 9. Curve caratteristiche: transcaratteristica e famiglia di uscita

### 9.1 Transcaratteristica $I_D$ vs $V_{GS}$

È la curva chiave: a $V_{DS}$ fisso (in saturazione), come varia $I_D$ al variare di $V_{GS}$?

```
  I_D ↑
       │        ╱╲ ← curva parabolica
  I_DSS│       ╱  ╲      I_D = I_DSS · (1 - V_GS/V_P)²
       │      ╱    ╲
       │     ╱      ╲
       │    ╱        ╲
       │   ╱          ╲
       │  ╱            ╲
       │ ╱              ╲
       │╱                ╲
   ────┼──────┼───────────┼──→ V_GS
       0      V_P/2       V_P (negativo, ← attenzione ai segni!)
```

Punti notevoli:
- $V_{GS} = 0$: $I_D = I_{DSS}$ (conduzione massima).
- $V_{GS} = V_P$ (negativo): $I_D = 0$ (cutoff).
- $V_{GS} = V_P/2$: $I_D = I_{DSS}(1 - 1/2)^2 = I_{DSS}/4$ (un quarto della corrente massima).

> [!tip] "A metà di $V_P$, la corrente è un quarto"
> È una regola mnemonica comoda: a $V_{GS} = V_P/2$ (sempre negativo!), la corrente è $I_{DSS}/4$, NON $I_{DSS}/2$ (parabola!).

### 9.2 Famiglia di curve di uscita $I_D$ vs $V_{DS}$

Per ogni valore di $V_{GS}$ (a passi di 1 V), si disegna una curva $I_D(V_{DS})$:

```
  I_D ↑
       │   V_GS=0   V_GS=-1   V_GS=-2   V_GS=-3   V_GS=-4 (=V_P)
       │     │        │        │        │        │
       │     │        │        │        │        │ ← I_DSS (≈ 8 mA)
  I_DSS│─────●────────●────────●────────●────────●
       │     │        │        │        │        │
       │     │ ╱      │ ╱      │ ╱      │ ╱      │
       │     │╱       │╱       │╱       │╱       │
       │     ●────────●────────●────────●────────●
       │   ╱│       ╱│       ╱│       ╱│         
       │  ╱ │      ╱ │      ╱ │      ╱ │ ← regione triodo (resistiva)
       │ ╱  │     ╱  │     ╱  │     ╱  │    pendenza = 1/R_DS(on)
       │╱   │    ╱   │    ╱   │    ╱   │
   ────┼────┼───┼────┼───┼────┼───┼────┼────→  V_DS
       │    V_GS-V_P ↑ pinch-off (locus parabolico)
```

Caratteristiche della famiglia:
- **Zona triodo (resistiva)**: per $V_{DS} < V_{GS} - V_P$, $I_D \approx V_{DS}/R_{DS(on)}$ con $R_{DS}$ controllata da $V_{GS}$.
- **Zona saturazione (pinch-off)**: per $V_{DS} \ge V_{GS} - V_P$, $I_D$ è circa costante. Il "locus" dei punti di pinch-off ($V_{DS} = V_{GS} - V_P$) è una parabola (è proprio $V_{GS} - V_P$ al variare di $V_{GS}$!).
- **Zona breakdown**: per $V_{DS} > V_{BR}$ (tipicamente 20–50 V), $I_D$ sale a "valanga" → guasto.

> [!danger] Dove operare in amplificazione
> Il JFET come amplificatore lavora in **saturazione**: la corrente $I_D$ è controllata solo da $V_{GS}$, non da $V_{DS}$ (entro un ampio range). Questo è ciò che lo rende utile come "valvola di corrente controllata".

---

## 10. Transconduttanza $g_m$ — il parametro chiave per piccoli segnali

### 10.1 Definizione

$$g_m = \frac{\partial I_D}{\partial V_{GS}}\bigg|_{V_{DS}=\text{cost}}$$

È la **pendenza locale** della transcaratteristica: "di quanto varia $I_D$ per una piccola variazione di $V_{GS}$".

Unità di misura: siemens (S) o mS (millisiemens). Per JFET piccolo segnale: $g_m = 1\text{ – }10\text{ mS}$ tipici.

### 10.2 Formule

Derivando la parabolica $I_D = I_{DSS} (1 - V_{GS}/V_P)^2$ rispetto a $V_{GS}$:

$$g_m = \frac{2 I_{DSS}}{-V_P} \cdot \left(1 - \frac{V_{GS}}{V_P}\right) = g_{m0} \cdot \left(1 - \frac{V_{GS}}{V_P}\right)$$

dove $g_{m0} = 2 I_{DSS} / |V_P|$ è la **transconduttanza a $V_{GS}=0$** (massima).

> [!tip] Linearità di $g_m$ in $V_{GS}$
> Sorprendentemente, $g_m(V_{GS})$ è **lineare** in $(1 - V_{GS}/V_P)$. Quindi, mentre $I_D$ cresce come una parabola, $g_m$ cresce in modo lineare fino al massimo a $V_{GS}=0$.

### 10.3 Esempio numerico

Con $I_{DSS}=8\text{ mA}$, $V_P=-4\text{ V}$, $V_{GS}=-1\text{ V}$:
- $g_{m0} = 2 \cdot 8 / 4 = 4\text{ mS}$
- $g_m = 4 \cdot (1 - (-1)/(-4)) = 4 \cdot (1 - 0{,}25) = 3\text{ mS}$

Significato: una variazione $\Delta V_{GS}$ di 1 mV provoca $\Delta I_D = g_m \cdot \Delta V_{GS} = 3\text{ mS} \cdot 1\text{ mV} = 3\text{ }\mu\text{A}$.

---

## 11. Amplificatore Source Comune (CS) — piccolo segnale

### 11.1 Schema

```
        V_DD
         │
         R_D
         │
   V_out ┤
         │  D
         │
         │  ●──── v_gs ─── (signal)
       JFET
         │  G
         │
         R_G (verso massa o verso partitore)
         │
   ─── S ─┴── R_S ── massa
```

(R_S spesso bypassato da $C_{S}$ alle frequenze di centro banda.)

### 11.2 Modello per piccoli segnali

Nel modello a piccolo segnale (AC), il JFET è equivalente a un **generatore di corrente controllato in tensione** $g_m \cdot v_{gs}$ (sull'uscita drain-source), con gate "aperto" (resistenza di gate ≈ ∞ data la giunzione inversa).

```
        v_gs (ingresso, gate → source)
         │
         ├──► ─ ─ ─ ─ ─ ─ ─ ─ ─┐
         │                     │
         │    [g_m · v_gs]     │  (generatore di corrente verso source)
         │    (drain → source) │
         │                     │  R_D verso V_DD (= AC massa)
         │                     │
       ─────────────────────────┘  (source a massa)
```

### 11.3 Guadagno di tensione $A_v$ in centro banda

Con $R_S$ **bypassato** da $C_S$ (cioè AC a massa sul source):

$$A_v = -g_m \cdot (R_D \parallel R_L)$$

Dove $R_L$ è il carico (se presente). Il segno "-" indica **inversione di fase** (180°, come nel BJT CE).

> [!example] Esempio numerico: amplificatore CS con $g_m = 3\text{ mS}$, $R_D = 2{,}2\text{ k}\Omega$, $R_L = 4{,}7\text{ k}\Omega$.
> - $R_D \parallel R_L = (2{,}2 \cdot 4{,}7)/(2{,}2 + 4{,}7) = 10{,}34 / 6{,}9 \approx 1{,}50\text{ k}\Omega$.
> - $A_v = -3\text{ mS} \cdot 1{,}50\text{ k}\Omega = -4{,}5$.
> In dB: $A_v \approx 20\log_{10}(4{,}5) \approx 13\text{ dB}$ (guadagno modesto, tipico del JFET).

Con $R_S$ **non bypassato**:

$$A_v = -\frac{g_m \cdot R_D}{1 + g_m \cdot R_S}$$

> [!warning] Quando il source è non bypassato
> Il guadagno **cala** a $-g_m R_D / (1 + g_m R_S)$: per $g_m R_S \gg 1$, si riduce a $-R_D/R_S$ (comportamento "resistivo", indipendente da $g_m$ → molto stabile al variare del transistor e della temperatura). È il tradeoff guadagno/stabilità.

### 11.4 Resistenza di ingresso e uscita

- **$R_{in}$** (vista dall'ingresso AC): $\approx R_G$ (di solito $1\text{ M}\Omega$ o più). **ALTISSIMA** rispetto al BJT CE ($\sim$k$\Omega$). È il vantaggio principale del JFET.
- **$R_{out}$** (vista dall'uscita): $\approx R_D$ (trascurando $r_d$, che è grande in saturazione).

---

## 12. Amplificatore Drain Comune / Source Follower (CD)

### 12.1 Schema

```
        V_DD
         │   (drain direttamente a V_DD!)
         │
         ●  D
         │
       JFET
         │  G ← v_in (al gate)
         │
   v_out ●  S (segnale di uscita sul source!)
         │
         R_S (verso massa)
```

Qui il **drain è direttamente a $V_{DD}$** (AC = massa). L'uscita è presa sul source.

### 12.2 Guadagno

$$A_v = \frac{g_m R_S}{1 + g_m R_S} \approx 1 \text{ (per } g_m R_S \gg 1\text{)}$$

Nessuna inversione di fase: l'uscita "segue" l'ingresso, attenuata di poco (es. $A_v = 0{,}95$).

### 12.3 Perché si usa

È un **buffer**:
- $R_{in} \approx R_G$ (altissima, ottima).
- $R_{out} = R_S \parallel (1/g_m) \approx 1/g_m$ (bassa, ottima per pilotare carichi).

Applicazione tipica: adattatore di impedenza tra uno stadio ad alta impedenza (pickup piezo, microfono a condensatore) e uno stadio a bassa impedenza (cavo, amplificatore di potenza).

---

## 13. Amplificatore CS con degenerazione di source

Combinazione dei due: CS con $R_S$ **non bypassato** da $C_S$.

$$A_v = -\frac{g_m R_D}{1 + g_m R_S}$$

- **Stabilità**: il guadagno dipende solo da $R_D/R_S$ (rapporto di resistori), non da $g_m$ del transistor. Poco sensibile a variazioni di $V_P$, $I_{DSS}$, temperatura.
- **Tradeoff**: $A_v$ è **più basso** rispetto al CS puro. Si perde linearità (distorsione minore), si guadagna stabilità.

> [!tip] Per l'orale Carli
> "Perché in certi schemi c'è $R_S$ non bypassato accanto al BJT o al JFET?" → "Per stabilizzare il punto di lavoro e linearizzare il guadagno, al prezzo di $|A_v|$ più basso."

---

## 14. JFET come VCR (Voltage Controlled Resistor)

### 14.1 Idea

Nella **zona triodo** (vicino all'origine), il JFET si comporta come una **resistenza lineare** $R_{DS}$ controllata dalla tensione di gate $V_{GS}$:

$$R_{DS} \approx \frac{V_{DS}}{I_D}$$

Per la parabolica in zona triodo, vale approssimativamente:

$$R_{DS}(V_{GS}) \approx \frac{1}{K \cdot (V_{GS} - V_P)}$$

(per JFET n, con $K = 2 I_{DSS}/V_P^2$).

### 14.2 Applicazioni tipiche

- **AGC** (Automatic Gain Control): $V_{GS}$ controllato dal livello del segnale → $R_{DS}$ cambia → guadagno di un amplificatore cambia → compressione automatica.
- **Compressore audio**: stessa idea, applicata al segnale musicale.
- **Mixer audio**: JFET usato come resistenza variabile tra due canali → controllo di volume manuale o automatico.
- **Oscillatori controllati in tensione (VCO)**: non è un JFET direttamente, ma è un principio simile (varicap).

> [!example] Esempio: dimensionare $V_{GS}$ per $R_{DS} = 1\text{ k}\Omega$
> Con $I_{DSS} = 8\text{ mA}$, $V_P = -4\text{ V}$:
> - $K = 2 \cdot 8 / 16 = 1\text{ mA/V}^2$. (Attenzione: in zona triodo le formule sono diverse dal pinch-off, qui è solo un'indicazione di massima.)
> - Serve sapere esattamente a quale $V_{DS}$ si opera; per $V_{DS}$ piccolo, $R_{DS}$ è dominato dal parametro $r_{DS(on)}$ del datasheet.

---

## 15. JFET come interruttore analogico (Analog Switch)

### 15.1 ON/OFF pilotati da $V_{GS}$

- **OFF**: $V_{GS} \le V_P$ → $I_D \approx 0$ → il JFET è un circuito aperto.
- **ON**: $V_{GS} \approx 0$ → $I_D$ tende a $I_{DSS}$ (zona triodo, $V_{DS}$ piccolo) → il JFET è una **resistenza piccola** $r_{DS(on)}$ (da pochi ohm a 100 Ω, da datasheet).

### 15.2 Applicazioni classiche

- **Sample-and-hold**: commutare un condensatore di memoria dentro/fuori dal segnale.
- **Multiplexer analogico**: selezionare uno tra più segnali da inviare a una linea ADC.
- **Chopper**: modulatore per segnali DC molto piccoli, in strumentazione di precisione.

### 15.3 Vantaggi rispetto a relé o transistor BJT

- **Velocità**: ns vs ms (1000 volte più veloce di un relé).
- **Resistenza ON bassa**: pochi ohm (BJT in saturazione ne ha alcuni).
- **Corrente di pilotaggio ≈ 0**: alta impedenza di controllo.
- **Assenza di offset**: il JFET non ha $V_{BE}$ come il BJT, quindi la tensione di uscita è "pulita".
- **Limite**: bassa tensione di breakdown (20–50 V), quindi inadatto a commutare tensioni alte.

---

## 16. JFET P-channel — il duale

### 16.1 Cosa cambia

Tutti i segni si invertono:

| Grandezza | JFET n-channel | JFET P-channel |
|---|---|---|
| $V_P$ | $< 0$ | $> 0$ |
| $V_{GS}$ operativo | $V_P \le V_{GS} \le 0$ | $0 \le V_{GS} \le V_P$ |
| Verso di $I_D$ | Da D a S | Da S a D |
| Alimentazione tipica | $V_{DD} > 0$ | $V_{SS} < 0$ |

L'equazione parabolica resta la stessa: $I_D = I_{DSS} (1 - V_{GS}/V_P)^2$, ma con $V_P>0$. Anche la zona operativa ($V_{GS}$ con valori **positivi**) è invertita.

### 16.2 Simbolo circuitale

Il simbolo cambia nella **direzione della freccia** sul gate: freccia **uscente** dal gate (verso l'esterno del canale) → canale p. Freccia **entrante** → canale n.

### 16.3 Esempio numerico (P-channel)

Dati: $I_{DSS} = -6\text{ mA}$ (negativo!), $V_P = +4\text{ V}$, $V_{GS} = +2\text{ V}$.

$$I_D = -6 \cdot (1 - 2/4)^2 = -6 \cdot (1/2)^2 = -6/4 = -1{,}5\text{ mA}$$

Il segno negativo di $I_D$ significa che la corrente convenzionale fluisce dal source al drain (in un P-channel, è il verso "naturale").

> [!warning] Trappola trabocchetto
> Alla Carli scritta, un JFET P-channel con $V_{DD} < 0$ e $V_{SS} > 0$ è un classico errore per chi applica le formule del canale n senza pensarci. **Verifica sempre i segni di $V_P$, $V_{GS}$, $V_{DD}$ prima di mettere numeri nei conti.**

---

## 17. Piedinatura, package e simboli circuitali

### 17.1 Simboli circuitali

```
  JFET n-channel              JFET p-channel
  
        D                          D
        │                          │
   ─────┤────                ──────┤────
        │ ← freccia                │ freccia →
        │ verso il                 │ verso
        │ canale                   │ l'esterno
   ─────┤────                ──────┤────
        │                          │
        S                          S
        │
        G (freccia dal basso verso l'alto = verso il canale; l'altra polarità = p-channel)
```

### 17.2 Package TO-92 (il più comune per JFET discreti)

Per il JFET n-channel tipo 2N3819, 2N4222, MP102 etc., package TO-92 con piedini:

```
   Vista dal basso               Vista frontale
   (lato piatto)                 
  
      ┌──┐                        ●
   1 ─┤  ├─ 3   ──→   G  D  S    /│\
      │  │                       / │ \
   2 ─┤  ├       (in ORDINE     G  D  S
      └──┘         ANTIORARIO   )
                                
         1 = Drain
         2 = Source
         3 = Gate
```

> [!danger] Convenzioni invertite tra produttori
> Le piedinature G-D-S e G-S-D si trovano entrambe a seconda del produttore. ** consultare SEMPRE il datasheet** prima di montare. Un errore di piedinatura col JFET è meno catastrofico che col BJT (bassi livelli di potenza), ma porta a comportamenti strani.

### 17.3 Identificazione pratica con multimetro

Per riconoscere S, D, G senza datasheet:
1. Multimetro in modalità **test diodi**.
2. Misura tra ogni coppia di pin: una coppia mostrerà **una caduta di tensione** ($\sim 0{,}5\text{ – }0{,}7\text{ V}$) e una polarità di giunzione → è la giunzione **Gate-Canale**.
3. Il pin che è dal lato "anodo" della giunzione è il **Gate**; gli altri due sono **Source** e **Drain**.
4. Per distinguere S da D: il multimetro non basta (sono simmetrici nella struttura!), serve il datasheet OPPURE la prova funzionale (colleghi in un circuito e vedi quale polarità funziona).

---

## 18. Misure in laboratorio (per Protti)

### 18.1 Misura di $I_{DSS}$

Setup:
- $V_{GS} = 0$ → collegare Gate a Source (**cortocircuitare G e S**).
- $V_{DS} \approx 5\text{ – }10\text{ V}$ → alimentazione tramite milliamperometro in serie al drain.
- $R_D$ di protezione (es. $100\text{ }\Omega$) per limitare la corrente in caso di pin invertiti.

Lettura: il milliamperometro misura $I_D = I_{DSS}$ direttamente. Per un 2N3819 tipico: $I_{DSS} \approx 2\text{ – }20\text{ mA}$ (verrà specificato nel datasheet).

### 18.2 Misura di $V_P$ ($V_{GS(off)}$)

Setup:
- Aumentare la resistenza di source (es. $R_S = 1\text{ M}\Omega$) così che $V_{GS}$ diventi molto negativo.
- $V_{GS} = -I_D \cdot R_S$, sempre in saturazione.
- Aumentare $R_S$ finché $I_D$ diventa trascurabile (es. $< 10\text{ }\mu\text{A}$).
- $V_P \approx -I_D \cdot R_S$ a quel punto.

In pratica: con $R_S$ variabile (potenziometro), regolare finché $I_D$ non crolla a zero → leggere la $V_{GS}$ dal potenziometro: è $V_P$.

### 18.3 Tracciamento della transcaratteristica a punti

Setup con alimentatore variabile, multimetri per $V_{GS}$ e $I_D$:
1. Polarizza il JFET in un circuito noto (es. autopolarizzazione).
2. Misura $I_D$ a vari $V_{GS}$ (spazzolando il partitore di gate).
3. Tabula e disegna la curva $I_D(V_{GS})$.
4. Adatta la curva parabolica $I_D = I_{DSS}(1 - V_{GS}/V_P)^2$ ai dati → ricava $I_{DSS}$ e $V_P$.

### 18.4 Misura del guadagno di un amplificatore CS

1. Misura $V_{CE}$ (o $V_{DS}$) a riposo → deve essere metà di $V_{DD}$ (in saturazione).
2. Applica un segnale sinusoidale piccolo (decine di mV) al gate.
3. Misura $A_v = V_{out,pp}/V_{in,pp}$ con l'oscilloscopio (i due canali).
4. Verifica l'inversione di fase (180°) tra ingresso e uscita.
5. Aumenta $f$ finché il guadagno cala di $1/\sqrt{2}$ → è la $f_H$.

---

## 19. Effetto della temperatura e punto ZTC

### 19.1 Due effetti contrastanti

Quando il JFET si scalda:
- ⬇ La **mobilità dei portatori** nel canale DIMINUISCE (per agitazione termica) → $I_D$ tende a calare.
- ⬇ La **barriera di potenziale** della giunzione gate-canale DIMINUISCE (~2 mV/°C) → l'effetto di "strozzamento" del canale si riduce → $I_D$ tende a salire.

### 19.2 Il punto ZTC (Zero Temperature Coefficient)

I due effetti si compensano esattamente in un **punto di lavoro specifico**:
- Se $V_{PZTC} \approx V_P + 0{,}7\text{ V}$ (per JFET n) → in quel punto, $I_D$ è **stabile in temperatura**.

In pratica: se il JFET è polarizzato a $V_{GS} \approx V_P/2$ (la "regola del quarto di corrente" vista sopra), la stabilità termica è già accettabile. Polarizzare a $V_{GS}=0$ (cioè $I_D = I_{DSS}$) → JFET molto sensibile alla temperatura.

> [!tip] Per il laboratorio Protti
> Se vedi che il circuito si "scalda" e la polarizzazione slitta, controlla se sei vicino al punto ZTC.

---

## 20. Confronto JFET vs BJT nel pre-amplificatore

### 20.1 Tabella comparativa per applicazioni audio/RF/instrumentazione

| Caratteristica | JFET (es. 2N3819) | BJT (es. BC547) |
|---|---|---|
| Pilotaggio | Tensione ($V_{GS}$) | Corrente ($I_B$) |
| $Z_{in}$ tipica | $\sim 10^{10}\text{ }\Omega$ | $\sim 10^5\text{ – }10^6\text{ }\Omega$ |
| Corrente di pilotaggio DC | ≈ 0 | $\sim I_C/\beta$ |
| Rumore | **Basso** (resistivo, no shot noise B-E) | Più alto (shot noise nella giunzione B-E) |
| Tensione di offset | Bassa | $V_{BE} \approx 0{,}7\text{ V}$ (va bilanciata) |
| Velocità di commutazione | Buona ma inferiore al MOSFET | Buona (transistor più maturo) |
| Disponibilità / costo | Minore, più caro | Ubiquitario, economico |

### 20.2 Quando si sceglie il JFET

- **Pre-amplificatori a basso rumore**: stadio input di un Hi-Fi, strumentazione di misura, microfono a condensatore.
- **Applicazioni ad alta impedenza**: pickup piezo, sensori ad alto $Z$.
- **Circuiti analogici a lunga costante di tempo**: $R \cdot C$ grandi, dove l'alta $Z_{in}$ del JFET è essenziale.

### 20.3 Quando si sceglie il BJT

- **Amplificatori a guadagno elevato** (con pochi stadi).
- **Applicazioni a bassa tensione di alimentazione**: il BJT ha bisogno di ~0,7 V per accendersi, il JFET no.
- **Pilotaggio preciso**: la relazione $\beta I_B = I_C$ è "lineare" e ben modellizzata.

---

## 21. Limitazioni pratiche e zona di breakdown

### 21.1 Tensione di breakdown

Ogni JFET ha un $V_{(BR)DSS}$ massimo (tipicamente 20–50 V, da datasheet). Operare oltre questo valore → guasto irreversibile.

### 21.2 Corrente di gate inversa a caldo

A temperature elevate, la giunzione gate-canale (anche in inversa) ha una **corrente di perdita** che cresce. In applicazioni di precisione, questo può disturbare la polarizzazione.

### 21.3 Corrente di perdita drain-source in cutoff

Anche quando "spento" ($V_{GS} \le V_P$), un JFET reale ha una piccola corrente $I_{D(off)}$ di qualche µA o nA. Tranne che per applicazioni estreme, è trascurabile.

### 21.4 Variabilità dei parametri

$I_{DSS}$ e $V_P$ hanno **tolleranze ampie** (anche ±50% rispetto al valore nominale). Due JFET dello stesso lotto possono dare risultati abbastanza diversi. Per questo la polarizzazione più stabile è quella con degenerazione di source.

---
