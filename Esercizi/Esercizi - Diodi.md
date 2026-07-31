---
tags: [recupero, elettronica, diodi, esercizi, scritta, pratica]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ (2026-07-19) — coerente con Mirandola Vol.2, Cap. 5 «I diodi», pp. 192-233. Esercizi 1-2 del vault ricalcolati e confermati; corretto un errore dimensionale in Es. 2(c) (P_D). Esercizi edutecnica Z2 e Z9 ricalcolati e confermati; Z3 segnalato come non ricostruibile senza schema. Vedi [[Prove/00 - Audit e correzioni]]."
prove: [scritta, orale, pratica]
---

# Esercizi — Diodi

Teoria di riferimento: [[Diodi]]

> [!tip] Come usare questa pagina
> Gli esercizi seguenti coprono i tre livelli: analisi di circuiti con diodo (scritta), ragionamenti sul funzionamento (orale), misure in laboratorio (pratica). Chiudi ogni esercizio con un **controllo di plausibilità** — è la trappola che il libro di testo tende a non dichiarare esplicitamente.

---

# Parte A — Quesiti (prova orale)

> [!important] I quesiti veri stanno altrove
> I 5 quesiti qui sotto sono **ricostruiti**. Le domande che Carli ha davvero posto sui diodi — **39, da due verifiche alla classe 4E** — sono trascritte e risposte in **[[04 - Verifica tipo Carli — Diodi]]**. Se hai poco tempo, parti da lì: questa Parte A è un supplemento, non il banco di prova.

> [!question]- 1 — Cos'è la barriera di potenziale in una giunzione p-n?
> È il campo elettrico interno che si crea nella zona di contatto tra le regioni **p** ed **n**. Senza polarizzazione esterna, impedisce ai portatori di attraversare la giunzione (corrisponde a ~0,7 V per il silicio, ~0,3 V per il germanio). Viene superata applicando una tensione esterna in polarizzazione diretta che la "abbassa" di una quantità pari a $V_D$ — quando $V_D \geq V_\gamma$, il diodo conduce.

> [!question]- 2 — Cosa succede a un diodo quando la tensione inversa supera $V_{BR}$?
> Il diodo entra nella zona di **breakdown**. In un diodo normale questo è distruttivo (la corrente cresce illimitatamente fino a bruciare il componente). In un diodo **Zener** è il funzionamento normale: la tensione si stabilizza a $-V_Z$.

> [!question]- 3 — Perché in un ponte di Graetz servono 4 diodi e non 2?
> Per garantire che la corrente di carico scorra sempre nello stesso verso sul carico, **indipendentemente** dal segno di $v_{in}$. Con 2 diodi (semplice semionda) si rettifica solo una semisonde.

> [!question]- 4 — Perché serve il condensatore di filtro in un alimentatore?
> Per livellare la tensione pulsante del raddrizzatore. Il condensatore si carica al valore di picco, poi si scarica lentamente attraverso il carico. La tensione di uscita diventa quasi continua, con un piccolo ripple la cui ampiezza è $V_{ripple,pp} \approx I_{load}/(f_r \cdot C)$.

> [!question]- 5 — Cosa si intende per "approssimazione a 0,7 V"?
> Un modello che semplifica l'analisi: il diodo diretto si sostituisce con un **generatore di tensione** di valore $V_\gamma = 0{,}7\ \text{V}$. Permette di calcolare tensioni e correnti in modo accurato per circuiti a bassa potenza.

---

# Parte B — Esercizi (prova scritta)

## Esercizio 1 — Stabilizzatore Zener

**Testo.** Un alimentatore fornisce $V_{in} = 15\ \text{V}$ con resistenza di sorgente $R_S = 220\ \Omega$. Vuoi alimentare un carico che assorbe $I_L = 20\ \text{mA}$ a $V_{out} = 5\ \text{V}$. Disponi di uno Zener da $V_Z = 5{,}1\ \text{V}$ con $P_{Z,\max} = 1\ \text{W}$.

(a) Calcola la corrente che attraversa lo Zener e verifica che sia nel range di sicurezza.
(b) Calcola la potenza dissipata dallo Zener.

**Soluzione:**

**(a)** La corrente che attraversa $R_S$:
$$I_S = \frac{V_{in} - V_Z}{R_S} = \frac{15 - 5{,}1}{220} = 45\ \text{mA}$$

La corrente che va nel carico è $I_L = 20\ \text{mA}$. Quindi:
$$I_Z = I_S - I_L = 45 - 20 = 25\ \text{mA}$$

