---
tags: [recupero, elettronica, fonti, trasparenza, lettera-majorana, audit]
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO)"
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave"
libro_mirandola: "VERIFICATO ✔ (dal 2026-07-19) — PDF scansionato 152 pagg. SENZA testo digitale, ma leggibile via OCR (tesseract -l ita) + lettura diretta delle immagini. Contenuti incrociati col testo reale capitolo per capitolo. Vedi §2 e la mappa pagine in §2bis."
---

# 📚 Fonti del vault — Note di trasparenza

> Questo file è la **dichiarazione di fonti** del vault Obsidian `Recupero Elettronica`. In 1 sola lettura, lo studente Carli può capire **da dove vengono i contenuti**, **cosa è verificato**, e **cosa NON è verificabile**. Tutti gli altri file del vault rimandano qui quando serve trasparenza.

---

## 🎯 1. Estratto LETTERA Majorana (fonte ufficiale)

> **Protocollo n° 2760** · **IIS Ettore Majorana, San Lazzaro di Savena (BO)** · **Com. del Consiglio di Classe 4BEM Meccanica-Elettronica** · **09/06/2026** · **Studente: Davide Rocca** · **Materia: Elettrotecnica ed Elettronica, voto 3**

### 📋 Cosa deve dimostrare lo studente

#### **PARTE DI TEORIA — Prof. Carlo Carli**

**PROVA SCRITTA**: esercizi su

| Argomento richiesto | File vault | Note |
|---|---|---|
| Circuiti in corrente alternata | [[Impedenza dei bipoli R, L, C]] + [[Il metodo simbolico]] + [[Le potenze in alternata]] | impedenze, fasori, P/Q/S |
| Filtri passivi del **primo ordine** | [[Filtri passivi del primo ordine]] | RC/RL PB/PA |
| Transistor BJT | [[BJT]] + [[Esercizi - BJT]] | pilotaggio in corrente ($I_B$) |
| Transistor JFET **a canale N** | [[JFET]] + [[Esercizi - JFET]] | pilotaggio in tensione parabolico |
| Transistor MOSFET **a canale N ad arricchimento** (enhancement) | [[MOSFET]] + [[Esercizi - MOSFET]] | pilotaggio in tensione |

**PROVA ORALE**: domande su

| Argomento richiesto | File vault | Note |
|---|---|---|
| Diodo | [[Diodi]] + [[Esercizi - Diodi]] | normale, Zener, Schottky |
| Circuiti in corrente alternata | vedi sopra | |
| Filtri passivi del primo ordine | vedi sopra | |

#### **PARTE PRATICA — Prof. Giampaolo Protti**

Domande, esercizi, esperienze e misure con l'oscilloscopio su tutto il programma svolto nell'anno pubblicato sul registro elettronico:

| Argomento richiesto | File vault | Note |
|---|---|---|
| Circuiti con diodi | [[Diodi]] + [[Alimentatori]] | misure con oscilloscopio |
| Segnali sinusoidali | [[Segnali sinusoidali e fasori]] | generazione, misura T e V |
| Reti RLC in regime sinusoidale | [[Reti RLC e risonanza]] + [[Impedenza dei bipoli R, L, C]] | risonanza, ω₀, Q |
| Filtri passivi | [[Filtri passivi del primo ordine]] | misura $f_t$, $A_v(f)$ |
| BJT | [[BJT]] | misura curve caratteristiche |
| Amplificatori con BJT | [[Amplificatori a BJT]] | CE, CC, CB — guadagno, impedenze |

