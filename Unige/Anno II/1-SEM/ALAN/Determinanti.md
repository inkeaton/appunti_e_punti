* Il __determinante__ di una matrice è un valore che rappresenta alcune proprietà geometriche ed algebriche di una matrice quadrata
* Il modo in cui calcolarlo varia in base al numero di righe e colonne della matrice:
	* $n = 1 \to A = (a) \quad \to \quad det(A) = a$ 
	* $n = 2 \to A = \begin{pmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \\ \end{pmatrix} \quad \to \quad det(A) = a_{11}a_{22} - a_{12}a_{21}$ 
	* $n = 3 \to A = \begin{pmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \\ \end{pmatrix} \quad \to \quad det(A) = a_{11}det(A_{11}) - a_{12}det(A_{12}) + a_{13}det(A_{13})$
		* $A_{ij}$ è la sottomatrice di $A$ ottenuta cancellando $R_i$ e $C_j$ 
	* $det(I_n) = 1$ 
	* $det(\Delta) = a_{11}a_{22}\cdots a_{nn}$ 
	* $det(E_{ij}) = -1$
	* $det(E_i(\lambda)) = \lambda$
	* $det(E_{ij}(\lambda)) = 1$
		* Possiamo notare che il determinante di tutte le matrici elementari è diverso da 0
* __Teorema di Binèt:__
	* $\forall A, B \in M_n(K), \quad det(A) \cdot det(B) = det(AB)$ 
---
* Usando il teorema di Binèt e le osservazioni precedenti, possiamo dire:
	* $R_i \leftrightarrow R_j$ : il determinante cambia segno
	* $R_i \to \lambda R_j$ : il determinante è moltiplicato per $\lambda$ 
	* $R_i \to R_i + \lambda R_j$ : Il determinante non cambia
* Possiamo notare che e il determinante di A è $\ne$  0 se e solo se il determinante della totalmente ridotta A' è $\ne$  0.
---
* Se una matrice è invertibile, $det(A^{-1}) = \frac{1}{det(A)}$ 
---
* __Espansione di Laplace__
	* Data $A = (a_{ij}) \in M_n(K) \forall i \in [1, 0]$ 
	* $\det(A) = \sum^{n}_{j=1}(-1)^{i+j}a_{ij}A_{ij}$ 
		* L'espansione può essere fatta anche per colonne, semplicemnete scambiamo i e j
* Questo metodo ci permette di calcolare facilmente il determinante, qualunque sia il numero di righe o colonne di una matrice
	* Per ogni matrice abbiamo che : $\det A = \det A^T$ 