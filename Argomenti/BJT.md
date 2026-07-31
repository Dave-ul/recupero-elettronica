---
tags: [recupero, elettronica, transistor, bjt]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-19) — Mirandola Vol.2, Cap. 7 «Gli amplificatori a transistor», pp. 312-347 (pagg.-PDF 95-112). ATTENZIONE: il capitolo è il 7, NON il 6 (il Cap. 6 è sugli amplificatori operazionali). Conversione: pagina stampata = (pagina-PDF − 95)·2 + 312 — verificata su PDF 95 → pp. 312-313 e PDF 110 → pp. 342-343. Mappa sezioni: §1 Il transistor bipolare (BJT) p. 312 · §1.1 Il funzionamento del BJT NPN p. 313 (FIG. 1 simboli, FIG. 2 polarizzazione) · analogia col triodo FIG. 3 pp. 314-315 · modello di Ebers-Moll FIG. 4 e saturazione pp. 316-317 · curve caratteristiche, h_FE e iperbole di massima dissipazione FIG. 7 pp. 318-319 · ESEMPIO 2, dispersione di h_fe FIG. 8, resistenza termica pp. 320-321 · polarizzazione FIG. 9-10, formule 7.5 (maglia d'ingresso) e 7.6 (maglia d'uscita) pp. 322-323 · ESEMPIO 3 e rette di carico pp. 324-325 · FIG. 12 punto di lavoro, FIG. 13 polarizzazione con resistenza di base, ESEMPIO 4, FIG. 14 partitore + R_E pp. 326-327 · procedura di dimensionamento formule 7.8-7.11 ed ESEMPIO 5 pp. 328-329 · BJT in commutazione FIG. 16 ed ESEMPIO 6 pp. 330-331 · amplificatore a emettitore comune FIG. 17-19 pp. 332-333 · banda passante FIG. 21-23 pp. 336-337 · parametri ibridi h e quadripolo FIG. 26-27 pp. 340-341 · formule 7.13-7.14 pp. 342-343 · collettore comune (inseguitore) FIG. 30 pp. 346-347."
prove: [scritta, orale]
---

# transistor BJT — struttura, regioni, polarizzazione

> [!info] Dove serve
> **Scritta Carli** (LETTERA): «transistor BJT». **Orale Carli** (LETTERA): NON cita BJT/JFET/MOSFET — solo «diodo, circuiti AC, filtri 1° ordine». I confronti BJT/JFET/MOSFET all'orale sono **estensione naturale** (si parla del BJT parlando del MOSFET) ma non testualmente obbligatori. È il blocco fondamentale di amplificatori, interruttori, porte logiche (transistor-transistor logic, TTL).

Prerequisiti: [[Impedenza dei bipoli R, L, C]] (per i circuiti di polarizzazione), [[Diodi]] (perché la giunzione B-E è un diodo).

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §8**.

## 1. La struttura: tre regioni, due giunzioni

Un BJT (Bipolar Junction Transistor) è formato da **tre regioni di semiconduttore** alternate:

- **NPN**: strati n-p-n → gli elettroni sono i portatori maggioritari che attraversano il transistor dall'emettitore al collettore.
- **PNP**: strati p-n-p → analogamente, ma con lacune; la convenzione delle correnti è invertita.

> Struttura e simboli elettrici dei due tipi di BJT — **Mirandola Cap. 7 §1, p. 313, FIGURA 1** (A: NPN; B: PNP):
>
> ![[libro-cap7-p313-fig1-simboli-bjt.png]]
>
> Il libro sottolinea due dettagli costruttivi che spiegano il funzionamento: le **due zone esterne sono fortemente drogate**, mentre la **base ha spessore inferiore alle altre ed è debolmente drogata**. Da qui si deduce che il BJT è schematizzabile in prima approssimazione con **due diodi a giunzione PN «back-to-back»** — ma il libro avverte esplicitamente che *questo modello non riesce a spiegare il meccanismo dell'amplificazione*, che dipende proprio dal ridotto spessore della base, non riproducibile con due diodi distinti.
>
> Nota di scope: la struttura PNP «è meno utilizzata, specie nella realizzazione di circuiti integrati; per questo motivo nel seguito, salvo casi particolari, si farà sempre riferimento alla struttura NPN» (p. 313).

