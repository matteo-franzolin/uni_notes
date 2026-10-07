
Dato il seguente sistema dinamico non lineare:
$$
\begin{cases}
\dot{x}_1(t) = x_2(t) + x_1(t)u(t) \\
\dot{x}_2(t) = -x_1(t) + x_2^2(t)
\end{cases}
$$

---

## 📌 1. Ricerca degli Stati di Equilibrio
Per calcolare gli stati di equilibrio, poniamo le derivate temporali pari a zero ($\dot{x}_1 = 0$, $\dot{x}_2 = 0$):
$$
\begin{cases}
0 = \bar{x}_2 + \bar{x}_1\bar{u} \\
0 = -\bar{x}_1 + \bar{x}_2^2
\end{cases}
$$
*(Abbiamo un sistema di 2 equazioni in 3 incognite: $\bar{x}_1, \bar{x}_2, \bar{u}$)*

### 🔹 Caso A: Fissato un ingresso costante $\bar{u} = 1$
Sostituendo $\bar{u} = 1$ nel sistema delle relazioni di equilibrio si ottiene:
$$
\begin{cases}
0 = \bar{x}_2 + \bar{x}_1 \\
0 = -\bar{x}_1 + \bar{x}_2^2
\end{cases}
$$

Dalla prima equazione ricaviamo:
$$\bar{x}_2 = -\bar{x}_1$$

Sostituendo nella seconda equazione:
$$-\bar{x}_1 + (-\bar{x}_1)^2 = 0 \implies -\bar{x}_1 + \bar{x}_1^2 = 0 \implies \bar{x}_1(\bar{x}_1 - 1) = 0$$

Otteniamo quindi due soluzioni distinte per $\bar{x}_1$:
1. Se $\bar{x}_1 = 0 \implies \bar{x}_2 = 0$
2. Se $\bar{x}_1 = 1 \implies \bar{x}_2 = -1$

Si individuano così i primi due punti di equilibrio:
* **Punto di Equilibrio 1:** $E_{p,1} = (\bar{x}_1, \bar{x}_2, \bar{u}) = (0, 0, 1)$
* **Punto di Equilibrio 2:** $E_{l,2} = (\bar{x}_1, \bar{x}_2, \bar{u}) = (1, -1, 1)$

---

### 🔹 Caso B: Fissato un ingresso costante $\bar{u} = 4$
Sostituendo $\bar{u} = 4$ nel sistema delle relazioni di equilibrio si ottiene:
$$
\begin{cases}
0 = \bar{x}_2 + 4\bar{x}_1 \implies \bar{x}_1 = -\frac{\bar{x}_2}{4} \\
0 = -\bar{x}_1 + \bar{x}_2^2
\end{cases}
$$

Sostituendo $\bar{x}_1$ nella seconda equazione:
$$\bar{x}_2^2 - \left(-\frac{\bar{x}_2}{4}\right) = 0 \implies \bar{x}_2^2 + \frac{\bar{x}_2}{4} = 0 \implies \bar{x}_2\left(\bar{x}_2 + \frac{1}{4}\right) = 0$$

Otteniamo due soluzioni per $\bar{x}_2$:
1. Se $\bar{x}_2 = 0 \implies \bar{x}_1 = 0$
2. Se $\bar{x}_2 = -1/4 \implies \bar{x}_1 = -(-1/4)/4 = 1/16$

Si individuano ulteriori punti di equilibrio:
* **Punto di Equilibrio 3:** $E_{p,3} = (0, 0, 4)$
* **Punto di Equilibrio 4:** $E_{p,4} = (1/16, -1/4, 4)$

---

### 🔹 Caso C: Fissato un ingresso costante $\bar{u} = -4$
Sostituendo $\bar{u} = -4$ nel sistema delle relazioni di equilibrio si ottiene:
$$
\begin{cases}
0 = \bar{x}_2 - 4\bar{x}_1 \\
0 = -\bar{x}_1 + \bar{x}_2^2 \implies \bar{x}_1 = \bar{x}_2^2
\end{cases}
$$

Sostituendo nella prima equazione:
$$\bar{x}_2 - 4\bar{x}_2^2 = 0 \implies \bar{x}_2(1 - 4\bar{x}_2) = 0$$

Otteniamo due soluzioni per $\bar{x}_2$:
1. Se $\bar{x}_2 = 0 \implies \bar{x}_1 = 0$
2. Se $\bar{x}_2 = 1/4 \implies \bar{x}_1 = (1/4)^2 = 1/16$

Si individuano gli ultimi punti di equilibrio:
* **Punto di Equilibrio 5:** $E_{p,5} = (0, 0, -4)$
* **Punto di Equilibrio 6:** $E_{p,6} = (1/16, 1/4, -4)$

---

## 🛠️ 2. Linearizzazione nell'intorno dell'equilibrio $E_{l,2} = (1, -1, 1)$

Consideriamo le funzioni non lineari del sistema:
$$f_1(x_1, x_2, u) = x_2 + x_1 u$$
$$f_2(x_1, x_2, u) = -x_1 + x_2^2$$

Definiamo le variabili alle variazioni (scostamenti rispetto al punto di equilibrio):
$$\tilde{x}_1 = x_1 - \bar{x}_1 = x_1 - 1$$
$$\tilde{x}_2 = x_2 - \bar{x}_2 = x_2 + 1$$
$$\tilde{u} = u - \bar{u} = u - 1$$

Il sistema linearizzato assume la forma standard:
$$
\begin{bmatrix} \dot{\tilde{x}}_1 \\ \dot{\tilde{x}}_2 \end{bmatrix} = A \begin{bmatrix} \tilde{x}_1 \\ \tilde{x}_2 \end{bmatrix} + B \tilde{u}
$$

### Calcolo della Matrice delle Dinamiche $A$ (Matrice Jacobiana rispetto allo stato)
$$
A = \begin{bmatrix} \frac{\partial f_1}{\partial x_1} & \frac{\partial f_1}{\partial x_2} \\ \frac{\partial f_2}{\partial x_1} & \frac{\partial f_2}{\partial x_2} \end{bmatrix}_{E_{l,2}} = \begin{bmatrix} u & 1 \\ -1 & 2x_2 \end{bmatrix}_{(1, -1, 1)} = \begin{bmatrix} 1 & 1 \\ -1 & -2 \end{bmatrix}
$$

### Calcolo della Matrice degli Ingressi $B$ (Matrice Jacobiana rispetto all'ingresso)
$$
B = \begin{bmatrix} \frac{\partial f_1}{\partial u} \\ \frac{\partial f_2}{\partial u} \end{bmatrix}_{E_{l,2}} = \begin{bmatrix} x_1 \\ 0 \end{bmatrix}_{(1, -1, 1)} = \begin{bmatrix} 1 \\ 0 \end{bmatrix}
$$

### Modello Lineare alle Variazioni Conclusivo
Il sistema linearizzato nell'intorno del punto di equilibrio scelto è governato dalle seguenti equazioni differenziali lineari:
$$
\begin{cases}
\dot{\tilde{x}}_1(t) = \tilde{x}_1(t) + \tilde{x}_2(t) + \tilde{u}(t) \\
\dot{\tilde{x}}_2(t) = -\tilde{x}_1(t) - 2\tilde{x}_2(t)
\end{cases}
$$