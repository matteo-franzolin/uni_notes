# Guida Completa per il Tracciamento del Luogo delle Radici

Il **Luogo delle Radici** (Root Locus) è uno strumento grafico fondamentale nell'analisi e nella sintesi dei sistemi di controllo lineari e stazionari (LTI). Rappresenta la traiettoria dei poli in ciclo chiuso al variare di un parametro di guadagno (solitamente $k$) da $0$ a $+\infty$.

Si consideri la funzione di trasferimento in ciclo aperto $L(s) = k \cdot G(s)H(s) = k \cdot rac{N(s)}{D(s)}$, dove il polinomio a numeratore ha grado $m$ (zeri) e il polinomio a denominatore ha grado $n$ (poli), con $n \ge m$.

L'equazione caratteristica del sistema in ciclo chiuso è:
$$1 + k \cdot L(s) = 0 \implies D(s) + k \cdot N(s) = 0$$

Di seguito sono riportati, passo dopo passo, tutte le regole e gli step analitici per tracciare il **Luogo Diretto** ($k > 0$).

---

## 1. Identificazione di Poli e Zeri
Determinare i poli e gli zeri della funzione di trasferimento in ciclo aperto $L(s)$ per $k=1$.
- **Numero di poli ($n$):** Radici di $D(s) = 0$. Rappresentano i punti di partenza delle traiettorie per $k 	o 0$.
- **Numero di zeri ($m$):** Radici di $N(s) = 0$. Rappresentano i punti di arrivo di $m$ traiettorie per $k 	o \infty$.
- **Grado relativo ($n - m$):** Determina il numero di rami che vanno all'infinito ($z_\infty$).

## 2. Simmetria del Luogo
Il luogo delle radici è **simmetrico rispetto all'asse reale** ($	ext{Re}(s)$). Questo accade perché i coefficienti dei polinomi $N(s)$ e $D(s)$ sono reali, e di conseguenza le radici complesse coniugate compaiono sempre in coppie.

## 3. Segmenti sull'Asse Reale
Un punto dell'asse reale appartiene al luogo delle radici (diretto, $k > 0$) se e solo se:
* Il numero totale di poli e zeri reali alla sua **destra** è **dispari**.

*Nota: I poli e gli zeri complessi coniugati non influenzano il conteggio sull'asse reale poiché si trovano a coppie.*

## 4. Comportamento all'Infinito: Asintoti
Se $n > m$, ci sono $n - m$ rami che tendono all'infinito seguendo degli asintoti lineari.

### Centro degli Asintoti ($s_0$ o $\sigma_a$)
Il punto di intersezione degli asintoti sull'asse reale si calcola come:
$$s_0 = \frac{\sum \text{Poli} - \sum \text{Zeri}}{n - m} = \frac{\sum_{i=1}^n p_i - \sum_{j=1}^m z_j}{n - m}$$

### Angoli degli Asintoti ($\phi_a$)
Gli angoli che gli asintoti formano con l'asse reale positivo sono dati da:
$\phi_a = \frac{(2h + 1)\pi}{n - m} \quad \text{per } h = 0, 1, 2, \dots, (n - m - 1)$
## 5. Punti di Diramazione e di Confluenza (Break-away e Break-in)
I punti in cui due o più rami si scontrano e si separano dall'asse reale (o vi ritornano) corrispondono alle radici multiple dell'equazione caratteristica. Si trovano risolvendo:
$$\frac{dk}{ds} = 0 \quad \implies \quad \frac{d}{ds}\left(-\frac{D(s)}{N(s)}\right) = 0 \quad \implies \quad D'(s)N(s) - D(s)N'(s) = 0$$

* Condizione di ammissibilità: Un punto $s^*$ ricavato da questa equazione è un vero punto di diramazione solo se il valore di guadagno corrispondente $k = -rac{D(s^*)}{N(s^*)}$ è **reale e positivo** ($k > 0$).

## 6. Angoli di Partenza e di Arrivo (per Poli/Zeri Complessi)
Se ci sono poli o zeri complessi coniugati, è necessario calcolare l'angolo con cui i rami partono dai poli o arrivano negli zeri.

### Angolo di partenza da un polo complesso $p_k$:
$$	heta_{partenza} = (2h + 1)\pi - \sum_{i 
eq k} ngle(p_k - p_i) + \sum_{j=1}^m ngle(p_k - z_j)$$

### Angolo di arrivo in uno zero complesso $z_k$:
$$	heta_{arrivo} = (2h + 1)\pi + \sum_{i=1}^n ngle(z_k - p_i) - \sum_{j 
eq k} ngle(z_k - z_j)$$

## 7. Intersezione con l'Asse Immaginario ($	ext{Im}(s)$)
Per determinare i punti in cui il luogo taglia l'asse immaginario (soglia di stabilità del sistema), si può procedere in due modi:
1. **Criterio di Routh-Hurwitz:** Si costruisce la tabella di Routh sul polinomio caratteristico $D(s) + kN(s) = 0$. Si trova il valore critico $k_{critico}$ che annulla una riga, e si calcolano le radici dell'equazione ausiliaria.
2. **Sostituzione diretta $s = j\omega$:** Si sostituisce $s = j\omega$ nell'equazione caratteristica:
   $$D(j\omega) + k N(j\omega) = 0$$
   Si separano la parte reale e la parte immaginaria ottenendo un sistema di due equazioni nelle incognite $k$ e $\omega$.

---

## Tabella Riassuntiva delle Regole

| Step | Parametro | Formula / Condizione |
| :--- | :--- | :--- |
| **1** | Punti di partenza | Poli di $L(s)$ (per $k=0$) |
| **2** | Punti di arrivo | Zeri di $L(s)$ (per $k 	o \infty$) |
| **3** | Asse Reale | Numero dispari di poli + zeri a destra |
| **4** | Centro Asintoti | $s_0 = rac{\sum p_i - \sum z_j}{n - m}$ |
| **5** | Angoli Asintoti | $\phi_a = rac{(2h + 1)\pi}{n - m}$ |
| **6** | Diramazioni | $rac{dk}{ds} = 0 \implies D'N - DN' = 0$ |
| **7** | Intersezione Immaginario | Sostituzione $s = j\omega$ o Tabella di Routh |
