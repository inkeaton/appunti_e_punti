* La complessità di partition è $\theta$ (inizio - fine), ovvero dipende dalla dimensione della zona su cui opera
* La complessità di QS è $\theta$ ($n\log{n}$) nel caso migliore, $\theta$ ($n^2$) in quello peggiore
* Il caso migliore di quicksort si ha quando ad ogni chiamata di partition, il pivot è **il mediano** degli elementi degli elementi compresi nella porzione dell'array A tra inizio e fine. Ovviamente questo caso migliore è teorico: non si può infatti calcolare l'elemento mediano senza riordinare prima gli elementi.
* Il fattore n di n log(n) viene dal numero di operazioni svolte ad ogni livello dell'albero della ricorsione:  al livello j si effettuano 2^j chiamate a partition, ciascuna su una porzione di array lunga n/(2^j). Ciascuna di queste chiamate ha complessità lineare nella dimensione della porzione di array su cui viene chiamata, quindi Theta ( n/(2^j) ): ad ogni livello faccio 2^j * Theta ( n/(2^j) ) operazioni, che determinano la complessità Theta( n )
* Il log n viene invece dal numero dei livelli dell'albero della ricorsione
* Facciamo log n volte n operazioni, ergo theta (n log n)
* Cose da includere
	1) il vostro nome, cognome, matricola  
	2) su cosa è il vostro podcast (uno tra: quicksort caso migliore; quicksort caso peggiore; mergesort caso migliore e peggiore in base alla associazione che trovate in fondo al messaggio)  
	3) quando si verifica il caso di vostro interesse (es: se dovete fare un podcast su quicksort caso peggiore, dite quali sono le condizioni sotto cui si verifica il caso peggiore di quicksort)  
	4) qual è la complessità dell'algoritmo nel caso di vostro interesse  
	5) spiegare con molta precisione e chiarezza come si arriva al calcolo della complessità che avete indicato al punto 4; ad esempio, per mergesort e per quicksort nel caso migliore dovrete spiegare quanti sono i livelli dell'albero di ricorsione, di che tipi sono i "problemi" incontrati ad ogni livello (partiton oppure merge), quanti "problemi" vengono incontrati ad ogni livello, qual è la complessità di ciascuno di essi e perché; il calcolo di complessità di quicksort nel caso peggiore è diverso ma va spiegato chiaramente e dettagliatamente  
	6) un esempio di chiamata (o "simulazione di esecuzione", fatta manualmente con carta e penna come io ho fatto alla lavagna) dell'algoritmo di vostro interesse, nel caso indicato.
* Struttura generale
	* Presentazione
	* Funzionamento teorico
	* Esempio
	* Spiegazione caso migliore 

### Script 
* Buongiorno! Il mio nome è Edoardo Vassallo, matricola s4965918, ed oggi parleremo di uno degli algoritmi di ordinamento più utilizzati al mondo, il QUICKSORT!
* Tradotto letteralmente significa "ordinamento rapido". L'idea di base dell'algoritmo consiste nello scegliere un elemento della nostra struttura dati, denominato "pivot" o perno e scansionare il resto della struttura.
* Ad ogni ciclo, confronteremo il pivot con un elemento della struttura. In caso questo sia minore del pivot, sarà spostato a sinistra del pivot, altrimenti messo a destra.
* Alla fine del nostro loop, avremo a sinistra di pivot tutti gli elementi minori di esso, e a destra tutti quelli maggiori. Nonostante queste due porzioni non siano ordinate, risulta ovvio come pivot si trovi adesso nella posizione giusta 
* L'idea adesso è di richiamare ricorsivamente la funzione su queste due porzioni, e fermarci quando un gruppo diventa di un solo elemento. DI chiamata in chiamata, arriveremo ad aver ordinato tutti i nostri elementi 
* (_Numeri da ordinare: 5 9 3 6 1 0 4_ ?)