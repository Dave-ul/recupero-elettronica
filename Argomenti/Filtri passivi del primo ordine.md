---
tags: [recupero, elettronica, filtri, quadripoli]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-22) — Cap. 4 «I quadripoli lineari e non lineari», §3 «I filtri» pp. 155-158, §3.1 «I filtri RC e RL (1° ordine)» pp. 159-161, §3.2 «I filtri RLC (2° ordine)» pp. 161-163. Pagg.-PDF 56-60, folio letti dal piè di pagina. Verifica su OCR + immagini a 150/400 dpi."
prove: [scritta, orale, pratica]
---

# Filtri passivi del primo ordine

> [!info] Perché questo argomento conta il triplo
> È l'unico che la lettera di giudizio sospeso richiede in **tutte e tre le prove**: esercizi allo scritto (Carli), domande all'orale (Carli), misure e verifiche alla pratica (Protti). Se c'è un argomento su cui non puoi permetterti buchi, è questo.

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §6**.

## 1. Che cos'è un filtro

Partiamo dalla definizione del libro (Mirandola, Cap. 4 §3 «I filtri», p. 155):

> Un **filtro** (*filter*) è un quadripolo che permette il passaggio della porzione dello spettro del segnale in ingresso compresa in un dato intervallo di frequenze (**banda passante**) e attenua la parte dello spettro al di fuori di esso (**banda oscura**).

Questa frase è densa, quindi smontiamola.

Un segnale qualsiasi non è fatto di una sola frequenza: per il **teorema di Fourier** qualunque forma d'onda si può scomporre in una somma di sinusoidi di frequenze diverse. L'insieme di queste frequenze, con le rispettive ampiezze, è lo **spettro** del segnale. Un filtro è un circuito che tratta le varie frequenze in modo *diverso*: alcune le lascia passare quasi intatte, altre le smorza.

Le due zone hanno un nome:

- **Banda passante**: la banda delle frequenze in cui la risposta in ampiezza del filtro è pressoché costante, compresa in una fascia ampia **±3 dB**.
- **Banda oscura**: tutta la porzione di spettro esterna alla banda passante.
- **Frequenze (o pulsazioni) di taglio** $f_t$ / $\omega_t$: i valori corrispondenti alle **transizioni** tra banda passante e banda oscura.

### Perché proprio ±3 dB?

Il libro dà il numero senza spiegarlo, ma è il punto che i professori amano chiedere all'orale. Il motivo è che $-3$ dB corrisponde a un **dimezzamento della potenza**:

$$|G|_{dB} = 20\log_{10}|G| = -3 \;\Longrightarrow\; |G| = 10^{-3/20} \simeq 0{,}707 = \frac{1}{\sqrt{2}}$$

L'ampiezza scende a $1/\sqrt{2}$, ma la potenza è proporzionale al **quadrato** dell'ampiezza, quindi va a $\left(\frac{1}{\sqrt2}\right)^2 = \frac{1}{2}$, cioè **metà**. Per questo la frequenza di taglio si chiama anche *frequenza a metà potenza*. Il confine della banda passante è convenzionalmente fissato dove il filtro comincia a buttare via metà della potenza del segnale.

### Filtro ideale e filtro reale

![[fig-4-44-filtro-ideale-e-reale.png]]
*FIGURA 44 — Filtro **A)** ideale; **B)** reale. (Mirandola, Cap. 4 §3, p. 155)*

Un **filtro ideale** (FIGURA 44A) ha una banda passante perfettamente piatta fino alle frequenze di taglio, oltre le quali l'attenuazione passa **di colpo** a un valore infinito: le componenti a quelle frequenze sono completamente eliminate. È un muro verticale.

Un **filtro reale** (FIGURA 44B) non ha muri: le frequenze che cadono nella banda oscura sono tanto più attenuate quanto più si distanziano dalla frequenza di taglio. La transizione è graduale.

Da qui una frase del libro da ricordare:

> Il comportamento del filtro si avvicina a quello ideale all'aumentare della **pendenza** della curva di risposta in banda oscura e quindi al crescere dell'**ordine** della sua funzione di trasferimento.

