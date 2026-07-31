---
tags: [recupero, elettronica, corrente-alternata, metodo-simbolico]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2, Cap. 2 «La corrente alternata», §3 «Il metodo simbolico», pp. 60-61 (pag.-PDF 8). Folio letto dal piè di pagina; citazioni confrontate parola per parola su OCR + immagine a 220 dpi. ESEMPIO 5 (FIG. 17A-17B) verificato sull'immagine."
prove: [scritta, orale]
---

# Il metodo simbolico

> [!info] Dove serve
> **Scritta** e **orale** (Carli): «circuiti in corrente alternata». È il **procedimento operativo** con cui risolverai concretamente gli esercizi: le note precedenti costruiscono gli strumenti, questa dice come usarli.

Prerequisiti: [[Segnali sinusoidali e fasori]] · [[Impedenza dei bipoli R, L, C]].

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §3**.

## 1. Che cos'è, e a cosa serve

Dal libro (Mirandola, Cap. 2 §3, p. 60):

> Il **metodo simbolico** è utilizzato per semplificare l'analisi delle reti lineari in **regime sinusoidale**, resa complessa dalle relazioni integro-differenziali esistenti tra le grandezze elettriche, relative alla presenza di condensatori e induttori.

Ed ecco l'idea in una frase (sempre dal libro):

> Il metodo simbolico consiste nel **sostituire alle eccitazioni sinusoidali isofrequenziali di un circuito i relativi numeri complessi (o i vettori) rappresentativi**. Se la rete è lineare, qualunque grandezza al suo interno sarà sinusoidale, con frequenza identica a quella delle eccitazioni, e quindi rappresentabile con un numero complesso.
>
> Grazie a questa tecnica le relazioni integro-differenziali tra le grandezze in funzione del tempo, dovute alla presenza dei componenti reattivi, **si trasformano in relazioni algebriche** tra i numeri complessi rappresentativi di quelle grandezze, semplificando notevolmente i calcoli.

E la conseguenza che rende tutto il capitolo un affare:

> **Tutti i principi e i teoremi studiati per le reti in continua si possono così utilizzare in maniera formalmente identica**, sostituendo alle grandezze continue i numeri complessi rappresentativi di quelle sinusoidali e ricavando i numeri complessi delle incognite.

> [!tip] Il senso di tutto il capitolo, in tre righe
> Non stai imparando una nuova teoria dei circuiti. Stai imparando un **cambio di valuta**: converti le sinusoidi in numeri complessi, applichi **la stessa identica elettrotecnica** che sai già dalla continua (Ohm, Kirchhoff, partitore, Thévenin, Millman), e riconverti il risultato in sinusoidi.
> Il prezzo da pagare è fare i conti con i numeri complessi invece che con i reali. Il premio è non dover mai risolvere un'equazione differenziale.

---

## 2. I limiti: quando NON si può usare

Due condizioni, e il libro le mette in chiaro subito (Mirandola, Cap. 2 §3, p. 60, secondo capoverso). Sono **materiale da orale**, perché è la domanda naturale dopo «cos'è il metodo simbolico».

> Questo metodo vale **solo per la fase di regime permanente sinusoidale**, cioè una volta esaurito il **transitorio** successivo all'applicazione delle eccitazioni sinusoidali, che devono essere **isofrequenziali** nel caso fossero più di una.

Quindi:

1. **Solo a regime permanente.** Nell'istante in cui accendi il circuito c'è un transitorio, e lì il metodo simbolico non dice nulla. Bisogna aspettare che il transitorio si esaurisca.
2. **Solo con eccitazioni isofrequenziali.** Se nel circuito ci sono due generatori a frequenze diverse, non puoi rappresentarli con fasori nello stesso diagramma — per il motivo spiegato in [[Segnali sinusoidali e fasori]]: ruoterebbero a velocità diverse.

> Per lo studio della **fase transitoria**, compresa tra l'applicazione dei segnali e lo stabilirsi del regime sinusoidale, si utilizza invece il metodo della **trasformata di Laplace**.

> [!note] Laplace non ti serve
> Il libro rimanda al **Capitolo 3** per la trasformata di Laplace — capitolo che **c'è** nella tua scansione (inizia a **p. 102**, pag.-PDF 29, §1 «Metodo della trasformata di Laplace»). Semplicemente **non ti serve**: la tua lettera non lo richiede e Laplace non compare in nessuna delle tre prove. Puoi ignorarlo.
> Ti basta sapere che **esiste** e a cosa serve (i transitori), perché è la risposta alla domanda «e se il circuito non fosse a regime?».

