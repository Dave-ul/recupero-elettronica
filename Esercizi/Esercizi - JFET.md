---tags: [recupero, elettronica, esercizi, jfet, amplificatore, vcr, switch]
fonte: "edutecnica.it/elettronica/jfet/ + jfetx/ + ajfet/ + ajfetx/ + esercizi costruiti per il recupero"
libro_mirandola: "VERIFICATO ✔ (2026-07-28) — coerente con Mirandola Vol.2, Cap. 7 «Gli amplificatori a transistor», §3 «I transistor FET e gli amplificatori a FET» — parte JFET pp. 358-365. Struttura, pinch-off, polarizzazione, curve d'uscita del 2N3819 (FIG. 42 a p. 362). File trasversale: teoria già verificata nel [[Prove/00 - Audit e correzioni|Lotto 12]]. Conversion folio Cap. 7: pag. stampata = 2·PDF + 122."
prove: [scritta, orale, pratica]---

# Esercizi — JFET (n-channel, amplificatori, VCR, switch, P-channel)

> [!info] Dove serve
> **Scritta Carli** (LETTERA): esercizi su transistor JFET a canale n (polarizzazione + amplificazione). **Orale Carli** (LETTERA): NON cita JFET — solo «diodo, circuiti AC, filtri 1° ordine». I confronti BJT/MOSFET/JFET all'orale sono **estensione naturale** ma non testualmente richiesti. **Pratica Protti**: identificazione pin, misura $I_{DSS}$ e $V_P$, transcaratteristica.

Prerequisiti: [[JFET]], [[Impedenza dei bipoli R, L, C]], [[MOSFET]] (per confronto delle equazioni).

> [!warning] Convenzione di lavoro
> Ricorda sempre: nel JFET n-channel, $V_P < 0$. Se le grandezze sembrano "sbagliate", verifica il segno di $V_P$.

---

# 📚 PARTE I — Esercizi classici (polarizzazione)

## Esercizio 1 — Autopolarizzazione classica

**Testo.** Un JFET n-channel con $I_{DSS}=8\text{ mA}$, $V_P=-4\text{ V}$ è autopolarizzato con $V_{DD}=15\text{ V}$, $R_D=2{,}2\text{ k}\Omega$, $R_S=220\text{ }\Omega$. Calcola il punto di lavoro $I_D$ e $V_{DS}$.

**Svolgimento.**

1. **Gate:** la corrente di gate è ≈ 0, e si usa $R_G$ verso massa (anche se non disegnata, $V_G=0$).

2. **Source:** $V_{GS} = V_G - V_S = 0 - I_D R_S = -I_D R_S = -0{,}22 \cdot I_D$ (V, con $I_D$ in mA).

3. **Equazione parabolica** del JFET:
   $$I_D = I_{DSS} \left(1 - \frac{V_{GS}}{V_P}\right)^2$$
   
   Con $V_{GS}<0$ e $V_P<0$: il rapporto $V_{GS}/V_P$ è positivo:
   $$I_D = 8 \left(1 - \frac{-0{,}22 I_D}{-4}\right)^2 = 8 \left(1 - 0{,}055 I_D\right)^2$$

4. **Espansione:**
   $$I_D = 8 (1 - 0{,}11 I_D + 0{,}003025 I_D^2) = 8 - 0{,}88 I_D + 0{,}0242 I_D^2$$

5. **Equazione di 2° grado:**
   $$0{,}0242 I_D^2 - 1{,}88 I_D + 8 = 0$$

6. **Radici:**
   $$\Delta = 1{,}88^2 - 4 \cdot 0{,}0242 \cdot 8 = 3{,}534 - 0{,}774 = 2{,}76$$
   $$I_D = \frac{1{,}88 \pm \sqrt{2{,}76}}{0{,}0484} = \frac{1{,}88 \pm 1{,}66}{0{,}0484}$$
   
   - $I_{D1} = 3{,}54/0{,}0484 ≈ 73\text{ mA}$ (sopra $I_{DSS}=8\text{ mA}$; fisicamente impossibile) **SCARTATA**.
   - $I_{D2} = 0{,}22/0{,}0484 ≈ 4{,}55\text{ mA}$ → $V_{GS} = -1{,}0\text{ V}$, sopra $V_P=-4\text{ V}$: ✅ **ACCETTATA**.

7. **Tensione $V_{DS}$:**
   $$V_{DS} = V_{DD} - I_D (R_D + R_S) = 15 - 4{,}55 \cdot 2{,}42 ≈ 4{,}0\text{ V}$$

8. **Verifica pinch-off** (saturazione): serve $V_{DS} > V_{GS} - V_P$.
   $V_{GS} - V_P = -1{,}0 + 4 = 3{,}0\text{ V}$. $V_{DS} = 4{,}0 > 3{,}0$ → ✅ **in saturazione**.

> [!check] Risposta
> $I_D \approx 4{,}55\text{ mA}$, $V_{DS} \approx 4{,}0\text{ V}$, $V_{GS} \approx -1{,}0\text{ V}$, **in saturazione**.

---

## Esercizio 2 — $R_S$ troppo grande: discriminante e stabilità

**Testo.** Stesso JFET, ma con $R_S = 1\text{ k}\Omega$. Verifica se esiste un punto di lavoro in saturazione.

**Svolgimento.**

1. $V_{GS} = -I_D \cdot 1\text{ k}\Omega = -I_D$ (mA).

2. $I_D = 8 (1 - I_D/-4)^2 = 8 (1 - I_D/4)^2 = 8(1 - I_D/2 + I_D^2/16)$
   $$I_D = 8 - 4 I_D + 0{,}5 I_D^2$$

3. Equazione di 2° grado: $0{,}5 I_D^2 - 5 I_D + 8 = 0$.

4. $\Delta = 25 - 16 = 9$. $I_D = (5 \pm 3)/1 = 8$ o $2$ mA.

5. Per $I_D = 8\text{ mA}$: $V_{GS} = -8\text{ V}$ (sotto $V_P=-4$, **sotto pinch-off**) → la formula di saturazione **non è valida** qui. **SCARTATA**.

6. Per $I_D = 2\text{ mA}$: $V_{GS} = -2\text{ V}$, $V_{DS} = 15 - 2 \cdot 3{,}2 = 8{,}6\text{ V}$. Verifica pinch-off: $V_{GS} - V_P = -2 + 4 = 2$, $V_{DS} = 8{,}6 > 2$ → ✅ in saturazione.

> [!tip] "Discriminante = 0" come indicatore didattico
> $\Delta$ vicino a 0 significa che il JFET è **al limite** tra due regioni operative. Piccole variazioni di $R_S$ o di $V_{DD}$ producono grandi cambiamenti di $I_D$: la polarizzazione è poco stabile.

> [!warning] Criterio di stabilità per autopolarizzazione JFET
> Affinché esista un punto di lavoro in saturazione, deve valere $R_S \le |V_P| / (2 I_{DSS}) = 4 / 16 = 0{,}25\text{ k}\Omega = 250\text{ }\Omega$. Nel nostro caso $R_S = 220\text{ }\Omega$: ✅ appena sotto la soglia.

---

## Esercizio 3 — Calcolo veloce (solo parabolica)

