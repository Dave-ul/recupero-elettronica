---
tags: [recupero, elettronica, verifiche, carli, fonte-primaria, checkpoint]
fonte: "tre verifiche scritte del Prof. Carlo Carli, svolte da Alessio Fusi (4BE), corrette a mano e restituite"
file: "Fonti/FUSI_02-03-26… · Fonti/FUSI_24-04-26… · Fonti/FUSI_29-05-26…"
aggiunto: 2026-08-19
verificato: "2026-08-19 — tutte e 56 le pagine dei tre fascicoli lette come immagini (pdftoppm 110 dpi); i PDF non hanno strato di testo"
---

# 05 — Le tre verifiche del prof. Carli

> [!important] Perché questa è la pagina più importante del vault
> Tutto il resto del vault è **materiale analogo** a quello che potrebbe uscire. Queste
> tre no: sono le **prove vere dello stesso docente che correggerà a settembre**, con le
> sue annotazioni in rosso, la sua griglia di valutazione e — sui retro di alcune pagine —
> **le sue soluzioni scritte di suo pugno**.
>
> Per autorevolezza vengono subito dopo la LETTERA, e prima del libro e di Edutecnica:
> vedi [[00 - Fonti e note]] §2.

> [!warning] Di chi sono questi fogli
> Non sono tuoi. Sono le verifiche di **Alessio Fusi, 4BE, n. 3 di registro** — nome
> scritto in testa a ogni fascicolo, firma dell'alunno sul foglio delle condizioni, nome
> sulle tre griglie di valutazione. Da qui il prefisso `FUSI_` dei file.
>
> Cambia come si leggono, e non le rende meno preziose: **non** sono la lista degli errori
> di Davide, **sono la lista di come Carli formula, corregge e valuta** — e, per gli
> esercizi che il prof. ha risolto lui stesso, il **procedimento che si aspetta di vedere**.
> Gli errori di Fusi restano utili come campionario di trappole, non come diagnosi
> personale.

---

## Le tre verifiche

| Verifica | File | Pagine | Data della prova | Argomenti | Esiti | Voto | Dove nel calendario |
|---|---|---|---|---|---|---|---|
| **02-03** | `Fonti/FUSI_02-03-26_260616_183723.pdf` | 18 | **13/02/2026**, valutata 02/03 | circuiti in alternata + filtri del 1° ordine · **6 esercizi** | 1 ~OK · 2 errati · 1 non svolto · 1 OK · 1 ~OK | **3/10** (3,00 punti) | giorni **1** (20 ago, es. 1 e 6) e **4** (23 ago, integrale) |
| **24-04** | `Fonti/FUSI_24-04-26_260616_183749.pdf` | 18 | **24/04/2026**, valutata 09/05 | BJT: polarizzazione, progetto, commutazione, amplificatore · **7 esercizi** | 2 ~OK · 3 errati · 2 non svolti | **3/10** (1,50 punti) | giorno **7** (26 ago, tutti e 7) |
| **29-05** | `Fonti/FUSI_29-05-26_260616_183828.pdf` | 20 | **29/05/2026**, valutata 03/06 | JFET canale N (es. 1-5) + MOSFET enhancement (es. 6-8) · **8 esercizi** | 4 ~OK · 1 errato · 3 non svolti | **3/10** (3,00 punti) | giorni **9** (28 ago, es. 1-5) e **10** (29 ago, es. 6-8) |

E tutte e tre di seguito, sotto timer unico, nel pomeriggio del **giorno 11** (30 agosto):
è l'unica sessione lunga del piano, e serve a sapere com'è stare cinque ore sui conti.

> [!info] Com'è fatto un fascicolo (verificato pagina per pagina)
> - **Pagine dispari 1-7/9**: il **testo** degli esercizi, scritto a mano dal prof., con le
>   crocette rosse e il giudizio di ogni esercizio in testa.
> - **Pagine dispari 9-15**: lo **svolgimento dell'alunno**, numerato «1/3, 2/3, 3/3».
> - **Alcune pagine pari** (i retro): le **soluzioni e le correzioni del prof.** — sono
>   trascritte qui sotto. Le altre pagine pari sono bianche.
> - **Penultima pagina dispari**: la **griglia di valutazione** con punteggio per esercizio.
> - **Ultima pagina dispari**: il foglio delle **condizioni di svolgimento** firmato.
>
> Correzione di una versione precedente di questa nota: le ultime pagine **non** contengono
> lo svolgimento corretto — contengono griglia e regolamento. Le soluzioni del prof. stanno
> sui **retro** delle pagine dello svolgimento (02-03 p. 10 e 12 · 24-04 p. 10, 12, 14 ·
> 29-05 p. 12 e 14).

