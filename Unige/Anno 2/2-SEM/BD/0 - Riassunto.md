+ In questo foglio, riassumeremo i concetti principali del corso di Basi di Dati
# 1 - DBMS
## Struttura Generale
+  Un **DBMS** è un sistema di gestione di database, creato per superare alcune limitazioni degli **OS** tradizionali
+ Esso ha il vantaggio di utilizzare uno **Schema** per organizzare i dati, e usare **linguaggi dichiarativi**, molto semplici, creati ad hoc per gestire i dati
---
* Il __database__ può essere visto attraverso tre livelli:
	* Livello __fisico__: I dati vengono visti come sono conservati sul dispositivo fisico. A noi non ci serve molto
	* Livello __logico__: I dati vengono visti come descritti dalle strutture e dagli schemi del modello relazionale
	* Livello __esterno__: Presente solo in database di grandi dimensioni, permette di visionare solo alcune parti dei dati, tramite alcune __viste__, definite dall'amministratore, accessibili solo ad un gruppo di applicazioni
* Su di essi valgono due proprietà:
	* Indipendenza __fisica__: Cambiando la struttura del livello fisico, la struttura del livello logico __non__ cambia
	* Indipendenza __logica__: Cambiando la struttura del livello logico, alcune viste del livello esterno __potrebbero__ cambiare
+ Inoltre, ogni livello viene utilizzato e modificato tramite dei linguaggi dichiarativi specifici:
	* SDL: Permette di modificare lo schema dei dati, lavora sul livello esterno e logico
	* __DML__: Permette di modificare l'istanza dei dati, lavora principalmente sul livello logico
	* DDL: Permette di modificare lo schema fisico dei dati, lavora sul livello fisico
* Studieremo database di tipo __integration__ DB, in cui i dati vengono strutturati sulla base della loro __rappresentazione ideale__, e non in base a come devono essere usati
---
* I DBMS effettuano i compiti richiesti tramite vari moduli software, detti **servizi**
	* Essi si suddividono in __esterni__, richiesti esplicitamente dagli utenti, ed __interni__, utilizzati dal sistema per adempiere alle richieste
* Questi servizi sono suddivisi in tre gruppi:
	* __Gestore delle strutture di memorizzazione__: L'insieme dei servizi che si occupano di gestire e memorizzare i dati
	* __Query manager__: L'insieme dei servizi che gestiscono ed eseguono i comandi DML
	* __Transaction manager__: L'insieme dei servizi che si occupano di gestire richieste complesse, e garantire l'integrità dei dati

![[DBMS.png]]
+ I classici utenti di DBMS sono i seguenti:
	* Progettisti di database
	* Programmatori Applicativi
	* Amministratori di Database (DBA)
	* Progettisti di DBMS
---
* Esistono diversi modi in cui organizzare i DBMS:
	* __Centralizzata__: Sia gli utenti che i sistemi si trovano sulla stessa macchina
	* __Client-Server__: I sistemi sono memorizzati su di una macchina, gli utenti effettuano richieste da altri host
	* __Distribuite__: I dati e le applicazioni sono distribuiti su più macchine.
---
## Gestore delle Strutture di Memorizzazione
+ I dati del DBMS sono memorizzati su memoria fissa. 
+ Per essere elaborati, questi devono ovviamente essere caricati sulla memoria centrale. Ma nonostante l'avanzare del tempo, questa rimane comunque un operazione **costosa**
+ Dobbiamo organizzare i nostri dati in file nel modo più **efficiente** possibile e trovare un modo altrettanto efficiente per caricarli in RAM
---
+ Di per se, le relazioni saranno organizzate in uno o più  **file**, in cui ogni **record** corrisponde ad una **tupla**, ed i **campi** dei record ad i singoli **attributi**
+ Questa organizzazione darà lo schema fisico sui dati
---
+ Ogni volta che eseguiamo un __comando__, questi viene:
	* __Controllato__ ed approvato dal Query Manager, venendo tradotto in un programma specifico
	* Quest'ultimo __accede__ ad i dati del database, tramite il File Manager ed il Buffer Manager
		* Il DBMS utilizza un proprio file manager così da migliorare la portabilità e l'efficienza
