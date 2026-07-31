---
tags: [recupero, elettronica, corrente-alternata, potenze, rifasamento]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2, Cap. 2, §4 «La potenza in alternata» (pp. 62-65, pagg.-PDF 9-10) e §4.2 «Il rifasamento degli impianti industriali» (pp. 65-67, pagg.-PDF 10-11). Folio 64/65 e 66/67 letti dal piè di pagina; formule 2.26-2.33, FIGURE 18-24, ESEMPI 6-7-8 verificati su OCR + immagine a 220 dpi."
prove: [scritta, orale]
---

# Le potenze in alternata

> [!info] Dove serve
> **Scritta** e **orale** (Carli): «circuiti in corrente alternata». È l'ultimo pezzo del Cap. 2 che ti serve, ed è quello con più contenuto da orale — il **rifasamento** è pieno di domande a risposta discorsiva.

> [!danger] Un errore vero del libro in questo paragrafo
> Vedi il §6 «Errata corrige». È grosso: un risultato sbagliato di **un fattore mille** (ESEMPIO 7, p. 65) — verificato sull'immagine della pagina.
> Ci sono anche due **imprecisioni minori**, che il §6 distingue dall'errore vero: il segno di $Q$ omesso per i carichi capacitivi (una convenzione del libro, non una svista) e un'etichetta $\varphi'$ ripetuta nell'ESEMPIO 8.

Prerequisiti: [[Impedenza dei bipoli R, L, C]] · [[Il metodo simbolico]].

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §4**.

## 1. Da dove nasce lo sfasamento

![[fig-2-18-bipolo-e-sfasamento.png]]
*FIGURA 18 — **A)** Bipolo alimentato in alternata. **B)** Sfasamento $\varphi$ tra tensione e corrente dovuto alla componente reattiva del bipolo. Mirandola, Cap. 2 §4, p. 62.*

Dal libro (Mirandola, Cap. 2 §4, **p. 62**, riquadro DIMOSTRAZIONE):

> In un bipolo lineare $\bar{Z}$ sottoposto a una tensione sinusoidale $v(t)$, scorre una corrente $i(t)$ sinusoidale con identica frequenza; tensione e corrente risultano **sfasate di una quantità $\varphi$, pari all'argomento dell'impedenza del bipolo**.

Il perché è già tutto in $\bar{V} = \bar{Z}\cdot\bar{I}$: essendo un prodotto tra numeri complessi, il modulo di $\bar{V}$ è il prodotto dei moduli e **la fase è la somma delle fasi**. Disegnando $\bar{I}$ sull'asse reale (fase zero), la fase di $\bar{V}$ risulta pari proprio a $\varphi$ — **in anticipo** rispetto a $\bar{I}$ se $\varphi > 0$, **in ritardo** se $\varphi < 0$.

> [!check] $\varphi$ non è un numero nuovo
> Lo sfasamento tra tensione e corrente **è** l'argomento dell'impedenza. Non è una grandezza in più da calcolare: se hai già $\bar{Z} = R + jX$, allora $\varphi = \arctan\frac{X}{R}$, e da lì discende tutto il resto di questa nota.
> Ricollegandoti al §4 di [[Impedenza dei bipoli R, L, C]]: $X > 0$ (induttivo) → $\varphi > 0$; $X < 0$ (capacitivo) → $\varphi < 0$.

---

## 2. La potenza istantanea, e i due termini che la compongono

La potenza dissipata sul bipolo nell'istante generico $t$ è la **potenza istantanea**:

$$p(t) = v(t)\cdot i(t) \tag{2.26}$$

In regime sinusoidale, sostituendo le funzioni sinusoidali:

$$p(t) = V_p\operatorname{sen}(\omega t + \varphi)\,I_p\operatorname{sen}(\omega t) = \frac{1}{2}V_p I_p \cos\varphi\,(1 - \cos 2\omega t) + \frac{1}{2}V_p I_p \operatorname{sen}\varphi\cdot\operatorname{sen}2\omega t \tag{2.27}$$

