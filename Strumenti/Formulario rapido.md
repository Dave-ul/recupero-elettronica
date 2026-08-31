---
tags: [recupero, elettronica, formulario, cheat-sheet, criteri-progetto, comparazione, compito, rapido]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), studente Davide Rocca, classe 4BEM"
criteri_progetto: "Parte 0 §0.2 — ricette R1-R9 estratte dalle verifiche vere di Carli (Prove/05, Prove/06) e dalle procedure di dimensionamento del Mirandola (BJT 7.8-7.11 p. 328-329; JFET §4-bis; MOSFET §3-bis; Zener p. 228; alimentatori Cap. 8)"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) per derivazione — file trasversale: non cita direttamente il libro, ma raccoglie le formule dei file di argomento, ciascuno verificato pagina per pagina sul Mirandola nei Lotti 1-13 della bonifica. Per il riferimento di libro di ogni formula si va alla nota dell'argomento corrispondente. Vedi «00 - Fonti e note» e «00 - Audit e correzioni»."
prove: [scritta]
nota_unione: "2026-08-27 — «Cheat Sheet A4 visuale» fuso qui come Parte A (§A1-§A7); §1-§13 del Formulario invariate. 2026-08-31 — aggiunta la Parte 0 «I 5 minuti prima di entrare»: criteri di progetto (ricette R1-R9), numeri da scegliere, trappole e regole di chiusura. Parte A e Parte B non toccate nei contenuti, solo rimandi."
---

# 📋 Formulario + Criteri di progetto — compito Carli (1 set., 8:00-13:00)

