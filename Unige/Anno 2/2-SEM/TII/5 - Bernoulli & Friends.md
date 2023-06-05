* Vedremo una specifica variabile aleatoria, ed alcuni suoi derivati
### Bernoulli
* La prima è legata al __lancio delle monete__. Essa possiede due risultati possibili, 0 e 1
* Le probabilità legate ai due casi vengono rappresentate da una variabile $p$:
	* $P(X=0) = 1-p$ 
	* $P(X=1) = p$ 
		* Nel caso di una moneta onesta, $p=\cfrac{1}{2}$ 
* Ricaviamo che:
	* $\mathbb{E}[X] = p$
	* $Var[X] = p\cdot(1-p)$ 
* È interessante notare che, se la moneta è "__onesta__", la varianza è __massima__

### Binomiale
* Qual'è la __distribuzione di probabilità__ dei risultati di __lanciare una moneta $n$ volte?__
* Innanzitutto possiamo ricavarci che, aspettandoci $i$ volte un risultato su $n$, esso avrà una possibilità di avvenire uguale a:
	* $P(X=i) = \binom{n}{i} \cdot p^i \cdot(1-p)^{n - i}$ 
* Sappiamo inoltre che:
	* $\mathbb{E}[X] = n \cdot p$ 
	* $Var(X) = n \cdot p \cdot (1-p)$ 
---
* Se disegnassimo la __PMF__ di questa variabile aleatoria, noteremmo che il grafico assumarebbe la forma di una __campana__, in quanto i casi più comuni si troverebbero sulla zona centrale
* All'aumentare di $n$, il grafico sarebbe __assimilabile__ a quello della cosiddetta __funzione normale o gaussiana__
* Essa viene espressa dalle formule seguenti:
	* $\mu = \mathbb{E}[X]$
	* $v^2 = Var(X)$
		* $\symbfup{f}(x) = - \cfrac{(n - \mu)^2}{2\cdot v^2} = \cfrac{1}{\sqrt{n \cdot p \cdot (1-p)^2} \cdot \sqrt{2 \pi}} \cdot e^{\cfrac{-(x-np)^2}{\frac{n \cdot p \cdot (1-p)}{2}}}$

### Geometrico
* Qual'è la probabilità che mi esca testa al lancio $i$? ( I valori della variabile sono il numero di lanci in  cui esce testa)
	* $P(X=i) = (1-p)^{i-p}\cdot p$ 
	* $\mathbb{E}[X] = \cfrac{1}{p}$
	* $Var(X) = \cfrac{1-p}{p^2}$ 

### Poisson
* Se so che ci sono in media $\mu$ errori in un libro, qual'è la probabilità di trovare $n$ errori?
	* $P(X=n) = e^{-\mu} \cdot \cfrac{\mu^i}{i!}$ 
	* $\mathbb{E}[X] = \mu$ 
	* $Var(X) = \mu$ 