---
tags: [recupero, elettronica, verifiche, carli, soluzioni, fonte-derivata]
fonte: "risoluzione integrale dei 21 esercizi contenuti nelle tre verifiche del Prof. Carlo Carli"
file: "Fonti/FUSI_02-03-26_260616_183723.pdf · Fonti/FUSI_24-04-26_260616_183749.pdf · Fonti/FUSI_29-05-26_260616_183828.pdf"
aggiunto: 2026-08-28
verificato: "2026-08-28 — testi riletti pagina per pagina dai tre PDF (scansioni senza strato di testo); ogni risultato ricalcolato da zero · 2026-08-30 — corretta la V_DD della Verifica 3 es. 7 (25 V, non 15 V) su ritaglio a 300 dpi"
---

# 06 — Soluzioni complete delle verifiche FUSI

Companion di [[05 - Verifiche FUSI (Carli)]]. Quella nota racconta **come Carli corregge e
valuta**; questa contiene lo **svolgimento completo di tutti e 21 gli esercizi**, compresi i
sette che Fusi non ha svolto per niente e i sei che ha sbagliato.

> [!info] Come leggere questa nota
> Per ogni esercizio trovi: **Testo** (dati come li ha scritti il prof.) → **Ragionamento**
> (quale legge si applica e perché) → **Calcoli** → **Risultato**. Dove Fusi ha sbagliato,
> un blocco *Trappola* isola l'errore preciso, perché è quello il valore didattico dei
> fascicoli.

> [!warning] Convenzioni usate ovunque
> - `ω = 2πf`; `X_L = ωL`; `X_C = 1/(ωC)`; `Z_L = jωL`; `Z_C = −j/(ωC) = 1/(jωC)`.
> - Per un numero complesso `Z = a + jb`: `|Z| = √(a²+b²)`, `arg Z = arctan(b/a)`
>   (con la correzione di quadrante se `a < 0`).
> - Resistenze arrotondate ai valori commerciali della serie E24 solo dove indicato.

---

# Verifica 1 — 13/02/2026 (valutata 02/03)
**Circuiti in corrente alternata e filtri passivi del primo ordine · 6 esercizi**

Esiti di Fusi: 1 ~OK · 2 errato · 3 ~OK · 4 errato · 5 non svolto · 6 OK → **3,00/10**.

---

## Es. 1 — Modulo e argomento dell'impedenza equivalente

### Ragionamento comune ai due bipoli
In entrambi i casi la corrente `Ī` entra da un morsetto, attraversa il primo componente e
torna dall'altro morsetto attraversando il secondo: i due bipoli sono **in serie**, non in
parallelo. Il disegno trae in inganno perché il secondo componente è disegnato in verticale,
ma non c'è nessun ramo che lo scavalchi: è una maglia unica.

Per una serie le impedenze si **sommano come numeri complessi**:
`Z̄_eq = Z̄₁ + Z̄₂`.

---

### 1A) Serie R–C

**Dati:** `C = 10 nF`, `R = 1 kΩ`, `f = 10 kHz`.

**Calcoli**

```
ω    = 2πf = 2π · 10⁴ = 6,2832 · 10⁴ rad/s

X_C  = 1/(ωC) = 1 / (6,2832·10⁴ · 10·10⁻⁹)
     = 1 / (6,2832·10⁻⁴) = 1591,5 Ω

Z̄_eq = R − jX_C = 1000 − j1591,5  Ω

|Z_eq| = √(1000² + 1591,5²) = √(1,000·10⁶ + 2,533·10⁶)
       = √(3,533·10⁶) = 1879,6 Ω

φ = arctan(−1591,5 / 1000) = arctan(−1,5915) = −57,86°
```

> [!success] Risultato 1A
> **|Z_eq| ≈ 1,88 kΩ**, **φ ≈ −57,9°** (bipolo **ohmico-capacitivo**: la corrente è in
> anticipo sulla tensione, argomento negativo).

> [!danger] Trappola — l'errore di Fusi qui
> Ha usato `f = 1 kHz` invece dei 10 kHz del testo (`ω = 6,3·10³` anziché `6,28·10⁴`), e ha
> poi scritto `Z̄_C = −1/(jωC)` con un segno meno di troppo: `1/(jωC)` vale **già** `−j/(ωC)`,
> perché `1/j = −j`. Aggiungendo un altro meno l'impedenza capacitiva diventa induttiva e
> l'argomento cambia segno. Il prof. ha cerchiato in rosso proprio quel `−1/(jωC)`.

---

### 1B) Serie R–L

**Dati:** `R = 330 Ω`, `L = 12 mH`, `f = 10 kHz`.

**Calcoli**

```
ω    = 2π · 10⁴ = 6,2832 · 10⁴ rad/s

X_L  = ωL = 6,2832·10⁴ · 12·10⁻³ = 753,98 Ω

Z̄_eq = R + jX_L = 330 + j754  Ω

|Z_eq| = √(330² + 753,98²) = √(108 900 + 568 486)
       = √677 386 = 823,0 Ω

φ = arctan(753,98 / 330) = arctan(2,2848) = +66,36°
```

> [!success] Risultato 1B
> **|Z_eq| ≈ 823 Ω**, **φ ≈ +66,4°** (bipolo **ohmico-induttivo**: corrente in ritardo,
> argomento positivo).

> [!danger] Trappola
> Fusi aveva `Z̄_L = 7,5·10²` e `Z̄_R = 3,3·10²` giusti, ma nel modulo ha scritto
> `√(330² + 75²)` perdendo un ordine di grandezza sulla reattanza, e nell'argomento ha usato
> `arctan(1/328,9)` invece di `arctan(X_L/R)`. **L'argomento non è mai `arctan(1/|Z|)`**:
> è sempre `arctan(parte immaginaria / parte reale)`.

---

## Es. 2 — Poli delle funzioni di trasferimento

### Ragionamento
I **poli** di `G(s)` sono le radici del **denominatore** `D(s) = 0`; gli **zeri** sono le
radici del numeratore. Non c'entra nulla il limite di `G(s)`: si annulla il denominatore e
si risolve.

---

### 2A)

`G(s) = 3 / (s² + 5s + 6)`

```
D(s) = s² + 5s + 6 = 0
Δ = 25 − 24 = 1;   √Δ = 1
s = (−5 ± 1)/2   →   s₁ = −2 ,  s₂ = −3
```

Oppure per scomposizione diretta: `s² + 5s + 6 = (s+2)(s+3)`.

> [!success] Risultato 2A
> **Poli: s₁ = −2 rad/s, s₂ = −3 rad/s.** Entrambi reali, negativi e distinti → sistema
> **stabile**, del secondo ordine sovrasmorzato, senza zeri.

---

### 2B)

`G(s) = (s + 1) / [3s(s + 5)]`

```
D(s) = 3s(s + 5) = 0   →   s₁ = 0 ,  s₂ = −5
N(s) = s + 1 = 0       →   z₁ = −1
```

> [!success] Risultato 2B
> **Poli: s₁ = 0 (polo nell'origine), s₂ = −5 rad/s.** In più uno **zero in z₁ = −1 rad/s**.
> Il polo nell'origine significa un comportamento **integratore**: il sistema è al limite
> della stabilità (marginalmente stabile).

> [!danger] Trappola
> Fusi ha calcolato `lim(s→…) G(s)` ottenendo «0,6», che è il **guadagno statico** di 2A,
> non un polo. Il prof. ha scritto in rosso: *«completamente errato»*, e poi ha annotato lui
> stesso la procedura giusta: `D(s) = 0 → s² + 5s + 6 = 0`.

---

## Es. 3 — Risposta in ampiezza e in fase di un quadripolo

**Circuito:** `R₁` in serie sul ramo d'ingresso; sul nodo d'uscita `R₂` e `L` in **parallelo**
verso massa; `v_o(t)` presa ai capi del parallelo.

**Dati:** `R₁ = 2,2 kΩ`, `R₂ = 5,6 kΩ`, `L = 1 mH`.
Frequenze richieste: `f₁ = 0 Hz`, `f₂ = 100 kHz`, `f₃ = 20 MHz`.

### Ragionamento
È un **partitore di tensione fra impedenze**. Prima si riduce il parallelo `R₂ ∥ Z_L`, poi
si applica la formula del partitore:

```
Z̄_p = (Z̄_L · R₂)/(Z̄_L + R₂)   con  Z̄_L = jωL

Ḡ(jω) = V̄_o/V̄_i = Z̄_p / (R₁ + Z̄_p)
```

Sostituendo e semplificando (moltiplico numeratore e denominatore per `R₂ + jωL`):

```
                    jωL·R₂
Ḡ(jω) = ───────────────────────────────
          R₁R₂ + jωL·(R₁ + R₂)
```

Da qui si leggono direttamente le due risposte richieste:

```
RISPOSTA IN AMPIEZZA
                      ωL·R₂
|G(ω)| = ────────────────────────────────────
          √[ (R₁R₂)² + (ωL(R₁+R₂))² ]

RISPOSTA IN FASE
φ(ω) = 90° − arctan[ ωL(R₁+R₂) / (R₁R₂) ]
```

Il `+90°` viene dalla `j` al numeratore (uno zero nell'origine), l'arcotangente dal polo.
**È un filtro passa-alto del primo ordine.**

Costanti caratteristiche:

```
ω_t = R₁R₂ / [L(R₁+R₂)] = (2200·5600) / (1·10⁻³ · 7800)
    = 12,32·10⁶ / 7,8 = 1,5795·10⁶ rad/s
f_t = ω_t/2π = 251,4 kHz

Guadagno asintotico (ω → ∞): R₂/(R₁+R₂) = 5600/7800 = 0,718
```

### Calcoli alle tre frequenze

**1) f₁ = 0 Hz (continua)**

```
ω = 0  →  Z̄_L = j·0·L = 0  →  l'induttore è un CORTOCIRCUITO
|G| = 0        (0 in scala lineare, −∞ dB)
φ   = +90°
```

Interpretazione fisica: in continua l'induttore cortocircuita l'uscita a massa, quindi non
passa nulla. Coerente con un passa-alto.

**2) f₂ = 100 kHz**

