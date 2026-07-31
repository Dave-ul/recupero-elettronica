---
tags: [recupero, elettronica, moc, hub, indice, esercizi]
fonte: "hub di navigazione centralizzato"
prove: [scritta, orale, pratica]
---

# ✏️ Esercizi — Hub di navigazione (Map of Content)

> [!info] Scopo
> Questo file è un **MOC (Map of Content)** centralizzato per la cartella `Esercizi/`. Risolve i link `[[Esercizi]]` da qualsiasi punto del vault. **Ogni scheda Esercizi coppia**: teoria in `Argomenti/` → esercizi svolti qui → prove in `Prove/`.

> [!tip] Come usarlo
> - In Obsidian: clicca sui link `[[...]]` per saltare al file.
> - Per ogni macroarea: 1) rileggi la teoria in `Argomenti/` → 2) fai gli esercizi qui → 3) verifica con `Prove/01 - Prova Scritta Carli`.
> - Per la simulazione completa d'esame: `[[Esercizi - Simulazione finale]]` (90 min).

---

## 🎯 Macroaree e relativi file di esercizi

| Macroarea | Esercizi svolti | Teoria collegata | Prove rilevanti |
|---|---|---|---|
| **AC / fasori** | [[Esercizi - Segnali sinusoidali e fasori]] | [[Argomenti/Segnali sinusoidali e fasori\|Segnali sinusoidali e fasori]] | 01, 02, 03 |
| **Impedenze R, L, C** | [[Esercizi - Impedenza dei bipoli R, L, C]] | [[Argomenti/Impedenza dei bipoli R, L, C\|Impedenza]] | 01, 02, 03 |
| **Metodo simbolico** | [[Esercizi - Il metodo simbolico]] | [[Argomenti/Il metodo simbolico\|Il metodo simbolico]] | 01, 02 |
| **Potenze AC + rifasamento** | [[Esercizi - Le potenze in alternata]] | [[Argomenti/Le potenze in alternata\|Le potenze in alternata]] | 01, 02 |
| **Reti RLC + risonanza** | [[Esercizi - Reti RLC e risonanza]] | [[Argomenti/Reti RLC e risonanza\|Reti RLC]] | 01, 02 |
| **Filtri primo ordine** | [[Esercizi - Filtri passivi del primo ordine]] | [[Argomenti/Filtri passivi del primo ordine\|Filtri]] | 01, 02, 03 |
| **Diodi + Zener** | [[Esercizi - Diodi]] | [[Argomenti/Diodi\|Diodi]] | 01, 02, 03 |
| **BJT** | [[Esercizi - BJT]] | [[Argomenti/BJT\|BJT]] | 01, 02 |
| **MOSFET enhancement n** | [[Esercizi - MOSFET]] | [[Argomenti/MOSFET\|MOSFET]] | 01, 02 |
| **JFET n** | [[Esercizi - JFET]] | [[Argomenti/JFET\|JFET]] | 01, 02 |
| **Amplificatori a BJT** | [[Esercizi - Amplificatori a BJT]] | [[Argomenti/Amplificatori a BJT\|Amplificatori a BJT]] | 02, 03 |
| **Alimentatori** | [[Esercizi - Alimentatori]] | [[Argomenti/Alimentatori\|Alimentatori]] | 01, 02, 03 |
| **Simulazione d'esame** | [[Esercizi - Simulazione finale]] | (tutti gli Argomenti) | 01 (simulazione 90 min) |

---

## 📚 Struttura di ogni file `Esercizi - X.md`

Ogni file di esercizi in `Esercizi/` segue la stessa struttura standard, per consistenza e velocità di consultazione:

1. **Frontmatter** con tag, fonte (libro + edutecnica), prove dove cade.
2. **Sezione "Dove serve"** (callout `info`) che indica in quali prove è richiesto.
3. **Prerequisiti** (link alla teoria in `Argomenti/`).
4. **Esercizi svolti dal libro Mirandola** (4-5 esercizi classici per ogni macroarea).
5. **Esercizi svolti da edutecnica.it** (catalogo completo dal sito, con soluzioni numeriche).
6. **Pattern di errore frequenti** (i 2-3 errori "trappola" specifici).
7. **"Da qui in poi"** con link al resto del percorso (successive esercitazioni + prove).
8. **Fonti** (libro + URL edutecnica).

> Esempio: vedi `[[Esercizi - Diodi]]` per il pattern completo (esercita la consultazione scorrendo questo file).

---

## 🎓 Percorso di studio consigliato per la **prova scritta Carli**

Segui questo ordine, dal facile al difficile:

| Step | File | Tempo studio stimato | Cosa impari |
|---|---|---|---|
| 1 | `[[Esercizi - Segnali sinusoidali e fasori]]` | 1h | Conversioni di forma, operazioni con vettori |
| 2 | `[[Esercizi - Impedenza dei bipoli R, L, C]]` | 1h | Serie/parallelo, $X_L$/$X_C$ |
| 3 | `[[Esercizi - Il metodo simbolico]]` | 1h | Procedure standard 4 passi |
| 4 | `[[Esercizi - Le potenze in alternata]]` | 1.5h | P/Q/S, $\cos\varphi$, rifasamento ⭐ |
| 5 | `[[Esercizi - Reti RLC e risonanza]]` | 1h | Q-factor, banda passante |
| 6 | `[[Esercizi - Filtri passivi del primo ordine]]` | 1.5h | $f_t$ RC/RL (errata corrige libro!) |
| 7 | `[[Esercizi - Diodi]]` | 1.5h | Spezzata, Zener, raddrizzatore, limitatore |
| 8 | `[[Esercizi - BJT]]` | 2h | Polarizzazioni, commutazione, Darlington |
| 9 | `[[Esercizi - MOSFET]]` | 2h | Parabolica + verifica saturazione ⭐ |
| 10 | `[[Esercizi - JFET]]` | 1.5h | Autopolarizzazione, discriminante |
| 11 | `[[Esercizi - Amplificatori a BJT]]` | 2h | Parametri h CE/CC/CB |
| 12 | `[[Esercizi - Alimentatori]]` | 1.5h | Ripple, dropout 78xx, regolatore serie |
| 13 | `[[Esercizi - Simulazione finale]]` | 2h (×3 sessioni) | Tutto insieme sotto timer 90 min |

**Tempo totale stimato**: ~20 ore di studio distribuite su 2-3 settimane.

---

## ❌ Errori "trappola" più frequenti (consultazione rapida)

Per ogni `Esercizi - X.md`, c'è una sezione **"Pattern di errore frequenti (Carli scritta)"** con i 2-3 errori tipici. Riassunto dei 3 peggiori (da NON fare mai):

1. **MOSFET/JFET senza verifica di saturazione**: applicare la parabolica $I_D = K(V_{GS}-V_{th})^2$ senza controllare $V_{DS} > V_{GS}-V_{th}$ è la causa #1 di errore alla Carli scritta. → Vedi `[[Esercizi - MOSFET]]`.
2. **Filtri RL con $L/R$ invece di $R/L$**: errore del libro Mirandola (pag. 160), già corretto nel vault. Se uno studente "impara dal libro" di prendere l'abitudine, sbaglia alla Carli. → Vedi `[[Esercizi - Filtri passivi del primo ordine]]`.
3. **Rifasamento trifase senza dividere per 3**: $C_{\text{fase}} = \Delta Q/(3\omega V_{\text{fase}}^2)$ — confondere con la formula monofase è un errore da 4 punti persi. → Vedi `[[Esercizi - Le potenze in alternata]]`.

---

## 📐 Simulazione d'esame completa

Il file [[Esercizi - Simulazione finale]] contiene **6 problemi misti** (E1–E6, uno per macroarea) da svolgere sotto timer 90 min, esattamente come la prova reale Carli.

- E1: Impedenze + regime sinusoidale (15 min, medio)
- E2: Filtro passa-basso RL (15 min, facile)
- E3: Potenze + rifasamento trifase (15 min, medio) ⭐
- E4: Stabilizzatore Zener (15 min, facile)
- E5: BJT con partitore di base (15 min, medio)
- E6: MOSFET enhancement n (15 min, difficile) ⭐

> [!warning] Preparazione minima
> Prima di tentare la simulazione: aver svolto **almeno 2 sessioni complete** sui file `Esercizi - X.md` per macroarea, e aver letto la sezione "Pattern di errore frequenti" di ciascuno. 5/6 corretti = pronto per la prova reale.

---

## 🔗 Link rapidi ad altre aree del vault

- **Tutti gli argomenti teorici** → vedi [[Argomenti]]
- **Prove d'esame (Carli + Protti)** → vedi [[Prove/00 - Indice Generale|Indice Generale]]
- **Formulario rapido** per il compito → vedi [[Prove/Formulario rapido|Formulario rapido]]
- **Trasparenza fonti** (LETTERA Majorana + edutecnica.it + libro Mirandola) → vedi [[Prove/00 - Fonti e note]]
- **Tutorial su misure di laboratorio** → vedi `[[Diodi#6.b Misurazioni Pratiche]]` + `[[L'oscilloscopio]]`