**Modalità di recupero**: studio individuale + prove di verifica **prima settimana di settembre 2026** (data precisa pubblicata sul sito dell'Istituto).

---

## 📂 2. Policy sulle fonti

### ✅ FONTI VERIFICATE

#### **LETTERA Majorana** (fonte ufficiale del compito)
- **Cosa**: documento protocollato dell'IIS Majorana che specifica gli argomenti d'esame
- **Affidabilità**: 100% (firmato da Dirigente Scolastico Serafina Patrizia Scerra)
- **Come la uso nel vault**: come **mappa argomenti** — ogni `[[Argomenti/X]]` deve coprire gli argomenti elencati nella LETTERA
- **File di riferimento**: `~/Scaricati/MAJORANA_lettera_giudizio_sospeso_recuperi_(Secondo_Periodo).pdf` — **il PDF originale, con strato di testo** (a differenza del libro): si rilegge in qualunque momento con `pdftotext -layout`. *(Aggiornato il 2026-07-28: la versione precedente puntava a `/tmp/lettera_giudizio.txt`, un estratto temporaneo **che non esiste più**. Puntare a `/tmp` significava avere una fonte ufficiale non più verificabile.)*
- **Testo verbatim delle due prove Carli** (riletto dal PDF il 2026-07-28):
  > PROVA SCRITTA: **esercizi** sui circuiti in corrente alternata, sui filtri passivi del primo ordine, sui transistor BJT, sui transistor JFET a canale N e sui transistor MOSFET a canale N ad arricchimento. PROVA ORALE: **domande sul diodo**, sui circuiti in corrente alternata e sui filtri passivi del primo ordine.

#### **Verifiche reali del Prof. Carli** — 3 fogli fotografati, aggiunta 2026-07-28

- **Cosa**: due compiti in classe sui diodi, **16 + 23 = 39 domande aperte**, stesso docente. I Fogli B e C portano il riferimento *«libro capitolo 5 I diodi da pagina 192 a pagina 224»*; il Foglio A **no** (la sua consegna finisce a «in modo esaustivo:»). Fogli in `Allegati/`: `verifica-carli-diodi-16dom.jpeg`, `verifica-carli-4E-diodi-parte1.jpeg`, `verifica-carli-4E-diodi-parte2.jpeg` — **copie byte-identiche** agli originali (MD5 confrontati il 2026-07-28).
- **Affidabilità**: **fonte diretta e di prima mano** su *come Carli interroga*. Per autorevolezza viene **subito dopo la LETTERA** e **prima** del libro e di edutecnica: non è materiale *analogo* alle domande d'esame, sono le domande del docente vero.
- **Perché sono tue**: l'intestazione dei **Fogli B e C** dice **«Classe 4E»**. **4E è la sezione di elettronica dell'articolata 4BEM Meccanica-Elettronica**, cioè la classe dello studente indicata nella LETTERA. Sui fogli e nel frontmatter compaiono due sigle diverse per **la stessa classe**: non sono due sezioni.
- **Il limite del Foglio A**: quel foglio ha il campo **CLASSE in bianco** (è il modulo vuoto della verifica). Prova il **docente** e l'**argomento**, non la classe. Le 16 domande sono comunque le stesse dei Fogli B/C nella sostanza, ma se serve citare un foglio con la classe accertata, sono B e C.
- **Il limite, esplicito**: sono verifiche **in corso d'anno**, non la prova di recupero. Provano il **formato** (domande aperte con disegni, zero esercizi numerici), **non il programma**. Sullo **scope** del recupero prevale la LETTERA, che mette i diodi **all'orale** Carli e alla pratica Protti.
- **Dove sono usate nel vault**: [[04 - Verifica tipo Carli — Diodi]] (trascrizione, mappa, risposte, checklist dei disegni); ricadute su [[Diodi]], [[02 - Prova Orale Carli]] e il callout di formato in [[01 - Prova Scritta Carli]].

#### **[edutecnica.it](https://www.edutecnica.it/)** (fonte secondaria online)
- **Cosa**: manuale online di elettronica ed elettrotecnica, stile didattico ITI
- **Affidabilità**: 8/8 topic chiave verificati coerenti col vault (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)
- **Come la uso**: conferma formule, terminologie, correttezza tecnica
- **URL principale per argomento**:
  - BJT: <https://www.edutecnica.it/elettronica/transistor/transistor.htm>
  - MOSFET: <https://www.edutecnica.it/elettronica/mosfet/mosfet.htm>
  - JFET: <https://www.edutecnica.it/elettronica/jfet/jfet.htm>
  - Amplificatori: <https://www.edutecnica.it/elettronica/amp/amp.htm>
  - Diodi/Zener: <https://www.edutecnica.it/elettronica/zener/zener.htm>
  - Filtri: <https://www.edutecnica.it/elettronica/filtrip/filtrip.htm>
  - Alimentatori: <https://www.edutecnica.it/elettronica/alimentatori/alimentatori.htm>
  - Trifase: <https://www.edutecnica.it/elettrotecnica/trifase/trifase.htm>

### ✅ FONTE VERIFICATA (via OCR) — aggiornato 2026-07-19

#### **Libro Mirandola "Elettrotecnica ed Elettronica Vol.2"** (Zanichelli 2012)
- **File**: `/home/davide/Scaricati/libro per il recupero.pdf` — ~76 MB, **152 pagine-PDF**
- **Stato**: PDF scansionato (immagini). `pdftotext` restituisce 0 caratteri **perché non c'è uno strato di testo** — MA le pagine sono immagini nitide, quindi **leggibili**.
- **Come è stato reso verificabile**: le pagine sono state passate all'**OCR** (`pdftoppm` a 200 dpi + `tesseract -l ita`) e **lette direttamente come immagini**. Il testo integrale è nel file **`/home/davide/Scaricati/libro-OCR-completo.txt`** (una pagina per blocco `===== PAGINA-PDF nnn =====`).
- **Titolo confermato dai piè di pagina**: *Stefano Mirandola — ELETTROTECNICA ED ELETTRONICA Vol.2 © Zanichelli 2012, per Elettronica*.
- **Implicazione**: i contenuti del vault **sono stati incrociati col testo reale**. Dove un argomento è stato verificato, il frontmatter riporta `libro_mirandola: "VERIFICATO ✔ …"` con capitolo, sezione e pagine reali. I segnaposto storici «pag. NON verificabile» vengono sostituiti mano a mano con i riferimenti veri.

### ✅ FONTE VERIFICATA — aggiunta 2026-07-25 (Lotto 13)

#### **Approfondimenti online Zanichelli dello stesso corso Mirandola**

- **Cosa**: schede di approfondimento e di laboratorio pubblicate da Zanichelli a corredo del *Corso di elettrotecnica ed elettronica* di Stefano Mirandola. Sono materiale **dello stesso autore e dello stesso editore** del libro cartaceo, quindi affidabilità pari al libro.
- **Come sono state trovate**: cercando la sonda dell'oscilloscopio, argomento che **non è nelle 152 pagine scansionate**. Lo è invece qui.
- **Scheda usata finora**: *La cancellazione polo-zero nella sonda dell'oscilloscopio (partitore compensato)* — $R_i = 1\ \text{M}\Omega$, $C_i \approx 150$ pF (oscilloscopio **+ cavo**), $R_s = 9\ \text{M}\Omega$, condizione $R_sC_s = R_iC_i$, dimostrazione della f.d.t. costante a $1/10$, $C_s = 16{,}7$ pF, taratura empirica con onda quadra.
  <https://online.scuola.zanichelli.it/mirandola-files/Corso_Elettr_V02/Laboratorio/Mirandola_V2_Laboratorio_Partitore_compensato.pdf>
- **Dove è usata nel vault**: [[L'oscilloscopio]] §2 e §7; [[00 - Perchè (spiegazione intuitiva)]] §13.

> [!important] Il PDF scansionato non è «il libro»
> È **una parte** del libro: pp. ~48-427 del Vol. 2. Fuori da quell'intervallo ci sono il resto del volume, il **Volume 1** (a cui il libro stesso rimanda a p. 84 per le definizioni di segnale) e gli **approfondimenti online**. Prima di dichiarare un argomento assente dal libro — il difetto sistemico **#2**, che ha già colpito 4 volte — va cercato anche lì. Nel Lotto 13 questa ricerca ha evitato la quinta occorrenza.

> [!warning] Numero di pagina PDF ≠ numero di pagina stampato
> Ogni **pagina-PDF** della scansione contiene **due pagine stampate** affiancate (una apertura di libro). Esempio verificato: la pagina-PDF **80** mostra le pagine stampate **202-203**; la pagina-PDF **2** mostra le **48-49**. La corrispondenza **non è una formula fissa** (c'è uno scarto di ~2 pagine da qualche parte nel volume), quindi i folio vengono controllati **sezione per sezione** dal piè di pagina reale.
>
> **Formula verificata per il Cap. 5** (diodi): $\text{pagina stampata} = (\text{pagina-PDF} - 75)\cdot 2 + 192$. Non estrapolarla ad altri capitoli senza ricontrollare il piè di pagina.

> [!tip] Come estrarre una figura dal PDF (metodo del Lotto 3)
> ```bash
> pdftoppm -f N -l N -r 200 -x X -y Y -W W -H H -png "libro per il recupero.pdf" out
> ```
> Ritaglia la **singola figura** invece della doppia pagina intera: ~20-50 KB contro ~1,2 MB. Non serve ImageMagick. Le coordinate si trovano renderizzando prima la pagina intera a 150 dpi (1754×987 px) e moltiplicando per 1,333 per passare a 200 dpi.
>
> ⚠️ **I filename delle immagini in `Allegati/` non sono affidabili** per il numero di pagina: quelli generati prima del 2026-07-19 hanno numeri **non verificati** — controlla il piè di pagina nell'immagine prima di citarla. **Corretti il 2026-07-25** (Lotti 10-11, folio letti dall'immagine): `libro-cap7-pag100-mosfet-invertitore` → `libro-cap7-pp368-369-mosfet-polarizzazione-invertitore`; `libro-alim-pag110` → `libro-cap8-pp388-389-alimentatore-schema-blocchi`; `libro-alim-pag120-regolatori-78xx` → `libro-cap8-pp408-409-tabella-78xx`.
> **Completato il 2026-07-26** (Lotto 15, folio e testatine letti dall'immagine): `libro-cap6-pag80-bjt-polarizzazione` → `libro-cap7-pp328-329-bjt-progetto-polarizzazione` (testatina «7 Gli amplificatori a transistor / 1 Il transistor bipolare (BJT)»); `libro-cap6-pag90-bjt-cc` → `libro-cap7-pp348-349-bjt-collettore-comune` (testatina «7 … / 2 Gli amplificatori a BJT»). Erano sbagliati **due volte**: capitolo (il BJT è il Cap. **7**) e pagina (80/90 invece di 328-329/348-349). **Nessun filename residuo non verificato.**

#### **§2bis — Mappa capitoli → pagine (verificata mano a mano)**

| Cap. | Titolo (dal libro) | Pagine-libro | Pagine-PDF | Stato |
|---|---|---|---|---|
| 2 | La corrente alternata — fasori | 46-51 | 1-3 | ✔ verificato |
| 2 | La corrente alternata — impedenza R/L/C, reattanza, serie/parallelo, componenti reali | 52-61 | 4-8 | ✔ verificato |
| 2 | La corrente alternata — **§2.1 «Risonanza serie»** (form. **2.20**, **2.21**, FIG. 11-12, ESEMPIO 3) | **55-56** | **5-6** | ✔ verificato (OCR + immagini) |
| 2 | La corrente alternata — **§2.2 «Risonanza parallelo»** (form. **2.22**, **2.23**, correzione con $R_L$/$R_C$, FIG. 13-14, ESEMPIO 4) | **57-58** | **6-7** | ✔ verificato (OCR + immagini) |
| 2 | La corrente alternata — chiusura §2 (oscillatori e filtri) + **§2.3 «Condensatori e induttori reali»** (FIG. 15, tg δ **2.24**) | **59** | **7** | ✔ verificato (immagine) |
| 2 | La corrente alternata — **§3 «Il metodo simbolico»** (riquadro PROCEDIMENTO, ESEMPIO 5, FIG. 17A-17B) | **60-61** | **8** | ✔ verificato (OCR + immagine) |
| 2 | La corrente alternata — **§4 «La potenza in alternata»** + §4.1 (form. 2.26-2.32, FIG. 18-19, ESEMPI 6-7) | **62-65** | **9-10** | ✔ verificato (OCR + immagini) |
| 2 | La corrente alternata — **§4.2 «Il rifasamento degli impianti industriali»** (form. **2.33**, FIG. 22-24, ESEMPIO 8) | **65-67** | **10-11** | ✔ verificato (OCR + immagini) |
| 2 | La corrente alternata — quesiti di riepilogo (**n. 13 risonanza serie/parallelo**, nn. 15-18 metodo simbolico, 19-24 potenze) | **80-81** | 18 | ✔ verificato (n. 13 letto dall'immagine) |
| 2 | La corrente alternata — esercizi di fine capitolo (FIG. 40-44; nn. 9-10 FIG. 45-46; nn. 11-13 FIG. 47-49) | **82-83** | 19 | ✔ folio letto dal piè di pagina |
| 3 | **«L'analisi dei segnali»** — apertura del capitolo + §1 «I segnali analogici», §1.1 «Il segnale audio» (FIG. 1-2) | **84-85** | **20** | ✔ verificato (immagine, 2026-07-25) — qui il libro cita l'**oscilloscopio** come strumento del dominio del tempo, e rimanda al **VOLUME 1** per le definizioni di base |
| 3 | Metodo della trasformata di Laplace (**sezione interna** del Cap. 3, non il titolo del capitolo) | **102+** | **29+** | ✔ **presente nella scansione** — fuori programma |
| 4 | I quadripoli — **§2.3 «Risposta di un quadripolo nel dominio del tempo»** (TABELLA 3 forme canoniche, form. **4.26**, FIGURA 24) | **138-139** | **48** | ✔ verificato (immagine, 2026-07-25) — «*per visualizzare la risposta al gradino sull'oscilloscopio si pone in ingresso un'**onda quadra***» |
| 4 | I quadripoli — **§2.4 «Risposta di un quadripolo nel dominio della frequenza»** (form. **4.30-4.32**, FIGURA 29, ESEMPI 11-12) | **142-143** | **50** | ✔ verificato (immagine, 2026-07-25) — ampiezza e **sfasamento** rilevati con l'oscilloscopio al variare della frequenza |
| 4 | I quadripoli — §6 «La qualità dei quadripoli (distorsione e **rumore**)» (Johnson/shot, form. 4.61-4.62) | **180-181** | **69** | ✔ folio letto dal piè di pagina (2026-07-22) |
| 4 | I quadripoli — GUIDA ALLA PROGETTAZIONE: filtri **crossover** per diffusori acustici + PROGETTO 1 | **184-187** | **71-72** | ✔ folio letto dal piè di pagina |
| 4 | I quadripoli — **quesiti di riepilogo** (parametri Z, adattamento, impedenze immagine; FIG. 80/83/86) | **188-189** | **73** | ✔ folio letto dal piè di pagina |
| 4 | I quadripoli — **esercizi di fine capitolo** (nn. 17-19: RC serie, risposta ampiezza/fase, progetto passa alto 1° ordine) | **190-191** | **74** | ✔ folio letto dal piè di pagina |
| 4 | I quadripoli — **§? «I filtri passivi del primo ordine»** (TABELLA 6 RC/RL passa basso e passa alto, TABELLA 7 filtri 2° ordine RLC, ESEMPIO 18) | **156-163** | **57-60** | ✔ folio verificato (PDF 58 → 158-159) — contenuto da auditare |
| 4 | I quadripoli — **filtri del 2° ordine e fattore di qualità**: form. **4.49-4.50** (passa alto/passa banda RLC), **4.51** (picco), **4.52** $\xi = 1/2Q$, **4.53** $Q$, **4.54** $\omega_0$ media geometrica, **4.55-4.56** (Wien, doppio T); FIGURA 49-50 | **162-163** | **60** | ✔ **verificato (immagine, 2026-07-26, Lotto 15)** — folio e testatina «4 I quadripoli» letti dal piè di pagina. La **4.53** è stampata **in pulsazioni**: $Q = \omega_0/(\omega_{tH}-\omega_{tL})$, non $f_0/B$ |
| 5 | **I diodi** — capitolo completo | **192-233** | **75-94** | ✔ verificato (OCR + immagini) |
| 5 | I diodi — **§1 struttura, simbolo, polarizzazione** (FIGURA 5 «Diodo a semiconduttore: A) struttura; B) simboli circuitali; C) contenitore», FIGURA 6 «Polarizzazione di un diodo: A) diretta; B) inversa») | **196** | **77** | ✔ verificato (immagine, 2026-07-28) |
| 5 | I diodi — **§1.3 curva caratteristica** (FIGURA 7 versi convenzionali + zone diretta/inversa; i sei punti dell'andamento; soglia $V_s \approx 0{,}6$ V) | **197** | **77** | ✔ verificato (immagine, 2026-07-28) |
| 5 | I diodi — **§2.6 «Il limitatore»** (definizione del box RIEPILOGO; FIGURA 24 «Limitatori a bassa soglia e forme d'onda relative») | **210-211** | **84** | ✔ verificato (immagine, 2026-07-28) |
| 5 | I diodi — limitatori, seguito (FIGURA 25 «Limitatori con diodi: A) in serie; B) in antiparallelo»; FIGURA 26 limitatore con generatore) | **212** | **85** | ✔ verificato (immagine, 2026-07-28) |
| 5 | I diodi — **§4.2 breakdown inverso: effetto Zener ($V_Z<5$ V) vs effetto valanga ($V_Z>6$ V)** + TABELLA 4 (serie BZX55C, colonna $T_C$) | **220** | **89** | ✔ verificato (immagine + testatina «5 I diodi», 2026-07-28) |
| 5 | I diodi — **§4.3 «Il regolatore di tensione a Zener»** (definizione di quadripolo regolatore, FIGURA 33 blocco funzionale, FIGURA 34 regolatore a Zener, form. **5.10** e **5.11**) | **221** | **89** | ✔ verificato (immagine + testatina, 2026-07-28) |
| 6 | Amplificatori operazionali | — | — | ⚠️ **NON è il capitolo BJT** (vedi nota sotto) |
| 7 | **Gli amplificatori a transistor** (BJT) — capitolo completo | **312-347** | **95-112** | ✔ verificato (OCR + immagini) |
| 7 | Gli amplificatori a transistor — **§3 «I transistor FET e gli amplificatori a FET»** (JFET, MOSFET, ampl. a FET) | **358-369** | **118-124** | ✔ folio letto dall'immagine (2026-07-25) |
| 7 | — **§3.3 «I MOSFET e le porte CMOS»** (FIG. 45 struttura, 46 simboli, 47 caratteristiche, **48 polarizzazione**, 49-50 invertitore/CMOS) | **366-368** | **122-123** | ✔ verificato (immagini) |
| 8 | **Gli alimentatori** — §1 non stabilizzati + **fattore di ripple form. 8.1** (FIG. 3-5) | **388-389** | **133** | ✔ folio letto dall'immagine (2026-07-25) |
| 8 | Gli alimentatori — **§3.1 «Regolatori integrati 78XX/79XX»** (FIG. **20** struttura interna, FIG. **21** collegamento completo) | **406-407** | **142** | ✔ verificato (immagine) |
| 8 | Gli alimentatori — **TABELLA 1** famiglia 78XX ($V_D=2{,}5$ V), §3.2 duale FIG. 22, §3.3 correnti elevate FIG. 23, ESEMPIO 7 (form. $C=I_L/2fV_{rpp}$) | **408-409** | **143** | ✔ verificato (immagine) |

