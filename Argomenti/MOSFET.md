---
tags: [recupero, elettronica, transistor, mosfet, fet]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) — Cap. 7 «Gli amplificatori a transistor», §3 «I transistor FET e gli amplificatori a FET» (pp. 358-369). MOSFET e porte CMOS: §3.3, pp. 366-368 (FIG. 45 struttura, FIG. 46 simboli, FIG. 47 caratteristiche depletion, FIG. 48 polarizzazione, FIG. 49-50 invertitore/CMOS). Conversione folio Cap. 7: pag. stampata = 2·PDF + 122."
prove: [scritta, orale, pratica-cenni]
---

# MOSFET — Struttura, regioni e polarizzazione (n-channel enhancement)

> [!info] Dove serve
> **Scritta** Carli: esercizi su transistor MOSFET enhancement canale n. **Orale** Carli: paragoni con BJT e JFET. **Pratica** Protti: solo cenni (gli amplificatori in laboratorio sono a BJT).

Prerequisiti: [[Impedenza dei bipoli R, L, C]], [[Diodi]] (la giunzione p-n del substrato è costruita come un diodo).

> Schema di polarizzazione di un MOSFET enhancement a canale n, con $R_S$ che alza il source (Mirandola Vol.2, Cap. 7 §3.3, **FIGURA 48A**, p. 368; la variante depletion è la FIG. 48B). Il partitore $R_1$–$R_2$ fissa $V_G$ e $R_S$ stabilizza il punto di lavoro, come nel BJT a partitore.
> ![[libro-cap7-pp368-369-mosfet-polarizzazione-invertitore.png]]

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §9**.

## 1. Cos'è un MOSFET enhancement n-channel

Il **MOSFET** (Metal-Oxide-Semiconductor FET) è un transistor **controllato in tensione**, non in corrente. Ha quattro terminali:

- **Gate (G)** — isolato dal canale da uno strato di **ossido** → corrente di gate ≈ 0 (trascurabile).
- **Source (S)** — terminale "a valle" del canale (convenzione: da dove entrano i portatori).
- **Drain (D)** — terminale "a monte" (da dove escono).
- **Body / Bulk (B)** — substrato del chip; quasi sempre connesso al source. Nei circuiti discreti è raramente disegnato.

> [!tip] Perché si chiama "enhancement"
> In un MOSFET enhancement **a canale n** a $V_{GS}=0$ **non esiste canale conduttivo**. Applicando $V_{GS}$ positiva oltre la **tensione di soglia** $V_{th}$ (tipicamente 1–4 V), si "crea" (enhance) il canale sotto l'ossido.

### Equazione di design (regione di saturazione)

$$I_D = K \cdot (V_{GS} - V_{th})^2$$

dove $K$ è il **parametro di transconduttanza**, in **A/V²** (dipendente dal dispositivo specifico).

---

## 2. Regioni di funzionamento

| Regione | Condizione | Comportamento |
|---|---|---|
| **Cutoff** | $V_{GS} < V_{th}$ | $I_D = 0$; il MOSFET è un interruttore aperto |
| **Triodo (lineare)** | $V_{GS} > V_{th}$ **e** $V_{DS} < V_{GS} - V_{th}$ | Si comporta da resistenza controllata da $V_{GS}$ |
| **Saturazione (attiva)** | $V_{GS} > V_{th}$ **e** $V_{DS} > V_{GS} - V_{th}$ | $I_D ≈ \text{costante}$ data da $V_{GS}$, usata in amplificazione |

> [!warning] "Saturazione" nel MOSFET ≠ "saturazione" nel BJT
> Nel MOSFET, "**saturazione**" è la zona in cui il transistor **amplifica** (corrisponde alla zona attiva del BJT). Il MOSFET **non ha** una vera zona di saturazione come il BJT dove $V_{CE}$ collassa a ~0,2 V. Nel MOSFET in triodo, il chip si comporta da resistenza variabile.

---

## 3. La polarizzazione (calcolo del punto di lavoro Q)

Curva parabolica $I_D(V_{GS})$ + retta di carico di drain = punto Q.

### 3.1 Maglia di gate (ingresso)