**Testo.** Un JFET ha $I_{DSS}=10\text{ mA}$, $V_P=-3\text{ V}$. Con $V_{GS}=-1\text{ V}$ in saturazione, calcola $I_D$.

**Svolgimento.**

$$I_D = 10 \cdot \left(1 - \frac{-1}{-3}\right)^2 = 10 \cdot \left(1 - \frac{1}{3}\right)^2 = 10 \cdot \left(\frac{2}{3}\right)^2 = 10 \cdot \frac{4}{9} \approx 4{,}44\text{ mA}$$

> [!tip] Esercizio "veloce" per l'orale Carli
> All'orale Carli può chiedere: "Date $I_{DSS}$ e $V_P$, calcola $I_D$ per $V_{GS}=-2\text{ V}$". È la stessa formula, sempre. Impara a farla in 10 secondi.

---

## Esercizio 4 — Identificare $I_{DSS}$ e $V_P$ da misure

**Testo.** Misuri $I_D = 4\text{ mA}$ con $V_{GS} = -1\text{ V}$ e $I_D = 9\text{ mA}$ con $V_{GS} = 0$. Trova $I_{DSS}$ e $V_P$.

**Svolgimento.**

A $V_{GS}=0$, la formula restituisce $I_{DSS} \cdot 1 = I_{DSS}$. Quindi direttamente $I_{DSS} = 9\text{ mA}$.

Poi con $V_{GS}=-1\text{ V}$: $4 = 9 \cdot (1 - (-1)/V_P)^2 \Rightarrow (1 + 1/V_P)^2 = 4/9 = 0{,}444$.
Quindi $1 + 1/V_P = ±0{,}667$.
- $1 + 1/V_P = -0{,}667 \Rightarrow 1/V_P = -1{,}667 \Rightarrow V_P = -0{,}6\text{ V}$ (V_P "piccolo" → solo a $V_{GS}=0$ conduce, JFET molto "debole").
- $1 + 1/V_P = +0{,}667 \Rightarrow 1/V_P = -0{,}333 \Rightarrow V_P = -3\text{ V}$ ✅ valore plausibile per un JFET tipico.

> Risposta: $I_{DSS} = 9\text{ mA}$, $V_P = -3\text{ V}$.

---

# 📈 PARTE II — Amplificatori Source Comune (CS) e Source Follower (CD)

## Esercizio 5 — Source Comune (edutecnica ajfetx/1) — guadagno con $g_m$ data

**Testo.** Un amplificatore CS a JFET ha i seguenti parametri di polarizzazione:
- $I_{DSS} = 4\text{ mA}$, $V_P = -2\text{ V}$, punto di lavoro $I_D = 1\text{ mA}$
- $R_D = 4{,}7\text{ k}\Omega$
- $R_G = 1\text{ M}\Omega$
- $R_S$ bypassato da $C_S$ (quindi AC source a massa)

Calcolare:
- $V_{GS}$ nel punto di lavoro
- La transconduttanza $g_m$ in quel punto
- Il guadagno di tensione $A_v$ a centro banda
- La resistenza di ingresso $R_{in}$ vista dal generatore di segnale

**Svolgimento passo-passo.**

1. **Calcolo di $V_{GS}$:**
   Dalla parabolica: $V_{GS} = V_P \cdot \left(1 - \sqrt{I_D / I_{DSS}}\right)$.
   $$V_{GS} = -2 \cdot \left(1 - \sqrt{1/4}\right) = -2 \cdot (1 - 0{,}5) = -2 \cdot 0{,}5 = -1{,}0\text{ V}$$

2. **Calcolo di $g_{m0}$ (a $V_{GS}=0$):**
   $$g_{m0} = \frac{2 I_{DSS}}{|V_P|} = \frac{2 \cdot 4}{2} = 4\text{ mS}$$

3. **Calcolo di $g_m$ nel punto di lavoro:**
   $$g_m = g_{m0} \cdot \left(1 - \frac{V_{GS}}{V_P}\right) = 4 \cdot \left(1 - \frac{-1}{-2}\right) = 4 \cdot (1 - 0{,}5) = 2\text{ mS}$$

4. **Guadagno $A_v$** (con $R_S$ bypassato):
   $$A_v = -g_m \cdot R_D = -2\text{ mS} \cdot 4{,}7\text{ k}\Omega = -9{,}4$$
   In dB: $|A_v|_{dB} = 20 \log_{10}(9{,}4) \approx 19{,}5\text{ dB}$.
   Segno negativo → inversione di fase 180°.

5. **Resistenza di ingresso $R_{in}$:**
   Il gate del JFET è resistenza quasi-infinita ($Z_{in,\text{JFET}} \approx 10^{10}\text{ }\Omega$). In parallelo c'è solo $R_G$.
   $$R_{in} = R_G = 1\text{ M}\Omega$$
   (ALTISSIMA rispetto a BJT CE: $\sim$k$\Omega$!)

> [!check] Risposta
> $V_{GS} = -1\text{ V}$, $g_m = 2\text{ mS}$, $A_v = -9{,}4$ ($19{,}5$ dB), $R_{in} = 1\text{ M}\Omega$.

---

## Esercizio 6 — Calcolo completo: polarizzazione + amplificazione (edutecnica ajfetx/2)

**Testo.** Schema con i seguenti dati:
- JFET con $I_{DSS} = 9\text{ mA}$, $V_P = -3{,}5\text{ V}$
- $V_{DD} = 18\text{ V}$
- Partitore di gate: $R_1 = 1\text{ M}\Omega$, $R_2 = 220\text{ k}\Omega$ (collegato a massa, NON al source)
- $R_S = 820\text{ }\Omega$
- $R_D = 2{,}2\text{ k}\Omega$
- Carico $R_L = 4{,}7\text{ k}\Omega$ (accoppiato in AC tramite $C_{out}$)

Calcolare: $V_G$, $V_S$, $I_D$, $V_{DS}$, $g_m$, $A_v$ a centro banda con $R_L$.

**Svolgimento passo-passo.**

1. **Tensione di gate** (dal partitore):
   $$V_G = V_{DD} \cdot \frac{R_2}{R_1 + R_2} = 18 \cdot \frac{220}{1000 + 220} = 18 \cdot 0{,}180 = 3{,}25\text{ V}$$

2. **Punto di lavoro $I_D$**: serve un'equazione con $V_G$ nota.
   $$V_{GS} = V_G - I_D \cdot R_S = 3{,}25 - 0{,}82 \cdot I_D \text{ (V, con } I_D \text{ in mA)}$$

   Parabolica:
   $$I_D = 9 \cdot \left(1 - \frac{V_{GS}}{V_P}\right)^2 = 9 \cdot \left(1 - \frac{3{,}25 - 0{,}82 I_D}{-3{,}5}\right)^2 = 9 \cdot \left(1 + \frac{3{,}25 - 0{,}82 I_D}{3{,}5}\right)^2$$
   $$= 9 \cdot \left(1 + 0{,}929 - 0{,}234 I_D\right)^2 = 9 \cdot (1{,}929 - 0{,}234 I_D)^2$$
   $$= 9 \cdot (3{,}72 - 0{,}904 I_D + 0{,}0549 I_D^2) = 33{,}5 - 8{,}13 I_D + 0{,}494 I_D^2$$

   Equazione di 2° grado: $0{,}494 I_D^2 - 9{,}13 I_D + 33{,}5 = 0$.
   $$\Delta = 83{,}4 - 66{,}2 = 17{,}2 \Rightarrow \sqrt\Delta = 4{,}15$$
   $$I_D = \frac{9{,}13 \pm 4{,}15}{0{,}988}$$

   - $I_{D1} = 13{,}28/0{,}988 ≈ 13{,}4\text{ mA}$ → sopra $I_{DSS}=9\text{ mA}$: SCARTATA.
   - $I_{D2} = 4{,}98/0{,}988 ≈ 5{,}04\text{ mA}$ → ✅.

