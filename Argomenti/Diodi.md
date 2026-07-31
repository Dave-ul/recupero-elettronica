---
tags: [recupero, elettronica, diodi, semiconduttori]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-19) — Mirandola Vol.2, Cap. 5 «I diodi», pp. 192-233 (pagg.-PDF 75-94). Verificati: §1 giunzione PN e modelli (pp. 192-201, FIGURE 10-12, form. 5.3), §2 impieghi — raddrizzatori/rivelatori/fissatore/limitatore (pp. 204-213, FIGURE 17-22, form. 5.4-5.6), §3 data sheets (pp. 214-217, form. 5.7-5.9), §4.3 Zener (pp. 219-221, FIGURA 32, TABELLA 4), esempio Zener + tabella Formule (pp. 228-229). AGGIUNTE 2026-07-28 (Fase Studio, Lotto 1): §1 struttura/simbolo/polarizzazione (p. 196, FIGURE 5-6), §1.3 curva e versi convenzionali (p. 197, FIGURA 7), §2.6 limitatori (pp. 210-212, FIGURE 24-26), §4.2 breakdown Zener/valanga (p. 220, TABELLA 4), §4.3 regolatore (p. 221, FIGURE 33-34, form. 5.10-5.11). Figure ritagliate dal PDF in Allegati/. Vedi [[Prove/00 - Audit e correzioni]]."
prove: [scritta, orale, pratica]
---

# Diodi

> [!info] Dove serve
> **Orale Carli** (LETTERA): «diodi». **Pratica Protti** (LETTERA): «circuiti con diodi». (NB: la LETTERA Carli scritta NON cita i diodi esplicitamente — solo AC + filtri 1° ordine + BJT + JFET N + MOSFET N enhancement. I diodi sono **prerequisito concettuale** del BJT/MOSFET e capitolo d'esame orale Carli.) È il primo componente **attivo** della scansione: ha un comportamento marcatamente **non lineare**, e introduce una serie di metodi di analisi nuova (spezzata di carico, modello a tratti, approssimazione a soglia).

Prerequisiti: [[Segnali sinusoidali e fasori]] (per raddrizzatori), [[Impedenza dei bipoli R, L, C]] (per i circuiti RC).

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §7**.

## 1. La giunzione p-n: perché esiste il diodo

Un diodo a giunzione è formato da una regione di semiconduttore **p** a contatto con una regione **n**. Nella zona di contatto (la «giunzione») i portatori si ricombinano e si crea una **barriera di potenziale** — il campo elettrico interno che impedisce ai portatori di attraversare la giunzione.

Questa barriera vale, per il silicio, circa $V_\gamma \approx 0{,}7\ \text{V}$ (ge­rmanio: ~0,3 V).

![[libro-cap5-p196-fig5-struttura-simbolo-diodo.png]]
*Mirandola, Cap. 5, **FIGURA 5**, p. 196 — **A)** struttura: la zona **P** sta dalla parte dell'**anodo** ($A$), la zona **N** dalla parte del **catodo** ($K$); **B)** simboli circuitali (il triangolo punta da $A$ verso $K$, la **barra** è il catodo); **C)** contenitore dei diodi di piccola potenza, dove la **fascetta** stampata marca il catodo.*

> [!check] Il disegno che ti chiedono (A-D1 · A-D2 · B-D1 · B-D2)
> **Struttura**: due blocchi affiancati etichettati **P** e **N**, il terminale $A$ **sul lato P**, il terminale $K$ **sul lato N**, la giunzione marcata in mezzo. **Simbolo**: triangolo + **barra**; $A$ e $K$ etichettati; la freccia punta **dall'anodo al catodo**, cioè nel verso in cui il diodo lascia passare la corrente. Chi disegna il triangolo e si dimentica la barra ha disegnato un generatore, non un diodo.

> [!tip] Il senso della barriera
> Senza barriera, un elettrone potrebbe cadere dalla zona n alla zona p senza che nessuno gli dia energia, e ci sarebbe conduzione spontanea in entrambi i versi. La barriera di potenziale è ciò che **rende il diodo un componente che conduce in un solo verso**.

---

## 2. Polarizzazione diretta e inversa

![[libro-cap5-p196-fig6-polarizzazione-diretta-inversa.png]]
*Mirandola, Cap. 5, **FIGURA 6**, p. 196 — **A)** polarizzazione **diretta**: il **+** del generatore $E$ è dalla parte dell'**anodo**, la corrente $I$ circola; **B)** polarizzazione **inversa**: il generatore è **capovolto** e resta la sola corrente di saturazione, $I_0 \approx 0$.*

> [!check] Il disegno che ti chiedono (B-D4 · B-D5)
> Due maglie separate, ciascuna con generatore + diodo (+ la $R$ di limitazione, che nella figura del libro è sottintesa). Ciò che **non** può mancare: la **polarità del generatore visibile** ($+$ e $-$ marcati), il diodo orientato di conseguenza, la freccia della corrente nel caso diretto e la nota $I_0 \approx 0$ nel caso inverso. Non basta scrivere «diretta» e «inversa» sotto due disegni identici.

### Polarizzazione diretta

Colleghi il polo **+** della pila all'**anodo** (lato p) e il **−** al **catodo** (lato n). Se la tensione applicata supera la barriera, i portatori fluiscono e il diodo conduce. La tensione ai suoi capi resta praticamente fissa a $V_D \approx 0{,}7\ \text{V}$ (silicio) — è il motivo per cui in molte analisi il diodo si sostituisce con un **generatore ideale di tensione** $V_D$.

### Polarizzazione inversa

Inverti la pila: + al catodo, − all'anodo. La barriera si alza, i portatori non fluiscono, il diodo **non conduce**. In condizioni ordinarie scorre una corrente inversa **piccolissima** ($I_{R} \approx \text{nA}$ o μA, dipende dal diodo), spesso trascurabile.