Tradotto: più il filtro è "ripido" appena fuori dalla banda passante, più assomiglia all'ideale. E la ripidità dipende dall'ordine — che è il concetto del §4 qui sotto.

---

## 2. I quattro tipi di filtro

I filtri si classificano in base all'andamento della risposta in ampiezza:

![[fig-4-t5-tipi-di-filtro.png]]
*TABELLA 5 — Simboli e risposte in ampiezza dei filtri passa basso, passa alto, passa banda ed elimina banda. (Mirandola, Cap. 4 §3, p. 156)*

- **Passa basso** (LPF, *Low Pass Filter*): la banda passante si trova **al di sotto** della frequenza di taglio. Lascia passare le frequenze basse.
- **Passa alto** (HPF, *High Pass Filter*): la banda passante si trova **al di sopra** della frequenza di taglio. Lascia passare le frequenze alte.
- **Passa banda** (BPF, *Band Pass Filter*): la banda passante è compresa **tra due** frequenze di taglio. Si dicono *selettivi* se la banda passante è stretta e il massimo del modulo è raggiunto per una sola frequenza, oppure *a banda larga* se la banda passante rimane piatta per un intervallo di frequenze.
- **Elimina banda** (BRF, *Band Reject Filter*, o **notch**): attenua le frequenze comprese tra due frequenze di taglio. È l'opposto del passa banda.

> [!tip] Come ricordarli
> Il nome dice sempre **cosa passa**, mai cosa viene bloccato. "Passa basso" = passano le basse. Sembra ovvio, ma sotto esame è l'errore numero uno.

Per il tuo recupero servono soprattutto **passa basso** e **passa alto**: sono gli unici realizzabili con un filtro passivo del primo ordine.

---

## 3. Filtri passivi e filtri attivi

Il libro (Cap. 4 §3, p. 156) distingue:

- **Filtri passivi**: realizzati **esclusivamente** con componenti passivi ($R$, $L$, $C$, trasformatore). Per essi il diagramma di Bode asintotico del modulo si mantiene **sempre al di sotto di 0 dB**: il segnale d'uscita può avere al massimo la stessa ampiezza di quello d'ingresso.
- **Filtri attivi**: impiegano, oltre a componenti passivi (generalmente $R$ e $C$), anche **amplificatori** (in genere operazionali). Consentono risposte in banda passante superiori a 0 dB e basse resistenze d'uscita: permettono quindi anche l'**amplificazione** dei segnali.

> [!note] Fuori programma
> Il libro rimanda lo studio dei filtri attivi al **Volume 3**, e la tua lettera parla solo di *filtri passivi*. Quindi: tutto ciò che studi qui non può amplificare. Il guadagno massimo è 1 (cioè 0 dB), mai di più.

Il perché è fisico, e vale la pena capirlo: resistori, condensatori e induttori non hanno una sorgente di energia propria. Possono solo dissipare, o immagazzinare e restituire, energia. Senza un'alimentazione esterna che inietti potenza, non c'è modo di far uscire un segnale più grande di quello che è entrato.

---

## 4. L'ordine di un filtro

![[fig-4-45-bode-ordini-filtro.png]]
*FIGURA 45 — Diagrammi di Bode asintotici del modulo di filtri passa alto del 1°, 2°, 3° ordine e ideale. (Mirandola, Cap. 4 §3, p. 157)*

Dal libro:

- **Filtri del primo ordine**: la funzione di trasferimento presenta **un solo polo**; il diagramma di Bode del modulo ha una pendenza massima di **±20 dB/dec**.
- **Filtri del secondo ordine**: la funzione di trasferimento presenta **due poli**; pendenza massima **±40 dB/dec**.

> In generale l'**ordine** di un filtro coincide con il **numero di poli**, e quindi con l'ordine della sua funzione di trasferimento.

E la frase che riguarda direttamente il tuo programma:

> I filtri passivi del **primo ordine** si realizzano con coppie **RC** o **RL**, mentre per quelli del secondo ordine sono necessari **due componenti reattivi**.

Guardando la FIGURA 45 si capisce il senso dell'ordine: tutte le curve tagliano alla stessa pulsazione ($10^3$ rad/s), ma il 1° ordine scende a 20 dB/dec, il 2° a 40, il 3° a 60. Più poli = discesa più ripida = più vicino al filtro ideale (la linea verticale tratteggiata).

