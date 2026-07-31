---
tags: [recupero, elettronica, amplificatori, bjt, piccolo-segnale]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-19) — Mirandola Vol.2, Cap. 7 «Gli amplificatori a transistor», pp. 312-351 (pagg.-PDF 95-114). ATTENZIONE: è il Cap. 7, NON il 6 (il Cap. 6 è sugli amplificatori operazionali). Conversione: pagina stampata = (pagina-PDF − 95)·2 + 312. Mappa sezioni di questo file: §2.1 amplificatore «didattico» a emettitore comune FIG. 17-19 pp. 332-333 · rumore, rapporto S/N e figura di rumore p. 336 · risposta in ampiezza e banda passante FIG. 21 p. 336 · §2.2 L'amplificatore a emettitore comune FIG. 22 (A: polarizzazione; B: schema completo con accoppiamento e by-pass) p. 336 · condensatori d'accoppiamento e di by-pass, FIG. 23 ed ESEMPIO 7 pp. 336-337 · circuito dinamico FIG. 24 pp. 338-339 · quadripolo e parametri ibridi h FIG. 26-27, sistema 7.12, pp. 340-341 · FIG. 28-29 e parametri dell'amplificatore: R_i (7.13), G_i (7.14), G_v (7.15), R_o = R_C (7.16), pp. 342-345 · TABELLA 1 di progetto ed ESEMPIO 12 p. 346 · §2.3 collettore comune (inseguitore) FIG. 30-31 pp. 347-349 · base comune FIG. 33 pp. 350-351 · amplificatori multistadio pp. 351+."
prove: [orale, pratica]
---

# Amplificatori a BJT

> [!info] Dove serve
> **Orale** (Carli): amplificatori a BJT nel colloquio teorico. **Pratica** (Protti): «amplificatori a BJT (con misure all'oscilloscopio)». È l'applicazione del BJT che ha senso di studiare — la polarizzazione senza un amplificatore è un esercizio scolastico, un amplificatore è il transistor "al lavoro".

Prerequisiti: [[BJT]], [[Impedenza dei bipoli R, L, C]].

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §11**.

## 1. Che cos'è un amplificatore

Un **amplificatore** è un sistema che, dato un segnale di ingresso $v_{in}(t)$ di piccola ampiezza, fornisce in uscita $v_{out}(t)$ con **ampiezza maggiore** (guadagno $|A_v| > 1$) e, idealmente, **stessa forma d'onda**.

Il segnale amplificato è fornito da una **sorgente di energia esterna** (l'alimentazione $V_{CC}$): il transistor è solo il "rubinetto" che dosa l'energia dell'alimentazione in funzione del segnale di ingresso.

> [!tip] Il senso della frase "il transistor è pilotato in corrente"
> Non è il BJT che "crea" energia. È l'alimentazione $V_{CC}$ che fornisce l'energia; il BJT, tramite la piccola $I_B$, decide quanto dell'energia dell'alimentazione può fluire nel carico. Il segnale di ingresso non fa altro che **modulare** questa corrente.

---

## 2. Le tre configurazioni fondamentali

Ogni amplificatore a BJT ha una "regola pratica": si sceglie quale terminale è **comune** all'ingresso e all'uscita. Da qui il nome.

| Configurazione | Terminale comune | Applicazione tipica |
|---|---|---|
| **Emettitore comune** (CE) | Emettitore | Amplificazione di tensione — la più usata |
| **Collettore comune** (CC, *emitter follower*) | Collettore | Buffer, adattatore di impedenza ($A_v \approx 1$) |
| **Base comune** (CB) | Base | Alta frequenza, applicazioni RF |

### 2.1 Emettitore comune (CE)

> Amplificatore a BJT a emettitore comune — **Mirandola Cap. 7 §2.2, p. 336, FIGURA 22**. **A)** circuito di polarizzazione e stabilizzazione (è lo stesso della FIGURA 14, vedi [[BJT]]); **B)** schema **completo**, con i condensatori d'accoppiamento e di by-pass:
>
> ![[libro-cap7-p336-fig22-amplificatore-ce-completo.png]]
>
> Il libro costruisce l'amplificatore proprio così: «si può realizzare **completando** il circuito di polarizzazione e stabilizzazione del BJT con i condensatori d'accoppiamento e di by-pass». La rete DC non cambia — si aggiungono solo i condensatori.