> [!danger] Correzione di numerazione scoperta nel Lotto 4
> Il vault dava il BJT come «Capitolo 6». **È sbagliato**: il capitolo del BJT è il **7, «Gli amplificatori a transistor»** (p. 312, frontespizio con il numero 7; formule numerate 7.1-7.14). Il **Capitolo 6 è quello sugli amplificatori operazionali** — il libro stesso lo cita a p. 312: «amplificatori operazionali, visti nel CAPITOLO 6».
>
> Conseguenza pratica: i file `Allegati/libro-cap6-*.png` hanno **nomi non affidabili** (numero di capitolo e/o folio) — verificare prima dell'uso. Il file `libro-cap7-pag100-mosfet-*` è stato invece verificato e rinominato il 2026-07-25: era davvero Cap. 7 (§3.3), ma alle pp. **368-369**, non «pag. 100».

> [!danger] Seconda affermazione falsa sulla scansione, scoperta nel Lotto 6
> `Il metodo simbolico` sosteneva che il **Capitolo 3** (trasformata di Laplace) «**non è nella scansione** che hai». **È falso**: il Cap. 3 inizia a **p. 102** (pag.-PDF 29). Resta vero che è **fuori programma** — ma è una cosa diversa dal non esserci, e il vault presentava la seconda come giustificazione della prima.
>
> È la **terza volta** che il vault dichiara assente dal libro qualcosa che c'è (Lotto 1: la stessa affermazione sul Cap. 3 nei fasori; Lotto 5: la base comune; qui). **Pattern da cercare attivamente**: `grep -rn "non è nella scansione\|non è presente\|il libro non tratta" Argomenti Esercizi`.