I filtri con ordine superiore al 2° si ottengono combinando **in cascata** filtri del 1° e del 2° ordine.

> [!warning] Il "primo ordine" nella tua lettera
> Un solo componente reattivo ($C$ **oppure** $L$), un solo polo, pendenza 20 dB/dec. Se in un esercizio vedi **due** condensatori, o un condensatore **e** un'induttanza che lavorano insieme, non è più primo ordine.

---

## 5. Il cuore: i filtri RC e RL del primo ordine

Questa è la tabella da sapere a memoria.

![[fig-4-t6-filtri-rc-rl-primo-ordine.png]]
*TABELLA 6 — Filtri passivi del primo ordine passa basso e passa alto, RC e RL. (Mirandola, Cap. 4 §3.1, p. 159)*

### 5.1 L'idea che li spiega tutti e quattro: il partitore di tensione

Il libro lo dice in una riga, quasi di sfuggita, ma è la chiave di tutto:

> …osservando che i circuiti hanno la struttura del **partitore di tensione**.

Tutti e quattro i circuiti della TABELLA 6 sono lo stesso circuito: due impedenze in serie, con l'uscita presa su quella in basso.

$$v_o = \frac{Z_2}{Z_1 + Z_2}\, v_i \qquad\Longrightarrow\qquad G(s) = \frac{v_o}{v_i} = \frac{Z_2}{Z_1 + Z_2}$$

Cambia solo **chi mettiamo** in $Z_1$ e in $Z_2$:

| Filtro | $Z_1$ (serie) | $Z_2$ (uscita, verso massa) |
|---|---|---|
| Passa basso RC | $R$ | $C$ |
| Passa basso RL | $L$ | $R$ |
| Passa alto RC | $C$ | $R$ |
| Passa alto RL | $R$ | $L$ |

Se ti ricordi le impedenze — $Z_R = R$, $Z_L = sL$, $Z_C = \dfrac{1}{sC}$ — puoi **ricavare** ogni funzione di trasferimento in trenta secondi, senza impararne nessuna a memoria. Vedi [[Impedenza dei bipoli R, L, C]].

Esempio, il passa basso RC:

$$G(s) = \frac{Z_C}{Z_R + Z_C} = \frac{\frac{1}{sC}}{R + \frac{1}{sC}} = \frac{1}{1 + sRC}$$

(moltiplicando numeratore e denominatore per $sC$). Fatto.

### 5.2 Il trucco dei casi limite: capire il tipo senza fare conti

Prima ancora di scrivere formule, si può capire *che filtro è* guardando cosa fanno i componenti reattivi ai due estremi:

| Componente | a $f = 0$ (continua) | a $f = \infty$ |
|---|---|---|
| **Condensatore** $C$ | circuito **aperto** | **cortocircuito** |
| **Induttanza** $L$ | **cortocircuito** | circuito **aperto** |

Il perché sta nelle reattanze: $X_C = \dfrac{1}{\omega C} \to \infty$ per $\omega \to 0$, mentre $X_L = \omega L \to 0$ per $\omega \to 0$. Condensatore e induttanza fanno esattamente il contrario l'uno dell'altro — ed è per questo che con entrambi si possono fare sia passa basso sia passa alto, semplicemente scambiandoli di posto.

Applichiamolo ai quattro casi:

**Passa basso RC** ($R$ in serie, $C$ verso massa, uscita su $C$)
- $f = 0$: $C$ è aperto → non scorre corrente → nessuna caduta su $R$ → $v_o = v_i$ ✅ passa
- $f = \infty$: $C$ è un corto → l'uscita è cortocircuitata a massa → $v_o = 0$ ❌ bloccato
- Passa il basso, blocca l'alto → **passa basso**.

**Passa basso RL** ($L$ in serie, $R$ verso massa, uscita su $R$)
- $f = 0$: $L$ è un corto → il segnale arriva intatto su $R$ → $v_o = v_i$ ✅
- $f = \infty$: $L$ è aperta → nulla arriva all'uscita → $v_o = 0$ ❌
- → **passa basso**.

