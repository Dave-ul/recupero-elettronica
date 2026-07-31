---
tags: [recupero, elettronica, cheat-sheet, comparazione]
fonte: "confronto diretto per consultazione 5s durante compito 90 min"
---

# 🗺️ Cheat Sheet A4 — 5s lookup compito 90' Carli

> Tabella comparativa = confronto diretto. Per approfondire → `[[Formulario rapido]]` o hub `[[00 - Perchè (spiegazione intuitiva)]] §N`.

---

## 1. BJT vs MOSFET vs JFET

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

## 2. Amplificatori BJT — CE vs CC vs CB

| | **CE** (Emettitore Comune) | **CC** (Emitter Follower) | **CB** (Base Comune) |
|---|---|---|---|
| **$A_v$** | Alto (10–100), **inverte 180°** | ≈ 1 (0,95–0,99) | Alto, NO inversione |
| **$Z_{in}$** | ~kΩ | **alta** ~100 kΩ | bassa ~100 Ω |
| **$Z_{out}$** | ~10 kΩ | **bassa** ~100 Ω | alta ~MΩ |
| **$A_i$** | ≈ β (~100) | ≈ β | ≈ 1 |
| **Uso** | generale, amplif. tensione | **buffer**, adatt. impedenza | RF, alte frequenze |

## 3. RLC serie vs parallelo @ $\omega_0 = 1/\sqrt{LC}$

| | **SERIE** | **PARALLELO** |
|---|---|---|
| **Impedenza a $\omega_0$** | **MINIMA** (= $R$) | **MASSIMA** (= $R$) |
| **Corrente totale** | **MASSIMA** | minima |
| **$V_L$ o $V_C$** | $= Q \cdot V_{tot}$ ⚠️ | $= V_{tot}$ |
| **$I_L$ o $I_C$** | $= I_{tot}$ | $= Q \cdot I_{tot}$ ⚠️ |
| **$Q$ (merito)** | $\omega_0 L / R$ | $\omega_0 L / R$ |
| **Banda passante** | $\omega_0 / Q$ | $\omega_0 / Q$ |

### 3b. Diodi — normale vs Zener vs Schottky

| | **Diodo normale** | **Zener** | **Schottky** |
|---|---|---|---|
| **$V_F$ diretta** | ≈ 0,7 V (Si) | ≈ 0,7 V | ≈ 0,2–0,4 V |
| **Funzione tipica** | raddrizzatore | regolatore ($V_Z$ fisso) | switching rapido |
| **Breakdown** | DISTRUTTIVO ⚠️ | **modalità di lavoro** | bassa backward leakage |
| **Switching** | medio (~μs) | medio (~μs) | veloce (ns) |
| **Uso** | Graetz, OR/AND logica | stabilizzatore (es. 5,6 V) | free-wheeling, RF, SMPS |

## 4. Filtri RC vs RL (PB = passa-basso, PA = passa-alto)

| Filtro | $f_t$ (taglio) | Dove va C/L |
|---|---|---|
| **RC PB** | $1/(2\pi R C)$ | C verso massa |
| **RC PA** | $1/(2\pi R C)$ | C in serie |
| **RL PB** | $R/(2\pi L)$ | L verso massa |
| **RL PA** | $R/(2\pi L)$ | L in serie |

**Regola**: reattivo in **serie** blocca le basse, verso **massa** blocca le alte. **−3 dB** = metà potenza.

## 5. Monofase vs Trifase

| | **MONOFASE** | **TRIFASE** |
|---|---|---|
| **Fili** | 2 (fase + neutro) | 3 (R,S,T) + neutro opz. |
| **Sfasamento** | — | 120° tra fasi |
| **$V_{\text{conc}}$** | = $V_{\text{fase}}$ | $= \sqrt{3} \cdot V_{\text{fase}}$ |
| **$P$ totale** | $P = V I \cos\varphi$ | $P = \sqrt{3} \cdot V_{\text{conc}} \cdot I \cos\varphi$ |
| **$Q$ totale** | $Q = V I \sin\varphi$ | $Q = \sqrt{3} \cdot V_{\text{conc}} \cdot I \sin\varphi$ |
| **Uso** | civile (230 V 50 Hz) | industriale (400 V 50 Hz) |

## 6. AC vs DC

| | **DC** (ω = 0) | **AC** (sinusoidale) |
|---|---|---|
| **$X_L$** | 0 (corto) | $j\omega L$ |
| **$X_C$** | ∞ (aperto) | $-j/(\omega C)$ |
| **$V$ vs $I$ su L** | — | $V$ anticipa $I$ di 90° |
| **$V$ vs $I$ su C** | — | $V$ ritarda $I$ di 90° |
| **Potenza** | $P = V I$ | $P=VI\cos\varphi$, $Q=VI\sin\varphi$, $S=\sqrt{P^2+Q^2}$ |
| **Rifasamento** | non serve | $C$ parallelo al carico induttivo → annulla $Q$ |

## 7. Alimentatore a blocchi

```
AC 230V 50Hz → trafo (abbassa + isola) → AC es.12V
→ ponte Graetz (4 diodi) → DC pulsante ~17V picco
→ C filtro (livella, ripple ≈ I_carico/(f·C), f=100Hz dopo ponte)
→ regolatore 78xx (dropout 2V, V_in ≥ V_out + 2V) → DC stabile
```

## 8. Mnemonico 30s (visione d'insieme)

- **Sinusoidi**: rotazione → $\cos\omega t$ → derivata = $\sin$ (**Faraday**)
- **Impedenze**: R pura, L anticipa +90°, C ritarda −90°
- **Potenze**: $P$ consumata, $Q$ rimbalzo, $S=\sqrt{P^2+Q^2}$ → **P+Q≠S**
- **Risonanza**: $\omega_0^2=1/LC$ → $X_L=X_C$ → tutto resistivo
- **Filtri**: ω alta → C verso massa; ω bassa → C in serie
- **Transistor**: BJT $I_C=\beta I_B$ (sat=ON); MOSFET/JFET $I_D=K(…)^2$ (sat=amplifica)
- **Amplificatori**: CE amplif+inverte; CC buffer $A_v\approx 1$; CB alte freq
- **Alimentatore**: AC → trafo → ponte → C filtro → regolatore → DC
- **Rifasamento**: C parallelo a $L$ → annulla $Q$ → meno $I$ in linea
- **Trifase**: $P = \sqrt{3}\,V_{\text{conc}}\,I\cos\varphi$; $V_{\text{conc}}=\sqrt{3}\,V_{\text{fase}}$

> **Lookup 5s** (§1 transistor · §2 amplif · §3 risonante · §3b diodi · §4 filtri · §5 trifase · §6 AC/DC · §7 alimentatore · §8 visione 30s)
