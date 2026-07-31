---
tags: [recupero, elettronica, corrente-alternata, impedenza, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2 (Zanichelli 2012), Cap. 2 «La corrente alternata». Quesiti 6-14 ed esercizi 4-6 di fine capitolo (FIGURE 40-42) controllati sul testo e sulle immagini via OCR+lettura pagine (2026-07-19): valori dei componenti e risposte del libro (I₂=23,3 mA, V₂=7,67 V; |Z|=1880 Ω/823 Ω; |Z|=815 Ω) confermati. Vedi [[00 - Fonti e note]]."
prove: [scritta, orale, pratica]
---

# Esercizi — Impedenza dei bipoli R, L, C

Teoria di riferimento: [[Impedenza dei bipoli R, L, C]]

---

# Parte A — Quesiti (prova orale)

> [!question]- 6 — Quali sono le relazioni tra le tensioni applicate e le correnti che scorrono nei bipoli lineari elementari?
> | Componente | Nel tempo | In campo complesso | Sfasamento |
> |---|---|---|---|
> | **R** | $v = Ri$ | $\bar{V} = R\bar{I}$ (2.12) | nessuno: in fase |
> | **L** | $v = L\frac{di}{dt}$ (2.8) | $\bar{V} = j\omega L\bar{I}$ (2.9) | **tensione in anticipo di 90°** |
> | **C** | $i = C\frac{dv}{dt}$ (2.10) | $\bar{I} = j\omega C\bar{V}$ (2.11) | **corrente in anticipo di 90°** |
>
> Il punto da sottolineare: nel tempo sono relazioni **integro-differenziali**; in campo complesso diventano **algebriche**. È tutto il senso del metodo simbolico.

> [!question]- 7 — Com'è definita l'impedenza di un bipolo?
> È il **numero complesso ottenuto come rapporto tra i numeri complessi rappresentativi della tensione e della corrente** sul bipolo alimentato in alternata:
> $$\bar{Z} = \frac{\bar{V}}{\bar{I}} \tag{2.13}$$
> Essendo un rapporto tra complessi, porta **due** informazioni: il **modulo** è il rapporto tra i moduli (quanto il bipolo si oppone) e l'**argomento** è lo **sfasamento** tra tensione e corrente (come il bipolo sfasa).

> [!question]- 8 — Scrivere le espressioni delle impedenze dei bipoli passivi elementari.
> $$\bar{Z}_R = R \qquad \bar{Z}_L = j\omega L \qquad \bar{Z}_C = \frac{1}{j\omega C} = -\frac{j}{\omega C}$$

> [!question]- 9 — In che cosa differisce l'impedenza di un componente reattivo da quella di un resistore?
> Due differenze:
> 1. **Dipende dalla frequenza.** $\bar{Z}_R = R$ è costante; $\bar{Z}_L$ e $\bar{Z}_C$ cambiano con $\omega$.
> 2. **È immaginaria pura, non reale.** Quindi introduce uno **sfasamento di 90°**, mentre il resistore non sfasa.
>
> Alla radice c'è la fisica: il resistore **dissipa** energia (e ciò che dissipa è la parte reale), i reattivi la **immagazzinano e restituiscono** (e ciò che palleggia è la parte immaginaria). Vedi [[Le potenze in alternata]].

> [!question]- 10 — In che cosa differisce la reattanza di un condensatore da quella di un induttore?
> $$X_L = \omega L \;\; (\text{positiva, cresce con } \omega) \qquad X_C = -\frac{1}{\omega C} \;\; (\text{negativa, decresce con } \omega)$$
> Sono **opposte in tutto**: nel segno e nell'andamento con la frequenza. È il motivo per cui possono annullarsi a vicenda ([[Reti RLC e risonanza]]) e per cui, scambiandoli di posto, un passa basso diventa un passa alto ([[Filtri passivi del primo ordine]]).

> [!question]- 11 — Qual è il significato del modulo dell'impedenza di un bipolo?
> È il **rapporto tra il modulo della tensione e il modulo della corrente**: $|\bar{Z}| = \frac{|V|}{|I|}$. È la generalizzazione della resistenza: dice **quanto** il bipolo si oppone al passaggio della corrente, indipendentemente dallo sfasamento, che è invece nell'argomento.

> [!question]- 12 — Come si calcola l'impedenza equivalente di più bipoli connessi in serie o in parallelo?
> Con formule **formalmente identiche** a quelle dei resistori:
> $$\bar{Z}_{eq} = \bar{Z}_1 + \bar{Z}_2 + \bar{Z}_3 \tag{2.18} \qquad \frac{1}{\bar{Z}_{eq}} = \frac{1}{\bar{Z}_1} + \frac{1}{\bar{Z}_2} + \frac{1}{\bar{Z}_3} \tag{2.19}$$
> L'unica differenza è che i conti si fanno con i **numeri complessi**.

> [!question]- 14 — Quali sono i circuiti equivalenti dei condensatori e degli induttori reali? Con quali parametri viene valutata la loro purezza?
> Vedi il §7 di [[Impedenza dei bipoli R, L, C]].
> - **Condensatore reale** (FIGURA 15B): $R'$ e $L$ sono resistenza e induttanza di reofori e armature, $R''$ le perdite nel dielettrico. Purezza: **fattore di perdita** $\operatorname{tg}\delta = \omega C R_s = \frac{1}{\omega C R_P}$ — più è **piccolo**, più è puro.
> - **Induttore reale** (FIGURA 16B): $R$ sono le perdite ohmiche, magnetiche e dielettriche, $C$ la capacità distribuita tra le spire. Purezza: **fattore di merito** $Q = \frac{\omega L}{R_s} = \frac{R_P}{\omega L}$ — più è **grande**, più è puro.
>
> Entrambi hanno una **frequenza di risonanza propria** $f_r = \frac{1}{2\pi\sqrt{LC}}$, dovuta ai parassiti: si usano ben al di sotto di essa.

---

# Parte B — Esercizi (prova scritta)

## Esercizio 4 — Regime continuo: il trucco della TABELLA 1

**Testo.** Calcolare il valore della tensione $V_o$ e della corrente $I_2$ nella rete di FIGURA 40, una volta raggiunto lo stato di **regime permanente continuo**.
*Suggerimento del libro: ricordare il comportamento di $C$ e $L$ in continua a regime.*
**Risposte del libro:** $I_2 = 23{,}3$ mA; $V_o = 7{,}67$ V

![[fig-2-40-rete-esercizio-4.png]]
*FIGURA 40 — $E = 10$ V, $L_1 = 0{,}1$ mH, $R_1 = 100\ \Omega$, $C_1 = 2{,}2\ \mu$F, $R_2 = 330\ \Omega$, $R_3 = 560\ \Omega$, $L_2 = 0{,}4$ mH, $C_2 = 1\ \mu$F (Mirandola, Cap. 2, esercizio 4; valori letti dalla FIGURA 40 del libro).*

> [!success]- Soluzione
> Il suggerimento è tutto l'esercizio. **In continua a regime** ($\omega = 0$), dalla TABELLA 1:
> - ogni **induttanza** diventa un **cortocircuito** → $L_1$ e $L_2$ sono pezzi di filo;
> - ogni **condensatore** diventa un **circuito aperto** → $C_1$ e $C_2$ spariscono.
>
> Cancellando i componenti reattivi, di quella rete apparentemente complicata resta:
> $$E \;-\; R_1 \;-\; R_2 \;-\; \text{massa}$$
> un banale partitore di tensione. Il ramo con $R_3$ è **interrotto da $C_2$** (aperto), quindi non porta corrente e non conta.
>
> **Tensione d'uscita** (partitore):
> $$V_o = E\,\frac{R_2}{R_1 + R_2} = 10\cdot\frac{330}{100+330} = 10\cdot 0{,}767 = 7{,}67\ \text{V} \;✅$$
>
> **Corrente**: essendo $L_2$ un corto, $I_2$ è la corrente che attraversa $R_2$, cioè quella di tutta la maglia:
> $$I_2 = \frac{E}{R_1+R_2} = \frac{10}{430} = 23{,}3\ \text{mA} \;✅$$
>
> Verifica incrociata: $I_2 \cdot R_2 = 0{,}0233 \cdot 330 = 7{,}69$ V $\simeq V_o$ ✅

> [!tip] Perché questo esercizio è nel capitolo sull'alternata
> Sembra fuori posto — è un esercizio in continua. Ma è messo lì apposta: ti costringe a usare **i valori limite della TABELLA 1**, che sono la cosa più preziosa del paragrafo.
> È anche il caso $\omega \to 0$ della tabella: se sai risolvere questo, sai anche cosa succede al circuito a **frequenza infinita** — basta invertire tutto ($L$ aperte, $C$ cortocircuitate). Sono i due estremi tra cui vive tutto il resto.

---

## Esercizio 5 — Impedenza equivalente di due bipoli

**Testo.** Calcolare il modulo e l'argomento dell'impedenza equivalente dei bipoli di FIGURA 41 alla frequenza $f = 10$ kHz. *(Vedi ESEMPIO 2)*
**Risposte del libro:** a) $|Z_{eq}| = 1880\ \Omega$, $\angle Z_{eq} = -57{,}6°$; b) $|Z_{eq}| = 823\ \Omega$, $\angle Z_{eq} = +66{,}4°$