**Passa alto RC** ($C$ in serie, $R$ verso massa, uscita su $R$)
- $f = 0$: $C$ è aperto → non scorre corrente → sulla resistenza non cade nulla → $v_o = 0$ ❌
- $f = \infty$: $C$ è un corto → il segnale arriva intatto su $R$ → $v_o = v_i$ ✅
- → **passa alto**.

**Passa alto RL** ($R$ in serie, $L$ verso massa, uscita su $L$)
- $f = 0$: $L$ è un corto → l'uscita è cortocircuitata a massa → $v_o = 0$ ❌
- $f = \infty$: $L$ è aperta → tutta la tensione cade sull'uscita → $v_o = v_i$ ✅
- → **passa alto**.

> [!tip] La regola in una riga
> **L'uscita presa su $C$ dà un passa basso. L'uscita presa su $L$ dà un passa alto.** Sempre.
> Se l'uscita è su $R$, guarda cosa c'è in serie: se in serie c'è $C$ è un passa alto, se in serie c'è $L$ è un passa basso.

### 5.3 Le quattro funzioni di trasferimento

**Filtro passa basso RC** — formula (4.44) del libro:
$$G(s) = \frac{1}{1 + sRC} \qquad p = -\frac{1}{RC} \qquad \omega_p = \frac{1}{RC} \qquad f_t = \frac{\omega_p}{2\pi} = \frac{1}{2\pi RC}$$

**Filtro passa basso RL** — formula (4.45), **corretta** (vedi §6):
$$G(s) = \frac{1}{1 + s\frac{L}{R}} \qquad p = -\frac{R}{L} \qquad \omega_p = \frac{R}{L} \qquad f_t = \frac{\omega_p}{2\pi} = \frac{R}{2\pi L}$$

**Filtro passa alto RC** — formula (4.46) del libro:
$$G(s) = \frac{sRC}{1 + sRC} \qquad p = -\frac{1}{RC} \qquad \omega_p = \frac{1}{RC} \qquad f_t = \frac{\omega_p}{2\pi} = \frac{1}{2\pi RC}$$

**Filtro passa alto RL** — formula (4.47), **corretta** (vedi §6):
$$G(s) = \frac{s\frac{L}{R}}{1 + s\frac{L}{R}} \qquad p = -\frac{R}{L} \qquad \omega_p = \frac{R}{L} \qquad f_t = \frac{\omega_p}{2\pi} = \frac{R}{2\pi L}$$

### 5.4 La chiave che unifica tutto: la costante di tempo

C'è un modo per non sbagliare mai una frequenza di taglio, e il libro non lo mette in evidenza. Ogni filtro del primo ordine ha una **costante di tempo** $\tau$, ed è **sempre** vero che:

$$\boxed{\;\omega_p = \frac{1}{\tau}\;}$$

dove

$$\tau_{RC} = RC \qquad\qquad \tau_{RL} = \frac{L}{R}$$

Da cui, automaticamente:

$$\omega_p^{RC} = \frac{1}{RC} \qquad\qquad \omega_p^{RL} = \frac{1}{L/R} = \frac{R}{L}$$

Questa singola regola ti dà tutte e quattro le pulsazioni di taglio, e ti protegge dal refuso del libro (§6). Se ti ricordi solo una cosa di questa nota, ricordati questa.

> [!check] Controllo dimensionale — il tuo salvagente
> $\tau$ è un **tempo**, si misura in secondi. Verifichiamo:
> - $RC$: $\Omega \cdot \text{F} = \frac{V}{A}\cdot\frac{A\cdot s}{V} = s$ ✅
> - $L/R$: $\frac{\text{H}}{\Omega} = \frac{V\cdot s/A}{V/A} = s$ ✅
>
> Una **pulsazione** si misura in rad/s, cioè $1/s$. Quindi $\omega_p$ deve essere $1/\tau$, mai $\tau$.
>
> **Se in un esercizio ottieni $\omega_p = L/R$, hai scritto un tempo dove serviva una pulsazione: è sbagliato al 100%, senza bisogno di ricontrollare i conti.**

### 5.5 Quattro osservazioni del libro da non perdere

Dal testo di p. 160, subito dopo la formula (4.47):