Il libro spiega cosa sono i due termini, ed è il passaggio concettuale più importante del paragrafo:

> dove il **primo termine si mantiene sempre positivo** e rappresenta quindi la potenza **assorbita** dal bipolo (*potenza attiva*), che viene trasformata in calore per effetto Joule o in lavoro utile nelle macchine elettriche. Il **secondo termine** invece ha **valor medio nullo** e rappresenta la potenza **alternativamente immagazzinata e ceduta** dal bipolo (*potenza reattiva*).

> [!tip] Perché il primo termine è sempre positivo e il secondo no
> Guarda le due espressioni con attenzione, perché la differenza è tutta lì.
> - **Primo termine**: contiene $(1 - \cos 2\omega t)$. Il coseno oscilla tra $-1$ e $+1$, quindi $(1 - \cos 2\omega t)$ oscilla tra **0 e 2**: non è mai negativo. Il suo valor medio è 1, quindi il termine ha media $\frac{1}{2}V_p I_p\cos\varphi$ — che è la potenza attiva.
> - **Secondo termine**: contiene $\operatorname{sen}2\omega t$, che oscilla tra $-1$ e $+1$ in modo simmetrico. Media: **zero**.
>
> Cosa significa fisicamente: il primo termine è energia che **entra e non torna più** (diventa calore o lavoro). Il secondo è energia che entra e poi **esce di nuovo**, avanti e indietro, senza mai essere consumata. È lo stesso palleggio di energia che hai visto nella risonanza in [[Reti RLC e risonanza]].
>
> Nota anche il $2\omega$: la potenza oscilla al **doppio** della frequenza di tensione e corrente. Sensato — il prodotto di due sinusoidi alla stessa frequenza oscilla a frequenza doppia.

---

## 3. Potenza attiva, reattiva e apparente

Dal libro (Mirandola, Cap. 2 **§4.1 «Potenza attiva, reattiva e apparente», p. 63**):

> Si definisce **potenza attiva** la potenza media dissipata in calore su un bipolo in regime sinusoidale:
> $$P = V_{eff} I_{eff}\cos\varphi \quad [\text{W}] \tag{2.28}$$
> dove $V_{eff}$ e $I_{eff}$ sono i valori efficaci di tensione e corrente, ottenuti dividendo i valori di picco per $\sqrt{2}$; il termine $\cos\varphi$ è detto **fattore di potenza** e $\varphi$ corrisponde all'argomento di $\bar{Z}$, cioè allo sfasamento tra $\bar{V}$ e $\bar{I}$.

> Si definisce **potenza reattiva** (misurata in volt-ampere reattivi) la potenza media alternativamente immagazzinata e ceduta dal bipolo:
> $$Q = V_{eff} I_{eff}\operatorname{sen}\varphi \quad [\text{VAR}] \tag{2.29}$$

> Si definisce **potenza apparente** (misurata in volt-ampere) il prodotto:
> $$S = V_{eff} I_{eff} \quad [\text{VA}] \tag{2.30}$$
> che in regime sinusoidale corrisponde all'**ampiezza dell'oscillazione** della potenza istantanea e la cui conoscenza può essere utile per il **dimensionamento di conduttori e generatori**.

E un'osservazione che il libro fa quasi di sfuggita ma che è una domanda da orale:

> Le potenze $P$, $Q$ e $S$ hanno **fisicamente la stessa dimensione** (lavoro/tempo = watt), ma vengono espresse con **unità di misura differenti** per evidenziare il fatto che **non ha senso sommarle tra loro**.

