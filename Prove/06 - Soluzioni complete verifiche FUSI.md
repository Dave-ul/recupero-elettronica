---
tags: [recupero, elettronica, verifiche, carli, soluzioni, fonte-derivata]
fonte: "risoluzione integrale dei 21 esercizi contenuti nelle tre verifiche del Prof. Carlo Carli"
file: "Fonti/FUSI_02-03-26_260616_183723.pdf · Fonti/FUSI_24-04-26_260616_183749.pdf · Fonti/FUSI_29-05-26_260616_183828.pdf"
aggiunto: 2026-08-28
verificato: "2026-08-28 — testi riletti pagina per pagina dai tre PDF (scansioni senza strato di testo); ogni risultato ricalcolato da zero · 2026-08-30 — corretta la V_DD della Verifica 3 es. 7 (25 V, non 15 V) su ritaglio a 300 dpi · 2026-08-31 — aggiunti gli schemi circuitali ASCII a 20 esercizi su 21"
---

# 06 — Soluzioni complete delle verifiche FUSI

Companion di [[05 - Verifiche FUSI (Carli)]]. Quella nota racconta **come Carli corregge e
valuta**; questa contiene lo **svolgimento completo di tutti e 21 gli esercizi**, compresi i
sei che Fusi non ha svolto per niente e i sei che ha sbagliato.

> [!info] Come leggere questa nota
> Per ogni esercizio trovi: **Testo** (dati come li ha scritti il prof.) → **Circuito**
> (schema ASCII della topologia, con sopra i dati e sotto le maglie che servono) →
> **Ragionamento** (quale legge si applica e perché) → **Calcoli** → **Risultato**.
> L'unico senza schema è il 2 della Verifica 1: è puro calcolo di poli, non c'è circuito. Dove Fusi ha sbagliato,
> un blocco *Trappola* isola l'errore preciso, perché è quello il valore didattico dei
> fascicoli.

> [!warning] Convenzioni usate ovunque
> - $\omega = 2\pi f$; $X_L = \omega L$; $X_C = 1/(\omega C)$; $Z_L = j\omega L$; $Z_C = -j/(\omega C) = 1/(j\omega C)$.
> - Per un numero complesso $Z = a + jb$: $|Z| = \sqrt{a^{2}+b^{2}}$, $\arg Z = \arctan (b/a)$
>   (con la correzione di quadrante se $a < 0$).
> - Resistenze arrotondate ai valori commerciali della serie E24 solo dove indicato.

---

# Verifica 1 — 13/02/2026 (valutata 02/03)
**Circuiti in corrente alternata e filtri passivi del primo ordine · 6 esercizi**

Esiti di Fusi: 1 ~OK · 2 errato · 3 ~OK · 4 errato · 5 non svolto · 6 OK → $3{,}00/10$.

---

## Es. 1 — Modulo e argomento dell'impedenza equivalente

### Circuito

```
                       Ī →
 1A)   A ●───[ R = 1 kΩ ]───┐
                            │
                           ───    C = 10 nF
                           ───
                            │
       B ●──────────────────┘        Z̄_eq = R − jX_C     f = 10 kHz


                       Ī →
 1B)   A ●───[ R = 330 Ω ]──┐
                            │
                            ∩
                            ∩     L = 12 mH
                            ∩
                            │
       B ●──────────────────┘        Z̄_eq = R + jX_L     f = 10 kHz

 Il secondo componente è disegnato in verticale ma nessun ramo lo scavalca:
 maglia unica → i due bipoli sono in SERIE, le impedenze si sommano.
```

### Ragionamento comune ai due bipoli
In entrambi i casi la corrente $Ī$ entra da un morsetto, attraversa il primo componente e
torna dall'altro morsetto attraversando il secondo: i due bipoli sono **in serie**, non in
parallelo. Il disegno trae in inganno perché il secondo componente è disegnato in verticale,
ma non c'è nessun ramo che lo scavalchi: è una maglia unica.

Per una serie le impedenze si **sommano come numeri complessi**:
$\bar{Z}_{eq} = \bar{Z}_{1} + \bar{Z}_{2}$.

---

### 1A) Serie R–C

**Dati:** $C = 10\ \text{nF}$, $R = 1\ \text{k}\Omega$, $f = 10\ \text{kHz}$.

**Calcoli**

$$\begin{aligned}
\omega &= 2\pi f = 2\pi \cdot 10^{4} = 6{,}2832 \cdot 10^{4}\ \text{rad/s} \\[8pt]
X_C &= 1/(\omega C) = 1 / (6{,}2832\cdot 10^{4} \cdot 10\cdot 10^{-9}) \\[2pt]
&= 1 / (6{,}2832\cdot 10^{-4}) = 1591{,}5\,\Omega \\[8pt]
\bar{Z}_{eq} &= R - jX_C = 1000 - j1591{,}5\,\Omega \\[8pt]
|Z_{eq}| &= \sqrt{1000^{2} + 1591{,}5^{2}} = \sqrt{1{,}000\cdot 10^{6} + 2{,}533\cdot 10^{6}} \\[2pt]
&= \sqrt{3{,}533\cdot 10^{6}} = 1879{,}6\,\Omega \\[8pt]
\varphi &= \arctan (-1591{,}5 / 1000) = \arctan (-1{,}5915) = -57{,}86^\circ
\end{aligned}$$

> [!success] Risultato 1A
> $|Z_{eq}| \approx 1{,}88\ \text{k}\Omega$, $\varphi \approx -57{,}9^\circ$ (bipolo **ohmico-capacitivo**: la corrente è in
> anticipo sulla tensione, argomento negativo).

> [!danger] Trappola — l'errore di Fusi qui
> Ha usato $f = 1\ \text{kHz}$ invece dei 10 kHz del testo ($\omega = 6{,}3\cdot 10^{3}$ anziché $6{,}28\cdot 10^{4}$), e ha
> poi scritto $\bar{Z}_C = -1/(j\omega C)$ con un segno meno di troppo: $1/(j\omega C)$ vale $già$ $-j/(\omega C)$,
> perché $1/j = -j$. Aggiungendo un altro meno l'impedenza capacitiva diventa induttiva e
> l'argomento cambia segno. Il prof. ha cerchiato in rosso proprio quel $-1/(j\omega C)$.

---

### 1B) Serie R–L

**Dati:** $R = 330\,\Omega$, $L = 12\ \text{mH}$, $f = 10\ \text{kHz}$.

**Calcoli**

$$\begin{aligned}
\omega &= 2\pi \cdot 10^{4} = 6{,}2832 \cdot 10^{4}\ \text{rad/s} \\[8pt]
X_L &= \omega L = 6{,}2832\cdot 10^{4} \cdot 12\cdot 10^{-3} = 753{,}98\,\Omega \\[8pt]
\bar{Z}_{eq} &= R + jX_L = 330 + j754\,\Omega \\[8pt]
|Z_{eq}| &= \sqrt{330^{2} + 753{,}98^{2}} = \sqrt{108\,900 + 568\,486} \\[2pt]
&= \sqrt{677\,386} = 823{,}0\,\Omega \\[8pt]
\varphi &= \arctan (753{,}98 / 330) = \arctan (2{,}2848) = +66{,}36^\circ
\end{aligned}$$

> [!success] Risultato 1B
> $|Z_{eq}| \approx 823\,\Omega$, $\varphi \approx +66{,}4^\circ$ (bipolo **ohmico-induttivo**: corrente in ritardo,
> argomento positivo).

> [!danger] Trappola
> Fusi aveva $\bar{Z}_L = 7{,}5\cdot 10^{2}$ e $\bar{Z}_R = 3{,}3\cdot 10^{2}$ giusti, ma nel modulo ha scritto
> $\sqrt{330^{2} + 75^{2}}$ perdendo un ordine di grandezza sulla reattanza, e nell'argomento ha usato
> $\arctan (1/328{,}9)$ invece di $\arctan (X_L/R)$. **L'argomento non è mai $\arctan (1/|Z|)$**:
> è sempre $\arctan (parte immaginaria / parte reale)$.

---

## Es. 2 — Poli delle funzioni di trasferimento

### Ragionamento
I **poli** di $G(s)$ sono le radici del **denominatore** $D(s) = 0$; gli **zeri** sono le
radici del numeratore. Non c'entra nulla il limite di $G(s)$: si annulla il denominatore e
si risolve.

---

### 2A)

$G(s) = 3 / (s^{2} + 5s + 6)$

$$\begin{aligned}
D(s) &= s^{2} + 5s + 6 = 0 \\[2pt]
\Delta &= 25 - 24 = 1; \sqrt{\Delta } = 1 \\[2pt]
s &= (-5 \pm 1)/2 \;\Rightarrow\; s_{1} = -2 , s_{2} = -3
\end{aligned}$$

Oppure per scomposizione diretta: $s^{2} + 5s + 6 = (s+2)(s+3)$.

> [!success] Risultato 2A
> **Poli: s₁ = −2 rad/s, s₂ = −3 rad/s.** Entrambi reali, negativi e distinti → sistema
> **stabile**, del secondo ordine sovrasmorzato, senza zeri.

---

### 2B)

$G(s) = (s + 1) / [3s(s + 5)]$

$$\begin{aligned}
D(s) &= 3s(s + 5) = 0 \;\Rightarrow\; s_{1} = 0 , s_{2} = -5 \\[2pt]
N(s) &= s + 1 = 0 \;\Rightarrow\; z_{1} = -1
\end{aligned}$$

