---
tags: [recupero, elettronica, corrente-alternata, fasori]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2 (Zanichelli 2012), Cap. 2 «La corrente alternata», §§1.1-1.3, pp. 46-51 (pagg.-PDF 1-3). Formule (2.1)-(2.7) ed ESEMPIO 1 controllati fedeli al testo via OCR+lettura pagine (2026-07-19). Vedi [[00 - Fonti e note]]."
prove: [scritta, orale, pratica]
---

# Segnali sinusoidali e fasori

> [!info] Dove serve
> **Scritta** e **orale** (Carli): «circuiti in corrente alternata». **Pratica** (Protti): «segnali sinusoidali». È il primo mattone di tutto il capitolo: senza questo, impedenza e potenze non stanno in piedi.

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §1**.

## 1. Perché tutto ruota attorno alle sinusoidi

Il libro apre il capitolo con una domanda implicita: perché dedicare un capitolo intero a *una sola* forma d'onda? Due motivi (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3):

- **la tensione disponibile nella rete di distribuzione elettrica ha forma sinusoidale**;
- **qualunque forma d'onda può essere scomposta in una somma di sinusoidi** (teorema di Fourier).

Il secondo motivo è quello grosso, e vale la pena fermarsi. Non stai studiando un caso particolare: stai studiando il **mattone universale**. Se sai come un circuito lineare risponde a *una* sinusoide di una certa frequenza, sai come risponde a *qualunque* segnale — perché basta scomporlo in sinusoidi, vedere cosa succede a ciascuna, e risommare. È esattamente quello che farai con i filtri in [[Filtri passivi del primo ordine]].

### Il problema che i fasori risolvono

Ecco la parte che il libro spiega bene e che conviene capire subito, perché è la ragione d'essere di tutto il capitolo (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3).

In continua, a regime, la vita è facile: per analizzare una rete basta **cortocircuitare gli induttori e aprire i condensatori**, e resta una rete di sole resistenze. Legge di Ohm e via.

Ma appena le tensioni variano nel tempo, condensatori e induttori si comportano secondo relazioni **integro-differenziali**:

$$v_L(t) = L\frac{di(t)}{dt} \qquad\qquad i_C(t) = C\frac{dv(t)}{dt}$$

Analizzare una rete significherebbe risolvere un sistema di **equazioni differenziali**. Per un circuito di quattro componenti diventa già un incubo.

> Si utilizzano in questi casi metodi matematici di **trasformazione**, che consentono di convertire le relazioni integro-differenziali tra le grandezze elettriche della rete in **equazioni algebriche**, di più agevole soluzione.
>
> In generale si definisce *trasformazione* un'operazione che, attraverso l'opportuna modifica delle variabili, consente di trasformare operazioni complesse in altre più semplici.

Questa è l'idea centrale: **cambiare linguaggio per rendere facile un problema difficile**. Le derivate diventano moltiplicazioni. Le equazioni differenziali diventano equazioni algebriche di primo grado.

Il metodo si chiama **metodo simbolico** (o trasformata di Steinmetz), e lo vedi in dettaglio in [[Il metodo simbolico]]. Funziona **solo** in regime sinusoidale permanente. Per i transitori serve la trasformata di Laplace (Cap. 3 del libro; fuori programma per il tuo esame).

---

## 2. Il fasore: una sinusoide diventa una freccia

Un segnale sinusoidale è descritto da:

$$v(t) = V_p \operatorname{sen}(\omega t + \varphi)$$

Tre numeri lo definiscono: l'**ampiezza di picco** $V_p$, la **pulsazione** $\omega$, la **fase iniziale** $\varphi$.

Ora l'osservazione chiave del libro (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3):

> È possibile associare a segnali sinusoidali **isofrequenziali** altrettanti **vettori in un piano** (*fasori*): facendo ruotare il sistema di vettori con velocità angolare pari alla pulsazione $\omega$, comune a tutti i segnali, le rispettive proiezioni su uno degli assi cartesiani presentano, in funzione del tempo, l'andamento sinusoidale dei segnali originari.