> [!warning] W, VAR e VA sono lo stesso watt travestito
> È una scelta di notazione, non di fisica. Le tre unità servono a impedirti di scrivere $P + Q = S$, che sarebbe **sbagliato**: si sommano come **vettori perpendicolari**, non come numeri.
> E servono a te che leggi: se trovi «1,37 kVA» sai che è potenza apparente; se fosse scritto «1,37 kW» penseresti che sia potenza consumata — e sono due cose diversissime in bolletta.

### Il triangolo delle potenze

![[fig-2-19-triangolo-delle-potenze.png]]
*FIGURA 19 — Triangolo delle potenze. Mirandola, Cap. 2 §4.1, p. 63.*

$$P = S\cos\varphi \qquad Q = S\operatorname{sen}\varphi \qquad S = \sqrt{P^2 + Q^2} \tag{2.31}$$

E se il bipolo è attraversato da una corrente di modulo $I$:

$$P = R I^2 \qquad Q = |X| I^2 \qquad S = |Z| I^2 \tag{2.32}$$

> [!check] Il triangolo delle potenze è il triangolo delle impedenze
> Confronta la (2.32) con $\bar{Z} = R + jX$ e $|Z| = \sqrt{R^2+X^2}$. Sono **lo stesso triangolo**, moltiplicato per $I^2$:
>
> | Impedenze | Potenze |
> |---|---|
> | $R$ (parte reale) | $P$ (attiva) |
> | $X$ (parte immaginaria) | $Q$ (reattiva) |
> | $\|Z\|$ (ipotenusa) | $S$ (apparente) |
> | $\varphi = \arctan\frac{X}{R}$ | $\varphi = \arctan\frac{Q}{P}$ |
>
> Se hai capito il triangolo delle impedenze, il triangolo delle potenze **non è niente di nuovo**. E ti dà un controllo gratis: $S$ deve **sempre** essere la più grande delle tre, perché è l'ipotenusa. Tienilo a mente: nel §6 vedrai che è proprio questo controllo a smascherare un errore del libro.

> [!question] Il quesito 20 del libro
> *«Quale significato ha, dal punto di vista della potenza, lo sfasamento $\varphi$ tra tensione e corrente su un bipolo?»*
>
> $\varphi$ decide **come si spartisce** la potenza apparente tra attiva e reattiva:
> - $\varphi = 0$ (bipolo resistivo) → $\cos\varphi = 1$ → $P = S$, $Q = 0$: **tutta** la potenza è utile.
> - $\varphi = \pm90°$ (bipolo puramente reattivo) → $\cos\varphi = 0$ → $P = 0$, $|Q| = S$: **nessuna** potenza utile, solo palleggio.
> - In mezzo, $\cos\varphi$ misura la frazione utile.
>
> Ecco perché $\cos\varphi$ si chiama **fattore di potenza**: dice letteralmente quale frazione della potenza che il generatore deve fornire viene effettivamente sfruttata.

---

## 4. Gli esempi svolti del libro

### ESEMPIO 6 — Bipolo RC (Mirandola, **p. 64**)

![[fig-2-20-esempio-6-rc.png]]
*FIGURA 20 — $C = 100$ nF in serie a $R = 1$ k$\Omega$, generatore da 5 V$_{eff}$ a 1 kHz. Mirandola, p. 64.*

$$\omega = 2\pi f = 6{,}28\ \text{krad/s}$$

$$\bar{Z} = R + \frac{1}{j\omega C} = R - \frac{j}{2\pi f C} = 10^{3} - j\,1{,}59\cdot10^{3}$$

Il libro nota: **la presenza del condensatore causa il segno negativo** nella parte immaginaria (reattanza capacitiva).

$$|\bar{Z}| = \sqrt{1000^2 + 1590^2} = 1{,}88\ \text{k}\Omega \qquad \angle\bar{Z} = \varphi = \arctan\!\left(\frac{-1590}{1000}\right) = -1{,}01\ \text{rad} = -57{,}8°$$

La tensione risulta quindi **in ritardo** di 57,8° rispetto alla corrente; il fattore di potenza vale $\cos\varphi = 0{,}533$.