> [!success] Risultato 2B
> **Poli: s₁ = 0 (polo nell'origine), s₂ = −5 rad/s.** In più uno **zero in z₁ = −1 rad/s**.
> Il polo nell'origine significa un comportamento **integratore**: il sistema è al limite
> della stabilità (marginalmente stabile).

> [!danger] Trappola
> Fusi ha calcolato $lim(s\;\Rightarrow\;…) G(s)$ ottenendo «0,6», che è il **guadagno statico** di 2A,
> non un polo. Il prof. ha scritto in rosso: *«completamente errato»*, e poi ha annotato lui
> stesso la procedura giusta: $D(s) = 0 \;\Rightarrow\; s^{2} + 5s + 6 = 0$.

---

## Es. 3 — Risposta in ampiezza e in fase di un quadripolo

**Circuito:** $R_{1}$ in serie sul ramo d'ingresso; sul nodo d'uscita $R_{2}$ e $L$ in **parallelo**
verso massa; $v_o(t)$ presa ai capi del parallelo.

**Dati:** $R_{1} = 2{,}2\ \text{k}\Omega$, $R_{2} = 5{,}6\ \text{k}\Omega$, $L = 1\ \text{mH}$.
Frequenze richieste: $f_{1} = 0\ \text{Hz}$, $f_{2} = 100\ \text{kHz}$, $f_{3} = 20\ \text{MHz}$.

### Circuito

```
        ●───[ R₁ = 2,2 kΩ ]───┬──────────┬───●
        │                     │          │
        │                    ┌┴┐         ∩
  v_i   │                    │ │ R₂      ∩    L = 1 mH      v_o
        │                    │ │ 5,6 kΩ  ∩
        │                    └┬┘         │
        ●─────────────────────┴──────────┴───●

 Partitore fra R₁ e il parallelo (R₂ ∥ Z̄_L); l'uscita è sul parallelo.
 In continua L è un corto → v_o = 0; ad alta frequenza L è aperto → v_o = v_i·R₂/(R₁+R₂).
```

### Ragionamento
È un **partitore di tensione fra impedenze**. Prima si riduce il parallelo $R_{2} ∥ Z_L$, poi
si applica la formula del partitore:

$$\begin{aligned}
\bar{Z}_p &= \frac{\bar{Z}_L \cdot R_2}{\bar{Z}_L + R_2}\,,\qquad \bar{Z}_L = j\omega L \\[8pt]
Ḡ(j\omega ) &= \bar{V}_o/\bar{V}_i = \bar{Z}_p / (R_{1} + \bar{Z}_p)
\end{aligned}$$

Sostituendo e semplificando (moltiplico numeratore e denominatore per $R_{2} + j\omega L$):

$$\bar{G}(j\omega) = \frac{j\omega L\cdot R_2}{R_1R_2 + j\omega L\,(R_1 + R_2)}$$

Da qui si leggono direttamente le due risposte richieste:

**Risposta in ampiezza**

$$|G(\omega)| = \frac{\omega L\cdot R_2}{\sqrt{(R_1R_2)^2 + \big(\omega L(R_1+R_2)\big)^2}}$$

**Risposta in fase**

$$\varphi(\omega) = 90^\circ - \arctan\!\left[\frac{\omega L(R_1+R_2)}{R_1R_2}\right]$$

Il $+90^\circ$ viene dalla $j$ al numeratore (uno zero nell'origine), l'arcotangente dal polo.
**È un filtro passa-alto del primo ordine.**

Costanti caratteristiche:

$$\begin{aligned}
\omega _t &= R_{1}R_{2} / [L(R_{1}+R_{2})] = (2200\cdot 5600) / (1\cdot 10^{-3} \cdot 7800) \\[2pt]
&= 12{,}32\cdot 10^{6} / 7{,}8 = 1{,}5795\cdot 10^{6}\ \text{rad/s} \\[2pt]
f_t &= \omega _t/2\pi = 251{,}4\ \text{kHz} \\[8pt]
\text{guadagno asintotico }(\omega\to\infty):\;\; R_2/(R_1+R_2) &= 5600/7800 = 0{,}718
\end{aligned}$$

### Calcoli alle tre frequenze

$1) f_{1} = 0\ \text{Hz} (continua)$

$$\begin{aligned}
\omega &= 0 \;\Rightarrow\; \bar{Z}_L = j\cdot 0\cdot L = 0
   \quad\text{(l'induttore è un CORTOCIRCUITO)} \\[2pt]
|G| &= 0\quad\text{(0 in scala lineare, −∞ dB)} \\[2pt]
\varphi &= +90^\circ
\end{aligned}$$

Interpretazione fisica: in continua l'induttore cortocircuita l'uscita a massa, quindi non
passa nulla. Coerente con un passa-alto.

$2) f_{2} = 100\ \text{kHz}$

$$\begin{aligned}
\omega &= 2\pi \cdot 10^{5} = 6{,}2832\cdot 10^{5}\ \text{rad/s} \\[2pt]
\omega L &= 6{,}2832\cdot 10^{5} \cdot 10^{-3} = 628{,}3\,\Omega \\[8pt]
\text{numeratore}:\;\; \omega L\cdot R_2 &= 628{,}3 \cdot 5600 = 3{,}519\cdot 10^{6} \\[2pt]
R_{1}R_{2} &= 2200 \cdot 5600 = 12{,}32\cdot 10^{6} \\[2pt]
\omega L(R_{1}+R_{2}) &= 628{,}3 \cdot 7800 = 4{,}901\cdot 10^{6} \\[2pt]
&\text{denominatore}:\;\; \sqrt{(12{,}32\cdot 10^{6})^{2} + (4{,}901\cdot 10^{6})^{2}} = \sqrt{1{,}758\cdot 10^{14}} = 1{,}326\cdot 10^{7} \\[8pt]
|G| &= 3{,}519\cdot 10^{6} / 1{,}326\cdot 10^{7} = 0{,}265 \;\Rightarrow\; 20\cdot \log _{10}(0{,}265) = -11{,}5\ \text{dB} \\[2pt]
\varphi &= 90^\circ - \arctan (4{,}901/12{,}32) = 90^\circ - 21{,}7^\circ = +68{,}3^\circ
\end{aligned}$$

$3) f_{3} = 20\ \text{MHz}$

$$\begin{aligned}
\omega &= 2\pi \cdot 2\cdot 10^{7} = 1{,}2566\cdot 10^{8}\ \text{rad/s} \\[2pt]
\omega L &= 1{,}2566\cdot 10^{8} \cdot 10^{-3} = 1{,}2566\cdot 10^{5}\,\Omega \\[8pt]
\text{numeratore}:\;\; 1{,}2566\cdot 10^{5} \cdot 5600 &= 7{,}037\cdot 10^{8} \\[2pt]
\omega L(R_{1}+R_{2}) &= 1{,}2566\cdot 10^{5} \cdot 7800 = 9{,}802\cdot 10^{8} \\[2pt]
&\text{denominatore}:\;\; \sqrt{(1{,}232\cdot 10^{7})^{2} + (9{,}802\cdot 10^{8})^{2}} \approx 9{,}803\cdot 10^{8} \\[8pt]
|G| &= 7{,}037\cdot 10^{8} / 9{,}803\cdot 10^{8} = 0{,}718 \;\Rightarrow\; -2{,}9\ \text{dB} \\[2pt]
\varphi &= 90^\circ - \arctan (9{,}802\cdot 10^{8} / 1{,}232\cdot 10^{7}) = 90^\circ - 89{,}3^\circ = +0{,}7^\circ
\end{aligned}$$

> [!success] Risultato Es. 3
> | f | \|G\| | \|G\|_dB | φ |
> |---|---|---|---|
> | 0 Hz | 0 | −∞ | +90° |
> | 100 kHz | 0,265 | −11,5 dB | +68,3° |
> | 20 MHz | 0,718 | −2,9 dB | +0,7° |
>
> Filtro **passa-alto** con $f_t \approx 251\ \text{kHz}$ e guadagno in banda passante $0{,}718$ (−2,9 dB).
> A 20 MHz siamo ben oltre il taglio: il guadagno è già a regime e la fase quasi nulla.

---

## Es. 4 — Funzione di trasferimento dei quadripoli

### Circuito

```
 4A)  R in serie, L verso massa, uscita su L  →  passa-ALTO

        ●───[ R = 560 Ω ]───┬───●
        │                   │
        │                   ∩
  v_i   │                   ∩    L = 3 mH        v_o
        │                   ∩
        ●───────────────────┴───●


 4B)  L in serie, R verso massa, uscita su R  →  passa-BASSO

        ●───[ L = 0,3 mH ]───┬───●
        │                    │
        │                   ┌┴┐
  v_i   │                   │ │  R = 1,2 kΩ      v_o
        │                   └┬┘
        ●────────────────────┴───●

 Stessa coppia di componenti, filtro opposto: conta SU QUALE si preleva l'uscita.
```

### Ragionamento comune
Entrambi sono **partitori di tensione** fra due impedenze in serie, con l'uscita presa ai
capi della seconda:

$$\begin{aligned}
\bar{G}(s) &= \frac{\bar{Z}_{uscita}}{\bar{Z}_{serie} + \bar{Z}_{uscita}}
\end{aligned}$$

Con $Z_R = R$ e $Z_L = sL$. Il tipo di filtro dipende da **su quale componente si preleva
l'uscita**, non dall'ordine in cui sono disegnati.

---

### 4A) R in serie, L in parallelo, uscita su L

**Dati:** $R = 560\,\Omega$, $L = 3\ \text{mH}$.

$$\begin{aligned}
G(s) &= sL / (R + sL) \\[2pt]

\end{aligned}$$
Divido numeratore e denominatore per L:
$$\begin{aligned}
G(s) &= s / (s + R/L) \\[8pt]
\omega _t &= R/L = 560 / (3\cdot 10^{-3}) = 1{,}867\cdot 10^{5}\ \text{rad/s} \\[2pt]
f_t &= \omega _t/2\pi = 29{,}7\ \text{kHz}
\end{aligned}$$

Forma normalizzata (quella che Carli si aspetta):

$$G(s) = \frac{s/\omega_t}{1 + s/\omega_t},
  \qquad \omega_t = 1{,}867\cdot 10^{5}\ \text{rad/s}$$

> [!success] Risultato 4A
> $G(s) = sL/(R+sL) = s/(s + 1{,}867\cdot 10^{5})$ — **filtro passa-alto** del primo ordine,
> $f_t \approx 29{,}7\ \text{kHz}$, guadagno in banda passante unitario, uno **zero nell'origine** e un
> **polo in s = −1,867·10⁵ rad/s**.

---

### 4B) L in serie, R in parallelo, uscita su R

**Dati:** $L = 0{,}3\ \text{mH}$, $R = 1{,}2\ \text{k}\Omega$.

$$\begin{aligned}
G(s) &= R / (R + sL) = 1 / (1 + sL/R) \\[8pt]
L/R &= 0{,}3\cdot 10^{-3} / 1200 = 2{,}5\cdot 10^{-7}\ \text{s}\quad\text{(costante di tempo τ)} \\[8pt]
\omega _t &= R/L = 1200 / (0{,}3\cdot 10^{-3}) = 4\cdot 10^{6}\ \text{rad/s} \\[2pt]
f_t &= 636{,}6\ \text{kHz}
\end{aligned}$$

> [!success] Risultato 4B
> $G(s) = R/(R+sL) = 1/(1 + 2{,}5\cdot 10^{-7}\cdot s)$ — **filtro passa-basso** del primo ordine,
> $f_t \approx 636{,}6\ \text{kHz}$, guadagno in continua unitario, un **polo in s = −4·10⁶ rad/s**,
> nessuno zero.

> [!danger] Trappola
> Fusi ha scritto $V_o(s) = V_i(s)\cdot (Z_R + Z_C)$ e $V_o = V_i\cdot Z_{eq}$: ha **sommato** le
> impedenze invece di fare il rapporto del partitore, e in 4A ha usato un condensatore
> quando nel disegno c'è un'**induttanza** (annotazione rossa del prof.: *«nel circuito
> assegnato è presente, oltre a una resistenza, un'induttanza non una capacità»*).
> La funzione di trasferimento è sempre **adimensionale**: se il risultato ha le dimensioni
> di ohm, è sbagliato.

---

## Es. 5 — Frequenza di taglio dei filtri

### Circuito

```
 5A)  C in serie, R verso massa, uscita su R  →  passa-ALTO

        ●───[ C = 150 nF ]───┬───●
        │                    │
        │                   ┌┴┐
  v_i   │                   │ │  R = 6,8 kΩ      v_o
        │                   └┬┘
        ●────────────────────┴───●


 5B)  R in serie, C verso massa, uscita su C  →  passa-BASSO

        ●───[ R = 1 kΩ ]───┬───●
        │                  │
        │                 ───
  v_i   │                 ───   C = 2,2 µF       v_o
        │                  │
        ●──────────────────┴───●

 In tutti e due  f_t = 1/(2πRC): il taglio non dipende dal tipo di filtro.
```

### Ragionamento
Per un filtro RC del primo ordine la frequenza di taglio è quella in cui **la reattanza
eguaglia la resistenza** ($X_C = R$), cioè dove il modulo scende di 3 dB:

$$\begin{aligned}
1/(2\pi f_t C) &= R \;\Rightarrow\; f_t = 1/(2\pi RC)
\end{aligned}$$

La formula è **la stessa** per passa-alto e passa-basso: cambia il tipo di filtro (cioè
quale banda passa), non il valore del taglio.

---

### 5A) C in serie, R verso massa, uscita su R → **passa-alto**

**Dati:** $C = 150\ \text{nF}$, $R = 6{,}8\ \text{k}\Omega$.

$$\begin{aligned}
RC &= 6800 \cdot 150\cdot 10^{-9} = 1{,}02\cdot 10^{-3}\ \text{s} \\[2pt]
f_t &= 1/(2\pi \cdot 1{,}02\cdot 10^{-3}) = 1/(6{,}409\cdot 10^{-3}) = 156{,}0\ \text{Hz}
\end{aligned}$$

> [!success] Risultato 5A
> $f_t \approx 156\ \text{Hz}$ — filtro **passa-alto** (blocca la continua, lascia passare sopra i 156 Hz).

---

### 5B) R in serie, C verso massa, uscita su C → **passa-basso**

**Dati:** $R = 1\ \text{k}\Omega$, $C = 2{,}2\ \mu\text{F}$.

$$\begin{aligned}
RC &= 1000 \cdot 2{,}2\cdot 10^{-6} = 2{,}2\cdot 10^{-3}\ \text{s} \\[2pt]
f_t &= 1/(2\pi \cdot 2{,}2\cdot 10^{-3}) = 1/(1{,}382\cdot 10^{-2}) = 72{,}3\ \text{Hz}
\end{aligned}$$

> [!success] Risultato 5B
> $f_t \approx 72{,}3\ \text{Hz}$ — filtro **passa-basso**.

> [!note] Esercizio lasciato in bianco
> Il prof. ha scritto *«NON SVOLTO PER NULLA»*: 0,00/2,00 punti. È l'esercizio più veloce di
> tutta la verifica — due divisioni. Vale il 20% del voto.

---

## Es. 6 — Impedenza equivalente di una rete

**Dati:**
$\bar{Z}_{1} = (2 + j6)\,\Omega$ · $\bar{Z}_{2} = (2 - j2)\,\Omega$ · $\bar{Z}_{3} = (j10)\,\Omega$ · $\bar{Z}_{4} = (2 + j4)\,\Omega$

### Circuito

```
 Sul foglio Z̄₁, Z̄₃ e Z̄₄ convergono su un nodo centrale che un filo collega al
 morsetto ALTO: stesso nodo elettrico, chiamalo A. Il morsetto BASSO, il filo di
 fondo e il nodo di destra sono anch'essi un solo nodo, chiamalo B.

 Ridisegnato ai due SOLI nodi elettrici (A = morsetto alto + nodo centrale,
 B = morsetto basso + filo di fondo + nodo di destra):

   A ●────┬────────┬────────┬────────┬────
          │        │        │        │
        [ Z̄₁ ]   [ Z̄₂ ]   [ Z̄₃ ]   [ Z̄₄ ]
        2+j6     2−j2      j10     2+j4
          │        │        │        │
   B ●────┴────────┴────────┴────────┴────

 Tutte e quattro fra A e B  →  quattro impedenze in PARALLELO.
```

### Ragionamento — riconoscere la topologia
Questo è il passaggio che vale l'esercizio. Guardando il disegno:

- il morsetto **superiore** e il nodo centrale (dove convergono $\bar{Z}_{1}$, $\bar{Z}_{3}$, $\bar{Z}_{4}$) sono
  **collegati da un filo**: sono lo **stesso nodo elettrico**, chiamiamolo $A$
- il morsetto **inferiore**, il filo di fondo e il nodo di destra sono anch'essi **un unico
  nodo**, chiamiamolo **B**.

Ricondotto ai due nodi A e B, ogni impedenza è **fra A e B**:

| Impedenza | Da | A |
|---|---|---|
| $\bar{Z}_{1}$ | B | A |
| $\bar{Z}_{2}$ | A | B (via nodo di destra) |
| $\bar{Z}_{3}$ | A | B |
| $\bar{Z}_{4}$ | A | B (via nodo di destra) |

Quindi **tutte e quattro sono in parallelo**:
$\bar{Z}_{eq} = \bar{Z}_{1} ∥ \bar{Z}_{2} ∥ \bar{Z}_{3} ∥ \bar{Z}_{4}$.

Si risolve a coppie, come ha fatto (correttamente, come impostazione) Fusi:
$\bar{Z}_{24} = \bar{Z}_{2} ∥ \bar{Z}_{4}$ → $\bar{Z}_{234} = \bar{Z}_{24} ∥ \bar{Z}_{3}$ → $\bar{Z}_{eq} = \bar{Z}_{1} ∥ \bar{Z}_{234}$.

### Calcoli

$Passo 1 — \bar{Z}_{24} = \bar{Z}_{2} \cdot \bar{Z}_{4} / (\bar{Z}_{2} + \bar{Z}_{4})$

$$\begin{aligned}
\text{numeratore}:\;\; (2 - j2)(2 + j4) &= 4 + j8 - j4 - j^{2}8 = 4 + j4 + 8 = 12 + j4 \\[2pt]
\text{denominatore}:\;\; (2 - j2) + (2 + j4) &= 4 + j2 \\[8pt]
&(12 + j4)/(4 + j2) \cdot (4 - j2)/(4 - j2) \\[8pt]
num &= (12 + j4)(4 - j2) = 48 - j24 + j16 - j^{2}8 = 48 - j8 + 8 = 56 - j8 \\[2pt]
den &= 4^{2} + 2^{2} = 20 \\[8pt]
\bar{Z}_{24} &= (56 - j8)/20 = 2{,}8 - j0{,}4\,\Omega
\end{aligned}$$

$Passo 2 — \bar{Z}_{234} = \bar{Z}_{24} \cdot \bar{Z}_{3} / (\bar{Z}_{24} + \bar{Z}_{3})$

$$\begin{aligned}
\text{numeratore}:\;\; (2{,}8 - j0{,}4)(j10) &= j28 - j^{2}4 = 4 + j28 \\[2pt]
\text{denominatore}:\;\; (2{,}8 - j0{,}4) + j10 &= 2{,}8 + j9{,}6 \\[8pt]
&(4 + j28)/(2{,}8 + j9{,}6) \cdot (2{,}8 - j9{,}6)/(2{,}8 - j9{,}6) \\[8pt]
num &= (4 + j28)(2{,}8 - j9{,}6) = 11{,}2 - j38{,}4 + j78{,}4 - j^{2}268{,}8 = 280 + j40 \\[2pt]
den &= 2{,}8^{2} + 9{,}6^{2} = 7{,}84 + 92{,}16 = 100 \\[8pt]
\bar{Z}_{234} &= (280 + j40)/100 = 2{,}8 + j0{,}4\,\Omega
\end{aligned}$$

$Passo 3 — \bar{Z}_{eq} = \bar{Z}_{1} \cdot \bar{Z}_{234} / (\bar{Z}_{1} + \bar{Z}_{234})$

$$\begin{aligned}
\text{numeratore}:\;\; (2 + j6)(2{,}8 + j0{,}4) &= 5{,}6 + j0{,}8 + j16{,}8 + j^{2}2{,}4 = 3{,}2 + j17{,}6 \\[2pt]
\text{denominatore}:\;\; (2 + j6) + (2{,}8 + j0{,}4) &= 4{,}8 + j6{,}4 \\[8pt]
&(3{,}2 + j17{,}6)/(4{,}8 + j6{,}4) \cdot (4{,}8 - j6{,}4)/(4{,}8 - j6{,}4) \\[8pt]
num &= (3{,}2 + j17{,}6)(4{,}8 - j6{,}4) = 15{,}36 - j20{,}48 + j84{,}48 - j^{2}112{,}64 = 128 + j64 \\[2pt]
den &= 4{,}8^{2} + 6{,}4^{2} = 23{,}04 + 40{,}96 = 64 \\[8pt]
\bar{Z}_{eq} &= (128 + j64)/64 = 2 + j1\,\Omega
\end{aligned}$$

> [!success] Risultato Es. 6
> $\bar{Z}_{eq} = (2 + j1)\,\Omega$
> $|Z_{eq}| = \sqrt{5} = 2{,}24\,\Omega$, **arg Z_eq = arctan(1/2) = +26,6°** → bipolo **ohmico-induttivo**.
>
> Il risultato esce con numeri esatti: è la verifica che la topologia è stata letta bene.

> [!danger] Trappola
> Fusi ha impostato bene i tre paralleli (il prof. gli ha dato 2,00/2,00, pieno) ma ha
> sbagliato il $passo 1$: da $(12+j4)/(4+j2)$ ha scritto $3 + j2$ invece di $2{,}8 - j0{,}4$,
> arrivando poi a $\bar{Z}_{eq} = 2{,}69 - j1{,}7$.
> **Controllo veloce per non cascarci:** i moduli si dividono.
> $|12+j4| = 12{,}65$, $|4+j2| = 4{,}47$ → il modulo del risultato deve valere $2{,}83$.
> $|3+j2| = 3{,}61$ ✗ · $|2{,}8-j0{,}4| = 2{,}83$ \;\checkmark.

---

# Verifica 2 — 24/04/2026 (valutata 09/05)
**BJT: polarizzazione, progetto, commutazione, amplificatore · 7 esercizi**

Esiti di Fusi: 1 ~OK · 2 ~OK · 3 errato · 4 non svolto · 5 non svolto · 6 errato · 7 errato
→ **1,50 punti, voto 3/10**.

> [!abstract] Le tre relazioni che risolvono cinque esercizi su sette
> Tutti gli esercizi su BJT in zona attiva si aprono con le stesse tre equazioni, applicate
> **in quest'ordine**:
> 1. **Maglia d'ingresso** (Kirchhoff sulla maglia base–emettitore) → dà $I_B$.
> 2. **Relazione del transistor**: $I_C = h_{FE} \cdot I_B$, $I_E = I_C + I_B = (h_{FE} + 1)\cdot I_B$.
> 3. **Maglia d'uscita** (Kirchhoff sulla maglia collettore–emettitore) → dà $V_{CE}$.
>
> **L'errore capitale**, quello che Carli segna in rosso ogni volta: mettere $R_B$ nella
> maglia d'uscita o $R_C$ nella maglia d'ingresso. Le due maglie sono **separate** e
> condividono solo il ramo di emettitore.

---

## Es. 1 — Determinare V_CE, I_C e I_B

**Dati:** $V_{CC} = 12\ \text{V}$, $R_C = 820\,\Omega$, $V_{BB} = 5\ \text{V}$, $R_B = 56\ \text{k}\Omega$, $h_{FE} = 100$,
$V_{BE} = 0{,}7\ \text{V}$ (zona attiva lineare, per ipotesi del testo).

**Circuito:** polarizzazione a **due alimentazioni**, $V_{BB}$ in serie a $R_B$ sulla base,
emettitore a massa, $R_C$ fra $V_{CC}$ e collettore.

### Circuito

```
                   V_CC = 12 V
                       ●
                       │
                      ┌┴┐
                      │ │  R_C = 820 Ω
                      └┬┘
                       │
                       ├───── V_C
                       │ C
                     ┌─┴─┐
 V_BB ──[ R_B ]──────┤ Q │   NPN   h_FE = 100
  5 V    56 kΩ     B └─┬─┘         V_BE = 0,7 V
                       │ E
                      ─┴─   massa comune a V_BB e V_CC

 Maglia d'INGRESSO (a sinistra, percorsa da I_B):  V_BB = R_B·I_B + V_BE
 Maglia d'USCITA   (a destra,  percorsa da I_C):   V_CC = R_C·I_C + V_CE
 Le due maglie sono separate: condividono solo il ramo di emettitore.
```

### Calcoli

**1) Maglia d'ingresso:** $V_{BB} = R_B\cdot I_B + V_{BE}$

$$\begin{aligned}
I_B &= (V_{BB} - V_{BE})/R_B = (5 - 0{,}7)/56\cdot 10^{3} = 4{,}3/56\,000 \\[2pt]
&= 76{,}8\cdot 10^{-6}\ \text{A} = 76{,}8\ \mu\text{A}
\end{aligned}$$

**2) Relazione del transistor:**

