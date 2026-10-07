Il **Criterio di Routh** serve a determinare la stabilità di un sistema analizzando il suo polinomio caratteristico (il denominatore della funzione di trasferimento a ciclo chiuso $D(s)$). Permette di scoprire quante radici hanno **parte reale positiva** (poli instabili) senza doverle calcolare esplicitamente.

---

## 📌 1. PRE-REQUISITO (Condizione Necessaria)
Dato il polinomio di grado $n$:
$$p(s) = a_n s^n + a_{n-1} s^{n-1} + a_{n-2} s^{n-2} + \dots + a_1 s + a_0$$

⚠️ **Verifica preliminare:** Tutti i coefficienti da $a_n$ ad $a_0$ devono essere presenti (nessun termine mancante) e devono avere **tutti lo stesso segno**.
* Se manca un termine (coefficiente nullo) o c'è un cambio di segno nel polinomio di partenza, il sistema è **sicuramente instabile** (o al più marginalmente stabile). Puoi fermarti subito.

---

## 📊 2. COSTRUZIONE DELLA TABELLA DI ROUTH
Si costruisce una tabella con $n+1$ righe associate alle potenze decrescenti di $s$:

| Potenza | Colonna 1 | Colonna 2 | Colonna 3 | Colonna 4 |
| :--- | :--- | :--- | :--- | :--- |
| **$s^n$** | $a_n$ | $a_{n-2}$ | $a_{n-4}$ | $a_{n-6}$ ... |
| **$s^{n-1}$** | $a_{n-1}$ | $a_{n-3}$ | $a_{n-5}$ | $a_{n-7}$ ... |
| **$s^{n-2}$** | $b_1$ | $b_2$ | $b_3$ | ... |
| **$s^{n-3}$** | $c_1$ | $c_2$ | $c_3$ | ... |
| $\dots$ | $\dots$ | $\dots$ | $\dots$ | $\dots$ |
| **$s^0$** | $a_0$ | | | |

### 🛠️ Regole di riempimento:
1. **Righe 1 e 2:** Si inseriscono i coefficienti del polinomio alternandoli (la prima riga prende i coefficienti dei termini di posto pari/dispari partendo da $a_n$, la seconda riga i rimanenti).
2. **Righe successive:** Ogni elemento si calcola come il **determinante 2x2 cambiato di segno** costruito usando la prima colonna e la colonna immediatamente a destra della riga precedente, il tutto diviso per il per il primo elemento della prima colonna nella prima riga sopra a quella che stiamo calcolando

$$b_1 = \frac{a_{n-1} \cdot a_{n-2} - a_n \cdot a_{n-3}}{a_{n-1}} = -\frac{\det\begin{pmatrix} a_n & a_{n-2} \\ a_{n-1} & a_{n-3} \end{pmatrix}}{a_{n-1}}$$

$$b_2 = \frac{a_{n-1} \cdot a_{n-4} - a_n \cdot a_{n-5}}{a_{n-1}} = -\frac{\det\begin{pmatrix} a_n & a_{n-4} \\ a_{n-1} & a_{n-5} \end{pmatrix}}{a_{n-1}}$$

$$c_1 = \frac{b_1 \cdot a_{n-3} - a_{n-1} \cdot b_2}{b_1} = -\frac{\det\begin{pmatrix} a_{n-1} & a_{n-3} \\ b_1 & b_2 \end{pmatrix}}{b_1}$$

💡 *Trucco algebrico: Puoi moltiplicare o dividere un'intera riga per una qualsiasi costante **strettamente positiva** per semplificare i calcoli numerici e rimuovere le frazioni senza alterare i segni finali.*

---

## 🎯 3. ENUNCIATO E INTERPRETAZIONE (La Regola dei Segni)
Una volta completata la tabella, si analizza **esclusivamente la PRIMA COLONNA**:

1. ✅ **STABILITÀ ASINTOTICA:** Il sistema è asintoticamente stabile se e solo se **tutti gli elementi della prima colonna hanno lo stesso segno** (nessun cambio di segno).
2. ❌ **NUMERO DI POLI INSTABILI:** Se ci sono cambi di segno, il sistema è **instabile**. Il numero di radici con parte reale positiva (poli instabili) è esattamente pari al **numero di variazioni di segno** lungo la prima colonna.

*Esempio di conteggio delle variazioni:*
* Segni della prima colonna: `[+ , + , - , +]`
  * Da $+$ a $+$ $\to$ 0 variazioni
  * Da $+$ a $-$ $\to$ **1ª variazione**
  * Da $-$ a $+$ $\to$ **2ª variazione**
* *Esito:* Il sistema ha esattamente 2 poli instabili (a parte reale positiva).

---

## ⚠️ 4. CASI PARTICOLARI ANOMALI

### Caso A: Il primo elemento di una riga è $0$, ma gli altri elementi della riga NON sono tutti nulli
* **Problema:** Non puoi calcolare la riga successiva perché l'elemento pivot è nullo e causeretbbe una divisione per zero.
* **Soluzione:** Sostituisci lo $0$ con una variabile infinitesima positiva $\epsilon$ (con $\epsilon > 0$ e $\epsilon \to 0$). Continua a calcolare i termini successivi trascinando la variabile $\epsilon$. Al termine, valuta il segno degli elementi della prima colonna calcolando il limite per $\epsilon \to 0^+$.

### Caso B: Un'intera riga è composta da soli zeri `[0, 0, 0, ...]`
* **Significato fisico:** Indica la presenza di radici simmetriche rispetto all'origine nel piano complesso (coppie di poli immaginari puri $\pm j\omega$, poli reali simmetrici $\pm \sigma$ o quaterne di poli complessi coniugati simmetrici). Il sistema non è asintoticamente stabile.
* **Soluzione per completare l'analisi:**
  1. Prendi la riga immediatamente **sopra** la riga di zeri e scrivi il suo **Polinomio Ausiliario** $A(s)$, combinando i coefficienti della riga con le potenze di $s$ che scalano di due in due (es. se la riga è $s^4$, avrai $A(s) = c_1 s^4 + c_2 s^2 + c_3 s^0$).
  2. Calcola la derivata prima rispetto a $s$ di questo polinomio: $\frac{dA(s)}{ds}$.
  3. Sostituisci la riga di zeri con i coefficienti della derivata appena calcolata e riprendi il calcolo standard della tabella.

---

## ⚡ 5. UTILIZZO A TEMPO DISCRETO (Sistemi Campionati)
Il criterio di Routh verifica che le radici siano nel semipiano sinistro ($Re(s) < 0$). Se devi analizzare un polinomio a tempo discreto $p(z)$ per verificare che le radici siano dentro il cerchio unitario ($|z| < 1$):

1. Effettua la **Trasformazione Bilineare** sostituendo la variabile $z$:
   $$z = \frac{1 + w}{1 - w}$$
2. Moltiplica il polinomio ottenuto per $(1-w)^n$ per eliminare i denominatori, ricavando un nuovo polinomio equivalente nella variabile $w$:
   $$q(w) = (1-w)^n \cdot p\left(\frac{1+w}{1-w}\right)$$
3. Applica il Criterio di Routh standard descritto sopra sul nuovo polinomio $q(w)$.