---
tags: [recupero, elettronica, verifiche, carli, fonte-primaria, checkpoint]
fonte: "tre verifiche scritte del Prof. Carlo Carli, corrette a mano e restituite"
file: "Fonti/FUSI_02-03-26… · Fonti/FUSI_24-04-26… · Fonti/FUSI_29-05-26…"
aggiunto: 2026-08-19
---

# 05 — Le tre verifiche del prof. Carli

> [!important] Perché questa è la pagina più importante del vault
> Tutto il resto del vault è **materiale analogo** a quello che potrebbe uscire. Queste
> tre no: sono le **prove vere dello stesso docente che correggerà a settembre**, sui
> tuoi fogli, **con le sue annotazioni in rosso**.
>
> Non dicono solo *come* Carli formula un esercizio. Dicono **su cosa sei caduto** — ed è
> una lista scritta da lui, non ricostruita da noi. Per autorevolezza vengono subito dopo
> la LETTERA, e prima del libro e di Edutecnica: vedi [[00 - Fonti e note]] §2.

---

## Le tre verifiche

| Verifica | File | Pagine | Argomenti | Dove nel calendario |
|---|---|---|---|---|
| **02-03-2026** | `Fonti/FUSI_02-03-26_260616_183723.pdf` | 18 | circuiti in alternata + filtri del 1° ordine | giorni **1** (20 ago, es. 1 e 6) e **4** (23 ago, integrale) |
| **24-04-2026** | `Fonti/FUSI_24-04-26_260616_183749.pdf` | 18 | BJT: polarizzazione, commutazione, amplificatore | giorno **7** (26 ago, tutti e 7) |
| **29-05-2026** | `Fonti/FUSI_29-05-26_260616_183828.pdf` | 20 | JFET canale N + MOSFET enhancement | giorni **9** (28 ago, es. 1-5) e **10** (29 ago, es. 6-8) |

E tutte e tre di seguito, sotto timer unico, nel pomeriggio del **giorno 11** (30 agosto):
è l'unica sessione lunga del piano, e serve a sapere com'è stare cinque ore sui conti.

> [!info] Come sono fatti i fascicoli
> Testo dell'esercizio, il tuo svolgimento, e nelle ultime pagine **lo svolgimento
> corretto**. Sono scansioni senza strato di testo: si leggono come immagini, `pdftotext`
> restituisce zero caratteri.

---

## 🔴 Gli argomenti che il docente sa già che non sai fare

Questa tabella è il cuore della pagina. **Ogni riga è un esercizio che a settembre può
tornare**, perché è un esercizio su cui il docente ha già visto che cadi.

| Verifica | Esercizio | Annotazione del prof. | Argomento | Il gemello su cui allenarsi |
|---|---|---|---|---|
| 02-03 | **Es. 5** | ⛔ «**NON SVOLTO PER NULLA**» | frequenze di taglio | Mirandola PDF 97-98 → libro 189-191, es. **18** (tipo di filtro e f_t di quattro reti) e **19** (progetto passa-alto a 300 Hz) |
| 02-03 | **Es. 4** | ❌ «**errato**» | funzione di trasferimento | Mirandola PDF 97 → libro 189, es. **9-10** (f.d.t. di quadripoli RL e RC) e PDF 97 es. **11** |
| 24-04 | **Es. 4** | ⛔ «**NON SVOLTO PER NULLA**» | interfaccia TTL-relè | Mirandola PDF 195 → libro 385, es. **8** — è lo stesso esercizio con altri numeri |
| 24-04 | **Es. 5** | ⛔ «**NON SVOLTO PER NULLA**» | capacità di by-pass C_E | Mirandola PDF 195 → libro 385, es. **9**; teoria a PDF 188-190 → libro 371-375 |
| 24-04 | **Es. 6** | ❌ «**errato**» | BJT in saturazione | Mirandola PDF 164-168 → libro 322-331 (BJT in commutazione) + Edutecnica Elettronica pp. 56-61 |
| 29-05 | **Es. 3, 4, 5** | ⛔ «**NON SVOLTO**» | JFET: progetto della polarizzazione | Edutecnica Elettronica pp. 30-34 (es. 1-8) e pp. 17-20 (amplificatore) |
| 29-05 | **Es. 1** | ❌ calcolo di **R_G errato** | JFET: resistenza di gate | Mirandola PDF 195 → libro 385, es. **15** — ha **gli stessi identici dati** (I_D0 = 8 mA, V_GS0 = −1 V, V_DS0 = 7 V): confronta i due svolgimenti riga per riga |
| 29-05 | MOSFET | ❌ «**errata relazione che fornisce V_GS**» | MOSFET: le due strade per V_GS | Edutecnica Elettronica pp. 1-4 (es. 1-7) e pp. 13-14 (esempi svolti) |