---

## 3. La curva V-I: la «spezzata» di carico

![[libro-cap5-p200-fig11-curva-rd.png]]
*Mirandola, Cap. 5, **FIGURA 11**, p. 200 — curva caratteristica reale del diodo al silicio. La pendenza del tratto rettilineo oltre il ginocchio vale $1/r_d$; i punti $A$ (1 V, 500 mA) e $B$ (0,7 V) sono quelli usati nell'ESEMPIO 1 per ricavare $r_d$.*

> [!quote] Riferimenti reali del libro (Mirandola Vol.2, Zanichelli 2012)
> **Cap. 5 «I diodi» — pp. 192-233** (pagg.-PDF 75-94). Sezioni utili a questo file:
> - **§1 Il diodo al silicio**, pp. 192-201 — giunzione PN, curva caratteristica, modelli approssimati, retta di carico (FIGURE 10-12, formula 5.3).
> - **§2 Impiego dei diodi nei circuiti**, pp. 204-213 — raddrizzatori (§2.1), rivelatore di picco (§2.2), rivelatore d'inviluppo (§2.3), fissatore (§2.4), moltiplicatore (§2.5), limitatore (FIGURE 17-22, formule 5.4-5.6).
> - **§4.3 Il diodo Zener**, pp. 219-221 — FIGURA 32, TABELLA 4 (serie BZX55C).
> - **Esempio Zener svolto + tabella «Formule»**, pp. 228-229.
>
> ⚠️ Il **rumore** nei componenti (Johnson nei resistori, *shot* nei semiconduttori) **non** appartiene a questo capitolo: è in **Cap. 4 «I quadripoli lineari e non lineari», §6 «La qualità dei quadripoli (distorsione e rumore)», pp. 180-181**, formule **4.61** ($E_n=\sqrt{4kTR\Delta f}$) e **4.62** ($I_n=\sqrt{2qI\Delta f}$). Vedi `Allegati/libro-cap4-pp180-181-rumore-johnson-shot.png`. *(Attribuzione corretta il 2026-07-19: la versione precedente di questa nota lo citava erroneamente come Cap. 5. Folio ri-verificato il 2026-07-22 leggendolo dal piè di pagina: pp. 180-181, pagina-PDF 69 — vedi [[00 - Audit e correzioni]], Lotto 8.)*

### La curva completa e i versi convenzionali (FIGURA 7, p. 197)

![[libro-cap5-p197-fig7-versi-convenzionali-curva.png]]
*Mirandola, **FIGURA 7**, p. 197 — **A)** convenzione per i versi di $I_D$ e $V_D$; **B)** curva caratteristica, con le zone **DIRETTA** (primo quadrante, mA) e **INVERSA** (terzo quadrante, µA/nA) esplicitamente etichettate.*

**I versi convenzionali** (convenzione degli utilizzatori, il diodo è un bipolo **passivo**): $I_D$ positiva **dall'anodo al catodo** — il verso della freccia del simbolo; $V_D$ positiva **con il + sull'anodo**, cioè misurata anodo-catodo. Con questa convenzione $V_D > 0$ ⇒ diretta, $V_D < 0$ ⇒ inversa.

**L'andamento completo**, nei sei punti del libro (§1.3, p. 197):

1. l'andamento **non è rettilineo**: il diodo è un componente **non lineare**;
2. tra $0$ V e $V_s \approx 0{,}6$ V in diretta, la **corrente è nulla**;
3. sopra $V_s \approx 0{,}6$ V scorre corrente, che aumenta **velocemente** oltre i **0,7 V**;
4. a normali valori di corrente il diodo presenta ai capi **circa 0,7 V**; sopra una **corrente limite** (dai data sheets) il calore dissipato provoca la **fusione e distruzione della giunzione**;
5. in inversa, tra $0$ V e $V_B$ (**tensione di breakdown**), la corrente è la sola $I_0$ — pochi **nA**;
6. raggiunta $V_B$, la corrente inversa **aumenta bruscamente** e rompe la giunzione, per **moltiplicazione a valanga**. Secondo il tipo di diodo $V_B$ va da qualche **decina** a qualche **migliaio** di volt.

> [!warning] $0{,}6$ V o $0{,}7$ V? Il libro li distingue, il vault li confondeva
> - $V_s \approx \mathbf{0{,}6}$ **V** è la **tensione di soglia**: il confine oltre il quale il diodo *inizia* a condurre (p. 196).
> - $\approx \mathbf{0{,}7}$ **V** è la **caduta ai capi di un diodo percorso da normali valori di corrente**, ed è il valore usato nei modelli A e B.
>
> Se ti chiedono *«che cosa rappresenta la tensione di soglia»* (domanda **A-D6**), la risposta del libro è **0,6 V**. Altrove in questa nota si usa $V_\gamma \approx 0{,}7$ V perché è il valore operativo dei modelli — sono due grandezze diverse, non un'incoerenza. La soglia **diminuisce** con la temperatura, di circa **−2 mV/°C** (FIGURA 8, p. 198).

### L'equazione di Shockley e la sua legenda (form. 5.1, p. 198)

Il tratto di caratteristica **a destra della tensione di breakdown** è descritto dall'espressione elaborata da **William Bradford Shockley**, uno dei tre inventori del transistor:

$$I_D = I_0\left(e^{\frac{V_D}{V_T}} - 1\right) \tag{5.1}$$

| Simbolo | Significato |
|---|---|
| $I_D$, $V_D$ | corrente e tensione del diodo, nei versi convenzionali di FIGURA 7A |
| $I_0$ | **corrente inversa di saturazione** — pochi nA, dalle cariche minoritarie |
| $V_T$ | **tensione termica**: $V_T = kT/q \approx 26$ mV a 25 °C ($T \approx 300$ K) |
| $k$ | costante di Boltzmann |
| $T$ | temperatura **assoluta** della giunzione [K] |
| $q$ | carica dell'elettrone |