I tre terminali sono:

| Terminale | Sigla | Funzione |
|---|---|---|
| **Base** (B) | **B** | Comando: una piccola $I_B$ controlla la grande $I_C$ |
| **Collettore** (C) | **C** | Uscita: la corrente "raccolta" dall'emettitore |
| **Emettitore** (E) | **E** | Ingresso: "emette" i portatori |

> [!tip] Il BJT è un amplificatore di corrente, non di tensione
> Il BJT, di per sé, è un amplificatore **di corrente**: una piccola $I_B$ controlla una grande $I_C$. Per avere un amplificatore **di tensione** devi costruirci intorno una rete che trasformi la variazione di $I_C$ in una variazione di tensione (es. una resistenza di collettore). Vedi [[Amplificatori a BJT]].

---

## 2. Le tre regioni di funzionamento

### Zona attiva (ACTIVE)

- Giunzione **base-emettitore** (BE): **diretta** ($V_{BE} \approx 0{,}7\ \text{V}$).
- Giunzione **base-collettore** (BC): **inversa**.

In zona attiva vale:

$$I_C = \beta \cdot I_B \qquad I_E = I_B + I_C = (\beta + 1) I_B$$

dove $\beta = h_{FE}$ è il **guadagno di corrente** (tipicamente 100–300 per transistor di segnale).

> [!check] Segno di V_BE in zona attiva
> NPN: $V_{BE} \approx +0{,}7\ \text{V}$
> PNP: $V_{BE} \approx -0{,}7\ \text{V}$
>
> Ricordalo sempre: la giunzione BE è un diodo, e quindi ha la stessa tensione di soglia.

### Saturazione (SAT)

- Entrambe le giunzioni **dirette** ($V_{BE} \approx 0{,}7$, $V_{BC} \approx 0{,}7$).
- La tensione $V_{CE}$ scende al minimo: $V_{CE,\text{sat}} \approx 0{,}2\ \text{V}$ (NPN).
- Il transistor si comporta come un **interruttore chiuso** (piccola $V_{CE}$, grande $I_C$).

### Interdizione (CUTOFF)

- Entrambe le giunzioni **inverse**.
- Il transistor è un **interruttore aperto** ($I_C \approx 0$, $V_{CE} = V_{CC}$).

> [!tip] Tabella mentale
>
> | Zona | B-E | B-C | $V_{CE}$ | $I_C$ |
> |---|---|---|---|---|
> | **Attiva** | ON | OFF | dipende da $I_C \cdot R_C$ | $\beta I_B$ |
> | **Saturazione** | ON | ON | ~0,2 V | limitato da $R_C$ |
> | **Interdizione** | OFF | OFF | $V_{CC}$ | ~0 |
>
> Nella figura: il BJT è un interruttore in saturazione/interdizione; è un amplificatore in zona attiva.

---

## 3. Le curve caratteristiche

> Punto di lavoro sulle caratteristiche — **Mirandola Cap. 7, p. 326, FIGURA 12**. **A)** punto di lavoro sulle caratteristiche d'**ingresso** ($I_B$ vs $V_{BE}$); **B)** punto di lavoro e **retta di carico** sulle caratteristiche d'**uscita** ($I_C$ vs $V_{CE}$, parametrizzate in $I_B$):
>
> ![[libro-cap7-p326-fig12-punto-lavoro-retta-carico.png]]

Dalle curve puoi leggere:

- **Curva $I_C$–$V_{BE}$**: a $V_{BE} \approx 0{,}7$ V la corrente $I_C$ inizia a salire esponenzialmente — è la stessa curva di un diodo, semplicemente "moltiplicata" per $\beta$.
- **Curve $I_C$–$V_{CE}$**: per ogni valore di $I_B$ hai una curva; in **zona attiva** le curve sono quasi orizzontali (poco dipendenti da $V_{CE}$).
- **Retta di carico**: la linea che il punto di lavoro può percorrere. È il grafico dell'equazione della **maglia d'uscita** (Mirandola, formula **7.6**, p. 323):
  $$V_{CE} = V_{CC} - R_C I_C$$
  Si traccia per intercette, esattamente come la retta di carico del diodo:
  - $I_C = 0 \;\Rightarrow\; V_{CE} = V_{CC}$ (intercetta sull'asse delle tensioni);
  - $V_{CE} = 0 \;\Rightarrow\; I_C = V_{CC}/R_C$ (intercetta sull'asse delle correnti).

  Il **punto di lavoro Q** è l'intersezione della retta di carico con la curva corrispondente alla $I_B$ effettivamente imposta dal circuito di polarizzazione.

> [!warning] L'iperbole di massima dissipazione
> Nella FIGURA 12B compare una curva tratteggiata che **non è una caratteristica del transistor**: è l'**iperbole di massima dissipazione**, il luogo dei punti in cui la potenza dissipata sul BJT raggiunge il valore massimo ammesso (Mirandola, FIGURA 7, p. 319). La potenza dissipata vale (formula **7.2**, p. 318):
> $$P = V_{CE} \cdot I_C$$
> Poiché $P$ è costante lungo la curva, $I_C = P_{\max}/V_{CE}$ è appunto un'iperbole. **Il punto di lavoro deve stare sotto di essa**: è un vincolo di progetto che si aggiunge alla retta di carico, non una conseguenza di essa.

---

## 4. Polarizzazione: il calcolo del punto di lavoro

### Schema base

Lo schema con **due generatori** $V_{BB}$ e $V_{CC}$ è quello di **Mirandola FIGURA 10, p. 323**. Le due equazioni fondamentali sono le maglie d'ingresso e d'uscita (formule **7.5** e **7.6**):

Maglia di base / d'ingresso (**7.5**):
$$V_{BB} = R_B I_B + V_{BE} \quad \Rightarrow \quad I_B = \frac{V_{BB} - V_{BE}}{R_B}$$

Maglia di collettore / d'uscita (**7.6**):
$$V_{CE} = V_{CC} - R_C I_C \qquad \text{con} \quad I_C = h_{FE} I_B$$

> [!warning] Questo schema è solo didattico — parola del libro
> Mirandola è esplicito (p. 326): «il circuito di polarizzazione in FIGURA 10 ha solo **valenza didattica**». Nella pratica **non si usano due alimentatori separati**: tutte le reti reali derivano la polarizzazione di base dal solo $V_{CC}$. Il libro approfondisce **due** soluzioni a singola alimentazione:
> - **a) con resistenza di base** → ottiene *solamente* la polarizzazione;
> - **b) con partitore sulla base e resistenza sull'emettitore** → ottiene la polarizzazione **e la stabilizzazione** del punto di lavoro.

### a) Polarizzazione con resistenza di base

> Circuito di polarizzazione del BJT a emettitore comune con resistenza di base — **Mirandola Cap. 7, p. 326, FIGURA 13**:
>
> ![[libro-cap7-p326-fig13-polarizzazione-resistenza-base.png]]

Un solo generatore $V_{CC}$ e due resistori $R_B$, $R_C$. Il **procedimento** di dimensionamento (p. 326), noti $V_{CC}$ e il punto di lavoro voluto $I_{CQ}$, $V_{CEQ}$:

1. si legge $h_{FE}$ dai data sheet e si ricava $I_{BQ} = I_{CQ}/h_{FE}$;
2. si suppone $V_{BEQ} = 0{,}7$ V;
3. dalla maglia d'ingresso (**7.5**): $\;R_B = \dfrac{V_{CC} - V_{BEQ}}{I_{BQ}}$;
4. dalla maglia d'uscita (**7.6**): $\;R_C = \dfrac{V_{CC} - V_{CEQ}}{I_{CQ}}$.

