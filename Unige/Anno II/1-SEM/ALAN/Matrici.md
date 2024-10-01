* Nel corso di __Algebra Lineare__ impareremo ad utilizzare le matrici, per risolvere sistemi lineari ed imparare il calcolo vettoriale
---
* Una __Matrice__ $m \times n$ in $K$ è: $$A_{m\times n} =
\left[ {\begin{array}{cccc}
a_{11} & a_{12} & \cdots & a_{1n}\\
a_{21} & a_{22} & \cdots & a_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
a_{m1} & a_{m2} & \cdots & a_{mn}\\
\end{array} } \right]$$
  * $m$ è il numero di righe, n il numero di colonne
  * L'insieme delle matrici $m \times n$ ad entrate in $K$ viene denominato come $\color{Apricot} M_{mn}(K)$ 
  
### Matrici Particolari
 * __Nulla__: $M = 0: M = (a_{ji})$ 
 * __Riga__: $(1 \times n)$  
 * __Colonna__: $(m \times 1)$ 
 * __Quadrate__: $m = n$, vengono indicate con $M_n(K)$. Di queste esistono:
	* __Triangolari__: divise in __superiori__ ed __inferiori__, presentano le prime tutti gli elementi sopra la diagonale uguali a 0, i secondi sotto la diagonale
	* __Diagonali__: particolari matrici triangolari in cui sia sopra che sotto la diagonale sono presenti 0
	* __Matrice Identica__: particolare matrice diagonale in cui tutti gli elementi della diagonale sono uguali ad __1__
---
* La __Trasposta__ di una matrice $(m × n)$ è la matrice $(n × m)$ ottenuta scambiando le righe con le colonne
	* $X = (x_{ij}) ∈ M_{mn}(K) \quad → \quad X^T = (y_{ij}) ∈ M_{nm}(K), \quad  y_{ij} = x_{ji}$
* Una matrice quadrata si dice __Simmetrica__ se $A = A^T$ 
---
### Somma
* La matrice __Somma__ di due matrici è definita come:
	* $X + Y = (x_{ij} + y_{ij}) ∈ M_{mn}(K)$
* Si forma quindi il __gruppo__ __commutativo__ $\color{Apricot}(M_{mn}(K), +)$ 
	* L’elemento __neutro__ è la matrice nulla
	* L'__inversa__ di $A$ è la matrice opposta $-A$ 
	* Valgono le proprietà __associativa__ e __commutativa__
* Si può notare che:
	* La __somma__ di due matrici __diagonali__ è __diagonale__. 
	* La __somma__ di due matrici __triangolari__ __superiori__ è __triangolare superiore__
	* La __somma__ di due matrici __triangolari__ __inferiori__ è __triangolare inferiore.__
	* La __somma__ di matrici __simmetriche__ è __simmetrica__, ovvero $(A + B)^T = A^T + B^T$ 
---
### Prodotto
* Il __Prodotto per Scalare__ viene definito come:
	* $\lambda X = (\lambda x_{ij}) \in M_{mn}(K)$ 
* Il __Prodotto Riga per Colonna__ viene invece definito come:

	 $\begin{pmatrix}a_1 & a_2 & \cdots & a_n \end{pmatrix} \cdot \begin{pmatrix}b_1 \\ b_2 \\ \vdots \\ b_n \end{pmatrix} = a_1b_1 + a_2b_2 + \dots + a_nb_n$
* Data una matrice, denotiamo:
	* $R^{A}_i = \begin{pmatrix}a_{i1} & a_{i2} & \cdots & a_{in} \end{pmatrix} \quad \forall i = 1, \dots, m$
	* $C^{A}_j = \begin{pmatrix}b_{1j} \\ b_{2j} \\ \vdots \\ b_{mj} \end{pmatrix}\quad \forall j = 1, \dots, n$
* Il __Prodotto fra Matrici__ viene quindi definito come:
	* $A \cdot B = (c_{ij}) \in M_{mr}, \quad c_{ij} = R^{A}_i \cdot C^{B}_j$ 
* Il prodotto possiede le proprietà __associativa__ e __distributiva__ con la somma
* Forma  $(M_n(K), \cdot)$  __monoide non commutativo__ e $(M_n(K), +,  \cdot)$ __anello unitario__ con la somma
* Si ha che $(A\cdot B)^T = B^T \cdot A^T$ 
* Si può notare che:
	* Il __prodotto__ di due matrici __diagonali__ è __diagonale__
	* Il __prodotto__ di due matrici __triangolari__ __superiori__ è __triangolare superiore__
	* Il __prodotto__ di due matrici __triangolari__ __inferiori__ è __triangolare inferiore__
	* Il __prodotto__ di due matrici __simmetriche__ _non_ è una __simmetrica__
---
* Il prodotto __non__ forma un __gruppo__ in quanto non tutte le matrici sono invertibili
* Una matrice si dice __invertibile__ se esiste una seconda matrice tale che:
	* $A \cdot B = I_n = B \cdot A$ 
* L'inversa è __unica__ e viene definita come $A^{-1}$ 