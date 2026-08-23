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
> - Per allenarti a batteria: `[[Esercizi - Simulazione finale]]` (75 min). ⚠️ Non è la
>   simulazione della prova reale, che dura **cinque ore**: quella è la sessione lunga del
>   30 agosto, con le tre verifiche FUSI in fila — vedi [[Calendario]] e [[05 - Verifiche FUSI (Carli)]].

---

## 🎯 Macroaree e relativi file di esercizi

| Macroarea | Esercizi svolti | Teoria collegata | Prove rilevanti |
|---|---|---|---|
| **AC / fasori** | [[Esercizi - Segnali sinusoidali e fasori]] | [[Segnali sinusoidali e fasori\|Segnali sinusoidali e fasori]] | 01, 02, 03 |
| **Impedenze R, L, C** | [[Esercizi - Impedenza dei bipoli R, L, C]] | [[Impedenza dei bipoli R, L, C\|Impedenza]] | 01, 02, 03 |
| **Metodo simbolico** | [[Esercizi - Il metodo simbolico]] | [[Il metodo simbolico\|Il metodo simbolico]] | 01, 02 |
| **Potenze AC + rifasamento** | [[Esercizi - Le potenze in alternata]] | [[Le potenze in alternata\|Le potenze in alternata]] | 01, 02 |
| **Reti RLC + risonanza** | [[Esercizi - Reti RLC e risonanza]] | [[Reti RLC e risonanza\|Reti RLC]] | 01, 02 |
| **Filtri primo ordine** | [[Esercizi - Filtri passivi del primo ordine]] | [[Filtri passivi del primo ordine\|Filtri]] | 01, 02, 03 |
| **Diodi + Zener** | [[Esercizi - Diodi]] | [[Diodi\|Diodi]] | 01, 02, 03 |
| **BJT** | [[Esercizi - BJT]] | [[BJT\|BJT]] | 01, 02 |
| **MOSFET enhancement n** | [[Esercizi - MOSFET]] | [[MOSFET\|MOSFET]] | 01, 02 |
| **JFET n** | [[Esercizi - JFET]] | [[JFET\|JFET]] | 01, 02 |
| **Amplificatori a BJT** | [[Esercizi - Amplificatori a BJT]] | [[Amplificatori a BJT\|Amplificatori a BJT]] | 02, 03 |
| **Alimentatori** | [[Esercizi - Alimentatori]] | [[Alimentatori\|Alimentatori]] | 01, 02, 03 |
| **Batteria da 75 min** | [[Esercizi - Simulazione finale]] | (tutti gli Argomenti) | 01 (allenamento, non la prova reale da 5h) |

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

Segui questo ordine, dal facile al difficile. La colonna **Giorno** dice dove ciascuna voce
cade nel [[Calendario]]: i due piani vanno letti insieme, e dove divergono comanda il Calendario.

