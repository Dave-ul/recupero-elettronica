---
tags: [recupero, elettronica, fonti, trasparenza, lettera-majorana, audit]
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO)"
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave; ora anche in PDF in Fonti/"
libro_mirandola: "VERIFICATO ✔ (mappa pagine rifatta il 2026-08-19) — Fonti/Mirandola Volume 2/, 12 PDF, 282 pagine-PDF, senza strato di testo. Conversione: pagina stampata = 2·(pagina-PDF) − 6, offset costante, verificata su 4 folio in 3 capitoli. Vedi §2bis."
fonti_aggiunte_2026_08_19: "appunti Poggi · tre verifiche FUSI del prof. Carli · Edutecnica in PDF · Mirandola Vol.1 e Vol.2"
fonti_aggiunte_2026_08_28: "pagina di quaderno del 18/3 sul BJT (foto) — seguito della p. 3 degli appunti Poggi, assente dal PDF. Vedi §2 e [[BJT]] §1-bis."
esame: "1 settembre 2026 — scritto 8:00-13:00 (Carli) · orale+pratico 14:00-17:00 (Carli e Protti insieme)"
---

# 📚 Fonti del vault — Note di trasparenza

> Questo file è la **dichiarazione di fonti** del vault Obsidian `elettronicaa`. In 1 sola lettura, lo studente Carli può capire **da dove vengono i contenuti**, **cosa è verificato**, e **cosa NON è verificabile**. Tutti gli altri file del vault rimandano qui quando serve trasparenza.

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

> [!important] Riallineamento del 2026-08-19
> Questo paragrafo è stato riscritto. Il vault era stato costruito a luglio su un'altra
> macchina, e **tutti i path che citava non esistono più**. Nel frattempo sono arrivate
> **quattro fonti nuove** — gli appunti Poggi, le tre verifiche del prof. Carli, Edutecnica
> in PDF e le scansioni complete dei due volumi Mirandola — di cui il vault non sapeva
> niente. Tutto il materiale sta ora in un posto solo:
>
> ```
> /home/parzivalkey/Scrivania/elettronicaa/Fonti/
> ```

### 🥇 Gerarchia delle fonti

Quando due fonti dicono cose diverse, vince quella più in alto. Quando una fonte **tace**
su un argomento, quello è un indizio che l'argomento è fuori programma — ed è il criterio
con cui è stato potato [[Calendario]].

| # | Fonte | Cosa stabilisce |
|---|---|---|
| 1 | **La LETTERA** | **cosa esce.** Non si discute |
| 2 | **Le tre verifiche FUSI del prof. Carli** | **come interroga, e su cosa sei caduto** |
| 3 | **Le tre verifiche 4E sui diodi (foto)** | come interroga *a domande aperte* |
| 4 | **Gli appunti Poggi** (PDF a 20 pp. **+** la pagina fotografata del 18/3) | **cosa è stato fatto davvero in classe** |
| 5 | **Mirandola Vol. 2** | la teoria e il linguaggio ufficiali del corso |
| 6 | **Edutecnica** | gli svolgimenti passo-passo che il Mirandola non dà |

---

### ✅ **La LETTERA Majorana** — fonte ufficiale del compito

- **File**: `Fonti/MAJORANA_lettera_giudizio_sospeso_recuperi_(Secondo_Periodo).pdf`
- **Affidabilità**: 100% (protocollo 2760, firmata dal Dirigente Scolastico)
- **Ha uno strato di testo**: si rilegge in qualunque momento con `pdftotext -layout`
- **Testo verbatim delle due prove Carli**:
  > PROVA SCRITTA: **esercizi** sui circuiti in corrente alternata, sui filtri passivi del primo ordine, sui transistor BJT, sui transistor JFET a canale N e sui transistor MOSFET a canale N ad arricchimento. PROVA ORALE: **domande sul diodo**, sui circuiti in corrente alternata e sui filtri passivi del primo ordine.

