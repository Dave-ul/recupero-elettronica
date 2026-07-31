---
tags: [recupero, elettronica, alimentatori, power-supply, regolatori]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica"
libro_mirandola: "VERIFICATO ✔ (2026-07-25) — Cap. 8 «Gli alimentatori»: §1 alimentatori non stabilizzati e fattore di ripple (form. 8.1) pp. 388-389; regolatori integrati 78XX/79XX §3.1 pp. 406-407 (FIG. 20 struttura interna, FIG. 21 collegamento); TABELLA 1 famiglia 78XX pp. 408-409. Raddrizzatori/Zener anche nel Cap. 5 (diodi). Conversione folio Cap. 8: pag. stampata = 2·PDF + 122."
prove: [scritta, orale, pratica]
---

# Alimentatori — schema a blocchi, raddrizzatori, regolatori

> [!info] Dove serve
> **Pratica Protti**: rientra in «circuiti con diodi» (LETTERA Protti). Misura del ripple, regolazione di linea/load, test del regolatore 78xx. È il capitolo applicativo che unisce **diodi + BJT + filtro RC**. (NB: la LETTERA Carli scritta NON cita esplicitamente gli alimentatori — solo pratica Protti.)

Prerequisiti: [[Diodi]] · [[Filtri passivi del primo ordine]] · [[BJT]].

---

## 0. Spiegazione intuitiva (perché?)

> [!tip] Prima di iniziare
> Questo capitolo ti dà le formule e le procedure. **Ma perché funzionano così?** Per le risposte intuitive ("perché ricorsivo, come se spiegassi a un bambino di 4 anni che continua a chiedere perché"), apri il file hub: **[[00 - Perchè (spiegazione intuitiva)]] §12**.

## 1. Schema a blocchi di un alimentatore stabilizzato

```
       AC mains          DC
      ↓          ↓      ↓
  [Trasformatore] [Raddrizzatore] [Filtro C] [Regolatore] → V_out stabilizzato
      ↓                                     ↑
   230V → es. 12V      ponte     C elettrolitico    Zener / BJT / 78xx
```

Perché serve ogni blocco:
1. **Trasformatore**: abbassa la tensione di rete (230 V AC → es. 12 V AC) e isola galvanicamente.
2. **Raddrizzatore**: converte AC → DC (semionda, ponte di Graetz).
3. **Filtro C**: livella la tensione pulsante in una quasi-DC con ripple.
4. **Regolatore**: mantiene $V_{out}$ costante al variare di $V_{in}$ (regolazione di linea) e di $I_{load}$ (regolazione di carico).

> [!example]- La pagina del libro: FIGURA 3-5 e la **form. 8.1** — **Mirandola Cap. 8 §1, pp. 388-389**
> ![[libro-cap8-pp388-389-alimentatore-schema-blocchi.png]]
>
> **FIGURA 3** è lo schema a blocchi dell'alimentatore **non** stabilizzato (trasformatore → raddrizzatore → filtro → carico), disegnato con **la forma d'onda sotto ogni blocco**: sinusoide → semionde → semionde smussate → quasi-continua con ondulazione. Guardarla una volta vale più di rileggere l'elenco qui sopra: si vede *cosa fa* ogni stadio al segnale.
>
> **FIGURA 4** è la tensione d'uscita col ripple, e sopra c'è la definizione che conta:
> $$r = \frac{V_{Reff}}{V_{Lm}} \qquad (8.1)$$
> «*Si definisce **fattore di ripple** il rapporto $r$ tra il **valore efficace** dell'ondulazione residua a valle del filtro $V_r$ e il **valor medio** $V_{Lm}$ della tensione ai capi del carico.*»
>
> ⚠️ **Efficace su medio** — non picco-picco su medio. È esattamente l'equivoco che ha prodotto l'errore dell'Es. A1 (Lotto 10), con una $C$ sbagliata di un fattore ~3,5. Vedi il riquadro in [[Formulario rapido]] su quale delle due formule usare.
>
> **FIGURA 5** è il raddrizzatore a una semionda con filtro capacitivo, con i due passaggi da sapere: senza $C$, $V_{Lp} = V_{2p} - 0{,}7$ e $V_L = (V_{2p}-0{,}7)/\pi$ (valor medio di una semionda = picco/$\pi$); con $C$ in parallelo al carico la tensione non si annulla più, perché il condensatore si scarica su $R_L$ con $\tau = R_L C$ e una nuova semionda lo ricarica prima che arrivi a zero.