> [!example] ESEMPIO 4 del libro (p. 327) — 2N2222
> Dati: $V_{CC} = 12$ V, punto di lavoro voluto $V_{CEQ} = 6$ V, $I_{CQ} = 10$ mA. Dai data sheet, in corrispondenza di questi valori, $h_{FE} \approx 100$.
>
> $$I_{BQ} = \frac{I_{CQ}}{h_{FE}} = \frac{10 \cdot 10^{-3}}{100} = 100\ \mu\text{A}$$
> $$R_B = \frac{V_{CC} - V_{BEQ}}{I_{BQ}} = \frac{12 - 0{,}7}{100 \cdot 10^{-6}} = 113\ \text{k}\Omega$$
> $$R_C = \frac{V_{CC} - V_{CEQ}}{I_{CQ}} = \frac{12 - 6}{10 \cdot 10^{-3}} = 600\ \Omega$$

### Perché la polarizzazione con sola $R_B$ non basta

Il libro (p. 326) individua la causa precisa, ed è importante non confonderla:

> «Il punto di lavoro così determinato difficilmente sarà confermato nella pratica, a causa della **tolleranza con cui è noto il valore di $h_{FE}$** che, inoltre, **varia in funzione della corrente $I_C$ e della temperatura $T$**.»

Il difetto non è quindi "la temperatura" in astratto: è che **tutto il punto di lavoro è appeso a $h_{FE}$**, il parametro peggio controllato del transistor. Nello schema con sola $R_B$, la $R_B$ fissa $I_B$; ma $I_C = h_{FE} I_B$, quindi ogni dispersione o deriva di $h_{FE}$ si scarica **direttamente** su $I_{CQ}$ e, tramite la maglia d'uscita, su $V_{CEQ}$.

Le conseguenze pratiche che il libro elenca sono due, e sono entrambe da amplificatore, non da guasto:
- un **guadagno di tensione diverso da quello previsto**;
- una **riduzione della dinamica d'uscita**, cioè del campo di valori ottenibili senza distorsione della forma d'onda.

### b) Polarizzazione con partitore di base e resistore sull'emettitore

> Circuito di polarizzazione **e stabilizzazione** del BJT — **Mirandola Cap. 7, p. 327, FIGURA 14**:
>
> ![[libro-cap7-p327-fig14-partitore-stabilizzazione.png]]

È la configurazione standard. Il libro (pp. 327-328) spiega che il suo funzionamento «è basato su **due effetti**» — e sono due, distinti, non uno solo:

**Effetto 1 — il partitore fissa $V_B$.** Le resistenze $R_1$ e $R_2$ mantengono il potenziale di base a un valore **costante, indipendente dalle variazioni indesiderate di $I_B$**. Perché ciò valga davvero serve una condizione di progetto: la corrente nel partitore deve essere *assai maggiore* di quella che entra in base,
$$I_{R1} \approx I_{R2} \gg I_B$$
in pratica si sceglie $I = 10\,I_B$. Solo così il partitore si può considerare **scarico** e $V_B$ è davvero un riferimento fisso.

**Effetto 2 — $R_E$ introduce una retroazione negativa.** Questo è il vero meccanismo stabilizzante, ed è una catena causale che va seguita fino in fondo:

$$I_C \uparrow \;\Rightarrow\; I_E \uparrow \;\Rightarrow\; V_E = R_E I_E \uparrow \;\underset{V_B \text{ costante}}{\Longrightarrow}\; V_{BE} = V_B - V_E \downarrow \;\Rightarrow\; I_B \downarrow \;\Rightarrow\; I_C \downarrow$$

L'aumento iniziale di $I_C$ **si autocorregge**, riportando la corrente al valore di progetto. Il libro sottolinea che questo vale «**indipendentemente dalla causa** che lo determina»: deriva termica, dispersione di $h_{FE}$, sostituzione del transistor. È una **retroazione negativa tra la maglia d'uscita e quella d'ingresso**.

> [!danger] Il punto che si sbaglia più spesso
> L'effetto 2 **funziona solo se vale l'effetto 1**. Se il partitore è troppo "debole" (correnti confrontabili con $I_B$), allora $V_B$ scende quando $I_B$ sale, la catena sopra si spezza e $R_E$ non stabilizza più nulla. I due effetti non sono alternativi: sono in serie logica.
>
> Corollario: $R_E$ da sola, senza un $V_B$ fisso, non stabilizza; e un partitore rigido senza $R_E$ nemmeno. Servono entrambi.

