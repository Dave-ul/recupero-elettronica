---
tags: [recupero, elettronica, corrente-alternata, metodo-simbolico, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2, Cap. 2, §3 «Il metodo simbolico», pp. 60-61. Quesiti 15-18 dal riepilogo di p. 80 (pag.-PDF 18); esercizi 9-10 (FIG. 45-46) da p. 82 (pag.-PDF 19), risposte stampate lette dall'immagine a 220 dpi."
prove: [scritta, orale]
---

# Esercizi — Il metodo simbolico

Teoria di riferimento: [[Il metodo simbolico]]

---

# Parte A — Quesiti (prova orale)

> [!question]- 15 — Come si effettua l'analisi a regime delle reti in continua contenenti condensatori e induttori?
> Si sfruttano i **valori limite per $\omega \to 0$** della TABELLA 1:
> - ogni **induttore** diventa un **cortocircuito** ($\bar{Z}_L = j\omega L \to 0$);
> - ogni **condensatore** diventa un **circuito aperto** ($\bar{Z}_C = -j/\omega C \to \infty$).
>
> Quello che resta è una **rete puramente resistiva**, che si risolve con Ohm e Kirchhoff.
> Attenzione al «**a regime**»: vale solo dopo che il transitorio si è esaurito. Durante il transitorio i reattivi stanno caricandosi e la semplificazione non vale.
> È esattamente l'esercizio 4 di [[Esercizi - Impedenza dei bipoli R, L, C]].

> [!question]- 16 — Quali vantaggi consentono di ottenere i metodi di trasformazione?
> Trasformano le **relazioni integro-differenziali** tra le grandezze elettriche in **equazioni algebriche**, di più agevole soluzione.
> In generale, una *trasformazione* è «un'operazione che, attraverso l'opportuna modifica delle variabili, consente di trasformare operazioni complesse in altre più semplici» (Mirandola, **apertura del Cap. 2, p. 46**).
> *Chicca da orale*: il libro, nella stessa pagina, chiama il metodo simbolico anche **trasformata di Steinmetz**, e lo inquadra come *un* metodo di trasformazione accanto a quello **più generale** di Laplace.
> Il guadagno concreto: invece di risolvere un **sistema di equazioni differenziali**, risolvi un **sistema di equazioni di primo grado** — solo con i numeri complessi al posto dei reali.

> [!question]- 17 — In quali casi si utilizza il metodo simbolico?
> Solo quando valgono **due condizioni**:
> 1. la rete è in **regime permanente sinusoidale** (transitorio esaurito);
> 2. le eccitazioni sono **isofrequenziali**, se più di una.
>
> Fuori da queste condizioni serve la **trasformata di Laplace** (Cap. 3 del libro), che gestisce anche i transitori e i segnali di forma qualunque.
> *Se il prof chiede il caso di generatori a frequenze diverse*: si applica la **sovrapposizione degli effetti**, risolvendo una frequenza alla volta e sommando i risultati **nel dominio del tempo** — non i fasori, che non sarebbero sommabili.

> [!question]- 18 — Come si analizzano i circuiti con il metodo simbolico?
> Il riquadro **PROCEDIMENTO** del libro (Cap. 2 §3, **p. 61**), in tre passi:
> 1. Si associano alle tensioni e correnti di eccitazione i corrispondenti **numeri complessi** (o fasori) rappresentativi.
> 2. Si risolve la rete usando **gli stessi principi e teoremi del regime continuo**: nei bipoli lineari vale $\bar{V} = \bar{Z}\cdot\bar{I}$, e le operazioni si eseguono sui numeri complessi o graficamente sui vettori.
> 3. Ogni grandezza risulta **sinusoidale**, con la **stessa frequenza** dei generatori (per la linearità), e ampiezza e fase si ricavano da modulo e argomento trovati.

---

# Parte B — Esercizi (prova scritta)

> [!warning] Su questi due esercizi il segno dell'argomento è invertito rispetto al libro
> **Le risposte del libro sono state verificate sull'immagine della pagina** (p. 82, pag.-PDF 19), non dedotte: il libro stampa davvero `[|Vc| = 0,40 Veff; ∠Vc = 0,91 rad]` per il 9 e `[|Vc| = 0,64 Veff; ∠Vc = −1,2 rad]` per il 10 (**p. 82**).
> In entrambi il **modulo coincide** col mio; l'**argomento ha il segno opposto**. Ricontrollate topologia e fisica: il segno che ottengo è quello coerente col circuito. Leggi i riquadri — più che il numero, ti serve **saper decidere il segno guardando lo schema**, ed è quello che ti salva all'esame.

## Esercizio 9 — Tensione su un parallelo RC

**Testo.** Disegnare il diagramma vettoriale delle tensioni $V_C$ e $V_g$ nel circuito di FIGURA 45, supponendo $V_g$ con frequenza $f = 9{,}2$ kHz, modulo $|V_g| = 0{,}8$ V$_{eff}$ e fase iniziale nulla. Calcolare, inoltre, il modulo e l'argomento della tensione $V_C$. *(Vedi ESEMPIO 5)*
**Risposte del libro:** $|V_C| = 0{,}40$ V$_{eff}$; $\angle V_C = 0{,}91$ rad

![[fig-2-45-esercizio-9.png]]
*FIGURA 45 — $R_1 = 1{,}8$ k$\Omega$ in serie al parallelo tra $R_2 = 9$ k$\Omega$ e $C = 15$ nF; l'uscita $V_C$ è presa sul condensatore. Valori letti sull'immagine della figura, Mirandola p. 82.*

> [!success]- Soluzione
> **Passo 1 — entrare nel complesso:**
> $$\omega = 2\pi f = 2\pi\cdot 9200 = 57{.}805\ \text{rad/s} \qquad \bar{V}_g = 0{,}8 \;(\text{fase nulla})$$
> $$\bar{Z}_C = -\frac{j}{\omega C} = -\frac{j}{57805 \cdot 15\cdot10^{-9}} = -j\,1153{,}3\ \Omega$$
>
> **Passo 2 — il parallelo $R_2$–$C$** (coniugato):
> $$\bar{Z}_P = \frac{R_2\cdot\bar{Z}_C}{R_2 + \bar{Z}_C} = \frac{9000\cdot(-j1153{,}3)}{9000 - j1153{,}3} = 145{,}4 - j\,1134{,}7\ \Omega$$
>
> **Passo 3 — il partitore:**
> $$\bar{V}_C = \bar{V}_g\,\frac{\bar{Z}_P}{R_1 + \bar{Z}_P} = 0{,}8\cdot\frac{145{,}4 - j1134{,}7}{1945{,}4 - j1134{,}7}$$
>
> Lavorando in **polare** (rapporto → moduli si dividono, fasi si sottraggono):
> $$|\text{num}| = \sqrt{145{,}4^2 + 1134{,}7^2} = 1144{,}0 \qquad \angle\text{num} = \arctan\frac{-1134{,}7}{145{,}4} = -82{,}7°$$
> $$|\text{den}| = \sqrt{1945{,}4^2 + 1134{,}7^2} = 2252{,}1 \qquad \angle\text{den} = \arctan\frac{-1134{,}7}{1945{,}4} = -30{,}3°$$
>
> $$|\bar{V}_C| = 0{,}8\cdot\frac{1144{,}0}{2252{,}1} = 0{,}8 \cdot 0{,}508 = \mathbf{0{,}41\ V_{eff}} \;✅ \;(\text{il libro: } 0{,}40)$$
> $$\angle\bar{V}_C = -82{,}7° - (-30{,}3°) = -52{,}4° = \mathbf{-0{,}91\ rad}$$

> [!danger] Il segno dell'argomento
> Il libro riporta $\angle V_C = 0{,}91$ rad, **positivo**. Io ottengo lo stesso valore ma **negativo**: $-0{,}91$ rad.
>
> **Il segno negativo è l'unico compatibile col circuito**, e lo puoi stabilire senza calcoli: l'uscita è presa **sul condensatore**, quindi è una configurazione **passa basso** — e in un passa basso la tensione d'uscita è sempre **in ritardo** su quella d'ingresso. Guarda i diagrammi di Bode-fase nella TABELLA 6 di [[Filtri passivi del primo ordine]]: la fase va da $0°$ a $-90°$, non sale mai sopra lo zero.
> Conferma dal calcolo: $\bar{Z}_P$ ha parte immaginaria **negativa** ($-1134{,}7$), cioè è capacitiva. Non può produrre un anticipo.
>
> Anche il valore $-52{,}4°$ è plausibile: sta tra $0°$ e $-90°$, più vicino a $-90°$ perché siamo oltre la frequenza di taglio.

---

## Esercizio 10 — Tensione su una serie RC

**Testo.** Disegnare il diagramma vettoriale delle tensioni $V_{R2}$ e $V_g$ nel circuito di FIGURA 46, supponendo $V_g$ con frequenza $f = 1{,}2$ kHz, modulo $|V_g| = 2{,}5$ V$_{eff}$ e fase iniziale nulla. Calcolare, inoltre, il modulo e l'argomento della tensione $V_{R2}$. *(Vedi ESEMPIO 5)*
**Risposte del libro:** $|V_c| = 0{,}64$ V$_{eff}$; $\angle V_c = -1{,}2$ rad

> [!bug] Attenzione: nella chiave del libro l'etichetta è sbagliata
> L'esercizio chiede $V_{R2}$, ma la risposta stampata è etichettata **$V_c$** (copiata dall'esercizio 9). Non è un dubbio interpretativo: il **valore** 0,64 V è inequivocabilmente $V_{R2}$ — la tensione sul condensatore in questo circuito vale $2{,}34$ V, non 0,64. È solo l'etichetta a essere errata.