> [!info] Data e orario della prova — noti dal 2026-08-19
> **Martedì 1 settembre 2026**: scritto **8:00-13:00** (cinque ore), orale **e** pratico
> insieme **14:00-17:00**. Non sono due prove in due giorni: sono due sessioni dello stesso
> giorno, con Carli e Protti insieme il pomeriggio. Vedi [[00 - Indice Generale]].

---

### ✅ **Le tre verifiche del prof. Carli** — aggiunte il 2026-08-19

- **File**: `Fonti/FUSI_02-03-26_260616_183723.pdf` (18 pp.) ·
  `Fonti/FUSI_24-04-26_260616_183749.pdf` (18 pp.) ·
  `Fonti/FUSI_29-05-26_260616_183828.pdf` (20 pp.)
- **Cosa sono**: le prove scritte vere del docente, date in corso d'anno, **corrette a mano
  e restituite**. Ogni fascicolo contiene il testo, il tuo svolgimento, e — nelle pagine
  finali — lo svolgimento corretto.
- **Perché contano più di qualunque libro**: non dicono solo *come* Carli formula un
  esercizio. Dicono **su cosa sei caduto**, con le annotazioni in rosso del docente
  («NON SVOLTO PER NULLA», «errato», «errata relazione che fornisce V_GS»). È la lista
  degli argomenti da rifare, scritta da chi correggerà anche a settembre.
- **Scansionate, senza strato di testo**: `pdftotext` restituisce 0 caratteri. Si leggono
  come immagini.
- **Dove sono usate nel vault**: [[05 - Verifiche FUSI (Carli)]] — trascrizione della mappa
  esercizio → argomento e degli errori segnati — e in [[Calendario]], dove sono i
  checkpoint dei giorni 1, 4, 7, 9, 10 e la sessione lunga del giorno 11.

---

### ✅ **Gli appunti Poggi** — aggiunti il 2026-08-19

- **File**: `Fonti/appunti poggi.pdf` — **20** pagine, il quaderno del corso (più la pagina
  sciolta del **18/3**, vedi la voce qui sotto)
- **Cosa stabiliscono**: sono la prova documentale di **cosa è stato svolto in classe**.
  Un argomento che non c'è né qui, né nella lettera, né in nessuna delle tre verifiche FUSI
  è quasi certamente fuori programma: è il triplo filtro con cui [[Calendario]] ha tolto
  risonanza, potenza in alternata, diagrammi di Bode, trifase e derating.
- **Il limite, esplicito**: sono un **riassunto**, non una fonte a sé. Ogni pagina ha un
  corrispettivo sul Mirandola, più esteso e con gli esempi svolti. Negli appunti mancano i
  passaggi intermedi, ed è lì che si perdono i punti allo scritto. **Vanno sempre usati in
  coppia col libro.**

| appunti Poggi | Mirandola Vol. 2 |
|---|---|
| p. 1, 5, 7, 8 — numeri complessi, forme di rappresentazione | PDF 27-28 → libro 48-51 |
| p. 6, 7 — segnale sinusoidale, T/f/ω | PDF 48-49 → libro 90-93 |
| p. 4, 10 — impedenza, reattanze, serie e parallelo | PDF 28-30 → libro 51-55 |
| p. 12, 16 — bipolo, quadripolo, matrice Z | PDF 63 → libro 120-121 |
| p. 9, 18 — f.d.t., filtri del 1° ordine, poli | PDF 70-73 → libro 134-141 |
| p. 3, 11, 13, 15 — BJT: struttura, zone, h_FE, caratteristiche | PDF 160-162 → libro 314-319 |
| p. 17, 19 — JFET: analogia col BJT, maglie di polarizzazione | PDF 183-185 → libro 360-365 |
| **foto del 18/3** (fuori dal PDF) — drogaggio As/B, polarizzazione delle giunzioni, 3 schemi | PDF 160-163 → libro 313-317 e 326 |

