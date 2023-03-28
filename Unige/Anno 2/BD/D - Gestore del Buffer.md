* Le componenti principali del gestore delle strutture di memorizzazione sono due:
	* Gestore dei __File__
	* Gestore del __Buffer__
* Quest'ultimo è molto importante allo scopo di ottimizzare le richieste
---
* Per accedere ad un file, il DBMS lavora in modo simile al SO: Possiede un __buffer__ in memoria RAM (detta __Main Memory__) in cui vengono ricopiati i blocchi di dati da elaborare
* Questo buffer viene gestito con tecniche simili a quelle necessarie all'ottimizzazione di una memoria __cache__. Interessante è la politica di __rimpiazzamento__ utilizzata
* Infatti, mentre normalmente potremmo preferire l'algoritmo __LRU__, il DBMS è capace di scegliere __differenti algoritmi__ a seconda della situazione. A differenza di un SO, abbiamo __maggiore__ __coscienza__ di cosa sono i __dati__ che manipoliamo, e quindi quali potrebbe esser meglio conservare nel buffer
* In alcuni casi, viene addirittura scelto l'__MRU__
	* In generale, possiamo dire che ad influire sulle __prestazioni__ sono la __dimensione__ del buffer e la __politica__ di rimpiazzamento scelta
---
* Ritornando ai nostri __file__, essi potrebbero essere __organizzati internamente__ in più modi:
	* __Heap__: senza un particolare ordine
	* __Ordinati__: secondo un attributo
	* __Hash__: in gruppi di attributi simili
* Nell'attuazione delle visite sembra __inevitabile__ trovarsi a leggere __blocchi non necessari__, in quanto è impossibile sapere a priori la posizione esatta dei nostri dati. Questo però ci __rallenta__
* A tal scopo vengono introdotte le __strutture ausiliarie d'accesso__ o __indici__, file contenenti coppie di attributi, detti __chiavi__, e __puntatori__ alle tuple contenenti questi attributi
* Questi file risulteranno di __dimensioni__ molto __minori__. Se scorressimo su di essi per cercare i dati richiesti, dovremmo caricare __molti meno blocchi inutili__