---
tags: [recupero, elettronica, prova-pratica, protti, laboratorio]
fonte: "MAJORANA — Lettera di giudizio sospeso (Secondo Periodo), 09/06/2026"
docente: Prof. Giampaolo Protti
tipologia: Orale + Pratica (laboratorio)
---

# 03 — Prova Pratica (Prof. Protti)

> [!info] Dove serve
> È la **prova pratica** di laboratorio del docente Giampaolo Protti. Si svolge in laboratorio: ti vengono chiesti **esercizi di misura** sull'oscilloscopio, sul collaudo di circuiti, e domande sul funzionamento di circuiti reali. È la prova dove "capisci se hai capito davvero".

---

## Cosa chiede la lettera

Dalla lettera di giudizio sospeso:

> Domande, esercizi, **misure con l'oscilloscopio** sul programma svolto: **diodi**, **segnali sinusoidali**, **reti RLC**, **filtri**, **amplificatori a BJT**.

In pratica questo significa:

- **Misurare** all'oscilloscopio tensioni (picco, efficace, media), frequenze, sfasamenti
- **Distinguere** il segnale DC dal componente AC (coupling AC/DC)
- **Riconoscere** sullo schermo un passa-basso, un passa-alto, una risonanza
- **Rispondere a domande** sul funzionamento dei componenti visti durante l'anno
- **Collaudare** un circuito reale (alimentatore, amplificatore) e riconoscere quando è rotto

---

## Le cinque "famiglie" di prove pratiche

### 1️⃣ Segnali sinusoidali — "Misura e caratterizza"

- **Cosa ti danno**: un generatore di funzioni impostato su una sinusoide di una certa ampiezza e frequenza, o un circuito con un'onda da misurare.
- **Cosa ti chiedono**:
  - "Misura il valore di picco, il valore efficace, la frequenza di $v_1$"
  - "Quanto vale lo sfasamento tra $v_1$ e $v_2$?"
  - "È un segnale sinusoidale puro o distorto?"

- **Come farlo**:
  1. Imposta l'oscilloscopio in **DC coupling** (per vedere anche l'eventuale offset DC).
  2. Scala la base tempi in modo da vedere 2–3 periodi.
  3. Misura l'ampiezza picco-picco dal cursore verticale; $V_p = V_{pp}/2$; $V_{eff} = V_p/\sqrt{2}$.
  4. Misura il periodo $T$ (distanza tra due fronti dello stesso tipo); $f = 1/T$.
  5. Per lo sfasamento: misura il ritardo $\Delta t$ tra i due passa-per-lo-zero; $\varphi = 2\pi \Delta t / T$.

> [!check] Concetto chiave: AC vs DC coupling
> - **DC coupling**: mostri la forma d'onda **compresa la componente continua** (offset).
> - **AC coupling**: blocchi la componente continua con un C interno; mostri solo la parte che oscilla attorno allo zero.
> - Se colleghi un'uscita con offset (es. un alimentatore a 12 V), in DC vedi la retta a 12 V, in AC vedi l'oscillazione residua (ripple).
> - Errore classico: misurare in AC e non accorgerti che manca l'offset → $V_{eff}$ calcolato male.

