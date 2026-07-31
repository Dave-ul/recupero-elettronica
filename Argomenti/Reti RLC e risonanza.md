---
tags: [recupero, elettronica, corrente-alternata, risonanza]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-22) — Cap. 2 «La corrente alternata», §2.1 «Risonanza serie» pp. 55-56, §2.2 «Risonanza parallelo» pp. 57-58, chiusura a p. 59. Pagg.-PDF 5-7, folio letti dal piè di pagina. Quesito 13 a p. 80."
prove: [scritta, orale, pratica]
---

# Reti RLC e risonanza

> [!info] Dove serve
> La lettera lo nomina **testualmente** per la prova pratica del prof. Protti: «**reti RLC in regime sinusoidale**». Ed è dentro «circuiti in corrente alternata» per lo scritto e l'orale di Carli. Il quesito 13 del libro è esattamente su questo.

Prerequisito: [[Impedenza dei bipoli R, L, C]].

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §5**.

## 1. L'idea: due reattanze che si annullano

Tutto nasce da una constatazione che avevi già in mano dalla nota sull'impedenza:

$$X_L = \omega L \quad\text{(positiva, cresce con } \omega) \qquad\qquad X_C = -\frac{1}{\omega C} \quad\text{(negativa, si riduce con } \omega)$$

Una **cresce** con la frequenza, l'altra **si riduce**. Una è **positiva**, l'altra **negativa**. È inevitabile: esiste **una** frequenza in cui hanno lo stesso modulo e si **cancellano a vicenda**.

Quella frequenza si chiama **frequenza di risonanza**, ed è il fenomeno più spettacolare del capitolo.

---

## 2. Risonanza serie

![[fig-2-11-lc-risonante-serie.png]]
*FIGURA 11 — Circuito LC risonante serie (con resistenza equivalente parassita $R$). (Mirandola, Cap. 2 §2.1, p. 55)*

Un bipolo costituito da un induttore e un condensatore **in serie** è caratterizzato da una pulsazione $\omega_s$ alla quale l'impedenza equivalente **si annulla**.

> **Si definisce in risonanza serie** una serie $LC$ eccitata con la pulsazione $\omega_s = \dfrac{1}{\sqrt{LC}}$; il bipolo si comporta come un **cortocircuito**, in quanto le tensioni sui due componenti sono **uguali in modulo e opposte in fase**.

### La dimostrazione (una riga)

L'espressione di $\omega_s$ si ricava **annullando** l'impedenza equivalente della serie $LC$:

$$\bar{Z}_{eq} = j\omega L - \frac{j}{\omega C} = 0$$

Raccogliendo $j$: $\;\omega L = \dfrac{1}{\omega C}\;\Rightarrow\; \omega^2 = \dfrac{1}{LC}$, e quindi:

$$\boxed{\;\omega_s = \frac{1}{\sqrt{LC}}\;} \tag{2.20}$$

Alla pulsazione di risonanza le reattanze sono **uguali in modulo e di segno opposto**: le tensioni $V_C$ e $V_L$, avendo identica ampiezza ma fase opposta, danno **risultante nulla**, e il bipolo è assimilabile a un cortocircuito.

### Il paradosso, e perché la realtà lo smorza

Qui il libro dice una cosa che va letta con attenzione (p. 55, subito sotto la DIMOSTRAZIONE della 2.20):

> Teoricamente un generatore di tensione alternata che alimenta un circuito risonante serie alla pulsazione $\omega_s$ dovrebbe fornire una **corrente infinita**, quindi l'ampiezza della tensione ai capi di **ognuno** dei due componenti dovrebbe essere **infinita**; in realtà, a causa della resistenza dei conduttori e della bobina e della resistenza d'uscita del generatore, le tensioni sui componenti risultano di valore finito e la tensione d'ingresso non è nulla.

Fermiamoci un secondo, perché è controintuitivo. La serie $LC$ a risonanza è un **cortocircuito**: impedenza zero. Legge di Ohm: $I = V/0 = \infty$. Ma allora sui singoli componenti, che hanno reattanza **non nulla**, cadrebbero tensioni infinite — pur essendo la loro **somma** zero.

Non è un paradosso: è ciò che rende la risonanza utile. **Le tensioni sui singoli componenti possono essere molto più grandi della tensione d'ingresso**, purché opposte in fase. Nella realtà è la resistenza parassita $R$ (quella tratteggiata in FIGURA 11) a limitare tutto: è lei che impedisce alla corrente di divergere.

### Il fattore di qualità serie