$$\begin{aligned}
I_C &= h_{FE} \cdot I_B = 100 \cdot 76{,}8\cdot 10^{-6} = 7{,}68\cdot 10^{-3}\ \text{A} = 7{,}68\ \text{mA}
\end{aligned}$$

**3) Maglia d'uscita:** $V_{CC} = R_C\cdot I_C + V_{CE}$

$$\begin{aligned}
V_{CE} &= V_{CC} - R_C\cdot I_C = 12 - 820 \cdot 7{,}68\cdot 10^{-3} \\[2pt]
&= 12 - 6{,}30 = 5{,}70\ \text{V}
\end{aligned}$$

**4) Verifica dell'ipotesi di zona attiva.** La corrente che circolerebbe a saturazione è

$$\begin{aligned}
I_C(sat) &= (V_{CC} - V_{CEsat})/R_C = (12 - 0{,}2)/820 = 14{,}4\ \text{mA}
\end{aligned}$$

$I_C = 7{,}68\ \text{mA} < 14{,}4\ \text{mA}$ e $V_{CE} = 5{,}70\ \text{V} > V_{CEsat}$ → **il BJT è davvero in zona attiva**,
l'ipotesi regge.

> [!success] Risultato Es. 1
> $I_B = 76{,}8\ \mu\text{A}$ · $I_C = 7{,}68\ \text{mA}$ · $V_{CE} = 5{,}70\ \text{V}$
> Punto di lavoro Q(5,70 V ; 7,68 mA), circa a metà della retta di carico → buona
> polarizzazione per un amplificatore.

> [!danger] Trappola
> Fusi ha impostato tutto correttamente ma nell'ultimo passaggio ha scritto
> $V_{CE} = (10 - 6{,}3)\ \text{V} = 3{,}7\ \text{V}$: ha usato **10 V al posto dei 12 V** del testo. Il prof. ha
> cerchiato il 10 e scritto *«errato a sostituire il valore, in quanto V_CC = 12 V»*.
> Mezzo punto perso per una cifra.

---

## Es. 2 — Progetto: determinare R_C e R_B per il punto di lavoro assegnato

**Dati:** $V_{CEO} = 4{,}8\ \text{V}$, $I_{CO} = 14\ \text{mA}$, $h_{FE} = 100$, $V_{CC} = 10\ \text{V}$, $V_{BE} = 0{,}7\ \text{V}$.
**Circuito:** polarizzazione **a base fissa** ($R_B$ fra $V_{CC}$ e base, $R_C$ fra $V_{CC}$ e
collettore, emettitore a massa).

### Circuito

```
                V_CC = 10 V
        ●───────────────────●
        │                   │
       ┌┴┐                 ┌┴┐
       │ │  R_B = ?        │ │  R_C = ?
       └┬┘                 └┬┘
        │                   │ C
        │                 ┌─┴─┐
        └─────────────────┤ Q │   h_FE = 100
                        B └─┬─┘   V_BE = 0,7 V
                            │ E
                           ─┴─

 Polarizzazione a BASE FISSA: R_B parte da V_CC, non da un'alimentazione a parte.
 Qui il punto di lavoro Q(V_CEO = 4,8 V ; I_CO = 14 mA) è il dato, le R sono l'incognita.
```

### Ragionamento
È l'esercizio 1 letto al contrario: il punto di lavoro è il **dato**, le resistenze sono
l'**incognita**. Le maglie restano due e restano separate.

### Calcoli

**Maglia d'uscita → R_C**

$$\begin{aligned}
V_{CC} &= R_C\cdot I_{CO} + V_{CEO} \\[8pt]
R_C &= (V_{CC} - V_{CEO})/I_{CO} = (10 - 4{,}8)/14\cdot 10^{-3} \\[2pt]
&= 5{,}2/0{,}014 = 371{,}4\,\Omega
\end{aligned}$$

**Corrente di base**

$$\begin{aligned}
I_B &= I_{CO}/h_{FE} = 14\cdot 10^{-3}/100 = 140\cdot 10^{-6}\ \text{A} = 140\ \mu\text{A}
\end{aligned}$$

**Maglia d'ingresso → R_B**

$$\begin{aligned}
V_{CC} &= R_B\cdot I_B + V_{BE} \\[8pt]
R_B &= (V_{CC} - V_{BE})/I_B = (10 - 0{,}7)/140\cdot 10^{-6} \\[2pt]
&= 9{,}3/1{,}4\cdot 10^{-4} = 66{,}4\cdot 10^{3}\,\Omega = 66{,}4\ \text{k}\Omega
\end{aligned}$$

> [!success] Risultato Es. 2
> $R_C \approx 371\,\Omega$ (valore commerciale $390\,\Omega$) · $R_B \approx 66{,}4\ \text{k}\Omega$ (valore commerciale
> $68\ \text{k}\Omega$).
>
> Con i valori commerciali il punto di lavoro si sposta di poco:
> $I_B = 9{,}3/68k = 137\ \mu\text{A}$ → $I_C = 13{,}7\ \text{mA}$ → $V_{CE} = 10 - 390\cdot 0{,}0137 = 4{,}66\ \text{V}$. Accettabile.

> [!danger] Trappola
> Fusi ha ottenuto i numeri giusti ma è partito da $V_{CE} = R_B\cdot I_B + R_C\cdot I_C$, che è
> **falsa**: mette insieme un elemento della maglia d'ingresso ($R_B$) e uno della maglia
> d'uscita ($R_C$). Annotazione del prof.: *«errata, in quanto R_B fa parte della maglia
> d'ingresso non della maglia d'uscita»*, e più sotto *«non si spiega questo passaggio dalla
> relazione precedente»*. **I risultati giusti da una relazione sbagliata non valgono il
> punteggio pieno.**

---

## Es. 3 — Progetto del circuito di polarizzazione e stabilizzazione (partitore + R_E)

**Dati:** $V_{CC} = 10\ \text{V}$, $I_{CO} = 10\ \text{mA}$, $h_{FEmin} = 75$, $V_{BE} = 0{,}7\ \text{V}$.
**Incognite:** $I_B$, $I_E$, $R_C$, $R_E$, $R_{1}$, $R_{2}$.

### Circuito

```
                     V_CC = 10 V
        ●─────────────────────────●
        │                         │
       ┌┴┐                       ┌┴┐
       │ │  R₁ = ?               │ │  R_C = ?
       └┬┘                       └┬┘
        │                         │ C
        │                       ┌─┴─┐
        ├───────────────────────┤ Q │   h_FEmin = 75
        │  V_BO = 1,7 V       B └─┬─┘
       ┌┴┐                        │ E
       │ │  R₂ = ?               ┌┴┐
       └┬┘                       │ │  R_E = ?
        │                        └┬┘
        │                         │
       ─┴─────────────────────────┴─   massa

 I = corrente nel partitore (R₁, R₂);  I_B esce dal nodo di base;  nodo: I_R1 = I_B + I_R2.
 Criteri di progetto: V_E = V_CC/10 · V_RC = V_CE = 9·V_CC/20 · I = 10·I_B (con h_FEmin).
 Maglia d'uscita COMPLETA:  V_CC = R_C·I_C + V_CE + R_E·I_E   (tre termini, non due).
```