---
+ Considerando un hard-drive, i costi di accesso sono suddivisibili nei seguenti:
	+ Tempo di __latenza__: Tempo di spostamento del braccio laser sul disco ($\approx 10 ms$)
	* Tempo di __trasferimento__: ($\approx 1 ms$ per blocco)
	* Tempo di __accesso__: ($\approx1$ milionesimo di secondo)
---
+ Possiamo __migliorare__ il tempo di __latenza__ organizzando in modo ottimale i dati su disco!
* Possiamo organizzarli in tre modi:
	* Allocazione __contigua__: Tutti i blocchi relativi ad un file si trovano vicini
		* Diminuisce il tempo richiesto, ma è difficile espandere i file
	* Allocazione __concatenata__: I blocchi sono sparsi, ed ognuno punta al successivo
		* Facile espandere, ma aumenta il tempo richiesto
	* Allocazione __???__: I blocchi si trovano su tracce diverse, sullo stesso "cilindro", ma alla stessa distanza dal centro. 
		* In questo modo, le braccia si devono muovere comunque una sola volta, ma abbiamo lo spazio per espandere il file. Organizzazione ottimale
* Considerando invece la struttura __interna__ di un file, conviene fare in modo che in un blocco si trovino solo record fra loro __collegati__, così da __ridurre__ il numero di letture richieste, e mettere vicini blocchi diversi con dati collegati
---
## Gestore del Buffer
+ Per accedere ad un file, il DBMS lavora in modo simile al SO: Possiede un __buffer__ in memoria RAM (detta __Main Memory__) in cui vengono ricopiati i blocchi di dati da elaborare
* Questo buffer viene gestito con tecniche simili a quelle necessarie all'ottimizzazione di una memoria __cache__. Interessante è la politica di __rimpiazzamento__ utilizzata
* Infatti, mentre normalmente potremmo preferire l'algoritmo __LRU__, il DBMS è capace di scegliere __differenti algoritmi__ a seconda della situazione. A differenza di un SO, abbiamo __maggiore__ __coscienza__ di cosa sono i __dati__ che manipoliamo, e quindi quali potrebbe esser meglio conservare nel buffer
* In alcuni casi, viene addirittura scelto l'__MRU__
	* In generale, possiamo dire che ad influire sulle __prestazioni__ sono la __dimensione__ del buffer e la __politica__ di rimpiazzamento scelta

---
## Indici
+ Nell'attuazione delle visite sembra __inevitabile__ trovarsi a leggere __blocchi non necessari__, in quanto è impossibile sapere a priori la posizione esatta dei nostri dati. Questo però ci __rallenta__
* A tal scopo vengono introdotte le __strutture ausiliarie d'accesso__ o __indici__, file contenenti coppie di attributi, detti __chiavi__, e __puntatori__ alle tuple contenenti questi attributi
* Questi file risulteranno di __dimensioni__ molto __minori__. Se scorressimo su di essi per cercare i dati richiesti, dovremmo caricare __molti meno blocchi inutili__
+ Nonostante l'ovvia ottimizzazione alle letture, l'utilizzo di indici comporta un __peggioramento__ delle operazioni di __aggiunta__, __rimozione__ o __modifica__ di elementi od attributi della relazione
---
* Gli __indici__ possono essere
	* __Primari__: L'indice si basa su un attributo chiave candidata
	* __Secondari__: L'indice non si basa su un attributo chiave candidata
* Essi possono essere __implementati__ in due modi:
	* Indici __Ordinati__: Fisicamente memorizzati in memoria, ordinati secondo un criterio
	* Indici __Heap__: I valori vengono calcolati tramite una funzione di hash
* Un __indice__  si dice
	* __Clusterizzato__: Se il database a cui si riferisce è __ordinato__ secondo il suo attributo
	* __Non-Clusterizzato__ altrimenti
* La presenza di un indice clusterizzato __facilita__ notevolmente le __operazioni__ sul file
* Un indice può anche essere __multi attributo__, ovvero utilizzare più chiavi di ricerca

