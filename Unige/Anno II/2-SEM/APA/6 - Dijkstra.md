* Questo algoritmo ha l'obbiettivo di ritrovare i cammini __minimi__ a partire da un nodo in un grafo __pesato__
* L'algoritmo è stato per la prima volta ideato nel 1956, ma studieremo una versione più recente, ottimizzata dall'utilizzo di __heap binari__ per memorizzare i nodi
* Quest'ultimo permette operazioni di modifica economiche, in $\theta(\log{n})$ 
---
* L'idea centrale consiste nel cominciare dando ad ogni nodo, ad eccezione di quello di partenza, distanza __infinita__
* Dopo di che, selezioniamo nell'heap il nodo con distanza __minore__ (All'inizio il primo). Guardo i nodi ad esso adiacente ed __aggiorno__ le distanze, dopo di che lo __rimuovo__ dall'heap
* Nei cicli seguenti, se dovessi trovare distanze __minori__, tramite altri nodi, __aggiorno__ le distanze
* Avrò alla fine le __distanze minime__
---
* Allo scopo di garantire la __correttezza__ dell'algoritmo, è necessario che tutti i __pesi__ del grafo siano __positivi__
---
* Ha complessità $\Theta ((m+n)\log{n})$ 