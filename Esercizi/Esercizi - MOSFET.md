---tags: [recupero, elettronica, esercizi, mosfet]
fonte: "edutecnica.it/elettronica/mosfetx/ (esercizi svolti)"
libro_mirandola: "VERIFICATO ✔ (2026-07-28) — coerente con Mirandola Vol.2, Cap. 7 §3.3 «I transistor MOSFET e le porte CMOS», pp. 366-368. MOSFET enhancement n: FIG. 45 struttura, FIG. 46 simboli, FIG. 47 caratteristiche depletion, FIG. 48 polarizzazione, FIG. 49-50 invertitore/CMOS. File trasversale: teoria già verificata nel [[Prove/00 - Audit e correzioni|Lotto 11]]. Conversion folio Cap. 7: pag. stampata = 2·PDF + 122."
prove: [scritta]---

# Esercizi — MOSFET enhancement (n-channel)

> [!info] Dove serve
> **Scritta** Carli: esercizi su MOSFET enhancement canale n.

Prerequisiti: [[MOSFET]], [[Impedenza dei bipoli R, L, C]], [[Il metodo simbolico]].

---

## Esercizio 1 — Polarizzazione a partitore (da edutecnica.it)

**Testo.** Calcola il punto di lavoro del MOSFET enhancement di figura, dove:
$V_{DD}=18\text{ V}$, $R_1=5{,}6\text{ k}\Omega$, $R_2=4{,}7\text{ k}\Omega$, $R_D=2{,}2\text{ k}\Omega$, $R_S=1{,}2\text{ k}\Omega$, $K=0{,}4\text{ mA/V}^2$, $V_{th}=3\text{ V}$.

Determina $I_D$ e $V_{DS}$ e verifica se il transistor è in saturazione.

**Svolgimento.**

1. **Tensione di gate** (data dal partitore di gate, con corrente di gate ≈ 0):
   $$V_G = V_{DD} \frac{R_2}{R_1 + R_2} = 18 \cdot \frac{4{,}7}{5{,}6 + 4{,}7} = 18 \cdot \frac{4{,}7}{10{,}3} \approx 8{,}21\text{ V}$$

2. **Equazione di gate-source** ($V_{GS}$ dipende da $I_D$ per via di $R_S$):
   $$V_{GS} = V_G - I_D R_S = 8{,}21 - 1{,}2 \cdot I_D \quad (I_D \text{ in mA})$$

3. **Equazione parabolica** del MOSFET:
   $$I_D = K (V_{GS} - V_{th})^2 = 0{,}4 (8{,}21 - 1{,}2 I_D - 3)^2 = 0{,}4 (5{,}21 - 1{,}2 I_D)^2$$

4. **Espansione:**
   $$I_D = 0{,}4 (27{,}14 - 12{,}5 I_D + 1{,}44 I_D^2) = 10{,}86 - 5{,}00 I_D + 0{,}576 I_D^2$$

5. **Equazione di 2° grado:**
   $$0{,}576 I_D^2 - 6{,}00 I_D + 10{,}86 = 0$$

6. **Radici:**
   $$\Delta = (-6)^2 - 4 \cdot 0{,}576 \cdot 10{,}86 = 36{,}0 - 25{,}0 = 11{,}0$$
   $$I_D = \frac{6{,}00 \pm \sqrt{11{,}0}}{2 \cdot 0{,}576} = \frac{6{,}00 \pm 3{,}32}{1{,}152}$$

   - $I_{D1} = 9{,}32/1{,}152 ≈ 8{,}09\text{ mA}$ → darebbe $V_{GS} = 8{,}21 - 9{,}71 ≈ -1{,}5\text{ V}$ (sotto $V_{th}$!) **SCARTATA**.
   - $I_{D2} = 2{,}68/1{,}152 ≈ 2{,}33\text{ mA}$ → $V_{GS} = 8{,}21 - 2{,}80 = 5{,}42\text{ V} > V_{th}$ ✅ **ACCETTATA**.

7. **Tensione $V_{DS}$:**
   $$V_{DS} = V_{DD} - I_D (R_D + R_S) = 18 - 2{,}33 \cdot 3{,}4 ≈ 10{,}1\text{ V}$$

8. **Verifica di saturazione**: serve $V_{DS} > V_{GS} - V_{th}$.
   $V_{GS} - V_{th} = 5{,}42 - 3 = 2{,}42\text{ V}$. Poiché $V_{DS} = 10{,}1\text{ V} > 2{,}42\text{ V}$ → ✅ **in saturazione**.

> [!check] Risposta
> $I_D ≈ 2{,}33\text{ mA}$, $V_{DS} ≈ 10\text{ V}$ — coincide con la soluzione ufficiale di edutecnica.

---

## Esercizio 2 — Cosa succede se cambio $R_D$?