> [!tip] Le due pagine che valgono più delle altre
> **p. 9** (ricavo completo della G(s) di un passa-basso RC col partitore) e **p. 19** (le
> due maglie del JFET: V_GS0 = −R_S·I_D0 e V_DD = I_D0·(R_S + R_D) + V_DS0). Sono i due
> modelli di svolgimento su cui si reggono gli esercizi di progetto delle verifiche.

---

### ✅ **La pagina di quaderno del 18/3 sul BJT** — foto, aggiunta 2026-08-28

- **File**: `Fonti/WhatsApp Image 2026-08-28 at 18.03.57.jpeg` · copia linkabile in
  `Allegati/appunti-poggi-18-03-bjt.jpeg`
- **Cosa è**: **una pagina sola**, datata **18/3** in alto a destra, intitolata in rosso
  «TRANSISTOR BJT». Contiene, nell'ordine: un richiamo sul **condensatore** (dielettrico,
  campo elettrico, «le cariche libere non possono restare»), l'**etimologia** *transfer
  resistor* con lo schema a blocchi ingresso/uscita, il **funzionamento del BJT** con la
  struttura **n⁺⁺ — p — n** e i droganti **arsenico** e **boro** disegnati nel reticolo, il
  **funzionamento con le polarizzazioni delle giunzioni**, e **tre schemi di
  polarizzazione**.
- **Perché sta nella famiglia «appunti Poggi»**: è lo **stesso quaderno** della **p. 3** di
  `Fonti/appunti poggi.pdf` — stessa carta a quadretti a spirale, stessa mano, stessi
  titoli in rosso, stessa data in alto a destra (lì «6/3»). La p. 3 è la lezione
  **precedente** (definizione, npn/pnp, simboli, Kirchhoff); questa è il **seguito**, e nel
  PDF a 20 pagine **non c'è**. Vale quindi lo stesso posto nella gerarchia: **#4 — cosa è
  stato fatto davvero in classe**.
- **Cosa aggiunge davvero al vault** (il resto era già coperto):
  1. **i droganti hanno un nome**: **arsenico (As)** per la zona n, **boro (B)** per la p.
     Il vault spiegava il drogaggio n col **fosforo** — stesso gruppo 15, stessa fisica, ma
     a lezione si è detto arsenico;
  2. **la struttura è asimmetrica**: **n⁺⁺** l'emettitore, **n** semplice il collettore. Il
     Mirandola dice solo «le due zone esterne sono fortemente drogate»;
  3. le due frasi da ripetere all'orale: «**BASE molto stretta**» e «**zona di svuotamento
     tra base e collettore decisamente grande**»;
  4. il **condensatore come modello della zona di svuotamento** — regione con campo e
     senza portatori liberi.
- **Il limite, esplicito**: è **una foto di una pagina**, non una fonte con numero di
  pagina citabile. Come per tutti gli appunti, **vale in coppia col libro**: ogni
  affermazione qui sopra ha un riscontro in Mirandola Cap. 7 §1, pp. 313-317 e p. 326.
- **Dove è usata nel vault**: [[BJT]] §1-bis e §1-ter (trascrizione integrale) ·
  [[00 - Perchè (spiegazione intuitiva)]] §0.E (nota su arsenico e boro).

---

### ✅ **Le tre verifiche 4E sui diodi** — fogli fotografati, aggiunte 2026-07-28

- **Cosa**: due compiti in classe sui diodi, **16 + 23 = 39 domande aperte**, stesso docente.
  I Fogli B e C portano il riferimento *«libro capitolo 5 I diodi da pagina 192 a pagina 224»*;
  il Foglio A no. Fogli in `Allegati/`: `verifica-carli-diodi-16dom.jpeg`,
  `verifica-carli-4E-diodi-parte1.jpeg`, `verifica-carli-4E-diodi-parte2.jpeg`.
