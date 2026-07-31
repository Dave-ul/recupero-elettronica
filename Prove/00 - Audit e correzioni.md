---
tags: [recupero, elettronica, audit, trasparenza, correzioni]
aggiornato: 2026-07-28
---

# 🔧 Audit e correzioni del vault

> Registro **trasparente** di ogni discrepanza trovata fra le fonti (lettera Majorana, edutecnica.it, libro Mirandola) e di come è stata risolta. Serve a fidarti del vault: se una nota è stata verificata, qui trovi cosa è cambiato e perché. Complementare a [[00 - Fonti e note]].

## Metodo di verifica

- **Libro Mirandola** *Elettrotecnica ed Elettronica Vol.2* (Zanichelli 2012): reso verificabile via **OCR** (`pdftoppm` 200 dpi + `tesseract -l ita`) e **lettura diretta delle pagine**. Testo integrale in `/home/davide/Scaricati/libro-OCR-completo.txt` (152 pagine-PDF, blocchi `===== PAGINA-PDF nnn =====`).
- **edutecnica.it**: confronto formule/terminologia.
- ⚠️ **pagina-PDF ≠ pagina stampata**: ogni pagina-PDF = 2 pagine di libro affiancate; la corrispondenza non è lineare, i folio si controllano dal piè di pagina reale.

---

## Discrepanza trasversale #0 — «libro NON VERIFICABILE» (FALSA)

- **Trovato**: tutte le note dichiaravano nel frontmatter `libro_mirandola: "NON VERIFICABILE — PDF senza OCR"`, con decine di segnaposto «pag. NON verificabile» e caption «(vedi teoria generale di questo argomento)».
- **Realtà**: il PDF non ha *strato di testo* (per questo `pdftotext` dà 0 caratteri), ma le pagine sono immagini **nitide e leggibili**. Con OCR + lettura sono state verificate sul testo reale.
- **Risolto**: `00 - Fonti e note` aggiornato (fonte → «VERIFICATA»); frontmatter e segnaposto sostituiti mano a mano con riferimenti reali `Cap. N, pp. X-Y`.

---

## Lotto 1 — Segnali sinusoidali e fasori ✔ (2026-07-19)

**Fonte libro**: Cap. 2 «La corrente alternata», §§1.1-1.3 «Rappresentazione vettoriale/complessa/esponenziale», **pp. 46-51** (pagg.-PDF 1-3).

**Verifica di correttezza**: la teoria è **fedele al libro**.
- Formule (2.1) somma, (2.2)-(2.5) conversioni cartesiane↔polari, (2.6) Eulero, (2.7) inverse: **coincidono** col testo.
- **ESEMPIO 1** (fasori $\bar V_1=4+2j$, $\bar V_2=-2+j$; moduli 4,47 e 2,23; $\varphi$ 27° e 153°; somma $2+3j$; prodotto $10\,e^{j\pi}=-10$): **identico** al libro (pp. 50-51). ✔

**Correzioni applicate**:
1. Frontmatter `libro_mirandola` → «VERIFICATO ✔ … Cap. 2, pp. 46-51» in `Segnali sinusoidali e fasori.md` e `Esercizi - Segnali sinusoidali e fasori.md`.
2. Segnaposto «(pag. NON verificabile — vedi …)» → «Mirandola, Cap. 2, pp. 46-51» (entrambe le note).
3. Caption rotte «(vedi teoria generale di questo argomento)» → rimosse (le didascalie restanti coincidono col testo del libro: FIG. 2 fasori, FIG. 3 operazioni, FIG. 5 Eulero).
4. Caption esercizi FIGURA 38/39 «(NON VERIFICABILE — vedi …)» → «diagramma vettoriale, Mirandola, esercizi di fine Cap. 2».
5. Affermazione non verificata «Cap. 3 … nella tua scansione non c'è» → «Cap. 3 del libro; fuori programma» (non era stato verificato che manchi).

**Da ricontrollare** (non bloccante): i valori numerici letti dai **diagrammi vettoriali FIGURA 38-39** degli esercizi provengono da grafici a bassa risoluzione; vanno confrontati sul libro cartaceo o su lettura ad alta risoluzione della pagina.

---

## Lotto 2 — Impedenza dei bipoli R, L, C ✔ (2026-07-19)

**Fonte libro**: Cap. 2 «La corrente alternata», §§ impedenza/reattanza/serie-parallelo/componenti reali, **pp. 52-61** (pagg.-PDF 4-8); esercizi di fine capitolo (FIGURE 40-42) su pagg.-PDF 18-19.

**Verifica di correttezza**: teoria **fedele al libro**.
- Definizione (2.13), $\bar Z = R+jX$ (2.14), ammettenza (2.15), $X_L=\omega L$ (2.16), $X_C=-1/\omega C$ (2.17), serie (2.18)/parallelo (2.19): **coincidono** col testo (OCR righe 396-483).
- **ESEMPIO 2** (parallelo R–L in serie a C, $f=1$ kHz, $\omega=6280$ rad/s; $\bar Z_{eq}=17{,}9\cdot10^{-3}-j\,1{,}59\cdot10^{3}$; $|\bar Z|=1{,}59\cdot10^{3}\,\Omega$; arg $=270°=4{,}71$ rad): **identico** al libro. ✔
- **Fattore di perdita** $\operatorname{tg}\delta$ (2.24) e **fattore di merito** $Q$ (2.25): confermati (OCR righe 780-800).
- **Esercizi 4-6** — verifica **rigorosa sulle immagini** delle FIGURE 40/41/42: valori dei componenti e risposte del libro ($I_2=23{,}3$ mA, $V_2=7{,}67$ V; $|Z|=1880\,\Omega/823\,\Omega$; $|Z|=815\,\Omega$) **letti dalle figure e confermati**. Le soluzioni svolte nel vault ricalcolano correttamente questi valori. ✔

**Correzioni applicate**:
1. Frontmatter `libro_mirandola` → «VERIFICATO ✔ … Cap. 2, pp. 52-61» in teoria ed esercizi.
2. 5 segnaposto «(pag. NON verificabile — vedi …)» → riferimenti reali `Mirandola, Cap. 2, pp. …` (teoria).
3. 5 caption rotte «(vedi teoria generale di questo argomento)» → didascalie con riferimento reale (TABELLA 1, FIGURE 9/15/16, bipolo).
4. 3 caption esercizi «(NON VERIFICABILE — vedi …)» **con escape rotto `—`** → riferimento reale FIGURA 40/41/42; escape corretto.

**Discrepanza registrata (non bloccante)**: nel §3 la definizione di impedenza (2.13) è illustrata con l'immagine `fig-2-18` (bipolo + sfasamento, **FIGURA 18** del capitolo, usata anche per le potenze), mentre il libro riferisce la definizione alla propria **FIGURA 8**. L'illustrazione è comunque corretta e pertinente; la caption lo segnala.

---

## Lotto 3 — Diodi ✔ (2026-07-19)

**Fonte libro**: Cap. 5 «I diodi», **pp. 192-233** (pagg.-PDF 75-94). Folio verificato sulle immagini (PDF 75 → pp. 192-193; PDF 92 → pp. 228-229).

> [!important] Regola di conversione pagine, ora verificata
> $$\text{pagina stampata} = (\text{pagina-PDF} - 75)\cdot 2 + 192$$
> Vale per il Cap. 5. Ogni pagina-PDF contiene **due** pagine stampate affiancate (pari a sinistra, dispari a destra).

**Mappa sezioni** (confermate su OCR + immagine):

| Sezione | pp. stampate | pag.-PDF |
|---|---|---|
| §1 Il diodo al silicio — giunzione PN, modelli, retta di carico (FIG. 10-12, form. 5.3) | 192-201 | 75-79 |
| §2.1 I raddrizzatori — semionda, presa centrale, Graetz (FIG. 17-19, form. 5.4) | 204-207 | 81-82 |
| §2.2-2.5 Rivelatore di picco, d'inviluppo, fissatore, moltiplicatore (FIG. 20-23, form. 5.5-5.6) | 207-209 | 82-83 |
| §2.6 Il limitatore (clipper) | 210-211 | 84 |
| §3 Data sheets e scelta dei diodi (form. 5.7-5.9, TAB. 2) | 214-217 | 86-87 |
| §4.1-4.3 LED, fotodiodo, **diodo Zener** (FIG. 30-32, TAB. 4 serie BZX55C) | 218-221 | 88-89 |
| GUIDA ALLA PROGETTAZIONE + tabella «Formule» | 226-229 | 91-92 |

**Correzioni — `Argomenti/Diodi.md`** (206 → 323 righe):

1. Frontmatter `libro_mirandola` → VERIFICATO ✔ con mappa sezioni.
2. **11 segnaposto** «(pag. NON verificabile — …)» → riferimenti reali con figura e pagina.
3. **10 embed immagine vuoti** (` `` `) → 8 figure reali ritagliate dal PDF a 200 dpi.
4. ❌ **Errore di attribuzione**: il riquadro citava «rumore Johnson/Shot» come Cap. 5 pp. 50-70. È invece **Cap. 4 §6, pp. 180-181** (form. 4.61-4.62). Ri-attribuito e annotato.
5. ❌ **Errore di contenuto**: «$I_{Z,\min}\approx 5$ mA» → per la serie **BZX55C** del libro $I_{ZK}=1$ mA (minimo di ginocchio), $I_{ZT}=5$ mA (corrente di **test**). Aggiunta tabella $I_{ZK}/I_{ZT}/I_{ZM}$.
6. ❌ **Range $V_Z$**: «da pochi V a ~200 V» → il libro dice «da pochi volt a qualche centinaio di volt».

**Espansioni**:

- §3: i **tre modelli approssimati A/B/C** con la nomenclatura del libro, ESEMPIO 1 svolto ($I_A=16{,}60$ / $I_B=16{,}62$ / $I_C=17{,}65$ mA) e il motivo per cui il libro consiglia il modello B.
- §3: la **retta di carico e il punto di lavoro $Q$** (form. 5.3, FIGURA 12) — mancava del tutto, ed è il ponte concettuale verso la polarizzazione di [[BJT]] e [[MOSFET]].
- §4: la **resistenza differenziale $Z_z=\Delta V/\Delta I$** (FIGURA 32B) — mancava, ed è la ragione per cui lo Zener non stabilizza perfettamente.
- §4: il **dimensionamento svolto** del libro (p. 228): $R_Z$ dal caso peggiore *minima $V_i$ + massimo carico*, potenza dal caso peggiore **opposto** *(massima $V_i$ + carico staccato)*.
- §5: valori medi $V_p/\pi$ e $2V_p/\pi$, quali diodi conducono nel ponte, e perché Graetz è preferito alla presa centrale (metà avvolgimenti).
- §5: riconciliata la formula del ripple con la forma di progetto del libro $C=I_{L\max}\Delta t/V_{RPP}$.
- §6: distinzione **limitatore vs fissatore** (il clipper toglie, il clamper sposta).

**Correzioni — `Esercizi/Esercizi - Diodi.md`**:

1. Frontmatter → VERIFICATO ✔.
2. **Es. 1** ricalcolato ✔ ($I_S=45$ mA, $I_Z=25$ mA, $P_Z=127{,}5$ mW); allineato il range $I_{ZK}/I_{ZT}$.
3. **Es. 2(a)(b)** ricalcolati ✔ ($V_{DC}=23{,}3$ V, ripple $=0{,}466$ V).
4. ❌ **Es. 2(c) — errore dimensionale**: il testo faceva $P_D\approx\frac12 V_D\cdot 0{,}466$, moltiplicando $V_D$ per il **ripple** (volt × volt ≠ watt). Sostituito con l'argomento di conservazione della carica: $\overline{I_D}=\overline{I_{load}}$, quindi $P_D=V_D\cdot 23{,}3\ \text{mA}=16{,}3$ mW.
5. ❌ **Es. Z2** — rimosso il ragionamento irrisolto («…aspetta: edutecnica dice 62,5 mA…»). Risolto: $i=(E-V_Z)/(R+r_D)=13/208=62{,}5$ mA ✔.
6. ❌ **Es. Z9** — rimossa la falsa «discrepanza». Risolto col bilancio al nodo: $\frac{12-v_o}{50}=\frac{v_o-5}{20}+\frac{v_o}{250}\Rightarrow v_o=6{,}62$ V ✔, $i_L=26{,}5$ mA ✔, $P_Z=537$ mW ✔ (fonte: 536 mW). **edutecnica era corretta.**
7. ⚠️ **Es. Z3** — rimossa l'accusa infondata di «typo di edutecnica». Recuperato il dato mancante $V_{Z1}=5$ V, ma lo svolgimento **non è ricostruibile senza lo schema**: segnalato come tale.