```
ω    = 2π·10⁵ = 6,2832·10⁵ rad/s
ωL   = 6,2832·10⁵ · 10⁻³ = 628,3 Ω

Numeratore   : ωL·R₂ = 628,3 · 5600 = 3,519·10⁶
R₁R₂         = 2200 · 5600 = 12,32·10⁶
ωL(R₁+R₂)    = 628,3 · 7800 = 4,901·10⁶
Denominatore : √[(12,32·10⁶)² + (4,901·10⁶)²] = √(1,758·10¹⁴) = 1,326·10⁷

|G| = 3,519·10⁶ / 1,326·10⁷ = 0,265   →  20·log₁₀(0,265) = −11,5 dB
φ   = 90° − arctan(4,901/12,32) = 90° − 21,7° = +68,3°
```

**3) f₃ = 20 MHz**

```
ω    = 2π·2·10⁷ = 1,2566·10⁸ rad/s
ωL   = 1,2566·10⁸ · 10⁻³ = 1,2566·10⁵ Ω

Numeratore   : 1,2566·10⁵ · 5600 = 7,037·10⁸
ωL(R₁+R₂)    = 1,2566·10⁵ · 7800 = 9,802·10⁸
Denominatore : √[(1,232·10⁷)² + (9,802·10⁸)²] ≈ 9,803·10⁸

|G| = 7,037·10⁸ / 9,803·10⁸ = 0,718   →  −2,9 dB
φ   = 90° − arctan(9,802·10⁸ / 1,232·10⁷) = 90° − 89,3° = +0,7°
```

> [!success] Risultato Es. 3
> | f | \|G\| | \|G\|_dB | φ |
> |---|---|---|---|
> | 0 Hz | 0 | −∞ | +90° |
> | 100 kHz | 0,265 | −11,5 dB | +68,3° |
> | 20 MHz | 0,718 | −2,9 dB | +0,7° |
>
> Filtro **passa-alto** con `f_t ≈ 251 kHz` e guadagno in banda passante `0,718` (−2,9 dB).
> A 20 MHz siamo ben oltre il taglio: il guadagno è già a regime e la fase quasi nulla.

---

## Es. 4 — Funzione di trasferimento dei quadripoli

### Ragionamento comune
Entrambi sono **partitori di tensione** fra due impedenze in serie, con l'uscita presa ai
capi della seconda:

```
Ḡ(s) = Z̄_uscita / (Z̄_serie + Z̄_uscita)
```

Con `Z_R = R` e `Z_L = sL`. Il tipo di filtro dipende da **su quale componente si preleva
l'uscita**, non dall'ordine in cui sono disegnati.

---

### 4A) R in serie, L in parallelo, uscita su L

**Dati:** `R = 560 Ω`, `L = 3 mH`.

```
G(s) = sL / (R + sL)

Divido numeratore e denominatore per L:

G(s) = s / (s + R/L)

ω_t = R/L = 560 / (3·10⁻³) = 1,867·10⁵ rad/s
f_t = ω_t/2π = 29,7 kHz
```

Forma normalizzata (quella che Carli si aspetta):

```
          s/ω_t
G(s) = ─────────── ,   ω_t = 1,867·10⁵ rad/s
        1 + s/ω_t
```

> [!success] Risultato 4A
> **G(s) = sL/(R+sL) = s/(s + 1,867·10⁵)** — **filtro passa-alto** del primo ordine,
> `f_t ≈ 29,7 kHz`, guadagno in banda passante unitario, uno **zero nell'origine** e un
> **polo in s = −1,867·10⁵ rad/s**.

---

### 4B) L in serie, R in parallelo, uscita su R

**Dati:** `L = 0,3 mH`, `R = 1,2 kΩ`.

```
G(s) = R / (R + sL) = 1 / (1 + sL/R)

L/R = 0,3·10⁻³ / 1200 = 2,5·10⁻⁷ s   (costante di tempo τ)

ω_t = R/L = 1200 / (0,3·10⁻³) = 4·10⁶ rad/s
f_t = 636,6 kHz
```

> [!success] Risultato 4B
> **G(s) = R/(R+sL) = 1/(1 + 2,5·10⁻⁷·s)** — **filtro passa-basso** del primo ordine,
> `f_t ≈ 636,6 kHz`, guadagno in continua unitario, un **polo in s = −4·10⁶ rad/s**,
> nessuno zero.