$$I_{eff} = \frac{V_{eff}}{|Z|} = \frac{5}{1880} = 2{,}66\ \text{mA}$$

$$P = V_{eff}I_{eff}\cos\varphi = 5\cdot 2{,}66\cdot10^{-3}\cdot 0{,}533 = 7{,}09\ \text{mW}$$

$$Q = V_{eff}I_{eff}\operatorname{sen}\varphi = 5\cdot 2{,}66\cdot10^{-3}\cdot(-0{,}846) = \mathbf{-11{,}3\ mVAR}$$

$$S = V_{eff}I_{eff} = 5\cdot 2{,}66\cdot10^{-3} = 13{,}3\ \text{mVA}$$

Le ampiezze sui componenti:

$$V_R = R\,I_{eff} = 1000\cdot 2{,}66\cdot10^{-3} = 2{,}66\ \text{V} \qquad V_C = X_C I_{eff} = \frac{I_{eff}}{\omega C} = 4{,}24\ \text{V}$$

Il libro chiude con un'osservazione importante:

> Si noti che la somma delle ampiezze $V_R$ e $V_C$ **non è uguale a $V_g$**: il principio di Kirchhoff è rispettato **istante per istante** dai valori delle tensioni della maglia, che in questo caso sono sinusoidi sfasate tra loro.

> [!check] Kirchhoff non è violato: si somma coi vettori
> $2{,}66 + 4{,}24 = 6{,}9$ V, mentre il generatore dà 5 V. Sembra un assurdo, ma le due tensioni sono **sfasate di 90°**, quindi si sommano col teorema di Pitagora:
> $$\sqrt{V_R^2 + V_C^2} = \sqrt{2{,}66^2 + 4{,}24^2} = \sqrt{7{,}08 + 17{,}98} = \sqrt{25{,}06} = 5{,}01\ \text{V} \;✅$$
> Torna esattamente. **È il controllo migliore che puoi fare su questi esercizi**: se la somma pitagorica delle tensioni non dà quella del generatore, hai sbagliato qualcosa.

