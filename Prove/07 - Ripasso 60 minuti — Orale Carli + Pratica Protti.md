---
tags: [recupero, elettronica, prova-orale, prova-pratica, carli, protti, ripasso]
fonte: "Piano dell'ora di pausa deciso in [[Calendario]] (13:00-14:00) — versione cronometrata"
docenti: [Prof. Carlo Carli, Prof. Giampaolo Protti]
tipologia: Ripasso a tempo
---
# 07 — Ripasso 60 minuti · orale Carli + pratica Protti

> [!important] ⏱️ 13:00 – 14:00 · lo scritto è finito, restano sessanta minuti
> Questa è la versione **cronometrata** della decisione già presa in [[Calendario]] per
> quest'ora: *«solo due cose — le risposte D1-D23 e il cheat sheet. Niente esercizi, niente
> libro, niente cose nuove»*. Qui quelle due cose sono spalmate sui minuti, con in più il
> blocco Protti che alle 14:00 arriva insieme a Carli.
>
> **La regola dell'ora**: si **scrive** e si **parla**. Non si legge. Un'ora di lettura
> passiva prima di un orale non sposta niente; venti minuti di disegni a memoria sì.

> [!warning] Cosa NON si fa in quest'ora
> ⛔ Niente esercizi numerici · ⛔ niente libro · ⛔ niente argomenti nuovi ·
> ⛔ **niente BJT/JFET/MOSFET da studiare**: erano la materia dello **scritto**, ormai
> consegnato. Restano solo come *confronto* a voce (BJT vs MOSFET), non come capitoli.

---

## Lo scope, in due righe

Dalla LETTERA, verbatim, le due prove del pomeriggio:

| Prova | Cosa chiede |
|---|---|
| **Orale — Carli** | domande sul **diodo**, sui **circuiti in corrente alternata** e sui **filtri passivi del primo ordine** |
| **Pratica — Protti** | domande, esercizi, **misure con l'oscilloscopio**: diodi, segnali sinusoidali, reti RLC, filtri, amplificatori a BJT |

Il **diodo** è l'unico componente nominato da entrambe. Per questo si prende metà dell'ora.

---

## La tabella di marcia

| Minuti | Blocco | Come si fa |
|---|---|---|
| **0-3** | Scope lock | Rileggi le due righe qui sopra. Basta. |
| **3-23** | 🖊️ **Diodi a matita** — 9 disegni a memoria | foglio bianco, penna, niente appunti |
| **23-33** | 🗣️ **Le 5 domande 🔴 dei diodi** — a voce | a voce alta, non nella testa |
| **33-43** | 🗣️ **AC e filtri** — le 3 derivazioni | a voce, con la mano che scrive i passaggi |
| **43-56** | 🔧 **Protti** — la sequenza operativa e i 6 errori | ripetizione a memoria |
| **56-60** | ⚠️ Trappole lessicali + come si risponde | lettura, questa sì |

---

## 🖊️ Minuti 3-23 · I nove disegni (il blocco che pesa di più)

> [!danger] Perché venti minuti su questo
> **21 domande su 39** dei fogli veri di Carli iniziano con «**Disegnare**». Un disegno
> incompleto vale meno di una descrizione completa — ed è la parte che si dimentica per prima.

Foglio bianco. Nove disegni, **senza guardare niente**. Circa 2 minuti l'uno.

1. **Struttura del diodo** — le due zone **P** e **N** etichettate, **A** su P e **K** su N, la giunzione marcata.
2. **Simbolo + versi convenzionali** — triangolo e **barra** del catodo; $I_D$ con la freccia **da A a K**; $V_D$ con il **+ sull'anodo**.
3. **Curva caratteristica completa** — assi **con le unità** ($V_D$ in V; $I_D$ in **mA** sopra e **µA/nA** sotto), $V_s \approx 0{,}6$ V, il tratto piatto inverso, il ginocchio a $-V_B$, e **le due zone scritte**: DIRETTA e INVERSA.
4. **La tabella 3×3 dei tre modelli** — per A, B, C: inversa, diretta e **curva**. La curva di A **inclinata** (pendenza $1/r_D$), quella di B **verticale a 0,7 V**, quella di C **verticale a 0 V**.
5. **Raddrizzatore a semionda** — generatore, **un** diodo in serie, $R_L$, e la forma d'onda con il picco a $V_p - 0{,}7$.
6. **Ponte di Graetz** — **4 diodi orientati bene**, quali conducono su ciascuna semionda, picco a $V_p - 1{,}4$, valor medio $\overline{V_o} = 2V_p/\pi$.
7. **Limitatore con diodi in serie** — la **$R$ in serie al segnale**, $n$ diodi impilati nello stesso verso, la soglia $n \cdot 0{,}7$ **segnata sulla forma d'onda**.
8. **Limitatore in antiparallelo** — la **$R$**, due diodi con versi opposti, la fascia $\pm 0{,}7$ V marcata.
9. **Regolatore a Zener** — $R$ in serie, Zener **in inversa** (catodo verso il nodo alto), $R_L$ in parallelo, e le **tre correnti** $I_R$, $I_Z$, $I_L$ marcate. Accanto: simbolo dello Zener con i **«baffi»** e curva col tratto verticale a $-V_Z$ nel **terzo quadrante**.

