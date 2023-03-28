* La programmazione dinamica è un __paradigma__ di programmazione, come il divide-et-impera
* Essa si basa sul partire da problemi __piccoli__ e, risolvendoli, arrivare a risolvere problemi più __grandi__ (__bottom-up__). Nel mentre le soluzioni ritrovate possono venire __memorizzate__, in modo da poter essere __riutilizzate__ in seguito
---
* Un esempio di problema risolto tramite programmazione dinamica è LCS, il ritrovare la sottosequenza più grande in comune tra due sequenze
* L'algoritmo dinamico riduce in sottoproblemi in cui dobbiamo controllare su i elementi della prima sequenza e j della seconda
* Definizione induttiva
	* Caso Base
		* Se una delle sue sequenze è 0, ritorniamo 0
	* Passo Induttivo
		* Se i caratteri in posizione i e j sono uguali, concateniamo a LCS(i-1, j-1)
		* Se sono diversi, prendiamo $max(LCS(i-1,j), LCS(i, j-1))$ 
* Questo algoritmo può essre implementato in __divide-et-impera__ con complessità __esponenziale__, o in modo __dinamico__ con complessità __quadratica__
	* Useremo una __matrice__ per contenere i risultati dei sottoproblemi
---
* Un altro problema consiste nel calcolo di tutti i cammini minimi possibili in un grafo pesato orientato
* Questo problema viene risolto grazie all'algoritmo di __Floyd-Warshall__
* L'idea alla base è dividere in sottoproblemi scritti come "qual'è il peso minimo di un cammino da X a Y che usa come nodi quelli da 1 a K?" (Cammini K-Vincolati)
* Definizione Induttiva
	* Caso Base
		* In questo caso, K=0
		* Se X=Y, il cammino è 0
		* Se X $\neq$ Y il cammino è lungo quanto il cammino fra X e Y. Se non esiste, è $\infty$ 
	* Passo Induttivo
		* Usiamo K = K +1
		* Se il cammino non usa K, allora è uguale a $d^K(X,Y)$ 
		* Altrimenti è $d^K(X,K+1) + d^K(K+1,Y)$ 
* La __complessità__ finale dell'algoritmo è __cubica__