Per valutare il peso della componente resistiva $R$, **indesiderata**, rispetto a quella reattiva, si definisce il **fattore di qualità serie $Q$** come rapporto tra il modulo della tensione ai capi di **ognuno** dei componenti reattivi e la tensione d'ingresso (identica a quella sulla resistenza $R$):

$$Q = \frac{|\bar{V}_L|}{|\bar{V}_R|} = \frac{|\bar{V}_C|}{|\bar{V}_R|} = \frac{1}{R}\sqrt{\frac{L}{C}} \tag{2.21}$$

**per cui all'aumentare di $R$ la qualità diminuisce.**

> [!check] La dimostrazione della (2.21), passo per passo
> Il libro la comprime in tre righe. Espansa:
> alla risonanza, i moduli delle tensioni sui reattivi valgono
> $$|V_L| = \omega_s L |I| \qquad |V_C| = \frac{|I|}{\omega_s C}$$
> mentre sulla resistenza parassita $|V_R| = R|I|$. Quindi:
> $$Q = \frac{|V_L|}{|V_R|} = \frac{\omega_s L |I|}{R|I|} = \frac{\omega_s L}{R}$$
> Sostituendo $\omega_s = \dfrac{1}{\sqrt{LC}}$ dalla (2.20):
> $$Q = \frac{L}{R\sqrt{LC}} = \frac{1}{R}\sqrt{\frac{L^2}{LC}} = \frac{1}{R}\sqrt{\frac{L}{C}} \;✅$$
> La corrente $|I|$ si semplifica: **$Q$ non dipende da quanto forte alimenti il circuito**, solo dai componenti. È una proprietà del circuito, non del segnale.

### Il comportamento fuori dalla risonanza

Alla risonanza il bipolo è **puramente resistivo**. Fuori:

- **resistivo-capacitivo** per $\omega < \omega_s$, perché alle basse frequenze $X_L \to 0$;
- **resistivo-induttivo** per $\omega > \omega_s$, perché alle alte frequenze $X_C \to 0$.

> [!tip] Come ricordarlo senza formule
> Sotto la risonanza «vince» il condensatore, sopra «vince» l'induttanza. Torna alla TABELLA 1 di [[Impedenza dei bipoli R, L, C]]: a bassa frequenza la $C$ è un circuito aperto (impedenza enorme, quindi domina lei), ad alta frequenza è la $L$ ad aprirsi. **Chi ha l'impedenza più grande comanda**, perché sono in serie.

---

## 3. Risonanza parallelo (antirisonanza)

![[fig-2-13-lc-risonante-parallelo.png]]
*FIGURA 13 — Circuito LC risonante parallelo (con resistenza equivalente parassita $R$). (Mirandola, Cap. 2 §2.2, p. 57)*

Il **parallelo** di un induttore e un condensatore è caratterizzato da una pulsazione $\omega_p$ che rende **infinita** l'impedenza equivalente.

> **Si definisce in risonanza parallelo** (o **antirisonanza**) un parallelo $LC$ eccitato con la pulsazione $\omega_p = \dfrac{1}{\sqrt{LC}}$; il bipolo si comporta come un **circuito aperto**, poiché le correnti nei due componenti sono **uguali in modulo e opposte in fase**.

### La dimostrazione

Si annulla l'**inverso** dell'impedenza equivalente — perché stavolta vogliamo $Z \to \infty$, cioè $1/Z \to 0$:

$$\frac{1}{\bar{Z}_{eq}} = \frac{1}{\bar{Z}_L} + \frac{1}{\bar{Z}_C} = \frac{1}{j\omega L} + j\omega C = 0$$

$$\frac{1 + j^2\omega^2 LC}{j\omega L} = \frac{1 - \omega^2 LC}{j\omega L} = 0 \;\Longrightarrow\; 1 - \omega^2 LC = 0$$

$$\boxed{\;\omega_p = \frac{1}{\sqrt{LC}}\;} \tag{2.22}$$

**espressione identica a quella ricavata per la risonanza serie.**

> [!warning] Stessa formula, comportamento opposto
> $\omega_s$ e $\omega_p$ hanno **la stessa identica formula** $\dfrac{1}{\sqrt{LC}}$ — ma il bipolo fa l'opposto:
>
> | | Serie | Parallelo |
> |---|---|---|
> | $\bar{Z}_{eq}$ a risonanza | $\to 0$ | $\to \infty$ |
> | si comporta come | **cortocircuito** | **circuito aperto** |
> | si annullano | le **tensioni** ($V_L + V_C = 0$) | le **correnti** ($I_L + I_C = 0$) |
> | diventa grande | la **corrente** | la **tensione** |
> | $Q$ | $\dfrac{1}{R}\sqrt{\dfrac{L}{C}}$ | $R\sqrt{\dfrac{C}{L}}$ |
> | qualità migliore se | $R$ **piccola** | $R$ **grande** |
>
> Ricordare solo la formula non basta: all'orale la domanda è «cosa succede», non «quanto vale $\omega$».