> [!question] E se ci fossero due generatori a frequenze diverse?
> Domanda plausibile all'orale, e la risposta è elegante: si usa il **principio di sovrapposizione degli effetti**. Si risolve il circuito **una frequenza alla volta** — spegnendo gli altri generatori — con il metodo simbolico, e poi si **sommano nel tempo** i risultati.
> Non si possono sommare i fasori (frequenze diverse!), ma si possono sommare le sinusoidi una volta ritornati nel dominio del tempo. La linearità della rete è ciò che lo consente.

---

## 3. Il procedimento

![[fig-2-proc-metodo-simbolico.png]]
*Riquadro **PROCEDIMENTO** — i tre passi dell'analisi col metodo simbolico. Mirandola, Cap. 2 §3, p. 61.*

I tre passi, dal libro:

1. **Si associano alle tensioni e alle correnti di eccitazione sinusoidali i corrispondenti numeri complessi** (o vettori/fasori) rappresentativi.
2. **Per risolvere la rete si utilizzano gli stessi principi e teoremi validi per il regime continuo**: nei bipoli lineari la relazione tra tensione e corrente è data dall'impedenza del bipolo ($\bar{V} = \bar{Z}\cdot\bar{I}$) e le operazioni tra i segnali possono essere eseguite sui numeri complessi oppure graficamente sui relativi vettori.
3. **Ogni tensione o corrente nella rete risulterà sinusoidale**, a causa della linearità, con frequenza di valore identico a quella dei generatori, e ampiezza e fase ricavabili dai moduli e argomenti trovati.

E il libro chiude con la nota operativa (Mirandola, Cap. 2 §3, p. 60, ultimo capoverso prima del riquadro PROCEDIMENTO):

> Alla fine è sufficiente calcolare i valori dei **moduli** e degli **argomenti** dai numeri complessi ottenuti, per risalire alle corrispondenti espressioni, in funzione del tempo, delle grandezze sinusoidali incognite.

> [!check] La struttura è sempre questa
> Ogni esercizio di questo capitolo ha la stessa forma a tre tempi:
>
> **1. ENTRA nel mondo complesso** — trasforma i dati: $\omega = 2\pi f$; i generatori diventano numeri complessi; $R \to R$, $L \to j\omega L$, $C \to -j/\omega C$.
> **2. RISOLVI come in continua** — partitore, serie, parallelo, Kirchhoff. Nessuna formula nuova, solo aritmetica complessa.
> **3. ESCI dal mondo complesso** — calcola modulo e argomento del risultato, e traducili in ampiezza e fase.
>
> Se in un esercizio ti blocchi, quasi sempre è perché hai saltato il passo 1 (dimenticato di convertire un componente) o il passo 3 (fermato al numero complesso senza dare modulo e fase).

---

## 4. L'esempio svolto del libro

**ESEMPIO 5** (Mirandola, Cap. 2 §3, **p. 61**). Calcolare modulo e argomento della tensione $v_{R2}$ nel circuito di FIGURA 17A e disegnare il diagramma vettoriale delle tensioni $v_{R2}$ e $v_g$, supponendo $v_g$ di frequenza $f = 2$ kHz, ampiezza $V_g = 2$ V$_{eff}$ e fase iniziale nulla ($\varphi = 0$).

![[fig-2-17a-esempio-5.png]]
*FIGURA 17A — Il circuito dell'ESEMPIO 5: $R_1 = 5{,}6$ k$\Omega$ in parallelo a $C = 22$ nF, il tutto in serie a $R_2 = 1{,}8$ k$\Omega$. Mirandola, Cap. 2 §3, p. 61.*

### Passo 1 — Entrare nel mondo complesso

Il numero complesso rappresentativo di $v_g$ ha **parte immaginaria uguale a zero**, avendo supposto fase nulla:

$$\bar{V}_g = 2$$

La frequenza $f = 2$ kHz corrisponde alla pulsazione:

$$\omega = 2\pi f = 12{,}6\cdot10^{3}\ \text{rad/s}$$

### Passo 2 — Risolvere come in continua

Il circuito è un **partitore di tensione** tra l'impedenza del parallelo $C$–$R_1$ e la resistenza $R_2$. Prima serve l'impedenza del parallelo:

$$\bar{Z}_{CR_1} = \frac{R_1 \cdot \frac{1}{j\omega C}}{R_1 + \frac{1}{j\omega C}} = \frac{R_1}{1 + j\omega C R_1} = \frac{R_1(1 - j\omega C R_1)}{(1 + j\omega C R_1)(1 - j\omega C R_1)} = \frac{R_1 - j\omega C R_1^2}{1 + \omega^2 C^2 R_1^2}$$

(di nuovo la moltiplicazione per il coniugato, come nell'ESEMPIO 2). Sostituendo i valori:

$$\bar{Z}_{CR_1} = 1{,}6\cdot10^{3} - j\,2{,}6\cdot10^{3}$$

Ora il partitore, considerando nulla la fase iniziale di $v_g$:

$$\bar{V}_{R_2} = \frac{\bar{V}_g \cdot \bar{Z}_2}{\bar{Z}_{CR_1} + \bar{Z}_2} = \frac{|V_g|\cdot R_2}{\bar{Z}_{CR_1} + R_2} = \frac{2\cdot 1{,}8\cdot10^{3}}{1{,}6\cdot10^{3} - j\,2{,}6\cdot10^{3} + 1{,}8\cdot10^{3}} = \frac{3{,}6}{3{,}4 - j\,2{,}6}$$

Per separare la parte reale da quella immaginaria si moltiplicano numeratore e denominatore per $(3{,}4 + j\,2{,}6)$, in modo da rendere reale il denominatore:

$$\bar{V}_{R_2} = \frac{3{,}6(3{,}4 + j\,2{,}6)}{(3{,}4 - j\,2{,}6)(3{,}4 + j\,2{,}6)} = \frac{12 + j\,9{,}4}{3{,}4^2 + 2{,}6^2} = 0{,}66 + j\,0{,}51$$

### Passo 3 — Uscire dal mondo complesso

$$|\bar{V}_{R_2}| = \sqrt{0{,}66^2 + 0{,}51^2} = 0{,}83\ \text{V}$$

$$\varphi = \angle\bar{V}_{R_2} = \arctan\frac{0{,}51}{0{,}66} = 0{,}66\ \text{rad} = 37{,}7°$$

Il diagramma vettoriale delle tensioni $v_{R_2}$ e $v_g$ è riportato in FIGURA 17B.

> [!note] Se rifai i conti senza arrotondare, ti viene 0,84 V e 36,5°
> Il libro **è coerente con sé stesso**: scrive $0{,}66 + j\,0{,}51$ e da lì ricava 0,83 V e 37,7°. Il punto è che arrotonda **a ogni passaggio**, e gli errori si accumulano.
> Rifacendo la catena con i valori pieni ($\omega = 12\,566$ rad/s, $\bar Z_{CR_1} = 1{,}649 - j\,2{,}552$ k$\Omega$) si ottiene $\bar V_{R_2} = 0{,}674 + j\,0{,}499$, cioè **0,84 V** e **36,5°**.
> Uno scarto di 0,01 V e 1,2°: irrilevante in pratica, ma se all'esame il tuo numero differisce dal libro nella seconda cifra, **non stai necessariamente sbagliando** — controlla prima quanti arrotondamenti intermedi hai fatto. Qui ho lasciato i numeri del libro, così il confronto con la pagina è immediato.

> [!check] Il senso fisico del risultato
> Da 2 V in ingresso escono **0,83 V**, sfasati **in anticipo di 37,7°**.
> - **L'attenuazione** è normale: è un partitore fatto di componenti passivi, l'uscita non può che essere minore dell'ingresso.
> - **L'anticipo** ti dice quale componente comanda. La fase è **positiva**, e infatti $\bar{Z}_{CR_1}$ ha parte immaginaria **negativa** ($-2{,}6$ k$\Omega$): reattanza capacitiva. Vedi il §4 di [[Impedenza dei bipoli R, L, C]].
> - **Controllo rapido**: senza il condensatore avresti un partitore puramente resistivo, $2\cdot\frac{1800}{5600+1800} = 0{,}49$ V con fase zero. Il condensatore, riducendo l'impedenza del ramo superiore, fa **passare più segnale** (0,83 > 0,49) e introduce lo sfasamento. Torna tutto.

---

## 5. Da qui in poi

- Prerequisiti: [[Segnali sinusoidali e fasori]] · [[Impedenza dei bipoli R, L, C]]
- Poi: [[Le potenze in alternata]] · [[Reti RLC e risonanza]]
- Applicazione: [[Filtri passivi del primo ordine]]
- Esercizi: [[Esercizi - Il metodo simbolico]]
