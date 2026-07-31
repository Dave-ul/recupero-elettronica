---
tags: [recupero, elettronica, corrente-alternata, impedenza]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2 (Zanichelli 2012), Cap. 2 «La corrente alternata»: definizione di impedenza (2.13), reattanza/ammettenza (2.14)-(2.17), serie/parallelo (2.18)-(2.19), ESEMPIO 2, condensatore/induttore reale (2.24)-(2.25). pp. 52-61 (pagg.-PDF 4-8). Formule ed esempio controllati fedeli al testo via OCR+lettura pagine (2026-07-19). Vedi [[00 - Fonti e note]]."
prove: [scritta, orale, pratica]
---

# Impedenza dei bipoli R, L, C

> [!info] Dove serve
> **Scritta** e **orale** (Carli): «circuiti in corrente alternata». **Pratica** (Protti): «reti RLC in regime sinusoidale». È il concetto che rende l'alternata gestibile come la continua — e la base di ogni esercizio del capitolo.

Prerequisito: [[Segnali sinusoidali e fasori]].

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §2**.

## 1. Il problema: la frequenza cambia tutto

Il libro parte da un fatto sperimentale (Mirandola, Cap. 2, pp. 52-53):

> Alimentando in alternata una rete contenente bipoli lineari ($R$, $C$, $L$), si verifica che le **ampiezze e le fasi** delle correnti e delle tensioni nei vari punti della rete **dipendono dalla frequenza** dell'alimentazione. Ciò è dovuto al diverso comportamento dei **componenti reattivi** ($L$ e $C$) al variare della frequenza.

Questa è la differenza radicale rispetto alla continua. In una rete di sole resistenze, se raddoppi la frequenza non cambia nulla. Appena metti un condensatore o un'induttanza, **lo stesso circuito si comporta in modo diverso a frequenze diverse**. Tutto il capitolo — e i filtri — nascono da qui.

---

## 2. La derivazione: come sparisce la derivata

Questa è la parte che vale la pena seguire riga per riga, perché è il momento in cui il calcolo differenziale si trasforma in algebra.

### L'induttore

La relazione fisica tra tensione e corrente in un induttore è una **derivata**:

$$v(t) = L\frac{di(t)}{dt} \tag{2.8}$$

Se la corrente è sinusoidale, $i(t) = I\operatorname{sen}(\omega t + \varphi)$, l'espressione della tensione si ottiene derivando e moltiplicando per la costante $L$:

$$v(t) = L\frac{d[I\operatorname{sen}(\omega t + \varphi)]}{dt} = LI\omega\cos(\omega t + \varphi) = LI\omega \operatorname{sen}\!\left(\omega t + \varphi + \frac{\pi}{2}\right)$$

essendo $I$ costante e la derivata di $\operatorname{sen}(\omega t + \varphi)$ pari a $\omega\cos(\omega t + \varphi)$.

Guarda cosa è successo, perché è il cuore di tutto: **la derivata di una sinusoide è ancora una sinusoide**. Cambiano solo due cose:
- l'ampiezza viene moltiplicata per $\omega$;
- la fase avanza di $\pi/2$, perché il coseno è il seno spostato di 90°.

Quindi:

$$v(t) = \omega L I \operatorname{sen}\!\left(\omega t + \varphi + \frac{\pi}{2}\right)$$

Ora il passo decisivo. Sostituendo alle grandezze sinusoidali i numeri complessi rappresentativi, e ricordando che **moltiplicare per $j$ equivale a sfasare di $\pi/2$ in anticipo**, la (2.8) diventa:

$$\bar{V} = j\omega L \bar{I} \tag{2.9}$$

> [!check] Perché $j\omega L$ è esattamente la derivata
> Confronta le due espressioni:
> - «moltiplica l'ampiezza per $\omega$» → il fattore $\omega$
> - «sfasa di $+90°$» → il fattore $j$
> - «moltiplica per $L$» → il fattore $L$
>
> $j\omega L$ **è** l'operazione «derivare e moltiplicare per $L$», scritta come una moltiplicazione. Ecco perché il metodo simbolico funziona: **derivare nel tempo = moltiplicare per $j\omega$ nel dominio dei fasori.**
> Non è un trucco mnemonico: è il motivo per cui le equazioni differenziali diventano equazioni di primo grado.