> [!danger] Falsa correzione del 2026-07-20, ritirata il 2026-07-22 — il folio del rumore è **pp. 180-181**
> Il 20/07 era stato annotato qui che la sezione sul **rumore** (Johnson/shot, form. 4.61-4.62), registrata a **pp. 180-181**, andava corretta in **pp. 190-191**. **Quella correzione era sbagliata**: il valore originale era giusto.
>
> Verificato il 22/07 per **tre vie indipendenti**:
> 1. L'**OCR** colloca le formule 4.61-4.62 nella pagina-PDF **069**, non nella 074.
> 2. Il **piè di pagina della pagina-PDF 069**, letto a 300 dpi, riporta **180 | 181**, con testatina «**6** La qualità dei quadripoli (distorsione e rumore)».
> 3. L'**immagine dell'allegato stesso** mostra il folio **180 | 181**: il rename del 20/07 aveva reso il filename in contraddizione col folio visibile dentro l'immagine.
>
> La pagina-PDF **074 è davvero pp. 190-191** — ma contiene gli **esercizi di fine capitolo**, non il rumore. L'errore è stato leggere il folio della pagina giusta e attribuirlo alla **sezione sbagliata**.
>
> **Ripristinato** in `Diodi.md`, `Amplificatori a BJT.md`, nella tabella §2bis qui sopra e nel nome dell'allegato (`libro-cap4-pp180-181-rumore-johnson-shot.png`).
>
> **Lezione**: leggere il folio non basta se poi lo si associa alla sezione sbagliata. Va letta la **testatina** (che nomina il paragrafo) insieme al numero di pagina. Vedi [[00 - Audit e correzioni]], Lotto 8, difetto sistemico #4.

