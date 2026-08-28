---
tags: [recupero, elettronica, esercizi, simulazione, esame]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) per derivazione — file trasversale: gli esercizi sono composti sui metodi dei file di argomento, ciascuno verificato sul Mirandola nei Lotti 1-13 della bonifica. I testi degli esercizi sono originali della simulazione, non tratti dal libro. Vedi «00 - Fonti e note» e «00 - Audit e correzioni»."
prove: [scritta, orale, pratica]
---

# Esercizi — Batteria da 75 minuti (allenamento alla velocità)

> [!info] Come usare questo file
> Cinque esercizi, uno per macroarea, sotto timer da 75 minuti. **Non è la simulazione della
> prova reale**: quella dura **cinque ore** (1 settembre, 8:00-13:00) e si prova il 30 agosto
> mettendo in fila le tre verifiche del prof. — vedi [[05 - Verifiche FUSI (Carli)]] e
> [[Calendario]]. Questo file allena una cosa diversa e comunque necessaria: la **velocità**
> su un esercizio tipo per argomento. Per ogni esercizio è indicato il tempo consigliato. Comincia dagli esercizi che conosci meglio (per prendere confidenza), poi passa a quelli più complessi. Usa una calcolatrice scientifica + formulario personale di numeri complessi/fasori. Tieni d'occhio l'orologio: se a metà tempo non hai fatto almeno 3 esercizi, lascia perdere la precisione sull'ultimo e metti la formula anche senza il calcolo finale.

---

## Setup della simulazione

**Tempo totale**: 75 minuti (= 1,25 ore). *La prova reale ne dura 300.*
**Esercizi**: 5.
**Materiali ammessi**: penna, calcolatrice, formulario (NO libro, NO appunti di teoria).

> [!warning] Setup realistico
> Prima di partire, metti un timer a 75 minuti. Togli cellulare, internet, chat. Quando hai finito, correggi e segna per ognuno: (a) **risolto correttamente**; (b) **risolto con errori**; (c) **non risolto**. Poi fai la sessione di "recupero" su quelli errati o non risolti.

---

## E1 — Impedenze e regime sinusoidale (15 min, medio)

**Testo.** Data la rete in figura (serie di $R = 100\,\Omega$, $L = 10$ mH, $C = 1\,\mu\text{F}$), calcolare:
- (a) Impedenza equivalente $\bar{Z}_{\text{eq}}$, in forma binomiale.
- (b) Pulsazione di risonanza $\omega_0$ della rete.
- (c) Se la rete fosse alimentata con $V = 220$ V a 50 Hz, la corrente $I_{\text{eff}}$ che scorre.

**Dati figura** (vedi Allegati): tre bipoli in serie.

**Svolgimento (bozza)**:

- $Z_L = j\omega L$, $Z_C = -j/(\omega C)$
- $\bar{Z} = R + j(\omega L - 1/(\omega C))$
- $\omega_0 = 1/\sqrt{LC} = 1/\sqrt{10\text{mH} \cdot 1\mu\text{F}} = 10^4$ rad/s ≈ 1,59 kHz
- A $\omega = 2\pi \cdot 50 = 314$ rad/s: $X_L \approx 3{,}14$ Ω, $X_C \approx 3183$ Ω → rete quasi capacitiva

> [!tip] Trappola
> A 50 Hz la rete è dominata da $C$. A 1,59 kHz è in risonanza. La "sorpresa" è che $f = 50$ Hz è lontanissima dalla risonanza → $Z_{\text{eq}}$ è quasi $-j 3183\,\Omega$ (capacitivo puro).

---

## E2 — Filtro passa-basso RL (15 min, facile)

**Testo.** In un filtro passa-basso RL con $R = 1\,\text{k}\Omega$ e $L = 10$ mH, calcolare:
- (a) Frequenza di taglio $f_t$.
- (b) Funzione di trasferimento $G(s)$ in forma esplicita.
- (c) Se in ingresso c'è un'onda quadra di $V_p = 5$ V e $f = 1$ kHz, qualitativamente cosa esce?

**Svolgimento**:

- $f_t = R/(2\pi L) = 1000/(2\pi \cdot 0{,}01) = 15915$ Hz ≈ 15,9 kHz
- $G(s) = 1/(1 + sL/R) = 1/(1 + s \cdot 10\mu\text{s})$ — polo a $\omega_p = R/L = 10^5$ rad/s
- A 1 kHz: $|G| \approx 1$ in modulo (lontano da $f_t$) → esce ancora "quasi" l'onda quadra ma con bordi arrotondati (i transienti rapidi vengono filtrati)

---

## E3 — Stabilizzatore Zener (15 min, facile)

**Testo.** Uno stabilizzatore Zener è formato da $R_S = 200\,\Omega$ in serie a uno Zener da $V_Z = 5{,}1$ V ($I_{Z,\min} = 5$ mA, $I_{Z,\max} = 60$ mA), con $V_{in} = 12$ V (variabile $\pm 10\%$).
- (a) Calcolare la tensione di uscita $V_{out}$ (entro i limiti).
- (b) Calcolare il range di $I_L$ che mantiene la regolazione.
- (c) Calcolare la potenza dissipata da $R_S$ nel caso peggiore.

**Svolgimento**:

- (a) $V_{out} = V_Z = 5{,}1$ V (assumendo Zener in breakdown).
- (b) Caso peggiore: $V_{in,\min} = 10{,}8$ V, $I_L$ massima.
  $I_{S} = (10{,}8 - 5{,}1)/200 = 28{,}5$ mA. $I_{L,\max} = I_S - I_{Z,\min} = 23{,}5$ mA.
- (c) Caso peggiore: $V_{in,\max} = 13{,}2$ V, $I_L = 0$: $I_S = 8{,}1/200 = 40{,}5$ mA; $P_{R_S} = 40{,}5^2 \cdot 200 \cdot 10^{-6} = 0{,}328$ W.

> [!tip] Errore classico
> Dimenticare che $R_S$ dissipa. La potenza di $R_S$ è $(V_{in} - V_Z)^2 / R_S$. Per $V_{in,\max}$ e $I_L = 0$ spesso è la condizione peggiore per $R_S$.

---

## E4 — Polarizzazione BJT con partitore (15 min, medio)

**Testo.** Un BJT NPN è polarizzato con partitore $R_1 = 100\,\text{k}\Omega$, $R_2 = 50\,\text{k}\Omega$ (entrambi tra $V_{CC}$ e GND, con la base prelevata sul centrale), $R_C = 2\,\text{k}\Omega$, $R_E = 1\,\text{k}\Omega$, $V_{CC} = 20$ V, $\beta = 100$, $V_{BE} = 0{,}7$ V. Calcolare $I_C$ e $V_{CE}$.

**Svolgimento**:

- $V_B = V_{CC} \cdot R_2/(R_1+R_2) = 20 \cdot 50/150 = 6{,}67$ V.
- $V_E = V_B - V_{BE} = 5{,}97$ V.
- $I_E = V_E/R_E = 5{,}97/1 = 5{,}97$ mA.
- $I_C = \alpha \cdot I_E = \beta/(\beta+1) \cdot I_E = 100/101 \cdot 5{,}97 \approx 5{,}91$ mA.
- $V_{CE} = V_{CC} - I_C R_C - I_E R_E = 20 - 5{,}91\cdot 2 - 5{,}97\cdot 1 = 20 - 11{,}82 - 5{,}97 = 2{,}21$ V.

> [!warning] Verifica zona attiva
> $V_{CE} = 2{,}21$ V $> V_{CE,\text{sat}} = 0{,}2$ V ✅ il BJT è in zona attiva. Verificare SEMPRE. Se fosse $< 0{,}2$ V, il transistor è saturo e i calcoli non valgono.

