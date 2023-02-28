* Un __Problema__ viene descritto, in modo formale, come una relazione $P$ su $I \times S$, dove $I$ è l'insieme degli input, e $S$ l'insieme delle soluzioni
	* $\forall i \in I \; \exists s \in S$, soluzione o insieme di soluzioni che si vogliono ottenere
* Come troviamo queste soluzioni? Tramite gli __Algoritmi__!
* Un Algoritmo è un __procedimento di calcolo meccanico__, atto allo scopo di risolvere una problema, descritto in modo preciso e disambiguo
	* In termini formali, è una funzione che risolve $P$, dando per ogni $i$ un $s$ 
---
* Possiamo analizzare due componenti di un algoritmo, la sua __correttezza__ e la sua __complessità__
---
* La correttezza indica che $\forall i \in I, \; A(i)$ è __soluzione__ di $P$
* Come possiamo verificarlo?
	* Per algoritmi __ricorsivi__ possiamo sfruttare il principio d'__induzione__
	* Per algoritmi __iterativi__, gli __invarianti__ di ciclo
---
* La complessità indica il __tempo__ necessario affinchè si ritrovi la soluzione. Esso varia in base al numero di valori in input
* Un modo per indicarla è tramite il paragone con alcune funzioni elementari, caratterizzate da comportamento __asintotico__
* In ordine di complessità, abbiamo:
	* $\log n$    -> logaritmica
	* $n^{\frac{1}{2}}$       -> radice quadrata
	* $n$         -> lineare
	* $n \log n$ -> pseudo lineare
	* $n^2$        -> quadratica
	* $n^3$        -> cubica
	* $2^{n}$        -> esponenziale
	* $n^{n}$        
* Per indicare il __rapporto__ fra la complessità del nostro __algoritmo__ e queste __funzioni__ elementari, in funzione del numero di valori in input $n$ useremo i seguenti __operatori__:
	* $O(f(n))$ -> La complessità cresce __non più__ di un funzione $f$
	* $\Omega(f(n))$ -> La complessità cresce __non meno__ di una funzione $f$
	* $\Theta(f(n))$ -> La complessità cresce __come__ la funzione $f$
* Diremo che un algoritmo è __trattabile__ se $A \in O(n^3)$, __intrattabile__ se $A \in \Omega(2^n)$. Cercheremo sempre di usare algoritmi trattabili
---
* Purtroppo la complessità __non__ dipende __solo__ dalla __dimensione__ dell'input, ma anche dai valori __specifici__
* Per questo dovremo considerare la complessità in tre casi separati: 
	* Caso __migliore__
	* Caso __peggiore__
	* Caso __medio__
* La complessità di quest'ultimo verrà calcolata tramite una media __pesata__, considerando le probabilità di avvenimento dei diversi casi
	* Solitamente ci __interesseremo__ del caso __peggiore__, in quanto ci da la garanzia che l'algoritmo non può "andar peggio" di così