**Conversione pagina Cap. 4**: `pagina stampata = 2·(pagina-PDF) + 42` — verificata in **cinque** punti con folio letti dal piè di pagina: PDF 58 → p. 158, PDF 69 → p. 180, PDF 71 → p. 184, PDF 72 → p. 186, PDF 73 → p. 188, PDF 74 → p. 190.

> [!check] Le tre conversioni sono coerenti fra loro
> Riscritte nella stessa forma: Cap. 2 → $2\cdot\text{PDF} + 44$; Cap. 4 → $2\cdot\text{PDF} + 42$; Cap. 5 → $2\cdot\text{PDF} + 42$; Cap. 7 → $2\cdot\text{PDF} + 122$; **Cap. 8 → $2\cdot\text{PDF} + 122$** (stesso offset del Cap. 7: la scansione è continua da Cap. 7 a Cap. 8 — verificato su PDF 142 → p. 406). Il FET (Cap. 7 §3) segue lo stesso offset: PDF 118 → p. 358, PDF 122 → p. 366, PDF 123 → p. 368.
> Cap. 4 e Cap. 5 condividono lo stesso offset: fra Cap. 2 e Cap. 4 c'è lo **scarto di 2 pagine** già ipotizzato nel riquadro qui sopra, e da lì in poi la corrispondenza resta stabile fino al Cap. 5. Il salto grosso prima del Cap. 7 indica invece che **la scansione non è continua** (mancano pagine fra Cap. 5 e Cap. 7). ⚠️ Continuare comunque a leggere il folio prima di citare.