$I_0$ e $V_T$ **aumentano entrambi** con $T$; poiché prevale l'effetto di $I_0$, *la corrente nella giunzione, a parità di tensione applicata, aumenta al crescere della temperatura*.

> [!question] «Il diodo è un componente lineare?» — la giustificazione da dare
> **No.** Il libro lo dichiara già a p. 192: bipolo **passivo** (non amplifica) e **non lineare** (*non c'è proporzionalità tra $V$ e $I$*).
>
> Se fosse lineare la caratteristica sarebbe una **retta per l'origine** e $V/I$ sarebbe costante. Invece sotto $V_s$ la corrente è nulla mentre la tensione cresce, e sopra $V_s$ la corrente esplode a tensione quasi ferma: lo stesso $\Delta V$ dà $\Delta I$ diversissimi.
>
> **Conseguenza operativa** — è questo il punto: non essendo lineare **non valgono** legge di Ohm, sovrapposizione degli effetti, Thévenin e Norton. Per riusarli si **linearizza a tratti**, ed è esattamente la ragione d'essere dei modelli approssimati qui sotto.

### I tre modelli approssimati (nomenclatura del libro)

Per l'analisi circuitale il diodo in conduzione si sostituisce con un **circuito equivalente**. Mirandola ne usa **tre**, in ordine di raffinatezza decrescente (Cap. 5, §1, p. 200, **TABELLA 1** e **FIGURA 10**):

![[libro-cap5-p200-fig10-modelli-diodo.png]]
*Mirandola, Cap. 5, **FIGURA 10**, p. 200 — **A)** circuito reale; **B)** modello A; **C)** modello B; **D)** modello C. Valori dell'ESEMPIO 1: $E=12$ V, $R_L=680\ \Omega$.*

| Modello | Circuito equivalente in conduzione | Quando usarlo |
|---|---|---|
| **A** | generatore $0{,}7$ V **+ resistenza** $r_d$ in serie | il più accurato; serve solo se $r_d$ è confrontabile con le altre resistenze del circuito |
| **B** | generatore $0{,}7$ V (interruttore + generatore) | **il migliore compromesso** — è quello da usare di default |
| **C** | **diodo ideale**: cortocircuito in conduzione, aperto in interdizione | quando le tensioni in gioco sono molto maggiori di 0,7 V, o per l'analisi qualitativa ON/OFF |

In tutti e tre, in **interdizione** il diodo è un **circuito aperto**.

> [!check] Perché il libro consiglia il modello B — ESEMPIO 1, p. 200
> Stesso circuito ($E=12$ V, $R_L=680\ \Omega$), risolto con i tre modelli:
>
> $$I_A=\frac{E-0{,}7}{r_d+R_L}=\frac{12-0{,}7}{0{,}6+680}=16{,}60\ \text{mA} \qquad I_B=\frac{E-0{,}7}{R_L}=16{,}62\ \text{mA} \qquad I_C=\frac{E}{R_L}=17{,}65\ \text{mA}$$
>
> - **A e B danno praticamente lo stesso risultato** (scarto 0,1%): $r_d=0{,}6\ \Omega$ è trascurabile rispetto ai 680 Ω del carico. Quindi il modello A, più laborioso, non ripaga.
> - **C sbaglia di circa il 6%**, perché ignora una caduta di 0,7 V che *non* è trascurabile rispetto ai 12 V del generatore.
>
> Il valore $r_d=0{,}6\ \Omega$ si ricava dalla FIGURA 11 come rapporto incrementale: $r_d=\dfrac{V_A-V_B}{I_A-I_B}=\dfrac{1-0{,}7}{0{,}5-0}=0{,}6\ \Omega$.

### La retta di carico e il punto di lavoro

Quando serve il risultato **esatto** (o quando la caratteristica del diodo è data solo come grafico), si usa la **soluzione grafica** (Mirandola, Cap. 5, p. 201, **FIGURA 12**).

![[libro-cap5-p201-fig12-retta-di-carico.png]]
*Mirandola, Cap. 5, **FIGURA 12**, p. 201 — **A)** circuito con generatore, resistore e diodo; **B)** soluzione grafica: il **punto di lavoro** $Q$ è l'intersezione tra la curva caratteristica del diodo e la retta di carico.*

Il resto del circuito (generatore $E$ + resistore $R$), che è **lineare**, impone tra $V_D$ e $I_D$ la relazione:

$$I_D = \frac{E - V_D}{R} \tag{5.3}$$

Nel piano $V_D/I_D$ questa è una **retta a pendenza negativa** — la **retta di carico** — che interseca:

- l'asse $V_D$ nel punto $V_D = E$ (diodo aperto: tutta la tensione cade sul diodo);
- l'asse $I_D$ nel punto $I_D = E/R$ (diodo in corto: corrente limitata dal solo resistore).

Il **punto di lavoro** $Q$ è l'unico punto che soddisfa **contemporaneamente** la relazione imposta dal diodo (la sua curva) e quella imposta dal circuito (la retta): è la loro **intersezione**. Le coordinate di $Q$ sono $(V_o,\ I_o)$, cioè la soluzione del problema.

> [!tip] Il metodo vale anche per circuiti complessi
> Se il circuito attorno al diodo è più complicato ma **lineare**, si riduce sempre a un generatore + un resistore in serie con il **teorema di Thévenin**, e poi si traccia la retta di carico come sopra.
>
> Nella pratica la soluzione grafica si usa poco (i data sheets spesso non riportano la curva), **ma il concetto di punto di lavoro è essenziale**: è esattamente lo stesso che userai per polarizzare i [[BJT]] e i [[MOSFET]].

---

## 4. Il diodo Zener