> [!danger] I tre errori di disegno che Carli smonta in una domanda
> 1. **Zener disegnato in diretta** nel regolatore → non è più un regolatore, è un diodo normale.
> 2. **Limitatore senza la $R$ in serie** → il diodo che conduce cortocircuita il generatore. La $R$ non è un dettaglio: è ciò su cui cade $v_i - v_o$.
> 3. **Curva V-I senza le unità sugli assi** → mA sopra e µA sotto non sono un vezzo: sono la prova che hai capito quanto è asimmetrica.

Controllo, solo alla fine: [[04 - Verifica tipo Carli — Diodi]] §4 — la checklist di cosa **deve** esserci.

---

## 🗣️ Minuti 23-33 · Le cinque domande che fanno il 9

Due minuti l'una, **a voce alta**. Sono le 🔴: quelle dove la risposta è una riga e la
**giustificazione** è tutto il punto.

> [!question] 1 · «Il diodo è un componente lineare?»
> **No, ed è pure unidirezionale.** Lineare = caratteristica **retta per l'origine** con $R$ costante. Qui: la curva è **esponenziale**, quindi $V_D/I_D$ cambia punto per punto (non esiste «la resistenza del diodo», solo quella statica o differenziale **attorno a un Q**); e $+5$ V danno **mA**, $-5$ V danno **nA**. Non valgono omogeneità e sovrapposizione → **niente Thévenin, Norton, sovrapposizione** sui circuiti a diodi.
> **La chiusura che vale il punto**: è proprio la non linearità a renderlo utile (raddrizzare, limitare, stabilizzare); il prezzo si paga con la **retta di carico** o con i **modelli a tratti**.

> [!question] 2 · «Perché si usano modelli approssimati?»
> Cinque motivi, ne bastano tre detti bene: Shockley è **trascendente** → con Kirchhoff dà un sistema non risolvibile algebricamente; **linearizzando a tratti tornano applicabili i teoremi delle reti lineari**; $I_S$ e $\eta$ variano con temperatura e da esemplare a esemplare, quindi il calcolo «esatto» è **precisione finta**; e di solito serve solo sapere **se conduce o no**.

> [!question] 3 · «I tre modelli, e da cosa dipende la scelta»
> **A** = interruttore + $V_\gamma$ + $r_D$ (semiretta inclinata, alta precisione) · **B** = interruttore + $V_\gamma$ ($V_D = 0{,}7$ V costante, **la più usata**) · **C** = interruttore ideale ($V_D = 0$, qualitativa). **In inversa tutti e tre coincidono**: interruttore aperto.
> **Il criterio**: rapporto fra le tensioni in gioco e $V_\gamma$ (con 24 V, 0,7 V è < 3% → basta C); rapporto fra $r_D$ e le resistenze del circuito (kΩ → $r_D$ trascurabile, B); e la precisione richiesta. **Si sceglie il modello più semplice che garantisce l'accuratezza richiesta.**

> [!question] 4 · «Diodi in serie o in antiparallelo: perché?» ⚠️ è la trappola
> Sono **due circuiti diversi in una domanda sola**. **In serie**: stessa corrente, le cadute si **sommano** → conduzione a $n \cdot 0{,}7$ V, cioè si alza la soglia **senza generatori ausiliari** (svantaggio: soglia quantizzata a multipli di 0,7). **In antiparallelo**: due diodi in parallelo con **verso opposto** → per ogni polarità uno è in diretta → taglio **bilaterale a $\pm 0{,}7$ V**. E si combinano: due gruppi da $n$ in serie, in antiparallelo, danno $\pm n \cdot 0{,}7$ V.