**Conversione pagina Cap. 2**: `pagina stampata = (pagina-PDF − 1)·2 + 46` — verificata agli estremi su PDF 4 → p. 52 e PDF 8 → p. 60 (folio letto dal piè di pagina).

**Conversione pagina Cap. 7**: `pagina stampata = (pagina-PDF − 95)·2 + 312` — verificata agli estremi su PDF 95 → pp. 312-313 e PDF 110 → pp. 342-343. ⚠️ Come per il Cap. 5, **non estrapolarla ad altri capitoli** senza ricontrollare il piè di pagina.

> La tabella viene estesa a ogni lotto di audit (vedi [[00 - Audit e correzioni]]).

---

## 🗺️ 3. Tracciamento: mappa LETTERA → Argomenti del vault

### **Carli — prova scritta** (esercizi)

| LETTERA | Argomenti vault | Esercizi svolti |
|---|---|---|
| Circuiti AC (impedenze, P/Q/S, fasori) | `[[Impedenza]]`, `[[Metodo simbolico]]`, `[[Potenze AC]]` | `[[Esercizi - Impedenza]]`, `[[Esercizi - Metodo simbolico]]`, `[[Esercizi - Potenze AC]]` |
| Filtri passivi **1° ordine** (RC/RL) | `[[Filtri 1° ordine]]` | `[[Esercizi - Filtri]]` |
| BJT (pilota in corrente) | `[[BJT]]` | `[[Esercizi - BJT]]` |
| JFET **canale N** | `[[JFET]]` | `[[Esercizi - JFET]]` |
| MOSFET **canale N enhancement** | `[[MOSFET]]` | `[[Esercizi - MOSFET]]` |

