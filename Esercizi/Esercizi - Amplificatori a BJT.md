---
tags: [recupero, elettronica, amplificatori, bjt, piccolo-segnale, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ (2026-07-19) — Mirandola Vol.2, Cap. 7 «Gli amplificatori a transistor», pp. 312-351 (pagg.-PDF 95-114). Riferimenti d'esercizio: parametri dell'amplificatore CE — R_i (7.13), G_i (7.14), G_v (7.15), R_o = R_C (7.16), pp. 342-345 · attenuazione del partitore d'ingresso p. 344 · dimensionamento del by-pass ed ESEMPIO 7 p. 337 · TABELLA 1 di progetto ed ESEMPIO 12 p. 346 · collettore comune pp. 347-349 · base comune pp. 350-351. Mappa completa in [[Amplificatori a BJT]]."
prove: [orale, pratica]
---

# Esercizi — Amplificatori a BJT

Teoria di riferimento: [[Amplificatori a BJT]], [[L'oscilloscopio]]

---

# Parte A — Quesiti (prova orale)

> [!question]- 1 — Perché in CE c'è inversione di fase?
> Perché $V_{out} = V_{CC} - I_C R_C$: quando $I_C$ sale (l'ingresso sale), $V_{out}$ scende. È la firma del CE: se non c'è inversione, **non è un CE**.

> [!question]- 2 — Cos'è l'emitter follower e a cosa serve?
> È un amplificatore in configurazione **collettore comune** (CC). Ha $A_v \approx 1$ (l'uscita "segue" la base con offset di ~0,7 V), alta impedenza di ingresso, bassa impedenza di uscita. Serve come **buffer** — adatta l'impedenza tra una sorgente ad alta Z e un carico a bassa Z.

> [!question]- 3 — Come si misura la $f_H$ di un amplificatore?
> Si varia la frequenza del segnale di ingresso (ampiezza costante) e si trova la frequenza a cui $|V_{out}|$ cala a $|A_v|/\sqrt{2} \approx 0{,}707 \cdot |A_v|$ (cioè -3 dB). Quella è $f_H$.

> [!question]- 4 — Perché un amplificatore è "passa-banda" e non "passa-basso"?
> Perché ha due tagli: $f_L$ sotto (dovuto alle C di accoppiamento in serie) e $f_H$ sopra (dovuto alle C parassite del transistor). Solo tra $f_L$ e $f_H$ il guadagno è piatto.

> [!question]- 5 — Cos'è la distorsione di clipping?
> È il "taglio" della forma d'onda quando l'escursione del segnale supera la zona attiva: il transistor o satura o va in cutoff, e la sinusoide in uscita appare "tronca". Riduci l'ampiezza del segnale di ingresso.

---

# Parte B — Esercizi (prova scritta/orale su calcoli)

## Esercizio 1 — Calcolo del guadagno di tensione in CE

**Testo.** Un amplificatore CE ha: $V_{CC} = 12\ \text{V}$, $R_C = 2{,}2\ \text{k}\Omega$, $R_E = 470\ \Omega$, $R_E$ bypassata da un $C_E$ (in AC $R_E$ non c'è), $I_C = 1\ \text{mA}$, $\beta = 200$.

Calcola il guadagno di tensione ai piccoli segnali $A_v$ in banda passante.

**Soluzione:**

> [!note] Modello usato: T equivalent o $r_e$
> Useremo il modello a $r_e$ di Ebers-Moll:
> $$r_e = \frac{V_T}{I_E} \approx \frac{25\ \text{mV}}{I_E}$$

Con $I_C \approx I_E = 1\ \text{mA}$:
$$r_e = \frac{25\ \text{mV}}{1\ \text{mA}} = 25\ \Omega$$

> [!tip] Come bypass funziona
> Il condensatore $C_E$ ha impedenza $\bar{Z}_{C_E} = -j/(\omega C_E)$, che ai piccoli segnali è ≈ 0 (cortocircuito). Quindi, in AC, l'emettitore è "a massa" — $R_E$ non contribuisce al guadagno.

Guadagno (modello semplificato con $C_E$):
$$A_v \approx -\frac{R_C}{r_e} = -\frac{2200}{25} = -88$$

> [!warning] Qui manca il carico — è lecito solo perché non è dato
> La formula corretta è $A_v = -R_p/r_e$ con $R_p = R_C \parallel R_L$. In questo esercizio $R_L$ non è specificato, quindi si assume **uscita a vuoto** ($R_L \to \infty$, $R_p = R_C$) e −88 è giusto. Ma se all'esame compare un $R_L$, **usalo**: con $R_L = R_C$ il guadagno si **dimezza**.

> [!danger] Il segno meno (inversione di fase)
> Il guadagno è **negativo**: l'uscita è in **opposizione di fase** rispetto all'ingresso. È la firma del CE.

> [!check] Ordine di grandezza
> $|A_v| = 88$ è un guadagno realistico per un CE con $I_C = 1\ \text{mA}$ e $R_C = 2{,}2\ \text{k}\Omega$. CE di laboratorio hanno guadagni da 10 a 300. ✅

---

## Esercizio 2 — Calcolo dell'escursione massima

**Testo.** Un amplificatore CE con $V_{CC} = 12\ \text{V}$ ha, a riposo, $V_C = 6\ \text{V}$ (è il valore di $V_{CE}$ perché $V_E$ è vicino a massa con $C_E$). $R_C = 1\ \text{k}\Omega$.

(a) Calcola l'escursione massima picco-picco in uscita.
(b) Quanto vale l'ampiezza massima del segnale di ingresso, se $A_v = 50$?

**Soluzione:**

**(a)** Il punto di riposo è a $V_C = 6\ \text{V}$, quindi:
- **Saturazione**: $V_C$ può scendere al massimo a $V_{CE,sat} \approx 0{,}2\ \text{V}$. Escursione in basso: $6 - 0{,}2 = 5{,}8\ \text{V}$.
- **Cutoff**: $I_C = 0$, quindi $V_C$ sale fino a $V_{CC} = 12\ \text{V}$. Escursione in alto: $12 - 6 = 6\ \text{V}$.

L'escursione è limitata dal lato **saturazione**, più stretto: $5{,}8\ \text{V}$ sotto il riposo.
$$V_{out,pp,\max} = 2 \cdot \min(5{,}8, 6) = 11{,}6\ \text{V}$$

> [!warning] Limite teorico $V_{CC}$
> $V_{out,pp,\max}$ non può superare $V_{CC} = 12\ \text{V}$ (il transistor non può dare più di quanto c'è). Qui siamo a 11,6 V, appena sotto ✅.

**(b)** Con $A_v = 50$:
$$V_{in,pp,\max} = \frac{V_{out,pp,\max}}{A_v} = \frac{11{,}6}{50} = 0{,}232\ \text{V}$$

> [!tip] Nota
> Per stare in linearità senza clipping all'ingressio $V_{in,pp,\max} = 232\ \text{mV}$. Oltre questo valore l'uscita sarà clippata.

---

## Esercizio 3 — Calcolo dell'impedenza di ingresso

**Testo.** Un CE con $R_1 = 100\ \text{k}\Omega$ (alto), $R_2 = 22\ \text{k}\Omega$ (basso), $\beta = 100$, $I_C = 1\ \text{mA}$, ha $C_E$ da 100 µF (cortocircuito in AC).

Calcola $R_{in}$ (resistenza di ingresso vista tra base e massa).

**Soluzione:**

> [!note] Approssimazione con $C_E$ in corto
> Grazie al bypass di $R_E$, l'impedenza di ingresso è dominata dalla $r_\pi$:
> $$R_{in} \approx r_\pi = (\beta + 1) \cdot r_e = 101 \cdot 25 = 2525\ \Omega \approx 2{,}5\ \text{k}\Omega$$

> [!tip] Senza $C_E$
> Se non ci fosse il bypass, il contributo di $R_E$ salirebbe a:
> $$R_{in} \approx r_\pi + (\beta+1) \cdot R_E = 2525 + 101 \cdot 470 \approx 50\ \text{k}\Omega$$
>
> Il bypass abbatte l'impedenza di ingresso di un fattore ~20: perché? Perché senza bypass, il segnale su $R_E$ "ruba" tensione $v_{in}$ e quindi serve più $V_{in}$ per ottenere la stessa $V_{BE}$.

---

# Parte C — Misure in laboratorio (prova pratica Protti)

> [!success]- Misura 1 — Verifica del guadagno del CE
> 1. Monta un CE con $V_{CC} = 12\ \text{V}$, $R_C = 2{,}2\ \text{k}\Omega$, $R_E = 470\ \Omega$, $C_E = 100\ \mu\text{F}$, transistor 2N2222 o simile.
> 2. Misura con multimetro la $V_{CE}$ a riposo: deve essere ~metà di $V_{CC}$.
> 3. Applica al generatore una sinusoide a 1 kHz, ampiezza 10 mV$_{pp}$.
> 4. Misura con oscilloscopio (DC coupling) $V_{out,pp}$ su CH1 (collettore) e $V_{in,pp}$ su CH2 (base).
> 5. Calcola $A_v = V_{out,pp}/V_{in,pp}$. Deve tornare ~−80 (segno negativo: inversione di fase).
> 6. Aumenta $V_{in}$ fino a vedere il clipping: hai trovato l'escursione massima.

> [!success]- Misura 2 — Misura della $f_H$
> 1. Con lo stesso CE, tieni $V_{in,pp}$ costante (es. 10 mV$_{pp}$).
> 2. Varia la frequenza del generatore di funzioni da 100 Hz a 1 MHz.
> 3. Misura $V_{out,pp}$ a ogni frequenza.
> 4. Identifica la frequenza dove $V_{out,pp}$ scende a $0{,}707 \cdot V_{out,pp}$ di mid-band.
> 5. Quella è $f_H$ — confrontala con il valore atteso (~1–10 MHz per un 2N2222 con questa polarizzazione).

> [!success]- Misura 3 — Trigger in lab
> 1. Genera un'onda quadra rumorosa a 1 kHz.
> 2. Metti l'oscilloscopio in modalità **AUTO**: l'immagine probabilmente "salta" sullo schermo.
> 3. Passa a **NORMAL** trigger.
> 4. Regola il **LEVEL** lentamente fino a trovare il punto in cui l'immagine si stabilizza.
> 5. Verifica che cambiando lo **SLOPE** tra +/− l'immagine si blocca su fronti diversi.

---

# Parte D — Esercizio di confronto (BJT vs MOSFET amplificatore)

> [!success]- "Quando conviene un BJT, quando un MOSFET in un amplificatore a basso rumore?"
> **BJT**: minor rumore 1/f (la giunzione p-n è "pulita"); pilotaggio in corrente ma più prevedibile; guadagno in tensione ben modellizzato.
>
> **MOSFET**: impedenza di ingresso altissima (gate isolato), ma più sensibile a ESD e più rumoroso in bassa frequenza.
>
> In generale: BJT per il primo stadio di amplificatori audio di qualità; MOSFET per circuiti integrati (CMOS) e per applicazioni di potenza / switching.

---

# Esercizi aggiuntivi (edutecnica.it)

> [!tip] Esercizi interattivi e svolti
> Vai alle pagine specifiche di **[edutecnica.it](https://www.edutecnica.it/)**:
>
> | Argomento | URL | Cosa trovi |
> |---|---|---|
> | **Esercizi amplificatori a transistor** | <https://www.edutecnica.it/elettronica/ampx/ampx.htm> | Esercizi su guadagno di tensione, configurazioni CE/CC/CB, modello a piccoli segnali |
> | **Esercizi polarizzazione BJT** | <https://www.edutecnica.it/elettronica/transistorx/transistorx.htm> | Calcolo del punto di lavoro propedeutico agli amplificatori |
>
> Le pagine `ampx/*.htm` contengono spesso una selezione strutturata di esercizi (base, intermedio, cascata). Consulta l'indice interno di quella sezione per scegliere in base al livello. Per il laboratorio: alcuni esercizi sono accompagnati da "verifica con simulazione" — utile anche per la prova pratica.

---

## Esercizi svolti da Edutecnica.it (catalogo ampx)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/ampx/ampx.htm](https://www.edutecnica.it/elettronica/ampx/ampx.htm). Modello a **parametri h** per CE/CC.

### Es. A1 — CE: parametri h completi, calcolo di $A_v, A_i, R_{in}, R_o$

- **Dati**: $R_1 = 40\,\text{k}\Omega$, $R_2 = 6\,\text{k}\Omega$, $R_E = 600\,\Omega$, $R_S = 2\,\text{k}\Omega$, $R_C = 2{,}5\,\text{k}\Omega$, $R_L = 2\,\text{k}\Omega$, $h_{ie} = 1\,\text{k}\Omega$, $h_{fe} = 100$, $h_{oe} = h_{re} = 0$.
- **Trovare**: guadagno di tensione $A_v$, guadagno di corrente $A_i$, $R_{in}$, $R_o$ mid-band.
- **Soluzione edutecnica**: $A_v = -32{,}77$ · $A_i = -46{,}52$ · $R_{in} = 0{,}839\,\text{k}\Omega$ · $R_o = 2{,}5\,\text{k}\Omega$.
- **Svolgimento verificato** (formule 7.13-7.16, Mirandola pp. 342-345):
  $$R_B = R_1 \Vert R_2 = 40 \Vert 6 = 5{,}217\ \text{k}\Omega$$
  $$R_{in} = R_B \Vert h_{ie} = 5{,}217 \Vert 1 = \mathbf{0{,}839\ k\Omega}\ ✔ \qquad R_p = R_C \Vert R_L = 2{,}5 \Vert 2 = 1{,}111\ \text{k}\Omega$$
  $$G_i = \frac{R_{in}}{h_{ie}}\,h_{fe}\,\frac{R_p}{R_L} = 0{,}839 \cdot 100 \cdot \frac{1{,}111}{2} = \mathbf{46{,}6}\ (\text{ed. } 46{,}52)\ ✔ \qquad R_o = R_C = \mathbf{2{,}5\ k\Omega}\ ✔$$

> [!danger] La formula che era scritta qui non dà il risultato dichiarato accanto
> La nota riportava «$A_v \approx -g_m(R_C \parallel R_L)$», che vale
> $$G_v = -h_{fe}\frac{R_p}{h_{ie}} = -100 \cdot \frac{1111}{1000} = -111$$
> cioè **−111, non −32,77**. La formula non era sbagliata: era **incompleta**, e nessuno aveva verificato che producesse il numero stampato di fianco.
>
> I −32,77 di edutecnica includono l'**attenuazione del partitore d'ingresso** formato da $R_S = 2$ k$\Omega$ e $R_{in} = 0{,}839$ k$\Omega$:
> $$\frac{v_i}{v_s} = \frac{R_{in}}{R_S + R_{in}} = \frac{0{,}839}{2{,}839} = 0{,}2955 \quad\Longrightarrow\quad G_{v,\text{tot}} = -111 \cdot 0{,}2955 = \mathbf{-32{,}8}\ ✔$$
>
> **edutecnica è corretta.** Qui $R_S$ è più del doppio di $R_{in}$: si perde il **70%** del segnale prima ancora di entrare nel transistor. Chiediti sempre se ti è chiesto $v_o/v_i$ (guadagno dello **stadio**) o $v_o/v_s$ (guadagno dell'**amplificatore**): con questi dati differiscono di 3,4 volte. Vedi [[Amplificatori a BJT#Le quattro formule dell'amplificatore CE (pp. 342-345)]].

### Es. A2 — CE con $V_{BB}$ e $V_{CC}$

- **Dati**: $V_{CC}=20\text{ V}$, $V_{BB}=2\text{ V}$, $R_B=13\,\text{k}\Omega$, $R_C=1\,\text{k}\Omega$, $\beta=100$, $V_{BE}=0{,}7\text{ V}$, $h_{ie}=1{,}5\,\text{k}\Omega$, $h_{fe}=130$.
- **Soluzione**: $I_B = (2-0{,}7)/13\,\text{k} = 0{,}1\,\text{mA}$; $I_C = 13\,\text{mA}$; **$V_{CE}=10\text{ V}$**; **$A_v = -8{,}96$**.

### Es. A3 — Collettore comune (emitter follower)

- **Dati**: $R_S=600\,\Omega$, $R_1=33\,\text{k}$, $R_2=47\,\text{k}$, $R_E=2\,\text{k}$, $R_L=500\,\Omega$, $h_{ie}=1{,}3\,\text{k}$, $h_{fe}=140$.
- **Soluzione edutecnica**: $A_v = 0{,}98$ (tipico del follower!).
- **Note**: la $A_v$ è sempre < 1 ma prossima a 1. L'alto guadagno di corrente ($A_i$ grande) è ciò che rende utile il CC come buffer.

### Es. A4 — CE con $h_{oe} \neq 0$

- **Dati**: $R_C = 2\,\text{k}$, $R_1 = 60\,\text{k}$, $R_2 = 8\,\text{k}$, $R_S = 1\,\text{k}$, $R_L = 2\,\text{k}$, $h_{fe} = 100$, **$h_{oe} = 0{,}1\text{ mS}$**, $h_{ie} = 1\,\text{k}$.
- **Soluzione edutecnica**: $A_v = -42{,}77$ · $A_i = -40{,}2$ · $R_{in} = 0{,}88\,\text{k}\Omega$ · $R_o = 1{,}67\,\text{k}\Omega$.
- **Nota**: $h_{oe}$ NON trascurabile: $R_o = R_C \parallel 1/h_{oe} = 2\,\text{k} \parallel 10\,\text{k} = 1{,}67\,\text{k}\Omega$. Confronto: con $h_{oe}=0$ si avrebbe $R_o = R_C = 2\,\text{k}\Omega$.

### Es. A5 — Amplificatore in cascata (2 stadi CE)

- **Dati**: $h_{ie}=4\,\text{k}$, $h_{fe}=120$, $h_{oe}=0{,}05\text{ mS}$, $R_{1,3}=40\,\text{k}$, $R_{2,4}=5\,\text{k}$, $R_{C1,2}=2\,\text{k}$, $R_{E1,2}=400\,\Omega$, $R_S=R_L=2\,\text{k}$.
- **Soluzione edutecnica**: $A_{v,\text{tot}} = 430{,}24$.
- **Procedura**: $A_{v,\text{tot}} = A_{v1} \cdot A_{v2}$ con effetto di carico del 2° stadio sul 1° tramite $R_{in2}$.

### Pattern di errore frequenti (Carli scritta)

1. **Confondere $A_v$ con $|A_v|$**: in CE il segno è negativo. Nei calcoli di potenza si usa sempre $|A_v|$.
2. **Dimenticare l'effetto di carico**: $R_L$ va in parallelo a $R_C$ nel calcolo di $A_v$. Errore: usare solo $R_C$, sovrastimare $A_v$ di un fattore 2.
3. **Confondere CE e CC**: in CC l'uscita è sull'emettitore, in CE sul collettore. Se l'esercizio chiede emitter follower, sbagli se calcoli guadagno di tensione.
