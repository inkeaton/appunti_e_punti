# Algoritmi
* ### Selection Sort
	* Complessità:  $\theta(n^2)$
* ### Insertion Sort
	* Caso migliore $\theta(n)$
	* Caso peggiore $\theta(n^2)$
* ### Bubble Sort 
	* Caso migliore $\theta(n)$ 
	* Caso peggiore $\theta(n^2)$
* ### Ricerca Binaria
	* Complessità:  $\theta(\log_2(n))$
* ### MergeSort
	* Complessità:  $\theta(n\log_2(n))$
* ### MergeSort
	* Caso medio:  $\theta(\log_2(n))$
	* Caso peggiore: $\theta(x^2)$
---
---
# Tipi di Dato
## List
### Una sequenza S di n elementi
1. Operazioni
	* __emptyList__:→List 
	* __set__: N x Elem x List → List 
	* __add__: N x Elem x List → List 
	* __addBack__: Elem x List → List 
	* __addFront__: Elem x List → List 
	* __removePos__: N x List → List 
	* __get__: N x List → Elem 
	* __isEmpty__: List → Bool 
	* __size__: List → N
2. Strutture Dati
	* __Array Dinamici__
	* __Liste (semplici, doppiamente collegate, circolari, etc.)__
	
## Queue
### Una sequenza LIFO S di n elementi 
1. Operazioni
	*  __isEmpty__: List → Bool 
	* __push__: Elem x List → List
	* __pop__: List → Elem
	* __top__: List → Elem
2.  Strutture Dati
	* __Array Dinamici__
	* __Liste (semplici, doppiamente collegate, circolari, etc.)__
## Stack
### Una sequenza FIFO S di n elementi
1. Operazioni
	*  __isEmpty__: List → Bool 
	* __queue__: Elem x List → List
	* __dequeue__: List → Elem
	* __first__: List → Elem
2.  Strutture Dati
	* __Array Dinamici__
	* __Liste (semplici, doppiamente collegate, circolari, etc.)__
## Set
### Un aggregato di elementi dal valore omogeneo e distinto
1. Operazioni
	* **emptySet:** → Set 
	* **insertElem**: Elem x Set → Set 
	* **deleteElem**: Elem x Set → Set 
	* **setUnion**: Set x Set → Set 
	* **setIntersection**: Set x Set → Set 
	* **setDifference**: Set x Set → Set 
	* **isEmpty**: Set → Bool 
	* **isSubset**: Set x Set → Bool 
	* **size**: Set → N 
	* **member**: Elem xSet → Bool
2. Strutture Dati
	* __Array Dinamici__
	* __Array Dinamici Ordinati__
	* __Liste (semplici, doppiamente collegate, circolari, etc.)__
	* __Bit Vector__

## Dictionary
### Un insieme S di coppie (Elem, Key)
1. Operazioni
	* __insert__: Elem x Key x Dictionary  → Dictionary
	* __delete__:  Key x Dictionary  → Dictionary
	* __search__: Key x Dictionary  → Elem
2. Strutture Dati
	* __Array Dinamici__
	* __Liste (semplici, doppiamente collegate, circolari, etc.)__
	* __Tabelle ad Accesso Diretto__
	* __Tabelle di Hash con Liste di Collisione__
	* __Trees__
## Tree
### Un insieme di Nodi ed Archi
1. Operazioni
	* __numNodi__: 
	* __grado__:  
	* __figli__: 
	* **padre**:
	* **aggiungiNodo**:
	* **aggiungiSottoalbero**:
	* **rimuoviSottoalbero**;
2. Strutture Dati
	* __Array Dinamici__
	* __Liste (semplici, doppiamente collegate, circolari, etc.)__
## Graph
### Un insieme di Vertici e Archi
2. Strutture Dati
	* __Liste D'Adiacenza (implementate con array, liste o matrici)
## Priority Queue
## RB Tree