---

## 2. Raddrizzatore a semionda vs ponte

| Tipo | Schema | Tensione picco in uscita | Ripple ($f_r$) | Vantaggi/Svantaggi |
|---|---|---|---|---|
| **Semionda** | 1 diodo | $V_{out,p} \approx V_{in,p} - V_D$ | $f_{line}$ | Semplice, ma ripple grande e $V_{DC}$ bassa |
| **Ponte Graetz** | 4 diodi | $V_{out,p} \approx V_{in,p} - 2 V_D$ | $2 f_{line}$ | $V_{DC}$ più alta, ripple più piccolo, 4 diodi |

> [!warning] Caduta di $2 V_D$ nel ponte
> In un ponte Graetz, due diodi sono sempre in serie al carico → caduta di $\approx 1{,}4$ V. Per $V_{in,p} = 12$ V (tipico), $V_{out,p} \approx 10{,}6$ V.

Vedi [[Diodi#5. Il raddrizzatore]] per l'analisi circuitale.

---

## 3. Filtro a condensatore — calcolo del ripple

Il condensatore si carica al valore di picco, poi si scarica lentamente attraverso $R_L$ durante l'intervallo tra un picco e il successivo.

La tensione di uscita è $V_{DC} \approx V_{in,p} - n \cdot V_D$ (con $n = 1$ o $2$ rispettivamente).

Il ripple picco-picco è:
$$V_{r,pp} \approx \frac{I_{load}}{f_r \cdot C}$$

dove $f_r$ è:
- $f_{line}$ (es. 50 Hz) per **semionda**
- $2 f_{line}$ (es. 100 Hz) per **ponte**

> [!tip] Parametri operativi tipici
> - $I_{load}$ tra 100 mA e 1 A
> - $C$ tra 100 µF e 10.000 µF (condensatori elettrolitici)
> - $V_{r,pp}$ desiderato: 5% di $V_{DC}$ circa. Es. con $V_{DC} = 12$ V → $V_{r,pp} \leq 0{,}6$ V.

**Esempio di dimensionamento**: $I_{load} = 500$ mA, $f_r = 100$ Hz, $V_{r,pp}$ desiderato 0{,}5 V.
$$C = \frac{I_{load}}{f_r \cdot V_{r,pp}} = \frac{0{,}5}{100 \cdot 0{,}5} = 0{,}01\text{ F} = 10.000\,\mu\text{F}$$

Vedi anche [[Filtri passivi del primo ordine]] per l'analisi del comportamento in frequenza.

---

## 4. Regolazione di linea e di carico

Due parametri che definiscono la "bontà" di un regolatore:

- **Regolazione di linea** $\Delta V_{out}/\Delta V_{in}$: quanto $V_{out}$ cambia al variare di $V_{in}$. Ideale: 0.
- **Regolazione di carico** $\Delta V_{out}/\Delta I_{load}$: quanto $V_{out}$ cambia al variare del carico. Ideale: 0.
- **Resistenza di uscita** $r_{out} = \Delta V_{out}/\Delta I_{load}$: è un altro modo di esprimere la regolazione di carico.

> [!tip] Misura pratica (Protti)
> Per misurare la regolazione di carico: collega una resistenza variabile (reostato) come carico. Misura $V_{out}$ con multimetro DC per diversi valori di $I_{load}$ (calcolata da $V_{out}/R_L$). Il rapporto $\Delta V_{out}/\Delta I_{load}$ è la resistenza di uscita.

---

## 5. Regolatore a Zener (in parallelo)

Schema: $R_S$ in serie all'ingresso variabile, Zener in parallelo al carico.

$$V_{out} = V_Z \text{ (entro i limiti)}$$

**Dimensionamento di $R_S$**:
- $R_{S,\min} = \dfrac{V_{in,\max} - V_Z}{I_{Z,\max} + I_{L,\min}}$
- $R_{S,\max} = \dfrac{V_{in,\min} - V_Z}{I_{Z,\min} + I_{L,\max}}$

Devi scegliere $R_S$ dentro questo range per garantire la stabilizzazione in **tutte** le condizioni operative. Vedi [[Diodi#4. Il diodo Zener]] per i dettagli.

---

## 6. Regolatore serie a BJT (passo-passo per carichi medio-alti)

Limitazione del regolatore Zener: dissipa molta potenza e non può erogare correnti alte. Soluzione: **regolatore serie a BJT**.

```
V_in -- [R_S] -- [BJT (CE)] -- V_out
              |       (emettitore)
              Zener   |
              |       Collettore
              |-------| (a V_in)
              GND     Base
```

Il BJT è in **emitter follower**: $V_{out} = V_Z - V_{BE} = V_Z - 0{,}7$. La $R_S$ alimenta lo Zener; il BJT "replica" la tensione di Zener all'uscita, ma può erogare correnti molto più alte perché la corrente che attraversa lo Zener è piccola e costante.

**Procedura di dimensionamento**:
1. Scegli $V_Z$ (tensione di Zener) = $V_{out} + 0{,}7$ V.
2. Dimensiona $R_S$ per dare $I_Z \approx 5{-}10$ mA a tutti i regimi.
3. Il BJT deve essere in **zona attiva** ($V_{CE} > V_{CE,\text{sat}} = 0{,}2$ V). Per garantire questo: $V_{in,\min} > V_{out} + 1$ V (margine di 1 V).

> [!warning] Potenza dissipata dal BJT
> $P_{BJT} = (V_{in} - V_{out}) \cdot I_{load}$. Con $V_{in} = 15$ V, $V_{out} = 12$ V, $I_{load} = 1$ A: $P_{BJT} = 3$ W. Serve dissipatore!

---

## 7. Regolatori integrati 78xx e 79xx

> Struttura interna di un regolatore integrato a tre pin (Mirandola Vol.2, Cap. 8, **FIGURA 20**, p. 406): comprende il riferimento di tensione a Zener, un generatore di corrente costante, il BJT di regolazione e le protezioni contro cortocircuito/sovratemperatura.
> ![[libro-cap8-pp406-407-regolatore-integrato-78xx.png]]

> Collegamento di un regolatore integrato a tre pin in un alimentatore completo (Mirandola Vol.2, Cap. 8, **FIGURA 21**, p. 407): catena rete → trasformatore → raddrizzatore → filtro C → regolatore 78xx → carico, con i condensatori $C_i \approx 0{,}33\,\mu$F e $C_o \approx 0{,}1\,\mu$F ai morsetti dell'integrato. *(Le due figure stanno sulla stessa apertura del libro: è la stessa immagine qui sopra.)*

### La TABELLA 1 del libro (pp. 408-409)

> [!example]- La pagina del libro: TABELLA 1, ESEMPIO 7, alimentatori duali — **Mirandola Cap. 8 §3.1-3.3, pp. 408-409**
> ![[libro-cap8-pp408-409-tabella-78xx.png]]

Questi sono i valori **veri della TABELLA 1**, «*caratteristiche principali degli integrati della famiglia 78XX; le resistenze termiche sono riferite al contenitore TO-220*»:

| sigla | $V_i$ [V] | $V_o$ [V] | $I_o$ [A] | $I_{cc}$ [A] | $R_r$ [dB] | $\theta_{jc}$ [°C/W] | $\theta_{ja}$ [°C/W] | $V_D$ [V] |
|---|---|---|---|---|---|---|---|---|
| 7805 | 7 ÷ 35 | 4,8 ÷ 5,2 | 1 | 1,2 | 62 | 5 | 65 | 2,5 |
| 7806 | 8 ÷ 35 | 5,75 ÷ 6,25 | 1 | 1,2 | 59 | 5 | 65 | 2,5 |
| 7808 | 10 ÷ 35 | 7,7 ÷ 8,3 | 1 | 1,2 | 56 | 5 | 65 | 2,5 |
| 7812 | 14 ÷ 35 | 11,5 ÷ 12,5 | 1 | 1,2 | 55 | 5 | 65 | 2,5 |
| 7815 | 17 ÷ 35 | 14,4 ÷ 15,6 | 1 | 1,2 | 54 | 5 | 65 | 2,5 |
| 7818 | 20 ÷ 35 | 17,3 ÷ 18,7 | 1 | 1,2 | 53 | 5 | 65 | 2,5 |
| 7824 | 26 ÷ 35 | 23 ÷ 25 | 1 | 1,2 | 50 | 5 | 65 | 2,5 |
| 78G | 7,5 ÷ 40 | 5 ÷ 35 | 1 | 1,2 | 62 | 8 | 80 | 3 |

> [!danger] Correzione (Lotto 15) — la tabella precedente **non era** la TABELLA 1
> Questa nota attribuiva alla «TABELLA 1, pp. 408-409» una tabella di quattro colonne (Sigla / Tensione / Corrente / Note) che elencava **7805, 7812, 7815, 7905, 7912**. I valori di tensione e corrente erano giusti, ma:
> - la TABELLA 1 riguarda la **sola famiglia 78XX**: i **7905 e 7912 non ci sono**, e attribuirglieli è falso;
> - mancavano **7806, 7808, 7818, 7824, 78G**;
> - mancavano le tre colonne che contano davvero all'esame — $V_D$, $R_r$, $\theta$ — e la colonna «Note» era commento redazionale presentato come dato del libro.
>
> È una forma attenuata del **difetto sistemico #3** (la conferma fabbricata): non valori inventati, ma un'**attribuzione falsa** — una tabella propria spacciata per la tabella della fonte.

> [!tip] Le tre grandezze da ricordare, che prima non c'erano
> - **$V_D$ = 2,5 V (drop-out)**: «*in tutta la famiglia la tensione d'ingresso deve essere sempre almeno 2,5 V superiore alla tensione che si desidera in uscita*». Per un 7812 servono ≥ 14,5 V in ingresso — **nel punto più basso del ripple**, non in media. È l'errore classico da scritto.
> - **$R_r$ [dB], reiezione del ripple**: quanto l'integrato attenua il ripple residuo. Per il 7805, $R_r = 62$ dB ⇒ fattore $10^{62/20} = 1259$.
> - **$I_{cc}$ = 1,2 A**: la corrente di cortocircuito, maggiore di $I_o = 1$ A — è la protezione che interviene.
>
> La sigla si legge così (p. 408): dopo le prime due cifre, una lettera dà la corrente massima (**L** = 0,1 A, **C** = 0,5 A, **S** = 2 A, **T** = 3 A, **H** = 5 A, **P** = 10 A); **senza lettera si intende 1 A**. La **G** individua i regolatori a tensione variabile. Le due cifre finali (XX) sono la tensione d'uscita nominale. I **79XX** sono i regolatori di tensioni negative.

> [!note] Sulla stessa apertura, due cose che il vault non citava
> - **ESEMPIO 7** (p. 408): dimensionamento di $C$ di filtro e stabilizzatore per $V_o = 5$ V, $I_{L\max} = 0{,}8$ A, ripple d'uscita 7 mV picco-picco. Si sceglie il 7805, si legge $R_r = 62$ dB dalla TABELLA 1 ⇒ $V_{RPPi}/V_{RPPo} = 10^{62/20} = 1259$, quindi ripple ammesso in ingresso $= 1259 \cdot 7\text{ mV} = 8{,}8$ V; la $V_i$ può oscillare da 7,5 a 16,3 V. Poi con la **relazione 8.4**: $C = I_{L\max}\dfrac{\Delta t}{V_{RPP}} = \dfrac{0{,}8}{2 \cdot 50 \cdot 8{,}8} = 909\ \mu$F → **valore commerciale 1000 µF**.
> - **FIGURA 22** (p. 409): l'**alimentatore duale**, un solo trasformatore a presa centrale, un ponte di Graetz, due condensatori e due regolatori (78XX per la positiva, 79XX per la negativa). È qui che entrano i 7905/7912.
> - **FIGURA 23** (p. 409): come aumentare la corrente d'uscita con un BJT esterno **T** in Darlington col regolatore — **A)** NPN, con $V_{out} = V_o - 0{,}7$ (TIP 110, $I_L = 4$ A); **B)** PNP, che mantiene la tensione nominale (TIP 115, $I_L = 4$ A).

> [!tip] Codice identificativo
> Le lettere **78** = regolatore positivo, **79** = regolatore negativo. Il numero finale = tensione di uscita. La lettera intermedia indica la corrente:
> - **L** = 100 mA (es. 78L12)
> - **M** = 500 mA (es. 78M12)
> - **Senza lettera** = 1 A (es. 7812)
> - **T** = 3 A (es. 78T12)

### Schema di applicazione tipico

```
   V_in ──┬──[78xx]── V_out
          │   │
          C_in C_out
          │   │
          GND GND
```

- $C_{in} \approx 0{,}33\,\mu\text{F}$ (per stabilità)
- $C_{out} \approx 0{,}1\,\mu\text{F}$ (per ridurre il ripple)

> [!check] Regolazione di linea vs carico
> I 78xx hanno tipicamente:
> - Regolazione di linea: $\sim 0{,}01\%$/V (ottima)
> - Regolazione di carico: $\sim 1\%$ (accettabile)
> - Ripple rejection: $\sim 60$ dB (1 µV di ripple in uscita se l'ingresso ha 1 mV di ripple)

### Alimentazione duale per amplificatori operazionali

Per circuiti con operazionali (che richiedono $\pm V_{CC}$):
- Un ponte raddrizzatore fornisce $V_{+}$ (es. +15 V) → entra in un 7815 → $V_{+}$ stabilizzato.
- Un secondo ponte (o parte del primo) fornisce $V_{-}$ (es. −15 V) → entra in un 7915 → $V_{-}$ stabilizzato.
- Collega $V_{-}$ "al contrario" rispetto al ponte positivo.

---

## 8. Calcoli tipici per un alimentatore completo (esempio svolto)

**Specifiche**: $V_{out} = 12$ V, $I_{load,\max} = 1$ A, ripple $\leq 0{,}5\%$, $V_{in} = 230$ V AC a 50 Hz.

**Soluzione**:

1. **Trasformatore**: $V_{2,\text{eff}} = V_{out}/(\sqrt{2} - 2V_D/V_{in,p}) \approx 10$ V (per avere $V_{out,p} \approx 12{,}7$ V prima della regolazione).
2. **Ponte Graetz**: 4 diodi ($V_D = 0{,}7$ V ciascuno, due in serie → $1{,}4$ V di caduta).
3. **Filtro C**: $C = I_{load}/(f_r \cdot V_{r,pp}) = 1\text{A}/(100\text{Hz} \cdot 0{,}5\% \cdot 12{,}7\text{V}) \approx 1575\,\mu\text{F}$.
4. **Regolatore**: 7812 (12 V, 1 A). Dissipa $P = (V_{in} - 12) \cdot I = (12{,}7 - 12) \cdot 1 = 0{,}7$ W (accettabile senza diss.).

> [!warning] Tensione di dropout
> Il 7812 ha una **dropout voltage** di $\approx 2{,}5$ V (TABELLA 1 del libro: $V_D = 2{,}5$ V per tutta la famiglia standard; l'ingresso deve stare **almeno 2,5 V** sopra l'uscita): $V_{in}$ deve essere $\geq 14{,}5$ V perché funzioni bene. Per $V_{in} = 12{,}7$ V il 7812 è **fuori regolazione**. Aumentare il trasformatore a $V_{2,\text{eff}} = 12$ V → $V_{in,p} \approx 17$ V → margine sufficiente.

---

## Quesiti tipo — Guida rapida

> [!question] Perché serve un condensatore di filtro dopo il raddrizzatore?
> Per "livellare" la tensione di uscita: senza filtro, l'uscita è una doppia semionda rettificata (varia tra 0 e il picco). Con il condensatore, l'uscita diventa quasi continua — pari al picco, con un piccolo ripple sovrapposto.

> [!question] Perché lo Zener da solo non basta per carichi pesanti?
> Perché dissipa troppa potenza: $P_Z = (V_{in} - V_Z) \cdot I_Z$. Per $I_{load} = 1$ A, serve una $R_S$ piccola → $I_Z$ enorme → Zener brucia. La soluzione è il **regolatore serie a BJT**, dove lo Zener pilota solo la base del BJT.

> [!question] Differenza tra 7812 e 78L12?
> Stessa tensione (12 V), ma il 78L12 eroga al massimo 100 mA (l'arrangiamento interno usa transistor più piccoli). Il 7812 eroga 1 A.

> [!question] Posso usare un 7812 per alimentare un circuito che richiede esattamente 12 V e 50 mA?
> Sì, ma il 7812 brucia $\approx (15-12) \cdot 0{,}05 = 0{,}15$ W di potenza "in eccesso". In questo caso il 78L12 (100 mA) basterebbe, con meno calore dissipato.

> [!question] Come misuro il ripple in laboratorio (Protti)?
> Collega l'oscilloscopio in **AC coupling** sull'uscita del regolatore → leggi $V_{r,pp}$ direttamente sullo schermo. Se il ripple è troppo alto per la specifica, aumenta $C_{in}$ o aggiungi un filtro LC all'uscita.

---

## 9. Da qui in poi

- Prerequisiti: [[Diodi]], [[Filtri passivi del primo ordine]], [[BJT]]
- Esercizi: [[Esercizi - Alimentatori]]
- Simulazione completa: [[Esercizi - Simulazione finale]]