> [!danger] USO — questo file NON entra in aula
> Sul foglio firmato della verifica il prof. scrive: **niente libro, niente quaderno, niente telefono; chi li usa viene ritirato con 2/10**. Quindi questo file è materiale da **memorizzare**, non da consultare.
> - **[Parte 0](#parte-0--i-5-minuti-prima-di-entrare)** = i **5 minuti prima di entrare**. I criteri di progetto e le formule chiave, in forma di ricette. Se leggi una cosa sola, leggi questa.
> - **[Parte A](#parte-a--tabelle-comparative-lookup-5-secondi)** = tabelle comparative (§A1-§A7) — per lo studio.
> - **[Parte B](#parte-b--formule-per-macroarea)** = formulario per macroarea (§1-§13) — per lo studio.

---

# Parte 0 — I 5 minuti prima di entrare

> [!important] Perché i **criteri di progetto** e non le formule
> Le verifiche vere di Carli ([[05 - Verifiche FUSI (Carli)]], [[06 - Soluzioni complete verifiche FUSI]]) sono in maggioranza esercizi di **progetto**, non di analisi: 5 su 8 nella verifica JFET/MOSFET, 2 su 3 nella parte MOSFET. Nel progetto le formule non bastano — servono le **scelte** che il testo non dà e che devi imporre tu ($V_E = V_{CC}/10$, $R_G$ si sceglie, $I = 10I_B$, $V_{DS}$ si fissa). Sono quelle qui sotto.
>
> **Scope della LETTERA per lo scritto**: AC · filtri passivi del 1° ordine · BJT · JFET a canale N · MOSFET a canale N ad arricchimento → ricette **R1-R7**.
> Diodi, Zener e alimentatori sono **orale (Carli) e pratica (Protti)** → ricette **R8-R9**.

## 0.0 Se hai davvero solo 5 minuti, leggi **solo questo**

```
LE SCELTE DI PROGETTO (quelle che il testo non ti dà e che devi imporre tu)
  R_G          si SCEGLIE, 1÷10 MΩ  — non si calcola mai (I_G = 0)
  V_E          = V_CC/10                                        → R_E = V_E/I_C0
  V_RC = V_CE  = 9·V_CC/20                                      → R_C = V_RC/I_C0
  I partitore  = 10·I_B , con h_FE,MIN                          → R_2=V_B0/I, R_1=(V_CC−V_B0)/I
  V_DS         si SCEGLIE entro V_DS ≥ V_GS − V_t  (tipico V_DD/2)
  overdrive    I_B = (2÷5)·I_B,min   + DIODO DI RICIRCOLO se il carico è induttivo
  Zener        dimensiona su I_ZT ≈ 5 mA, e verifica i DUE casi peggiori OPPOSTI
               (R: V_in,min + carico max) · (potenza: V_in,max + carico staccato)
  alimentatore l'ordine è DROPOUT → trafo → C → potenze. Mai partire dal trafo.

LE TRE COSE CHE FANNO PERDERE PIÙ PUNTI
  1. mescolare maglia d'ingresso e maglia d'uscita in un'unica equazione
  2. dimenticare V_S / V_E : V_DD = V_RD + V_DS + V_S  ·  V_G = V_GS + V_S   (TRE termini)
  3. non chiudere con la verifica dell'ipotesi (saturo? zona attiva? V_DS > V_GS−V_t?)

E COMUNQUE: mai un foglio in bianco. La sola relazione di partenza vale punti.
```

> Il resto della Parte 0 (§0.1-§0.4) è la versione da 15 minuti: le stesse cose con i passaggi completi e il perché.

## 0.1 Le sette trappole che costano il 70% dei punti

| # | Trappola | Come non caderci |
|---|---|---|
| 1 | **Maglie d'ingresso e d'uscita mescolate** ($R_B$ con $R_C$) | Prima di scrivere l'equazione chiediti: *questa resistenza è percorsa da $I_B$, $I_C$ o $I_E$?* Le due maglie condividono **solo** il ramo di emettitore/source. |
| 2 | **$I_G \approx 0$ dimenticato** → $R_G$ calcolata da una legge | Nel JFET/MOSFET il gate non assorbe corrente. **$R_G$ si sceglie (1÷10 MΩ), non si calcola.** |
| 3 | **$V_S$ / $V_E$ dimenticata** nella maglia d'uscita o nel partitore | Se c'è $R_S$/$R_E$: $V_{DD} = V_{RD} + V_{DS} + V_S$ e $V_G = V_{GS} + V_S$. **Tre** termini, non due. |
| 4 | **Formule dimensionalmente impossibili** ($\sqrt{I_D/R_D}$, $\arctan(1/\|Z\|)$) | Controlla le unità del risultato: se non sono V/A/Ω come devono, la formula è sbagliata **a prescindere dai numeri**. |
| 5 | **Valori sostituiti male** (10 al posto di 12, $f$ errata) | Riscrivi i dati in colonna prima di iniziare e spuntali man mano che li usi. |
| 6 | **Ipotesi non verificata alla fine** (saturo / zona attiva) | Ogni esercizio con un'ipotesi si **chiude** con la verifica. Se non regge, **dillo per iscritto** e rifai con l'altra zona. |
| 7 | **Esercizio lasciato in bianco** | Sui tre fascicoli 6 esercizi su 21 sono vuoti = **7,50 punti su 30**. Carli dà punti a «relazioni usate corrette» anche coi conti sbagliati: **scrivi sempre almeno la relazione di partenza**. |

## 0.2 Le ricette di progetto

> Formato fisso: **DATI → passi → VERIFICA**. La verifica finale non è facoltativa: è l'unica riga che il prof. cerca per ultima.

### R1 · AC — impedenza, modulo e argomento, funzione di trasferimento

```
ω = 2πf        X_L = ωL        X_C = 1/(ωC)
Z̄_L = +jωL     Z̄_C = 1/(jωC) = −j/(ωC)      ← 1/j vale GIÀ −j: niente meno davanti
serie  Z̄ = Z̄₁ + Z̄₂        parallelo  Z̄ = Z̄₁Z̄₂/(Z̄₁+Z̄₂)
|Z| = √(Re² + Im²)        φ = arctan(Im/Re)   ← MAI arctan(1/|Z|)
f.d.t.  Ḡ(s) = Z̄_uscita / (Z̄_serie + Z̄_uscita)     ← è un PARTITORE, adimensionale
                                                      mai V_i · Z̄_eq
```
**VERIFICA** — segno di φ coerente col bipolo: `+` = ohmico-induttivo (I in ritardo), `−` = ohmico-capacitivo (I in anticipo). Correggi $\arctan$ per il quadrante (→ §2).

### R2 · Filtri del primo ordine — taglio, poli, zeri

```
RC:  f_t = 1/(2πRC)        RL:  f_t = R/(2πL)      ← NON L/R;  τ_RL = L/R
poli = radici del DENOMINATORE      zeri = radici del NUMERATORE
riconoscere la topologia:  C a massa = PB · C in serie = PA
                           L in serie = PB · L a massa = PA
```
**VERIFICA** — controllo dimensionale su $\tau$: $[RC] = \Omega\!\cdot\!$F $=$ s, $[L/R] = $ H/Ω $=$ s. Un polo positivo = errore di segno.

### R3 · BJT — progetto polarizzazione a partitore + $R_E$ *(la procedura che Carli chiede)*

```
DATI  V_CC, I_C0, h_FE,min (dal data sheet: il MINIMO, non il tipico)

1. V_E  = V_CC/10                 →  R_E = V_E / I_C0                (7.8)
2. V_RC = V_CE = 9·V_CC/20        →  R_C = V_RC / I_C0               (7.9)
      (cioè: metà di quel che resta dopo V_E)
3. I_B  = I_C0 / h_FE,min    ·    I = 10·I_B      ← partitore "scarico"
4. V_B0 = V_BE + V_E = 0,7 + R_E·I_C0
5. R_2  = V_B0 / I           ·    R_1 = (V_CC − V_B0) / I      (7.10-7.11)
```
**VERIFICA** — $V_{CE} > V_{CE,sat} = 0{,}2$ V; la corrente di partitore è davvero $10 I_B$.
**PERCHÉ** — $V_{RC} = V_{CE}$ massimizza l'escursione simmetrica **e** evita la fuga termica (Mirandola p. 329). $I = 10I_B$ è ciò che rende $V_B$ un riferimento fisso: senza, $R_E$ non stabilizza più nulla.

### R4 · BJT — progetto con sola $R_B$ / $R_C$ dal punto di lavoro

```
DATI  V_CC, punto di lavoro voluto (I_C0, V_CE0), h_FE

1. I_B0 = I_C0 / h_FE
2. V_BE = 0,7 V   (Carli su una verifica scrive 0,8 V: usa il valore del TESTO)
3. R_B  = (V_CC − V_BE) / I_B0                                        (7.5)
4. R_C  = (V_CC − V_CE0) / I_C0                                       (7.6)
```
**VERIFICA** — zona attiva: $V_{CE0} > 0{,}2$ V.
**PERCHÉ** — schema instabile: tutto il punto di lavoro è appeso a $h_{FE}$, che ha tolleranza larga e deriva con $I_C$ e $T$. Se il testo chiede *stabilità*, la risposta è R3, non R4.

### R5 · BJT — verifica di saturazione e commutazione

```
VERIFICA SATURAZIONE (3 passi, le maglie NON si mescolano)
1. maglia d'ingresso:  I_B = (V_CC − V_BE) / R_B          [+ R_E·I_E se c'è]
2. maglia d'uscita con V_CE = V_CEsat = 0,2 V:
      I_C,sat = (V_CC − 0,2) / R_C                        [+ R_E se c'è]
3. saturo  ⟺  I_B > I_C,sat / h_FE                        ← la conclusione, scritta

COMMUTAZIONE / pilotaggio carico
   I_B,min = I_C / h_FE,min        poi  I_B = k · I_B,min   con k = 2÷5 (overdrive)
   CARICO INDUTTIVO (relè, bobina) → DIODO DI RICIRCOLO in antiparallelo, obbligatorio
   by-pass di emettitore:  X_CE ≤ R_E/10  →  C_E ≥ 10 / (2π·f_min·R_E)
```
**VERIFICA** — scrivi la disuguaglianza finale per esteso: senza quella riga l'esercizio non è chiuso. Il diodo di ricircolo va **disegnato**: senza, il progetto è incompleto anche con tutti i conti giusti.

### R6 · JFET canale N — progetto dell'autopolarizzazione

```
DATI  V_DD, I_D0, V_DS0, e V_GS0  (oppure V_P e I_DSS)
      V_P < 0 per il canale N. Se il testo lo dà positivo sta usando |V_P|:
      scegli il segno che rende R_S POSITIVA.

0. se V_GS0 non è dato, inverti Shockley:  V_GS = V_P·(1 − √(I_D/I_DSS))
1. maglia d'ingresso:  V_GS0 = −R_S·I_D0    →   R_S = −V_GS0 / I_D0
2. maglia d'uscita:    V_DD = I_D0(R_S + R_D) + V_DS0
                       →   R_D = (V_DD − V_DS0 − R_S·I_D0) / I_D0
3. R_G NON SI CALCOLA: si sceglie, es. R_G = 5 MΩ (campo 1÷10 MΩ)

VARIANTE a PARTITORE DI GATE (R_1-R_2 invece del solo R_G a massa)
   V_G = V_GS + V_S      con V_S = R_S·I_D     ← TRE termini, non due
   V_G = V_DD·R_2/(R_1+R_2)   →   R_2 = (V_G/V_DD)·(R_1+R_2) ,  R_1 = (R_1+R_2) − R_2
   qui V_GS può restare negativa anche con V_G > 0: è V_S che la tira giù
```
**VERIFICA** — pinch-off $V_{DS} \ge V_{GS} - V_P$; $V_{GS}$ compresa fra $V_P$ e 0; $R_S > 0$.
**PERCHÉ** — la giunzione di gate è polarizzata **inversamente**, quindi $I_G \approx 0$ e in $R_G$ non scorre corrente: non esiste equazione da cui ricavarla. Serve solo a dare al gate il riferimento di massa, e si prende grande per non abbassare la $Z_{in}$. **All'esame scrivi il valore *e* la frase che lo giustifica** — il prof. ha barrato con un doppio «NO» chi ha provato a calcolarla.

### R7 · MOSFET canale N ad arricchimento — progetto della polarizzazione

```
Le DUE STRADE per V_GS, da non scambiare mai:
   ANALISI  (partitore dato)  →  V_GS = V_DD·R_2/(R_1+R_2) − V_S
   PROGETTO (I_D dato)        →  V_GS = √(I_D/K) + V_t      ← non √(I_D/R_D)!

DATI  V_DD, I_D, K, V_t, (R_1+R_2)

1. V_GS = √(I_D/K) + V_t
2. SI SCEGLIE V_DS, rispettando  V_DS ≥ V_GS − V_t   (tipico V_DD/2)
   — non è un calcolo, è una scelta di progetto: dichiarala e motivala
3. R_D = (V_DD − V_DS − V_S) / I_D           con V_S = R_S·I_D  (0 se non c'è R_S)
4. V_R2 = V_GS + V_S
5. R_2 = (V_R2 / V_DD)·(R_1+R_2)      ·      R_1 = (R_1+R_2) − R_2
6. R_G / partitore di gate: I_G = 0, I_S = I_D  (non partitori di corrente)
```
**VERIFICA** — saturazione $V_{DS} > V_{GS} - V_t$; se non regge sei in **ohmica/triodo** e la parabolica non vale ($I_D = K[2(V_{GS}-V_t)V_{DS} - V_{DS}^2]$).
**CONTROLLO UNITÀ che salva l'esercizio** — $K$ si dà in **mA/V²**: con $K = 0{,}6$ mA/V² e $V_{GS}-V_t = 11{,}9$ V viene $I_D = 0{,}6\cdot10^{-3}\cdot141{,}6 = 84{,}9$ **mA**, non 84,9 A.

### R8 · Zener — dimensionamento di $R_S$ e le due verifiche di potenza *(orale/pratica)*

```
LE TRE CORRENTI, in ordine:  I_ZK (ginocchio, ~1 mA) < I_ZT (test, ~5 mA) < I_ZM = P_max/V_Z
   in PROGETTO ci si dimensiona su I_ZT, non su I_ZK.
Al nodo:  I_R = I_Z + I_L        V_o = V_Z + I_Z·r_D   (r_D è interna, ≠ R esterna)

DUE CASI PEGGIORI OPPOSTI — è il cuore dell'esercizio
1. scelta di R_S → V_in,MIN + carico MASSIMO
      R_S,max = (V_in,min − V_Z) / (I_ZT + I_L,max)      → scegli R_S ≤ R_S,max
2. potenza sullo Zener → V_in,MAX + carico STACCATO (I_L = 0: tutto va nello Zener)
      R_S,min = (V_in,max − V_Z) / (I_ZM + I_L,min)
      P_Z = V_Z · I_Z,max < P_Z,max   → arrotonda alla potenza commerciale SUPERIORE
3. potenza su R_S:  P_R = (V_in,max − V_Z)² / R_S   → idem, potenza commerciale superiore
```
**VERIFICA** — deve valere $R_{S,min} \le R_S \le R_{S,max}$. **Se l'intervallo è vuoto** (caso reale in [[Esercizi - Alimentatori]] Es. S1: 188 Ω > 41,9 Ω) il progetto a solo Zener è **impossibile**: cambia Zener o passa al regolatore serie a BJT. Dirlo vale punti.
**Zener in INVERSA** — catodo verso il nodo alto. Disegnarlo in diretta è errore da zero.

### R9 · Alimentatore completo — l'ordine dei vincoli *(orale/pratica)*

```
IL VINCOLO CHE COMANDA È IL DROPOUT, non il trasformatore. Ordine obbligato:

1. DROPOUT   78xx: V_D = 2,5 V  →  V_in ≥ V_out + 2,5 V
             e va verificato NEL MINIMO DEL RIPPLE, non in media
2. TRAFO     V_in,p = V_2·√2 − 2·0,7  (ponte)   oppure  − 0,7 (semionda)
             scegli V_2 lasciando margine per l'ondulazione
3. FILTRO C  quale formula? guarda COSA DÀ IL TESTO:
               volt di ondulazione (V_r,pp)  →  C = I_L / (f_r · V_r,pp)
               percentuale ("ripple 5%")     →  è r, rapporto fra EFFICACI:
                                                r = 1/(2√3 · f_r · R_L · C)
             scambiarle sbaglia C di un fattore ~3,5
             f_r = 100 Hz dopo il ponte, 50 Hz dopo la semionda  ← conta i diodi
             arrotonda C al valore commerciale SUPERIORE (909 µF → 1000 µF)
4. POTENZE   P_BJT = (V_in − V_out)·I_L   → serve dissipatore sopra ~1 W
             regolatore serie a BJT:  V_o = V_Z − 0,7  ·  V_in ≥ V_o + 1 V
```
**VERIFICA** — $V_{in}$ nel punto più basso del ripple è ancora $\ge V_{out} + 2{,}5$ V.
**Ponte vs semionda** — il ponte usa **metà** avvolgimento secondario a parità di $V_o$: si preferisce sempre, il rame costa più di due diodi.

## 0.3 I numeri che si scelgono (non si calcolano)

| Grandezza | Valore da imporre | Perché |
|---|---|---|
| $R_G$ (JFET/MOSFET) | **1÷10 MΩ**, es. 5 MΩ | $I_G \approx 0$: nessuna equazione la vincola. Grande per non abbassare $Z_{in}$ |
| $V_E$ (BJT partitore) | $V_{CC}/10$ | caduta piccola ma sufficiente alla retroazione |
| $V_{RC} = V_{CE}$ (BJT) | $9V_{CC}/20$ | escursione simmetrica + niente fuga termica |
| $I$ nel partitore di base | $10\,I_B$, con $h_{FE,\min}$ | rende $V_B$ un riferimento fisso |
| Overdrive in commutazione | $k = 2\div5$ | garantisce saturazione col transistor peggiore |
| $V_{DS}$ (progetto MOS/JFET) | libera entro $V_{DS} \ge V_{GS}-V_t$; tipico $V_{DD}/2$ | massima escursione simmetrica |
| $C_E$ di by-pass | $X_{CE} \le R_E/10$ | "molto minore" = rapporto almeno 10 |
| $I_Z$ di progetto | $I_{ZT} \approx 5$ mA | sopra il ginocchio in ogni condizione |
| $V_{r,pp}$ ammesso | ≈ **5%** di $V_{DC}$ | regola pratica |
| Dropout 78xx/79xx | **2,5 V** | TABELLA 1 Mirandola |
| $C_{in}$ / $C_{out}$ regolatore | 0,33 µF / 0,1 µF | stabilità |
| Arrotondamenti | $C$ e potenze → commerciale **superiore**; una $R_{max}$ → commerciale **inferiore** | si arrotonda sempre dalla parte sicura |

**Costanti**: $V_\gamma$(Si) $= 0{,}7$ V · $V_\gamma$(Ge/Schottky) $= 0{,}2\div0{,}3$ V · $V_{BE} = 0{,}7$ V *(Carli su una verifica impone 0,8 V: usa il valore del testo)* · $V_{CE,sat} = 0{,}2$ V · $V_T = 26$ mV · $V_P < 0$ (JFET n) · $V_{th} > 0$ (MOSFET n arricchimento) · $\beta = 100\div300$.

## 0.4 Le cinque regole di chiusura

1. **Dati in colonna** prima di iniziare, e spuntali man mano che li usi.
2. **Una maglia per volta**: ingresso e uscita non si mescolano mai in un'unica equazione.
3. **Controllo dimensionale prima del numero**: se le unità non tornano, la formula è sbagliata comunque.
4. **Ogni ipotesi si chiude con la sua verifica**. Se non regge, scrivilo e rifai con l'altra zona.
5. **Mai un esercizio in bianco**: la relazione di partenza, anche senza conti, vale punti. Carli scrive *«perché non ha continuato lo svolgimento?»* — e toglie punti a un risultato giusto ottenuto da una relazione sbagliata, quindi **fai vedere i passaggi**.

---

# Parte A — Tabelle comparative (lookup 5 secondi)

> Tabella comparativa = confronto diretto. Per la formula esatta scendi in **Parte B**; per il perché intuitivo vedi l'hub [[00 - Perchè (spiegazione intuitiva)]] §N.

## A1. BJT vs MOSFET vs JFET

| | **BJT** | **MOSFET** | **JFET** |
|---|---|---|---|
| **Pilotaggio** | Corrente $I_B$ | Tensione $V_{GS}$ (≥0) | Tensione $V_{GS}$ (≤0) |
| **$Z_{in}$** | Bassa (~kΩ) | ~∞ (ossido isolante) | Molto alta (giunz. inversa) |
| **Statico a riposo** | $I_B > 0$ sempre | ~0 (solo leak gate) | ~0 (gate inversa) |
| **Corrente uscita** | $I_C = \beta I_B$ | $I_D = K(V_{GS}-V_{th})^2$ | $I_D = I_{DSS}(1-V_{GS}/V_P)^2$ |
| **"Saturazione"** | Trans. **ON** ($V_{CE}\!\approx\!0{,}2$V) | **Amplifica** (I costante vs V) | come MOSFET |
| **Switching** | lento (μs) | veloce (ns) | veloce (ns) |
| **Rumore** | medio-alto (shot) | basso | bassissimo |
| **Uso tipico** | amplif. analogica, TTL | CMOS, switching potenza | pre-amp audio, VCR |

## A2. Amplificatori BJT — CE vs CC vs CB

| | **CE** (Emettitore Comune) | **CC** (Emitter Follower) | **CB** (Base Comune) |
|---|---|---|---|
| **$A_v$** | Alto (10–100), **inverte 180°** | ≈ 1 (0,95–0,99) | Alto, NO inversione |
| **$Z_{in}$** | ~kΩ | **alta** ~100 kΩ | bassa ~100 Ω |
| **$Z_{out}$** | ~10 kΩ | **bassa** ~100 Ω | alta ~MΩ |
| **$A_i$** | ≈ β (~100) | ≈ β | ≈ 1 |
| **Uso** | generale, amplif. tensione | **buffer**, adatt. impedenza | RF, alte frequenze |

## A3. RLC serie vs parallelo @ $\omega_0 = 1/\sqrt{LC}$

| | **SERIE** | **PARALLELO** |
|---|---|---|
| **Impedenza a $\omega_0$** | **MINIMA** (= $R$) | **MASSIMA** (= $R$) |
| **Corrente totale** | **MASSIMA** | minima |
| **$V_L$ o $V_C$** | $= Q \cdot V_{tot}$ ⚠️ | $= V_{tot}$ |
| **$I_L$ o $I_C$** | $= I_{tot}$ | $= Q \cdot I_{tot}$ ⚠️ |
| **$Q$ (merito)** | $\dfrac{\omega_0 L}{R}$ | $\dfrac{R}{\omega_0 L}$ ⚠️ **reciproco, non uguale** |
| **Banda passante** | $\omega_0 / Q$ | $\omega_0 / Q$ |

### A3b. Diodi — normale vs Zener vs Schottky

| | **Diodo normale** | **Zener** | **Schottky** |
|---|---|---|---|
| **$V_F$ diretta** | ≈ 0,7 V (Si) | ≈ 0,7 V | ≈ 0,2–0,4 V |
| **Funzione tipica** | raddrizzatore | regolatore ($V_Z$ fisso) | switching rapido |
| **Breakdown** | DISTRUTTIVO ⚠️ | **modalità di lavoro** | $V_{BR}$ bassa (20–100 V), leakage inverso **alto** ⚠️ |
| **Switching** | medio (~μs) | medio (~μs) | veloce (ns) |
| **Uso** | Graetz, OR/AND logica | stabilizzatore (es. 5,6 V) | free-wheeling, RF, SMPS |

## A4. Filtri RC vs RL (PB = passa-basso, PA = passa-alto)

| Filtro | $f_t$ (taglio) | Dove va C/L |
|---|---|---|
| **RC PB** | $1/(2\pi R C)$ | C verso massa |
| **RC PA** | $1/(2\pi R C)$ | C in serie |
| **RL PB** | $R/(2\pi L)$ | L in serie (R a massa) |
| **RL PA** | $R/(2\pi L)$ | L verso massa (R in serie) |

**Regola**: guarda cosa fa il reattivo **alle alte frequenze**. $C$: alle alte è un corto → $C$ a massa = PB, $C$ in serie = PA. $L$: alle alte è un aperto → $L$ in serie = PB, $L$ a massa = PA. **−3 dB** = metà potenza.

## A5. AC vs DC

| | **DC** (ω = 0) | **AC** (sinusoidale) |
|---|---|---|
| **$X_L$** | 0 (corto) | $j\omega L$ |
| **$X_C$** | ∞ (aperto) | $-j/(\omega C)$ |
| **$V$ vs $I$ su L** | — | $V$ anticipa $I$ di 90° |
| **$V$ vs $I$ su C** | — | $V$ ritarda $I$ di 90° |
| **Potenza** | $P = V I$ | $P=VI\cos\varphi$, $Q=VI\sin\varphi$, $S=\sqrt{P^2+Q^2}$ |
| **Rifasamento** | non serve | $C$ parallelo al carico induttivo → annulla $Q$ *(monofase: in programma)* |

## A6. Alimentatore a blocchi

```
AC 230V 50Hz → trafo (abbassa + isola) → AC es.12V
→ ponte Graetz (4 diodi) → DC pulsante ~15,6V picco (12·√2 = 17V, meno 2·0,7V dei diodi)
→ C filtro (livella, ripple ≈ I_carico/(f·C), f=100Hz dopo ponte)
→ regolatore 78xx (dropout 2,5V, V_in ≥ V_out + 2,5V) → DC stabile
```

## A7. Mnemonico 30s (visione d'insieme)

- **Sinusoidi**: rotazione → $\cos\omega t$ → derivata = $\sin$ (**Faraday**)
- **Impedenze**: R pura, L anticipa +90°, C ritarda −90°
- **Potenze**: $P$ consumata, $Q$ rimbalzo, $S=\sqrt{P^2+Q^2}$ → **P+Q≠S**
- **Risonanza**: $\omega_0^2=1/LC$ → $X_L=X_C$ → tutto resistivo
- **Filtri**: $C$ a massa = PB, $C$ in serie = PA; $L$ in serie = PB, $L$ a massa = PA
- **Transistor**: BJT $I_C=\beta I_B$ (sat=ON); MOSFET/JFET $I_D=K(…)^2$ (sat=amplifica)
- **Amplificatori**: CE amplif+inverte; CC buffer $A_v\approx 1$; CB alte freq
- **Alimentatore**: AC → trafo → ponte → C filtro → regolatore → DC
- **Rifasamento**: C parallelo a $L$ → annulla $Q$ → meno $I$ in linea

---

# Parte B — Formule per macroarea

## 1. Impedenze (R, L, C) — regime sinusoidale

| Bipolo | $Z$ in forma complessa | Note |
|---|---|---|
| $R$ | $Z_R = R$ | Nessuno sfasamento |
| $L$ | $Z_L = j\omega L$ | $+90°$ V anticipo su I |
| $C$ | $Z_C = \dfrac{1}{j\omega C} = -\dfrac{j}{\omega C}$ | $-90°$ V ritardo su I |

$$\omega = 2\pi f \qquad X_L = \omega L \qquad X_C = \dfrac{1}{\omega C}$$

### 1.1 Costante di tempo $\tau$ (transitori)

$$\boxed{\tau_{RC} = RC \qquad \tau_{RL} = L/R} \qquad [\tau] = \text{s}$$

$$v(t) = V_\infty + (V_0 - V_\infty)\,e^{-t/\tau}$$

| $t$ | % del transitorio completata |
|---|---|
| $1\tau$ | 63% (scarica: sceso al 37%) |
| $2\tau$ | 86% |
| $3\tau$ | 95% |
| $5\tau$ | 99% → **a regime** |

Legame coi filtri (§4): $f_t = \dfrac{1}{2\pi\tau}$ → RC: $1/(2\pi RC)$; RL: $R/(2\pi L)$.
$\tau$ grande = circuito lento = taglio basso.

> **Errata corrige libro**: $\tau = L/R$ per RL, NON $R/L$. ⚠️ (controllo dimensionale: $[L/R] = \text{H}/\Omega = \text{s}$)

---

## 2. Fasori e numeri complessi

| Conversione | Formula |
|---|---|
| Polare → Cartesiano | $A\cos\varphi + jA\sin\varphi$ |
| Cartesiano → Polare | $A = \sqrt{a^2+b^2}; \varphi = \arctan(b/a)$ |
| Somma/Diff | usare **cartesiano** |
| Prod/Quoz | usare **polare** ($r_1 r_2 \angle(\varphi_1+\varphi_2)$) |

> ⚠️ $\arctan$ va corretto per il quadrante (vedi tabella sotto):
> - II quadrante ($x<0, y>0$): $\varphi = \arctan(y/x) + 180°$
> - III quadrante ($x<0, y<0$): $\varphi = \arctan(y/x) - 180°$
> - IV quadrante ($x>0, y<0$): $\varphi = \arctan(y/x)$

---

## 3. Potenze in alternata

| Grandezza | Unità | Formula |
|---|---|---|
| $P$ (attiva) | W | $P = V_{\text{eff}} I_{\text{eff}} \cos\varphi$ |
| $Q$ (reattiva) | VAR | $Q = V_{\text{eff}} I_{\text{eff}} \sin\varphi$ |
| $S$ (apparente) | VA | $S = V_{\text{eff}} I_{\text{eff}} = \sqrt{P^2+Q^2}$ |
| $\cos\varphi$ | — | $P/S$ |

$$\tan\varphi = Q/P \qquad \varphi = \arg Z$$

**Triangolo delle potenze**: $P$ orizzontale, $Q$ verticale (induttivo +, capacitivo −), $S$ ipotenusa.

---

## 4. Filtri passivi del primo ordine

| Topologia | $f_t$ | $G(s)$ | $G(s\to 0)$ | $G(s\to\infty)$ |
|---|---|---|---|---|
| RC passa-basso | $\dfrac{1}{2\pi RC}$ | $\dfrac{1}{1+sRC}$ | 1 | 0 |
| RL passa-basso | $\dfrac{R}{2\pi L}$ ⚠️ | $\dfrac{1}{1+sL/R}$ | 1 | 0 |
| RC passa-alto | $\dfrac{1}{2\pi RC}$ | $\dfrac{sRC}{1+sRC}$ | 0 | 1 |
| RL passa-alto | $\dfrac{R}{2\pi L}$ ⚠️ | $\dfrac{sL/R}{1+sL/R}$ | 0 | 1 |

> ⚠️ $\tau = RC$ per RC, $\tau = L/R$ per RL.

---

## 5. Reti RLC e risonanza

$$\omega_0 = \frac{1}{\sqrt{LC}} = 2\pi f_0 \qquad f_0 \approx \frac{159{,}15}{\sqrt{L_{\text{mH}} \cdot C_{\text{nF}}}} \text{ kHz}$$

> ⚠️ **Attenzione alle unità della scorciatoia**: la costante $159{,}15$ vale con $L$ in **mH** e $C$ in **nF**.
> Con $C$ in **µF** la costante diventa $5{,}033$. Controllo: $L = 100\ \mu$H $= 0{,}1$ mH, $C = 10$ nF
> $\Rightarrow f_0 = 159{,}15/\sqrt{0{,}1 \cdot 10} = 159{,}15$ kHz — è l'Es. R1 di [[Esercizi - Reti RLC e risonanza]].

**Serie RLC** (risonanza serie):
$$Q_s = \frac{\omega_0 L}{R} = \frac{1}{R\omega_0 C} = \frac{1}{R}\sqrt{\frac{L}{C}} = \frac{f_0}{\text{BW}}$$
A risonanza: $Z = R$ (min), $I = $ max, $V_L = V_C = Q \cdot V_{\text{ingresso}}$.

**Parallelo RLC** (antirisonanza):
$$Q_p = \frac{R}{\omega_0 L} = R\omega_0 C = R\sqrt{\frac{C}{L}}$$
A risonanza: $Z$ = max, $V = $ max, $I_L = I_C = Q \cdot I_{\text{totale}}$.

> [!warning] Nel parallelo, **guarda dov'è la resistenza** prima di scrivere $Z=R$
> | Dove sta $R$ | A risonanza |
> |---|---|
> | in **serie** al ramo (caso serie) | $\|Z\|_{\min} = R$, $\omega_0 = 1/\sqrt{LC}$ |
> | in **parallelo** al serbatoio $LC$ | $\|Z\|_{\max} = R$, $\omega_0 = 1/\sqrt{LC}$ |
> | in **serie all'induttore** (parallelo reale) | $\|Z\|_{\max} = \dfrac{L}{RC}$ (**resistenza dinamica**, non $R$) e $\omega_0 = \dfrac{1}{\sqrt{LC}}\sqrt{1 - \dfrac{CR^2}{L}}$ |
>
> Il terzo caso è quello **realistico** (la $R$ è quella del filo dell'induttore) ed è la correzione del libro a p. 58. Vedi [[Reti RLC e risonanza]].

**Banda passante a −3 dB**: $\text{BW} = f_H - f_L = f_0/Q$.

---

## 6. BJT — struttura, regioni, polarizzazione

> **Progetto** (dato il punto di lavoro, dimensiona le resistenze) → **§0.2 R3** (partitore) e **R4** (sola $R_B$). Verifica di saturazione → **R5**.

### 6.1 Tre regioni

| Regione | B-E | B-C | $V_{CE}$ | $I_C$ |
|---|---|---|---|---|
| Attiva | diretta | inversa | $> V_{CE,\text{sat}}\approx 0{,}2$ V | $\beta I_B$ |
| Saturazione | diretta | diretta | $\approx 0{,}2$ V | limitato da $R_C$ |
| Interdizione | inversa | inversa | $= V_{CC}$ | $\approx 0$ |

### 6.2 Polarizzazione classica (Vbb + Rb)

$$I_B = \frac{V_{BB} - V_{BE}}{R_B} \qquad I_C = \beta I_B \qquad V_{CE} = V_{CC} - I_C R_C$$

### 6.3 Polarizzazione con partitore

$$V_B = V_{CC} \frac{R_2}{R_1+R_2} \qquad V_E = V_B - V_{BE}$$
$$I_E = V_E / R_E \qquad I_C = \frac{\beta}{\beta+1} I_E \approx I_E$$
$$V_{CE} = V_{CC} - I_C R_C - I_E R_E$$

> ⚠️ Con $R_E$, **non** dimenticare la caduta su $R_E$ nel calcolo di $V_{CE}$.

### 6.4 BJT come interruttore

In saturazione: $V_{CE} \approx 0{,}2$ V; $I_C \approx (V_{CC}-0{,}2)/R_C$.
Verifica: serve $I_B > I_{B,\text{sat}} = I_C/\beta$.

---

## 7. MOSFET enhancement n-channel (design in saturazione)

> ⚠️ Tutte le formule valgono SOLO **in saturazione**. Verifica finale: $V_{DS} > V_{GS} - V_{th}$.
> Se la verifica fallisce il MOSFET è in **zona ohmica (triodo)**, che è l'**opposto** della saturazione,
> e la parabolica non vale più: vedi l'Es. 4 di [[Esercizi - BJT]], risolto in triodo.

> **Progetto** (dato $I_D$, dimensiona $R_D$, $R_1$, $R_2$) → **§0.2 R7**. Le due strade per $V_{GS}$ non vanno scambiate.

### 7.1 Equazione parabolica

$$\boxed{I_D = K (V_{GS} - V_{th})^2} \qquad \text{in saturazione}$$

$K$ in A/V², $V_{th}$ > 0 (n-channel), $V_{GS} > V_{th}$.

### 7.2 Polarizzazione a partitore (con $R_S$)

$$V_G = V_{DD} \frac{R_2}{R_1+R_2} \qquad V_{GS} = V_G - I_D R_S$$

Sostituendo nella parabolica: equazione di **2° grado in $I_D$**:
$$K R_S^2 I_D^2 - (2K R_S (V_G-V_{th}) + 1) I_D + K(V_G-V_{th})^2 = 0$$

Risolvi: scarta la radice che dà $V_{GS} < V_{th}$.

### 7.3 Retta di carico (output)

$$V_{DS} = V_{DD} - I_D (R_D + R_S)$$

> ⚠️ Verifica SEMPRE: $V_{DS} > V_{GS} - V_{th}$ (altrimenti si è in **triodo**, e la parabolica non vale più).

---

## 8. JFET n-channel (design in saturazione)

> **Progetto** (dato il punto di lavoro, dimensiona $R_S$, $R_D$, $R_G$) → **§0.2 R6**. $R_G$ si sceglie, non si calcola.

### 8.1 Equazione parabolica (paradossale: $I_D$ MAX a $V_{GS}=0$)

$$\boxed{I_D = I_{DSS}\left(1 - \frac{V_{GS}}{V_P}\right)^2}$$

$V_P < 0$ (JFET n); $V_{GS} \le 0$ (polarità inversa!); $I_{DSS}$ = corrente a $V_{GS}=0$.

> [!warning] **P-channel (per Trabocchetto)**
> JFET P-channel: **$V_P > 0$**, $I_{DSS}$ può essere dichiarato **negativo** (convenzione Millman/Sedra), alimentazione tramite $V_{SS}$ negativa. **Le formule sono IDENTICHE**, applicate con i segni riflessi. Risultato: $I_D < 0$ (flusso source→drain). **Verifica i segni di $V_P$ e $I_{DSS}$ PRIMA di mettere numeri nei conti.**

### 8.2 Autopolarizzazione (schema standard)

$$V_{GS} = -I_D R_S \quad (\text{perché } V_G = 0 \text{ con } R_G \text{ verso massa})$$

Sostituendo nella parabolica: 2° grado in $I_D$. Scarta la radice con $V_{GS}<V_P$.

### 8.3 Retta di carico

$$V_{DS} = V_{DD} - I_D (R_D + R_S)$$

Verifica pinch-off: $V_{DS} > V_{GS} - V_P$.

### 8.4 Transconduttanza $g_m$ (parametro chiave amplificazione)

$$\boxed{g_m = \dfrac{2 I_{DSS}}{|V_P|} \cdot \left(1 - \dfrac{V_{GS}}{V_P}\right) = g_{m0} \cdot \left(1 - \dfrac{V_{GS}}{V_P}\right)}$$

- $g_{m0} = 2 I_{DSS}/|V_P|$ = transconduttanza a $V_{GS}=0$ (massima).
- Unità: siemens (S) o millisiemens (mS). Tipico: $g_m = 1\text{–}10$ mS.
- Calcolare SEMPRE DOPO aver trovato il punto di lavoro (V_GS noto).

### 8.5 Amplificatore Source Comune (CS, mid-band, $R_S$ bypassato)

$$\boxed{A_v = -g_m \cdot (R_D \parallel R_L)} \quad \text{(inversione 180°)}$$

Con $R_S$ **non bypassato** (degenerazione):
$$\boxed{A_v = -\dfrac{g_m R_D}{1 + g_m R_S}} \quad \text{(stabile, ma guadagno minore)}$$

$R_{in} \approx R_G$ (tipicamente 1 MΩ; **scelta standard del progettista**, non costante del JFET). $R_{out} \approx R_D$ (trascurando $r_d$).

### 8.6 Source Follower / Drain Comune (CD)

$$\boxed{A_v = +\dfrac{g_m R_S}{1 + g_m R_S} \approx 1 \text{ (per } g_m R_S \gg 1\text{)}}$$

$R_{in} \approx R_G$ (MΩ), $R_{out} \approx 1/g_m$ (centinaia di Ω). **Adattatore di impedenza**.

### 8.7 JFET come VCR (Voltage Controlled Resistor, zona triodo)

$$R_{DS}(V_{GS}) \approx \dfrac{r_{DS(on)}}{1 - V_{GS}/V_P}$$

> ⚠️ **Valida solo per $V_{DS} \to 0$**. Per $V_{DS}$ apprezzabile, $R_{DS}$ dipende anche da $V_{DS}$ (curva parabolica in zona triodo).

### 8.8 JFET come interruttore analogico (analog switch)

| Stato | $V_{GS}$ | Comportamento |
|---|---|---|
| **OFF** | $V_{GS} \le V_P$ | $R_{DS} \to \infty$, segnale bloccato |
| **ON** | $V_{GS} \approx 0$ | $R_{DS} = r_{DS(on)}$ (da datasheet, pochi Ω a 100 Ω), segnale passa |

---

## 9. Amplificatori a BJT — parametri h (mid-band)

### 9.1 CE — Common Emitter

$$A_v = -h_{fe} \frac{R_C \parallel R_L}{h_{ie} + (\beta+1)R_E} \approx -\frac{R_C \parallel R_L}{r_e}$$

$r_e = V_T/I_E$ con $V_T \approx 26$ mV a Tamb. ⚠️ **SEGNOMEMO**: $A_v$ negativo in CE.

$$R_{in,\text{base}} = h_{ie} \approx \beta r_e \qquad R_{out} \approx R_C \parallel 1/h_{oe}$$

### 9.2 CC — Emitter Follower

$$A_v = \frac{(\beta+1)R_E \parallel R_L}{h_{ie} + (\beta+1)R_E \parallel R_L} \approx 1 \quad (0{,}95{-}0{,}99)$$

> $A_v$ positivo, ma **alto guadagno di corrente**. Usato come buffer.

### 9.3 CB — Common Base

$$A_v = +\frac{h_{fe} \cdot R_C \parallel R_L}{h_{ie}}$$

> $A_v$ positivo, $R_{in}$ bassissima. Alta frequenza.

### 9.4 Risposta in frequenza (passa-banda)

$$A_v(s) = A_{v,\text{mid}} \cdot \underbrace{\dfrac{s/(2\pi f_L)}{1 + s/(2\pi f_L)}}_{\text{passa-ALTO} \to f_L} \cdot \underbrace{\dfrac{1}{1 + s/(2\pi f_H)}}_{\text{passa-basso} \to f_H}$$

In modulo: $|A_v(f)| = \dfrac{A_{v,\text{mid}}}{\sqrt{1+(f_L/f)^2}\ \sqrt{1+(f/f_H)^2}}$

$f_L$: taglio inferiore (da $C$ di accoppiamento). $f_H$: taglio superiore (parassiti). BW $= f_H - f_L$.

> ⚠️ Il termine di $f_L$ è **passa-alto** ($\to 0$ in DC): se lo scrivi come $1/(1+s/2\pi f_L)$ il guadagno resterebbe pieno in continua, e i $C$ di accoppiamento non taglierebbero nulla.

---

## 10. Diodi e Zener

### 10.1 Diodo a giunzione (modello a tratti)

| Condizione | Comportamento |
|---|---|
| $V < V_\gamma \approx 0{,}7$ V | OFF (circuito aperto) |
| $V \ge V_\gamma$ | ON ($V_D \approx 0{,}7$ V + $r_D \cdot I_D$) |

### 10.2 Diodo Zener (regolazione in breakdown)

$$V_o = V_Z + I_Z \cdot r_D \qquad P_Z = V_Z \cdot I_Z < P_{Z,\max}$$

**Range di $R_S$ per stabilizzazione**:
$$R_{S,\min} = \frac{V_{in,\max} - V_Z}{I_{Z,\max} + I_{L,\min}} \qquad R_{S,\max} = \frac{V_{in,\min} - V_Z}{I_{Z,\min} + I_{L,\max}}$$

> Caso peggiore di $R_{S,\min}$: $V_{in}$ massima **e carico staccato** ($I_{L,\min}=0$) → tutta la corrente va nello Zener.

---

## 11. Alimentatori

### 11.1 Raddrizzatore

- **Semionda**: $V_{out,p} = V_{in,p} - V_D$; ripple con $f_r = f_{\text{rete}}$.
- **Ponte Graetz**: $V_{out,p} = V_{in,p} - 2V_D$; ripple con $f_r = 2 f_{\text{rete}}$.

> **Ordine dei vincoli nel progetto di un alimentatore completo** (dropout → trafo → $C$ → potenze) → **§0.2 R9**.

### 11.2 Ripple a frequenza $f_r$ e corrente di carico $I_L$

$$V_{r,pp} = \frac{I_L}{f_r \cdot C} \qquad I_L = V_L/R_L \qquad C = \frac{I_L}{f_r V_{r,pp}}$$

**Fattore di ripple** (Mirandola form. **8.1**, Cap. 8 pp. 388-389) — è un valore **efficace**, non picco-picco:

$$\boxed{r = \frac{V_{r,\text{eff}}}{V_{Lm}} = \frac{1}{2\sqrt{3}\, f_r R_L C}} \qquad\Rightarrow\qquad C = \frac{1}{2\sqrt{3}\, f_r R_L\, r}$$

> ⚠️ La $f$ qui è $f_r$ (**ondulazione**: 100 Hz dopo il ponte), non i 50 Hz di rete. Con la $f$ di rete la costante diventa $4\sqrt{3}$.

> [!danger] Le due formule rispondono a domande diverse — non scambiarle
> Se il testo dà i **volt** di ondulazione ($V_{r,pp} = 2$ V) usi la **11.2**. Se dà una **percentuale** («ripple del 5%») quella percentuale è $r$, cioè un **rapporto fra valori efficaci**: usi la 8.1. Interpretare il 5% come picco-picco porta a una $C$ sbagliata di un fattore ~3,5 — è l'errore trovato e corretto nell'Es. A1 di [[Esercizi - Alimentatori]].

### 11.3 Regolatore serie a BJT

$$V_o = V_Z - V_{BE} = V_Z - 0{,}7 \text{ V} \qquad V_{in} \ge V_o + 1 \text{ V (margine zona attiva)}$$

$$P_{BJT} = (V_{in} - V_o) I_L$$

### 11.4 Regolatori integrati 78xx / 79xx

- $V_{dropout} = 2{,}5$ V (TABELLA 1 Mirandola) → serve $V_{in} \ge V_{out} + 2{,}5$ V **nel minimo del ripple**
- 78xx = positivo, 79xx = negativo; xx = tensione (es. 7812 = +12 V)
- $I_{out,\max}$: standard 1 A, suffix L=100 mA, M=500 mA
- $C_{in} \approx 0{,}33\,\mu$F, $C_{out} \approx 0{,}1\,\mu$F (per stabilità)

---

## 12. Costanti e numeri da ricordare

| Simbolo | Valore |
|---|---|
| $V_{BE}$ (BJT NPN) | $\approx +0{,}7$ V |
| $V_{BE}$ (BJT PNP) | $\approx -0{,}7$ V |
| $V_{CE,\text{sat}}$ (BJT) | $\approx 0{,}2$ V |
| $V_\gamma$ (diodo Si) | $\approx 0{,}7$ V |
| $V_{th}$ (MOSFET enhancement n) | $>0$ (1–4 V) |
| $V_P$ (JFET n) | $<0$ (−2 a −8 V) |
| $V_T$ (tensione termica) | $\approx 26$ mV a Tamb |
| $\beta$ (BJT piccolo segnale) | 100–300 |
| $g_m$ (transconduttanza BJT) | $I_C / V_T$ |

---

## 13. Mnemonico finale (le 5 cose che DEVI ricordare)

> Se hai poco tempo, il punto di ingresso non è questo elenco ma la **Parte 0**: lì ci sono i **criteri di progetto**, che è ciò che Carli chiede davvero.

1. **Filtri**: RC → $f_t = 1/(2\pi RC)$. RL → $f_t = R/(2\pi L)$ (NON $L/R$).
2. **Fasori**: cartesiano per somma/diff, polare per prod/quot. **Attenzione ai quadranti di $\arctan$**.
3. **BJT**: $V_{CE} = V_{CC} - I_C R_C - I_E R_E$ (con $R_E$: non dimenticare il terzo termine).
4. **MOSFET**: parabolica SOLO in saturazione. **Verifica finale** $V_{DS} > V_{GS} - V_{th}$.
5. **JFET**: tutti gli esercizi di progetto escono da due sole relazioni —
   $V_{GS0} = -R_S I_{D0}$ e $V_{DD} = I_{D0}(R_S + R_D) + V_{DS0}$.
   *(Sulla verifica 29-05 tre esercizi su cinque sono «NON SVOLTO»: è l'argomento più scoperto.)*

---

## Da qui in poi

- Teoria completa: [[Argomenti]]
- Esercizi svolti: [[Esercizi]]
- Simulazione completa d'esame: [[Esercizi - Simulazione finale]]
- Prove: [[01 - Prova Scritta Carli]], [[02 - Prova Orale Carli]], [[03 - Prova Pratica Protti]]