---

## 🔴 Esercizio per esercizio, come l'ha valutato Carli

Tabella ricostruita **leggendo i tre fascicoli**, non dal calendario. La colonna «punti» è
quella della griglia firmata dal prof.

### FUSI 02-03 (13/02/2026) — alternata e filtri · totale 3,00/10

| Es. | Cosa chiede | Giudizio | Punti | Nota del prof. |
|---|---|---|---|---|
| **1** | modulo e argomento di $\bar{Z}$ di due bipoli: (a) C+R serie, $C=10$ nF, $R=1$ k$\Omega$, $f=10$ kHz · (b) R+L, $R=330\ \Omega$, $L=12$ mH | ~OK | 0,50/2,00 | segno di $\bar{Z}_C$ sbagliato e $\bar{Z}_{eq}$ ricopiata male (vedi sotto) |
| **2** | **i poli** di $G(s)=\dfrac{3}{s^2+5s+6}$ e $G(s)=\dfrac{s+1}{3s(s+5)}$ | **ERRATO** | 0,00/1,00 | «completamente errato, in quanto è stata errata la consegna dell'esercizio stesso»: Fusi ha calcolato l'argomento di $G$ invece dei poli |
| **3** | risposta in ampiezza e fase di un quadripolo $R_1$–($R_2\parallel L$), a $f=0$, 100 kHz, 20 MHz | ~OK | 0,50/1,00 | «si deve indicare innanzitutto l'espressione della risposta in frequenza $G(j\omega)=V_o(j\omega)/V_i(j\omega)$» |
| **4** | **funzione di trasferimento** di due quadripoli: (a) R serie–L parallelo, $R=560\ \Omega$, $L=3$ mH · (b) L serie–R parallelo, $L=0{,}3$ mH, $R=1{,}2$ k$\Omega$ | **ERRATO** | 0,00/2,00 | ha scritto $V_o = V_i\cdot Z_{eq}$ invece del **partitore**; e ha usato un condensatore dove il circuito ha un'induttanza |
| **5** | **frequenza di taglio** di due filtri: (a) C serie–R parallelo, $C=150$ nF, $R=6{,}8$ k$\Omega$ · (b) R serie–C parallelo, $R=1$ k$\Omega$, $C=2{,}2\ \mu$F | ⛔ **NON SVOLTO** | 0,00/2,00 | — |
| **6** | $\bar{Z}_{eq}$ di quattro impedenze: $\bar{Z}_1=2+j6$, $\bar{Z}_2=2-j2$, $\bar{Z}_3=j10$, $\bar{Z}_4=2+j4$ | **OK** | 2,00/2,00 | l'unico esercizio pieno delle tre verifiche |

### FUSI 24-04 (24/04/2026) — BJT · totale 1,50/10

