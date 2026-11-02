## [[1. Semiconduttori#Densità di portatori instrinseci|Densità di portatori intrinseci]]

$$n_{i} = BT^3 \exp\left( -\frac{E_{G}}{kT} \right)$$
In cui $E_{G}$ è l'**energy gap** (energia per rompere il legame), T è la temperatura, B è una costante dipendente dal materiale, k è la costante di Boltzmann.

## [[1. Semiconduttori#Tasso di generazione e di ricombinazione in equilibrio termodinamico|Legge di azione di massa]]

$$n \cdot p = n_{i}^2$$

## [[1. Semiconduttori#Corrente di deriva|Velocità di elettroni e lacune]]

Gli elettroni si spostano con velocità  $v_{n} = -\mu_{n}E$
Le lacune si spostano con velocità $v_{p} = \mu_{p}E$


## [[1. Semiconduttori#Corrente di deriva|Valore correnti di elettroni e lacune]]

$$I_{n}=\frac{-q\cdot n\cdot A\cdot dx}{dt} = -q\cdot n\cdot A\cdot v_{n}$$
$$I_{p}=\frac{q\cdot p\cdot A\cdot dx}{dt} = q\cdot p\cdot A\cdot v_{p}$$

## [[1. Semiconduttori#Corrente di deriva|Densità di elettroni e lacune]]

$$J_{n} = -q\cdot n\cdot v_{n}=q\cdot n\cdot\mu_{n}E$$
$$J_{p} = q\cdot p\cdot v_{p}=q\cdot p\cdot\mu_{p}E$$

## [[1. Semiconduttori#Corrente di deriva|Corrente di deriva]]
$$J_{drift}=q(n\mu_{n}+p\mu_{p})E = J_{n} + J_{p}$$ 
## [[1. Semiconduttori#Corrente di deriva|Resistività del semiconduttore]]

$$\rho=\frac{E}{J_{drift}}=\frac{1}{q(\mu_{n}n+\mu_{p}p)}$$
## [[1. Semiconduttori#Corrente di diffusione|Flusso proporzionale al gradiente di concentrazione]]

$$\phi(x) = -D\frac{dC}{dx}(x)$$
In cui C(x) è la **concentrazione** per unità di volume e D è una **costante di diffusione**.

**Flussi** per elettroni (n) e lacune (p):
$$\begin{array}{l}{{\,\phi_{n}(x)=-D_{n}{\frac{d n}{d x}}}}\\ {{\phi_{p}(x)=-D_{p}{\frac{d p}{d x}}\,\mathrm{{}}}}\end{array}$$

## [[1. Semiconduttori#Corrente di diffusione|Corrente di diffusione]]

Corrente di diffusione di elettroni e lacune:
$$J_{n}^{D I F F}=-q\cdot\Phi_{n}=q D_{n}\frac{d n}{d x}$$ $$J_{p}^{D I F F}=+q\cdot\Phi_{p}=-q D_{p}\frac{d p}{d x}$$
Corrente di diffusione totale:
 $$J_{D I F F}=q D_{n}{\frac{d n}{d x}}-q D_{p}{\frac{d p}{d x}} = J_{p}^{D I F F} + J_{n}^{D I F F}$$

## [[1. Semiconduttori#Corrente di diffusione|Relazione di Einstein]]

Le costanti di diffusione per elettroni e lacune sono legate dalla **relazione di Einstein**.
$$\frac{D_{n}}{\mu_{n}}=\frac{D_{P}}{\mu_{p}}=\frac{kT}{q}=V_{T}$$
In cui $V_{T}$ è il **potenziale termico**.

## [[1. Semiconduttori#Corrente di diffusione|Corrente totale in un semiconduttore]]

$$J_{T O T}=\left(q\mu_{n}n E+q\mu_{p}p E\right)+\left(q D_{n}{\frac{d n}{d x}}\!-q D_{p}{\frac{d p}{d x}}\right)=J_{D E R}+J_{D I F F}$$


## [[1. Semiconduttori#Relazione tra gradienti|Relazione tra gradienti]]
$${\frac{n_{2}}{n_{1}}}={\frac{p_{1}}{p_{2}}}=\exp\left({\frac{v_{2}-v_{1}}{V_{T}}}\right)$$