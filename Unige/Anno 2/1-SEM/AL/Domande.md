## 1. Come trovare il determinante?
*  Se la matrice è __quadrata__, esso è $|A| = a_{11}a_{22} − a_{12}a_{21}$
*  Se la matrice è __3x3__, esso è $|A| = a_{11} |A_{11}| − a_{12} |A_{12}| + a_{13}  |A_{13}|$
*  In generale, possiamo usare l'espansione di __Laplace__, sia su righe che su colonne
	*  $|A| = \sum^{n}_{j=1}(-1)^{i+j}a_{ij}|A_{ij}|$ 

## 2. Come trovare l'inversa di una matrice?
1. Prima di tutto verifichiamo che il __determinante__ della matrice sia __diverso__ da __0__: $|A| \neq 0$  
*  Abbiamo poi due modi diversi per calcolarla:
	1. Effettuiamo sulla matrice __identica__ tutte le operazioni necessarie a trovare la __totalmente ridotta__ di $A$. il risultato finale è l'inversa
	2. Calcoliamo i __complementi algebrici__ di ogni membro della matrice $c_{ij} = (-1)^{i+j}|A_{ij}|$. Dopo di che otteniamo la __matrice aggiunta__, mettendo questi complementi nella matrice in, __trasponendoli__ $A^∗ = (c_{ij})^T ∈ M_n(K)$. La matrice inversa è quindi l'aggiunta fratto il determinante $A^{-1} = \frac{1}{|A|} \cdot A^*$ 

## 3. Come calcolare il rango?
*  Possiamo agire in due modi diversi:
	1. __Riduciamo__ la matrice e __contiamo__ il numero dei __pivot__: questo corrisponderà al rango della matrice
*  Oppure
	2. Applichiamo il teorema di __Kronecker__. Troviamo un __minore__ di $A$ con __determinante diverso da 0__. Se tutti i __minori__ ottenuti __orlando__ questo minore hanno __determinante nullo__, il __rango__ è uguale all'__ordine__ del __minore__ di partenza

## 4. Come risolvere un sistema lineare?
1. Prima di tutto, verifichiamo che il numero di __incognite__ (colonne) $n$ sia __uguale__ al numero di __righe__ (equazioni) $m$ 
2. Se sono uguali $m = n$,  possiamo applicare il teorema di __Cramer__
	1. $AX = B$ ammette una __sola__ soluzione se e solo se il determinante di $A$ è diverso da 0, $|A| \neq 0$, e la soluzione è $(X = A^{-1}B = \frac{1}{|A|} \cdot A^* \cdot B)$ 
	2. Ogni soluzione $x_i$ sarà uguale al __determinante__ della matrice $A$, a cui abbiamo sostituito alla colonna $i$ il vettore $B$, fratto il __determinante__ della matrice $A$, $x_i = \frac{|A_{C^A_i \leftrightarrow B}|}{|A|}$
3. Se sono diversi, $m \neq n$, possiamo applicare il teorema di __Rouché-Capelli__ e la riduzione di __Gauss__
	1.  Il sistema __ammette__ soluzioni se e solo se il rango della matrice $A$ è uguale a quello della matrice $A$ con aggiunta la colonna $B$  $rk(A) =rk(A|B)$ 
	2. In tal caso, queste __saranno__ $\infty^{n-rk(A)}$. Se $n = rk(A)$, esiste un' unica soluzione
	3. Per trovarle, possiamo __triangolarizzare__ la matrice $A|B$, e calcolarle tramite l'__algoritmo gaussiano__, o con metodi normali

## 5. Vettori???
* Per capire se i vettori in $A$ __generano__ il vettore $b$, deve __esistere__ la __soluzione__ di $AX = b$, e quindi controlliamo che $Rk(A) = Rk(A|B)$ (Rouchè-Capelli) 
* Per capire se un gruppo di vettori sono linearmente __indipendenti__, dobbiamo verificare che il sistema $AX = 0$ abbia come __soluzione__ solo __0__, e quindi una sola soluzione. Il modo per verificarlo è che $Rk(A)= n$ (Rouchè-Capelli), oppure che $|A| \neq 0$ (Cramer) 
* Per capire se i vettori in $A$ sono una __base__, devono essere sia __generatori__ dello spazio richiesto, sia linearmente __indipendenti__
---
* Due vettori sono __paralleli__ se sono __linearmente dipendenti__, ciò vuol dire che hanno la stessa direzione
* Due vettori sono __ortogonali__ (perpendicolari), se il loro __prodotto scalare__ è uguale a __0__. Inoltre, sono __linearmente indipendenti__
---
* Per capire se un vettore è __combinazione lineare__ di altri due possiamo:
	* Risolvere il __sistema__ AX = B, dove B è il vettore e A la matrice formata dai generatori
	* Verificare che __non__ siano __linearmente indipendenti__, e quindi verificare che $|A|B| = 0$, dandole rango non massimo 