Poiché la corrente di gate è ≈ 0, $V_G$ è dato dal **partitore resistivo** $R_1$–$R_2$ tra $V_{DD}$ e GND:

$$V_G = V_{DD} \cdot \frac{R_2}{R_1 + R_2}$$

Il source è "alzato" dalla resistenza $R_S$:

$$V_S = I_D \cdot R_S \quad \Rightarrow \quad V_{GS} = V_G - V_S = V_G - I_D R_S$$

### 3.2 Equazione di progetto

$$I_D = K \cdot (V_{GS} - V_{th})^2 = K \cdot (V_G - I_D R_S - V_{th})^2$$

Questa è un'**equazione di 2° grado in $I_D$**. Si risolve espandendo il quadrato e applicando la formula risolutiva.

> [!danger] Scelta della radice (regola operativa)
> Scarta **sempre** la radice che, sostituita nell'equazione $V_{GS} = V_G - I_D R_S$, porterebbe a $V_{GS} < V_{th}$ (in quel caso il MOSFET sarebbe in cutoff e l'equazione parabolica **non è applicabile**). Però non affidarti ciecamente alla regola euristica *"la più piccola è quella giusta"* — anche se in pratica (per circuito standard con $R_S > 0$) la radice più piccola è **sempre** quella valida, **verifica comunque** il $V_{GS}$ ottenuto e confrontalo con $V_{th}$ per non sbagliare un segno o scambiare i parametri.

### 3.3 Maglia di drain (uscita)

In saturazione vale la retta di carico:

$$V_{DS} = V_{DD} - I_D \cdot (R_D + R_S)$$

**Verifica di zona**: serve $V_{DS} > V_{GS} - V_{th}$ per essere in saturazione. Se la condizione non è verificata, il transistor è in triodo e l'equazione quadratica non è più valida (la corrente è minore).

---

## 3-bis. Come lo chiede Carli: il **progetto** (la strada inversa)

> [!important] Due esercizi su tre della parte MOSFET sono di progetto
> Il §3 risolve l'**analisi**: dato il partitore, trova $I_D$ e $V_{DS}$. Carli chiede anche
> l'inverso — **dato $I_D$, dimensiona $R_D$, $R_1$, $R_2$** — e lì $V_{GS}$ arriva da
> un'altra strada. Confonderle è l'errore che il prof. ha segnato a lettere maiuscole:
> «errata relazione che fornisce $V_{GS}$».

**Le due strade per $V_{GS}$, da tenere separate:**

| Situazione | Da dove viene $V_{GS}$ | A che serve la parabolica |
|---|---|---|
| **Analisi** — il partitore è dato | $V_{GS}=V_{R2}=V_{DD}\dfrac{R_2}{R_1+R_2}$ (meno $V_S$ se c'è $R_S$) | a ricavare $I_D = K(V_{GS}-V_t)^2$ |
| **Progetto** — $I_D$ è dato | $V_{GS}=\sqrt{\dfrac{I_D}{K}}+V_t$ | è la stessa formula, invertita |

> [!danger] Sull'esercizio di analisi il prof. ha cancellato la radice scrivendo «NON SERVE»
> Se il partitore è dato, $V_{GS}$ è già determinato dal circuito: usare
> $\sqrt{I_D/K}+V_t$ lì significa risolvere due volte lo stesso vincolo. E attenzione a non
> scrivere $\sqrt{I_D/R_D}$ al posto di $\sqrt{I_D/K}$: è l'errore esatto della verifica.

**La procedura di progetto, nell'ordine in cui la scrive Carli** (dati $V_{DD}$, $I_D$, $K$,
$V_t$, $R_1+R_2$):

1. $V_{GS} = \sqrt{I_D/K} + V_t$
2. **Si sceglie $V_{DS}$**, rispettando il vincolo di saturazione $V_{DS}\ge V_{GS}-V_t$ —
   testualmente: «quindi ad esempio si fissa $V_{DS}=6$ V». Non è un calcolo, è una scelta
   di progetto: dichiarala e motivala.