> [!danger] Trappola
> Fusi ha scritto `V_o(s) = V_i(s)·(Z_R + Z_C)` e `V_o = V_i·Z_eq`: ha **sommato** le
> impedenze invece di fare il rapporto del partitore, e in 4A ha usato un condensatore
> quando nel disegno c'è un'**induttanza** (annotazione rossa del prof.: *«nel circuito
> assegnato è presente, oltre a una resistenza, un'induttanza non una capacità»*).
> La funzione di trasferimento è sempre **adimensionale**: se il risultato ha le dimensioni
> di ohm, è sbagliato.

---

## Es. 5 — Frequenza di taglio dei filtri

### Ragionamento
Per un filtro RC del primo ordine la frequenza di taglio è quella in cui **la reattanza
eguaglia la resistenza** (`X_C = R`), cioè dove il modulo scende di 3 dB:

```
1/(2πf_t C) = R   →   f_t = 1/(2πRC)
```

La formula è **la stessa** per passa-alto e passa-basso: cambia il tipo di filtro (cioè
quale banda passa), non il valore del taglio.

---

### 5A) C in serie, R verso massa, uscita su R → **passa-alto**

**Dati:** `C = 150 nF`, `R = 6,8 kΩ`.

```
RC   = 6800 · 150·10⁻⁹ = 1,02·10⁻³ s
f_t  = 1/(2π · 1,02·10⁻³) = 1/(6,409·10⁻³) = 156,0 Hz
```

> [!success] Risultato 5A
> **f_t ≈ 156 Hz** — filtro **passa-alto** (blocca la continua, lascia passare sopra i 156 Hz).

---

### 5B) R in serie, C verso massa, uscita su C → **passa-basso**

**Dati:** `R = 1 kΩ`, `C = 2,2 µF`.

```
RC   = 1000 · 2,2·10⁻⁶ = 2,2·10⁻³ s
f_t  = 1/(2π · 2,2·10⁻³) = 1/(1,382·10⁻²) = 72,3 Hz
```

> [!success] Risultato 5B
> **f_t ≈ 72,3 Hz** — filtro **passa-basso**.

> [!note] Esercizio lasciato in bianco
> Il prof. ha scritto *«NON SVOLTO PER NULLA»*: 0,00/2,00 punti. È l'esercizio più veloce di
> tutta la verifica — due divisioni. Vale il 20% del voto.

---

## Es. 6 — Impedenza equivalente di una rete

**Dati:**
`Z̄₁ = (2 + j6) Ω` · `Z̄₂ = (2 − j2) Ω` · `Z̄₃ = (j10) Ω` · `Z̄₄ = (2 + j4) Ω`

### Ragionamento — riconoscere la topologia
Questo è il passaggio che vale l'esercizio. Guardando il disegno:

- il morsetto **superiore** e il nodo centrale (dove convergono `Z̄₁`, `Z̄₃`, `Z̄₄`) sono
  **collegati da un filo**: sono lo **stesso nodo elettrico**, chiamiamolo **A**;
- il morsetto **inferiore**, il filo di fondo e il nodo di destra sono anch'essi **un unico
  nodo**, chiamiamolo **B**.

Ricondotto ai due nodi A e B, ogni impedenza è **fra A e B**:

| Impedenza | Da | A |
|---|---|---|
| `Z̄₁` | B | A |
| `Z̄₂` | A | B (via nodo di destra) |
| `Z̄₃` | A | B |
| `Z̄₄` | A | B (via nodo di destra) |

Quindi **tutte e quattro sono in parallelo**:
`Z̄_eq = Z̄₁ ∥ Z̄₂ ∥ Z̄₃ ∥ Z̄₄`.

Si risolve a coppie, come ha fatto (correttamente, come impostazione) Fusi:
`Z̄₂₄ = Z̄₂ ∥ Z̄₄` → `Z̄₂₃₄ = Z̄₂₄ ∥ Z̄₃` → `Z̄_eq = Z̄₁ ∥ Z̄₂₃₄`.

### Calcoli

**Passo 1 — Z̄₂₄ = Z̄₂ · Z̄₄ / (Z̄₂ + Z̄₄)**

```
Numeratore  : (2 − j2)(2 + j4) = 4 + j8 − j4 − j²8 = 4 + j4 + 8 = 12 + j4
Denominatore: (2 − j2) + (2 + j4) = 4 + j2

(12 + j4)/(4 + j2)  ·  (4 − j2)/(4 − j2)

num = (12 + j4)(4 − j2) = 48 − j24 + j16 − j²8 = 48 − j8 + 8 = 56 − j8
den = 4² + 2² = 20

Z̄₂₄ = (56 − j8)/20 = 2,8 − j0,4  Ω
```

**Passo 2 — Z̄₂₃₄ = Z̄₂₄ · Z̄₃ / (Z̄₂₄ + Z̄₃)**

```
Numeratore  : (2,8 − j0,4)(j10) = j28 − j²4 = 4 + j28
Denominatore: (2,8 − j0,4) + j10 = 2,8 + j9,6

(4 + j28)/(2,8 + j9,6) · (2,8 − j9,6)/(2,8 − j9,6)

num = (4 + j28)(2,8 − j9,6) = 11,2 − j38,4 + j78,4 − j²268,8 = 280 + j40
den = 2,8² + 9,6² = 7,84 + 92,16 = 100

Z̄₂₃₄ = (280 + j40)/100 = 2,8 + j0,4  Ω
```

**Passo 3 — Z̄_eq = Z̄₁ · Z̄₂₃₄ / (Z̄₁ + Z̄₂₃₄)**

```
Numeratore  : (2 + j6)(2,8 + j0,4) = 5,6 + j0,8 + j16,8 + j²2,4 = 3,2 + j17,6
Denominatore: (2 + j6) + (2,8 + j0,4) = 4,8 + j6,4

(3,2 + j17,6)/(4,8 + j6,4) · (4,8 − j6,4)/(4,8 − j6,4)

num = (3,2 + j17,6)(4,8 − j6,4) = 15,36 − j20,48 + j84,48 − j²112,64 = 128 + j64
den = 4,8² + 6,4² = 23,04 + 40,96 = 64

Z̄_eq = (128 + j64)/64 = 2 + j1  Ω
```

> [!success] Risultato Es. 6
> **Z̄_eq = (2 + j1) Ω**
> **|Z_eq| = √5 = 2,24 Ω**, **arg Z_eq = arctan(1/2) = +26,6°** → bipolo **ohmico-induttivo**.
>
> Il risultato esce con numeri esatti: è la verifica che la topologia è stata letta bene.

> [!danger] Trappola
> Fusi ha impostato bene i tre paralleli (il prof. gli ha dato 2,00/2,00, pieno) ma ha
> sbagliato il **passo 1**: da `(12+j4)/(4+j2)` ha scritto `3 + j2` invece di `2,8 − j0,4`,
> arrivando poi a `Z̄_eq = 2,69 − j1,7`.
> **Controllo veloce per non cascarci:** i moduli si dividono.
> `|12+j4| = 12,65`, `|4+j2| = 4,47` → il modulo del risultato deve valere `2,83`.
> `|3+j2| = 3,61` ✗ · `|2,8−j0,4| = 2,83` ✓.

---

# Verifica 2 — 24/04/2026 (valutata 09/05)
**BJT: polarizzazione, progetto, commutazione, amplificatore · 7 esercizi**

Esiti di Fusi: 1 ~OK · 2 ~OK · 3 errato · 4 non svolto · 5 non svolto · 6 errato · 7 errato
→ **1,50 punti, voto 3/10**.

> [!abstract] Le tre relazioni che risolvono cinque esercizi su sette
> Tutti gli esercizi su BJT in zona attiva si aprono con le stesse tre equazioni, applicate
> **in quest'ordine**:
> 1. **Maglia d'ingresso** (Kirchhoff sulla maglia base–emettitore) → dà `I_B`.
> 2. **Relazione del transistor**: `I_C = h_FE · I_B`, `I_E = I_C + I_B = (h_FE + 1)·I_B`.
> 3. **Maglia d'uscita** (Kirchhoff sulla maglia collettore–emettitore) → dà `V_CE`.
>
> **L'errore capitale**, quello che Carli segna in rosso ogni volta: mettere `R_B` nella
> maglia d'uscita o `R_C` nella maglia d'ingresso. Le due maglie sono **separate** e
> condividono solo il ramo di emettitore.

---

## Es. 1 — Determinare V_CE, I_C e I_B

**Dati:** `V_CC = 12 V`, `R_C = 820 Ω`, `V_BB = 5 V`, `R_B = 56 kΩ`, `h_FE = 100`,
`V_BE = 0,7 V` (zona attiva lineare, per ipotesi del testo).

**Circuito:** polarizzazione a **due alimentazioni**, `V_BB` in serie a `R_B` sulla base,
emettitore a massa, `R_C` fra `V_CC` e collettore.

### Calcoli

**1) Maglia d'ingresso:** `V_BB = R_B·I_B + V_BE`

```
I_B = (V_BB − V_BE)/R_B = (5 − 0,7)/56·10³ = 4,3/56 000
    = 76,8·10⁻⁶ A = 76,8 µA
```

**2) Relazione del transistor:**

```
I_C = h_FE · I_B = 100 · 76,8·10⁻⁶ = 7,68·10⁻³ A = 7,68 mA
```

**3) Maglia d'uscita:** `V_CC = R_C·I_C + V_CE`

```
V_CE = V_CC − R_C·I_C = 12 − 820 · 7,68·10⁻³
     = 12 − 6,30 = 5,70 V
```

**4) Verifica dell'ipotesi di zona attiva.** La corrente che circolerebbe a saturazione è

```
I_C(sat) = (V_CC − V_CEsat)/R_C = (12 − 0,2)/820 = 14,4 mA
```

`I_C = 7,68 mA < 14,4 mA` e `V_CE = 5,70 V > V_CEsat` → **il BJT è davvero in zona attiva**,
l'ipotesi regge.

> [!success] Risultato Es. 1
> **I_B = 76,8 µA · I_C = 7,68 mA · V_CE = 5,70 V**
> Punto di lavoro Q(5,70 V ; 7,68 mA), circa a metà della retta di carico → buona
> polarizzazione per un amplificatore.

> [!danger] Trappola
> Fusi ha impostato tutto correttamente ma nell'ultimo passaggio ha scritto
> `V_CE = (10 − 6,3) V = 3,7 V`: ha usato **10 V al posto dei 12 V** del testo. Il prof. ha
> cerchiato il 10 e scritto *«errato a sostituire il valore, in quanto V_CC = 12 V»*.
> Mezzo punto perso per una cifra.

---

## Es. 2 — Progetto: determinare R_C e R_B per il punto di lavoro assegnato

**Dati:** `V_CEO = 4,8 V`, `I_CO = 14 mA`, `h_FE = 100`, `V_CC = 10 V`, `V_BE = 0,7 V`.
**Circuito:** polarizzazione **a base fissa** (`R_B` fra `V_CC` e base, `R_C` fra `V_CC` e
collettore, emettitore a massa).

### Ragionamento
È l'esercizio 1 letto al contrario: il punto di lavoro è il **dato**, le resistenze sono
l'**incognita**. Le maglie restano due e restano separate.

### Calcoli

**Maglia d'uscita → R_C**

```
V_CC = R_C·I_CO + V_CEO

R_C = (V_CC − V_CEO)/I_CO = (10 − 4,8)/14·10⁻³
    = 5,2/0,014 = 371,4 Ω
```

**Corrente di base**

```
I_B = I_CO/h_FE = 14·10⁻³/100 = 140·10⁻⁶ A = 140 µA
```

**Maglia d'ingresso → R_B**

```
V_CC = R_B·I_B + V_BE

R_B = (V_CC − V_BE)/I_B = (10 − 0,7)/140·10⁻⁶
    = 9,3/1,4·10⁻⁴ = 66,4·10³ Ω = 66,4 kΩ
```

> [!success] Risultato Es. 2
> **R_C ≈ 371 Ω** (valore commerciale **390 Ω**) · **R_B ≈ 66,4 kΩ** (valore commerciale
> **68 kΩ**).
>
> Con i valori commerciali il punto di lavoro si sposta di poco:
> `I_B = 9,3/68k = 137 µA` → `I_C = 13,7 mA` → `V_CE = 10 − 390·0,0137 = 4,66 V`. Accettabile.

> [!danger] Trappola
> Fusi ha ottenuto i numeri giusti ma è partito da `V_CE = R_B·I_B + R_C·I_C`, che è
> **falsa**: mette insieme un elemento della maglia d'ingresso (`R_B`) e uno della maglia
> d'uscita (`R_C`). Annotazione del prof.: *«errata, in quanto R_B fa parte della maglia
> d'ingresso non della maglia d'uscita»*, e più sotto *«non si spiega questo passaggio dalla
> relazione precedente»*. **I risultati giusti da una relazione sbagliata non valgono il
> punteggio pieno.**

---

## Es. 3 — Progetto del circuito di polarizzazione e stabilizzazione (partitore + R_E)

**Dati:** `V_CC = 10 V`, `I_CO = 10 mA`, `h_FEmin = 75`, `V_BE = 0,7 V`.
**Incognite:** `I_B`, `I_E`, `R_C`, `R_E`, `R₁`, `R₂`.

### Ragionamento — perché servono criteri di progetto
Qui le incognite (4 resistenze) sono più delle equazioni indipendenti: il problema è
**sottodeterminato**. Si chiude imponendo i **criteri standard di progetto**, quelli che
Carli ha scritto di suo pugno sul retro del foglio:

1. **Tensione di emettitore** `V_E = V_CC/10` → rende il punto di lavoro insensibile alle
   variazioni di `h_FE` e della temperatura (è la *stabilizzazione*), senza sprecare troppa
   dinamica.
2. I restanti `9·V_CC/10` si dividono **a metà** fra `R_C` e il transistor:
   `V_RC = V_CE = 9·V_CC/20`. Così l'escursione del segnale è massima e simmetrica.
3. **Corrente nel partitore** `I = 10·I_B` calcolata con **h_FEmin** → il ramo di base
   assorbe un decimo della corrente del partitore, che quindi impone `V_BO` in modo rigido
   e indipendente dal transistor.

### Calcoli

**Resistenza di emettitore**

```
V_E = V_CC/10 = 1 V
R_E = V_E/I_CO = V_CC/(10·I_CO) = 10/(10 · 10·10⁻³) = 100 Ω
```

**Resistenza di collettore**

```
V_RC = 9·V_CC/20 = 4,5 V
R_C  = 9·V_CC/(20·I_CO) = 90/(20 · 10·10⁻³) = 90/0,2 = 450 Ω
```

*(Verifica della maglia d'uscita: `V_RC + V_CE + V_E = 4,5 + 4,5 + 1 = 10 V = V_CC` ✓)*

**Tensione di base e corrente del partitore**

```
V_BO = V_BE + V_RE = V_BE + R_E·I_CO = 0,7 + 100 · 10·10⁻³ = 0,7 + 1 = 1,7 V

I_B = I_CO/h_FEmin = 10·10⁻³/75 = 133,3 µA
I   = 10·I_B = 1,33 mA  ≈ 1,3 mA
```

**Partitore di base**

```
R₂ (verso massa) = V_BO/I = 1,7/1,3·10⁻³ = 1,31 kΩ  ≈ 1,3 kΩ
R₁ (verso V_CC)  = (V_CC − V_BO)/I = (10 − 1,7)/1,3·10⁻³ = 6,38 kΩ  ≈ 6,4 kΩ
```

**Corrente di emettitore**

```
I_E = I_C + I_B = 10 + 0,133 = 10,13 mA  ≈ 10,1 mA
```

> [!success] Risultato Es. 3
> **R_E = 100 Ω · R_C = 450 Ω · R₂ = 1,3 kΩ · R₁ = 6,4 kΩ**
> **I_B = 133 µA · I_E = 10,1 mA · V_BO = 1,7 V · V_CE = 4,5 V**
>
> Valori commerciali: `R_E = 100 Ω`, `R_C = 470 Ω`, `R₂ = 1,3 kΩ`, `R₁ = 6,2 kΩ`.

> [!tip] Questo è l'esercizio con la soluzione autografa del prof.
> Sul retro (p. 12 del PDF) c'è la sequenza completa in rosso, di mano di Carli. È il
> modello di svolgimento che si aspetta di vedere: **prima R_E, poi R_C, poi V_BO, poi I,
> poi il partitore.** Vale la pena impararla in quest'ordine.

> [!danger] Trappola
> Fusi ha scritto `R_C = (V_CC − V_CE)/I_CO` **dimenticando la caduta su R_E**: in un
> circuito con emettitore resistivo la maglia d'uscita è `V_CC = R_C·I_C + V_CE + R_E·I_E`,
> non `V_CC = R_C·I_C + V_CE`. Ha inoltre scritto `I_B = I_R1 − I_R2` con il segno
> invertito: il nodo di base dà `I_R1 = I_B + I_R2`, quindi `I_B = I_R1 − I_R2` è
> formalmente giusta, ma va usata insieme al criterio `I_R2 = 10·I_B`, che lui non ha
> imposto — senza quel criterio il sistema resta indeterminato.

---

## Es. 4 — Interfaccia fra porta TTL e bobina di relè

**Dati:** porta TTL con uscita `0 V` (livello basso) o `5 V` (livello alto); relè con
**tensione di bobina 12 V** e **corrente 70 mA**; `h_FEmin = 75`.

### Ragionamento
La porta TTL non può pilotare il relè per due motivi indipendenti:
- **tensione**: fornisce 5 V, la bobina ne vuole 12;
- **corrente**: un'uscita TTL eroga tipicamente ~0,4÷16 mA, la bobina ne chiede 70.

Serve quindi un **BJT NPN in commutazione** (interruttore comandato): la bobina va sul
**collettore**, alimentata a 12 V; l'emettitore a massa; la base pilotata dalla TTL
attraverso `R_B`. Il transistor deve lavorare fra **interdizione** (TTL a 0 V, relè
diseccitato) e **saturazione** (TTL a 5 V, relè eccitato) — mai in zona attiva, dove
dissiperebbe potenza inutilmente.

### Calcoli

**1) Corrente di collettore richiesta (a saturazione)**

```
I_C = 70 mA   (corrente nominale della bobina)
```

**2) Corrente di base minima per saturare**

```
I_Bmin = I_C/h_FEmin = 70·10⁻³/75 = 0,933 mA
```

**3) Sovrapilotaggio (overdrive).** Si moltiplica per un fattore 2÷5 per garantire la
saturazione anche col peggiore esemplare di transistor e alle basse temperature. Prendo
**×2**:

```
I_B = 2 · 0,933 = 1,87 mA
```

**4) Resistenza di base.** Maglia d'ingresso con `V_OH = 5 V` e `V_BEsat ≈ 0,7 V`:

```
R_B = (V_OH − V_BEsat)/I_B = (5 − 0,7)/1,87·10⁻³
    = 4,3/1,87·10⁻³ = 2,30 kΩ
```

**Valore commerciale: R_B = 2,2 kΩ.**

**5) Verifica con il valore commerciale**

```
I_B(reale) = 4,3/2200 = 1,95 mA
h_FE richiesto = I_C/I_B = 70/1,95 = 35,9  <  75  ✓ SATURO con ampio margine
```

**6) Diodo di libera circolazione (indispensabile).** La bobina è un'induttanza: quando il
BJT si interdice, la corrente non può annullarsi di colpo e genera una sovratensione
`v = L·di/dt` che distruggerebbe il transistor. Si mette un **diodo in antiparallelo alla
bobina**, catodo verso +12 V, anodo verso il collettore: alla commutazione offre alla
corrente una via di richiusura.
Tipo adatto: **1N4001÷1N4007** (I_F = 1 A ≫ 70 mA).

**7) Scelta del transistor e potenza dissipata**

```
P_diss = V_CEsat · I_C ≈ 0,2 · 70·10⁻³ = 14 mW   (trascurabile, niente dissipatore)
```

Transistor adatto: **BC337** (`I_Cmax = 800 mA`, `V_CEO = 45 V`) o **2N2222**.

> [!success] Risultato Es. 4
> **BJT NPN in commutazione** con `R_B = 2,2 kΩ` in serie alla base, bobina sul collettore
> alimentata a 12 V, emettitore a massa, **diodo 1N4007 in antiparallelo alla bobina**.
> `I_B = 1,95 mA`, `h_FE richiesto = 36 < 75` → saturazione garantita.
>
> Le due masse (TTL e alimentazione 12 V) devono essere **in comune**.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO PER NULLA»* — 0,00/1,00. Il **diodo di ricircolo** è la parte che Carli
> cerca: senza quello il progetto è considerato incompleto anche col resto giusto.

---

## Es. 5 — Condensatore di by-pass C_E

**Dati:** amplificatore BJT a **emettitore comune**, `R_E = 1 kΩ`, banda del segnale
`50 Hz ÷ 8 kHz`.

### Ragionamento
`R_E` serve alla **stabilizzazione del punto di lavoro in continua**, ma introduce
**controreazione in alternata** che abbatte il guadagno (`A_v ≈ −R_C/R_E`). Il condensatore
`C_E` in parallelo a `R_E` risolve il conflitto: in continua è un circuito aperto (`R_E`
lavora e stabilizza), in alternata deve essere un **cortocircuito** che mette l'emettitore a
massa e restituisce il guadagno pieno.

La condizione critica è alla **frequenza più bassa** della banda (50 Hz), dove la reattanza
del condensatore è massima. Il criterio di progetto standard è che la reattanza sia almeno
**dieci volte più piccola** di `R_E`:

```
X_CE ≤ R_E/10   alla   f_min
```

### Calcoli

```
1/(2π·f_min·C_E) ≤ R_E/10

C_E ≥ 10/(2π·f_min·R_E) = 10/(2π · 50 · 1000)
    = 10/(3,1416·10⁵) = 31,8·10⁻⁶ F = 31,8 µF
```

**Valore commerciale: C_E = 33 µF elettrolitico** (o 47 µF, andando più larghi).

**Verifica a 50 Hz con 33 µF:**

```
X_CE = 1/(2π · 50 · 33·10⁻⁶) = 1/(1,0367·10⁻²) = 96,5 Ω
96,5 Ω ≪ 1000 Ω  ✓  (rapporto ~1/10)
```

A 8 kHz `X_CE` scende a 0,6 Ω: la condizione è ancora più che soddisfatta, come atteso.