3. **Verifica**: $V_{GS} = 3{,}25 - 0{,}82 \cdot 5{,}04 = 3{,}25 - 4{,}13 = -0{,}88\text{ V}$. Dalla parabolica: $V_{GS}(5\text{ mA}) = -3{,}5 \cdot (1 - \sqrt{5/9}) = -3{,}5 \cdot (1 - 0{,}745) = -0{,}89\text{ V}$ ✅ coerente.

4. **Tensione $V_{DS}$:**
   $$V_{DS} = V_{DD} - I_D (R_D + R_S) = 18 - 5{,}04 \cdot (2{,}2 + 0{,}82) = 18 - 15{,}22 = 2{,}78\text{ V}$$
   Verifica pinch-off: $V_{GS} - V_P = -0{,}88 + 3{,}5 = 2{,}62\text{ V}$. $V_{DS} = 2{,}78 > 2{,}62$ ✅ in saturazione (di poco).

5. **Transconduttanza:**
   $$g_{m0} = 2 \cdot 9 / 3{,}5 = 5{,}14\text{ mS}$$
   $$g_m = 5{,}14 \cdot (1 - (-0{,}88)/(-3{,}5)) = 5{,}14 \cdot (1 - 0{,}252) = 5{,}14 \cdot 0{,}748 = 3{,}85\text{ mS}$$

6. **Guadagno $A_v$** (con $R_S$ bypassato, $R_L$ accoppiato):
   $$R_D \parallel R_L = \frac{2{,}2 \cdot 4{,}7}{2{,}2 + 4{,}7} = \frac{10{,}34}{6{,}9} = 1{,}50\text{ k}\Omega$$
   $$A_v = -g_m \cdot (R_D \parallel R_L) = -3{,}85\text{ mS} \cdot 1{,}50\text{ k}\Omega = -5{,}77$$

> [!check] Risposta
> $I_D \approx 5{,}04\text{ mA}$, $V_{DS} \approx 2{,}78\text{ V}$, $V_{GS} \approx -0{,}88\text{ V}$, $g_m \approx 3{,}85\text{ mS}$, $A_v \approx -5{,}8$ (15,2 dB).

---

## Esercizio 7 — Source Follower / Drain Comune (edutecnica ajfetx/3)

**Testo.** Un JFET n in configurazione source-follower ha:
- $I_{DSS} = 5\text{ mA}$, $V_P = -2\text{ V}$
- $V_{DD} = 12\text{ V}$
- $R_S = 1{,}5\text{ k}\Omega$ (carico di source)
- drain direttamente a $V_{DD}$ (no $R_D$)

Calcolare: $I_D$, $V_{GS}$, $g_m$, $A_v$ (guadagno), $R_{in}$, $R_{out}$.

**Svolgimento passo-passo.**

1. **Polarizzazione** (drain a $V_{DD}$, $V_G = 0$ dal $R_G$ verso massa):
   $$V_{GS} = -I_D \cdot R_S = -1{,}5 \cdot I_D \text{ (V, con } I_D \text{ in mA)}$$
   
   Parabolica: $I_D = 5 \cdot (1 - V_{GS}/(-2))^2 = 5 \cdot (1 + I_D \cdot 1{,}5 / 2)^2 = 5 \cdot (1 + 0{,}75 I_D)^2$
   $$= 5 \cdot (1 + 1{,}5 I_D + 0{,}5625 I_D^2) = 5 + 7{,}5 I_D + 2{,}8125 I_D^2$$
   
   Equazione di 2° grado: $2{,}8125 I_D^2 + 6{,}5 I_D + 5 = 0$.
   $$\Delta = 42{,}25 - 56{,}25 = -14 < 0$$ ❌
   
   **Problema:** con $R_S = 1{,}5\text{ k}\Omega$ non esiste soluzione. La polarizzazione è **instabile** (criterio $R_S \le |V_P|/(2 I_{DSS}) = 2/10 = 200\text{ }\Omega$).

2. **Cambio $R_S$** a $200\text{ }\Omega$ (per rientrare nel criterio di stabilità):
   $$V_{GS} = -0{,}2 \cdot I_D \text{ (V)}$$
   $$I_D = 5 \cdot (1 + 0{,}2 I_D / 2)^2 = 5 \cdot (1 + 0{,}1 I_D)^2 = 5 \cdot (1 + 0{,}2 I_D + 0{,}01 I_D^2)$$
   $$= 5 + I_D + 0{,}05 I_D^2$$
   
   Equazione: $0{,}05 I_D^2 + 0 I_D - 0 = 0$ → $\Delta = 0$, $I_D = 0$ ✅ (degenerato).

3. **Cambio $R_S$** a $180\text{ }\Omega$ (per avere una soluzione non degenere):
   Le formule danno $I_D \approx 3{,}14\text{ mA}$, $V_{GS} \approx -0{,}57\text{ V}$.

> [!tip] Verifica didattica
> Per il source follower è più difficile trovare polarizzazioni "comode" perché il source è il terminale dove si misura l'uscita, e la $R_S$ deve essere "ragionevole" sia in DC (per la polarizzazione) sia in AC (per l'amplificazione).

4. **Risultato finale** (usando il punto di lavoro stabilito $I_D \approx 3\text{ mA}$, $V_{GS} \approx -0{,}6\text{ V}$):
   $$g_m = (2 \cdot 5 / 2) \cdot (1 - (-0{,}6)/(-2)) = 5 \cdot (1 - 0{,}3) = 3{,}5\text{ mS}$$
   
   **Guadagno** (formula del source follower):
   $$A_v = \frac{g_m R_S}{1 + g_m R_S} = \frac{3{,}5 \cdot 0{,}18}{1 + 3{,}5 \cdot 0{,}18} = \frac{0{,}63}{1{,}63} \approx 0{,}39$$ 
   
   > [!warning] Nota di contesto
   > Nel caso specifico del testo edutecnica, i valori numerici sono un po' "borderline" rispetto a $R_S$ di 1,5 kΩ. Con $R_S$ ridotti a 180 Ω, $A_v$ è ancora sotto 0.5 (perché $g_m R_S$ non è >>1). Con $R_S$ da 1 kΩ, è ben oltre 0.9.

5. **Resistenze**:
   $$R_{in} \approx R_G \text{ (scelta standard)} = 1\text{ M}\Omega \text{ (alta!)}$$
   $$R_{out} = R_S \parallel (1/g_m) = R_S \parallel r_d/\mu \approx 1/g_m \approx 286\text{ }\Omega \text{ (bassa!)}$$

> [!check] Risposta
> Source follower: $A_v < 1$, $R_{in}$ altissima, $R_{out}$ bassa → è un **adattatore di impedenza**.