> [!warning] Il libro omette il segno di $Q$ — e lo fa sistematicamente
> Il libro scrive «$Q = V_{eff}I_{eff}\operatorname{sen}\varphi = 5\cdot2{,}66\cdot10^{-3}\cdot\mathbf{0{,}846} = 11{,}3$ mVAR», con il seno **positivo** (verificato sull'immagine di p. 64).
> Ma il libro stesso ha appena calcolato $\varphi = -57{,}8°$, e $\operatorname{sen}(-57{,}8°) = \mathbf{-0{,}846}$. Con la (2.29) applicata alla lettera il risultato è $Q = \mathbf{-11{,}3}$ mVAR.
>
> **Non è un refuso isolato**: nell'**esercizio 11** (p. 82), che è lo stesso tipo di circuito RC capacitivo, la chiave stampa $Q = \mathbf{87{,}6}$ µVAR — anche lì **senza il meno**. Il libro è dunque *coerente con sé stesso*: riporta il **modulo** di $Q$ e lascia la natura del carico (capacitivo/induttivo) al commento a parole. È una convenzione sciatta, non una svista.
>
> **Cosa fare tu**: scrivi comunque il segno. $Q < 0$ → carico **capacitivo**, $Q > 0$ → **induttivo**; è informazione che il modulo da solo non porta, e la (2.29) del libro te la dà gratis. Se all'esame riporti $-11{,}3$ mVAR con la motivazione, sei più corretto del libro, non meno.

### ESEMPIO 7 — Bipolo RL (Mirandola, **pp. 64-65**)

![[fig-2-21-esempio-7-rl.png]]
*FIGURA 21 — $L = 60$ mH in serie a $R = 30\ \Omega$, generatore da 220 V$_{eff}$ a 50 Hz. Mirandola, p. 64.*

$$\omega = 2\pi f = 314\ \text{rad/s} \qquad \bar{Z} = R + j\omega L = 30 + j\,18{,}8$$

Ora la parte immaginaria è **positiva**, a causa della reattanza induttiva.

$$|\bar{Z}| = \sqrt{30^2 + 18{,}8^2} = 35{,}4\ \Omega \qquad \varphi = \arctan\frac{18{,}8}{30} = 0{,}560\ \text{rad} = 32{,}1°$$

La tensione risulta **in anticipo** di 32,1° sulla corrente; $\cos\varphi = 0{,}847$.

$$I_{eff} = \frac{220}{35{,}4} = 6{,}21\ \text{A}$$

$$P = 220\cdot 6{,}21\cdot 0{,}847 = 1{,}16\ \text{kW}$$

$$Q = 220\cdot 6{,}21\cdot 0{,}532 = \mathbf{727\ VAR} \quad \text{(il libro stampa «727 kVAR» — vedi §6)}$$

$$S = 220\cdot 6{,}21 = 1{,}37\ \text{kVA}$$

$$V_R = 30\cdot 6{,}21 = 186{,}3\ \text{V} \qquad V_L = \omega L\,I_{eff} = 314\cdot 60\cdot10^{-3}\cdot 6{,}21 = 117{,}0\ \text{V}$$

> [!check] Anche qui il controllo pitagorico funziona
> $\sqrt{186{,}3^2 + 117^2} = \sqrt{34708 + 13689} = \sqrt{48397} = 220{,}0$ V ✅ — esattamente la tensione del generatore.
>
> E nota il contrasto con l'ESEMPIO 6: stesso schema di ragionamento, ma **tutti i segni sono opposti** perché il componente reattivo è un'induttanza invece di un condensatore. $X > 0$, $\varphi > 0$, $Q > 0$, tensione in anticipo.

---

## 5. Il rifasamento degli impianti industriali

Questa è la parte con più domande da orale (quesiti 21–24 del libro).

### Il problema

Dal libro (Mirandola, **§4.2 «Il rifasamento degli impianti industriali», p. 65**):

> Come si è visto negli esempi precedenti, la presenza di una componente reattiva nel carico introduce uno sfasamento $\varphi$ tra la tensione e la corrente fornita dal generatore. Ciò fa sì che la potenza realmente sfruttata dal carico (**potenza attiva**) sia **inferiore di un fattore $\cos\varphi$** rispetto a quella calcolata con il prodotto $V_{eff}I_{eff}$ sul generatore (**potenza apparente**), a causa della potenza reattiva mutuamente scambiata tra generatore e carico.
>
> Questo scambio di potenza reattiva provoca una **corrente sulla linea** di collegamento tra generatore e carico e la relativa **dissipazione di potenza per effetto Joule**; nel caso di impianti industriali ciò costringerebbe l'ente distributore a **sovradimensionare i cavi di trasporto e le macchine generatrici**, senza che ciò si traduca in maggiore potenza fruibile dall'utilizzatore.

> [!tip] Il punto in una frase
> La potenza reattiva **non si consuma**, ma **viaggia**. E mentre viaggia sui cavi, li scalda. Paghi il trasporto di energia che non usi.

Il libro spiega perché il problema è industriale:

> Gli impianti industriali generalmente presentano verso la linea elettrica un **carico resistivo-induttivo**, come quello dell'ESEMPIO 7, a causa degli utilizzatori come i **motori, le saldatrici, gli alimentatori delle lampade fluorescenti, i trasformatori** ecc., che hanno al loro interno degli **avvolgimenti**.

Un avvolgimento è un'induttanza. Ecco perché il carico industriale è quasi sempre induttivo — e perché la correzione si fa **sempre** con condensatori.

### La soluzione

> La soluzione adottata è quella di inserire, **in parallelo al carico**, una batteria di **condensatori di rifasamento**, con valore tale da compensare, per lo meno parzialmente, la reattanza induttiva del carico e aumentare quindi il $\cos\varphi$ dell'impianto.

![[fig-2-23-rifasamento.png]]
*FIGURA 23 — **A)** Condensatore di rifasamento in parallelo al carico resistivo-induttivo. **B)** Diagramma vettoriale. Mirandola, §4.2, p. 66.*