#### Ordinati
+ Gli indici di tipo ordinato sono solitamente implementati tramite __strutture ad albero__, su disco, le quali rispettano le seguenti __proprietà__:
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
#### Hash
+ A differenza degli indici ordinati, gli indici hash non vengono direttamente salvati in memoria
* I dati sono organizzati in blocchi, detti bucket, ed ad ognuno di essi corrisponde un valore. 
* Quando ricevo la mia chiave, essa viene trasformata tramite una funzione di hash in uno di questi valori, il quale mi indicherà in quale blocco cercare l'informazione
* Dovremo conservare un array contenente i puntatori ai blocchi, ma per il resto riparmiamo molta memoria
---
* Nonostante le ovvie migliorie di memorizzazione, abbiamo delle complicazioni:
	* In caso di aggiunta di dati, dovremo controllare che il bucket corrispondente abbia ancora spazio libero in cui metterli. In caso contrario, dovremo allocare un nuovo blocco, detto overflow, collegato tramite puntatore. Questo peggiorà le operazioni di lettura
	* È impossibile effettuare ricerche in intervalli
---
* Il problema dell'overflow può essere risolto allocando lo spazio ideale ai bucket, congiuntamente all'utilizzo di una funzione di hash perfetta
* Questa distribuisce uniformemente i valori nei bucket, alzando la soglia per cui è necessario usare un overflow
---
* Una classica funzione di hash è la funzione modulo.
	* Si è notato che la funzione è maggiormente efficace nella distribuzione uniforme se il valore di modulo utilizzato è numero primo oppure è composto da fattori primi maggiori di 20
---
* Anche gli indici hash possono essere primari/secondari, mono o multiattributo
	* Nel caso dei multiattributo potrebbe essere importante l'ordine dei dati
* Un poco differente è la definizione di indice clusterizzato. Viene detto clusterizzato quando gli attributi con valori simili sono tutti nello stesso bucket. 
* Questo effetto viene normalmente ottenuto tramite la funzione di hash, ma solo per uno degli indici. Nel caso di indici secondari, sarà necessario un secondo set di bucket, contenenti puntatori ai dati. Questo viene detto indice multilivello

## Gestore delle Interrogazioni
+ Come viene elaborata una query?
+ Ogni query viene tradotta in un **Piano di Esecuzione Logico** (LQP), una riscrittura in algebra relazionale dell'interrogazione. Questo potrà essere **rappresentato** da un **albero**.
* Esistono **multipli** LQP per una singola query. Il sistema dovrà determinare il più **efficace**.

* Una volta **fissato** un **LQP**, il sistema dovrà determinare un **Piano di Esecuzione Fisico** (PQP), ovvero l'insieme delle operazioni (**algoritmi**) utilizzati per eseguire l'interrogazione a livello fisico.
* Questo non **dipenderà** solo dal **LQP**, ma anche dallo **schema fisico** dei dati (Se sono presenti indici, se i record sono ordinati, etc.)
---
+ Il Query Processor elabora le interrogazioni nel seguente modo, attraverso i suoi componenti:
	1. Query Compiler
		 1. **Parser**
			* Viene controllata la correttezza della query e trasformata in un parse tree
		2. **Translator**
			* Preso il parse tree, viene trasformato nella formula algebrica relazionale più **ovvia** (non la più ottimale)
	2. Query Optimizer 
		1. **Logic Optimizer**
			* Questa formula viene riscritta nella maniera più ottimale (LQP)
		2. **Physical Optimizer**
			* Fissato l'LQP e lo schema fisico, viene elaborato il piano fisico più efficente (PQP)
				* Come? Tramite statistiche di sistema, vedremo più avanti
	3. Query Engine 
		1. **Execution**
			* La query viene eseguita
---
#### Logic Optimizer
* Come fa a determinare il piano migliore? Esso possiede due insiemi di concetti utili
	* **Equivalenze** Algebriche
	* Regole di **Riscrittura** (basate su **euristiche**)

