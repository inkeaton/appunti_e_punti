* Molto speso può risultare utile trovare un __albero minimo ricoprente__ di un grafo, ovvero un sottografo connesso, aciclico e ricoprente
* Esistono __due__ algoritmi principali:
	* Algoritmo di __Prim__:
		* L'idea principale è molto __simile al Dijkstra__. Ad ogni ciclo salviamo le distanze minori del nodo che analizziamo, fino a svuotare l'heap
		* Ha complessità __equivalente__ a Dijkstra
	* Algoritmo di __Kuskal__:
		* L'idea consiste nello scorrere una lista contenente tutti gli __archi__ del grafo. A ogni ciclo, consideriamo gli archi minori, e nel caso escano archi maggiori, non li consideriamo
		* Nonostante la maggior semplicità, può avere un __costo molto grande__, a seconda del controllo di connessione fra due nodi
		* Questo si può __risolvere__ tramite le __Union-Find__
---
* Gli Union-Find sono strutture utilizzate nel caso di un universo composto da __sottoinsiemi__
* Possiamo eseguire tre operazioni su di essi:
	* __Mkset__ 
	* __Find__
	* __Union__
* Vengono solitamente implementate come __alberi n-ari__, in due modi differenti:
	* __QuickFind__
		* Gli alberi utilizzati sono tutti unari. Questo permette di __trovare facilmente__ ogni nodo richiesto, in tempo 1, ma ci metteremo __n__ per eseguire la __Union__,in quanto dovremo riorganizzare l'albero
	* __QuickUnion__
		* Gli alberi hanno struttura normale. L'__unione__ avverrà __semplicemente__ mettendo la radice di un albero come radice del secondo, in $O(1)$ , ma la __find__ potrà __peggiorare__ in $O(n)$ 
---
* Per il nostro scopo ci __converrebbe__ utilizzare il __secondo__ paradigma, ma sarebbe comunque __fastidioso__ dover peggiorare la ricerca. 
* A tal scopo possiamo cambiare il modo in cui facciamo la Union così da rendere gli alberi __bilanciati__, e rendere la complessità della find __logaritmica__
* Possiamo fare:
	* Union By __Size__: L'albero con più nodi rimane radice
	* Union By __Rank__: L'albero più alto rimane radice
* Un'ulteriore metodo è la __Path Compression__: Nel compiere la find e la union ogni volta che attraversiamo un nodo, lo __stacchiamo__ e __attacchiamo__ alla __radice__, a meno che non lo sia già
* In questo modo l'__altezza__ __diminuisce__, e diminuisce la __complessità ammortizzata__, ovvero la complessità totale di una sequenza di operazioni
---
* Tramite tutte queste __ottimizzazioni__, l'algoritmo ottiene una __complessità__ totale di:
	* $O((m+n)\log^*{n}) \approx O(n+m)$ 
* La funzione $\log^*$ è una funzione reminescente del logaritmo, la quale cresce molto lentamente, stabilizzandosi già intorno a $\log^*{4}$ 