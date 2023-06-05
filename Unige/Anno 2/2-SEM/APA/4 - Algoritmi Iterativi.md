* La __correttezza__ di un algoritmo __iterativo__ si determina sulla base dei cosiddetti __invarianti di ciclo__, condizioni che rimangono uguali alla fine di ogni ciclo.
* Considerando __pre__ come l'insieme delle condizioni iniziali e __post__ l'insieme delle condizioni finali, un invariante rispetta le seguenti condizioni:
	1. $Pre \to Inv$ 
	2. $Inv \land \neg LoopCondition \to Post$ 
	3.  $Inv \land LoopCondition \to LoopCode$ 
* L'algoritmo si dice quindi __parzialmente__ corretto. Per ritenerlo __totalmente__ corretto, dobbiamo provare che l'algoritmo è in grado di terminare, ovvero può uscire dal ciclo. 
* Per fare ciò, basta trovare la __funzione di terminazione__, un valore delimitato inferiormente che diminuisce ad ogni ciclo, determinandone poi la terminazione
---
* __Esempi__ di algoritmi iterativi che abbiamo visto sono il problema della __bandiera__ __olandese__, e la __ricerca binaria iterativa__