Dalla (2.9) si legge la fisica: se un induttore con induttanza $L$ è percorso da una corrente sinusoidale di ampiezza $I$ e pulsazione $\omega$, la tensione ai suoi capi è **sfasata in anticipo di 90°** e ha modulo $\omega L I$, quindi **direttamente proporzionale alla pulsazione**.

### Il condensatore

Con un ragionamento analogo, per il condensatore la relazione

$$i(t) = C\frac{dv(t)}{dt} \tag{2.10}$$

si trasforma in campo complesso nella:

$$\bar{I} = j\omega C \bar{V} \tag{2.11}$$

cioè **corrente in anticipo di 90° rispetto alla tensione**, con modulo $\omega C V$.

> [!warning] Nel condensatore è la CORRENTE ad essere in anticipo
> Nota bene la differenza, ed è la fonte di metà degli errori di segno negli esercizi:
> - **Induttore**: la **tensione** è in anticipo di 90° sulla corrente.
> - **Condensatore**: la **corrente** è in anticipo di 90° sulla tensione — cioè la tensione è **in ritardo**.
>
> Un modo per non sbagliare mai: nel condensatore devi prima accumulare carica e poi hai tensione, quindi la tensione «arriva dopo». Nell'induttore devi prima applicare tensione e poi la corrente cresce, quindi la corrente «arriva dopo».

### Il resistore

Per il resistore, **non essendo un componente ad accumulo di energia**, la relazione rimane identica (legge di Ohm) anche in campo complesso:

$$\bar{V} = R\bar{I} \tag{2.12}$$

Niente $j$, niente $\omega$: nessuno sfasamento, nessuna dipendenza dalla frequenza.

### Le tre osservazioni del libro

Dalle (2.9), (2.11) e (2.12) il libro trae tre conclusioni (Mirandola, Cap. 2, p. 52) — sono materiale da orale:

1. Le relazioni tra i numeri complessi di tensione e corrente sono **algebriche**: non presentano derivate né integrali.
2. Tensione e corrente sono **in fase nel resistore**, mentre sono **sfasate di 90°** nei componenti reattivi (tensione in anticipo nell'induttore, in ritardo nel condensatore, rispetto alla corrente).
3. Nel resistore il rapporto tra i moduli dipende **solo dalla resistenza**; nell'induttore o nel condensatore dipende **anche dalla pulsazione**. Per esempio, il modulo della corrente in un condensatore sottoposto a tensione sinusoidale **cresce proporzionalmente a $\omega$**.

---

## 3. La definizione di impedenza

![[fig-2-18-bipolo-e-sfasamento.png]]
*FIGURA 18 — **A)** Bipolo alimentato in alternata. **B)** Sfasamento $\varphi$ tra tensione e corrente dovuto alla componente reattiva del bipolo (Mirandola, Cap. 2; il libro riferisce la definizione (2.13) alla sua FIGURA 8).*

> Si definisce **impedenza di un bipolo** il numero complesso ottenuto come **rapporto** tra i numeri complessi rappresentativi della tensione e della corrente sul bipolo alimentato in alternata:
> $$\bar{Z} = \frac{\bar{V}}{\bar{I}} \tag{2.13}$$

È la legge di Ohm, generalizzata. Ma essendo un **rapporto tra numeri complessi**, per le regole del §3 di [[Segnali sinusoidali e fasori]] porta con sé **due** informazioni invece di una:

- il **modulo** $|\bar{Z}|$ è pari al **rapporto tra i moduli** di tensione e corrente — cioè «quanto» il bipolo si oppone;
- l'**argomento** $\angle\bar{Z}$ è pari allo **sfasamento** tra tensione e corrente — cioè «come» il bipolo sfasa.

> [!tip] L'impedenza in una frase
> **La resistenza dice solo quanto freni. L'impedenza dice quanto freni *e* di quanto sfasi.** Ed è per questo che serve un numero complesso: un numero reale non basterebbe a contenere due informazioni.

Il libro aggiunge una nota pratica sulle frecce nei circuiti (Mirandola, Cap. 2, p. 52): nonostante si tratti di grandezze alternate, tensioni e correnti si rappresentano con delle frecce come in continua; **se il bipolo non introduce sfasamento**, la corrente entra nel verso della freccia quando la tensione è positiva nel verso della freccia.

---

## 4. La tabella da sapere a memoria