> [!danger] I tre punti che valgono più di tutti gli altri
> 1. **Frequenze di taglio** — non consegnato per nulla. È metà del giorno 3 del calendario.
>    E attenzione all'errore che il vault registra come il più frequente in assoluto: per un
>    **RL**, f_t = R/(2πL), **non** L/R. Vedi [[Filtri passivi del primo ordine]] §4.
> 2. **JFET, il progetto della polarizzazione** — tre esercizi su cinque non consegnati. È
>    l'argomento più scoperto che hai, ed è per questo che ha una giornata intera tutta sua.
>    Tutto si regge su due sole relazioni (appunti Poggi p. 19):
>    `V_GS0 = −R_S·I_D0` e `V_DD = I_D0·(R_S + R_D) + V_DS0`.
> 3. **Le due strade per V_GS nel MOSFET**, che vanno tenute distinte:
>    - dal **partitore di gate**: `V_GS0 = V_DD · R₂/(R₁+R₂)`
>    - dalla **caratteristica**: `I_D = K(V_GS − V_T)²` → `V_GS = V_T + √(I_D/K)`
>
>    E la parabolica vale **solo in saturazione**: verifica sempre `V_DS > V_GS − V_T`.
>    Vedi [[MOSFET]] §3.

---

## Come si usano nel calendario

Non sono un ripasso finale: sono il **termometro**. Ogni checkpoint ne rifà una porzione
**da zero, cronometrata, senza guardare la correzione**, e solo dopo si confronta.

| Giorno | Cosa si rifà | Timer | Cosa decide |
|---|---|---|---|
| **1** · gio 20 | 02-03, es. **1 e 6** | 30 min | se l'alternata regge, si aprono i filtri il giorno dopo. Se no, si ruba la prima ora del 21 |
| **4** · dom 23 | 02-03, es. **2-5**, poi **tutta** di seguito | 60 min + integrale | chiude alternata e filtri: due dei cinque argomenti dello scritto, e tutti e tre quelli dell'orale |
| **7** · mer 26 | 24-04, **tutti e 7** | 90 min | chiude il BJT, che nella LETTERA vale sia per Carli sia per Protti |
| **9** · ven 28 | 29-05, es. **1-5** | 60 min | chiude il JFET |
| **10** · sab 29 | 29-05, es. **6-8** | 45 min | chiude il MOSFET, e con lui tutti e cinque gli argomenti dello scritto |
| **11** · dom 30 | **tutte e tre in fila** | unico, ~2h30 | non è per imparare: è per provare la resistenza sulle cinque ore |

> [!tip] La regola di correzione
> Dopo ogni checkpoint si rifanno **solo gli esercizi sbagliati**, non tutta la verifica.
> E alla prova generale del 30 si ripassa **solo ciò che si è sbagliato più di una volta**:
> un errore isolato è disattenzione, un errore ripetuto è un buco.

---

## Cosa insegnano sul formato

- **Sono esercizi numerici**, non domande aperte. Le domande aperte sono l'altro formato di
  Carli, quello delle verifiche sui diodi — vedi [[04 - Verifica tipo Carli — Diodi]]. La
  LETTERA li tiene separati allo stesso modo: **esercizi** alla scritta, **domande** all'orale.
- **Gli esercizi non consegnati pesano più di quelli sbagliati.** Su tre verifiche ci sono
  sei «NON SVOLTO» contro tre «errato». Alla prova del 1° settembre, su ogni esercizio che
  non chiudi, **scrivi comunque la formula di partenza e il procedimento**.
- **Il progetto è il tipo di esercizio ricorrente**: dati i valori voluti, dimensiona le
  resistenze. Vale per il BJT (partitore e R_E), per il JFET (R_S, R_D, R_G) e per il
  MOSFET (partitore di gate). È lo stesso schema tre volte, con tre relazioni diverse.

---

## Link

- Il piano giorno per giorno: [[Calendario]]
- Le altre due prove del 1° settembre: [[02 - Prova Orale Carli]] · [[03 - Prova Pratica Protti]]
- Le domande aperte sui diodi: [[04 - Verifica tipo Carli — Diodi]]
- Da dove viene questa fonte e quanto vale: [[00 - Fonti e note]] §2
- Note di teoria: [[Filtri passivi del primo ordine]] · [[BJT]] · [[Amplificatori a BJT]] · [[JFET]] · [[MOSFET]]