### Il dimensionamento completo (formule 7.8-7.11, pp. 328-329)

Le incognite sono **quattro** resistenze ($R_1$, $R_2$, $R_C$, $R_E$), quindi servono **quattro equazioni**. Il libro le ricava da quattro scelte di progetto:

| # | Grandezza | Criterio di progetto | Formula |
|---|---|---|---|
| 1 | $R_E$ | La caduta su $R_E$ deve essere **molto minore** di $V_{CC}$, di norma 1/10 | $V_{RE} = V_{CC}/10$, poi $R_E = V_{RE}/I_{CQ}$ **(7.8)** |
| 2 | $R_C$ | La caduta su $R_C$ deve **uguagliare** $V_{CEQ}$, per massimizzare l'escursione d'uscita | $V_{RC} = V_{CEQ} = \dfrac{V_{CC} - V_{RE}}{2}$, poi $R_C = V_{RC}/I_{CQ}$ **(7.9)** |
| 3 | $R_2$ | Il partitore deve fissare $V_{B}$, con $I = 10\,I_B$ | $V_{B} = V_{BE} + V_{RE} = 0{,}7 + R_E I_E$, poi $R_2 = V_{B}/I$ **(7.10)** |
| 4 | $R_1$ | Ai capi di $R_1$ cade il resto | $R_1 = \dfrac{V_{CC} - V_{B}}{I}$ **(7.11)** |

> [!example]- La pagina del libro: PROCEDIMENTO + ESEMPIO 5 — **Mirandola Cap. 7 §1, pp. 328-329**
> ![[libro-cap7-pp328-329-bjt-progetto-polarizzazione.png]]
>
> A sinistra il riquadro PROCEDIMENTO con le quattro formule nell'ordine in cui vanno applicate; a destra l'**ESEMPIO 5** svolto per intero su un **2N2222** con $V_{CC} = 9$ V e $I_{C0} = 4$ mA:
>
> | Passo | Conto del libro | Risultato |
> |---|---|---|
> | $h_{FE\min}$ dal data sheet | — | 75 |
> | $R_E$ **(7.8)** | $\dfrac{9}{10 \cdot 4 \cdot 10^{-3}}$ | $\approx 220\ \Omega$ |
> | $R_C$ **(7.9)** | $\dfrac{9 \cdot 9}{20 \cdot 4 \cdot 10^{-3}}$ | $\approx 1$ k$\Omega$ |
> | $I_{B\max}$ | $\dfrac{I_{C0}}{h_{FE\min}} = \dfrac{4\text{ mA}}{75}$ | 53 µA |
> | $I$ nel partitore | $10\,I_{B\max}$ | 0,53 mA |
> | $V_{B}$ | $V_{BE} + R_E I_{C0} = 0{,}7 + 0{,}9$ | 1,6 V |
> | $R_2$ **(7.10)** | $\dfrac{1{,}6}{0{,}53 \cdot 10^{-3}}$ | 3,0 k$\Omega$ |
> | $R_1$ **(7.11)** | $\dfrac{9 - 1{,}6}{0{,}53 \cdot 10^{-3}}$ | 14 k$\Omega$ |
>
> Vale la pena rifarlo a mano una volta: è **esattamente** il formato in cui Carli chiede il dimensionamento allo scritto.

> [!tip] Perché $V_{RC} = V_{CEQ}$ e non un valore qualsiasi
> La ragione ovvia è la **simmetria dell'escursione**: mettendo il punto di lavoro a metà tra saturazione e interdizione, il segnale può oscillare al massimo in entrambi i versi prima di distorcere.
>
> Ma il libro ne aggiunge una seconda, meno intuitiva e più importante: «si può dimostrare che ciò **evita fenomeni di fuga termica**, cioè la crescita a catena di $I_{CQ}$ a causa dell'aumento di temperatura» (p. 329). Il criterio $V_{RC} = V_{CEQ}$ è quindi al tempo stesso un criterio di **dinamica** e un criterio di **sicurezza termica**.