![[fig-2-46-esercizio-10.png]]
*FIGURA 46 — $R_1 = 330\ \Omega$ e $C = 40$ nF in serie, $R_2 = 900\ \Omega$ verso massa; l'uscita $V_{R2}$ è presa sulla resistenza. Valori letti sull'immagine della figura, Mirandola p. 82.*

> [!success]- Soluzione
> Questo è più semplice del precedente: **è tutta una maglia in serie**, nessun parallelo, quindi niente coniugati.
>
> **Passo 1:**
> $$\omega = 2\pi\cdot 1200 = 7539{,}8\ \text{rad/s} \qquad \bar{Z}_C = -\frac{j}{7539{,}8\cdot 40\cdot10^{-9}} = -j\,3315{,}7\ \Omega$$
>
> **Passo 2 — impedenza totale della maglia:**
> $$\bar{Z}_{tot} = R_1 + \bar{Z}_C + R_2 = 330 - j3315{,}7 + 900 = 1230 - j\,3315{,}7\ \Omega$$
> $$|\bar{Z}_{tot}| = \sqrt{1230^2 + 3315{,}7^2} = 3536{,}5\ \Omega \qquad \angle\bar{Z}_{tot} = \arctan\frac{-3315{,}7}{1230} = -69{,}7°$$
>
> **Passo 3 — partitore su $R_2$:**
> $$\bar{V}_{R2} = \bar{V}_g\,\frac{R_2}{\bar{Z}_{tot}} = \frac{2{,}5\cdot 900}{3536{,}5\,\angle{-69{,}7°}} = \frac{2250}{3536{,}5}\,\angle{+69{,}7°}$$
> $$|\bar{V}_{R2}| = \mathbf{0{,}64\ V_{eff}} \;✅ \qquad \angle\bar{V}_{R2} = \mathbf{+69{,}7° = +1{,}22\ rad}$$
>
> Nota il meccanismo del segno: $R_2$ è **reale** (fase zero), quindi la fase del risultato è $0 - \angle\bar{Z}_{tot} = +69{,}7°$. **Dividere per un numero con fase negativa produce una fase positiva.**