- **Perché sono tue**: l'intestazione dei Fogli B e C dice «Classe 4E», che è la sezione di
  elettronica dell'articolata 4BEM indicata nella LETTERA. Due sigle, una classe sola.
- **Il limite del Foglio A**: campo CLASSE in bianco — prova il docente e l'argomento, non
  la classe.
- **Il limite, esplicito**: sono verifiche **in corso d'anno**. Provano il **formato**
  (domande aperte con disegni, zero esercizi numerici), **non il programma**. Sullo scope
  prevale la LETTERA, che mette i diodi all'**orale** Carli e alla pratica Protti.
- **Dove sono usate**: [[04 - Verifica tipo Carli — Diodi]], con ricadute su [[Diodi]] e
  [[02 - Prova Orale Carli]].

> [!success] Le risposte sono già scritte
> Le risposte alle **D1-D23** sono state redatte il 2026-08-19 e stanno in
> [[diodi-risposte]] (in `Strumenti/`). Il [[Calendario]] non le fa più riscrivere: le fa
> **ripetere a voce** il 31 agosto, come richiamo a distanza.

---

### ✅ **Mirandola, «Elettrotecnica ed Elettronica» Vol. 2** (Zanichelli 2012)

- **Dove**: `Fonti/Mirandola Volume 2/` — **12 PDF** divisi per intervallo di pagina-PDF
  (`001-003.pdf`, `004-025.pdf`, … `237-282.pdf`), per un totale di **282 pagine-PDF**.
- **Cos'è davvero**: non una scansione di carta, ma la **cattura schermo del lettore
  digitale Zanichelli** — si vede la barra di interfaccia sovrapposta al centro di ogni
  pagina («Tieni premuto ESC per uscire dalla modalità a schermo intero»). Conseguenza
  pratica: la barra **copre una striscia orizzontale** a circa il 90% dell'altezza, e può
  nascondere una riga di testo o una parte di figura. Se una figura sembra tagliata, non
  è la figura: è la barra.
- **Nessuno strato di testo**: `pdftotext` restituisce 0 caratteri. Si legge come immagine.
- **Titolo confermato dal piè di pagina**: *Stefano Mirandola — ELETTROTECNICA ED
  ELETTRONICA Vol.2 © Zanichelli 2012, per Elettronica*.
- **Come si usa**: è il libro di classe, quello a cui il prof. rimanda esplicitamente. Le
  sezioni QUESITI sono formulate come le domande dell'orale e le pagine FORMULE sono il
  riassunto ufficiale. **Per la teoria e per l'orale è la fonte da usare.**

#### §2bis — Da pagina-PDF a pagina stampata

> [!check] Una formula sola, e stavolta è costante
> ```
> pagina stampata (sinistra) = 2 · (pagina-PDF) − 6
> ```
> Ogni pagina-PDF è **un'apertura di libro**, quindi mostra **due** folio: quello pari a
> sinistra e il dispari a destra.
>
> **Verificata il 2026-08-19 leggendo il piè di pagina** su quattro punti in tre capitoli
> diversi:
>
> | pagina-PDF | folio letti | testatina | atteso da formula |
> |---|---|---|---|
> | 27 | **48 \| 49** | «2 La corrente alternata» | 48 ✔ |
> | 42 | **78 \| 79** | «2 La corrente alternata» | 78 ✔ |
> | 99 | **192 \| 193** | «5 I diodi» | 192 ✔ |
> | 160 | **314 \| 315** | «7 Gli amplificatori a transistor» | 314 ✔ |
>
> L'offset è **costante su tutto il volume**: questa scansione è continua, e non ha i salti
> che aveva quella precedente. Resta comunque valida la regola di sempre — **leggi il folio
> e la testatina prima di citare**, perché la testatina è l'unica cosa che dice a quale
> *paragrafo* appartiene la pagina, e l'errore già commesso in passato è stato leggere il
> folio giusto e attribuirlo alla sezione sbagliata.

