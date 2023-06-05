* Una __variabile aleatoria__ è una __funzione__ che, partendo dallo __spazio campionario__, ci ritorna un __valore numerico__
* Inizieremo studiando le cosiddette __variabili aleatorie discrete__, le quali possiedono un numero __finito__ di risultati
---
* Ogni __possibile valore__ di una variabile aleatoria possiede una __probabilità associata__
* Queste possono essere __rappresentate__ tramite delle __distribuzioni di probabilità__:
	* La __funzione probabilità di massa__ (PMF), la quale associa ad ogni valore la sua probabilità
	* La __funzione probabilità cumulata__ (CDF), la quale associa ad ogni valore la sua probabilità sommata alle probabilità dei casi precedenti. 
		* Assume la forma di una __funzione a gradini__, non decrescente
* Potremmo però __riassumere__ i disparati __valori__ di una variabile aleatoria in un __unico__ numero? Certo, tramite una __media__. Dovremo però tener conto del diverso __peso__ di ogni valore, in base alla __probabilità__ che esso avvenga. 
* Calcoliamo quindi il __valor medio__ di una variabile aleatoria $X$, dotata di $N$ valori $n$ come:
	* $\mathbb{E}[X] = \sum^{N}_{i=1}  n_i \cdot P(n_i)$ 
* Valgono le seguenti proprietà:
	* $\mathbb{E}[aX-b] = a \cdot \mathbb{E}[X] -b$ 
---
* A seconda dei valori, la __media__ può essere __più o meno rappresentativa__ dei valori reali.
* A tal scopo introduciamo un secondo numero, la __varianza__, la quale indica la __distanza media__ dal valor medio:
	* $Var(X) = \sum^{N}_{i=1} (n_i - \mathbb{E}[X])^2 \cdot P(n_i) = \mathbb{E}[(X - \mathbb{E}[X])^2]$ 
	* La sua radice assume il nome di __deviazione standard__
* Valgono le seguenti proprietà:
	*  $Var(aX -b) = a^2 \cdot Var(X)$ 
	*  $Var(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2$ 