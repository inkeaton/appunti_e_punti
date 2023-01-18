* Per gestire la memoria nell'HEAP si usano principalmente queste due funzioni:
```
void * malloc(size_t size)  // alloca

void free(void * ptr)       // dealloca
```

* La prima restituise un indirizzo ad un numero di byte, introdotti come parametro. Allo scopo di sapere il numero di byte necessari per un determinato tipo, spesso si usa in congiunzione con la pseudo funzione `sizeof()` la quale restituisce la dimensione di un tipo.
* Invece `free()` libera un gruppo di byte sulla base di un indirizzo, fornitogli da un puntatore
* Entrambe le funzioni vengono dichiarate attraverso dei puntatori a vuoto, puntatori che non sono specifici di un tipo, allo scopo di renderle generiche. Allo scopo di chiarire al compilatore il passaggio di valore da un puntatore void ad uno di tipo specificato, il linguaggio effettua un CAST, dando idealmente un tipo al puntatore void
* ES
	* ```char * p = (char * ) malloc(5)```
* Queste due non sono le uniche funzioni usate per la gestione dell'HEAP:
```
void * calloc(size_t n_memb, size_t size)
```
* `calloc()` viene usata per formare un array. Lo stesso risultato potrebbe essere ottenuto moltiplicando lo spazio necessario per un dato per il numero di elementi dell'array in `malloc()`, ma questa scrittura semplifica il procedimento, e nel caso di array di grandi dimensioni, rassicura eviatndo il pericolo di overflow della moltiplicazione
* A differenza di `malloc()`, `calloc()` inizializza i valori dell'array, azzerandolo. 
```
void * realloc(void * ptr, size_t size)
```

* `realloc()` permette di ridimensionare la dimensione dello spazio associato ad un puntatore, agendo sulla coda. Nel caso lo si stia riducendo, i valori rimossi vengono deallocati dalla funzione stessa
* Il nuovo spazio può essere dato anche ad un differente puntatore
---
### Particolarità
* Se passo puntatore `NULL` a `realloc()` essa si comporta come `malloc()`
* Se passo `size == 0` a `realloc()`, essa si comporta come `free()`
* Posso allocare 0 Byte ad un puntatore con `malloc()`(ricevendo `null`), e liberare questo spazio con `free()` senza errori