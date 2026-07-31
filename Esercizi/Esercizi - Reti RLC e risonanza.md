---
tags: [recupero, elettronica, corrente-alternata, risonanza, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ (2026-07-22) — Cap. 2, ESEMPIO 3 (p. 56) ed ESEMPIO 4 (p. 58); esercizi 7-8 di fine capitolo con FIGURE 43-44 a pp. 82-83. Teoria §2.1-2.2 pp. 55-58, folio letti dal piè di pagina."
prove: [scritta, orale, pratica]
---

# Esercizi — Reti RLC e risonanza

Teoria di riferimento: [[Reti RLC e risonanza]]

---

# Parte A — Quesito (prova orale)

> [!question]- 13 — Quando si verificano la risonanza serie e la risonanza parallelo? Quali fenomeni producono?
> **Quando**: entrambe alla stessa pulsazione,
> $$\omega_s = \omega_p = \frac{1}{\sqrt{LC}}$$
> cioè quando le due reattanze hanno **uguale modulo e segno opposto** e si annullano a vicenda.
>
> **Quali fenomeni** — e qui sta il punto, perché le formule sono identiche ma i comportamenti sono opposti:
>
> | | **Serie** | **Parallelo** (antirisonanza) |
> |---|---|---|
> | $\bar{Z}_{eq}$ | $\to 0$: **cortocircuito** | $\to \infty$: **circuito aperto** |
> | si annullano | le **tensioni**: $V_L + V_C = 0$ | le **correnti**: $I_L + I_C = 0$ |
> | diventa massima | la **corrente** assorbita | la **tensione** ai capi |
> | sui componenti | tensioni molto maggiori di quella d'ingresso | correnti molto maggiori di quella d'ingresso |
> | fattore di qualità | $Q = \frac{1}{R}\sqrt{\frac{L}{C}}$ | $Q = R\sqrt{\frac{C}{L}}$ |
>
> **In entrambi i casi**, alla risonanza il bipolo è **puramente resistivo**: tensione e corrente sono **in fase**.
>
> Da aggiungere se il prof scava: fuori dalla risonanza la serie è **resistivo-capacitiva** per $\omega < \omega_s$ (alle basse frequenze $X_L \to 0$) e **resistivo-induttiva** per $\omega > \omega_s$ (alle alte $X_C \to 0$).

---

# Parte B — Esercizi (prova scritta)

## Esercizio 7 — Risonanza serie

**Testo.** Calcolare il valore della frequenza di risonanza serie della rete $LC$ contenuta nel circuito in FIGURA 43; a questa frequenza calcolare i valori efficaci della tensione e della corrente sul resistore $R_1$. *(Vedi ESEMPIO 3)*
**Risposte del libro:** $f_s = 10730$ Hz; $I_1 = 1{,}49$ mA; $V_1 = 7$ V

![[fig-2-43-risonanza-serie-esercizio-7.png]]
*FIGURA 43 — $v_g = 7$ V$_{eff}$, $R_1 = 4{,}7$ k$\Omega$, $C = 220$ nF, $L = 1$ mH, $R_2 = 1$ k$\Omega$. (Mirandola, esercizi di fine Cap. 2, pp. 82-83)*

> [!success]- Soluzione
> **La frequenza di risonanza** dipende solo da $L$ e $C$ — le resistenze non contano:
> $$f_s = \frac{\omega_s}{2\pi} = \frac{1}{2\pi\sqrt{LC}} = \frac{1}{2\pi\sqrt{1\cdot10^{-3}\cdot 220\cdot10^{-9}}} = \frac{1}{2\pi\sqrt{2{,}2\cdot10^{-10}}}$$
> $$= \frac{1}{2\pi\cdot 1{,}483\cdot10^{-5}} = 10{.}730\ \text{Hz} \;✅$$
>
> **Il colpo di scena.** Alla risonanza la serie $LC$ è un **cortocircuito**: il nodo a valle di $R_1$ va **direttamente a massa**. Quindi:
> - $R_2$ è cortocircuitata e **non conta più nulla**;
> - **tutta** la tensione del generatore cade su $R_1$.
>
> $$V_1 = v_g = 7\ \text{V} \;✅$$
> $$I_1 = \frac{V_1}{R_1} = \frac{7}{4700} = 1{,}489\ \text{mA} \simeq 1{,}49\ \text{mA} \;✅$$

> [!tip] Riconoscere l'idea dell'esercizio
> Il valore di $R_2 = 1$ k$\Omega$ è messo lì **apposta come esca**: alla risonanza è irrilevante, perché la serie $LC$ la cortocircuita. Se ti sei messo a calcolare il parallelo tra $R_2$ e qualcosa, hai perso tempo.
> **La mossa è sempre la stessa**: alla risonanza, sostituisci mentalmente la serie $LC$ con un filo. Il circuito che resta è banale.

---

## Esercizio 8 — Risonanza parallelo

**Testo.** Calcolare il valore della frequenza di risonanza parallelo della rete $LC$ contenuta in FIGURA 44; a questa frequenza calcolare i valori efficaci della tensione e della corrente sul resistore $R_1$. *(Vedi ESEMPIO 4)*
**Risposte del libro:** $f_p = 7118$ Hz; $I_1 = 270$ µA; $V_1 = 0{,}730$ V

![[fig-2-44-risonanza-parallelo-esercizio-8.png]]
*FIGURA 44 — $v_g = 2$ V$_{eff}$, $R_1 = 2{,}7$ k$\Omega$, $C = 100$ nF, $R_2 = 4{,}7$ k$\Omega$, $L = 5$ mH. (Mirandola, esercizi di fine Cap. 2, pp. 82-83)*

> [!success]- Soluzione
> **La frequenza di risonanza**:
> $$f_p = \frac{1}{2\pi\sqrt{LC}} = \frac{1}{2\pi\sqrt{5\cdot10^{-3}\cdot 100\cdot10^{-9}}} = \frac{1}{2\pi\sqrt{5\cdot10^{-10}}} = \frac{1}{2\pi\cdot 2{,}236\cdot10^{-5}} = 7118\ \text{Hz} \;✅$$
>
> **Il colpo di scena, stavolta rovesciato.** Alla risonanza il parallelo $LC$ è un **circuito aperto**: $C$ e $L$ spariscono dal circuito. Resta un semplice partitore $R_1$–$R_2$, e la tensione su $R_1$ vale:
> $$V_1 = v_g\,\frac{R_1}{R_1+R_2} = 2\cdot\frac{2700}{2700+4700} = 2\cdot 0{,}365 = 0{,}730\ \text{V} \;✅$$
>
> (verifica: su $R_2$ cade $v_g\frac{R_2}{R_1+R_2} = 2\cdot 0{,}635 = 1{,}27$ V, e $0{,}73 + 1{,}27 = 2$ V ✅ — qui le tensioni si sommano normalmente, perché sono tutte in fase: il circuito è puramente resistivo)
>
> $$I_1 = \frac{V_1}{R_1} = \frac{0{,}730}{2700} = 270\ \mu\text{A} \;✅$$

> [!check] I due esercizi sono lo stesso esercizio, rovesciato
> Confrontali, perché è il modo migliore per fissare la differenza:
>
> | | Esercizio 7 (serie) | Esercizio 8 (parallelo) |
> |---|---|---|
> | alla risonanza l'$LC$ è… | un **filo** | un **buco** |
> | quindi $R_2$… | è **cortocircuitata**, sparisce | resta, e forma il partitore |
> | su $R_1$ c'è… | **tutta** la $v_g$ (7 V su 7 V) | solo una **parte** (0,73 V su 2 V) |
>
> **Il metodo è identico in entrambi**: calcola $f = \frac{1}{2\pi\sqrt{LC}}$, poi sostituisci l'$LC$ con un filo (serie) o toglilo (parallelo), e risolvi il circuito resistivo che resta. Niente numeri complessi, niente coniugati.
>
> È anche il motivo per cui questi due esercizi sono facili **se hai capito**, e impossibili se provi ad affrontarli di forza bruta calcolando impedenze complesse.

---

## Esercizi correlati su edutecnica

Fra gli esercizi di fine Cap. 2 **non ce n'è nessuno di dimensionamento** di circuiti risonanti: i due sulla risonanza (nn. 7-8, qui sopra) sono entrambi di *analisi*. Su [Edutecnica](https://www.edutecnica.it/elettronica/filtripx/filtripx.htm) ce ne sono due che vanno nella direzione opposta (dai requisiti ai componenti):

- **Esercizio 6**: dimensionare un circuito risonante **parallelo** con $f_o = 1$ MHz, banda passante $B = 20$ kHz, disponendo di $L = 80$ µH.
- **Esercizio 7**: dimensionare un circuito risonante **serie** con $f_o = 100$ kHz, banda passante $B = 5$ kHz, disponendo di $L = 7$ mH.

Introducono il legame tra **fattore di qualità e banda passante**, che il libro tratta nel **Cap. 4 «I quadripoli», formula 4.53, p. 162** (folio letto dall'immagine), a proposito dei filtri passa banda RLC: «*Nei filtri passa banda a banda stretta, il valore del parametro $Q$ equivale al rapporto tra la pulsazione centrale ($\omega_0$) e la larghezza di banda ($\omega_{tH} - \omega_{tL}$) del filtro*», e per questo «*$Q$ esprime la selettività del filtro: maggiore è il valore di $Q$ più il filtro è selettivo*».

> [!info] Il libro la stampa **in pulsazioni**, non in frequenze
> La forma stampata della **4.53** è
> $$Q = \frac{\omega_0}{\omega_{tH} - \omega_{tL}}$$
> mentre in giro (edutecnica compresa) si trova quasi sempre $Q = f_0/B$. **Sono la stessa cosa**: il $2\pi$ si semplifica fra numeratore e denominatore, $\omega_0/(\omega_{tH}-\omega_{tL}) = 2\pi f_0 / [2\pi(f_{tH}-f_{tL})] = f_0/B$. Nei conti usa pure $f_0/B$; **all'orale enuncia la forma stampata**, che è quella che Carli si aspetta di sentire.
>
> Sulla stessa pagina, due formule che vale la pena portarsi dietro:
> - **(4.52)** $\xi = \dfrac{1}{2Q}$ — il legame fra coefficiente di smorzamento e fattore di qualità;
> - **(4.54)** $\omega_0 = \sqrt{\omega_{tH}\cdot\omega_{tL}}$ — in un passa banda la pulsazione centrale è la **media geometrica** delle pulsazioni di taglio, **non** la media aritmetica.

**Sono già svolti**, in [[Esercizi - Filtri passivi del primo ordine]] come **Es. F6** (parallelo) ed **Es. F7** (serie): stanno lì perché vengono dal catalogo `filtripx` di edutecnica, che è la fonte della Parte B di quella nota. Vedili là; qui restano elencati perché è questa la nota in cui l'argomento «risonanza» viene studiato.

---

## Esercizi svolti — circuiti risonanti (serie e parallelo)

### Es. R1 — Calcolo $f_0$ e verifica di risonanza serie

- **Dati**: $R = 50\,\Omega$, $L = 100\,\mu\text{H}$, $C = 10$ nF.
- **Procedura**: $\omega_0 = 1/\sqrt{LC} = 1/\sqrt{100\mu\text{H} \cdot 10\text{nF}} = 1/\sqrt{10^{-12}} = 10^6$ rad/s. $f_0 = 159{,}15$ kHz.
- Q-factor serie: $Q = \omega_0 L/R = 10^6 \cdot 100\mu\text{H}/50 = 2$. Banda passante: $BW = f_0/Q = 159{,}15\text{kHz}/2 = 79{,}6$ kHz.

### Es. R2 — Risonanza parallelo (antirisonanza)

- **Dati**: $R = 10\,\text{k}\Omega$ (resistenza di perdita), $L = 1$ mH, $C = 1$ nF.
- **Procedura**: $\omega_0 = 1/\sqrt{LC} = 1/\sqrt{10^{-12}} = 10^6$ rad/s. $f_0 = 159{,}15$ kHz.
- Q-factor parallelo: $Q = R/(\omega_0 L) = 10\text{k}/(10^6 \cdot 1\text{mH}) = 10$. $BW = f_0/Q = 15{,}9$ kHz.

### Es. R3 — Circuito risonante a tre elementi con calcolo Correnti

- **Dati**: serie $R = 20\,\Omega$, $L = 5$ mH, $C = 50$ nF; alimentazione $V = 10$ V a frequenza incognita.
- **Trovare**: $f_0$, comportamento a risonanza, $I_{\text{max}}$.
- **Svolgimento**: $f_0 = 1/(2\pi\sqrt{LC}) = 1/(2\pi\sqrt{5\text{mH} \cdot 50\text{nF}}) = 1/(2\pi\sqrt{2{,}5 \cdot 10^{-10}}) = 1/(2\pi \cdot 1{,}58\text{e-5}) = 10065$ Hz.
- A risonanza, $X_L = X_C$, $Z = R = 20\,\Omega$. $I_{\text{max}} = 10\text{V}/20\,\Omega = 500$ mA.

### Es. R4 — Questo è il classico "TRUCCO" da uscita

Spesso all'orale Carli chiede: "Data una rete RLC, dimostrare che a risonanza il modulo dell'impedenza è solo R."

**Risposta — caso serie.** A $\omega_0$ si ha $X_L = \omega_0 L$ e $X_C = 1/(\omega_0 C)$; poiché per definizione $\omega_0 L = 1/(\omega_0 C)$, le due reattanze sono uguali e
$$\bar Z = R + j(X_L - X_C) = R \;✔$$
Questa è la dimostrazione che serve nel 90% dei casi.

> [!danger] Attenzione: nel **parallelo reale** la risposta è diversa — e non è $R$
> Una versione precedente di questa nota si interrompeva qui con «$Y = 1/(R+j\omega_0 L) + j\omega_0 C$… vedi caso specifico», lasciando intendere che venisse ancora $R$. **Non è così**, e se lo dici all'orale sbagli.
>
> Con l'induttore reale ($R$ **in serie** a $L$, il tutto in parallelo a $C$):
> $$\bar Y = \frac{1}{R+j\omega L} + j\omega C = \frac{R - j\omega L}{R^2+\omega^2L^2} + j\omega C$$
> La risonanza si ha dove la parte immaginaria si annulla:
> $$\omega C = \frac{\omega L}{R^2+\omega^2 L^2} \;\Longrightarrow\; C\,(R^2+\omega^2L^2) = L \;\Longrightarrow\; \omega_0 = \frac{1}{\sqrt{LC}}\sqrt{1 - \frac{CR^2}{L}}$$
> che è **esattamente** la correzione realistica del libro a p. 58 nel caso $R_C = 0$ (condensatore ideale): $\omega_p = \frac{1}{\sqrt{LC}}\sqrt{\frac{L-CR_L^2}{L-CR_C^2}}$. Vedi §3 di [[Reti RLC e risonanza]].
>
> E a quella pulsazione l'impedenza vale
> $$|\bar Z|_{\max} = \frac{1}{\operatorname{Re}(\bar Y)} = \frac{R^2+\omega_0^2L^2}{R} = \frac{L}{RC}$$
> — la cosiddetta **resistenza dinamica**, che è tanto più **grande** quanto più $R$ è **piccola**. È il duale del caso serie e il motivo per cui $Q_{\text{parallelo}}$ migliora al crescere di $R$ nel modello di FIGURA 13, dove però $R$ è in **parallelo**, non in serie.
>
> **Morale**: prima di rispondere, guarda **dov'è la resistenza**. In serie al ramo → $Z_{\min}=R$. In parallelo al serbatoio (FIGURA 13) → $Z_{\max}=R$. In serie all'induttore (caso reale) → $Z_{\max}=L/RC$, e la $\omega_0$ si sposta.

## Pattern di errore frequenti (Carli scritta)

1. **Confondere $X_L$ e $X_C$**: $X_L = \omega L$ (positiva), $X_C = -1/(\omega C)$ (negativa). Errore: stesso segno.
2. **Confondere serie e parallelo**: in serie $Z_{\min} = R$; in parallelo $Z_{\max} = R$. Errore opposto comune.
3. **Dimenticare $Q$ nel calcolo della BW**: $BW = f_0/Q$, NON $f_0 - f_L$.
