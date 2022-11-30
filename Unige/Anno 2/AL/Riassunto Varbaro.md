# Tipi di Matrici
 * __Nulla__: $M = 0: M = (a_{ji})$ 
 * __Riga__: $(1 \times n)$  
 * __Colonna__: $(m \times 1)$ 
 * __Quadrate__: $m = n$, vengono indicate con $M_n(K)$. Di queste esistono:
	* __Triangolari__: divise in __superiori__ ed __inferiori__, presentano le prime tutti gli elementi sopra la diagonale uguali a 0, i secondi sotto la diagonale
	* __Diagonali__: particolari matrici triangolari in cui sia sopra che sotto la diagonale sono presenti 0
	* __Matrice Identica__: particolare matrice diagonale in cui tutti gli elementi della diagonale sono uguali ad __1__
* __Trasposta__: la matrice $X^T$ ottenuta scambiando le righe con le colonne 
* __A Scalini__: il primo elemento non nullo della riga i + 1-esima si trova più a destra del primo elemento non nullo della riga i-esima. Tali elementi non nulli sono detti __pivot__.
* __Elementari__:
	* $Eij : R_i ↔ R_j$  
	* $Ei(λ): R_i → λR_i$ 
	* $Eij(λ): R_i → R_i + λR_j$

# Riduzione di Gauss

 ![[Gauss.png]]
 
# Invertibilità
* Una matrice è __invertibile__ se e solo se il determinante è __diverso__ da __0__. Il determinante dell'inversa è l'__inverso__ del determinante dell'originale
* Una matrice nilpotente __non__ è invertibile
* Il prodotto di matrici invertibili è invertibile, la sua inversa è:
	*  $(AB)^{-1} = B^{-1} \cdot A^{-1}$ 
* Un modo per __trovare l'inversa__ di $A$ è __effettuare sull'identica__ tutte le __operazioni elementari effettuate__ su $A$ per giungere alla sua __totalmente__ ridotta, riducendo totalmente $A$ otteniamo anche la sua inversa
* Il __complemento algebrico__ di $a_{ij}$ è $c_{ij} = (-1)^{i+j}|A_{ij}|$ 
* La __matrice aggiunta__ è quindi $A^∗ = (c_{ij})^T ∈ M_n(K)$
* Quindi, posso trovare l'__inversa__ come $A^{-1} = \frac{1}{|A|} \cdot A^*$ 

# Sistemi Lineari
* Possiamo __ridurre__ la matrice $A|B$ per ottenere un sistema più semplice da risolvere. 
* Se c'è un __pivot__ nell'__ultima colonna__, __non__ c'è __soluzione__
* Le __soluzioni__ sono normalmente $\infty^{n-p}$, dove $n$ è il numero di __incognite__, $p$ il numero di __pivot__
	* Se $p = n$ esiste un’__unica__ soluzione. 
* Un sistema __omogeneo__ ha sempre una soluzione: 0
* ### Teorema di Cramer
	* Se $m = n,\; AX = B$ ammette una sola soluzione se e solo se $|A| \neq 0$, e la soluzione è ($X = A^{-1}B = \frac{1}{|A|} \cdot A^* \cdot B)$
