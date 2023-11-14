* Nonostante l'ovvia ottimizzazione alle letture, l'utilizzo di indici comporta un __peggioramento__ delle operazioni di __aggiunta__, __rimozione__ o __modifica__ di elementi od attributi della relazione
---
* Gli __indici__ possono essere
	* __Primari__: L'indice si basa su un attributo chiave candidata
	* __Secondari__: L'indice non si basa su un attributo chiave candidata
* Essi possono essere __implementati__ in due modi:
	* Indici __Ordinati__: Fisicamente memorizzati in memoria, ordinati secondo un criterio
	* Indici __Heap__: I valori vengono calcolati tramite una funzione di hash
---
* Gli indici di tipo ordinato sono solitamente implementati tramite __strutture ad albero__, su disco, le quali rispettano le seguenti __proprietà__:
	* __Bilanciati__, rispetto al numero di blocchi usati
	* __Occupazione minima__, ovvero ogni blocco usato contiene una quantità minima di dati, così da non sprecare letture di memoria
	* __Aggiornabili__ in modo efficente
---
* Una struttura che implementa queste proprietà è il __B+Tree__
* È una struttura reminescente dei __BST__, funzionante secondo i seguenti __criteri__:
	* Ogni __nodo__ che compone l'albero è un __blocco__ di memoria, che può contenere multipli elementi
	* Le __operazioni__ di ricerca, inserimento, e cancellazione sono in __complessità__ relativa all'__altezza dell'albero__, ovvero $O(\log N)$, ove $N$ corrisponde al numero di blocchi usati
	* Ogni blocco contiene __minimo__ $m - 1$ elementi, al __massimo__ $\cfrac{m}{2} -1$. In essi $m$ corrisponde all'__ordine__ dell'albero, un valore collegato alle __dimensioni__ di un blocco 
	* Ogni nodo __non-foglia__ con $j$ elementi possiederà $j - 1$ figli, ognuno riferendosi ad un range fra i valori del padre
	* I nodi __foglia__ saranno i blocchi contenenti i veri valori. Ad ogni valore sarà associato un __puntatore__ all'__oggetto__ nella struttura dati. Inoltre, ogni foglia è collegata alle altre foglie
		* Questo permette di __scorrere facilmente__ negli indici, nel caso siano richiesti dei range
		* Nel caso di indici __secondari__, verrà aggiunto un __ulteriore__ blocco contenente i __puntatori__ ad i vari valori che condividono quella chiave
	* Nel caso dell'__aggiunta__ di un dato ad albero pieno, sarà necessaria un operazione di split o di ribilanciamento, relativamente __costosa__
---
* Una variante del B+Tree è il __Btree__, il quale non conserva i dati nei blocchi foglia, ma nei blocchi-nodi stessi
	* Questo __ottimizza__ le __ricerche__ singole e l'occupazione della __memoria__
	* __Peggiora__ però le __ricerche in un range__
---
* Un __indice__ ad albero si dice
	* __Clusterizzato__: Se il database a cui si riferisce è __ordinato__ secondo il suo attributo
	* __Non-Clusterizzato__: 
* La presenza di un indice clusterizzato __facilita__ notevolmente le __operazioni__ sul file
---
* L'indice può anche essere __multiattributo__, ovvero utilizzare più chiavi di ricerca
* I nodi foglia verranno organizzati in maniere più __complesse__, favorendo le ricerche di un solo attributo