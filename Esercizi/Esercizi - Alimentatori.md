---
tags: [recupero, elettronica, esercizi, alimentatori, power-supply]
fonte: "edutecnica.it/elettronica/alimentatorix + /stabix"
libro_mirandola: "VERIFICATO ✔ (2026-07-28) — coerente con Mirandola Vol.2, Cap. 8 «Gli alimentatori». Sezioni coperte: §1 alimentatori non stabilizzati e fattore di ripple (form. 8.1) pp. 388-389; §3.1 regolatori integrati 78XX/79XX (FIG. 20-21) pp. 406-407; §3 regolatore serie a BJT, §3.2 duale e §3.3 correnti elevate pp. 408-409. ESEMPIO 7 del libro (dimensionamento C con raddrizzatore a ponte) pp. 408-409. File trasversale: teoria già verificata nel [[00 - Audit e correzioni|Lotto 10]]. Inoltre: refuso edutecnica confermato il 2026-07-28 (Es. A3: 12 mF vs 1,2 mF)."
prove: [scritta, pratica]
---

# Esercizi — Alimentatori (raddrizzatori, filtri, regolatori)

> [!info] Dove serve
> **Pratica Protti** (in «circuiti con diodi», LETTERA): misura ripple, regolazione di linea/carico, test del 78xx. (NB: la LETTERA Carli scritta NON cita alimentatori — è solo Protti pratica.)

Prerequisiti: [[Alimentatori]] · [[Diodi]] · [[BJT]] · [[Filtri passivi del primo ordine]].

---