> [!tip] I tre condensatori, e perché ce ne vogliono tre
> - **$C_i$, $C_o$ (accoppiamento)**: «consentono di isolare lo stadio amplificatore dal punto di vista della **continua**, e quindi di non alterare i valori di polarizzazione, una volta collegati i circuiti a monte e a valle» (p. 336). Con $X_C = 1/(2\pi f C)$, sono **infiniti in continua** ($f=0$) e trascurabili in banda: insieme a $R_i$ e $R_L$ formano due **filtri passa-alto** di taglio $f_t = 1/(2\pi RC)$.
> - **$C_E$ (by-pass)**: il parallelo $R_E \Vert C_E$ **separa le due componenti** di $i_E = I_E + i_e$: la continua $I_E$ passa in $R_E$ (dove $C_E$ è una reattanza infinita), il segnale $i_e$ passa in $C_E$, scavalcando $R_E$.
>
> **Il punto**: $R_E$ serve a stabilizzare il punto di lavoro, ma «lo stesso effetto si avrebbe sul segnale, annullando o riducendo l'amplificazione». Il by-pass «consente di far vedere $R_E$ alla **continua** ma non al **segnale**, in modo da non abbassare il guadagno in tensione» (p. 337). È il classico trade-off risolto con un condensatore.
>
> Dimensionamento: si impone $X_{CE} = \dfrac{1}{2\pi f_{\min} C_E} \ll R_E$, dove «molto minore» significa un rapporto di **almeno 10**.
>
> *ESEMPIO 7 del libro (p. 337)*: $R_E = 560\ \Omega$, banda audio da 20 Hz → $C_E \ge \dfrac{10}{2\pi f_i R_E} = \dfrac{10}{2\pi \cdot 20 \cdot 560} = 142\ \mu\text{F}$.

La maglia di uscita contiene $V_{CC}$, $R_C$ e la $V_{CE}$ del transistor. Il segnale di ingresso è applicato alla **base**; il segnale di uscita è prelevato al **collettore**.

**Punto di lavoro (DC):**
$$V_{BB} \approx V_{CC} \cdot \frac{R_2}{R_1 + R_2} \quad \text{(se il partitore è ben dimensionato)}$$
$$I_B = \frac{V_{BB} - V_{BE}}{R_B} \approx \frac{V_{BB} - 0{,}7}{R_B}$$
$$I_C = \beta I_B \qquad V_{CE} = V_{CC} - I_C R_C$$