![[fig-2-02-fasori.png]]
*FIGURA 2 — Relazione tra l'andamento temporale di segnali sinusoidali e i corrispondenti vettori «rotanti» (fasori).*

Guarda bene la figura: **a sinistra** ci sono due frecce in un piano, **a destra** due sinusoidi nel tempo. Non sono due cose diverse: sono **la stessa cosa vista in due modi**. Se fai ruotare le frecce a velocità $\omega$ e proietti la loro punta sull'asse verticale, ottieni le sinusoidi di destra.

Le regole di corrispondenza (dal libro):

- **a)** la lunghezza del vettore, cioè il **modulo** $|V|$, è pari al valore di picco $V_p$ del segnale;
- **b)** l'angolo tra il vettore e l'asse orizzontale **nell'istante $t = 0$** è la **fase iniziale** o argomento ($\angle V$, $\varphi$);
- **c)** l'angolo compreso tra due vettori rappresenta lo **sfasamento** $\Delta\varphi = \varphi_1 - \varphi_2$ tra i corrispondenti segnali.

Modulo e argomento sono le **coordinate polari** del vettore al tempo $t = 0$.

### Leggere la FIGURA 2

Il libro fa un esempio concreto: nei segnali di FIGURA 2 si ha $\varphi_1 = +\pi/4$ rad e $\varphi_2 = -\pi/4$ rad, per cui lo sfasamento vale

$$\Delta\varphi = \varphi_1 - \varphi_2 = \frac{\pi}{2}\ \text{rad} = 90°$$

Questo significa che $v_2(t)$ è in **ritardo di 1/4 di periodo** rispetto a $v_1(t)$ — e lo puoi verificare guardando il grafico nel tempo.

> [!tip] Da radianti a frazioni di periodo
> Un giro completo, $2\pi$ rad, è **un periodo**. Quindi $\pi/2$ rad $= \frac{1}{4}$ di giro $= \frac{1}{4}$ di periodo. È la conversione che ti serve ogni volta che l'oscilloscopio ti mostra due onde sfasate e devi dire di quanto: misuri lo scarto in millisecondi, lo dividi per il periodo, moltiplichi per 360°. Vedi [[L'oscilloscopio]].

### Le due cose che il fasore NON ti dice

Due avvertenze del libro che a un orale valgono oro (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3):

1. **Il diagramma vettoriale non contiene nessuna informazione sulla pulsazione $\omega$**, e quindi sulla frequenza, che «deve essere comunicata a parte». Il fasore congela il segnale a $t = 0$: dice ampiezza e fase, non dice quanto va veloce.
2. Poiché i vettori **ruotano come fossero connessi rigidamente tra loro**, ciò che interessa è la loro **posizione reciproca**. Per questo si tende a far coincidere un vettore con un asse, a scelta, per semplificare i calcoli.

> [!warning] La condizione che non puoi violare
> I fasori funzionano **solo tra segnali isofrequenziali**. Se due sinusoidi hanno frequenze diverse, i loro vettori ruoterebbero a velocità diverse, l'angolo tra loro cambierebbe di continuo e il disegno perderebbe senso. Tutta l'analisi in regime sinusoidale presuppone **una sola frequenza alla volta**.

---

## 3. Le operazioni tra fasori

Tutte le operazioni tra grandezze sinusoidali si possono fare sui vettori corrispondenti:

![[fig-2-03-operazioni-tra-vettori.png]]
*FIGURA 3 — Operazioni tra vettori: **A)** moltiplicazione per una costante $k$; **B)** somma; **C)** differenza; **D)** prodotto; **E)** rapporto.*

