---
tags: [recupero, elettronica, hub, spiegazione-intuitiva, perche-ricorsivo, bambino-4-anni]
fonte: "compilazione didattica per il recupero: domande 'perché?' ricorsive su ogni concetto"
prove: [scritta, orale, pratica]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) per derivazione — file trasversale: è il commento intuitivo ai file di argomento, ciascuno verificato pagina per pagina sul Mirandola nei Lotti 1-13 della bonifica. Non contiene citazioni dirette del libro: dove serve il riferimento di pagina si va alla nota dell'argomento. Vedi «00 - Fonti e note» e «00 - Audit e correzioni»."
---

# 🧒 Spiegazione intuitiva (bambino di 4 anni) — HUB

> [!info] Scopo di questo file
> Ogni argomento del recupero (Carli scritto + orale, Protti pratica) viene qui **smontato in una catena di "perché?" ricorsivi**: cos'è → perché → perché ancora → perché ancora → ... → cosa c'entra con gli altri.
>
> Il libro Mirandola è ottimo ma presuppone che tu sappia "perché", e salta i passaggi intuitivi. Questo file ricostruisce quei passaggi, esattamente come se spiegassi a un bambino che continua a chiedere "perché?".
>
> **Come usarlo**: in [[Argomenti]], ogni file ha in cima un link a questo hub (`→ Vedi [[00 - Perchè (spiegazione intuitiva)]] §N`). Quando ti sei perso o non ti ricordi "perché funziona così?", apri la sezione corrispondente.

> [!tip] Regola di lettura
> Questo file **non sostituisce** la teoria di [[Argomenti]] — è un **complemento** per chi vuole capire, non solo ricordare. Il libro ha le formule; qui c'è l'intuizione. Spesso la risposta a un "perché?" è dentro un altro capitolo: i link `[[...]]` ti portano alle sezioni giuste.

---

## 0. Dal silicio al transistor (prerequisito atomico per §§7-10)

> [!info] Nota di apertura
> Questa sezione è il **prerequisito atomico** per [[Diodi]], [[BJT]], [[MOSFET]], [[JFET]]. Se non capisci la fisica di base (reticolo, drogaggio, bande, giunzione p-n), le sezioni §§7-10 ti sembreranno magia buona. Qui smonto la magia in tanti piccoli "perché?" , esattamente come le altre 13 sezioni del hub.

> [!tip] Come usarla
> È una **catena di "perché?" ricorsivi** sull'atomo di silicio, sul suo reticolo, sul drogaggio, sulla giunzione, e infine sul transistor a 3 regioni. Alla fine avrai capito **perché** esiste la barriera di 0,7 V, **perché** il silicio e non il germanio, **perché** servono 3 regioni per amplificare. Se una frase ti sembra troppo densa, ricomincia dal capoverso precedente — i "perché?" sono annidati, non paralleli.

---

> [!warning] Trasparenza fonti
> La fisica atomica di questa §0 (configurazione elettronica, reticolo covalente, bande di energia, drogaggio, giunzione p-n) non è verificabile nel libro Mirandola (PDF 152 pp scansionato SENZA OCR — vedi [[Prove/00 - Fonti e note]]). Le spiegazioni seguono prassi didattica standard (controllata su edutecnica.it e letteratura elettronica). Se devi portare un numero all’orale Carli, citane la fonte: è la fisica, non il libro.


**A. L'atomo grezzo: cos'è davvero un atomo di silicio**

> **Cos'è un atomo?** Un nucleo (protoni + neutroni) circondato da elettroni. I protoni sono carichi +, i neutroni neutri, gli elettroni carichi −. In un atomo neutro, protoni = elettroni. Il "**numero atomico Z**" è il numero di protoni, fissa l'identità chimica dell'elemento sulla tavola periodica.
>
> **Cos'è il silicio?** Un elemento con **Z=14**: 14 protoni nel nucleo, 14 elettroni che gli orbitano intorno (se neutro). È il secondo elemento più abbondante sulla crosta terrestre dopo l'ossigeno (la sabbia è biossido di silicio, SiO₂).
>
> **Perché Z=14 e non un altro numero?** Perché nella tavola periodica è il 14° elemento: ha 14 protoni nel nucleo. Cambia Z, cambia elemento. Z=6 → carbonio; Z=14 → silicio; Z=32 → germanio. Tre elementi **diversi**, ognuno con le sue proprietà.
>
> **Dove stanno i 14 elettroni?** Distribuiti su "gusci" (orbitali) a energie diverse: i primi 10 riempiono i gusci interni (1s², 2s², 2p⁶) come "core" stretto attorno al nucleo; gli ultimi 4 stanno nel guscio esterno (3s², 3p²) e sono quelli che fanno "chimica".
>
> **Perché i primi 10 sono "invisibili" ai fini dell'elettronica?** Perché stanno strtti attorno al nucleo (orbitali 1s, 2s, 2p), schermati e bloccati dal nucleo stesso. Non partecipano alle reazioni chimiche né al passaggio di carica. Sono solo "zavorra" interna.
>
> **Perché gli ultimi 4 sono "i protagonisti"?** Perché sono i più esterni (guscio 3), i più lontani dal nucleo, i più "mobili". Sono loro che fanno i **legami con gli atomi vicini** e che possono essere "strappati via" per diventare portatori di corrente.

---

**B. Il reticolo: come 10²³ atomi diventano un cristallo**

> **Cos'è un cristallo di silicio?** Un **reticolo** dove ogni atomo è legato a 4 vicini tramite **legami covalenti** → struttura **tetraedrica** ripetuta miliardi di volte (un cubetto di silicio da 1 cm³ contiene ~5·10²² atomi, tutti legati nella stessa geometria).
>
> **Perché 4 vicini?** Perché il silicio ha 4 elettroni di valenza → "vuole" completarne altri 4 per raggiungere la regola dell'ottetto (8 elettroni totali nel guscio esterno = stabilità massima). La soluzione geometrica elegante è circondarsi di 4 vicini: uno per ogni elettrone.
>
> **Cos'è un legame covalente?** Ogni atomo "mette sul piatto" 1 elettrone e il vicino ne mette un altro. I due elettroni vengono condivisi tra i due nuclei → formano una "nuvola" elettronica che **tiene insieme** i due atomi. Nessuno dei due "perde" l'elettrone (non diventa ione): lo **condividono**.
>
> **Perché "covalente" e non ionico?** Perché 4 elettroni di valenza sono un numero "neutro" che non permette di diventare né +4 né −4 strappando o donando: sarebbe troppo energeticamene costoso. La via d'uscita naturale è **condividere**, non trasferire. Per questo carbonio, silicio, germanio fanno **legami covalenti**, non ionici.
>
> **Cosa succede a T = 0 (zero assoluto)?** Tutti gli elettroni di valenza sono **perfettamente** congelati nei loro legami covalenti. Nessuno è libero. Il cristallo è un **isolante perfetto** (anche se apparentemente è solido!).
>
> **Cosa succede a T ambiente (es. 25 °C)?** L'agitazione termica "scuote" gli elettroni nei legami. **Ogni tanto** un elettrone riceve abbastanza "calcio termico" da liberarsi dal legame e vagare per il cristallo. Pochissimi in confronto al totale (~1 elettrone libero ogni 10¹² atomi). Sono **così pochi** che il silicio puro a T ambiente è quasi un isolante.

---

**C. Le bande di energia: perché pochi elettroni sono "liberi"**

> **Cos'è la banda di valenza?** L'**insieme di tutti gli orbitali 3s e 3p** dei miliardi di miliardi di atomi del cristallo. In un cristallo gli orbitali atomici **si fondono** in una banda continua di energie permesse. La banda di valenza è il "guscio esterno" del cristallo, dove stanno gli elettroni che fan legami covalenti.
>
> **Cos'è la banda di conduzione?** L'**insieme di orbitali vuoti** a energia leggermente superiore. È una "strada" dove gli elettroni possono muoversi liberamente senza essere legati a nessun atomo specifico → sono **portatori di corrente elettrica**.
>
> **Cos'è il band gap (gap proibito)?** L'**intervallo di energia VIETATO** che separa la banda di valenza da quella di conduzione. In questa zona di energia **non può stare nessun elettrone** (è vietata dalle leggi della meccanica quantistica). Per il silicio, il gap vale **1,12 eV** (elettronvolt).
>
> **Perché 1,12 eV e non un altro valore?** Perché è la "forza di gravità" specifica che il nucleo Z=14 esercita sui 4 elettroni più esterni, **schermata** dai 10 elettroni interni. È una proprietà del materiale, fissata dalla fisica quantistica del nucleo + elettroni. Cambiando elemento, cambia il gap.
>
> **Perché un isolante ha un gap enorme?** Perché gli elettroni sono così strettamente legati al nucleo che serve un'energia enorme (> 5 eV) per strappare uno solo. Esempio: il diamante (carbonio puro) ha gap ~5,5 eV → nessun elettrone libero a T ambiente → **isolante perfetto**.
>
> **Perché un conduttore metallico ha gap = 0?** Perché il nucleo metallico (es. rame Z=29) lega debolmente gli elettroni più esterni → le bande di valenza e conduzione si **sovrappongono** → gli elettroni sono già "liberi" a T=0 → conducono sempre. Per questo un filo di rame a T=0 ha già resistenza bassa.

---

**D. Perché il silicio è "il" semiconduttore**

> **Cos'è un semiconduttore?** Un materiale con **gap intermedio** (1–3 eV). A T = 0 è isolante (tutti gli elettroni sono "inchiodati" nei legami). A T ambiente, **un po'** di elettroni riescono a saltare il gap e diventare portatori. Non abbastanza da essere un conduttore, ma abbastanza da **essere controllabile**. È la **"via di mezzo"**.
>
> **Perché il silicio ha "vinto" tutto?** Perché ha 1,12 eV di gap → "perfetto" per applicazioni elettroniche: a T=0 isolante (nessuna perdita statica), a T ambiente pochissimi portatori termici (pochissima perdita), e si **drogano bene** controllando esattamente i portatori.
>
> **Perché non il germanio (Ge, Z=32)?** Perché ha gap più piccolo: 0,67 eV. A T ambiente ha **troppi** portatori termici → corrente di perdita → i transistor "perdevano" e si scaldavano da soli negli anni '50. Negli anni '60 il silicio ha soppiantato il germanio, tranne in applicazioni specifiche (rivelatori IR, alcuni circuiti vintage).
>
> **Perché il SiC (carburo di silicio) sta emergendo oggi?** Perché ha gap **3,26 eV**, enorme. A T ambiente gli elettroni termici sono quasi zero → **perdite bassissime** anche a tensioni e correnti alte → applicazioni di **potenza** (inverter per auto elettriche, ricarica veloce, alta tensione). Il "super-silicio".

---

**E. Il drogaggio: come ottenere portatori a comando**