### Ragionamento — perché servono criteri di progetto
Qui le incognite (4 resistenze) sono più delle equazioni indipendenti: il problema è
**sottodeterminato**. Si chiude imponendo i **criteri standard di progetto**, quelli che
Carli ha scritto di suo pugno sul retro del foglio:

1. **Tensione di emettitore** $V_E = V_{CC}/10$ → rende il punto di lavoro insensibile alle
   variazioni di $h_{FE}$ e della temperatura (è la *stabilizzazione*), senza sprecare troppa
   dinamica.
2. I restanti $9\cdot V_{CC}/10$ si dividono **a metà** fra $R_C$ e il transistor:
   $V_{RC} = V_{CE} = 9\cdot V_{CC}/20$. Così l'escursione del segnale è massima e simmetrica.
3. **Corrente nel partitore** $I = 10\cdot I_B$ calcolata con $h_{FEmin}$ → il ramo di base
   assorbe un decimo della corrente del partitore, che quindi impone $V_{BO}$ in modo rigido
   e indipendente dal transistor.

### Calcoli

**Resistenza di emettitore**

$$\begin{aligned}
V_E &= V_{CC}/10 = 1\ \text{V} \\[2pt]
R_E &= V_E/I_{CO} = V_{CC}/(10\cdot I_{CO}) = 10/(10 \cdot 10\cdot 10^{-3}) = 100\,\Omega
\end{aligned}$$

**Resistenza di collettore**

$$\begin{aligned}
V_{RC} &= 9\cdot V_{CC}/20 = 4{,}5\ \text{V} \\[2pt]
R_C &= 9\cdot V_{CC}/(20\cdot I_{CO}) = 90/(20 \cdot 10\cdot 10^{-3}) = 90/0{,}2 = 450\,\Omega
\end{aligned}$$

*(Verifica della maglia d'uscita: $V_{RC} + V_{CE} + V_E = 4{,}5 + 4{,}5 + 1 = 10\ \text{V} = V_{CC}$ \;\checkmark)*

**Tensione di base e corrente del partitore**

$$\begin{aligned}
V_{BO} &= V_{BE} + V_{RE} = V_{BE} + R_E\cdot I_{CO} = 0{,}7 + 100 \cdot 10\cdot 10^{-3} = 0{,}7 + 1 = 1{,}7\ \text{V} \\[8pt]
I_B &= I_{CO}/h_{FEmin} = 10\cdot 10^{-3}/75 = 133{,}3\ \mu\text{A} \\[2pt]
I &= 10\cdot I_B = 1{,}33\ \text{mA} \approx 1{,}3\ \text{mA}
\end{aligned}$$

**Partitore di base**

$$\begin{aligned}
R_{2} \text{(verso massa)} &= V_{BO}/I = 1{,}7/1{,}3\cdot 10^{-3} = 1{,}31\ \text{k}\Omega \approx 1{,}3\ \text{k}\Omega \\[2pt]
R_{1} \text{(verso }V_{CC}\text{)} &= (V_{CC} - V_{BO})/I = (10 - 1{,}7)/1{,}3\cdot 10^{-3} = 6{,}38\ \text{k}\Omega \approx 6{,}4\ \text{k}\Omega
\end{aligned}$$

**Corrente di emettitore**

$$\begin{aligned}
I_E &= I_C + I_B = 10 + 0{,}133 = 10{,}13\ \text{mA} \approx 10{,}1\ \text{mA}
\end{aligned}$$

> [!success] Risultato Es. 3
> $R_E = 100\,\Omega$ · $R_C = 450\,\Omega$ · $R_{2} = 1{,}3\ \text{k}\Omega$ · $R_{1} = 6{,}4\ \text{k}\Omega$
> $I_B = 133\ \mu\text{A}$ · $I_E = 10{,}1\ \text{mA}$ · $V_{BO} = 1{,}7\ \text{V}$ · $V_{CE} = 4{,}5\ \text{V}$
>
> Valori commerciali: $R_E = 100\,\Omega$, $R_C = 470\,\Omega$, $R_{2} = 1{,}3\ \text{k}\Omega$, $R_{1} = 6{,}2\ \text{k}\Omega$.

> [!tip] Questo è l'esercizio con la soluzione autografa del prof.
> Sul retro (p. 12 del PDF) c'è la sequenza completa in rosso, di mano di Carli. È il
> modello di svolgimento che si aspetta di vedere: **prima R_E, poi R_C, poi V_BO, poi I,
> poi il partitore.** Vale la pena impararla in quest'ordine.

> [!danger] Trappola
> Fusi ha scritto $R_C = (V_{CC} - V_{CE})/I_{CO}$ **dimenticando la caduta su R_E**: in un
> circuito con emettitore resistivo la maglia d'uscita è $V_{CC} = R_C\cdot I_C + V_{CE} + R_E\cdot I_E$,
> non $V_{CC} = R_C\cdot I_C + V_{CE}$. Ha inoltre scritto $I_B = I_{R1} - I_{R2}$ con il segno
> invertito: il nodo di base dà $I_{R1} = I_B + I_{R2}$, quindi $I_B = I_{R1} - I_{R2}$ è
> formalmente giusta, ma va usata insieme al criterio $I_{R2} = 10\cdot I_B$, che lui non ha
> imposto — senza quel criterio il sistema resta indeterminato.

---

## Es. 4 — Interfaccia fra porta TTL e bobina di relè

**Dati:** porta TTL con uscita $0\ \text{V}$ (livello basso) o $5\ \text{V}$ (livello alto); relè con
**tensione di bobina 12 V** e $corrente 70\ \text{mA}$; $h_{FEmin} = 75$.

### Circuito

```
                      +12 V
                        ●
                ┌───────┴───────┐
                │               │
               ───              ∩
                ▲  D 1N4007     ∩    bobina relè
                │  (catodo in   ∩    12 V · 70 mA
                │   alto)       │
                └───────┬───────┘
                        │ C
                      ┌─┴─┐
 TTL ──[ R_B ]────────┤ Q │   NPN  BC337 / 2N2222
 0/5 V   2,2 kΩ     B └─┬─┘   h_FEmin = 75
                        │ E
                       ─┴─   massa comune TTL / alimentazione 12 V

 TTL a 0 V → BJT interdetto, relè diseccitato.  TTL a 5 V → BJT saturo, relè eccitato.
 Il diodo in ANTIPARALLELO alla bobina scarica la sovratensione L·di/dt allo spegnimento:
 senza di lui il progetto è incompleto anche con tutti i conti giusti.
```

### Ragionamento
La porta TTL non può pilotare il relè per due motivi indipendenti:
- **tensione**: fornisce 5 V, la bobina ne vuole 12
- **corrente**: un'uscita TTL eroga tipicamente ~0,4÷16 mA, la bobina ne chiede 70.

Serve quindi un **BJT NPN in commutazione** (interruttore comandato): la bobina va sul
**collettore**, alimentata a 12 V; l'emettitore a massa; la base pilotata dalla TTL
attraverso $R_B$. Il transistor deve lavorare fra **interdizione** (TTL a 0 V, relè
diseccitato) e **saturazione** (TTL a 5 V, relè eccitato) — mai in zona attiva, dove
dissiperebbe potenza inutilmente.

### Calcoli

**1) Corrente di collettore richiesta (a saturazione)**

$$\begin{aligned}
I_C &= 70\ \text{mA}\quad\text{(corrente nominale della bobina)}
\end{aligned}$$

**2) Corrente di base minima per saturare**

$$\begin{aligned}
I_{Bmin} &= I_C/h_{FEmin} = 70\cdot 10^{-3}/75 = 0{,}933\ \text{mA}
\end{aligned}$$

**3) Sovrapilotaggio (overdrive).** Si moltiplica per un fattore 2÷5 per garantire la
saturazione anche col peggiore esemplare di transistor e alle basse temperature. Prendo
$\times 2$:

$$\begin{aligned}
I_B &= 2 \cdot 0{,}933 = 1{,}87\ \text{mA}
\end{aligned}$$

**4) Resistenza di base.** Maglia d'ingresso con $V_{OH} = 5\ \text{V}$ e $V_{BEsat} \approx 0{,}7\ \text{V}$:

$$\begin{aligned}
R_B &= (V_{OH} - V_{BEsat})/I_B = (5 - 0{,}7)/1{,}87\cdot 10^{-3} \\[2pt]
&= 4{,}3/1{,}87\cdot 10^{-3} = 2{,}30\ \text{k}\Omega
\end{aligned}$$

**Valore commerciale: R_B = 2,2 kΩ.**

**5) Verifica con il valore commerciale**

$$\begin{aligned}
I_{B,\text{reale}} &= 4{,}3/2200 = 1{,}95\ \text{mA} \\[2pt]
h_{FE}\text{ richiesto} &= I_C/I_B = 70/1{,}95 = 35{,}9 < 75 \;\checkmark\quad\text{(saturo con ampio margine)}
\end{aligned}$$

**6) Diodo di libera circolazione (indispensabile).** La bobina è un'induttanza: quando il
BJT si interdice, la corrente non può annullarsi di colpo e genera una sovratensione
$v = L\cdot di/dt$ che distruggerebbe il transistor. Si mette un **diodo in antiparallelo alla
bobina**, catodo verso +12 V, anodo verso il collettore: alla commutazione offre alla
corrente una via di richiusura.
Tipo adatto: $1N4001\div 1N4007$ (I_F = 1 A ≫ 70 mA).

**7) Scelta del transistor e potenza dissipata**

$$\begin{aligned}
P_{diss} &= V_{CEsat} \cdot I_C \approx 0{,}2 \cdot 70\cdot 10^{-3} = 14\ \text{mW}\quad\text{(trascurabile, niente dissipatore)}
\end{aligned}$$

Transistor adatto: $BC337$ ($I_{Cmax} = 800\ \text{mA}$, $V_{CEO} = 45\ \text{V}$) o $2N2222$.

> [!success] Risultato Es. 4
> **BJT NPN in commutazione** con $R_B = 2{,}2\ \text{k}\Omega$ in serie alla base, bobina sul collettore
> alimentata a 12 V, emettitore a massa, **diodo 1N4007 in antiparallelo alla bobina**.
> $I_B = 1{,}95\ \text{mA}$, $h_{FE} richiesto = 36 < 75$ → saturazione garantita.
>
> Le due masse (TTL e alimentazione 12 V) devono essere **in comune**.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO PER NULLA»* — 0,00/1,00. Il **diodo di ricircolo** è la parte che Carli
> cerca: senza quello il progetto è considerato incompleto anche col resto giusto.

---

## Es. 5 — Condensatore di by-pass C_E

**Dati:** amplificatore BJT a **emettitore comune**, $R_E = 1\ \text{k}\Omega$, banda del segnale
$50\ \text{Hz} \div 8\ \text{kHz}$.

### Circuito

```
                     V_CC
        ●─────────────────────────●
        │                         │
       ┌┴┐                       ┌┴┐
       │ │  R₁                   │ │  R_C
       └┬┘                       └┬┘
        │                         │ C
        │                       ┌─┴─┐
        ├───────────────────────┤ Q │────── v_o
        │                     B └─┬─┘
       ┌┴┐                        │ E
       │ │  R₂                    ├────────┐
       └┬┘                       ┌┴┐      ───
        │                        │ │ R_E  ───  C_E
        │                        │ │ 1 kΩ  │   = 33 µF
        │                        └┬┘       │
        │                         ├────────┘
       ─┴─────────────────────────┴─   massa

 In CONTINUA C_E è un aperto: R_E lavora e stabilizza il punto di lavoro.
 In ALTERNATA C_E deve essere un corto: l'emettitore va a massa e il guadagno torna pieno.
 Condizione critica alla f più bassa della banda (50 Hz):  X_CE ≤ R_E/10.
```

### Ragionamento
$R_E$ serve alla **stabilizzazione del punto di lavoro in continua**, ma introduce
**controreazione in alternata** che abbatte il guadagno ($A_v \approx -R_C/R_E$). Il condensatore
$C_E$ in parallelo a $R_E$ risolve il conflitto: in continua è un circuito aperto ($R_E$
lavora e stabilizza), in alternata deve essere un **cortocircuito** che mette l'emettitore a
massa e restituisce il guadagno pieno.

La condizione critica è alla **frequenza più bassa** della banda (50 Hz), dove la reattanza
del condensatore è massima. Il criterio di progetto standard è che la reattanza sia almeno
**dieci volte più piccola** di $R_E$:

$$\begin{aligned}
&X_{CE} \le R_E/10 \quad\text{alla } f_{\min}
\end{aligned}$$

### Calcoli

$$\begin{aligned}
&1/(2\pi \cdot f_{\min}\cdot C_E) \le R_E/10 \\[8pt]
C_E \ge 10/(2\pi \cdot f_{\min}\cdot R_E) &= 10/(2\pi \cdot 50 \cdot 1000) \\[2pt]
&= 10/(3{,}1416\cdot 10^{5}) = 31{,}8\cdot 10^{-6}\ \text{F} = 31{,}8\ \mu\text{F}
\end{aligned}$$

**Valore commerciale: C_E = 33 µF elettrolitico** (o 47 µF, andando più larghi).

**Verifica a 50 Hz con 33 µF:**

$$\begin{aligned}
X_{CE} &= 1/(2\pi \cdot 50 \cdot 33\cdot 10^{-6}) = 1/(1{,}0367\cdot 10^{-2}) = 96{,}5\,\Omega \\[2pt]
&96{,}5\,\Omega \ll 1000\,\Omega \;\checkmark\quad\text{(rapporto } \sim\!1/10)
\end{aligned}$$

A 8 kHz $X_{CE}$ scende a 0,6 Ω: la condizione è ancora più che soddisfatta, come atteso.