| Es. | Cosa chiede | Giudizio | Punti | Nota del prof. |
|---|---|---|---|---|
| **1** | $V_{CE}$, $I_C$, $I_B$ con $V_{CC}=12$ V, $R_C=820\ \Omega$, $V_{BB}=5$ V, $R_B=56$ k$\Omega$, $h_{FE}=100$ | ~OK | 0,50/1,50 | $I_B$ e $I_C$ giusti; $V_{CE}$ errato per aver sostituito 10 V al posto di $V_{CC}=12$ V |
| **2** | progetto di $R_C$ e $R_B$ per $V_{CE0}=4{,}8$ V, $I_{C0}=14$ mA, $V_{CC}=10$ V, $h_{FE}=100$ | ~OK | 1,00/1,50 | risultati giusti ($R_C=371\ \Omega$, $R_B=66$ k$\Omega$), ma relazione di partenza sbagliata e passaggio non spiegato |
| **3** | **progetto polarizzazione + stabilizzazione** (partitore $R_1$/$R_2$ + $R_E$) per $I_{C0}=10$ mA, $V_{CC}=10$ V, $h_{FE\min}=75$ | **ERRATO** | 0,00/1,50 | soluzione del prof. sul retro — è la ricetta riportata più sotto |
| **4** | **interfaccia porta TTL (0÷5 V) – bobina di relè** 12 V / 70 mA, $h_{FE\min}=75$ | ⛔ **NON SVOLTO** | 0,00/1,00 | — |
| **5** | **capacità di by-pass $C_E$** di un CE con $R_E=1$ k$\Omega$, banda 50 Hz ÷ 8 kHz | ⛔ **NON SVOLTO** | 0,00/1,00 | — |
| **6** | verificare la **saturazione**: $V_{CC}=10$ V, $h_{FE}=50$, $R_B=5{,}2$ k$\Omega$, $R_C=0{,}33$ k$\Omega$, $V_{BE}=0{,}8$ V, $V_{CEsat}=0{,}2$ V | **ERRATO** | 0,00/2,00 | procedura del prof. sul retro — vedi sotto |
| **7** | punto di lavoro con $R_E$: $V_{CC}=20$ V, $V_{BB}=10$ V, $R_C=300\ \Omega$, $R_E=200\ \Omega$, $R_B=20$ k$\Omega$, $h_{FE}=100$ | **ERRATO** | 0,00/1,50 | maglia d'uscita scritta senza $V_{CE}$; «perché non ha continuato lo svolgimento dell'esercizio?» |

### FUSI 29-05 (29/05/2026) — JFET e MOSFET · totale 3,00/10

| Es. | Cosa chiede | Giudizio | Punti | Nota del prof. |
|---|---|---|---|---|
| **1** | progetto $R_D$, $R_S$, $R_G$ · JFET, $V_{DD}=12$ V, $I_{D0}=8$ mA, $V_{GS0}=-1$ V, $V_{DS0}=7$ V | ~OK | 0,75/1,00 | $R_D$ e $R_S$ OK; **$R_G$ errato** — la correzione è il punto più istruttivo dei tre fascicoli |
| **2** | progetto $R_S$, $R_D$, $R_G$ con Shockley: $V_{DD}=18$ V, $I_{D0}=5$ mA, $V_{DS0}=10$ V, $V_P=5$ V, $I_{DSS}=12$ mA | ~OK | 0,75/1,50 | «relazioni usate corrette ma errati tutti i calcoli» |
| **3** | $V_{GG}$ e $V_{DD}$ dati $I_{D0}=5$ mA, $V_{DS0}=10$ V, $V_{GS0}=-2$ V, $R_D=6$ k$\Omega$ (polarizzazione a due alimentazioni) | ⛔ **NON SVOLTO** | 0,00/1,00 | — |
| **4** | punto di lavoro e $V_{DD}$: $I_{DSS}=12$ mA, $V_P=-4{,}5$ V, $V_{DS0}=10$ V, $V_{GS0}=-2$ V, $R_D=2{,}7$ k$\Omega$ | ⛔ **NON SVOLTO** | 0,00/1,00 | — |
| **5** | progetto $R_S$, $R_1$, $R_2$ con partitore di gate: $I_{D0}=35$ mA, $V_{GS0}=-1{,}5$ V, $V_{DS0}=11$ V, $V_{DD}=25$ V, $R_1+R_2=2$ M$\Omega$, $R_D=3$ k$\Omega$ | ⛔ **NON SVOLTO** | 0,00/1,50 | — |
| **6** | punto di lavoro MOSFET: $V_{DD}=15$ V, $R_1=1{,}27$ k$\Omega$, $R_2=825$ k$\Omega$, $R_D=1{,}8$ k$\Omega$, $K=0{,}6$ mA/V², $V_t=3$ V | ~OK | 0,75/1,50 | il prof. rifà tutto il calcolo sul retro: vedi sotto |
| **7** | **progetto** MOSFET: $V_{DD}=25$ V, $I_D=3$ mA, $K=0{,}3$ mA/V², $V_t=4$ V, $R_1+R_2=10$ M$\Omega$ | ~OK | 0,75/1,50 | «**errata relazione che fornisce $V_{GS}$** e ragionamento per stimare $V_{DS}$» |
| **8** | progetto con $R_S$: $I_{D0}=8$ mA, $V_{GS0}=6$ V, $V_{DS0}=10$ V, $V_{DD}=15$ V, $V_S=3$ V, $R_1+R_2=2$ M$\Omega$ | **ERRATO** | 0,00/1,00 | dimenticato che **il source non è a massa**: vedi sotto |