---

## Esercizio 8 — Calcolo di $g_m$ in un generico punto di lavoro

**Testo.** JFET con $I_{DSS}=10\text{ mA}$, $V_P=-4\text{ V}$, polarizzato in modo che $I_D = 4\text{ mA}$. Calcolare $V_{GS}$ e $g_m$ in quel punto.

**Svolgimento.**

1. **Dalla parabolica inversa**:
   $$V_{GS} = V_P \cdot \left(1 - \sqrt{I_D/I_{DSS}}\right) = -4 \cdot \left(1 - \sqrt{4/10}\right) = -4 \cdot (1 - 0{,}632) = -4 \cdot 0{,}368 = -1{,}47\text{ V}$$

2. **$g_{m0}$**:
   $$g_{m0} = \frac{2 I_{DSS}}{|V_P|} = \frac{20}{4} = 5\text{ mS}$$

3. **$g_m$** nel punto di lavoro:
   $$g_m = g_{m0} \cdot \left(1 - \frac{V_{GS}}{V_P}\right) = 5 \cdot \left(1 - \frac{-1{,}47}{-4}\right) = 5 \cdot (1 - 0{,}368) = 5 \cdot 0{,}632 = 3{,}16\text{ mS}$$

> [!check] Risposta
> $V_{GS} = -1{,}47\text{ V}$, $g_m = 3{,}16\text{ mS}$.

> [!tip] Regola del quarto di corrente
> $I_D = 4\text{ mA}$ è proprio $I_{DSS}/2{,}5$ (non un multiplo semplice). Però se fosse stato $I_D = I_{DSS}/4 = 2{,}5\text{ mA}$, allora $V_{GS} = V_P/2 = -2\text{ V}$ e $g_m = g_{m0}/2 = 2{,}5\text{ mS}$. È un utile mnemonico.

---

## Esercizio 9 — JFET P-channel (stesse formule, segni invertiti)

> [!tip] Principio didattico
> Il P-channel **non è un argomento nuovo**: è un N-channel con tutti i segni "rovesciati". Si usano le **stesse formule** dell'Es.1, applicate con $V_P > 0$ e alimentazione negativa. Nessuna nuova notazione, nessun formalismo inventato.

> [!info] Convenzione usata in questo esercizio
> Useremo la convenzione "P-channel con $I_{DSS}$ **negativo**" (come in alcuni testi: Millman, Sedra/Smith). In altre fonti (es. alcuni datasheet) $I_{DSS}$ è dato come **positivo** e il segno va gestito a parte nell'equazione. Stai attento: usa la convenzione che il tuo professore adotta, ma i **risultati numerici coincidono** (con segni applicati coerentemente).