1. Tutte queste funzioni di trasferimento sono del **1° ordine**: presentano un solo polo, quindi in banda oscura il modulo ha pendenza $\pm20$ dB/dec e **le pulsazioni di taglio coincidono con quelle dei poli**.
2. La frequenza di taglio dei filtri **RC** è data dalla **stessa** espressione sia per il passa alto sia per il passa basso; **lo stesso vale per i filtri RL**. Cambia il *tipo* di filtro, non la formula della $f_t$: dipende solo dai componenti, non da come li disponi.
3. Il modulo della funzione di trasferimento è **sempre $\le$ 0 dB**: il segnale d'uscita ha ampiezza minore o uguale a quello d'ingresso. È la firma del filtro passivo.
4. Le funzioni di trasferimento sono calcolate considerando le **uscite scollegate**. Vedi §8 sul carico.

---

## 6. ⚠️ Errata corrige — due errori nel libro

> [!danger] Leggi questo prima di aprire il libro a **p. 160**
> Quella pagina contiene **due errori veri**. Non sono sottigliezze: se la studi alla lettera, sbagli gli esercizi dello scritto.
> *(Entrambi verificati il 2026-07-22 sull'immagine della pagina-PDF 59 a 150 dpi — non dedotti dall'OCR. Vedi [[00 - Audit e correzioni]], Lotto 8.)*

### Errore 1 — Le formule (4.45) e (4.47): $L/R$ al posto di $R/L$

Il libro **stampa**:

$$p = -\frac{L}{R} \qquad \omega_p = \frac{L}{R} \qquad f_t = \frac{L}{2\pi R} \qquad \text{(come stampato — SBAGLIATO)}$$

Il valore **corretto** è:

$$p = -\frac{R}{L} \qquad \omega_p = \frac{R}{L} \qquad f_t = \frac{R}{2\pi L} \qquad \text{(CORRETTO)}$$

**Quattro prove indipendenti che il libro sbaglia:**

1. **Analisi dimensionale.** $L/R$ ha unità $\text{H}/\Omega = \text{s}$: è un *tempo*, non una pulsazione. Una $\omega$ si misura in rad/s. Impossibile.
2. **La matematica.** Il polo di $G(s) = \dfrac{1}{1 + s\frac{L}{R}}$ si trova annullando il denominatore: $1 + s\frac{L}{R} = 0 \Rightarrow s = -\dfrac{R}{L}$. Non c'è margine di interpretazione.
3. **Il libro contraddice sé stesso.** Nell'**ESEMPIO 19**, due paragrafi più sotto — stessa pagina 160! — calcola:
   $$f_t = \frac{R}{2\pi L} = \frac{47\cdot10^3}{2\pi\cdot 12\cdot 10^{-3}} = 623\ \text{kHz}$$
   cioè usa la formula **corretta**, quella che contraddice la (4.47) stampata poche righe sopra.
