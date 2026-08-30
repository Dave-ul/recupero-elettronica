---
tags: [recupero, elettronica, ripasso, carli, soluzioni, diodi, zener, fonte-derivata]
fonte: "condensazione di [[06 - Soluzioni complete verifiche FUSI]] e [[diodi-risposte]] in un'unica nota di ripasso"
file: "Fonti/FUSI_02-03-26_260616_183723.pdf · Fonti/FUSI_24-04-26_260616_183749.pdf · Fonti/FUSI_29-05-26_260616_183828.pdf"
aggiunto: 2026-08-30
verificato: "2026-08-30 — testi ricontrollati sulle scansioni (ritagli a 300 dpi per V3 es. 5 e 6); risultati ripresi dalla nota 06, già ricalcolati da zero il 2026-08-28"
prove: [scritta, orale]
---

# Ripasso finale — Verifiche FUSI e Diodi

Tutto quello che serve il **1° settembre** in un file solo: i **21 esercizi** delle tre
verifiche del Prof. Carli risolti in forma compatta, più le **risposte sui diodi** per l'orale.

> [!info] Come si legge
> Ogni esercizio è ridotto all'osso: **dati → formula → calcolo → risultato**, più una riga di
> *trappola* con l'errore che Carli ha segnato in rosso sul fascicolo di Fusi.
> Sopra ogni gruppo di esercizi c'è la **scansione della pagina originale**, così leggi il testo
> del prof. con i suoi disegni e le sue correzioni in rosso senza aprire il PDF.
> Serve il ragionamento esteso, il perché di ogni passaggio? È in
> [[06 - Soluzioni complete verifiche FUSI]]. Come corregge e valuta:
> [[05 - Verifiche FUSI (Carli)]]. Versione stampabile dei diodi:
> [[diodi-risposte]] (e `Strumenti/diodi-risposte.html` per la cartellina).

> [!warning] Convenzioni valide ovunque
> `ω = 2πf` · `X_L = ωL` · `X_C = 1/(ωC)` · `Z̄_L = jωL` · `Z̄_C = 1/(jωC) = −j/(ωC)`.
> Per `Z̄ = a + jb`: `|Z| = √(a²+b²)`, `arg Z̄ = arctan(b/a)` (correggi il quadrante se `a < 0`).
> BJT in zona attiva: `V_BE = 0,7 V`. JFET/MOSFET: **`I_G = 0`** sempre.

