* A differenza degli indici ordinati, gli indici hash non vengono direttamente salvati in memoria
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