![[fig-2-t1-impedenze-r-l-c.png]]
*TABELLA 1 — Espressioni delle impedenze dei bipoli elementari passivi e valori limite per $\omega \to 0$ e $\omega \to \infty$ (Mirandola, Cap. 2, TABELLA 1).*

In forma scritta:

| Componente | Impedenza $\bar{Z}$ | per $\omega \to 0$ (continua) | per $\omega \to \infty$ (alta frequenza) |
|---|---|---|---|
| **R** | $R$ | $R$ | $R$ |
| **L** | $j\omega L$ | $\to 0$ — **cortocircuito** | $\to \infty$ — **circuito aperto** |
| **C** | $\dfrac{1}{j\omega C} = -\dfrac{j}{\omega C}$ | $\to \infty$ — **circuito aperto** | $\to 0$ — **cortocircuito** |

Il libro commenta: il modulo dell'impedenza di un condensatore **aumenta alle basse frequenze** e **diminuisce alle alte**; all'aumentare della frequenza il condensatore **conduce sempre di più**. Ai limiti, in continua è un circuito aperto (impedenza infinita), alle alte frequenze un cortocircuito (impedenza trascurabile).

> [!tip] Questa tabella è il tuo strumento più redditizio
> Le due righe di $L$ e $C$ sono l'**esatto opposto** l'una dell'altra, ed è tutto ciò che serve per:
> - capire al volo se un circuito è un **passa basso o un passa alto**, senza fare un conto (vedi [[Filtri passivi del primo ordine]] §5.2);
> - risolvere gli esercizi «a regime in continua», dove basta aprire le C e cortocircuitare le L;
> - fare il **controllo di sanità** su qualunque risultato: calcola cosa deve succedere a $\omega\to0$ e $\omega\to\infty$ e verifica che la tua formula lo faccia.
>
> Se impari solo una tabella di questo capitolo, impara questa.

### Resistenza, reattanza, ammettenza

L'impedenza si scompone in parte reale e parte immaginaria:

$$\bar{Z} = R + jX \tag{2.14}$$

dove $R$ è la **resistenza** (parte reale) e $X$ la **reattanza** (parte immaginaria).

L'inverso dell'impedenza è l'**ammettenza**:

$$\bar{Y} = \frac{1}{\bar{Z}} = G + jS \tag{2.15}$$

composta dalla **conduttanza** $G$ e dalla **suscettanza** $S$.

Per l'induttore, $\bar{Z}_L = jX_L = j\omega L$, quindi la **reattanza induttiva è positiva**:

$$X_L = \omega L \tag{2.16}$$

Per il condensatore, $\bar{Z}_C = jX_C = j\left(-\dfrac{1}{\omega C}\right)$, quindi la **reattanza capacitiva è negativa**:

$$X_C = -\frac{1}{\omega C} \tag{2.17}$$

> [!check] Il segno della reattanza è una diagnosi immediata
> Guarda la parte immaginaria di $\bar{Z}$ e sai subito che tipo di bipolo hai davanti:
> - $X > 0$ → prevale l'**induttanza** → la tensione è **in anticipo** sulla corrente → $\varphi > 0$
> - $X < 0$ → prevale la **capacità** → la tensione è **in ritardo** sulla corrente → $\varphi < 0$
> - $X = 0$ → il bipolo è **puramente resistivo** → tensione e corrente in fase → è la condizione di **risonanza** (vedi [[Reti RLC e risonanza]])
>
> Negli esercizi sulle potenze questo determina il **segno di $Q$**: reattanza negativa → potenza reattiva negativa. Vedi [[Le potenze in alternata]].

---

## 5. Serie e parallelo: le formule di sempre

![[fig-2-09-impedenze-serie-parallelo.png]]
*FIGURA 9 — Impedenze: **A)** in serie; **B)** in parallelo (Mirandola, Cap. 2, FIGURA 9).*

L'impedenza equivalente di più bipoli si calcola con formule **formalmente identiche** a quelle dei resistori:

$$\text{Serie:}\qquad \bar{Z}_{eq} = \bar{Z}_1 + \bar{Z}_2 + \bar{Z}_3 \tag{2.18}$$

$$\text{Parallelo:}\qquad \frac{1}{\bar{Z}_{eq}} = \frac{1}{\bar{Z}_1} + \frac{1}{\bar{Z}_2} + \frac{1}{\bar{Z}_3} \tag{2.19}$$