* Ogni soluzione avrà __forma__ $x_i = \frac{|A_{C^A_i \leftrightarrow B}|}{\det(A)}$ , in cui cambiamo la colonna $i$ di $A$ con $B$ 
* ### Teorema di Rouché-Capelli
	* Il sistema __ammette__ soluzioni se e solo se $rk(A) =rk(A|B)$ 
	* Nel caso ci siano soluzioni, queste __saranno__ $\infty^{n-rk(A)}$ ($n$ è il numero d'incognite)
	* Se il __rango__ di $A$ è __uguale__ al numero di __incognite__ , esiste un __unica soluzione__

# Determinante
* In una matrice __quadrata__, $|A| = a_{11}a_{22} − a_{12}a_{21}$
* In una matrice $A_3$,  $|A| = a_{11} |A_{11}| − a_{12} |A_{12}| + a_{13}  |A_{13}|$
* ### Teorema di Binet
	* $\forall A, B ∈ Mn(K), |A| · |B| = |A · B|$
* Usando il teorema, possiamo __notare__ che: 
	*  $R_i \leftrightarrow R_j$ : il determinante __cambia__ segno
	* $R_i \to \lambda R_j$ : il determinante è __moltiplicato__ per $\lambda$ 
	* $R_i \to R_i + \lambda R_j$ : Il determinante __non cambia__
* In generale:
* ### Espansione di Laplace
	* $A = (a_{ij}) \in M_n(K) \quad \forall i \in [1, n]$ 
	* $|A| = \sum^{n}_{j=1}(-1)^{i+j}a_{ij}|A_{ij}|$ 
* Il __determinante__ di una matrice è __uguale__ al determinante della sua __trasposta__
* Il __determinante__ di $A$ è __uguale__ a $0$ se
	* Una riga o colonna è $0$
	* Due righe o due colonne sono proporzionali
* $A \cdot A^* = |A| \cdot I$ 

# Rango
* Un __minore__ di ordine $r$ è una sottomatrice $r × r$ di $A$ $(ottenuta considerando $r$ righe e $r$ colonne)
* Il __rango__ (o la caratteristica) di $A ∈ M_{mn}(K)$, denotato con $rk(A)$ (o $ρ(A)$) è il massimo ordine di un minore con determinante $\neq$ 0.
* ### Teorema di Kronecker
	* Una matrice $A ∈ M_{mn}(K)$ ha rango $r$ se e solo se: 
		* Esiste un minore $M$ di $A$ di ordine $r$ con determinante $\neq$ 0 
		* Tutti i minori di $A$ di ordine $r + 1$ ottenuti “orlando” $M$ hanno determinante nullo (sono soltanto $(m − r)(n − r)$...)
* Il __rango__ di una matrice __ridotta__ è uguale al __numero__ dei suoi __pivot__
* Eseguire operazioni elementari non cambia il valore del rango

# Vettori
* Un Vettore in $K^n$ è una matrice colonna o riga in $M_{n1}(K)$ 
* Un vettore possiede:
	* __Lunghezza__ o __Norma__: $||v|| = \sqrt{x_1^2 + \cdots + x_n^2}$
	* __Direzione__: Parte per cui passa
	* __Verso__: da dove verso dove
* Operazioni fra vettori:
	* __Somma__: $v + w = \begin{pmatrix} x_1 + y_1 \\ \vdots \\ x_n + y_n \end{pmatrix}$ 
	* __Moltiplicazione__: $\lambda v = \begin{pmatrix} \lambda x_1 \\ \vdots \\ \lambda x_n \end{pmatrix}$  
	* __Prodotto Scalare__: $v \cdot w = \langle v, w \rangle= v^T \cdot w = x_1y_1 + x_2y_2 + \cdots + x_ny_n = ||v|| ||w|| \cos(\widehat{vw})$ 
	* __Proiezione Ortogonale__: $p = \frac{v\cdot w}{||w||^2}w$ 
	* L'__Angolo__ fra i due viene detto $\widehat{vw}$ e:  
		* $v · w = 0 \leftrightarrow v ⊥ w$
		* $v · w > 0 \leftrightarrow \widehat{vw} < \frac{\pi}{2}$ 
		* $v · w < 0 \leftrightarrow \widehat{vw} > \frac{\pi}{2}$ 
	*  __Prodotto Vettoriale__ (In $K^3$)
		* $v \wedge w = \begin{pmatrix} \begin{vmatrix} x_2 && y_2 \\ x_3 && y_3 \end{vmatrix} \\ - \begin{vmatrix} x_1&& y_1 \\ x_3 && y_3 \end{vmatrix} \\ \begin{vmatrix} x_1 && y_1 \\ x_2 && y_2 \end{vmatrix} \end{pmatrix}$
		* $v \perp (v \wedge w) \quad w \perp (v \wedge w)$ 
		* $||v ∧ w|| = ||v|| ||w|| \sin \widehat{vw}$
---
* La __Combinazione Lineare__ di $r$ vettori in $K^n$ a coefficienti $\lambda_1, \cdots, \lambda_r$ è uguale a $\lambda_1v_1 + \lambda_2v_2 + \cdots + \lambda_rv_r$ 
* L'insieme delle possibili combinazioni lineari di più vettori viene chiamato __Spazio Vettoriale__, e scritto come $\langle v_1, \cdots, v_r \rangle$ 
	* Un vettore $w$ __appartiene__ ad uno __spazio vettoriale__ $\langle v_1, \cdots, v_r \rangle$  se e solo se $rk(A) = rk(A | B)$, dove $A = (v_1 \cdots v_r)$ e $B = w$ 
---
* Diciamo che dei vettori sono __Linearmente Dipendenti__, se esistono $\lambda_1, \cdots, \lambda_r$ non tutti nulli tali che la loro __combinazione__ lineare è __uguale a 0__. 
	* Dei vettori sono __linearmente dipendenti__ se uno di essi è __combinazione lineare__ degli altri, e se sono __proporzionali__
* Se ciò __non__ avviene, essi sono __Linearmente Indipendenti__
	* Un gruppo di $r$ vettori sono linearmente indipendenti se la matrice formata da essi ha __rango__ $r$
		* Per verificare ciò, posso anche solo calcolare il determinante di un minore $r \times r$ 
	* Un gruppo di $r$ vettori in $K^n$ con $r > n$ sono __indipendenti__
	* Un gruppo di $n$ vettori in $K^n$ sono __indipendenti__ se il __determinante__ della matrice formata dai vettori è diverso da __0__
---
* Diciamo che $v_1, \cdots, v_r$ sono una __Base__ di $\langle v_1, \cdots, v_r \rangle$ (o di $K^r$) se sono linearmente __indipendenti__
* Esistono __Basi Canoniche__, $n$ vettori fatti con $( 0 ... 0 1 0 ... 0)$ che sono basi di $K^n$ 
* Una base di uno specifico spazio ha sempre lo stesso numero di elementi. Questa è la __Dimensione__ dello spazio
* Una Base viene detta Base __Ortogonale__, se il prodotto $v_i \cdot v_j = 0 \quad \forall i, j$ 
	* A sua volta, una base ortogonale è una base __Ortonormale__ se $v \cdot v = 1 \quad \forall i$ 