> [!danger] Anche qui il segno non torna — ed è opposto a quello del libro
> Il libro riporta $-1{,}2$ rad; io ottengo $+1{,}22$ rad. Il **modulo coincide esattamente** (0,64), quindi la lettura del circuito è giusta: la discrepanza è solo nel segno.
>
> **Perché il positivo è quello giusto**: il condensatore è **in serie** e l'uscita è **sulla resistenza**. È la configurazione **passa alto** (TABELLA 6 di [[Filtri passivi del primo ordine]]), e in un passa alto la fase va da $+90°$ a $0°$: **sempre positiva**.
>
> **Controllo di plausibilità sul valore**: la frequenza di taglio della maglia è
> $$f_t = \frac{1}{2\pi (R_1+R_2)C} = \frac{1}{2\pi\cdot 1230\cdot 40\cdot10^{-9}} = 3235\ \text{Hz}$$
> Lavoriamo a 1200 Hz, cioè **ben sotto** la frequenza di taglio: siamo nella banda oscura del passa alto, dove la fase è vicina a $+90°$. E infatti $+69{,}7°$ ✅. Coerente anche il modulo: 0,64 V su 2,5 V è una forte attenuazione, come ci si aspetta sotto il taglio.

> [!tip] La lezione dei due esercizi — non sono due refusi indipendenti
> A prima vista i due scarti sembrano casuali e «in direzioni opposte»: nel 9 il libro mette il più dove va il meno, nel 10 il meno dove va il più. **Ma non è casualità.** Sono due circuiti di carattere opposto (passa basso / passa alto), e in *entrambi* il libro riporta esattamente **l'opposto** del valore corretto:
>
> | Es. | Circuito | Argomento corretto | Chiave del libro |
> |---|---|---|---|
> | 9 | passa basso (uscita su $C$) | $-0{,}91$ rad | $+0{,}91$ rad |
> | 10 | passa alto (uscita su $R_2$) | $+1{,}22$ rad | $-1{,}2$ rad |
>
> Un solo errore spiega tutti e due: la chiave riporta lo **sfasamento dell'ingresso rispetto all'uscita** ($\angle \bar V_g - \angle \bar V_{out}$) invece di quello dell'uscita rispetto all'ingresso. È il segno rovesciato della convenzione standard — la stessa che usa il libro nell'ESEMPIO 5, dove il $+37{,}7°$ è correttamente riferito all'uscita.
>
> ⚠️ Due casi non *dimostrano* la regola: è la spiegazione più economica, non una certezza. Ma la conclusione operativa non cambia, e vale comunque:
>
> **Non fidarti del segno di una soluzione: ricavalo dal circuito.** Uscita sul condensatore → ritardo (fase negativa). Uscita sulla resistenza con $C$ in serie → anticipo (fase positiva). Sono due righe di ragionamento e non sbagli mai.