> [!note] Nota di scope — auto-polarizzazione (collector-feedback)
> Una precedente versione di questo file citava anche lo schema con $R_B$ collegata **dal collettore alla base**. Mirandola **non lo tratta**: a p. 326 dichiara che «tra le numerose soluzioni circuitali che rendono possibile la polarizzazione del BJT se ne approfondiscono **due**», cioè la sola $R_B$ e il partitore con $R_E$. Lo schema collector-feedback esiste ed è corretto in sé, ma **non è materia di questo libro** e non va citato come se lo fosse.

---

## 5. Cross-link a MOSFET e JFET — file dedicati

I transistor **MOSFET** e **JFET** hanno **equazioni** e **regioni operative** *diverse* dal BJT (sono controllati **in tensione**, non in corrente). Per questo hanno ciascuno un file dedicato:

- **MOSFET enhancement n-channel** → [[MOSFET]] · equazione $I_D = K(V_{GS}-V_{th})^2$, polarizzazione a partitore, esempio numerico svolto (edutecnica.it/elettronica/mosfetx/).
- **JFET canale n** → [[JFET]] · equazione $I_D = I_{DSS}\bigl(1 - V_{GS}/V_P\bigr)^2$, autopolarizzazione con $R_S$, cutoff per $V_{GS} \le V_P$.

In questo file BJT resta solo il **confronto trasversale** (§ 6), utile per la prova orale Carli, dove i confronti sono frequenti. Per le specifiche domande orali su MOSFET e JFET vedi i file dedicati.

---

## 6. Confronto BJT vs MOSFET vs JFET

> [!danger] Quando si usa cosa
>
> | Componente | Pilotaggio | Quando sceglierlo |
> |---|---|---|
> | **BJT** | in corrente ($I_B$) | Amplificatori a piccolo segnale a basso rumore |
> | **MOSFET** | in tensione ($V_{GS}$) | Elettronica digitale (CMOS), switching di potenza, alimentatori switching |
> | **JFET** | in tensione (con limiti) | Amplificatori a basso rumore all'ingresso, interruttori analogici |

---

## Quesiti tipo — Guida rapida

> [!question] Perché la base è sottile?
> Per minimizzare la ricombinazione dei portatori nella zona di base: solo una piccola $I_B$ deve fluire, e la maggior parte degli elettroni dall'emettitore arriva al collettore. È il motivo fisico del guadagno $\beta$ alto.

> [!question] Cosa succede se $I_B$ diventa 0?
> In zona attiva, $I_C = \beta I_B \to 0$. Il transistor passa in **interdizione**: $I_C \approx 0$, $V_{CE} \approx V_{CC}$. È il modo di "spegnere" il BJT.

> [!question] Cosa succede in saturazione?
> Il transistor si comporta come un interruttore chiuso: $V_{CE} \approx 0{,}2\ \text{V}$ (NPN). $I_C$ non è più $\beta I_B$ ma è limitata dal circuito esterno (es. $R_C$): $I_C = (V_{CC} - V_{CE,sat})/R_C$.

> [!tip] Quesiti specifici sui transistor FET
> Per le domande su pilotaggio in tensione, equazione parabolica, regioni di cutoff / triodo / saturazione dei transistor a effetto di campo (MOSFET enhancement n e JFET n) vedi i file dedicati:
> - [[MOSFET#Quesiti tipo — Guida rapida]]
> - [[JFET#Quesiti tipo — Guida rapida]]

---

## 7. Da qui in poi

> [!note] Nota di scope
> In questo file **BJT** trovi struttura, regioni di funzionamento e polarizzazione del transistor a giunzione bipolare (il blocco fondamentale per lo **scritto Carli** sul pilotaggio in corrente). Per i transistor **MOSFET** e **JFET** — controllati in tensione, con equazioni paraboliche diverse — vedi i file dedicati [[MOSFET]] e [[JFET]]; il confronto trasversale è nella § 6 di questo file.

- Prerequisiti: [[Impedenza dei bipoli R, L, C]], [[Diodi]]
- Amplificatori: [[Amplificatori a BJT]]
- Esercizi: [[Esercizi - BJT]], [[Esercizi - MOSFET]], [[Esercizi - JFET]]