3. $R_D = \dfrac{V_{DD}-V_{DS}}{I_D}$ &nbsp;(se c'è $R_S$: $R_D = \dfrac{V_{DD}-V_{DS}-V_S}{I_D}$)
4. $V_{R2} = V_{GS}$ &nbsp;(se c'è $R_S$: $V_{R2} = V_{GS}+V_S$, con $V_S = R_S I_D$)
5. $R_2 = \dfrac{V_{R2}}{V_{DD}}(R_1+R_2)$, &nbsp; $R_1 = (R_1+R_2)-R_2$

> [!danger] Con $R_S$, il source non è a massa
> Sull'ultimo esercizio della verifica il prof. corregge quattro righe di fila, tutte figlie
> di questa dimenticanza: $I_S = I_D$ (non un partitore di correnti), $V_S = R_S I_D$ (non un
> partitore di tensioni), $V_{R2} = V_{GS}+V_S$, e $R_D$ calcolata sottraendo anche $V_S$.
> Vedi [[05 - Verifiche FUSI (Carli)]] §6.

> [!tip] Controllo di unità che salva un esercizio
> $K$ si dà in **mA/V²**: con $K=0{,}6$ mA/V² e $V_{GS}-V_t=11{,}9$ V viene
> $I_D = 0{,}6\cdot10^{-3}\cdot141{,}6 = 84{,}9$ **mA**, non 84,9 A. Sul foglio della verifica
> quel fattore $10^{-3}$ perso è segnato in rosso.

---

## 4. Esempio numerico completo (da edutecnica.it — Esercizio 5)

**Dati:** $V_{DD}=18\text{ V}$, $R_1=5{,}6\text{ k}\Omega$, $R_2=4{,}7\text{ k}\Omega$, $R_D=2{,}2\text{ k}\Omega$, $R_S=1{,}2\text{ k}\Omega$, $K=0{,}4\text{ mA/V}^2$, $V_{th}=3\text{ V}$.

**Svolgimento passo passo** (mantengo le unità: $I_D$ in mA, tensioni in V):

1. **Tensione di gate** (dal partitore):
   $$V_G = 18 \cdot \frac{4{,}7}{5{,}6 + 4{,}7} = 18 \cdot \frac{4{,}7}{10{,}3} \approx 8{,}21\text{ V}$$

2. **$V_{GS}$ in funzione di $I_D$** (per la presenza di $R_S$):
   $$V_{GS} = V_G - I_D R_S = 8{,}21 - 1{,}2 \cdot I_D$$

3. **Equazione parabolica** del MOSFET:
   $$I_D = 0{,}4 \cdot (8{,}21 - 1{,}2 I_D - 3)^2 = 0{,}4 \cdot (5{,}21 - 1{,}2 I_D)^2$$

4. **Espansione del quadrato**:
   $$I_D = 0{,}4 \cdot (27{,}14 - 12{,}50 I_D + 1{,}44 I_D^2) = 10{,}86 - 5{,}00 I_D + 0{,}576 I_D^2$$

5. **Riformulo come 2° grado**:
   $$0{,}576 I_D^2 - 6{,}00 I_D + 10{,}86 = 0$$

6. **Radici** (formula $ax^2+bx+c=0$):
   $$\Delta = 36{,}00 - 25{,}01 = 10{,}99 \approx 11{,}0$$
   $$I_D = \frac{6{,}00 \pm \sqrt{11{,}0}}{2 \cdot 0{,}576} = \frac{6{,}00 \pm 3{,}32}{1{,}152}$$

   - $I_{D1} = 9{,}32/1{,}152 ≈ 8{,}09\text{ mA}$ → porterebbe $V_{GS} ≈ 8{,}21 - 9{,}71 = -1{,}5\text{ V} < V_{th}$: **SCARTATA** (non fisica).
   - $I_{D2} = 2{,}68/1{,}152 ≈ 2{,}33\text{ mA}$ → $V_{GS} = 5{,}42\text{ V} > V_{th}$: ✅ **ACCETTATA**.

7. **Tensione $V_{DS}$**:
   $$V_{DS} = 18 - 2{,}33 \cdot (2{,}2 + 1{,}2) = 18 - 7{,}92 \approx 10{,}1\text{ V}$$

8. **Verifica di saturazione**: $V_{GS} - V_{th} = 5{,}42 - 3 = 2{,}42\text{ V}$. Poiché $V_{DS} = 10{,}1\text{ V} > 2{,}42\text{ V}$ → ✅ **in saturazione**.

> [!check] Confronto con la soluzione edutecnica
> $I_D = 2{,}33\text{ mA}$, $V_{DS} = 10\text{ V}$ — coincidenti con la soluzione ufficiale di [edutecnica.it](https://www.edutecnica.it/elettronica/mosfetx/mosfetx.htm).

---

## 5. Quesiti tipo — Guida rapida

> [!question] Differenza tra MOSFET enhancement e depletion?
> Enhancement: a $V_{GS}=0$ non conduce; serve $V_{GS}>V_{th}$ per accenderlo.
> Depletion: a $V_{GS}=0$ conduce già (canale pre-esiste); serve $V_{GS}<0$ per "svuotarlo".

> [!question] Perché la corrente di gate è praticamente zero?
> Perché il gate è isolato dal canale da uno strato di ossido (~1 nm). L'unica corrente è una piccolissima corrente di **leakage** (pA–nA). Per questo il MOSFET **non assorbe** corrente di pilotaggio → perfetto per CMOS e pilotaggio di potenza.

> [!question] Quando il MOSFET è in "triodo" (regione lineare)?
> Quando $V_{DS}$ è piccolo abbastanza da non raggiungere il pinch-off: $V_{DS} < V_{GS} - V_{th}$. In questa zona il MOSFET si comporta come una resistenza lineare $R_{DS} = V_{DS}/I_D$ il cui valore è controllato da $V_{GS}$.

> [!question] Verifica di saturazione: cosa controllare?
> Deve valere $V_{DS} ≥ V_{GS} - V_{th}$. Se la condizione NON è verificata, il transistor è in triodo e la formula parabolica $I_D = K(V_{GS}-V_{th})^2$ **non è più valida**.

> [!question] Perché il MOSFET è dominante nell'elettronica digitale?
> Perché scalda molto meno in commutazione: la corrente di gate è ≈ 0, quindi la potenza di pilotaggio è trascurabile. Inoltre un MOSFET è molto più "denso" di un BJT in un circuito integrato (un transistor CMOS = 1 MOSFET n + 1 MOSFET p).

---

## 6. Quando il MOSFET NON va in saturazione anche con $V_{GS} > V_{th}$?

Più precisamente: anche con $V_{GS} > V_{th}$, se la $V_{DS}$ **cade troppo** — cioè se $R_D$ è
**grande** (o $V_{DD}$ bassa) — il transistor finisce **in triodo**. ⚠️ Il verso è questo: nella maglia
d'uscita $V_{DS} = V_{DD} - I_D(R_D+R_S)$, quindi è la $R_D$ *grande* a mangiarsi la $V_{DS}$; una $R_D$
piccola spinge semmai più a fondo in saturazione. In tal caso:

- La corrente $I_D$ è determinata dalla legge di Ohm su $R_{DS}$, NON dalla parabola.
- In laboratorio questo si vede bene: riducendo $V_{DD}$ la $V_{DS}$ cala, e il punto sulla curva si avvicina al ginocchio → la corrente comincia a calare.

> [!tip] Osservazione di laboratorio (Protti)
> All'oscilloscopio puoi vedere il "ginocchio" della curva $I_D$–$V_{DS}$ quando il punto operativo passa da saturazione a triodo. È una buona occasione per imparare a muoversi nel piano delle caratteristiche.

---

## 7. Da qui in poi

- Prerequisiti: [[Impedenza dei bipoli R, L, C]], [[Diodi]]
- Confronto (sezione di [[BJT]]): BJT vs MOSFET vs JFET
- Parente stretto (n-channel, pilotaggio in tensione): [[JFET]]
- Esercizi: [[Esercizi - MOSFET]]
- Riferimenti libro: Mirandola Vol.2, **Cap. 7 §3.3 «I MOSFET e le porte CMOS», pp. 366-368** (FIG. 45-50)
- Riferimenti online: https://www.edutecnica.it/elettronica/mosfetx/mosfetx.htm