- **a) Moltiplicazione per una costante** ($k \cdot \bar{V}$): il modulo è pari al prodotto del modulo per la costante $k$; **la fase rimane invariata**.
- **b) Somma** ($\bar{V}_1 + \bar{V}_2$): si sfrutta la **regola del parallelogramma**.
- **c) Differenza** ($\bar{V}_1 - \bar{V}_2$): si somma $\bar{V}_1$ a $\bar{V}_2$ **con il verso invertito**; oppure si congiungono $\bar{V}_1$ e $\bar{V}_2$ con il verso che va **da $\bar{V}_2$ a $\bar{V}_1$**.
- **d) Prodotto** ($\bar{V}_1 \cdot \bar{V}_2$): il modulo è il **prodotto dei moduli**, la fase è la **somma delle fasi**.
- **e) Rapporto** ($\bar{V}_1 : \bar{V}_2$): il modulo è il **rapporto dei moduli**, la fase è la **differenza delle fasi**.

> [!tip] Il criterio per scegliere la rappresentazione
> Guarda le regole d) ed e): prodotto e rapporto lavorano su **moduli e fasi**, cioè su coordinate **polari**. La somma invece (regola b) è un parallelogramma, che sui numeri complessi si fa sommando parti reali e parti immaginarie: coordinate **cartesiane**.
> Da qui la regola pratica che ti fa risparmiare tempo negli esercizi:
> - **somme e differenze** → forma cartesiana $a + jb$
> - **prodotti, rapporti e potenze** → forma polare/esponenziale $|V|e^{j\varphi}$
>
> Passare avanti e indietro tra le due (§4) non è una perdita di tempo: è la mossa che rende ogni pezzo facile.

---

## 4. La rappresentazione complessa

Un vettore può essere individuato, oltre che da modulo e fase, anche mediante un **numero complesso**:

$$\bar{V} = a + jb$$

dove la **parte reale** $a$ e la **parte immaginaria** $b$ sono le coordinate del vertice del vettore nel **piano complesso** (o piano di Gauss). La rappresentazione in forma complessa di una grandezza sinusoidale si chiama **rappresentazione simbolica** — da cui il nome «metodo simbolico».

### Le proprietà di $j$

Il libro ne evidenzia due (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3), e la seconda è la più importante di tutto il capitolo:

- **a)** $j \cdot j = -1$;
- **b)** **moltiplicare per $j$ un numero complesso equivale a sfasare di 90° in anticipo la grandezza sinusoidale corrispondente.**

> [!check] Perché moltiplicare per $j$ ruota di 90°
> Il libro dà la proprietà b) senza dimostrarla, ma segue subito dalla forma esponenziale (§5). Poiché $j = e^{j\pi/2}$, moltiplicare per $j$ significa:
> $$|V|e^{j\varphi} \cdot e^{j\pi/2} = |V|e^{j(\varphi + \pi/2)}$$
> Il modulo non cambia, l'argomento aumenta di $\pi/2 = 90°$. Moltiplicare per $j$ **è** ruotare di un quarto di giro.
>
> Perché ti serve: è il motivo per cui l'impedenza dell'induttore è $\bar{Z}_L = j\omega L$ e quella del condensatore $\bar{Z}_C = -j/\omega C$. Quel $j$ **è** lo sfasamento di 90° tra tensione e corrente nei componenti reattivi. Non è un artificio di calcolo: è la fisica scritta in forma compatta. Vedi [[Impedenza dei bipoli R, L, C]].

### La somma in forma complessa

![[fig-2-05-formula-di-eulero.png]]
*FIGURA 5 — Costruzione grafica della formula di Eulero.*

Se $\bar{V}_1 = a_1 + jb_1$ e $\bar{V}_2 = a_2 + jb_2$, la somma vale:

$$\bar{V}_1 + \bar{V}_2 = a_1 + a_2 + j(b_1 + b_2) \tag{2.1}$$

Si sommano le parti reali tra loro e le parti immaginarie tra loro. Il risultato coincide con la regola del parallelogramma: sono la stessa operazione, scritta in due modi.