> [!success] Risultato Es. 5
> $C_E \ge 31{,}8\ \mu\text{F} \;\Rightarrow\; si sceglie C_E = 33\ \mu\text{F}$ (elettrolitico, tensione di lavoro ≥ 2·V_E,
> polarità positiva verso l'emettitore).
>
> *Se si applica il criterio minimo $f_{\min} = 1/(2\pi R_E C_E)$ invece della regola del fattore
> 10, verrebbe $C_E = 3{,}18\ \mu\text{F}$: è la frequenza a cui $X_{CE} = R_E$, cioè dove il by-pass
> comincia appena a funzionare — a 50 Hz il guadagno sarebbe già sceso di 3 dB. Il criterio
> corretto per un progetto è quello ×10.*

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO PER NULLA»* — 0,00/1,00. Una formula sola.

---

## Es. 6 — Verifica del funzionamento in zona di saturazione

**Dati:** $V_{CC} = 10\ \text{V}$, $h_{FE} = 50$, $R_B = 5{,}2\ \text{k}\Omega$, $R_C = 0{,}33\ \text{k}\Omega$, $V_{BE} = 0{,}8\ \text{V}$,
$V_{CEsat} = 0{,}2\ \text{V}$.
**Circuito:** base fissa ($R_B$ fra $V_{CC}$ e base), emettitore a massa.

### Circuito

```
                V_CC = 10 V
        ●───────────────────●
        │                   │
       ┌┴┐                 ┌┴┐
       │ │  R_B = 5,2 kΩ   │ │  R_C = 0,33 kΩ
       └┬┘                 └┬┘
        │                   │ C
        │                 ┌─┴─┐
        └─────────────────┤ Q │   h_FE = 50
                        B └─┬─┘   V_BE = 0,8 V · V_CEsat = 0,2 V
                            │ E
                           ─┴─

 Verifica in tre passi:  1) maglia d'ingresso → I_B reale
                         2) maglia d'uscita con V_CE = V_CEsat → I_C(sat)
                         3) confronto: I_B > I_C(sat)/h_FE  ⇒  saturo.
```

### Ragionamento — la procedura in tre passi
Carli l'ha scritta lui stesso in rosso sul foglio di Fusi:

1. **II principio di Kirchhoff alla maglia d'ingresso** → $I_B$ (reale, quella che il
   circuito fornisce davvero).
2. **II principio di Kirchhoff alla maglia d'uscita**, *ipotizzando il transistor saturo*
   ($V_{CE} = V_{CEsat}$) → $I_C(sat)$, cioè la corrente massima che il carico può far passare.
3. **Confronto:** se $I_B > I_C(sat)/h_{FE}$, la base è sovrapilotata e il transistor è
   **davvero** in saturazione. Se fosse $I_B < I_C(sat)/h_{FE}$, il transistor sarebbe in zona
   attiva e l'ipotesi sarebbe da scartare.

### Calcoli

**Passo 1 — maglia d'ingresso**

$$\begin{aligned}
V_{CC} &= R_B\cdot I_B + V_{BE} \\[8pt]
I_B &= (V_{CC} - V_{BE})/R_B = (10 - 0{,}8)/5200 = 9{,}2/5200 \\[2pt]
&= 1{,}769\cdot 10^{-3}\ \text{A} = 1{,}77\ \text{mA}
\end{aligned}$$

**Passo 2 — maglia d'uscita con ipotesi di saturazione**

$$\begin{aligned}
V_{CC} &= R_C\cdot I_C + V_{CEsat} \\[8pt]
I_C(sat) &= (V_{CC} - V_{CEsat})/R_C = (10 - 0{,}2)/330 = 9{,}8/330 \\[2pt]
&= 29{,}7\cdot 10^{-3}\ \text{A} = 29{,}7\ \text{mA}
\end{aligned}$$

**Passo 3 — verifica**

$$\begin{aligned}
I_B\text{ necessaria} &= I_C(sat)/h_{FE} = 29{,}7/50 = 0{,}594\ \text{mA} \\[8pt]
I_B\text{ disponibile} &= 1{,}77\ \text{mA} > 0{,}594\ \text{mA} \;\checkmark \\[8pt]
&\text{fattore di saturazione (overdrive)}:\;\; 1{,}77/0{,}594 = 2{,}98 \approx 3
\end{aligned}$$

> [!success] Risultato Es. 6
> **Il BJT è effettivamente in saturazione**, con fattore di sovrapilotaggio ≈ 3.
> Punto di lavoro: $V_{CE} = V_{CEsat} = 0{,}2\ \text{V}$, $I_C = 29{,}7\ \text{mA}$, $I_B = 1{,}77\ \text{mA}$.
>
> Controprova: se il transistor fosse in zona attiva, sarebbe
> $I_C = h_{FE}$ · $I_B = 50 \cdot 1{,}77 = 88{,}5\ \text{mA}$, che darebbe
> $V_{CE} = 10 - 330\cdot 0{,}0885 = -19{,}2\ \text{V}$, impossibile. È proprio questa impossibilità che
> **dimostra** la saturazione.

> [!danger] Trappola
> Fusi ha scritto $V_{CC} = R_B\cdot I_B + R_C\cdot I_C$ — di nuovo le due maglie mescolate. Il prof.:
> *«errata perché l'equazione contiene al suo interno sia un elemento della maglia
> d'ingresso che è R_B che un elemento della maglia d'uscita R_C»*, e ha poi trascritto la
> procedura corretta in tre punti. **È lo stesso errore dell'es. 2: costa 2,00 punti su 10.**

---

## Es. 7 — Punto di lavoro con resistenza di emettitore

**Dati:** $V_{CC} = 20\ \text{V}$, $V_{BB} = 10\ \text{V}$, $R_C = 300\,\Omega$, $R_E = 200\,\Omega$, $R_B = 20\ \text{k}\Omega$,
$h_{FE} = 100$, $V_{BE} = 0{,}7\ \text{V}$ (zona attiva per ipotesi).

### Circuito

```
                   V_CC = 20 V
                       ●
                       │
                      ┌┴┐
                      │ │  R_C = 300 Ω
                      └┬┘
                       │ C
                     ┌─┴─┐
 V_BB ──[ R_B ]──────┤ Q │   h_FE = 100
 10 V    20 kΩ     B └─┬─┘   V_BE = 0,7 V
                       │ E
                      ┌┴┐
                      │ │  R_E = 200 Ω     ← percorsa da I_E,
                      └┬┘                    non da I_B né da I_C
                       │
                      ─┴─   massa comune

 R_E appartiene a ENTRAMBE le maglie:
   ingresso:  V_BB = R_B·I_B + V_BE + R_E·I_E ,  con I_E = (h_FE+1)·I_B
   uscita  :  V_CC = R_C·I_C + V_CE + R_E·I_E
```

### Ragionamento
Rispetto all'es. 1 c'è $R_E$, che appartiene a **entrambe** le maglie: è attraversata da
$I_E$, non da $I_B$ né da $I_C$. La maglia d'ingresso diventa quindi

$$\begin{aligned}
V_{BB} &= R_B\cdot I_B + V_{BE} + R_E\cdot I_E
\end{aligned}$$

e siccome $I_E = (h_{FE} + 1)\cdot I_B$, resta una sola incognita. Questo effetto — la caduta su
$R_E$ che si oppone alla corrente di base — è esattamente la **controreazione di corrente**
che stabilizza il punto di lavoro.

### Calcoli

**1) Maglia d'ingresso**

$$\begin{aligned}
V_{BB} &= R_B\cdot I_B + V_{BE} + R_E\cdot (h_{FE} + 1)\cdot I_B \\[8pt]
10 &= 20\,000\cdot I_B + 0{,}7 + 200\cdot 101\cdot I_B \\[2pt]
10 - 0{,}7 &= I_B\cdot (20\,000 + 20\,200) \\[2pt]
9{,}3 &= 40\,200\cdot I_B \\[8pt]
I_B &= 9{,}3/40\,200 = 231{,}3\cdot 10^{-6}\ \text{A} = 231\ \mu\text{A}
\end{aligned}$$

**2) Correnti di collettore ed emettitore**

$$\begin{aligned}
I_C &= h_{FE}\cdot I_B = 100 \cdot 231{,}3\cdot 10^{-6} = 23{,}13\cdot 10^{-3}\ \text{A} = 23{,}1\ \text{mA} \\[2pt]
I_E &= (h_{FE} + 1)\cdot I_B = 101 \cdot 231{,}3\cdot 10^{-6} = 23{,}37\cdot 10^{-3}\ \text{A} = 23{,}4\ \text{mA}
\end{aligned}$$

$3) Tensioni$

$$\begin{aligned}
V_E &= R_E\cdot I_E = 200 \cdot 23{,}37\cdot 10^{-3} = 4{,}67\ \text{V} \\[2pt]
V_{RC} &= R_C\cdot I_C = 300 \cdot 23{,}13\cdot 10^{-3} = 6{,}94\ \text{V} \\[8pt]
V_{CE} &= V_{CC} - R_C\cdot I_C - R_E\cdot I_E = 20 - 6{,}94 - 4{,}67 = 8{,}39\ \text{V}
\end{aligned}$$

**4) Verifica zona attiva**

$$\begin{aligned}
V_{CE} &= 8{,}39\ \text{V} \gg V_{CEsat} = 0{,}2\ \text{V} \;\checkmark \\[2pt]
I_C(sat) &= (V_{CC} - V_{CEsat})/(R_C + R_E) = 19{,}8/500 = 39{,}6\ \text{mA} > 23{,}1\ \text{mA} \;\checkmark
\end{aligned}$$

> [!success] Risultato Es. 7
> **Punto di lavoro Q: V_CE = 8,39 V ; I_C = 23,1 mA**
> ($I_B = 231\ \mu\text{A}$, $I_E = 23{,}4\ \text{mA}$, $V_E = 4{,}67\ \text{V}$)
>
> *Approssimando $I_E \approx I_C$ (cioè $h_{FE} + 1 \approx h_{FE}$) si ottiene $I_B = 233\ \mu\text{A}$,
> $I_C = 23{,}3\ \text{mA}$, $V_{CE} = 8{,}38\ \text{V}$: differenza sotto l'1%. L'approssimazione è lecita e
> Carli l'accetta, ma va dichiarata.*

> [!danger] Trappola
> Fusi ha scritto le due maglie e si è fermato: $V_{BO} = V_{BB} - R_B\cdot I_B$ e
> $V_{CC} = R_C\cdot I_{CO} + I_E\cdot R_E$ — quest'ultima $dimentica V_{CE}$, che è proprio l'incognita.
> Annotazione del prof.: *«perché non ha continuato lo svolgimento dell'esercizio?»*.
> La maglia d'uscita completa è $V_{CC} = R_C\cdot I_C + V_{CE} + R_E\cdot I_E$.

---

# Verifica 3 — 29/05/2026 (valutata 03/06)
**JFET canale N (es. 1-5) + MOSFET enhancement (es. 6-8) · 8 esercizi**

Esiti di Fusi: 1 ~OK · 2 ~OK · 3 non svolto · 4 non svolto · 5 non svolto · 6 ~OK · 7 ~OK ·
8 errato → $3{,}00/10$.

> [!abstract] Le leggi che servono per tutti e otto
>
> **JFET a canale N** ($V_P < 0$, funziona a $V_{GS}$ negativa, $I_G \approx 0$):
> ```
> Equazione di Shockley:   I_D = I_DSS · (1 − V_GS/V_P)²
> Invertita:               V_GS = V_P · (1 − √(I_D/I_DSS))
> Saturazione (zona attiva): V_DS ≥ V_GS − V_P
> ```
>
> **MOSFET enhancement a canale N** ($V_t > 0$, funziona a $V_{GS} > V_t$, $I_G = 0$):
> ```
> Zona di saturazione:     I_D = K·(V_GS − V_t)²        se V_DS ≥ V_GS − V_t
> Invertita:               V_GS = V_t + √(I_D/K)
> Zona ohmica (triodo):    I_D = K·[2(V_GS − V_t)·V_DS − V_DS²]   se V_DS < V_GS − V_t
> ```
>
> **La regola d'oro che vale per entrambi: $I_G = 0$.** Il gate è isolato (MOSFET) o è una
> giunzione polarizzata inversamente (JFET). Conseguenze:
> - nessuna caduta di tensione su $R_G$ → $V_G$ = potenziale imposto dal circuito
> - $I_S = I_D$ (tutta la corrente di drain esce dal source)
> - **$R_G$ non si calcola mai da una legge: si sceglie** (tipicamente 1÷10 MΩ).

---

## Es. 1 — Progetto della polarizzazione automatica di un JFET

**Dati:** $V_{DD} = 12\ \text{V}$, $I_{DO} = 8\ \text{mA}$, $V_{GSO} = -1\ \text{V}$, $V_{DSO} = 7\ \text{V}$.
**Incognite:** $R_D$, $R_S$, $R_G$.
**Circuito:** **autopolarizzazione** — gate a massa tramite $R_G$, $R_S$ sul source, $R_D$
sul drain.

### Circuito

```
                 V_DD = 12 V
                     ●
                     │
                    ┌┴┐
                    │ │  R_D = ?
                    └┬┘
                     │
                     ├────── v_o (drain)
                     │ D
                   ┌─┴─┐
        ┌──────────┤ J │   JFET canale N
        │        G └─┬─┘   I_G = 0
       ┌┴┐           │ S
       │ │  R_G     ┌┴┐
       │ │  (si     │ │  R_S = ?
       └┬┘  sceglie)└┬┘
        │            │
       ─┴────────────┴─   massa

 AUTOPOLARIZZAZIONE: I_G = 0 → nessuna caduta su R_G → V_G = 0,
 quindi  V_GS = V_G − V_S = −R_S·I_D  (negativa, come vuole il JFET-N).
 R_G sta su un ramo percorso da corrente nulla: NON si calcola, si sceglie (1÷10 MΩ).
```