> Vedi: [[L'oscilloscopio]] §3.

### 2️⃣ Reti RLC e filtri — "Caratterizza la risposta in frequenza"

- **Cosa ti danno**: un filtro RC, RL o RLC già montato su breadboard; un generatore di funzioni; un oscilloscopio.
- **Cosa ti chiedono**:
  - "Misura la frequenza di taglio di questo passa-basso"
  - "Verifica che è un filtro del primo ordine"
  - "A $f$ doppia rispetto a $f_t$, quanto vale il guadagno in dB?"
  - "Dove si trova la frequenza di risonanza di questo RLC?"

- **Come farlo**:
  1. Imposta il generatore su una sinusoide di ampiezza fissa (es. 1 V$_{pp}$).
  2. Misura $V_{out}$ a una frequenza di riferimento (banda passante) — questo è il guadagno di riferimento $G_0$.
  3. Varia la frequenza fino a trovare dove $V_{out}$ scende a $G_0/\sqrt{2}$ (la **frequenza di taglio**).
  4. Per i RLC parallelo: cerca il picco di $|V_{out}|$ al variare di $f$ — quello è $\omega_0$.
  5. Misura la larghezza di banda $\Delta f$ a $-3$ dB per ricavare $Q = f_0/\Delta f$.

> [!tip] Verifica pratica dei -20 dB/decade
> Lontano dalla frequenza di taglio, ogni decade di frequenza deve dare un'attenuazione di $\times 10$ in ampiezza (cioè -20 dB in potenza, o -20 dB/decade in guadagno). Questo è un controllo gratuito per verificare se è davvero un filtro del primo ordine.

### 3️⃣ Diodi — "Misure e collaudo"

- **Cosa ti danno**: un raddrizzatore a semionda o a ponte, magari con condensatore di livellamento; un multimetro; un oscilloscopio.
- **Cosa ti chiedono**:
  - "Misura la tensione ai capi del carico con e senza condensatore"
  - "Quanto vale il ripple?"
  - "A che corrente si rompe?"
  - "Perché il ponte ha 4 diodi e non solo 2?"

- **Come farlo**:
  1. Collega l'oscilloscopio in DC coupling all'uscita rettificata.
  2. Senza $C$ di livellamento: vedi una doppia semionda rettificata con $|V_{out}| = V_{in,p} - 2V_D$.
  3. Con $C$: la tensione sale a $V_{DC} \approx V_{in,p} - 2V_D$ e oscilla con ripple $\Delta V_{ripple} = I_{load}/(f_r C)$, dove $f_r = 2f_{line}$.

> Vedi: [[Diodi#Raddrizzatore]].

### 4️⃣ Amplificatori a BJT — "Misure sul piccolo segnale"

- **Cosa ti danno**: un amplificatore a BJT (CE o CC) montato; un generatore di piccolo segnale; un oscilloscopio.
- **Cosa ti chiedono**:
  - "Misura il guadagno di tensione $A_v = V_{out}/V_{in}$"
  - "A che frequenza il guadagno crolla di 3 dB?"
  - "Quanto vale la resistenza di ingresso?"

- **Come farlo**:
  1. Misura prima il **punto di lavoro DC**: $V_{CE}$ a riposo (segnale generatore a 0). Deve essere circa metà di $V_{CC}$ in zona attiva.
  2. Applica un segnale sinusoidale piccolo (decine di mV) alla frequenza centrale della banda passante.
  3. Misura $A_v = V_{out,pp}/V_{in,pp}$.
  4. Aumenta la frequenza finché il guadagno non cala di $1/\sqrt{2}$: è la $f_H$ (frequenza di taglio superiore).

> [!warning] Attenzione al clipping
> Se il segnale di uscita è "tagliato" (clippato) sopra o sotto, **non stai più in zona attiva** — stai saturando o andando in cutoff. Abbassa l'ampiezza del segnale di ingresso finché la forma d'onda di uscita torna pulita.

> Vedi: [[Amplificatori a BJT]].

### 5️⃣ Oscilloscopio — "Sai usarlo davvero?"

- **Cosa ti chiedono**:
  - "Misura la tensione efficace di questa sinusoide"
  - "Cambia l'accoppiamento da DC a AC e dimmi cosa cambia"
  - "Trigger: come fai a stabilizzare un segnale rumoroso?"
  - "Qual è la differenza tra AUTO e NORMAL trigger mode?"

- **Come farlo**: vedi [[L'oscilloscopio]] § trigger, coupling, sonde, misure.

---

## Workflow di una prova pratica "tipo"

> [!check] Sequenza operativa consigliata
>
> 1. **Leggi prima la traccia**: capisci cosa vuole il docente prima di toccare lo strumento.
> 2. **Identifica i punti di misura**: prima di accendere l'oscilloscopio, decidi dove metterai le sonde.
> 3. **Stima il valore atteso**: prima di misurare, prova a indovinare l'ordine di grandezza. Se misuri 12 V dove ti aspettavi 1.2 V, hai sbagliato la sonda (×1 vs ×10).
> 4. **Misura**: imposta scala verticale, base tempi, trigger; leggi il valore.
> 5. **Confronta con il teorico**: la misura torna al calcolo fatto su carta? Se no, riconsidera.
> 6. **Commenta**: spiega cosa hai fatto e perché — è metà del voto alla prova orale-pratica.

---

## Trappole pratiche (errori che costano il punto)

> [!danger] I 6 errori più comuni nelle prove pratiche Protti
>
> 1. **Sonda in ×10 ma scala calcolata in ×1**: l'oscilloscopio ti mostra $V_{pp}/10$. Se non te ne accorgi, rispondi con valori dimezzati.
> 2. **Trigger su AUTO quando il segnale è discontinuo**: l'immagine salta; passa a **NORMAL** e imposta il livello a metà dell'ampiezza.
> 3. **Confondere i due canali**: stai misurando $V_{in}$ su Ch1 ma $V_{out}$ su Ch2 — invertiti: è il caso classico dell'amplificatore dove Guadagno < 1 inaspettatamente.
> 4. **Non convertire da picco a efficace**: $V_{eff} = V_p/\sqrt{2}$ per sinusoidi — non dimenticarlo.
> 5. **Misurare in AC coupling un segnale con offset**: l'oscilloscopio ti mente sulla forma d'onda reale se c'è una componente DC.
> 6. **Non cortocircuitare le C in DC**: se stai facendo misure DC su un circuito, ricorda che le C sono circuiti aperti.

---

## Cose da portare / sapere per la prova

- [ ] Conoscere i comandi base dell'oscilloscopio (trigger, coupling, scale, sonde)
- [ ] Conoscere la differenza tra sonda ×1 e sonda ×10
- [ ] Saper passare da $V_p$, $V_{pp}$ e $V_{eff}$ per sinusoidi, onde quadre, trianglolari
- [ ] Saper calcolare il valore efficace **vero efficace** (True RMS) per segnali non sinusoidali
- [ ] Conoscere le formule di base: $f = 1/T$, $V_{eff} = V_p/\sqrt{2}$, $\omega = 2\pi f$, $\varphi = \Delta t / T \cdot 360°$
- [ ] Aver fatto almeno **3 esercizi pratici** prima della prova (vai in laboratorio e prova a misurare)

> [!success] Traguardo
> Riesci a fare la sequenza operativa completa su un circuito che non hai mai visto prima, **senza leggere appunti**, in meno di 15 minuti, e a spiegare a voce cosa stai facendo? Sei pronto per la prova pratica.

---

## Link utili

- Appunti completi sull'oscilloscopio: [[L'oscilloscopio]]
- Esercizi di teoria abbinati: [[Esercizi - Segnali sinusoidali e fasori]], [[Esercizi - Reti RLC e risonanza]], [[Esercizi - Filtri passivi del primo ordine]]
- Esercizi di elettronica: [[Esercizi - Diodi]], [[Esercizi - BJT]], [[Esercizi - Amplificatori a BJT]]
