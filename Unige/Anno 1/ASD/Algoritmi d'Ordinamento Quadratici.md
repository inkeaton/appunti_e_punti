# Algoritmi d'Ordinamento Quadratici

* Immaginiamo di avere una sequenza di numeri, di cui non sappiamo niente, e di volerla ordinare in ordine crescente
* Possiamo immaginare tre algoritmi:
* ## SELECTION SORT
	* Scansioniamo la lista cercando l'elemento minimo. Una volta trovato, questo viene posizionato in prima posizione
	* Ciò viene ripetuto più volte, considerando ogni volta solo la porzione di insieme non ordinato, fino ad avere la lista completamente ordinata
	* ES
		* 1 3 22 3 32 4
		* 1 3 22 3 32 4
		* 1 3 3 22 32 4
		* 1 3 3 4 22 32
	* In C++, una versione in grado di ordinare gli elementi di un vector può essere realizzata nel seguente modo:
	```
	void selectionSort(vector<int>& v) {
   	int current_min_index;
   	unsigned int size = v.size();
   	for (unsigned int i=0; i<size; ++i) { 
     	current_min_index = i;
     	for (unsigned int j=i+1;j<size; ++j)
        		if (v[current_min_index] > v[j])
            		current_min_index = j;
     		scambia(v, i, current_min_index);
   		}
	}
	
	// la funzione scambia i due valori
	```

* ## INSERTION SORT
	* Cerco di ordinare i numeri pezzo per pezzo, ordinando delle sotto-sequenze.
	* ad ogni ciclo aggiungo un elemento alla sottosequenza, e riordino, fino a quando non ho ordinato l'intera sequenza
	* ES
		* 1 2 25 4 17 3 6
		* 1 2 25 4 17 3 6
		* 1 2 25 4 17 3 6
		* 1 2 25 4 17 3 6
		* 1 2 4 25 17 3 6
		* 1 2 4 17 25 3 6
		* 1 2 3 4 17 25 6
		* 1 2 3 4 6 17 25 
	* Una versione dell'algoritmo in C++ è la seguente:
	```
	void insertionSort(vector<int>& v) {
	   int current, prev;
	   unsigned int size = v.size();
	   for (unsigned int i=1; i<size; ++i) { 
		 current=i; 
		 prev=i-1;
		 while(prev>=0 && v[current]<v[prev]) {
			 scambia(v, current, prev);
			 --current;
			 --prev;
		 }
	  }
	}
	```

* ## BUBBLE SORT 
	* Partiamo dalle prime cifre e guardiamo se il numero subito successivo è maggiore di esso. in cao affermativo, li invertiamo
	* Andiamo avanti controllando numero per numero, e cicliamo fino a quando non avviene un ciclo senza scambi 
	* in questo modo, i numeri maggiori "galleggiano", andando a finire in fondo
	* ES
		* 9 21 53 10 3 2 
		* 9 21 10 3 2 53
		* 9 10 3 2 21 53
		* 9 3 2 10 21 53
		* 3 2 9 10 21 53
		* 2 3 9 10 21 53
	* Una versione dell'algoritmo in C++ è la seguente:
	```
	void bubbleSort(vector<int>& v) {
   unsigned int size = v.size();
   bool scambiati;
   for (unsigned int i=1; i<size; ++i) {
      scambiati = false;
      for (unsigned int j=0; j<size-i; ++j)
          if(v[j]>v[j+1]) { 
              scambia(v, j, j+1);
              scambiati = true;
            }
      if (!scambiati) return;
      }
	}
	```

* ### Efficienza 
* Il Selection sort è molto più efficente rispetto agli altri nell'ordinare, ma un suo difetto si trova nel caso in cui ad essere analizzata è una sequenza già ordinata
* Infatti, Insertion e Bubble sort sono strutturati in modo da evitare scambi in casi non necessari, riducendo quindi notevolmente i tempi nel caso di una sequenza già ordinata. Essi sono **algoritmi adattivi**
* Al contrario il Selection sort esegue comunque questi scambi, perdendo una notevole quantità di tempo su insiemi di elementi molto elevati