> **Cos'è il drogaggio?** **Iniettare** nel cristallo di silicio puro **piccole quantità** (1 atomo drogante ogni 10⁶ atomi di silicio!) di un altro elemento, scelto per avere un elettrone di valenza **in più** o **in meno**. Risultato: il cristallo **non è più isolante** → conduce.
>
> **Perché serve il drogaggio?** Perché il silicio puro ha portatori in numero **non controllabile** e **troppo pochi** per farci un circuito. Il drogaggio **aumenta di milioni di volte** il numero di portatori e permette di **fissarlo** con precisione.
>
> **Perché drogare con il fosforo (P, Z=15)?** Perché il fosforo è del **gruppo 15** (5 elettroni di valenza → gruppo sotto al silicio gruppo 14 sulla tavola periodica). Quando un atomo di fosforo prende il posto di un silicio nel reticolo, fa **4 legami covalenti** con i vicini (come tutti) ma ha **1 elettrone in più** che **NON** entra nei legami → resta **libero** sulla banda di conduzione → portatore maggioritario.
>
> **Perché l'elettrone in più resta libero?** Perché non c'è un "posto legame" dove metterlo: i 4 vicini hanno già 4 elettroni da "legare". Il quinto è di troppo → vaga per il cristallo come un elettrone di conduzione → **portatore di tipo n** (n sta per "negativo", perché l'elettrone è −).
>
> **Cos'è il drogaggio di tipo p?** L'opposto: drogare con un elemento del **gruppo 13** (3 elettroni di valenza) come il **boro** (B, Z=5). Il boro prende il posto di un silicio ma fa solo **3 legami covalenti** col vicinato → al quarto legame **manca un elettrone** → **lacuna**.
>
> **Cos'è una lacuna?** Un "**posto vuoto**" nel reticolo dove "dovrebbe" esserci un elettrone di valenza per completare il quarto legame covalente. È un'**assenza**, non un oggetto fisico vero — ma si **comporta come una carica positiva mobile**.
>
> **Perché la lacuna si comporta come carica positiva?** Perché è un **buco in un mare di elettroni**. Quando l'elettrone del legame vicino si sposta a riempire la lacuna, il "buco" si sposta nella direzione opposta. Visto da fuori, il "buco" si muove come una pallina con carica + (è convenzione, in fisica si tratta come una **quasi-particella positiva**).
>
> **Perché le lacune sono più lente degli elettroni liberi?** Perché l'elettrone libero corre sulla banda di conduzione "vuota" senza ostacoli. La lacuna invece si sposta "a scatola cinese" nella banda di valenza piena: ogni spostamento è uno scambio di elettrone tra legami vicini, **più caotico**. La mobilità μ_p è circa **1/3** di μ_n (150 vs 450 cm²/V·s).
>
> **Cosa significa "tipo n" o "tipo p"?** Sono **etichette** che dicono chi sono i **portatori maggioritari**. Nel tipo n → elettroni. Nel tipo p → lacune (per analogia "positiva"). Il materiale drogato resta **globalmente neutro** (gli ioni droganti carichi compensano esattamente i portatori).
>
> **Cos'è un drogante "compensato"?** Se droghi con **sia** fosforo **sia** boro, si **cancellano** a vicenda. Per avere **drogaggio netto** serve un drogante in eccesso. Nei circuiti integrati le concentrazioni sono controllate al ppm per garantire precisione.

---

**F. La giunzione p-n: l'incontro che crea un muro**

> **Cos'è la giunzione p-n?** Il **confine fisico** tra una zona di silicio drogata p (ricca di lacune) e una zona drogata n (ricca di elettroni liberi). È il mattone fondamentale di **diodi, transistor, LED, fotodiodi, celle solari**.
>
> **Cosa succede appena le due zone si toccano?** Le lacune della zona p e gli elettroni della zona n cominciano a **diffondere** attraverso il confine (leggi statistiche: le particelle si muovono da dove sono in tanti a dove sono in pochi).
>
> **Cosa si incontrano al confine?** Elettrone dal lato n + lacuna dal lato p → si **ricombinano** (l'elettrone cade dentro la lacuna, completando un legame covalente, e **sparisce** come coppia mobile). Risultato: entrambi scompaiono.
>
> **Cosa resta al posto di portatori scomparsi?** **Ioni droganti scoperti**: atomi di fosforo che hanno perso l'elettrone libero (ora carichi **+**, fissi nel reticolo), atomi di boro che hanno perso la lacuna (ora carichi **−**, fissi nel reticolo). Si crea una **ZONA DI SVUOTAMENTO (depletion)** larga tipicamente **0,1–1 µm** dove ci sono ioni ma **non** ci sono portatori mobili.
>
> **Perché la diffusione si ferma?** Perché la zona depletion è carica (+ dal lato n, − dal lato p vicino al confine) → genera un **campo elettrico** che **respinge** ulteriore diffusione di portatori (e− respinto dal lato n+ negativi; lacune respinte dal lato p+ positivi). A un certo punto **campo elettrico = spinta statistica** → **equilibrio**.
>
> **Cos'è la barriera di potenziale (0,7 V)?** La **traduzione in volt** di quel campo elettrico. Per il silicio a 25 °C vale **~0,7 V** (per il germanio ~0,3 V, per il SiC ~3 V). È la tensione che un elettrone deve ricevere dall'esterno per **vincere** il campo e attraversare la giunzione.
>
> **Perché circa 0,7 V per il silicio? (versione pratica)** In pratica, $V_{bi} \approx 0{,}7$ V **per drogaggio moderato** (i drogaggi tipici dei circuiti integrati). Scende a ~0,5-0,6 V per drogaggio molto pesante (10¹⁸-10¹⁹ cm⁻³, le "soglie basse" dei diodi Zener). Sale a ~0,9-1,0 V per drogaggio leggero (i diodi raddrizzatori di segnale).
>
> **Per i curiosi (versione formula completa)**: $V_{bi} = (kT/q) \, \ln(N_a N_d / n_i^2)$ dove $N_a, N_d$ sono le concentrazioni di drogaggio p ed n, e $n_i$ è la concentrazione **intrinseca** del silicio (~10¹⁰ cm⁻³ a 25 °C, gli elettroni "liberi" presenti anche nel silicio puro). Non serve saperla a memoria per il compito Carli: ricorda solo 0,7 V come valore "di default" del silicio drogato moderatamente.
>
> **Perché il germanio ha barriera 0,3 V?** Perché ha gap **0,67 eV** (più piccolo → barriera più bassa). Per questo i primi diodi (1950) erano al germanio: erano più "gentili" (conducevano già a 0,3 V) ma "perdevano" molto (corrente inversa alta). Negli anni '60 il silicio ha vinto proprio perché 0,7 V è un **buon compromesso**.
>
> **Perché lo "Zener" usa la giunzione in breakdown?** Perché polarizzando la giunzione **in inversa** a tensione molto alta (~−5 V per uno Zener da 5 V), il campo elettrico è così forte che **strappa** gli elettroni dai legami covalenti → corrente inversa che sale. Il drogaggio è **forte e uniforme** → questa corrente è distribuita **su tutta la giunzione**, non concentrata → non brucia il componente. La $V_Z$ è stabile → si usa come **riferimento di tensione** (vedi [[Diodi]] §sui Zener).

---

**G. Dal diodo al transistor: perché servono 3 regioni**

> **Cos'è un transistor?** Un sandwich a **3 regioni** di semiconduttore drogato alternativamente: **NPN** o **PNP**. Il NPN ha una sottile fetta di tipo p in mezzo a due fette di tipo n; il PNP l'opposto. È il "mattone" fondamentale di amplificatori, interruttori, logica digitale.
>
> **Perché 3 regioni e non 2 (che farebbe un diodo)?** Perché servono **2 giunzioni in cascata** per poter **controllare** una grossa corrente con una piccola → effetto transistor (= "transfer resistor"). 1 giunzione = passa/non passa (diodo). 2 giunzioni interagenti = amplifica/interruttore.
>
> **Perché "transfer resistor"?** Storicamente: il nome venne dal fatto che una **piccola corrente** in un terminale (la base) "trasferisce" il controllo di una **grossa corrente** tra gli altri due (emettitore → collettore). Il transistor è un **resistore controllato da corrente** (BJT) o da tensione (FET).
>
> **Cos'è la giunzione B-E e la giunzione B-C?** Nel NPN: la prima giunzione è tra **base (p) ed emettitore (n)**, tipicamente **diretta** (polarizzata con $V_{BE} \approx 0{,}7$ V per farla condurre). La seconda è tra **base (p) e collettore (n)**, tipicamente **inversa** (polarizzata con $V_{BC}$ negativa). Insieme: **diretta + inversa** → flusso netto di elettroni.
>
> **Perché la base è STRATOSFERICAMENTE sottile (~µm)?** Perché gli elettroni iniettati dall'emettitore nella base devono **attraversarla senza quasi mai ricombinarsi** con le lacune della base (altrimenti sparirebbero). Più è sottile, meno tempo passano dentro, meno ricombinazioni → più elettroni arrivano al collettore → **β = I_C / I_B** più alto (tipicamente 100–300).
>
> **Perché non posso mettere due diodi back-to-back?** Perché tra i due diodi non avrei la **base sottile**: avrei due barriere di potenziale in serie (≈ 1,4 V) ma **senza l'effetto di pilotaggio**. Nessuno controllerebbe la corrente. Il transistor è l'**unico** modo di ottenere due giunzioni interagenti con la base sottile.
>
> **Come fa la base a "pilotare" la corrente?** Iniettando una piccola corrente $I_B$ → la giunzione B-E va in diretta → elettroni dall'emettitore fluiscono nella base → attraversano la base (sottile!) → arrivano al collettore → $I_C = \beta I_B$ → corrente **molto più grande** → **amplificazione**.
>
> **Perché β è "imperfetto"?** Perché alcuni elettroni si ricombinano nella base (anche se è sottile). β = 100–300 significa che su 100–300 elettroni che passano, **1** si ricombina in base. Il resto (99%) arriva al collettore. È un'efficienza "alta" ma non "totale".
>
> **Cos'è il FET (field-effect transistor)?** Un transistor **piloto in tensione**, non in corrente (a differenza del BJT). Invece di pilotare la corrente di base, si pilota un **campo elettrico** al gate che **modula** la sezione del canale di drain-source. Famiglie principali: **JFET** (gate con giunzione p-n, polarizzata in inversa) e **MOSFET** (gate isolato da strato di ossido).
>
> **Cosa cambia tra JFET e MOSFET?** Il **meccanismo di pilotaggio**:
> - **JFET**: gate si connette al canale tramite **giunzione p-n** (polarizzata in inversa) → il campo elettrico della depletion zone "strozzia" il canale.
> - **MOSFET**: gate è **isolato** da uno strato di **ossido** (~1 nm di SiO₂) → il gate "non tocca" mai il canale → pilotaggio **quasi senza corrente** (solo per caricare la capacità parassita).
>
> **Perché il MOSFET è dominante in elettronica digitale?** Perché:
> 1. Il pilotaggio è **senza corrente** → consumi statici bassissimi.
> 2. La struttura planare (gate-ossido-canale sopra-sotto) è facilissima da **integrare** in miliardi di transistor/centimetro quadrato.
> 3. Il pilotaggio serve solo a **caricare/scaricare** la capacità del gate (perdita $E = \frac{1}{2}CV^2$ a ogni commutazione).
>
> **Cosa c'entra con il resto?** Tutte le sezioni §§7-10 ([[Diodi]], [[BJT]], [[MOSFET]], [[JFET]]) **presuppongono** quanto spiegato qui: reticolo, drogaggio n/p, giunzione p-n, barriera di potenziale, tre regioni del transistor. Se qualcosa sotto ti sembra "magia", torna qui a leggere il sotto-blocco corrispondente.

---

---

## 1. Perché un segnale sinusoidale? ([[Segnali sinusoidali e fasori]])

> **Cos'è una sinusoide?** Una curva che oscilla avanti e indietro fra un valore massimo positivo e uno negativo, passando per lo zero, sempre nello stesso tempo.
>
> **Perché ci servono sinusoidi?** Perché la **rete elettrica di casa** le usa: 230 V a 50 Hz (Italia), 120 V a 60 Hz (USA), tutte sinusoidali. Se si vuole capire l'elettronica di potenza, bisogna partire da qui.
>
> **Perché proprio la sinusoidale?** Tre motivi storici e matematici:
> 1. I **generatori meccanici** (alternatori) producono naturalmente sinusoidi (rotazione uniforme → proiezione → seno).
> 2. La **somma di due sinusoidi** alla stessa frequenza è ancora una sinusoide alla stessa frequenza → linearità.
> 3. **Ogni** segnale periodico si può scomporre in **somma di sinusoidi** (Fourier): poter analizzare una sinusoide basta per analizzare *tutto*.
>
> **Perché la somma di sinusoidi è importante?** Perché una forma d'onda qualunque (onda quadra, dente di sega, perfino un singolo click) si può descrivere come una **ricetta**: "1 sinusoide a 1 kHz + 1 sinusoide a 3 kHz a un terzo dell'ampiezza + 1 sinusoide a 5 kHz a un quinto + ...". Studiare le sinusoidi significa poter descrivere *qualsiasi* segnale.
>
> **Perché proprio la sinusoidale?** (Motivo 4) **Perché la rotazione uniforme di una spira produce una sinusoide?** Perché la **legge di Faraday-Neumann-Lenz** dice che la tensione indotta è $V = -\frac{d\Phi}{dt}$, dove $\Phi$ è il flusso magnetico concatenato. Se una spira gira a velocità angolare costante in un campo magnetico uniforme, l'**area esposta** varia come $\cos(\omega t)$ (proiezione dell'area sulla perpendicolare al campo). La derivata di un coseno è un **seno**, moltiplicato per $\omega B A_{\max}$. Ecco perché escono sinusoidi dalla presa di casa — è Faraday meccanica.
>
> **Perché una rete in onde quadre sarebbe un disastro?** Perché un'onda quadra ha fronti **verticali** (derivata $dV/dt$ idealmente infinita). Dentro induttanze e trasformatori, $V = L \cdot di/dt$ → se la derivata è infinita, anche la tensione sarebbe idealmente infinita → **scariche sugli isolanti**, guasti a cascata, esplosioni nei trasformatori di distribuzione. La sinusoide ha derivata morbida ($dV/dt = \omega V_{\max}$), prevedibile, contenuta.
>
> **Cos'è un fasore?** Un **vettore** che rappresenta una sinusoide in modo compatto: l'angolo è la fase, la lunghezza è l'ampiezza. Quando la sinusoide "vibra" nel tempo, il fasore "ruota" in un diagramma.
>
> **Perché serve il fasore?** Perché se sommi/differenzi/deriv/integrali sinusoidi diventa un inferno di trigonometria. Con i fasori (numeri complessi) la derivata diventa una **moltiplicazione per $j\omega$**. Equazioni differenziali → equazioni di primo grado.
>
> **Perché ruota?** Perché una sinusoide $A\sin(\omega t + \varphi)$ si può descrivere come la proiezione (sull'asse y) di un vettore di lunghezza $A$ che ruota a velocità $\omega$ con posizione iniziale $\varphi$. Più facile da disegnare.
>
> **Perché $j$ (non $i$)?** Per non confondere $i$ (corrente) con $i$ (unità immaginaria). È solo una convenzione: in ingegneria $j$, in matematica $i$.
>
> **Perché $-j$ = "in ritardo di 90°"?** Perché $j$ moltiplicato per un fasore lo fa ruotare di $+90°$ in senso antiorario. $-j = \frac{1}{j}$ lo fa ruotare di $-90°$, cioè "in ritardo".
>
> **Cosa succede se la frequenza è zero?** Non c'è oscillazione, è una costante (DC). Il fasore diventa un numero reale (la tensione è costante).
>
> **Cosa succede se la frequenza è altissima?** Il periodo diventa piccolissimo, $T = 1/f$. Il fasore ruota velocissimo → diventa difficile da disegnare, ma la matematica funziona lo stesso.
>
> **Cosa c'entra con tutto il resto?** I fasori sono il **linguaggio** di tutto il capitolo AC. Impedenze, potenze, filtri, risonanza: tutti si esprimono in fasori.

---

## 2. Perché l'impedenza? ([[Impedenza dei bipoli R, L, C]])

> **Cos'è l'impedenza?** È una **resistenza "complessa"**: contiene un numero reale (quanto frena) + un numero immaginario (di quanto sfasamento). Si misura in ohm ($\Omega$) come la resistenza.
>
> **Perché non basta la resistenza?** Perché in AC il componente non si limita a **frenare** la corrente, ma può anche **sfasarla** (anticiparla o ritardarla). Serve un numero complesso per contenere due informazioni, non più solo una.
>
> **Cos'è il numero immaginario $j$?** È la radice di $-1$: $j^2 = -1$. Non esiste "fisicamente", ma serve come strumento matematico per descrivere rotazioni di 90°.
>
> **Perché serve $j$?** Perché se hai una tensione che **anticipa** di 90° la corrente, e moltiplichi per $j$ un fasore lo fai **ruotare** di 90°. Quindi $\bar{V} = j \cdot R \cdot \bar{I}$ significa "V anticipa I di 90°".
>
> **Perché $R$ non ha $j$?** Perché la resistenza è "pura": tensione e corrente sono in fase, nessuno sfasamento. La legge di Ohm è lineare: $V = R I$ senza effetti di memoria.
>
> **Perché $L$ ha $j\omega L$?** Perché l'induttore "accumula energia in un campo magnetico", e la tensione deve vincere la forza di questo campo per cambiare la corrente → è in **anticipo** di 90° rispetto alla corrente.
>
> **Perché l'anticipo di 90°?** È conseguenza della **derivata**: $v = L \, di/dt$. Derivare nel tempo = anticipare la fase di 90°. La costante $L$ moltiplica l'ampiezza della tensione. Insieme: $\bar{V} = j \omega L \bar{I}$.
>
> **Perché $\omega$?** Perché una derivata "pesa di più" se la funzione varia velocemente. Più alta è la frequenza, più rapidamente la corrente cambia, più tensione serve per starle dietro.
>
> **Perché proprio $\omega$ è quello che fa moltiplicare il "freno" dell'induttore?** Immagina l'induttore come una grossa ruota idraulica di mulino (la sua inerzia magnetica). Se fai scorrere l'acqua lentamente avanti e indietro (bassa $\omega$), la ruota ha tutto il tempo per girare e l'acqua passa. Ma se cerchi di invertire il flusso 500 volte al secondo (alta $\omega$), il peso morto della ruota diventa un muro di cemento invalicabile: ogni inversione trova la ruota ancora "impegnata" a girare nel senso opposto → blocco. Più veloce è il cambiamento, più "muro" fa l'induttore. Matematicamente: $X_L = \omega L$ cresce linearmente con $\omega$.
>
> **Perché $C$ ha $-j/\omega C$?** Perché il condensatore accumula energia in un campo elettrico, e **rilascia** la tensione solo DOPO che si è accumulata carica → la tensione è **in ritardo** di 90° rispetto alla corrente. Il $-j$ codifica proprio il "ritardo".
>
> **Cosa succede a $\omega = 0$ (DC)?** $L$ diventa **cortocircuito** ($X_L = 0$), $C$ diventa **circuito aperto** ($X_C = \infty$). Solo $R$ funziona come in continua.
>
> **Cosa succede a $\omega = \infty$?** $L$ diventa circuito aperto, $C$ diventa cortocircuito. Opposto esatto della DC. Questo crea i **filtri**.
>
> **Perché serie e parallelo funzionano come per le resistenze?** Perché l'impedenza è una **generalizzazione lineare** della resistenza: $[R, +]$ e $[1/R]$ funzionano a patto di essere sostituiti da $[\bar{Z}, +]$ e $[1/\bar{Z}]$. Perché la linearità (ohm + Kirchhoff) è indipendente dal fatto che $\bar{Z}$ sia complesso.
>
> **Ma perché le regole sono identiche al DC se qui la corrente va avanti e indietro tutto il tempo?** Immagina di camminare in due corridoi in serie pieni di fango (le impedenze). Sia che tu cammini sempre dritto, sia che tu faccia tre passi avanti e tre indietro tutto il giorno, devi comunque faticare attraverso la somma del calpestio di **entrambi** i corridoi. L'ostacolo totale non dipende da quale direzione prevale in quell'istante, ma da quanta "roba" fisica è messa in sequenza nel percorso. Stessa logica per il parallelo: due vicoli ciechi dove devi passare impedenza $\bar{Z}_1$ **e** $\bar{Z}_2$, la resistenza complessiva è quella "combinata" $1/(1/\bar{Z}_1 + 1/\bar{Z}_2)$. È linearità pura, indipendente dal fatto che il segnale oscilli.
>
> **Cosa c'entra con il resto?** L'impedenza è il blocco fondamentale per: filtri (cap. prossimo), calcolo di potenze, risonanza, amplificatori in AC.

---

## 3. Perché il metodo simbolico? ([[Il metodo simbolico]])

> **Cos'è?** Una procedura in 3-4 passi per analizzare circuiti AC sostituendo le sinusoidi con i loro fasori, così le equazioni differenziali diventano equazioni algebriche.
>
> **Perché serve?** Perché in AC le tensioni/correnti sono sinusoidali, e applicare Kirchhoff a seni/coseni trigonometrici è un incubo. Con i fasori diventa algebra lineare.
>
> **Perché funziona?** Per due motivi:
> 1. La **derivata di una sinusoide** è ancora una sinusoide (a parte fase e ampiezza).
> 2. **Derivare = moltiplicare per $j\omega$** — operazione lineare che si fa al volo sui fasori.
>
> **Qual è il limite n.1?** Funziona solo se **tutti** i generatori del circuito hanno la **stessa frequenza**. Se ne hai due a frequenze diverse, i fasori ruotano a velocità diverse → non puoi sommarli in un diagramma fermo.
>
> **Qual è il limite n.2?** Funziona in **regime stazionario**, non durante i transitori (accensione del circuito, commutazione di interruttori). Per i transitori serve Laplace.
>
> **Procedura tipo**: 1) Converti tutte le tensioni/correnti in fasori. 2) Converti $L$ e $C$ in impedenze. 3) Scrivi e risolvi le equazioni di Kirchhoff in $\bar{V}$ e $\bar{I}$. 4) Se serve, riconverti in sinusoidi.
>
> **Perché riconvertire alla fine?** Perché la risposta in fasori è matematicamente completa, ma l'oscilloscopio ti mostra sinusoidi. Per ottenere il segno, l'ampiezza, il tempo — riconverti.
>
> **Cosa c'entra con il resto?** È il metodo generale per risolvere **tutti** gli esercizi AC. Lo userai per impedenze, potenze, filtri, risonanza.

