---
tags: [recupero, elettronica, bjt, transistor, polarizzazione, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ (2026-07-19) — Mirandola Vol.2, Cap. 7 «Gli amplificatori a transistor», pp. 312-347 (pagg.-PDF 95-112). Riferimenti d'esercizio: maglie d'ingresso/uscita formule 7.5-7.6 p. 323 · ESEMPIO 3 (punto di lavoro) pp. 324-325 · ESEMPIO 4 (dimensionamento con resistenza di base) p. 327 · procedura di dimensionamento con partitore, formule 7.8-7.11, ed ESEMPIO 5 pp. 328-329 · BJT in commutazione ed ESEMPIO 6 pp. 330-331. Mappa completa delle sezioni in [[BJT]]."
prove: [scritta, orale]
---

# Esercizi — transistor BJT

Teoria di riferimento: [[BJT]]

> [!tip] Come usare questa pagina
> Gli esercizi seguenti coprono i tre punti chiave delle prove Carli: calcolare il punto di lavoro, verificare la zona di funzionamento, e ragionare sui MOSFET/JFET in modo comparativo.

---

# Parte A — Quesiti (prova orale)

> [!question]- 1 — Perché la base di un BJT è fisicamente sottile?
> Per minimizzare la ricombinazione: solo una piccola frazione dei portatori iniettati dall'emettitore si ricombina in base, e la maggior parte attraversa la giunzione B-C e arriva al collettore. È il motivo del guadagno $\beta$ alto.

> [!question]- 2 — Cosa distingue la zona attiva dalla saturazione?
> Nella zona **attiva**, la giunzione B-E è polarizzata direttamente ($V_{BE} \approx 0{,}7\ \text{V}$) e la giunzione B-C è polarizzata inversamente. $I_C = \beta I_B$ è libera. Nella **saturazione**, **entrambe** le giunzioni sono dirette: $V_{CE} \approx 0{,}2\ \text{V}$ e $I_C$ è limitata dal circuito esterno (non da $\beta I_B$).

> [!question]- 3 — Perché un PNP ha segno opposto rispetto a un NPN?
> Perché le regioni sono invertite (p-n-p anziché n-p-n). Le tensioni e correnti hanno segni opposti: in PNP, $V_{BE} \approx -0{,}7\ \text{V}$, $V_{CE} \approx -V_{CC}/2$ a riposo.

> [!question]- 4 — Differenza sostanziale tra MOSFET e BJT?
> Il MOSFET è controllato in **tensione** ($V_{GS}$), con corrente di gate ≈ 0. Il BJT è controllato in **corrente** ($I_B$). Conseguenze:
> - Il MOSFET scalda meno in pilotaggio.
> - Il MOSFET è dominante nell'elettronica digitale (CMOS).
> - Il BJT è tradizionalmente preferito in amplificatori a basso rumore.

> [!question]- 5 — A cosa serve la resistenza di emettitore $R_E$?
> A stabilizzare il punto di lavoro contro le variazioni di $\beta$ e temperatura. Anche senza segnale, la $R_E$ "vede" $I_E$ che scorre e crea una caduta che contrasta le variazioni termiche di $V_{BE}$. C'è di solito un condensatore $C_E$ in parallelo che ripristina il guadagno ai piccoli segnali in AC.

---

# Parte B — Esercizi (prova scritta)

## Esercizio 1 — Calcolo del punto di lavoro (polarizzazione a $V_{BB}$)

**Testo.** Un transistor NPN con $\beta = 200$ è polarizzato con $V_{CC} = 12\ \text{V}$, $V_{BB} = 2\ \text{V}$, $R_B = 100\ \text{k}\Omega$, $R_C = 1\ \text{k}\Omega$. Calcola il punto di lavoro $I_C$ e $V_{CE}$.

**Soluzione:**

Calcolo di $I_B$ dalla maglia di base:
$$I_B = \frac{V_{BB} - V_{BE}}{R_B} = \frac{2 - 0{,}7}{100\,000} = 13\ \mu\text{A}$$

Calcolo di $I_C$:
$$I_C = \beta \cdot I_B = 200 \cdot 13 \cdot 10^{-6} = 2{,}6\ \text{mA}$$

Calcolo di $V_{CE}$:
$$V_{CE} = V_{CC} - I_C R_C = 12 - 2{,}6 \cdot 10^{-3} \cdot 1000 = 9{,}4\ \text{V}$$

**Verifica della zona di funzionamento:**
- $V_{BE} = 0{,}7\ \text{V}$ — positivo → giunzione B-E diretta ✅
- $V_{BC}$: l'emettitore è **a massa**, quindi i potenziali di base e collettore coincidono con le tensioni rispetto a massa: $V_B = V_{BE} = 0{,}7\ \text{V}$ e $V_C = V_{CE} = 9{,}4\ \text{V}$. Dunque
  $$V_{BC} = V_B - V_C = 0{,}7 - 9{,}4 = -8{,}7\ \text{V}$$
  negativo → giunzione B-C **inversa** ✅
- Il transistor è in **zona attiva** ✅

> [!check] Controllo di sanità
> $V_{CE} = 9{,}4\ \text{V}$ è tra $V_{CE,sat} = 0{,}2\ \text{V}$ e $V_{CC} = 12\ \text{V}$. C'è ampio margine sia verso la saturazione sia verso il cutoff.
>
> Inoltre $I_C = 2{,}6\ \text{mA}$ è positiva e non troppo grande: la potenza dissipata è $P_C = V_{CE} \cdot I_C = 9{,}4 \cdot 2{,}6 = 24\ \text{mW}$, ben entro i limiti di un BJT di segnale (tipicamente 200–500 mW).

---

## Esercizio 2 — Calcolo con partitore di base

**Testo.** Un transistor NPN con $\beta = 150$ ha questo circuito: $V_{CC} = 15\ \text{V}$, partitore con $R_1 = 100\ \text{k}\Omega$ (da $V_{CC}$ a base), $R_2 = 22\ \text{k}\Omega$ (da base a massa), $R_C = 2{,}2\ \text{k}\Omega$, $R_E = 1\ \text{k}\Omega$. Calcola il punto di lavoro.

**Soluzione:**

> [!note] Semplificazione
> Trascuriamo la corrente di base rispetto a quella del partitore ($I_B \ll I_{R_1}$). Questa è un'approssimazione standard per analisi di prima mano; per valori "precisi" si applica Thévenin al partitore.

Tensione di base:
$$V_B \approx V_{CC} \cdot \frac{R_2}{R_1 + R_2} = 15 \cdot \frac{22}{100 + 22} = 2{,}70\ \text{V}$$

Tensione di emettitore:
$$V_E = V_B - V_{BE} = 2{,}70 - 0{,}7 = 2{,}00\ \text{V}$$

Corrente di emettitore:
$$I_E = \frac{V_E}{R_E} = \frac{2{,}00}{1000} = 2{,}00\ \text{mA}$$

Corrente di collettore:
$$I_C \approx I_E = 2{,}00\ \text{mA}$$ (è $\beta/(\beta+1)$ ma con $\beta = 150$ la differenza è ~0,7%)

Tensione di collettore:
$$V_C = V_{CC} - I_C R_C = 15 - 2{,}00 \cdot 2{,}2 = 10{,}6\ \text{V}$$

Tensione collettore-emettitore:
$$V_{CE} = V_C - V_E = 10{,}6 - 2{,}00 = 8{,}6\ \text{V}$$

**Verifica zona:**
- $V_{BE} = 0{,}7\ \text{V}$ ✅ (diretta)
- $V_{BC} = V_B - V_C = 2{,}70 - 10{,}6 = -7{,}9\ \text{V}$ ✅ (inversa)
- → **Zona attiva** ✅

> [!check] Margine di saturazione
> $V_{CE} = 8{,}6\ \text{V}$. Il transistor può essere portato in saturazione solo se $I_C$ cresce di $\Delta I_C \geq V_{CE}/R_C = 8{,}6/2{,}2 = 3{,}9\ \text{mA}$. In zona attiva, $\Delta I_C = \beta \Delta I_B$, quindi serve $\Delta I_B \geq \Delta I_C / \beta = 3{,}9/150 \approx 26\ \mu\text{A}$ per saturare.

---

## Esercizio 3 — Identificazione della zona di lavoro

> [!warning] Esercizio di **analisi critica**, non di puro calcolo
> I dati sono volutamente al limite — l'obiettivo è allenarti a **verificare la coerenza** prima di accettare i risultati. In un esame vero, se trovi un risultato fisicamente impossibile, fermati e riconsidera ipotesi e calcoli.

**Testo.** Un transistor NPN con $\beta = 100$ ha: $V_{CC} = 9\ \text{V}$, $R_B = 470\ \text{k}\Omega$, $V_{BB} = 5\ \text{V}$ (ingresso DC). In uscita: $R_C = 1\ \text{k}\Omega$. Si misura $V_{CE} = 0{,}3\ \text{V}$. In che zona sta lavorando il transistor?

**Soluzione:**

$I_B$ dalla maglia di base:
$$I_B = \frac{V_{BB} - V_{BE}}{R_B} = \frac{5 - 0{,}7}{470\,\text{k}\Omega} = 9{,}15\ \mu\text{A}$$

Corrente di collettore **in zona attiva**:
$$I_C^{act} = \beta \cdot I_B = 100 \cdot 9{,}15\ \mu\text{A} = 0{,}915\ \text{mA}$$

Corrente di collettore **limite dalla saturazione** (se $V_{CE} = V_{CE,sat} = 0{,}3\ \text{V}$):
$$I_C^{max} = \frac{V_{CC} - V_{CE,sat}}{R_C} = \frac{9 - 0{,}3}{1\,\text{k}\Omega} = 8{,}7\ \text{mA}$$

Confronto: $I_C^{act} = 0{,}915\ \text{mA} \ll I_C^{max} = 8{,}7\ \text{mA}$.

**Verdetto**: la corrente "richiesta" dal $\beta I_B$ è **molto minore** di quella che il circuito può effettivamente far scorrere, quindi il transistor non è in saturazione. Eppure $V_{CE}$ è 0,3 V — **vicino a $V_{CE,sat}$**.

> [!danger] Conflitto nei dati — verificare la misura
> I dati del problema sono contraddittori. Se $V_{CE} = 0{,}3\ \text{V}$, il transistor è in saturazione. Ma con $I_B = 9{,}15\ \mu\text{A}$ e $\beta = 100$, "vorrebbe" solo $0{,}915\ \text{mA}$ — non abbastanza da saturare.
>
> Possibili spiegazioni:
> - $\beta$ è in realtà più alto (es. 250) → $I_C = 2{,}29\ \text{mA}$, ancora non basta.
> - C'è un errore di misura di $V_{CE}$.
> - C'è un altro componente (es. una resistenza di emettitore) non dichiarata.
>
> Nella prova scritta, in caso di dubbio: **scrivi l'analisi**, segnala l'incoerenza, concludi che i dati sono inconsistenti.

> [!tip] Lezione operativa
> Un BJT è in **saturazione** quando la corrente "richiesta" $\beta I_B$ è **maggiore** di quella che il circuito può fornire. In saturazione $V_{CE} \approx V_{CE,sat}$ e il transistor è "completamente ON". Un transistor è in **interdizione** quando $I_B \leq 0$ (o la giunzione B-E è off).

---

## Esercizio 4 — MOSFET enhancement: calcolo di $I_D$ e $V_{DS}$

**Testo.** Un MOSFET enhancement n-channel ha $V_{th} = 2\ \text{V}$ e $K = 0{,}5\ \text{mA/V}^2$. È montato con $V_{GS} = 5\ \text{V}$ e $R_D = 4{,}7\ \text{k}\Omega$ da $V_{DD} = 12\ \text{V}$ al drain.

Calcola $I_D$ e $V_{DS}$.

**Soluzione:**

Sopra soglia: $V_{GS} > V_{th}$, qui $5 > 2$ ✅. La tensione di *overdrive* è $V_{ov} = V_{GS} - V_{th} = 3$ V.

**Passo 1 — si ipotizza la saturazione** (è sempre il tentativo di partenza):

$$I_D = K (V_{GS} - V_{th})^2 = 0{,}5 \cdot 10^{-3} \cdot 3^2 = 4{,}5\ \text{mA}$$
$$V_{DS} = V_{DD} - I_D R_D = 12 - 4{,}5 \cdot 10^{-3} \cdot 4700 = 12 - 21{,}15 = -9{,}15\ \text{V}$$

**Passo 2 — l'ipotesi va rifiutata.**

> [!danger] Un $V_{DS}$ negativo NON significa "è in saturazione" — significa l'opposto
> $V_{DS} < 0$ è **fisicamente impossibile** in questo circuito: con $V_{DD} = 12$ V positiva e una sola $R_D$, il drain non può finire sotto massa. Il risultato assurdo è la prova per assurdo che **l'ipotesi di partenza era sbagliata**.
>
> La condizione di saturazione è $V_{DS} \ge V_{ov} = 3$ V. Abbiamo ottenuto $-9{,}15$ V, che la viola clamorosamente: la $R_D$ è troppo grande perché ci scorrano 4,5 mA. Il MOSFET lavora quindi in **zona di triodo**, dove $I_D$ dipende anche da $V_{DS}$ e risulta *minore* del valore di saturazione.

**Passo 3 — si risolve in zona di triodo**, dove vale

$$I_D = K\left[2(V_{GS}-V_{th})V_{DS} - V_{DS}^2\right]$$

messa a sistema con la maglia d'uscita $I_D = (V_{DD} - V_{DS})/R_D$:

$$0{,}5\left(6V_{DS} - V_{DS}^2\right) = \frac{12 - V_{DS}}{4{,}7} \quad\Longrightarrow\quad 2{,}35\,V_{DS}^2 - 15{,}1\,V_{DS} + 12 = 0$$

$$V_{DS} = \frac{15{,}1 \pm \sqrt{115{,}21}}{4{,}7} \;\Rightarrow\; V_{DS} = 5{,}50\ \text{V} \;\text{ oppure }\; V_{DS} = 0{,}93\ \text{V}$$

Si scarta la radice $5{,}50$ V perché **violerebbe la condizione di triodo** ($V_{DS} < V_{ov} = 3$ V). Resta:

$$\boxed{V_{DS} \approx 0{,}93\ \text{V} \qquad I_D = \frac{12 - 0{,}93}{4700} \approx 2{,}36\ \text{mA}}$$

*Verifica:* $0{,}5\,(6 \cdot 0{,}93 - 0{,}93^2) = 0{,}5 \cdot 4{,}71 = 2{,}36$ mA ✔ — e $I_D = 2{,}36 < 4{,}5$ mA, come deve essere in triodo.

> [!tip] Le due zone del MOSFET — e il metodo per capire in quale sei
> - **Triodo** (o "ohmica"): $V_{DS} < V_{GS} - V_{th}$. $I_D$ dipende **sia** da $V_{GS}$ **sia** da $V_{DS}$; per $V_{DS}$ molto piccola il MOSFET si comporta come un resistore comandato in tensione.
> - **Saturazione**: $V_{DS} \ge V_{GS} - V_{th}$. $I_D$ è costante, determinata solo da $V_{GS}$: il MOSFET è un generatore di corrente comandato.
>
> **Metodo d'esame**: ipotizza sempre la saturazione (i conti sono più semplici), calcola $V_{DS}$, poi **verifica** $V_{DS} \ge V_{ov}$. Se la verifica fallisce, rifai in triodo. Non "aggiustare" il segno del risultato.
>
> Per amplificatori si vuole la saturazione ($I_D$ stabile). Per interruttori si passa da triodo (ON) a interdizione ($V_{GS} < V_{th}$, OFF).

---

# Parte C — Quesiti di confronto (orale)

> [!success]- "Perché il MOSFET si usa nei circuiti digitali CMOS?"
> Perché scalda pochissimo: la corrente di gate è praticamente zero in DC. Il pilotaggio è in tensione, quindi un MOSFET statico dissipa $P = V_{DS} \cdot I_D$ solo quando è in conduzione. Nelle commutazioni CMOS, il consumo avviene solo durante le transizioni.

> [!success]- "Quando preferisco il BJT al MOSFET in un amplificatore?"
> In applicazioni a basso rumore (la giunzione p-n del BJT ha meno rumore 1/f rispetto all'ossido del MOSFET), in circuiti ad alta precisione (gli h-parameters del BJT sono molto controllati), o quando serve il classico CE con guadagno fino a 100–300 V/V.

> [!success]- "Confronto JFET vs MOSFET in un input strumentazione"
> Il JFET ha gate con giunzione p-n (quindi non assorbe corrente continua ma il leakage è presente); usato come input strumentazione ad alta impedenza. Il MOSFET a gate isolato ha impedenza anche più alta ma più sensibile a scariche elettrostatiche.

---

# Esercizi aggiuntivi (edutecnica.it)

> [!tip] Esercizi interattivi e svolti
> Vai alle pagine specifiche di **[edutecnica.it](https://www.edutecnica.it/)**:
>
> | Argomento | URL | Cosa trovi |
> |---|---|---|
> | **Esercizi sulla polarizzazione del BJT** | <https://www.edutecnica.it/elettronica/transistorx/transistorx.htm> | Raccolta di esercizi su polarizzazione fissa, partitore, Darlington con calcolo di $I_C$ e $V_{CE}$ |
> | **Esercizi sui MOSFET** | <https://www.edutecnica.it/elettronica/mosfetx/mosfetx.htm> | Esercizi su MOSFET enhancement/depletion in saturazione |
> | **Approfondimento amplificatore a JFET** | <https://www.edutecnica.it/elettronica/ajfet/ajfet.htm> | Analisi amplificatore a JFET |
>
> In particolare sono presenti esercizi su polarizzazione complessa e configurazione Darlington — vedi l'indice aggiornato sulla pagina del sito.

---

## Esercizi svolti da Edutecnica.it (catalogo transistorx)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/transistorx/transistorx.htm](https://www.edutecnica.it/elettronica/transistorx/transistorx.htm). 10 esercizi di polarizzazione BJT NPN.

### Es. B1 — NPN con $R_E$ (base da generatore + emettitore a massa)

- **Dati**: $E_C = 20$ V, $E_B = 10$ V, $R_C = 300\,\Omega$, $R_E = 200\,\Omega$, $R_B = 20\,\text{k}\Omega$, $\beta = 100$, $V_{BE} = 0{,}7$ V.
- **Soluzione edutecnica**: $V_{CE} = 8{,}4$ V, $I_C = 23{,}1$ mA.
- **Svolgimento passo-passo**:
  1. $V_{BB} = E_B = 10$ V (esatto, dato).
  2. $I_B = \dfrac{E_B - V_{BE}}{R_B + (\beta+1)R_E} = \dfrac{10 - 0{,}7}{20000 + 101 \cdot 200} = \dfrac{9{,}3}{40200} \approx 231\,\mu\text{A}$.
  3. $I_C = \beta \cdot I_B = 100 \cdot 231\,\mu\text{A} = 23{,}1$ mA.
  4. $V_{CE} = E_C - I_C R_C - I_E R_E \approx E_C - I_C(R_C + R_E) = 20 - 23{,}1\text{ mA} \cdot 500\,\Omega = 20 - 11{,}55 = 8{,}45$ V ≈ **8,4 V** ✓.

### Es. B2 — NPN a base fissa (senza $R_E$)

- **Dati**: $E_C = 12$ V, $R_C = 200\,\Omega$, $R_B = 50\,\text{k}\Omega$, $\beta = 100$, $V_{BE} = 0{,}7$ V.
- **Soluzione edutecnica**: $I_C = 22{,}6$ mA, $V_{CE} = 7{,}48$ V.
- **Procedura**: $I_B = (V_{BB} - V_{BE})/R_B = (12 - 0{,}7)/50000 = 226\,\mu\text{A}$ (qui $V_{BB} = E_C$ perché la maglia di base non scende in $R_E$). $I_C = 22{,}6$ mA. $V_{CE} = E_C - I_C R_C = 12 - 4{,}52 = 7{,}48$ V.

### Es. B3 — NPN con partitore di base + $R_E = 0$

- **Dati**: $R_1 = 30\,\text{k}$, $R_2 = 50\,\text{k}$, $R_C = 250\,\Omega$, $E_C = 12$ V, $\beta = 100$, $V_{BE} = 0{,}7$ V.
- **Soluzione edutecnica**: $I_C = 36{,}2$ mA, $V_{CE} = 2{,}95$ V.
- **Procedura**: non manca alcun dato — la resistenza vista dalla base **è** il partitore stesso, tramite Thévenin:
  $$V_{TH} = E_C \cdot \frac{R_2}{R_1+R_2} = 12 \cdot \frac{50}{80} = 7{,}5\ \text{V} \qquad R_{TH} = R_1 \Vert R_2 = \frac{30 \cdot 50}{80} = 18{,}75\ \text{k}\Omega$$
  Poiché $R_E = 0$, la maglia di base non contiene il termine $(\beta+1)R_E$:
  $$I_B = \frac{V_{TH} - V_{BE}}{R_{TH}} = \frac{6{,}8}{18\,750} = 362\,\mu\text{A} \qquad I_C = \beta I_B = 36{,}2\ \text{mA}$$
  $$V_{CE} = E_C - I_C R_C = 12 - 36{,}2\ \text{mA} \cdot 250\,\Omega = 12 - 9{,}06 = 2{,}94\ \text{V} \approx \mathbf{2{,}95\ V}\ ✔$$

> [!warning] Circuito volutamente pessimo — capisci perché
> Questo è un partitore **senza $R_E$**: manca del tutto l'effetto 2 di Mirandola (la retroazione negativa). $I_C$ è direttamente proporzionale a $\beta$, quindi con un $\beta$ doppio si avrebbe $I_C = 72$ mA e $V_{CE}$ finirebbe **in saturazione**. Inoltre $V_{CE} = 2{,}94$ V su $E_C = 12$ V è già molto sbilanciato verso il basso: dinamica d'uscita ridotta.
>
> Usalo come esercizio di calcolo, non come schema da imitare. Confrontalo con il criterio di progetto del libro ($V_{RC} = V_{CEQ}$, cioè $V_{CE}$ a metà) in [[BJT#Il dimensionamento completo (formule 7.8-7.11, pp. 328-329)]].

### Es. B4 — NPN con partitore + $R_E$ (potenza)

- **Dati**: $R_1 = R_2 = 100\,\text{k}$, $R_C = 300\,\Omega$, $R_E = 1\,\text{k}$, $E_C = 25$ V, $\beta = 90$, $V_{BE} = 0{,}7$ V.
- **Soluzione edutecnica**: $I_C = 7{,}47$ mA, $V_{CE} = 15{,}2$ V, $P_C = 191$ mW.
- **Procedura (metodo esatto, Thévenin sul partitore)**: $V_{TH} = E_C \cdot \frac{R_2}{R_1+R_2} = 12{,}5$ V, $R_{TH} = R_1 \Vert R_2 = 50\,\text{k}\Omega$.
  $$I_B = \frac{V_{TH} - V_{BE}}{R_{TH} + (\beta+1)R_E} = \frac{11{,}8}{50\,000 + 91 \cdot 1000} = \frac{11{,}8}{141\,\text{k}} = 83{,}7\,\mu\text{A}$$
  $$I_C = \beta I_B = 90 \cdot 83{,}7\,\mu\text{A} = 7{,}53\ \text{mA} \qquad I_E = (\beta+1)I_B = 7{,}62\ \text{mA}$$
  $$V_{CE} = E_C - I_C R_C - I_E R_E = 25 - 2{,}26 - 7{,}62 = 15{,}12\ \text{V} \approx \mathbf{15{,}2\ V}\ ✔$$

> [!check] edutecnica è corretta — l'errore era in questa scheda
> Una precedente versione di questa nota accusava edutecnica di aver «dimenticato la caduta su $R_E$», ottenendo $V_{CE} = 10{,}96$ V invece di 15,2 V. **L'accusa era infondata**: rifacendo i conti col metodo esatto si ottiene esattamente 15,12 V.
>
> Il vero errore era **mescolare due metodi diversi**: si prendeva $I_C = 7{,}47$ mA (dal metodo esatto, che tiene conto del carico del partitore) ma $I_E = 11{,}8$ mA (dal metodo approssimato $I_E = V_E/R_E$, che lo ignora). $I_C$ e $I_E$ devono venire dallo **stesso** modello: con $\beta = 90$ non possono differire di un fattore 1,6.
>
> **Perché qui l'approssimazione non regge**: il metodo rapido ($V_E = V_B - 0{,}7$, $I_E = V_E/R_E$) presuppone il partitore scarico, cioè $I_{partitore} \gg I_B$. Qui $I_{partitore} = 25/200\text{k} = 125\,\mu$A contro $I_B = 84\,\mu$A: sono **confrontabili**. Il partitore è pesantemente caricato e $V_B$ crolla ben sotto i 12,5 V nominali. È esattamente la condizione di progetto violata di cui parla Mirandola a p. 328 ($I = 10\,I_B$) — vedi [[BJT#b) Polarizzazione con partitore di base e resistore sull'emettitore]].

- **Sulla potenza dichiarata (191 mW)**: attenzione, non è la potenza dissipata *dal transistor*. Quella vale
  $$P_{BJT} = V_{CE} \cdot I_C = 15{,}12 \cdot 7{,}53\ \text{mA} \approx 114\ \text{mW}$$
  Il valore 191 mW corrisponde invece alla potenza **complessivamente erogata dall'alimentatore al ramo d'uscita**, $P = E_C \cdot I_E = 25 \cdot 7{,}62\ \text{mA} = 190{,}5$ mW — cioè i 114 mW del BJT più i 17 mW su $R_C$ e i 58 mW su $R_E$. Le due grandezze sono entrambe legittime ma **rispondono a domande diverse**: per dimensionare il dissipatore serve la prima, per dimensionare l'alimentatore la seconda.

### Es. B5 — BJT in configurazione Darlington

- **Dati**: $\beta_1 = 100$, $\beta_2 = 75$, $V_{BE} = 0{,}7$ V, $R_1 = R_2 = 50\,\text{k}$, $R_E = 1{,}2\,\text{k}$, $E_C = 20$ V.
- **Soluzione edutecnica**: $I_{C1} = 0{,}093$ mA, $I_{C2} = 7{,}11$ mA, $V_{CE1} = 10{,}66$ V, $V_{CE2} = 11{,}36$ V.
- **Procedura**: $\beta_{\text{eq}} \approx \beta_1 \cdot \beta_2 = 100 \cdot 75 = 7500$. È il vantaggio del Darlington: guadagno di corrente enorme e **resistenza d'ingresso enorme**.
  $$V_{TH} = 20 \cdot \tfrac{50}{100} = 10\ \text{V} \qquad R_{TH} = 25\ \text{k}\Omega$$
  Attenzione a **due** cadute base-emettitore in serie ($T_1$ e $T_2$), non una:
  $$I_{B1} = \frac{V_{TH} - 2V_{BE}}{R_{TH} + (\beta_1+1)(\beta_2+1)R_E} = \frac{10 - 1{,}4}{25\,\text{k} + 101 \cdot 76 \cdot 1200} = \frac{8{,}6}{9{,}23\ \text{M}\Omega} = 0{,}93\,\mu\text{A}$$
  $$I_{C1} = \beta_1 I_{B1} = \mathbf{0{,}093\ mA}\ ✔ \qquad I_{B2} = I_{E1} = 101 \cdot 0{,}93\,\mu\text{A} = 94\,\mu\text{A}$$
  $$I_{C2} = \beta_2 I_{B2} = 75 \cdot 94\,\mu\text{A} = \mathbf{7{,}05\ mA} \;(\text{ed.}\ 7{,}11)\ ✔ \qquad I_{E2} = 7{,}14\ \text{mA}$$
  $$V_E = I_{E2}R_E = 8{,}57\ \text{V} \;\Rightarrow\; V_{CE2} = 20 - 8{,}57 = \mathbf{11{,}43\ V}\ (\text{ed.}\ 11{,}36)\ ✔$$
  $$V_{CE1} = E_C - (V_{BE2} + V_E) = 20 - (0{,}7 + 8{,}57) = \mathbf{10{,}73\ V}\ (\text{ed.}\ 10{,}66)\ ✔$$
  Tutti e quattro i valori di edutecnica sono confermati entro l'arrotondamento.

> [!tip] Il dato che conta del Darlington
> $R_{in} = (\beta_1+1)(\beta_2+1)R_E \approx 9{,}2\ \text{M}\Omega$: è **370 volte** la $R_{TH} = 25$ k$\Omega$ del partitore. Per questo qui il partitore si può considerare scarico e $I_{B1}$ è dell'ordine del **microampere**. È il motivo per cui il Darlington si usa come stadio d'ingresso ad altissima impedenza e come driver di potenza.

### Es. B6-B10 — Switching BJT (varianti ON/OFF)

Per i restanti 5 esercizi edutecnica (interruttori BJT):
- Determinare se il transistor è in saturazione o interdizione
- Calcolare $I_B$ e verificare se $I_B > I_{B,\text{sat}} = I_{C,\text{sat}}/\beta$
- In saturazione: $V_{CE} \approx 0{,}2$ V; in interdizione: $I_C = 0$

## Pattern di errore frequenti (Carli scritta)

1. **Trascurare $R_E$**: in configurazione con $R_E$, la $V_{CE}$ è $E_C - I_C R_C - I_E R_E$. Errore: $V_{CE} = E_C - I_C R_C$ → sovrastima $V_{CE}$.
2. **Usare $\beta$ invece di $\beta+1$**: nella maglia di base con $R_E$, $I_B$ passa anche in $R_E$ (amplificata di $\beta+1$). Errore: usare solo $R_B$ → $I_B$ sovrastimato.
3. **Confondere NPN con PNP**: PNP ha tensioni di segno opposto. Errore: $V_{CE}$ calcolato positivo per PNP → $-7$, non $+7$.