Range operativo: il minimo assoluto per restare in breakdown è $I_{ZK} \approx 1\ \text{mA}$; in progetto ci si tiene sopra $I_{ZT} \approx 5\ \text{mA}$ (corrente di test, dove la $V_Z$ è più stabile). Vedi [[Diodi#4. Il diodo Zener]].
Massima ammessa: $I_{Z,\max} = P_{Z,\max}/V_Z = 1000/5{,}1 \approx 196\ \text{mA}$.

$5\ \text{mA} < 25\ \text{mA} < 196\ \text{mA}$ ✅ — il circuito funziona.

**(b)** $P_Z = V_Z \cdot I_Z = 5{,}1 \cdot 25 = 127{,}5\ \text{mW}$.

Verifica: $127{,}5\ \text{mW} \ll 1\ \text{W}$ ✅.

> [!check] Controllo di plausibilità
> La tensione di uscita è praticamente $V_Z = 5{,}1\ \text{V}$, indipendente da $V_{in}$ e $I_L$ (entro i limiti operativi). Se la misuri con un multimetro e leggi 5,1 V → circuito OK. Se leggi 15 V → c'è un guasto (R_S bruciata o Zener in corto o circuito aperto).

---

## Esercizio 2 — Raddrizzatore a semionda con filtro

**Testo.** Un raddrizzatore a semionda è alimentato da $v_{in}(t) = 24 \sin(2\pi \cdot 50\ t)\ \text{V}$. Il diodo ha $V_D = 0{,}7\ \text{V}$. Il carico è $R_L = 1\ \text{k}\Omega$. È presente un condensatore di filtro $C = 1000\ \mu\text{F}$.

(a) Calcola la tensione di uscita approssimata (DC).
(b) Calcola il ripple picco-picco.
(c) Calcola la potenza dissipata dal diodo.

**Soluzione:**

**(a)** La tensione al picco, **prima** del diodo è 24 V. **Dopo** il diodo, la tensione di picco è:
$$V_{p} = V_{in,p} - V_D = 24 - 0{,}7 = 23{,}3\ \text{V}$$

Con il condensatore, la tensione si mantiene approssimativamente al valore di picco durante l'intervallo tra i picchi consecutivi:
$$V_{DC} \approx 23{,}3\ \text{V}$$

> [!warning] Nota: a semionda la $V_{DC}$ è vicina al picco
> A differenza del ponte, qui la tensione decade significativamente tra un picco e il successivo (la pausa è di mezzo periodo). Per questo il ripple è **maggiore** rispetto al ponte.

**(b)** La frequenza di ripple per un raddrizzatore a **semionda** è $f_r = f_{line} = 50\ \text{Hz}$. Per un ponte di Graetz sarebbe $f_r = 2f_{line} = 100\ \text{Hz}$.

La corrente di carico:
$$I_{load} = \frac{V_{DC}}{R_L} = \frac{23{,}3}{1000} = 23{,}3\ \text{mA}$$

Il ripple:
$$V_{ripple,pp} = \frac{I_{load}}{f_r \cdot C} = \frac{23{,}3 \cdot 10^{-3}}{50 \cdot 1000 \cdot 10^{-6}} = \frac{0{,}0233}{0{,}05} = 0{,}466\ \text{V}$$

**(c)** Il diodo conduce solo nel breve intervallo in cui $v_{in}$ supera la tensione già presente sul condensatore: in quegli istanti la corrente di picco è **alta**, ma dura **poco**.

Per la **potenza media** non serve conoscere né il picco né la durata, grazie a un ragionamento di conservazione della carica: **tutta** la carica che il carico consuma in un periodo deve passare per il diodo (è l'unica via). Quindi la corrente **media** nel diodo è uguale alla corrente media di carico:

$$\overline{I_D} = \overline{I_{load}} = 23{,}3\ \text{mA}$$

e poiché quando conduce il diodo ha ai capi $V_D \approx 0{,}7$ V:

$$P_D \approx V_D \cdot \overline{I_D} = 0{,}7 \cdot 23{,}3\ \text{mA} = \mathbf{16{,}3\ mW}$$

> [!warning] Errore corretto il 2026-07-19
> La versione precedente scriveva $P_D \approx \frac{1}{2}V_D \cdot 0{,}466$, moltiplicando $V_D$ per il **ripple** (che è una **tensione**): volt × volt **non** è una potenza. Il risultato "decine di mW" era casualmente nell'ordine giusto, ma la formula era dimensionalmente sbagliata — all'orale è il tipo di passaggio che Carli può smontare in una domanda.

> [!tip] Nota pratica
> Il diodo di un raddrizzatore a semionda deve dissipare **la corrente di carico** durante la breve conduzione, quindi è più sollecitato di un diodo di un ponte di Graetz (dove la corrente è distribuita su due diodi alternati).

---

# Parte C — Misure in laboratorio (prova pratica Protti)

> [!success]- Misura 1 — Verifica del raddrizzatore a ponte
> 1. Monta il ponte di Graetz con 4 diodi (1N4007 o equivalenti) e un carico resistivo da 1 kΩ.
> 2. Collega l'oscilloscopio in **DC coupling** all'uscita.
> 3. Misura $V_{in,p}$ all'ingresso (CH1) e $V_{out}$ all'uscita (CH2).
> 4. Verifica che $|V_{out,p}| \approx V_{in,p} - 2V_D$ (ca. 1,4 V in meno).
> 5. Aggiungi un condensatore da 1000 µF all'uscita. Misura il ripple $V_{ripple,pp}$.

> [!success]- Misura 2 — Verifica dello stabilizzatore Zener
> 1. Prendi un alimentatore da banco, regolalo a 15 V.
> 2. Collegalo allo stabilizzatore Zener ($R_S = 220\ \Omega$, Zener 5,1 V).
> 3. Misura con il multimetro la tensione di uscita: deve essere ~5,1 V.
> 4. Varia la tensione di alimentazione da 10 V a 20 V: la tensione di uscita deve restare ~5,1 V (la "stabilizzazione" funziona).
> 5. Collega un carico variabile: la tensione deve restare stabile finché $I_Z$ resta nel range operativo.

---

# Esercizi aggiuntivi (edutecnica.it)

> [!tip] Esercizi interattivi e svolti
> La piattaforma **[edutecnica.it](https://www.edutecnica.it/)** offre esercizi svolti e strumenti di calcolo. Per i diodi, le pagine di riferimento sono:
>
> | Argomento | URL | Cosa trovi |
> |---|---|---|
> | **Esercizi sui diodi** (clipper, raddrizzatori) | <https://www.edutecnica.it/elettronica/diodox/diodox.htm> | Raccolta di esercizi su stati di conduzione/interdizione in circuiti vari |
> | **Esercizi sui diodi Zener** | <https://www.edutecnica.it/elettronica/zenerx/zenerx.htm> | Raccolta di esercizi di stabilizzatori di tensione |
>
> In particolare, sono presenti esercizi su circuiti con onde triangolari/sinusoidali (clipper) e analisi di stabilizzatori con carico variabile — vedi la pagina del sito per l'indice aggiornato.

---

## Esercizi svolti da Edutecnica.it — Catalogo diodox (10 es.)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/diodox/diodox.htm](https://www.edutecnica.it/elettronica/diodox/diodox.htm). Limiter, circuiti con diodi, modello ideale/reale.

### Es. DD1 — Resistenza equivalente morsetti A-B

- **Dati**: $R_1=R_3=1\,\text{k}$, $R_2=2\,\text{k}$, diodi in configurazione ponte.
- **Soluzione edutecnica**: $R_{AB} = 3\,\text{k}\Omega$ per $V>0$ (tutti diodi on), $R_{AB} = 1\,\text{k}\Omega$ per $V<0$.

### Es. DD5 — Circuito con diodo: trovare $v_o$

- **Dati**: $V_\gamma = 0{,}5$ V, $r_D = 50\,\Omega$, $R_L = 500\,\Omega$, $v_i = 5/6/2$ V.
- **Soluzione edutecnica**:
  - $v_o(5\text{V}) = 4{,}1$ V
  - $v_o(6\text{V}) = 5$ V (saturazione!)
  - $v_o(2\text{V}) = 1{,}36$ V
- **Modello**: diodo ON se $v_i > V_\gamma + r_D \cdot I_D$, con $I_D = (v_i - V_\gamma)/(r_D + R_L)$.

### Es. DD6 — Onda uscita (input triangolare)

- **Dati**: $V_\gamma = 0{,}5$ V, $r_D = 0$, input triangolare $\pm 15$ V.
- **Procedura**: per $v_i > 0$: $v_o = v_i - V_\gamma = v_i - 0{,}5$ V; per $v_i < 0$: $v_o = 0$ (diodo inverso, off).

### Es. DD8 — Diodo polarizzato (rivelatore di inviluppo)

- **Dati**: $E = 9$ V, $R = 6\,\text{k}\Omega$, $R_L = 3\,\text{k}$, $V_\gamma = 0{,}5$ V, $r_D = 0$, input seno 6 V.
- **Comportamento**: il diodo si accende solo durante le semionde positive quando $v_i > 9 + V_\gamma$ (eccesso). Nelle negative, scarica attraverso $R_L$.

### Es. DD10 — Simile a Es. DD5

- **Dati**: $V_\gamma = 0{,}6$ V, $r_D = 40\,\Omega$, $R_L = 500\,\Omega$, $v_i = 5/6/2$ V.
- **Soluzioni**: $v_o(5\text{V}) = 4{,}07$ V; $v_o(6\text{V}) = 5$ V; $v_o(2\text{V}) = 1{,}29$ V.

## Esercizi svolti da Edutecnica.it — Catalogo zenerx (10 es.)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/zenerx/zenerx.htm](https://www.edutecnica.it/elettronica/zenerx/zenerx.htm). Stabilizzatori a diodo Zener.

### Es. Z1 — Calcolo $i$ ed $E$ (stabilizzatore)

- **Dati**: $V_Z = 5$ V, $V_R = 18$ V (caduta su $R$), $r_D = 5\,\Omega$, $R = 3\,\text{k}$.
- **Soluzione edutecnica**: $i = 6$ mA, $E = 23$ V.
- **Svolgimento**: $V_E = V_R + V_Z = 18 + 5 = 23$ V. $i = V_R/R = 18/3\text{k} = 6$ mA.

### Es. Z2 — Calcolo $i$ ed $R$

- **Dati**: $E = 18$ V, $V_Z = 5$ V, $V_R = 12{,}5$ V, $r_D = 8\,\Omega$.
- **Soluzione edutecnica**: $i = 62{,}5$ mA, $R = 200\,\Omega$.
- **Svolgimento** (verificato 2026-07-19): la maglia contiene $R$ in serie allo Zener reale ($V_Z$ + $r_D$), quindi
  $$i = \frac{E - V_Z}{R + r_D} = \frac{18 - 5}{200 + 8} = \frac{13}{208} = 62{,}5\ \text{mA}$$
  da cui $V_R = i \cdot R = 0{,}0625 \cdot 200 = 12{,}5$ V ✔ e la tensione sul ramo Zener vale $V_Z + i\,r_D = 5 + 0{,}5 = 5{,}5$ V (infatti $12{,}5 + 5{,}5 = 18 = E$ ✔).
- ⚠️ **Errore da non ripetere**: $i \ne V_R/r_D$. La $r_D$ è la resistenza **differenziale interna dello Zener**, non il componente su cui cade $V_R$: quella è $R$. Confonderle dà 1,56 A invece di 62,5 mA (fattore 25).

### Es. Z3 — Calcolo correnti (2 Zener)

- **Dati**: $V_{CC} = 24$ V, $V_{DD} = 6$ V, $R_1 = 1\,\text{k}$, $R_2 = 3\,\text{k}$, $i_2 = 5$ mA.
- **Soluzione edutecnica**: $i_1 = 10$ mA, $i_{Z2} = 5$ mA.
- **Dato mancante recuperato dalla fonte**: $V_{Z1} = 5$ V.
- ⚠️ **Esercizio NON ricostruibile senza lo schema** (verificato 2026-07-19): serve sapere come sono collegati i due Zener. Le ipotesi semplici non tornano — se il nodo su $R_1$ fosse a $V_{Z1}=5$ V si avrebbe $i_1=(24-5)/1\text{k}=19$ mA, se fosse a $V_{DD}=6$ V si avrebbe 18 mA; la fonte dichiara **10 mA**, che richiede una caduta di 10 V su $R_1$ (nodo a 14 V) — compatibile solo con una configurazione a più Zener in serie.
- 👉 **Cosa fare**: apri lo schema su [zenerx.htm](https://www.edutecnica.it/elettronica/zenerx/zenerx.htm) prima di usare questo esercizio. *(La versione precedente di questa nota concludeva "probabile typo di edutecnica": conclusione non giustificata, rimossa.)*

### Es. Z4 — Calcolo correnti (più elementi)

- **Dati**: $R = 10\,\text{k}$, $R_1 = 2\,\text{k}$, $R_2 = 3\,\text{k}$, $V_{CC} = 15$ V, $V_{DD} = 18$ V, $V_{Z1} = 5$ V, $V_{Z2} = 7{,}5$ V.
- **Soluzione edutecnica**: $i_1 = 5$ mA, $i_2 = 3{,}5$ mA, $i = 0{,}55$ mA, $i_{Z1} = 5{,}55$ mA, $i_{Z2} = 4{,}05$ mA.

### Es. Z5 — Schema con $R_1, R_2$, partenza da alimentazione

- **Dati**: $V_{CC} = 18$ V, $V_{DD} = 24$ V, $R_1 = 5\,\text{k}$, $R_2 = 2\,\text{k}$.
- **Soluzione**: $i_1 = 2{,}24$ mA, $i_2 = 11{,}65$ mA, $i_{Z2} = 9{,}41$ mA.

### Es. Z6 — Analisi Zener + potenziometro

- **Dati**: $i_1 = 2$ mA, $R_p = 100\,\text{k}$, $R_1 = 3\,\text{k}$, $R_2 = 2\,\text{k}$.
- **Soluzione edutecnica**: $V_{Z1} = V_{Z2} = 6$ V, $i_2 = 2$ mA.

### Es. Z7 — Stabilità ($V_o$ range, $i_Z$ range)

- **Dati**: $V_Z = 8$ V, $r_D = 6\,\Omega$, $R = 200\,\Omega$, $i_{Z\max} = 60$ mA.
- **Soluzione**: $V_o$ range $8{,}02 - 8{,}17$ V, $i_Z$ range $4{,}8 - 29{,}1$ mA.

### Es. Z8 — $V_o$ max/min

- **Dati**: $V_Z = 8$ V, $r_D = 6\,\Omega$, $R = 200\,\Omega$, $V_i = 15$ V, $i_L = 0 - 50$ mA.
- **Soluzione**: $v_o = 8{,}02 - 8{,}2$ V, $i_Z = 4 - 33$ mA.

### Es. Z9 — $V_o, i_L, P_Z$

- **Dati**: $V_Z = 5$ V, $r_D = 20\,\Omega$, $R = 50\,\Omega$, $V_i = 12$ V, $R_L = 250/500\,\Omega$.
- **Soluzione**: $v_o = 6{,}62$ V, $i_L = 26{,}5$ mA, $P_Z = 536$ mW.
- **Svolgimento** (ricalcolato e confermato 2026-07-19): non serve indovinare la $i$ — si scrive il **bilancio delle correnti al nodo d'uscita**. Lo Zener reale è $V_Z$ in serie a $r_D$, in parallelo a $R_L$:
  $$\frac{V_i - v_o}{R} = \frac{v_o - V_Z}{r_D} + \frac{v_o}{R_L} \quad\Rightarrow\quad \frac{12 - v_o}{50} = \frac{v_o - 5}{20} + \frac{v_o}{250}$$
  Moltiplicando per 500: $10(12-v_o) = 25(v_o-5) + 2v_o \Rightarrow 245 = 37\,v_o \Rightarrow \boxed{v_o = 6{,}62\ \text{V}}$
  $$i_L = \frac{v_o}{R_L} = \frac{6{,}62}{250} = 26{,}5\ \text{mA} \qquad i_Z = \frac{v_o - V_Z}{r_D} = \frac{1{,}62}{20} = 81{,}1\ \text{mA}$$
  $$P_Z = v_o \cdot i_Z = 6{,}62 \cdot 0{,}0811 = 0{,}537\ \text{W} \approx 536\ \text{mW} \ ✔$$
- 💡 **Il punto didattico**: con $r_D$ **non trascurabile** ($20\,\Omega$ contro $R=50\,\Omega$!) la tensione stabilizzata **non** è $V_Z$: qui è 6,62 V invece di 5 V, cioè **il 32% in più**. Lo Zener "tiene" bene solo se $r_D \ll R$. *(La versione precedente segnalava una "discrepanza": non c'era, mancava solo il bilancio al nodo.)*

### Es. Z10 — Range di $R$ per stabilizzazione

- **Dati**: $V_Z = 10$ V, $i_{Z\min} = 5$ mA, $i_{Z\max} = 80$ mA, $V_i = 20 - 25$ V.
- **Soluzione edutecnica**: $R = 150 - 222\,\Omega$, $P_R = 0{,}68 - 2{,}22$ W.

## Pattern di errore frequenti (Carli orale + Protti pratica)

1. **Dimenticare $r_D$**: il diodo Zener reale ha $r_D \neq 0$. La $V_o$ esatta è $V_Z + i_Z \cdot r_D$, non solo $V_Z$.
2. **Confondere $i_L$ e $i_Z$**: $i_R = i_Z + i_L$. Errore: usare solo $i_L$ per dimensionare $R$.
3. **Stabilità**: per essere in **regolazione**, serve $i_Z > i_{Z\min}$. Errore: dimensionare $R$ che porta $i_Z$ sotto $i_{Z\min}$.