> **Perché i diagrammi vettoriali funzionano?** Perché la matematica dei fasori è identica a quella dei vettori: si sommano "punta-coda", si scompongono in parte reale/immaginaria. Disegnarli permette di visualizzare le relazioni di fase a colpo d'occhio, senza calcoli trigonometrici.
>
> **Perché si può passare da sinusoidi a fasori e ritorno senza perdere informazione?** Perché un fasore contiene **due** parametri (modulo + fase) che codificano esattamente i due parametri della sinusoide (ampiezza + fase iniziale). La frequenza è informazione "esterna" al fasore (nota a priori perché i generatori del circuito sono isofrequenziali).
>
> **Perché a volte si usano i numeri complessi in forma rettangolare e a volte polare?** Rettangolare ($a + jb$): per **somme** di tensioni/correnti (parti reali e immaginarie separate → comodo per Kirchhoff). Polare ($V\angle\varphi$): per **prodotti/quozienti** (moltiplicare moduli, sommare argomenti → comodo per calcolare $\bar{V} = \bar{Z}\bar{I}$). Conversione con $\arctan$ e $\sqrt{a^2+b^2}$.

---

## 4. Perché tre potenze? ([[Le potenze in alternata]])

> **Cos'è la potenza attiva $P$?** L'energia che il bipolo **consuma davvero**: si trasforma in calore, in lavoro meccanico, in luce. Si misura in **W**.
>
> **Cos'è la potenza reattiva $Q$?** L'energia che va e **torna indietro**: il bipolo la riceve e poi la restituisce. Nessun consumo netto. Si misura in **VAR** (Volt-Ampere Reattivi) — apparentemente è una potenza, ma non consuma.
>
> **Cos'è la potenza apparente $S$?** Il **prodotto di V per I** senza considerare la fase. È la "potenza lorda" che la linea deve trasportare. Si misura in **VA**.
>
> **Perché tre misure?** Perché il segno di $\varphi$ (tra V e I) determina se l'energia è "consumata" o solo "scambiata". Serve un numero che distingua i due casi:
> - $P$ è la parte che **resta** nel bipolo.
> - $Q$ è la parte che **oscilla**.
> - $S$ è la dimensione "ingombrante" del trasporto.
>
> **Perché $P + Q \neq S$?** Perché $P$ e $Q$ sono **ortogonali** (perpendicolari nel "triangolo delle potenze"): la loro somma **vettoriale** è $S = \sqrt{P^2 + Q^2}$, non la somma aritmetica. W, VAR e VA sembrano unità simili, ma non si sommano direttamente.
>
> **Ma perché fisicamente sono ad angolo retto?** Immagina di spingere su una salita ripida uno zaino pesante attaccato a una fune **elastica**. La forza che spendi per far salire lo zaino verso la vetta è **$P$** (lavoro utile in avanti). Quella che invece fa rimbalzare lo zaino su e giù a causa dell'elastico, senza spostarlo di un metro in avanti verso la meta, è **$Q$**. Moto "di rimbalzo" (su/giù) e moto "in avanzamento" (avanti) viaggiano su **dimensioni perpendicolari**: ecco perché non puoi sommarli col segno "+". Serve la somma vettoriale (Pitagora: $S^2 = P^2 + Q^2$).
>
> **Cos'è $\cos\varphi$?** È il **fattore di potenza**: $P / S$. È anche lo sfasamento tra V e I. $\cos\varphi = 1$ ⇒ $V$ e $I$ in fase (solo resistenza); $\cos\varphi = 0$ ⇒ $V$ e $I$ in quadratura (solo reattanza).
>
> **Perché si chiama proprio "coseno" e non "seno" o altro?** Torniamo allo zaino in salita: la fatica totale ($S$) è l'**ipotenusa** nel triangolo delle potenze, che "punta" lungo la salita con un certo angolo $\varphi$ rispetto all'orizzontale. La trigonometria ci dice che l'**ombra proiettata a terra** sul piano dell'avanzamento dritto ($P$) vale ipotenusa × coseno dell'angolo: $P = S \cdot \cos\varphi$. Più $\cos\varphi$ è vicino a 1, più l'angolo è "schiacciato" e tutta la tua fatica è rivolta in avanti (lavoro utile). Più è vicino a 0, più l'angolo è verticale e la tua fatica è quasi solo rimbalzo ($Q$ domina).
>
> **Cos'è il rifasamento?** L'azione di **installare condensatori** in parallelo al carico per **annullare la $Q$** induttiva. Risultato: $I$ totale cala, la linea trasporta meno corrente, le perdite ohmiche della linea diminuiscono.
>
> **Ma come fa un condensatore ad "annullare" un induttore fisicamente, senza toccarlo?** Immagina l'induttore come una persona che, su una barca che dondola, **si alza** quando l'onda sale e **si accuccia** quando l'onda scende, facendo rollare la barca da mal di mare. Mettendo un condensatore in parallelo installi un "passeggero opposto" che fa *esattamente* i movimenti **invertiti** in sincronia: si accuccia quando l'altro si alza, e viceversa. L'effetto combinato dei due si elide perfettamente: la barca smette di rollare, e il motore (la linea elettrica della rete) non deve più faticare per stabilizzarla. Risultato: la linea trasporta meno corrente totale.
>
> **Perché lo fa la compagnia elettrica?** Perché la $Q$ che circola non le dà soldi (non viene "consumata"), ma le fa perdere soldi (perdite sulla linea). Il rifasamento obbligatorio sulle utenze industriali è un modo per far pagare le perdite di linea.
>
> **Cos'è il trifase?** Una distribuzione di potenza con **3 fili** invece di 2, sfasati di 120°. Il vantaggio: si può trasmettere più potenza con meno cavi. Il trifase di potenza è la spina "industriale" che si vede nelle officine.
>
> **Cosa c'entra con il resto?** Le potenze AC sono richieste praticamente in OGNI esercizio della Carli scritta. Senza conoscerle, non risolvi gli esercizi con $\bar{Z}$ e $\varphi$.