![[libro-cap5-p219-fig32-zener.png]]
*Mirandola, Cap. 5, **FIGURA 32**, p. 219 — **A)** simbolo circuitale (nota i "baffi" sulla barra del catodo); **B)** curva caratteristica. In inversa, oltre il **ginocchio** (*knee*), la tensione resta bloccata a $-V_Z$.*

Il **diodo Zener** è un diodo al silicio progettato per lavorare **nella zona di breakdown inverso** senza danneggiarsi. La tensione di Zener $V_Z$ è determinata dai **livelli di drogaggio** (più alti che in un diodo normale) e può andare da pochi volt fino a **qualche centinaio di volt**; è **molto stabile** al variare della corrente inversa, purché questa resti sopra un valore minimo.

### I due meccanismi di breakdown: effetto Zener ed effetto valanga (p. 220)

Il libro è esplicito: *«Il passaggio della corrente dal catodo all'anodo (**breakdown inverso**) è causato da **due meccanismi differenti**, a seconda del valore della tensione di Zener»* (Mirandola, Cap. 5, **p. 220**, testatina «5 I diodi»).

| | **Effetto Zener** | **Effetto valanga** |
|---|---|---|
| **Quando** | $V_Z < 5$ V | $V_Z > 6$ V |
| **Com'è fatta la giunzione** | zone P e N **fortemente drogate** ⇒ zona di svuotamento **molto stretta** | il libro **non** descrive la giunzione in questo caso: parla solo del campo e degli urti |
| **Cosa succede** | anche una **ridotta** tensione inversa crea un campo elettrico sufficiente a **rompere direttamente** numerosi legami covalenti | gli elettroni, **accelerati** dal campo, **urtano** gli atomi limitrofi, rompono legami e liberano altri elettroni (**moltiplicazione a valanga**) |
| **Chi rompe i legami** | il **campo elettrico** | l'**urto** dei portatori già in moto |

> [!tip] La conferma sta nella TABELLA 4, stessa pagina
> La colonna $T_C$ (coefficiente di temperatura) della serie BZX55C **cambia segno** proprio tra i due meccanismi: **negativo** fino al 4V7 ($-0{,}020\ \%/°\text{C}$), **positivo** dal 5V1 in su ($+0{,}010\ \%/°\text{C}$). Due meccanismi fisici diversi ⇒ due comportamenti opposti con la temperatura. È il modo più rapido per ricordare quale dei due lavora a bassa $V_Z$.
>
> Nella fascia **5-6 V** il libro **non** assegna la rottura a nessuno dei due: dà $<5$ V per lo Zener e $>6$ V per la valanga, e lì si ferma. Non riempirla a memoria in sede d'esame.

> [!question] Perché lo Zener non si distrugge e un diodo normale sì? — domanda **C-D21**
> Il meccanismo è lo stesso; a cambiare è il **progetto**. In un diodo normale il breakdown non è previsto: la corrente inversa non è limitata da niente, la potenza $V_B \cdot I_R$ fonde la giunzione (è il punto 6 della curva, §3). Lo Zener è drogato **apposta** per avere un $V_Z$ basso e preciso, è costruito per **dissipare** la potenza di breakdown ($P_{\max}$ dichiarata), e nel circuito lavora **sempre** con una $R$ in serie che gli limita la corrente. Togli la $R$ e si brucia anche lui.

> [!warning] Tre correnti diverse — non confonderle
> Sulla curva della FIGURA 32 il libro marca **tre** valori, e sono cose distinte (dati della serie **BZX55C**, TABELLA 4, p. 220):
>
> | Simbolo | Nome | Valore tipico BZX55C | Significato |
> |---|---|---|---|
> | $I_{ZK}$ | corrente di **ginocchio** (*knee*) | **1 mA** | il **minimo** per stare in breakdown: sotto questa soglia la $V_Z$ non è più garantita |
> | $I_{ZT}$ | corrente di **test** | **5 mA** | corrente a cui il costruttore misura la $V_Z$ dichiarata; garantisce la stabilità migliore |
> | $I_{ZM}$ | corrente **massima** | dipende da $V_Z$ | limite imposto da $P_{\max}$: $I_{ZM} = P_{\max}/V_Z$ |
>
> Per tutta la serie BZX55C: $V_Z$ da **3,3 V a 33 V** (tolleranza ~5%), $P_{\max} = \mathbf{0{,}5\ W}$. Poiché $I_{ZM}=P_{\max}/V_Z$, **più alta è la $V_Z$, minore è la corrente ammessa**.
>
> ⚠️ *Correzione 2026-07-19*: la versione precedente di questa nota dava «$I_{Z,\min}\approx 5$ mA». È sbagliato — i 5 mA sono la corrente di **test** $I_{ZT}$; il minimo vero è $I_{ZK}=1$ mA.

> [!tip] Lo Zener non è ideale: la resistenza differenziale $Z_z$
> Nella FIGURA 32B il tratto di breakdown non è perfettamente verticale: ha una piccola pendenza, misurata dalla **resistenza differenziale**
>
> $$Z_z = \frac{\Delta V}{\Delta I}$$
>
> Uno Zener **ideale** avrebbe $Z_z = 0$ (curva verticale, $V_Z$ assolutamente costante). Nella realtà $Z_z$ vale da qualche ohm a qualche decina di ohm, ed è la ragione per cui la tensione stabilizzata **varia un po'** quando cambia la corrente di carico: $\Delta V_{out} = Z_z \cdot \Delta I_Z$. È il limite principale dello stabilizzatore a solo Zener.

### Stabilizzatore di tensione con Zener

> Lo schema classico di stabilizzatore ($R_S$ in serie, Zener in parallelo al carico) è il **§4.3 «Il regolatore di tensione a Zener»**, Mirandola Cap. 5, **pp. 220-221**. Il dimensionamento completo è svolto nella **GUIDA ALLA PROGETTAZIONE** di fine capitolo, **p. 228** (immagine sotto).