**Indice** — [[#Parte A — Verifica 1 · AC e filtri del primo ordine|A · AC e filtri]] ·
[[#Parte B — Verifica 2 · BJT|B · BJT]] ·
[[#Parte C — Verifica 3 · JFET e MOSFET|C · JFET e MOSFET]] ·
[[#Parte D — Diodi · le risposte per l'orale|D · Diodi]] ·
[[#Formule chiave|Formule chiave]] ·
[[#Le sei trappole che costano il 70% dei punti|Le sei trappole]]

---

# Parte A — Verifica 1 · AC e filtri del primo ordine
**13/02/2026, valutata 02/03 · 6 esercizi · Fusi 3,00/10**

## Es. 1 — Modulo e argomento dell'impedenza equivalente

![[fusi-02-03-p1-es1.png]]
*Verifica 1, p. 1 — intestazione e **es. 1** (bipoli 1A e 1B).*

I due componenti sono **in serie** (maglia unica: il disegno verticale inganna, ma nessun ramo
scavalca il secondo componente) → `Z̄_eq = Z̄₁ + Z̄₂`.

**1A · serie R–C** — `C = 10 nF`, `R = 1 kΩ`, `f = 10 kHz`

```
ω    = 2π·10⁴ = 6,2832·10⁴ rad/s
X_C  = 1/(ωC) = 1/(6,2832·10⁴ · 10·10⁻⁹) = 1591,5 Ω
Z̄_eq = 1000 − j1591,5 Ω
|Z|  = √(1000² + 1591,5²) = 1879,6 Ω
φ    = arctan(−1591,5/1000) = −57,86°
```

> [!success] **|Z_eq| ≈ 1,88 kΩ · φ ≈ −57,9°** → bipolo **ohmico-capacitivo** (corrente in anticipo).

> [!danger] Trappola
> Fusi ha usato `f = 1 kHz` invece di 10 kHz, e ha scritto `Z̄_C = −1/(jωC)`: un meno di troppo,
> perché `1/(jωC)` vale **già** `−j/(ωC)` (dato che `1/j = −j`). Con quel segno la capacità
> diventa un'induttanza.

**1B · serie R–L** — `R = 330 Ω`, `L = 12 mH`, `f = 10 kHz`

```
X_L  = ωL = 6,2832·10⁴ · 12·10⁻³ = 753,98 Ω
Z̄_eq = 330 + j754 Ω
|Z|  = √(330² + 753,98²) = 823,0 Ω
φ    = arctan(753,98/330) = +66,36°
```

> [!success] **|Z_eq| ≈ 823 Ω · φ ≈ +66,4°** → bipolo **ohmico-induttivo** (corrente in ritardo).

> [!danger] Trappola
> Ha scritto `√(330² + 75²)` (ordine di grandezza perso su `X_L`) e `arctan(1/328,9)`.
> **L'argomento non è mai `arctan(1/|Z|)`**: è sempre `arctan(Im/Re)`.

---

## Es. 2 — Poli delle funzioni di trasferimento

![[fusi-02-03-p3-es2-3.png]]
*Verifica 1, p. 3 — **es. 2** (poli) ed **es. 3** (risposta in ampiezza e fase).*

I **poli** sono le radici del **denominatore**; gli zeri quelle del numeratore. Nessun limite,
nessun guadagno: si annulla `D(s)` e si risolve.

**2A** — `G(s) = 3/(s² + 5s + 6)`

```
s² + 5s + 6 = 0   →   Δ = 25 − 24 = 1
s = (−5 ± 1)/2    →   s₁ = −2 ,  s₂ = −3     [ (s+2)(s+3) ]
```

> [!success] **Poli: s₁ = −2 rad/s, s₂ = −3 rad/s** — reali, negativi, distinti → **stabile**,
> secondo ordine sovrasmorzato, nessuno zero.

**2B** — `G(s) = (s + 1)/[3s(s + 5)]`

```
D(s) = 3s(s+5) = 0  →  s₁ = 0 ,  s₂ = −5
N(s) = s + 1  = 0  →  z₁ = −1
```

> [!success] **Poli: s₁ = 0 (nell'origine), s₂ = −5 rad/s · Zero: z₁ = −1 rad/s.**
> Il polo nell'origine = comportamento **integratore** → **marginalmente stabile**.

> [!danger] Trappola
> Fusi ha calcolato un limite ottenendo «0,6», che è il guadagno statico di 2A, non un polo.
> Nota del prof.: *«completamente errato»*.

---

## Es. 3 — Risposta in ampiezza e in fase del quadripolo

`R₁` in serie; `R₂ ∥ L` verso massa; uscita sul parallelo.
**Dati:** `R₁ = 2,2 kΩ`, `R₂ = 5,6 kΩ`, `L = 1 mH` · `f = 0 / 100 kHz / 20 MHz`

Partitore fra impedenze, $\bar{G}(j\omega) = \bar{Z}_p/(R_1 + \bar{Z}_p)$ con
$\bar{Z}_p = R_2 \parallel j\omega L$. Semplificando:

```
                jωL·R₂                                    ωL·R₂
Ḡ(jω) = ───────────────────────      |G| = ──────────────────────────────
          R₁R₂ + jωL(R₁+R₂)                 √[(R₁R₂)² + (ωL(R₁+R₂))²]

φ(ω) = 90° − arctan[ ωL(R₁+R₂)/(R₁R₂) ]        ← +90° dalla j (zero nell'origine)
```

**È un passa-alto del primo ordine.**

```
ω_t = R₁R₂/[L(R₁+R₂)] = 12,32·10⁶/7,8 = 1,5795·10⁶ rad/s  →  f_t = 251,4 kHz
Guadagno asintotico (ω→∞) = R₂/(R₁+R₂) = 5600/7800 = 0,718

f = 0      : Z̄_L = 0 → L cortocircuita l'uscita → |G| = 0 , φ = +90°
f = 100 kHz: ωL = 628,3 Ω · num = 3,519·10⁶ · den = √[(12,32·10⁶)²+(4,901·10⁶)²] = 1,326·10⁷
             |G| = 0,265 (−11,5 dB) · φ = 90° − 21,7° = +68,3°
f = 20 MHz : ωL = 1,2566·10⁵ Ω · num = 7,037·10⁸ · den ≈ 9,803·10⁸
             |G| = 0,718 (−2,9 dB) · φ = 90° − 89,3° = +0,7°
```

> [!success] Risultato
> | f | \|G\| | dB | φ |
> |---|---|---|---|
> | 0 Hz | 0 | −∞ | +90° |
> | 100 kHz | 0,265 | −11,5 | +68,3° |
> | 20 MHz | 0,718 | −2,9 | +0,7° |
>
> Passa-alto, `f_t ≈ 251 kHz`, guadagno in banda `0,718`.

---

## Es. 4 — Funzione di trasferimento dei quadripoli

![[fusi-02-03-p5-es4-5.png]]
*Verifica 1, p. 5 — **es. 4** (funzioni di trasferimento) ed **es. 5** (frequenze di taglio).*

Partitore: `Ḡ(s) = Z̄_uscita/(Z̄_serie + Z̄_uscita)`. Il tipo di filtro dipende da **su quale
componente si preleva l'uscita**. `Ḡ(s)` è sempre **adimensionale**: se viene in ohm, è sbagliata.

**4A · R in serie, L verso massa, uscita su L** — `R = 560 Ω`, `L = 3 mH`

```
G(s) = sL/(R + sL) = s/(s + R/L)
ω_t  = R/L = 560/3·10⁻³ = 1,867·10⁵ rad/s  →  f_t = 29,7 kHz
```

> [!success] **G(s) = s/(s + 1,867·10⁵)** — **passa-alto**, `f_t ≈ 29,7 kHz`, guadagno unitario in
> banda, **zero nell'origine**, polo in `−1,867·10⁵ rad/s`.

**4B · L in serie, R verso massa, uscita su R** — `L = 0,3 mH`, `R = 1,2 kΩ`

```
G(s) = R/(R + sL) = 1/(1 + sL/R)
τ    = L/R = 2,5·10⁻⁷ s   ·   ω_t = R/L = 4·10⁶ rad/s  →  f_t = 636,6 kHz
```

> [!success] **G(s) = 1/(1 + 2,5·10⁻⁷·s)** — **passa-basso**, `f_t ≈ 637 kHz`, guadagno unitario in
> continua, polo in `−4·10⁶ rad/s`, nessuno zero.

> [!danger] Trappola
> Fusi ha **sommato** le impedenze (`V_o = V_i·(Z_R + Z_C)`) invece di fare il rapporto del
> partitore, e in 4A ha messo un condensatore dove c'è un'**induttanza**.

---

## Es. 5 — Frequenza di taglio dei filtri

Il taglio è dove **la reattanza eguaglia la resistenza** (`X_C = R`, −3 dB):
`f_t = 1/(2πRC)`. **Stessa formula** per passa-alto e passa-basso.

**5A · C in serie, R verso massa → passa-alto** — `C = 150 nF`, `R = 6,8 kΩ`

```
RC  = 6800 · 150·10⁻⁹ = 1,02·10⁻³ s
f_t = 1/(2π · 1,02·10⁻³) = 156,0 Hz
```

**5B · R in serie, C verso massa → passa-basso** — `R = 1 kΩ`, `C = 2,2 µF`

```
RC  = 1000 · 2,2·10⁻⁶ = 2,2·10⁻³ s
f_t = 1/(2π · 2,2·10⁻³) = 72,3 Hz
```

> [!success] **5A: f_t ≈ 156 Hz (passa-alto) · 5B: f_t ≈ 72,3 Hz (passa-basso).**

> [!note] «NON SVOLTO PER NULLA» — 0,00/2,00 punti. Due divisioni, il 20% del voto.

---

## Es. 6 — Impedenza equivalente della rete

![[fusi-02-03-p7-es6.png]]
*Verifica 1, p. 7 — **es. 6**, la rete di quattro impedenze.*

`Z̄₁ = 2 + j6` · `Z̄₂ = 2 − j2` · `Z̄₃ = j10` · `Z̄₄ = 2 + j4` (Ω)

**Topologia**: il morsetto superiore e il nodo centrale sono lo stesso nodo **A**; il morsetto
inferiore, il filo di fondo e il nodo di destra sono lo stesso nodo **B**. Quindi **tutte e
quattro sono in parallelo** fra A e B. Si risolve a coppie.

```
Z̄₂₄  = Z̄₂Z̄₄/(Z̄₂+Z̄₄):  num (2−j2)(2+j4) = 12 + j4 ;  den = 4 + j2
                        (12+j4)(4−j2)/20 = (56 − j8)/20  →  Z̄₂₄ = 2,8 − j0,4 Ω

Z̄₂₃₄ = Z̄₂₄Z̄₃/(Z̄₂₄+Z̄₃): num (2,8−j0,4)(j10) = 4 + j28 ; den = 2,8 + j9,6
                        (4+j28)(2,8−j9,6)/100 = (280 + j40)/100  →  Z̄₂₃₄ = 2,8 + j0,4 Ω

Z̄_eq = Z̄₁Z̄₂₃₄/(Z̄₁+Z̄₂₃₄): num (2+j6)(2,8+j0,4) = 3,2 + j17,6 ; den = 4,8 + j6,4
                        (3,2+j17,6)(4,8−j6,4)/64 = (128 + j64)/64  →  Z̄_eq = 2 + j1 Ω
```

> [!success] **Z̄_eq = (2 + j1) Ω · |Z_eq| = √5 = 2,24 Ω · arg = +26,6°** → ohmico-induttivo.
> I numeri escono esatti: è la conferma che la topologia è stata letta bene.

> [!danger] Trappola
> Fusi ha impostato bene i paralleli ma nel passo 1 ha scritto `3 + j2` invece di `2,8 − j0,4`.
> **Controllo veloce: i moduli si dividono.** `|12+j4|/|4+j2| = 12,65/4,47 = 2,83`;
> `|3+j2| = 3,61` ✗ · `|2,8−j0,4| = 2,83` ✓.

---

# Parte B — Verifica 2 · BJT
**24/04/2026, valutata 09/05 · 7 esercizi · Fusi 1,50 punti, 3/10**

> [!abstract] Le tre relazioni che risolvono cinque esercizi su sette
> **In quest'ordine, sempre:**
> 1. **Maglia d'ingresso** (Kirchhoff base–emettitore) → `I_B`
> 2. **Transistor**: `I_C = h_FE·I_B` · `I_E = (h_FE + 1)·I_B`
> 3. **Maglia d'uscita** (Kirchhoff collettore–emettitore) → `V_CE`
>
> **L'errore capitale**, segnato in rosso tre volte: `R_B` nella maglia d'uscita o `R_C` in
> quella d'ingresso. **Le due maglie sono separate** e condividono solo il ramo di emettitore.

## Es. 1 — Determinare V_CE, I_C, I_B

![[fusi-24-04-p1-es1.png]]
*Verifica 2, p. 1 — intestazione e **es. 1**.*

`V_CC = 12 V` · `R_C = 820 Ω` · `V_BB = 5 V` · `R_B = 56 kΩ` · `h_FE = 100` · `V_BE = 0,7 V`
(due alimentazioni, emettitore a massa)

```
I_B  = (V_BB − V_BE)/R_B = 4,3/56·10³ = 76,8 µA
I_C  = h_FE·I_B = 7,68 mA
V_CE = V_CC − R_C·I_C = 12 − 820·7,68·10⁻³ = 12 − 6,30 = 5,70 V

Verifica zona attiva: I_C(sat) = (12 − 0,2)/820 = 14,4 mA > 7,68 mA  ✓
```

> [!success] **I_B = 76,8 µA · I_C = 7,68 mA · V_CE = 5,70 V** — Q a metà retta di carico.

> [!danger] Trappola
> Ultimo passaggio con `10 V` al posto di `12 V` → `V_CE = 3,7 V`. Mezzo punto per una cifra.
> *«errato a sostituire il valore, in quanto V_CC = 12 V»*.

---

## Es. 2 — Progetto di R_C e R_B per il punto di lavoro assegnato

![[fusi-24-04-p3-es2-3.png]]
*Verifica 2, p. 3 — **es. 2** (progetto R_C e R_B) ed **es. 3** (partitore + R_E).*

`V_CEO = 4,8 V` · `I_CO = 14 mA` · `h_FE = 100` · `V_CC = 10 V` · base fissa, emettitore a massa

```
R_C = (V_CC − V_CEO)/I_CO = 5,2/14·10⁻³ = 371,4 Ω
I_B = I_CO/h_FE = 140 µA
R_B = (V_CC − V_BE)/I_B = 9,3/140·10⁻⁶ = 66,4 kΩ
```

> [!success] **R_C ≈ 371 Ω (comm. 390 Ω) · R_B ≈ 66,4 kΩ (comm. 68 kΩ).**
> Con i commerciali: `I_B = 137 µA`, `I_C = 13,7 mA`, `V_CE = 4,66 V` — accettabile.

> [!danger] Trappola
> Numeri giusti da una relazione falsa: `V_CE = R_B·I_B + R_C·I_C` mescola le due maglie.
> **Risultati giusti da una relazione sbagliata non prendono il punteggio pieno.**

---

## Es. 3 — Progetto polarizzazione e stabilizzazione (partitore + R_E)

`V_CC = 10 V` · `I_CO = 10 mA` · `h_FEmin = 75` · incognite `R_C, R_E, R₁, R₂`

Quattro incognite, meno equazioni: si chiude con i **criteri di progetto** che Carli ha scritto
di suo pugno sul retro (p. 12 del PDF) — **impara questa sequenza**:

```
1)  V_E = V_CC/10 = 1 V            →  R_E = V_E/I_CO = 100 Ω
2)  V_RC = V_CE = 9·V_CC/20 = 4,5 V →  R_C = 4,5/10·10⁻³ = 450 Ω
       (verifica maglia: 4,5 + 4,5 + 1 = 10 V = V_CC ✓)
3)  V_BO = V_BE + R_E·I_CO = 0,7 + 1 = 1,7 V
4)  I_B  = I_CO/h_FEmin = 133,3 µA   →   I = 10·I_B = 1,3 mA
5)  R₂ = V_BO/I = 1,7/1,3·10⁻³ = 1,31 kΩ
    R₁ = (V_CC − V_BO)/I = 8,3/1,3·10⁻³ = 6,38 kΩ
I_E = I_C + I_B = 10,13 mA
```

> [!success] **R_E = 100 Ω · R_C = 450 Ω · R₂ = 1,3 kΩ · R₁ = 6,4 kΩ**
> `I_B = 133 µA · I_E = 10,1 mA · V_BO = 1,7 V · V_CE = 4,5 V`
> Commerciali: 100 Ω · 470 Ω · 1,3 kΩ · 6,2 kΩ.

> [!danger] Trappola
> Ha scritto `R_C = (V_CC − V_CE)/I_CO` **dimenticando la caduta su R_E**: con emettitore
> resistivo la maglia d'uscita è `V_CC = R_C·I_C + V_CE + R_E·I_E`. E non ha imposto il criterio
> `I = 10·I_B`, senza il quale il sistema resta indeterminato.

---

## Es. 4 — Interfaccia porta TTL → bobina di relè

![[fusi-24-04-p5-es4-5.png]]
*Verifica 2, p. 5 — **es. 4** (interfaccia TTL-relè) ed **es. 5** (condensatore di by-pass).*

Uscita TTL `0 V / 5 V` · relè **12 V, 70 mA** · `h_FEmin = 75`

La TTL non basta né in tensione (5 V contro 12) né in corrente (~mA contro 70 mA). Serve un
**BJT NPN in commutazione**: bobina sul collettore a 12 V, emettitore a massa, base pilotata
dalla TTL tramite `R_B`. Lavora fra **interdizione** e **saturazione**, mai in zona attiva.

```
I_C     = 70 mA
I_Bmin  = I_C/h_FEmin = 0,933 mA
I_B     = 2 · I_Bmin = 1,87 mA          (sovrapilotaggio ×2, margine su esemplare e temperatura)
R_B     = (V_OH − V_BEsat)/I_B = 4,3/1,87·10⁻³ = 2,30 kΩ   →  commerciale 2,2 kΩ

Verifica: I_B = 4,3/2200 = 1,95 mA  →  h_FE richiesto = 70/1,95 = 36 < 75  ✓ saturo
P_diss  = V_CEsat·I_C = 0,2 · 0,07 = 14 mW  (niente dissipatore)
```

> [!success] **`R_B = 2,2 kΩ` + BJT NPN (BC337 o 2N2222) + `diodo 1N4007 in antiparallelo alla
> bobina`**, catodo verso +12 V. Masse TTL e 12 V **in comune**.

> [!important] Il diodo di libera circolazione è la parte che Carli cerca
> La bobina è un'induttanza: all'interdizione la corrente non può annullarsi di colpo e genera
> `v = L·di/dt` che distrugge il transistor. Senza quel diodo il progetto è **incompleto** anche
> con tutto il resto giusto. «NON SVOLTO PER NULLA» — 0,00/1,00.

---

## Es. 5 — Condensatore di by-pass C_E

Amplificatore a emettitore comune · `R_E = 1 kΩ` · banda `50 Hz ÷ 8 kHz`

`R_E` stabilizza in continua ma controreaziona in alternata (`A_v ≈ −R_C/R_E`). `C_E` in
parallelo la cortocircuita in alternata. Condizione critica alla **f minima**, criterio
`X_CE ≤ R_E/10`:

```
C_E ≥ 10/(2π·f_min·R_E) = 10/(2π·50·1000) = 31,8 µF   →  commerciale 33 µF

Verifica a 50 Hz con 33 µF: X_CE = 1/(2π·50·33·10⁻⁶) = 96,5 Ω ≪ 1000 Ω  ✓
```

> [!success] **C_E ≥ 31,8 µF → C_E = 33 µF elettrolitico**, tensione di lavoro ≥ 2·V_E, positivo
> verso l'emettitore.
>
> *Col criterio minimo `f_min = 1/(2πR_E C_E)` verrebbe 3,18 µF: è la frequenza a cui
> `X_CE = R_E`, cioè dove il by-pass comincia appena — a 50 Hz saresti già a −3 dB. Per un
> progetto vale il criterio **×10**.*

> [!note] «NON SVOLTO PER NULLA» — 0,00/1,00. Una formula sola.

---

## Es. 6 — Verifica del funzionamento in saturazione

![[fusi-24-04-p7-es6-7.png]]
*Verifica 2, p. 7 — **es. 6** (verifica di saturazione) ed **es. 7** (punto di lavoro con R_E).*

`V_CC = 10 V` · `h_FE = 50` · `R_B = 5,2 kΩ` · `R_C = 0,33 kΩ` · `V_BE = 0,8 V` ·
`V_CEsat = 0,2 V` · base fissa, emettitore a massa

**La procedura in tre passi, scritta in rosso dal prof.:**

```
1) maglia d'ingresso        I_B      = (V_CC − V_BE)/R_B = 9,2/5200 = 1,77 mA
2) maglia d'uscita, V_CE = V_CEsat   I_C(sat) = (10 − 0,2)/330 = 29,7 mA
3) confronto                I_B necessaria = I_C(sat)/h_FE = 29,7/50 = 0,594 mA
                            I_B disponibile 1,77 mA > 0,594 mA  ✓
                            fattore di sovrapilotaggio = 1,77/0,594 ≈ 3
```

> [!success] **Il BJT è in saturazione** (overdrive ≈ 3): `V_CE = 0,2 V`, `I_C = 29,7 mA`,
> `I_B = 1,77 mA`.
> Controprova: in zona attiva sarebbe `I_C = 50·1,77 = 88,5 mA` → `V_CE = −19,2 V`, impossibile.
> È proprio l'assurdo che **dimostra** la saturazione.

> [!danger] Trappola
> Di nuovo `V_CC = R_B·I_B + R_C·I_C`, maglie mescolate. **Stesso errore dell'es. 2: 2,00 punti.**

---

## Es. 7 — Punto di lavoro con resistenza di emettitore

`V_CC = 20 V` · `V_BB = 10 V` · `R_C = 300 Ω` · `R_E = 200 Ω` · `R_B = 20 kΩ` · `h_FE = 100`

`R_E` sta in **entrambe** le maglie ed è percorsa da `I_E`, non da `I_B` né da `I_C`:

```
V_BB = R_B·I_B + V_BE + R_E·(h_FE + 1)·I_B
9,3  = I_B·(20 000 + 200·101) = 40 200·I_B     →   I_B = 231 µA

I_C  = 100·I_B = 23,1 mA        I_E = 101·I_B = 23,4 mA
V_E  = 200·23,37·10⁻³ = 4,67 V  V_RC = 300·23,13·10⁻³ = 6,94 V
V_CE = 20 − 6,94 − 4,67 = 8,39 V

Verifica: V_CE ≫ 0,2 V ✓ · I_C(sat) = 19,8/500 = 39,6 mA > 23,1 mA ✓
```

> [!success] **Q: V_CE = 8,39 V ; I_C = 23,1 mA** (`I_B = 231 µA`, `I_E = 23,4 mA`, `V_E = 4,67 V`)
> *Approssimando `I_E ≈ I_C` viene `V_CE = 8,38 V`: differenza < 1%, lecita ma va dichiarata.*

> [!danger] Trappola
> Ha scritto `V_CC = R_C·I_CO + I_E·R_E` **dimenticando V_CE**, che è proprio l'incognita, e si è
> fermato lì. *«perché non ha continuato lo svolgimento dell'esercizio?»*
> La maglia completa è `V_CC = R_C·I_C + V_CE + R_E·I_E`.

---

# Parte C — Verifica 3 · JFET e MOSFET
**29/05/2026, valutata 03/06 · 8 esercizi (JFET 1–5, MOSFET 6–8) · Fusi 3,00/10**

> [!abstract] Le leggi che servono per tutti e otto
> **JFET canale N** (`V_P < 0`, lavora a `V_GS` negativa):
> ```
> Shockley:    I_D = I_DSS·(1 − V_GS/V_P)²
> invertita:   V_GS = V_P·(1 − √(I_D/I_DSS))
> saturazione: V_DS ≥ V_GS − V_P
> ```
> **MOSFET enhancement canale N** (`V_t > 0`, lavora a `V_GS > V_t`):
> ```
> saturazione: I_D = K·(V_GS − V_t)²          se V_DS ≥ V_GS − V_t
> invertita:   V_GS = V_t + √(I_D/K)
> zona ohmica: I_D = K·[2(V_GS − V_t)·V_DS − V_DS²]   se V_DS < V_GS − V_t
> ```
> **Regola d'oro: `I_G = 0`.** Quindi nessuna caduta su `R_G`, `I_S = I_D`, e soprattutto
> **`R_G` non si calcola mai: si sceglie** (1 ÷ 10 MΩ).

## Es. 1 — Progetto dell'autopolarizzazione di un JFET

![[fusi-29-05-p1-es1.png]]
*Verifica 3, p. 1 — intestazione e **es. 1** (autopolarizzazione JFET).*

`V_DD = 12 V` · `I_DO = 8 mA` · `V_GSO = −1 V` · `V_DSO = 7 V` · incognite `R_D, R_S, R_G`

Gate a massa tramite `R_G` → `V_G = 0`; la `V_GS` negativa nasce dalla caduta su `R_S`:
`V_GS = 0 − R_S·I_D`.

```
R_S = −V_GSO/I_DO = 1/8·10⁻³ = 125 Ω
R_D = (V_DD − V_DSO − R_S·I_DO)/I_DO = (12 − 7 − 1)/8·10⁻³ = 500 Ω
R_G = si sceglie: 1 MΩ  (il prof. indica 5 MΩ)
```

> [!success] **R_S = 125 Ω · R_D = 500 Ω · R_G = 1 MΩ (scelta).**

> [!danger] Trappola — l'errore concettuale più grave della verifica
> Fusi ha scritto `R_G = V_GS/I_G` con `I_G = V_GS/(R_S + R_D) = −1,6 mA`, ottenendo 625 Ω.
> Due errori: **`I_G ≈ 0`** (giunzione gate-canale polarizzata inversamente, nanoampere), e
> `R_G` **non è in serie** a `R_S` e `R_D`. Il prof. ha cancellato tutto: **«si fissa: R_G = 5 MΩ»**.
> Lo stesso errore ritorna identico nell'es. 2.

---

## Es. 2 — Progetto con l'equazione di Shockley

![[fusi-29-05-p3-es2-3.png]]
*Verifica 3, p. 3 — **es. 2** (Shockley) ed **es. 3** (V_GG e V_DD).*

`V_DD = 18 V` · `I_DO = 5 mA` · `V_DSO = 10 V` · `I_DSS = 12 mA` · `V_P = −5 V`

> [!warning] Sul segno di V_P
> Il testo scrive `V_P = 5 V`, ma per un **JFET a canale N** il pinch-off è **negativo**:
> `V_P = −5 V`. Senza correggerlo Shockley dà risultati privi di senso.

Manca `V_GSO`: si ricava prima da Shockley invertita, poi si procede come nell'es. 1.

```
√(I_D/I_DSS) = √(5/12) = 0,6455
V_GS = V_P·(1 − 0,6455) = −5 · 0,3545 = −1,77 V
R_S  = −V_GS/I_D = 1,77/5·10⁻³ = 354,5 Ω
R_D  = (18 − 10 − 1,77)/5·10⁻³ = 6,23/0,005 = 1245 Ω
R_G  = si sceglie: 1 MΩ

Verifica saturazione: V_GS − V_P = −1,77 + 5 = 3,23 V ≤ V_DS = 10 V  ✓
```

> [!success] **V_GSO = −1,77 V · R_S ≈ 355 Ω (comm. 360) · R_D ≈ 1,25 kΩ (comm. 1,2 k) · R_G = 1 MΩ.**

> [!danger] Trappola
> Impostazione giusta (tre «OK» del prof.) ma aritmetica sbagliata dentro Shockley: da
> `−5·(1 − 0,6455)` gli è uscito prima −1,85, poi −4,9, poi **−24 V**, e quindi `R_S = 4,8 kΩ`.
> **Controllo di sanità: `V_GS` sta sempre fra `V_P` e 0.** Fuori da lì è certamente sbagliato.

---

## Es. 3 — Determinare V_GG e V_DD

`I_DO = 5 mA` · `V_DSO = 10 V` · `V_GSO = −2 V` · `R_D = 6 kΩ` · batteria di gate separata,
source a massa (niente `R_S`)

```
V_S = 0  →  V_GS = V_G  →  V_GG = 2 V, col morsetto POSITIVO verso massa
                            (gate negativo rispetto al source)
V_DD = R_D·I_DO + V_DSO = 6·10³·5·10⁻³ + 10 = 30 + 10 = 40 V
```

> [!success] **V_GG = 2 V (polarità che rende il gate negativo) · V_DD = 40 V.**

> [!note] «NON SVOLTO» — 0,00/1,00. Due somme.

---

## Es. 4 — Punto di lavoro e tensione di alimentazione

![[fusi-29-05-p5-es4-5.png]]
*Verifica 3, p. 5 — **es. 4** (punto di lavoro) ed **es. 5** (partitore JFET).*

`I_DSS = 12 mA` · `V_P = −4,5 V` · `V_DSO = 10 V` · `V_GSO = −2 V` · `R_D = 2,7 kΩ`

Qui `V_GS` è **dato** → Shockley in verso diretto.

```
V_GS/V_P = (−2)/(−4,5) = 0,4444
I_D = 12·10⁻³·(1 − 0,4444)² = 12·10⁻³·0,3086 = 3,70 mA

Verifica: V_GS − V_P = 2,5 V ≤ V_DS = 10 V  ✓  zona attiva
V_DD = V_DS + R_D·I_D = 10 + 2700·3,70·10⁻³ = 10 + 10,0 = 20 V
```

> [!success] **Q: V_GSO = −2 V ; I_DO = 3,70 mA ; V_DSO = 10 V · V_DD = 20 V.**
> `R_D·I_D = 10,0 V` esattamente metà di `V_DD`: l'esercizio è costruito così, è la conferma.

> [!note] «NON SVOLTO» — 0,00/1,00.

---

## Es. 5 — Progetto della polarizzazione a partitore di un JFET

`I_DO = 3,5 mA` · `V_GSO = −1,5 V` · `V_DSO = 11 V` · `V_DD = 25 V` · `R₁ + R₂ = 2 MΩ` ·
`R_D = 3 kΩ` · incognite `R_S, R₁, R₂`

Il gate **non** è a massa: sta a `V_G` positiva fissata dal partitore, e la `V_GS` negativa si
ottiene tenendo il **source più in alto del gate** (`V_GS = V_G − V_S`).

```
V_RD = R_D·I_DO = 3·10³·3,5·10⁻³ = 10,5 V
V_S  = V_DD − V_DSO − V_RD = 25 − 11 − 10,5 = 3,5 V
R_S  = V_S/I_DO = 3,5/3,5·10⁻³ = 1 kΩ
V_G  = V_GS + V_S = −1,5 + 3,5 = 2 V
R₂   = V_G·(R₁+R₂)/V_DD = 2·2·10⁶/25 = 160 kΩ      (verso massa)
R₁   = 2·10⁶ − 160·10³ = 1,84 MΩ                    (verso V_DD)

Verifica: V_G = 25·160k/2M = 2 V  ✓
```

> [!success] **R_S = 1 kΩ · R₂ = 160 kΩ · R₁ = 1,84 MΩ**, con `V_S = 3,5 V`, `V_G = 2 V`.
> `R₁ ∥ R₂ ≈ 147 kΩ` = impedenza d'ingresso, alta come serve a uno stadio a JFET.

> [!note] «NON SVOLTO» — 0,00/1,50. È l'esercizio da 1,50 punti più meccanico dei tre fascicoli.

---

## Es. 6 — MOSFET: determinare il punto di lavoro

![[fusi-29-05-p7-es6-7.png]]
*Verifica 3, p. 7 — **es. 6** ed **es. 7**, i due MOSFET, con le due `V_DD` diverse (vedi l'avviso nell'es. 7).*

`V_DD = 15 V` · `R₁ = 1,27 kΩ` · `R₂ = 825 kΩ` · `R_D = 1,8 kΩ` · `K = 0,6 mA/V²` · `V_t = 3 V`
· ipotesi del testo: **MOS saturo** · partitore sul gate, source a massa

Source a massa → `V_GS = V_G`, imposta dal partitore a vuoto (`I_G = 0`).
**Ma l'ipotesi va verificata alla fine** — ed è tutto il punto dell'esercizio.

```
V_GS = V_DD·R₂/(R₁+R₂) = 15 · 825/826,27 = 14,98 V
I_D  = K·(V_GS − V_t)² = 0,6·10⁻³·(11,98)² = 86,1 mA        ← in ipotesi di saturazione
V_DS = V_DD − R_D·I_D = 15 − 1800·0,086 = −140 V            ← IMPOSSIBILE

L'ipotesi è falsa: il MOS lavora in ZONA OHMICA. Si risolve il sistema

  I_D = K·[2(V_GS − V_t)·V_DS − V_DS²]   e   I_D = (V_DD − V_DS)/R_D

  (15 − V_DS)/1800 = 0,6·10⁻³·[2·11,98·V_DS − V_DS²]
  1,08·V_DS² − 26,88·V_DS + 15 = 0    →  Δ = 657,7 , √Δ = 25,64
  V_DS = (26,88 ± 25,64)/2,16  →  V_DS = 0,574 V   (l'altra, 24,3 V, è > V_DD: scartata)
  I_D  = (15 − 0,574)/1800 = 8,0 mA

Verifica: V_DS = 0,574 V < V_GS − V_t = 11,98 V  ✓  ohmica confermata
```

> [!success] **L'ipotesi «MOS saturo» NON è verificata: il MOSFET è in zona ohmica.**
> **Q reale: V_DS ≈ 0,57 V ; I_D ≈ 8,0 mA** (`V_GS = 14,98 V`). Si comporta da interruttore
> chiuso, `R_DSon ≈ 72 Ω`.

> [!warning] Il dato è probabilmente un refuso: `R₁ = 1,27 MΩ`, non kΩ
> *(verificato sulla scansione a 300 dpi: sul foglio c'è scritto proprio «1,27 KΩ»)*. Con 1,27 MΩ
> l'esercizio torna pulito:
> ```
> V_GS = 15·825/(1270 + 825) = 5,91 V
> I_D  = 0,6·10⁻³·(5,91 − 3)² = 5,07 mA
> V_DS = 15 − 1800·5,07·10⁻³ = 5,87 V
> Verifica: 5,87 ≥ V_GS − V_t = 2,91  ✓  MOS SATURO
> ```
> **All'esame:** svolgi coi dati letterali, accorgiti che l'ipotesi non regge, **scrivilo**, e
> aggiungi la soluzione coerente col refuso. Carli premia il controllo, non il numero.

> [!danger] Trappola
> Fusi ha scritto `I_D = 84,9 A` (ampere invece di milliampere) e ha usato
> `V_GS = V_t + √(I_D/R_D)`, cancellata dal prof. con «NON SERVE»: corrente diviso resistenza
> sotto radice è **dimensionalmente impossibile**. `V_GS` viene **solo** dal partitore.

---

## Es. 7 — Progetto della polarizzazione di un MOSFET (senza R_S)

`V_DD = 25 V` · `I_D = 3 mA` · `K = 0,3 mA/V²` · `V_t = 4 V` · `R₁ + R₂ = 10 MΩ` ·
partitore sul gate, source a massa · incognite `R_D, R₁, R₂`

`V_GS` è determinata dai dati; `V_DS` invece è **una scelta di progetto**, vincolata solo da
`V_DS ≥ V_GS − V_t`. Si prende `V_DS = V_DD/2`, che dà l'escursione di segnale più simmetrica.

```
V_GS = V_t + √(I_D/K) = 4 + √(3/0,3) = 4 + 3,162 = 7,16 V
Vincolo di saturazione: V_DS ≥ 7,16 − 4 = 3,16 V   →   si sceglie V_DS = V_DD/2 = 12,5 V
R_D  = (V_DD − V_DS)/I_D = 12,5/3·10⁻³ = 4,17 kΩ
R₂   = (V_GS/V_DD)·(R₁+R₂) = (7,16/25)·10·10⁶ = 2,86 MΩ     (verso massa)
R₁   = 10·10⁶ − 2,86·10⁶ = 7,14 MΩ                           (verso V_DD)

Verifica: V_G = 25·2,86/10 = 7,16 V ✓ · I_D = 0,3·10⁻³·(3,162)² = 3,0 mA ✓ · 12,5 ≥ 3,16 ✓
```

> [!success] **R_D ≈ 4,17 kΩ (comm. 3,9 kΩ) · R₂ ≈ 2,86 MΩ · R₁ ≈ 7,14 MΩ**, con `V_GS = 7,16 V`,
> `V_DS = 12,5 V` (scelta di progetto).
> *`V_DS` diversa → risultati diversi ma ugualmente validi, purché resti `≥ 3,16 V` e tu dichiari
> la scelta. Solo `V_GS = 7,16 V` è obbligata dai dati.*

> [!warning] Attenzione al dato: `V_DD = 25 V`, non 15 V
> Sul foglio Fusi ha lavorato con 15 V, e con 15 V la vecchia versione di
> [[06 - Soluzioni complete verifiche FUSI]] dava `R_D = 2 kΩ`, `R₂ = 4,78 MΩ`, `R₁ = 5,22 MΩ`.
> Ricontrollata la scansione a 300 dpi: il testo dell'es. 7 dice **25 V** (i 15 V sono la `V_DD`
> dell'es. 6, subito sopra sulla stessa pagina). Le due righe, ritagliate dalla stessa pagina:
>
> ![[fusi-29-05-vdd-es6-300dpi.png]]
> *Es. 6 — l'«1» è un tratto dritto, senza base.*
>
> ![[fusi-29-05-vdd-es7-300dpi.png]]
> *Es. 7 — il «2» ha il ricciolo in alto e la base orizzontale.*

> [!danger] Trappola
> `R_D` a parte, Fusi ha scritto `V_GS = V_t + √(I_D/R_D) = 4,1 V` — **la stessa formula
> dimensionalmente impossibile dell'es. 6**: sotto radice va `I_D/K`, non `I_D/R_D`.
> Il prof.: **«relazione errata»**, e ha ricalcolato lui `V_GS = √(I_D/K) + V_t = 7,16 V`.

---

## Es. 8 — Progetto della polarizzazione di un MOSFET con R_S

![[fusi-29-05-p9-es8.png]]
*Verifica 3, p. 9 — **es. 8**, MOSFET con R_S.*

`I_DO = 8 mA` · `V_GSO = 6 V` · `V_DSO = 10 V` · `V_DD = 15 V` · `V_S = 3 V` · `R₁ + R₂ = 2 MΩ`
· incognite `R_D, R_S, R₁, R₂`

Con `R_S` cambiano **due cose**, ed entrambe sono le trappole: la maglia d'uscita ha **tre**
cadute, e il gate sta a `V_G = V_GS + V_S`, non a `V_GS`.

```
R_S = V_S/I_DO = 3/8·10⁻³ = 375 Ω
R_D = (V_DD − V_DSO − V_S)/I_DO = (15 − 10 − 3)/8·10⁻³ = 250 Ω
V_G = V_GS + V_S = 6 + 3 = 9 V
R₂  = (V_G/V_DD)·(R₁+R₂) = (9/15)·2·10⁶ = 1,2 MΩ     (verso massa)
R₁  = 2·10⁶ − 1,2·10⁶ = 800 kΩ                        (verso V_DD)

Verifica: V_GS = 9 − 3 = 6 V ✓ · maglia: 250·0,008 + 10 + 3 = 15 V = V_DD ✓
```

> [!success] **R_S = 375 Ω · R_D = 250 Ω · R₂ = 1,2 MΩ · R₁ = 800 kΩ**
> Commerciali: 390 Ω · 240 Ω · 1,2 MΩ · 820 kΩ.

> [!danger] Trappola — l'unico «ERRATO» pieno della verifica
> 1. `R_D = (15−10)/8m = 625 Ω`: **V_S dimenticata**. Il prof. ha aggiunto in rosso `− V_S`.
> 2. `R₂` calcolata con `V_R2 = 6 V` invece di 9 V: **ha usato V_GS al posto di V_G**. Il prof.
>    ha aggiunto `+ V_S`, scrivendo `V_R2 = V_GS + V_S`.
>
> Ha anche applicato formule da partitore fra `R_D` e `R_S`, che **non sono in serie fra loro**:
> in mezzo c'è il transistor. Vale sempre `I_S = I_D` e `V_S = R_S·I_D`.

---

# Parte D — Diodi · le risposte per l'orale

Nessuna delle tre verifiche FUSI tocca i diodi: sono **materia d'orale**, dalla scheda
«Verifica di elettronica» di Carli (Mirandola Vol. 2, cap. 5, pp. 192–224). Qui le **D1–D23**
in forma condensata; la versione distesa da leggere ad alta voce è [[diodi-risposte]].

**Indice** — D1 struttura · D2 simbolo · D3 polarizzazione · D4 diretta · D5 inversa ·
D6 versi convenzionali · D6★ tensione di soglia · D7 rappresentazione ai morsetti ·
D8 curva e zone · D9 grandezze · D10 linearità · D11 Shockley · D12 perché i modelli ·
D13 i tre modelli · D14 raddrizzatore · D15 semionda e onda intera · D16 limitatore ·
D17 bassa soglia · D18 serie e antiparallelo · D19 schemi · D20 Zener · D21 valanga e tunnel ·
D22 stabilizzatore · D23 regolatore Zener

## Prima parte · D1–D12

### D1 — Struttura del diodo a semiconduttore

![[diodi-fig-01.svg]]
*Fig. 1 — Struttura interna del diodo a giunzione.*

Componente **a due terminali**, **un unico cristallo** di silicio (raro il germanio) drogato in
modo **non uniforme**:
- metà con impurità **trivalenti** (accettori: boro, gallio, indio) → **regione P**, maggioritari
  le **lacune**;
- metà con impurità **pentavalenti** (donatori: fosforo, arsenico, antimonio) → **regione N**,
  maggioritari gli **elettroni**.

La superficie di separazione è la **giunzione PN** — non due pezzi incollati, ma un reticolo
continuo: solo così funziona.

**Cosa succede appena formata:** per la differenza di concentrazione gli elettroni della N
**diffondono** verso la P e le lacune viceversa, ricombinandosi. Restano scoperti gli **ioni
fissi** (negativi in P, positivi in N) → si forma la **regione di svuotamento** (o di carica
spaziale, o di deplezione), priva di cariche mobili, sede di un **campo elettrico interno** da N
verso P, cui corrisponde una **barriera di potenziale** $V_0 \approx 0{,}6 \div 0{,}7$ V nel
silicio ($0{,}2 \div 0{,}3$ V nel germanio). La barriera si oppone a un'ulteriore diffusione:
all'equilibrio, senza tensioni esterne, **la corrente complessiva è nulla**.

I terminali sono saldati con **contatti ohmici** (non raddrizzanti): **anodo (A)** sulla P,
**catodo (K)** sulla N. Sul contenitore reale il catodo è marcato da un **anello**.

### D2 — Simbolo circuitale

![[diodi-fig-02.svg]]
*Fig. 2 — Simbolo circuitale del diodo.*

**Triangolo pieno** = anodo (regione P) · **barretta trasversale** al vertice = catodo (regione N).
Il simbolo è **mnemonico**: il triangolo è una **freccia** e indica il verso in cui la corrente
convenzionale può passare (**da A a K**); la barretta è una **parete** che sbarra il verso opposto.
Il diodo è quindi **polarizzato**: invertire anodo e catodo cambia completamente il circuito.

### D3 — Definizione di polarizzazione della giunzione PN

**Polarizzare significa applicare dall'esterno una tensione continua ai terminali**, alterando
l'equilibrio della giunzione isolata. La tensione esterna si sovrappone a $V_0$ e, secondo il
segno, la **abbassa** o la **innalza**, cambiando la larghezza della regione di svuotamento e la
corrente. Due modi, con comportamenti opposti: **diretta** (potenziale maggiore sulla P) e
**inversa** (potenziale maggiore sulla N). È ciò che stabilisce il **punto di lavoro** sulla curva.

### D4 — Polarizzazione diretta

![[diodi-fig-03.svg]]
*Fig. 3 — Le due polarizzazioni a confronto.*

Generatore col **+ sull'anodo (P)** e **− sul catodo (N)**: $V_A > V_K$, quindi $V_D > 0$.
- il campo esterno è **opposto** a quello interno → la **barriera si abbassa** ($V_0 - V$);
- la **regione di svuotamento si restringe**;
- i **maggioritari** attraversano la giunzione → **corrente diretta $I_D$ elevata** (mA ÷ A).

Sotto la **soglia $V_\gamma$** ($\approx 0{,}7$ V nel silicio) la corrente è trascurabile; oltre
$V_\gamma$ cresce **esponenzialmente** mentre $V_D$ resta inchiodata attorno a 0,7 V: il diodo è
**ON**, quasi un **interruttore chiuso**.

> [!warning] In conduzione il diodo **non limita la corrente**: serve **sempre una resistenza R
> in serie**, altrimenti si distrugge per effetto Joule.

### D5 — Polarizzazione inversa

Generatore col **+ sul catodo (N)** e **− sull'anodo (P)**: $V_A < V_K$, quindi $V_D < 0$.
- campo esterno **concorde** con quello interno → la **barriera si innalza** ($V_0 + V$);
- la **regione di svuotamento si allarga**;
- i maggioritari **non passano più**.

Resta la **corrente inversa di saturazione $I_S$**, dovuta ai **portatori minoritari** generati
termicamente: ordine dei **nA** (Si) o µA (Ge), **indipendente dalla tensione inversa** ma
**fortemente dipendente dalla temperatura** (raddoppia ogni ≈10 °C).

Il diodo è **OFF**, un **interruttore aperto** — ma solo fino alla **tensione di breakdown
$V_{BR}$**, oltre la quale la corrente inversa cresce bruscamente e, se non limitata, distrugge
il componente.

### D6 — Versi convenzionali di corrente e tensione

![[diodi-fig-04.svg]]
*Fig. 4 — Versi convenzionali positivi sul simbolo.*

Si usa la **convenzione degli utilizzatori** (il diodo è passivo): la corrente entra dal morsetto
a potenziale maggiore.
- **$I_D$** positiva quando **entra dall'anodo ed esce dal catodo** (verso del triangolo).
- **$V_D$** positiva col **+ sull'anodo**: $V_D = V_A - V_K$.

Il segno diventa così coerente con lo stato: **diretta** → $V_D>0, I_D>0$ → **I quadrante**;
**inversa** → $V_D<0, I_D<0$ (pari a $-I_S$) → **III quadrante**.

> [!tip] Se dai calcoli esce $I_D$ **negativa** dove avevi ipotizzato conduzione, **l'ipotesi era
> sbagliata**: il diodo è interdetto.

### D6★ — Che cosa rappresenta la tensione di soglia

La **tensione di soglia $V_\gamma$** (di ginocchio, di *cut-in*, di accensione) è il **valore di
tensione diretta sotto il quale la corrente è trascurabile e oltre il quale il diodo entra in
piena conduzione**.
- **Fisicamente**: la tensione necessaria ad **abbattere la barriera di potenziale**; dipende dal
  **materiale**.
- **Graficamente**: la posizione del **ginocchio** della curva caratteristica.
- **Circuitalmente**: il generatore costante dei **modelli B e A**, cioè la **caduta fissa** ai
  capi del diodo in conduzione.

| Materiale / tipo | $V_\gamma$ tipica |
|---|---|
| Germanio | 0,2 ÷ 0,3 V |
| Silicio | 0,6 ÷ 0,7 V |
| Schottky | 0,2 ÷ 0,4 V |
| LED (rosso → blu) | 1,6 ÷ 3,4 V |

### D7 — Con quale rappresentazione grafica si descrive il funzionamento ai morsetti

Con la **curva caratteristica tensione–corrente** (caratteristica **statica** o **V–I**), cioè il
grafico di $I_D = f(V_D)$ sul piano cartesiano, $V_D$ in ascissa e $I_D$ in ordinata.

Il vantaggio: descrive **completamente il comportamento esterno** senza dover sapere che cosa
accade dentro la giunzione — è il **modello a scatola nera**. Si ricava sperimentalmente punto per
punto o si legge sul **data sheet**, ed è lo strumento su cui si esegue l'**analisi con la retta di
carico** per trovare il punto di lavoro Q.

### D8 — Curva caratteristica: zona diretta e zona inversa

![[diodi-fig-05.svg]]
*Fig. 5 — Curva caratteristica: zona diretta, zona inversa, breakdown.*

- **Diretta — I quadrante** ($V_D>0$, $I_D>0$): fra 0 e $V_\gamma$ la corrente è trascurabile; al
  **ginocchio** la curva si alza e diventa quasi **verticale**. Il diodo **conduce**.
- **Inversa — III quadrante** ($V_D<0$, $I_D<0$): curva **orizzontale**, schiacciata sull'asse, a
  $-I_S$ costante e minuscola. Il diodo è **interdetto**.
- **Breakdown** — a $-V_{BR}$ la curva **precipita**: la corrente inversa cresce bruscamente a
  tensione quasi costante.

> [!note] Nei grafici reali le **scale dei due semiassi sono diverse** (mA e frazioni di volt in
> diretta; nA/µA e decine o centinaia di volt in inversa), altrimenti il ramo inverso sarebbe
> indistinguibile dall'asse.

### D9 — Descrizione della curva e significato delle grandezze

| Grandezza | Nome | Significato | Valori tipici (Si) |
|---|---|---|---|
| $V_D$ | tensione ai morsetti | $V_A - V_K$; ascissa | — |
| $I_D$ | corrente nel diodo | da A a K; ordinata | — |
| $V_\gamma$ | tensione di soglia | oltre la quale entra in piena conduzione | 0,6 ÷ 0,7 V (Ge 0,2 ÷ 0,3) |
| $I_S$ | corrente inversa di saturazione | dei minoritari; costante con V, raddoppia ogni ≈10 °C | nA ÷ µA |
| $V_{BR}$ | tensione di breakdown | oltre la quale la corrente inversa esplode | 50 ÷ 1000 V |
| $r_D$ | resistenza differenziale | $r_D = \Delta V_D/\Delta I_D$, inverso della pendenza in Q | 1 ÷ 20 Ω |
| $Q$ | punto di lavoro | coppia $(V_{DQ}, I_{DQ})$ effettiva nel circuito | — |

**Tratto per tratto:** $0<V_D<V_\gamma$ barriera non ancora abbattuta, corrente trascurabile ·
$V_D \approx V_\gamma$ **ginocchio**, transizione rapida di pendenza · $V_D > V_\gamma$ crescita
**esponenziale**, $V_D$ inchiodata a ≈0,7 V · $-V_{BR}<V_D<0$ corrente costante $-I_S$ ·
$V_D \le -V_{BR}$ **breakdown**: distruttivo per un raddrizzatore, **zona di lavoro voluta** per
lo Zener.

### D10 — Il diodo è lineare?

**No: è NON lineare**, e per di più **unidirezionale** (polarizzato). Un bipolo è lineare se la
caratteristica è una **retta per l'origine** ($V = RI$ con $R$ costante). Qui non accade:

1. **La caratteristica è esponenziale**, non una retta: $I_D = I_S(e^{V_D/(\eta V_T)} - 1)$. Il
   rapporto $V_D/I_D$ **cambia punto per punto** → non esiste «la resistenza del diodo», solo
   quella statica ($V_{DQ}/I_{DQ}$) o differenziale ($\Delta V/\Delta I$), valide **attorno a un
   preciso Q**.
2. **Il comportamento dipende dal verso**: +5 V danno mA, −5 V danno nA. **Non è simmetrico.**
3. **Non valgono omogeneità e sovrapposizione** → **non si possono applicare i teoremi delle reti
   lineari** (sovrapposizione, Thévenin, Norton) ai circuiti con diodi.

È proprio la non linearità a renderlo utile (raddrizzare, limitare, rivelare, stabilizzare). Il
prezzo è la difficoltà di calcolo, che si aggira con la **retta di carico** o con i **modelli
lineari a tratti** (D12, D13).

### D11 — Espressione matematica a destra del breakdown (Shockley)

$$I_D = I_S\left(e^{\frac{V_D}{\eta\,V_T}} - 1\right) \qquad V_T = \frac{kT}{q} \approx 26\ \text{mV a } T = 300\ \text{K}$$

- $I_D$ — corrente nel diodo [A], positiva se entrante nell'anodo.
- $V_D$ — tensione ai morsetti [V], positiva in diretta.
- $I_S$ — **corrente inversa di saturazione** [A]: dipende da materiale, drogaggio, area della
  giunzione e fortemente dalla temperatura; nA nel silicio.
- $\eta$ (o $n$) — **coefficiente di emissione**, numero puro **fra 1 e 2**; ≈2 nel silicio a
  basse correnti, → 1 ad alte correnti e nel germanio.
- $V_T$ — **tensione termica** [V], $kT/q$, ≈**26 mV** a temperatura ambiente.
- $k = 1{,}38\cdot10^{-23}$ J/K · $T$ temperatura **assoluta** [K] · $q = 1{,}602\cdot10^{-19}$ C.

**Verifica nei due casi:** in diretta con $V_D \gg V_T$ l'esponenziale domina →
$I_D \approx I_S e^{V_D/(\eta V_T)}$ (crescita esponenziale); in inversa con $|V_D| \gg V_T$
l'esponenziale → 0 e resta $I_D \approx -I_S$ (costante — da qui «di saturazione»).

> [!note] Perché «a destra del breakdown»
> Shockley descrive solo la **diffusione** dei portatori e **non contiene termini per valanga o
> effetto tunnel**: per $V_D \le -V_{BR}$ continuerebbe a prevedere $-I_S$, in contrasto totale
> con la realtà.

### D12 — Perché si usano modelli equivalenti approssimati

1. **Difficoltà matematica**: Shockley è **trascendente**; nelle equazioni di Kirchhoff dà un
   sistema **non risolvibile algebricamente** (l'incognita è dentro e fuori l'esponenziale).
2. **Impossibile usare i teoremi delle reti lineari** finché c'è un elemento non lineare;
   **linearizzando a tratti** tornano tutti applicabili.
3. **Parametri incerti**: $I_S$ e $\eta$ variano con temperatura, invecchiamento e **da esemplare
   a esemplare**. Un calcolo «esatto» su dati incerti è precisione finta.
4. **Di solito serve solo sapere se il diodo conduce o no** (raddrizzatore, limitatore, logica a
   diodi): la forma esatta del ginocchio è irrilevante.
5. **L'errore è accettabile**: con tensioni ≫ $V_\gamma$ (12 V contro 0,7) e resistenze ≫ $r_D$
   (kΩ contro pochi Ω) si sbaglia di pochi punti percentuali, dentro le tolleranze dei componenti.

I modelli **sostituiscono al diodo componenti lineari ideali** (interruttore, generatore,
resistore): calcolo rapido, a mano, abbastanza accurato.

## Seconda parte · D13–D23

### D13 — I tre modelli equivalenti approssimati (A, B, C)

![[diodi-fig-06.svg]]
*Fig. 6 — I tre modelli e le caratteristiche linearizzate.*

**In polarizzazione inversa tutti e tre coincidono**: interruttore **aperto** (si trascura $I_S$).

| Modello | Conduzione | Interdizione | $V_D$ in conduzione | Precisione |
|---|---|---|---|---|
| **A** | interruttore + $V_\gamma$ + $r_D$ | aperto | $V_\gamma + r_D I_D$ | alta |
| **B** | interruttore + $V_\gamma$ | aperto | $V_\gamma \approx 0{,}7$ V | media — **la più usata** |
| **C** | interruttore | aperto | 0 V | bassa (qualitativa) |

- **A** — il più completo: caratteristica = **semiretta inclinata** da $V_\gamma$ con pendenza
  $1/r_D$ ($r_D$ tipicamente 1÷20 Ω). Riproduce meglio il diodo reale.
- **B** — si trascura $r_D$: $V_D = V_\gamma$ costante, caratteristica = **semiretta verticale**.
  Miglior compromesso, quello normalmente adottato.
- **C** — diodo **ideale**: puro interruttore, corto in diretta ($V_D=0$), aperto in inversa. La
  caratteristica **coincide coi due semiassi**. Per l'analisi qualitativa rapida.

**Da cosa dipende la scelta:**
- **rapporto fra le tensioni in gioco e $V_\gamma$** — con 24 V i 0,7 V sono < 3% → basta **C**;
  con segnali di pochi volt serve almeno **B**;
- **rapporto fra $r_D$ e le resistenze del circuito** — resistenze in kΩ → $r_D$ trascurabile
  (**B**); circuiti a bassa impedenza e forti correnti → serve **A**;
- **precisione richiesta e scopo** — dimensionamento di massima vs. calcolo di potenza dissipata;
- **dati disponibili** — se il data sheet non dà $r_D$, il modello A è **falsa precisione**.

> [!tip] Si sceglie sempre il **modello più semplice che garantisce l'accuratezza richiesta**.

### D14 — Definizione e importanza del raddrizzatore

**Definizione.** Circuito che, sfruttando l'unidirezionalità del diodo, **converte una tensione
alternata** (bidirezionale, valor medio nullo) **in una tensione unidirezionale**, di un solo
segno, pulsante, con **valor medio diverso da zero**. Da solo **non produce ancora la continua**:
servono filtro e stabilizzatore.

**Importanza.**
- È il **primo stadio attivo di ogni alimentatore in continua**:
  **trasformatore → raddrizzatore → filtro → stabilizzatore → carico**.
- Risolve il problema di fondo: l'energia si **distribuisce in alternata** (facile da trasformare
  e trasportare) ma **l'elettronica funziona in continua**. È il ponte fra i due mondi.
- Presente in **ogni apparecchio alimentato da rete** (alimentatori PC, caricabatterie, TV).
- Anche fuori dall'alimentazione: **rivelatore d'inviluppo** AM, misure di valor medio,
  saldatrici, processi galvanici.

### D15 — Raddrizzatori a singola e a doppia semionda

![[diodi-fig-07.svg]]
*Fig. 7 — Singola semionda e ponte di Graetz, con le forme d'onda.*

**1) Singola semionda** — un solo diodo in serie al carico $R_L$.
- semionda **positiva**: diodo in conduzione, $v_o = v_i - V_\gamma$;
- semionda **negativa**: diodo interdetto, $v_o = 0$; tutta la tensione d'ingresso cade sul diodo
  → deve sopportare un **PIV** (*Peak Inverse Voltage*) pari a $V_{max}$.

$$V_{o,med} = \frac{V_{max}}{\pi} \approx 0{,}318\,V_{max} \qquad f_{ripple} = f_{rete} = 50\ \text{Hz}$$

Semplice ed economico, ma metà del tempo l'uscita è nulla: valor medio basso, ripple grande alla
frequenza di rete (filtro con condensatori enormi), trasformatore sfruttato male.

**2) Doppia semionda (onda intera)** — due realizzazioni:
- **ponte di Graetz**: **quattro diodi** a rombo; in ogni semionda conducono **due diodi opposti**
  in serie e la corrente attraversa il carico **sempre nello stesso verso**. Caduta $2V_\gamma
  \approx 1{,}4$ V. Non serve il trasformatore a presa centrale.
- **con presa centrale**: due diodi, secondario a presa centrale a massa. Caduta di un solo
  $V_\gamma$, ma serve un trasformatore speciale e ogni diodo sopporta tensione inversa doppia.

$$V_{o,med} = \frac{2V_{max}}{\pi} \approx 0{,}637\,V_{max} \qquad f_{ripple} = 2f_{rete} = 100\ \text{Hz}$$

**Vantaggi:** valor medio doppio, miglior rendimento e sfruttamento del trasformatore, ripple a
frequenza doppia e ampiezza minore → **filtraggio molto più facile**. È la soluzione praticamente
sempre adottata.

### D16 — Definizione di limitatore e suoi utilizzi

**Definizione.** Il **limitatore** (*clipper*) **impedisce alla tensione d'uscita di superare uno
o due livelli di soglia prefissati**, tagliando ciò che eccede e lasciando **inalterata** la parte
di segnale entro le soglie. Può essere **unilaterale** o **bilaterale/simmetrico**.

**Utilizzi.**
- **Protezione degli ingressi** (strumenti, amplificatori, porte logiche, microcontrollori) da
  **sovratensioni** — l'impiego più importante.
- **Sagomatura** (*wave shaping*): tagliando le creste di una sinusoide grande si ottiene una
  forma **quasi rettangolare** (clock, sincronismi).
- **Eliminazione di disturbi impulsivi** (spike) oltre una certa ampiezza.
- **Selezione di ampiezza** · **adattamento della dinamica** al fondo scala di un ADC.
- **Protezione ESD** nei circuiti integrati (diodi di clamp su ogni pin).

### D17 — Limitatori a bassa soglia

![[diodi-fig-08.svg]]
*Fig. 8 — Limitatore a bassa soglia con un diodo verso massa, e forme d'onda.*

Sono i limitatori in cui **la soglia è fissata solo da $V_\gamma$**, senza generatori di
polarizzazione ausiliari: soglia ≈ **0,7 V** (o un suo multiplo con più diodi in serie).

**Struttura:** una **R in serie** fra ingresso e uscita (limita la corrente nel diodo e assorbe
l'eccesso di tensione) e un **diodo in parallelo all'uscita, verso massa**.

**Funzionamento:**
- **$v_i < V_\gamma$** → diodo interdetto, nessuna corrente, nessuna caduta su R → $v_o = v_i$,
  segnale **inalterato**;
- **$v_i$ oltre $V_\gamma$** → diodo in conduzione, si comporta da generatore costante: l'uscita
  resta **clampata a $v_o \approx V_\gamma \approx 0{,}7$ V** comunque cresca l'ingresso; tutta
  l'eccedenza $(v_i - V_\gamma)$ cade su R, percorsa da $I = (v_i - V_\gamma)/R$;
- **semionde negative** → diodo interdetto, l'uscita segue l'ingresso.

Con un solo diodo la limitazione è **unilaterale** (creste positive tosate a un livello piatto,
negative intatte); invertendo il diodo si limitano le negative.

### D18 — Scopo di più diodi in serie o in antiparallelo

**In serie — alzare la soglia.** I diodi in serie sono percorsi dalla stessa corrente e le cadute
si **sommano**: con **n diodi** la conduzione parte a $n \cdot V_\gamma$. Si ottiene il livello di
taglio voluto **senza generatori di polarizzazione ausiliari**.

| Diodi in serie | Soglia |
|---|---|
| 1 | ≈ 0,7 V |
| 2 | ≈ 1,4 V |
| 3 | ≈ 2,1 V |
| n | ≈ n · 0,7 V |

Svantaggio: soglia **quantizzata** a multipli di 0,7 V, niente valori intermedi.

**In antiparallelo — limitazione simmetrica.** Due diodi in parallelo ma con **verso opposto**
(anodo dell'uno sul catodo dell'altro): per ogni polarità ce n'è sempre uno in diretta → taglio
**bilaterale** a $\pm V_\gamma$.

Le due tecniche si **combinano**: due *gruppi* di n diodi in serie, in antiparallelo, danno
$\pm n V_\gamma$ (es. ±1,4 V con due diodi per ramo).

### D19 — Schemi dei limitatori

![[diodi-fig-09.svg]]
*Fig. 9 — Limitatore con diodi in serie (soglia più alta) e con diodi in antiparallelo (taglio simmetrico).*

![[diodi-fig-10.svg]]
*Fig. 10 — Sinusoide di ampiezza ≫ soglia su limitatore in antiparallelo: sagomatura in onda quasi quadra.*

### D20 — Diodo Zener: simbolo, curva, zona di lavoro, impieghi

![[diodi-fig-11.svg]]
*Fig. 11 — Simbolo dello Zener, polarizzazione di lavoro e curva caratteristica.*

**Simbolo:** come il diodo normale ma con la **barretta del catodo ripiegata alle due estremità**
a ricordare una **Z**.

**Curva:**
- **in diretta** si comporta **esattamente come un diodo normale** (conduce oltre 0,7 V), ma
  **non viene mai usato così**;
- **in inversa** ha un **ginocchio molto netto** alla tensione $V_Z$, oltre il quale la
  caratteristica è **quasi verticale**.

**Zona di funzionamento: il breakdown inverso** (III quadrante, oltre il ginocchio). Mentre in un
diodo comune il breakdown è distruttivo, lo Zener è **costruito apposta** (drogaggi elevati,
dissipazione adeguata) per **lavorarci stabilmente**, purché la corrente sia **limitata
dall'esterno**. Lì la tensione ai suoi capi **resta praticamente costante a $V_Z$** anche se la
corrente varia moltissimo, entro due limiti:
- $I_{ZK}$ (*knee*) — corrente **minima** per stare oltre il ginocchio: sotto, esce dalla
  regolazione;
- $I_{ZM} = P_{Zmax}/V_Z$ — corrente **massima**, oltre la quale si distrugge per
  surriscaldamento.

La pendenza residua è la **resistenza differenziale $r_Z$** (pochi ohm): $\Delta V_Z = r_Z \Delta
I_Z$. Più piccola è $r_Z$, migliore è lo Zener.

**Impieghi:** **stabilizzatore/regolatore di tensione** (principale, D22–D23) · **riferimento di
tensione** di precisione · **limitatore e protezione da sovratensioni** (due in antiparallelo →
taglio simmetrico a valori scelti) · **traslatore di livello** (sposta il continuo di $V_Z$) ·
**sagomatura** a soglie alte (gli Zener coprono da ≈2,4 V a oltre 100 V, i diodi comuni solo
multipli di 0,7 V).

### D21 — I due meccanismi di conduzione dal catodo all'anodo

Conduzione **dal catodo all'anodo** = conduzione **inversa**, cioè nella **zona di breakdown**.
Due meccanismi fisici distinti:

**1) Effetto valanga** (*avalanche breakdown*). Il campo elettrico intenso **accelera** i pochi
portatori minoritari, che urtando gli atomi del reticolo **rompono legami covalenti** e liberano
nuove **coppie elettrone–lacuna** (ionizzazione per urto); queste ne liberano altre, in un
**processo a catena**.
- prevale nei diodi a **drogaggio basso** (regione di svuotamento larga, spazio per accelerare);
- dominante per $V_{BR}$ **oltre ≈ 6 V**;
- **coefficiente di temperatura positivo**: $V_{BR}$ **aumenta** con la temperatura.

**2) Effetto Zener / tunnel** (*Zener breakdown*). Con **drogaggi molto pesanti** la regione di
svuotamento è **sottilissima** e già a tensioni modeste il campo supera $10^8$ V/m: **strappa
direttamente gli elettroni dai legami covalenti**, che passano per **effetto tunnel** dalla banda
di valenza della P alla banda di conduzione della N, senza urti né accelerazione.
- prevale nei diodi **fortemente drogati**;
- dominante per $V_{BR}$ **sotto ≈ 5 V**;
- **coefficiente di temperatura negativo**: $V_Z$ **diminuisce** con la temperatura.

> [!important]
> - **Fra 5 e 6 V i due meccanismi coesistono** e i coefficienti di temperatura, di segno opposto,
>   **si compensano**: gli Zener attorno a **5,6 V** sono i più **stabili in temperatura** e si
>   preferiscono come riferimenti di precisione.
> - Il fenomeno è **reversibile e non distruttivo** di per sé: il diodo si rovina solo se la
>   **potenza dissipata** supera il massimo, cioè se la corrente non è limitata dall'esterno.
> - Nell'uso corrente si chiamano «Zener» tutti i diodi che lavorano in quella zona, anche quando
>   il meccanismo reale è la valanga.

### D22 — Definizione di stabilizzatore (regolatore) di tensione

**Definizione.** Circuito posto fra sorgente e carico che **mantiene la tensione d'uscita costante
al valore voluto**, indipendentemente dalle grandezze che tenderebbero a farla variare:
- **variazioni della tensione d'ingresso** (fluttuazioni di rete, ripple residuo) →
  **regolazione di linea** $S_V = \Delta V_o/\Delta V_i$;
- **variazioni della corrente di carico** → **regolazione di carico** $R_o = \Delta V_o/\Delta I_L$;
- **variazioni di temperatura** → coefficiente termico $S_T = \Delta V_o/\Delta T$.

**Idealmente tutti e tre valgono zero.**

**Collocazione:** è l'**ultimo stadio** dell'alimentatore — *trasformatore → raddrizzatore →
filtro → **stabilizzatore** → carico*. Raddrizzatore e filtro da soli lasciano ripple e dipendenza
dal carico; è lo stabilizzatore a produrre una **vera continua**. Indispensabile perché integrati
e microprocessori richiedono tolleranze strettissime.

### D23 — Schema più semplice di regolatore, con le relazioni

![[diodi-fig-12.svg]]
*Fig. 12 — Regolatore di tensione a diodo Zener.*

**Struttura:** due soli componenti — una **resistenza di zavorra $R_S$ in serie** e uno **Zener in
parallelo al carico**, polarizzato inversamente (catodo al positivo). È un **regolatore parallelo**
(*shunt*).

$$V_o = V_Z \qquad I_S = \frac{V_i - V_Z}{R_S} \qquad I_L = \frac{V_Z}{R_L} \qquad I_Z = I_S - I_L$$

$$V_i = R_S I_S + V_Z \qquad P_Z = V_Z I_Z \le P_{Zmax} \qquad I_{ZK} \le I_Z \le I_{ZM} = \frac{P_{Zmax}}{V_Z}$$

Da $I_{ZK} \le I_Z \le I_{ZM}$ si ricava l'intervallo di $R_S$, nei due casi peggiori:

$$R_{S,max} = \frac{V_{i,min} - V_Z}{I_{ZK} + I_{L,max}} \qquad R_{S,min} = \frac{V_{i,max} - V_Z}{I_{ZM} + I_{L,min}}$$

**Perché stabilizza.** Lo Zener, nel tratto quasi verticale, **impone la propria $V_Z$** al nodo
d'uscita:
- **se aumenta $V_i$** → aumenta $I_S$, ma l'uscita è bloccata a $V_Z$ quindi $I_L$ non cambia:
  **tutto l'incremento va nello Zener**; cresce la caduta su $R_S$, che **assorbe l'eccesso**;
- **se aumenta $I_L$** (cioè cala $R_L$) → lo Zener **cede corrente al carico**, $I_Z$ diminuisce
  esattamente di quanto $I_L$ aumenta; $I_S$ resta invariata, la caduta su $R_S$ pure, l'uscita
  resta $V_Z$.

Lo Zener è un **serbatoio di corrente in parallelo al carico**: assorbe ciò che al carico non
serve, restituisce ciò che gli occorre in più.

**Limiti:** la stabilizzazione non è perfetta perché $r_Z \ne 0$ ($\Delta V_o = r_Z \Delta I_Z$);
il **rendimento è basso** (la potenza su $R_S$ e sullo Zener c'è sempre, anche a vuoto); va bene
solo per **correnti di carico modeste e poco variabili**. Per prestazioni migliori: regolatori
**serie a transistor** con controreazione, o **integrati 78xx/79xx** — che comunque usano uno
Zener interno come riferimento.

### Corrispondenza fra la scheda «Verifica» (D1–D16) e queste risposte

| Scheda «Verifica» | Argomento | Vedi |
|---|---|---|
| D1 | Struttura del diodo | D1 |
| D2 | Simbolo circuitale | D2 |
| D3 | Zone di polarizzazione sulla caratteristica | D8 |
| D4 | Grandezze dell'equazione a destra del breakdown | D11 |
| D5 | Motivi dei modelli approssimati | D12 |
| D6 | Tensione di soglia | D6★ |
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

# Formule chiave

**A · Corrente alternata e filtri del primo ordine**

```
ω = 2πf          X_L = ωL          X_C = 1/(ωC)
Z̄_L = jωL        Z̄_C = 1/(jωC) = −j/(ωC)
serie:  Z̄ = Z̄₁ + Z̄₂        parallelo:  Z̄ = Z̄₁Z̄₂/(Z̄₁+Z̄₂)
|Z| = √(a²+b²)   arg Z̄ = arctan(b/a)
partitore:  Ḡ(s) = Z̄_uscita/(Z̄_serie + Z̄_uscita)      (adimensionale!)
taglio RC:  f_t = 1/(2πRC)        taglio RL:  f_t = R/(2πL)
poli = radici del denominatore     zeri = radici del numeratore
```

**B · BJT**

```
maglia d'ingresso   V_BB = R_B·I_B + V_BE [+ R_E·I_E]     →  I_B
transistor          I_C = h_FE·I_B      I_E = (h_FE+1)·I_B
maglia d'uscita     V_CC = R_C·I_C + V_CE [+ R_E·I_E]     →  V_CE
saturazione         I_C(sat) = (V_CC − V_CEsat)/(R_C [+ R_E])
                    saturo se  I_B > I_C(sat)/h_FE
progetto partitore  V_E = V_CC/10 · V_RC = V_CE = 9V_CC/20
                    V_BO = V_BE + R_E·I_CO · I = 10·I_B  (con h_FEmin)
                    R₂ = V_BO/I · R₁ = (V_CC − V_BO)/I
by-pass             C_E ≥ 10/(2π·f_min·R_E)
commutazione        I_Bmin = I_C/h_FEmin, poi ×2÷5 di overdrive
                    + DIODO DI RICIRCOLO su ogni carico induttivo
```

**C · JFET e MOSFET**

```
I_G = 0  →  V_G imposta dal circuito · I_S = I_D · R_G si SCEGLIE (1÷10 MΩ)

JFET canale N (V_P < 0)
  I_D  = I_DSS·(1 − V_GS/V_P)²        V_GS = V_P·(1 − √(I_D/I_DSS))
  saturazione:  V_DS ≥ V_GS − V_P     V_GS sta sempre fra V_P e 0

MOSFET enhancement canale N (V_t > 0)
  saturazione:  I_D = K·(V_GS − V_t)²       V_GS = V_t + √(I_D/K)
  ohmica:       I_D = K·[2(V_GS − V_t)V_DS − V_DS²]   se V_DS < V_GS − V_t

autopolarizzazione   V_GS = −R_S·I_D             R_S = −V_GS/I_D
maglia d'uscita      V_DD = R_D·I_D + V_DS + R_S·I_D        (tre termini se c'è R_S!)
partitore di gate    V_G = V_GS + V_S            R₂ = (V_G/V_DD)·(R₁+R₂)
```

**D · Diodi**

```
Shockley       I_D = I_S·(e^(V_D/(ηV_T)) − 1)        V_T = kT/q ≈ 26 mV
soglia         V_γ ≈ 0,7 V (Si) · 0,2÷0,3 V (Ge)
modelli        A: V_γ + r_D    B: V_γ    C: ideale (0 V)
raddrizzatore  1 semionda: V_med = V_max/π ≈ 0,318·V_max   f_ripple = 50 Hz
               2 semionde: V_med = 2V_max/π ≈ 0,637·V_max  f_ripple = 100 Hz
limitatore     n diodi in serie → soglia n·V_γ  ·  antiparallelo → ±V_γ
Zener          V_o = V_Z · I_S = (V_i − V_Z)/R_S · I_L = V_Z/R_L · I_Z = I_S − I_L
               I_ZK ≤ I_Z ≤ I_ZM = P_Zmax/V_Z
               R_S,max = (V_i,min − V_Z)/(I_ZK + I_L,max)
               R_S,min = (V_i,max − V_Z)/(I_ZM + I_L,min)
```

---

# Le sei trappole che costano il 70% dei punti

| # | Trappola | Dove | Come non caderci |
|---|---|---|---|
| 1 | **Maglie d'ingresso e d'uscita mescolate** (`R_B` con `R_C`) | B es. 2, 6, 7 | Prima di scrivere l'equazione chiediti: *questa resistenza è percorsa da I_B, I_C o I_E?* Le due maglie condividono solo il ramo di emettitore. |
| 2 | **`I_G ≈ 0` dimenticato** → `R_G` calcolata da una legge | C es. 1, 2 | Nel JFET/MOSFET il gate non assorbe corrente. **`R_G` si sceglie (1÷10 MΩ), non si calcola.** |
| 3 | **`V_S`/`V_E` dimenticata** nella maglia d'uscita o nel partitore | B es. 3, C es. 8 | Se c'è `R_S`/`R_E`: `V_DD = V_RD + V_DS + V_S` e `V_G = V_GS + V_S`. **Tre** termini, non due. |
| 4 | **Formule dimensionalmente impossibili** (`√(I_D/R_D)`, `arctan(1/\|Z\|)`) | A es. 1B, C es. 6, 7 | Controlla le unità del risultato: se non sono V/A/Ω come devono, la formula è sbagliata a prescindere dai numeri. |
| 5 | **Valori sostituiti male** (10 al posto di 12, f errata) | A es. 1A, B es. 1 | Riscrivi i dati in colonna prima di iniziare e spuntali man mano che li usi. |
| 6 | **Ipotesi non verificata alla fine** (saturo / zona attiva) | C es. 6, B es. 6 | Ogni esercizio con un'ipotesi si **chiude** con la verifica. Se non regge, **dillo per iscritto** e rifai con l'altra zona. |

> [!tip] La differenza fra 3/10 e 7/10
> Sui tre fascicoli **7 esercizi su 21 sono stati lasciati completamente in bianco**, e valgono
> **8,00 punti su 30**: A es. 5 (due divisioni), B es. 4 e 5, C es. 3, 4 e 5. Nessuno richiede più
> di dieci minuti. Il messaggio dei fascicoli non è «gli esercizi sono difficili»: è
> **«va svolto tutto»**.

---

## Collegamenti

- [[06 - Soluzioni complete verifiche FUSI]] — le stesse 21 soluzioni in forma estesa e ragionata
- [[05 - Verifiche FUSI (Carli)]] — come Carli formula, corregge e valuta
- [[diodi-risposte]] — le risposte sui diodi per esteso (e la versione stampabile in HTML)
- [[Formulario rapido]] — tutte le formule, in forma di cartellina
- [[02 - Prova Orale Carli]] · [[01 - Prova Scritta Carli]] — struttura delle prove
- [[Esercizi - Impedenza dei bipoli R, L, C]] · [[Esercizi - Filtri passivi del primo ordine]] — Parte A
- [[Esercizi - BJT]] · [[Esercizi - Amplificatori a BJT]] — Parte B
- [[Esercizi - JFET]] · [[Esercizi - MOSFET]] — Parte C
- [[Diodi]] · [[Esercizi - Diodi]] — Parte D
- [[Calendario]] — il piano del 30 e 31 agosto