> [!question] 5 · «I due meccanismi di breakdown»
> **Valanga**: il campo **accelera** i minoritari, che per **urto** rompono legami e liberano coppie a catena. Drogaggio **basso**, dominante **sopra ~6 V**, coefficiente di temperatura **positivo**.
> **Zener/tunnel**: drogaggio **pesante** → zona di svuotamento sottilissima → il campo **strappa** direttamente gli elettroni dai legami, che passano per **effetto tunnel**, senza urti. Dominante **sotto ~5 V**, coefficiente **negativo**.
> **La frase che chiude**: fra **5 e 6 V** coesistono e i due coefficienti **si compensano** → gli Zener attorno a **5,6 V** sono i più stabili in temperatura. E il breakdown **non è distruttivo** di per sé: lo diventa se la potenza dissipata supera il massimo, cioè se la corrente non è limitata dall'esterno.

Se avanza tempo, il resto è in [[Ripasso finale — FUSI e Diodi]] Parte D (D1-D23) o in [[diodi-risposte]].

---

## 🗣️ Minuti 33-43 · Alternata e filtri: tre derivazioni, non tre formule

> [!tip] Carli chiede di **spiegare a parole** un passaggio che sai fare per iscritto
> Memorizza la **sequenza**, non il risultato. Tre minuti l'una.

**1 · Da dove viene $\bar{Z}_L = j\omega L$**
- legge fisica: $v(t) = L \, di/dt$
- se $i(t) = I\sin(\omega t + \varphi)$, allora $v(t) = L\omega I\cos(\omega t + \varphi) = L\omega I \sin(\omega t + \varphi + \pi/2)$
- in fasori la derivata **è** la moltiplicazione per $j\omega$ → $\bar{V} = j\omega L \bar{I}$

**2 · Da dove viene $\bar{Z}_C = -j/(\omega C)$, e cosa vuol dire quel $-j$**
- $\bar{I} = j\omega C\bar{V}$ → $\bar{Z}_C = \bar{V}/\bar{I} = 1/(j\omega C) = -j/(\omega C)$
- il $-j$ dice che la **corrente è in anticipo di 90° sulla tensione** (la tensione è in ritardo)
- corollario da avere pronto: $\omega \to \infty \Rightarrow Z_C \to 0$, **il condensatore è un corto alle alte frequenze**; $\omega \to 0 \Rightarrow$ circuito aperto (in DC le C sono aperte)

**3 · Perché la frequenza di taglio dell'RC passa-basso è $\omega_t = 1/(RC)$**
$$\frac{\bar{V}_{out}}{\bar{V}_{in}} = \frac{1/(j\omega C)}{R + 1/(j\omega C)} = \frac{1}{1 + j\omega RC}, \qquad \left|\;\cdot\;\right| = \frac{1}{\sqrt{1 + (\omega RC)^2}}$$
- quando $\omega RC = 1$ il modulo vale $1/\sqrt{2}$ — che è **la definizione operativa** di $f_t$ ($-3$ dB)
- quindi $\omega_t = 1/(RC)$ e $f_t = 1/(2\pi RC)$

**E le due domande di contorno che arrivano quasi sempre:**
- *Limiti del metodo simbolico*: vale solo **a regime** e con eccitazioni **isofrequenziali** — il fasore ha senso solo fra sinusoidi che ruotano alla stessa velocità; a frequenze diverse l'angolo fra i vettori cambierebbe di continuo e la rappresentazione perderebbe significato.
- *Perché il fattore di potenza è $\cos\varphi$*: nel triangolo delle potenze $P$ è il **cateto orizzontale** e $S$ l'**ipotenusa**, quindi $P/S = \cos\varphi$. E $S^2 = P^2 + Q^2$ — Pitagora: **$P + Q \neq S$**, ed è per questo che si scrivono in W, VAR, VA.

---

## 🔧 Minuti 43-56 · Protti: la sequenza, poi i sei errori

> [!check] La sequenza operativa — ripetila finché non esce da sola
> 1. **Leggi la traccia** e capisci cosa vuole, prima di toccare lo strumento.
> 2. **Decidi i punti di misura** — dove vanno le sonde — prima di accendere.
> 3. **Stima l'ordine di grandezza atteso.** (Se ti aspetti 1,2 V e leggi 12 V, non è il circuito: è la sonda.)
> 4. **Misura**: scala verticale, base tempi, trigger.
> 5. **Confronta col teorico.** Torna? Se no, riconsidera prima di dichiarare il risultato.
> 6. **Commenta ad alta voce cosa stai facendo e perché.** Alla pratica spiegare il procedimento è **metà del voto**.

**Le quattro misure, con le formule pronte:**

| Misura | Come |
|---|---|
| Tensione | divisioni × VOLTS/DIV = $V_{pp}$ → $V_p = V_{pp}/2$ → $V_{eff} = V_p/\sqrt{2}$ *(sinusoide pura)* |
| Frequenza | divisioni × TIME/DIV = $T$ → $f = 1/T$ |
| Sfasamento | $\Delta t$ fra i passaggi per lo zero **sullo stesso fronte** → $\varphi = 360° \cdot \Delta t / T$ |
| Frequenza di taglio | misura $G_0$ in banda passante, poi sposta $f$ finché l'uscita scende a $0{,}707\,G_0$ |

