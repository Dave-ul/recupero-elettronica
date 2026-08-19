---
tags: [recupero, elettronica, moc, hub, indice]
fonte: "hub di navigazione centralizzato"
prove: [scritta, orale, pratica]
---

# 📚 Argomenti — Hub di navigazione (Map of Content)

> [!info] Scopo
> Questo file è un **MOC (Map of Content)** centralizzato per la cartella `Argomenti/`. Risolve i link `[[Argomenti]]` da qualsiasi punto del vault e offre una navigazione veloce per macroarea tematica. Clicca su un link per aprire direttamente la nota di teoria.

> [!success] 🧒 **Cerchi il "perché?" intuitivo?**
> Apri [[00 - Perchè (spiegazione intuitiva)]] — è il file hub con spiegazioni ricorsive "bambino di 4 anni" per **tutti i 13 argomenti** del vault. Ogni sezione parte da "Cos'è?" → "Perché?" → "Perché ancora?" → ... → "Cosa c'entra con il resto?". Da consultare quando una formula o un concetto non "scende".

> [!warning] Trasparenza fonti — leggi prima di fidarti
> Le fonti del vault sono dichiarate in [[Prove/00 - Fonti e note]], in ordine di autorità:
> la **LETTERA** Majorana del 09/06/2026 (cosa esce), le **tre verifiche FUSI del prof. Carli**
> corrette a mano — i fogli di un compagno, non i tuoi: vedi [[05 - Verifiche FUSI (Carli)]], gli **appunti
> Poggi** (cosa è stato fatto in classe), il **Mirandola Vol. 2** e **Edutecnica**.
> *(Riallineato il 2026-08-19: questo callout diceva che il Mirandola è «NON verificabile», il che
> contraddiceva [[Prove/00 - Fonti e note]] e non è più vero. Le pagine del libro sono citabili con
> la conversione `pagina stampata = 2·(pagina-PDF) − 6`, verificata su quattro folio.)*

> [!tip] 📅 Quando si studia cosa
> Il piano giorno per giorno è in **[[Calendario]]** — 12 giorni fino alla prova del
> **1 settembre** (scritto 8:00-13:00, orale + pratico insieme 14:00-17:00). Ogni giornata
> dice quali di queste note aprire.




> [!tip] Come usarlo
> - In Obsidian: clicca sui link `[[...]]` per saltare al file.
> - Da Graph view: questo nodo si connette a tutti gli `Argomenti/*.md`, formando il cuore del vault.
> - In [[Prove/00 - Indice Generale|Indice Generale]] trovi il mapping Argomenti → Esercizi → Prove.

---

## 🎯 Macroaree dello scope (lettera di giudizio sospeso)

