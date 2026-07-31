---
tags: [recupero, elettronica, filtri, esercizi]
fonte_secondaria: "edutecnica.it — verificato coerente su 8/8 topic chiave (BJT, MOSFET, JFET, Amplificatori, Diodi/Zener, Filtri RC/RL, Alimentatori, Trifase)"
fonte_ufficiale: "MAJORANA lettera giudizio sospeso 09/06/2026 — IIS San Lazzaro di Savena (BO), classe 4BEM Meccanica-Elettronica, studente Davide Rocca"
libro_mirandola: "VERIFICATO ✔ (2026-07-22) — Cap. 4 §3.1, ESEMPIO 19 e FIGURA 48 a p. 160, ESEMPIO 20 a p. 161. Esercizi e quesiti di fine Cap. 4 a pp. 188-191 (pagg.-PDF 73-74), folio letti dal piè di pagina."
prove: [scritta, orale, pratica]
---

# Esercizi — Filtri passivi del primo ordine

Teoria di riferimento: [[Filtri passivi del primo ordine]]

> [!warning] Perché qui c'è anche edutecnica
> Il libro copre i filtri con due **esempi svolti** dentro il capitolo (ESEMPIO 19 a p. 160 e ESEMPIO 20 a p. 161, qui sotto) più i **quesiti ed esercizi di fine Cap. 4** (pp. 188-191). Sono pochi per allenarsi allo scritto, quindi la Parte B viene da [Edutecnica](https://www.edutecnica.it/elettronica/filtripx/filtripx.htm), l'unico sito che mi hai autorizzato.
>
> ⚠️ *Correzione del Lotto 8 (2026-07-22).* Una versione precedente di questo riquadro affermava che «la scansione **non contiene gli esercizi del Capitolo 4**» e che «le pagine 184-191 mancano». **È falso**: le pagine ci sono tutte (pagg.-PDF 71-74, folio letti dal piè di pagina) — pp. 184-187 GUIDA ALLA PROGETTAZIONE sui filtri crossover, pp. 188-189 quesiti di riepilogo, **pp. 190-191 esercizi numerati** (fra cui il n. 19, *progettare un filtro passa alto del primo ordine*, e il n. 17 sulla risposta in ampiezza). È la **quarta volta** che il vault dichiara assente dal libro materiale presente — vedi [[00 - Audit e correzioni]].

> [!tip] Come usarli
> Le soluzioni sono **ripiegate**: clicca sulla freccia per aprirle. Prova a risolvere prima di guardare — un esercizio letto non è un esercizio fatto, e allo scritto la differenza si vede.

---

# Parte A — Dal libro

## ESEMPIO 19 — Riconoscere il tipo e calcolare la frequenza di taglio

*(Mirandola, Cap. 4 §3.1, p. 160)*

**Testo.** Dei filtri in FIGURA 48 individuare il tipo di risposta e il valore della frequenza di taglio.

![[fig-4-48-circuiti-esempio-19.png]]
*FIGURA 48 — I quattro circuiti dell'ESEMPIO 19: passa alto RC (2,2 µF / 1,8 kΩ), passa alto RL (47 kΩ / 12 mH), passa basso RL (5 mH / 3,3 kΩ), passa basso RC (5,6 kΩ / 47 nF). (Mirandola, p. 160)*

> [!success]- Soluzione
> Si procede in due passi per ciascun circuito: prima si guarda **dov'è l'uscita** per capire il tipo (§5.2 della teoria), poi si applica la formula della $f_t$.
>
> **1° circuito** — $C = 2{,}2\ \mu$F in serie, $R = 1{,}8$ k$\Omega$ verso massa, uscita su $R$.
> Il condensatore è in serie → a $f=0$ è aperto → $v_o = 0$ → **passa alto RC**.
> $$f_t = \frac{1}{2\pi RC} = \frac{1}{2\pi \cdot 1800 \cdot 2{,}2\cdot10^{-6}} = 40{,}2\ \text{Hz}$$
>
> **2° circuito** — $R = 47$ k$\Omega$ in serie, $L = 12$ mH verso massa, uscita su $L$.
> L'uscita è su $L$ → **passa alto RL**.
> $$f_t = \frac{R}{2\pi L} = \frac{47\cdot10^{3}}{2\pi \cdot 12\cdot10^{-3}} = 623\ \text{kHz}$$
>
> **3° circuito** — $L = 5$ mH in serie, $R = 3{,}3$ k$\Omega$ verso massa, uscita su $R$.
> L'induttanza è in serie → a $f=0$ è un corto → $v_o = v_i$ → **passa basso RL**.
> $$f_t = \frac{R}{2\pi L} = \frac{3{,}3\cdot10^{3}}{2\pi \cdot 5\cdot10^{-3}} = 105\ \text{kHz}$$
>
> **4° circuito** — $R = 5{,}6$ k$\Omega$ in serie, $C = 47$ nF verso massa, uscita su $C$.
> L'uscita è su $C$ → **passa basso RC**.
> $$f_t = \frac{1}{2\pi RC} = \frac{1}{2\pi \cdot 5600 \cdot 47\cdot10^{-9}} = 604\ \text{Hz}$$
>
> Il libro chiude invitando a rilevare la risposta in ampiezza di ogni filtro con il simulatore Multisim, verificando le frequenze di taglio e la pendenza della curva in banda oscura.

> [!question] Nota importante su questo esempio
> È proprio qui che il libro **usa la formula corretta** $f_t = \dfrac{R}{2\pi L}$, contraddicendo le formule (4.45) e (4.47) stampate poche righe più sopra sulla stessa pagina. Vedi l'errata corrige nel §6 di [[Filtri passivi del primo ordine]].

---

## ESEMPIO 20 — Progettare un filtro

*(Mirandola, Cap. 4 §3.1, p. 161)*

**Testo.** Progettare un filtro passa basso del primo ordine con frequenza di taglio $f_t = 3400$ Hz.

> [!success]- Soluzione
> Si sceglie la configurazione **passa basso RC** rappresentata in TABELLA 6.
> Si deve individuare una coppia di valori di $R$ e $C$ tali che:
> $$f_t = \frac{\omega_p}{2\pi} = \frac{1}{2\pi RC} = 3400\ \text{Hz}$$
>
> Qui sta il punto didattico: **un'equazione, due incognite**. Il problema è *sottodeterminato*, quindi è possibile fissare a piacere il valore di uno dei due componenti e calcolare l'altro.
>
> Si fissa per esempio $C = 10$ nF e si ricava $R$:
> $$R = \frac{1}{2\pi C f_t} = \frac{1}{2\pi \cdot 10\cdot10^{-9} \cdot 3400} = 4681\ \Omega$$
>
> che si può approssimare col **valore commerciale** $R = 4{,}7$ k$\Omega$.

> [!tip] Il metodo di progetto, in generale
> Nei problemi di dimensionamento conviene **sempre** fissare il condensatore e ricavare la resistenza, mai il contrario. Il motivo è pratico: i condensatori esistono in pochi valori standard e con tolleranze larghe, mentre i resistori si trovano in tantissimi valori con tolleranze strette. Fissare $C$ a un valore comodo e ricavare $R$ dà quasi sempre un componente reperibile; al contrario si finisce spesso con capacità impossibili da comprare.
> Poi si arrotonda al valore commerciale della serie E12/E24 (4,7 k$\Omega$ nell'esempio) e si verifica che la $f_t$ risultante sia ancora accettabile.

---

# Parte B — Da Edutecnica

*Fonte: [Esercizi su filtri passivi — Edutecnica](https://www.edutecnica.it/elettronica/filtripx/filtripx.htm). Testi e soluzioni sono riscritti e ricontrollati; dove ho trovato errori li ho segnalati.*

## Esercizio 1 — Frequenza di taglio di un passa basso RC

**Testo.** Calcolare la frequenza angolare (frequenza di taglio) di un filtro RC passa basso formato da $R = 10$ k$\Omega$ e $C = 2$ nF.

> [!success]- Soluzione
> Per il circuito assegnato la funzione di trasferimento vale:
> $$A_v(s) = \frac{v_o(s)}{v_i(s)} = \frac{1/sC}{R + 1/sC} = \frac{1}{1 + sCR}$$
>
> La frequenza angolare si ha in corrispondenza del **polo**, che si ottiene ponendo:
> $$1 + sCR = 0 \;\Longrightarrow\; |s| = \omega_p = \frac{1}{RC} = \frac{1}{\tau_p} = \frac{1}{10\cdot10^{3}\cdot 2\cdot10^{-9}} = 50\cdot10^{3}\ \text{rad/s}$$
>
> Poi:
> $$f_p = f_H = \frac{\omega_p}{2\pi} = \frac{50\cdot10^{3}}{2\pi} = 7{,}96\ \text{kHz}$$
>
> Si chiama $f_H$ (*high*) perché per un passa basso è la frequenza di taglio **superiore**: la banda passante va da 0 a $f_H$.

---

## Esercizio 2 — Dimensionamento con vincolo sull'impedenza d'ingresso

**Testo.** Dimensionare un filtro passa-basso RC in modo che presenti alle alte frequenze un'impedenza di ingresso $Z_i = 10$ k$\Omega$ e una frequenza di taglio $f_H = 20$ kHz.

> [!success]- Soluzione
> Del circuito assegnato è nota la funzione di trasferimento $A_v = \dfrac{v_o}{v_i} = \dfrac{1}{1+sCR}$, usando la pulsazione complessa $s = \sigma + j\omega$.
>
> **Primo passo: sfruttare il vincolo sulle alte frequenze.**
> Alle alte frequenze $\omega = 2\pi f \to \infty$, che è come dire $s \to \infty$. Per il condensatore:
> $$\lim_{s\to\infty} \frac{1}{sC} = \frac{1}{\infty} = 0$$
> impedenza nulla, cioè il condensatore è un **cortocircuito**. Il circuito si riduce alla sola $R$ vista dall'ingresso, quindi:
> $$Z_i = \frac{v}{i} = R = 10\ \text{k}\Omega$$
>
> Ecco perché il problema è risolvibile: il vincolo su $Z_i$ **fissa $R$**, eliminando l'indeterminazione che avevamo nell'ESEMPIO 20.
>
> **Secondo passo: ricavare $C$ dalla frequenza di taglio.**
> $$\omega_p = \frac{1}{\tau_p} = \frac{1}{RC}, \qquad \omega_p = 2\pi f_H = 2\pi\cdot 20\cdot10^{3} = 125.664\ \text{rad/s}$$
> $$C = \frac{1}{R\,\omega_p} = \frac{1}{10^{4}\cdot 125.664} = 7{,}95\cdot10^{-10}\ \text{F} = 795\ \text{pF}$$

---

## Esercizio 3 — Filtro RL con Thévenin

**Testo.** Nel circuito assegnato dire di che tipo di filtro si tratta, ricavarne la funzione di trasferimento ed eventuali frequenze di taglio.

![[circuito-edutecnica-es3.png]]
*Dati: $R_1 = 1$ k$\Omega$, $R_2 = 2$ k$\Omega$, $R_3 = 1{,}5$ k$\Omega$, $L = 10$ mH. (Edutecnica)*

> [!success]- Soluzione
> Il circuito **non** è un partitore semplice: prima di $L$ c'è già una rete resistiva. Si semplifica col **teorema di Thévenin** la parte a monte del taglio.
>
> **Generatore equivalente** (partitore fra $R_1$ e $R_2$):
> $$v_q = \frac{R_2\, v_i}{R_1 + R_2} = \frac{2}{1+2}\,v_i = \frac{2}{3}\,v_i$$
>
> **Resistenza equivalente** (parallelo fra le due resistenze, con il generatore spento):
> $$R_q = R_1 \parallel R_2 = \frac{1\cdot 2}{1+2} = \frac{2}{3}\ \text{k}\Omega \simeq 0{,}667\ \text{k}\Omega$$
>
> Ora il circuito è diventato un semplice **passa basso RL**: $R_q$ ed $L$ in serie, $R_3$ verso massa. Trattandosi di un partitore:
> $$v_o = \frac{R_3}{R_q + R_3 + sL}\, v_q$$
>
> Mettendo in forma canonica e sostituendo $v_q$:
> $$\frac{v_o}{v_i} = \left(\frac{R_3}{R_q+R_3}\right) \cdot \frac{1}{1 + s\left(\frac{L}{R_q+R_3}\right)} \cdot \left(\frac{R_2}{R_1+R_2}\right)$$
>
> dove il primo fattore è il partitore d'uscita, il secondo è il filtro vero e proprio e il terzo è il partitore d'ingresso.
>
> Passando ai valori numerici ($R_q + R_3 = 0{,}667 + 1{,}5 = 2{,}167$ k$\Omega$):
> $$\frac{v_o}{v_i} = \left(\frac{1{,}5}{2{,}167}\right)\cdot\left(\frac{2}{3}\right)\cdot \frac{1}{1 + s\,\frac{10\cdot10^{-3}}{2167}} = \frac{0{,}461}{1 + s\,4{,}61\cdot10^{-6}}$$
>
> Si tratta di un **filtro passa basso** con pulsazione di taglio:
> $$\omega_p = \frac{1}{\tau_p} = \frac{1}{4{,}61\cdot10^{-6}} = 216.666\ \text{rad/s} \qquad f_p = f_H = \frac{216.666}{2\pi} = 34{,}48\ \text{kHz}$$
>
> In continua ($s = \omega = 0$):
> $$A_v = \frac{v_o}{v_i} = 0{,}461 \;\Longrightarrow\; |A_v|_{dB} = 20\lg 0{,}461 = -6{,}71\ \text{dB}$$
>
> Il diagramma di Bode del modulo è quindi piatto a $-6{,}71$ dB fino a $2{,}16\cdot10^5$ rad/s, poi scende a $-20$ dB/dec. La fase va da $0°$ a $-90°$, con pendenza $-45°/$dec.

> [!note] Due cose da notare
> **1.** Il guadagno in banda passante **non è 0 dB** ma $-6{,}71$ dB: le resistenze $R_1$, $R_2$, $R_3$ formano partitori che attenuano il segnale anche in continua. Resta comunque $\le$ 0 dB — coerente con la natura passiva del filtro (§3 della teoria).
> **2.** La costante di tempo è $\tau = \dfrac{L}{R_q + R_3}$, cioè $L$ diviso **tutta** la resistenza che l'induttanza "vede". È di nuovo la regola $\omega_p = 1/\tau$ del §5.4: non $L/R$, ma $R/L$ con la $R$ giusta.

---

## Esercizio 4 — Filtro con uno zero e un polo

**Testo.** Nel circuito assegnato, dire di che tipo di filtro si tratta dopo aver trovato la funzione di trasferimento e disegnato la risposta in frequenza per il modulo e per la fase.

![[circuito-edutecnica-es4.png]]
*Dati: $R_1 = 9$ k$\Omega$, $R_2 = 1$ k$\Omega$, $C = 10$ nF. (Edutecnica)*

> [!success]- Soluzione
> Il circuito è un partitore fra la resistenza $R_1$ e l'impedenza $Z$, con
> $$Z = R_2 + \frac{1}{sC} = \frac{1 + sCR_2}{sC}$$
>
> La funzione di trasferimento è:
> $$A_v = \frac{v_o}{v_i} = \frac{Z}{R_1 + Z} = \frac{\frac{1+sCR_2}{sC}}{R_1 + \frac{1+sCR_2}{sC}} = \frac{1 + sCR_2}{1 + sC(R_1+R_2)}$$
>
> quindi **un polo e uno zero**.
>
> **Zero:**
> $$1 + sCR_2 = 0 \Rightarrow z = -\frac{1}{CR_2} \qquad \omega_z = \frac{1}{CR_2} = \frac{1}{10\cdot10^{-9}\cdot 10^{3}} = 10^{5}\ \text{rad/s}$$
> $$f_z = \frac{\omega_z}{2\pi} = \frac{10^{5}}{2\pi} = 15{,}9\ \text{kHz}$$
>
> **Polo:**
> $$1 + sC(R_1+R_2) = 0 \Rightarrow p = -\frac{1}{C(R_1+R_2)} \qquad \omega_p = \frac{1}{10\cdot10^{-9}\cdot(1+9)\cdot10^{3}} = 10^{4}\ \text{rad/s}$$
> $$f_p = \frac{\omega_p}{2\pi} = \frac{10^{4}}{2\pi} = \mathbf{1{,}59\ kHz}$$
>
> **Comportamento agli estremi.**
> In continua e alle basse frequenze l'attenuazione è unitaria:
> $$A_v\Big|_{s=0} = \frac{1+0}{1+0} = 1 \;\Longrightarrow\; |A_v|_{dB} = 20\lg 1 = 0\ \text{dB}$$
> Alle alte frequenze:
> $$\lim_{s\to\infty} A_v = \lim_{s\to\infty}\frac{1+sCR_2}{1+sC(R_1+R_2)} = \frac{R_2}{R_1+R_2} = \frac{1}{10} \;\Longrightarrow\; |A_v|_{dB} = 20\lg\frac{1}{10} = -20\ \text{dB}$$
>
> **Diagramma.** Si vede come sia $\omega_p < \omega_z$: il diagramma asintotico rimane costante a 0 dB fino a $\omega_p = 10^4$ rad/s, poi inizia a scendere con pendenza $-20$ dB/dec. Raggiunta la pulsazione dello zero ($10^5$ rad/s), che contribuisce con $+20$ dB/dec, il diagramma torna **orizzontale**, all'altezza di $-20$ dB.
>
> Dal diagramma del modulo si ricava che si tratta di un **filtro passa basso**.

> [!danger] Errore su Edutecnica in questo esercizio
> Edutecnica scrive: «*ovviamente* è $f_p = \dfrac{\omega_p}{2\pi} = \dfrac{10^4}{2\pi} = 15{,}9$ kHz».
> **È sbagliato**: $\dfrac{10^4}{2\pi} = 1591\ \text{Hz} = \mathbf{1{,}59\ kHz}$. Hanno ricopiato il risultato dello zero, che è davvero 15,9 kHz ma parte da $10^5$.
> Il controllo è immediato: $\omega_z = 10^5$ è **dieci volte** $\omega_p = 10^4$, quindi anche le frequenze devono stare in rapporto 10:1. Non possono essere entrambe 15,9 kHz.

> [!note] Non è un passa basso "puro"
> Attenzione: questo filtro ha uno zero oltre al polo, quindi alle altissime frequenze non continua a scendere ma si **appiattisce** a $-20$ dB. Non azzera mai davvero il segnale. In gergo è uno *shelf*, a gradino. Resta comunque un unico polo → pendenza massima 20 dB/dec.

---

## Esercizio 5 — Passa alto con condensatore in parallelo

**Testo.** Nel circuito assegnato dire di che tipo di filtro si tratta dopo aver trovato la funzione di trasferimento e disegnato il diagramma asintotico del modulo.

![[circuito-edutecnica-es5.png]]
*Dati: $R_1 = 10$ k$\Omega$, $R_2 = 2{,}2$ k$\Omega$, $C = 10$ nF. (Edutecnica)*

> [!success]- Soluzione
> Bisogna prima risolvere il **parallelo** fra il condensatore $C$ e la resistenza $R_1$:
> $$Z = \frac{\frac{R_1}{sC}}{R_1 + \frac{1}{sC}} = \frac{R_1}{1 + sCR_1}$$
>
> Poi, per la regola del partitore, $\dfrac{v_o}{v_i} = \dfrac{R_2}{R_2 + Z}$:
> $$A_v = \frac{R_2}{R_2 + \frac{R_1}{1+sCR_1}} = \frac{R_2(1+sCR_1)}{R_1 + R_2 + sCR_1R_2} = \frac{R_2}{R_1+R_2}\cdot\frac{1 + sCR_1}{1 + sC\frac{R_1R_2}{R_1+R_2}}$$
>
> **Guadagno in continua:**
> $$\frac{R_2}{R_1+R_2} = \frac{2{,}2}{2{,}2+10} = 0{,}18 \;\Longrightarrow\; |A_v|_{dB} = 20\lg 0{,}18 = \mathbf{-14{,}9\ dB}$$
>
> **Resistenza equivalente del parallelo:**
> $$\frac{R_1R_2}{R_1+R_2} = \frac{22}{12{,}2} = 1{,}8\ \text{k}\Omega$$
>
> **Zero:**
> $$\omega_z = \frac{1}{CR_1} = \frac{1}{10\cdot10^{-9}\cdot10^{4}} = 10^{4}\ \text{rad/s}$$
>
> **Polo:**
> $$\omega_p = \frac{1}{C\,\frac{R_1R_2}{R_1+R_2}} = \frac{1}{10\cdot10^{-9}\cdot 1{,}8\cdot10^{3}} = 5{,}5\cdot10^{4}\ \text{rad/s}$$
>
> Qui lo zero viene **prima** del polo ($\omega_z < \omega_p$): il diagramma parte piatto a $-14{,}9$ dB, dallo zero sale a $+20$ dB/dec, e dal polo torna piatto a 0 dB. Il guadagno **cresce** con la frequenza → si tratta di un **filtro passa alto**, con frequenza di taglio:
> $$f_L = \frac{\omega_p}{2\pi} = \frac{5{,}5\cdot10^{4}}{2\pi} \simeq 8{,}8\ \text{kHz}$$
>
> Si chiama $f_L$ (*low*) perché per un passa alto è la frequenza di taglio **inferiore**.

> [!danger] Errore su Edutecnica in questo esercizio
> Edutecnica scrive: «sul diagramma asintotico sarà $20\lg 0{,}18 = 5{,}12$ dB».
> **È sbagliato**: il logaritmo di un numero **minore di 1** è negativo, quindi il risultato non può essere positivo. Il valore corretto è:
> $$20\log_{10}(0{,}18) = 20\cdot(-0{,}745) = -14{,}9\ \text{dB}$$
> Che sia negativo lo conferma anche il loro stesso disegno, dove l'asintoto di sinistra sta **sotto** la tacca dei $-10$ dB. E lo impone la teoria: è un filtro **passivo**, quindi non può avere guadagni positivi in dB (§3 della teoria).

---

## Esercizio 8 — Trovare la frequenza data l'attenuazione

**Testo.** Calcolare a quale frequenza un filtro passa alto con $C = 10$ nF e $R = 5$ k$\Omega$ presenta un'attenuazione di 6 dB.

> [!success]- Soluzione
> In questo tipo di filtro la funzione di trasferimento è $A_v(s) = \dfrac{sCR}{1+sCR}$ e la pulsazione di taglio coincide con il polo:
> $$p = \omega_p = \frac{1}{CR} = \frac{1}{10\cdot10^{-9}\cdot 5\cdot10^{3}} = 20.000\ \text{rad/s}$$
>
> **Primo passo: dai dB al rapporto.** Sapendo che per un filtro passivo l'attenuazione massima è a 0 dB, un'attenuazione di 6 dB vuol dire:
> $$-6 = 20\lg A_v \;\Longrightarrow\; A_v = 10^{-6/20} = \frac{1}{2}$$
>
> Utile ricordarlo: **$-6$ dB $=$ metà ampiezza**, così come $-3$ dB $=$ metà *potenza*.
>
> **Secondo passo: l'espressione del modulo.** Ponendo $s = j\omega$ e ricordando che $\omega_p = 1/CR$:
> $$A_v = \frac{1}{1 - j\left(\frac{\omega_p}{\omega}\right)} \;\Longrightarrow\; |A_v| = \frac{1}{\sqrt{1 + \left(\frac{\omega_p}{\omega}\right)^2}}$$
>
> **Terzo passo: imporre la condizione.**
> $$\frac{1}{\sqrt{1+\left(\frac{20000}{\omega}\right)^2}} = \frac{1}{2} \;\Longrightarrow\; \sqrt{1+\left(\frac{20000}{\omega}\right)^2} = 2 \;\Longrightarrow\; \left(\frac{20000}{\omega}\right)^2 = 3$$
> $$\omega^2 = \frac{4\cdot10^{8}}{3} \;\Longrightarrow\; \omega = \sqrt{\frac{4\cdot10^{8}}{3}} = 11.547\ \text{rad/s}$$
>
> La frequenza cercata vale:
> $$f = \frac{11.547}{2\pi} = 1837\ \text{Hz}$$

> [!check] Controllo di plausibilità
> Il risultato **deve** stare sotto la frequenza di taglio, e infatti:
> $$f_t = \frac{\omega_p}{2\pi} = \frac{20.000}{2\pi} = 3183\ \text{Hz} \qquad\text{e}\qquad 1837 < 3183 \;✅$$
> Ha senso: è un **passa alto**, quindi scendendo di frequenza l'attenuazione aumenta. A $f_t$ l'attenuazione è 3 dB; per averne 6 dB bisogna scendere ancora. Se ti fosse venuto un valore *sopra* i 3183 Hz, avresti sicuramente sbagliato un passaggio.

---

> [!info] Esercizi non inclusi
> Gli esercizi 6 e 7 di Edutecnica riguardano i **circuiti risonanti** (serie e parallelo): sono del secondo ordine, quindi fuori da questa nota. Li trovi in [[Reti RLC e risonanza]].

## Esercizi svolti da Edutecnica.it (catalogo filtripx completo)

> [!tip] Fonte
> Esercizi tratti da [edutecnica.it/elettronica/filtripx/filtripx.htm](https://www.edutecnica.it/elettronica/filtripx/filtripx.htm). 8 esercizi su filtri passivi del primo ordine (RC/RL) e circuiti risonanti.

### Es. F1 — RC passa-basso: calcolo $f_H$

- **Dati**: $R = 10\,\text{k}\Omega$, $C = 2$ nF.
- **Soluzione edutecnica**: $f_H = 7{,}96$ kHz.
- **Svolgimento**: $f_H = 1/(2\pi RC) = 1/(2\pi \cdot 10\text{k} \cdot 2\text{ nF}) = 1/(2\pi \cdot 20\,\mu\text{s}) = 1/(125{,}66\,\mu\text{s}) \approx 7{,}96$ kHz ✓.

### Es. F2 — Dimensionamento RC passa-basso

- **Dati**: $Z_i = 10\,\text{k}\Omega$ (alle alte frequenze), $f_H = 20$ kHz.
- **Procedura**: $R \approx Z_i = 10\,\text{k}\Omega$. $C = 1/(2\pi R f_H) = 1/(2\pi \cdot 10\text{k} \cdot 20\text{k}) = 795{,}8$ pF.

### Es. F3 — 3R + L con un componente (RL passa-basso)

- **Dati**: $R_1=1\,\text{k}$, $R_2=2\,\text{k}$, $R_3=1{,}5\,\text{k}$, $L=10$ mH.
- **Soluzione edutecnica**: **passa-basso**, $f_H = 34{,}5$ kHz.
- **Svolgimento**: il filtro è RL con l'uscita sull'induttore assente — l'uscita è sulla rete resistiva, quindi è un **passa basso RL** e la $f_H$ dipende dalla $R_{eq}$ che l'induttore «vede» guardando indietro nel circuito (teorema di Thévenin, con il generatore spento cioè cortocircuitato).
- **Risolto** (Lotto 8): la combinazione che torna è $R_{eq} = (R_1 \parallel R_2) + R_3$, cioè le due resistenze del partitore d'ingresso in parallelo, in serie con la terza:
$$R_{eq} = \frac{1\cdot 2}{1+2}\text{k} + 1{,}5\text{k} = 666{,}7 + 1500 = 2166{,}7\ \Omega$$
$$f_H = \frac{R_{eq}}{2\pi L} = \frac{2166{,}7}{2\pi \cdot 10\cdot10^{-3}} = 34{,}48\ \text{kHz} \simeq 34{,}5\ \text{kHz} \;✔$$
> [!note] Perché le due ipotesi precedenti erano sbagliate
> Una versione precedente di questa nota si fermava a «*probabilmente serie = 4,5 k? O parallelo?*», lasciando il conto a metà. Nessuna delle due ipotesi funziona: le tre resistenze **in serie** danno 4,5 k$\Omega$ (→ 71,6 kHz, il doppio del vero), mentre $(R_1+R_2)\parallel R_3$ dà 1,0 k$\Omega$ (→ 15,9 kHz). Solo $(R_1\parallel R_2)+R_3$ riproduce i 34,5 kHz di edutecnica — che è quindi **corretta**. Il modo per non sbagliare è partire dal risultato: $R_{eq} = 2\pi L f_H = 2168\ \Omega$, poi cercare quale combinazione dei valori dati lo produce.

### Es. F4 — 2R + C (passa-basso a partitore)

- **Dati**: $R_1=9\,\text{k}$, $R_2=1\,\text{k}$, $C=10$ nF.
- **Soluzione edutecnica**: passa-basso.
- **Svolgimento**: tipico schema: $R_1$ in serie all'ingresso, poi $R_2$ in parallelo a $C$ all'uscita. All'uscita prelevi tensione su $R_2 || C$ (è la $Z_2$ del partitore). Funzione di trasferimento: $G(s) = (R_2 || (1/sC))/(R_1 + R_2 || (1/sC))$.

### Es. F5 — 2R + C (passa-alto a partitore)

- **Dati**: $R_1=10\,\text{k}$, $R_2=2{,}2\,\text{k}$, $C=10$ nF.
- **Soluzione edutecnica**: passa-alto.
- **Svolgimento**: schema: $C$ in serie a $R_1$ all'ingresso, poi $R_2$ all'uscita. Uscita su $R_2$.

### Es. F6 — Dimensionamento circuito risonante parallelo

> [!tip] Sono gli unici due esercizi **di dimensionamento** del vault
> F6 e F7 vanno nella direzione opposta a tutti gli altri: non dai componenti alla risposta, ma **dai requisiti ($f_0$, $B$) ai componenti**. È la forma in cui Carli li chiede più volentieri allo scritto, perché non si può risolvere a memoria. Il procedimento è sempre lo stesso in tre passi: $C$ dalla $f_0$, poi $Q = f_0/B$, poi $R$ dalla definizione di $Q$ — **che è diversa fra serie e parallelo**.

- **Dati**: $f_0 = 1$ MHz, $BW = 20$ kHz, $L = 80\,\mu\text{H}$.
- **Trovare**: $C$ e $R$.
- **Svolgimento**:
  1. $C = 1/((2\pi f_0)^2 L) = 1/((2\pi \cdot 10^6)^2 \cdot 80\,\mu\text{H}) = 1/(39{,}48 \cdot 10^{12} \cdot 80 \cdot 10^{-6}) = 1/(3{,}158 \cdot 10^9) \approx 316{,}6$ pF.
  2. $Q = f_0/BW = 10^6/(20 \cdot 10^3) = 50$.
  3. Per parallelo RLC: $Q = R/(\omega_0 L) \implies R = Q \cdot \omega_0 L = 50 \cdot 2\pi \cdot 10^6 \cdot 80\,\mu\text{H} = 50 \cdot 502{,}65\,\Omega = 25133\,\Omega \approx 25\,\text{k}\Omega$.
- **Controllo**: $|Z|_{\max} = R = 25$ k$\Omega$ a $f_0$, e la banda a $-3$ dB è larga $f_0/Q = 20$ kHz ✔ (è il requisito di partenza).

> [!warning] Quale «parallelo»? Qui $R$ è **in parallelo** al serbatoio
> La formula $Q = R/(\omega_0 L)$ vale per il modello di **FIGURA 13** del libro, con $R$ in parallelo a $L$ e $C$ — ed è quello che usa edutecnica. Se invece $R$ è **in serie all'induttore** (l'induttore reale, con la sua resistenza di avvolgimento) le formule cambiano: $|Z|_{\max} = L/RC$ e la $\omega_0$ si sposta di $\sqrt{1 - CR^2/L}$.
> **Prima di applicare la formula, guarda dov'è la resistenza.** È lo stesso errore corretto nell'Es. R4 di [[Esercizi - Reti RLC e risonanza]] e nel formulario: la tabella a tre casi sta in [[Formulario rapido]].

### Es. F7 — Dimensionamento circuito risonante serie

- **Dati**: $f_0 = 100$ kHz, $BW = 5$ kHz, $L = 7$ mH.
- **Trovare**: $C$ e $R$.
- **Svolgimento** (con $\omega_0 = 2\pi f_0 = 6{,}283 \cdot 10^5$ rad/s):
  1. $C = \dfrac{1}{\omega_0^2 L} = \dfrac{1}{(6{,}283 \cdot 10^5)^2 \cdot 7 \cdot 10^{-3}} = \dfrac{1}{2{,}763 \cdot 10^{9}} \approx 361{,}9$ **pF**.
  2. $Q = f_0/BW = 100\text{k}/5\text{k} = 20$.
  3. Per serie RLC: $Q = \omega_0 L/R \implies R = \omega_0 L/Q = (6{,}283 \cdot 10^5 \cdot 7 \cdot 10^{-3})/20 = 4398/20 \approx 220\,\Omega$.
- **Controllo**: 220 $\Omega$ è un valore **E12** commerciale, e $|Z|_{\min} = R$ a $f_0$ ✔.

> [!danger] Correzione — qui c'era un errore di **1000×** (Lotto 15)
> Questa soluzione riportava «$C \approx 361{,}7$ **nF**»: sono **pF**. L'errore nasceva dalla scorciatoia di scrittura dei due passaggi, dove $\omega_0$ era scritta `628` invece di $628 \cdot 10^3$ — mille volte più piccola. Col `628` letterale il passo 3 darebbe $0{,}22\ \Omega$ invece di 220 $\Omega$, quindi l'errore era **nella scrittura, non nel risultato** del passo 3; ma al passo 1 è finito anche nell'unità di misura.
> Verificato contro la soluzione di edutecnica (esercizio 7 del catalogo `filtripx`), che dà **362 pF**, $Q = 20$, $R = 220\ \Omega$: i valori coincidono. **Regola**: non abbreviare mai una pulsazione lasciando cadere la potenza di dieci — è il tipo di refuso che l'ordine di grandezza del risultato non segnala, perché «361,7» resta plausibile.

### Es. F8 — Attenuazione 6 dB su passa-alto

- **Dati**: $C = 10$ nF, $R = 5\,\text{k}\Omega$, attenuazione $-6$ dB.
- **Trovare**: $f$ corrispondente.
- **Svolgimento**: per passa-alto RC $|A_v| = (f/f_L)/\sqrt{1 + (f/f_L)^2}$. Per $|A_v| = 10^{-6/20} \approx 0{,}501$: risolvendo si trova $f \approx 0{,}509 \cdot f_L$. $f_L = 1/(2\pi RC) = 1/(2\pi \cdot 5\text{k} \cdot 10\text{nF}) = 1/(2\pi \cdot 50\,\mu\text{s}) = 3183$ Hz. $f_{6dB} \approx 0{,}509 \cdot 3183 \approx 1620$ Hz.

## Pattern di errore frequenti (Carli scritta)

1. **Confondere la costante di tempo con la frequenza di taglio**: per il gruppo RL la $\tau = L/R$ (è un tempo, si misura in secondi), ma la pulsazione di taglio è il suo **reciproco**, $\omega_p = R/L$. È esattamente qui che il libro sbaglia: a **p. 160** le formule (4.45) e (4.47) stampano $\omega_p = L/R$ e $f_t = L/2\pi R$ — vedi l'errata corrige nel §6 di [[Filtri passivi del primo ordine]]. Verifica sempre dimensionalmente.
2. **Sbagliare $f = \omega/(2\pi)$**: $f$ in Hz, $\omega$ in rad/s. Errore: usare $\omega$ come se fosse $f$ → fattore $2\pi$.
3. **Confondere LPF e HPF**: "in serie C, in uscita R" → HPF. "in serie R, in uscita C" → LPF. Errore opposto è comune.