---

## Procedure operativa e trucchi

### Pattern risolutivo standard (scrivi in 4 passi)

1. **Converti eccitazioni**: $\bar{E} = E_{\text{eff}}\angle 0°$, $\bar{I}_{\text{sorg}} = I_{\text{eff}}\angle\varphi$, ecc.
2. **Converti impedenze**: $R \to R$, $L \to j\omega L$, $C \to 1/(j\omega C) = -j/(\omega C)$.
3. **Risolvi la rete**: applica Kirchhoff/Ohm/Thevenin in campo complesso. Ottieni $\bar{V}_{\text{out}}$ e/o $\bar{I}_{\text{out}}$ come fasori.
4. **Torna nel tempo**: $|\bar{V}| \to V_p = \sqrt{2} |\bar{V}|$, $\angle\bar{V} \to$ sfasamento rispetto al riferimento.

### Esempio svolto commentato

Rete: $\bar{E} = 10\angle 0°$ V, $R = 100\,\Omega$, $L = 10$ mH in serie. $\omega = 1000$ rad/s.
1. $\bar{Z}_L = j\omega L = j \cdot 1000 \cdot 0{,}01 = j10\,\Omega$.
2. $\bar{Z}_{\text{tot}} = 100 + j10 = 100{,}5 \angle 5{,}71°\,\Omega$.
3. $\bar{I} = \bar{E}/\bar{Z}_{\text{tot}} = 10\angle 0° / 100{,}5 \angle 5{,}71° = 0{,}0995 \angle -5{,}71°$ A.
4. $i(t) = 0{,}0995\sqrt{2} \sin(1000 t - 5{,}71°) \approx 0{,}141 \sin(1000 t - 5{,}71°)$ A.

## Errori "trappola" sul metodo simbolico

1. **Fasori solo a frequenza singola**: se il circuito ha più generatori a frequenze diverse, il metodo simbolico **non si può applicare direttamente**: devi usare la sovrapposizione calcolando i fasori separatamente per ogni frequenza.
2. **Errore iniziale di conversione**: ricorda $V_{\text{eff}} = V_p/\sqrt{2}$, non $V_p \cdot \sqrt{2}$.
3. **Uscita a regime**: il metodo fornisce la soluzione di regime. Se il problema chiede il transitorio, NON è metodo simbolico.