### Le conversioni — da sapere a memoria

**Cartesiane → Polari**

$$\text{Modulo:}\qquad V_p = |\bar{V}| = \sqrt{a^2 + b^2} \tag{2.2}$$

$$\text{Argomento:}\quad
\begin{cases}
\varphi = \arctan\dfrac{b}{a} & \text{(1° quadrante: } a>0,\ b>0)\\[6pt]
\varphi = \arctan\dfrac{b}{a} + \pi & \text{(2° e 3° quadrante: } a<0)\\[6pt]
\varphi = \arctan\dfrac{b}{a} + 2\pi & \text{(4° quadrante: } a>0,\ b<0)
\end{cases} \tag{2.3}$$

**Polari → Cartesiane**

$$a = |\bar{V}|\cos\varphi \tag{2.4} \qquad\qquad b = |\bar{V}|\operatorname{sen}\varphi \tag{2.5}$$

> [!danger] L'errore che la calcolatrice ti fa fare
> La **(2.3)** non è pedanteria: è la trappola numero uno degli esercizi sui fasori.
> La funzione $\arctan$ della calcolatrice restituisce **sempre** un angolo tra $-90°$ e $+90°$, cioè risponde **solo** nel 1° e nel 4° quadrante. Non può fare altro: riceve il **rapporto** $b/a$, e in quel rapporto i due segni meno si annullano.
>
> Esempio concreto: $\bar{V} = -2 + j1$ sta nel **2° quadrante**, in alto a sinistra. La calcolatrice fa $\arctan(1/-2) = \arctan(-0{,}5) = -26{,}6°$ → **4° quadrante**, in basso a destra. È il vettore **opposto**, sbagliato di 180°.
> Aggiungendo $\pi$: $-26{,}6° + 180° = 153{,}4°$ ✅ — ed è esattamente il valore che il libro trova nell'ESEMPIO 1.
>
> **Regola di sopravvivenza: disegna sempre il vettore prima di fidarti della calcolatrice.** Se $a < 0$, aggiungi $180°$. Se $a>0$ e $b<0$, il risultato negativo va bene così (oppure aggiungi $360°$: è lo stesso angolo).

---

## 5. La rappresentazione esponenziale e la formula di Eulero

La **formula di Eulero** (Leonhard Euler, 1748) mette in relazione le funzioni trigonometriche con la funzione esponenziale complessa:

$$e^{j\varphi} = \cos\varphi + j\operatorname{sen}\varphi \tag{2.6}$$

dove $a = \cos\varphi$ e $b = \operatorname{sen}\varphi$ sono la parte reale e la parte immaginaria di $e^{j\varphi}$.

Guarda la FIGURA 5 qui sopra: è tutta la formula in un disegno. Il **cerchio ha raggio 1**; il punto $e^{j\varphi}$ ci sta sopra; la sua proiezione orizzontale è $\cos\varphi$, quella verticale è $\operatorname{sen}\varphi$. Ecco perché $e^{j\varphi}$ significa «vai sul cerchio unitario, all'angolo $\varphi$».

Le formule inverse:

$$\cos\varphi = \frac{e^{j\varphi} + e^{-j\varphi}}{2} \qquad\qquad \operatorname{sen}\varphi = \frac{e^{j\varphi} - e^{-j\varphi}}{2j} \tag{2.7}$$

> [!note] Attenzione al modulo
> La **(2.6)** si riferisce a una grandezza con **ampiezza unitaria**; se il modulo è diverso da uno, il suo valore deve moltiplicare l'esponenziale:
> $$\bar{V} = a + jb = |\bar{V}|\,e^{j\varphi}$$
> Questa riga è il ponte tra le tre rappresentazioni: cartesiana, polare, esponenziale. Sono **tre modi di dire la stessa cosa**, e si sceglie il più comodo per l'operazione da fare.