> [!info] «Formalmente identiche» è la ricompensa
> Tutto il lavoro fatto con i fasori serve a questo: **non devi imparare niente di nuovo**. Serie, parallelo, partitore di tensione, Kirchhoff, Thévenin, Millman — tutti i teoremi della continua valgono identici, a patto di sostituire i numeri reali con i numeri complessi.
> L'unica cosa che cambia è che i conti si fanno con i complessi. È il messaggio centrale de [[Il metodo simbolico]].

---

## 6. L'esempio svolto del libro

**ESEMPIO 2** (Mirandola, Cap. 2, ESEMPIO 2, pp. 53-54). Calcolare modulo e argomento dell'impedenza equivalente del bipolo di FIGURA 10 alla frequenza $f = 1$ kHz, con $C = 100$ nF, $L = 1$ mH, $R = 2{,}2$ k$\Omega$ (il parallelo $R$–$L$ in serie a $C$).

**Il parallelo $R$–$L$:**

$$\bar{Z}_{RL} = \frac{\bar{Z}_R \cdot \bar{Z}_L}{\bar{Z}_R + \bar{Z}_L} = \frac{R\cdot j\omega L}{R + j\omega L}$$

Per eliminare $j$ dal denominatore si moltiplica numeratore e denominatore per il **coniugato** $(R - j\omega L)$, e ricordando che $j\cdot j = -1$:

$$\bar{Z}_{RL} = \frac{j\omega R L(R - j\omega L)}{(R + j\omega L)(R - j\omega L)} = \frac{\omega^2 R L^2}{R^2 + \omega^2 L^2} + j\frac{\omega R^2 L}{R^2 + \omega^2 L^2}$$

Aggiungendo il condensatore in serie:

$$\bar{Z}_{eq} = \bar{Z}_C + \bar{Z}_{RL} = \frac{\omega^2 R L^2}{R^2 + \omega^2 L^2} + j\left(\frac{\omega R^2 L}{R^2 + \omega^2 L^2} - \frac{1}{\omega C}\right)$$

**Numeri.** La pulsazione vale $\omega = 2\pi f = 6280$ rad/s. Sostituendo:

$$\bar{Z}_{eq} = 17{,}9\cdot10^{-3} - j\,1{,}59\cdot10^{3}$$

$$|\bar{Z}_{eq}| = \sqrt{(17{,}9\cdot10^{-3})^2 + (1{,}59\cdot10^{3})^2} = 1{,}59\cdot10^{3}\ \Omega$$

L'argomento, essendo nel **4° quadrante** ($a > 0$, $b < 0$):

$$\angle\bar{Z}_{eq} = \arctan\frac{-1{,}59\cdot10^{3}}{17{,}9\cdot10^{-3}} + 2\pi = 4{,}71\ \text{rad} = 270° \;\left(= \tfrac{3}{2}\pi\ \text{rad}\right)$$

Applicando una tensione di 1 V$_{eff}$ a 1 kHz, la corrente vale:

$$I = \frac{V}{|Z_{eq}|} = \frac{1}{1{,}59\cdot10^{3}} = 0{,}629\ \text{mA}$$

e la differenza di fase è 270° (tensione in anticipo di 270° sulla corrente), **che equivale a dire che la tensione è in ritardo di 90°** sulla corrente.

> [!check] Tre cose da imparare da questo esempio
> **1. Il coniugato è la mossa standard.** Ogni volta che hai $j$ al denominatore, moltiplica sopra e sotto per il coniugato: il denominatore diventa reale — $(a+jb)(a-jb) = a^2+b^2$ — e puoi separare parte reale e immaginaria. È il passaggio che ricorre in **ogni** esercizio sulle impedenze.
>
> **2. Il risultato dice che a 1 kHz vince il condensatore.** La parte reale è $0{,}018\ \Omega$, quella immaginaria $-1590\ \Omega$: la reattanza è quasi centomila volte più grande della resistenza, ed è **negativa**. Il bipolo è di fatto un condensatore puro, e infatti lo sfasamento è $-90°$.
> Perché? A 1 kHz, $X_L = \omega L = 6{,}3\ \Omega$ è piccolissima rispetto a $R = 2200\ \Omega$: nel parallelo, **l'induttanza cortocircuita la resistenza**. Resta solo la $C$ in serie. La TABELLA 1 lo prevedeva.
>
> **3. Attenzione a 270° e $-90°$**: sono lo stesso angolo, e vanno letti come «tensione in ritardo di 90°». Il $+2\pi$ della (2.3) è la ragione per cui esce 270° invece di $-90°$.