### **Carli — prova orale** (domande)

| LETTERA | Argomenti vault |
|---|---|
| Diodo (normale, Zener, Schottky) | `[[Diodi]]` |
| Circuiti AC | vedi sopra |
| Filtri 1° ordine | vedi sopra |

### **Protti — prova pratica** (misure con oscilloscopio)

| LETTERA | Argomenti vault |
|---|---|
| Circuiti con diodi | `[[Diodi]]`, `[[Alimentatori]]` |
| Segnali sinusoidali | `[[Segnali sinusoidali e fasori]]` |
| Reti RLC in regime sinusoidale | `[[Reti RLC]]`, `[[Impedenza]]` |
| Filtri passivi | `[[Filtri 1° ordine]]` |
| BJT | `[[BJT]]` |
| Amplificatori con BJT | `[[Amplificatori a BJT]]` |
| **Uso oscilloscopio** | `[[L'oscilloscopio]]` ← strumento trasversale a tutti i punti |

### Argomenti "extra" nel vault (fuori LETTERA — solo approfondimento)

| Argomento | File | Perché presente |
|---|---|---|
| Sinusoidi, fasori, Fourier | `[[Segnali sinusoidali e fasori]]` | propedeutico ai circuiti AC (Carli scritta + Protti pratica) |
| Potenze AC (P, Q, S, $\cos\varphi$) | `[[Potenze AC]]` | parte integrante "circuiti AC" Carli scritta |
| Metodo simbolico | `[[Metodo simbolico]]` | procedura per risolvere circuiti AC |
| Risonanza (ω₀, Q) | `[[Reti RLC]]` | parte integrante "reti RLC" Protti pratica |
| Raddrizzatori, Graetz, 78xx | `[[Alimentatori]]` | parte integrante "circuiti con diodi" Carli orale + Protti pratica |
| **Operazionali** | ❌ **ASSENTE** dal vault | non richiesto dalla LETTERA e non coperto dal libro/corso |
| **MOSFET depletion / P-channel** | solo accenno in `[[MOSFET]]` | solo enhancement n è richiesto dalla LETTERA |

---

## 📋 4. Note operative per lo studente Carli

1. **Studia dalla LETTERA + edutecnica.it + Mirandola** — ora tutte e 3 sono fonti VERIFICATE (il libro via OCR/lettura pagine, vedi `libro-OCR-completo.txt`).
2. **Mirandola** è il libro di testo del corso: usalo con fiducia per **figure**, **schemi** ed **esempi svolti**. I riferimenti di pagina nel vault sono controllati sul testo reale; ricorda solo che *pagina-PDF ≠ pagina stampata* (vedi riquadro in §2).
3. **Per la prova Carli (settembre 2026)**: punta sugli argomenti della LETTERA scritta/orale. Gli "extra" (operazionali, P-channel, depletion) sono **fuori programma** — non sprecare tempo.
4. **Per la prova Protti (settembre 2026)**: pratica con l'oscilloscopio reale; usa `[[L'oscilloscopio]]` del vault + misure in laboratorio.
5. **In caso di dubbio su una formula**: è confermata sia da edutecnica.it sia dal testo Mirandola (OCR in `libro-OCR-completo.txt`). Le discrepanze trovate e risolte sono elencate in [[00 - Audit e correzioni]].