* Quest'ultime sono regole basate sui seguenti principi:
	* **Anticipare** il più possibile le operazioni che permettono di **ridurre** la dimensione dei risultati intermedi  
		* **Selezione** e **Proiezione**  
	* Fattorizzare condizioni di selezione complesse e lunghe liste di attributi in proiezioni, per aumentare la possibilità di applicare regole di riscrittura
* Derivano le seguenti regole:
	* Eseguire le operazioni di **selezione** (σ) il più **presto** possibile
	* Eseguire le operazioni di **proiezione** (π) il più **presto** possibile
	* **Introdurre ulteriori proiezioni** nell’espressione, gli unici attributi da non eliminare sono quelli che appaiono nel risultato della query  o sono necessari in operazioni successive

* Alla fine l'ottimizzatore restituirà un unico piano. Potrebbe restituirne di più equivalenti, ma aumenterebbe esponenzialmente il lavoro dell'ottimizzatore fisico
---
#### Physical Optimizer
+ Come facciamo a trasformare gli LQP ottimi in corrispondenti PQP?
+ Partiamo considerando i LQP stessi.
* Ogni **nodo** e **foglia** dell'albero dovrà essere trasformato in un **algoritmo**
	* Le foglie serviranno per accedere alle relazioni
	* I nodi interni effettueranno operazioni algebriche
---
+ Concentriamoci sull'**accesso** alle **relazioni**
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

+ Ora pensiamo al **costo** di questi algoritmi
	* La SEQ SCAN costa il numero di **blocchi** della relazione acceduta
	* L'INDEX SCAN dipende dal tipo di indice, oscillando fra 1 e log n blocchi, unito al costo d'accesso alle tuple localizzate
* Nel caso dell'INDEX SCAN influisce anche la **clusterizzazione** dei dati.
* Un'idea potrebbe essere **ordinare** i puntatori ai blocchi di memoria, **prima** di accedervi. Questo da vita ad un ulteriore algoritmo, **BITMAP INDEX SCAN**
---
+ Vediamo le **operazioni** algebriche
* Ora che stiamo operando su risultati precedenti, operazioni come **selezione** e **proiezione** non possono che essere eseguite tramite **SEQ SCAN**
* Diverso è il discorso sul **JOIN**. Esso non viene mai unito all'accesso ai dati, e può essere eseguito tramite **4 algoritmi**:
	1. **NESTED LOOP JOIN**
		* Può sempre essere eseguito
		* Tramite due loop, si confronta ogni tupla di una relazione con tutte le tuple della seconda
		* **Non molto efficente**, costa $B(R) + T(R) \cdot B(S)$
		* Conviene nel caso in cui la seconda relazione $S$ è relativamente piccola, e tenuta in memoria principale
		* Esiste una variante, il BLOCK NESTED LOOP, che invece di lavorare sulle tuple, lavora sulle pagine. Questo riduce i costi a $B(R) + B(R) \cdot B(S)$
	2. **INDEX NESTED LOOP**
		* Supponiamo di avere un indice sull'attributo di JOIN in $S$
		* Cicliamo su $R$, e per cercare il valore dell'attributo della tupla in $S$ usiamo l'indice
		* Costo: $B(R) + T(R) \cdot AccessoConIndiceSuS$ 
	3. **MERGE JOIN**
		+  Utilizzato solo in caso di Equi-JOIN
		* Se le relazioni sono ordinate, è possibile scorrere su entrambe, in modo simile al mergesort
		* Se non sono ordinate, si può pensare di ordinarle con un ulteriore algoritmo
		* Costo: $B(R) + B(S)$ 
	5. **HASH JOIN**
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

---
+ Come facciamo a calcolare il costo di un piano?
+ Si utilizza un approccio bottom-up, e partendo dalle radici dei piani, si contano i costi parziali, sia di tempo che di spazio.
* Questi costi sono statistiche, stime ottenute tramite i dati contenuti nei cataloghi di sistema
* Idealmente, questi costi andrebbero ricalcolati ad ogni modifica della base di dati. Essendo un'operazione costosa, nella realtà questo avviene periodicamente, o quando richiesto tramite il comando ANALYZE
---
* Nello stimare il costo di una selezione si usa una probabilità, detta fattore di selettività.
* Questo indica quanto è probabile che una tupla nella relazione soddisfi la selezione
	* Se una selezione restituisce molte tuple, viene detta poco selettiva