4. **Conferma esterna.** [Edutecnica](https://www.edutecnica.it/elettronica/filtrip/filtrip.htm) riporta per il filtro RL: $f_H = \dfrac{R}{2\pi L}$, con polo in $s = -\dfrac{R}{L} = -\dfrac{1}{\tau_p}$.

**Cosa fare all'esame:** usa sempre $\omega_p = \dfrac{R}{L}$ e $f_t = \dfrac{R}{2\pi L}$. Nel dubbio, applica il controllo dimensionale del §5.4.

### Errore 2 — Il testo del passa alto RC (p. 160)

Il libro scrive:

> «Filtro passa alto *RC*: il condensatore per $f = 0$ risulta un circuito aperto, per cui $v_o = v_i$, mentre per $f = \infty$ è un cortocircuito e quindi $v_o = 0$»

Le due conclusioni sono **invertite**. Come si vede nello schema della TABELLA 6, nel passa alto RC il condensatore è **in serie** e la resistenza va a massa: se a $f = 0$ il condensatore è aperto, **non scorre corrente**, quindi sulla resistenza non cade nulla e $v_o = 0$ — non $v_o = v_i$.

Lo conferma la formula (4.46) del libro stesso: $G(s) = \dfrac{sRC}{1+sRC}$, che per $s \to 0$ dà $G \to 0$, cioè $v_o = 0$.

Il testo corretto è:

> Filtro passa alto RC: il condensatore per $f = 0$ risulta un circuito aperto, per cui **$v_o = 0$**, mentre per $f = \infty$ è un cortocircuito e quindi **$v_o = v_i$**.

**Da dove nasce l'errore:** la frase è identica, parola per parola, a quella del **passa basso RC** di **p. 159** (formula 4.44) — dove è giusta, perché lì il condensatore è davvero l'elemento d'uscita. L'autore ha copiato il periodo, ha aggiornato la formula e si è dimenticato di invertire le conclusioni. Riconoscere l'origine dell'errore aiuta a non farsi confondere.

> [!question] Possibile domanda all'orale
> Questo è esattamente il tipo di ragionamento che il prof. Carli può chiedere: *«perché questo circuito è un passa alto?»*. Rispondere «perché lo dice la tabella» vale poco. Rispondere «perché a $f=0$ il condensatore è aperto, non scorre corrente e quindi sulla resistenza d'uscita non cade tensione» dimostra che hai capito il meccanismo.

---

## 7. I diagrammi di Bode: modulo e fase

Guarda le due colonne di destra della TABELLA 6 (§5).

### Il modulo

**Passa basso**: la curva è piatta a 0 dB fino a $\omega_p$, poi scende a $-20$ dB/dec.
**Passa alto**: sale a $+20$ dB/dec fino a $\omega_p$, poi diventa piatta.

In entrambi i casi il "ginocchio" è esattamente in $\omega_p$, cioè alla pulsazione di taglio, che coincide con il polo.

> [!note] Asintotico e reale
> Il diagramma di Bode disegnato con le rette è quello **asintotico**: un'approssimazione. La curva vera non ha spigoli e nel punto $\omega_p$ passa **3 dB sotto** l'incrocio degli asintoti. Ecco che torna il $-3$ dB del §1: la frequenza di taglio è dove la curva reale sta 3 dB sotto la banda passante.

### La fase

**Passa basso**: parte da $0°$, vale $-45°$ esattamente in $\omega_p$, tende a $-90°$.
**Passa alto**: parte da $+90°$, vale $+45°$ esattamente in $\omega_p$, tende a $0°$.

La transizione non è istantanea: come si vede dalle etichette $0{,}1\,\omega_p$ / $\omega_p$ / $10\,\omega_p$ in tabella, la fase comincia a muoversi **una decade prima** del polo e finisce **una decade dopo**, con pendenza di $-45°/\text{dec}$.

> [!tip] Il valore a $\omega_p$ è un regalo
> Alla pulsazione di taglio sai **sempre** due cose, senza calcoli: il modulo è a $-3$ dB dalla banda passante, e la fase è a $\pm45°$. Sono due controlli gratuiti su qualunque esercizio.

Perché $-45°$? A $\omega = \omega_p$ nel passa basso RC si ha $\omega RC = 1$, quindi:

$$G(j\omega_p) = \frac{1}{1 + j\cdot 1} = \frac{1}{1+j}$$

L'argomento di $\dfrac{1}{1+j}$ è $-\arctan(1) = -45°$, e il modulo è $\dfrac{1}{|1+j|} = \dfrac{1}{\sqrt2} = 0{,}707$, cioè proprio $-3$ dB. Tutto torna.

---

## 8. L'effetto del carico

Un'osservazione del libro (p. 160, quarta delle quattro del §3.1) che vale un esercizio intero:

> Le funzioni di trasferimento dei filtri sono calcolate considerando le **uscite scollegate**. Un eventuale **carico** si troverà in **parallelo all'elemento d'uscita** del quadripolo, alterando le risposte riportate in tabella; l'effetto di tale carico sarà tanto minore quanto **maggiore è la sua impedenza** rispetto a quella dell'elemento d'uscita in parallelo.

In pratica: le formule della TABELLA 6 valgono per un filtro "a vuoto". Appena colleghi qualcosa all'uscita — uno strumento, uno stadio successivo — quel qualcosa si mette in parallelo e cambia il partitore, quindi cambia sia il guadagno sia la frequenza di taglio.

Regola pratica: se l'impedenza del carico è molto maggiore di quella dell'elemento d'uscita, l'errore è trascurabile. È il motivo per cui l'oscilloscopio ha un ingresso da 1 M$\Omega$ — vedi [[L'oscilloscopio]].