### Ragionamento
Il gate è a potenziale zero ($I_G = 0$ → nessuna caduta su $R_G$ → $V_G = 0$). La tensione
$V_{GS}$ negativa che serve al JFET viene creata **dalla caduta su R_S**:

$$\begin{aligned}
V_{GS} &= V_G - V_S = 0 - R_S\cdot I_D = -R_S\cdot I_D
\end{aligned}$$

È elegante: il JFET si polarizza da solo, con una sola alimentazione.

### Calcoli

**Resistenza di source**

$$\begin{aligned}
R_S &= -V_{GSO}/I_{DO} = -(-1)/8\cdot 10^{-3} = 1/0{,}008 = 125\,\Omega
\end{aligned}$$

**Resistenza di drain** — maglia d'uscita $V_{DD} = R_D\cdot I_D + V_{DS} + R_S\cdot I_D$:

$$\begin{aligned}
R_D &= (V_{DD} - V_{DSO} - R_S\cdot I_{DO})/I_{DO} \\[2pt]
&= (12 - 7 - 125\cdot 8\cdot 10^{-3})/8\cdot 10^{-3} \\[2pt]
&= (12 - 7 - 1)/0{,}008 = 4/0{,}008 = 500\,\Omega
\end{aligned}$$

**Resistenza di gate**