**Dove trovare un capitolo** (pagina-PDF calcolata come `(pagina libro + 6) / 2`):

| Cap. | Titolo | Pagine libro | Pagine-PDF | File |
|---|---|---|---|---|
| 2 | La corrente alternata | 46-83 | 26-44 | `026-044.pdf` |
| 3 | L'analisi dei segnali | 84-119 | 45-62 | `045-062.pdf` |
| 4 | I quadripoli | 120-191 | 63-98 | `063-098.pdf` |
| 5 | I diodi | 192-233 | 99-119 | `099-118.pdf` + `119-158.pdf` |
| 6 | Amplificatori operazionali | 234-311 | 120-158 | ⛔ fuori programma |
| 7 | Gli amplificatori a transistor (BJT e FET) | 312-385 | 159-195 | `159-195.pdf` |
| 8 | Gli alimentatori | 386-427 | 196-216 | `196-216.pdf` |

> [!warning] Il capitolo del BJT è il **7**, non il 6
> Correzione storica che resta valida: il vault dava il BJT come «Capitolo 6». Il Capitolo 6
> è quello sugli **amplificatori operazionali** — il libro stesso lo cita a p. 312:
> «amplificatori operazionali, visti nel CAPITOLO 6». Gli allegati `libro-cap6-*.png` hanno
> nomi non affidabili: verificare prima dell'uso.

> [!danger] Fonte ritirata: `libro-OCR-completo.txt`
> Fino al 2026-07-31 questo file dichiarava che il testo integrale del libro stava in
> `/home/davide/Scaricati/libro-OCR-completo.txt`, prodotto con `tesseract` da una scansione
> **diversa, a 152 pagine-PDF**, su un'altra macchina. **Quel file non esiste più, e neanche
> quella scansione.**
>
> È la terza volta che il vault cita una fonte che non può più riaprire (prima
> `/tmp/lettera_giudizio.txt`, poi i backup in `/tmp/recrop_work/`): è il difetto sistemico
> **#6** registrato in [[00 - Audit e correzioni]]. Qui viene **ritirata**, non riscritta.
>
> **Cosa resta valido** dei riferimenti prodotti con quella fonte: i riferimenti *di
> contenuto* — numero di FIGURA, numero di formula, titolo di paragrafo, numero di pagina
> **stampata**. Quelli erano letti dal libro e il libro non è cambiato.
> **Cosa non è più valido**: qualunque numero di **pagina-PDF** scritto prima del
> 2026-08-19, e le tre formule di conversione per capitolo (`2·PDF+44`, `2·PDF+42`,
> `2·PDF+122`) — erano corrette per la vecchia scansione e sono sbagliate per questa.

---

### ✅ **Edutecnica** — ora anche in PDF, aggiunto il 2026-08-19

- **File**: `Fonti/Edutecnica Elettronica.pdf` · `Fonti/Edutecnica Elettrotecnica.pdf`
- **Novità**: il vault citava solo il sito. I due PDF sono la stessa fonte, ma **citabile
  per pagina e consultabile offline** — ed è così che [[Calendario]] la usa.
- **A cosa serve davvero**: il Mirandola dà solo il risultato tra parentesi quadre;
  Edutecnica mostra **lo svolgimento intero**. Quando devi imparare *come si fa* un
  esercizio, e non solo se il risultato torna, vale di più. **Per la prova scritta è la
  fonte da usare.**
- **Affidabilità**: 8/8 topic chiave verificati coerenti col vault.
- **Le due eccezioni da ricordare**:
  - **Filtri del 1° ordine** — Edutecnica **non li tratta**. I suoi «circuiti accoppiati e
    filtri di banda» (pp. 48-57) sono circuiti risonanti per radiofrequenza, un altro
    argomento. Lì le uniche fonti sono il Mirandola e le pp. 9 e 18 di Poggi.
  - **MOSFET** — qui è il contrario: il Mirandola gli dedica 5 pagine, la fonte vera è
    Edutecnica (pp. 1-16).