**La definizione del libro** (p. 221, testatina «Il regolatore di tensione a Zener»):

> Uno **stabilizzatore** o **regolatore di tensione** (*voltage regulator*) è un **quadripolo** che riceve una tensione d'ingresso di valore **variabile** in un dato intervallo ($V_i = V_{i\min} \div V_{i\max}$) e produce una tensione d'uscita di valore **predefinito, accurato e stabile**, **indipendente** dall'intensità di corrente assorbita dal carico ($I_L = I_{L\min} \div I_{L\max}$).

![[libro-cap5-p221-fig33-definizione-regolatore.png]]
*Mirandola, Cap. 5, **FIGURA 33**, p. 221 — **blocco funzionale** del regolatore di tensione: a sinistra l'ingresso $v_i$ **con il ripple**, a destra l'uscita $v_o$ **piatta**, in mezzo il blocco REGOLATORE DI TENSIONE, e il carico $R_L$. È il disegno che rispondono **A-D15** e **C-D22**: due forme d'onda + un blocco, niente componenti.*

![[libro-cap5-p221-fig34-regolatore-zener.png]]
*Mirandola, Cap. 5, **FIGURA 34**, p. 221 — **regolatore a Zener**, lo schema più semplice: il resistore $R$ in serie, lo Zener in **polarizzazione inversa** (catodo verso il nodo alto), il carico $R_L$ in parallelo allo Zener. Marcate le tre correnti: $I_R$ nel resistore, $I_Z$ nello Zener, $I_L$ nel carico. È il disegno di **A-D16** e **C-D23**.*

Le due relazioni che il libro associa allo schema:

$$I_R = \frac{V_i - V_o}{R} \tag{5.10}$$
$$I_Z = I_R - I_L \tag{5.11}$$

La **5.10** dice che $I_R$ è sensibile alle variazioni di $V_i$ **ma non** a quelle di $I_L$; la **5.11** è l'equilibrio delle correnti al nodo di uscita, e mostra che su $I_Z$ si ripercuotono **entrambe** le variazioni. Lo Zener le assorbe: finché $I_Z$ resta sopra $I_{ZT}$, ai suoi capi tiene $V_Z$, e l'uscita resta costante.

Funzionamento:

1. La tensione in ingresso $V_{in}$ varia (es. da un raddrizzatore) o è fissa ma più alta di $V_Z$.
2. $R_S$ è scelta in modo che, anche alla minima $V_{in}$ e alla massima corrente di carico, scorra abbastanza $I_Z$ da tenere il diodo in breakdown. Il minimo assoluto è $I_{ZK}$ (1 mA per la BZX55C), ma **in progetto si dimensiona sulla corrente di test $I_{ZT}$** (5 mA), che garantisce una $V_Z$ più stabile — è quello che fa il libro nella guida alla progettazione.
3. Se la corrente di carico $I_L$ aumenta, $I_Z$ diminuisce; se $V_{in}$ aumenta, $I_Z$ aumenta. La tensione $V_{out}$ resta praticamente fissa a $V_Z$.

> [!warning] La potenza è la prima cosa da verificare
> La potenza dissipata dallo Zener è $P_Z = V_Z \cdot I_Z$. Deve essere **minore** della $P_{Z,\max}$ dichiarata dal costruttore (altrimenti lo Zener si rompe).
> Formula operativa:
>
> $$I_{S,\max} = \frac{P_{Z,\max}}{V_Z}, \quad I_{S,\min} = I_{Z,\min} + I_{L,\max}$$
>
> deve essere $I_{S,\min} < I_S < I_{S,\max}$ per tutti i valori di $V_{in}$ e $I_L$ previsti.

### Dimensionamento svolto (Mirandola, p. 228)

![[libro-cap5-pp228-229-zener-esempio-formule.png]]
*Mirandola, Cap. 5, **pp. 228-229** — a sinistra la coda del dimensionamento dello stabilizzatore a Zener; a destra la tabella **«Formule»** riepilogativa del capitolo.*

Dati: $V_{i}$ tra **8,2 V e 9 V**, $V_Z = 6{,}2$ V, $I_{L}$ tra **0 e 100 mA**, $I_{ZT} = 5$ mA.

**1 — Scelta di $R_Z$** (caso peggiore: minima $V_i$ e massimo carico, perché è lì che rischi di *spegnere* lo Zener):

$$I_{R(\min)} = I_{L(\max)} + I_{ZT} = 100 + 5 = 105\ \text{mA}$$
$$R_{Z\max} = \frac{V_{i(\min)} - V_Z}{I_{R(\min)}} = \frac{8{,}2 - 6{,}2}{0{,}105} = 19\ \Omega \;\Rightarrow\; \text{si sceglie } R_Z = 18\ \Omega$$

**2 — Verifica della potenza sullo Zener** (caso peggiore opposto: massima $V_i$ e **carico staccato**, perché è lì che *tutta* la corrente passa nello Zener):

$$I_{Z\max} = \frac{V_{i\max} - V_Z}{R_Z} - I_{L\min} = \frac{9 - 6{,}2}{18} - 0 = 0{,}15\ \text{A}$$
$$P_{Z(\max)} = V_Z \cdot I_{Z\max} = 6{,}2 \cdot 0{,}15 = 0{,}93\ \text{W} \;\Rightarrow\; \text{Zener da \textbf{1 W}}$$

**3 — Verifica della potenza sul resistore**:

$$P_{RZ(\max)} = \frac{(V_{i\max} - V_Z)^2}{R_Z} = \frac{(9-6{,}2)^2}{18} = 0{,}43\ \text{W} \;\Rightarrow\; \text{resistore da \textbf{0,5 W}}$$