![[fig-2-41-bipoli-esercizio-5.png]]
*FIGURA 41 — **A)** $C = 10$ nF in serie a $R = 1$ k$\Omega$; **B)** $R = 330\ \Omega$ in serie a $L = 12$ mH (Mirandola, Cap. 2, esercizio 5; valori letti dalla FIGURA 41 del libro).*

> [!success]- Soluzione
> $$\omega = 2\pi f = 2\pi\cdot 10^4 = 62{.}832\ \text{rad/s}$$
>
> **Bipolo A** — serie $R$–$C$:
> $$X_C = -\frac{1}{\omega C} = -\frac{1}{62832\cdot 10\cdot10^{-9}} = -1591{,}5\ \Omega$$
> $$\bar{Z}_A = R + jX_C = 1000 - j\,1591{,}5$$
> $$|\bar{Z}_A| = \sqrt{1000^2 + 1591{,}5^2} = \sqrt{3{,}533\cdot10^6} = 1880\ \Omega \;✅$$
> $$\angle\bar{Z}_A = \arctan\frac{-1591{,}5}{1000} = -57{,}9° \;✅ \;\text{(il libro arrotonda a } -57{,}6°)$$
> Argomento **negativo** → bipolo **capacitivo** → tensione in ritardo sulla corrente.
>
> **Bipolo B** — serie $R$–$L$:
> $$X_L = \omega L = 62832 \cdot 12\cdot10^{-3} = 754{,}0\ \Omega$$
> $$\bar{Z}_B = R + jX_L = 330 + j\,754$$
> $$|\bar{Z}_B| = \sqrt{330^2 + 754^2} = \sqrt{677{.}416} = 823{,}0\ \Omega \;✅$$
> $$\angle\bar{Z}_B = \arctan\frac{754}{330} = +66{,}4° \;✅$$
> Argomento **positivo** → bipolo **induttivo** → tensione in anticipo sulla corrente.

