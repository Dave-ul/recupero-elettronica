---
tags: [recupero, elettronica, audit, trasparenza, carli, poggi]
fonte: "confronto delle 14 note in Argomenti/ con gli appunti Poggi (20 pp. + la pagina del 18/3) e le tre verifiche FUSI del prof. Carli"
aggiunto: 2026-08-19
metodo: "lettura diretta delle pagine come immagini — nessuno dei due PDF ha strato di testo"
---

# 06 — Audit delle note di teoria contro le fonti del docente

> [!info] Che cosa è stato fatto
> Le note in `Argomenti/` erano state scritte tra il 19 e il 28 luglio 2026 **prima** che
> gli appunti Poggi e le tre verifiche del prof. Carli entrassero in `Fonti/`. Il 19 agosto
> sono state confrontate con quelle due fonti, pagina per pagina: 19 pagine di appunti e 56
> pagine di verifiche, tutte lette come immagini.
>
> **Esito in una riga: nessuna nota dice cose sbagliate.** Dove i due mondi si toccano, le
> note coincidono con gli appunti del corso. I buchi trovati sono di **copertura** — tipi di
> esercizio che Carli assegna e che nessuna nota affrontava — e sono stati chiusi
> aggiungendo alle note interessate un riquadro «Come lo chiede Carli».

---

## 1. Le corrispondenze verificate (nessuna correzione necessaria)