| Macroarea | Argomenti coperti | Dove cade |
|---|---|---|
| **AC in regime sinusoidale** | [[Segnali sinusoidali e fasori]], [[Impedenza dei bipoli R, L, C]], [[Il metodo simbolico]], [[Reti RLC e risonanza]] §1-2, [[Filtri passivi del primo ordine]] | **scritto** + **orale** Carli + **pratico** Protti |
| **Semiconduttori e circuiti attivi** | [[BJT]], [[MOSFET]], [[JFET]] | **scritto** Carli · [[Diodi]] → **orale** Carli + **pratico** Protti |
| **Applicazioni** | [[Amplificatori a BJT]] | **pratico** Protti (nominato dalla lettera) |
| **Strumentazione** | [[L'oscilloscopio]] | **pratico** Protti — trasversale a tutto |
| **Solo lettura per l'orale** | [[Le potenze in alternata]] §1-2, [[Reti RLC e risonanza]] §3, [[Alimentatori]] §1 e §4 | 45 minuti in tutto, zero esercizi — vedi [[Calendario]] |

---

## 📖 Tutti gli argomenti (ordine per difficoltà crescente)

### 🔰 Fondamentali (inizia da qui)

| # | Argomento | Prerequisiti | Note |
|---|---|---|---|
| 1 | [[Segnali sinusoidali e fasori]] | — | Base di tutto: rappresentazione fasoriale |
| 2 | [[Impedenza dei bipoli R, L, C]] | [[Segnali sinusoidali e fasori]] | $Z_R$, $Z_L$, $Z_C$, comportamento in freq. |
| 3 | [[Il metodo simbolico]] | i due sopra | Procedura operativa per risolvere reti AC |
| 4 | [[Diodi]] | — | Primo componente non-lineare |

### 🟡 Intermedi

| # | Argomento | Prerequisiti | Note |
|---|---|---|---|
| 5 | [[Le potenze in alternata]] | [[Il metodo simbolico]] | P, Q, S, cosφ, rifasamento |
| 6 | [[Reti RLC e risonanza]] | [[Impedenza dei bipoli R, L, C]] | Serie + parallelo, Q-factor |
| 7 | [[Filtri passivi del primo ordine]] | [[Impedenza dei bipoli R, L, C]] | RC + RL, passa-basso/alto |
| 8 | [[BJT]] | [[Impedenza dei bipoli R, L, C]] | Pilotaggio in corrente, regioni |
| 9 | [[Alimentatori]] | [[Diodi]], [[BJT]] | Raddrizzatori, filtri, regolatori 78xx |

### 🔴 Avanzati

| # | Argomento | Prerequisiti | Note |
|---|---|---|---|
| 10 | [[MOSFET]] | [[BJT]] | Pilotaggio in tensione, formula parabolica |
| 11 | [[JFET]] | [[MOSFET]] | Parabolica inversa, autopolarizzazione |
| 12 | [[Amplificatori a BJT]] | [[BJT]] | CE/CC/CB, parametri h |
| 13 | [[L'oscilloscopio]] | — | Strumento di misura (cruciale per Protti) |

---

## 🧭 Percorso rapido per ciascuna prova

### 📝 Prova scritta Carli (1 settembre, 8:00-13:00 — **cinque ore**)

La lettera nomina **cinque** argomenti, e sono questi. In cinque ore ci stanno tutti:
non contare su nessuno che non esca.

1. **Circuiti in corrente alternata** — [[Segnali sinusoidali e fasori]] · [[Impedenza dei bipoli R, L, C]] · [[Il metodo simbolico]] · [[Reti RLC e risonanza]] §1-2
2. **Filtri passivi del primo ordine** — [[Filtri passivi del primo ordine]], RC/RL, $f_t$ ⭐
3. **Transistor BJT** — [[BJT]], polarizzazione a partitore
4. **Transistor JFET a canale N** — [[JFET]], autopolarizzazione ⭐
5. **Transistor MOSFET a canale N ad arricchimento** — [[MOSFET]], parabolica con verifica di saturazione ⭐

> [!warning] Cosa **non** è nella prova scritta
> Il **diodo** (la lettera lo mette all'orale e alla pratica), le **potenze in alternata** e
> il **rifasamento trifase**, la **risonanza** con Q-factor e banda, gli **alimentatori**, i
> **diagrammi di Bode** e i **filtri del 2° ordine**. Fino al 2026-08-19 questa lista ne
> elencava undici invece di cinque: la lettera ne dice cinque.

### 🎙️ Prova orale Carli (1 settembre, pomeriggio — insieme a Protti)

La lettera ne nomina **tre**, non uno solo:

1. **Il diodo** — [[Diodi]] · le 39 domande vere in [[04 - Verifica tipo Carli — Diodi]] · le risposte D1-D23 già scritte in `elettronicaa/diodi-risposte.html`
2. **I circuiti in corrente alternata** — [[Impedenza dei bipoli R, L, C]] · [[Il metodo simbolico]]
3. **I filtri passivi del primo ordine** — [[Filtri passivi del primo ordine]]

> Le domande già pronte, divise per livello (definizione / spiegazione / confronto), sono in
> [[Prove/02 - Prova Orale Carli]]. Il diodo è coperto; **alternata e filtri vanno provati a
> voce**, ed è quello che si fa la mattina del 30 agosto.

### 🔬 Prova pratica Protti (1 settembre, 14:00-17:00 — stessa sessione dell'orale)

«Domande, esercizi, esperienze e **misure con l'oscilloscopio** su tutto il programma»:

1. [[L'oscilloscopio]] — procedure di misura, coupling AC/DC, trigger, sonda ×1 e ×10
2. [[Diodi]] — circuiti con diodi: raddrizzatore, ripple, breakdown Zener · e [[Alimentatori]]
3. [[Segnali sinusoidali e fasori]] — misura di $V_p$, $V_{eff}$, $T$, sfasamento
4. [[Reti RLC e risonanza]] §1-2 — reti RLC in regime sinusoidale
5. [[Filtri passivi del primo ordine]] — verifica di $f_t$ con sweep di frequenza
6. [[BJT]] — punto di lavoro e [[Amplificatori a BJT]] — misura di $A_v$, verifica dell'inversione di fase

> Procedure, trappole e sequenza operativa: [[Prove/03 - Prova Pratica Protti]].

---

## ❌ Errori comuni (consultazione rapida)

Gli errori "trappola" della [[Prove/01 - Prova Scritta Carli|prova scritta Carli]] sono documentati alla fine di ogni nota di teoria nella sezione **"Pattern di errore frequenti"** (vedi `[[Esercizi - Filtri passivi del primo ordine#Errori tipici]]`, `[[Esercizi - Diodi#Errori tipici]]`, ecc.).

I tre più critici in assoluto (da memorizzare):

1. **Filtri**: RL → $f_t = R/(2\pi L)$ (NON $L/R$). Vedi `[[Filtri passivi del primo ordine]]` §4.
2. **MOSFET**: parabolica $I_D = K(V_{GS}-V_{th})^2$ vale SOLO in saturazione. **Verifica sempre** $V_{DS} > V_{GS} - V_{th}$. Vedi `[[MOSFET]]` §3.
3. **JFET**: tutti gli esercizi di progetto escono da due sole relazioni — $V_{GS0} = -R_S I_{D0}$ e $V_{DD} = I_{D0}(R_S + R_D) + V_{DS0}$. Sulla verifica 29-05 tre esercizi su cinque sono «NON SVOLTO»: vedi [[05 - Verifiche FUSI (Carli)]].

---

## 🔗 Link rapidi ad altre aree del vault

- **Esercizi svolti** → vedi [[Esercizi]]
- **Prove d'esame (Carli + Protti)** → vedi [[Prove/00 - Indice Generale|Indice Generale]]
- **Formulario rapido** → vedi [[Prove/Formulario rapido|Formulario rapido]]
- **Le tre verifiche vere del prof.** → vedi [[05 - Verifiche FUSI (Carli)]]
- **Il piano giorno per giorno** → vedi [[Calendario]]
- **Simulazione d'esame completa** → vedi [[Esercizi/Esercizi - Simulazione finale|Simulazione finale]]
