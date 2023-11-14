# Esecuzione di codice

* Proviamo a vedere cosa succede fisicamente quando eseguiamo un semplice programma in C
* Prendiamo per esempio una funzione capace di trovare il valore più alto di un array
```
char findmax(int dim, char array[dim]) {
	char max;
	if(dim <= 0) exit(1);
	max = array[--dim];
	while(dim) {
		if(max < array[--dim]) max = array[dim];
	}
	return max;
}

```
* Ora cerchiamo di capire come queste righe vengono identificate dal compilatore
* Nello stack verranno memorizzate le tre variabili dichiarate, in particolare i parametri si troveranno in una zona di confine fra le variabili del programma chiamante e quelle della funzione, mentre `max` si troverà nella zona della funzione
* L'array vero e proprio potrebbe essere conservato nello STACK, nell'HEAP o nella sezione DATI STATICI, dipende da come è stato creato nel programma
---
* Possiamo notare che nell'esecuzione del codice saranno eseguiti numerosi cicli while, a seconda del numero di elementi presenti nell'array
* La CPU quindi richiederà nel tempo gli indirizzi di tutti gli elementi dell'array, e richiederà più volte gli indirizzi di `dim` e di `max`.
* E' stato dimostrato che questo comportamento non è un caso, ma una proprietà dei programmi,in particolare queste due proprietà, le proprietà di **LOCALITA'**:
	* LOCALITA' nel TEMPO:
		* Se il processore richiede l'indirizzo i, è molto probabile che questo venga nuovamente richiesto in futuro
	* LOCALITA' nello SPAZIO
		* Se il processore richiede l'indirizzo j, è molto probabile che richieda in futuro l'indirizzo j +1, j + 2, etc.
---
* Queste proprietà possono essere utilizzate per ottimizzare la velocità del processore
* Ad esempio, sapendo che mi troverò spesso a utilizzare gli stessi indirizzi, o indirizzi presenti nella stessa pagina, posso pensare di utilizzare una TLB di dimensioni minori, senza influire in alcun modo sulle prestazioni del computer, e riparmiando
# Cache
* Il nome viene dal francese *cacher*, nascondere, questo perchè questo dispositivo non deve agire sul funzionamento della CPU, ma solo sulla velocità di esecuzione dei programmi
* Essa si tratta di una memoria RAM associativa di tipo statico, di dimensioni minori rispetto alla RAM
* Questa potrà essere utilizzata dalla CPU qualora la RAM fosse nel mezzo della procedura di REFRESH, così da evitare rallentamenti dovuti alla memoria
* Nonostante le dimensioni minori, essa sarà capace di contenere i dati necessari, grazie alle già citate proprietà di località
---
* Uno dei modi in cui realizzarne una è una **Struttura Completamente Associativa**
	* La sezione dati di ogni cella della CACHE conterrà più di un dato. Questo perchè per via della proprietà di località nello spazio, i dati successivi a quello richiesto saranno richiesti a breve. In questo modo li carichiamo già, in un singolo ciclo di CLOCK
	* Il numero di dati immagazzinati in una cella sarà $2^N$. Questo perchè in questo modo potremo segnare nella sezione tag solo i bit meno più significativi, in comune a tutte le celle. Inoltre nel tag saranno riservati bit per identificare il dato richiesto e per indicare la dimensione delle celle
* Una cella sarà chiamata una LINEA
* Idealmente vorremmo avere + celle possibili, sulla base del budget, più piccole, così da copiare i dati da RAM a CACHE in meno cicli di CLOCK possibile