| Cosa dice la fonte del docente | Dove sta | Cosa dice il vault | Esito |
|---|---|---|---|
| $X_L=\omega L$, $X_C=-\dfrac{1}{\omega C}$, $\bar{Z}=R+jX$, $\lvert\bar{Z}\rvert=\sqrt{R^2+X^2}$ | Poggi p. 4 | [[Impedenza dei bipoli R, L, C]] §2 — reattanza capacitiva **negativa**, formula (2.17) | ✅ identico |
| $\varphi=\arctan\frac{b}{a}$, $+\pi$ nel 2°/3° quadrante, $+2\pi$ nel 4° | Poggi p. 7 | [[Segnali sinusoidali e fasori]] §4, formula (2.3) e il callout sulla calcolatrice | ✅ identico |
| $\bar{V}=\bar{Z}\bar{I}$, «prima legge di Ohm in forma simbolica» | Poggi p. 10 | [[Il metodo simbolico]] §3 | ✅ identico |
| $f_t=\dfrac{\omega_p}{2\pi}$, e nei filtri del 1° ordine la pulsazione di taglio **coincide col polo**; $f_t=\dfrac{1}{2\pi RC}$ | Poggi p. 18 | [[Filtri passivi del primo ordine]] §5 (e $f_t = \frac{R}{2\pi L}$ per l'RL, con la verifica dimensionale) | ✅ identico |
| $G(s)=\dfrac{N(s)}{D(s)}$; poli = valori che annullano $D(s)$ | Poggi p. 18 | [[Filtri passivi del primo ordine]] §5 | ✅ identico |
| Filtri del 1° ordine: passa-basso RC e LR, passa-alto CR e RL; si risolvono col **partitore** dopo aver trasformato in $s$ | Poggi p. 9 | [[Filtri passivi del primo ordine]] §2-3 | ✅ identico |
| Zone del BJT via polarizzazione delle due giunzioni ($V_{BE}>0,V_{CB}<0$ attiva; entrambe dirette = saturazione; entrambe inverse = interdizione) | Poggi p. 11 | [[BJT]] §2 | ✅ identico |
| $h_{FE}=I_C/I_B$, adimensionale, $50<h_{FE}<500$; **$I_C=h_{FE}I_B$ non vale in saturazione**; $V_{BE}=0{,}7$ V, $V_{CEsat}\approx0{,}2$ V | Poggi p. 13 | [[BJT]] §2 e §5 | ✅ identico |
| Progetto a partitore: $V_{RE}=V_{CC}/10$, $I_{partitore}=10\,I_B$ | Carli, sol. es. 3 del 24-04 · Mirandola 7.8-7.11 | [[BJT]] §4b, tabella dei quattro criteri | ✅ identico — **e questa è la ricetta che Carli usa** |
| $C_E$ di by-pass: $X_{CE}\ll R_E$, rapporto almeno 10 | Mirandola ESEMPIO 7 | [[Amplificatori a BJT]] §2 | ✅ già copre l'es. 5 mai svolto da Fusi |
| Struttura **n⁺⁺ — p — n**; droganti **As** (zona n) e **B** (zona p); «BASE molto stretta»; «zona di svuotamento tra base e collettore decisamente grande» | Poggi, **foto del 18/3** | [[BJT]] §1-bis | ✅ recepito il 2026-08-28 — il vault diceva «zone esterne fortemente drogate» (Mirandola) e drogante n = **fosforo** |
| *Transfer resistor* = «resistore variabile a seconda della corrente ricevuta»; schema a blocchi corrente di comando → corrente d'uscita | Poggi, **foto del 18/3** | [[BJT]] §1-bis · [[00 - Perchè (spiegazione intuitiva)]] §8 | ✅ identico |
| Giunzione **B-E diretta** ($V_{BE}=0{,}7$ V $=V_S$), **B-C inversa**; tre schemi di polarizzazione ($V_{BE}$+$V_{CB}$ · $V_{BE}$+$V_{CE}$ · $V_{CC}$ con $R_B$ e $R_C$) | Poggi, **foto del 18/3** | [[BJT]] §2 e §4a | ✅ identico |
| Il condensatore: fra le armature c'è campo elettrico e **le cariche libere non possono restare** | Poggi, **foto del 18/3** | [[BJT]] §1-ter | ✅ recepito il 2026-08-28 — è il modello della zona di svuotamento |
| JFET: $V_{GS0}=-R_S I_{D0}$ e $V_{DD}=I_{D0}(R_S+R_D)+V_{DS0}$ | Poggi p. 19 | [[JFET]] §4 (autopolarizzazione) | ✅ identico |
| Quadripolo: $\bar{V}_i=\bar{Z}_{11}\bar{I}_i+\bar{Z}_{12}\bar{I}_o$, matrice $\bar{Z}$ | Poggi p. 16 | [[Amplificatori a BJT]] §5 (parametri ibridi $h$) | ⚠️ vedi §2, punto 6 |

---

## 2. I buchi di copertura trovati, e come sono stati chiusi

> [!danger] Il criterio
> Un buco conta se **Carli lo ha messo in una verifica** e nessuna nota lo affrontava. Sei
> casi su ventuno esercizi. Tutti chiusi con un riquadro nella nota competente; nessuna
> riscrittura.

1. **$R_G$ del JFET non si calcola, si sceglie.** Le note dicevano che $I_G\approx 0$ e che
   $R_G$ è «di solito 1 M$\Omega$ o più», ma nel contesto dell'amplificatore, non del
   progetto. Fusi ha provato a ricavarla da una legge di Ohm e ha perso il punto; il prof.
   scrive «$R_G$ si fissa ad esempio a 5 M$\Omega$». → aggiunto in [[JFET]].
2. **Il progetto del JFET in tre righe** ($R_S$, $R_D$ dai dati di lavoro, $R_G$ scelta) e
   la **Shockley invertita** $V_{GS}=V_P\left(1-\sqrt{I_D/I_{DSS}}\right)$, che serve quando
   $V_{GS0}$ non è dato. Le note avevano solo la strada di **analisi** (equazione di 2°
   grado). Sono cinque esercizi su otto della verifica 29-05. → aggiunto in [[JFET]].
3. **Il progetto del MOSFET.** Le note avevano solo l'analisi (dato il partitore, trova $Q$).
   Carli chiede due volte l'inverso: dato $I_D$, ricava $V_{GS}=\sqrt{I_D/K}+V_t$, **scegli**
   $V_{DS}$ rispettando $V_{DS}\ge V_{GS}-V_t$, e dimensiona. → aggiunto in [[MOSFET]].
4. **La verifica della saturazione del BJT.** La nota spiegava *che cosa* è la saturazione,
   non *come si dimostra*. Carli scrive la procedura: Kirchhoff all'ingresso per $I_B$,
   Kirchhoff all'uscita per $I_C$, poi il test $I_B>I_C/h_{FE}$. → aggiunto in [[BJT]].
5. **L'interfaccia porta TTL – bobina di relè.** Nessuna nota la tratta, in nessuna forma.
   È l'es. 4 del 24-04, non svolto. → aggiunto in [[BJT]] come procedura completa.
6. **Il segno di $V_P$ nei testi di Carli.** Le note insistono (giustamente) che nel JFET a
   canale n $V_P<0$. Carli però nell'es. 2 del 29-05 scrive «$V_P=5$ V» e nell'es. 4
   «$V_P=-4{,}5$ V»: usa entrambe le convenzioni nella stessa prova. → nota di lettura
   aggiunta in [[JFET]]: guardare il **circuito**, non il segno stampato.

---

## 3. Le note che non erano verificabili con queste due fonti

Non è un difetto delle note: è che le fonti del docente non le toccano. Restano appoggiate
al Mirandola e a Edutecnica, come dichiarato in [[00 - Fonti e note]].

| Nota | Perché non verificabile |
|---|---|
| [[Diodi]] | Gli appunti Poggi elencano il diodo nel programma ma non lo sviluppano; nessuna delle tre verifiche FUSI lo tocca. Il riscontro è l'altra verifica di Carli, quella a domande aperte: [[04 - Verifica tipo Carli — Diodi]] |
| [[Alimentatori]] | Fuori dagli appunti e fuori dalle verifiche. Resta lettura descrittiva per l'orale, come deciso il 19 agosto |
| [[L'oscilloscopio]] | Fuori da entrambe: è materia della pratica Protti, non di Carli |
| [[Le potenze in alternata]] · [[Reti RLC e risonanza]] | Poggi non arriva alle potenze; nessun esercizio FUSI le chiede. Restano lettura descrittiva per l'orale |
| [[00 - Perchè (spiegazione intuitiva)]] | È il livello intuitivo, non ha corrispondenti nelle fonti. Nessuna contraddizione trovata con esse |

---

## 4. Quello che le fonti dicono e il vault non diceva affatto

Tre fatti che non stavano in nessuna nota e che valgono per il 1° settembre:

- **Carli pretende di vedere i passaggi.** Due annotazioni in rosso su tre verifiche sono
  «non si spiega questo passaggio dalla relazione precedente» e «perché non ha continuato lo
  svolgimento?» — scritte anche accanto a risultati numericamente giusti.
- **Le maglie non si mescolano.** L'errore che Carli segna più volte è scrivere una sola
  equazione con dentro un elemento della maglia d'ingresso e uno di quella d'uscita.
- **La griglia dà punti parziali.** «Relazioni usate corrette ma errati tutti i calcoli» vale
  0,75 su 1,50. Impostare bene un esercizio che non si chiude vale metà del punteggio: è la
  ragione pratica per non lasciare mai un foglio bianco.

Il programma degli appunti Poggi, per inciso, arriva fino agli **amplificatori operazionali**
(ideali, reali, applicazioni) marcandoli però come materia del **5° anno**: sono fuori dal
recupero, coerentemente con la LETTERA.

---

## Link

- Le tre verifiche, esercizio per esercizio: [[05 - Verifiche FUSI (Carli)]]
- Il registro storico delle correzioni al vault: [[00 - Audit e correzioni]]
- Da dove viene ogni fonte: [[00 - Fonti e note]]
- Il piano: [[Calendario]]