* Anch'esso viene calcolato, come le altre statistiche
---
+ Similmente all'ottimizzazione logica, anche i piani fisici vengono scelti in base ad alcune euristiche. 
* Queste permettono di effettuare una prima scrematura fra i possibili piani da scegliere. Verrà poi scelto un ultimo piano, quello più economico, fra i rimanenti
* Per i JOIN
	* Si preferiscono in piani Left-Deep, in quanto permettono di usare il pipelining
	* Non vengono considerate permutazioni di JOIN che implicano dei prodotti cartesiani
---
* Rimane infine l'attività di Progettazione Fisica (PAG 75)

# 2 - Modello Concettuale
## ER
+ Per quanto il modello relazionale sia ottimale per costruire basi di dati, non è facilmente comprensibile
* Utilizziamo quindi un modello __concettuale__ per poter rappresentare in un modo più semplice i nostri dati, e comprendere più facilmente l'organizzazione
* Studieremo in particolare il modello __Entity-Relationship__ (ER), sviluppato da Peter Chen nel 1976
---
+ Un __entità__ è un __insieme__ di oggetti, le __istanze__ dell'entità
	* Vengono rappresentate graficamente come __rettangoli__
* Una __associazione__ è un insieme di __legami__ fra due o più istanze. Queste possono appartenere a più entità, od ad una stessa, con i cosiddetti __ruoli__ ad indicare il significato di ognuna
	* Vengono rappresentate graficamente come __rombi__
* Queste vengono __classificate__ in base al __numero__ di oggetti nella associazione.
* Dobbiamo cercare di usare associazioni il più possibile __semplici__, ovvero con numero minore di istanze collegate
---
* Sia entità che associazioni possiedono degli __attributi__, ovvero __funzioni__ applicabili sulle istanze capaci di ritornare valori
	* Vengono rappresentati graficamente come __pallini__ __bianchi__
* Questi attributi possono avere dei __vincoli di cardinalità__, __limiti__ inferiori e superiori al __numero__ di __valori__ che l'attributo può possedere
	* Attributi con __vincolo__ inferiore __nullo__ vengono detti __opzionali__
	* Questi vincoli esistono anche per le associazioni, riguardo il numero di associazioni possibili con alcune istanze
* Esistono anche attributi composti, formati da più proprietà variabili
* Facilitano la scrittura di alcuni vincoli di cardinalità
	* Indicati come __grossi pallini__ bianchi
---
* Un __identificatore__ è un insieme di attributi o associazioni capaci di identificare univocamente un' istanza di un entità
	* Vengono indicati graficamente da __pallini neri__
* Si suddividono in:
	* __Interni__: basati sui valori degli __attributi__
	* __Esterni__: basati sui valori delle __associazioni__
		* Le entità che possiedono solo identificatori esterni vengono dette __deboli__
	* __Misti__: basati __sia__ su associazioni che attributi
* Inoltre si dicono:
	* __Semplici__: formati da una __sola__ proprietà
	* __Composti__: formati da __più__ proprietà
* Gli identificatori __misti__ sono tutti __composti__
---
* Le __gerarchie di ereditarietà__ sono una componente presente nell'__extended__ ER
* Consistono in una relazione fra entità che indica alcune come __sottoinsiemi__ o specializzazioni di un altra.
	* Vengono rappresentate graficamente con delle __frecce__
* Esse si classificano in:
	* __Esclusiva__: Se i sottoinsiemi possiedono __intersezioni__
	* __Condivisa__: Se i sottoinsiemi __non__ possiedono intersezioni
* Oppure in:
	* __Totale__: Se tutti gli elementi del padre vengono __suddivisi__ nei figli
	* __Parziale__: Se __non__ __tutti__ gli elementi del padre vengono suddivisi

