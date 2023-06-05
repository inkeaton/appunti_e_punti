* Un albero __binario__ viene definito __induttivamente__ nel seguente modo:ù
	* Passo __Base__: l'albero vuoto
	* Passo __Induttivo__: Un nodo con due figli
* Vale la seguente proprietà:
	* $h + 1 \leq n \leq 2^{h+1} -1$ 
---
* Vediamo ora il problema delle __Torri di Hanoi__. Esso viene impostato come:
	* Avendo dei dischi di dimensione differente infilati su di un palo, come faccio a spostarli tutti, nell'ordine corretto, su di un secondo palo, potendo utilizzare un terzo palo per tenerli?
* Questo è un problema __intrattabile__ ($\Omega (2^n - 1)$), esiste un algoritmo ricorsivo in $\Theta (2^n -1)$ 
---
* Le __complessità__ possono essere studiate tramite lo studio delle __relazioni di ricorrenza__, utilizzando __sostituzioni__, oppure tramite lo __studio__ dell'__albero__ delle chiamate ricorsive
* I risultati possono poi essere verificati tramite l'__induzione__ 