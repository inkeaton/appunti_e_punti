* L'espansione può essere compiuta anche su più righe o colonne contemporaneamente
* Il determinante di $A \in M_n(K)$  è 0 se: 
	* Una riga (o una colonna) di A sono 0. 
	* Due righe (o due colonne) di A sono uguali o proporzionali.
---
* Data $A = a_{ij} \in M_n(K)$, il __complemento algebrico__ di $a_{ij}$ è:
	* $c_{ij} = (-1)^{i+j} \det A_{ij}$ 
* La matrice __aggiunta__ $A^*$ è quella formata dai complementi algebrici della matrice $A$ 
* $AA^* = A^*A = \det A I_n \quad \to \quad A^{-1} = \frac{1}{\det A}A^*$  
---
* Un __minore__ di ordine $r$ è una sottomatrice $r \times r$ di di una matrice, (ottenuta considerando r righe e r colonne
* Essendo un minore una Matrice quadrata, ha senso calcolarne il determinante
* Il __Rango__ o caratteristica di $A$, ($rk(A)$), è il massimo ordine di un minore con determinante $\ne$ 0
* Dalla definizione, $A ∈ M_{mn}(K)$ ha rango r se e solo se: 
	* Esiste un minore di A di ordine r con determinante non nullo.
	* Tutti i minori di A di ordine = r + 1 hanno determinante nullo.
* Teorema di __Kronecker__:
* Una matrice $A ∈ M_{mn}(K)$ ha rango r se e solo se: 
	* Esiste un minore M di A di ordine r con determinante non nullo. 
	* Tutti i minori di A di ordine = r + 1 ottenuti “orlando” M hanno determinante nullo (sono soltanto (m − r)(n − r)...)
		* "orlare" significa aggiungere una riga ed una colonna ad un minore in tutti i modi possibili
* In una matrice __ridotta per righe__, il __rango__ corrisponde al __numero di pivot__
* Le operazioni elementari __non cambiano__ il valore del rango, quindi possiamo trovarlo __riducendo__ una matrice, e poi contando il numero di pivot