| Step | File | Giorno | Tempo | Cosa impari |
|---|---|---|---|---|
| 1 | `[[Esercizi - Segnali sinusoidali e fasori]]` | **1** · 20 ago | 1h | Conversioni di forma, operazioni con vettori |
| 2 | `[[Esercizi - Impedenza dei bipoli R, L, C]]` | **1** · 20 ago | 1h | Serie/parallelo, $X_L$/$X_C$ |
| 3 | `[[Esercizi - Il metodo simbolico]]` | **1** · 20 ago ⭐ | 1h | Procedure standard 4 passi |
| 4 | `[[Esercizi - Le potenze in alternata]]` | **1** · solo lettura | 20 min | P/Q/S e $\cos\varphi$ *(descrittivi, per l'orale — niente rifasamento numerico)* |
| 5 | `[[Esercizi - Reti RLC e risonanza]]` | **1** · §1-2 | 1h | Risonanza; il Q-factor solo se avanza tempo |
| 6 | `[[Esercizi - Filtri passivi del primo ordine]]` | **2-3** · 21-22 ago ⭐ | 1.5h | $f_t$ RC/RL (errata corrige libro!) |
| 7 | `[[Esercizi - Diodi]]` | **4** · 23 ago | 1.5h | Spezzata, Zener, raddrizzatore, limitatore |
| 8 | `[[Esercizi - BJT]]` | **5-6** · 24-25 ago | 2h | Polarizzazioni, commutazione, Darlington |
| 9 | `[[Esercizi - MOSFET]]` | **10** · 29 ago ⭐ | 2h | Parabolica + verifica saturazione |
| 10 | `[[Esercizi - JFET]]` | **8-9** · 27-28 ago ⭐ | 1.5h | Autopolarizzazione, discriminante |
| 11 | `[[Esercizi - Amplificatori a BJT]]` | **7** · 26 ago | 2h | Parametri h CE/CC/CB |
| 12 | `[[Esercizi - Alimentatori]]` | **4** · solo lettura | 25 min | Schema a blocchi, ripple, 78xx *(descrittivi, per la pratica Protti)* |
| 13 | `[[Esercizi - Simulazione finale]]` | *libera* | 1h15 | Allenamento alla velocità. La prova di resistenza sulle 5 ore è il **giorno 11** |

**Tempo totale stimato**: ~20 ore. Non sono però 20 ore a sé stanti: sono **dentro** le
circa 40 ore dei 12 giorni del [[Calendario]], che a ciascuna di queste voci assegna un
giorno preciso — vedi la colonna qui sopra. Se i due piani divergono, comanda il Calendario.

---

## ❌ Errori "trappola" più frequenti (consultazione rapida)

Per ogni `Esercizi - X.md`, c'è una sezione **"Pattern di errore frequenti (Carli scritta)"** con i 2-3 errori tipici. Riassunto dei 3 peggiori (da NON fare mai):

1. **MOSFET/JFET senza verifica di saturazione**: applicare la parabolica $I_D = K(V_{GS}-V_{th})^2$ senza controllare $V_{DS} > V_{GS}-V_{th}$ è la causa #1 di errore alla Carli scritta. → Vedi `[[Esercizi - MOSFET]]`.
2. **Filtri RL con $L/R$ invece di $R/L$**: errore del libro Mirandola (pag. 160), già corretto nel vault. Se uno studente "impara dal libro" di prendere l'abitudine, sbaglia alla Carli. → Vedi `[[Esercizi - Filtri passivi del primo ordine]]`.
3. **JFET, le due relazioni di progetto non sapute a memoria**: $V_{GS0} = -R_S I_{D0}$ e
   $V_{DD} = I_{D0}(R_S + R_D) + V_{DS0}$. Sulla verifica 29-05 del prof. **tre esercizi su cinque**
   sono segnati «NON SVOLTO»: è l'argomento più scoperto, e sono due formule.
   → Vedi `[[Esercizi - JFET]]` e [[05 - Verifiche FUSI (Carli)]].

> *(Fino al 2026-08-20 il terzo posto era del rifasamento trifase, che il [[Calendario]]
> mette fuori programma. Il 2026-08-21 le formule trifase sono state rimosse dal vault:
> resta il rifasamento **monofase**, che è in programma — vedi [[Le potenze in alternata]] §5.)*

---

## 📐 Simulazione d'esame completa

Il file [[Esercizi - Simulazione finale]] contiene **5 problemi misti** (E1–E5, uno per macroarea) da svolgere sotto timer 75 min.

> [!warning] Non confonderla con la prova reale
> La prova scritta del 1° settembre dura **cinque ore** (8:00-13:00). Questa batteria da 75
> minuti serve ad allenare la velocità su un esercizio per macroarea; la prova di resistenza
> sulle cinque ore è la sessione lunga del **30 agosto** con le tre verifiche del prof. in
> fila — vedi [[05 - Verifiche FUSI (Carli)]].

- E1: Impedenze + regime sinusoidale (15 min, medio)
- E2: Filtro passa-basso RL (15 min, facile)
- E3: Stabilizzatore Zener (15 min, facile)
- E4: BJT con partitore di base (15 min, medio)
- E5: MOSFET enhancement n (15 min, difficile) ⭐

> [!warning] Preparazione minima
> Prima di tentare la simulazione: aver svolto **almeno 2 sessioni complete** sui file `Esercizi - X.md` per macroarea, e aver letto la sezione "Pattern di errore frequenti" di ciascuno. 5/6 corretti = pronto per la prova reale.

---

## 🔗 Link rapidi ad altre aree del vault

- **Tutti gli argomenti teorici** → vedi [[Argomenti]]
- **Prove d'esame (Carli + Protti)** → vedi [[00 - Indice Generale|Indice Generale]]
- **Formulario rapido** per il compito → vedi [[Formulario rapido|Formulario rapido]]
- **Trasparenza fonti** (LETTERA Majorana + edutecnica.it + libro Mirandola) → vedi [[00 - Fonti e note]]
- **Tutorial su misure di laboratorio** → vedi `[[Diodi#6.b Misurazioni Pratiche]]` + `[[L'oscilloscopio]]`