> [!check] I due bipoli sono l'immagine speculare l'uno dell'altro
> Guarda i segni degli argomenti: $-57{,}9°$ e $+66{,}4°$. Non serve calcolarli per sapere il segno — basta guardare **quale reattivo c'è**: condensatore → negativo, induttanza → positivo. È il §4 della teoria.
> **Sono entrambi serie semplici**: qui non serve il coniugato, perché non c'è nessun parallelo. Si sommano le impedenze e basta. Il coniugato serve solo quando hai $j$ **al denominatore**.

---

## Esercizio 6 — Impedenza con un parallelo

**Testo.** Calcolare il modulo e l'argomento dell'impedenza equivalente del bipolo di FIGURA 42 alla frequenza $f = 10$ kHz. *(Vedi ESEMPIO 2)*
**Risposte del libro:** $|Z_{eq}| = 815\ \Omega$; $\angle Z_{eq} = -28{,}5°$

![[fig-2-42-bipolo-esercizio-6.png]]
*FIGURA 42 — $L = 1$ mH in serie al parallelo tra $C = 10$ nF e $R = 1$ k$\Omega$ (Mirandola, Cap. 2, esercizio 6; valori letti dalla FIGURA 42 del libro).*

> [!success]- Soluzione
> $$\omega = 62{.}832\ \text{rad/s} \qquad X_L = \omega L = 62{,}83\ \Omega \qquad \bar{Z}_C = -j\,1591{,}5\ \Omega$$
>
> **Passo 1 — il parallelo $R$–$C$** (qui serve il coniugato):
> $$\bar{Z}_P = \frac{R\cdot \bar{Z}_C}{R + \bar{Z}_C} = \frac{1000\cdot(-j1591{,}5)}{1000 - j1591{,}5}$$
> Moltiplicando numeratore e denominatore per il coniugato $(1000 + j1591{,}5)$:
> $$\bar{Z}_P = \frac{-j\,1{,}5915\cdot10^{6}\,(1000 + j1591{,}5)}{1000^2 + 1591{,}5^2} = \frac{2{,}533\cdot10^{9} - j\,1{,}5915\cdot10^{9}}{3{,}533\cdot10^{6}} = 716{,}9 - j\,450{,}5$$
>
> **Passo 2 — aggiungere $L$ in serie**:
> $$\bar{Z}_{eq} = jX_L + \bar{Z}_P = j\,62{,}83 + 716{,}9 - j\,450{,}5 = 716{,}9 - j\,387{,}7$$
>
> **Passo 3 — modulo e argomento**:
> $$|\bar{Z}_{eq}| = \sqrt{716{,}9^2 + 387{,}7^2} = \sqrt{664{.}200} = 815{,}0\ \Omega \;✅$$
> $$\angle\bar{Z}_{eq} = \arctan\frac{-387{,}7}{716{,}9} = -28{,}4° \;✅$$