---
# 3 - Modello Relazionale
## Introduzione
+ Questo è un modello inventato da Edward Codd negli anni 80
+ Si basa sull'utilizzo di **relazioni**, sottoinsiemi di prodotti cartesiani fra **domini**.
	+ Il __grado__ della relazione è il numero di domini coinvolti, corrisponde al numero di "colonne"
	* La __cardinalità__ è il numero di elementi presenti nella relazione, corrisponde al numero di "righe"
* Ogni elemento di questo prodotto viene detto **attributo** della relazione.
* Ogni istanza della relazione viene detta **tupla**
---
* Ci occuperemo di sistemi __schema-first__, in cui viene prima pensato lo schema da usare, poi vengono inseriti i dati
---
## Componenti
+ Viene utilizzato il valore speciale `null` per indicare la __mancanza__ di valore in un campo. Ogni tipo di dato può assumere questo valore. 
---
+ Una __chiave__ è un attributo __unico__ di un' istanza della relazione, capace di __identificarla__.
* Formalmente, possiede le seguenti __proprietà__:
	* $\forall r \in \mathbb{R} \; \;\exists k \subseteq {A_1, \cdots ,A_n } \; | \; se k_{r_1} = k_{r_2} \to r_1[k] = r_2[k]$  (__proprietà d'univocità__)
	* Non esistono sottoinsiemi propri di k che sono a loro volta chiavi
* Una chiave che non rispetta la seconda proprietà viene detta __superchiave__. I suoi sottoinsiemi possono essere a loro volta chiavi o superchiavi, più minimali
* L'insieme di tutti gli attributi di un elemento è sempre superchiave
* A noi interessa trovare chiavi __minimali__, ovvero l'insieme di attributi univoci di cardinalità minore
---
+ Possiamo anche avere più chiavi utilizzabili. L'insieme di esse viene detto chiavi __candidate__.
* Fra esse sceglieremo una chiave __primaria__, un insieme di attributi che non possono essere nulli, e che useremo come chiave. 
* Le rimanenti verranno chiamate chiavi __alternative__
---
+ Esistono anche le cosiddette chiavi __esterne__. Esse __non__ sono vere e proprie __chiavi__, ma un insieme di attributi appartenenti ad una seconda relazione (referente) i quali avranno lo stesso valore di alcuni attributi della relazione riferita. 
* Questo permette di creare un __associazione__ fra diversi elementi di diverse relazioni

---
# 5 - Progettazione Fisica
+ Dato un carico di lavoro, l'attività di progettazione fisica si preoccupa di progettare uno schema fisico, ovvero l'insieme degli indici creati, che faciliti l'esecuzione delle operazioni appartenenti al workload
+ Come facciamo?
+ In generale:
	+ Guardiamo ogni interrogazione, a partire dalle più frequenti
	+ Per ognuna, valutiamo il PQP ideale, e creiamo gli indici capaci di effettuarlo
	+ Si valuta empiricamente se questi indici sono utili
	+ Se non lo sono, si valuta se rimuoverli e modificarli
	+ Si controlla se questi indici sono **compatibili** con quelli creati in precedenza

# 6  - Algebra Relazionale
##### Ridenominazione
* Quest'operazione riporta gli attributi richiesti nel formato indicato
	* $\rho_{b_1,\cdots,b_k \; \leftarrow \; c_1, \cdots, c_k} R$ 
* Su può usare in SQL come:
```SQL
SELECT Anno AS Uscita
FROM Film
```

##### Proiezione
* Riporta solo alcune colonne della relazione, eliminando i duplicati
	* $\Pi_{b_1, \cdots, b_k} R$ 
* Il grado sarà uguale all'originale, la cardinalità minore o uguale
* Si può usare in SQL in due modi:
```SQL
SELECT Anno, Regista    
FROM Film;

SELECT DISTINCT Anno, Regista /* Elimina i duplicati */
FROM Film;
```

##### Selezione
* Questa operazione estrae alcune righe da una relazione sulla base di una formula logica
	* $\sigma_{F} R$ 
* La formula sarà composta da $\wedge, \vee, \neg$ e formule atomiche di forma $A_i \theta A_j$ dove $\theta \in \{=, \neq, \leq, <, \geq, > \}$ e $A_i, A_j$ sono attributi della relazione o valori degli attributi
* In SQL si scrive nel seguente modo
```SQL
SELECT *
FROM Film
WHERE Regista = "Tim Burton"
```
---
* Un problema non presente in algebra relazionale ma importante in SQL è la presenza di __attributi__ __nulli__. Nel valutare questi valori nelle formule logiche, si aggiunge ai valori logici un terzo valore, __unknown__, il quale non è ne vero o falso, e non influenza direttamente i valori delle formule
* Viene inoltre aggiunto un predicato per cercare valori nulli, ovvero `IS NULL`

##### Prodotto Cartesiano
* Questa famosa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \times S$ 
* Dato $U_R \bigcap U_S$ ,  $U_{R \times S} = U_R \bigcup U_S$ 
* grado($R \times S$) = grado($R$) + grado($S$)
* cardinalità($R \times S$) = cardinalità($R$) $\cdot$ cardinalità($S$)
* In SQL viene scritta come
```SQL
SELECT *
FROM Film, Cinema
```
---
* Possiamo gestire la presenza di attributi omonimi tramite l'utilizzo di una denominazione. Questa accortezza non è necessaria in SQL, in quanto il sistema etichetta automaticamente gli attributi con la relazione a cui sono associati

##### Unione
* Anche questa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \bigcup S$ 
* __grado__($R \bigcup S$) = grado($R$) = grado($S$)
* max(cardinalità($R$), cardinalità($S$)) $\leq$ __cardinalità__($R \bigcup S$) $\leq$  cardinalità($R$) + cardinalità($S$)
* Essa può essere utilizzata solo se le relazioni possiedono uno stesso schema, $U_R = U_S$, ed in SQL solo se i due schemi sono equivalenti, caratterizzati da tipi comuni 
*  In SQL viene scritta come
```SQL
SELECT *
FROM Film
UNION
SELECT *
FROM Documentario
```

##### Sottrazione Insiemistica
* Anche questa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \setminus S$ 
* $U_R = U_S = R_{R \setminus S}$ 
* cardinalità($R \setminus S$) $\leq$  cardinalità($R$)
*  In SQL viene scritta come
```SQL
SELECT *
FROM Film
EXCEPT/MINUS  // Uno di questi due
SELECT *
FROM Documentario
```

---
* Oltre a queste operazioni, è possibile ottenerne alcune, dette derivate, combinando quelle esistenti
---
##### Intersezione
*  Anche questa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \bigcap S$ = $R \setminus (R \setminus S)$ 
* $U_R = U_S = R_{R \bigcap S}$ 
* 0 $\leq$ cardinalità($R \bigcap S$) $\leq$ min(cardinalità($R$), cardinalità($S$))
*  In SQL viene scritta come
```SQL
SELECT *
FROM Film
INTERSECT
SELECT *
FROM Documentario
```

##### Theta-Join
* Esso rappresenta un prodotto cartesiano seguito da una selezione, e ci permette di prendere elementi di relazioni che rispettano una formula atomica
* Viene scritta come:
	* $R \bowtie_{A\theta B} S$ 
* 0 $\leq$ cardinalità($R \bowtie_{A\theta B} S$) $\leq$ min(cardinalità($R$), cardinalità($S$))
* In SQL viene scritto come
```SQL
SELECT DISTINCT Titolo, Regista
FROM Noleggio JOIN Video
ON Noleggio.Colloc = Video.Colloc
```

##### Natural-Join
* Questa è una variante del Join, in cui vengono unite le righe sulla base di attributi comuni. Questo viene solitamente utilizzato per navigare chiavi esterne
* Bisogna fare attenzione perchè unisce TUTTI gli attributi comuni, sono solo quelli che vogliamo, ed è quindi utile utilizzarlo in comune ad una Ridenominazione

##### Differenza
# 7 - SQL