> [!danger] Qui l'approssimazione «partitore scarico» **non regge**: il risultato vero è $V_{CE} = 6{,}6$ V
> Il metodo rapido usato sopra vale solo se la corrente nel partitore è $\gg I_B$. Verifichiamolo:
> $$I_{\text{partitore}} = \frac{20}{150\text{ k}} = 133\ \mu\text{A} \qquad\text{contro}\qquad I_B \approx \frac{I_C}{\beta} \approx 59\ \mu\text{A}$$
> Sono **confrontabili** (rapporto 2,3, non 10): la base "ruba" corrente al partitore e $V_B$ crolla sotto
> i 6,67 V nominali. Col metodo esatto (Thévenin, $V_{TH} = 6{,}67$ V, $R_{TH} = R_1\parallel R_2 = 33{,}3$ k$\Omega$):
> $$I_B = \frac{V_{TH}-V_{BE}}{R_{TH}+(\beta+1)R_E} = \frac{5{,}97}{33{,}3\text{k}+101\text{k}} = 44{,}4\ \mu\text{A}$$
> $$I_C = \beta I_B = 4{,}44\text{ mA} \qquad I_E = 4{,}49\text{ mA} \qquad V_{CE} = 20 - 8{,}88 - 4{,}49 = \mathbf{6{,}63\text{ V}}$$
> Differenza di **4,4 V** su $V_{CE}$: non un arrotondamento. Entrambi i metodi dicono "zona attiva", ma
> se l'esercizio chiede il punto di lavoro, il numero giusto è 6,63 V. **Prima di usare la scorciatoia,
> confronta sempre $I_{\text{partitore}}$ con $I_B$**: stessa trappola dell'Es. B4 di [[Esercizi - BJT]].

---

## E5 — MOSFET enhancement n (15 min, difficile)

**Testo.** Un MOSFET NMOS enhancement ($K = 0{,}5\text{ mA/V}^2$, $V_T = 2$ V) è polarizzato con partitore di gate $R_1 = 1\,\text{M}\Omega$, $R_2 = 2\,\text{M}\Omega$ (tra $V_{DD}$ e GND), $R_S = 300\,\Omega$, $R_D = 2\,\text{k}\Omega$, **$V_{DD} = 24$ V**.
- (a) Calcolare $V_{GS}$ e $I_D$ in regime.
- (b) Verificare se il MOSFET è in saturazione.
- (c) Calcolare $V_{DS}$.

**Svolgimento**:

- $V_G = V_{DD} \cdot R_2/(R_1+R_2) = 24 \cdot 2/3 = 16$ V.
- Equazione parabolica: $I_D = K(V_{GS} - V_T)^2 = 0{,}5(V_G - I_D R_S - V_T)^2 = 0{,}5(16 - 0{,}3 I_D - 2)^2 = 0{,}5(14 - 0{,}3 I_D)^2$ (mA).
- Espando: $(14 - 0{,}3 I_D)^2 = 196 - 8{,}4 I_D + 0{,}09 I_D^2$. Quindi $I_D = 98 - 4{,}2 I_D + 0{,}045 I_D^2$.
- Equazione di 2° grado: $0{,}045 I_D^2 - 5{,}2 I_D + 98 = 0$.
- $\Delta = 27{,}04 - 17{,}64 = 9{,}40$. $I_D = (5{,}2 \pm 3{,}07)/0{,}09$.
- $I_{D1} = 91{,}9$ mA e $I_{D2} = 23{,}7$ mA. **La prima si scarta**, e vale la pena vedere *perché*: con $I_D = 91{,}9$ mA sarebbe $V_{GS} = 16 - 91{,}9 \cdot 0{,}3 = -11{,}6$ V, cioè $V_{GS} < V_T$ — il MOSFET sarebbe **interdetto** e non condurrebbe affatto, in contraddizione con l'$I_D$ da cui siamo partiti. È la radice spuria che l'elevamento al quadrato introduce sempre: la parabola $K(V_{GS}-V_T)^2$ vale **solo** per $V_{GS} > V_T$, ma l'equazione di 2° grado non lo sa. **Controlla sempre il segno di $V_{GS}$ sulle due radici**: è il modo più rapido per scegliere quella giusta.
- $V_{GS} = 16 - 23{,}7 \cdot 0{,}3 = 16 - 7{,}1 = 8{,}9$ V.
- $V_{DS} = 24 - 23{,}7 \cdot (2 + 0{,}3) = 24 - 54{,}5 = -30{,}5$ V... **errore di dimensionamento!**

> [!danger] $V_{DS}$ negativo = rete mal dimensionata
> Con questi parametri la rete **non è sostenibile**: serve ridurre $K$ del MOSFET (è un parametro, scelta del componente), o aumentare molto $V_{DD}$, o usare un partitore di gate diverso. La formula parabolica è corretta, ma i parametri sono fisicamente inconsistenti.

**Procedura corretta** (parametri fisicamente sensati, con $V_{DD} = 15$ V e $R_D = 1\,\text{k}\Omega$):