$R_G$ **non è determinabile da nessuna equazione**: qualunque valore dà $V_G = 0$, perché
la corrente che la attraversa è nulla. Si sceglie in base a due criteri opposti:
- **grande**, per non caricare la sorgente di segnale collegata al gate (l'impedenza
  d'ingresso dello stadio è praticamente $R_G$)
- **non enorme**, perché la corrente di dispersione del gate (nA) su una $R_G$ troppo grande
  produrrebbe uno sbilanciamento della polarizzazione.

Valore tipico $1\ \text{M}\Omega$; il prof. indica $5\ \text{M}\Omega$.

> [!success] Risultato Es. 1
> $R_S = 125\,\Omega$ · $R_D = 500\,\Omega$ · $R_G = 1\ \text{M}\Omega$ (si sceglie; il prof. propone 5 MΩ)
>
> Verifica della zona di saturazione: $V_{DS} \ge V_{GS} - V_P$. Con $V_P$ non assegnato non si
> può controllare numericamente, ma $V_{DS} = 7\ \text{V}$ su $V_{DD} = 12\ \text{V}$ è un valore ampiamente
> prudenziale.

> [!danger] Trappola — l'unico vero errore di questa verifica su $R_G$
> Fusi ha scritto $R_G = V_{GS}/I_G$ e poi $I_G = V_{GS}/(R_S + R_D) = -1{,}6\ \text{mA}$, ottenendo
> $R_G = 625\,\Omega$. Sono **due errori concatenati**:
> 1. **$I_G \approx 0$**, non 1,6 mA: la giunzione gate-canale del JFET è polarizzata
>    **inversamente**, ci passano nanoampere.
> 2. $R_G$ non è in serie a $R_S$ e $R_D$: è su un ramo a sé, percorso da corrente nulla.
>
> Il prof. ha cancellato tutto con una croce e scritto: $«si fissa: R_G = 5\ \text{M}\Omega»$.
> Lo stesso errore ritorna identico nell'es. 2 — è il concetto più frainteso di tutta la
> verifica.

---

## Es. 2 — Progetto della polarizzazione con equazione di Shockley

**Dati:** $V_{DD} = 18\ \text{V}$, $I_{DO} = 5\ \text{mA}$, $V_{DSO} = 10\ \text{V}$, $V_P = -5\ \text{V}$, $I_{DSS} = 12\ \text{mA}$.
**Incognite:** $R_D$, $R_S$, $R_G$.

> [!warning] Sul segno di V_P
> Il testo scrive $V_P = 5\ \text{V}$, ma per un **JFET a canale N** la tensione di pinch-off è
> **negativa**: $V_P = -5\ \text{V}$. Va corretto, altrimenti la formula di Shockley dà risultati
> senza senso ($V_{GS}$ positiva porterebbe il JFET in conduzione diretta della giunzione).

### Circuito

```
                 V_DD = 18 V
                     ●
                     │
                    ┌┴┐
                    │ │  R_D = ?
                    └┬┘
                     │ D
                   ┌─┴─┐
        ┌──────────┤ J │   JFET-N   I_DSS = 12 mA
        │        G └─┬─┘            V_P = −5 V
       ┌┴┐           │ S
       │ │  R_G     ┌┴┐
       │ │  1 MΩ    │ │  R_S = ?
       └┬┘          └┬┘
        │            │
       ─┴────────────┴─   massa

 Stessa topologia dell'es. 1, ma manca V_GSO: prima si ricava dalla Shockley invertita
 V_GS = V_P·(1 − √(I_D/I_DSS)), poi si procede identici.  V_GS deve stare fra V_P e 0.
```

### Ragionamento
Rispetto all'es. 1 manca $V_{GSO}$, quindi bisogna **prima ricavarlo** dall'equazione di
Shockley invertita, e solo dopo si procede identici all'es. 1.

### Calcoli

**Passo 1 — V_GS dalla Shockley invertita**

$$\begin{aligned}
I_D &= I_{DSS}\cdot (1 - V_{GS}/V_P)^{2} \\[8pt]
\sqrt{I_D/I_{DSS}} &= 1 - V_{GS}/V_P \\[8pt]
V_{GS} &= V_P\cdot (1 - \sqrt{I_D/I_{DSS}}) \\[8pt]
\sqrt{I_D/I_{DSS}} &= \sqrt{5\cdot 10^{-3}/12\cdot 10^{-3}} = \sqrt{0{,}4167} = 0{,}6455 \\[8pt]
V_{GS} &= -5 \cdot (1 - 0{,}6455) = -5 \cdot 0{,}3545 = -1{,}77\ \text{V}
\end{aligned}$$

*(Delle due radici, si scarta quella che darebbe $V_{GS} < V_P$, fuori dalla zona attiva.)*

$Passo 2 — R_S$

$$\begin{aligned}
R_S &= -V_{GS}/I_D = 1{,}77/5\cdot 10^{-3} = 354{,}5\,\Omega
\end{aligned}$$

$Passo 3 — R_D$

$$\begin{aligned}
R_D &= (V_{DD} - V_{DS} - R_S\cdot I_D)/I_D \\[2pt]
&= (18 - 10 - 354{,}5\cdot 5\cdot 10^{-3})/5\cdot 10^{-3} \\[2pt]
&= (18 - 10 - 1{,}77)/0{,}005 = 6{,}23/0{,}005 = 1245\,\Omega
\end{aligned}$$

$Passo 4 — R_G$: si sceglie, $1\ \text{M}\Omega$ (prof.: 5 MΩ).

**Verifica della saturazione**

$$\begin{aligned}
V_{GS} - V_P &= -1{,}77 - (-5) = 3{,}23\ \text{V} \\[2pt]
V_{DS} &= 10\ \text{V} \ge 3{,}23\ \text{V} \;\checkmark\quad\text{JFET in zona attiva}
\end{aligned}$$

> [!success] Risultato Es. 2
> $V_{GSO} = -1{,}77\ \text{V}$ · $R_S \approx 355\,\Omega$ (comm. $360\,\Omega$) · $R_D \approx 1{,}25\ \text{k}\Omega$ (comm. $1{,}2\ \text{k}\Omega$) · $R_G = 1\ \text{M}\Omega$ (scelta)

> [!danger] Trappola
> Fusi aveva l'impostazione giusta (il prof. ha segnato «OK» su tutte e tre le relazioni!)
> ma ha sbagliato l'aritmetica dentro Shockley: da $-5\cdot (1 - 0{,}6455)$ ha ottenuto prima
> $-1{,}85$, poi $-4{,}9$, poi $-24\ \text{V}$. Con $V_{GS} = -24\ \text{V}$ gli è uscito $R_S = 4{,}8\ \text{k}\Omega$.
> **Controllo di sanità mentale:** $V_{GS}$ deve sempre stare $fra V_P e 0$ (qui fra −5 e 0).
> Un $V_{GS}$ fuori da quell'intervallo è certamente sbagliato.

---

## Es. 3 — Determinare le tensioni di alimentazione V_GG e V_DD

**Dati:** $I_{DO} = 5\ \text{mA}$, $V_{DSO} = 10\ \text{V}$, $V_{GSO} = -2\ \text{V}$, $R_D = 6\ \text{k}\Omega$.
**Circuito:** polarizzazione **con batteria di gate separata** — $V_{GG}$ in serie al gate,
source direttamente a massa, $R_D$ fra drain e $V_{DD}$.

### Circuito

```
                 V_DD = ?
                     ●
                     │
                    ┌┴┐
                    │ │  R_D = 6 kΩ
                    └┬┘
                     │ D
                   ┌─┴─┐
        ┌──────────┤ J │   JFET-N
        │        G └─┬─┘
       ───           │ S
        ─   V_GG = ? │      (source direttamente a massa → V_GS = V_G)
        │  + verso   │
        │    massa   │
       ─┴────────────┴─   massa

 Batteria di gate separata, niente R_S: I_G = 0 → nessuna caduta nel ramo di gate,
 quindi V_G è esattamente la tensione della batteria, col segno dato dalla polarità.
 Maglia d'uscita con due soli termini:  V_DD = R_D·I_D + V_DS.
```

### Ragionamento
È il circuito più semplice di tutti, ed è per questo che l'esercizio vale poco tempo:
- il source è a massa → $V_S = 0$ → $V_{GS} = V_G$
- $I_G = 0$ → nessuna caduta nel ramo di gate → $V_G$ è **esattamente** la tensione della
  batteria (col segno imposto dalla polarità con cui è inserita)
- la maglia d'uscita ha solo $R_D$ e il transistor, perché non c'è $R_S$.

### Calcoli

**Tensione di gate**

$$\begin{aligned}
V_{GS} &= V_G - V_S = V_G - 0 = V_G = -2\ \text{V} \\[8pt]
\;\Rightarrow\; V_{GG} &= 2\ \text{V}
   \quad\text{(inserita col MORSETTO POSITIVO verso massa)}
\end{aligned}$$
(cioè con il gate al potenziale negativo rispetto al source)

**Tensione di alimentazione del drain** — maglia d'uscita $V_{DD} = R_D\cdot I_D + V_{DS}$:

$$\begin{aligned}
V_{DD} &= R_D\cdot I_{DO} + V_{DSO} = 6\cdot 10^{3} \cdot 5\cdot 10^{-3} + 10 \\[2pt]
&= 30 + 10 = 40\ \text{V}
\end{aligned}$$

> [!success] Risultato Es. 3
> $V_{GG} = 2\ \text{V}$ (polarità tale da rendere il gate negativo rispetto al source)
> $V_{DD} = 40\ \text{V}$
>
> Nota: $R_D\cdot I_D = 30\ \text{V}$ è tre volte $V_{DS}$. È una polarizzazione poco efficiente — tipica
> degli esercizi didattici, non di un progetto reale.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO»* — 0,00/1,00. Due somme.

---

## Es. 4 — Determinare il punto di lavoro e la tensione di alimentazione

**Dati:** $I_{DSS} = 12\ \text{mA}$, $V_P = -4{,}5\ \text{V}$, $V_{DSO} = 10\ \text{V}$, $V_{GSO} = -2\ \text{V}$, $R_D = 2{,}7\ \text{k}\Omega$.

### Circuito

```
                 V_DD = ?
                     ●
                     │
                    ┌┴┐
                    │ │  R_D = 2,7 kΩ
                    └┬┘
                     │ D
                   ┌─┴─┐
        ┌──────────┤ J │   JFET-N   I_DSS = 12 mA · V_P = −4,5 V
        │        G └─┬─┘
       ───           │ S
        ─   V_GG     │      V_GSO = −2 V (dato)
        │            │      V_DSO = 10 V (dato)
       ─┴────────────┴─   massa

 Qui V_GS è DATA: Shockley si usa in verso diretto, I_D = I_DSS·(1 − V_GS/V_P)²,
 poi la maglia d'uscita dà V_DD = V_DS + R_D·I_D.  È l'inverso dell'es. 2.
```

### Ragionamento
Qui $V_{GS}$ è **dato**, quindi Shockley si usa in **verso diretto** per ricavare $I_D$. Poi
la maglia d'uscita dà $V_{DD}$. È l'inverso dell'es. 2.

### Calcoli

**Passo 1 — corrente di drain da Shockley**

$$\begin{aligned}
I_D &= I_{DSS} \cdot (1 - V_{GS}/V_P)^{2} \\[8pt]
V_{GS}/V_P &= (-2)/(-4{,}5) = 0{,}4444 \\[8pt]
I_D &= 12\cdot 10^{-3} \cdot (1 - 0{,}4444)^{2} \\[2pt]
&= 12\cdot 10^{-3} \cdot (0{,}5556)^{2} \\[2pt]
&= 12\cdot 10^{-3} \cdot 0{,}3086 = 3{,}70\cdot 10^{-3}\ \text{A} = 3{,}70\ \text{mA}
\end{aligned}$$

**Passo 2 — verifica della zona di saturazione**

$$\begin{aligned}
V_{GS} - V_P &= -2 - (-4{,}5) = 2{,}5\ \text{V} \\[2pt]
V_{DS} &= 10\ \text{V} \ge 2{,}5\ \text{V} \;\checkmark
   \quad\text{(JFET in zona attiva, Shockley applicabile)}
\end{aligned}$$

**Passo 3 — tensione di alimentazione**

$$\begin{aligned}
V_{DD} &= V_{DS} + R_D\cdot I_D = 10 + 2700 \cdot 3{,}70\cdot 10^{-3} \\[2pt]
&= 10 + 10{,}0 = 20\ \text{V}
\end{aligned}$$

> [!success] Risultato Es. 4
> **Punto di lavoro Q: V_GSO = −2 V ; I_DO = 3,70 mA ; V_DSO = 10 V**
> $V_{DD} = 20\ \text{V}$
>
> Il risultato esatto ($R_D\cdot I_D = 10{,}0\ \text{V}$, esattamente metà di $V_{DD}$) è la conferma che i
> conti tornano: l'esercizio è costruito perché $V_{DS} = V_{RD} = V_{DD}/2$.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO»* — 0,00/1,00.

---

## Es. 5 — Progetto della polarizzazione a partitore di un JFET

**Dati:** $I_{DO} = 3{,}5\ \text{mA}$, $V_{GSO} = -1{,}5\ \text{V}$, $V_{DSO} = 11\ \text{V}$, $V_{DD} = 25\ \text{V}$,
$R_{1} + R_{2} = 2\ \text{M}\Omega$, $R_D = 3\ \text{k}\Omega$.
**Incognite:** $R_S$, $R_{1}$, $R_{2}$.

### Circuito

```
                     V_DD = 25 V
        ●─────────────────────────●
        │                         │
       ┌┴┐                       ┌┴┐
       │ │  R₁ = ?               │ │  R_D = 3 kΩ
       └┬┘                       └┬┘
        │                         │ D
        │                       ┌─┴─┐
        ├───────────────────────┤ J │   JFET-N
        │  V_G = 2 V          G └─┬─┘   I_G = 0
       ┌┴┐                        │ S
       │ │  R₂ = ?               ┌┴┐
       └┬┘                       │ │  R_S = ?
        │   R₁ + R₂ = 2 MΩ       └┬┘   V_S = 3,5 V
        │                         │
       ─┴─────────────────────────┴─   massa

 Partitore + autopolarizzazione: il gate NON è a massa, sta a V_G positiva,
 ma il source sta più in alto ancora  →  V_GS = V_G − V_S < 0.
 Il vincolo R₁ + R₂ = 2 MΩ chiude il problema e tiene alta l'impedenza d'ingresso.
```

### Ragionamento
È la polarizzazione **a partitore con autopolarizzazione** (la più stabile). A differenza
dell'autopolarizzazione pura, il gate $non$ è a massa ma a un potenziale positivo $V_G$
fissato dal partitore. La $V_{GS}$ negativa si ottiene facendo in modo che il source stia
**più in alto** del gate:

$$\begin{aligned}
V_{GS} &= V_G - V_S\,,\qquad V_S = R_S\cdot I_D
\end{aligned}$$

Quindi $V_S$ deve superare $V_G$ di 1,5 V. Il vincolo $R_{1} + R_{2} = 2\ \text{M}\Omega$ chiude il problema
(altrimenti il partitore sarebbe indeterminato) e garantisce alta impedenza d'ingresso.

### Calcoli

**Passo 1 — caduta su R_D**

$$\begin{aligned}
V_{RD} &= R_D\cdot I_{DO} = 3\cdot 10^{3} \cdot 3{,}5\cdot 10^{-3} = 10{,}5\ \text{V}
\end{aligned}$$

**Passo 2 — tensione di source dalla maglia d'uscita**
$V_{DD} = V_{RD} + V_{DS} + V_S$:

$$\begin{aligned}
V_S &= V_{DD} - V_{DSO} - V_{RD} = 25 - 11 - 10{,}5 = 3{,}5\ \text{V}
\end{aligned}$$

$Passo 3 — R_S$

$$\begin{aligned}
R_S &= V_S/I_{DO} = 3{,}5/3{,}5\cdot 10^{-3} = 1000\,\Omega = 1\ \text{k}\Omega
\end{aligned}$$

**Passo 4 — tensione di gate dalla maglia d'ingresso**
$V_{GS} = V_G - V_S$ → $V_G = V_{GS} + V_S$:

$$\begin{aligned}
V_G &= -1{,}5 + 3{,}5 = 2\ \text{V}
\end{aligned}$$

**Passo 5 — partitore**

$$\begin{aligned}
V_G &= V_{DD} \cdot R_{2}/(R_{1} + R_{2}) \\[8pt]
R_{2} &= V_G\cdot (R_{1} + R_{2})/V_{DD} = 2 \cdot 2\cdot 10^{6}/25 = 160\cdot 10^{3}\,\Omega = 160\ \text{k}\Omega \\[8pt]
R_{1} &= (R_{1} + R_{2}) - R_{2} = 2\cdot 10^{6} - 160\cdot 10^{3} = 1{,}84\cdot 10^{6}\,\Omega = 1{,}84\ \text{M}\Omega
\end{aligned}$$

**Verifica:** $V_G = 25 \cdot 160k/2M = 25 \cdot 0{,}08 = 2\ \text{V}$ \;\checkmark

> [!success] Risultato Es. 5
> **R_S = 1 kΩ · R₂ = 160 kΩ \text{(verso massa)} · R₁ = 1,84 MΩ (verso V_DD)**
> con $V_S = 3{,}5\ \text{V}$, $V_G = 2\ \text{V}$, $V_{GS} = -1{,}5\ \text{V}$.
>
> $R_{1} ∥ R_{2} \approx 147\ \text{k}\Omega$ è l'impedenza d'ingresso vista dal segnale: alta, come richiesto da uno
> stadio a JFET.

> [!note] Esercizio lasciato in bianco
> *«NON SVOLTO»* — 0,00/1,50. È l'esercizio da 1,50 punti più meccanico dei tre fascicoli.

---

## Es. 6 — MOSFET enhancement: determinare il punto di lavoro

**Dati:** $V_{DD} = 15\ \text{V}$, $R_{1} = 1{,}27\ \text{k}\Omega$, $R_{2} = 825\ \text{k}\Omega$, $R_D = 1{,}8\ \text{k}\Omega$, $K = 0{,}6\ \text{mA}/V^{2}$,
$V_t = 3\ \text{V}$. Ipotesi del testo: **MOS saturo**.
**Circuito:** partitore $R_{1}$(verso V_DD)–$R_{2}$\text{(verso massa)} sul gate, source a massa,
$R_D$ sul drain.

### Circuito

```
                     V_DD = 15 V
        ●─────────────────────────●
        │                         │
       ┌┴┐                       ┌┴┐
       │ │  R₁ = 1,27 kΩ         │ │  R_D = 1,8 kΩ
       └┬┘                       └┬┘
        │                         │ D
        │                       ┌─┴─┐
        ├───────────────────────┤ M │   MOSFET enh. canale N
        │  V_G = V_GS         G └─┬─┘   K = 0,6 mA/V² · V_t = 3 V
       ┌┴┐                        │ S
       │ │  R₂ = 825 kΩ           │
       └┬┘                        │      (source a massa: niente R_S)
        │                         │
       ─┴─────────────────────────┴─   massa

 Source a massa → V_GS = V_G, imposta SOLO dal partitore (I_G = 0, partitore a vuoto).
 L'ipotesi «MOS saturo» del testo va verificata alla fine: se V_DS risulta assurda,
 il MOS lavora in zona ohmica e si rifà il conto con I_D = K·[2(V_GS−V_t)V_DS − V_DS²].
```

### Ragionamento
Source a massa → $V_{GS} = V_G = V_{R2}$, imposta direttamente dal partitore ($I_G = 0$, il
partitore è a vuoto). Poi Shockley-MOS dà $I_D$, e la maglia d'uscita dà $V_{DS}$.
**Ma l'ipotesi «MOS saturo» va sempre verificata alla fine**, e qui è il punto dell'esercizio.

### Calcoli

**Passo 1 — V_GS dal partitore**

$$\begin{aligned}
V_{GS} &= V_{R2} = V_{DD} \cdot R_{2}/(R_{1} + R_{2}) \\[2pt]
&= 15 \cdot 825\cdot 10^{3}/(1{,}27\cdot 10^{3} + 825\cdot 10^{3}) \\[2pt]
&= 15 \cdot 825/826{,}27 = 14{,}98\ \text{V} \approx 14{,}9\ \text{V}
\end{aligned}$$

**Passo 2 — I_D in ipotesi di saturazione**

$$\begin{aligned}
I_D &= K\cdot (V_{GS} - V_t)^{2} = 0{,}6\cdot 10^{-3} \cdot (14{,}98 - 3)^{2} \\[2pt]
&= 0{,}6\cdot 10^{-3} \cdot (11{,}98)^{2} = 0{,}6\cdot 10^{-3} \cdot 143{,}5 \\[2pt]
&= 86{,}1\cdot 10^{-3}\ \text{A} \approx 85\ \text{mA}
\end{aligned}$$

**Passo 3 — verifica dell'ipotesi (il passaggio decisivo)**

$$\begin{aligned}
V_{DS} &= V_{DD} - R_D\cdot I_D = 15 - 1800 \cdot 0{,}0861 = 15 - 155 = -140\ \text{V}
\end{aligned}$$

**Impossibile**: $V_{DS}$ non può essere negativa in questo circuito. **L'ipotesi di
saturazione è falsa**: il MOSFET lavora in **zona ohmica (triodo)**.

**Passo 4 — soluzione corretta in zona ohmica**

$$\begin{aligned}
I_D &= K\cdot [2(V_{GS} - V_t)\cdot V_{DS} - V_{DS}^{2}]\quad\text{(equazione del MOS in triodo)} \\[2pt]
I_D &= (V_{DD} - V_{DS})/R_D\quad\text{(maglia d'uscita)} \\[8pt]
\text{uguagliando, con } V_{GS} - V_t &= 11{,}98\ \text{V}: \\[8pt]
(15 - V_{DS})/1800 &= 0{,}6\cdot 10^{-3}\cdot [2\cdot 11{,}98\cdot V_{DS} - V_{DS}^{2}] \\[2pt]
15 - V_{DS} &= 1{,}08\cdot [23{,}96\cdot V_{DS} - V_{DS}^{2}] \\[2pt]
15 - V_{DS} &= 25{,}88\cdot V_{DS} - 1{,}08\cdot V_{DS}^{2} \\[8pt]
1{,}08\cdot V_{DS}^{2} - 26{,}88\cdot V_{DS} + 15 &= 0 \\[8pt]
\Delta &= 26{,}88^{2} - 4\cdot 1{,}08\cdot 15 = 722{,}5 - 64{,}8 = 657{,}7 \\[2pt]
\sqrt{\Delta } &= 25{,}64 \\[8pt]
V_{DS} &= (26{,}88 \pm 25{,}64)/2{,}16 \;\Rightarrow\; V_{DS} = 0{,}574\ \text{V} \;\text{ oppure }\; V_{DS} = 24{,}3\ \text{V}\ \text{(scartata: } > V_{DD}) \\[8pt]
I_D &= (15 - 0{,}574)/1800 = 8{,}01\cdot 10^{-3}\ \text{A} = 8{,}0\ \text{mA}
\end{aligned}$$

Verifica: $V_{DS} = 0{,}574\ \text{V} < V_{GS} - V_t = 11{,}98\ \text{V}$ \;\checkmark → zona ohmica confermata.

> [!success] Risultato Es. 6
> $V_{GS} = 14{,}98\ \text{V}$ (imposta dal partitore)
> **L'ipotesi «MOS saturo» del testo NON è verificata**: il MOSFET lavora in **zona ohmica**.
> **Punto di lavoro reale: V_DS ≈ 0,57 V ; I_D ≈ 8,0 mA.**
>
> Il MOSFET si comporta praticamente da interruttore chiuso: $R_{DSon} \approx 0{,}574/0{,}008 = 72\,\Omega$.

> [!warning] Il dato è probabilmente un refuso del testo
> Se $R_{1}$ fosse $1{,}27\ \text{M}\Omega$ (e non 1,27 kΩ) l'esercizio tornerebbe pulito:
> ```
> V_GS = 15 · 825/(1270 + 825) = 5,91 V
> I_D  = 0,6·10⁻³·(5,91 − 3)² = 5,07 mA
> V_DS = 15 − 1800·5,07·10⁻³ = 5,87 V
> Verifica: V_DS = 5,87 ≥ V_GS − V_t = 2,91  \;\checkmark  MOS SATURO
> ```
> Cioè $Q(V_{DS} = 5{,}87\ \text{V} ; I_D = 5{,}07\ \text{mA})$, che è una polarizzazione sensata per un
> amplificatore. All'esame conviene: svolgere con i dati letterali, accorgersi che
> l'ipotesi non regge, **dichiararlo per iscritto**, e — se si sospetta il refuso —
> aggiungere la soluzione coerente. Il prof. premia il controllo, non il numero.

> [!danger] Trappola
> Fusi ha scritto $I_D = 84{,}9\ \text{A}$ (ampere invece di milliampere) e ha usato una relazione
> $V_{GS} = V_t + \sqrt{I_D/R_D}$ che il prof. ha cancellato con «NON SERVE»: mescola una corrente
> con una resistenza sotto radice, è dimensionalmente impossibile. La sola relazione da usare
> è $I_D = K\cdot (V_{GS} - V_t)^{2}$, e $V_{GS}$ viene **solo** dal partitore.

---

## Es. 7 — Progetto della polarizzazione di un MOSFET (senza R_S)

**Dati:** $V_{DD} = 25\ \text{V}$, $I_D = 3\ \text{mA}$, $K = 0{,}3\ \text{mA}/V^{2}$, $V_t = 4\ \text{V}$, $R_{1} + R_{2} = 10\ \text{M}\Omega$.
Ipotesi: MOS saturo. **Incognite:** $R_D$, $R_{1}$, $R_{2}$.
**Circuito:** partitore sul gate, source a massa, $R_D$ sul drain.

### Circuito

```
                     V_DD = 25 V
        ●─────────────────────────●
        │                         │
       ┌┴┐                       ┌┴┐
       │ │  R₁ = ?               │ │  R_D = ?
       └┬┘                       └┬┘
        │                         │ D
        │                       ┌─┴─┐
        ├───────────────────────┤ M │   MOSFET enh. canale N
        │  V_G = V_GS         G └─┬─┘   K = 0,3 mA/V² · V_t = 4 V
       ┌┴┐                        │ S
       │ │  R₂ = ?                │
       └┬┘                        │      (source a massa: niente R_S)
        │   R₁ + R₂ = 10 MΩ       │
       ─┴─────────────────────────┴─   massa

 Stessa topologia dell'es. 6, ma è un PROGETTO: I_D è data, V_GS esce da
 V_GS = V_t + √(I_D/K), mentre V_DS è una scelta libera purché V_DS ≥ V_GS − V_t.
```

### Ragionamento
Corrente e transistor sono dati, quindi $V_{GS}$ è **determinata**. $V_{DS}$ invece è **libera**:
è una scelta di progetto, vincolata solo dalla condizione di saturazione
$V_{DS} \ge V_{GS} - V_t$. Si sceglie un valore comodo e ampiamente dentro la zona attiva.

### Calcoli

**Passo 1 — V_GS dall'equazione del MOS invertita**

$$\begin{aligned}
I_D &= K\cdot (V_{GS} - V_t)^{2} \;\Rightarrow\; V_{GS} = V_t + \sqrt{I_D/K} \\[8pt]
\sqrt{I_D/K} &= \sqrt{3\cdot 10^{-3} / 0{,}3\cdot 10^{-3}} = \sqrt{10} = 3{,}162 \\[8pt]
V_{GS} &= 4 + 3{,}162 = 7{,}16\ \text{V}
\end{aligned}$$

**Passo 2 — scelta di V_DS**

$$\begin{aligned}
&\text{vincolo di saturazione}:\;\; V_{DS} \ge V_{GS} - V_t = 7{,}16 - 4 = 3{,}16\ \text{V} \\[8pt]
\text{si sceglie } V_{DS} &= V_{DD}/2 = 12{,}5\ \text{V}\quad\text{(ampiamente > 3,16 V e < V\_DD, escursione simmetrica)}
\end{aligned}$$

**Passo 3 — R_D dalla maglia d'uscita**

$$\begin{aligned}
R_D &= (V_{DD} - V_{DS})/I_D = (25 - 12{,}5)/3\cdot 10^{-3} = 12{,}5/0{,}003 = 4167\,\Omega \approx 4{,}17\ \text{k}\Omega
\end{aligned}$$

**Passo 4 — partitore di gate** (source a massa → $V_G = V_{GS}$)

$$\begin{aligned}
V_{GS} &= V_{DD} \cdot R_{2}/(R_{1} + R_{2}) \\[8pt]
R_{2} &= (V_{GS}/V_{DD})\cdot (R_{1} + R_{2}) = (7{,}16/25) \cdot 10\cdot 10^{6} \\[2pt]
&= 0{,}2865 \cdot 10^{7} = 2{,}86\cdot 10^{6}\,\Omega = 2{,}86\ \text{M}\Omega \\[8pt]
R_{1} &= 10\cdot 10^{6} - 2{,}86\cdot 10^{6} = 7{,}14\cdot 10^{6}\,\Omega = 7{,}14\ \text{M}\Omega
\end{aligned}$$

**Verifica finale**

$$\begin{aligned}
V_G &= 25 \cdot 2{,}86/10 = 7{,}16\ \text{V} \approx V_{GS} \;\checkmark \\[2pt]
I_D &= 0{,}3\cdot 10^{-3}\cdot (7{,}16 - 4)^{2} = 0{,}3\cdot 10^{-3}\cdot 9{,}99 = 3{,}0\ \text{mA} \;\checkmark \\[2pt]
V_{DS} &= 12{,}5\ \text{V} \ge 3{,}16\ \text{V} \;\checkmark\quad\text{(saturo)}
\end{aligned}$$

> [!success] Risultato Es. 7
> **R_D ≈ 4,17 kΩ (comm. 3,9 kΩ) · R₂ ≈ 2,86 MΩ \text{(verso massa)} · R₁ ≈ 7,14 MΩ (verso V_DD)**
> con $V_{GS} = 7{,}16\ \text{V}$, $V_{DS} = 12{,}5\ \text{V}$ (scelta di progetto).
>
> Una $V_{DS}$ diversa dà $R_D$, $R_{1}$ e $R_{2}$ diversi ma ugualmente validi, purché resti
> $V_{DS} \ge 3{,}16\ \text{V}$ e la scelta sia dichiarata. Solo $V_{GS} = 7{,}16\ \text{V}$ è imposta dai dati.

> [!warning] Correzione di una versione precedente di questa nota (2026-08-30)
> Qui era riportato $V_{DD} = 15\ \text{V}$, con $R_D = 2\ \text{k}\Omega$, $R_{2} = 4{,}78\ \text{M}\Omega$, $R_{1} = 5{,}22\ \text{M}\Omega$. Rileggendo
> la scansione a 300 dpi il testo dell'es. 7 dice **$V_{DD} = 25\ \text{V}$**: i 15 V sono la $V_{DD}$
> dell'$es. 6$, che sta subito sopra sulla stessa pagina. Anche Fusi aveva lavorato con 15 V.
> Il «2» dell'es. 7 è tondo, l'«1» dell'es. 6 è un tratto dritto: alla risoluzione piena si
> distinguono.

> [!danger] Trappola
> Fusi ha poi scritto
> $V_{GS} = V_t + \sqrt{I_D/R_D} = 4 + \sqrt{3\cdot 10^{-3}/2\cdot 10^{3}} = 4{,}1\ \text{V}$ — **la stessa relazione
> dimensionalmente impossibile dell'es. 6**: sotto radice va $I_D/K$, non $I_D/R_D$.
> Con $V_{GS} = 4{,}1\ \text{V}$ e $V_{DD} = 15\ \text{V}$ gli è uscito $R_{2} = 2{,}73\ \text{M}\Omega$.
> Il prof. ha cerchiato la formula e scritto **«relazione errata»**, poi ha ricalcolato lui
> $V_{GS} = \sqrt{I_D/K} + V_t = 7{,}16\ \text{V}$.

---

## Es. 8 — Progetto della polarizzazione di un MOSFET con R_S

**Dati:** $I_{DO} = 8\ \text{mA}$, $V_{GSO} = 6\ \text{V}$, $V_{DSO} = 10\ \text{V}$, $V_{DD} = 15\ \text{V}$, $V_S = 3\ \text{V}$,
$R_{1} + R_{2} = 2\ \text{M}\Omega$.
**Incognite:** $R_D$, $R_S$, $R_{1}$, $R_{2}$.

### Circuito

```
                     V_DD = 15 V
        ●─────────────────────────●
        │                         │
       ┌┴┐                       ┌┴┐
       │ │  R₁ = ?               │ │  R_D = ?
       └┬┘                       └┬┘
        │                         │ D
        │                       ┌─┴─┐
        ├───────────────────────┤ M │   MOSFET enh. canale N
        │  V_G = V_GS + V_S   G └─┬─┘   V_GSO = 6 V · I_DO = 8 mA
       ┌┴┐     = 9 V              │ S
       │ │  R₂ = ?               ┌┴┐
       └┬┘                       │ │  R_S = ?
        │   R₁ + R₂ = 2 MΩ       └┬┘   V_S = 3 V
        │                         │
       ─┴─────────────────────────┴─   massa

 Rispetto all'es. 7 c'è R_S, e cambia DUE cose (le due trappole di questo esercizio):
   1) maglia d'uscita con tre cadute:  V_DD = R_D·I_D + V_DS + V_S
   2) il partitore impone V_G = V_GS + V_S, non V_GS: il source è sollevato da massa.
 R_D e R_S non sono in serie fra loro — in mezzo c'è il transistor. Vale I_S = I_D.
```

### Ragionamento
Rispetto all'es. 7 c'è $R_S$, che introduce **due differenze**, ed entrambe sono le trappole
che Fusi ha centrato:

1. la maglia d'uscita ha $tre$ cadute: $V_{DD} = V_{RD} + V_{DS} + V_S$
2. il gate non è più a $V_{GS}$ ma a $V_G = V_{GS} + V_S$, perché il source è sollevato da massa.

$R_S$ serve a stabilizzare il punto di lavoro: se $I_D$ tende a crescere, $V_S$ sale, $V_{GS}$
scende e $I_D$ viene riportata giù (controreazione).

### Calcoli

$Passo 1 — R_S$

$$\begin{aligned}
R_S &= V_S/I_{DO} = 3/8\cdot 10^{-3} = 375\,\Omega
\end{aligned}$$

**Passo 2 — R_D dalla maglia d'uscita completa**

$$\begin{aligned}
V_{DD} &= R_D\cdot I_D + V_{DS} + V_S \\[8pt]
R_D &= (V_{DD} - V_{DSO} - V_S)/I_{DO} = (15 - 10 - 3)/8\cdot 10^{-3} \\[2pt]
&= 2/0{,}008 = 250\,\Omega
\end{aligned}$$

**Passo 3 — tensione di gate**

$$\begin{aligned}
V_G &= V_{GS} + V_S = 6 + 3 = 9\ \text{V}
\end{aligned}$$

**Passo 4 — partitore**

$$\begin{aligned}
V_G &= V_{DD} \cdot R_{2}/(R_{1} + R_{2}) \\[8pt]
R_{2} &= (V_G/V_{DD})\cdot (R_{1} + R_{2}) = (9/15) \cdot 2\cdot 10^{6} = 0{,}6 \cdot 2\cdot 10^{6} = 1{,}2\cdot 10^{6}\,\Omega = 1{,}2\ \text{M}\Omega \\[8pt]
R_{1} &= 2\cdot 10^{6} - 1{,}2\cdot 10^{6} = 0{,}8\cdot 10^{6}\,\Omega = 800\ \text{k}\Omega
\end{aligned}$$

**Verifica**

$$\begin{aligned}
V_G &= 15 \cdot 1{,}2/2 = 9\ \text{V} \;\checkmark \\[2pt]
V_{GS} &= V_G - V_S = 9 - 3 = 6\ \text{V} \;\checkmark \\[2pt]
\text{maglia d'uscita}:\;\; 250\cdot 0{,}008 + 10 + 3 &= 2 + 10 + 3 = 15\ \text{V} = V_{DD} \;\checkmark
\end{aligned}$$

> [!success] Risultato Es. 8
> **R_S = 375 Ω · R_D = 250 Ω · R₂ = 1,2 MΩ \text{(verso massa)} · R₁ = 800 kΩ (verso V_DD)**
>
> Valori commerciali: $R_S = 390\,\Omega$, $R_D = 240\,\Omega$, $R_{2} = 1{,}2\ \text{M}\Omega$, $R_{1} = 820\ \text{k}\Omega$.

> [!danger] Trappola — l'unico «ERRATO» pieno di questa verifica
> Fusi ha commesso **entrambi** gli errori tipici del circuito con $R_S$:
> 1. $R_D = (V_{DD} - V_{DS})/I_D = (15-10)/8m = 625\,\Omega$ → $ha dimenticato V_S$ nella maglia
>    d'uscita. Il prof. ha aggiunto in rosso «$- V_S$».
> 2. $R_{2} = (V_{R2}/V_{DD})\cdot (R_{1}+R_{2})$ con $V_{R2} = 6\ \text{V}$ invece di 9 V → **ha usato V_GS al posto di
>    V_G**, dimenticando che il source è a 3 V. Il prof. ha aggiunto in rosso «$+ V_S$»,
>    scrivendo $V_{R2} = V_{GS} + V_S$.
>
> Ha inoltre scritto $I_S = R_S/(R_D+R_S)\cdot I_D$ e $V_S = R_S/(R_D+R_S)\cdot V_{DD}$: sono formule da
> partitore applicate a un ramo che **non è un partitore** — $R_D$ e $R_S$ non sono in serie
> fra loro con niente in mezzo, c'è il transistor. Vale sempre $I_S = I_D$ e
> $V_S = R_S\cdot I_D$.

---

# Appendice — Le sei trappole che valgono il 70% dei punti persi

Un riassunto operativo, ordinato per quante volte Carli l'ha segnata in rosso sui tre
fascicoli.

| # | Trappola | Dove compare | Come non caderci |
|---|---|---|---|
| 1 | **Maglie d'ingresso e d'uscita mescolate** ($R_B$ con $R_C$) | V2 es. 2, 6, 7 | Prima di scrivere l'equazione, chiediti: *questa resistenza è percorsa da I_B, I_C o I_E?* Le due maglie condividono solo il ramo di emettitore. |
| 2 | **$I_G \approx 0$ dimenticato** → $R_G$ calcolata da una legge | V3 es. 1, 2 | Nel JFET/MOSFET il gate non assorbe corrente. **$R_G$ si sceglie (1÷10 MΩ), non si calcola.** |
| 3 | **$V_S$ dimenticata** nella maglia d'uscita o nel partitore | V2 es. 3, V3 es. 8 | Se c'è $R_S$/$R_E$: $V_{DD} = V_{RD} + V_{DS} + V_S$ e $V_G = V_{GS} + V_S$. Tre termini, non due. |
| 4 | **Formule dimensionalmente impossibili** ($\sqrt{I_D/R_D}$, $\arctan (1/\|Z\|)$) | V1 es. 1B, V3 es. 6, 7 | Controlla le unità di misura del risultato: se non sono volt/ampere/ohm come devono, la formula è sbagliata a prescindere dai numeri. |
| 5 | **Valori numerici sostituiti male** (10 al posto di 12, f errata) | V1 es. 1A, V2 es. 1 | Riscrivi i dati in colonna prima di iniziare e spuntali man mano che li usi. |
| 6 | **Ipotesi non verificata a fine esercizio** (saturo/attivo) | V3 es. 6, V2 es. 6 | Ogni esercizio con un'ipotesi (`MOS saturo`, `BJT in zona attiva`) si **chiude** con la verifica. Se non regge, dillo e rifai con l'altra zona. |

> [!tip] La differenza fra 3/10 e 7/10
> Sui tre fascicoli, **6 esercizi su 21 sono stati lasciati completamente in bianco** — e
> valgono 7,50 punti su 30. Sono, in ordine: V1 es. 5 (due divisioni), V2 es. 4 e 5, V3
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