- **URL per argomento** (dominio unico autorizzato):
  - BJT: <https://www.edutecnica.it/elettronica/transistor/transistor.htm>
  - MOSFET: <https://www.edutecnica.it/elettronica/mosfet/mosfet.htm>
  - JFET: <https://www.edutecnica.it/elettronica/jfet/jfet.htm>
  - Amplificatori: <https://www.edutecnica.it/elettronica/amp/amp.htm>
  - Diodi/Zener: <https://www.edutecnica.it/elettronica/zener/zener.htm>
  - Filtri: <https://www.edutecnica.it/elettronica/filtrip/filtrip.htm>
  - Alimentatori: <https://www.edutecnica.it/elettronica/alimentatori/alimentatori.htm>

---

### ✅ **Approfondimenti online Zanichelli** dello stesso corso Mirandola

- **Cosa**: schede di approfondimento e di laboratorio pubblicate da Zanichelli a corredo
  del corso. Stesso autore, stesso editore: affidabilità pari al libro.
- **Scheda usata**: *La cancellazione polo-zero nella sonda dell'oscilloscopio (partitore
  compensato)* — R_i = 1 MΩ, C_i ≈ 150 pF (oscilloscopio + cavo), R_s = 9 MΩ, condizione
  R_sC_s = R_iC_i, f.d.t. costante a 1/10, C_s = 16,7 pF, taratura empirica con onda quadra.
  <https://online.scuola.zanichelli.it/mirandola-files/Corso_Elettr_V02/Laboratorio/Mirandola_V2_Laboratorio_Partitore_compensato.pdf>