> [!tip] "Punto di lavoro a metà" — ma metà di cosa, esattamente
> La regola pratica è che il transistor amplifica senza clippare se $V_{CE}$ sta **a metà dell'escursione disponibile**. Attenzione però: con la $R_E$ presente, il criterio esatto di Mirandola (formula **7.9**, p. 329) **non** è $V_{CE} = V_{CC}/2$ ma
> $$V_{RC} = V_{CEQ} = \frac{V_{CC} - V_{RE}}{2} \qquad\text{con } V_{RE} = V_{CC}/10$$
> cioè $V_{CEQ} = 0{,}45\,V_{CC}$: la caduta su $R_E$ va tolta *prima* di dividere per due. Con $V_{CC} = 12$ V si ha $V_{CEQ} = 5{,}4$ V, non 6 V.
>
> E il criterio non serve solo alla dinamica: il libro precisa che così «si evitano fenomeni di **fuga termica**». Dettagli e procedura completa in [[BJT#Il dimensionamento completo (formule 7.8-7.11, pp. 328-329)]].

**Funzionamento in AC (piccolo segnale):**

Il segnale $\Delta v_{in} = v_{in} - V_{BB}$ si sovrappone al punto di lavoro. Si comporta come una piccola variazione di $V_{BE}$, che produce una variazione di $I_C$ che si traduce in una variazione di $V_{CE}$ (segnale di uscita).

**Guadagno di tensione ai piccoli segnali (in banda passante):**

Mirandola lo ricava con i **parametri ibridi** (formula **7.15**, p. 344):

$$\boxed{G_v = \frac{v_o}{v_i} = -\,h_{fe}\,\frac{R_p}{h_{ie}}} \qquad \text{con } R_p = R_C \parallel R_L$$

> [!danger] Due errori che erano in questa nota — leggi prima di usare la formula
> Una versione precedente riportava $A_v = -\dfrac{R_C}{r_e + R_E/(\beta+1)}$. **Sbagliata due volte:**
>
> 1. **La divisione per $(\beta+1)$ non esiste.** Riportare $R_E$ dall'emettitore alla base la *moltiplica* per $(\beta+1)$, non la divide. Nel guadagno, $R_E$ compare invece **così com'è**, in serie a $r_e$ (le due resistenze sono entrambe viste dall'emettitore).
> 2. **Manca il carico.** Al numeratore non va $R_C$ ma il **parallelo** $R_p = R_C \parallel R_L$: il segnale d'uscita vede la resistenza di collettore *e* il carico. Trascurare $R_L$ sovrastima il guadagno, anche di parecchio.
>
> Le forme corrette, a seconda che $R_E$ sia by-passata o no:
> $$\text{con } C_E:\quad G_v \approx -\frac{R_p}{r_e} \qquad\qquad \text{senza } C_E:\quad G_v \approx -\frac{R_p}{r_e + R_E}$$

**Ponte fra le due notazioni** (il libro usa $h$, molti eserciziari usano $r_e$):

$$h_{ie} = (\beta+1)\,r_e \approx \beta\, r_e \qquad h_{fe} = \beta$$

da cui $-h_{fe}R_p/h_{ie} = -\beta R_p/(\beta r_e) = -R_p/r_e$: **le due scritture sono la stessa formula**. Qui $r_e = V_T/I_E$ è la resistenza differenziale d'emettitore, con $V_T \approx 26$ mV a temperatura ambiente (spesso arrotondata a 25 mV — usa un valore solo e sii coerente).

> [!warning] Il guadagno dell'**amplificatore** è minore di quello dello **stadio**
> La 7.15 dà il guadagno del BJT. Il guadagno visto dal generatore è più basso, perché $R_G$ e $R_i$ formano un **partitore d'ingresso** che attenua (p. 344):
> $$\frac{v_i}{v_s} = \frac{R_i}{R_G + R_i} \qquad\Longrightarrow\qquad G_{v,\text{tot}} = -\,h_{fe}\frac{R_p}{h_{ie}} \cdot \frac{R_i}{R_G+R_i}$$
>
> *ESEMPIO del libro (p. 344, FIGURA 29)*: con $h_{ie}=3$ k$\Omega$, $h_{fe}=100$, $R_p=920\ \Omega$, $R_i=1{,}4$ k$\Omega$, $R_G=330\ \Omega$:
> $$G_v = -100 \cdot \frac{920}{3000} = -30{,}7 \qquad G_{v,\text{tot}} = -30{,}7 \cdot \frac{1400}{330+1400} \approx -24{,}8$$
> Un quinto del guadagno se ne va nel partitore d'ingresso. È l'errore d'esame più frequente: dichiarare $G_v$ e dimenticare l'attenuazione di sorgente.

> [!danger] Il segno meno (inversione di fase)
> In CE, l'uscita è **in opposizione di fase** rispetto all'ingresso: quando $v_{in}$ sale, $I_C$ sale, e $V_{CE}$ scende. È una firma del CE: se non c'è inversione di fase, **non è un CE**.

### 2.2 Collettore comune (CC, *emitter follower*)

> Amplificatore a BJT a collettore comune (inseguitore), schema elettrico — **Mirandola Cap. 7 §2.3, p. 347, FIGURA 30**:
>
> ![[libro-cap7-p347-fig30-collettore-comune.png]]
>
> Il libro definisce così la configurazione: «l'elettrodo di riferimento è il **collettore** del BJT (collegato al potenziale fisso $+V_{CC}$, ma **dinamicamente a massa**); il segnale viene introdotto tra la base e il riferimento, mentre l'uscita viene prelevata tra l'emettitore e il riferimento».

> [!example]- La **FIGURA 31** e l'ESEMPIO 13 — **Mirandola Cap. 7 §2.3, pp. 348-349**
> ![[libro-cap7-pp348-349-bjt-collettore-comune.png]]
>
> FIGURA 31: **A)** circuito statico · **B)** circuito dinamico · **C)** circuito equivalente alle variazioni. È il passaggio che manca fra lo schema elettrico della FIGURA 30 e le formule dei parametri: si sostituisce il BJT col suo modello a parametri $h$ e si ricava tutto da lì.
>
> L'**ESEMPIO 13** applica le formule a $R_s = 300\ \Omega$, $R_1 = 100$ k$\Omega$, $R_2 = 390$ k$\Omega$, $R_E = 8{,}2$ k$\Omega$, $R_L = 47$ k$\Omega$, con un 2N2222 ($h_{ie} = 3{,}3$ k$\Omega$, $h_{fe} = 110$):
>
> | Grandezza | Risultato |
> |---|---|
> | $R_{i(BE')} = h_{ie} + (1+h_{fe})\dfrac{R_E R_L}{R_E + R_L}$ | 780 k$\Omega$ |
> | $R_p = R_E \parallel R_L$ | 7,0 k$\Omega$ |
> | $R_B = R_1 \parallel R_2$ | 80 k$\Omega$ |
> | $R_i = R_B \parallel R_{i(BE')}$ | **73 k$\Omega$** |
> | $G_i$ | 1,5 |
> | $G_v$ | $\approx 1$ |
> | $R_o = \dfrac{(R_B \parallel R_s) + h_{ie}}{1 + h_{fe}} \parallel R_E$ | **32 $\Omega$** |
>
> I due numeri da ricordare sono l'ultimo e il quart'ultimo: $R_i = 73$ k$\Omega$ **alta**, $R_o = 32\ \Omega$ **bassa**, $G_v \approx 1$. È tutto il senso del buffer in tre numeri.

- Il collettore è collegato direttamente a $V_{CC}$ (quindi "a massa" per il segnale AC).
- L'ingresso è applicato alla **base**.
- L'uscita è prelevata dall'**emettitore**.

**Le caratteristiche, testuali dal libro (p. 347):**

| Parametro | Valore | Nota del libro |
|---|---|---|
| Guadagno di **tensione** | basso, $G_v \approx 1$ | quindi $v_o \approx v_i$ |
| Guadagno di **corrente** | alto, $G_i \approx h_{fe}$ | è qui che sta l'amplificazione |
| Resistenza d'**ingresso** | molto elevata (**decine di k$\Omega$**) | |
| Resistenza d'**uscita** | molto bassa (**decine di $\Omega$**) | |
| **Fase** dell'uscita | **uguale** a quella d'ingresso | nessuna inversione, a differenza del CE |

per questo si dice "**inseguitore**" (*emitter follower*): l'uscita insegue la base.

> [!tip] Il collegamento che il libro fa esplicitamente
> «L'impiego dell'amplificatore a collettore comune è **identico a quello dell'inseguitore ad amplificatore operazionale**» (Cap. 6, §2.6): è un **adattatore d'impedenza (buffer)** per disaccoppiare l'uscita di un circuito dal carico. Grazie all'alta $R_i$ «non assorbe corrente dal circuito a monte, mentre fornisce corrente al carico con una tensione uguale a quella d'ingresso».
>
> Detto altrimenti: il CC **non amplifica la tensione, amplifica la corrente** — ed è esattamente ciò che serve per pilotare un carico senza far crollare il segnale.

> [!check] Perché si chiama "follower"
> La tensione di emettitore è sempre $\approx V_B - 0{,}7$. Quando $V_B$ sale, $V_E$ sale di conseguenza: l'uscita **segue** l'ingresso.

**A cosa serve**: il CC ha **alta impedenza di ingresso** e **bassa impedenza di uscita**, quindi è un perfetto **buffer** — collega una sorgente ad alta impedenza a un carico a bassa impedenza, senza attenuare il segnale.

### 2.3 Base comune (CB)

> [!check] Correzione — il libro **tratta** la base comune
> Una versione precedente di questa nota affermava che «non è presente un riferimento a figura specifica nella scansione del libro». **È falso**: Mirandola dedica al CB una sezione dentro il §2.3 «Gli amplificatori a collettore comune **e a base comune**», con la **FIGURA 33** (A: schema elettrico; B: circuito dinamico) alle **pp. 350-351**.

In questa configurazione «il terminale di riferimento è la **base** del BJT; il segnale viene introdotto tra l'**emettitore** e il riferimento e l'uscita viene prelevata tra il **collettore** e il riferimento» (p. 350).

> [!tip] Il condensatore $C_B$
> Nel CB c'è un condensatore in più, $C_B$, che fa da **by-pass della base**: «consente la polarizzazione della base agli effetti della continua, mentre la porta a massa per il segnale». È lo stesso trucco del $C_E$ nel CE, applicato a un altro terminale — ed è ciò che rende la base "comune" *dinamicamente*, pur essendo polarizzata in DC.

**Le caratteristiche, testuali dal libro (p. 351):**

| Parametro | Valore |
|---|---|
| Guadagno di **tensione** | abbastanza **elevato** |
| Guadagno di **corrente** | $\approx 1$ |
| Resistenza d'**ingresso** | **molto bassa** (poche decine di $\Omega$) |
| Resistenza d'**uscita** | coincide con quella del carico $R_L$ |
| **Fase** dell'uscita | **uguale** a quella d'ingresso |

> [!info] Perché si usa — le due motivazioni del libro
> 1. **Circuiti d'ingresso di apparati radiotelevisivi**: la bassa resistenza d'ingresso «si adatta all'**impedenza caratteristica delle antenne** (75 o 150 $\Omega$)». È un caso raro in cui una $R_i$ bassa è un *pregio*: serve l'adattamento, non la massima tensione.
> 2. **Amplificatori selettivi per alte frequenze**, in cui il carico è un **circuito risonante parallelo**: alla risonanza presenta la massima resistenza, «cui consegue il massimo guadagno di tensione».

> [!warning] Attenzione al confronto CE / CC / CB
> Le tre configurazioni **non** si distinguono per "quanto amplificano" in generale, ma per **quale grandezza** amplificano e con quali impedenze:
>
> | | $G_v$ | $G_i$ | $R_i$ | $R_o$ | Fase |
> |---|---|---|---|---|---|
> | **CE** | alto | alto | media (k$\Omega$) | $= R_C$, non bassa | **invertita** |
> | **CC** | $\approx 1$ | alto ($h_{fe}$) | molto alta | molto bassa | uguale |
> | **CB** | alto | $\approx 1$ | molto bassa | $= R_L$ | uguale |
>
> Solo il **CE** amplifica *entrambe* le grandezze — per questo il libro lo chiama «il più utilizzato nella pratica». CC e CB sacrificano un guadagno per ottenere un'impedenza estrema.

---

## 3. I parametri tipici di un amplificatore

| Parametro | Definizione | Come si misura |
|---|---|---|
| $A_v$ | Guadagno di tensione (mid-band) | $V_{out,pp} / V_{in,pp}$ |
| $A_i$ | Guadagno di corrente | $I_{out} / I_{in}$ |
| $R_{in}$ | Resistenza di ingresso | $V_{in} / I_{in}$ |
| $R_{out}$ | Resistenza di uscita | $V_{out,\text{open}} / V_{out,\text{loaded}}$ |
| $f_L$, $f_H$ | Frequenze di taglio inferiore/superiore | Dove $|A_v|$ cala di 3 dB |
| $BW$ | Banda passante | $f_H - f_L$ |
| $A_{v,\text{max}}$ | Escursione massima senza clipping | $V_{out,\text{clippato}} / V_{in}$ |
| THD | Distorsione armonica totale | % di armoniche spurie su $V_{out}$ |

---

## 4. Il modello a piccoli segnali con $h$-parametri

Nell'analisi ai piccoli segnali il transistor si rappresenta con un modello linearizzato a parametri $h$:

- $h_{ie}$: impedenza di ingresso
- $h_{re}$: tensione di feedback inversa (spesso trascurata, $h_{re} \approx 0$)
- $h_{fe}$: guadagno di corrente diretto
- $h_{oe}$: ammettenza di uscita (spesso trascurata)

> [!tip] Le ipotesi del modello a $h$-parametri
> Il transistor è in **zona attiva** e il segnale è **piccolo** (tipicamente $\leq 10\ \text{mV}$ di picco, per restare nella linearità della curva $I_C$–$V_{BE}$). Se il segnale è troppo grande, escursioni non lineari → distorsione.
>
> Mirandola aggiunge (p. 341) che «i parametri ibridi **dipendono dal punto di lavoro**»: non sono costanti del componente. I data sheet li danno a una condizione precisa — per il 2N2222, $h_{ie} = 2 \div 8$ k$\Omega$ e $h_{fe} = 50 \div 300$ misurati a $I_C = 1$ mA, $V_{CE} = 10$ V, $f = 1$ kHz (p. 342). La dispersione è enorme: **6× su $h_{fe}$**.

### Le quattro formule dell'amplificatore CE (pp. 342-345)

Sono le relazioni che il libro usa sia per l'**analisi** sia per il **progetto**. Con $R_B = R_1 \parallel R_2$ e $R_p = R_C \parallel R_L$:

| Parametro | Formula | N. |
|---|---|---|
| Resistenza d'**ingresso** | $R_i = \dfrac{v_i}{i_i} = R_B \parallel h_{ie} = \dfrac{R_B\,h_{ie}}{R_B + h_{ie}}$ | **7.13** |
| Guadagno di **corrente** | $G_i = \dfrac{i_o}{i_i} = \dfrac{R_i}{h_{ie}}\cdot h_{fe} \cdot \dfrac{R_p}{R_L}$ | **7.14** |
| Guadagno di **tensione** | $G_v = -\,h_{fe}\dfrac{R_p}{h_{ie}}$ | **7.15** |
| Resistenza d'**uscita** | $R_o = R_C$ | **7.16** |

> [!tip] Perché $R_o = R_C$ e basta
> «La resistenza d'uscita dell'amplificatore è quella vista verso il BJT in assenza di segnale d'ingresso; essa **coincide con $R_C$** perché il generatore di corrente dipendente, in parallelo a $R_C$, presenta **impedenza infinita**» (p. 345). Un generatore di corrente ideale, spento, è un circuito aperto: sparisce dal parallelo. Resta solo $R_C$.
>
> Conseguenza pratica che il libro mette nel riassunto: la $R_o$ del CE **non è bassa**. Se devi pilotare un carico piccolo, ti serve un CC a valle.

> [!example] Verifica numerica del libro (FIGURA 29, p. 343): $R_1=14$ k, $R_2=3$ k, $R_C=1$ k, $R_L=12$ k, $h_{ie}=3$ k, $h_{fe}=100$
> $$R_B = 14\Vert 3 = 2{,}5\ \text{k}\Omega \qquad R_i = 2{,}5 \Vert 3 = 1{,}4\ \text{k}\Omega \qquad R_p = 1 \Vert 12 = 920\ \Omega$$
> $$G_v = -100 \cdot \frac{920}{3000} = -30{,}7 \qquad R_o = R_C = 1\ \text{k}\Omega$$

### Il progetto: TABELLA 1 (p. 346)

Progettare significa il problema **inverso**: dati $G_v$, $G_i$, $R_i$, $R_o$ desiderati, ricavare $R_1$, $R_2$, $R_C$, $R_E$. Il libro inverte le 7.13-7.16 e raccoglie i risultati in una tabella:

![[libro-cap7-p346-tabella1-progetto-ce.png]]

> [!note] Come si legge
> Si parte da $R_o = R_C$ (immediata), poi $R_p$ dal guadagno voluto, poi si risale a $R_C$ con l'inversa del parallelo $R_C = \dfrac{R_p R_L}{R_L - R_p}$, e infine $R_B$ dalla resistenza d'ingresso: $R_B = \dfrac{R_i h_{ie}}{h_{ie} - R_i}$.
>
> ⚠️ Nota il **segno meno al denominatore** in entrambe le inverse: se chiedi $R_i \ge h_{ie}$ (o $R_p \ge R_L$) il risultato diventa negativo o infinito. Non è un errore di conto: significa che **la specifica è impossibile**: un parallelo non può mai superare il minore dei suoi termini. È un buon controllo di sanità in sede d'esame.

---

## 5. La distorsione e l'escursione massima

In regime di "grandi segnali" il transistor ha limiti:

- **Saturazione**: $V_{CE}$ non può scendere sotto $0{,}2\ \text{V}$ → **clipping inferiore** in uscita.
- **Cutoff**: $I_C$ non può andare a 0$^+$ → **clipping superiore** in uscita.

L'**escursione picco-picco** in uscita è quindi limitata a:
$$V_{out,pp,\max} = 2 \cdot \min(V_{CE} - V_{CE,sat}, I_C \cdot R_C)$$

> [!warning] Clipping in laboratorio
> Se sull'oscilloscopio vedi le punte della sinusoide "tagliate", stai saturando o andando in cutoff. Abbassa l'ampiezza del segnale di ingresso o aumenta la tensione di alimentazione.

---

## 6. La risposta in frequenza

> Risposta in ampiezza e banda passante di un amplificatore — **Mirandola Cap. 7, p. 336, FIGURA 21**:
>
> ![[libro-cap7-p336-fig21-banda-passante.png]]
>
> Il libro definisce **banda passante** come «la differenza tra le due frequenze (di taglio) entro le quali il guadagno non scende oltre **3 dB** rispetto ai valori assunti in banda, in cui i condensatori sono assimilabili a cortocircuiti». Vedi anche i diagrammi di Bode in [[Filtri passivi del primo ordine]] § Bode.

> [!info] Rumore e figura di rumore (p. 336) — spesso chiesto all'orale
> Il libro definisce il **rumore** come «un segnale spurio di disturbo che si somma al segnale ed è causato dal funzionamento dei componenti dell'amplificatore». Due indicatori distinti, da non confondere:
> - **Rapporto segnale-disturbo $S/N$**: rapporto tra la potenza di segnale e quella del disturbo, **presenti all'uscita**. Qualifica il **segnale**.
> - **Figura di rumore $F$**: quoziente tra il rapporto $[S_i/N_i]$ d'**ingresso** e il rapporto $[S_o/N_o]$ d'**uscita**, generalmente espressa in dB. Qualifica l'**amplificatore** — misura quanto l'amplificatore *peggiora* il rapporto segnale-rumore che gli arriva.
>
> Un amplificatore ideale ha $F = 1$ (0 dB): non aggiunge rumore proprio. Per i meccanismi fisici del rumore (Johnson e shot) vedi [[Diodi]] — il libro li tratta al Cap. 4 §6, pp. 180-181.

Nel dominio della frequenza il CE ha un comportamento passa-banda:

- **Banda passante**: guadagno $A_v$ costante (regione "mid-band").
- **$f_L$**: frequenza di taglio inferiore, legata alle **C di accoppiamento** in ingresso/uscita e all'eventuale $C_E$ di bypass.
- **$f_H$**: frequenza di taglio superiore, legata alle **capacità parassite** del transistor e ai limiti fisici del dispositivo.

> [!tip] Il CE è naturalmente passa-banda
> Alle basse frequenze le C di accoppiamento (in serie al segnale) presentano impedenza alta → attenuano.
> Alle alte frequenze le C parassite del BJT creano percorsi a bassa impedenza verso massa → attenuano ancora.
> È un filtro passa-banda con due tagli.

---

## 7. Misure in laboratorio

> [!check] La sequenza di misura su un amplificatore
>
> 1. **Controlla la polarizzazione a riposo** (segnale di ingresso = 0). Misura $V_{CE}$ con un multimetro. Deve essere ≈ $V_{CC}/2$.
> 2. **Applica il segnale** a frequenza centrale (es. 1 kHz), ampiezza piccola (es. 10 mV$_{pp}$).
> 3. **Misura $A_v$** dal rapporto $V_{out,pp} / V_{in,pp}$.
> 4. **Verifica l'inversione di fase** (se è un CE): quando l'ingresso sale, l'uscita scende.
> 5. **Aumenta l'ampiezza** fino a vedere il clipping — hai trovato l'escursione massima.
> 6. **Varia la frequenza** e cerca la $f_H$ e $f_L$.

---

## Quesiti tipo — Guida rapida

> [!question] Perché in CE c'è inversione di fase?
> Perché $v_{out} = V_{CC} - I_C R_C$: quando $I_C$ sale (segnale di ingresso sale), $v_{out}$ scende. È una firma: se il segnale è in fase, **non è un CE**.

> [!question] Perché il CC è chiamato "emitter follower"?
> Perché $V_{out} = V_E \approx V_B - 0{,}7\ \text{V}$: l'uscita **segue** la base con uno "sfasamento" costante di $V_{BE} = 0{,}7\ \text{V}$ (trascurabile ai fini del segnale AC). L'amplificazione di tensione è ≈ 1, ma quella di corrente è alta.

> [!question] Quando uso il CE vs il CC?
> **CE** quando voglio amplificazione di tensione ($A_v > 1$, anche 10–100).
> **CC** quando voglio adattare impedenze (alta $R_{in}$, bassa $R_{out}$, $A_v \approx 1$).
> Spesso CE e CC in cascata: il CE amplifica in tensione, il CC adatta l'impedenza d'uscita al carico successivo.

> [!question] Come si misura la $f_H$ di un amplificatore?
> Si varia la frequenza del segnale di ingresso, tenendo fissa l'ampiezza. Si trova la frequenza a cui $V_{out,pp}$ cala a $A_v/\sqrt{2} \approx 0{,}707 A_v$. Quella è $f_H$ (per il taglio superiore).

> [!question] Cos'è il "clipping"?
> È il taglio della forma d'onda quando il transistor esce dalla zona attiva: in alto quando $I_C$ è limitato da $R_C$ (saturazione), in basso quando $V_{CE}$ è vicino a 0 (saturazione). In entrambi i casi la sinusoide viene "tronca".

---

## 8. Da qui in poi

- Prerequisiti: [[BJT]], [[Impedenza dei bipoli R, L, C]]
- Per la pratica: [[L'oscilloscopio]]
- Esercizi: [[Esercizi - Amplificatori a BJT]]