> [!check] I due casi peggiori sono opposti — è il cuore dell'esercizio
> - $R_Z$ si dimensiona col **minimo** $V_i$ e il **massimo** carico → altrimenti lo Zener esce dal breakdown e **smette di stabilizzare**.
> - La **potenza** si verifica col **massimo** $V_i$ e il carico **staccato** → altrimenti lo Zener **brucia**.
>
> Se ti ricordi solo una cosa di questo paragrafo, ricorda che devi controllare **entrambi gli estremi**.

---

## 5. Il raddrizzatore

### Raddrizzatore a semionda

![[libro-cap5-p205-fig17-raddrizzatore-semionda.png]]
*Mirandola, Cap. 5, **FIGURA 17**, p. 205 — **A)** raddrizzatore a una semionda; **B)** forme d'onda. Nota che il picco d'uscita è $V_{ip} - 0{,}7$: la caduta sul diodo c'è sempre.*

- **Ingresso**: sinusoide alternata $v_{in}(t)$.
- **Uscita**: metà del periodo, solo la semionda positiva; l'altra metà è bloccata dal diodo.
- **Valore medio**: $\overline{V_o} = \dfrac{V_p}{\pi}$ (trascurando la caduta di 0,7 V) — Mirandola §2.1, p. 205.

### Raddrizzatore a ponte (Graetz)

![[libro-cap5-p206-fig19-ponte-di-graetz.png]]
*Mirandola, Cap. 5, **FIGURA 19**, p. 206 — **A)** ponte di Graetz; **B)** forme d'onda. Il picco d'uscita è $V_{2p} - 1{,}4$, non $V_{2p}-0{,}7$: ci sono **sempre due diodi in serie** al carico.*

- **Ingresso**: sinusoide alternata $v_{in}(t)$.
- **Uscita**: **entrambe** le semionde rese positive (doppia semionda).
- **Valore medio**: $\overline{V_o} = \dfrac{2V_p}{\pi}$ — **doppio** rispetto alla semionda.
- **Quali diodi conducono**: nelle semionde positive $D_1$ e $D_3$; nelle negative $D_2$ e $D_4$. In entrambi i casi la corrente attraversa il carico **nello stesso verso** — ed è esattamente questo il trucco del ponte.

> [!tip] Perché Graetz e non il trasformatore a presa centrale?
> Esiste un'alternativa a doppia semionda con **2 soli diodi** e un trasformatore a **presa centrale** (Mirandola, FIGURA 18, p. 206), con lo stesso valore medio $2V_p/\pi$.
>
> Il libro spiega perché in pratica si preferisce **Graetz**: a parità di condizioni richiede **metà degli avvolgimenti** sul secondario del trasformatore. Il trasformatore è il componente più costoso e ingombrante dell'alimentatore — risparmiare rame lì vale più che risparmiare due diodi, che costano pochi centesimi e si comprano già pronti in un unico contenitore a 4 terminali.

Passaggio chiave: in un ponte, **due diodi sono sempre ON** (uno per ramo) e **cadono di $\approx 0{,}7$ V ciascuno**, quindi in totale $\approx 1{,}4\ \text{V}$.

> [!check] La tensione di uscita di un ponte
> Per un ingresso con valore di picco $V_{in,p}$, la tensione di uscita a vuoto è:
>
> $$|V_{out,p}| = V_{in,p} - 2 V_D$$
>
> Il "−2 $V_D$" è la caduta di tensione sui due diodi in serie. Sotto carico, $V_{out}$ cala leggermente per via della resistenza interna dei diodi e di $R_S$.

### Raddrizzatore con filtro a condensatore

> Il condensatore di filtro all'uscita del ponte è trattato da Mirandola nella **GUIDA ALLA PROGETTAZIONE** di fine capitolo (Cap. 5, **pp. 226-229**); la formula di dimensionamento è nella tabella **«Formule»**, **p. 229**.

Il condensatore si carica al valore di picco, poi si scarica lentamente attraverso la resistenza di carico. L'uscita diventa una tensione quasi continua con un piccolo **ripple** sovrapposto:

- $V_{DC} \approx V_{in,p} - 2 V_D$ (per ponte con filtro)
- $V_{ripple,pp} \approx \dfrac{I_{load}}{f_r \cdot C}$, dove $f_r = 2 f_{line}$ (per ponte) o $f_r = f_{line}$ (semionda)

> [!check] La stessa formula, nella forma del libro
> Mirandola la scrive **girata**, come formula di **progetto** (tabella «Formule», p. 229):
>
> $$C = I_{L\max} \cdot \frac{\Delta t}{V_{RPP}}$$
>
> dove $\Delta t$ è il **periodo del segnale raddrizzato** e $V_{RPP}$ il ripple picco-picco voluto. È identica alla precedente: basta ricordare che $\Delta t = 1/f_r$, quindi $V_{RPP} = I_{L\max}/(f_r C)$.
>
> Le due versioni rispondono a domande diverse — **«che ripple avrò?»** (analisi) vs **«che condensatore devo comprare?»** (progetto). All'esame può arrivarti in entrambe le forme.
>
> ⚠️ Per la **rete italiana a 50 Hz**: ponte → $f_r = 100$ Hz e $\Delta t = 10$ ms; semionda → $f_r = 50$ Hz e $\Delta t = 20$ ms.

> [!tip] Il ripple decresce con la costante di tempo $RC$
> Maggiore è $C$ o minore è $I_{load}$, più "liscia" è la tensione di uscita. In laboratorio è facile verificarlo collegando l'oscilloscopio: vedi la sinusoide livellata sovrapposta a piccole oscillazioni residue.

---

## 6. Limitatori di tensione (clipper)

