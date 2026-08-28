---
tags: [recupero, elettronica, formulario, cheat-sheet, comparazione, compito, rapido]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), studente Davide Rocca, classe 4BEM"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) per derivazione — file trasversale: non cita direttamente il libro, ma raccoglie le formule dei file di argomento, ciascuno verificato pagina per pagina sul Mirandola nei Lotti 1-13 della bonifica. Per il riferimento di libro di ogni formula si va alla nota dell'argomento corrispondente. Vedi «00 - Fonti e note» e «00 - Audit e correzioni»."
prove: [scritta]
nota_unione: "2026-08-27 — «Cheat Sheet A4 visuale» è stato fuso qui dentro come Parte A. Le vecchie sezioni §1-§7 del Cheat Sheet sono ora §A1-§A7; la numerazione §1-§13 del Formulario è invariata."
---

# 📋 Formulario + Cheat Sheet — da portare al compito Carli (1 set., 8:00-13:00)

> [!warning] USO
> Questo file è **SOLO formule e tabelle**. Nessuna spiegazione: per i perché vedi [[Argomenti]] e [[Esercizi]]. Stampalo (A4 fronte-retro) o tienilo aperto su un telefono durante lo scritto.
> - **[Parte A](#parte-a--tabelle-comparative-lookup-5-secondi)** = tabelle comparative, lookup da 5 secondi (§A1-§A7)
> - **[Parte B](#parte-b--formule-per-macroarea)** = formulario per macroarea (§1-§13)

> **Lookup 5s** → §A1 transistor · §A2 amplif · §A3 risonante · §A3b diodi · §A4 filtri · §A5 AC/DC · §A6 alimentatore · §A7 visione 30s

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