---

## 5. Perché risonanza? ([[Reti RLC e risonanza]])

> **Cos'è la risonanza?** Una frequenza $\omega_0 = 1/\sqrt{LC}$ alla quale un circuito RLC diventa **puramente resistivo**: $X_L + X_C = 0$, e quindi $\varphi = 0$.
>
> **Perché succede?** Perché a una certa frequenza $X_L = \omega L$ (che cresce con $\omega$) eguaglia $X_C = 1/\omega C$ (che decresce con $\omega$). A quel punto, le due si annullano a vicenda.
>
> **Perché il valore $\omega_0$?** Perché è il valore in cui $X_L = X_C$:
> $$\omega_0 L = \frac{1}{\omega_0 C} \quad\Rightarrow\quad \omega_0^2 = \frac{1}{LC} \quad\Rightarrow\quad \omega_0 = \frac{1}{\sqrt{LC}}$$
>
> **Perché proprio quel valore cancella tutto, fisicamente?** Immagina una bimba su un'altalena di lunghezza $L$ fissata a un supporto "soffice" di elasticità $1/C$. Se la spingi a casaccio (frequenze fuori $\omega_0$), la bimba si limita a ondeggiare in malo modo senza prendere il ritmo. Ma se la spingi **nel momento esatto** e **al ritmo perfetto** del suo pendolo naturale (quello è $\omega_0 = 1/\sqrt{LC}$), ogni spinta aggiunge energia che si accumula → l'altalena vola in alto! A quel punto la "forza" dell'inerzia ($L$) e la "forza" dell'elasticità ($C$) si equivalgono esattamente in **opposizione di fase**, e non c'è più resistenza netta al moto oscillatorio: tutto procede al massimo dell'efficienza. $L$ grande = bimba pesante = altalena lenta. $C$ grande = catenelle elastiche = altalena lenta. Per andare veloce servono entrambi piccoli.
>
> **Cos'è Q-factor?** Il **fattore di merito** del circuito risonante: $Q = \omega_0 L / R$ (serie). Misura quanto "streita" e "alta" è la curva di risonanza:
> - $Q$ alto = curva stretta e alta (selettivo, sensibile a piccole variazioni di $\omega$).
> - $Q$ basso = curva larga e bassa (poco selettivo, smorza molto).
>
> **Perché il Q-factor fa diventare il picco "appuntito" rispetto alla resistenza base?** Torna alla bimba sull'altalena. Se i ganci del dondolo sono arrugginiti (alta $R$ = basso $Q$), l'attrito continuo **frena subito** lo slancio del pendolo: le oscillazioni decadono velocemente, la curva di risonanza è larga e bassa. Se pulisci e olli i cardini (bassa $R$ = alto $Q$), l'altalena vola in alto con oscillazioni che durano a lungo; la curva diventa strettissima e altissima, e l'altalena "ignora" le spinte a frequenze vicine ma non uguali a $\omega_0$ → super selettiva. In elettronica: $Q$ alto = ricevitore radio che isola stazioni adiacenti, $Q$ basso = equalizzatore audio che copre una banda larga.
>
> **Perché $Q$ conta in pratica?** Perché sintonizzare una radio, isolare una frequenza in un equalizzatore, costruire un oscillatore (orologio al quarzo!) **tutti richiedono** $Q$ alto.
>
> **Serie vs parallelo RLC**:
> - **Serie**: a $\omega_0$ l'impedenza è **minima** (= $R$), la corrente è **massima**. Tensione ai capi di $L$ o $C$ = $Q \cdot V_{\text{totale}}$. Può essere alto!
> - **Parallelo**: a $\omega_0$ l'impedenza è **massima** (= $R$), la tensione di uscita è **massima**. Corrente in $L$ o $C$ = $Q \cdot I_{\text{totale}}$.
>
> **Perché $V_L$ (o $V_C$) può essere molto alta in serie a risonanza?** Perché $L$ e $C$ hanno impedenze che si cancellano ma tensioni che si sommano (perché sono sfasate di 180° tra loro). Risultato: tensioni alte ai capi dei componenti reattivi anche se la tensione totale è piccola. Fenomeno pericoloso se il $Q$ è alto.
>
> **Cos'è la banda passante?** L'intervallo di frequenze attorno a $\omega_0$ in cui la potenza dissipata è almeno metà del massimo. Larghezza: $BW = \omega_0 / Q$.
>
> **Perché la banda passante è inversamente proporzionale a Q?** Matematicamente: se il picco è alto e stretto (Q alto), allora per "allargare" la base fino a $-3$ dB devi muoverti di poco sull'asse $\omega$ — la banda è stretta. Se il picco è basso e largo (Q basso), ti devi muovere di molto per scendere a metà potenza — la banda è larga. La relazione inversa $BW = \omega_0/Q$ lo cattura: prodotto $BW \cdot Q$ è costante = $\omega_0$.
>
> **Quando Q alto NON è desiderabile?** In molte applicazioni audio (equalizzatore, crossover, filtri anti-aliasing) serve una banda **larga** che copra l'intera gamma udibile (20 Hz–20 kHz) o che attenui gradualmente su un'ottava. In questi casi Q basso (~0,7 per Butterworth) è preferibile: curva dolce, nessun picco risonante che "colorerebbe" il suono. Anche nei **filtri anti-aliasing** prima di un ADC vuoi Q basso per evitare oscillazioni spurie nella banda utile. In sintesi: $Q$ alto = "super selettivo, isolo solo $\omega_0$" (radio, oscillatori); $Q$ basso = "dolce e largo, non coloro" (audio, processing).
>
> **Cosa c'entra con il resto?** I filtri passa-banda sono circuiti risonanti. Anche i "notch filter" (elimina-banda) usano risonanza. La risonanza è il cuore della sintonia di frequenza.