## Esercizi svolti da Edutecnica.it — Alimentatori non stabilizzati

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/alimentatorix/alimentatorix.htm](https://www.edutecnica.it/elettronica/alimentatorix/alimentatorix.htm).

### Es. A1 — Raddrizzatore a semionda: dimensionamento trasformatore e C

- **Dati**: $f = 50$ Hz, $V_L = 12$ V, $R_L = 50\,\Omega$. **Richieste**: $V_{2,\text{eff}}$ e $C$ per ripple 5% e 1%.
- **Soluzione edutecnica**: $C = 2{,}31$ mF (5%) | $11{,}56$ mF (1%). ✅ **Verificate corrette** (vedi sotto).
- **Svolgimento**:
  1. $I_{load} = V_L/R_L = 12/50 = 240$ mA.
  2. **Attenzione a cosa significa «5%»**: qui è il **fattore di ripple** $r = V_{r,\text{eff}}/V_{Lm}$ (rapporto tra il valore *efficace* dell'ondulazione e il valor medio), come definito nel libro Mirandola formula (8.1), Cap. 8 p. 388. **Non** è il picco-picco in percentuale del valor medio.
  3. Per un raddrizzatore a semionda con filtro C, il fattore di ripple vale $r = \dfrac{1}{2\sqrt{3}\, f\, R_L\, C}$, da cui:
     $$C = \frac{1}{2\sqrt{3}\, f\, R_L\, r} = \frac{1}{2\sqrt{3}\cdot 50 \cdot 50 \cdot 0{,}05} = \frac{1}{433} \approx 2{,}31\text{ mF}$$
  4. Per ripple 1%: $C = \dfrac{1}{2\sqrt{3}\cdot 50 \cdot 50 \cdot 0{,}01} = \dfrac{1}{86{,}6} \approx 11{,}56$ mF. ✅
  → La formula picco-picco $C = I_{load}/(f_r V_{r,pp})$ di [[Alimentatori#3. Filtro a condensatore — calcolo del ripple]] risponde a una domanda **diversa** (quanto vale il picco-picco), non al fattore di ripple efficace: applicandola a «5% = picco-picco» darebbe 8 mF, che qui sarebbe fuori luogo.

### Es. A2 — Semionda con Vin specificato

- **Dati**: $R_L = 2\,\text{k}\Omega$, $V_L = 20$ V, $r = 0{,}5\%$.
- **Soluzione edutecnica**: $C = 580\,\mu\text{F}$, $N_1/N_2 = 15$ (rapporto di trasformazione).
- **Procedura**: $V_{2,p} = V_L/(1 - r/2)$ con approssimazione di scarica lineare. $N_1/N_2 = V_1/V_2 = 230/V_2$.
- ⚠️ **Il titolo dice «semionda», ma i 580 µF vengono dalla formula della doppia semionda.** Verifica:
  con la costante della **semionda** ($f_r = f$) sarebbe $C = 1/(2\sqrt3\,f R_L r) = 1/(2\sqrt3 \cdot 50 \cdot 2000 \cdot 0{,}005) = 1{,}16$ mF;
  con quella del **ponte** ($f_r = 2f$, costante $4\sqrt3$) viene $C = 577\ \mu$F, cioè i 580 µF dichiarati.
  Quindi questo esercizio è a **ponte di Graetz**. È lo stesso discrimine dell'Es. A1 (che invece è
  davvero a semionda, e infatti torna con $2\sqrt3$): **prima di scegliere la costante, guarda quanti
  diodi ci sono.**

### Es. A3 — Ponte Graetz con ripple specificato

- **Dati**: $V_L = 12$ V, $R_L = 50\,\Omega$, $V_{r,pp} = 2$ V (ondulazione **picco-picco**, data esplicitamente).
- **Soluzione edutecnica**: $C = 12$ mF. ⚠️ **Errore nel testo di edutecnica: il valore corretto è $1{,}2$ mF** (vedi sotto).
- **Procedura**: $I_{load} = V_L/R_L = 0{,}24$ A. Poiché $V_{r,pp}$ è dato come picco-picco, si usa la formula del libro Mirandola (ESEMPIO 7, Cap. 8 p. 409) per la doppia semionda:
  $$C = \frac{I_{load}}{2 f \cdot V_{r,pp}} = \frac{0{,}24}{2\cdot 50 \cdot 2} = \frac{0{,}24}{200} = 1{,}2\text{ mF}$$
- **Perché $1{,}2$ mF e non $12$**: con $C = 12$ mF si otterrebbe $V_{r,pp} = I_{load}/(2 f C) = 0{,}24/(100\cdot 0{,}012) = 0{,}2$ V, dieci volte **meno** ripple di quanto richiesto. La stessa formula, applicata all'**Es. A4** di edutecnica ($I_{L,\max}=2$ A, $V_{r,pp}=4$ V), dà $C = 2/(100\cdot 4) = 5000\,\mu$F, che **coincide** con la soluzione edutecnica: è la prova che il metodo è questo e che il «12 mF» dell'Es. A3 è un refuso ($\times 10$). Il valore fisicamente corretto è $\mathbf{1{,}2}$ **mF**.

> [!check] Verifica diretta della fonte (2026-07-28)
> Il catalog di <https://www.edutecnica.it/elettronica/alimentatorix/alimentatorix.htm>, scaricato con `curl -L -A 'Mozilla/5.0'`, mostra per l'Esercizio 3 la risposta boxed `[ 12 mF ]` (sotto i dati $V_L=12$V, $R_L=50\Omega$, $V_{rpp}=2$V, doppia semionda). La pagina di dettaglio `3.htm` non pubblica lo svolgimento: edutecnica fornisce solo la risposta. La diagnosi del vault (refuso $\times 10$ nel catalog di edutecnica) **regge**: la fonte stampa effettivamente `12 mF`, ma il valore fisicamente corretto è $1{,}2$ mF.

### Es. A4 — Ponte con $I_{L,\max}$ specificato

- **Dati**: $V_L = 20$ V, $V_{r,pp} = 4$ V, $I_{L,\max} = 2$ A.
- **Soluzione edutecnica**: $r = 5{,}77\%$, $C = 5000\,\mu\text{F}$.

### Es. A5 — Ponte con tolleranza ±10%

- **Dati**: $V_L = 12$ V $\pm 10\%$, $I_{L,\max} = 1$ A.
- **Soluzione edutecnica**: $r = 5{,}8\%$, $C = 4166\,\mu\text{F}$.

---

## Esercizi svolti da Edutecnica.it — Alimentatori stabilizzati (stabix)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/stabix/stabix.htm](https://www.edutecnica.it/elettronica/stabix/stabix.htm).

### Es. S1 — Stabilizzatore Zener: dimensionamento $R_S$

- **Dati**: $V_{in}$ varia $10{-}15$ V, $V_Z = 5{,}6$ V, $I_{Z,\min} = 5$ mA, $I_{Z,\max} = 50$ mA, $I_{L,\max} = 100$ mA.
- **Procedura**:
  1. **Vincolo dal basso** (caso peggiore: $V_{in,\min}$ e carico massimo). La $R_S$ deve lasciar passare
     abbastanza corrente per il carico *più* la minima che tiene lo Zener in breakdown:
     $$R_S \le \frac{V_{in,\min}-V_Z}{I_{Z,\min}+I_{L,\max}} = \frac{10-5{,}6}{105\text{ mA}} = 41{,}9\,\Omega \;=\; R_{S,\max}$$
  2. **Vincolo dall'alto** (caso peggiore: $V_{in,\max}$ e carico staccato). Tutta la corrente finisce
     nello Zener, che non deve superare $I_{Z,\max}$:
     $$R_S \ge \frac{V_{in,\max}-V_Z}{I_{Z,\max}+I_{L,\min}} = \frac{15-5{,}6}{50\text{ mA}} = 188\,\Omega \;=\; R_{S,\min}$$

> [!danger] Con questi dati **non esiste nessuna $R_S$ valida** — ed è il punto dell'esercizio
> Servirebbe $R_S \ge 188\ \Omega$ **e** $R_S \le 41{,}9\ \Omega$ contemporaneamente: l'intervallo è **vuoto**.
> La scelta «$R_S = 100\ \Omega$, valore commerciale tra 40 e 188» che compariva qui era doppiamente
> sbagliata: i due estremi erano scambiati di nome (il 41,9 è il **massimo**, il 188 il **minimo**) e
> soprattutto non c'è nessun intervallo in cui stare. La verifica lo dimostra: con $R_S = 100\ \Omega$ e
> $V_{in}=10$ V passano $I_S = 4{,}4/100 = 44$ mA, ma il carico da solo ne vuole 100 — lo Zener dovrebbe
> **erogare** corrente, cosa che non può fare, e la regolazione salta.
>
> **Come si sistema**: o si riduce $I_{L,\max}$ (con $I_L \le 45$ mA i due vincoli si incontrano), o si
> prende uno Zener che regga $I_{Z,\max} \ge (15-5{,}6)/41{,}9 = 224$ mA — cioè $P_Z = 5{,}6 \cdot 0{,}224 = 1{,}25$ W,
> quindi uno Zener da 2 W. È il limite strutturale del regolatore a solo Zener, e il motivo per cui
> con carichi da 100 mA in su si passa al **regolatore serie a BJT** (Es. S2).
  3. **Potenza su $R_S$** (caso peggiore $V_{in,\max}$), con la $R_S = 188\ \Omega$ minima ammissibile:
     $$P_{R_S} = \frac{(V_{in,\max}-V_Z)^2}{R_S} = \frac{9{,}4^2}{188} = 0{,}47\text{ W} \;\Rightarrow\; \text{resistore da 1 W}$$
     ⚠️ Il valore «88 mW» che era scritto qui era sbagliato di un fattore 10: con $R_S = 100\ \Omega$ si ha
     $I_S = 94$ mA e $P = I_S^2 R_S = 0{,}094^2 \cdot 100 = 0{,}88$ W, non 88 mW. Un quarto di watt non basta.

### Es. S2 — Regolatore serie BJT

- **Dati**: $V_{in} = 15$ V, $V_{out} = 12$ V, $I_{load,\max} = 1$ A, BJT con $\beta = 50$, $V_{BE} = 0{,}7$ V.
- **Procedura**:
  1. $V_Z = V_{out} + V_{BE} = 12{,}7$ V → usa Zener da 12 V (scelta commerciale) → $V_{out} \approx 11{,}3$ V. **Tipico errore**: serve Zener da $V_{out} + 0{,}7$ V.
  2. $I_{B,\max} = I_{load,\max}/\beta = 1\text{ A}/50 = 20$ mA.
  3. $R_S = (V_{in} - V_Z)/(I_Z + I_{load,\max}/\beta) = (15 - 12{,}7)/(5\text{ mA} + 20\text{ mA}) = 92\,\Omega$ (ma diversa da edutecnica che potrebbe dare risultati diversi).
  4. Potenza BJT: $P_{BJT,\max} = (V_{in} - V_{out}) \cdot I_{load,\max} = (15 - 12) \cdot 1 = 3$ W → serve dissipatore!

### Es. S3 — Regolatore con 7812

- **Dati**: $V_{in,\text{nom}} = 15$ V, $V_{out} = 12$ V, $I_{load} = 0{,}5$ A.
- **Procedura**:
  1. Dropout del 7812: $V_D = 2{,}5$ V (TABELLA 1 del libro) → $V_{in} \ge 14{,}5$ V **nel minimo del ripple**. Con $V_{in,\text{nom}} = 15$ V il margine è di soli 0,5 V: va verificato che l'ondulazione picco-picco resti sotto 1 V, altrimenti nei minimi si va in dropout.
  2. Potenza dissipata: $P = (15 - 12) \cdot 0{,}5 = 1{,}5$ W. Dissipatore consigliato.

### Es. S4 — Alimentazione duale ±12 V

- **Dati**: serve $\pm 12$ V, $I_{load} = 200$ mA per ramo.
- **Procedura**:
  1. Trasformatore con **presa centrale** (es. 12-0-12 V AC).
  2. **Due ponti raddrizzatori** (o un ponte duale):
     - Ramo positivo: $V_{+,p} \approx 12 \cdot \sqrt{2} - 1{,}4 \approx 15{,}6$ V → entra nel 7812 → +12 V.
     - Ramo negativo: invertito, $V_{-,p} \approx -15{,}6$ V → entra nel 7912 → −12 V.
  3. GND collegato al **center tap** del trasformatore.

---

## Esercizi extra (libro Mirandola + procedimenti)

### Es. AM1 — Alimentatore completo da zero

**Specifiche**: $V_{out} = 5$ V, $I_{load,\max} = 1$ A, $V_{in} = 230$ V AC 50 Hz, ripple $\leq 50$ mV.

**Procedura completa**:

1. **Trasformatore**: $V_{2,\text{eff}} \approx 9$ V (per avere $V_{in,p} \approx 12{,}7$ V al filtro, dato che $V_{out,\text{reg}}$ = 5 V dal 7805).
2. **Ponte**: 4 diodi ($V_D = 0{,}7$ V; caduta totale $1{,}4$ V).
3. **Filtro C**: $V_{DC} \approx 12{,}7 - 1{,}4 = 11{,}3$ V. Per $V_{r,pp} = 0{,}5$ V: $C = 1\text{A}/(100\text{Hz} \cdot 0{,}5\text{V}) = 20$ mF.
4. **Regolatore 7805**: dropout $V_D = 2{,}5$ V (TABELLA 1) → $V_{in}$ minimo al 7805 $= 5 + 2{,}5 = 7{,}5$ V. Con $V_{DC} = 11{,}3$ V e ripple 0,5 V il minimo è 10,8 V: margine ampio ✅.
5. **Calore dissipato dal 7805**: $P_{7805} = (V_{in} - V_{out}) \cdot I_{load} = (11{,}3 - 5) \cdot 1 = 6{,}3$ W → serve dissipatore serio!
6. **$C_{out}$**: 0,1 µF ceramico in uscita → stabilizza il regolatore.

> [!warning] Verifica dropout
> Se $V_{DC}$ dopo il filtro scende sotto $V_{out} + 2$ V (es. a $I_{load,\max}$ con tensione di rete minima), il 7805 "esce dalla regolazione" e $V_{out}$ crolla. Verifica SEMPRE con tensione di rete −15%.

---

## Pattern di errore frequenti (Carli scritta)

1. **Dimenticare la caduta di $2V_D$ nel ponte**: $V_{out,p}$ è $V_{in,p} - 1{,}4$ V. Errore: pensare che basti $V_{in,p} = V_{out}$.
2. **Capire male il dropout**: per tutta la famiglia 78xx il libro dà $V_D = 2{,}5$ V (TABELLA 1, p. 408). Se $V_{in} < V_{out} + 2{,}5$ V **nel punto più basso del ripple** (non in media!), il regolatore esce di regolazione e $V_{out}$ crolla.
3. **Confondere $P_{BJT}$ in zona attiva con $P_{BJT}$ in saturazione**: nel regolatore serie, BJT è in **zona attiva** → $P = V_{CE} \cdot I_C$. In saturazione, $V_{CE} \approx 0{,}2$ V → $P$ bassa. Regime attivo è quello "pericoloso" per la dissipazione.
4. **Zener rovesciato**: lo Zener va usato in polarizzazione **inversa** (catodo positivo!). Errore: usarlo come un diodo normale → dissipa ma non stabilizza.

---

## Da qui in poi

- Teoria: [[Alimentatori]]
- Prerequisiti: [[Diodi]], [[BJT]], [[Filtri passivi del primo ordine]]
- Simulazione completa: [[Esercizi - Simulazione finale]]
- Riferimenti: https://www.edutecnica.it/elettronica/alimentatorix/alimentatorix.htm · https://www.edutecnica.it/elettronica/stabix/stabix.htm
