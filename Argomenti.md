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
> Le 3 fonti del vault sono dichiarate in modo trasparente nel file [[Prove/00 - Fonti e note]]: la LETTERA Majorana del 09/06/2026 (fonte UFFICIALE del compito), edutecnica.it (fonte secondaria verificata 8/8 topic), e il libro Mirandola Vol.2 che è NON verificabile (PDF scansionato 152 pp senza OCR — le citazioni storiche di 'pag. 80', 'Cap. 6' sono basate sulla prassi didattica, non sul testo reale). Per questo studia usando LETTERA + edutecnica.it, e usa Mirandola solo come riferimento per le figure che hai visto in classe.




> [!tip] Come usarlo
> - In Obsidian: clicca sui link `[[...]]` per saltare al file.
> - Da Graph view: questo nodo si connette a tutti gli `Argomenti/*.md`, formando il cuore del vault.
> - In [[Prove/00 - Indice Generale|Indice Generale]] trovi il mapping Argomenti → Esercizi → Prove.

---

## 🎯 Macroaree dello scope (lettera di giudizio sospeso)

| Macroarea | Argomenti coperti | Esami dove cade |
|---|---|---|
| **AC in regime sinusoidale** | [[Segnali sinusoidali e fasori]], [[Impedenza dei bipoli R, L, C]], [[Il metodo simbolico]], [[Le potenze in alternata]], [[Reti RLC e risonanza]], [[Filtri passivi del primo ordine]] | Scritta + Orale Carli |
| **Semiconduttori e circuiti attivi** | [[Diodi]], [[BJT]], [[MOSFET]], [[JFET]] | BJT/MOSFET/JFET: Scritta Carli • Diodi: Orale Carli + Pratica Protti |
| **Applicazioni** | [[Amplificatori a BJT]] (Protti pratica) · [[Alimentatori]] (Protti pratica, in «circuiti con diodi») | Pratica Protti |
| **Strumentazione** | [[L'oscilloscopio]] | Pratica Protti |

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

### 📝 Prova scritta Carli (90 min, 6 esercizi)
1. [[Segnali sinusoidali e fasori]] — conversioni di forma
2. [[Impedenza dei bipoli R, L, C]] — calcolo $\bar{Z}_{\text{eq}}$
3. [[Il metodo simbolico]] — procedura operativa
4. [[Le potenze in alternata]] — P, Q, S, rifasamento trifase ⭐
5. [[Reti RLC e risonanza]] — Q-factor, banda passante
6. [[Filtri passivi del primo ordine]] — RC/RL, $f_t$ (con errata corrige libro)
7. [[Diodi]] — circuiti con diodi, Zener stabilizzatore
8. [[Alimentatori]] — raddrizzatori, regolatori
9. [[BJT]] — polarizzazione partitore, Darlington
10. [[MOSFET]] — parabolica con verifica di saturazione ⭐
11. [[JFET]] — autopolarizzazione, discriminante

### 🎙️ Prova orale Carli (definizioni + confronti)
1. [[Diodi]] — barriera di potenziale, Zener vs normale
2. Tutti i 13 argomenti — domande tipo pronte in ogni nota

### 🔬 Prova pratica Protti (lab)
1. [[L'oscilloscopio]] — procedure di misura, AC/DC coupling, probe
2. [[Diodi]] — misura V_γ, ripple, breakdown Zener (vedi `[[Diodi#6.b Misurazioni Pratiche]]`)
3. [[Amplificatori a BJT]] — misura $A_v$ con oscilloscopio, verifica inversione di fase
4. [[Alimentatori]] — misura ripple, test regolatore 78xx
5. [[Filtri passivi del primo ordine]] — verifica $f_t$ con sweep di frequenza
6. [[BJT]] — verifica punto di lavoro con multimetro ($V_{CE} \approx V_{CC}/2$)
7. [[Reti RLC e risonanza]] — sweep e misura $f_0$

---

## ❌ Errori comuni (consultazione rapida)

Gli errori "trappola" della [[Prove/01 - Prova Scritta Carli|prova scritta Carli]] sono documentati alla fine di ogni nota di teoria nella sezione **"Pattern di errore frequenti"** (vedi `[[Esercizi - Filtri passivi del primo ordine#Errori tipici]]`, `[[Esercizi - Diodi#Errori tipici]]`, ecc.).

I tre più critici in assoluto (da memorizzare):

1. **Filtri**: RL → $f_t = R/(2\pi L)$ (NON $L/R$). Vedi `[[Filtri passivi del primo ordine]]` §4.
2. **MOSFET**: parabolica $I_D = K(V_{GS}-V_{th})^2$ vale SOLO in saturazione. **Verifica sempre** $V_{DS} > V_{GS} - V_{th}$. Vedi `[[MOSFET]]` §3.
3. **Trifase**: $C_{\text{fase}} = \Delta Q/(3\omega V_{\text{fase}}^2)$ con $V_{\text{fase}} = V_{\text{conc}}/\sqrt{3}$. Vedi `[[Le potenze in alternata]]` §3.

---

## 🔗 Link rapidi ad altre aree del vault

- **Esercizi svolti** → vedi [[Esercizi]]
- **Prove d'esame (Carli + Protti)** → vedi [[Prove/00 - Indice Generale|Indice Generale]]
- **Formulario rapido** → vedi [[Prove/Formulario rapido|Formulario rapido]]
- **Simulazione d'esame completa** → vedi [[Esercizi/Esercizi - Simulazione finale|Simulazione finale]]