Il valore della capacità si calcola con:

$$C_{rifas} = \frac{P(\operatorname{tg}\varphi - \operatorname{tg}\varphi')}{\omega V^2} \tag{2.33}$$

dove $\varphi$ è il **vecchio** sfasamento, $\varphi'$ il **nuovo** (minore di $\varphi$), $P$ la potenza attiva assorbita dal carico, $\omega$ la pulsazione, $V$ il valore efficace della tensione d'ingresso.

Come funziona, guardando la FIGURA 23B:

> la corrente di linea $I'$ è la risultante della somma (regola del parallelogramma) della corrente $I_C$ del condensatore (**in anticipo di 90° rispetto a $V$**) con la $I$ del carico; si ottiene così uno sfasamento $\varphi'$ tra $V$ e $I'$ **inferiore** rispetto allo sfasamento $\varphi$ che si aveva in assenza del condensatore.

> [!check] Perché proprio un condensatore
> Il carico induttivo assorbe $Q > 0$. Il condensatore fornisce $Q < 0$. Messi in parallelo, **le due potenze reattive si sottraggono** e la linea deve trasportarne meno.
> È lo stesso meccanismo della risonanza di [[Reti RLC e risonanza]] — reattanze di segno opposto che si compensano — solo che qui la compensazione è **parziale e voluta**: non si punta a $\cos\varphi = 1$ esatto, ma a un valore obiettivo (tipicamente 0,9–0,95).

Due precisazioni del libro:

- Il valore di $C_{rifas}$ è **riferito a un dato valore $P$**; se la potenza è variabile (macchinari accesi o spenti), serve un **circuito che misura il $\cos\varphi$ e inserisce automaticamente i condensatori opportuni**.
- **La potenza attiva $P$ dell'utenza non viene modificata** dalla presenza dei condensatori di rifasamento.

> [!warning] Il rifasamento non ti fa consumare meno
> Punto che all'orale fa la differenza: rifasare **non riduce la bolletta dell'energia attiva**. $P$ resta identica, i motori girano uguale. Quello che cambia è la **corrente di linea** e le **penali**.

### La normativa

> La **normativa** richiede che, per carichi con $P > 15$ kW, l'utente assorba energia con un fattore di potenza (media mensile) $\cos\varphi_{mm} \ge 0{,}9$.
> - Se $0{,}7 \le \cos\varphi_{mm} < 0{,}9$, l'utente può **scegliere** se pagare una penale o rifasare il carico.
> - Se $\cos\varphi_{mm} < 0{,}7$, l'utente è **obbligato** a rifasare.
>
> In nessun caso comunque l'impianto dell'utente deve **erogare energia reattiva di tipo capacitivo** alla rete.

E la valutazione economica:

> In genere il rifasamento è la soluzione migliore sia dal punto di vista del **risparmio energetico** che da quello **economico**, in quanto il costo della batteria di condensatori viene **recuperato in breve tempo** rispetto a quello che si dovrebbe sostenere per le penali.

> [!note] Attenzione al «non erogare reattiva capacitiva»
> Vuol dire: **non esagerare col rifasamento**. Se metti troppa capacità, il $\cos\varphi$ torna a peggiorare — ma dall'altra parte, con $\varphi$ che diventa negativo. È il motivo per cui si punta a 0,9–0,95 e non a 1,00: si lascia un margine per non rischiare di sovracompensare quando i carichi variano.

### I vantaggi (quesito 24)

I vantaggi che si ottengono con il rifasamento, cioè con l'aumento del $\cos\varphi$:

- **diminuisce la potenza apparente** dell'utenza (carico + batteria) e quindi si riduce la **corrente nella linea**;
- **diminuiscono le perdite di potenza in linea** e quindi aumenta il **rendimento** della linea;
- diminuendo la corrente si può progettare la linea con una **sezione inferiore**;
- anche le **macchine che producono** l'energia elettrica possono essere dimensionate per una corrente inferiore;
- diminuiscono le **cadute di tensione** sulla linea;
- l'utenza rifasata richiede minore potenza apparente e quindi l'ente che eroga l'energia può **soddisfare più utenze**.

E la conseguenza pratica:

> Poiché i vantaggi del rifasamento si fanno sentire su **tutta la rete a monte**, è evidente la convenienza di un **rifasamento capillare**, con i condensatori il più vicino possibile ai luoghi dove la potenza induttiva è assorbita, e quindi ai morsetti degli apparecchi utilizzatori; questo riduce le perdite per energia reattiva sui cavi **all'interno dell'industria**, con un risparmio sulla bolletta da parte dell'utente.

> [!tip] Tutti i vantaggi discendono da uno solo
> Non impararli a memoria come sei punti scollegati. **Sono tutti conseguenze di una cosa sola: scende la corrente di linea.**
> Meno corrente → meno perdite Joule ($P_{persa} = R_{linea}I^2$) → meno cadute di tensione ($\Delta V = R_{linea}I$) → cavi più sottili → generatori più piccoli → più utenti serviti con la stessa rete.
> All'orale, dire «diminuisce la corrente di linea, e da qui discende tutto il resto» vale più che elencare sei punti a memoria.

### ESEMPIO 8 — Rifasamento (Mirandola, **p. 67**)

![[fig-2-24-esempio-8.png]]
*FIGURA 24 — Il bipolo dell'ESEMPIO 7 con il condensatore di rifasamento da 22,7 µF. Mirandola, p. 67.*

Determinare $C_{rifas}$ da porre in parallelo al bipolo dell'ESEMPIO 7 per rifasare a $\cos\varphi' = 0{,}95$.

Il nuovo sfasamento deve risultare:

$$\varphi' = \arccos 0{,}95 = 0{,}318\ \text{rad} = 18{,}2°$$

Applicando la (2.33), con $\varphi = 0{,}560$ rad (vecchio sfasamento, dall'ESEMPIO 7), $\varphi' = 0{,}318$ rad (nuovo), $P = 1{,}16$ kW, $\omega = 314$ rad/s, $V = 220$ V:

$$C_{rifas} = \frac{1160\cdot(0{,}627 - 0{,}329)}{314\cdot 220^2} = 22{,}7\ \mu\text{F}$$

Il libro invita a verificare con Multisim che il valore efficace della corrente fornita dal generatore (**5,58 A**) è inferiore rispetto al caso non rifasato (**6,21 A**), mentre la potenza attiva — e quindi la tensione sulla porzione resistiva del carico — è **inalterata**.

> [!check] Verifica il risultato senza Multisim
> Puoi controllare la corrente rifasata con una riga. Dopo il rifasamento $P$ non cambia, quindi:
> $$I' = \frac{P}{V\cos\varphi'} = \frac{1160}{220\cdot 0{,}95} = 5{,}55\ \text{A}$$
> Il libro dice 5,58 A ✅ (la differenza è arrotondamento).
> Guadagno: da 6,21 A a 5,55 A, cioè **circa l'11% di corrente in meno** sulla linea — e le perdite Joule, che vanno col **quadrato** della corrente, calano di circa il 20%. Con lo stesso lavoro utile.

> [!note] Un refuso innocuo nel libro ✅ *verificato sull'immagine di p. 67*
> Nell'ESEMPIO 8 il libro scrive «$\varphi' = 0{,}560$ rad (vecchio sfasamento), $\varphi' = 0{,}318$ rad (nuovo sfasamento)»: ha etichettato **entrambi** $\varphi'$. Il primo è ovviamente $\varphi$, senza apice. I conti sono giusti, è solo la stampa.

---

## 6. ⚠️ Errata corrige

> [!danger] Errore grosso — ESEMPIO 7, **p. 65**: «727 kVAR» ✅ *verificato sull'immagine*
> Il libro calcola la potenza reattiva dell'ESEMPIO 7 così:
> $$Q = V_{eff}I_{eff}\operatorname{sen}\varphi = 220\cdot 6{,}21\cdot 0{,}532 = 727\ \mathbf{kVAR}$$
> **Il risultato è 727 VAR, non 727 kVAR.** Fai il prodotto: $220 \times 6{,}21 = 1366$, e $1366 \times 0{,}532 = 727$. Nessun migliaio in vista.
>
> **Come smascherarlo in tre secondi**, senza rifare il conto: due righe più sotto il libro scrive $S = 1{,}37$ **kVA**. Ma dal triangolo delle potenze (§3), $S = \sqrt{P^2+Q^2}$ è l'**ipotenusa**: deve essere **la più grande delle tre**. Se $Q$ fosse davvero 727 kVAR, sarebbe **530 volte** più grande di $S$ — geometricamente impossibile.
>
> Con il valore corretto torna tutto:
> $$S = \sqrt{P^2 + Q^2} = \sqrt{1160^2 + 727^2} = \sqrt{1.345.600 + 528.529} = 1369\ \text{VA} = 1{,}37\ \text{kVA} \;✅$$
>
> **La lezione**: in questo tipo di esercizio hai sempre un controllo gratuito. Calcola $P$, $Q$ e $S$ per strade indipendenti e verifica che il triangolo chiuda. Se non chiude, uno dei tre è sbagliato.

> [!warning] Segno omesso (non un errore isolato) — ESEMPIO 6, **p. 64**: «$Q = 11{,}3$ mVAR»
> Vedi il riquadro nel §4. Applicando la (2.29) alla lettera il valore è $Q = \mathbf{-11{,}3}$ mVAR, perché il carico è **capacitivo**.
> ⚠️ **Correzione di una versione precedente di questa nota**, che sosteneva «il libro stesso usa il segno negativo nell'esercizio 11». **È falso**: la chiave dell'esercizio 11 (p. 82) stampa $Q = 87{,}6$ µVAR, *senza* meno — verificato sull'immagine. Il libro omette il segno in **entrambi** i casi capacitivi, quindi non si contraddice: adotta la convenzione del modulo. Il consiglio operativo (scrivi il segno) resta valido; l'argomento «lo dice il libro» no.

> [!info] Perché te lo segnalo invece di riscrivere il libro e basta
> Non è per screditare il libro, che resta il tuo testo: è perché **studiare quelle righe alla lettera ti farebbe sbagliare l'esercizio**.
> Ma attenzione a non fare l'errore opposto — cioè accumulare una lista di «errori del libro» senza verificarli. Qui, aprendo le pagine a 220 dpi, dei tre addebiti iniziali **uno solo era un errore vero** (i 727 kVAR); gli altri due sono una convenzione discutibile e un refuso tipografico. Il conteggio onesto per questo paragrafo è quindi **1 errore**, non 2.
> E c'è una cosa che vale più delle formule: l'errore vero era smascherabile **con un controllo interno** — il triangolo delle potenze che non chiude, $Q$ 530 volte più grande dell'ipotenusa $S$. Se impari a fare quei controlli, non ti serve che qualcuno ti dica dove sono gli errori.

---

## 7. Da qui in poi

- Prerequisiti: [[Impedenza dei bipoli R, L, C]] · [[Il metodo simbolico]]
- Correlati: [[Segnali sinusoidali e fasori]] · [[Reti RLC e risonanza]]
- Esercizi: [[Esercizi - Le potenze in alternata]]