---

## 7. Condensatori e induttori reali

Il §2.3 del libro (Mirandola, Cap. 2, «Condensatori e induttori reali», pp. 59-61) aggiunge una dose di realtà:

> Come già accennato, le descrizioni dei condensatori e degli induttori sintetizzate nella TABELLA 1 si riferiscono a un funzionamento **ideale** di tali componenti. La loro struttura reale comporta la presenza di **parametri parassiti**.

### Il condensatore reale

![[fig-2-15-condensatore-reale.png]]
*FIGURA 15 — Condensatore: **A)** ideale; **B)** circuito equivalente reale; **C)** circuiti equivalenti serie e parallelo per $f \ll f_r$ (Mirandola, Cap. 2, FIGURA 15).*

Nel circuito equivalente (FIGURA 15B), $R'$ e $L$ rappresentano **la resistenza e l'induttanza dei reofori e delle armature**, mentre $R''$ tiene conto delle **perdite nel dielettrico**.

La presenza contemporanea di $L$ e $C$ individua una **frequenza di risonanza** $f_r = \dfrac{1}{2\pi\sqrt{LC}}$ alla quale il comportamento del componente è **puramente resistivo**. Alla frequenza d'utilizzo, che deve essere molto inferiore a quella di risonanza, l'effetto di $L$ è trascurabile e ci si riconduce alle forme serie o parallelo della FIGURA 15C.

Per quantificare l'incidenza della resistenza parassita si introduce il **fattore di perdita** ($\operatorname{tg}\delta$):

$$\operatorname{tg}\delta = \frac{R_s}{X_C} = \omega C R_s = \frac{X_C}{R_P} = \frac{1}{\omega C R_P} \tag{2.24}$$

che risulta tanto più **piccolo** quanto minore è l'effetto della resistenza parassita ($R_s$ piccola o $R_P$ grande), e **dipende da $\omega$**.

### L'induttore reale

![[fig-2-16-induttore-reale.png]]
*FIGURA 16 — Induttore: **A)** ideale; **B)** circuito equivalente reale; **C)** circuiti equivalenti serie e parallelo per $f \ll f_r$ (Mirandola, Cap. 2, FIGURA 16).*

Nel circuito equivalente (FIGURA 16B), $R$ esprime le **perdite ohmiche, magnetiche e dielettriche**, mentre $C$ tiene conto della **capacità distribuita tra le spire**.

Anche qui c'è una frequenza di risonanza $f_r = \dfrac{1}{2\pi\sqrt{LC}}$, al di sotto della quale si trascura la capacità parassita.

Il **fattore di merito** ($Q$) si definisce:

$$Q = \frac{X_L}{R_s} = \frac{\omega L}{R_s} = \frac{R_P}{X_L} = \frac{R_P}{\omega L} \tag{2.25}$$

che risulta tanto più **grande** quanto minore è l'effetto della resistenza parassita ($R_s$ piccola o $R_P$ grande).

> [!question] Il quesito 14 del libro
> *«Quali sono i circuiti equivalenti dei condensatori e degli induttori reali? Con quali parametri viene valutata la loro purezza?»*
>
> La risposta sta tutta qui: i circuiti equivalenti sono quelli delle FIGURE 15 e 16, e i parametri di purezza sono il **fattore di perdita $\operatorname{tg}\delta$** per il condensatore (più è **piccolo**, più è puro) e il **fattore di merito $Q$** per l'induttore (più è **grande**, più è puro).
> Nota la simmetria e non confonderli: come logica sono uno l'inverso dell'altro. Un condensatore buono ha $\operatorname{tg}\delta \to 0$; un induttore buono ha $Q \to \infty$.

---

## 8. Da qui in poi

- Prerequisito: [[Segnali sinusoidali e fasori]]
- Prosegue in: [[Reti RLC e risonanza]] — cosa succede quando $X_L$ e $X_C$ si annullano a vicenda
- Poi: [[Il metodo simbolico]] · [[Le potenze in alternata]]
- Applicazione: [[Filtri passivi del primo ordine]]
- Esercizi: [[Esercizi - Impedenza dei bipoli R, L, C]]
