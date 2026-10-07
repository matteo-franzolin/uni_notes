La **Trasformata Z** è lo strumento matematico fondamentale per l'analisi dei sistemi LTI (Lineari Tempo-Invarianti) a tempo discreto. Svolge esattamente lo stesso ruolo che la Trasformata di Laplace ha per il tempo continuo, convertendo le equazioni alle differenze in più semplici equazioni algebriche nella variabile complessa $z = e^{sT}$, dove $T$ è il periodo di campionamento.

---

## 📌 1. DEFINIZIONE GENERALE
Data una sequenza numerica temporale $f(k)$ definita per passi discreti $k \ge 0$, la sua trasformata Z unilatera è definita dalla serie complessa:
$$\mathcal{Z}[f(k)] = F(z) = \sum_{k=0}^{\infty} f(k) z^{-k}$$

---

## 🛠️ 2. PROPRIETÀ E REGOLE OPERATIVE FONDAMENTALI

Nel dominio discreto, i ritardi e gli anticipi temporali si convertono in moltiplicazioni per potenze di $z$:

| Proprietà | Dominio del Tempo Discreto ($k$) | Dominio Z ($z$) |
| :--- | :--- | :--- |
| **Linearità** | $\alpha f(k) + \beta g(k)$ | $\alpha F(z) + \beta G(z)$ |
| **Ritardo Temporale (Shift a destra)** | $f(k - 1) \cdot \delta_{-1}(k - 1)$ | $z^{-1} F(z)$ *(Fondamentale per i filtri digitali)* |
| **Ritardo Temporale di $n$ passi** | $f(k - n) \cdot \delta_{-1}(k - n)$ | $z^{-n} F(z)$ |
| **Anticipo Temporale (Shift a sinistra)** | $f(k + 1)$ | $z F(z) - z f(0)$ |
| **Anticipo Temporale di $n$ passi** | $f(k + n)$ | $z^n F(z) - \sum_{i=0}^{n-1} f(i) z^{n-i}$ |
| **Convoluzione Discreta** | $f(k) * g(k) = \sum_{i=0}^{k} f(i)g(k-i)$ | $F(z) \cdot G(z)$ |

💡 *Importante per i controlli:* Quando calcoli la **Funzione di Trasferimento Discreta** $G(z)$, si assume che tutte le **condizioni iniziali siano rigorosamente nulle** ($f(0)=0, f(1)=0, \dots$), riducendo la proprietà di anticipo a un semplice prodotto: $\mathcal{Z}[f(k+n)] = z^n F(z)$.

---

## 🎯 3. COPPIE NOTEVOLI (Segnali Canonici Discreti)

Queste sono le trasformate Z dei segnali standard usati nel tempo discreto:

1. **Impulso Unitario ($\delta(k)$):**
   $$\mathcal{Z}[\delta(k)] = 1$$
   *Nota:* Vale $1$ solo per $k=0$ e zero altrove. La risposta a questo ingresso è la risposta impulsiva discreta $g(k)$, la cui trasformata coincide con $G(z)$.
2. **Gradino Unitario ($\delta_{-1}(k)$ o $1(k)$):**
   $$\mathcal{Z}[\delta_{-1}(k)] = \frac{z}{z - 1} = \frac{1}{1 - z^{-1}}$$
3. **Rampa Unitaria ($k \cdot \delta_{-1}(k)$):**
   $$\mathcal{Z}[k] = \frac{z}{(z - 1)^2}$$
4. **Sequenza Geometrica / Esponenziale ($a^k \cdot \delta_{-1}(k)$):**
   $$\mathcal{Z}[a^k] = \frac{z}{z - a}$$
   *Nota:* Se la sequenza deriva dal campionamento di un esponenziale continuo $e^{-\alpha t}$ con passo $T$, allora $a = e^{-\alpha T}$.
5. **Seno e Coseno Discreti ($\sin(\omega k)$, $\cos(\omega k)$):**
   $$\mathcal{Z}[\sin(\omega k)] = \frac{z \sin(\omega)}{z^2 - 2z \cos(\omega) + 1}, \qquad \mathcal{Z}[\cos(\omega k)] = \frac{z(z - \cos(\omega))}{z^2 - 2z \cos(\omega) + 1}$$

---

## 🏛️ 4. I DUE TEOREMI LIMITE DISCRETI

Consentono di conoscere il comportamento limite della sequenza direttamente in $z$, senza dover antitrasformare.

### I. Teorema del Valore Iniziale
Permette di calcolare il primo valore della sequenza nell'istante $k = 0$:
$$f(0) = \lim_{z \to \infty} F(z)$$

### II. Teorema del Valore Finale
Permette di calcolare il valore di regime o l'errore statico a transitorio esaurito quando il numero di passi tende all'infinito ($k \to \infty$):
$$f(\infty) = \lim_{k \to \infty} f(k) = \lim_{z \to 1} (z - 1) F(z)$$
* ⚠️ **ATTENZIONE AL VINCOLO CRITICO:** Puoi applicare questo teorema **SOLO SE** il sistema è asintoticamente stabile. Nel dominio discreto, questo significa che la funzione $(z - 1)F(z)$ deve avere tutti i poli **strettamente dentro il cerchio unitario del piano z**, ovvero con modulo strettamente minore di 1 ($|p| < 1$). Se ci sono poli fuori o sul cerchio unitario (eccetto il polo singolo in $z=1$ che viene cancellato), la sequenza diverge o oscilla indefinitamente, e il teorema fallisce.

---

## 🔄 5. ANTITRASFORMAZIONE Z (Ritorno alla sequenza $k$)
Per ritornare nel dominio del tempo discreto partendo da una funzione razionale $F(z) = \frac{N(z)}{D(z)}$, il metodo standard prevede di scomporre in fratti semplici la funzione **$\frac{F(z)}{z}$** (per far comparire la $z$ al numeratore nei fratti finali):

### Metodo dei Fratti Semplici Passo-Passo:
1. Prendi la funzione e dividila per $z$: $\frac{F(z)}{z}$.
2. Scomponi $\frac{F(z)}{z}$ in fratti semplici in base ai poli (radici di $D(z)$).
3. Moltiplica nuovamente tutto per $z$, in modo che ogni termine sia nella forma $\frac{A \cdot z}{z - p_i}$.
4. Antitrasforma ogni singolo fratto usando le coppie note.

### Caso A: Poli Reali Distinti ($p_1, p_2, \dots$)
$$F(z) = \frac{A \cdot z}{z - p_1} + \frac{B \cdot z}{z - p_2} \implies f(k) = A (p_1)^k + B (p_2)^k$$
* I poli determinano i **modi naturali discreti** ($(p_i)^k$). Il sistema è asintoticamente stabile se e solo se tutti i poli soddisfano $|p_i| < 1$, poichè solo in quel caso $(p_i)^k \to 0$ quando $k \to \infty$.

### Caso B: Poli Complessi Coniugati ($r e^{\pm j\theta}$)
Generano oscillazioni campionate la cui stabilità dipende dal modulo $r$:
$$f(k) = C \cdot r^k \cdot \sin(\theta k + \phi)$$
* Se il modulo $r < 1$, i poli sono dentro il cerchio unitario e l'oscillazione si smorza; se $r > 1$ l'oscillazione diverge.