* Consiste nell'__ordinare__ i __nodi__ di un __grafo aciclico ordinato__ a partire dal nodo sorgente, sulla base dell'__ordine degli archi__
* Esiste sempre almeno un ordine topologico
---
* Esistono più __algoritmi__ per risolvere questo __problema__
* Il __primo__ che potremmo pensare si basa sulla seguente idea:
	* A ogni giro, __prendiamo__ un nodo __sorgente__, e lo mettiamo nella __lista__
	* __Abbassiamo__ di uno il numero di __nodi entranti__ in tutti i suoi nodi "figli"
	* Al ciclo successivo, dovrebbe esserci almeno un __nuovo__ nodo __sorgente__, e ripartiamo da lì
* Alla fine ha all'incirca la __complessità__ di una comune __visita__
---
* Un __secondo__ algoritmo si basa sull'utilizzo di una __visita di profondità con timestamp__
	* Effettuo una visita __DFS__, ma su ogni nodo che visito lascio un __numero__, che indica il momento in cui l'ho visitato
	* Quando finisco di visitare i figli del nodo, aggiungo un __secondo timestamp__ su di esso
	* Aggiungendo i nodi nella __lista__ secondo l'__ordine dei timestamp__ dovrebbe fornirci una lista ordinata dei nodi
* Alla fine ha anche esso all'incirca la __complessità__ di una comune __visita__
---
* Dato un grafo G orientato, come facciamo a trovare le __componenti fortemente connesse__ (CFC) ?
	* Una CFC è un sottografo formato da nodi mutualmente raggiungibili
---
* L'algoritmo per risolverlo ritornerà un __grafo quoziente__, ovvero una lista di nodi in cui ogni nodo è un CFC. Possiamo considerarlo una __generalizzazione__ dell'__ordinamento topologico__
	* Inizialmente ottengo un ordinamento topologico del grafo tramite __DFS__ con Timestamp
	* Ottengo una __copia trasposta__ del grafo, e comincio una __DFS__ del grafo a partire dal nodo con timestamp maggiore fino ad arrivare al nodo di partenza, Questo __cammino__ sarà una CFC e, una volta salvata, rimuoveremo questi nodi dal grafo
	* Ripetiamo fino all'__esaurimento__ dei nodi
* Anche questo algoritmo rimane in $O(n+m)$ 