Alla pulsazione di risonanza le reattanze in parallelo sono uguali in modulo e di segno opposto, quindi le correnti $I_C$ e $I_L$, con identica ampiezza ma fase opposta, danno **risultante nulla**.

Nella realtà, a causa delle resistenze parassite, la corrente in ingresso non sarà nulla ma dovrà **ripristinare l'energia dissipata**: è la $R$ tratteggiata in FIGURA 13, percorsa da $I_R$.

### Il fattore di qualità parallelo

$$Q = \frac{|I_L|}{|I_R|} = \frac{|I_C|}{|I_R|} = R\sqrt{\frac{C}{L}} \tag{2.23}$$

che è il **reciproco** della (2.21), **per cui al calare di $R$ la qualità diminuisce**.

> [!check] Attenzione: qui $R$ va nella direzione opposta
> Nella serie, $Q$ migliora se $R$ è **piccola**. Nel parallelo, $Q$ migliora se $R$ è **grande**. Non è una svista del libro: è coerente.
> Il motivo è dove sta la resistenza. Nella serie, $R$ è **in serie** e dissipa la corrente che attraversa tutto: meno resistenza, meno perdite. Nel parallelo, $R$ è **in parallelo** e sottrae corrente al circuito risonante: più è grande, meno corrente le passa, meno perdite.
> In entrambi i casi la sostanza è la stessa: **$Q$ alto = poche perdite = risonanza più marcata e selettiva.**

### La correzione realistica

Il libro aggiunge un'osservazione fine (p. 58, subito dopo la 2.23): a rigore le resistenze parassite $R_L$ e $R_C$ sono **in serie** ai componenti, e questo modifica la pulsazione di risonanza, che si dimostra essere:

$$\omega_p = \frac{1}{\sqrt{LC}}\sqrt{\frac{L - CR_L^2}{L - CR_C^2}}$$

che per $R_L = R_C = 0$ si riduce alla (2.22).

> [!note] Quando serve davvero
> Questa formula è un raffinamento: se le resistenze parassite sono piccole (il caso normale), la frazione sotto radice vale circa 1 e si torna alla formula semplice. Ti serve saperla **esistere** — all'orale può valere la domanda «e se i componenti non fossero ideali?» — ma negli esercizi userai la (2.22).

---

## 4. Gli esempi svolti del libro

### ESEMPIO 3 — Risonanza serie (p. 56, FIGURA 12)

Rete con $V = 3$ V, $R = 100\ \Omega$, $L = 0{,}6$ mH, $C = 180$ nF.

$$\omega_s = \frac{1}{\sqrt{LC}} = \frac{1}{\sqrt{0{,}6\cdot10^{-3}\cdot 180\cdot10^{-9}}} = 96{,}2\cdot10^{3}\ \text{rad/s}$$

$$f_s = \frac{\omega_s}{2\pi} = 15{,}3\ \text{kHz}$$

A questa frequenza la serie $LC$ si comporta come un **cortocircuito**, quindi ai capi di $R$ c'è tutta la tensione del generatore:

$$|I| = \frac{|V|}{R} = \frac{3}{100} = 0{,}03\ \text{A}$$

Le tensioni sui reattivi:

$$|V_C| = \frac{1}{\omega_s C}|I| = \frac{0{,}03}{96{,}2\cdot10^{3}\cdot 180\cdot10^{-9}} = 1{,}7\ \text{V}$$

$$|V_L| = \omega_s L |I| = 96{,}2\cdot10^{3}\cdot 0{,}6\cdot10^{-3}\cdot 0{,}03 = 1{,}7\ \text{V}$$

