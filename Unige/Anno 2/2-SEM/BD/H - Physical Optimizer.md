* Vediamo nel dettaglio l'ottimizzatore fisico. 
* Come facciamo a trasformare gli LQP ottimi in corrispondenti PQP?
---
* Partiamo considerando i LQP stessi.
* Ogni **nodo** e **foglia** dell'albero dovrà essere trasformato in un **algoritmo**
	* Le foglie serviranno per accedere alle relazioni
	* I nodi interni effettueranno operazioni algebriche
---
* Concentriamoci sull'**accesso** alle **relazioni**
* A seconda dello schema fisico dei dati, potrebbero esistere più **modi** per accedervi, chiamati **cammini d'accesso**
* Di per sé, possiamo effettuare
	* Una **scansione sequenziale**, sempre attuabile
	* Una **selezione**, unita ad un **indice**
* Questi due algoritmi sono
	* **SEQ SCAN** FILTER(A = 5)
	* **INDEX SCAN** (Ir(A), A = 5)
* Entrambi possono fare una selezione, nel nostro caso sull'attributo A
* A se, possono già essere dei PQP
* Nel caso in cui il filtro fosse una **disuguaglianza**, **non** è possibile usare l'INDEX SCAN
* Le condizioni di selezione possono complicarsi, ma è possibile combinare più algoritmi insieme per soddisfarle

* Ora pensiamo al **costo** di questi algoritmi
	* La SEQ SCAN costa il numero di **blocchi** della relazione acceduta
	* L'INDEX SCAN dipende dal tipo di indice, oscillando fra 1 e log n blocchi, unito al costo d'accesso alle tuple localizzate
* Nel caso dell'INDEX SCAN influisce anche la **clusterizzazione** dei dati.
* Un'idea potrebbe essere **ordinare** i puntatori ai blocchi di memoria, **prima** di accedervi. QUesto da vita ad un ulteriore algoritmo, **BITMAP INDEX SCAN**
---
* Vediamo le **operazioni** algebriche
* Ora che stiamo operando su risultati precedenti, operazioni come **selezione** e **proiezione** non possono che essere eseguite tramite **SEQ SCAN**
* Diverso è il discorso sul **JOIN**. Esso non viene mai unito all'accesso ai dati, e può essere eseguito tramite **4 algoritmi**:
	1. **NESTED LOOP JOIN**
		* Può sempre essere eseguito
		* Tramite due loop, si confronta ogni tupla di una relazione con tutte le tuple della seconda
		* **Non molto efficente**, costa $B(R) + T(R) \cdot B(S)$
		* Conveine nel caso in cui la seconda relazione $S$ è relativamente piccola, e tenuta in memoria principale
		* Esiste una variante, il BLOCK NESTED LOOP, che invece di lavorare sulle tuple, lavora sulle pagine. Questo riduce i costi a $B(R) + B(R) \cdot B(S)$
	2. **INDEX NESTED LOOP**
		* Supponiamo di avere un indice sull'attributo di JOIN in $S$
		* Cicliamo su $R$, e per cercare il valore dell'attributo della tupla in $S$ usiamo l'indice
		* Costo: $B(R) + T(R) \cdot AccessoConIndiceSuS$ 
	3. **MERGE JOIN**
		* Se le relazioni sono ordinate, è possibile scorrere su entrambe, in modo simile al mergesort
		* Se non sono ordinate, si può pensare di ordinarle con un ulteriore algoritmo
		* Costo: $B(R) + B(S)$ 
	4. **HASH JOIN**
		* Utilizzabile solo in caso di Equi-JOIN
		* Utilizza una funzione di hash per raggruppare tuple simili
---
* Una volta determinati gli algoritmi, dobbiamo pensare a come fare a **passare** i **risultati intermedi** da nodo a nodo
* Possiamo organizzarci in due modi:
	* **PIPELINING**
		* Ogni tupla viene elaborata indipendentemente
		* Questo permette di passarla, in catena di montaggio, al nodo successivo
		* Per quanto più conveniente, non può essere sempre usato 
	* **MATERIALIZZAZIONE**: 
		* Le tuple vengono tutte elaborate insieme