**Testo.** Stesso circuito dell'esercizio 1, ma con $R_D = 0{,}5\text{ k}\Omega$. Il transistor è ancora in saturazione?

**Svolgimento.**

Il punto Q cambia perché $R_D$ compare solo nella maglia di drain:

- $V_G$, $I_D$ ≈ 2,33 mA (invariati — $R_D$ non è nelle equazioni di gate).
- $V_{DS} = 18 - 2{,}33 \cdot (0{,}5 + 1{,}2) = 18 - 3{,}96 ≈ 14{,}0\text{ V}$.
- Verifica: $V_{DS} = 14{,}0 > 2{,}42 = V_{GS}-V_{th}$ → **ancora in saturazione**.

> [!tip] Riflessione didattica
> Per *spostare* il transistor in triodo serve ridurre $R_D$ **molto** di più (es. $R_D = 0{,}1\text{ k}\Omega$). Riducendo $V_{DD}$ si ha lo stesso effetto: la $V_{DS}$ "cala" e il ginocchio si avvicina.

---

## Esercizio 3 — Calcolo veloce "da orale"

**Testo.** Un MOSFET enhancement ha $K=0{,}5\text{ mA/V}^2$, $V_{th}=2\text{ V}$ ed è polarizzato con $V_{GS}=5\text{ V}$. Calcola $I_D$.

**Svolgimento.**

Direttamente dall'equazione parabolica:

$$I_D = K (V_{GS} - V_{th})^2 = 0{,}5 \cdot (5 - 2)^2 = 0{,}5 \cdot 9 = 4{,}5\text{ mA}$$

> [!tip] Esercizio "veloce" per l'orale Carli
> Quando Carli chiede alla lavagna un calcolo di $I_D$ con valori dati, riconducilo sempre a questa formula: una moltiplicazione, un quadrato, una moltiplicazione. **Non serve** $R_D$, $R_S$, $V_{DD}$ — è pura applicazione della parabola.

---

## Esercizio 4 — Il MOSFET è in cutoff?

**Testo.** In un circuito, $V_G = 4\text{ V}$, $R_S = 0$, $V_{th} = 3\text{ V}$, $V_{DD}$ molto grande. Il MOSFET conduce?

**Svolgimento.**

$V_{GS} = V_G - I_D \cdot 0 = V_G = 4\text{ V}$ (con $R_S = 0$, la $V_{GS}$ è fissata direttamente).

$V_{GS} = 4\text{ V} > V_{th} = 3\text{ V}$ → **conduce**.

$$I_D = K (V_{GS} - V_{th})^2 = K \cdot 1 = K \cdot 1 \text{ (A/V²)}$$

Il valore di $K$ determina la corrente: se $K = 0{,}5\text{ mA/V}^2$ → $I_D = 0{,}5\text{ mA}$.

---

## Errori tipici da evitare

> [!danger] Confondere la radice "grande" con quella valida
> Nel 2° grado, la radice con $I_D$ "grande" porta sempre a $V_{GS} < V_{th}$ → **non fisica**. Scarta sempre la radice più grande.

> [!danger] Dimenticare la verifica di saturazione
> Se $V_{DS} < V_{GS} - V_{th}$ il transistor è in triodo, NON in saturazione. La formula parabolica **non è valida** in triodo: darebbe $I_D$ sovrastimato.

> [!danger] Scambiare i segni della corrente
> $I_D$ è **positiva** per definizione (è una corrente che scorre dal drain al source). Se nei conti ottieni $I_D < 0$, hai sbagliato un segno nelle equazioni.

---

## Da qui in poi

- Teoria: [[MOSFET]]
- Esercizi correlati (JFET, simile pilotaggio in tensione): [[Esercizi - JFET]]
- Esercizi BJT (diverso pilotaggio, in corrente): [[Esercizi - BJT]]
- Riferimenti: https://www.edutecnica.it/elettronica/mosfetx/mosfetx.htm

## Esercizi svolti da Edutecnica.it (catalogo mosfetx completo)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/mosfetx/mosfetx.htm](https://www.edutecnica.it/elettronica/mosfetx/mosfetx.htm). 7 esercizi su MOSFET NMOS enhancement.

### Es. M1 — Dimensionamento partitore di gate

