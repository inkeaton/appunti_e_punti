* Consideriamo insieme due VA __discrete__
* La loro __PMF congiunta__ è:
	* $\sum^{n}_{i=1}\sum^{m}_{j=1} P(i, j) = 1$ 
* Possiamo calcolare le probabilità delle singole VA, a partire dai valori della PMF Congiunta
* Queste sono le __marginalità__
	* $P_X(i) = \sum^{m}_{k=1} P(i, k)$ 
* La __CDF congiunta__ ha forma:
	* $F_{(X, Y)}(a, b) = \sum_{X_i<a}\sum_{Y_j<b} P(i, j)$ 
* Si può anche calcolare la __CDF della marginale__
	* $F_{X}(a) = \sum_{X_i<a}\sum^{m}_{j=1} P_X(i, j)$ 
---
* Questi concetti sono applicabili anche nel campo delle VA continue, ma sarebbero necessari concetti matematici, quali gli integrali doppi, che non sappiamo ancora usare
---
* Due VA sono dette __indipendenti__ se valgono le seguenti uguaglianze:
	* $P(X \in A, Y \in B) = P(X \in A) \cdot P(X \in B)$ 
	* $F_{(X, Y)}(a, b) = F_{X}(a) \cdot F_{Y}(b)$ 
* Sappiamo che vale
	* $\mathbb{E}[X + Y] = \mathbb{E}[X] + \mathbb{E}[Y]$ 
	* $\mathbb{E}[X \cdot Y] = \mathbb{E}[X] \cdot \mathbb{E}[Y]$        <-- Solo se le due __VA__ sono __indipendenti__ 
* Da quest'ultima proprietà possiamo ottenere due numeri capaci di __quantificare la dipendenza__ di due VA:
	* La __Covarianza__
		* $Cov(X, Y) = \mathbb{E}[X \cdot Y] - \mathbb{E}[X] \cdot \mathbb{E}[Y]$ 
			* Vale che $Cov(a\cdot X, b \cdot Y) = a \cdot b \cdot Cov (X, Y)$ 
	* La __Correlazione__ (Versione __normalizzata__ della Covarianza)
		* $\rho(X, Y) = \cfrac{Cov(X, Y)}{\sqrt{Var(X)} \cdot \sqrt{Var(Y)}}$ 
		* È sempre vero che $-1 \leq \rho(X, Y) \leq 1$ 
---
* __Varianza__ di una __somma__ di VA
	* $Var(X + Y) = Var(X) + Var(Y) + 2 \cdot Cov(X, Y)$ 
	* Si nota che, se le variabili sono indipendenti, $Cov(X, Y) = 0$ 
* Lo stesso discorso vale all'aumentare delle variabili sommate
* __Varianza__ di una __somma__ di VA __indipendenti__
	* $Var(\sum^{N}_{i=1} X_i) = \sum^{N}_{i=1} Var(X_i)$ 