Le due tensioni sono **uguali in modulo ma di fase opposta**, a causa degli opposti segni delle reattanze. Il libro invita a verificare con Multisim che **al diminuire di $R$** (cioè all'aumentare di $Q$) le tensioni sui reattivi **tendono all'infinito**.

> [!check] Verifica incrociata con il fattore di qualità
> Qui i conti si controllano da soli. Dalla (2.21):
> $$Q = \frac{1}{R}\sqrt{\frac{L}{C}} = \frac{1}{100}\sqrt{\frac{0{,}6\cdot10^{-3}}{180\cdot10^{-9}}} = \frac{1}{100}\sqrt{3333} = \frac{57{,}7}{100} = 0{,}577$$
> E per definizione $Q = |V_L|/|V_R| = 1{,}7/3 = 0{,}567$. ✅ Coincidono, a meno degli arrotondamenti.
>
> Nota che qui $Q < 1$: le tensioni sui reattivi sono **più piccole** di quella d'ingresso. Con $R = 100\ \Omega$ questo circuito ha una risonanza **scadente**. Se $R$ scendesse a $1\ \Omega$, $Q$ salirebbe a 57,7 e sui componenti troveresti **173 V** partendo da 3 V. È così che funziona un circuito di sintonia radio.

### ESEMPIO 4 — Risonanza parallelo (p. 58, FIGURA 14)

Rete con $V = 2$ V, $C = 2{,}2\ \mu$F, $R = 100\ \Omega$, $L = 0{,}01$ mH in parallelo.

$$\omega_p = \frac{1}{\sqrt{LC}} = \frac{1}{\sqrt{0{,}01\cdot10^{-3}\cdot 2{,}2\cdot10^{-6}}} = 213\cdot10^{3}\ \text{rad/s} \qquad f_p = \frac{\omega_p}{2\pi} = 33{,}9\ \text{kHz}$$

A questa frequenza il parallelo $LC$ si comporta come un **circuito aperto**, quindi ai capi di $R$ è presente la tensione del generatore:

$$|I| = \frac{|V|}{R} = \frac{2}{100} = 20\ \text{mA}$$

Le correnti nei componenti reattivi:

$$|I_C| = \omega_p C |V| = 213\cdot10^{3}\cdot 2{,}2\cdot10^{-6}\cdot 2 = 0{,}94\ \text{A}$$

$$|I_L| = \frac{|V|}{\omega_p L} = \frac{2}{213\cdot10^{3}\cdot 0{,}01\cdot10^{-3}} = 0{,}94\ \text{A}$$

Le due correnti sono **uguali in modulo** — e di valore **molto superiore** a $I$ — mentre hanno **fase opposta**, a causa degli opposti segni delle reattanze.

> [!tip] Guarda i numeri: 0,94 A contro 20 mA
> Nel serbatoio $LC$ circolano **47 volte** più ampere di quanti ne entrino dal generatore. È il duale esatto dell'ESEMPIO 3: là erano le tensioni a gonfiarsi, qui sono le correnti.
> Il senso fisico è lo stesso in entrambi i casi: **l'energia rimbalza avanti e indietro tra il condensatore e l'induttanza**, e il generatore deve solo rimpiazzare le briciole dissipate da $R$. Come spingere un'altalena: non devi sollevarla tu, basta una spintarella al momento giusto.

---

## 5. A cosa servono

Il libro chiude il paragrafo così (p. 59, appena prima del §2.3 «Condensatori e induttori reali»):

> Le reti risonanti serie e parallelo sono utilizzate per la realizzazione di vari circuiti elettronici come **oscillatori** e **filtri**; in questi casi la presenza di una componente resistiva, dovuta per esempio alla resistenza dei conduttori o degli avvolgimenti degli induttori, provoca generalmente un **peggioramento delle prestazioni** del circuito.

Il collegamento con la tua prova scritta è diretto: i **filtri RLC del secondo ordine** (libro §3.2 del Cap. 4) sono reti risonanti, e il loro coefficiente di smorzamento $\xi$ è legato al fattore di qualità dalla relazione $\xi = \dfrac{1}{2Q}$. Vedi [[Filtri passivi del primo ordine]].

> [!question] Il quesito 13 del libro (p. 80)
> *«Quando si verificano la risonanza serie e la risonanza parallelo? Quali fenomeni producono?»*
>
> **Quando**: entrambe alla pulsazione $\omega = \dfrac{1}{\sqrt{LC}}$ — stessa formula.
> **Quali fenomeni**: nella **serie** l'impedenza si annulla (cortocircuito), la corrente diventa massima e sui componenti reattivi compaiono tensioni uguali e opposte, potenzialmente molto maggiori di quella d'ingresso. Nel **parallelo** l'impedenza diventa infinita (circuito aperto), la corrente d'ingresso si annulla e nei componenti circolano correnti uguali e opposte, molto maggiori di quella d'ingresso.
> In entrambi i casi, alla risonanza il bipolo è **puramente resistivo**: tensione e corrente sono in fase.

---

## 6. Da qui in poi

- Prerequisiti: [[Segnali sinusoidali e fasori]] · [[Impedenza dei bipoli R, L, C]]
- Poi: [[Il metodo simbolico]] · [[Le potenze in alternata]]
- Applicazione: [[Filtri passivi del primo ordine]] · [[L'oscilloscopio]]
- Esercizi: [[Esercizi - Reti RLC e risonanza]]
