---
tags: [recupero, elettronica, formulario, compito, rapido]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), studente Davide Rocca, classe 4BEM"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) per derivazione — file trasversale: non cita direttamente il libro, ma raccoglie le formule dei file di argomento, ciascuno verificato pagina per pagina sul Mirandola nei Lotti 1-13 della bonifica. Per il riferimento di libro di ogni formula si va alla nota dell'argomento corrispondente. Vedi «00 - Fonti e note» e «00 - Audit e correzioni»."
prove: [scritta]
---

# 📋 Formulario rapido — da portare al compito Carli

> [!warning] USO
> Questo file è **SOLO formule**. Nessuna spiegazione: per i perché vedi [[Argomenti]] e [[Esercizi]]. Stampalo o tienilo aperto su un telefono durante il compito scritto. Il contenuto è organizzato per macroarea.

---

## 1. Impedenze (R, L, C) — regime sinusoidale

| Bipolo | $Z$ in forma complessa | Note |
|---|---|---|
| $R$ | $Z_R = R$ | Nessuno sfasamento |
| $L$ | $Z_L = j\omega L$ | $+90°$ V anticipo su I |
| $C$ | $Z_C = \dfrac{1}{j\omega C} = -\dfrac{j}{\omega C}$ | $-90°$ V ritardo su I |

$$\omega = 2\pi f \qquad X_L = \omega L \qquad X_C = \dfrac{1}{\omega C}$$

> **Errata corrige libro**: $\tau = L/R$ per RL, NON $R/L$. ⚠️

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

$$\omega_0 = \frac{1}{\sqrt{LC}} = 2\pi f_0 \qquad f_0 \approx 159{,}15 / \sqrt{L_{\text{mH}} C_{\mu\text{F}}} \text{ kHz}$$

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

> ⚠️ Tutte le formule valgono SOLO **in saturazione** (zona ohmica). Verifica finale: $V_{DS} > V_{GS} - V_{th}$.

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

$$A_v(s) = \frac{A_{v,\text{mid}}}{\left(1 + \dfrac{s}{2\pi f_L}\right)\left(1 + \dfrac{s}{2\pi f_H}\right)}$$

$f_L$: taglio inferiore (da $C$ di accoppiamento). $f_H$: taglio superiore (parassiti).

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
$$R_{S,\min} = \frac{V_{in,\max} - V_Z}{I_{Z,\max}} \qquad R_{S,\max} = \frac{V_{in,\min} - V_Z}{I_{Z,\min} + I_{L,\max}}$$

---

## 11. Alimentatori

### 11.1 Raddrizzatore

- **Semionda**: $V_{out,p} = V_{in,p} - V_D$; ripple con $f_r = f_{\text{rete}}$.
- **Ponte Graetz**: $V_{out,p} = V_{in,p} - 2V_D$; ripple con $f_r = 2 f_{\text{rete}}$.

### 11.2 Ripple a frequenza $f_r$ e corrente di carico $I_L$

$$V_{r,pp} = \frac{I_L}{f_r \cdot C} \qquad I_L = V_L/R_L \qquad C = \frac{I_L}{f_r V_{r,pp}}$$

**Fattore di ripple** (Mirandola form. **8.1**, Cap. 8 pp. 388-389) — è un valore **efficace**, non picco-picco:

$$\boxed{r = \frac{V_{r,\text{eff}}}{V_{Lm}} = \frac{1}{2\sqrt{3}\, f R_L C}} \qquad\Rightarrow\qquad C = \frac{1}{2\sqrt{3}\, f R_L\, r}$$

> [!danger] Le due formule rispondono a domande diverse — non scambiarle
> Se il testo dà i **volt** di ondulazione ($V_{r,pp} = 2$ V) usi la **11.2**. Se dà una **percentuale** («ripple del 5%») quella percentuale è $r$, cioè un **rapporto fra valori efficaci**: usi la 8.1. Interpretare il 5% come picco-picco porta a una $C$ sbagliata di un fattore ~3,5 — è l'errore trovato e corretto nell'Es. A1 di [[Esercizi - Alimentatori]].

### 11.3 Regolatore serie a BJT

$$V_o = V_Z - V_{BE} = V_Z - 0{,}7 \text{ V} \qquad V_{in} \ge V_o + 1 \text{ V (margine zona attiva)}$$

$$P_{BJT} = (V_{in} - V_o) I_L$$

### 11.4 Regolatori integrati 78xx / 79xx

- $V_{dropout} \approx 2$ V → serve $V_{in} \ge V_{out} + 2$ V
- 78xx = positivo, 79xx = negativo; xx = tensione (es. 7812 = +12 V)
- $I_{out,\max}$: standard 1 A, suffix L=100 mA, M=500 mA
- $C_{in} \approx 0{,}33\,\mu$F, $C_{out} \approx 0{,}1\,\mu$F (per stabilità)

---

## 12. Rifasamento trifase

### 12.1 Tensioni trifase

$$V_{\text{fase}} = \frac{V_{\text{conc}}}{\sqrt{3}} \qquad V_{\text{conc}} = \sqrt{3} \cdot V_{\text{fase}}$$

### 12.2 Potenze trifase (carico equilibrato)

$$P = \sqrt{3} V_{\text{conc}} I \cos\varphi \qquad Q = \sqrt{3} V_{\text{conc}} I \sin\varphi \qquad S = \sqrt{3} V_{\text{conc}} I$$

### 12.3 Rifasamento (3 C tra fase e neutro, configurazione stella)

$$C_{\text{fase}} = \frac{\Delta Q / 3}{\omega V_{\text{fase}}^2} = \frac{P(\tan\varphi - \tan\varphi')}{3 \omega V_{\text{fase}}^2}$$

⚠️ **Mnemonico**: il risultato è la $C$ di **ciascuno dei 3 condensatori**. Per la **$C$ totale equivalente**: $C_{\text{eq}} = 3 C_{\text{fase}}$.

### 12.4 Target

$$\cos\varphi' \ge 0{,}9 \quad \text{(tipico, mai }1{,}0\text{ per evitare autoeccitazione)}$$

---

## 13. Costanti e numeri da ricordare

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

## 14. Mnemonico finale (le 5 cose che DEVI ricordare)

1. **Filtri**: RC → $f_t = 1/(2\pi RC)$. RL → $f_t = R/(2\pi L)$ (NON $L/R$).
2. **Fasori**: cartesiano per somma/diff, polare per prod/quot. **Attenzione ai quadranti di $\arctan$**.
3. **BJT**: $V_{CE} = V_{CC} - I_C R_C - I_E R_E$ (con $R_E$: non dimenticare il terzo termine).
4. **MOSFET**: parabolica SOLO in saturazione. **Verifica finale** $V_{DS} > V_{GS} - V_{th}$.
5. **Trifase**: $V_{\text{fase}} = V_{\text{conc}}/\sqrt{3}$, $\Delta Q_{\text{fase}} = \Delta Q/3$ (per il $C$ per fase).

---

## Da qui in poi

- Teoria completa: [[Argomenti]]
- Esercizi svolti: [[Esercizi]]
- Simulazione completa d'esame: [[Esercizi - Simulazione finale]]
- Prove: [[01 - Prova Scritta Carli]], [[02 - Prova Orale Carli]], [[03 - Prova Pratica Protti]]