- **Dove è usata**: [[L'oscilloscopio]] §2 e §7; [[00 - Perchè (spiegazione intuitiva)]] §13.

---

### ℹ️ **Mirandola Volume 1** — c'è, ed è fuori programma

- **Dove**: `Fonti/Mirandola Volume 1/` — 10 PDF, pagine-PDF 001-184.
- **Perché è annotato qui anche se non serve**: il difetto sistemico **#2** del vault è
  «dichiarare assente dal libro qualcosa che c'è», ed è già costato quattro correzioni. Il
  Volume 1 c'è: è elettronica **digitale** (reti logiche, contatori, memorie,
  microprocessori) e il Vol. 2 ci rimanda a p. 84 per le definizioni di base di segnale.
- **Quando aprirlo**: praticamente mai. Nessuna voce della LETTERA lo tocca. Se serve una
  definizione di segnale che il Vol. 2 dà per nota, sta lì.

---

### 🗺️ Dove sta cosa — mappa rapida

```
elettronicaa/                    ← il vault Obsidian: tutto è qui dentro, tutto è linkabile
├── 00 - Indice Generale.md      la mappa d'ingresso alle tre prove
├── Calendario.md                il piano giorno per giorno — copia unica
├── Argomenti.md · Esercizi.md   i due MOC di navigazione
├── Argomenti/                   13 note di teoria + l'hub «00 - Perchè»
├── Esercizi/                    13 note di esercizi svolti
├── Prove/                       01-03 le tre prove · 04-05 il materiale vero del docente
├── Strumenti/                   quello che si porta al compito
│   ├── Formulario rapido.md      Parte A cheat sheet + Parte B formule (uniti il 2026-08-27)
│   └── diodi-risposte.html      risposte D1-D23, già scritte
├── Meta/                        trasparenza e registro — questo file sta qui
├── Allegati/                    74 immagini + INDEX.md
└── Fonti/                       i sorgenti, fuori da git perché pesano 274 MB
    ├── MAJORANA_lettera_…pdf    la LETTERA
    ├── FUSI_02-03-26_…pdf       verifica alternata + filtri
    ├── FUSI_24-04-26_…pdf       verifica BJT
    ├── FUSI_29-05-26_…pdf       verifica JFET + MOSFET
    ├── appunti poggi.pdf        il quaderno del corso
    ├── Edutecnica Elettronica.pdf
    ├── Edutecnica Elettrotecnica.pdf
    ├── Mirandola Volume 1/      10 PDF — digitale, fuori programma
    ├── Mirandola Volume 2/      12 PDF — il libro di classe
    └── WhatsApp Image …jpeg     le tre foto delle verifiche 4E sui diodi
                                  + la pagina di quaderno del 18/3 sul BJT
```

> [!info] Perché una radice sola
> Fino al 2026-08-20 il vault era la sottocartella `Recupero Elettronica/`, e `Fonti/` e
> `diodi-risposte.html` stavano **fuori**: si potevano solo citare come path testuali, non
> aprire con un clic. Il calendario, per lo stesso motivo, esisteva in due copie da tenere
> allineate a mano. Ora la radice è una: i PDF del Mirandola si aprono da dentro Obsidian e
> il calendario è uno solo.


---

## 🗺️ 3. Tracciamento: mappa LETTERA → Argomenti del vault

### **Carli — prova scritta** (esercizi)

| LETTERA | Argomenti vault | Esercizi svolti |
|---|---|---|
| Circuiti AC (impedenze, P/Q/S, fasori) | `[[Impedenza dei bipoli R, L, C]]`, `[[Il metodo simbolico]]`, `[[Le potenze in alternata]]` | `[[Esercizi - Impedenza dei bipoli R, L, C]]`, `[[Esercizi - Il metodo simbolico]]`, `[[Esercizi - Le potenze in alternata]]` |
| Filtri passivi **1° ordine** (RC/RL) | `[[Filtri passivi del primo ordine]]` | `[[Esercizi - Filtri passivi del primo ordine]]` |
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
| Reti RLC in regime sinusoidale | `[[Reti RLC e risonanza]]`, `[[Impedenza dei bipoli R, L, C]]` |
| Filtri passivi | `[[Filtri passivi del primo ordine]]` |
| BJT | `[[BJT]]` |
| Amplificatori con BJT | `[[Amplificatori a BJT]]` |
| **Uso oscilloscopio** | `[[L'oscilloscopio]]` ← strumento trasversale a tutti i punti |

### Argomenti presenti nel vault ma non nominati dalla LETTERA

Allineato il 2026-08-19 alla potatura di [[Calendario]]. Il criterio è il triplo filtro:
un argomento resta **solo** se compare nella LETTERA, negli appunti Poggi, o in una delle
tre verifiche FUSI.

| Argomento | File | Stato |
|---|---|---|
| Sinusoidi e fasori | `[[Segnali sinusoidali e fasori]]` | ✅ **dentro** — propedeutico ai circuiti AC, e «segnali sinusoidali» è nella LETTERA per Protti |
| Metodo simbolico | `[[Il metodo simbolico]]` | ✅ **dentro** — è *la* procedura per risolvere i circuiti AC della prova scritta |
| Reti RLC in regime sinusoidale | `[[Reti RLC e risonanza]]` §1-2 | ✅ **dentro** — nominato dalla LETTERA per Protti. È l'analisi con le impedenze complesse |
| Amplificatori a BJT | `[[Amplificatori a BJT]]` | ✅ **dentro** — nominato dalla LETTERA per Protti |
| Potenze AC (P, Q, S, cos φ) | `[[Le potenze in alternata]]` §1-2 | 📖 **solo lettura per l'orale**, 20 min il 20 agosto. Non è in Poggi né in nessuna verifica, ma all'orale la LETTERA dice «circuiti in corrente alternata» senza restringere |
| Risonanza (ω₀, Q, banda) | `[[Reti RLC e risonanza]]` §3+ | 📖 **solo la definizione**, stessi 20 minuti. Non fatta in classe: la parola «risonanza» non compare né in Poggi né in nessuna delle tre verifiche |
| Alimentatori (raddrizzatori, Graetz, 78xx) | `[[Alimentatori]]` §1 e §4 | 📖 **solo lettura**, 25 min il 23 agosto. La LETTERA dice «circuiti con diodi» per Protti, e l'alimentatore è il circuito con diodi del banco di laboratorio |
| Rifasamento **monofase** | `[[Le potenze in alternata]]` §5 | 📖 **dentro per l'orale** — è il rifasamento del libro (Mirandola §4.2, 220 V, una sola $C$ in parallelo al carico) |
| Rifasamento **trifase** (sistema a 3 fili, $V_{\text{conc}}$, $C$ per fase) | **rimosso dal vault il 2026-08-21** | ⛔ **fuori** — non nella LETTERA, non in Poggi, non in nessuna verifica |
| Diagrammi di Bode, filtri 2° ordine, passa-banda | `[[Filtri passivi del primo ordine]]` | ⛔ **fuori** — la LETTERA dice «filtri passivi del **primo** ordine» |
| Amplificatori operazionali | ❌ assente dal vault | ⛔ **fuori** — Cap. 6 del libro, mai richiesto |
| MOSFET depletion | accenno di confronto in `[[MOSFET]]` §5 | ⛔ **fuori** — la LETTERA dice «ad arricchimento». Resta solo il quesito d'orale «differenza enhancement/depletion» |
| JFET canale P | **rimosso dal vault il 2026-08-21** | ⛔ **fuori** — la LETTERA dice «canale N». Resta il warning anti-trabocchetto in `[[Formulario rapido]]` §8.1 |

## 📋 4. Note operative

1. **L'ordine in cui aprire le cose**, quando studi un argomento: prima la pagina di
   [[Calendario]] del giorno, che dice cosa e in che ordine; poi gli **appunti Poggi**
   come indice; poi le pagine del **Mirandola** corrispondenti, per i passaggi intermedi;
   poi **Edutecnica** per gli esercizi svolti; e la nota del **vault** quando una
   spiegazione non scende al primo colpo.
2. **Le verifiche FUSI non sono un ripasso finale, sono il termometro.** Ogni checkpoint
   del calendario ne rifà una porzione da zero e cronometrata. Gli esercizi segnati «NON
   SVOLTO PER NULLA» o «errato» in rosso sono, letteralmente, la lista di cosa il docente
   sa già che non sai fare: vedi [[05 - Verifiche FUSI (Carli)]].
3. **Mirandola per la teoria e per l'orale, Edutecnica per lo scritto.** Il libro dà solo
   il risultato tra parentesi quadre; Edutecnica mostra lo svolgimento. Due eccezioni:
   i **filtri del 1° ordine** (solo Mirandola + Poggi) e i **MOSFET** (soprattutto
   Edutecnica).
4. **Fuori programma, e non è una perdita: è tempo guadagnato.** Amplificatori
   operazionali, MOSFET depletion e canale P, JFET canale P, trifase e rifasamento
   industriale, diagrammi di Bode, filtri del 2° ordine, derating. Nessuno compare nella
   LETTERA, negli appunti Poggi o nelle tre verifiche FUSI.
5. **Per il pomeriggio del 1° settembre** (orale + pratico insieme, 14:00-17:00): le tre
   domande d'orale di Carli sono **diodo, circuiti in alternata, filtri del 1° ordine** —
   tutte e tre, non solo il diodo. Per Protti serve l'oscilloscopio su tutto il programma:
   [[L'oscilloscopio]] e [[03 - Prova Pratica Protti]].
6. **In caso di dubbio su una formula**: si controlla su Edutecnica **e** sul Mirandola.
   Le discrepanze trovate e risolte sono in [[00 - Audit e correzioni]].