> [!check] Due controlli che puoi fare a mente
> **1. Il segno.** L'induttanza contribuisce $+62{,}8$, il parallelo $RC$ contribuisce $-450{,}5$. Vince il condensatore, quindi la reattanza totale è **negativa** e il bipolo è **capacitivo**: argomento negativo ✅.
> **2. L'ordine di grandezza.** $X_L = 62{,}8\ \Omega$ è **piccolissima** rispetto a tutto il resto: a 10 kHz quell'induttanza da 1 mH è quasi un pezzo di filo. Se la togliessi otterresti $|Z| = \sqrt{716{,}9^2 + 450{,}5^2} = 846\ \Omega$ invece di 815: uno scarto del 4%. Utile per stimare il risultato prima di calcolarlo.

---

## Esercizi svolti da Edutecnica.it (impedenze e bipoli)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettrotecnica/alternatax/alternatax.htm](https://www.edutecnica.it/elettrotecnica/alternatax/alternatax.htm). Parte 7-12: calcolo impedenze equivalenti di reti RLC.

### Es. I1 — Impedenza equivalente serie R + C

- **Dati**: $R = 100\,\Omega$, $C = 10\,\mu\text{F}$, $f = 1$ kHz.
- **Procedura**: $X_C = 1/(2\pi f C) = 1/(2\pi \cdot 1000 \cdot 10\,\mu\text{F}) = 15{,}92\,\Omega$.
- $\bar{Z}_{RC,\text{serie}} = R - j X_C = 100 - j15{,}92\,\Omega$.
- $|Z| = \sqrt{100^2 + 15{,}92^2} = 101{,}26\,\Omega$, $\varphi = -9{,}05°$.

### Es. I2 — Impedenza equivalente parallelo R || C

- **Dati**: $R = 1\,\text{k}\Omega$, $C = 100$ nF, $f = 10$ kHz.
- **Procedura**: in parallelo si sommano le ammettenze: $\bar{Y} = 1/R + j\omega C = 10^{-3} + j 2\pi f C$.
- $\omega C = 2\pi \cdot 10000 \cdot 100\text{nF} = 6{,}283 \cdot 10^{-3}$ S. $\bar{Y} = (1 + j6{,}283) \cdot 10^{-3}$ S.
- $\bar{Z} = 1/\bar{Y} = 1000/(1 + j6{,}283) = 159{,}15 \angle -80{,}96°\,\Omega$.

### Es. I3 — Impedenza equivalente parallelo R || L

- **Dati**: $R = 100\,\Omega$, $L = 10$ mH, $f = 1$ kHz.
- **Procedura**: $\bar{Y} = 1/R + 1/(j\omega L) = 0{,}01 - j/(2\pi \cdot 1000 \cdot 0{,}01) = 0{,}01 - j 0{,}0159$ S.
- $\bar{Z} = 1/\bar{Y} = 1/(0{,}0182 \angle -57{,}86°) = 54{,}93 \angle 57{,}86°\,\Omega$.

### Es. I4 — Conversione serie ↔ parallelo (tramite fattore $Q$)

- **Dati**: $R_s = 10\,\Omega$, $L_s = 1$ mH, $f = 10$ kHz.
- **Trovare**: $R_p$, $L_p$ equivalenti parallelo.
- **Procedura**: $Q = \omega L_s/R_s = 2\pi \cdot 10000 \cdot 1\text{mH}/10 = 6{,}28$.
  - $R_p = R_s(1+Q^2) = 10(1+39{,}5) = 405\,\Omega$.
  - $L_p = L_s(1+1/Q^2) = 1\text{mH}(1+0{,}025) = 1{,}025$ mH.

### Pattern di errore frequenti (Carli scritta)

1. **Confondere serie con parallelo**: in serie gli elementi si sommano come impedenze (numeri complessi); in parallelo si sommano le ammettenze (numeri complessi). Errore opposto molto comune.
2. **Reattanza $X_C$ vs $Z_C$**: $Z_C = -jX_C = -j/(\omega C)$. Errore: $Z_C = 1/(\omega C)$.
3. **Segno di $X_L$ vs $X_C$**: $X_L = +\omega L$, $X_C = -1/(\omega C)$. Errore: stesso segno.