Da qui discende una conseguenza che vale la pena esplicitare: **mettere in cascata** due filtri passivi del primo ordine *non* dà un filtro del secondo ordine pulito, perché il secondo stadio fa da carico al primo — i due si "caricano" a vicenda e la frequenza di taglio complessiva si discosta da quella del singolo filtro.

> [!warning] Questa conseguenza è **nostra**, non del libro
> Il libro a p. 160 dice soltanto che le funzioni di trasferimento sono calcolate a **uscite scollegate** e che un carico le altera. Non parla di cascata in quel punto. Anzi, a **p. 157** afferma che i filtri di ordine superiore al 2° «possono ottenersi **combinando (in cascata)** filtri del 1° e del 2° ordine», senza avvertire del problema di carico.
> Le due cose non si contraddicono — la cascata si usa davvero, ma nei filtri **attivi**, dove ogni stadio ha bassa impedenza d'uscita e non carica il precedente. Nei passivi l'effetto c'è, e il libro lo lascia implicito. *(Attribuzione corretta nel Lotto 8: una versione precedente presentava questa deduzione come un'affermazione del libro.)*

---

## 9. Il filtraggio dei segnali

Questa parte (libro, §«Il filtraggio dei segnali», p. 157) risponde alla domanda: *ok, ho il diagramma di Bode — e adesso come faccio a sapere cosa esce?*

Il procedimento è:

1. Scomponi il segnale d'ingresso nel suo **spettro**: le sue armoniche, ciascuna con la sua ampiezza e la sua fase.
2. Per **ogni** armonica, leggi sul diagramma di Bode quanto vale $|G(j\omega)|$ a *quella* pulsazione.
3. **Ampiezza in uscita** = ampiezza in ingresso $\times\;|G(j\omega)|$ a quella pulsazione.
4. **Fase in uscita** = fase in ingresso $+$ sfasamento $\angle G(j\omega)$ a quella pulsazione.

> Se i livelli dei segnali e la risposta in ampiezza sono espressi in **dB**, per le note proprietà dei logaritmi il livello di un'armonica in uscita si trova **sommando** a quello in ingresso il relativo guadagno del quadripolo.

Cioè: in scala lineare si **moltiplica**, in dB si **somma**. È tutto il vantaggio dei decibel.

### L'esempio del libro (ESEMPIO 18, p. 158)

Un segnale con quattro armoniche entra in un quadripolo con risposta passa basso:

| Armonica | Frequenza | Ampiezza in ingresso | Guadagno $G$ | Ampiezza in uscita |
|---|---|---|---|---|
| 1ª | 2 kHz | 300 mV | 0,83 | 250 mV |
| 2ª | 4 kHz | 100 mV | 0,57 | 57 mV |
| 3ª | 6 kHz | 80 mV | 0,43 | 34 mV |
| 4ª | 8 kHz | 50 mV | 0,33 | 16 mV |

Nota l'andamento: più sale la frequenza, più il guadagno cala (0,83 → 0,33). È un passa basso che fa il suo mestiere. Nel dominio del tempo il risultato è che il segnale d'uscita ha **l'ondulazione ridotta**, perché sono state smorzate le componenti armoniche di frequenza più alta. Il passa basso *arrotonda* il segnale.

Questo collega la teoria a quello che vedrai sull'oscilloscopio alla prova pratica: un'onda quadra che attraversa un passa basso esce con gli spigoli smussati, proprio perché gli spigoli *sono* le armoniche alte.

---

## 10. Da qui in poi

- Prerequisiti: [[Segnali sinusoidali e fasori]] · [[Impedenza dei bipoli R, L, C]]
- Esercizi: [[Esercizi - Filtri passivi del primo ordine]]
- Applicazione pratica: [[L'oscilloscopio]]
- Approfondimento (non richiesto dalla lettera): i filtri RLC del 2° ordine, libro **§3.2 «I filtri RLC (2° ordine)», pp. 161-163** (TABELLA 7 e formula 4.48)