**Immagini**: create 6 figure ritagliate (20-53 KB l'una, contro 1,2 MB a pagina intera) + riusate 2 pagine intere già presenti. Rinominate 3 immagini preesistenti che avevano **numeri di pagina sbagliati nel filename** (`pag50`→`pp180-181`, `pag60`→`pp208-209`, `pag70`→`pp228-229`); nessun link rotto, non erano referenziate.

**Da ricontrollare** (non bloccante): gli esercizi edutecnica Z3-Z8 e Z10 riportano i **risultati** ma non lo **svolgimento**; da verificare sugli schemi originali prima di usarli come esercizi d'esame.

---

## Lotto 4 — BJT ✔ (2026-07-19)

**File**: `Argomenti/BJT.md`, `Esercizi/Esercizi - BJT.md`.
**Fonte**: Mirandola Vol.2, **Cap. 7 «Gli amplificatori a transistor», pp. 312-347 (PDF 95-112)**.
Conversione verificata agli estremi: `stampata = (PDF − 95)·2 + 312` (PDF 95 → 312-313; PDF 110 → 342-343).

### ❌ Errore di inquadramento — il capitolo non è il 6
Tutto il vault dava il BJT come «Capitolo 6». È il **Capitolo 7**: frontespizio a p. 312, formule numerate 7.1-7.14. Il **Cap. 6 è sugli amplificatori operazionali** (il libro lo cita esplicitamente a p. 312). Registrato in [[00 - Fonti e note]].

### ❌ Correzioni di contenuto

1. **§4 «Stabilità termica» — riscritto da zero.** Non era solo confuso («…no, aspetta…»): era **sbagliato nel merito**. Attribuiva l'instabilità alla temperatura in astratto e sosteneva che «sale $V_{CE}$ che scorre in $R_B$» (una tensione che *scorre*). La causa reale, testuale a p. 326, è la **tolleranza e la deriva di $h_{FE}$**, che varia con $I_C$ **e** con $T$. Sostituito con i **due effetti** che il libro distingue (pp. 327-328): (1) il partitore fissa $V_B$, valido solo se $I_{part} \gg I_B$ (in pratica $I = 10I_B$); (2) $R_E$ introduce una **retroazione negativa**, con la catena completa $I_C\!\uparrow \Rightarrow V_E\!\uparrow \Rightarrow V_{BE}\!\downarrow \Rightarrow I_B\!\downarrow \Rightarrow I_C\!\downarrow$. Aggiunto il punto che il vault mancava: **l'effetto 2 funziona solo se vale l'effetto 1**.
2. ❌ **Auto-polarizzazione (collector-feedback) rimossa dalla teoria.** Il vault la presentava come una configurazione del libro. **Mirandola non la tratta**: a p. 326 dichiara che «se ne approfondiscono **due**» (sola $R_B$; partitore + $R_E$). Sostituita con una nota di scope esplicita.
3. ❌ **`Esercizi` Es. 4 (MOSFET) — errore concettuale grave.** Il calcolo dava $V_{DS} = -9{,}15$ V e il testo concludeva «risultato negativo → **il transistor è in saturazione**». È l'**opposto**: un $V_{DS}$ negativo è fisicamente impossibile e prova per assurdo che l'ipotesi di saturazione va **rifiutata**. Riscritto in 3 passi (ipotizza saturazione → verifica $V_{DS}\ge V_{ov}$ → se fallisce, risolvi in triodo). Soluzione reale da $2{,}35V_{DS}^2-15{,}1V_{DS}+12=0$: **$V_{DS}=0{,}93$ V, $I_D=2{,}36$ mA, zona di triodo** (scartata la radice 5,50 V perché viola $V_{DS}<V_{ov}=3$ V).
4. ❌ **Es. B4 — accusa infondata a edutecnica, ritirata.** Il vault sosteneva che edutecnica avesse «dimenticato la caduta su $R_E$» ($V_{CE}=10{,}96$ invece di 15,2 V). Rifatti i conti col metodo esatto: $V_{CE}=15{,}12$ V ✔ — **edutecnica era corretta**. Il vero errore era **mescolare due modelli**: $I_C=7{,}47$ mA dal metodo esatto e $I_E=11{,}8$ mA da quello approssimato (con $\beta=90$ non possono differire di 1,6×). Aggiunto il perché qui l'approssimazione non regge ($I_{part}=125\,\mu$A contro $I_B=84\,\mu$A: partitore caricato). Chiarito che i **191 mW** dichiarati non sono la dissipazione del BJT (114 mW) ma la potenza erogata dall'alimentatore al ramo d'uscita ($E_C I_E = 190{,}5$ mW).
5. ❌ **Es. 1 — passaggio incoerente.** La riga $V_{BC}=V_{BE}+V_{BB}-V_{CE}-I_CR_C+V_{CC}$ era priva di senso (il risultato finale era però giusto). Sostituita con la giustificazione corretta: **emettitore a massa**, quindi $V_B=V_{BE}$ e $V_C=V_{CE}$.
6. ⚠️ **Es. B3 — ragionamento lasciato a metà** («Servirebbe $R_B$ sui dati…»). Non manca nulla: $R_{TH}=R_1\Vert R_2=18{,}75$ k$\Omega$ **è** la resistenza vista dalla base. Svolto per intero ($V_{CE}=2{,}94$ V ✔) e aggiunto perché il circuito è didatticamente pessimo (nessuna $R_E$ → nessuna stabilizzazione).
7. ✔ **Es. B5 (Darlington)** — il vault asseriva solo $\beta_{eq}=7500$. Verificati **tutti e quattro** i valori di edutecnica ($I_{C1}=0{,}093$ mA; $I_{C2}=7{,}05$ vs 7,11 mA; $V_{CE2}=11{,}43$ vs 11,36 V; $V_{CE1}=10{,}73$ vs 10,66 V) ✔. Aggiunta la doppia caduta $2V_{BE}$ e $R_{in}=(\beta_1+1)(\beta_2+1)R_E\approx9{,}2$ M$\Omega$.

### ➕ Espansioni
- **Retta di carico** riscritta come formula **7.6** con le due intercette ($V_{CE}=V_{CC}$; $I_C=V_{CC}/R_C$) e definizione del punto Q.
- **Iperbole di massima dissipazione** (FIG. 7 p. 319, formula **7.2** $P=V_{CE}I_C$): aggiunta come **vincolo di progetto indipendente** dalla retta di carico — non c'era.
- **ESEMPIO 4 del libro** (p. 327, 2N2222) per intero: $I_{BQ}=100\,\mu$A, $R_B=113$ k$\Omega$, $R_C=600\ \Omega$.
- **Procedura di dimensionamento completa** (formule **7.8-7.11**, pp. 328-329) in tabella a 4 righe (4 incognite → 4 equazioni), con i criteri $V_{RE}=V_{CC}/10$ e $V_{RC}=V_{CEQ}$.
- Spiegato **perché $V_{RC}=V_{CEQ}$**: non solo simmetria dell'escursione, ma anche — testuale a p. 329 — perché «**evita fenomeni di fuga termica**, cioè la crescita a catena di $I_{CQ}$».
- Aggiunta la nota del libro che il modello «due diodi back-to-back» **non spiega l'amplificazione** (serve la base sottile).

**Immagini**: 4 nuovi ritagli (21-63 KB) dal Cap. 7 — `p313-fig1-simboli-bjt`, `p326-fig12-punto-lavoro-retta-carico`, `p326-fig13-polarizzazione-resistenza-base`, `p327-fig14-partitore-stabilizzazione`. I 4 embed vuoti di `BJT.md` sono ora pieni.

**Da ricontrollare** (non bloccante): Es. B6-B10 (switching) sono solo elencati come *pattern*, senza dati né svolgimento. Es. 3 resta a dati volutamente incoerenti — è dichiarato tale, va bene così.

---

## Lotto 5 — Amplificatori a BJT ✔ (2026-07-19)

**File**: `Argomenti/Amplificatori a BJT.md`, `Esercizi/Esercizi - Amplificatori a BJT.md`.
**Fonte**: Mirandola **Cap. 7**, §2.2-2.3, **pp. 332-351 (PDF 105-114)** — stesso capitolo del Lotto 4, mappatura già verificata.

### ❌ Correzioni di contenuto

1. ❌ **Formula del guadagno di tensione — sbagliata due volte.** Il file dava $A_v = -\dfrac{R_C}{r_e + R_E/(\beta+1)}$. (a) La **divisione per $(\beta+1)$ non esiste**: riportare $R_E$ alla base la *moltiplica* per $(\beta+1)$; nel guadagno $R_E$ compare così com'è, in serie a $r_e$. (b) **Manca il carico**: va $R_p = R_C \Vert R_L$, non $R_C$. Sostituita con la **7.15** del libro, $G_v = -h_{fe}R_p/h_{ie}$, più il ponte fra le due notazioni ($h_{ie}=(\beta+1)r_e$, da cui $-h_{fe}R_p/h_{ie} \equiv -R_p/r_e$).
2. ❌ **«Il libro non tratta la base comune» — falso.** Mirandola le dedica una sezione dentro il §2.3 «Gli amplificatori a collettore comune **e a base comune**», con **FIGURA 33** alle **pp. 350-351**. Sostituita l'affermazione con le caratteristiche testuali del libro, il ruolo del condensatore $C_B$ e le due applicazioni citate (ingressi RTV con adattamento a 75/150 $\Omega$; amplificatori selettivi con carico risonante).
3. ❌ **`Esercizi` Es. A1 — la formula citata non produceva il risultato citato.** Accanto a $A_v=-32{,}77$ era scritta $A_v \approx -g_m(R_C\Vert R_L)$, che dà **−111**. La formula era *incompleta*, e nessuno aveva verificato la coerenza col numero a fianco. Risolto: i −32,77 includono l'**attenuazione del partitore d'ingresso** ($R_S=2$ k$\Omega$ contro $R_{in}=0{,}839$ k$\Omega$ → fattore 0,2955; $-111 \cdot 0{,}2955 = -32{,}8$) ✔. **edutecnica corretta** (4ª volta su 4). Verificati anche $R_{in}=0{,}839$ k$\Omega$, $G_i=46{,}6$ e $R_o=2{,}5$ k$\Omega$.
4. ⚠️ **«$V_{CE} \approx V_{CC}/2$» — impreciso.** Col $R_E$ presente il criterio di Mirandola (**7.9**) è $V_{CEQ}=(V_{CC}-V_{RE})/2 = 0{,}45\,V_{CC}$, non $0{,}5\,V_{CC}$. Corretto e cross-linkato alla ragione di **fuga termica** in [[BJT]].
5. ⚠️ **Incoerenza $V_T$**: la stessa frase dava «$\approx 25$ mV» e «$V_T \approx 26$ mV». Uniformato a 26 mV con nota di coerenza. Aggiunto in `Esercizi` il caveat che $A_v = -R_C/r_e$ vale solo a vuoto (in Es. 1 $R_L$ non è dato).

### ➕ Espansioni
- **Le quattro formule del CE** (**7.13** $R_i = R_B \Vert h_{ie}$, **7.14** $G_i$, **7.15** $G_v$, **7.16** $R_o = R_C$) in tabella, con la verifica numerica del libro (FIG. 29, p. 343).
- **Perché $R_o = R_C$**: il generatore di corrente dipendente, spento, ha impedenza infinita e sparisce dal parallelo. Con il corollario del libro: la $R_o$ del CE **non è bassa** → serve un CC a valle.
- **Distinzione guadagno di stadio vs guadagno d'amplificatore** ($v_o/v_i$ contro $v_o/v_s$), con l'esempio del libro dove l'attenuazione di sorgente porta $-30{,}7$ a $-24{,}8$. È l'errore d'esame più frequente e non era menzionato.
- **I tre condensatori** ($C_i$, $C_o$ d'accoppiamento; $C_E$ di by-pass) col trade-off che risolvono e il dimensionamento $X_{CE} \le R_E/10$ + ESEMPIO 7 ($C_E \ge 142\ \mu$F).
- **Rumore e figura di rumore** (p. 336): distinzione fra $S/N$ (qualifica il segnale) e $F$ (qualifica l'amplificatore).
- **TABELLA 1 di progetto** (p. 346) con la nota sul **segno meno al denominatore** delle inverse del parallelo: se la specifica chiede $R_i \ge h_{ie}$ il risultato è negativo, e ciò significa **specifica impossibile** — buon controllo di sanità.
- **Tabella comparativa CE/CC/CB** su 5 parametri: solo il CE amplifica *entrambe* le grandezze.

**Immagini**: 5 nuovi ritagli — `p336-fig21-banda-passante`, `p336-fig22-amplificatore-ce-completo`, `p346-tabella1-progetto-ce`, `p347-fig30-collettore-comune` (+ riuso). I 2 backtick vuoti sono stati riempiti.

**Da ricontrollare** (non bloccante): Es. A2-A5 di edutecnica riportano i risultati ma non tutti gli svolgimenti. La FIGURA 33 (base comune, pp. 350-351) non è stata ritagliata: la sezione è verificata sul testo OCR, non sull'immagine.

---

## Lotto 6 — Il metodo simbolico ✔ (2026-07-20)

**File**: `Argomenti/Il metodo simbolico.md`, `Esercizi/Esercizi - Il metodo simbolico.md`.
**Fonte**: Mirandola **Cap. 2 «La corrente alternata», §3 «Il metodo simbolico», pp. 60-61 (pag.-PDF 8)**. Folio 60 letto dal piè di pagina; numero di sezione (**3**) letto dal badge blu del titolo.
Conversione Cap. 2 ricavata e verificata: `stampata = (PDF − 1)·2 + 46` (PDF 4 → p. 52; PDF 8 → p. 60).

**Verifica di correttezza**: le citazioni della teoria sono **fedeli al libro, parola per parola** (confronto OCR + immagine a 220 dpi). Il riquadro PROCEDIMENTO e i tre passi coincidono. L'**ESEMPIO 5** coincide in ogni passaggio.

### ❌ Correzioni di contenuto

1. ❌ **«Incoerenza di stampa» inventata.** Il file affermava che il libro stampa $0{,}65 + j\,0{,}51$ e poi calcola il modulo con $0{,}66$, definendolo «un arrotondamento incoerente del testo». **Falso**: sull'immagine a 220 dpi il libro stampa **$0{,}66 + j\,0{,}51$**, coerentemente, in entrambe le righe. Il vault aveva anche **alterato il numeratore del libro** (scriveva $12{,}2 + j\,9{,}4$ dove il libro scrive $12 + j\,9{,}4$) e poi usava quell'alterazione come prova dell'incoerenza. Ripristinato il numeratore e sostituita la nota con quella **vera**: il libro arrotonda a ogni passaggio, e la catena esatta dà **0,84 V e 36,5°** contro 0,83 V e 37,7° — scarto di 0,01 V e 1,2°, utile da sapere all'esame ma non un errore del libro.
2. ❌ **«Il Cap. 3 non è nella scansione» — falso.** Il Capitolo 3 (trasformata di Laplace) **c'è**: inizia a **p. 102** (pag.-PDF 29). Resta vero che è fuori programma. Corretto qui e in [[00 - Fonti e note]]. **Terza occorrenza** di questo pattern (vedi nota sistemica in fondo).
3. ⚠️ **`Esercizi` — le «discrepanze di segno» erano reali ma mal diagnosticate.** Le risposte del libro sono state **verificate sull'immagine** di p. 82: stampa davvero `∠Vc = 0,91 rad` (es. 9) e `∠Vc = −1,2 rad` (es. 10). I calcoli del vault sono **corretti** (rifatti: $-0{,}9155$ rad e $+1{,}2156$ rad) e la fisica invocata è giusta. Ma il vault chiudeva con «che siano refusi o una convenzione diversa» e li descriveva come errori «in direzioni opposte», cioè casuali. **Non lo sono**: in entrambi i casi la chiave riporta esattamente l'**opposto** del valore corretto, il che si spiega con **un solo** errore — la chiave dà lo sfasamento dell'**ingresso rispetto all'uscita**. Sostituito con la tabella dei due casi e l'ipotesi unificante, esplicitamente marcata come inferenza da 2 soli campioni.
4. ➕ **Trovato un refuso che il vault aveva mancato**: nell'esercizio 10 la risposta stampata è etichettata **$V_c$** mentre l'esercizio chiede $V_{R2}$ (etichetta copiata dall'es. 9). Dimostrato che è solo l'etichetta a essere sbagliata: il valore 0,64 V è inequivocabilmente $V_{R2}$, perché la tensione sul condensatore in quel circuito vale **2,34 V**.

### ➕ Espansioni
- Aggiunta la denominazione **«trasformata di Steinmetz»** che il libro usa per il metodo simbolico a p. 46, e il suo inquadramento come *un* metodo di trasformazione accanto a quello **più generale** di Laplace — materiale diretto da orale sul quesito 16.
- Le due didascalie di FIGURA 45/46 ora dicono **dove è presa l'uscita** (sul condensatore / sulla resistenza): è il dato da cui si decide il segno, e mancava proprio lì.

**Correzioni formali**: frontmatter `libro_mirandola` → VERIFICATO ✔ (entrambi i file); **5 segnaposto** «(pag. NON verificabile)» → riferimenti reali; **2 caption rotte** «(vedi teoria generale di questo argomento)» → didascalie reali; **2 caption** con **escape rotto `—`** riparate (stesso difetto del Lotto 2).

**Da ricontrollare** (non bloccante): l'ipotesi della convenzione invertita poggia su 2 casi. Se negli esercizi di altri capitoli ricompare uno scarto di segno con modulo corretto, si conferma; è annotato come inferenza, non come fatto.

---

## Lotto 7 — Le potenze in alternata ✔ (2026-07-20)

**File**: `Argomenti/Le potenze in alternata.md`, `Esercizi/Esercizi - Le potenze in alternata.md`.
**Fonte**: Mirandola **Cap. 2, §4 «La potenza in alternata» (pp. 62-65)** + **§4.1** (pp. 63) + **§4.2 «Il rifasamento degli impianti industriali» (pp. 65-67)**, pagg.-PDF 9-11. Folio **64/65** e **66/67** letti dal piè di pagina. Esercizi 11-13 a **p. 82**.

**Verifica di correttezza**: le citazioni della teoria (definizioni 2.28-2.30, triangolo 2.31-2.32, tutto il §4.2 sul rifasamento, normativa, elenco dei vantaggi) sono **fedeli al libro**. Formula **2.33** confermata col suo numero. ESEMPI 6-7-8 verificati passaggio per passaggio.

### 🔬 Le tre accuse al libro, verificate una per una sull'immagine a 220 dpi

Questo file accusava il libro di tre errori. Il verdetto **non è uniforme** — ed è il motivo per cui andavano aperte le pagine:

| Accusa | Verdetto |
|---|---|
| ESEMPIO 7 (p. 65): «$Q = 727$ **kVAR**» | ✅ **fondata** — il libro stampa davvero `kVAR` mentre due righe sotto dà $S = 1{,}37$ kVA. Errore vero di $10^3$. |
| ESEMPIO 6 (p. 64): $Q$ positiva per un carico capacitivo | ⚠️ **fondata ma mal diagnosticata** — vedi sotto |
| ESEMPIO 8 (p. 67): doppia etichetta $\varphi'$ | ✅ **fondata** — entrambe stampate con l'apice |

### ❌ Correzioni di contenuto

1. ❌ **Conferma fabbricata — il caso più grave del lotto.** Per sostenere che l'ESEMPIO 6 sbaglia il segno di $Q$, il vault scriveva: «lo conferma il libro stesso: nell'esercizio 11 la soluzione riporta $Q = \mathbf{-87{,}6}$ µVAR — **col meno**», e concludeva «il libro contraddice sé stesso a due pagine di distanza». Inoltre riportava quel valore col meno anche nella riga **«Risposte del libro»** dell'esercizio 11.
   **Verificato sull'immagine di p. 82: il libro stampa `Q = 87,6 µVAR`, senza meno.** Il vault aveva **alterato la risposta stampata della fonte** e poi l'aveva citata come prova indipendente.
   **Conseguenza sulla diagnosi**: poiché il libro omette il segno in *entrambi* i casi capacitivi (ESEMPIO 6 e es. 11), **non si contraddice affatto** — adotta la convenzione del **modulo** di $Q$. Non è una svista da errata corrige, è una convenzione sciatta. Riscritti i due riquadri: il consiglio operativo (scrivi il segno, perché $Q<0$ ⇒ capacitivo) resta, l'argomento «lo dice il libro» è stato rimosso.
2. ❌ **Conteggio errori gonfiato.** Il file si apriva con «il libro sbaglia **due volte** in questo paragrafo» e chiudeva con «sono ormai **tre errori** trovati nel Mirandola». Alla verifica, in questo paragrafo l'errore vero è **uno** (727 kVAR). Corretti entrambi i riquadri.
3. ❌ **`Esercizi` Es. P2 — conflitto con edutecnica lasciato irrisolto, e risolto male.** Il vault scriveva «$R = 38{,}72$… edutecnica dice 32 … **diverse approssimazioni** — vedi quale è giusta per i tuoi conti», con in mezzo un passaggio incoerente ($|Z| = V\cos\varphi/I$, che non è una formula valida).
   **Risolto**: con $V = 220$ V il valore corretto è $R = 38{,}72\ \Omega$ (verificato per due strade: $P/I^2$ e $|Z|\cos\varphi$). I valori di edutecnica (32 e 24 Ω) sono **esatti** ma corrispondono a $|Z| = 40\ \Omega$, cioè a $\mathbf{V = 200}$ **V**. Il testo su edutecnica dichiara però $V = 220$ V — **verificato sulla pagina originale**. La fonte è quindi *internamente incoerente*. Aggiunto anche $X_L = 29{,}04\ \Omega$, che il vault non calcolava.
   **Perché il vault ci era cascato**: aveva visto $Q = 600$ VAR combaciare e ne aveva dedotto che il resto fosse arrotondamento. Ma $Q = P\tan\varphi$ **non dipende da $V$**: è l'unico dei tre valori che non discrimina fra i due scenari.
4. ⚠️ **`Esercizi` Es. 12 — diagnosi presentata come certa quando non lo è.** Il vault affermava: «la diagnosi è che nel testo sia **caduto uno zero**: la frequenza doveva essere 16000 Hz». Serve $X_L \simeq 1005\ \Omega$, che si ottiene **in due modi indistinguibili**: $f = 16\,000$ Hz con $L = 10$ mH, *oppure* $f = 1600$ Hz con $L = 100$ mH. Le risposte del libro sono identiche nei due casi, quindi **non permettono di decidere**. Riscritto come alternativa aperta (con l'indizio debole che l'es. 13, stessa pagina, usa $L = 100$ mH).

**Correzioni formali**: frontmatter → VERIFICATO ✔ (entrambi); **10 segnaposto** «(pag. NON verificabile)» → riferimenti reali con pagina; **5 caption rotte** → didascalie reali; **3 caption** con escape rotto `—` riparate.

**Correzione di un mio errore del Lotto 6**: avevo annotato gli esercizi di fine Cap. 2 come p. 80 e i quesiti come p. 78. Il folio reale, letto oggi dal piè di pagina, è **p. 82** (esercizi) e **p. 80** (quesiti). Corretto qui, in [[00 - Fonti e note]] e in `Esercizi - Il metodo simbolico`.

**Da ricontrollare** (non bloccante): Es. 13 — il libro dà $C_{rifas} = 5{,}57$ µF, il calcolo (rifatto e verificato in ogni passaggio) dà **6,57 µF**. Nessuna variante plausibile dei dati produce 5,57, quindi l'ipotesi «refuso di una cifra» resta la più probabile ma **non è dimostrata**. Es. P4-P6 di edutecnica hanno dati incompleti nel vault.

---

## Lotto 8 — Filtri passivi del primo ordine ✔ (2026-07-22)

**File**: `Argomenti/Filtri passivi del primo ordine.md`, `Esercizi/Esercizi - Filtri passivi del primo ordine.md`.
**Fonte**: Mirandola **Cap. 4 «I quadripoli lineari e non lineari»**, §3 «I filtri» **pp. 155-158**, §3.1 «I filtri RC e RL (1° ordine)» **pp. 159-161**, §3.2 «I filtri RLC (2° ordine)» **pp. 161-163**. Pagg.-PDF 56-60.
Conversione Cap. 4 `stampata = 2·PDF + 42` verificata ora in **sei** punti (PDF 58→158, 69→180, 71→184, 72→186, 73→188, 74→190), tutti col folio **letto dal piè di pagina**.

**Mappa sezioni** (folio letti dall'immagine):

| Elemento | pag. stampata | pag.-PDF |
|---|---|---|
| §3 «I filtri» — definizione, banda passante/oscura, **FIGURA 44** (filtro ideale/reale) | 155 | 56 |
| **TABELLA 5** — simboli dei 4 tipi; filtri passivi vs attivi | 156 | 57 |
| Ordine del filtro, **FIGURA 45** (Bode 1°/2°/3°/ideale); «Il filtraggio dei segnali» | 157 | 57 |
| **ESEMPIO 18** + FIGURA 46-47 (spettri d'ampiezza in uscita) | 158-159 | 58 |
| **§3.1** + **TABELLA 6** + form. **4.44** (passa basso RC) | 159 | 58 |
| Form. **4.45**, **4.46**, **4.47**; le quattro osservazioni; **ESEMPIO 19** | 160 | 59 |
| **ESEMPIO 20**; **§3.2** + TABELLA 7 + form. **4.48** | 161 | 59 |

### ✅ Le tre accuse al libro: tutte e tre **fondate**, verificate sull'immagine

A differenza del Lotto 7, qui il verdetto è uniforme. Il §6 «Errata corrige» del vault **regge integralmente**.

| Accusa | Verdetto |
|---|---|
| Form. **(4.45)** e **(4.47)** stampano $p=-L/R$, $\omega_p=L/R$, $f_t=L/2\pi R$ | ✅ **fondata** — letto a p. 160. Il denominatore $1+s\frac{L}{R}$ è giusto ($\tau=L/R$), ma il polo è il **reciproco**: $-R/L$. |
| Testo del **passa alto RC** con le conclusioni invertite | ✅ **fondata** — a p. 160 il libro stampa «per $f=0$ … circuito aperto, per cui $v_o=v_i$, mentre per $f=\infty$ è un cortocircuito e quindi $v_o=0$», in contraddizione con la sua stessa (4.46) $G(s)=sRC/(1+sRC)$. |
| L'**ESEMPIO 19**, stessa p. 160, usa la formula **corretta** $R/2\pi L$ = 623 kHz | ✅ **verificata sull'immagine** — la conferma citata dal vault è **reale**, non fabbricata (a differenza dei Lotti 6 e 7). |

**Confermata anche l'ipotesi sull'origine dell'Errore 2**: la frase del passa alto RC è identica, parola per parola, a quella del **passa basso RC di p. 159** (form. 4.44), dove è corretta perché lì il condensatore *è* l'elemento d'uscita. Il passa alto **RL**, due righe sotto sulla stessa p. 160, è invece scritto giusto — coerente con un copia-incolla non aggiornato.

### ❌ Correzioni di contenuto

1. ❌ **Quarta occorrenza di «il libro non ce l'ha».** `Esercizi` dichiarava che «la scansione **non contiene gli esercizi del Capitolo 4**» e che «le pagine 184-191 mancano». **Falso**: ci sono tutte (pagg.-PDF 71-74, folio letti dal piè di pagina) — pp. 184-187 GUIDA ALLA PROGETTAZIONE sui filtri **crossover** per diffusori acustici, pp. 188-189 **quesiti di riepilogo**, pp. 190-191 **esercizi numerati** (n. 17 risposta in ampiezza, n. 19 *progettare un filtro passa alto del primo ordine*). Come nelle tre occorrenze precedenti, l'affermazione serviva a giustificare il ripiego totale su edutecnica. Riquadro riscritto e mappa in [[00 - Fonti e note]] estesa con le quattro righe mancanti.
2. ❌ **Attribuzione indebita al libro** (variante *speculare* del difetto #2: non «il libro non ce l'ha», ma «lo dice il libro» quando non lo dice). La teoria affermava: «Il libro nota anche che questo è il motivo per cui **mettere in cascata** due filtri passivi del primo ordine non dà un filtro del secondo ordine pulito». Il libro a p. 160 dice **soltanto** che le funzioni sono calcolate a *uscite scollegate* e che un carico le altera; di cascata non parla lì. Anzi a **p. 157** afferma che i filtri di ordine superiore «possono ottenersi **combinando (in cascata)** filtri del 1° e del 2° ordine», **senza** avvertire del problema di carico. La fisica del vault è corretta, l'attribuzione no: riscritta come deduzione propria, con la nota che nei filtri **attivi** la cascata funziona davvero perché ogni stadio ha bassa impedenza d'uscita.
3. ❌ **`Esercizi` Es. F3 — ragionamento lasciato a metà, risolto.** Il testo si fermava a «*ridurre a Thévenin … probabilmente $R_{eq}$ = (1+2+1,5)k serie = 4,5 k? O parallelo? Vedi Allegati*». **Risolto**: $R_{eq} = (R_1\parallel R_2) + R_3 = 666{,}7 + 1500 = 2166{,}7\ \Omega$, da cui $f_H = R_{eq}/2\pi L = 34{,}48$ kHz ✔, che riproduce i **34,5 kHz** di edutecnica. **Nessuna delle due ipotesi del vault funzionava**: le tre in serie danno 4,5 kΩ (→ 71,6 kHz, il doppio), $(R_1+R_2)\parallel R_3$ dà 1,0 kΩ (→ 15,9 kHz). **edutecnica scagionata (5ª volta su 6).** Aggiunto il metodo generale: partire da $R_{eq}=2\pi L f_H$ e cercare quale combinazione dei dati lo produce.
4. ⚠️ **`Esercizi` — «$\tau = L/R$, NON $R/L$» impreciso.** Presentava come errore del libro ciò che il libro scrive **giusto**: la costante di tempo *è* $L/R$, e il libro la stampa correttamente nel denominatore di $G(s)$. L'errore del libro è sulla **pulsazione di taglio**, che è il reciproco. Riscritto distinguendo le due grandezze e rimandando al §6 con la pagina esatta.

### ➕ Espansioni
- Le didascalie di **FIGURA 48** ora elencano i quattro circuiti con i loro valori (2,2 µF/1,8 kΩ; 47 kΩ/12 mH; 5 mH/3,3 kΩ; 5,6 kΩ/47 nF): servono per rifare l'ESEMPIO 19 senza riaprire il libro.
- §3.2 (filtri RLC 2° ordine) ora ha pagine reali **161-163** con il rimando a TABELLA 7 e alla formula 4.48.

**Correzioni formali**: frontmatter → VERIFICATO ✔ (entrambi i file); **18 segnaposto** «(pag. NON verificabile)» → riferimenti reali con pagina e figura; **5 caption rotte** «(vedi teoria generale di questo argomento)» → didascalie reali (FIG. 44, TAB. 5, FIG. 45, TAB. 6); **3 caption** con **escape rotto `\u2014`** riparate (stesso difetto dei Lotti 2, 6, 7).

**Da ricontrollare** (non bloccante): gli esercizi del libro alle pp. 190-191 sono ora noti come esistenti ma **non ancora trascritti** nel vault — la Parte A resta con i soli ESEMPI 19-20. Vanno letti dall'immagine e aggiunti. Es. F4-F6 di edutecnica hanno schemi descritti a parole («tipico schema: …») e non verificati sul disegno originale.

---

## Lotto 9 — Reti RLC e risonanza ✔ (2026-07-22)

**File**: `Argomenti/Reti RLC e risonanza.md`, `Esercizi/Esercizi - Reti RLC e risonanza.md`.
**Fonte**: Mirandola **Cap. 2 «La corrente alternata»**, **§2.1 «Risonanza serie» pp. 55-56**, **§2.2 «Risonanza parallelo» pp. 57-58**, chiusura del §2 a **p. 59**. Pagg.-PDF 5-7, folio letti dal piè di pagina (PDF 5→54-55, 6→56-57, 7→58-59). Esercizi 7-8 con FIGURE 43-44 a pp. 82-83; **quesito 13** a p. 80.

> L'argomento cadeva **dentro** l'intervallo del Lotto 2 (pp. 52-61) ma non era stato mappato a livello di sezione: da qui l'assenza dalla tabella §2bis.

### ✔ Il lotto più pulito finora

A differenza dei Lotti 6, 7 e 8, qui **nessuna conferma fabbricata e nessuna falsa assenza**. Le citazioni della teoria — definizioni di risonanza serie e parallelo, DIMOSTRAZIONI delle 2.20 e 2.22, formule **2.21** e **2.23**, comportamento fuori risonanza, osservazione sulle resistenze parassite, chiusura sugli oscillatori e filtri — sono **fedeli al libro parola per parola** (confronto OCR + immagini a 150 dpi). ESEMPI 3 e 4 verificati passaggio per passaggio: $\omega_s=96{,}2\cdot10^3$ rad/s, $f_s=15{,}3$ kHz, $I=0{,}03$ A, $V_L=V_C=1{,}7$ V; $\omega_p=213\cdot10^3$ rad/s, $f_p=33{,}9$ kHz, $I=20$ mA, $I_L=I_C=0{,}94$ A. ✔

**Due citazioni di contenuto stampato, entrambe confermate sull'immagine** (regola nata dal difetto #3):
- Il **quesito 13** («Quando si verificano la risonanza serie e la risonanza parallelo? Quali fenomeni producono?») esiste ed è davvero il n. 13, letto a **p. 80**.
- La **formula 4.53** citata dagli esercizi esiste, a **p. 162** (Cap. 4 §3.2), nel contesto giusto: «*nei filtri passa banda a banda stretta il valore del parametro Q equivale al…*», «*Q esprime la selettività del filtro*».

Verificati anche i conti derivati aggiunti dal vault: $Q=0{,}577$ dalla (2.21) contro $|V_L|/|V_R|=0{,}577$ ✔; i 173 V con $R=1\,\Omega$ ✔; il rapporto $0{,}94/0{,}02 = 47\times$ ✔; e la relazione $\xi = 1/2Q$, coerente con la (4.48) del Cap. 4.

### ❌ Correzioni di contenuto

1. ❌ **`Esercizi` Es. R4 — ragionamento lasciato a metà, e nascondeva un errore.** Alla domanda d'orale «dimostrare che a risonanza il modulo dell'impedenza è solo $R$» il testo svolgeva il caso serie e poi si interrompeva: «*Per parallelo (con $R$ in serie a $L$ e poi in parallelo a $C$): $Y = 1/(R+j\omega_0 L) + j\omega_0 C$… vedi caso specifico*», lasciando intendere che venisse ancora $R$. **Non viene $R$.** Svolto per intero: annullando $\operatorname{Im}(\bar Y)$ si ottiene $\omega_0 = \frac{1}{\sqrt{LC}}\sqrt{1-\frac{CR^2}{L}}$ — che è **esattamente la correzione realistica del libro a p. 58** nel caso $R_C=0$ — e a quella pulsazione $|\bar Z|_{\max} = L/RC$, la **resistenza dinamica**, non $R$. Aggiunta la regola per non sbagliare: guardare **dov'è la resistenza** (in serie al ramo → $Z_{\min}=R$; in parallelo al serbatoio come in FIGURA 13 → $Z_{\max}=R$; in serie all'induttore → $Z_{\max}=L/RC$ e la $\omega_0$ si sposta).
2. ⚠️ **Citazione parafrasata presentata come testuale.** Il riquadro del «paradosso» (p. 55) era riportato come citazione diretta ma diceva «*le tensioni ai capi dei due componenti dovrebbero essere infinite*», mentre il libro stampa «*l'ampiezza della tensione ai capi di **ognuno** dei due componenti dovrebbe essere infinita*». Senso identico, ma una citazione fra virgolette dev'essere letterale. Allineata al testo.
3. ⚠️ **Affermazione assoluta ristretta a ciò che è stato verificato.** «Il libro **non ha** esercizi di dimensionamento di circuiti risonanti» era una tesi sull'intero volume, della stessa famiglia del difetto sistemico #2. Verificato ciò che è verificabile e riscritto come: fra gli **esercizi di fine Cap. 2** non ce n'è nessuno di dimensionamento di circuiti risonanti — i due sulla risonanza (nn. 7-8) sono entrambi di analisi. *(Un esercizio di dimensionamento in quel gruppo c'è, il n. 13, ma riguarda il condensatore di rifasamento — vedi Lotto 7.)*

**Verifica degli esercizi**: Es. 7 ($f_s = 10\,730$ Hz, $V_1 = 7$ V, $I_1 = 1{,}49$ mA) ed Es. 8 ($f_p = 7118$ Hz, $V_1 = 0{,}730$ V, $I_1 = 270$ µA) **ricalcolati e confermati** ✔, comprese le due idee didattiche: alla risonanza serie $R_2$ è cortocircuitata e sparisce; alla parallelo l'$LC$ si apre e resta il partitore $R_1$-$R_2$. Es. R3 ($f_0 = 10\,065$ Hz, $I_{\max}=500$ mA) ✔.

**Correzioni formali**: frontmatter → VERIFICATO ✔ (entrambi i file); **6 segnaposto** «(pag. NON verificabile)» → riferimenti reali con pagina; **2 caption rotte** «(vedi teoria generale di questo argomento)» → FIGURA 11 (p. 55) e FIGURA 13 (p. 57); **2 caption** con **escape rotto `—`** riparate (FIGURE 43-44). Tabella §2bis di [[00 - Fonti e note]] estesa con tre righe nuove (§2.1, §2.2, §2.3) più il quesito 13.

**Da ricontrollare** (non bloccante): gli esercizi 6-7 di edutecnica sul **dimensionamento** di circuiti risonanti (citati in fondo agli esercizi) non sono svolti nel vault, solo elencati. Il legame $Q = f_o/B$ è ora localizzato (form. 4.53, p. 162) ma **non è stato letto dall'immagine**: la forma esatta della formula stampata va confermata prima di usarla all'esame.

> ✅ **Entrambe chiuse dal Lotto 15 (2026-07-26)** — e su entrambe questo paragrafo sbagliava. Gli esercizi 6-7 **erano già svolti** (come Es. F6/F7 in `Esercizi - Filtri passivi`, cercati nella nota sbagliata), e uno conteneva un errore di 1000×. La 4.53, letta dall'immagine, è stampata **in pulsazioni**: $Q = \omega_0/(\omega_{tH}-\omega_{tL})$.

---

> [!danger] Quarto difetto sistemico — **l'errore introdotto dalla bonifica** (1 occorrenza, Lotto 8)
> Il 2026-07-20 il folio della sezione **rumore** del Cap. 4 (Johnson/shot, form. 4.61-4.62) era stato «corretto» da **pp. 180-181** a **pp. 190-191**, e la modifica propagata in `Diodi.md`, `Amplificatori a BJT.md`, in [[00 - Fonti e note]] e nel **nome di un allegato**.
> **La correzione era sbagliata: il valore originale era giusto.** Verificato per tre vie il 22/07 — (1) l'OCR colloca le formule 4.61-4.62 nella pagina-PDF **069**, non nella 074; (2) il piè di pagina della pagina-PDF 069, letto a 300 dpi, riporta **180 | 181** con testatina «**6** La qualità dei quadripoli (distorsione e rumore)»; (3) **l'immagine dell'allegato stesso** mostra il folio 180 | 181 — il rename l'aveva messa in contraddizione col proprio contenuto.
> **Come è nato**: la pagina-PDF 074 **è** davvero pp. 190-191, ma contiene gli *esercizi di fine capitolo*, non il rumore. È stato letto il folio della pagina giusta e attribuito alla **sezione sbagliata**.
> **Regola operativa**: leggere il numero di pagina non basta. Va letta anche la **testatina**, che nomina il paragrafo, e va verificato che la sezione citata sia davvero su quella pagina. Un folio corretto ma associato alla sezione sbagliata è indistinguibile da un folio giusto, finché non si riapre la pagina.
> **Corollario più generale**: le correzioni della bonifica **non sono automaticamente più affidabili** del testo che correggono. Anche loro vanno verificate.

## Lotto 10 — Alimentatori ✔ (2026-07-25)

**Fonte libro**: Cap. 8 «Gli alimentatori» — §1 non stabilizzati + fattore di ripple (form. **8.1**) **pp. 388-389**; §3.1 regolatori integrati 78XX/79XX (FIG. **20** struttura interna, FIG. **21** collegamento) **pp. 406-407**; **TABELLA 1** famiglia 78XX **pp. 408-409**. Folio letti dall'immagine; conversione Cap. 8 = $2\cdot\text{PDF}+122$ (continua col Cap. 7).

**Verifica di correttezza + difetto sistemico #1 (ragionamenti a metà) — due discrepanze di ripple risolte**:
- **Es. A1** (semionda, ripple 5%/1%): il vault calcolava $C=8$ mF interpretando «5%» come **picco-picco**, poi lasciava a metà «edutecnica dice 2,31 mF… probabilmente usa un calcolo diverso». **Risolto**: «5%» è il **fattore di ripple efficace** $r=V_{r,\text{eff}}/V_{Lm}$ (libro form. 8.1). Con $r=1/(2\sqrt3\,f R_L C)$ → $C=2{,}31$ mF (5%) e $11{,}56$ mF (1%): **edutecnica corretto**, il vault aveva sbagliato la definizione.
- **Es. A3** (ponte Graetz, $V_{rpp}=2$ V dato): il vault calcolava $C=1{,}2$ mF ma si auto-sminuiva «edutecnica dice 12 mF… forse scarica più aggressiva». **Risolto**: con la formula del libro (ESEMPIO 7, p. 409) $C=I_L/(2fV_{rpp})=1{,}2$ mF. **Il vault aveva ragione: il «12 mF» di edutecnica è un refuso ×10.** Prova incrociata: la stessa formula sull'Es. A4 edutecnica ($I=2$ A, $V_{rpp}=4$ V) dà 5000 µF, che **coincide** con la soluzione edutecnica; fisicamente 12 mF darebbero $V_{rpp}=0{,}2$ V, non 2 V.

**Correzioni applicate**:
1. Frontmatter `libro_mirandola` → «VERIFICATO ✔ … Cap. 8».
2. Due embed vuoti riempiti: schema interno regolatore (FIG. 20, p. 406) e collegamento completo (FIG. 21, p. 407) → `![[libro-cap8-pp406-407-regolatore-integrato-78xx.png]]`.
3. **Dropout corretto**: «$\approx 2$ V» → «$\approx 2{,}5$ V» ($V_{in}\geq 14{,}5$ V per il 7812), dalla TABELLA 1 del libro ($V_D=2{,}5$ V per tutta la famiglia).
4. Tabella 78xx: aggiunta citazione TABELLA 1 (Cap. 8, pp. 408-409).
5. Es. A1 ed Es. A3 riscritti in forma conclusiva (niente più «probabilmente/forse»).

---

## Lotto 11 — MOSFET ✔ (2026-07-25)

**Fonte libro**: Cap. 7 «Gli amplificatori a transistor», **§3 «I transistor FET e gli amplificatori a FET»**, MOSFET in **§3.3 «I MOSFET e le porte CMOS», pp. 366-368** (FIG. 45-50). Folio letti dall'immagine.

> [!warning] Errore che stavo per introdurre (evitato leggendo l'immagine)
> Il piano di esecuzione dava per scontato che «Cap. 7» in `MOSFET.md` fosse **sbagliato** e che il MOSFET stesse in un «Capitolo 8 FET». **Falso**: il piè di pagina (pp. 366-368) e la testatina («7 Gli amplificatori a transistor») confermano che il FET è la **§3 del Cap. 7**. Il Cap. 8 è invece «Gli alimentatori». **«Cap. 7» era corretto e NON è stato cambiato.** È l'ennesima conferma della lezione del difetto #4: verificare sull'immagine prima di «correggere».

**Verifica di correttezza**:
- **ESEMPIO 5** (edutecnica: $V_{DD}=18$ V, $R_1=5{,}6$k, $R_2=4{,}7$k, $R_D=2{,}2$k, $R_S=1{,}2$k, $K=0{,}4$ mA/V², $V_{th}=3$ V): il vault ottiene $I_D=2{,}33$ mA, $V_{DS}=10{,}1$ V. **Verificato sulla fonte edutecnica reale**: risultato ufficiale $I_D=2{,}33$ mA, $V_{DS}=10$ V → il riquadro [!check] è una **conferma genuina**, non fabbricata.

**Correzioni applicate**:
1. Frontmatter `libro_mirandola` → «VERIFICATO ✔ … Cap. 7 §3.3, pp. 366-368».
2. Due embed vuoti riempiti con FIG. 48 (polarizzazione MOSFET, p. 368) → `![[libro-cap7-pp368-369-mosfet-polarizzazione-invertitore.png]]`.
3. Riferimento libro riga finale: «Cap. 7 (pag. NON verificabile)» → «Cap. 7 §3.3, pp. 366-368 (FIG. 45-50)».

**Allegati rinominati** (folio letti dall'immagine, difetto #4): `libro-cap7-pag100-mosfet-invertitore` → `…-pp368-369-…`; `libro-alim-pag110` → `…-cap8-pp388-389-…`; `libro-alim-pag120-regolatori-78xx` → `…-cap8-pp408-409-…`.

---

## Lotto 12 — JFET ✔ (2026-07-25)

**Fonte libro**: Cap. 7 «Gli amplificatori a transistor», **§3 «I transistor FET»**, parte JFET **pp. 358-365** (struttura, pinch-off, caratteristiche del 2N3819 in FIG. 42 a p. 362). Folio letto dall'immagine.

**Stato di partenza**: file già quasi puliti — **1 solo segnaposto** (frontmatter di `JFET.md`), **0 nei esercizi**, e **nessun embed vuoto**: i «~16 embed vuoti in JFET» temuti dal Lotto 3 **non esistono** con i pattern attuali (confermato il sospetto già annotato).

**Verifica di correttezza + difetto sistemico #1 — una discrepanza risolta**:
- **Es. J5** (partitore di gate: $I_{DSS}=20$ mA, $V_P=-5$ V, $V_{DD}=20$ V, $I_D=5$ mA, $V_{DS}=8$ V, $V_{RS}=4$ V): il vault calcolava $R_2\approx 8{,}1$ k ma si fermava a «edutecnica dice 123 k… probabilmente un'approssimazione». **Risolto**: il valore corretto è $R_2\approx 8{,}1$ k (dà $V_G=1{,}5$ V → $V_{GS}=-2{,}5$ V ✓). **I 123 k di edutecnica sono sbagliati**: darebbero $V_G\approx 11$ V → $V_{GS}=+7$ V, impossibile per un JFET a canale n (gate in inversa, $V_{GS}\le 0$). Corrisponde a un **errore di segno** su $V_{GS}$. Verificato su edutecnica reale (l'answer key riporta davvero 123 k) e per coerenza col metodo dell'Es. J7 dello stesso set. **Il vault aveva ragione** (secondo caso nel giro, dopo l'Es. A3 alimentatori).

**Correzioni applicate**:
1. Frontmatter `libro_mirandola` di `JFET.md` → «VERIFICATO ✔ … Cap. 7 §3, pp. 358-365».
2. Riga «Riferimenti libro: Cap. 7» → «Cap. 7 §3 «I transistor FET», pp. 358-365 (FIG. 42 caratteristiche 2N3819, p. 362)».
3. Es. J5 riscritto in forma conclusiva, con la dimostrazione del perché $R_2=123$ k è impossibile.

---

## Lotto 13 — L'oscilloscopio ✔ (2026-07-25)

**Fonte libro**: l'oscilloscopio **non ha una sezione propria** nelle 152 pagine scansionate (pp. 48-427). L'OCR completo lo nomina **3 volte**, tutte di passaggio; zero occorrenze di «trigger», «sonda», «base tempi», «volt/div». I tre folio sono stati **letti dall'immagine con la testatina** (regola del difetto #4):

| pag.-PDF | folio | testatina / sezione | contenuto |
|---|---|---|---|
| 020 | **84-85** | apertura **Cap. 3 «L'analisi dei segnali»**, §1 | tempo vs frequenza: l'oscilloscopio è lo strumento del **dominio del tempo** |
| 048 | **138-139** | **Cap. 4 «I quadripoli»** §2.3, FIGURA 24 | per vedere la risposta al gradino si usa un'**onda quadra**, «successione di gradini» |
| 050 | **142-143** | **Cap. 4** §2.4, FIGURA 29 | ampiezza e **sfasamento** rilevati con l'oscilloscopio al variare della frequenza |

> [!danger] Quinta occorrenza del difetto sistemico #2 — **evitata di un soffio**
> Il piano di questo lotto prevedeva di scrivere «il libro non tratta l'oscilloscopio». Prima di scriverlo è stata cercata la fonte, e **Mirandola lo tratta**: Zanichelli pubblica, fra gli approfondimenti online dello stesso corso, la scheda **«La cancellazione polo-zero nella sonda dell'oscilloscopio (partitore compensato)»** (© 2012 Zanichelli, Stefano Mirandola) — con $R_i$, $C_i$, la condizione $R_sC_s = R_iC_i$, la dimostrazione della f.d.t. costante e il calcolo $C_s = 16{,}7$ pF.
> **Sarebbe stata la quinta volta** che il vault dichiara assente dal libro qualcosa che c'è. La lacuna non era del libro: era **nel perimetro cercato**. Il PDF scansionato non è «il libro», è *una parte* del libro.
> **Regola operativa aggiornata**: prima di dichiarare un argomento assente, cercarlo **anche nei materiali online dell'editore** (`online.scuola.zanichelli.it/mirandola-files/...`), non solo nella scansione. E ricordare che il libro stesso, a p. 84, rimanda al **VOLUME 1** per le definizioni di base: un secondo perimetro che non abbiamo.

**Verifica di correttezza — un errore tecnico reale trovato e corretto**:

1. ❌ **§7, compensazione della sonda ×10: le due diagnosi erano invertite.** Il vault scriveva «gobba iniziale → **sotto**compensata; gradino arrotondato → **sovra**compensata». È l'opposto. Confermato da due fonti indipendenti — Rohde & Schwarz («*overcompensated probes create overshoot on the leading edge*») e Pico Technology («*under-compensated: the rising edges are curved up towards the flat top*») — e coerente con la fisica del partitore compensato: $C_s$ **troppo piccola** ⇒ $R_sC_s < R_iC_i$ ⇒ le alte frequenze sono attenuate ⇒ **fronte arrotondato**. Riscritto come tabella a tre righe (sotto / sovra / compensata) con la causa in termini di $R_sC_s$ vs $R_iC_i$.
2. ⚠️ **Capacità della sonda — non era un errore, erano due punti di misura diversi.** `L'oscilloscopio` diceva «×1: 1 MΩ, ~100 pF», `00 - Perchè §13` diceva «~20 pF». Il laboratorio Mirandola dà il numero giusto e scioglie l'apparente contraddizione: $C_i \approx 150$ pF **comprende l'oscilloscopio più il cavo della sonda**; i ~20 pF sono l'ingresso del solo strumento. Allineati **entrambi** i file su 150 pF alla punta della ×1 e ~15 pF a quella della ×10 ($C_sC_i/(C_s+C_i)$ con $C_s = 16{,}7$ pF), **dicendo esplicitamente cosa è incluso** invece di scegliere un numero e cancellare l'altro.
3. ✅ **«TV» fra i modi di trigger: verificato, NON corretto.** Sembrava un errore di categoria (TV è un separatore di sincronismi, non un modo). Ma sui pannelli degli oscilloscopi analogici TV **sta davvero sullo stesso selettore** di AUTO e NORM. Aggiunta solo una precisazione fra parentesi. *(Terza volta, dopo il Cap. 7 del MOSFET nel Lotto 11 e l'Es. A3 nel Lotto 10, che una «correzione» pianificata si è rivelata sbagliata alla verifica.)*

> [!danger] Quinto difetto sistemico — **l'embed rotto** (2 occorrenze, entrambe in `L'oscilloscopio`)
> Il Lotto 12 aveva concluso «zero embed vuoti» cercando il pattern `![[]]`. Quel pattern verifica la **sintassi**, non il **referente**: `![[oscilloscopio-schema.png]]` è sintatticamente perfetto e punta a un file **che non esiste**. Le due immagini non erano mai state create; al loro posto, in root, c'erano due file `.md` da **0 byte** chiamati `oscilloscopio-schema.png.md` e `coupling-dc-ac.png.md` — le note vuote che Obsidian crea quando si clicca un link rotto. Erano il *sintomo*, non la causa.
> **Il controllo giusto non è un grep ma un join** fra i link estratti e il contenuto di `Allegati/`:
> ```bash
> grep -rno '!\[\[[^]]*\]\]' Argomenti Esercizi | sed 's/.*!\[\[//;s/\]\]//' | sort -u \
>   | while read -r e; do [ -f "Allegati/$e" ] || echo "ROTTO: $e"; done
> ```
> Eseguito dopo le correzioni: **zero embed rotti**. I due stub da 0 byte sono stati spostati in `.trash/`.
>
> ⚠️ **Il comando va tenuto su `Argomenti Esercizi`, non esteso a `Prove`**: questo log *cita* i pattern che documenta (qui sopra, e a proposito degli embed vuoti), e un grep esteso segnalerebbe come «rotti» gli esempi scritti in questo file. Sono dentro `backtick`, quindi Obsidian non li rende come embed — ma il grep non lo sa. È lo stesso genere di trappola del difetto #3: uno strumento che scambia la *menzione* di una cosa per la cosa.

**Correzioni applicate**:
1. Frontmatter `libro_mirandola` → VERIFICATO ✔ con i tre folio e la distinzione «assente dalla scansione» ≠ «assente dal libro»; aggiunto un campo `fonte_laboratorio` col link alla scheda Zanichelli.
2. I **due embed rotti** sostituiti da **diagrammi Mermaid** scritti nella nota (schema a blocchi dello strumento; confronto AC/DC coupling). Niente più dipendenza da file binari mancanti.
3. **§7 riscritto e ampliato**: la teoria del **partitore compensato** con $R_sC_s = R_iC_i$, il calcolo di $C_s = 16{,}7$ pF, la tabella di diagnosi corretta, e il *perché* si usa un'onda quadra (molte armoniche = verifica istantanea di tutta la banda) collegato alla p. 139 del libro.
4. Le **tre citazioni collaterali** inserite dove servono davvero: p. 84 nel §1, p. 143 nel §5 (è la procedura del libro per rilevare $|G|$ e $\angle G$, la stessa dei filtri), p. 139 nel §7.
5. Tabella delle sonde rifatta con la colonna «vista dal circuito» e il baratto ampiezza/carico esplicitato.

---

## Lotto 14 — File-hub ✔ (2026-07-25)

**Ambito**: `Prove/Formulario rapido.md`, `Esercizi/Esercizi - Simulazione finale.md`, `Argomenti/00 - Perchè (spiegazione intuitiva).md`. Sono file **trasversali**: non citano il libro direttamente, derivano dai file di argomento. Frontmatter riformulato come «VERIFICATO ✔ per derivazione», con rimando ai lotti che hanno verificato le fonti.

> [!warning] Il conteggio dei segnaposto era sbagliato: erano **4, non 3**
> Il Lotto 12 dava per rimanenti tre file (`L'oscilloscopio`, `00 - Perchè`, `Esercizi - Simulazione finale`). Ne mancava uno all'appello: **`Prove/Formulario rapido.md`**, con lo stesso identico segnaposto «NON VERIFICABILE — PDF senza OCR». Sfuggito perché i conteggi precedenti giravano su `Argomenti` ed `Esercizi`, e questo file sta in **`Prove/`**. Da qui in avanti i grep di verifica includono tutte e tre le cartelle.

**Due correzioni non propagate, trovate nel formulario** — è il rischio strutturale di un file di sintesi: le correzioni dei lotti finiscono nella nota d'argomento e **il riassunto resta indietro**.

1. ❌ **Risonanza parallelo: `Z = R (max)` scritto senza condizioni.** È la stessa affermazione falsa corretta nel **Lotto 9** (Es. R4): dipende da **dove sta la resistenza**. Aggiunta la tabella a tre casi — $R$ in serie al ramo ($|Z|_{\min}=R$), $R$ in parallelo al serbatoio ($|Z|_{\max}=R$), $R$ in serie all'induttore, che è il caso **realistico** ($|Z|_{\max} = L/RC$, resistenza dinamica, e $\omega_0$ che si sposta di $\sqrt{1-CR^2/L}$ — la correzione del libro a p. 58).
2. ❌ **Mancava del tutto il fattore di ripple (form. 8.1).** Il formulario aveva solo $V_{r,pp} = I_L/(f_r C)$ — corretta, e coerente col libro — ma **non** $r = 1/(2\sqrt3 f R_L C)$, cioè proprio la formula la cui ignoranza aveva prodotto l'errore dell'Es. A1 nel **Lotto 10** (il «5%» letto come picco-picco invece che come rapporto fra valori **efficaci**, con una $C$ sbagliata di un fattore ~3,5). Aggiunta col riquadro che dice **quale delle due usare in base a come è formulato il testo**.

**Altre correzioni**:
3. `Esercizi - Simulazione finale`, **Es. E6**: «$I_{D1} = 91{,}9$ mA (scartata, sotto $V_T$)» era *ellittico*, non sbagliato — i conti sono stati rifatti tutti e tornano ($\Delta = 9{,}40$, $I_D = 23{,}7$ mA, $V_{DS} = -30{,}5$ V; seconda rete $V_{DS} = 0{,}7 < 4{,}7$ ⇒ triodo ✔). Riscritto in forma conclusiva mostrando *perché* si scarta: darebbe $V_{GS} = -11{,}6$ V, MOSFET interdetto, in contraddizione con l'$I_D$ di partenza — è la radice spuria introdotta dall'elevamento al quadrato.
4. `00 - Perchè` **§13** allineato al Lotto 13: capacità della sonda, compensazione ($R_sC_s = R_iC_i$ spiegata a parole), e **il reticolo**: «1 ms/div → lo schermo mostra **12 ms**» era in contraddizione con l'«8 divisioni» verticali dello stesso paragrafo. Il reticolo standard degli analogici è **10 × 8**: corretto a 10 ms, con la nota che certi digitali widescreen hanno 12 divisioni orizzontali.
5. `00 - Perchè` §13, trigger: «a metà ampiezza triggera su ogni **passaggio per lo zero**» (vero solo per segnali simmetrici sullo zero) e «schermo **bianco** o nero» riscritti sulla ragione vera — a metà ampiezza il segnale è **più ripido**, quindi l'istante di attraversamento è ripetibile — e distinguendo cosa si vede in NORMAL e cosa in AUTO.

---

## Lotto 15 — Manutenzione ✔ (2026-07-26)

**Ambito**: le tre voci lasciate aperte dal blocco «Manutenzione» dei Lotti 9, 10 e 11. Non è un lotto di bonifica (nessun argomento da riverificare): è il saldo di debiti tracciati. **Tutte e tre chiuse**, e due hanno prodotto scoperte non previste.

### 1. Form. 4.53 letta dall'immagine — la forma stampata **non** era quella del vault

Il legame $Q$–banda era localizzato dal Lotto 9 ma **mai letto dalla pagina**. Renderizzata la pagina-PDF **060**: folio **162-163**, testatina «**4 I quadripoli**», entrambi letti dal piè di pagina. Il vault dichiarava «p. 162» **per inferenza** (PDF 048 → 138-139 e PDF 050 → 142-143 ⇒ +2 per pagina): l'inferenza era giusta, ma restava un'inferenza.

La forma stampata è **in pulsazioni**:
$$Q = \frac{\omega_0}{\omega_{tH} - \omega_{tL}} \qquad (4.53)$$
mentre il vault (e edutecnica) la citano come $Q = f_0/B$. **Non è un errore**: il $2\pi$ si semplifica e le due forme sono identiche. È una **precisazione di forma**, registrata come tale e non come correzione — ma conta all'orale, dove va enunciata come sta scritta. Aggiunte anche le due formule vicine, mai censite: **4.52** $\xi = 1/2Q$ e **4.54** $\omega_0 = \sqrt{\omega_{tH}\omega_{tL}}$ (media **geometrica**, non aritmetica).

> [!note] Perché l'OCR non bastava, pur avendo «coperto» la pagina
> L'OCR di quella pagina è leggibile nella prosa ma rende la formula come `Q= (4.53)` seguito dalla stringa spuria `da Tn`: **il corpo della formula è perduto**. E i folio non sono catturati in nessuna delle 152 pagine — sono i numeroni d'angolo, che tesseract non estrae. Una fonte che funziona all'80% è più insidiosa di una inutilizzabile, perché non segnala dove smette di funzionare.
> *(Nota: la scansione è la cattura schermo di un lettore online — su ogni pagina una barra «Tieni premuto ESC…» copre la **testatina di destra**. Per questo il § di p. 163 non è confermabile: il vault dichiara «§3.2» e resta un dato ereditato.)*

### 2. I due allegati `cap6-pag80/90` — folio letti, e sono anche **orfani**

| Nome vecchio | Folio reale | Testatina | Nome nuovo |
|---|---|---|---|
| `libro-cap6-pag80-bjt-polarizzazione` | **328-329** | 7 *Gli amplificatori a transistor* / 1 *Il transistor bipolare (BJT)* | `libro-cap7-pp328-329-bjt-progetto-polarizzazione` |
| `libro-cap6-pag90-bjt-cc` | **348-349** | 7 *…* / 2 *Gli amplificatori a BJT* | `libro-cap7-pp348-349-bjt-collettore-comune` |

Sbagliati **due volte** ciascuno: capitolo (il BJT è il Cap. **7** — correzione del Lotto 4 mai propagata ai filename) e pagina. Entrambi ora rinominati; `00 - Fonti e note` §2 non ha più filename da verificare.

**Ma il fatto nuovo è un altro: nessuna nota li referenziava.** Erano in `Allegati/` da settimane senza che niente puntasse a loro — e il secondo è **la FIGURA 31 che `Amplificatori a BJT` cita nel testo senza mostrarla**. Entrambi sono stati agganciati dove servivano: le pp. 328-329 (PROCEDIMENTO + ESEMPIO 5, 2N2222) in `BJT.md` sotto la tabella delle formule 7.8-7.11, e le pp. 348-349 (FIGURA 31 + ESEMPIO 13) in `Amplificatori a BJT.md` subito dopo la frase che le nomina, entrambi con i valori dell'esempio trascritti in tabella.

> [!danger] Sesto difetto sistemico — **l'allegato orfano**
> Il join del Lotto 13 trova i **link senza file**. Non trova i **file senza link**: sono la direzione opposta della stessa relazione, e nessun controllo la copriva. Il controllo inverso:
> ```bash
> ls Allegati | while read -r a; do
>   grep -rqF "$a" Argomenti Esercizi || echo "ORFANO: $a"
> done
> ```
> Un orfano non rompe niente a schermo — per questo sopravvive. Ma qui nascondeva **una figura che il testo prometteva al lettore e non consegnava**.

### 2bis. Il controllo inverso ha subito trovato **altri due orfani** — e sotto c'era un errore vero

Alla prima esecuzione, il comando qui sopra ha segnalato due allegati che nessuno cercava: `libro-cap8-pp388-389-alimentatore-schema-blocchi.png` e `libro-cap8-pp408-409-tabella-78xx.png`. Sono **due dei tre file rinominati nel Lotto 10-11**: il rename aveva sistemato i nomi ma **non aveva mai agganciato le immagini alle note**.

Aprendo `Alimentatori.md` per collocarle è emerso il motivo per cui non se n'era accorto nessuno: la nota embeddava **due volte la stessa immagine** (`pp406-407`, righe 135 e 138) con due didascalie diverse, FIGURA 20 e FIGURA 21. In sé è legittimo — le due figure stanno sulla stessa apertura — ma dava l'impressione visiva che le immagini del Cap. 8 fossero al loro posto. **Il duplicato mascherava i due mancanti.**

❌ **E la TABELLA 1 non era la TABELLA 1.** La nota attribuiva alla «TABELLA 1, pp. 408-409» una tabella di quattro colonne con **7805, 7812, 7815, 7905, 7912**. Letta la pagina: la TABELLA 1 riguarda la **sola famiglia 78XX** — i **79XX non ci sono** — elenca anche 7806/7808/7818/7824/78G, e ha nove colonne, fra cui le tre che contano davvero:

- **$V_D = 2{,}5$ V (drop-out)**: «*in tutta la famiglia, la tensione d'ingresso deve essere sempre almeno 2,5 V superiore alla tensione che si desidera in uscita*»;
- **$R_r$ [dB]**, reiezione del ripple (62 dB per il 7805);
- **$I_{cc} = 1{,}2$ A**, corrente di cortocircuito.

I valori che c'erano non erano inventati, ma l'**attribuzione** era falsa: una tabella redazionale (con una colonna «Note» di commento) presentata come tabella della fonte. È il **difetto sistemico #3 in forma attenuata** — non un valore alterato, ma una paternità falsa. Sostituita con la TABELLA 1 vera, trascritta dall'immagine.

Recuperati nell'occasione anche l'**ESEMPIO 7** (dimensionamento di $C$ via $R_r$: 909 µF → 1000 µF commerciali), la **FIGURA 22** (alimentatore duale — è lì che entrano i 79XX) e la **FIGURA 23** (BJT esterno in Darlington per correnti elevate). E sulle pp. 388-389 la **form. 8.1** letta dalla pagina: $r = V_{Reff}/V_{Lm}$, **efficace su medio** — la definizione il cui equivoco aveva prodotto l'errore dell'Es. A1 nel Lotto 10.

> **Morale del controllo inverso**: è costato una riga di shell e ha trovato, in un file già dichiarato ✔ dal Lotto 10, un'attribuzione falsa alla fonte e due figure mai mostrate. I controlli che cercano ciò che *manca* pescano cose che i controlli su ciò che *c'è* non possono vedere.

### 3. Gli esercizi 6-7 di edutecnica — **erano già svolti**, e uno era sbagliato di 1000×

Il Lotto 9 aveva registrato che «non sono svolti nel vault, solo elencati». **È falso.** Sono svolti da sempre come **Es. F6** ed **Es. F7** in `Esercizi - Filtri passivi del primo ordine`, dove sono finiti perché vengono dal catalogo `filtripx`, la fonte della Parte B di quella nota. Il Lotto 9 li ha cercati nella nota dell'*argomento* (Reti RLC) invece che in quella della *fonte*, e non li ha trovati.

Scaricate e lette le soluzioni di edutecnica (sono immagini, `6.png` e `7.png` — le pagine HTML non contengono il testo). Confronto:

| | edutecnica | vault (prima) | esito |
|---|---|---|---|
| F6 $C$ | 316 pF | 316,7 pF | ✔ (arrotondamento) |
| F6 $Q$, $R$ | 50 · 25 k$\Omega$ | 50 · 25 k$\Omega$ | ✔ |
| F7 $Q$, $R$ | 20 · 220 $\Omega$ | 20 · 220 $\Omega$ | ✔ |
| **F7 $C$** | **362 pF** | **361,7 nF** | ❌ **sbagliato di 1000×** |

**Origine dell'errore, che è più interessante del refuso**: nei passi 1 e 3 la pulsazione era abbreviata in `628` invece di $628 \cdot 10^3$. Al passo 3 il risultato scritto restava giusto (220 $\Omega$) perché il conto vero era stato fatto a parte — la scrittura era sbagliata, non il numero. Al passo 1 invece **la potenza di dieci mancante è finita nell'unità di misura**, e «361,7 nF» ha l'aria di un valore plausibile: nessun controllo di ordine di grandezza lo segnala. Corretti entrambi i passi con $\omega_0$ scritta per esteso, aggiunti i controlli di plausibilità (220 $\Omega$ è E12; $|Z|_{\min}=R$ in serie, $|Z|_{\max}=R$ in parallelo).

Aggiunto inoltre a F6 l'avvertenza sul **modello di parallelo**: edutecnica usa $Q = R/(\omega_0 L)$, cioè $R$ **in parallelo** al serbatoio (FIGURA 13 del libro), non in serie all'induttore. È la distinzione dell'Es. R4 (Lotto 9) e del formulario (Lotto 14), che qui mancava. In `Esercizi - Reti RLC e risonanza` il rimando ora dice che sono svolti e dove.

> [!warning] Terza volta che un file di *sintesi* resta indietro rispetto ai file d'argomento
> Dopo le due correzioni non propagate del formulario (Lotto 14) e la numerazione di capitolo non propagata ai filename (punto 2 qui sopra), questa è la terza: `Esercizi - Filtri passivi` dichiara in testa «*Testi e soluzioni sono riscritti e ricontrollati; dove ho trovato errori li ho segnalati*» — e conteneva un errore di 1000×. **Un'affermazione di qualità dentro un file non è una verifica di quel file.**

---

## Fase Studio — Lotto 1: i diodi, dalle verifiche vere di Carli ✔ (2026-07-28)

**Non è bonifica.** La bonifica è chiusa col Lotto 15. Questo lotto apre la fase di studio, ma produce **sei correzioni** — e le correzioni si tracciano qui.

**Materiale nuovo**: tre fogli fotografati di **verifiche reali del Prof. Carli sui diodi**, due compiti alla classe **4E** (= sezione elettronica dell'articolata 4BEM, cioè *la tua* classe), **39 domande aperte**. Registrati come fonte in [[00 - Fonti e note]] §2, subito sotto la LETTERA. Prodotto: [[04 - Verifica tipo Carli — Diodi]] (trascrizione fedele · mappa 39 domande → 27 argomenti · risposte da compito · checklist dei 15 disegni).

### Gli 8 buchi di `Diodi.md` incrociati con le 39 domande

| # | Buco | Esito | Fonte letta |
|---|---|---|---|
| 1 | Limitatori — §6 aveva ~20 righe senza figure | riscritto: definizione del libro, i 4 casi a bassa soglia, serie ($n\cdot0{,}7$ V), antiparallelo, generatore | pp. 210-212, FIGURE 24-26 |
| 2 | I due meccanismi di breakdown | **aggiunto** §4: effetto Zener ($V_Z<5$ V) vs effetto valanga ($V_Z>6$ V), con la conferma del segno di $T_C$ in TABELLA 4 | **p. 220**, testatina «5 I diodi» |
| 3 | Legenda di Shockley (la formula era nuda) | aggiunta, 6 righe di legenda + effetto della temperatura | p. 198, form. 5.1 |
| 4 | Struttura PN e simbolo solo a parole | **aggiunte** FIGURA 5 e FIGURA 6 in §1/§2 con le checklist di disegno | **p. 196** |
| 5 | Versi convenzionali di $I_D$ e $V_D$ assenti | aggiunti | p. 197, FIGURA 7 |
| 6 | Zona inversa della curva non mostrata | risolto dalla FIGURA 7 (zone DIRETTA/INVERSA etichettate) + i sei punti del libro | p. 197 |
| 7 | Non linearità affermata ma non giustificata | aggiunta la giustificazione e la conseguenza operativa (saltano Ohm, sovrapposizione, Thévenin) | p. 192 |
| 8 | Schema del regolatore assente | **aggiunte** FIGURA 33 (blocco funzionale), FIGURA 34 (regolatore a Zener) e le form. **5.10**/**5.11** | **p. 221** |

### Le correzioni vere

**1 — Limitatore descritto con la polarità invertita.** §6 diceva che il «limitatore positivo con catodo sul segnale» impedisce all'uscita di superare $+0{,}7$ V: quel circuito conduce quando $v_o < -0{,}7$ V e limita quindi il picco **negativo**. Peggio: le tre configurazioni erano presentate tutte come parallelo, mentre il libro distingue **diodi in serie** (eliminano una semionda) da **diodi in parallelo** (tagliano un picco). Sono funzioni diverse, non varianti.

**2 — $0{,}6$ V e $0{,}7$ V usati come sinonimi.** Il libro li separa: $V_s \approx 0{,}6$ V è la **tensione di soglia** (p. 196), $\approx 0{,}7$ V è la **caduta a correnti normali**, il valore dei modelli A e B. La domanda A-D6 chiede la prima. Aggiunto il box che le distingue invece di uniformarle — uniformarle sarebbe stato «correggere» la fonte.

**3 e 4 — La LETTERA citata a memoria in `01` e `02`.** Entrambi i file portavano, in blockquote e introdotta da «*Dalla lettera di giudizio sospeso*», la frase *«Circuiti in corrente alternata, filtri passivi del primo ordine, transistor BJT / JFET / MOSFET, diodi»*. Non è la lettera: è una **fusione delle due prove**. Conseguenze concrete:
- in `01` metteva i **diodi nella prova scritta**, dove la LETTERA non li mette (li mette all'**orale**);
- in `02` metteva **BJT/JFET/MOSFET nell'orale**, che la LETTERA dedica a diodo + AC + filtri;
- in entrambi spariva «**a canale N**» e «**ad arricchimento**» — cioè proprio i limiti che escludono JFET a canale P e MOSFET depletion dal programma.

Testo riletto verbatim dal PDF originale della LETTERA e sostituito in tutti e due i file, ciascuno con la riga che gli compete.

**5 — L'istituto sbagliato.** `00 - Indice Generale.md` mandava a cercare il calendario sul sito del «Majorana **di Seriate**»: un altro istituto, in un'altra provincia. La LETTERA è protocollata dall'**IIS Ettore Majorana di San Lazzaro di Savena (BO)**, via Caselle 26. Corretto.

**6 — La fonte ufficiale puntava a un file che non esiste più.** `00 - Fonti e note` dava come riferimento della LETTERA `/tmp/lettera_giudizio.txt`, un estratto temporaneo ormai cancellato: la fonte più autorevole del vault era **non più verificabile**. Ora punta al PDF originale in `~/Scaricati/`, che ha lo strato di testo e si rilegge in ogni momento con `pdftotext -layout`. È la stessa lezione del difetto **#2**, applicata alle fonti invece che ai contenuti: *prima di dichiarare qualcosa verificato, controlla che resti verificabile*.

> [!danger] Sesto difetto sistemico — la **citazione ricostruita a memoria** (3 occorrenze)
> Una fonte viene parafrasata, poi la parafrasi viene presentata come **citazione testuale** e usata come vincolo. È diversa dalla *conferma fabbricata* (difetto #3, che altera un numero per vincere un ragionamento): qui non c'è tesi da sostenere, c'è solo una fonte riassunta e poi promossa a verbatim.
> - `01` e `02` — la riga della LETTERA, fusa e con i qualificatori persi (sopra).
> - Stessa radice del `/tmp/lettera_giudizio.txt`: la fonte era stata letta **una volta**, poi il vault ha continuato a citarla senza poterla riaprire.
>
> **Regola**: se una riga è tra virgolette o in blockquote, deve essere **riapribile**. Il file da cui viene si scrive accanto, e dev'essere un file che esiste ancora.

### Ricalibratura del formato — non è un cambio di programma

Le verifiche di Carli sono **interamente a domande aperte con disegni, zero esercizi numerici**, mentre `01` prometteva «la prova più computazionale, esercizi numerici». Callout aggiunto in testa a `01`, che **affianca** senza cancellare: sono verifiche **in corso d'anno**, provano *come Carli interroga*, non *cosa* entra nel recupero. Sullo **scope** comanda la LETTERA. **21 domande su 39 iniziano con «Disegnare»**: è il dato che cambia il modo di prepararsi.

### Registrazione

[[00 - Fonti e note]] (nuova fonte, il fatto 4E ≡ 4BEM, 6 righe nuove in §2bis coi folio letti) · [[02 - Prova Orale Carli]] (sezione diodi, 39 domande smistate in 🟢/🟡/🔴) · [[01 - Prova Scritta Carli]] (ricalibratura + citazione) · [[00 - Indice Generale]] (riga `04`, mappa argomenti, calendario) · [[Esercizi - Diodi]] (la Parte A rimanda al banco vero, non lo duplica).

### Controllo di fedeltà della trascrizione (2026-07-28, dopo la chiusura del lotto)

Le tre foto sono state **riaperte e confrontate riga per riga** con il §1 di `04`. Esito:

- **Integrità dei file**: le copie in `Allegati/` sono **byte-identiche** agli originali in `~/Scaricati/` (MD5 confrontati, 3 su 3). Il vault è autoconsistente e non è stata persa qualità nella copia.
- **Le 39 domande sono fedeli**, refusi compresi: il «Modello A,;» di C-D13 c'è, la punteggiatura strana di C-D20 pure.
- **Due affermazioni non erano sul foglio** — corrette:
  1. `04` diceva «**Entrambi i fogli** portano lo stesso riferimento *«…con riferimento sul libro capitolo 5…»*». Il **Foglio A non lo porta**: la sua consegna finisce a «in modo esaustivo:». Il riferimento è dei soli Fogli B e C.
  2. Il **Foglio A ha il campo CLASSE in bianco** — è il modulo vuoto della verifica. «Classe 4E» è stampato solo su **B e C**. Il vault attribuiva a tutti e tre i fogli una classe che due soli documentano. Ora la distinzione è scritta in `04`, nel suo frontmatter e in [[00 - Fonti e note]].
- **Tre slip di trascrizione** — sistemati: l'intestazione del Foglio A scrive «PROF**:** CARLO CARLI» (due punti, non il punto); C-D17 ha un **punto spurio** in mezzo alla frase («i circuiti limitatori**.** a bassa soglia») che era stato tolto in silenzio; il Foglio C scrive «dei **transistor** BJT» dove il Foglio B scrive «dei **transistori** BJT», e `04` liquidava la cosa con «stessa intestazione».

> Nessuno dei cinque cambia una risposta. Ma sono tutti la stessa cosa: **il documento raccontato invece che riportato**. Il caso 1 è il difetto #3 in versione mite (attribuire alla fonte una frase che non c'è), il caso 2 è il difetto #6 appena aperto (una parafrasi promossa a dato). Se la regola di trascrizione dichiarata in testa a `04` §1 dice «verbatim, refusi compresi», allora **è quella regola a dover reggere il controllo**, non le domande.

> [!note] Voce cosmetica lasciata aperta
> Il ritaglio `libro-cap5-p196-fig6-polarizzazione-diretta-inversa.png` include, in basso a destra, una striscia della barra del visualizzatore PDF usata per il ritaglio. Non copre contenuto della figura (i due circuiti e la nota $I_0 \approx 0$ sono interi) ed è l'unico dei 9 ritagli nuovi con questo difetto. Da rifare se dà fastidio in lettura.

---

## Lotti successivi

---

## Lotto 16 — Chiusura gap Esercizi trasversali e pulizia vault ✔ (2026-07-28)

> **Contesto**: Intervento di chiusura per (a) allineare i 3 file Esercizi che non avevano il campo `libro_mirandola` in frontmatter pur citando Mirandola nel corpo, e (b) ripulire 9 file residui in `.trash/`. È un lotto di **manutenzione**, non di verifica contenuto: nessuna formula ricalcolata. Tutte le affermazioni sono già state verificate nei Lotti 10, 11, 12.

### ❌ Correzioni di contenuto

1. **Frontmatter dei 3 Esercizi trasversali riallineati** — i file `Esercizi - Alimentatori.md`, `Esercizi - JFET.md`, `Esercizi - MOSFET.md` avevano solo `fonte: "edutecnica.it/..."`. I corrispondenti `Argomenti/*.md` (Lotti 10, 11, 12) sono dichiarati *«file trasversale… ciascuno verificato sul Mirandola nei Lotti 1-13 della bonifica»* — e quei Esercizi si appoggiano direttamente su quegli Argomenti. Aggiunti, in ognuno, il campo `libro_mirandola: VERIFICATO ✔ (2026-07-28)` con mappa puntuale di capitolo, pagine e figure:
   * `Esercizi - Alimentatori.md` → Cap. 8 «Gli alimentatori», §1, §3.1, §3.2, §3.3, ESEMPIO 7 (form. 8.1, FIG. 20-21, TAB. 1, pp. 388-409).
   * `Esercizi - MOSFET.md` → Cap. 7 §3.3 «MOSFET e porte CMOS», FIG. 45-50 (pp. 366-368).
   * `Esercizi - JFET.md` → Cap. 7 §3 parte JFET, FIG. 42 al 2N3819 (pp. 358-365).
2. **Conferma diretta del refuso di edutecnica Es. 3 (Alimentatori)** — il file `Esercizi - Alimentatori.md` Es. A3 dichiara: «edutecnica scrive $C = 12$ mF, il valore corretto è $1{,}2$ mF (refuso ×10)». Il 2026-07-28 la pagina <https://www.edutecnica.it/elettronica/alimentatorix/alimentatorix.htm> è stata scaricata con `curl -L -A 'Mozilla/5.0'` e la risposta boxed per l'esercizio 3 è confermata essere `[ 12 mF ]` (sotto la stessa ipotesi del vault: $V_L = 12$ V, $R_L = 50$ $\Omega$, $V_{rpp} = 2$ V, doppia semionda). La pagina di dettaglio `3.htm` mostra solo la risposta boxed senza svolgimento. Il calcolo del vault ($C = I_{load}/(2 f V_{rpp}) = 1{,}2$ mF) **regge**: nessuna modifica di sostanza al riquadro esistente, aggiunta solo un'annotazione di conferma.

### 🧹 Correzioni formali e manutenzione

- **Pulizia `.trash/`** — rimossi 9 file: 8 placeholder da 0 byte generati da rename/click accidentali (`Il metodo simbolico.md`, `Impedenza dei bipoli R, L, C.md`, `L'oscilloscopio.md`, `Reti RLC e risonanza.md`, `Segnali sinusoidali e fasori.md`, `coupling-dc-ac.png.md`, `oscilloscopio-schema.png.md`, `crea un collegamento.md`) e 1 file di benvenuto predefinito di Obsidian (`Benvenuto.md`, 214 byte). Nessuno era referenziato attivamente da altri file. La presenza di `coupling-dc-ac.png.md` e `oscilloscopio-schema.png.md` era già stata identificata nel Lotto 13 (false-positive trappola per i link a immagini mancanti): ora anche il *sintomo* è stato rimosso.
- **Frontmatter del registro** — `aggiornato: 2026-07-28`, data di chiusura di questo lotto.

### ✅ Post-condizioni raggiunte

* **27 file su 27** delle cartelle Argomenti (14) + Esercizi (13) hanno ora `libro_mirandola: VERIFICATO ✔` esplicito.
* **4 file su 9** delle Prove hanno `libro_mirandola: VERIFICATO ✔` (`00 - Audit e correzioni`, `00 - Fonti e note`, `04 - Verifica tipo Carli`, `Formulario rapido`).
* **5 file** NON hanno `libro_mirandola` perché non hanno claim specifici sul libro: 2 hub radice (`Argomenti.md`, `Esercizi.md`) che sono MoC di navigazione, 1 hub Prove (`00 - Indice Generale.md`), 3 Prove Carli/Protti (che pur citando Mirandola nel corpo non hanno il campo in frontmatter), 1 confronto comparativo (`Cheat Sheet A4 visuale.md`). Le 3 Prove Carli/Protti **potrebbero** ricevere il campo in un Lotto futuro non appena si decide se la loro natura di scaletta d'esame lo richieda.
* **`.trash/` vuoto.**
* La verifica del claim di Es. A3 è **documentata e ripetibile** (comando `curl` registrato).

### ⚠️ Da ricontrollare (non bloccante)

* **Lotto 13 «falsi positivi delle caption»** — chiuso dal **Lotto 17** (2026-07-28): il riferimento `![[oscilloscopio-schema.png]]` descritto qui è stato nel frattempo **sostituito** in `Argomenti/L'oscilloscopio.md` (sezione 1: schema a blocchi dell'oscilloscopio; sezione 3: AC/DC coupling) da diagrammi `mermaid`. La riga qui sopra diventa registro storico di un problema **superato**; vedi il Lotto 17 per la verifica.
* Il file `04 - Verifica tipo Carli — Diodi.md` è stato trascritto verbatim (Lotti Fase Studio) ma non era stato controllato per caption rotte con lo stesso pattern del Lotto 13. Chiuso dal **Lotto 17**: scrutinio OK, nessuna caption rotta identificata (0 match sui pattern Lotto 13, 0 jpeg embed orfani, 0 caption di FIGURA senza pagina).
* Le verifiche numeriche delle 39 domande Carli sui diodi non sono state confrontate con dati di datasheet reali dei componenti citati (2N2222, 1N4148, BZX55C × 7 sigle di V_Z). Da fare solo se gli esercizi di recupero li richiedono; non bloccante per la prova orale Carli.

---

## Lotto 17 — Verifica dei gap «da ricontrollare» del Lotto 16 ✔ (2026-07-28)

> **Contesto**: Il **[[#Lotto 16 — Chiusura gap Esercizi trasversali e pulizia vault ✔ (2026-07-28)|Lotto 16]]** aveva registrato 2 punti come «Da ricontrollare»: (a) la reference orfana `![[oscilloscopio-schema.png]]` (che il **[[#Lotto 13 — L'oscilloscopio ✔ (2026-07-25)|Lotto 13]]** narrava come sintomo di link a immagini mancanti), e (b) lo scrutinio delle caption di `Prove/04 - Verifica tipo Carli — Diodi.md` per lo stesso pattern di falsi positivi del Lotto 13. Entrambi i punti vengono qui **chiusi**.

### Sub-task (a) — Wikilink-immagine orfano `![[oscilloscopio-schema.png]]`

**Verifica di esistenza** (2026-07-28):
* `grep -rn 'oscilloscopio-schema' Argomenti Esercizi Prove` restituisce **solo righe dentro questo file di audit** (registro Lotto 13, voce Lotto 16 «da ricontrollare», Lotto 16 «pulizia .trash», e ora anche questo Lotto 17) — tutte in **contesti backtick code-literal**, dove la sintassi image-embed **non è resa** da Obsidian. Diffuse in un controllo Python-aware (cfr. blocco `RAFFORZATO` qui sotto), si conferma che **non esiste alcuna reference resa** (cioè che Obsidian interpreterebbe come image-embed attivo) di `![[oscilloscopio-schema.png]]` nei 27 file di contenuto del vault.
* Leggendo integralmente `Argomenti/L'oscilloscopio.md` (242 righe) si osserva che la sezione §1 «A cosa serve» e la sezione §3 «AC vs DC coupling» sono state rifattorizzate da PNG a **diagrammi `mermaid`** nativi di Obsidian. Le mermaid sostituiscono egregiamente lo schema a blocchi e il confronto AC/DC che l'immagine intendeva mostrare — niente di utile va perso.
* Il Lotto 13 aveva basato il proprio verdetto su una **reference che nel frattempo è stata rimossa** (probabilmente durante uno dei molteplici pass di bonifica del 2026-07 tra i **[[#Lotto 7 — Le potenze in alternata ✔ (2026-07-20)|Lotti 7]]** e il 15). Il Lotto 13 resta **storicamente corretto** al momento della sua scrittura: la stringa `![[oscilloscopio-schema.png]]` *esisteva davvero* come testo nel vault (reso o meno a seconda del viewer); ciò che il Lotto 17 corregge è la sua interpretazione attuale — oggi non rende più un broken-embed perché la stringa non è più in linee-rendering di alcun file di contenuto.

**Decisione operativa**:
* Nessuna azione di creazione immagine (la mermaid è già sul posto).
* Nessuna azione di rimozione reference (è già stata rimossa).
* **Aggiornamento del Da-ricontrollare del Lotto 16** (vedi sopra): il reference aria-oramai-non-più-orfano è marcato «chiuso dal Lotto 17».

### Sub-task (b) — Scrutinio caption di `04 - Verifica tipo Carli — Diodi.md`

**Method**:
1. `grep -E 'vedi teoria generale|NON VERIFICABILE|NON verificabile|fuori programma|non lo tratta|non ce l'ha|nella tua scansione'` → **0 match** (i pattern del Lotto 13 non compaiono).
2. `grep -E 'vedi libro|vedi testo|vedi pag'` → **0 match**.
3. `grep -E '\\u2014|\\u00d7|\\u00b1'` (escape rotti) → **0 match**.
4. Tutte le 3 immagini embed esistono in `Allegati/`:
   * `verifica-carli-diodi-16dom.jpeg` ✔
   * `verifica-carli-4E-diodi-parte1.jpeg` ✔
   * `verifica-carli-4E-diodi-parte2.jpeg` ✔
5. Tutti i wikilink-immagine a figure del libro (es. `libro-cap5-p196-fig5-struttura-simbolo-diodo.png`) sono stati verificati nel Lotto 3 (Diodi) e nel Fase Studio Lotto 1.
6. Tutte le caption FIGURA citate nella §3 specificano la pagina del libro Cap. 5. Le 22 caption FIGURA trovate coprono pp. 196, 197, 198, 205, 206, 211, 212, 219, 220, 221 — tutte coerenti con la mappa sezioni Cap. 5 del `[[00 - Fonti e note]] §2bis`.
7. **Nessuna caption cita una FIGURA X senza indicare la pagina** (tranne quelle che rimandano alla mappa §2, che è il comportamento atteso).
8. **Nessuna caption cita «FIGURA N» con un numero incoerente con la numerazione progressiva del libro** (FIGURA 5-8 nella §1, FIGURA 17-26 nella §2, FIGURA 32-34 nella §4 — la numerazione è continua e attesa).
9. Caso FIGURA 8 a p. 198 (citata nella risposta A-D6) — è la curva $V_s$ vs $T$ della §1.3 (successiva alla FIGURA 7 della caratteristica generale, sempre in Cap. 5); la pagina 198 è confermata dalla mappa del Lotto 3.

**Decisione operativa**:
* **Nessuna caption rotta.** Il file è pulito al livello richiesto dal pattern del Lotto 13 e oltre.
* Aggiornamento del Da-ricontrollare del Lotto 16 (vedi sopra): il punto «scrutinio caption di 04» è marcato «chiuso dal Lotto 17».

### ✅ Post-condizioni raggiunte

* I 2 punti del «Da ricontrollare» del Lotto 16 sono **chiusi**.
* Il vault non ha più alcuna **occorrenza resa** (cioè che Obsidian interpreterebbe come image-embed) dell'orfano `![[oscilloscopio-schema.png]]`. Le 3 menzioni della stringa nei Lotti 13, 16 e 17 sono tutte **dentro backtick code literal** in linee narrative del registro audit stesso, dove la sintassi è discussa senza essere renderizzata: nessuna di esse è un embed attivo.
* Il grep naive `grep -roh '!\\[\[' Argomenti Esercizi Prove` restituisce **1 riga «ORPHAN»** perché non distingue code literal da embed reale. Tutte e 1 le righe sono in `Prove/00 - Audit e correzioni.md` dentro contesto backtick (verificabile con `grep -n '!\[\[' Allegati/...`).Un grep **rafforzato** (esclude contesto backtick) restituisce 0 ORPHAN. Il comando rafforzato è documentato qui sotto.
* I 3 file `verifica-carli-*.jpeg` referenziati in 04-Verifica-Carli **esistono** e **risolvono correttamente** in `Allegati/`.
* **27/27 Argomenti+Esercizi** hanno `libro_mirandola: VERIFICATO ✔` (post-Lotto 16, confermato).
* Il registro audit `00 - Audit e correzioni.md` ha il frontmatter `aggiornato: 2026-07-28` aggiornato al Lotto 16.

### 🔬 Verifiche eseguite in data 2026-07-28

```bash
# a) Orphan reference check su TUTTI i file di contenuto
grep -roh '!\[\[[^]]*\]\]' Argomenti Esercizi Prove | sort -u | while read ref; do
  file=$(echo "$ref" | sed 's/!\[\[//;s/\]\]//')
  [ ! -f "Allegati/$file" ] && echo "ORPHAN: $ref"
done
# Risultato (GREP NAIVE): 1 ORPHAN — la menzione letterale `![[oscilloscopio-schema.png]]` backtick-quoted in questo stesso file di audit.
# È un falso positivo di contesto: la stringa non è in una linea-rendering, ma in block-code/backtick.
# Per il conteggio corretto (0 ORPHAN), vedi il blocco bash (a-RAFFORZATO) sotto, che esclude i contesti backtick del registry.

# b) Validazione I 3 jpeg embed di 04-Verifica-Carli
for img in verifica-carli-diodi-16dom.jpeg verifica-carli-4E-diodi-parte1.jpeg verifica-carli-4E-diodi-parte2.jpeg; do
  test -f "Allegati/$img" && echo "OK: $img" || echo "MISSING: $img"
done
# Risultato: 3 righe "OK:".

# c) Pattern Lotto 13 nelle caption di 04-Verifica-Carli
grep -E 'vedi teoria generale|NON VERIFICABILE|\\u2014|vedi libro' "Prove/04 - Verifica tipo Carli — Diodi.md"
# Risultato: 0 match.
```

### ⚠️ Da ricontrollare (non bloccante)

* **Cross-link al §13 della spiegazione intuitiva**: il file `Argomenti/00 - Perchè (spiegazione intuitiva).md` cita l'oscilloscopio in §13 (sonda). Andrebbe verificata la coerenza tra §13 e il file appena riconsiderato. Non bloccante per lo studio.
* **Verifica dei 22 file `fig-2-*`** (Cap. 2 figure fasori, impedenze, ecc.) — già coperti dal Lotto 1 e 2 nel 2026-07-19, ma da ricontrollare che nessuno sia stato rinominato male in un commit successivo. Pattern di controllo: `for fig in Allegati/fig-2-*.png; do basename "$fig" | grep -F "[[ ../../$fig ]]" 2>/dev/null || true; done`.
* **Aggiungere `allegato_index.md`** che elenchi tutte le 74 immagini con il loro file richiedente — il Lotto 15 ha già mezzo-implementato un controllo inverso; consolidarlo in un documento Allegati/INDEX.md aiuterebbe i futuri audit.

---

**Nessuno: la bonifica è completata.** ✅ Tutti e 13 gli argomenti del vault più i tre file-hub sono stati incrociati con la fonte. Verifica finale eseguita il 2026-07-25: **zero segnaposto** «NON verificabile / vedi teoria generale» in `Argomenti`, `Esercizi` e `Prove` (le sole occorrenze superstiti sono la **prosa storica di questo log**, che documenta i segnaposto rimossi); **zero embed rotti**; **zero embed vuoti**.

> **Manutenzione: chiusa col Lotto 15 (2026-07-26).** Le tre voci che erano aperte qui — la form. 4.53 mai letta dall'immagine (Lotto 9), il folio dell'allegato `libro-cap6-pag80-*` (Lotti 10-11) e gli esercizi 6-7 di edutecnica — sono tutte risolte; due hanno prodotto correzioni vere (un errore di 1000× in `Esercizi - Filtri passivi` Es. F7 e due filename sbagliati di capitolo *e* di pagina). Vedi il **Lotto 15** qui sopra.
>
> **Resta una sola voce, non azionabile da qui**: i due diagrammi Mermaid di `L'oscilloscopio` sostituiscono immagini mai esistite. Se in laboratorio fai una foto dello strumento vero, vale la pena aggiungerla accanto.
>
> **Il vault è verificato. Da qui in poi il lavoro è studiare, non auditare** — le checklist delle tre prove in `Prove/` sono ancora tutte da spuntare.
>
> ▶ **Fase studio avviata il 2026-07-28** col **Lotto 1 — Diodi** (qui sopra), unico argomento su cui è entrato materiale d'esame reale. Il lotto successivo si decide **dopo** aver fatto il Foglio A a mano: è quella prova a dire dove sono i buchi veri, non un'altra rilettura del vault.

> ✅ **Chiarito il conteggio degli embed vuoti**: i «~30 embed vuoti» (di cui 16 in JFET) segnalati nel Lotto 3 **non esistono** con i pattern attuali — verificato nel Lotto 12 che `JFET.md` e `Esercizi - JFET.md` non contengono alcun `![[]]` né `` inline vuoti. Erano probabilmente già stati riempiti o contati con un pattern diverso. **Il Lotto 13 ha però mostrato che quel pattern era comunque cieco** rispetto agli embed *rotti*: vedi il quinto difetto sistemico.

> **Difetto sistemico confermato su sei lotti.** I «ragionamenti lasciati a metà» erano in `Esercizi - Diodi` (Z2, Z9, Z3), in `BJT` (§4, Es. 1, Es. B3, Es. B4), in `Esercizi - Filtri` (Es. F3), in `Esercizi - Reti RLC` (Es. R4), in `Esercizi - Alimentatori` (Es. A1, Es. A3) e in `Esercizi - JFET` (Es. J5). In **due** casi (A3 e J5) la reticenza nascondeva la scoperta opposta al solito: **il vault aveva ragione e la fonte esterna torto** — edutecnica $12$ mF (giusto $1{,}2$) ed edutecnica $R_2=123$ k (giusto $\approx 8{,}1$ k, i 123 k danno $V_{GS}=+7$ V impossibile) — ma il vault si auto-sminuiva con un «forse» invece di concludere. Nel Lotto 10 un caso (A3) nascondeva la scoperta opposta al solito: **il vault aveva ragione e la fonte esterna torto** (edutecnica $12$ mF = refuso ×10; il valore giusto, già scritto dal vault, era $1{,}2$ mF), ma il vault si auto-sminuiva con un «forse» invece di concludere. In **sei** casi su nove nascondevano un errore reale, non solo prosa sciatta: un errore dimensionale (Diodi 2c), un errore concettuale invertito (BJT Es. 4 MOSFET), una mescolanza di modelli (BJT B4), due accuse infondate a edutecnica (Diodi Z9, BJT B4) e **due ipotesi entrambe sbagliate** presentate come alternative plausibili (Filtri F3: né la serie né $(R_1+R_2)\parallel R_3$ davano i 34,5 kHz — la risposta era $(R_1\parallel R_2)+R_3$) e una **conclusione falsa lasciata implicita** (Reti RLC R4: nel parallelo reale $|Z|$ a risonanza non è $R$ ma $L/RC$). Cercarli in ogni lotto con:
> ```
> grep -rn "aspetta\|discrepanza\|probabilmente\|errore edutecnica\|\.\.\." Argomenti Esercizi
> ```
> **Corollario operativo**: quando il vault accusa una fonte di un errore, **rifare i conti prima di crederci**. Bilancio aggiornato al Lotto 12: edutecnica **scagionata 6 volte, condannata 3** — Es. P2 (testo a 220 V, risposte a 200 V), Es. A3 alimentatori (12 mF invece di 1,2 mF, refuso ×10) ed Es. J5 JFET ($R_2=123$ k invece di $\approx 8{,}1$ k, errore di segno su $V_{GS}$); scagionata sull'Es. A1 (i suoi 2,31/11,56 mF sono corretti, il vault aveva sbagliato la definizione di «ripple»). ⚠️ **Non è quindi una regola universale**: nel Lotto 6 le due accuse al *libro* si sono rivelate **fondate** (segni invertiti negli esercizi 9-10), e nel **Lotto 8 tutte e tre** le accuse al libro sono state confermate sull'immagine (form. 4.45/4.47 con $L/R$ al posto di $R/L$; testo del passa alto RC invertito). Il difetto del vault lì non era l'accusa, era la **diagnosi**: fermarsi a «refusi o convenzione diversa» invece di notare che un solo errore spiegava entrambi i casi. Rifare i conti serve a *decidere*, non a scagionare per default.

> [!danger] Terzo difetto sistemico — la **conferma fabbricata** (2 occorrenze, entrambe scoperte aprendo le immagini)
> Il vault **altera silenziosamente un valore della fonte** e poi cita la versione alterata come prova indipendente della propria tesi.
> - **Lotto 6**: riscrive il numeratore del libro da $12$ a $12{,}2$, poi usa la discrepanza così creata per dichiarare «incoerenza di stampa» del libro.
> - **Lotto 7**: riporta la risposta stampata dell'es. 11 come $Q = -87{,}6$ µVAR (il libro stampa $+87{,}6$), poi la cita — «lo conferma il libro stesso» — per dimostrare che l'ESEMPIO 6 sbaglia.
>
> In **entrambi i casi la tesi di fondo era difendibile**, ma il sostegno era inventato. È il difetto più insidioso dei tre, perché produce note che *sembrano* verificate e che **non si possono smascherare leggendo il vault**: serve tornare alla pagina.
> **Regola operativa**: ogni riga che riporta un valore *stampato* nella fonte (risposte fra parentesi quadre, risultati degli esempi) va **letta dall'immagine**, mai dedotta né «corretta» in silenzio. Se il valore stampato è sbagliato, si riporta com'è e si segnala a parte — non lo si riscrive.

> [!danger] Secondo difetto sistemico — «il libro non ce l'ha» (**4 occorrenze su 8 lotti**)
> Il vault dichiara assente dal libro materiale che **è presente**: Lotto 1 e Lotto 6 («il Cap. 3 non è nella scansione» — c'è, p. 102); Lotto 5 («il libro non tratta la base comune» — la tratta, FIG. 33 pp. 350-351); **Lotto 8** («la scansione non contiene gli esercizi del Cap. 4, le pp. 184-191 mancano» — ci sono tutte, pagg.-PDF 71-74). In tutti e quattro i casi l'affermazione serviva a **giustificare una lacuna** del vault.
> Cercarlo in ogni lotto con:
> ```
> grep -rn "non è nella scansione\|non è presente\|il libro non tratta\|non c'è nel libro" Argomenti Esercizi
> ```
> **Corollario**: «fuori programma» e «assente dal libro» sono affermazioni diverse. La prima si ricava dalla lettera Majorana, la seconda **solo** aprendo il PDF.

> [!warning] Problema trasversale scoperto nel Lotto 3 — riguarda quasi tutti i file rimanenti
> Nel vault restano **~30 embed di immagine vuoti** (` `` `): **JFET 16**, **Alimentatori 8**, **BJT 4**, **MOSFET 2**, **Amplificatori a BJT 2**, **Esercizi - JFET 2**. Le 5 immagini di pagina già in `Allegati/` (cap6/cap7/alim) **non sono referenziate da nessuna nota** e hanno probabilmente **numeri di pagina sbagliati nel filename**, come quelle del Cap. 5: verificare il folio reale prima dell'uso.
>
> **Metodo stabilito**: `pdftoppm -f N -l N -r 200 -x X -y Y -W W -H H -png` ritaglia la singola figura direttamente dal PDF, senza ImageMagick. Costo ~20-50 KB per figura contro 1,2 MB per pagina intera.
---

## Lotto 19 — Re-crop massivo 9 immagini integrali ✔ (2026-07-28)

> **Contesto**: richiesta utente «le immagini siano tagliate bene (se non lo sono ritagliale nuovamente dal pdf allegato)». Identificate **9 immagini in `Allegati/` di peso ≥ 500 KB, dimensioni 2339×1584 px**: erano pagine intere PDF renderizzate a 200 dpi — non figure ritagliate. Tutte referenziate da `Argomenti/*.md` via `![[...]]`.

### Asset toccate e risultati

| Immagine | Origine (KB) | Finale (KB) | % | Note |
|---|---:|---:|---:|---|
| `libro-cap4-pp180-181-rumore-johnson-shot.png` | 1 471 | **273** | 18 % | OCR Johnson/Shot → §6 rumore sx |
| `libro-cap5-pp208-209-fissatore-moltiplicatore.png` | 1 211 | **643** | 53 % | OCR clamper → FIG 21 + §2.4/2.5 intera |
| `libro-cap5-pp228-229-zener-esempio-formule.png` | 1 224 | **629** | 51 % | OCR Formule → Zener sx + tab dx |
| `libro-cap7-pp328-329-bjt-progetto-polarizzazione.png` | 678 | **628** | 93 % | OCR PROCEDIMENTO+2N2222 → entrambe le metà |
| `libro-cap7-pp348-349-bjt-collettore-comune.png` | 501 | **362** | 72 % | OCR FIGURA+collettore → entrambe |
| `libro-cap7-pp368-369-mosfet-polarizzazione-invertitore.png` | 1 151 | **207** | 18 % | v1 KO (header §3.3); `fix2` aggancia `FIGURA 48` → enhancement |
| `libro-cap8-pp388-389-alimentatore-schema-blocchi.png` | 1 018 | **387** | 38 % | OCR alimentatore+FIGURA → schema a blocchi |
| `libro-cap8-pp406-407-regolatore-integrato-78xx.png` | 1 040 | **492** | 47 % | OCR 78+Zener → FIG 20 sx + FIG 21 dx |
| `libro-cap8-pp408-409-tabella-78xx.png` | 1 055 | **616** | 58 % | **TABELLA 1 è grafica pura** (no testo OCR-friendly); `fix3` adotta crop ampio 15–85 % Y × full-width per inclusione |
| **Totale** | **9 351** | **4 237** | **45 %** | — |

### Metodo OCR-guided (verificato dal thinker)

Per ogni immagine, mappata alla pagina PDF con le formule di conversione già verificate nei lotti precedenti:

```text
Cap. 4: stampata = 2·PDF + 42         (PDF 69  = pp. 180-181)
Cap. 5: stampata = (PDF-75)·2 + 192   (PDF 83  = pp. 208-209; PDF 93 = pp. 228-229)
Cap. 7: stampata = 2·PDF + 122         (PDF 103, 113, 123)
Cap. 8: stampata = 2·PDF + 122         (PDF 133, 142, 143)
```

Pipeline:

1. `pdftoppm -f N -l N -r 200 -singlefile -png` (200 dpi, ~2339×1316 px, file singolo niente suffixing)
2. Thumbnail via PIL (max-side 900 px) per OCR veloce (`tesseract -l ita TSV`)
3. Scala coordinate `thumb → HD` (`scale = W_hd / W_thumb`)
4. `crop_with_padding(hd_img, hit, mode)` con `pad_x=80, pad_y=400`
5. **Backup persistente** in `~/recrop_backups/` prima di sovrascrivere (risolve problema `/tmp`)
6. Verifica OCR sul crop finale (almeno metà delle `verify_kws` ritrovate)

### Casi limite gestiti e fix applicati

* **p123 (MOSFET polarizzazione FIG. 48A)**: `recrop.py` v1 ha agganciato la keyword `MOSFET` caduta sull'header §3.3 della pagina adiacente (depletion, non enhancement). `recrop_fix2.py` con anchor `FIG.48` e ricerca nella sola metà sinistra ha trovato la riga `FIGURA 48 Circuito di polarizzazione del MOSFET: A) enhancement; B) depletion.` → 207 KB. ✔
* **p143 (TABELLA 1 famiglia 78XX)**: la tabella è un **elemento puramente grafico** (9 colonne × n righe stampate) — la parola «TABELLA» non compare nel testo OCR-friendly. `recrop.py` v1 non trova la tabella; `recrop_fix3.py` adotta **strategia "good enough by inclusion"**: `Y in [15%, 85%]` × full-width → assicura la cattura della tabella, accetta un crop più ampio (~616 KB) che include anche FIGURA 22 adiacente — comunque leggibile.

### Sviluppi futuri (dal code-reviewer)

* **LOTTO 19° — problema n. 1** (tabelle grafiche): per future tabelle la soluzione robusta è **PIL connected-components**: rileva la regione rettangolare non-bianca più ampia nella metà attesa → bounding box deterministico, indipendente dal riconoscimento testuale OCR.
* **LOTTO 19° — problema n. 2** (cy-scarto OCR-keyword): `tesseract TSV` restituisce bbox di livello 4 (LINE) largo quanto un'intera riga OCR. Per centrare il crop sulla keyword reale serve filtrare `level == 5` (WORD), abbassando lo scarto di cy di ~50–150 px.
* **LOTTO 19° — problema n. 3** (UX): implementare `--dry-run` per testare senza rischio di sovrascrittura; centralizzare in un modulo condiviso `recrop_lib.py` (oggi `render`, `tsv_rows`, `ocr_text`, `save_optimized` sono duplicati in 3 script).

### Verifica finale

* Le 9 immagini re-croppate sono **tutte ancora presenti in `Allegati/`** con filename invariato ⇒ **nessun link rotto** (i wikilink `![[…]]` continuano a risolvere).
* `image-link count` (join fra wikilink ed esistenza file): **0 rotti** — escluso il già-noto falso positivo `![[oscilloscopio-schema.png]]` documentato nel **Lotto 17** (il riferimento è stato sostituito da diagrammi `mermaid` in `Argomenti/L'oscilloscopio.md`).
* I link interni `[[Argomenti/...]]` / `[[Esercizi - ...]]` / `[[Prove/...]]` continuano a risolvere (la struttura del vault non è stata toccata in questa sessione).
* 9 backup originali pesanti **spostati** da `/tmp/recrop_work/` a `~/recrop_backups/` per evitare perdita originals su cleanup di `/tmp`.
## Lotto 19 (Addendum) — Fix definitivo `libro-cap8-pp408-409-tabella-78xx.png` ✔ (2026-07-28)

> **Contesto**: la verifica strutturale del Lotto 19 (script `/tmp/verify_crops.py`, OCR + PIL ink-bbox analysis) ha rilevato che il primo crop di p143 era **impreciso**: catturava il *testo di spiegazione* della tabella ma non la griglia 9 colonne × ~10 righe della TABELLA 1 (famiglia 78XX).

### Diagnosi guidata dai dati (PIL ink ratio per fascia Y di 60 px su PDF page 143)

```
Y [   0- 600]  ink < 3% (testo paragrafi introduttivi, FIGURA 22 alim. duale)
Y [ 600- 700]  ink ≈ 5%   <-- ALTA: righe tabella (sigle 7812, 7815, 7818, 7824)
Y [ 700- 800]  ink ≈ 4%   <-- ALTA: label "TABELLA" + header colonne
Y [ 800-1000]  ink ≈ 2%   (righe tabella, density variabile)
Y [1000-1100]  ink ≈ 2%   <-- ultima riga tabella (7805 + label di chiusura)
Y [1100-1260]  ink ≈ 4%   <-- FIGURA 23 Darlington, OUT OF SCOPE per la tabella
Y [1260-1316]  ink 19-26% <-- FOOTER Zanichelli 2012 + folio (4 0 8 / 4 0 9)
```

**Insegnamento diagnostico**: il primo crop (Y 197-1118) aveva catturato lo strato testuale SOPRA la tabella (Y 0-600, didascalia "in assenza di lettere si intende 1 A. La lettera G individua i regolatori a tensione variabile…") ma la tabella vera era **al di sotto** di quel crop. Il check per fascia ha invertito la diagnosi.

### Fix applicato

* Nuovo crop: `Y 580-1140, X full-width` (entrambe p.408 sx e p.409 dx affiancate).
* Output: **380 KB** (`3224f7b0cb064fb3e6b8cf22cf243ca1`) vs **1055 KB originale** (64% risparmio).
* Verifica OCR post-fix: **6/8 sigle 78XX** trovate (`7805, 7808, 7812, 7815, 7818, 7824`), label **"TABELLA"** presente, valori celle corretti (`I_o = 1`, `I_cc = 1.2`, `R_r = 56 / 55 / 54 / 53 / 50`, `θ_jc/θ_ja/V_D = 5/65/2,5 per le sigle principali; 8/80/3 per 78G`).
* Backup persistente confermato in `~/recrop_backups/` (sha `a445a2b7…`): coincide con l'originale da 1055 KB — catena di rollback verificata.

### Note dal code-reviewer sullo script `verify_crops.py`

* **Threshold righe/colonne a 0.4** era troppo stretto per linee di griglia di tabella (segmenti di ~100 px su 2339 colonne non passano). Risultato: tutte le 9 immagini hanno `h_lines=0, v_lines=0` secondo il mio rilevatore — non un difetto dei crop, ma un limite della metrica di detection.
* **Threshold OCR keyword** (substring semplice) completamente case-insensitive funziona, ma non gestisce **errori OCR** (es. `Johnson` letto come `Iohnson`): falsi negativi su testi ad alta densità di caratteri ambigui.
* Per future tabelle: preferire **Hough line transform** (richiede numpy/scipy non disponibili) o **PIL connected-components** invece del conteggio "pixel continui per riga".

### Note dal code-reviewer sullo script `p143_recrop_v3.py`

* **Magic numbers cablati** (Y 580-1140): non riproducibili senza aver prima eseguito lo sweep OCR preliminare di `/tmp/p143_recrop_v2.py`. Da rendere autonomi integrando lo sweep nel v3 stesso, oppure parametrizzando i bounds via JSON.
* **Backup senza size sanity-check**: `if not BACKUP.exists` non distingue originale (1055 KB) da re-crop precedente (616 KB). Da aggiungere `assert BACKUP.stat().st_size > 800_000`.
* **Discrepanza "TABELLA 4" vs "TABELLA 1"**: l'OCR del crop mostra l'etichetta come `TABELLA 4`, mentre `Argomenti/Alimentatori.md` la cita come `TABELLA 1`. I valori nelle righe corrispondono perfettamente a quelli trascritti in `Alimentatori.md`. Probabilmente OCR ha letto male (1 ↔ 4 in certi font) **oppure** il libro Mirandola numera diversamente da come pensavamo. Decisione consigliata: aggiungere una nota breve in `Alimentatori.md` che dice «Mirandola etichetta questa tabella come **Tabella 4** nel layout» — così entrambi i riferimenti sono documentati e nessuno è sbagliato per partito preso.

### Verifica finale post-fix

* Le 9 immagini in `Allegati/` sono **tutte** referenziate correttamente dai wikilink `![[…]]` (zero link rossi).
* I 9 file sono coerenti col contenuto atteso (OCR match 6-8/8 sigle / keywords richieste tutte trovate / nessun file vuoto).
* Backup di sicurezza in `~/recrop_backups/` per ognuna — ripristinabili in qualsiasi momento.
* Audit file aggiornato: il Lotto 19 originale elencava p143 a 616 KB e segnalava il problema nella sezione "Casi limite gestiti e fix applicati"; questo addendum lo aggiorna a 380 KB e chiude il cerchio.