---

## 6. Perché un filtro? ([[Filtri passivi del primo ordine]])

> **Cos'è un filtro?** Un quadripolo che **lascia passare** alcune frequenze e ne **attanua** altre.
>
> **Perché serve?** Perché nel mondo reale i segnali sono "sporchi": un'onda quadra è idealmente alla frequenza principale $f$, ma porta con sé infinite armoniche superiori. Se vuoi solo la componente principale (es. per demodulare un segnale audio), ti serve un filtro passa-basso.
>
> **Perché "filtro" passa-basso?** Perché le basse frequenze passano, le alte vengono bloccate.
>
> **Cos'è la frequenza di taglio $f_t$?** La frequenza a cui il guadagno scende a $1/\sqrt{2}$ = 0.707 del valore in banda. Convenzionalmente, è dove **potenza** dimezza $\Rightarrow -3$ dB.
>
> **Perché $-3$ dB?** Perché $20\log_{10}(1/\sqrt{2}) = -3$ dB. È una convenzione numerica comoda.
>
> **Ma perché proprio "metà potenza" come confine del filtro?** Pensa ai fari di un'auto immersi via via in una nebbia fitta ad alta "frequenza luminosa". L'occhio è adattivo: a un calo del 10% dell'intensità non ti accorgi di nulla. Ma quando la potenza luminosa scende all'esatta metà dell'originale (esattamente $-3$ dB), il tuo occhio comincia a percepire distinta la differenza tra "vedo accettabilmente" e "non vedo più". È il confine naturale della percezione umana (legge di Weber-Fechner). In elettronica abbiamo adottato la stessa soglia psicologica come **convenzione tecnica** per dire "fino a qui il filtro passa, da qui in poi attenua": comodo, riproducibile, e corrisponde a un'interpretazione soggettiva intuitiva di "sufficiente / insufficiente".
>
> **Perché RC fa un passa-basso?** Perché la C **blocca le alte frequenze** (a $\omega\to\infty$, $C$ → cortocircuito verso massa, l'uscita va a 0). Mentre la R "frena" la corrente. Insieme, fanno un partitore di tensione dipendente dalla frequenza.
>
> **Ma perché invertendo la posizione di R e C si inverte anche il comportamento?** Immagina la linea elettrica come un tubo dell'acqua. Se il condensatore è montato **trasversalmente** (tra linea e massa), apre uno "scarico istantaneo verso il tombino" solo quando l'acqua sbatte verso destra e sinistra molto rapidamente (alte frequenze): cade rapida a terra, e verso casa tua fluirà solo l'acqua flemmatica delle basse frequenze = passa-basso. Se invece metti il condensatore **in serie** sul tubo (muro nel bel mezzo del tubo), l'unica roba che ha energia sufficiente per spingere contro il muro è quella che vibra velocemente (alte frequenze): le alte passano, le basse si fermano contro il muro di capacità = **passa-alto**. Solo la posizione conta, non il valore di C!
>
> **Perché in serie a un segnale AC è diverso che in DC?** Perché $C$ cambia impedenza con la frequenza. In DC è circuito aperto (impedenza infinita), in AC ad alta frequenza è cortocircuito.
>
> **Perché $f_t = 1/(2\pi RC)$?** Perché è la frequenza a cui $|Z_C| = R$: a quel punto, la caduta di tensione è equamente divisa fra $R$ e $C$. La matematica è: $\omega RC = 1 \Rightarrow \omega = 1/(RC) \Rightarrow f = \omega/(2\pi) = 1/(2\pi RC)$.
>
> **Perché passa-alto invece passa-basso quando inverti $R$ e $C$?** Perché se la $C$ è in serie (al posto di $R$), blocca le basse (DC) e fa passare le alte ($C$ diventa cortocircuito a $\omega\to\infty$).
>
> **Perché $f_t = R/(2\pi L)$ per RL?** Perché $\tau = L/R$, e l'analogo di $\omega RC$ è $\omega L/R$. È "l'inverso matematico" di RC.
>
> **Cosa c'entra con il resto?** I filtri sono usati **dappertutto**: alimentatori (filtro C sul raddrizzatore → tensione "pulita"), crossover audio (passa-alto per tweeter, passa-basso per woofer), radio (passa-banda stretto per selezionare una stazione).

---

## 7. Perché un diodo? ([[Diodi]])

> **Cos'è un diodo?** Un componente a 2 terminali che **conduce in un solo verso**: l'anodo (+) al catodo (−) → conduce; al contrario → blocca.
>
> **Perché serve?** Per "raddrizzare" l'AC in DC (alimentatori), per "segnale" (modulatori, rivelatori), per protezione (diodi di libera circolazione sui relé), per logica (OR, AND a diodi).
>
> **Perché conduce in un solo verso?** Perché è una **giunzione p-n**: due pezzi di semiconduttore drogati in modo diverso. Nella zona di contatto si crea una **barriera di potenziale** (~0,7 V). Senza polarizzazione esterna, questa barriera "impedisce" ai portatori di passare da una parte all'altra.
>
> **Cos'è la barriera?** È un campo elettrico naturale generato dalla differenza di concentrazione di portatori (elettroni in eccesso nella zona n, lacune in eccesso nella zona p). Gli elettroni del lato n tendono a diffondere verso il lato p, ma si fermano alla giunzione perché si crea un campo opposto che li blocca.
>
> **Perché 0,7 V?** Perché è la differenza di potenziale che serve per vincere la barriera. Per il silicio è ≈ 0,7 V; per il germanio ≈ 0,3 V. Per il "diodo ideale", instructionalmente, $V_\gamma = 0$.
>
> **Perché proprio 0,7 V e non 1 V o 0,5 V?** Dipende dal **materiale**: è l'energia esatta che serve per strappare un elettrone dai legami cristallini specifici del silicio e spingerlo fisicamente nella regione di svuotamento (la "depletion zone") al centro della giunzione. Il germanio ha legami più deboli (≈ 0,3 V), il carburo di silicio (SiC) più forti (≈ 3 V). È una costante di natura, la misuri al laboratorio per confermarla.
>
> **Cosa succede quando V supera 0,7 V?** La barriera è vinta, gli elettroni passano, il diodo conduce. La tensione ai capi resta ~0,7 V (per il silicio) indipendentemente dalla corrente che scorre (entro la zona attiva).
>
> **Cosa succede se V è negativo (inversa)?** La barriera si alza ancora di più, gli elettroni non passano. Scorre solo una corrente **piccolissima** (~nA o μA) di portatori "generati termicamente".
>
> **Cosa succede se V è TROPPO negativo?** Si arriva alla **tensione di breakdown** $V_{BR}$. A quel punto il diodo "rompe" la barriera inversa → conduce forte in inversa. In un diodo normale questo è **distruttivo**, in uno **Zener** è la modalità di funzionamento.
>
> **Perché il breakdown distrugge un diodo normale ma non uno Zener?** In un diodo normale il breakdown si concentra in pochi punti microscopici del cristallo (dovuti a difetti di reticolo, impurità): tutta la potenza si focalizza lì, fonde localmente il silicio come un raggio laser in miniatura → corto circuito distruttivo. Lo Zener è progettato con drogaggio uniforme e controllato, in modo che il breakdown si distribuisca su **tutta la larghezza della giunzione**: può dissipare la potenza termicamente senza bruciarsi.
>
> **Cos'è uno Zener?** Un diodo **progettato** per lavorare nella zona di breakdown senza rompersi. La tensione di breakdown ($V_Z$, da pochi V a ~200 V) è una caratteristica fissa del componente, usata come **riferimento di tensione** per stabilizzatori.
>
> **Perché uno Zener stabilizza?** Perché la tensione ai suoi capi rimane ≈ $V_Z$ anche se la corrente che lo attraversa varia (entro certi limiti). È una "batteria di tensione" non ricaricabile.
>
> **Perché il ponte di Graetz usa 4 diodi?** Per rettificare **entrambe** le semionde di un segnale AC. Due diodi conducono su una semionda, gli altri due sull'altra semionda — sempre nello stesso verso verso il carico.
>
> **Cosa c'entra con il resto?** I diodi sono il primo componente **non-lineare** nel percorso. Sono il fondamento di alimentatori, rivelatori, modulatori, logica a diodi (DL), regolatori Zener. La giunzione p-n è anche dentro al BJT (la base-emettitore è una giunzione!).

---

## 8. Perché un transistor BJT? ([[BJT]])

> **Cos'è un BJT?** Un transistor con **3 regioni** di semiconduttore (NPN o PNP), che fa da **amplificatore** o da **interruttore**.
>
> **Perché "bipolare"?** Perché usa **due tipi** di portatori: elettroni (maggioritari nella n) e lacune (maggioritarie nella p). Il MOSFET, invece, usa un solo tipo.
>
> **Perché "transistor"?** Dal latino "transfer + resistor": è un resistore controllato da un altro segnale (la base). Storicamente, il primo dispositivo che poteva "trasferire" la resistenza da un circuito a un altro.
>
> **Cos'è la base (B)?** Il terminale di **comando**, sottile fisicamente. Una piccola corrente $I_B$ lo attraversa.
>
> **Cos'è l'emettitore (E)?** Il terminale che "emette" portatori (elettroni in NPN) verso il collettore.
>
> **Cos'è il collettore (C)?** Il terminale che **raccoglie** i portatori provenienti dall'emettitore.
>
> **Perché $\beta = I_C / I_B$?** Perché la base è sottile, quindi la maggior parte dei portatori dell'emettitore **non si ricombina** nella base ma passa al collettore. Tipicamente 100-300 ne passa 1 che si ricombina. Il $\beta$ misura l'efficienza di questo passaggio.
>
> **Perché tre regioni?** Perché servono **due giunzioni p-n in cascata**: B-E (diretta) per iniettare portatori, B-C (inversa) per raccoglierli. La base è la zona "comune" fra le due giunzioni.
>
> **Perché la base è sottile?** Per **minimizzare la ricombinazione**. Più è sottile la base, meno tempo i portatori passano dentro, meno possibilità di ricombinarsi → $\beta$ più alto.
>
> **Cos'è la zona attiva?** Quando la giunzione B-E è **diretta** (circola corrente) e la B-C è **inversa** (non circola). In questa zona, $I_C = \beta I_B$ vale.
>
> **Cos'è la saturazione?** Quando **entrambe** le giunzioni sono dirette. Il transistor si comporta come un **interruttore chiuso**: $V_{CE} \approx 0{,}2$ V, $I_C$ limitato dal circuito esterno.
>
> **Cos'è l'interdizione?** Quando **entrambe** le giunzioni sono inverse. Il transistor è **aperto**: $I_C \approx 0$, $V_{CE} \approx V_{CC}$.
>
> **Perché serve la polarizzazione?** Per "posizionare" il transistor nel punto di lavoro in **zona attiva** con il Q-point giusto. Senza polarizzazione, il transistor è o OFF (interdizione) o saturo al limite.
>
> **Perché in zona attiva $V_{BE} \approx 0{,}7$ V?** Perché la giunzione B-E **è un diodo**, e in un diodo di silicio la tensione diretta è ~0,7 V.
>
> **Cosa succede se $\beta$ varia con la temperatura?** Il Q-point si sposta → il transistor può andare fuori zona attiva. Soluzione: polarizzazione con partitore + resistenza di emettitore (che "stabilizza" il punto).
>
> **Cosa c'entra con il resto?** Il BJT è il blocco fondamentale degli **amplificatori** (capitolo successivo) e degli **interruttori** (in elettronica digitale TTL).

---

## 9. Perché un MOSFET? ([[MOSFET]])

> **Cos'è?** Un transistor a **effetto di campo** con **gate isolato** da uno strato di ossido. La tensione $V_{GS}$ controlla la corrente $I_D$.
>
> **Perché un nome così?** Metal-Oxide-Semiconductor FET: la struttura fisica è: metallo del gate → strato di ossido → semiconduttore del canale.
>
> **Cos'è l'isolamento del gate?** Lo strato di ossido (~1 nm) **impedisce** il passaggio di corrente tra gate e canale. Risultato: la corrente di pilotaggio è praticamente **zero** (solo qualche pA di leakage).
>
> **Perché questo è importante?** Perché significa che il pilotaggio del MOSFET è **istantaneo** e **gratis**: la corrente di gate è 0, quindi la potenza di pilotaggio è 0. Perfetto per il digitale (milioni di transistor in un chip, ma il pilotaggio non consuma potenza statica).
>
> **Ma allora perché le CPU scottano da fondere se il pilotaggio è gratis?** È gratis **solo a regime statico**: se il gate sta fermo a una certa tensione, davvero non scorre corrente e non si dissipa nulla. Ma il **gate è un condensatore** (due piastre affacciate separate dall'ossido, capacità parassita ~pF). Per accenderlo (portarlo oltre $V_{th}$), devi **violentemente riempirlo** di carica; per spegnerlo, devi **svuotarlo**. In una CPU che commuta 3 miliardi di volte al secondo, stai facendo miliardi di "secchiate" avanti e indietro: quell'andirivieni di carica ha un costo energetico $E = \frac{1}{2} C V^2$ per commutazione, dissipato come calore. Più GHz, più MOSFET attivi, più calore. Il "gratis" è solo in stasi; il "dinamico" è ciò che scalda i processori.
>
> **Cos'è $V_{th}$ (tensione di soglia)?** La $V_{GS}$ minima per cui il canale si "forma" e il MOSFET inizia a condurre. Tipicamente 1-4 V per MOSFET enhancement n.
>
> **Cos'è $K$ (parametro di transconduttanza)?** Il coefficiente che lega $I_D$ a $(V_{GS} - V_{th})^2$. Tipicamente $K$ in mA/V². È una caratteristica del componente specifico.
>
> **Cos'è la parabolica $I_D = K (V_{GS} - V_{th})^2$?** Descrive la corrente di drain in funzione della tensione di gate, in **saturazione**. Parabolica perché (più $V_{GS}$ - $V_{th}$) = "più canale conduttivo sotto il gate" = più portatori = più corrente. La dipendenza è quadratica (non lineare!).
>
> **Perché parabolica e non lineare?** Viene dalla fisica: l'accumulo di portatori sotto l'ossido è lineare in $V_{GS}$, ma la mobilità dipende dal campo elettrico → quadratico.
>
> **Cos'è "enhancement"?** Vuol dire che a $V_{GS} = 0$ **non c'è canale**: bisogna "migliorare" (enhance) la conduzione applicando $V_{GS}$ positiva.
>
> **Cos'è "depletion"?** Al contrario: a $V_{GS} = 0$ il canale **esiste già** (il MOSFET conduce), e serve $V_{GS}$ **negativa** per "svuotarlo" (depletion = svuotamento).
>
> **Cos'è la regione di saturazione del MOSFET?** Quando $V_{DS}$ è abbastanza alto ($V_{DS} > V_{GS} - V_{th}$), la corrente $I_D$ è "schiacciata" e dipende solo da $V_{GS}$, non da $V_{DS}$. È la zona dove il MOSFET **amplifica**.
>
> **Perché diversa dalla saturazione del BJT?** Nel BJT, saturazione = $V_{CE}$ collassa (~0,2 V) = transistor ON. Nel MOSFET, saturazione = "corrente costante con $V_{DS}$" = zona attiva = transistor amplifica → concetti opposti!
>
> **Perché i due significati sono opposti?** Nel MOSFET, "saturazione" significa che il **canale** sotto il gate è stato compresso (pinch-off parziale) dal campo elettrico di $V_{DS}$. Il "rubinetto" del canale è stato stretto: l'acqua (la corrente) non può più scorrere liberamente per quanto alta sia la pressione a valle ($V_{DS}$). Resta costante e dipende solo da $V_{GS}$ — come un rubinetto con una strozzatura fissa che eroga sempre la stessa portata a prescindere dalla pressione. Ecco perché da quel regime puoi fare **amplificazione lineare**: piccoli $\Delta V_{GS}$ → piccoli $\Delta I_D$ → amplificazione. Nel BJT, "saturazione" = il transistor è **completamente ON** (rubinetto tutto aperto, $V_{CE}$ collassa): il nome "saturazione" nei due transistor fu scelto per ragioni storiche opposte, è solo una fastidiosa **omonimia** di due fisici del secolo scorso. Ricordala con un bigliettino mentale: "**MOSFET satura = amplifica**, **BJT satura = ON fisico**".
>
> **Cos'è la regione triodo (lineare)?** Quando $V_{DS}$ è piccolo ($V_{DS} < V_{GS} - V_{th}$), il MOSFET si comporta da **resistenza** $R_{DS}$ controllata da $V_{GS}$. È la zona "switch ON per davvero" (resistenza bassa = interruttore chiuso).
>
> **Perché il MOSFET è dominante in elettronica digitale?** Perché è **facilissimo da integrare**: le geometrie sono ripetitive, il pilotaggio è senza corrente, il consumo statico è zero. Miliardi di MOSFET CMOS in un processore.
>
> **Cosa c'entra con il resto?** Il MOSFET è il fratello "moderno" del BJT. Pilota in tensione (= logica CMOS facile). In elettronica di potenza switching, MOSFET e IGBT dominano (perdite minori a commutazione).

---

## 10. Perché un JFET? ([[JFET]])

> **Cos'è?** Un transistor a **effetto di campo a giunzione**: gate connesso al canale tramite una **giunzione p-n** (polarizzata in inversa).
>
> **Perché "junction"?** Perché il gate è connesso al canale **tramite una giunzione**, non tramite un ossido come il MOSFET.
>
> **Cos'è $V_P$ (pinch-off)?** La tensione $V_{GS}$ (negativa nel JFET n) alla quale il canale è "strozzato" completamente. Per $V_{GS} \le V_P$, $I_D = 0$.
>
> **Ma come fa una tensione "negativa" (VGS) a strozzare fisicamente il canale?** Immagina il canale centrale N come un morbido tubo di gomma gonfiabile da irrigazione (sezione che varia). La giunzione P laterale (gate) è come due **pollici giganti** premuti contro i fianchi del tubo. Aumentando la $V_{GS}$ in negativo, la giunzione p-n va sempre più in **polarizzazione inversa** → la **regione di svuotamento** (depletion zone) si espande. I "pollici" dei portatori svuotati diventano sempre più grandi in modo del tutto automatico (è la fisica del diodo inverso). A un certo punto i due pollici vanno a toccarsi al centro del tubo, **schiacciano** la gomma e il flusso d'acqua (gli elettroni) si interrompe. Quella è la pinch-off: tensione $V_P$ raggiunta, corrente $I_D = 0$.
>
> **Cos'è $I_{DSS}$?** La $I_D$ massima quando $V_{GS} = 0$ (cioè quando la giunzione è appena in inversa, ma il canale è ancora aperto).
>
> **Cos'è la parabolica $I_D = I_{DSS} (1 - V_{GS}/V_P)^2$?** Stessa forma della parabolica del MOSFET enhancement, ma con $V_P < 0$ (negativo) e $I_{DSS}$ al posto di $K V_{th}^2$.
>
> **Perché questa parabolica?** Viene dalla fisica: il "pinch-off" riduce lo spessore del canale in modo proporzionale a $(1 - V_{GS}/V_P)$, e la corrente dipende dall'area della sezione del canale = quadrato del "non-strozzato".
>
> **Perché il JFET n ha $V_{GS} \le 0$?** Perché la giunzione gate-canale deve stare **polarizzata in inversa**. Se $V_{GS} > 0$, la giunzione va in diretta → conduce corrente → pilotaggio "rotto".
>
> **Perché "JFET è rumoroso meno del BJT"?** Perché il pilotaggio in tensione non richiede corrente → non c'è **shot noise** (rumore di corrente di giunzione) tipico del BJT.
>
> **Cos'è la transconduttanza $g_m$?** La pendenza della transcaratteristica: $g_m = \Delta I_D / \Delta V_{GS}$. Misura "quanto $I_D$ cambia per 1 V di $V_{GS}$". Simile al $K$ del MOSFET.
>
> **Perché il JFET è limitato oggi?** Perché è **più difficile da integrare** del MOSFET (richiede una giunzione, non un ossido) → più costoso in produzione in grande scala. Resta importante in applicazioni analogiche specifiche (pre-amp a basso rumore, interruttore analogico).
>
> **Ma allora perché i produttori non hanno abbandonato del tutto il JFET?** In parte l'hanno fatto, ma in parte no. La ragione profonda è industriale: realizzare un MOSFET è come stendere strati di **lasagna** (gate-ossido-canale uno sopra l'altro) — una tecnica planare fotolitografica che le macchine moderne amano fare su wafer enormi, milioni di transistor per centimetro quadrato. Realizzare un JFET richiede di **impiantare** una giunzione p-n *dentro* un canale n preesistente, come piantare un "tappo di botte" tridimensionale dentro un tubo: richiede geometrie 3D più complesse, controllo di drogaggio differenziale, maschere aggiuntive. Si fa, ma non scala a miliardi di transistor come il MOSFET. Resta vivo in applicazioni dove servono le sue proprietà uniche (rumore bassissimo in pre-amp audio Hi-Fi, interruttore analogico preciso in strumentazione) — nicchie di mercato giustificano la produzione limitata.
>
> **Cos'è il JFET come VCR (Voltage Controlled Resistor)?** In zona triodo, $R_{DS}$ dipende da $V_{GS}$. Applicazione: AGC, compressori audio, mixer.
>
> **Cos'è il JFET come interruttore analogico?** ON/OFF pilotati da $V_{GS}$ (ON = $V_{GS} \approx 0$, OFF = $V_{GS} \le V_P$). Veloce (ns), bassa resistenza ON ($r_{DS(on)} \sim$ pochi ohm). Usato in sample-and-hold, multiplexer.
>
> **Cosa c'entra con il resto?** Il JFET è "l'antenato" del MOSFET: stessa idea, pilotaggio in tensione, ma con giunzione invece che ossido. Usato in pre-amp audio Hi-Fi, strumentazione.

---

## 11. Perché un amplificatore? ([[Amplificatori a BJT]])

> **Cos'è?** Un sistema che prende un segnale piccolo in ingresso e produce un segnale grande in uscita, mantenendo (idealmente) la stessa forma d'onda.
>
> **Perché serve?** Perché i segnali da misurare/trasmettere sono spesso **troppo deboli**. Il microfono di un telefono produce pochi mV — non puoi pilotare un altoparlante direttamente. Serve amplificazione.
>
> **Perché il transistor e non un trasformatore?** Perché il transistor **non ha bisogno di un campo magnetico** (non ha nuclei di ferro, non ha avvolgimenti pesanti). Può essere miniaturizzato.
>
> *(Vedi [[00 - Perchè (spiegazione intuitiva)#1. Perché un segnale sinusoidale? (Segnali sinusoidali e fasori)|§1 — Motivo 4]] per la genesi fisica della sinusoide, Faraday-Neumann-Lenz e perché una rete in onde quadre sarebbe un disastro.)*
>
> **Perché la configurazione "Emettitore Comune" si chiama così?** Perché, in AC, il terminale di **Emettitore** è collegato alla massa del segnale (tramite $C_E$ di bypass o direttamente). Diventa il punto in **COMUNE** a cui fanno riferimento sia il voltaggio in ingresso (iniettato sulla Base) sia quello generato in uscita (prelevato dal Collettore). Ingresso e uscita "parlano" riferendosi entrambi all'emettitore. Lo stesso ragionamento vale per "Collettore Comune (CC)" e "Base Comune (CB)".
>
> **Perché 3 configurazioni (CE, CC, CB)?** Perché cambiando **quale terminale è comune** tra ingresso e uscita, ottieni caratteristiche diverse:
> - **CE**: guadagno di tensione alto (10-100), inversione di fase. Uso generale.
> - **CC** (emitter follower): guadagno ≈ 1, alta impedenza ingresso, bassa impedenza uscita → **buffer**.
> - **CB**: alta impedenza uscita, bassa impedenza ingresso, alto guadagno **di corrente**. Uso: alte frequenze (RF).
>
> **Perché CE ha inversione di fase?** Perché $v_{out} = V_{CC} - I_C R_C$. Quando $I_C$ sale (ingresso sale), $v_{out}$ scende. È una firma: **se non c'è inversione, non è un CE**.
>
> **Cos'è il "punto di lavoro" (Q-point)?** Il valore di $I_C$, $V_{CE}$ a riposo (segnale = 0). Serve per garantire che il transistor resti in **zona attiva** durante l'amplificazione (altrimenti clippaggio).
>
> **Perché $V_{CE} \approx V_{CC}/2$ è una buona scelta?** Perché lascia la **massima escursione** simmetrica: il segnale può salire e scendere di uguale entità prima di clippare in alto o in basso.
>
> **Cos'è $r_e$ (resistenza di emettitore incrementale)?** Una resistenza "vista" dal segnale AC nell'emettitore. $r_e = V_T / I_E \approx 25\text{ mV}/I_E$. È una manifestazione del fatto che il BJT fa vedere un "frenamento" dipendente dalla corrente quando il segnale AC varia.
>
> **Perché $r_e$ entra nella formula del guadagno?** Perché nel modello a piccolo segnale, l'emettitore "frena" il segnale. Più $r_e$ è piccola, più guadagno hai. Più polarizzi il transistor (alta $I_E$), più $r_e$ è piccola, più $A_v$ è alto.
>
> **Perché il guadagno del CE è limitato a 10–100 e non arriva a 1000?** Per ottenere $A_v$ altissimo ($R_C / r_e$) dovresti usare $R_C$ enorme. Ma $I_C$ a riposo creerebbe su $R_C$ una caduta di tensione feroce ($I_C \cdot R_C$), consumando tutti i volt di alimentazione ($V_{CC}$) → il transistor va subito in **saturazione** prima ancora che il segnale AC possa variare attorno al Q-point. Il compromesso è: $R_C$ alto abbastanza per guadagno 10–100, ma non troppo da saturare a riposo. Voler guadagno altissimo (1000+) **richiede** un design multi-stadio (CE → CE → CC).
>
> **Perché CC ha $A_v \approx 1$ e non inferiore?** Nel Collettore Comune, l'uscita è sull'emettitore. La tensione di uscita "insegue" la tensione di base con un ritardo fisso ($V_{BE} = 0{,}7$ V DC). Per **segnali AC** (piccoli attorno al Q-point), il $V_{BE}$ è trascurabile in AC → l'uscita AC è quasi uguale all'ingresso AC → $A_v \approx 1$ (tipicamente 0,95–0,99). Il piccolo scarto da 1 dipende dalla corrente di polarizzazione: più $I_E$, più "robusto" l'inseguimento. La "magia" del CC è che l'**alta impedenza di ingresso** + la **bassa impedenza di uscita** formano un adattatore di impedenza ideale — l'amplificazione di tensione ≈ 1 è il prezzo accettabile per questa funzione.
>
> **Cos'è l'inversione di fase in CE?** Una rotazione di 180° del segnale in uscita rispetto all'ingresso. Causa fisica: l'aumento di $I_C$ causa una **caduta** su $R_C$, quindi $V_{CE}$ cala.
>
> **Cos'è il "clipping"?** Il **taglio** della forma d'onda quando il transistor esce dalla zona attiva. Sopra: saturazione (clipping inferiore dell'uscita). Sotto: cutoff (clipping superiore).
>
> **Cos'è la banda passante?** L'intervallo di frequenze in cui il guadagno è circa costante. Definisce "fino a che frequenza" l'amplificatore è utile.
>
> **Perché si mette una resistenza di degenerazione sull'emettitore anche se fa calare il guadagno?** Perché i BJT non sono tutti identici ($\beta$ varia tra 100 e 300 anche tra transistor dello stesso lotto) e, scaldandosi, conducono di più (il "transconductance" $g_m$ cresce con $I_C$ che cresce con la temperatura) → "sfuggono" rapidamente dalla zona attiva. La $R_E$ introduce un **feedback negativo automatico**: se $I_C$ prova a salire, $R_E$ assorbe più tensione ai suoi capi ($V_{R_E} = I_C \cdot R_E$ sale) → sottrae la "spinta" alla Base ($V_{BE} = V_B - V_E$ cala) → la corrente si stabilizza da sola. Il prezzo è un guadagno leggermente inferiore ($A_v = -g_m R_C / (1+g_m R_E)$ invece di $-g_m R_C$), ma il vantaggio è enorme: **stabilità termica + uniformità tra transistor diversi**.
>
> **Cosa c'entra con il resto?** Gli amplificatori sono il cuore di TUTTA l'elettronica analogica. Audio, radio, strumentazione, telecomunicazioni — sempre amplificatori prima o poi.

---

## 12. Perché un alimentatore? ([[Alimentatori]])

> **Cos'è?** Un circuito che prende la tensione AC dalla rete (230 V 50 Hz in Italia) e produce una tensione DC stabile (es. 5 V, 12 V) per alimentare circuiti elettronici.
>
> **Perché serve?** Perché tutti i circuiti elettronici che usiamo (telefono, computer, TV) hanno bisogno di **DC**, ma la rete fornisce AC.
>
> **Perché la rete è AC?** Storico: i generatori meccanici producono naturalmente AC (alternatori), e la trasmissione a lungo raggio è più efficiente in AC (trasformatori possono alzare/abbassare la tensione).
>
> **Perché i circuiti elettronici vogliono DC?** Perché i transistor, i circuiti integrati, i microprocessori funzionano in DC. Le correnti alternate creano complicazioni.
>
> **A cosa serve il trasformatore?** A **isolare** galvanicamente (sicurezza!) e ad **abbassare** la tensione (es. da 230 V a 12 V). Lavora solo in AC, sfruttando l'induzione magnetica.
>
> **A cosa serve il ponte di Graetz (4 diodi)?** A **raddrizzare** l'AC in DC pulsante: le semionde negative vengono "raddrizzate" in positive → uscita sempre positiva ma con buchi.
>
> **Ma perché servono 4 diodi, non basterebbe buttare la semionda negativa usandone solo 1?** Con un solo diodo in serie prendi **solo la metà** dell'energia disponibile dall'AC (l'altra metà la butti), oltre a non proteggere il carico dalla tensione inversa (rischio rottura). Con 4 diodi in ponte non butti via niente: immagina una rotonda a 4 ingressi dove 4 vigili del traffico (i diodi) reindirizzano **tutte** le auto verso un'unica uscita (il carico DC). Quando l'AC arriva in una direzione, 2 dei 4 diodi sono polarizzati direttamente e "fanno passare" le auto verso l'uscita positiva. Quando l'AC si inverte, gli **altri 2** diodi (prima in inversa, ora in diretta) prendono il testimone e instradano anche quelle auto verso la stessa uscita. Risultato: **entrambe** le semionde dell'AC arrivano al carico come tensione positiva, raddrizzata a onda intera. Zero semionde "buttate nel fosso", zero rischio di tensione inversa sul carico.
>
> **Perché serve un condensatore di filtro?** A **livellare** la tensione: il C si carica al valore di picco, poi si scarica lentamente durante le pause → uscita quasi costante (con un piccolo "ripple" residuo).
>
> **Cos'è il ripple?** La piccola oscillazione residua sulla tensione DC livellata. È il "respiro" del condensatore che si ricarica a ogni picco. Più $C$ è grande, meno ripple.
>
> **Perché serve uno stabilizzatore (Zener, BJT, 78xx)?** Perché la tensione di uscita del filtro dipende ancora da:
> - Tensione di rete (può variare ±10%)
> - Corrente di carico (più carico → più ripple, e la tensione scende).
>
> Serve un circuito che **misuri** la tensione di uscita e **aggiusti** il passaggio di corrente per mantenerla stabile.
>
> **Come funziona il regolatore serie a BJT?** Usa un transistor in zona attiva che "assorbe" la differenza tra tensione di ingresso e tensione di uscita. Più corrente di carico → più caduta sul BJT → $V_{out}$ stabile.
>
> **Cos'è il dropout?** La tensione **minima** differenza tra $V_{in}$ e $V_{out}$ perché il regolatore funzioni. Per i 78xx è ~2 V: serve $V_{in} \ge V_{out} + 2$ V.
>
> **Perché il dropout serve, e perché è proprio 2 V per i 78xx e non 0,5 V?** Considera lo stabilizzatore come uno "stiratore a spruzzo" che deve tenere i piani di tessuto alla tensione di uscita che ti serve (es. 5 V). Per mantenere il tessuto sempre teso, tu devi dargli in ingresso un avanzo di tensione pari a $V_{out} + 2\,V$ (7 V nel caso 7805), così che lo stabilizzatore possa **finemente modulare** la differenza: "tira su" la tensione di uscita se il carico assorbe di più, "allenta" se sale. Quel "gioco di 2 V" (dropout) gli serve per restare in **zona attiva** del transistor di passaggio interno, dove può reagire con prontezza a variazioni di carico o di tensione di rete. Se l'ingresso scendesse sotto $V_{out} + 2\,V$, lo stabilizzatore "uscirebbe" dalla zona attiva → $V_{out}$ crolla a seguire l'ingresso → addio regolazione. Quindi i 2 V di dropout sono la "riserva operativa" che il regolatore si tiene per poter fare il suo lavoro di stabilizzazione in tutte le condizioni reali (rete ±10%, carico variabile).
>
> **Perché i 78xx sono così comuni?** Perché sono **semplici da usare**, robusti, economici. Tre pin: $V_{in}$, GND, $V_{out}$. Aggiungi due condensatori di filtro e funzionano.
>
> **Cosa c'entra con il resto?** Gli alimentatori sono alla base di **tutti** i laboratori: oscilloscopio, generatore di funzioni, alimentatore da banco. **Rientrano in «circuiti con diodi» di Protti (parte pratica)**: misura del ripple, regolazione di linea/load, test del regolatore 78xx.

---

## 13. Perché un oscilloscopio? ([[L'oscilloscopio]])

> **Cos'è?** Uno strumento che **visualizza** tensioni elettriche nel tempo su uno schermo, permettendo di misurare ampiezza, frequenza, sfasamento, forma d'onda.
>
> **Perché serve?** Perché il multimetro misura solo valori "medi" (DC) o efficaci (AC), ma non ti fa vedere **la forma del segnale**. Molti problemi si vedono solo "guardando" il segnale.
>
> **Perché non basta un grafico carta-matita?** Perché l'oscilloscopio mostra segnali **in tempo reale** (anche a frequenze alte), mentre la carta non ha banda sufficiente.
>
> **Cos'è una sonda (probe)?** Il cavo che porta il segnale dal circuito all'oscilloscopio. Non è un filo neutro: l'oscilloscopio più il cavo presentano al circuito $1\ \text{M}\Omega$ in parallelo a **~150 pF**, e quei 150 pF a frequenza alta sono quasi un cortocircuito. La sonda ×10 esiste per ridurre questo carico (10 MΩ ∥ ~15 pF) — vedi [[L'oscilloscopio]] §7.
>
> **Cos'è il coupling AC/DC?** Interruttore che decide se mostrare la tensione **completa** (DC coupling) o solo la **componente variabile** (AC coupling, che rimuove la DC).
>
> **Quando usare AC coupling?** Quando vuoi vedere solo il **ripple** di un alimentatore (la DC è 12 V, ma il ripple alternato è di pochi mV: in DC coupling il ripple è "schiacciato" dalla scala, in AC coupling lo vedi chiaramente).
>
> **Quando usare DC coupling?** Quando vuoi **misurare il valore assoluto** della tensione DC (es. $V_{out}$ di un alimentatore).
>
> **Cos'è il trigger?** Il meccanismo che **stabilizza** la forma d'onda sullo schermo: l'oscilloscopio aspetta che il segnale passi per un certo livello prima di iniziare la sweep orizzontale.
>
> **Cos'è AUTO vs NORMAL trigger?** AUTO: trigger automatico, genera sweep anche senza trigger (per segnali lenti o fermi). NORMAL: trigger solo quando il segnale lo soddisfa (fondamentale per segnali non periodici o discontinui).
>
> **Cos'è la base tempi (timebase)?** La scala orizzontale, in secondi/divisione. Es. 1 ms/div → lo schermo mostra 10 ms (il reticolo standard è **10 divisioni orizzontali × 8 verticali**; certi oscilloscopi moderni "widescreen" ne hanno 12 in orizzontale — conta le tacche del *tuo* strumento prima di fidarti).
>
> **Cos'è la scala verticale (Volts/div)?** La sensibilità verticale. Es. 1 V/div → 8 divisioni = 8 V di picco-picco.
>
> **Come si misura una frequenza?** Misura il **periodo** $T$ dal grafico (distanza tra due fronti ascendenti consecutivi), poi $f = 1/T$.
>
> **Come si misura uno sfasamento?** Misura il **ritardo $\Delta t$** tra i passaggi per lo zero dei due segnali, poi $\varphi = 360° \cdot \Delta t / T$.
>
> **Cosa c'entra con il resto?** L'oscilloscopio è lo strumento che userai alla prova pratica Protti per misurare amplificatori, filtri, alimentatori. Senza saperlo usare, non risolvi gli esercizi pratici.

> **Perché la sonda ×10 riduce il carico sul circuito?** Perché contiene un partitore: 9 MΩ in serie al segnale + 1 MΩ dell'ingresso oscilloscopio. Il segnale viene attenuato di 10× ma l'impedenza vista dal circuito sale a 10 MΩ. **E lo stesso vale per la capacità**: i ~150 pF dell'oscilloscopio-più-cavo diventano ~15 pF alla punta. È questa la parte che conta ad alta frequenza, perché una capacità in parallelo al punto di misura è un cortocircuito che peggiora al salire della frequenza.
>
> **Perché la sonda ×10 ha un trimmer da regolare?** Perché un partitore fatto di sole resistenze divide per 10 in continua, ma **non** in alternata: la capacità dell'oscilloscopio "scavalca" la resistenza da 1 MΩ appena si sale in frequenza, e il rapporto di partizione cambia — cioè la sonda diventa un filtro passa basso involontario. Aggiungendo una capacità $C_s$ regolabile in parallelo ai 9 MΩ si ottiene che **anche le capacità partiscono nello stesso rapporto delle resistenze** ($R_sC_s = R_iC_i$): a quel punto il rapporto è 1/10 a *tutte* le frequenze. Si regola guardando un'onda quadra: tetto arrotondato = poca $C_s$ (sottocompensata), gobba = troppa (sovracompensata). Conto e dimostrazione in [[L'oscilloscopio]] §7.
>
> **Perché il trigger deve essere a metà dell'ampiezza?** Perché lì il segnale è **più ripido che mai**, quindi passa per la soglia in un istante ben definito e sempre lo stesso: l'immagine resta ferma. Vicino ai picchi invece il segnale è quasi piatto, e basta un po' di rumore per farlo attraversare la soglia in anticipo o in ritardo → la traccia balla. Se poi la soglia esce dall'ampiezza del segnale, il trigger **non scatta mai**: in NORMAL lo schermo resta vuoto (su un analogico: nero, nessuna traccia), in AUTO parte comunque la scansione libera e vedi una sinusoide che scorre.
>
> **Perché l'oscilloscopio misura il valore di picco e non quello efficace?** Perché sullo schermo vedi la **forma d'onda** istantanea nel tempo: la distanza picco-picco è immediatamente leggibile. Il valore efficace ($V_{\text{eff}} = V_p/\sqrt{2}$ per sinusoidi) è una media quadratica, **non** leggibile dallo schermo — serve calcolarla a parte.
>
> **Perché usare l'AC coupling per misurare il ripple di un alimentatore?** Perché l'alimentatore ha 12 V di DC + piccolo ripple alternato sovrapposto (qualche mV). Con DC coupling lo schermo mostrerebbe la traccia principale a 12 V: il ripple sarebbe "schiacciato" dalla scala verticale. Con AC coupling il DC viene bloccato → vedi solo il ripple, ampio sullo schermo. Misura agevole.
>
> **Perché le sonde ×1 sono più semplici ma si usano di rado in laboratorio?** Perché la ×1 non ha partitore: collega direttamente l'ingresso dell'oscilloscopio al punto di misura, quindi il circuito si porta addosso 1 MΩ **e tutti i ~150 pF** del cavo più lo strumento → alle frequenze alte carica molto e distorce. Le ×10 si usano di norma; le ×1 quando il segnale è piccolo e lento e non vuoi perdere un fattore 10 di ampiezza.

---

## 🧠 Mnemonico finale: la "regola d'oro" per ogni argomento

| Argomento | Regola d'oro mnemonica |
|---|---|
| Fasori | $V = R I$ continua; in AC, derivare = moltiplicare per $j\omega$. |
| Impedenze | $R$ non ha fase; $L$ anticipa di $+90°$; $C$ ritarda di $-90°$. |
| Metodo simbolico | Tutti i teoremi (Kirchhoff, Thévenin, Millman) valgono identici, solo con numeri complessi. |
| Potenze | $P$ = consumata; $Q$ = scambiata; $S = \sqrt{P^2 + Q^2}$; $P+Q \neq S$. |
| Risonanza | $X_L + X_C = 0$: la tensione diventa parallela alla corrente. |
| Filtri | RC: $\tau = RC$, $f_t = 1/(2\pi RC)$. RL: $\tau = L/R$, $f_t = R/(2\pi L)$. |
| Diodi | Conduce quando $V > 0{,}7$ V (silicio). Zener conduce in inversa a $V_Z$. |
| BJT | $I_C = \beta I_B$. Saturazione = ON. Interdizione = OFF. Attiva = amplifica. |
| MOSFET | $I_D = K (V_{GS} - V_{th})^2$ in **saturazione**. Gate isolato = pilotaggio senza corrente. |
| JFET | $I_D = I_{DSS} (1 - V_{GS}/V_P)^2$. $V_P < 0$ per JFET n. Gate in inversa. |
| Amplificatori | CE: inversione di fase. CC: $A_v \approx 1$, buffer. CB: alte frequenze. |
| Alimentatori | AC → trasformatore → ponte → filtro C → regolatore → DC stabile. |
| Oscilloscopio | Misuri T e V sullo schermo, poi derivi $f = 1/T$, $\cos\varphi = \Delta\varphi/\Delta t$. |

> [!tip] Quando hai dubbi
> 1. **Cos'è?**: definizione di 1 frase dalla prima riga.
> 2. **Serve?**: la "Perché?" sopra ti dice l'applicazione.
> 3. **Formula?**: dal file Argomenti dedicato (linkato in cima).
> 4. **Perché sbaglio?**: rileggi le 4-6 "Perché?" e scoprirai dove hai perso il filo.

---

## Vedi anche

- [[Argomenti]] — indice MOC per navigare
- Tutti i file `Argomenti/*.md` linkano a questo hub in cima (`→ Vedi [[00 - Perchè (spiegazione intuitiva)]] §N`).
