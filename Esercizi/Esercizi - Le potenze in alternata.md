---
tags: [recupero, elettronica, corrente-alternata, potenze, rifasamento, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ — Mirandola Vol.2, Cap. 2 §4 «La potenza in alternata», pp. 62-67. Esercizi 11-13 (FIG. 47-49) da p. 82 (pag.-PDF 19): testi, valori dei componenti e risposte stampate letti dall'immagine a 220 dpi. Quesiti di riepilogo a p. 80 (pag.-PDF 18)."
prove: [scritta, orale]
---

# Esercizi — Le potenze in alternata

Teoria di riferimento: [[Le potenze in alternata]]

> [!danger] Due esercizi del libro hanno dati o risposte incoerenti
> Esercizio 12 ed esercizio 13. Non è colpa tua se non ti tornano: vedi i riquadri rossi.

---

# Parte A — Quesiti (prova orale)

> [!question]- 19 — Come sono definite le potenze istantanea, attiva, reattiva e apparente? Quali relazioni le legano?
> - **Istantanea**: $p(t) = v(t)\cdot i(t)$ — il prodotto punto per punto, varia nel tempo a **frequenza doppia**.
> - **Attiva**: $P = V_{eff}I_{eff}\cos\varphi$ **[W]** — la potenza media **dissipata in calore**. È quella che paghi e che fa lavoro.
> - **Reattiva**: $Q = V_{eff}I_{eff}\operatorname{sen}\varphi$ **[VAR]** — la potenza media **alternativamente immagazzinata e ceduta**. Valor medio nullo: va e torna.
> - **Apparente**: $S = V_{eff}I_{eff}$ **[VA]** — il prodotto secco, l'ampiezza dell'oscillazione della potenza istantanea. Serve a dimensionare **conduttori e generatori**.
>
> **Le relazioni** — il triangolo delle potenze:
> $$P = S\cos\varphi \qquad Q = S\operatorname{sen}\varphi \qquad S = \sqrt{P^2 + Q^2}$$
> e in funzione della corrente: $P = RI^2$, $Q = |X|I^2$, $S = |Z|I^2$.
>
> **Il dettaglio che fa punteggio**: le tre hanno la **stessa dimensione fisica** (watt), ma unità diverse — proprio per ricordare che **non si sommano tra loro**. Si compongono come vettori perpendicolari.

> [!question]- 20 — Quale significato ha, dal punto di vista della potenza, lo sfasamento $\varphi$?
> Decide **come si spartisce** $S$ tra $P$ e $Q$:
> - $\varphi = 0$ (resistivo) → $\cos\varphi = 1$ → $P = S$, $Q = 0$: tutta la potenza è utile;
> - $\varphi = \pm90°$ (reattivo puro) → $\cos\varphi = 0$ → $P = 0$, $|Q| = S$: nessuna potenza utile, solo palleggio;
> - in mezzo, $\cos\varphi$ è la **frazione utile**.
>
> Da qui il nome **fattore di potenza**. E $\varphi$ non è una grandezza nuova: **è l'argomento dell'impedenza**.

> [!question]- 21 — Che cosa si intende per rifasamento di un impianto elettrico?
> È l'inserimento di una **batteria di condensatori in parallelo al carico**, con valore tale da compensare (almeno parzialmente) la **reattanza induttiva** del carico, aumentando così il $\cos\varphi$ dell'impianto.
> Il valore si calcola con:
> $$C_{rifas} = \frac{P(\operatorname{tg}\varphi - \operatorname{tg}\varphi')}{\omega V^2}$$
> Serve perché i carichi industriali (motori, saldatrici, trasformatori, alimentatori di lampade fluorescenti) contengono **avvolgimenti**, cioè induttanze.

> [!question]- 22 — Quali problemi può creare la potenza reattiva?
> La potenza reattiva **non viene consumata dal carico, ma deve comunque viaggiare** sulla linea. Questo:
> - provoca una **corrente in linea** più alta del necessario;
> - quella corrente **dissipa potenza per effetto Joule** sui cavi;
> - costringe il distributore a **sovradimensionare cavi e macchine generatrici**, senza che ciò dia più potenza utile all'utilizzatore.
>
> In una frase: **paghi il trasporto di energia che non usi**.

> [!question]- 23 — Che cosa prevede la normativa sul fattore di potenza e come si agisce per soddisfarla?
> Per carichi con **$P > 15$ kW**, l'utente deve assorbire energia con $\cos\varphi_{mm} \ge 0{,}9$ (media mensile).
> - $0{,}7 \le \cos\varphi_{mm} < 0{,}9$ → l'utente **sceglie**: pagare una penale o rifasare.
> - $\cos\varphi_{mm} < 0{,}7$ → **obbligo** di rifasare.
> - **In nessun caso** l'impianto deve **erogare energia reattiva capacitiva** alla rete, cioè non si deve sovracompensare.
>
> Si agisce inserendo la batteria di condensatori. Il libro nota che conviene quasi sempre: il costo dei condensatori si **recupera in breve tempo** rispetto alle penali.

> [!question]- 24 — Quali sono i vantaggi che si ottengono con il rifasamento?
> Tutti discendono da **uno solo: scende la corrente di linea**. Da lì:
> - diminuisce la **potenza apparente** dell'utenza;
> - diminuiscono le **perdite in linea** → aumenta il **rendimento**;
> - si può usare una **sezione di cavo inferiore**;
> - le **macchine generatrici** possono essere più piccole;
> - diminuiscono le **cadute di tensione**;
> - il distributore può **servire più utenze** con la stessa rete.
>
> E poiché i vantaggi si sentono su **tutta la rete a monte**, conviene il **rifasamento capillare**: condensatori il più vicino possibile agli utilizzatori, così da ridurre le perdite anche **dentro** l'industria.
>
> **Attenzione alla domanda trabocchetto**: il rifasamento **non riduce** la potenza attiva consumata. $P$ resta identica.

---

# Parte B — Esercizi (prova scritta)

## Esercizio 11 — Potenze su un bipolo RC

**Testo.** Con riferimento al bipolo RC di FIGURA 47, collegato a un generatore di tensione sinusoidale di 0,4 V$_{eff}$ e frequenza 600 Hz, calcolare il fattore di potenza, la potenza attiva, reattiva e apparente sul bipolo. *(Vedi ESEMPIO 6)*
**Risposte del libro (p. 82, lette sull'immagine):** $\cos\varphi = 0{,}58$; $P = 62{,}8$ µW; $Q = 87{,}6$ µVAR; $S = 108$ µVA — ⚠️ il libro stampa $Q$ **senza segno**, vedi sotto.

![[fig-2-47-esercizio-11.png]]
*FIGURA 47 — $R = 860\ \Omega$ in serie a $C = 220$ nF. Valori letti sull'immagine, Mirandola p. 82.*

> [!success]- Soluzione
> $$\omega = 2\pi\cdot 600 = 3769{,}9\ \text{rad/s} \qquad X_C = -\frac{1}{\omega C} = -\frac{1}{3769{,}9\cdot 220\cdot10^{-9}} = -1205{,}7\ \Omega$$
> $$\bar{Z} = 860 - j\,1205{,}7 \qquad |\bar{Z}| = \sqrt{860^2 + 1205{,}7^2} = 1481{,}0\ \Omega$$
> $$\varphi = \arctan\frac{-1205{,}7}{860} = -54{,}5° \qquad \cos\varphi = 0{,}581 \;✅ \qquad \operatorname{sen}\varphi = -0{,}814$$
> $$I_{eff} = \frac{0{,}4}{1481} = 270{,}1\ \mu\text{A}$$
> $$P = V_{eff}I_{eff}\cos\varphi = 0{,}4\cdot 270{,}1\cdot10^{-6}\cdot 0{,}581 = 62{,}8\ \mu\text{W} \;✅$$
> $$Q = V_{eff}I_{eff}\operatorname{sen}\varphi = 0{,}4\cdot 270{,}1\cdot10^{-6}\cdot(-0{,}814) = -87{,}9\ \mu\text{VAR} \;✅$$
> $$S = V_{eff}I_{eff} = 0{,}4\cdot 270{,}1\cdot10^{-6} = 108{,}0\ \mu\text{VA} \;✅$$
>
> **Verifica col triangolo delle potenze**:
> $$\sqrt{P^2+Q^2} = \sqrt{62{,}8^2 + 87{,}9^2} = \sqrt{3944 + 7726} = 108{,}0\ \mu\text{VA} = S \;✅$$

> [!warning] Il libro omette il segno di $Q$ — anche qui
> ⚠️ **Correzione di una versione precedente di questa nota.** Diceva: «la risposta del libro è $Q = -87{,}6$ µVAR, **col segno meno**; il libro contraddice sé stesso rispetto all'ESEMPIO 6». **Entrambe le affermazioni sono false.**
> Letta sull'immagine di p. 82, la chiave stampa $Q = \mathbf{87{,}6}$ µVAR, **senza meno** — esattamente come nell'ESEMPIO 6 (p. 64). Il libro **non** si contraddice: omette il segno di $Q$ in entrambi i casi capacitivi, adottando di fatto la convenzione del **modulo**.
>
> **Cosa resta valido**: il tuo risultato $Q = -87{,}9$ µVAR è quello corretto secondo la (2.29), e il segno è informazione vera ($Q<0$ → capacitivo). Scrivilo. Ma non appoggiarti all'argomento «lo fa anche il libro»: non lo fa.
>
> 📌 *Perché era importante correggerlo*: la nota precedente aveva **alterato la risposta stampata** (aggiungendo un meno che non c'è) e poi l'aveva citata come prova indipendente. Un vault che si auto-conferma così non è verificabile.

---

## Esercizio 12 — Potenze su un bipolo RL

**Testo.** Con riferimento al bipolo RL di FIGURA 48, collegato a un generatore di tensione sinusoidale da 1,5 V$_{eff}$ e frequenza **1600 Hz**, calcolare il fattore di potenza, la potenza attiva, reattiva e apparente sul bipolo. *(Vedi ESEMPIO 7)*
**Risposte del libro (p. 82, lette sull'immagine):** $\cos\varphi = 0{,}701$; $P = 1{,}10$ mW; $Q = 1{,}12$ mVAR; $S = 1{,}58$ mVA

![[fig-2-48-esercizio-12.png]]
*FIGURA 48 — $L = 10$ mH in serie a $R = 1$ k$\Omega$. Valori letti sull'immagine, Mirandola p. 82.*

> [!danger] I dati stampati non producono le risposte stampate
> **Con i dati del libro** ($f = 1600$ Hz, $L = 10$ mH, $R = 1$ k$\Omega$):
> $$\omega = 2\pi\cdot 1600 = 10{.}053\ \text{rad/s} \qquad X_L = \omega L = 100{,}5\ \Omega$$
> $$\bar{Z} = 1000 + j\,100{,}5 \qquad |\bar{Z}| = 1005\ \Omega \qquad \cos\varphi = \frac{1000}{1005} = \mathbf{0{,}995}$$
> Il libro dice $\cos\varphi = 0{,}701$. **Non torna**, e non è un arrotondamento: è tutta un'altra cosa.
>
> **Cosa darebbe le risposte del libro**: servirebbe $X_L \simeq 1005\ \Omega$, cioè **dieci volte** quella dei dati. Si ottiene con $f = \mathbf{16000}$ Hz (16 kHz), tenendo $L = 10$ mH:
> $$X_L = 1005{,}3\ \Omega \qquad |\bar{Z}| = \sqrt{1000^2+1005{,}3^2} = 1418\ \Omega \qquad \cos\varphi = \frac{1000}{1418} = 0{,}705 \;✅$$
> $$I = \frac{1{,}5}{1418} = 1{,}058\ \text{mA} \qquad P = 1{,}12\ \text{mW} \;✅ \qquad Q = +1{,}13\ \text{mVAR} \;✅ \qquad S = 1{,}59\ \text{mVA} \;✅$$
> **Tutte e quattro combaciano** entro l'arrotondamento (il libro dà $\cos\varphi = 0{,}701$ e $P = 1{,}10$ mW contro 0,705 e 1,12 mW: scarto sotto l'1%, mentre $Q$ e $S$ coincidono).
>
> ⚠️ **Ma attenzione a quale dato è sbagliato: non è deducibile.** Quello che serve è $X_L \simeq 1005\ \Omega$, e ci sono **due** modi di ottenerlo con un solo zero spostato:
> - $f = 16\,000$ Hz con $L = 10$ mH (il valore stampato in FIGURA 48), **oppure**
> - $f = 1600$ Hz (il valore stampato nel testo) con $L = \mathbf{100}$ **mH**.
>
> Producono lo **stesso** $X_L$ e quindi le stesse identiche risposte: le soluzioni del libro **non permettono di distinguere** quale dei due dati sia il refuso. Una versione precedente di questa nota affermava con certezza che fosse la frequenza — non c'è modo di saperlo.
> *Indizio debole a favore dell'induttanza*: l'esercizio 13, nella stessa pagina, usa proprio $L = 100$ mH. Resta un indizio, non una prova.
>
> **Come svolgerlo**: usa $f = 16$ kHz e i risultati del libro tornano. Se invece il prof desse davvero 1600 Hz, allora $\cos\varphi = 0{,}995$, $P = 2{,}23$ mW, $Q = 0{,}22$ mVAR, $S = 2{,}24$ mVA — e sono questi i valori giusti per quei dati.

> [!success]- Soluzione completa con $X_L = 1005\ \Omega$ (qui scritta come $f = 16$ kHz, $L = 10$ mH)
> $$\omega = 2\pi\cdot 16000 = 100{.}531\ \text{rad/s} \qquad X_L = \omega L = 100531\cdot 10\cdot10^{-3} = 1005{,}3\ \Omega$$
> $$\bar{Z} = R + jX_L = 1000 + j\,1005{,}3 \qquad |\bar{Z}| = \sqrt{1000^2 + 1005{,}3^2} = 1418{,}0\ \Omega$$
> $$\varphi = \arctan\frac{1005{,}3}{1000} = +45{,}2° \qquad \cos\varphi = 0{,}705 \qquad \operatorname{sen}\varphi = 0{,}709$$
> $$I_{eff} = \frac{1{,}5}{1418} = 1{,}058\ \text{mA}$$
> $$P = 1{,}5\cdot 1{,}058\cdot10^{-3}\cdot 0{,}705 = 1{,}12\ \text{mW}$$
> $$Q = 1{,}5\cdot 1{,}058\cdot10^{-3}\cdot 0{,}709 = +1{,}13\ \text{mVAR} \quad(\text{positiva: carico induttivo})$$
> $$S = 1{,}5\cdot 1{,}058\cdot10^{-3} = 1{,}59\ \text{mVA}$$
> Verifica col triangolo: $\sqrt{1{,}12^2 + 1{,}13^2} = 1{,}59$ ✅
>
> Nota che $\varphi \simeq 45°$: a questa frequenza $X_L \simeq R$, cioè siamo **esattamente alla frequenza di taglio** del bipolo. Non è un caso — l'esercizio è costruito così.

---

## Esercizio 13 — Rifasamento

**Testo.** Determinare il valore della capacità $C_{rifas}$ da porre in parallelo al bipolo di FIGURA 49, alimentato da un generatore di tensione sinusoidale da 380 V$_{eff}$ e frequenza 50 Hz, per rifasare al valore $\cos\varphi' = 0{,}90$. *(Vedi ESEMPIO 8)*
**Risposta del libro (p. 82, letta sull'immagine):** $C_{rifas} = 5{,}57$ µF

![[fig-2-49-esercizio-13.png]]
*FIGURA 49 — $L = 100$ mH in serie a $R = 50\ \Omega$. Valori letti sull'immagine, Mirandola p. 82.*

> [!success]- Soluzione
> **Passo 1 — caratterizzare il carico.**
> $$\omega = 2\pi\cdot 50 = 314{,}16\ \text{rad/s} \qquad X_L = \omega L = 314{,}16\cdot 0{,}1 = 31{,}42\ \Omega$$
> $$\bar{Z} = 50 + j\,31{,}42 \qquad |\bar{Z}| = \sqrt{50^2+31{,}42^2} = 59{,}05\ \Omega$$
> $$\operatorname{tg}\varphi = \frac{X_L}{R} = \frac{31{,}42}{50} = 0{,}6283 \qquad \varphi = 32{,}1° = 0{,}561\ \text{rad} \qquad \cos\varphi = 0{,}847$$
>
> **Passo 2 — la potenza attiva** (è l'unica grandezza del carico che serve nella 2.33):
> $$I_{eff} = \frac{380}{59{,}05} = 6{,}435\ \text{A} \qquad P = R\,I^2 = 50\cdot 6{,}435^2 = 2071\ \text{W}$$
>
> **Passo 3 — il nuovo sfasamento:**
> $$\varphi' = \arccos 0{,}90 = 25{,}84° = 0{,}451\ \text{rad} \qquad \operatorname{tg}\varphi' = 0{,}4843$$
>
> **Passo 4 — applicare la (2.33):**
> $$C_{rifas} = \frac{P(\operatorname{tg}\varphi - \operatorname{tg}\varphi')}{\omega V^2} = \frac{2071\cdot(0{,}6283 - 0{,}4843)}{314{,}16\cdot 380^2} = \frac{298{,}2}{45{,}36\cdot10^{6}} = \mathbf{6{,}57\ \mu F}$$

> [!danger] Il libro riporta 5,57 µF; io ottengo 6,57 µF
> Ho ricontrollato ogni passaggio, e la differenza è **esattamente 1,00 µF** — il che fa pensare a un **refuso di una cifra** (un 6 stampato come 5) più che a un errore di calcolo.
>
> Rifai tu il conto: i valori intermedi sono tutti verificabili in modo indipendente.
> - $\operatorname{tg}\varphi = X_L/R = 31{,}42/50 = 0{,}6283$ — esatto, senza passare per l'arcotangente.
> - $P = RI^2 = 50 \cdot 6{,}435^2 = 2071$ W — e come controllo, $P = V I\cos\varphi = 380\cdot 6{,}435\cdot 0{,}847 = 2071$ W ✅ (due strade indipendenti, stesso risultato).
> - $\operatorname{tg}\varphi'$ da $\cos\varphi' = 0{,}90$: $\operatorname{sen}\varphi' = \sqrt{1-0{,}81} = 0{,}436$, quindi $\operatorname{tg}\varphi' = 0{,}436/0{,}90 = 0{,}4843$ ✅
>
> Se il tuo libro cartaceo riporta 5,57, sappi che il procedimento qui sopra è corretto: è il **metodo** che devi saper riprodurre allo scritto.

> [!check] Verifica del risultato
> Puoi controllare che il rifasamento faccia il suo mestiere. La corrente di linea prima e dopo:
> $$I = 6{,}435\ \text{A} \qquad\longrightarrow\qquad I' = \frac{P}{V\cos\varphi'} = \frac{2071}{380\cdot 0{,}90} = 6{,}055\ \text{A}$$
> Scende del 6% — e le perdite in linea, che vanno col **quadrato**, dell'11,5%. La potenza attiva $P$ è rimasta 2071 W: il carico lavora esattamente come prima.
>
> Nota che qui il guadagno è modesto, perché il carico partiva già da un $\cos\varphi$ discreto (0,847). Il rifasamento rende molto di più sui carichi fortemente induttivi.

---

## Esercizi svolti da Edutecnica.it (catalogo palternax completo)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettrotecnica/palternax/palternax.htm](https://www.edutecnica.it/elettrotecnica/palternax/palternax.htm). 6 esercizi su potenze in alternata e rifasamento.

### Es. P1 — Calcolo P, Q, S da Z e i(t)

- **Dati**: $Z = 3 + j5\,\text{k}\Omega$, $i(t) = 12\sin(\omega t)$ mA.
- **Trovare**: $P$, $Q$, $S$.
- **Soluzione edutecnica**: $P = 0{,}216$ W, $Q = 0{,}36$ VAR, $S = 0{,}42$ VA.
- **Svolgimento passo-passo**:
  1. Fasore: $I_{\text{eff}} = 12/\sqrt{2} = 8{,}49$ mA. $\bar{I} = 8{,}49\angle 0$ mA.
  2. $\bar{Z} = 3 + j5\text{ k}\Omega$ → $|Z| = \sqrt{34} = 5{,}83\text{ k}\Omega$, $\varphi = \arctan(5/3) = 59{,}04°$.
  3. $\bar{V} = \bar{Z} \cdot \bar{I} = 5{,}83\text{k} \cdot 8{,}49\text{mA} \angle 59{,}04° = 49{,}5 \angle 59{,}04°$ V.
  4. $S = V_{\text{eff}} I_{\text{eff}} = 49{,}5 \cdot 8{,}49\text{mA} = 0{,}42$ VA ✓.
  5. $P = S \cos\varphi = 0{,}42 \cdot 0{,}515 = 0{,}216$ W ✓.
  6. $Q = S \sin\varphi = 0{,}42 \cdot 0{,}857 = 0{,}36$ VAR ✓.

### Es. P2 — Impedenza da P, V e cosφ

- **Dati**: $P = 800$ W, $V = 220$ V, $\cos\varphi = 0{,}8$ (carico induttivo).
- **Trovare**: $R$, $X_L$, $Q$.
- **Soluzione edutecnica**: $R = 32\,\Omega$, $X_L = 24\,\Omega$, $Q = 600$ VAR.
- **Svolgimento**:
  1. $I = P/(V\cos\varphi) = 800/(220 \cdot 0{,}8) = 4{,}545$ A.
  2. $|Z| = V/I = 220/4{,}545 = 48{,}4\,\Omega$.
  3. $R = |Z| \cos\varphi = 48{,}4 \cdot 0{,}8 = \mathbf{38{,}72\,\Omega}$ — **non** 32 come dice edutecnica (vedi riquadro).
  4. $X_L = |Z| \operatorname{sen}\varphi = 48{,}4 \cdot 0{,}6 = \mathbf{29{,}04\,\Omega}$ — **non** 24.
  5. $Q = P \tan\varphi = 800 \cdot \tan(36{,}87°) = 800 \cdot 0{,}75 = 600$ VAR ✓.

> [!danger] Qui edutecnica sbaglia — ed è la prima volta
> Il vault segnalava «diverse approssimazioni — vedi quale è giusta per i tuoi conti». **Non è una questione di approssimazioni**: con $V = 220$ V i valori corretti sono $R = 38{,}72\ \Omega$ e $X_L = 29{,}04\ \Omega$, verificati per **due strade indipendenti**:
> $$R = \frac{P}{I^2} = \frac{800}{4{,}545^2} = 38{,}72 \qquad R = |Z|\cos\varphi = 48{,}4\cdot0{,}8 = 38{,}72$$
> **Da dove vengono il 32 e il 24 di edutecnica**: corrispondono a $|Z| = 40\ \Omega$, cioè a $I = 5$ A, cioè a $\mathbf{V = 200}$ **V**. Con $V = 200$: $R = V^2\cos^2\varphi/P = 40000\cdot0{,}64/800 = 32$ ✔ e $X_L = 40000\cdot0{,}8\cdot0{,}6/800 = 24$ ✔ — **esatti, non approssimati**.
> Il testo di edutecnica però dichiara $V = 220$ V (verificato sulla pagina originale il 2026-07-20). Quindi la fonte è **internamente incoerente**: testo a 220 V, risposte calcolate a 200 V.
>
> **Perché il vault non se n'era accorto**: aveva visto $Q = 600$ VAR combaciare e aveva dedotto che il resto fosse questione di arrotondamenti. Ma $Q = P\tan\varphi$ **non dipende da $V$** — combacia in entrambi gli scenari, quindi non prova nulla. È l'unico dei tre valori che non discrimina.
>
> **Per l'esame**: se il testo dà $V = 220$ V, la risposta è $R = 38{,}72\ \Omega$.

### Es. P3 — Potenza con componente DC e AC

- **Dati**: $R = 2\,\text{k}\Omega$, $i(t) = 16 + 3\sin(\omega t)$ mA. (combinata DC + AC)
- **Trovare**: $P$ totale dissipata su $R$.
- **Soluzione edutecnica**: $P = 0{,}521$ W.
- **Svolgimento**: $P = R \cdot I_{\text{eff}}^2$. $I_{\text{eff}}^2 = I_{DC}^2 + I_{AC,\text{eff}}^2 = 16^2 + (3/\sqrt{2})^2 = 256 + 4{,}5 = 260{,}5$ mA². $P = 2\text{k} \cdot 260{,}5\text{ mA}^2 = 520{,}9$ mW = 0{,}521 W ✓.

### Es. P4 — Impedenze in serie con P, Q, S parziali

- **Dati**: 3 impedenze in serie con $P_1$, $Q_2$, $S_3$ noti. Trovare $P_{\text{tot}}$.
- **Soluzione edutecnica**: $P_{\text{tot}} = 1425$ W.
- **Note**: per sommare le potenze, ogni bipolo contribuisce a $P$ e $Q$ in modo vettoriale. $P_{\text{tot}} = \sum P_i$ (somma scalare). $Q_{\text{tot}} = \sum Q_i$ (somma scalare). $S_{\text{tot}} = \sqrt{P^2+Q^2}$.

### Es. P5 — Calcolo completo P, Q, S + rifasamento

- **Dati**: $R$, $L$ dati, $V_0$ noto. Trovare $I$, $C$ per rifasamento, $P$, $Q$, $S$.
- **Soluzione edutecnica**: $I = 44{,}2$ mA, $C = 0{,}87\,\mu\text{F}$, $P = 488{,}4$ mW (e valori analoghi per $Q$, $S$).
- **Procedura**: rifasamento → $C$ tale che $\cos\varphi_{\text{nuovo}} \geq 0{,}9$ (target). $C = P/(\omega V^2 (\tan\varphi_{\text{vecchio}} - \tan\varphi_{\text{nuovo}}))$.

### Es. P6 — Rifasamento di parallelo di impedenze

- **Dati**: $P$, $\cos\varphi$, $V_p$, $Q_C$, $X_C$ noti. Trovare $I$ totale, $I$ sui rami, $R_1$, $R_2$, $L$.
- **Procedura**: usare rifasamento per calcolare le correnti di ramo.

## Pattern di errore frequenti (Carli scritta)

1. **Confondere $P$, $Q$, $S$**: $P$ [W] dissipata, $Q$ [VAR] reattiva, $S$ [VA] apparente. Errore: sommare W + VAR! Mai. Si sommano vettorialmente: $S = \sqrt{P^2+Q^2}$.
2. **Segno di $Q$**: induttivo → $Q > 0$, capacitivo → $Q < 0$.
3. **Rifasamento: $\cos\varphi = 0{,}9$ TARGET**: non eccedere! $\cos\varphi$ troppo alto → rifasamento "in eccesso" → il carico diventa capacitivo, nuovo problema.
