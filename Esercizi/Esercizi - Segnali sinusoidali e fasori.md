---
tags: [recupero, elettronica, corrente-alternata, fasori, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2 (Zanichelli 2012), Cap. 2 «La corrente alternata», pp. 46-51 (pagg.-PDF 1-3). Quesiti ed ESEMPIO 1 controllati sul testo via OCR+lettura pagine (2026-07-19). NB: i valori letti dai diagrammi vettoriali FIGURA 38-39 vanno confrontati sul libro cartaceo. Vedi [[00 - Fonti e note]]."
prove: [scritta, orale, pratica]
---

# Esercizi — Segnali sinusoidali e fasori

Teoria di riferimento: [[Segnali sinusoidali e fasori]]

> [!tip] Come usarli
> I **quesiti** sono domande teoriche: sono il materiale della **prova orale** di Carli. Gli **esercizi** sono numerici: sono il materiale della **prova scritta**. Le soluzioni sono ripiegate — prova prima da solo.

---

# Parte A — Quesiti (prova orale)

*Dal libro, Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3. Il libro pone le domande e basta: le risposte qui sotto le ho ricavate dal testo del capitolo.*

> [!question]- 1 — Perché è importante lo studio dei segnali sinusoidali e dei circuiti in regime sinusoidale?
> Per due motivi, entrambi dal libro (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3):
> 1. **La tensione della rete di distribuzione elettrica ha forma sinusoidale**: è il segnale con cui hai a che fare ogni volta che colleghi qualcosa alla presa.
> 2. **Qualunque forma d'onda può essere scomposta in una somma di sinusoidi** (teorema di Fourier). Questo è il motivo forte: la sinusoide non è un caso particolare, è il **mattone universale**. Se sai come un circuito lineare risponde a una sinusoide di data frequenza, sai come risponde a *qualunque* segnale — scomponendolo, trattando ogni componente e risommando.

> [!question]- 2 — Quali relazioni esistono tra un segnale sinusoidale e i corrispondenti vettore e numero complesso rappresentativo?
> Dato $v(t) = V_p\operatorname{sen}(\omega t + \varphi)$:
> - la **lunghezza del vettore** (modulo $|V|$) è pari al **valore di picco** $V_p$;
> - l'**angolo con l'asse orizzontale a $t = 0$** è la **fase iniziale** $\varphi$ (argomento);
> - l'angolo **tra due vettori** è lo **sfasamento** tra i segnali corrispondenti.
>
> Il numero complesso $\bar{V} = a + jb$ ha come parte reale e immaginaria le **coordinate cartesiane della punta** del vettore nel piano di Gauss. Modulo e argomento ne sono le coordinate **polari**.
>
> **Due avvertenze da aggiungere** (fanno la differenza): il fasore **non contiene la frequenza**, che va comunicata a parte; e la corrispondenza vale **solo tra segnali isofrequenziali**.

> [!question]- 3 — Quali sono le proprietà dell'unità immaginaria $j$?
> Le due che il libro evidenzia (Mirandola, Cap. 2 «La corrente alternata», pp. 46-51 — pagg.-PDF 1-3):
> 1. $j \cdot j = -1$
> 2. **Moltiplicare per $j$ equivale a sfasare di 90° in anticipo** la grandezza sinusoidale corrispondente.
>
> La seconda è quella che conta: poiché $j = e^{j\pi/2}$, moltiplicare per $j$ lascia il modulo invariato e aggiunge $\pi/2$ all'argomento. È il motivo per cui $\bar{Z}_L = j\omega L$: quel $j$ **è** lo sfasamento di 90° tra tensione e corrente nell'induttore.

> [!question]- 4 — Come si effettuano le operazioni tra segnali sinusoidali nelle tre rappresentazioni?
> | Operazione | Vettoriale | Complessa (cartesiana) | Esponenziale |
> |---|---|---|---|
> | $k\cdot\bar{V}$ | modulo per $k$, fase invariata | $k(a+jb)$ | $k\,\|V\|e^{j\varphi}$ |
> | $\bar{V}_1 + \bar{V}_2$ | regola del **parallelogramma** | somma parti reali e immaginarie | scomoda |
> | $\bar{V}_1 - \bar{V}_2$ | somma con verso invertito | differenza parti reali e immaginarie | scomoda |
> | $\bar{V}_1 \cdot \bar{V}_2$ | moduli si moltiplicano, fasi si **sommano** | scomoda | $\|V_1\|\|V_2\|e^{j(\varphi_1+\varphi_2)}$ |
> | $\bar{V}_1 : \bar{V}_2$ | moduli si dividono, fasi si **sottraggono** | scomoda | $\frac{\|V_1\|}{\|V_2\|}e^{j(\varphi_1-\varphi_2)}$ |
>
> **La regola pratica**: somme e differenze → **cartesiana**; prodotti e rapporti → **esponenziale/polare**.

> [!question]- 5 — Come si convertono parte reale e immaginaria in modulo e argomento (e viceversa)?
> **Cartesiane → Polari:**
> $$|\bar{V}| = \sqrt{a^2+b^2} \qquad \varphi = \arctan\frac{b}{a} \;(+\pi \text{ se } a<0;\; +2\pi \text{ se } a>0,\, b<0)$$
> **Polari → Cartesiane:**
> $$a = |\bar{V}|\cos\varphi \qquad b = |\bar{V}|\operatorname{sen}\varphi$$
>
> **Il punto che il prof vuole sentire**: la correzione di quadrante. L'$\arctan$ della calcolatrice risponde solo tra $-90°$ e $+90°$, perché riceve il **rapporto** $b/a$ e non sa distinguere $\frac{1}{-2}$ da $\frac{-1}{2}$. Se $a < 0$ va aggiunto $\pi$, altrimenti ottieni il vettore **opposto**.

---

# Parte B — Esercizi (prova scritta)

## Esercizio 1 — Leggere i fasori dal diagramma

**Testo.** Rilevare dai diagrammi vettoriali di FIGURA 38 l'espressione complessa dei vettori $\bar{V}_1$ e $\bar{V}_2$ e calcolarne modulo e argomento; esprimerli anche in forma esponenziale. *(Vedi ESEMPIO 1)*

![[fig-2-38-vettori-esercizio-1.png]]
*FIGURA 38 — diagramma vettoriale, Mirandola, esercizi di fine Cap. 2*

> [!warning] Verifica i valori sul tuo libro
> I valori qui sotto li ho **letti dal grafico** della scansione, che è a bassa risoluzione. Le posizioni delle punte sono chiare, ma controlla sul libro cartaceo prima di fidarti al 100%.

> [!success]- Soluzione
> **Diagramma A** — la punta di $\bar{V}_1$ cade in $(4, 2)$:
> $$\bar{V}_1 = 4 + j2$$
> $$|\bar{V}_1| = \sqrt{4^2+2^2} = \sqrt{20} = 4{,}47 \qquad \varphi_1 = \arctan\frac{2}{4} = 0{,}46\ \text{rad} = 26{,}6°$$
> ($a > 0$, $b > 0$ → 1° quadrante → nessuna correzione)
> $$\bar{V}_1 = 4{,}47\,e^{j0{,}46}$$
>
> **Diagramma B** — la punta di $\bar{V}_2$ cade in $(2, -3)$:
> $$\bar{V}_2 = 2 - j3$$
> $$|\bar{V}_2| = \sqrt{2^2+(-3)^2} = \sqrt{13} = 3{,}61 \qquad \varphi_2 = \arctan\frac{-3}{2} = -0{,}98\ \text{rad} = -56{,}3°$$
> ($a > 0$, $b < 0$ → **4° quadrante**: il risultato negativo va bene così; volendo si può aggiungere $2\pi$ e scrivere $5{,}30$ rad $= 303{,}7°$, che è lo stesso angolo)
> $$\bar{V}_2 = 3{,}61\,e^{-j0{,}98}$$

> [!check] Il controllo che devi sempre fare
> **Disegna mentalmente il risultato e confrontalo col grafico.** $\bar{V}_1$ deve puntare in alto a destra (1° quadrante, angolo positivo piccolo): ✅ 26,6°. $\bar{V}_2$ deve puntare in basso a destra (4° quadrante, angolo negativo): ✅ $-56{,}3°$.
> Se avessi ottenuto per $\bar{V}_2$ un angolo positivo, sapresti subito di aver sbagliato.

---

## Esercizio 2 — Somma e differenza di fasori

**Testo.** Calcolare e disegnare i vettori somma e differenza dei vettori nei diagrammi di FIGURA 39; calcolare il modulo e l'argomento di tali vettori. *(Vedi ESEMPIO 1)*

![[fig-2-39-vettori-esercizi-2-3.png]]
*FIGURA 39 — diagramma vettoriale, Mirandola, esercizi di fine Cap. 2*

> [!success]- Soluzione
> **Diagramma A** — $\bar{V}_1 = 1 + j2$, $\bar{V}_2 = 3 - j2$
>
> *Somma* (si sommano parti reali e parti immaginarie — formula 2.1):
> $$\bar{V}_1 + \bar{V}_2 = (1+3) + j(2-2) = 4 + j0 = 4$$
> $$|\bar{V}_1+\bar{V}_2| = 4 \qquad \varphi = \arctan\frac{0}{4} = 0\ \text{rad} = 0°$$
> Le parti immaginarie si cancellano: la somma è un numero **reale puro**, un vettore orizzontale lungo 4.
>
> *Differenza*:
> $$\bar{V}_1 - \bar{V}_2 = (1-3) + j(2+2) = -2 + j4$$
> $$|\bar{V}_1-\bar{V}_2| = \sqrt{4+16} = 4{,}47 \qquad \varphi = \arctan\frac{4}{-2} + \pi = -1{,}107 + 3{,}142 = 2{,}03\ \text{rad} = 116{,}6°$$
> **Attenzione**: $a = -2 < 0$ → **va aggiunto $\pi$** (2° quadrante). Senza correzione la calcolatrice darebbe $-63{,}4°$, cioè il vettore opposto.
>
> **Diagramma B** — $\bar{V}_1 = -2 + j3$, $\bar{V}_2 = 3 - j1$
>
> *Somma*:
> $$\bar{V}_1 + \bar{V}_2 = (-2+3) + j(3-1) = 1 + j2$$
> $$|\cdot| = \sqrt{1+4} = 2{,}24 \qquad \varphi = \arctan\frac{2}{1} = 1{,}107\ \text{rad} = 63{,}4°$$
>
> *Differenza*:
> $$\bar{V}_1 - \bar{V}_2 = (-2-3) + j(3+1) = -5 + j4$$
> $$|\cdot| = \sqrt{25+16} = 6{,}40 \qquad \varphi = \arctan\frac{4}{-5} + \pi = -0{,}675 + 3{,}142 = 2{,}47\ \text{rad} = 141{,}3°$$
> Anche qui $a < 0$ → correzione di quadrante.
>
> **Il disegno**: la somma si costruisce con la **regola del parallelogramma**; la differenza si ottiene sommando $\bar{V}_1$ a $-\bar{V}_2$ (cioè $\bar{V}_2$ girato di 180°), oppure — più veloce — tracciando il vettore che va **dalla punta di $\bar{V}_2$ alla punta di $\bar{V}_1$**.

> [!tip] Due cose che questo esercizio insegna
> **1.** In due casi su quattro serve la correzione di quadrante. Non è un caso raro: **è la norma**.
> **2.** Nel diagramma A la somma dà un vettore puramente reale, perché le due parti immaginarie ($+2$ e $-2$) si annullano. Tradotto in segnali: le due sinusoidi hanno componenti in quadratura opposte che si cancellano. È lo stesso meccanismo della **risonanza** (vedi [[Reti RLC e risonanza]]) e del **rifasamento** (vedi [[Le potenze in alternata]]).

---

## Esercizio 3 — Prodotto e rapporto di fasori

**Testo.** Calcolare e disegnare i vettori prodotto e rapporto dei vettori nei diagrammi di FIGURA 39. *(Vedi ESEMPIO 2)*

> [!success]- Soluzione
> Qui conviene passare in **forma polare**: prodotto e rapporto sono immediati (moduli che si moltiplicano o dividono, fasi che si sommano o sottraggono), mentre in cartesiana sarebbero laboriosi.
>
> **Diagramma A** — $\bar{V}_1 = 1 + j2$, $\bar{V}_2 = 3 - j2$
>
> Prima le forme polari:
> $$|\bar{V}_1| = \sqrt{1+4} = 2{,}24 \qquad \varphi_1 = \arctan\frac{2}{1} = 1{,}107\ \text{rad} = 63{,}4°$$
> $$|\bar{V}_2| = \sqrt{9+4} = 3{,}61 \qquad \varphi_2 = \arctan\frac{-2}{3} = -0{,}588\ \text{rad} = -33{,}7°$$
>
> *Prodotto* — moduli si moltiplicano, fasi si **sommano**:
> $$|\bar{V}_1\cdot\bar{V}_2| = 2{,}24 \cdot 3{,}61 = 8{,}09 \qquad \varphi = 1{,}107 - 0{,}588 = 0{,}519\ \text{rad} = 29{,}7°$$
> $$\bar{V}_1\cdot\bar{V}_2 = 8{,}09\,e^{j0{,}519}$$
>
> *Rapporto* — moduli si dividono, fasi si **sottraggono**:
> $$\left|\frac{\bar{V}_1}{\bar{V}_2}\right| = \frac{2{,}24}{3{,}61} = 0{,}62 \qquad \varphi = 1{,}107 - (-0{,}588) = 1{,}695\ \text{rad} = 97{,}1°$$
> $$\frac{\bar{V}_1}{\bar{V}_2} = 0{,}62\,e^{j1{,}695}$$
>
> **Diagramma B** — $\bar{V}_1 = -2 + j3$, $\bar{V}_2 = 3 - j1$
> $$|\bar{V}_1| = \sqrt{4+9} = 3{,}61 \qquad \varphi_1 = \arctan\frac{3}{-2} + \pi = 2{,}16\ \text{rad} = 123{,}7°$$
> $$|\bar{V}_2| = \sqrt{9+1} = 3{,}16 \qquad \varphi_2 = \arctan\frac{-1}{3} = -0{,}322\ \text{rad} = -18{,}4°$$
>
> *Prodotto*: $\;|\cdot| = 3{,}61\cdot3{,}16 = 11{,}4$, $\;\varphi = 2{,}16 - 0{,}322 = 1{,}84$ rad $= 105{,}3°$
> *Rapporto*: $\;|\cdot| = \frac{3{,}61}{3{,}16} = 1{,}14$, $\;\varphi = 2{,}16 + 0{,}322 = 2{,}48$ rad $= 142{,}1°$

> [!check] Verifica il prodotto in cartesiana
> Vale la pena farlo almeno una volta, per convincerti che le due strade coincidono. Diagramma A:
> $$(1+j2)(3-j2) = 3 - j2 + j6 - j^2 4 = 3 + 4 + j4 = 7 + j4$$
> $$|7+j4| = \sqrt{49+16} = 8{,}06 \qquad \varphi = \arctan\frac{4}{7} = 0{,}519\ \text{rad} = 29{,}7°$$
> Confronta con la via polare: $8{,}09$ e $0{,}519$ rad ✅ — la differenza sul modulo è solo arrotondamento.
>
> Nota quanto è più laboriosa la strada cartesiana, e questo con numeri semplici. **Per prodotti e rapporti, la forma polare vince sempre.**

---

## Esercizi svolti da Edutecnica.it (catalogo alternatax completi)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettrotecnica/alternatax/alternatax.htm](https://www.edutecnica.it/elettrotecnica/alternatax/alternatax.htm). Esercizi numerici su AC: fasori, conversioni, bipoli RLC.

### Es. SF1 — Conversione forma binomiale → trigonometrica

- **Testo**: $\bar{V} = 3 + j4$ V. Convertire in $V_p \angle \varphi$.
- **Svolgimento**: $|V| = \sqrt{9+16} = 5$ V, $\varphi = \arctan(4/3) = 53{,}13°$. Quindi $\bar{V} = 5\angle 53{,}13°$ V.

### Es. SF2 — Conversione trigonometrica → binomiale

- **Testo**: $v(t) = 10\sin(2\pi \cdot 1\text{kHz} \cdot t + 30°)$ V. Scrivere in forma fasoriale.
- **Svolgimento**: $\bar{V} = 10/\sqrt{2} \angle 30° = 7{,}07\angle 30°$ V. In binomiale: $7{,}07(\cos 30° + j\sin 30°) = 6{,}12 + j3{,}54$ V.

### Es. SF3 — Dato $Z$ e $V$, trovare $I$ e sfasamento

- **Dati**: $\bar{Z} = 100 + j50\,\Omega$, $\bar{V} = 220\angle 0°$ V.
- **Procedura**: $\bar{I} = \bar{V}/\bar{Z} = 220/(100+j50) = 220/(111{,}8\angle 26{,}57°) = 1{,}97\angle -26{,}57°$ A.
- **Significato**: $i(t) = 1{,}97\sqrt{2} \sin(\omega t - 26{,}57°)$ A. La corrente è in ritardo di 26,57° rispetto alla tensione (carico induttivo).

### Es. SF4 — Dato $R$ serie $C$, $I$ noto, calcolare cadute

- **Dati**: $R = 3\,\text{k}\Omega$, $C = 100$ pF, serie, $I = 5$ mA, $\omega = 2{,}5$ Mrad/s.
- **Procedura**: $\bar{Z} = R + 1/(j\omega C) = 3000 + 1/(j \cdot 2{,}5\text{M} \cdot 100\text{pF}) = 3000 - j4000\,\Omega$. $|Z| = 5000\,\Omega$, $\varphi = \arctan(-4/3) = -53{,}13°$. $\bar{V} = \bar{I} \cdot \bar{Z} = 5\text{mA} \cdot 5\text{k}\angle -53{,}13° = 25\angle -53{,}13°$ V.

### Es. SF5 — Circuito misto RRC/RRL con generatore

- **Dati**: $E$, $R_1$, $R_2$, $R_3$, $C$ (variabile). Trovare $V_0$ e $I_C$.
- **Soluzione**: tipico esercizio di applicazione del metodo simbolico + Thévenin/Norton.

### Es. SF6 — Corrente con sfasamento noto

- **Dati**: $I_1$ anticipo 64°, $V_C$ noto, $R_1$, $R_2$. Trovare correnti di ramo.
- **Procedura**: scrivere i fasori con i corretti angoli, applicare Kirchhoff al nodo.

### Es. SF7-SF12 — Circuiti sempre più complessi (fino a 12 esercizi sul sito)

L'ultima parte del catalogo edutecnica alternatax include esercizi con:
- 2 segnali sinusoidali sovrapposti (somma fasoriale)
- Generatori con sfasamenti diversi
- Circuiti a T e a Π
- Effetto di sorgente con impedenza interna

## Pattern di errore frequenti (Carli scritta)

1. **arctan e quadrante**: $\arctan$ restituisce valori in $(-90°, +90°)$. Se il punto è nel 2° o 3° quadrante, correggere a mano: es. $(x,y) = (-1, +1)$ → $\arctan(-1) = -45°$, ma l'angolo corretto è $135°$.
2. **Conversione $V_{\text{eff}}/V_p$**: $V_{\text{eff}} = V_p/\sqrt{2}$. Errore opposto.
3. **Sfasamento di $\pi$**: $180°$ spesso si sottintende. Es. "anticipo di $\pi$" e "ritardo di $\pi$" sono la stessa cosa per i fasori.