### Perché l'esponenziale rende banale il prodotto

La rappresentazione esponenziale è particolarmente comoda per i **prodotti**. Il prodotto tra $\bar{Z} = |Z|e^{j\varphi_z}$ e $\bar{I} = |I|e^{j\varphi_i}$ vale:

$$\bar{V} = \bar{Z}\cdot\bar{I} = |Z|\cdot|I|\cdot e^{j\varphi_z}\cdot e^{j\varphi_i} = |Z|\cdot|I|\cdot e^{j(\varphi_z + \varphi_i)}$$

Si moltiplicano i moduli e si **sommano** gli esponenti — perché è la regola delle potenze, $e^x \cdot e^y = e^{x+y}$. Il prodotto tra numeri complessi, che in forma cartesiana richiede quattro moltiplicazioni e una gestione attenta di $j^2 = -1$, in forma esponenziale è **una moltiplicazione e una somma**.

Ed è esattamente la regola **d)** della FIGURA 3: «modulo pari al prodotto dei moduli, fase pari alla somma delle fasi». Il disegno e l'algebra dicono la stessa cosa.

---

## 6. L'esempio svolto del libro

**ESEMPIO 1** (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3). Dato il diagramma vettoriale di FIGURA 6, con $\bar{V}_1$ nel 1° quadrante e $\bar{V}_2$ nel 2°:

**1) Forma complessa.** Si leggono le coordinate dal grafico:
$$\bar{V}_1 = 4 + 2j \qquad \bar{V}_2 = -2 + j$$

**2) Modulo e argomento.**
$$|\bar{V}_1| = \sqrt{4^2 + 2^2} = 4{,}47 \qquad \varphi_1 = \arctan\frac{2}{4} = 0{,}46\ \text{rad} = 27°$$
$$|\bar{V}_2| = \sqrt{(-2)^2 + 1^2} = 2{,}23 \qquad \varphi_2 = \arctan\frac{1}{-2} + \pi = 2{,}68\ \text{rad} = 153°$$

Nota il $+\pi$ su $\varphi_2$: è la (2.3) al lavoro, perché $\bar{V}_2$ ha parte reale negativa.

**3) Somma.** Si sommano parti reali e parti immaginarie:
$$\bar{V} = \bar{V}_1 + \bar{V}_2 = (4 - 2) + j(2 + 1) = 2 + 3j$$

**4) Verifica grafica** con la regola del parallelogramma.

**5) Prodotto.** Modulo = prodotto dei moduli, argomento = somma degli argomenti:
$$|\bar{V}| = 4{,}47 \cdot 2{,}23 = 10{,}0 \qquad \varphi = 0{,}46 + 2{,}68 = 3{,}14\ \text{rad} \simeq \pi = 180°$$
$$\bar{V} = 10\,e^{j\pi} \quad \text{(forma esponenziale)}$$

> [!check] Il risultato è più elegante di quanto sembri
> $10\,e^{j\pi}$ con argomento esattamente $\pi$ vuol dire che il vettore prodotto punta lungo il **semiasse reale negativo**: è il numero reale $-10$.
> Puoi verificarlo in cartesiane: $(4+2j)(-2+j) = -8 + 4j - 4j + 2j^2 = -8 - 2 = -10$ ✅
> Due strade diverse, stesso risultato. Se in un esercizio le due strade non coincidono, hai sbagliato da qualche parte — ed è un ottimo autocontrollo.

---

## 7. Da qui in poi

- Prosegue in: [[Impedenza dei bipoli R, L, C]] — dove i fasori incontrano $R$, $L$ e $C$
- Poi: [[Il metodo simbolico]] · [[Le potenze in alternata]] · [[Reti RLC e risonanza]]
- Applicazione: [[Filtri passivi del primo ordine]] · [[L'oscilloscopio]]
- Esercizi: [[Esercizi - Segnali sinusoidali e fasori]]