- **Dati**: $V_{DD}=12$ V, $V_{DS}=6$ V, $V_{GS}=4$ V, $I_D=2$ mA, $R_1 + R_2 = 6\,\text{M}\Omega$.
- **Trovare**: $R_D$, $R_1$, $R_2$.
- **Soluzione edutecnica**: $R_1=4\,\text{M}\Omega$, $R_2=2\,\text{M}\Omega$, $R_D=3\,\text{k}\Omega$.
- **Svolgimento**:
  1. $V_G = V_{GS} + I_D \cdot 0$ (se $R_S = 0$): $V_G = V_{GS} = 4$ V.
  2. Partitore: $V_G = V_{DD} \cdot R_2/(R_1+R_2) = 4$ V → $R_2/(R_1+R_2) = 1/3$ → $R_2 = 2\,\text{M}$, $R_1 = 4\,\text{M}$.
  3. $R_D = (V_{DD} - V_{DS})/I_D = (12 - 6)/2\text{ mA} = 3\,\text{k}\Omega$.

### Es. M2 — Dimensionamento punto di lavoro

- **Dati**: $V_{DD}=18$ V, $I_D=5$ mA, $K=0{,}3\text{ mA/V}^2$, $V_T=3{,}5$ V.
- **Trovare**: dimensionare le resistenze per saturazione in zona attiva.
- **Procedura**: da $I_D = K(V_{GS}-V_T)^2$ ricavo $V_{GS} - V_T = \sqrt{5/0{,}3} = 4{,}08$ V → $V_{GS} = 7{,}58$ V. Fissato $V_G$ dal partitore.

### Es. M3 — MOSFET con $K = 0{,}2\text{ mA/V}^2$

- **Dati**: $V_{DD}=18$ V, $K=0{,}2\text{ mA/V}^2$, $V_T=3$ V, $R_1=8\,\text{M}$, $R_2=5\,\text{M}$, $R_D=2{,}7\,\text{k}$.
- **Soluzione edutecnica**: $I_D = 3{,}07$ mA, $V_{DS} = 9{,}71$ V.
- **Svolgimento**: $V_G = 18 \cdot 5/13 = 6{,}92$ V. $V_{GS} = V_G = 6{,}92$ V (no $R_S$). $I_D = 0{,}2 \cdot (6{,}92-3)^2 = 0{,}2 \cdot 15{,}37 = 3{,}07$ mA ✓.

### Es. M4 — Verifica dimensionamento

- **Dati**: $V_{DD}=12$ V, $V_{DS}=6$ V, $V_{GS}=6$ V, $I_D=2$ mA, $R_1=5\,\text{M}$.
- **Soluzione edutecnica**: $R_D = 3\,\text{k}\Omega$.
- **Svolgimento**: $R_D = (V_{DD} - V_{DS})/I_D = 6/2 = 3\,\text{k}\Omega$ ✓.

### Es. M5 — Standard (già visto nel libro)

- **Dati**: $V_{DD}=18$ V, $R_1=5{,}6\text{ k}$, $R_2=4{,}7\text{ k}$, $R_D=2{,}2\text{ k}$, $R_S=1{,}2\text{ k}$, $K=0{,}4\text{ mA/V}^2$, $V_T=3$ V.
- **Soluzione**: $I_D = 2{,}33$ mA, $V_{DS} = 10$ V. (vedi sezione precedente).

### Es. M6 — MOSFET come interruttore (relè)

- **Dati**: $V_{DD}=10$ V, $V_T=3$ V, $I_{D(\text{on})}=1{,}7$ A, $V_{GS}=10$ V, $r_{D(\text{on})}=2\,\Omega$, $R_L=100\,\Omega$.
- **Trovare**: $V_i$ per accendere il relè (si noti: $V_i$ = tensione di pilotaggio del gate, distinto da $V_{GS}$).
- **Procedura**: serve $V_{GS} > V_T + (\text{margine}) \approx 5$ V. Tipicamente $V_i = V_{GS} = 10$ V (vedi datasheet).

### Es. M7 — Source degeneration

- **Dati**: $V_T=3$ V, $I_{D(\text{on})}=18$ mA, $V_{GS}=10$ V, $I_D=4$ mA, $V_{DS}=6$ V, $V_{RS}=2$ V.
- **Trovare**: dimensionare $R_S$, $R_D$.
- **Procedura**: $R_S = V_{RS}/I_D = 2/4\text{ mA} = 500\,\Omega$. $R_D = (V_{DD} - V_{DS} - V_{RS})/I_D$.

## Pattern di errore frequenti (Carli scritta)

1. **Confondere $K$ con unità**: $K$ è data in $\text{mA/V}^2$; se $I_D$ deve essere in $\mu\text{A}$ o in A, convertire subito. Errore comune: $K = 0{,}3$ interpretato come $0{,}3\text{ A/V}^2$.
2. **Dimenticare la verifica di saturazione**: dopo aver trovato $I_D, V_{GS}$, controllare $V_{DS} > V_{GS} - V_T$. Se no, sei in triodo, NON in saturazione.
3. **$V_{GS}$ vs $V_G$**: se c'è $R_S$, $V_{GS} \neq V_G$. Errore: ignorare $R_S$ nel calcolo di $V_{GS}$.
