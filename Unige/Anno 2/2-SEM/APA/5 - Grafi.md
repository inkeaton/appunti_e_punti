* Cominciamo ad introdurre i grafi
* Vengono definiti come una coppia di due insiemi:
	* __Nodi__: Oggetti
	* __Archi__: Collegamenti fra più nodi
* Esistono più tipi di grafi:
	* __Orientati__: Nel considerare un arco conta la direzione
	* __Non__ orientati: Nel considerare un arco non conta la direzione
	* __Pesati__: Ogni arco possiede un "peso", una distanza
---
* Il __grado__ $\delta(u)$ di un nodo $u$ è il numero di __archi__ incidenti su di esso, nel caso di grafi orientato possiamo suddividerli in entranti ed uscenti
* Il __numero__ di __archi__ $m$ in un grafo con $n$ nodi è all'incirca:
	* $2m = \sum_{u \in V} \delta(u)$  in grafi non orientati
	* $m = \sum_{u \in V} = \sum_{u \in V} \delta_{out}(u)$ in grafi orientati
* Il numero __massimo__ di archi è:
	* $\frac{n(n+1)}{2} \approx O(n^2)$ in grafi non orientati
	* $n^2$ in grafi orientati
* Un grafo con $n^2$ nodi viene detto __denso__. È abbastanza raro che accada
---
* Un __cammino__ è un insieme di nodi che rappresenta un percorso fra essi
* Un cammino __semplice__ è composto da nodi tutti differenti, con l'eccezione dell'inizio e della fine
* Un __ciclo__ è un cammino che inizia e finisce con lo stesso nodo
* Un grafo viene detto __aciclico__ se qualunque nodo $u$ è raggiungibile da un unico cammino
---
* Un grafo viene detto __connesso__ se esiste un cammino fra ogni nodo
* Un grafo __orientato__ viene detto 
	* __Fortemente__ connesso se esiste un cammino __in ogni direzione__ fra ogni nodo
	* __Debolmente__ connesso se esiste un cammino fra ogni nodo
---
* Un __albero__ libero è un grafo non orientato aciclico connesso ($m = n-1$)
* Un albero __ricoprente__ di un grafo è un __sotto-grafo__ possedente le proprietà di un albero libero
	* Nel caso di grafi pesati, è interessante considerare il minimo albero ricoprente, dotato degli archi con peso minore
---
* Un grafo può essere __rappresentato__ in più modi:
	* Liste di __archi__
	* Liste d'__adiacenza__
	* __Matrici__ d'adiacenza
* Ognuno di essi ha proprietà diverse, e ha costi differenti

 | Operazioni             | Liste d'archi | Liste d'adiacenza           | Matrici d'adiacenza |
 | ---------------------- | ------------- | --------------------------- | ------------------- |
 | Spazio Richiesto       | n + m         | n + m                       | n^2                 |
 | Grado di un nodo       | m             | $\delta(u)$                 | n                   |
 | Calcolo Nodi Adiacenti | m             | $\delta(u)$                 | n                   |
 | Esiste Arco            | m             | $min(\delta(u), \delta(v))$ | 1                   |
 | Aggiungo Arco          | 1             | 1                           | 1                   |
 | Tolgo Arco             | m             | $\delta(u) + \delta(v)$     | 1                   |
 | Aggiungo Nodo          | 1             | 1                           | $n^2$               |
 | Tolgo Nodo             | m             | m                           | $n^2$               |

* Possiamo vedere che le liste d'adiacenza sono convenienti nel caso di visite, le matrici nel caso di modifica degli archi
---
* Esistono più tipi di __visite__
	* Visite a partire da un __nodo__
	* Visite __complete__
* Queste visite possono avvenire in due modi:
	* In __ampiezza__ (Algoritmi iterativi)
	* In __profondità__ (Algoritmi iterativi e ricorsivi)
* Attraverso la visita di un grafo generiamo un albero di ricoprimento
---
* L'algoritmo BFS iterativo stfrutta una __coda__, in cui inserire i nodi. 
* L'algoritmo DFS iterativo sfrutta invece una __pila__. Esso ha complessità __lineare__, se implementato con liste d'__adiacenza__