> Il **limitatore** (*clipper*) è definito da Mirandola in Cap. 5, **§2.6, pp. 210-211**. I circuiti "parenti" — **rivelatore di picco** (§2.2, p. 207, FIGURA 20), **rivelatore d'inviluppo** (§2.3, p. 208, FIGURA 21), **fissatore/clamper** (§2.4, p. 208, FIGURE 22, formule 5.5-5.6) e **moltiplicatore di tensione** (§2.5, p. 209) — sono nell'immagine sotto.

![[libro-cap5-pp208-209-fissatore-moltiplicatore.png]]
*Mirandola, Cap. 5, **pp. 208-209** — **FIGURA 21**: rivelatore d'inviluppo e demodulazione AM; **§2.4** il fissatore (*clamper*), con $v_o = v_i + V_{ip}$ (5.5) e $v_o = v_i - V_{ip}$ (5.6) a seconda del verso del diodo; **§2.5** duplicatore/triplicatore di tensione.*

> [!tip] Limitatore vs fissatore — la confusione classica
> Si somigliano ma fanno cose opposte:
> - **Limitatore** (*clipper*): **taglia** la parte di segnale che supera una soglia. L'ampiezza in uscita è **ridotta**.
> - **Fissatore** (*clamper*): **trasla** tutto il segnale sommandogli una continua pari al picco. L'ampiezza resta **la stessa**, cambia il livello attorno a cui oscilla.
>
> Regola mnemonica: il clipper *toglie*, il clamper *sposta*.

### La definizione del libro (§2.6, p. 210)

> Il **limitatore** (*clipper*) è un **quadripolo** che riduce la possibilità di escursione della tensione d'uscita a un **campo di valori prefissato**; se la tensione d'ingresso rimane all'interno di tale campo la tensione d'uscita è **identica** a quella d'ingresso, mentre per valori d'ingresso **esterni** l'uscita rimane **fissa al valore di soglia**.

### I due usi (p. 211)

Il libro ne dichiara **due**, e vanno detti entrambi:

1. **modificare la forma del segnale** (la *tosatura dei picchi*) — l'applicazione spinta è il **formatore di sinusoide** (§2.7, p. 212), che da un'onda triangolare ricava una sinusoide comprimendone i picchi;
2. **proteggere un circuito**, evitando che la tensione al suo **ingresso** raggiunga un valore tale da danneggiarlo.

### I quattro limitatori a bassa soglia (FIGURA 24, p. 211)

![[libro-cap5-p211-fig24-limitatori-bassa-soglia.png]]
*Mirandola, **FIGURA 24**, p. 211 — limitatori a bassa soglia e forme d'onda relative. Studiati con il **modello B**.*

Si dicono **a bassa soglia** perché la soglia è fissata dalla sola caduta sul diodo — nessun generatore. La distinzione che conta è **dove sta il diodo**:

| | Topologia | Funzione | Effetto sull'uscita |
|---|---|---|---|
| **24A** | diodo **in serie** al segnale | impedisce all'uscita di **superare 0 V** | restano le sole semionde **negative**, picco ridotto di 0,7 V |
| **24B** | diodo **in serie**, invertito | impedisce all'uscita di **scendere sotto 0 V** | restano le sole semionde **positive**, picco ridotto di 0,7 V |
| **24C** | diodo **in parallelo** all'uscita | impedisce all'uscita di **superare 0,7 V** | picchi positivi tosati a +0,7 V, la negativa passa intatta |
| **24D** | diodo **in parallelo**, invertito | impedisce all'uscita di **scendere sotto −0,7 V** | picchi negativi tosati a −0,7 V, la positiva passa intatta |

> [!danger] Correzione 2026-07-28 — la versione precedente di questa sezione era sbagliata
> Diceva: *«Limitatore positivo: diodo verso massa con **catodo sul segnale** → la tensione di uscita non può superare $+0{,}7$ V»*. È **invertito**: con il catodo sul nodo d'uscita e l'anodo a massa, il diodo conduce quando $0 - v_o > 0{,}7$, cioè quando $v_o < -0{,}7$ V — limita quindi il picco **negativo**, non quello positivo.
>
> Mancava inoltre del tutto la distinzione **serie vs parallelo**: la vecchia sezione presentava tre casi tutti shunt, mentre il libro ne dà **quattro** e i primi due hanno il diodo **in serie**. Sono funzioni diverse — con il diodo in serie si elimina **metà segnale**, con il diodo in parallelo si **tosa un picco** lasciando passare il resto.

### Alzare la soglia: diodi in serie, antiparallelo, generatore

![[libro-cap5-p212-fig25-limitatori-serie-antiparallelo.png]]
*Mirandola, **FIGURA 25**, p. 212 — limitatori con diodi: **A)** in serie; **B)** in antiparallelo.*

- **$n$ diodi in serie** (FIGURA 25A) — la soglia diventa $V_s = n \cdot 0{,}7$ V; nel caso in figura i diodi sono 3 e la soglia vale **2,1 V**. **Scopo: alzare la soglia di limitazione.**
- **Due diodi in antiparallelo** (FIGURA 25B) — obbligano la tensione d'uscita a rimanere compresa nella fascia **±0,7 V**. **Scopo: limitare simmetricamente entrambe le polarità** con un solo stadio.

> [!warning] «In serie» qui non vuol dire quel che sembra
> Nella FIGURA 25A i diodi sono **in serie tra loro**, impilati nel ramo verso massa — **non** in serie al segnale (che è il caso 24A/B). La parola è la stessa, i circuiti sono diversi. È la trappola delle domande A-D11 e C-D18 in [[04 - Verifica tipo Carli — Diodi]].

![[libro-cap5-p212-fig26-limitatore-con-generatore.png]]
*Mirandola, **FIGURA 26**, p. 212 — limitatori con generatore di tensione in serie al diodo.*