- $V_G = 15 \cdot 2/3 = 10$ V. $I_D = 0{,}5(10 - 0{,}3 I_D - 2)^2 = 0{,}5(8 - 0{,}3 I_D)^2$.
- Espando: $I_D = 0{,}5(64 - 4{,}8 I_D + 0{,}09 I_D^2) = 32 - 2{,}4 I_D + 0{,}045 I_D^2$.
- Equazione 2° grado: $0{,}045 I_D^2 - 3{,}4 I_D + 32 = 0$. $\Delta = 11{,}56 - 5{,}76 = 5{,}80$.
- $I_D = (3{,}4 \pm 2{,}41)/0{,}09 = 64{,}6$ mA (scartata) o $11{,}0$ mA ✅.
- $V_{GS} = 10 - 11 \cdot 0{,}3 = 6{,}7$ V. $V_{DS} = 15 - 11 \cdot 1{,}3 = 0{,}7$ V.
- Saturazione: serve $V_{DS} > V_{GS} - V_T = 4{,}7$ V. $V_{DS} = 0{,}7 < 4{,}7$ → **triodo, NON saturazione!**

**Si conclude risolvendo in zona di triodo** (perché l'$I_D = 11$ mA trovato sopra vale solo in
saturazione, e quindi **non è la risposta**). In triodo:
$$I_D = K\left[2(V_{GS}-V_T)V_{DS} - V_{DS}^2\right] \quad\text{con}\quad V_{GS} = 10 - 0{,}3 I_D,\;\; V_{DS} = 15 - 1{,}3 I_D$$
Risolvendo il sistema si ottiene
$$\boxed{I_D = 9{,}6\text{ mA} \qquad V_{GS} = 7{,}1\text{ V} \qquad V_{DS} = 2{,}5\text{ V}}$$
coerente con l'ipotesi: $V_{DS} = 2{,}5 < V_{GS}-V_T = 5{,}1$ ✅. Nota che $I_D$ è **minore** degli 11 mA della
parabolica: in triodo la corrente è sempre più bassa del valore di saturazione.

> [!tip] Lezione didattica
> Anche con $V_{DD}$ ragionevole, una rete di polarizzazione può portare il MOSFET fuori dalla
> saturazione. **Verifica SEMPRE** $V_{DS} > V_{GS} - V_T$ dopo aver trovato il punto di lavoro; se non è
> soddisfatta, il risultato della parabolica va buttato e si rifà in triodo.
> Per **riportarlo in saturazione**: aumenta $V_{DD}$, oppure **riduci $R_D$** (non aumentarla: nella
> maglia $V_{DS} = V_{DD}-I_D(R_D+R_S)$ è proprio $R_D$ a mangiarsi la $V_{DS}$), oppure riduci $I_D$
> alzando $R_S$.

---

## Griglia di correzione (uso dopo la simulazione)

| Esercizio | Tempo | Difficoltà | Errori tipici |
|---|---|---|---|
| E1 | 15' | medio | confondere $L$ con $C$ nella serie; sbagliare $\omega_0$ |
| E2 | 15' | facile | dimenticare che in RL è $R/L$ (non $RC$); errata corrige libro |
| E3 | 15' | facile | dimenticare il range $V_{in,\min}$/$V_{in,\max}$ |
| E4 | 15' | medio | non verificare la zona attiva ($\beta \to \alpha$ o errore $V_{CE}$) |
| E5 | 15' | difficile | non accorgersi che $V_{DS}$ è negativo = rete mal dimensionata |

> [!success] Dopo la simulazione
> 1. Per ogni esercizio risolto con errori, identifica il punto di errore preciso (aritmetica? concetto? unità di misura?).
> 2. Per ogni esercizio non risolto, leggi la soluzione e scomponila in 3-4 sotto-passi; ripeti l'esercizio il giorno dopo senza guardare.
> 3. Quando arrivi a 4/5 esercizi risolti correttamente in 60 minuti, hai la velocità che serve.
>    Manca ancora la **resistenza**: quella si prova il 30 agosto sulle tre verifiche in fila.

---

## Da qui in poi

- Teoria completa per ogni argomento: [[Impedenza dei bipoli R, L, C]], [[Filtri passivi del primo ordine]], [[Le potenze in alternata]], [[Diodi]], [[BJT]], [[MOSFET]]
- Esercizi per argomento: directory [[Esercizi]]
- Prove: [[01 - Prova Scritta Carli]]