> [!danger] I sei errori che costano il punto
> 1. **Sonda ×10 e conti fatti in ×1** → leggi valori dieci volte più piccoli.
> 2. **Trigger su AUTO con segnale discontinuo** → l'immagine salta: passa a **NORMAL** e metti il LEVEL a metà ampiezza. *(Schermo nero in NORMAL? LEVEL fuori ampiezza, SLOPE invertito, SOURCE sul canale sbagliato, o COUPLING su AC con un segnale solo DC.)*
> 3. **Canali invertiti** ($V_{in}$ su Ch2 e $V_{out}$ su Ch1) → è il classico amplificatore con guadagno «inspiegabilmente» < 1.
> 4. **Dimenticare $V_{eff} = V_p/\sqrt{2}$** — e ricordarsi che vale **per le sinusoidi**.
> 5. **AC coupling su un segnale con offset** → l'oscilloscopio ti nasconde la continua e la forma d'onda ti mente. In dubbio: **DC**.
> 6. **C trattate come corto in DC** → in continua le **C sono circuiti aperti**.

> [!check] Prima di toccare qualsiasi cosa, tre domande
> Sonda in ×1 o ×10? · Coupling in DC? · Trigger su NORMAL col livello a metà ampiezza?

**Se il circuito è un raddrizzatore** (il caso più probabile, visto che il diodo è di entrambe le prove): oscilloscopio in **DC coupling** sull'uscita; senza $C$ vedi la doppia semionda con picco $V_{in,p} - 2V_D$; con $C$ la tensione sale a $\approx V_{in,p} - 2V_D$ e resta un **ripple** $\Delta V = I_{load}/(f_r C)$ con $f_r = 2f_{rete}$.

**Se è un amplificatore a BJT**: prima il **punto di lavoro DC** a segnale spento ($V_{CE} \approx V_{CC}/2$ in zona attiva), poi un segnale di **decine di mV**, poi $A_v = V_{out,pp}/V_{in,pp}$. Se l'uscita è **clippata** sopra o sotto, non sei più in zona attiva: **abbassa l'ingresso**, non alzare la scala.

Fonti lunghe, per dopo: [[03 - Prova Pratica Protti]] · [[L'oscilloscopio]] §4, §5, §7.

---

## ⚠️ Minuti 56-60 · Le trappole di parola, e come si risponde

> [!danger] Quattro scambi di termini che fanno crollare una risposta giusta
> 1. **$f$ [Hz]** vs **$\omega$ [rad/s]** — scambiarli dentro una dimostrazione la annulla.
> 2. **Impedenza** vs **reattanza** — l'impedenza è il **numero complesso** $\bar{Z} = R + jX$; la reattanza è **solo** la parte immaginaria $X$.
> 3. **Passa-basso** vs **soppressore di banda** — il primo taglia le alte, il secondo toglie **una banda specifica** (notch).
> 4. **Le zone del BJT sono AND di due condizioni** — attiva = B-E **ON** *e* B-C **inversa**; saturazione = **entrambe ON**; interdizione = **entrambe OFF**.
>
> E non dire «il transistor amplifica in tensione»: il modo primario è l'**amplificazione di corrente** — la piccola $I_B$ che comanda la grande $I_C$.

> [!success] Lo schema di ogni risposta, in quest'ordine
> **definizione → formula → disegno → esempio.**
> Se ti chiedono qualcosa che non sai, **non stare zitto**: parti dalla definizione di quello
> che sai e dillo. Sui suoi stessi fogli Carli dà punti alle **relazioni di partenza corrette**
> anche quando i conti dopo sono sbagliati — e i «non svolto» pesano più degli «errato».
> Vale a voce esattamente come sul foglio.

---

## Collegamenti

- [[02 - Prova Orale Carli]] — la struttura completa dell'orale, i tre livelli di domanda
- [[03 - Prova Pratica Protti]] — le cinque famiglie di prove pratiche
- [[04 - Verifica tipo Carli — Diodi]] — le 39 domande vere e la checklist dei 15 disegni
- [[Ripasso finale — FUSI e Diodi]] — Parte D: le risposte D1-D23 per esteso
- [[diodi-risposte]] — le stesse risposte in versione stampabile
- [[Formulario rapido#Parte A — Tabelle comparative (lookup 5 secondi)|Formulario rapido, Parte A]] — il cheat sheet da tenere aperto
- [[Calendario]] — il piano della giornata, ora per ora