---

## 🟢 Le soluzioni scritte dal prof. — da imparare così come sono

Queste sei correzioni sono la parte di maggior valore dell'intero materiale: sono il
**procedimento che Carli si aspetta di vedere sul foglio**, con le sue parole.

### 1. Progetto della polarizzazione a partitore (24-04, es. 3)

Con $V_{CC}=10$ V, $I_{C0}=10$ mA, $h_{FE\min}=75$, $V_{BE}=0{,}7$ V:

$$R_E = \frac{V_{CC}}{10\,I_{C0}} = \frac{10}{10\cdot 10\text{ mA}} = 100\ \Omega
\qquad
R_C = \frac{0{,}9\,V_{CC}}{2\,I_{C0}} = \frac{9\cdot 10}{20\cdot 10\text{ mA}} = 450\ \Omega$$

$$V_{B0} = V_{BE} + R_E I_{C0} = 0{,}7 + 1 = 1{,}7\text{ V}
\qquad
I = 10\,I_B = 10\cdot\frac{I_{C0}}{h_{FE\min}} = 10\cdot\frac{10\text{ mA}}{75} = 1{,}3\text{ mA}$$

$$R_2 = \frac{V_{B0}}{I} = 1{,}3\text{ k}\Omega
\qquad
R_1 = \frac{V_{CC}-V_{B0}}{I} = \frac{10-1{,}7}{1{,}3\text{ mA}} = 6{,}4\text{ k}\Omega$$

