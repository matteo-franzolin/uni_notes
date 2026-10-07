La **Trasformata di Laplace** è lo strumento matematico fondamentale per l'analisi dei sistemi LTI (Lineari Tempo-Invarianti). Consente di trasformare le equazioni differenziali nel dominio del tempo ($t$) in più semplici equazioni algebriche nel dominio della variabile complessa $s = \sigma + j\omega$.

---

## 📌 1. DEFINIZIONE GENERALE
Data una funzione del tempo $f(t)$ definita per $t \ge 0$, la sua trasformata di Laplace unilatera è definita dall'integrale:
$$\mathcal{L}[f(t)] = F(s) = \int_{0^{-}}^{\infty} f(t) e^{-st} dt$$

* La presenza dell'estremo inferiore $0^{-}$ permette di catturare correttamente eventuali impulsi o discontinuità nell'origine $t=0$.

---

## 🛠️ 2. PROPRIETÀ E REGOLE OPERATIVE FONDAMENTALI

Ogni volta che analizzi un sistema dinamico, utilizzerai queste proprietà chiave per muoverti tra i domini:

| Proprietà | Dominio del Tempo ($t$) | Dominio di Laplace ($s$) |
| :--- | :--- | :--- |
| **Linearità** | $\alpha f(t) + \beta g(t)$ | $\alpha F(s) + \beta G(s)$ |
| **Derivazione Prima** | $\frac{df(t)}{dt}$ | $s F(s) - f(0^-)$ |
| **Derivazione $n$-esima** | $\frac{d^n f(t)}{dt^n}$ | $s^n F(s) - s^{n-1}f(0^-) - \dots - f^{(n-1)}(0^-)$ |
| **Integrazione** | $\int_{0}^{t} f(\tau) d\tau$ | $\frac{F(s)}{s}$ |
| **Traslazione nel tempo** | $f(t - \tau)\delta_{-1}(t - \tau)$ | $e^{-s\tau} F(s)$ *(Modella i ritardi finiti)* |
| **Convoluzione** | $f(t) * g(t)$ | $F(s) \cdot G(s)$ |

💡 *Importante per i controlli:* Quando si calcola la **Funzione di Trasferimento** $G(s)$, si applica la proprietà di derivazione assumendo tutte le **condizioni iniziali rigorosamente nulle** ($f(0^-)=0$).

---

## 🎯 3. COPPIE NOTEVOLI (Segnali Canonici di Ingresso)

Queste sono le trasformate dei segnali standard usati per testare i sistemi:

1. **Impulso di Dirac ($\delta(t)$):**
   $$\mathcal{L}[\delta(t)] = 1$$
   *Nota:* La risposta a questo ingresso è la *risposta impulsiva* $g(t)$, la cui trasformata coincide con la f.d.t. $G(s)$ del sistema.
2. **Gradino Unitario ($\delta_{-1}(t)$ o $u(t)$):**
   $$\mathcal{L}[\delta_{-1}(t)] = \frac{1}{s}$$
3. **Rampa Unitaria ($t \cdot \delta_{-1}(t)$):**
   $$\mathcal{L}[t] = \frac{1}{s^2}$$
4. **Esponenziale Decrescente ($e^{-at} \cdot \delta_{-1}(t)$):**
   $$\mathcal{L}[e^{-at}] = \frac{1}{s + a}$$
5. **Seno e Coseno ($\sin(\omega t)$, $\cos(\omega t)$):**
   $$\mathcal{L}[\sin(\omega t)] = \frac{\omega}{s^2 + \omega^2}, \qquad \mathcal{L}[\cos(\omega t)] = \frac{s}{s^2 + \omega^2}$$

---

## 🏛️ 4. I DUE TEOREMI LIMITE (Fondamentali per l'analisi a regime)

Consentono di conoscere il comportamento asintotico del sistema direttamente in $s$, senza dover antitrasformare.

### I. Teorema del Valore Iniziale
Permette di calcolare il valore della funzione nell'istante iniziale $t = 0^+$:
$$f(0^+) = \lim_{t \to 0^+} f(t) = \lim_{s \to \infty} s F(s)$$
* *Vincolo:* La funzione $sF(s)$ deve essere una funzione razionale propria.

### II. Teorema del Valore Finalne
Permette di calcolare il valore di regime o l'errore statico a transitorio esaurito ($t \to \infty$):
$$f(\infty) = \lim_{t \to \infty} f(t) = \lim_{s \to 0} s F(s)$$
* ⚠️ **ATTENZIONE AL VINCOLO (Critico all'esame):** Puoi applicare questo teorema **SOLO SE** il sistema è asintoticamente stabile. Matematicamente, la funzione $sF(s)$ deve avere tutti i poli con parte reale strettamente negativa ($Re(p) < 0$), ammettendo al più un polo singolo nell'origine. Se ci sono poli a parte reale positiva o immaginari puri, il limite nel tempo non esiste (il sistema diverge o oscilla) e il teorema fallisce.

---

## 🔄 5. ANTITRASFORMAZIONE (Ritorno al tempo $t$)
Per tornare nel dominio del tempo si scompone la funzione razionale $F(s) = \frac{N(s)}{D(s)}$ in **fratti semplici** (Fratti di Hermite) in base alle radici del denominatore (poli):

### Caso A: Poli Reali Distinti ($p_1, p_2, \dots$)
$$F(s) = \frac{A}{s - p_1} + \frac{B}{s - p_2} \implies f(t) = A e^{p_1 t} + B e^{p_2 t}$$
* I poli determinano i **modi naturali** del sistema ($e^{p_i t}$). Se $p_i < 0$, il modo è stabile (smorza a zero).

### Caso B: Poli Reali Coincidenti di molteplicità $m$
$$F(s) = \frac{A_1}{s - p} + \frac{A_2}{(s - p)^2} + \dots + \frac{A_m}{(s - p)^m}$$
$$\implies f(t) = \left(A_1 + A_2 t + \frac{A_3}{2!}t^2 + \dots + \frac{A_m}{(m-1)!}t^{m-1}\right)e^{pt}$$

### Caso C: Poli Complessi Coniugati ($\sigma \pm j\omega$)
Generano risposte oscillatorie smorzate:
$$F(s) = \frac{M s + N}{(s - \sigma)^2 + \omega^2} \implies f(t) = X e^{\sigma t} \sin(\omega t + \theta)$$
* Se $\sigma < 0$, l'oscillazione si smorza (sistema stabile); se $\sigma > 0$ l'oscillazione diverge (sistema instabile).