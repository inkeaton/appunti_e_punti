* Una variabile aleatoria __continua__ è una variabile aleatoria in cui il cui numero di valori possibili è __infinito__
* In essa, la funzione di probabilità di __massa__ si trasforma nella funzione di __densità__ di probabilità
	* $\mathbfup{f}_X : \mathbb{R} \to [0, + \infty)$ 
* Essa rispetta proprietà simili a quelle della $PMF$. Infatti, la sommatoria di tutti i suoi valori è sempre 1. Questo possiamo calcolarlo grazie ad un __integrale__
	* $P(S) = \int \symbf{f}(x) \mathop{dx} = 1$ 
* Infatti, possiamo considerare l'integrale come una __sommatoria__ di tutti i valori di $\symbf{f}(x)$ al variare della $x$ nel dominio. Da questa considerazione, possiamo dedurre le seguenti formule:
	* $B \subseteq \mathbb{R} \quad P(B) = \int_{B} \symbf{f}(x) \mathop{dx}$ 
	* $CDF \quad \symbf{F}(c) = \int^{c}_{-\infty} \symbf{f}(x) \mathop{dx}$ 
	* $\mathbb{E}[X] = \int x \cdot \symbf{f}(x) \mathop{dx}$ 
	* $Var(X) = \int (x - \mathbb{E}[X])^2 \cdot \symbf{f}(x) \mathop{dx} = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$
* È interessante notare che la $PDF$ e la $CDF$ sono l'una la __derivata__ dell'altra
---
* Se modificassimo linearmente la $PDF$, essa varierebbe in modo simile alla $PMF$ 
---
* Vediamo delle distribuzioni di probabilità
### Uniforme
* $\symbf{f}(x)$ viene definita come:
	* $\symbf{f}(x) = \begin{cases} \cfrac{1}{b-a} \quad a \leq x \leq b \\ 0 \qquad \quad altrimenti\end{cases}$ 
* Questa distribuzione si riferisce a casi in cui tutti i casi hanno la stessa probabilità d'avvenire.
* Il grafico appare come una linea dritta, che inizia in $a$ e finisce in $b$, all'altezza $\frac{1}{b-a}$ 
* Valgono:
	* $\symbf{F}(c) = \int^{c}_{a} \symbf{f}(x) \mathop{dx} = \cfrac{c - a}{b - a}$  

### Gaussiana o Normale
* $\symbf{f}(x)$ viene definita come:
	* $\symbf{f}(x) = \cfrac{1}{ \sqrt{2 \pi}\cdot \sigma} \cdot e^{\cfrac{-(x-\mu)^2}{2\sigma^2}}$ 
* Questa funzione, se disegnata, assume la forma di una "campana" simmetrica
* La forma precisa dipende da i due valori $\mu$ e $\sigma$. 
* Questi valori si comportano in modo simile a __media__ e __deviazione__ 
* Essendo molto complessa, studieremo in particolare la cosiddetta Gaussiana Standard
#### Gaussiana Standard
* $\mu = 0$ 
* $\sigma = 1$ 
	* $\symbf{f}(x) = \cfrac{1}{ \sqrt{2 \pi}} \cdot e^{-\cfrac{x^2}{2}}$ 
* Calcolando i valori, possiamo vedere che $\mu = \mathbb{E}[X]$ e $\sigma^2 = Var(X)$ 

### Esponenziale
* $\symbf{f}(x)$ viene definita come:
	* $\symbf{f}(x) = \begin{cases} \lambda \cdot e^{-\lambda\cdot x} \quad x > 0 \\ 0 \qquad \qquad altrimenti\end{cases}$ 
* Questa distribuzione è usata in casi simili a quella di __Poisson__
* Vale:
	* $\symbf{F}(c) = 1 - e^{-\lambda \cdot c}$ 
	* $\mathbb{E}[X] = \cfrac{1}{\lambda}$ 
	* $Var(X) = \cfrac{2}{\lambda^2}$ 