> [!success] Risultato Es. 5
> **C_E ≥ 31,8 µF → si sceglie C_E = 33 µF** (elettrolitico, tensione di lavoro ≥ 2·V_E,
> polarità positiva verso l'emettitore).
>
> *Se si applica il criterio minimo `f_min = 1/(2πR_E C_E)` invece della regola del fattore
> 10, verrebbe `C_E = 3,18 µF`: è la frequenza a cui `X_CE = R_E`, cioè dove il by-pass
> comincia appena a funzionare — a 50 Hz il guadagno sarebbe già sceso di 3 dB. Il criterio
> corretto per un progetto è quello ×10.*

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO PER NULLA»* — 0,00/1,00. Una formula sola.

---

## Es. 6 — Verifica del funzionamento in zona di saturazione

**Dati:** `V_CC = 10 V`, `h_FE = 50`, `R_B = 5,2 kΩ`, `R_C = 0,33 kΩ`, `V_BE = 0,8 V`,
`V_CEsat = 0,2 V`.
**Circuito:** base fissa (`R_B` fra `V_CC` e base), emettitore a massa.

### Ragionamento — la procedura in tre passi
Carli l'ha scritta lui stesso in rosso sul foglio di Fusi:

1. **II principio di Kirchhoff alla maglia d'ingresso** → `I_B` (reale, quella che il
   circuito fornisce davvero).
2. **II principio di Kirchhoff alla maglia d'uscita**, *ipotizzando il transistor saturo*
   (`V_CE = V_CEsat`) → `I_C(sat)`, cioè la corrente massima che il carico può far passare.
3. **Confronto:** se `I_B > I_C(sat)/h_FE`, la base è sovrapilotata e il transistor è
   **davvero** in saturazione. Se fosse `I_B < I_C(sat)/h_FE`, il transistor sarebbe in zona
   attiva e l'ipotesi sarebbe da scartare.

### Calcoli

**Passo 1 — maglia d'ingresso**

```
V_CC = R_B·I_B + V_BE

I_B = (V_CC − V_BE)/R_B = (10 − 0,8)/5200 = 9,2/5200
    = 1,769·10⁻³ A = 1,77 mA
```

**Passo 2 — maglia d'uscita con ipotesi di saturazione**

```
V_CC = R_C·I_C + V_CEsat

I_C(sat) = (V_CC − V_CEsat)/R_C = (10 − 0,2)/330 = 9,8/330
         = 29,7·10⁻³ A = 29,7 mA
```

**Passo 3 — verifica**

```
I_B necessaria = I_C(sat)/h_FE = 29,7/50 = 0,594 mA

I_B disponibile = 1,77 mA   >   0,594 mA   ✓

Fattore di saturazione (overdrive):  1,77/0,594 = 2,98 ≈ 3
```

> [!success] Risultato Es. 6
> **Il BJT è effettivamente in saturazione**, con fattore di sovrapilotaggio ≈ 3.
> Punto di lavoro: `V_CE = V_CEsat = 0,2 V`, `I_C = 29,7 mA`, `I_B = 1,77 mA`.
>
> Controprova: se il transistor fosse in zona attiva, sarebbe
> `I_C = h_FE·I_B = 50 · 1,77 = 88,5 mA`, che darebbe
> `V_CE = 10 − 330·0,0885 = −19,2 V`, impossibile. È proprio questa impossibilità che
> **dimostra** la saturazione.

> [!danger] Trappola
> Fusi ha scritto `V_CC = R_B·I_B + R_C·I_C` — di nuovo le due maglie mescolate. Il prof.:
> *«errata perché l'equazione contiene al suo interno sia un elemento della maglia
> d'ingresso che è R_B che un elemento della maglia d'uscita R_C»*, e ha poi trascritto la
> procedura corretta in tre punti. **È lo stesso errore dell'es. 2: costa 2,00 punti su 10.**

---

## Es. 7 — Punto di lavoro con resistenza di emettitore

**Dati:** `V_CC = 20 V`, `V_BB = 10 V`, `R_C = 300 Ω`, `R_E = 200 Ω`, `R_B = 20 kΩ`,
`h_FE = 100`, `V_BE = 0,7 V` (zona attiva per ipotesi).

### Ragionamento
Rispetto all'es. 1 c'è `R_E`, che appartiene a **entrambe** le maglie: è attraversata da
`I_E`, non da `I_B` né da `I_C`. La maglia d'ingresso diventa quindi

```
V_BB = R_B·I_B + V_BE + R_E·I_E
```

e siccome `I_E = (h_FE + 1)·I_B`, resta una sola incognita. Questo effetto — la caduta su
`R_E` che si oppone alla corrente di base — è esattamente la **controreazione di corrente**
che stabilizza il punto di lavoro.

### Calcoli

**1) Maglia d'ingresso**

```
V_BB = R_B·I_B + V_BE + R_E·(h_FE + 1)·I_B

10 = 20 000·I_B + 0,7 + 200·101·I_B
10 − 0,7 = I_B·(20 000 + 20 200)
9,3 = 40 200·I_B

I_B = 9,3/40 200 = 231,3·10⁻⁶ A = 231 µA
```

**2) Correnti di collettore ed emettitore**

```
I_C = h_FE·I_B = 100 · 231,3·10⁻⁶ = 23,13·10⁻³ A = 23,1 mA
I_E = (h_FE + 1)·I_B = 101 · 231,3·10⁻⁶ = 23,37·10⁻³ A = 23,4 mA
```

**3) Tensioni**

```
V_E  = R_E·I_E = 200 · 23,37·10⁻³ = 4,67 V
V_RC = R_C·I_C = 300 · 23,13·10⁻³ = 6,94 V

V_CE = V_CC − R_C·I_C − R_E·I_E = 20 − 6,94 − 4,67 = 8,39 V
```

**4) Verifica zona attiva**

```
V_CE = 8,39 V  ≫  V_CEsat = 0,2 V   ✓
I_C(sat) = (V_CC − V_CEsat)/(R_C + R_E) = 19,8/500 = 39,6 mA  >  23,1 mA  ✓
```

> [!success] Risultato Es. 7
> **Punto di lavoro Q: V_CE = 8,39 V ; I_C = 23,1 mA**
> (`I_B = 231 µA`, `I_E = 23,4 mA`, `V_E = 4,67 V`)
>
> *Approssimando `I_E ≈ I_C` (cioè `h_FE + 1 ≈ h_FE`) si ottiene `I_B = 233 µA`,
> `I_C = 23,3 mA`, `V_CE = 8,38 V`: differenza sotto l'1%. L'approssimazione è lecita e
> Carli l'accetta, ma va dichiarata.*

> [!danger] Trappola
> Fusi ha scritto le due maglie e si è fermato: `V_BO = V_BB − R_B·I_B` e
> `V_CC = R_C·I_CO + I_E·R_E` — quest'ultima **dimentica V_CE**, che è proprio l'incognita.
> Annotazione del prof.: *«perché non ha continuato lo svolgimento dell'esercizio?»*.
> La maglia d'uscita completa è `V_CC = R_C·I_C + V_CE + R_E·I_E`.

---

# Verifica 3 — 29/05/2026 (valutata 03/06)
**JFET canale N (es. 1-5) + MOSFET enhancement (es. 6-8) · 8 esercizi**

Esiti di Fusi: 1 ~OK · 2 ~OK · 3 non svolto · 4 non svolto · 5 non svolto · 6 ~OK · 7 ~OK ·
8 errato → **3,00/10**.

> [!abstract] Le leggi che servono per tutti e otto
>
> **JFET a canale N** (`V_P < 0`, funziona a `V_GS` negativa, `I_G ≈ 0`):
> ```
> Equazione di Shockley:   I_D = I_DSS · (1 − V_GS/V_P)²
> Invertita:               V_GS = V_P · (1 − √(I_D/I_DSS))
> Saturazione (zona attiva): V_DS ≥ V_GS − V_P
> ```
>
> **MOSFET enhancement a canale N** (`V_t > 0`, funziona a `V_GS > V_t`, `I_G = 0`):
> ```
> Zona di saturazione:     I_D = K·(V_GS − V_t)²        se V_DS ≥ V_GS − V_t
> Invertita:               V_GS = V_t + √(I_D/K)
> Zona ohmica (triodo):    I_D = K·[2(V_GS − V_t)·V_DS − V_DS²]   se V_DS < V_GS − V_t
> ```
>
> **La regola d'oro che vale per entrambi: `I_G = 0`.** Il gate è isolato (MOSFET) o è una
> giunzione polarizzata inversamente (JFET). Conseguenze:
> - nessuna caduta di tensione su `R_G` → `V_G` = potenziale imposto dal circuito;
> - `I_S = I_D` (tutta la corrente di drain esce dal source);
> - **`R_G` non si calcola mai da una legge: si sceglie** (tipicamente 1÷10 MΩ).

---

## Es. 1 — Progetto della polarizzazione automatica di un JFET

**Dati:** `V_DD = 12 V`, `I_DO = 8 mA`, `V_GSO = −1 V`, `V_DSO = 7 V`.
**Incognite:** `R_D`, `R_S`, `R_G`.
**Circuito:** **autopolarizzazione** — gate a massa tramite `R_G`, `R_S` sul source, `R_D`
sul drain.

### Ragionamento
Il gate è a potenziale zero (`I_G = 0` → nessuna caduta su `R_G` → `V_G = 0`). La tensione
`V_GS` negativa che serve al JFET viene creata **dalla caduta su R_S**:

```
V_GS = V_G − V_S = 0 − R_S·I_D = −R_S·I_D
```

È elegante: il JFET si polarizza da solo, con una sola alimentazione.

### Calcoli

**Resistenza di source**

```
R_S = −V_GSO/I_DO = −(−1)/8·10⁻³ = 1/0,008 = 125 Ω
```

**Resistenza di drain** — maglia d'uscita `V_DD = R_D·I_D + V_DS + R_S·I_D`:

```
R_D = (V_DD − V_DSO − R_S·I_DO)/I_DO
    = (12 − 7 − 125·8·10⁻³)/8·10⁻³
    = (12 − 7 − 1)/0,008 = 4/0,008 = 500 Ω
```

**Resistenza di gate**

`R_G` **non è determinabile da nessuna equazione**: qualunque valore dà `V_G = 0`, perché
la corrente che la attraversa è nulla. Si sceglie in base a due criteri opposti:
- **grande**, per non caricare la sorgente di segnale collegata al gate (l'impedenza
  d'ingresso dello stadio è praticamente `R_G`);
- **non enorme**, perché la corrente di dispersione del gate (nA) su una `R_G` troppo grande
  produrrebbe uno sbilanciamento della polarizzazione.

Valore tipico **1 MΩ**; il prof. indica **5 MΩ**.

> [!success] Risultato Es. 1
> **R_S = 125 Ω · R_D = 500 Ω · R_G = 1 MΩ** (si sceglie; il prof. propone 5 MΩ)
>
> Verifica della zona di saturazione: `V_DS ≥ V_GS − V_P`. Con `V_P` non assegnato non si
> può controllare numericamente, ma `V_DS = 7 V` su `V_DD = 12 V` è un valore ampiamente
> prudenziale.

> [!danger] Trappola — l'unico vero errore di questa verifica su `R_G`
> Fusi ha scritto `R_G = V_GS/I_G` e poi `I_G = V_GS/(R_S + R_D) = −1,6 mA`, ottenendo
> `R_G = 625 Ω`. Sono **due errori concatenati**:
> 1. **`I_G ≈ 0`**, non 1,6 mA: la giunzione gate-canale del JFET è polarizzata
>    **inversamente**, ci passano nanoampere.
> 2. `R_G` non è in serie a `R_S` e `R_D`: è su un ramo a sé, percorso da corrente nulla.
>
> Il prof. ha cancellato tutto con una croce e scritto: **«si fissa: R_G = 5 MΩ»**.
> Lo stesso errore ritorna identico nell'es. 2 — è il concetto più frainteso di tutta la
> verifica.

---

## Es. 2 — Progetto della polarizzazione con equazione di Shockley

**Dati:** `V_DD = 18 V`, `I_DO = 5 mA`, `V_DSO = 10 V`, `V_P = −5 V`, `I_DSS = 12 mA`.
**Incognite:** `R_D`, `R_S`, `R_G`.

> [!warning] Sul segno di V_P
> Il testo scrive `V_P = 5 V`, ma per un **JFET a canale N** la tensione di pinch-off è
> **negativa**: `V_P = −5 V`. Va corretto, altrimenti la formula di Shockley dà risultati
> senza senso (`V_GS` positiva porterebbe il JFET in conduzione diretta della giunzione).

### Ragionamento
Rispetto all'es. 1 manca `V_GSO`, quindi bisogna **prima ricavarlo** dall'equazione di
Shockley invertita, e solo dopo si procede identici all'es. 1.

### Calcoli

**Passo 1 — V_GS dalla Shockley invertita**

```
I_D = I_DSS·(1 − V_GS/V_P)²

√(I_D/I_DSS) = 1 − V_GS/V_P

V_GS = V_P·(1 − √(I_D/I_DSS))

√(I_D/I_DSS) = √(5·10⁻³/12·10⁻³) = √0,4167 = 0,6455

V_GS = −5 · (1 − 0,6455) = −5 · 0,3545 = −1,77 V
```

*(Delle due radici, si scarta quella che darebbe `V_GS < V_P`, fuori dalla zona attiva.)*

**Passo 2 — R_S**

```
R_S = −V_GS/I_D = 1,77/5·10⁻³ = 354,5 Ω
```

**Passo 3 — R_D**

```
R_D = (V_DD − V_DS − R_S·I_D)/I_D
    = (18 − 10 − 354,5·5·10⁻³)/5·10⁻³
    = (18 − 10 − 1,77)/0,005 = 6,23/0,005 = 1245 Ω
```

**Passo 4 — R_G**: si sceglie, `1 MΩ` (prof.: 5 MΩ).

**Verifica della saturazione**

```
V_GS − V_P = −1,77 − (−5) = 3,23 V
V_DS = 10 V  ≥  3,23 V   ✓  JFET in zona attiva
```

> [!success] Risultato Es. 2
> **V_GSO = −1,77 V · R_S ≈ 355 Ω** (comm. 360 Ω) **· R_D ≈ 1,25 kΩ** (comm. 1,2 kΩ)
> **· R_G = 1 MΩ** (scelta)

> [!danger] Trappola
> Fusi aveva l'impostazione giusta (il prof. ha segnato «OK» su tutte e tre le relazioni!)
> ma ha sbagliato l'aritmetica dentro Shockley: da `−5·(1 − 0,6455)` ha ottenuto prima
> `−1,85`, poi `−4,9`, poi `−24 V`. Con `V_GS = −24 V` gli è uscito `R_S = 4,8 kΩ`.
> **Controllo di sanità mentale:** `V_GS` deve sempre stare **fra V_P e 0** (qui fra −5 e 0).
> Un `V_GS` fuori da quell'intervallo è certamente sbagliato.

---

## Es. 3 — Determinare le tensioni di alimentazione V_GG e V_DD

**Dati:** `I_DO = 5 mA`, `V_DSO = 10 V`, `V_GSO = −2 V`, `R_D = 6 kΩ`.
**Circuito:** polarizzazione **con batteria di gate separata** — `V_GG` in serie al gate,
source direttamente a massa, `R_D` fra drain e `V_DD`.

### Ragionamento
È il circuito più semplice di tutti, ed è per questo che l'esercizio vale poco tempo:
- il source è a massa → `V_S = 0` → `V_GS = V_G`;
- `I_G = 0` → nessuna caduta nel ramo di gate → `V_G` è **esattamente** la tensione della
  batteria (col segno imposto dalla polarità con cui è inserita);
- la maglia d'uscita ha solo `R_D` e il transistor, perché non c'è `R_S`.

### Calcoli

**Tensione di gate**

```
V_GS = V_G − V_S = V_G − 0 = V_G = −2 V

→  V_GG = 2 V, inserita con il MORSETTO POSITIVO verso massa
   (cioè con il gate al potenziale negativo rispetto al source)
```

**Tensione di alimentazione del drain** — maglia d'uscita `V_DD = R_D·I_D + V_DS`:

```
V_DD = R_D·I_DO + V_DSO = 6·10³ · 5·10⁻³ + 10
     = 30 + 10 = 40 V
```

> [!success] Risultato Es. 3
> **V_GG = 2 V** (polarità tale da rendere il gate negativo rispetto al source)
> **V_DD = 40 V**
>
> Nota: `R_D·I_D = 30 V` è tre volte `V_DS`. È una polarizzazione poco efficiente — tipica
> degli esercizi didattici, non di un progetto reale.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO»* — 0,00/1,00. Due somme.

---

## Es. 4 — Determinare il punto di lavoro e la tensione di alimentazione

**Dati:** `I_DSS = 12 mA`, `V_P = −4,5 V`, `V_DSO = 10 V`, `V_GSO = −2 V`, `R_D = 2,7 kΩ`.

### Ragionamento
Qui `V_GS` è **dato**, quindi Shockley si usa in **verso diretto** per ricavare `I_D`. Poi
la maglia d'uscita dà `V_DD`. È l'inverso dell'es. 2.

### Calcoli

**Passo 1 — corrente di drain da Shockley**

```
I_D = I_DSS · (1 − V_GS/V_P)²

V_GS/V_P = (−2)/(−4,5) = 0,4444

I_D = 12·10⁻³ · (1 − 0,4444)²
    = 12·10⁻³ · (0,5556)²
    = 12·10⁻³ · 0,3086 = 3,70·10⁻³ A = 3,70 mA
```

**Passo 2 — verifica della zona di saturazione**

```
V_GS − V_P = −2 − (−4,5) = 2,5 V
V_DS = 10 V  ≥  2,5 V   ✓  il JFET è in zona attiva, Shockley è applicabile
```

**Passo 3 — tensione di alimentazione**

```
V_DD = V_DS + R_D·I_D = 10 + 2700 · 3,70·10⁻³
     = 10 + 10,0 = 20 V
```

> [!success] Risultato Es. 4
> **Punto di lavoro Q: V_GSO = −2 V ; I_DO = 3,70 mA ; V_DSO = 10 V**
> **V_DD = 20 V**
>
> Il risultato esatto (`R_D·I_D = 10,0 V`, esattamente metà di `V_DD`) è la conferma che i
> conti tornano: l'esercizio è costruito perché `V_DS = V_RD = V_DD/2`.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO»* — 0,00/1,00.

---

## Es. 5 — Progetto della polarizzazione a partitore di un JFET

**Dati:** `I_DO = 3,5 mA`, `V_GSO = −1,5 V`, `V_DSO = 11 V`, `V_DD = 25 V`,
`R₁ + R₂ = 2 MΩ`, `R_D = 3 kΩ`.
**Incognite:** `R_S`, `R₁`, `R₂`.

### Ragionamento
È la polarizzazione **a partitore con autopolarizzazione** (la più stabile). A differenza
dell'autopolarizzazione pura, il gate **non** è a massa ma a un potenziale positivo `V_G`
fissato dal partitore. La `V_GS` negativa si ottiene facendo in modo che il source stia
**più in alto** del gate:

```
V_GS = V_G − V_S      con V_S = R_S·I_D
```

Quindi `V_S` deve superare `V_G` di 1,5 V. Il vincolo `R₁ + R₂ = 2 MΩ` chiude il problema
(altrimenti il partitore sarebbe indeterminato) e garantisce alta impedenza d'ingresso.

### Calcoli

**Passo 1 — caduta su R_D**

```
V_RD = R_D·I_DO = 3·10³ · 3,5·10⁻³ = 10,5 V
```

**Passo 2 — tensione di source dalla maglia d'uscita**
`V_DD = V_RD + V_DS + V_S`:

```
V_S = V_DD − V_DSO − V_RD = 25 − 11 − 10,5 = 3,5 V
```

**Passo 3 — R_S**

```
R_S = V_S/I_DO = 3,5/3,5·10⁻³ = 1000 Ω = 1 kΩ
```

**Passo 4 — tensione di gate dalla maglia d'ingresso**
`V_GS = V_G − V_S` → `V_G = V_GS + V_S`:

```
V_G = −1,5 + 3,5 = 2 V
```

**Passo 5 — partitore**

```
V_G = V_DD · R₂/(R₁ + R₂)

R₂ = V_G·(R₁ + R₂)/V_DD = 2 · 2·10⁶/25 = 160·10³ Ω = 160 kΩ

R₁ = (R₁ + R₂) − R₂ = 2·10⁶ − 160·10³ = 1,84·10⁶ Ω = 1,84 MΩ
```

**Verifica:** `V_G = 25 · 160k/2M = 25 · 0,08 = 2 V` ✓

> [!success] Risultato Es. 5
> **R_S = 1 kΩ · R₂ = 160 kΩ (verso massa) · R₁ = 1,84 MΩ (verso V_DD)**
> con `V_S = 3,5 V`, `V_G = 2 V`, `V_GS = −1,5 V`.
>
> `R₁ ∥ R₂ ≈ 147 kΩ` è l'impedenza d'ingresso vista dal segnale: alta, come richiesto da uno
> stadio a JFET.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO»* — 0,00/1,50. È l'esercizio da 1,50 punti più meccanico dei tre fascicoli.

---

## Es. 6 — MOSFET enhancement: determinare il punto di lavoro

**Dati:** `V_DD = 15 V`, `R₁ = 1,27 kΩ`, `R₂ = 825 kΩ`, `R_D = 1,8 kΩ`, `K = 0,6 mA/V²`,
`V_t = 3 V`. Ipotesi del testo: **MOS saturo**.
**Circuito:** partitore `R₁`(verso V_DD)–`R₂`(verso massa) sul gate, source a massa,
`R_D` sul drain.

### Ragionamento
Source a massa → `V_GS = V_G = V_R2`, imposta direttamente dal partitore (`I_G = 0`, il
partitore è a vuoto). Poi Shockley-MOS dà `I_D`, e la maglia d'uscita dà `V_DS`.
**Ma l'ipotesi «MOS saturo» va sempre verificata alla fine**, e qui è il punto dell'esercizio.

### Calcoli

**Passo 1 — V_GS dal partitore**

```
V_GS = V_R2 = V_DD · R₂/(R₁ + R₂)
     = 15 · 825·10³/(1,27·10³ + 825·10³)
     = 15 · 825/826,27 = 14,98 V   ≈ 14,9 V
```

**Passo 2 — I_D in ipotesi di saturazione**

```
I_D = K·(V_GS − V_t)² = 0,6·10⁻³ · (14,98 − 3)²
    = 0,6·10⁻³ · (11,98)² = 0,6·10⁻³ · 143,5
    = 86,1·10⁻³ A ≈ 85 mA
```

**Passo 3 — verifica dell'ipotesi (il passaggio decisivo)**

```
V_DS = V_DD − R_D·I_D = 15 − 1800 · 0,085 = 15 − 153 = −138 V
```

**Impossibile**: `V_DS` non può essere negativa in questo circuito. **L'ipotesi di
saturazione è falsa**: il MOSFET lavora in **zona ohmica (triodo)**.

**Passo 4 — soluzione corretta in zona ohmica**

```
I_D = K·[2(V_GS − V_t)·V_DS − V_DS²]        (equazione del MOS in triodo)
I_D = (V_DD − V_DS)/R_D                      (maglia d'uscita)

Uguagliando, con V_GS − V_t = 11,98 V:

(15 − V_DS)/1800 = 0,6·10⁻³·[2·11,98·V_DS − V_DS²]
15 − V_DS        = 1,08·[23,96·V_DS − V_DS²]
15 − V_DS        = 25,88·V_DS − 1,08·V_DS²

1,08·V_DS² − 26,88·V_DS + 15 = 0

Δ  = 26,88² − 4·1,08·15 = 722,5 − 64,8 = 657,7
√Δ = 25,64

V_DS = (26,88 ± 25,64)/2,16   →   V_DS = 0,574 V   oppure   V_DS = 24,3 V (scartata: > V_DD)

I_D = (15 − 0,574)/1800 = 8,01·10⁻³ A = 8,0 mA
```

Verifica: `V_DS = 0,574 V < V_GS − V_t = 11,98 V` ✓ → zona ohmica confermata.

> [!success] Risultato Es. 6
> **V_GS = 14,98 V** (imposta dal partitore)
> **L'ipotesi «MOS saturo» del testo NON è verificata**: il MOSFET lavora in **zona ohmica**.
> **Punto di lavoro reale: V_DS ≈ 0,57 V ; I_D ≈ 8,0 mA.**
>
> Il MOSFET si comporta praticamente da interruttore chiuso: `R_DSon ≈ 0,574/0,008 = 72 Ω`.

> [!warning] Il dato è probabilmente un refuso del testo
> Se `R₁` fosse **1,27 MΩ** (e non 1,27 kΩ) l'esercizio tornerebbe pulito:
> ```
> V_GS = 15 · 825/(1270 + 825) = 5,91 V
> I_D  = 0,6·10⁻³·(5,91 − 3)² = 5,07 mA
> V_DS = 15 − 1800·5,07·10⁻³ = 5,87 V
> Verifica: V_DS = 5,87 ≥ V_GS − V_t = 2,91  ✓  MOS SATURO
> ```
> Cioè **Q(V_DS = 5,87 V ; I_D = 5,07 mA)**, che è una polarizzazione sensata per un
> amplificatore. All'esame conviene: svolgere con i dati letterali, accorgersi che
> l'ipotesi non regge, **dichiararlo per iscritto**, e — se si sospetta il refuso —
> aggiungere la soluzione coerente. Il prof. premia il controllo, non il numero.

> [!danger] Trappola
> Fusi ha scritto `I_D = 84,9 A` (ampere invece di milliampere) e ha usato una relazione
> `V_GS = V_t + √(I_D/R_D)` che il prof. ha cancellato con «NON SERVE»: mescola una corrente
> con una resistenza sotto radice, è dimensionalmente impossibile. La sola relazione da usare
> è `I_D = K·(V_GS − V_t)²`, e `V_GS` viene **solo** dal partitore.

---

## Es. 7 — Progetto della polarizzazione di un MOSFET (senza R_S)

**Dati:** `V_DD = 25 V`, `I_D = 3 mA`, `K = 0,3 mA/V²`, `V_t = 4 V`, `R₁ + R₂ = 10 MΩ`.
Ipotesi: MOS saturo. **Incognite:** `R_D`, `R₁`, `R₂`.
**Circuito:** partitore sul gate, source a massa, `R_D` sul drain.

### Ragionamento
Corrente e transistor sono dati, quindi `V_GS` è **determinata**. `V_DS` invece è **libera**:
è una scelta di progetto, vincolata solo dalla condizione di saturazione
`V_DS ≥ V_GS − V_t`. Si sceglie un valore comodo e ampiamente dentro la zona attiva.

### Calcoli

**Passo 1 — V_GS dall'equazione del MOS invertita**

```
I_D = K·(V_GS − V_t)²   →   V_GS = V_t + √(I_D/K)

√(I_D/K) = √(3·10⁻³ / 0,3·10⁻³) = √10 = 3,162

V_GS = 4 + 3,162 = 7,16 V
```

**Passo 2 — scelta di V_DS**

```
Vincolo di saturazione:  V_DS ≥ V_GS − V_t = 7,16 − 4 = 3,16 V

Si sceglie  V_DS = V_DD/2 = 12,5 V   (ampiamente > 3,16 V e < V_DD, escursione simmetrica)
```

**Passo 3 — R_D dalla maglia d'uscita**

```
R_D = (V_DD − V_DS)/I_D = (25 − 12,5)/3·10⁻³ = 12,5/0,003 = 4167 Ω ≈ 4,17 kΩ
```

**Passo 4 — partitore di gate** (source a massa → `V_G = V_GS`)

```
V_GS = V_DD · R₂/(R₁ + R₂)

R₂ = (V_GS/V_DD)·(R₁ + R₂) = (7,16/25) · 10·10⁶
   = 0,2865 · 10⁷ = 2,86·10⁶ Ω = 2,86 MΩ

R₁ = 10·10⁶ − 2,86·10⁶ = 7,14·10⁶ Ω = 7,14 MΩ
```

**Verifica finale**

```
V_G = 25 · 2,86/10 = 7,16 V ≈ V_GS  ✓
I_D = 0,3·10⁻³·(7,16 − 4)² = 0,3·10⁻³·9,99 = 3,0 mA  ✓
V_DS = 12,5 V ≥ 3,16 V  ✓  saturo
```

> [!success] Risultato Es. 7
> **R_D ≈ 4,17 kΩ (comm. 3,9 kΩ) · R₂ ≈ 2,86 MΩ (verso massa) · R₁ ≈ 7,14 MΩ (verso V_DD)**
> con `V_GS = 7,16 V`, `V_DS = 12,5 V` (scelta di progetto).
>
> Una `V_DS` diversa dà `R_D`, `R₁` e `R₂` diversi ma ugualmente validi, purché resti
> `V_DS ≥ 3,16 V` e la scelta sia dichiarata. Solo `V_GS = 7,16 V` è imposta dai dati.

> [!warning] Correzione di una versione precedente di questa nota (2026-08-30)
> Qui era riportato `V_DD = 15 V`, con `R_D = 2 kΩ`, `R₂ = 4,78 MΩ`, `R₁ = 5,22 MΩ`. Rileggendo
> la scansione a 300 dpi il testo dell'es. 7 dice **`V_DD = 25 V`**: i 15 V sono la `V_DD`
> dell'**es. 6**, che sta subito sopra sulla stessa pagina. Anche Fusi aveva lavorato con 15 V.
> Il «2» dell'es. 7 è tondo, l'«1» dell'es. 6 è un tratto dritto: alla risoluzione piena si
> distinguono.

> [!danger] Trappola
> Fusi ha poi scritto
> `V_GS = V_t + √(I_D/R_D) = 4 + √(3·10⁻³/2·10³) = 4,1 V` — **la stessa relazione
> dimensionalmente impossibile dell'es. 6**: sotto radice va `I_D/K`, non `I_D/R_D`.
> Con `V_GS = 4,1 V` e `V_DD = 15 V` gli è uscito `R₂ = 2,73 MΩ`.
> Il prof. ha cerchiato la formula e scritto **«relazione errata»**, poi ha ricalcolato lui
> `V_GS = √(I_D/K) + V_t = 7,16 V`.

---

## Es. 8 — Progetto della polarizzazione di un MOSFET con R_S

**Dati:** `I_DO = 8 mA`, `V_GSO = 6 V`, `V_DSO = 10 V`, `V_DD = 15 V`, `V_S = 3 V`,
`R₁ + R₂ = 2 MΩ`.
**Incognite:** `R_D`, `R_S`, `R₁`, `R₂`.

### Ragionamento
Rispetto all'es. 7 c'è `R_S`, che introduce **due differenze**, ed entrambe sono le trappole
che Fusi ha centrato:

1. la maglia d'uscita ha **tre** cadute: `V_DD = V_RD + V_DS + V_S`;
2. il gate non è più a `V_GS` ma a `V_G = V_GS + V_S`, perché il source è sollevato da massa.

`R_S` serve a stabilizzare il punto di lavoro: se `I_D` tende a crescere, `V_S` sale, `V_GS`
scende e `I_D` viene riportata giù (controreazione).

### Calcoli

**Passo 1 — R_S**

```
R_S = V_S/I_DO = 3/8·10⁻³ = 375 Ω
```

**Passo 2 — R_D dalla maglia d'uscita completa**

```
V_DD = R_D·I_D + V_DS + V_S

R_D = (V_DD − V_DSO − V_S)/I_DO = (15 − 10 − 3)/8·10⁻³
    = 2/0,008 = 250 Ω
```

**Passo 3 — tensione di gate**

```
V_G = V_GS + V_S = 6 + 3 = 9 V
```

**Passo 4 — partitore**

```
V_G = V_DD · R₂/(R₁ + R₂)

R₂ = (V_G/V_DD)·(R₁ + R₂) = (9/15) · 2·10⁶ = 0,6 · 2·10⁶ = 1,2·10⁶ Ω = 1,2 MΩ

R₁ = 2·10⁶ − 1,2·10⁶ = 0,8·10⁶ Ω = 800 kΩ
```

**Verifica**

```
V_G  = 15 · 1,2/2 = 9 V  ✓
V_GS = V_G − V_S = 9 − 3 = 6 V  ✓
Maglia d'uscita: 250·0,008 + 10 + 3 = 2 + 10 + 3 = 15 V = V_DD  ✓
```

> [!success] Risultato Es. 8
> **R_S = 375 Ω · R_D = 250 Ω · R₂ = 1,2 MΩ (verso massa) · R₁ = 800 kΩ (verso V_DD)**
>
> Valori commerciali: `R_S = 390 Ω`, `R_D = 240 Ω`, `R₂ = 1,2 MΩ`, `R₁ = 820 kΩ`.

> [!danger] Trappola — l'unico «ERRATO» pieno di questa verifica
> Fusi ha commesso **entrambi** gli errori tipici del circuito con `R_S`:
> 1. `R_D = (V_DD − V_DS)/I_D = (15−10)/8m = 625 Ω` → **ha dimenticato V_S** nella maglia
>    d'uscita. Il prof. ha aggiunto in rosso «`− V_S`».
> 2. `R₂ = (V_R2/V_DD)·(R₁+R₂)` con `V_R2 = 6 V` invece di 9 V → **ha usato V_GS al posto di
>    V_G**, dimenticando che il source è a 3 V. Il prof. ha aggiunto in rosso «`+ V_S`»,
>    scrivendo `V_R2 = V_GS + V_S`.
>
> Ha inoltre scritto `I_S = R_S/(R_D+R_S)·I_D` e `V_S = R_S/(R_D+R_S)·V_DD`: sono formule da
> partitore applicate a un ramo che **non è un partitore** — `R_D` e `R_S` non sono in serie
> fra loro con niente in mezzo, c'è il transistor. Vale sempre `I_S = I_D` e
> `V_S = R_S·I_D`.

---

# Appendice — Le sei trappole che valgono il 70% dei punti persi

Un riassunto operativo, ordinato per quante volte Carli l'ha segnata in rosso sui tre
fascicoli.

| # | Trappola | Dove compare | Come non caderci |
|---|---|---|---|
| 1 | **Maglie d'ingresso e d'uscita mescolate** (`R_B` con `R_C`) | V2 es. 2, 6, 7 | Prima di scrivere l'equazione, chiediti: *questa resistenza è percorsa da I_B, I_C o I_E?* Le due maglie condividono solo il ramo di emettitore. |
| 2 | **`I_G ≈ 0` dimenticato** → `R_G` calcolata da una legge | V3 es. 1, 2 | Nel JFET/MOSFET il gate non assorbe corrente. **`R_G` si sceglie (1÷10 MΩ), non si calcola.** |
| 3 | **`V_S` dimenticata** nella maglia d'uscita o nel partitore | V2 es. 3, V3 es. 8 | Se c'è `R_S`/`R_E`: `V_DD = V_RD + V_DS + V_S` e `V_G = V_GS + V_S`. Tre termini, non due. |
| 4 | **Formule dimensionalmente impossibili** (`√(I_D/R_D)`, `arctan(1/\|Z\|)`) | V1 es. 1B, V3 es. 6, 7 | Controlla le unità di misura del risultato: se non sono volt/ampere/ohm come devono, la formula è sbagliata a prescindere dai numeri. |
| 5 | **Valori numerici sostituiti male** (10 al posto di 12, f errata) | V1 es. 1A, V2 es. 1 | Riscrivi i dati in colonna prima di iniziare e spuntali man mano che li usi. |
| 6 | **Ipotesi non verificata a fine esercizio** (saturo/attivo) | V3 es. 6, V2 es. 6 | Ogni esercizio con un'ipotesi (`MOS saturo`, `BJT in zona attiva`) si **chiude** con la verifica. Se non regge, dillo e rifai con l'altra zona. |

> [!tip] La differenza fra 3/10 e 7/10
> Sui tre fascicoli, **7 esercizi su 21 sono stati lasciati completamente in bianco** — e
> valgono 8,00 punti su 30. Sono, in ordine: V1 es. 5 (due divisioni), V2 es. 4 e 5, V3
> es. 3, 4 e 5. Nessuno di questi richiede più di dieci minuti.
> Il messaggio dei fascicoli non è «gli esercizi sono difficili»: è **«va svolto tutto»**.

---

## Collegamenti

- [[05 - Verifiche FUSI (Carli)]] — come Carli formula, corregge e valuta
- [[Formulario rapido]] — tutte le formule usate qui, in forma compatta
- [[Esercizi - Impedenza dei bipoli R, L, C]] · [[Esercizi - Filtri passivi del primo ordine]] — V1
- [[Esercizi - BJT]] · [[Esercizi - Amplificatori a BJT]] — V2
- [[Esercizi - JFET]] · [[Esercizi - MOSFET]] — V3
- [[Calendario]] — giorni 1, 4, 7, 9, 10, 11