**Testo (analogo all'Es.1, ma P-channel).** Un JFET **P-channel** con:
- $V_P = +4\text{ V}$ (parametro positivo! opposto al canale n)
- $I_{DSS} = -6\text{ mA}$ (convenzione "segno-negativo"; la corrente massima è $|I_{DSS}|=6\text{ mA}$ ma nel P-channel scorre da S a D)
- $V_{SS} = -12\text{ V}$ (alimentazione negativa)
- $R_S = 220\text{ }\Omega$ (tra source e massa; massa è il potenziale alto per P-channel)
- $R_D = 2{,}2\text{ k}\Omega$ (tra drain e $V_{SS}$)
- $R_G$ da gate verso massa

Calcolare $I_D$, $V_S$, $V_{GS}$, $V_D$, $V_{SD}$ (per P-channel si misura $V_{SD}$ invece di $V_{DS}$, ma il valore assoluto è lo stesso).

**Svolgimento passo-passo (stesse formule dell'Es.1, segni "rovesciati").**

1. **Polarità**: nel P-channel, il source è verso massa (potenziale alto) e il drain verso $V_{SS}$ (potenziale basso). La corrente convenzionale scorre da S a D, quindi $I_D$ ha segno **negativo** rispetto al verso "standard del libro" (che è da D a S). Useremo $I_D$ con segno.

2. **Source**:
   $$V_S = 0 - (-I_D) R_S = I_D R_S$$
   (Attenzione: la corrente $I_D$ scorre dal source verso massa attraverso $R_S$, quindi $V_S$ è positivo se $I_D$ è negativo.)

3. **Gate** (con $R_G$ a massa):
   $$V_G = 0$$

4. **$V_{GS}$**:
   $$V_{GS} = V_G - V_S = 0 - I_D R_S = -I_D R_S = -0{,}220 \cdot I_D$$
   
   Stessa formula dell'Es.1, ma ora $I_D < 0$ → $V_{GS} > 0$ (richiesto dal P-channel).

5. **Parabolica** del JFET (stessa formula!):
   $$I_D = I_{DSS}\left(1 - \dfrac{V_{GS}}{V_P}\right)^2$$
   
   MA qui prendiamo $I_{DSS}$ come **negativo** (convenzione P-channel: la corrente massima scorre in verso opposto). Useremo il valore con segno $I_{DSS} = -6$ mA.
   
   Con $V_{GS} > 0$ e $V_P > 0$: il rapporto $V_{GS}/V_P$ è positivo.
   $$I_D = -6 \cdot \left(1 - \dfrac{-0{,}220 I_D}{+4}\right)^2 = -6 \cdot \left(1 + 0{,}055 I_D\right)^2$$

6. **Espansione**:
   $$I_D = -6 \cdot (1 + 0{,}110 I_D + 0{,}003025 I_D^2)$$
   $$= -6 - 0{,}660 I_D - 0{,}0182 I_D^2$$

7. **Equazione di 2° grado** (riarrangiata per $I_D$):
   $$0{,}0182 I_D^2 + 1{,}660 I_D + 6 = 0$$

8. **Risoluzione**:
   $$\Delta = 1{,}660^2 - 4 \cdot 0{,}0182 \cdot 6 = 2{,}756 - 0{,}437 = 2{,}319$$
   $$\sqrt{\Delta} = 1{,}523 \qquad I_D = \dfrac{-1{,}660 \pm 1{,}523}{2 \cdot 0{,}0182}$$

   - $I_{D1} = \dfrac{-1{,}660 + 1{,}523}{0{,}0364} = \dfrac{-0{,}137}{0{,}0364} \approx -3{,}76\text{ mA}$ ✅ ($\le |I_{DSS}|=6$)
   - $I_{D2} = \dfrac{-1{,}660 - 1{,}523}{0{,}0364} = \dfrac{-3{,}183}{0{,}0364} \approx -87{,}4\text{ mA}$ ❌ SCARTATA (sopra $|I_{DSS}|$).

   Risultato: $I_D \approx -3{,}76\text{ mA}$ (segno negativo = corrente da S a D, come per P-channel).

9. **Verifica $V_{GS}$**:
   $$V_{GS} = -0{,}220 \cdot (-3{,}76) = +0{,}827\text{ V} \quad (\text{tra } 0\text{ e } V_P=+4, ✅) $$

10. **Tensione drain**:
   $$V_D = V_{SS} + I_D R_D = -12 + (-3{,}76) \cdot 2{,}2 = -12 - 8{,}27 = -20{,}3\text{ V}$$
    
    (Significato: il drain è ancora più negativo di $V_{SS}$ perché la corrente crea una caduta ulteriore su $R_D$.)

11. **$V_{SD}$** (tensione source-drain, direzione "positiva" del P-channel):
   $$V_{SD} = V_S - V_D = (-I_D R_S) - V_D = 0{,}827 - (-20{,}3) = 21{,}1\text{ V}$$
    
    (Il source è a potenziale più alto del drain, come deve essere per il verso della corrente.)

12. **Verifica pinch-off** (nel P-channel il pinch-off è $V_{SD} \ge V_{GS} - V_P$):
   $$V_{GS} - V_P = 0{,}827 - 4 = -3{,}17\text{ V}$$
   $$V_{SD} = 21{,}1\text{ V} \ge -3{,}17\text{ V}$$ ✅ **in saturazione**.

> [!check] Risultato
> $I_D \approx -3{,}76\text{ mA}$ (verso S→D), $V_{GS} \approx +0{,}83\text{ V}$, $V_{SD} \approx 21\text{ V}$, **in saturazione**.

> [!tip] Confronto diretto con l'Es.1 (N-channel)
> Stessi numeri di componenti, stessi passi del 2° grado → ottieni $|I_D|$ e $|V_{GS}|$ confrontabili ma con **segni opposti**. Il P-channel è il "fotocopia invertito" del N-channel.

> [!danger] Trappola classica
> Se applichi le formule del N-channel al P-channel **senza riflettere i segni di $V_P$, $V_{SS}$, $I_{DSS}$**, ottieni numeri sbagliati di segno. La Carli scritta potrebbe darti un P-channel come trabocchetto: **verifica sempre i segni prima di mettere numeri**.

---

# 🔌 PARTE III — Applicazioni: VCR, Switch, Interruttore analogico

## Esercizio 10 — JFET come VCR (Voltage Controlled Resistor)

**Testo.** Un JFET è usato come resistenza variabile in un partitore di tensione, per un controllo automatico di guadagno (AGC).

Schema:
- Partitore: $R_{DS}$ del JFET (resistenza) in serie a $R_L = 10\text{ k}\Omega$ fisso
- $V_{GS}$ controllato da un circuito esterno (es. rivelatore di livello)
- $V_{DD} = 5\text{ V}$ (piccolo, per stare in zona triodo)
- JFET con $r_{DS(on)} = 50\text{ }\Omega$ (a $V_{GS}=0$), $I_{DSS} = 20\text{ mA}$, $V_P = -4\text{ V}$

Determinare la $V_{out}$ al partitore per:
- (a) $V_{GS} = 0$ (JFET in piena conduzione)
- (b) $V_{GS} = -2\text{ V}$ ($V_{GS} = V_P/2$, $I_D \approx I_{DSS}/4 = 5\text{ mA}$)
- (c) $V_{GS} = -4\text{ V} = V_P$ (JFET spento)

**Svolgimento.**

In zona triodo (vicino all'origine, $V_{DS}$ piccolo), il JFET è una resistenza:

$$R_{DS}(V_{GS}) \approx \frac{r_{DS(on)}}{1 - V_{GS}/V_P}$$

(approssimazione lineare nella zona triodo.)

1. **Caso (a): $V_{GS}=0$**: $R_{DS} \approx r_{DS(on)} = 50\text{ }\Omega$.
   $$V_{out} = 5 \cdot \frac{R_L}{R_{DS} + R_L} = 5 \cdot \frac{10000}{50 + 10000} = 5 \cdot 0{,}995 = 4{,}98\text{ V}$$
   Quasi tutta la tensione cade su $R_L$ → JFET è un filo.

2. **Caso (b): $V_{GS} = -2\text{ V}$**:
   $$R_{DS} \approx 50 / (1 - (-2)/(-4)) = 50 / (1 - 0{,}5) = 50 / 0{,}5 = 100\text{ }\Omega$$
   $$V_{out} = 5 \cdot 10000/(100+10000) = 5 \cdot 0{,}99 = 4{,}95\text{ V}$$
   Ancora $R_L$ domina.

3. **Caso (c): $V_{GS} = -4\text{ V}$**: $R_{DS} \to \infty$ (JFET spento).
   $$V_{out} = 5 \cdot 10000/(\infty + 10000) = 0\text{ V}$$

> [!warning] Limiti della formula $R_{DS}(V_{GS})$ usata sopra
> La formula $R_{DS}(V_{GS}) \approx r_{DS(on)} / (1 - V_{GS}/V_P)$ è un'**approssimazione didattica** valida SOLO per **$V_{DS}$ molto piccolo** (vicino all'origine delle curve). In zona triodo, la resistenza vera è:
>
> $$R_{DS}(V_{GS}, V_{DS}) = \dfrac{V_{DS}}{I_D} = \dfrac{V_{DS}}{K \left[2(V_{GS}-V_P)V_{DS} - V_{DS}^2\right]}$$
>
> Per $V_{DS}$ 'apprezzabile, $R_{DS}$ dipende anche da $V_{DS}$ — non è una pura resistenza. Per applicazioni VCR serie, tenere $V_{DS} < 100$ mV per restare nel regime lineare. Per applicazioni VCR in retroazione di op-amp (AGC audio), la linearizzazione 'e implicita nel loop di retroazione.

> [!tip] Per usare il JFET come VCR in modo più efficace
> Conviene lavorare con $V_{DS}$ molto piccolo e $R_L$ piccola (es. $R_L = 100\text{ }\Omega$ e $R_{DS}$ controlla davvero il partitore). Per AGC audio, il JFET è in genere tra l'uscita di un amplificatore operazionale e massa, modulando la retroazione.

> [!check] Risposta
> Variazione di $V_{GS}$ da 0 a $V_P$ fa variare $R_{DS}$ da $\sim 50\text{ }\Omega$ a $\infty$: un range di $\sim 200{:}1$ in resistenza. Questo è il cuore del VCR.

---

## Esercizio 11 — JFET come interruttore analogico (analog switch)

**Testo.** JFET 2N3819 con $r_{DS(on)} = 50\text{ }\Omega$, $V_P = -3\text{ V}$. Usato come switch ON/OFF su un segnale analogico.

Determinare lo stato del JFET e la tensione di uscita per:
- (a) $V_{GS,ctrl} = 0\text{ V}$ → segnale analogico di ampiezza ±5 V passa?
- (b) $V_{GS,ctrl} = -5\text{ V}$ → segnale analogico passa?

Circuito:
```
   v_in --[2N3819]-- v_out
            │
           (gate pilotato da V_GS,ctrl)
   v_out collegato a un carico R_L = 10 kΩ verso massa
```

**Svolgimento.**

1. **Stato (a) $V_{GS,ctrl} = 0$**: il JFET n con $V_{GS} = 0$ è in piena conduzione (verso $I_{DSS}$). In zona triodo con piccolo $V_{DS}$, $R_{DS} \approx 50\text{ }\Omega$.
   $$V_{out} \approx v_{in} \cdot \frac{R_L}{R_{DS} + R_L} \approx v_{in} \cdot 0{,}995 \approx 0{,}995 \cdot v_{in}$$
   ✅ Il segnale passa, attenuato di meno dell'1%.

2. **Stato (b) $V_{GS,ctrl} = -5\text{ V}$**: $V_{GS} \ll V_P=-3\text{ V}$ → il JFET è SPENTO, $R_{DS} \to \infty$.
   $$V_{out} = 0 \text{ V (nessun segnale passa)}$$
   ✅ Il segnale è bloccato.

> [!check] Risposta
> Pilotando il gate tra 0 V e $-5\text{ V}$, il JFET funziona da interruttore analogico con:
> - ON: $r_{DS(on)} = 50\text{ }\Omega$ (piccolo).
> - OFF: $R_{DS} > 10\text{ M}\Omega$ (praticamente aperto).
> - Velocità di commutazione: ~10–100 ns (molto veloce).
> - Limite di tensione: $V_{(BR)DSS} \approx 25\text{ V}$ per 2N3819.

> [!tip] Applicazione: sample-and-hold
> Il JFET switch è usato per "catturare" un valore analogico in un condensatore: quando ON, il condensatore si carica al valore del segnale; quando OFF, il condensatore "tiene" il valore.

---

# 🧪 PARTE IV — Quesiti orali tipici (esteso)

## Quesito orale 1 — Quando preferiresti un JFET a un BJT all'ingresso di un pre-amplificatore?

> **Risposta tipo**:
> - Se serve **alta impedenza di ingresso** ($Z_{in} \sim$M$\Omega$–G$\Omega$) → **JFET**.
> - Se serve **basso rumore** in applicazioni audio/RF → **JFET** (il BJT ha shot noise nella giunzione B-E, il JFET ha solo rumore termico nel canale).
> - Se serve **guadagno di tensione elevato** in pochi stadi → **BJT** (più alto $g_m$, $\beta$ alto).

## Quesito orale 2 — Spiega la curva parabolica del JFET e perché $V_{GS}=0$ dà $I_D = I_{DSS}$.

> La corrente $I_D$ è controllata dalla "strangolazione" del canale da parte della giunzione gate-canale inversa. A $V_{GS}=0$, la strangolazione è minima → il canale è "aperto" → $I_D$ è massima ($=I_{DSS}$). A $V_{GS} = V_P$ (negativo), la strangolazione è totale → canale "chiuso" → $I_D = 0$. Tra i due estremi, la sezione utile del canale cala con legge parabolica → $I_D$ cala con $(1 - V_{GS}/V_P)^2$.

## Quesito orale 3 — Perché il JFET non può avere $V_{GS} > 0$?

> Perché la giunzione p-n tra gate e canale andrebbe in diretta. La corrente di gate salirebbe (non più ≈ 0), la "strangolazione" del canale non sarebbe più controllabile, e in casi estremi il gate brucerebbe per eccesso di corrente.

## Quesito orale 4 — Che differenza c'è tra Source Comune JFET e Source Comune BJT?

> Sono topologicamente simili (segnale al gate/base, uscita dal drain/collettore, source/emitter a massa).
> Differenze:
> - Pilotaggio: JFET in tensione ($V_{GS}$), BJT in corrente ($I_B$).
> - $Z_{in}$: JFET altissima (≈ M$\Omega$), BJT media (≈ k$\Omega$).
> - Rumore: JFET più basso (no shot noise nella giunzione).
> - $A_v$: BJT CE ha generalmente $A_v$ più alti ($\beta$ più alto di $g_m R$).
> - Offset DC: JFET ha $V_{GS}$ piccolo, BJT ha $V_{BE} \approx 0{,}7\text{ V}$ da gestire.

## Quesito orale 5 — Cos'è la transconduttanza $g_m$ e come si calcola?

> È la pendenza della transcaratteristica: $g_m = \Delta I_D / \Delta V_{GS}$ (a $V_{DS}$ costante). Si misura in siemens (S).
> Per JFET in saturazione: $g_m = g_{m0} (1 - V_{GS}/V_P)$ dove $g_{m0} = 2 I_{DSS} / |V_P|$.
> **È il parametro principale del JFET in amplificazione**: $A_v \approx -g_m R_D$ (in source comune).

## Quesito orale 6 — Cosa sono i punti di pinch-off sulla famiglia di curve?

> Sono i punti dove la curva $I_D(V_{DS})$ "si stacca" dalla zona triodo (resistiva) ed entra in saturazione (corrente quasi costante). Su una famiglia di curve a diversi $V_{GS}$, **tutti i punti di pinch-off** formano una parabola — la **locus parabolica** che è la "frontiera" tra zona triodo e saturazione. Questa curva è proprio $V_{DS} = V_{GS} - V_P$.

## Quesito orale 7 — JFET vs BJT nella commutazione digitale: chi è più veloce?

> **Risposta tipo**:
> - **BJT** è più veloce in commutazione grazie alla struttura a giunzione "stretta" e all'assenza di ossido di gate (che nel MOSFET aggiunge capacità parassita). Tempi di commutazione: ns (BJT) vs decine di ns (JFET) vs centinaia di ns (MOSFET di potenza).
> - **MOSFET (CMOS)** è dominante nella logica digitale **proprio per lo scaling** (alto fan-out del gate, consumo statico zero). Velocità comparabile al BJT in tecnologia moderna.
> - **JFET** non si usa in logica digitale: la dipendenza dalla $I_{DSS}/V_P$ (con tolleranze ampie!) rende il design complicato, e il pilotaggio in tensione (è $\le 0$ V per il N) è poco compatibile con logica single-supply.
> - **Regola pratica ITI**: logica digitale = **MOSFET CMOS** (per scalare); pilotaggio analogico ad alta impedenza = **JFET**; amplificazione di piccoli segnali = **BJT CE** (a meno di non richiedere alta $Z_{in}$, dove serve JFET); pilotaggio di potenza = **MOSFET di potenza** o **BJT Darlington**.

## Quesito orale 8 — Perché il source follower JFET è utile come adattatore di impedenza?

> Perché ha $Z_{in}$ alta (≈ $R_G$, M$\Omega$) e $Z_{out}$ bassa (≈ $1/g_m$, centinaia di $\Omega$). Permette di prendere un segnale da una sorgente ad alta impedenza (pickup piezo, microfono a condensatore) e "passarlo" a un circuito a bassa impedenza (cavo, amplificatore di potenza) senza caricare la sorgente.

---

## Esercizio 12 — Punto ZTC (Zero Temperature Coefficient)

**Testo.** Un JFET n-channel con $I_{DSS} = 8\text{ mA}$, $V_P = -4\text{ V}$. A quale $V_{GS}$ il JFET è al **punto ZTC** (Zero Temperature Coefficient), cioè la corrente $I_D$ non varia apprezzabilmente con la temperatura?

**Svolgimento.**

La formula semi-empirica per il punto ZTC dei JFET al silicio è:

$$V_{ZTC} \approx V_P + 0{,}7\text{ V}$$

(Regola mnemonica: 'e la tensione in cui l'effetto "barriera di giunzione che si abbassa con T" (~2 mV/°C) compensa esattamente l'effetto "mobilità dei portatori che si abbassa con T".)

1. **Applicazione al caso**:
   $$V_{ZTC} = -4 + 0{,}7 = -3{,}3\text{ V}$$

2. **Verifica tramite $I_D$ al punto ZTC**:
   $$I_{D,ZTC} = I_{DSS} \left(1 - \dfrac{V_{ZTC}}{V_P}\right)^2 = 8 \cdot \left(1 - \dfrac{-3{,}3}{-4}\right)^2 = 8 \cdot (1 - 0{,}825)^2 = 8 \cdot 0{,}0306 \approx 0{,}245\text{ mA}$$

3. **Confronto con polarizzazioni tipiche** (stesso JFET):

| $V_{GS}$ | $I_D$ calcolata | Stabilità termica |
|---|---|---|
| $0\text{ V}$ (massima) | $I_{DSS} = 8\text{ mA}$ | ❌ Molto sensibile a T (la mobilità varia molto) |
| $-2\text{ V}$ (= $V_P/2$) | $I_{DSS}/4 = 2\text{ mA}$ | ✅ Buona — vicino al ZTC |
| $-3{,}3\text{ V}$ (= $V_{ZTC}$) | $0{,}245\text{ mA}$ | ✅ Ottima |
| $-4\text{ V}$ (= $V_P$) | $0$ | ⚠️ $I_D$ troppo piccola, % di variazione alta |

> [!check] Risposta
> $V_{GS} \approx -3{,}3\text{ V}$ è il punto ZTC di questo JFET. La polarizzazione "standard" con $V_{GS} = V_P/2$ (=-2 V qui) è già vicina al ZTC.

> [!tip] Regola pratica per il laboratorio Protti
> Per polarizzare un JFET in modo stabile in temperatura, scegliere $V_{GS}$ "moderatamente negativo" — né troppo vicino a 0 (sensibile a T), né troppo vicino a $V_P$ (la corrente è piccola e le variazioni percentuali sono grandi). La zona $V_{GS} \approx V_P/2$ è il **punto dolce**.

> [!warning] Domanda orale tipica
> *"Se il JFET si scalda in laboratorio, la $I_D$ aumenta o diminuisce?"*
> Dipende dalla polarizzazione:
> - Se $V_{GS}$ è vicino a 0 (sopra il ZTC): $I_D$ **diminuisce** (la mobilità cala più rapidamente dell'effetto barriera).
> - Se $V_{GS}$ è vicino a $V_P$ (sotto il ZTC): $I_D$ **aumenta** (la barriera cala, il canale 'e meno strozzato).
> - Se $V_{GS} = V_{ZTC}$: $I_D$ 'e stabile in temperatura.

---

# ✅ Errori tipici da evitare (esteso)

> [!danger] Segno di $V_P$
> Nei JFET n-channel, $V_P$ è **negativo**. Nei P-channel è **positivo**. Se ottieni $V_P$ del segno sbagliato, hai invertito qualcosa.

> [!danger] Confondere $V_{GS} = V_P$ con $V_{GS} = V_{th}$
> Per il **JFET n**, "cutoff" è $V_{GS} \le V_P$ (negativo), NON $V_{GS} \le 0$. Il valore di $V_{th}$ non c'entra: è un parametro del MOSFET, non del JFET.

> [!danger] Radice del 2° grado "grande"
> Nel 2° grado del JFET, la radice con $I_D$ molto grande è quasi sempre quella da scartare (porterebbe la $V_{GS}$ ben oltre $V_P$, fuori dalla zona di validità della parabola).

> [!danger] Saturazione non verificata
> Se $V_{DS}$ dopo il calcolo è MINORE di $V_{GS} - V_P$, allora non sei in saturazione e devi applicare le formule della zona triodo (NON la parabolica!). Spesso si vede questo errore in laboratorio: il JFET sembra non funzionare → era in triodo, non in pinch-off.

> [!danger] JFET P-channel trattato come N-channel
> Se hai un esercizio che dà $V_P > 0$ o alimentazione negativa, RIFLETTI i segni prima di mettere numeri nelle formule.

> [!danger] Confondere $g_m$ con $g_{m0}$
> $g_{m0} = 2 I_{DSS}/|V_P|$ è la transconduttanza a $V_{GS}=0$ (massima).
> $g_m = g_{m0} (1 - V_{GS}/V_P)$ è la transconduttanza nel punto di lavoro attuale (sempre minore di $g_{m0}$).
> Non scambiarli.

---

## Da qui in poi

- Teoria completa: [[JFET]]
- Esercizi correlati (MOSFET, simile pilotaggio in tensione): [[Esercizi - MOSFET]]
- Esercizi BJT (diverso pilotaggio, in corrente): [[Esercizi - BJT]]
- Confronto amplificatori: [[Esercizi - Amplificatori a BJT]]

---

# 📦 PARTE V — Esercizi svolti da Edutecnica.it

## Esercizi svolti da Edutecnica.it (catalogo jfetx completo)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/jfetx/jfetx.htm](https://www.edutecnica.it/elettronica/jfetx/jfetx.htm). 8 esercizi su JFET n-channel.

### Es. J1 — Polarizzazione con tensione di gate $V_{GG}$

- **Dati**: $V_{GG}=2{,}5\text{ V}$ (positiva! bypassata al source, quindi è *negativa* rispetto al source), $V_P=4\text{ V}$, $I_{DSS}=10\text{ mA}$, $V_{DD}=18\text{ V}$, $R_D=4{,}7\text{k}\Omega$.
- **Soluzione edutecnica**: $I_D = 1{,}4\text{ mA}$, $V_{DS} = 11{,}42\text{ V}$.
- **Svolgimento**: $V_{GS} = -V_{GG} = -2{,}5\text{ V}$ (la pila è tra source e gate, con gate negativo). $I_D = 10 \cdot (1 - (-2{,}5)/(-4))^2 = 10 \cdot (1 - 0{,}625)^2 = 10 \cdot 0{,}1406 = 1{,}41\text{ mA}$ ✓.

### Es. J2 — Autopolarizzazione (self-bias): dimensionamento

- **Dati**: $I_D = 5\text{ mA}$, $V_{DS} = 10\text{ V}$, $V_P = 5\text{ V}$, $I_{DSS} = 12\text{ mA}$, $V_{DD} = 18\text{ V}$.
- **Trovare**: dimensionare $R_S$, $R_D$, $R_G$.
- **Soluzione edutecnica**: $R_S = 354\text{ }\Omega$, $R_D = 1{,}246\text{ k}\Omega$, $R_G = 330\text{ k}\Omega$.
- **Svolgimento**:
  1. $V_{GS} = -I_D \cdot R_S$, ma serve $V_{GS}$ da determinare. Usa parabolica: $V_{GS} = V_P \cdot (1 - \sqrt{I_D/I_{DSS}}) = -5 \cdot (1 - \sqrt{5/12}) = -5 \cdot (1 - 0{,}645) = -1{,}77\text{ V}$.
  2. $R_S = -V_{GS}/I_D = 1{,}77/5\text{ mA} = 354\text{ }\Omega$ ✓.
  3. $R_D = (V_{DD} - V_{DS} - I_D R_S)/I_D = (18 - 10 - 5 \cdot 0{,}354)/5\text{ mA} = (18 - 10 - 1{,}77)/5\text{ mA} = 6{,}23/5\text{ mA} = 1{,}246\text{ k}\Omega$ ✓.
  4. $R_G$ è libera (su gate non scorre corrente), scelta standard $330\text{ k}\Omega$ per avere $V_G \approx 0$.

### Es. J3 — ON/OFF per pilotaggio manuale

- **Dati**: $V_{GS(\text{off})}=-3{,}5\text{ V}$, $I_{DSS}=5\text{ mA}$, $r_{DS(\text{on})}=350\text{ }\Omega$, $V_{DD}=15\text{ V}$, $R_D=10\text{ k}\Omega$.
- **Trovare**: stato del JFET per $V_{GS}=-10\text{ V}$ e $V_{GS}=0\text{ V}$.
- **Procedura**:
  - $V_{GS}=-10 \ll V_P=-3{,}5$: OFF, $I_D = 0$, $V_{DS} = V_{DD} = 15\text{ V}$.
  - $V_{GS}=0$: $I_D = I_{DSS} \cdot 1 = 5\text{ mA}$. **Ma c'è la $r_{DS(\text{on})}$!** In realtà siamo in zona triodo: $I_D = \min(5, V_{DS}/r_{DS})$ — il componente si comporta da resistenza. Da verificare con la retta di carico.

### Es. J4 — Autopolarizzazione dimensiona $R_D, R_S, R_G$

- **Dati**: $V_{DD}=30\text{ V}$, $I_{DSS}=20\text{ mA}$, $V_{GS(\text{off})}=-5\text{ V}$, $I_D=5\text{ mA}$, $V_{DS}=8\text{ V}$.
- **Soluzione edutecnica**: $R_S = 500\text{ }\Omega$, $R_D = 3{,}9\text{ k}\Omega$, $R_G = 300\text{ k}\Omega$.

### Es. J5 — Partitore di gate + source degeneration

- **Dati**: $I_{DSS}=20\text{ mA}$, $V_{GS(\text{off})}=-5\text{ V}$, $V_{DD}=20\text{ V}$, $I_D=5\text{ mA}$, $V_{DS}=8\text{ V}$, $V_{RS}=4\text{ V}$.
- **Soluzione edutecnica**: $R_S = 800\text{ }\Omega$, $R_D = 1{,}6\text{ k}\Omega$, $R_1 = 100\text{ k}\Omega$, $R_2 = 123\text{ k}\Omega$. ⚠️ **Il valore $R_2 = 123$ k di edutecnica è sbagliato: il valore corretto è $\approx 8{,}1$ k** (vedi sotto).
- **Svolgimento**: $R_S = V_{RS}/I_D = 4/5\text{mA} = 800\text{ }\Omega$ ✓. $R_D = (V_{DD} - V_{DS} - V_{RS})/I_D = (20 - 8 - 4)/5\text{mA} = 1{,}6\text{ k}\Omega$ ✓.
  - **Punto di lavoro (Shockley)**: serve $V_{GS} = V_P\left(1-\sqrt{I_D/I_{DSS}}\right) = -5\left(1-\sqrt{5/20}\right) = -5(1-0{,}5) = -2{,}5\text{ V}$ (l'altra radice, $-7{,}5$ V, è $< V_P$: scartata).
  - **Tensione di gate**: $V_S = I_D R_S = 4\text{ V}$, quindi $V_G = V_{GS} + V_S = -2{,}5 + 4 = 1{,}5\text{ V}$.
  - **Partitore** da $V_{DD} = 20$ V: $\dfrac{R_2}{R_1+R_2} = \dfrac{V_G}{V_{DD}} = \dfrac{1{,}5}{20} = 0{,}075$ → con $R_1 = 100$ k, $R_2 = R_1\cdot\dfrac{0{,}075}{1-0{,}075} \approx \mathbf{8{,}1\ \text{k}\Omega}$.
- **Perché edutecnica sbaglia**: con $R_2 = 123$ k e $R_1 = 100$ k il partitore darebbe $V_G = 20\cdot\frac{123}{223} \approx 11$ V, cioè $V_{GS} = V_G - V_S = +7$ V. **Impossibile per un JFET a canale n**: $V_{GS}$ deve essere $\le 0$ (la giunzione di gate è in inversa), altrimenti il gate conduce. I $123$ k corrispondono a un $V_G \approx 11$ V, coerente con un **errore di segno** su $V_{GS}$ ($+7$ invece di $-2{,}5$). La prova che il metodo è questo: applicato all'**Es. J7** ($R_1 = 820$ k, $R_2 = 180$ k → $V_G = 3{,}24$ V), edutecnica ottiene un risultato coerente. Il valore fisicamente corretto qui è $\mathbf{R_2 \approx 8{,}1}$ **k**.

### Es. J6 — JFET come interruttore per LED

- **Dati**: $V_{DD}=16\text{ V}$, $I_{DSS}=100\text{ mA}$, $V_L=6\text{ V}$ (LED), $V_{GS(\text{off})}=-2\text{ V}$, $r_{DS(\text{on})}=10\text{ }\Omega$.
- **Trovare**: $V_i$ per accendere il LED ($I_D = 10\text{ mA}$) e $R$ di limitazione.
- **Soluzione edutecnica**: $R = 1\text{ k}\Omega$, $V_i = -5\text{ V}$.
- **Procedura**: $V_i$ deve portare il JFET in piena conduzione. Con $I_{DSS} = 100\text{ mA}$, basta una piccola tensione negativa (es. $-2\text{ V}$ → ~25 mA, $-5\text{ V}$ → ~80 mA).

### Es. J7 — Source bias classico (partitore + $R_S$)

- **Dati**: $V_P=4\text{ V}$, $I_{DSS}=15\text{ mA}$, $V_{DD}=18\text{ V}$, $R_1=820\text{ k}$, $R_2=180\text{ k}$, $R_S=1\text{ k}$, $R_D=1{,}3\text{ k}$.
- **Soluzione edutecnica**: $I_D=4{,}94\text{ mA}$, $V_{DS}=6{,}63\text{ V}$.

### Es. J8 — ON/OFF (analisi stati)

- **Dati**: $I_{DSS}=20\text{ mA}$, $V_P=4\text{ V}$, $V_{DD}=15\text{ V}$, $R_D=10\text{ k}$.
- **Trovare**: $V_{GS}$ per cutoff e per ON; $V_{DS}$ nei due stati.

---

## Pattern di errore frequenti (Carli scritta)

1. **Segno di $V_{GS}$**: in JFET n, $V_{GS} \leq 0$. Errore: $V_{GS} = +V_G - V_S$. Mai dimenticare che la giunzione è in inversa.
2. **Confondere $V_P$ con $V_{th}$**: sono parametri diversi di transistor diversi. MOSFET ha $V_{th}$, JFET ha $V_P$.
3. **Discriminante sempre positivo**: nel 2° grado JFET con autopolarizzazione il discriminante è sempre > 0. La soluzione valida è quella che dà $V_{GS} > V_P$ (vedi JFET.md §5).
4. **Dimenticare la verifica di saturazione**: dopo aver trovato $I_D$, calcolare $V_{DS}$ e verificare $V_{DS} > V_{GS} - V_P$. Se violata, NON applicare la parabolica.
5. **$g_m$ calcolata nel posto sbagliato**: $g_m$ dipende da $V_{GS}$, e $V_{GS}$ dipende dal punto di lavoro. Calcolare sempre $g_m$ DOPO aver trovato il Q-point.
6. **P-channel trattato come N**: i segni sono tutti specchiati. Rifletti prima di mettere numeri.