- **Generatore $E$ in serie al diodo** (FIGURA 26) — la soglia diventa **$V_s = E + 0{,}7$** (26A, passano i valori *inferiori*) oppure **$V_s = E - 0{,}7$** (26B, passano i valori *superiori*). **Al posto del generatore $E$ si utilizza solitamente un diodo Zener** (§4.3).

> [!check] ESEMPIO 5 del libro (p. 212) — le due specifiche
> - **a)** uscita che non deve superare $V_s = 9{,}7$ V → schema **26A** con $E = 9$ V *(9 + 0,7)*;
> - **b)** uscita che non deve scendere sotto $V_s = -1{,}4$ V → schema **26B** con **due diodi in serie e senza generatore** *(2 × 0,7)*.
>
> Il caso b) è la dimostrazione pratica dello scopo dei diodi in serie: la specifica si ottiene **senza generatore**, solo impilando diodi.

> [!tip] Non dimenticare mai la $R$ in serie
> In tutti questi schemi la $R$ non è un dettaglio: senza di lei il diodo che conduce **cortocircuita il generatore**. È su $R$ che cade la differenza $v_i - v_o$, ed è quello che rende il circuito un limitatore invece che un guasto.

---

## Quesiti tipo — Guida rapida

> [!question] Cos'è la barriera di potenziale in una giunzione p-n?
> È il campo elettrico interno che si forma nella zona di contatto tra le regioni **p** ed **n**. Senza polarizzazione esterna, impedisce ai portatori di attraversare la giunzione. Viene "rotta" dalla polarizzazione diretta quando $V \geq V_\gamma$.

> [!question] Quando un diodo conduce?
> Quando la tensione **ai suoi capi** (anodo-catodo) supera $V_\gamma$ (≈ 0,7 V per il silicio) e il verso è concorde (anodo positivo). In tutti gli altri casi è praticamente un circuito aperto.

> [!question] Cos'è il breakdown di un diodo? È distruttivo?
> Il breakdown è il passaggio di corrente in polarizzazione inversa quando la tensione inversa supera $V_{BR}$. **È distruttivo** in un diodo normale (la corrente cresce a valore illimitato, il componente brucia). **Non lo è** in un diodo Zener, progettato per lavorare in quella zona.

> [!question] Perché in un ponte di Graetz servono 4 diodi e non 2?
> Per garantire che la **corrente di carico** scorra sempre nello **stesso verso** sul carico, indipendentemente dal segno di $v_{in}$. Con 2 diodi si rettifica solo una semionda; con il ponte si hanno entrambe.

> [!question] A cosa serve il condensatore di filtro in un raddrizzatore?
> A "livellare" la tensione di uscita: senza filtro, l'uscita del ponte è una doppia semionda rettificata (varia tra 0 e il picco). Con il condensatore, l'uscita diventa una tensione quasi continua — pari al picco, con un piccolo ripple (a causa delle piccole scariche del $C$ durante la pausa tra un picco e il successivo).

---

## 6.b Misurazioni Pratiche (per Protti — laboratorio)

> [!info] Dove serve in pratica
> Questa sezione collega [[L'oscilloscopio]] (misure generiche) ai circuiti con diodi che Protti può chiedere in laboratorio.

Misure tipiche che Protti può chiedere di eseguire su circuiti a diodi, e come farle con l'oscilloscopio:

1. **Misura della caduta di tensione $V_D \approx 0{,}7\text{ V}$**: collega un tester (multimetro in DC) tra i capi del diodo in polarizzazione diretta, con una resistenza in serie per limitare la corrente. Si legge la tensione ai capi del diodo $\approx 0{,}7\text{ V}$ indipendentemente dalla corrente (entro la zona attiva). Se leggi un valore molto diverso, il diodo è guasto (aperto o in corto).

2. **Visualizzazione della curva V-I** (avanzato): usando il generatore di funzione in **sweep** (rampa) e misurando tensione e corrente con due canali dell'oscilloscopio in **X-Y mode** → sullo schermo ottieni la "spezzata" della curva V-I del diodo. Vedi la [[Diodi#3. La curva V-I:spezzata di carico|curva]].

3. **Misura del ripple** di un raddrizzatore con filtro a condensatore: collega l'oscilloscopio in **AC coupling** sull'uscita del filtro → leggi $V_{pp,\text{ripple}} \approx \dfrac{I_{load}}{f_r \cdot C}$ (con $f_r = 2 f_{line}$ per ponte, $f_r = f_{line}$ per semionda). Vedi [[Diodi#5. Il raddrizzatore]].

4. **Misura della tensione di breakdown di uno Zener** (in modo sicuro!): con un alimentatore variabile in serie a una $R_S$ di protezione (es. $470\text{ }\Omega$), alza lentamente la tensione. L'oscilloscopio in **DC coupling** sul catodo dello Zener mostra la tensione stabilizzarsi a $V_Z$ quando lo Zener entra in breakdown.

5. **Visualizzazione di un limitatore (clipper)**: alimenta il circuito con una sinusoide da 5–10 V di picco, accoppia l'oscilloscopio in DC → vedrai la sinusoide "tagliata" a $\pm V_D \approx \pm 0{,}7\text{ V}$. Ottimo esercizio per la misura del **tempo di salita** del diodo (confronto con il caso ideale).

> [!tip] Regola pratica: AC vs DC coupling
> - **DC coupling** → vedi tutta la forma d'onda, inclusa la componente continua (es. tensione di uscita del raddrizzatore).
> - **AC coupling** → blocchi la continua, vedi solo la parte variabile (es. il ripple sopra una tensione media di 12 V).
>
> Vedi anche [[L'oscilloscopio]] per la spiegazione completa.

---

## 7. Da qui in poi

- Prerequisiti: [[Segnali sinusoidali e fasori]], [[Impedenza dei bipoli R, L, C]]
- Applicazione a transistor: [[BJT]]
- Esercizi: [[Esercizi - Diodi]]