> [!tip] È la stessa procedura del libro
> $V_{RE}=V_{CC}/10$ e $I=10\,I_B$ sono le formule **7.8-7.11** del Mirandola, già in
> [[BJT#b) Polarizzazione con partitore di base e resistore sull'emettitore]]. La novità è
> la scelta di $R_C$: Carli parte da $V_{CE}\simeq V_{CC}/2$, cioè $V_{RC}=0{,}45\,V_{CC}$.
> **Impara le sei righe a memoria**: sono un esercizio intero in meno di dieci minuti.

### 2. Come si verifica la saturazione (24-04, es. 6)

Il prof. scrive la procedura per esteso, in tre passi:

1. **II principio di Kirchhoff alla maglia d'ingresso** → $I_B = \dfrac{V_{CC}-V_{BE}}{R_B}$
2. **II principio di Kirchhoff alla maglia d'uscita** → $I_C = \dfrac{V_{CC}-V_{CEsat}}{R_C}$
3. **Verificare che** $\;I_B > \dfrac{I_C}{h_{FE}}\;$ «affinché il transistor BJT risulti
   effettivamente in saturazione».

> [!danger] L'errore da non ripetere
> Fusi aveva scritto $V_{CC} = R_B I_B + R_C I_C$. Il prof.: «errato perché l'equazione
> contiene al suo interno sia un elemento della maglia di ingresso che è $R_B$ sia un
> elemento della maglia di uscita $R_C$». **Le due maglie non si mescolano mai in una sola
> equazione.** Lo stesso errore torna nell'es. 2 della stessa verifica.
> Vale anche il richiamo degli appunti Poggi: $I_C = h_{FE} I_B$ **non è valida in
> saturazione**.

### 3. Maglia d'uscita con $R_E$ (24-04, es. 7)

$$V_{CC} = R_C I_{C0} + V_{CE} + R_E I_E$$

Fusi aveva scritto $V_{CC} = R_C I_{C0} + I_E R_E$, **senza $V_{CE}$** — cioè aveva
cancellato il transistor dalla maglia. Il prof. segna «errato» e chiede perché lo
svolgimento si fermi lì.

### 4. $R_G$ nel JFET: **non si calcola, si sceglie** (29-05, es. 1 e 2)

Fusi aveva scritto $R_G = V_{GS}/I_G$ con $I_G = V_{GS}/(R_S+R_D)$, ottenendo 625 $\Omega$.
Il prof. barra entrambe le righe con un doppio «NO» e scrive:

> «$R_G$ si fissa ad esempio al valore $\boxed{R_G = 5\ \text{M}\Omega}$»

Il motivo è fisico: nel JFET la giunzione di gate è **polarizzata inversamente**, quindi
$I_G \approx 0$ e $R_G$ non è percorsa da corrente — non c'è nessuna equazione da cui
ricavarla. Serve solo a dare il riferimento di massa al gate, e si prende grande
(1 ÷ 10 M$\Omega$) per non abbassare la resistenza d'ingresso.

Il resto dell'es. 1 (dato «OK» dal prof.) è il modello di progetto JFET:

$$R_S = -\frac{V_{GS0}}{I_{D0}} = \frac{1}{8\text{ mA}} = 125\ \Omega
\qquad
R_D = \frac{V_{DD}-V_{DS0}-R_S I_{D0}}{I_{D0}} = \frac{12-7-1}{8\text{ mA}} = 500\ \Omega$$

e, quando $V_{GS0}$ non è dato ma ci sono $V_P$ e $I_{DSS}$ (es. 2), la Shockley invertita:

$$V_{GS} = V_P\left(1-\sqrt{\frac{I_D}{I_{DSS}}}\right)$$

### 5. MOSFET: da dove viene $V_{GS}$ (29-05, es. 6 e 7)

Sono **due strade diverse**, e sceglierle male è l'errore che il prof. segna a lettere:

- **Se il partitore di gate è dato** (analisi, es. 6): $V_{GS} = V_{R2} = V_{DD}\dfrac{R_2}{R_1+R_2}$,
  e la parabolica serve solo a ricavare $I_D = K(V_{GS}-V_t)^2$. Sull'es. 6 il prof.
  cancella la formula con la radice e scrive «**NON SERVE**».
- **Se $I_D$ è dato e il partitore è l'incognita** (progetto, es. 7):
  $$V_{GS} = \sqrt{\frac{I_D}{K}} + V_t = \sqrt{\frac{3\text{ mA}}{0{,}3\text{ mA/V}^2}}+4 = 7{,}16\text{ V}$$
  Fusi aveva scritto $\sqrt{I_D/R_D}$ al posto di $\sqrt{I_D/K}$: «relazione errata».

Poi $V_{DS}$ **si sceglie**, rispettando il vincolo di saturazione:

$$V_{DS} \ge V_{GS}-V_t = 7{,}16-4 = 3{,}16\text{ V}
\quad\Rightarrow\quad \text{«quindi ad esempio si fissa } V_{DS}=6\text{ V»}$$

e da lì $R_D = \dfrac{V_{DD}-V_{DS}}{I_D}$, $\;R_2 = \dfrac{V_{GS}}{V_{DD}}(R_1+R_2)$,
$\;R_1 = (R_1+R_2)-R_2$.

### 6. Quando c'è $R_S$, il source non è a massa (29-05, es. 8)

Tre correzioni in fila sullo stesso foglio, tutte figlie dello stesso errore:

| Fusi aveva scritto | Il prof. corregge |
|---|---|
| $R_D = \dfrac{V_{DD}-V_{DS}}{I_D}$ | $R_D = \dfrac{V_{DD}-V_{DS}-V_S}{I_D}$ |
| $I_S = \dfrac{R_S}{R_D+R_S}I_D$ | $I_S = I_D$ (nel FET la corrente è la stessa) |
| $V_S = \dfrac{R_S}{R_D+R_S}V_{DD}$ | $V_S = R_S I_D$ |
| $V_{R2} = V_{GS}$ | $V_{R2} = V_{GS} + V_S$ |

> [!danger] La regola in una riga
> Con $R_S$ presente: $V_G = V_{GS}+V_S$ e $V_{DD} = I_D(R_D+R_S)+V_{DS}$. Vale identica
> per JFET (appunti Poggi p. 19) e MOSFET.

### 7. Le due sviste di calcolo che sono costate più punti (02-03)

- **$\bar{Z}_C$ ha il segno meno**: $\bar{Z}_C = \dfrac{1}{j\omega C} = -\dfrac{j}{\omega C}$.
  Fusi aveva scritto $-\dfrac{1}{j\omega C}$, che è il valore opposto.
- **La f.d.t. di un quadripolo è un partitore**: $V_o = V_i\dfrac{\bar{Z}_2}{\bar{Z}_1+\bar{Z}_2}$,
  **non** $V_i\cdot \bar{Z}_{eq}$. È l'errore che ha azzerato l'es. 4.
- Il prof. corregge anche $\omega = 2\pi f = 6{,}28\cdot 10^3$ **rad/s**: le unità si scrivono.

---

## Come si usano nel calendario

Non sono un ripasso finale: sono il **termometro**. Ogni checkpoint ne rifà una porzione
**da zero, cronometrata, senza guardare la correzione**, e solo dopo si confronta.

| Giorno | Cosa si rifà | Timer | Cosa decide |
|---|---|---|---|
| **1** · gio 20 | 02-03, es. **1 e 6** | 30 min | se l'alternata regge, si aprono i filtri il giorno dopo. Se no, si ruba la prima ora del 21 |
| **4** · dom 23 | 02-03, es. **2-5**, poi **tutta** di seguito | 60 min + integrale | chiude alternata e filtri: due dei cinque argomenti dello scritto, e tutti e tre quelli dell'orale |
| **7** · mer 26 | 24-04, **tutti e 7** | 90 min | chiude il BJT, che nella LETTERA vale sia per Carli sia per Protti |
| **9** · ven 28 | 29-05, es. **1-5** | 60 min | chiude il JFET |
| **10** · sab 29 | 29-05, es. **6-8** | 45 min | chiude il MOSFET, e con lui tutti e cinque gli argomenti dello scritto |
| **11** · dom 30 | **tutte e tre in fila** | unico, ~2h30 | non è per imparare: è per provare la resistenza sulle cinque ore |

> [!tip] La regola di correzione
> Dopo ogni checkpoint si rifanno **solo gli esercizi sbagliati**, non tutta la verifica.
> E alla prova generale del 30 si ripassa **solo ciò che si è sbagliato più di una volta**:
> un errore isolato è disattenzione, un errore ripetuto è un buco.

---

## Cosa insegnano sul formato

- **Sono esercizi numerici**, non domande aperte. Le domande aperte sono l'altro formato di
  Carli, quello delle verifiche sui diodi — vedi [[04 - Verifica tipo Carli — Diodi]]. La
  LETTERA li tiene separati allo stesso modo: **esercizi** alla scritta, **domande** all'orale.
- **Il progetto è il tipo di esercizio ricorrente.** Su 21 esercizi totali, **undici** sono
  «dati i valori voluti, dimensiona le resistenze»: BJT (partitore e $R_E$), JFET ($R_S$,
  $R_D$, $R_G$), MOSFET (partitore di gate). È lo stesso schema tre volte, con tre relazioni
  diverse.
- **I punteggi non sono uniformi**: ogni esercizio vale da 1,00 a 2,00 punti su 10, e la
  griglia assegna anche **mezzi punti** a chi imposta bene e sbaglia i conti («relazioni
  usate corrette ma errati tutti i calcoli» = 0,75 su 1,50). Impostare bene paga anche
  senza chiudere.
- **Gli esercizi non consegnati pesano più di quelli sbagliati**: sei «NON SVOLTO» contro
  cinque «errato». Su ogni esercizio che non chiudi, **scrivi comunque la formula di
  partenza e il procedimento**.
- **Carli vuole vedere i passaggi**: due annotazioni su tre verifiche sono «non si spiega
  questo passaggio dalla relazione precedente» e «perché non ha continuato lo svolgimento?».
  Anche quando il risultato è giusto.
- **Le condizioni di svolgimento** (foglio firmato in fondo a ogni fascicolo): penna nera o
  blu, **niente matita, niente bianchetto**, errori barrati con una croce, niente libro né
  quaderno, telefono spento — ritirato con 2/10 a chi lo usa. Il 1° settembre sarà lo stesso.

---

## Link

- Il piano giorno per giorno: [[Calendario]]
- L'audit delle note di teoria contro queste verifiche: [[06 - Audit delle note contro le fonti del docente]]
- Le altre due prove del 1° settembre: [[02 - Prova Orale Carli]] · [[03 - Prova Pratica Protti]]
- Le domande aperte sui diodi: [[04 - Verifica tipo Carli — Diodi]]
- Da dove viene questa fonte e quanto vale: [[00 - Fonti e note]] §2
- Note di teoria: [[Filtri passivi del primo ordine]] · [[BJT]] · [[Amplificatori a BJT]] · [[JFET]] · [[MOSFET]]
