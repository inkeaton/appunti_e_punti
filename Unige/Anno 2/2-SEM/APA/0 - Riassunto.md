+ In questo documento, proveremo a riassumere i concetti principali del corso di **Analisi e Progettazione Algoritmi** (APA)
---
# 1 - Analisi Algoritmi Deterministici 

## Complessità di un Algoritmo
+ La **complessità** di un algoritmo indica il __tempo__ necessario affinché si ritrovi la soluzione. Esso varia in base al numero di valori in input
* Un modo per indicarla è tramite il paragone con alcune funzioni elementari, caratterizzate da comportamento __asintotico__
* Possiamo classificare i **comportamenti** in:
	* **Trattabili**
		* $Θ(1)$ costante  
		+ $Θ(\log n)$ logaritmico  
		+ $Θ(\log n)^k$ poli-logaritmico  
		+ $Θ(\sqrt{n})$ radice quadrata  
		+ $Θ(n)$ lineare  
		+ $Θ(n \cdot \log n)$ pseudo-lineare  
		+ $Θ(n^2)$ quadratico  
		+ $Θ(n^3)$ cubico  
	+ **Intrattabili**  
		+ $Θ(2^n)$ esponenziale  
		+ $Θ(n!)$ fattoriale  
		+ $Θ(n^n)$ esponenziale in base n
+ Per indicare il comportamento del nostro algoritmo in confronto a questi, useremo la seguente notazione:
	+ $O(f(n))$ -> La complessità cresce __non più__ di un funzione $f$
	* $\Omega(f(n))$ -> La complessità cresce __non meno__ di una funzione $f$
	* $\Theta(f(n))$ -> La complessità cresce __come__ la funzione $f$
---
+ Purtroppo la complessità __non__ dipende __solo__ dalla __dimensione__ dell'input, ma anche dai valori __specifici__
* Per questo dovremo considerare la complessità in tre casi separati: 
	* Caso __migliore__
	* Caso __peggiore__
	* Caso __medio__
* Diremo che un algoritmo ha __complessità__:
	* $O(f(n))$ se $T_{worst} = O(f(n))$
	* $\Omega(f(n))$ se $T_{best} =\Omega(f(n))$
	* $\Theta(f(n))$ se $T_{worst} = T_{best} =\Theta(f(n))$

---
## Complessità di un Problema
+ Possono venire definire anche le __complessità__ di un __problema__, nel seguente modo
	* La $O(f(n))$ di un problema viene definita come la $O(f(n))$ __minima__ fra quelle degli algoritmi che risolvono il problema
	* La $\Omega(f(n))$ di un problema viene definita come la $\Omega(f(n))$, __comune__ a tutti gli algoritmi risolutori del problema. Bisogna dimostrare che è impossibile risolverlo in tempo minore
* I problemi vengono quindi __classificati__ in base alle loro complessità e presenza di algoritmi di risoluzione:
	* __Trattabili chiusi__: Risolvibili con algoritmi efficenti, non si possono migliorare
	* Trattabili __con gap algoritmico__: Risolvibili con algoritmi efficenti, se ne possono teoricamente creare di più efficenti
	* __Presumibilmente intrattabili__: Risolvibili con algoritmi esponenziali, se ne possono teoricamente creare di più efficenti
	* __Dimostrabilmente__ intrattabili: Risolvibili con algoritmi esponenziali, non si possono migliorare
	* Dimostrabilmente __insolubili__: Irrisolvibili tramite algoritmo

---
## Correttezza di un Algoritmo
+ La **correttezza** di un algoritmo $A$ su un problema $P$ è una proprietà che verifica che che $\forall i \in I, \; A(i)$ è __soluzione__ di $P$
* Come possiamo verificarla?
* Esistono più metodi, a seconda del **tipo** di algoritmo
---
#### Algoritmi Ricorsivi
---
+ Il metodo principale che si usa si basa sul **principio d'induzione**, un teorema applicabile ad insiemi di elementi definiti **induttivamente**, ovvero tramite un insieme di regole applicate ripetutamente, che permette di dimostrare **proprietà** su questi insiemi.
---
+ Esso può essere declinato in più forme. Vediamo:
+ __Induzione Aritmetica__:
	+ Sia $P$ un predicato sui numeri naturali tale che
		+ **Base**: vale $P (0)$
		+ **Passo induttivo**: se vale $P (n)$ allora vale $P (n + 1)$,
	+ allora $P(n)$ vale per ogni $n ∈ \mathbb{N}$
+ Questa versione permette di dimostrare proprietà come la **serie aritmetica** o la **serie geometrica** sui numeri naturali 
---
+ __Induzione Aritmetica Completa__:
	+ Sia $P$ un predicato sui numeri naturali tale che
		+ **Base**: vale $P (0)$
		+ **Passo induttivo**: se vale $P (m) \; \forall \; m < n$ allora vale $P (n)$,
	+ allora $P(n)$ vale per ogni $n ∈ \mathbb{N}$
+ Questa versione permette di dimostrare concetti più complessi come, nel caso di alberi definiti induttivamente, **l'altezza di un albero**
+ Possiamo usare questa definizione per **dimostrare la correttezza** di algoritmi definiti su insiemi induttivi.
+ Ad esempio, se un algoritmo è definito sui numeri naturali, possiamo dimostrare la sua correttezza se
	+ L'algoritmo è corretto per 0
	+ Assumendo che sia corretto su $n$, è corretto anche su $n+1$
+ Questo principio può essere usato anche per lo **sviluppo** degli algoritmi stessi su insiemi induttivi
---
#### Algoritmi Iterativi
---
+ Per comprendere la correttezza di un algoritmo **iterativo**, dobbiamo riscriverlo sulla base di alcune condizioni che ne garantiscono la correttezza
+ In generale, possiamo riassumere un algoritmo iterativo nel seguente modo:
```C
//Pre: precondizione = quello che sappiamo essere vero all’inizio  
while (B)  
C  
//Post: postcondizione = quello che vogliamo sia vero alla fine
```
+ L'algoritmo è quindi corretto se, assumendo che valga `Pre` all'inizio, valga `Post` alla fine
+ Per capirlo, dovremo considerare una condizione chiamata **invariante di ciclo** $Inv$, una condizione che rimane sempre vera per tutta la durata dell'algoritmo, e per cui vale:
	1. $Pre \to Inv$ 
	2. $Inv \land \neg B \to Post$ 
	3.  $Inv \land B \to C$ 
+ Ad esse dobbiamo aggiungere una quarta condizione, ovvero la **funzione di terminazione**, ovvero una quantità che se viene eseguita $C$ diminuisce, ed è limitata inferiormente.
	4. Funzione di Terminazione $t$
+ Essa garantisce la terminazione dell'algoritmo
---
+ Se valgono queste condizioni, l'algoritmo è **corretto** 
+ Il problema adesso è scegliere l'invariante e la funzione di terminazione **adatte** al nostro algoritmo, in quanto possono esserne presenti **più di una**
---
+ L'invariante di per sé è anche utile come **guida** per lo sviluppo di un algoritmo iterativo

---
## Grafi
+ Segniamo alcune definizioni sui **grafi**
+ Vengono definiti come una coppia di due insiemi:
	* __Nodi__: Oggetti
	* __Archi__: Collegamenti fra più nodi
* Esistono più tipi di grafi:
	* __Orientati__: Nel considerare un arco conta la direzione
	* __Non__ orientati: Nel considerare un arco non conta la direzione
	* __Pesati__: Ogni arco possiede un "peso", una distanza
---
* Il __grado__ $\delta(u)$ di un nodo $u$ è il numero di __archi__ incidenti su di esso, nel caso di grafi orientato possiamo suddividerli in entranti ed uscenti
* Il __numero__ di __archi__ $m$ in un grafo con $n$ nodi è all'incirca:
	* $2m = \sum_{u \in V} \delta(u)$ 
* Il numero __massimo__ di archi è:
	* $\frac{n(n+1)}{2} \approx O(n^2)$ in grafi non orientati
	* $n^2$ in grafi orientati
* Un grafo con $n^2$ nodi viene detto __denso__. È abbastanza raro che accada
---
* Un __cammino__ è un insieme di nodi che rappresenta un percorso fra essi
* Un cammino __semplice__ è composto da nodi tutti differenti, con l'eccezione dell'inizio e della fine
* Un __ciclo__ è un cammino che inizia e finisce con lo stesso nodo
* Un grafo viene detto __aciclico__ se qualunque nodo $u$ è raggiungibile da un unico cammino
---
* Un grafo viene detto __connesso__ se esiste un cammino fra ogni nodo
* Un grafo __orientato__ viene detto 
	* __Fortemente__ connesso se esiste un cammino __in ogni direzione__ fra ogni nodo
	* __Debolmente__ connesso se esiste un cammino fra ogni nodo
---
* Un __albero__ libero è un grafo non orientato aciclico connesso ($m = n-1$)
* Un albero __ricoprente__ di un grafo è un __sotto-grafo__ possedente le proprietà di un albero libero
	* Nel caso di grafi pesati, è interessante considerare il minimo albero ricoprente, dotato degli archi con peso minore
---
* Un grafo può essere __rappresentato__ in più modi:
	* Liste di __archi__
	* Liste d'__adiacenza__
	* __Matrici__ d'adiacenza
* Ognuno di essi ha proprietà diverse, e ha costi differenti

| Operazioni             | Liste d'archi | Liste d'adiacenza           | Matrici d'adiacenza |
|------------------------|---------------|-----------------------------|---------------------|
| Spazio Richiesto       | $n + m$       | $n + m$                     | $n^2$               |
| Grado di un nodo       | $m$           | $\delta(u)$                 | $n$                 |
| Calcolo Nodi Adiacenti | $m$           | $\delta(u)$                 | $n$                 |
| Esiste Arco            | $m$           | $min(\delta(u), \delta(v))$ | $1$                 |
| Aggiungo Arco          | $1$           | $1$                         | $1$                 |
| Tolgo Arco             | $m$           | $\delta(u) + \delta(v)$     | $1$                 |
| Aggiungo Nodo          | $1$           | $1$                         | $n^2$               |
| Tolgo Nodo             | $m$           | $m$                         | $n^2$               |

+ La rappresentazione solitamente **preferita** è a **liste** d'adiacenza
	+ Nel caso in cui il grafo sia **denso**, può essere preferibile quella a **matrice** d'adiacenza
 ---
## Union-Find
+ Gli Union-Find sono strutture utilizzate nel caso di un universo composto da __sottoinsiemi__
* Possiamo eseguire tre operazioni su di essi:
	* __Mkset(a)__: Crea l'insieme che contiene solo a
	* __Find(a)__: Trova l'insieme che contiene a
	* __Union(A, B)__: Unisce gli insiemi A e B
* Vengono solitamente implementate come __alberi n-ari__, in due modi differenti:
	* __Quick-Find__
		* Gli alberi utilizzati sono tutti unari. Questo permette di __trovare facilmente__ ogni nodo richiesto, in tempo 1, ma ci metteremo __n__ per eseguire la __Union__,in quanto dovremo riorganizzare l'albero
	* __Quick-Union__
		* Gli alberi hanno struttura normale. L'__unione__ avverrà __semplicemente__ mettendo la radice di un albero come radice del secondo, in $O(1)$ , ma la __find__ potrà __peggiorare__ in $O(n)$ 
---
+ Per ottimizzare la versione **Quick-Union**, possiamo cambiare il modo in cui facciamo la Union così da rendere gli alberi __bilanciati__, e rendere la complessità della find __logaritmica__
* Possiamo fare:
	* Union By __Size__: 
		* L'albero con più nodi rimane radice
	* Union By __Rank__: 
		* L'albero più alto rimane radice
---
* Un'ulteriore metodo è la __Path Compression__: Nel compiere la find e la union ogni volta che attraversiamo un nodo, lo __stacchiamo__ e __attacchiamo__ alla __radice__, a meno che non lo sia già
* In questo modo l'__altezza__ __diminuisce__, e diminuisce la __complessità ammortizzata__, ovvero la complessità totale di una sequenza di operazioni
---
# 2 - Teoria Della NP-Completezza
+ I problemi possono essere classificati in diverse classi in base alle loro complessità: 
	* Un problema di classe __P__ è risolvibile e verificabile in tempo polinomiale
	* Un problema di classe __NP__ è verificabile in tempo polinomiale
		* Risulta che $P \subseteq NP$ 
* Tra i problemi NP esiste una sottoclasse, detta __NP-C__, contenente problemi NP-Completi. Questi hanno la caratteristica di essere di **difficoltà superiore od equivalente** a tutti gli altri problemi presenti in NP
	* Un problema è più difficile di un altro se, risolvendolo, posso risolvere anche il secondo
	* Questa nozione ha proprietà riflessiva e transitiva
* Per **dimostrare** che un **problema** è **NP-Completo** basta trovare un problema che sappiamo già essere NP-Completo e dimostrare che il primo problema è **riducibile** al secondo
* È interessante sapere una proprietà dei problemi NP-C: Se dimostrassimo che che un algoritmo di risoluzione di un problema NP-C è polinomiale, dimostreremmo che tutti i problemi NP-C sono risolvibili in tempo polinomiale, quindi anche tutti gli NP, e quindi risulterebbe $P = NP$ 
---
+ Un esempio di problema NP-Completo è il problema __SAT__, ovvero la soddisfacibilità di formule logiche in forma congiuntiva-disgiuntiva  (**Teorema di Cook**) (Ad esempio, $(A\vee B)\wedge(\neg B\vee C))$ 
	* Esso ha un ovvio algoritmo di risoluzione esponenziale
	* Ma ogni singola soluzione è verificabile in tempo polinomiale
---
* Gli algoritmi di verifica sono algoritmi di __decisione__. 
* Hanno la particolarità di essere funzioni, cui, posta un istanza del problema ed un __certificato__, ovvero una soluzione, ritornano vero se il certificato è soluzione per l'istanza
---
* Un problema può essere ridotto ad un secondo problema tramite una funzione di __riduzione__.
* Questa è una funzione con complessità __polinomiale__ che converte l'input di un problema nell'input di un secondo. Essa __mantiene__ la __correttezza__ dell'input nella trasformazione
---
* Tramite l'utilizzo di algoritmi non deterministici, è possibile dire che $P \subseteq NP$, ma si può dire che $P = NP$ ?
* Beh non si può sapere:
	* Per dire che $P \neq NP$ devo trovare un $p \in NP$ per cui non è possibile trovare un algoritmo polinomiale di soluzione
	* Per dire che $P = NP$  devo trovare un $p \in NP-C$ per cui esiste un algoritmo di risoluzione polinomiale. Per definizione, tutti gli altri saranno risolvibili in tempo comparabile
* Nessuna di queste due cose è stata dimostrata
---
* Problemi NP-Completi che abbiamo visto sono:
	* __3SAT__ - Variante di SAT in cui le formule disgiuntive hanno al massimo dimensione 3
	* __CLIQUE__ - Ritrovare un insieme di nodi tutti collegati fra loro in un grafo
	* __INSIEME INDIPENDENTE__ - Contrario di CLIQUE, ritrovare un insieme di nodi scollegati fra loro
	* __PROBLEMA DEL COMMESSO VIAGGIATORE__ - Dato un grafo pesato e orientato, ritrovare il minimo ciclo hamiltoniano
	* __PROBLEMA DELLO ZAINO__ - Dato uno zaino che può portare n chili e un insieme di oggetti, ognuno dotato di peso e valore, trovare il valore massimo trasportabile nello zaino
	* __COPERTURA DI VERTICI__ - Dato un grafo, ritrovare l'insieme di vertici che è collegato a tutti gli archi della figura
---
* Controllare gli appunti __cartacei__ per maggiori dettagli...
* *Vedere bene SAT, 3SAT, CLIQUE, INSIEME INDIPENDENTE*
 ---
 
# 3 - Algoritmi Deterministici
## Algoritmi Ricorsivi d'Esempio
### Ricerca Binaria Ricorsiva
#### Problema 
+ Data una sequenza $a$ di $n$ elementi, è possibile trovare un elemento $x$ al suo interno?
#### Algoritmo
```C
bin_search(x, a)
	return aux_bin_search(x, a, 0, n-1)

aux_bin_search(x, a, inf, sup)
	if (inf <= sup)
		mid = (inf + sup) / 2
		if (x = a[mid])
			return true
		if (x < a[mid])
			return aux_bin_search(x, a, inf, mid-1)
		else
			return aux_bin_search(x, a, mid+1, sup)
	return false			
```
#### Correttezza
+ La sua correttezza si può dimostrare tramite il **principio d'induzione forte**.
+ *dimostrazione negli appunti*
#### Complessità
+ Possiamo ricavarci la seguente **relazione di ricorrenza**
	+ $T(2^0) = 1$
	+ $T(2^k) = 1 + T(2^{k-1})$ 
+ Tramite sostituzione, otteniamo che:
	+ $T(2^k = n) = k+1 \approx \color{Apricot}\Theta (\log n)$ 
---
+ È un algoritmo di tipo **divide-et-impera**
 ---
### Torri di Hanoi
![[hanoi.jpg]]
#### Problema
+ Si hanno **tre pioli** verticali (sinistro, centrale, destro), e $n$ dischi  forati, di diametri tutti diversi, che si possono infilare nei pioli. All'inizio tutti i dischi sono su un piolo in ordine decrescente di  diametro. 
+ **Scopo** del gioco: spostare tutti i dischi su un altro piolo, eventualmente utilizzando il piolo rimanente, senza violare le  seguenti **regole**:  
	+ Si può spostare un solo disco per volta, cioè quello più in alto nel piolo di partenza  
	+ Non si può mettere un disco sopra un altro di diametro inferiore.  
+ **Il gioco è risolubile per qualunque numero $n$ di dischi?** 
+ E se lo è qual'è per ogni n la sequenza di mosse che lo risolve?
#### Algoritmo e Correttezza
+ Innanzitutto possiamo **dimostrare induttivamente** che il problema è risolvibile per ogni $n$.
	+ Passo **Base**:
		+ Il gioco è risolubile per $n = 1$. 
		+ Ovvio, perché un solo disco può essere spostato con una sola mossa da un piolo a un altro.
	+ Passo **Induttivo**:
		+ Assumendo (ipotesi induttiva) che il problema sia risolubile per $n − 1$, proviamo che è risolubile per $n$. 
		+ Infatti, per ipotesi induttiva è possibile spostare gli $n − 1$ dischi superiori dal piolo di partenza (sia `from`) al piolo ausiliario (sia  `aux`). 
		+ A questo punto è possibile spostare il disco più grande da `from` al polo di arrivo (sia `to`). 
		+ Infine, sempre per ipotesi induttiva è possibile spostare gli $n − 1$ dischi superiori da `aux` a `to`.
+ Sulla base di questi ragionamenti, possiamo sviluppare il seguente algoritmo di risoluzione:
```C
hanoi(n, from, aux, to)  
	if (n = 1) 
		move(from, to)  
	else  
		hanoi(n-1, from, to, aux)  
		move(from, to)  
		hanoi(n-1, aux, from, to)
```
#### Complessità
+ Il tempo di calcolo è proporzionale al numero di mosse effettuate
	+ $T(1) = 1$
	+ $T(n) = 2 \cdot T(n -1) + 1$ 
+ Questa è una **relazione di ricorrenza**. Espandendola, **tramite sostituzioni**, troviamo che la complessità dell'algoritmo è:
	+ $T(n) = 2^{n-1} + 1 \approx \color{Apricot}\Theta (2^n)$ 
+ La complessità spaziale dell'algoritmo corrisponde all'altezza dell'albero della ricorsione, ovvero
	+ $S(n) = \Theta(n)$
---
+ Questo è un problema **dimostrabilmente intrattabile** 
+ *dimostrazione negli appunti cartacei*
 
### QuickSort
#### Problema
+ Data una sequenza $s$ lunga $|s|$ , vogliamo ordinarla
#### Algoritmo
```C
quicksort(s)
	if (|s| > 1)
		togli un elemento p da s (per esempio il primo)
		partiziona gli altri elementi di s in due parti:
			una sequenza s1 contenente tutti gli elementi < p
			una sequenza s2 contenente tutti gli elementi ≥ p
			forma la sequenza s1 p s2
		quicksort(s1)
		quicksort(s2)
```
#### Correttezza
+ Possiamo dimostrare la correttezza dell'algoritmo tramite l'**induzione aritmetica**
	+ Passo **Base**:
		+ Una sequenza di lunghezza zero o uno è ordinata, e infatti l’algoritmo non fa nulla
	+ Passo **Induttivo**:
		+ Dopo la partizione si ha:
			+ elementi di $s_1 < p ≤$ elementi di $s_2$
		+ Per ipotesi induttiva, l’algoritmo ordina correttamente sequenze di lunghezza $< n$. Le sequenze $s_1$ ed $s_2$ hanno certamente lunghezza $< n$ perché è stato tolto $p$, quindi dopo le due chiamate ricorsive $s_1$ ed $s_2$ sono ordinate; 
		+ Allora la sequenza $s_1 \cdot p \cdot s_2$ è **chiaramente ordinata**.
#### Complessità
+ In generale, abbiamo la **relazione di ricorrenza**:
	+ $T(1) = \Theta(1)$
	+ $T(n) = \Theta(n) + T(r) + T(n-r-1)$ 
		+ $\Theta(n)$ è il tempo necessario per partizionare
+ Questa però si può riscrivere sia per il caso **migliore** che il caso **peggiore**
	+ Caso **migliore**:
		+ L'algoritmo partiziona sempre in parti di **eguale lunghezza**
			+ $T(1) = \Theta(1)$
			+ $T(n) = \Theta(n) + T(\frac{n}{2}) + T(\frac{n}{2})$ 
		+ Risulta che $T(n) = \color{Apricot}\Theta(n \log n)$ 
	+ Caso **peggiore**:
		+ L'algoritmo partiziona sempre ottenendo **una parte lunga 0**
			+  $T(1) = \Theta(1)$
			+ $T(n) = \Theta(n) + T(n-1)$ 
		+ Risulta che $T(n) = \color{Apricot}\Theta(n^2)$ 
---
+ In **media**, $T_{avg}(n) = \Theta(n \log n$ )
+ L'algoritmo è anch'esso **divide-et-impera**

---
## Algoritmi Iterativi d'Esempio
### Ricerca Binaria Iterativa
#### Algoritmo
```C
binary_search(x,a)  
	//Pre: inf = 0 ∧ sup = n − 1  
	inf = 0
	sup = n-1
	//Inv: x ∈ a[0..n − 1] ⇒ x ∈ a[inf..sup]  
	while (inf <= sup) 
		mid = (inf + sup)/2  
		if (x < a[mid]) 
			sup = mid-1  
		else if (x > a[mid]) 
			inf = mid+1  
		else 
			return true  
	//Post: x 6 ∈ a[0..n − 1]  
	return false
```
#### Correttezza
+ Dobbiamo trovare un **invariante** adatta
+ In questo caso, è sempre vero che l'elemento da cercare si trova sempre fra `inf` e `sup`
	+ $Inv: x ∈ a[0\cdots n − 1] ⇒ x ∈ a[inf\cdots sup]$
+ Usando questa invariante, troviamo anche la **condizione di controllo**
	+ Essa è la dimensione dell'array, la quale non deve mai essere 0
	+ Dunque è limitata da $inf \leq sup$ 

---
### Bandiera Olandese
![[dutch2.jpg]]
#### Problema
+ Si ha una sequenza di $n$ elementi rossi, bianchi e blu. 
+ Vogliamo modificare la  sequenza in modo da avere prima tutti gli elementi **rossi**, poi tutti i **bianchi**, poi tutti i **blu**.
+ Vogliamo inoltre esaminare ogni elemento **una volta sola**.
+ Le operazioni che possiamo effettuare sulla sequenza sono:
	+ `swap(i,j)` scambia di posto due elementi, per $1 ≤ i, \; j ≤ n$
	+ `colour(i)` restituisce Red, White, Blue per $1 ≤ i ≤ n$
#### Algoritmo
+ Indichiamo con `Red/White/Blue(i, j)` l'espressione "gli elementi da i a j sono tutti di quel colore"
+ Inoltre indicheremo con `R`, `W` e `B` gli indici ignoti dei primi elementi di quel colore
+ Quindi, determiniamo la **post-condizione** come:
	+ `Post:` $Red (1, W − 1) ∧ White(W, B − 1) ∧ Blue(B, n)$
+ E l'**invariante**:
	+ `Inv:` $Red (1, U − 1) ∧ White(W, B − 1) ∧ Blue(B, n) ∧ U ≤ W$
+ Da essi, otteniamo il seguente algoritmo:
```C
//Pre: U = 1 ∧ W = B = n + 1  
//Inv: Red (1, U − 1) ∧ White(W, B − 1) ∧ Blue(B, n) ∧ U ≤ W  
while (U < W) 
	switch (Colour(W-1)  
		case Red : swap(U, W-1); U = U + 1  
		case White : W = W - 1  
		case Blue : swap(W-1, B-1); W = W-1; B = B-1  
//Post: Red (1, W − 1) ∧ White(W, B − 1) ∧ Blue(B, n)
```
#### Correttezza
+ Per comprenderne la correttezza, valutiamo le quattro condizioni necessarie:
	1. $Pre \to Inv$ 
		+ Questa vale banalmente, in quanto inizialmente tutti gli insiemi dell'invariante sono vuoti
	2. $Inv \land \neg B \to Post$ 
		+ Vale poiché in questo caso viene che $U = W$, trasformando `Inv` in `Post`
	3.  $Inv \land B \to C$ 
		+ Vale per costruzione
	4. Funzione di Terminazione $t$
		+ La funzione di terminazione è il numero di valori ignoti, ovvero $U-W$
		+ Il loro numero è **limitato** inferiormente a 0

---
### Selection Sort
+ *Negli appunti cartacei*
 ---
## Visite di un Grafo
+ Per visitare un grafo si utilizzano metodi simili a quelli utilizzati nella visita degli alberi, con la differenza della necessità del segnare i nodi già visitati.
+ Useremo la seguente notazione:
	+ Nodo **Bianco**: Inesplorato
	+ Nodo **Grigio**: Aperto, visita iniziata
	+ Nodo **Nero**: Chiuso, visita finita
---
+ In questi algoritmi si usa un sottoinsieme dei nodi da cui essi vengono estratti, detto **frangia**. Questa può essere una pila, una coda, un heap, etc. a seconda dell'algoritmo utilizzato
+ È possibile generare un **albero di ricoprimento** tramite la visita effettuata
---
### Visita in Ampiezza (BFS)
#### Algoritmo
```C
//visita nodi di G raggiungibili a partire da s  
BFS(G,s): 
	for each (u nodo in G) 
		marca u come bianco; 
		parent[s] = null  
	Q = coda vuota  
	Q.add(s); 
	marca s come grigio;  
	while (Q non vuota)  
		u = Q.remove() //u non nero  
		visita u  
		for each ((u,v) arco in G)  
			if (v bianco)  
			marca v come grigio; 
			Q.add(v); 
			parent[v]=u  
		marca u come nero
```
+ Questo algoritmo utilizza una **coda** come frangia.
+ Esso genera un **sotto-grafo dei predecessori** a partire dal nodo $s$, che è effettivamente un albero di ricoprimento
+ Da quest'albero otteniamo la **distanza**, ovvero la **lunghezza minima** di un cammino da $s$ a qualunque altro nodo
+ È possibile calcolarsi questo cammino tramite:
```C
path(s, u):
	if(s == u)
		return u
	return path(s, parent[u]) + u
```
#### Correttezza
+ La correttezza dell'algoritmo può essere ricavata tramite la seguente invariante:
	+ `Inv:` nodi nell'albero = nodi neri + nodi grigi
 ---
### Visita in Profondità (DFS) Iterativa
#### Algoritmo
```C
//visita nodi di G raggiungibili a partire da s
DFS(G,s)   
	for each (u nodo in G) 
		marca u come bianco; 
		parent[s] = null  
	S = pila vuota  
	S.push(s); 
	marca s come grigio;  
	while (S non vuota)  
		u = S.pop()  
		if (u non nero)  
			visita u  
			for each ((u,v) arco in G)  
				if (v bianco) 
					marca v come grigio; 
					S.push(v); 
					parent[v]= u  
				else if (v grigio) 
					S.push(v); 
					parent[v]= u //modifica il padre  
			marca u come nero
```
+ Questo algoritmo utilizza una **pila** come frangia.
+ Un nodo può rientrare nella pila più volte, tante volte quanto i suoi archi
#### Complessità
+ Ci mettiamo all'incirca
	+ $O(n)$ per **marcare** i nodi
	+ Ogni nodo viene **inserito** almeno una volta nella pila, e poi può essere tirato fuori e **reinserito** un numero di volte pari ai suoi archi. Quindi, all'incirca $O(n + m)$ 
	+ **Esploriamo** gli **archi** di ogni nodo. A seconda della struttura, impieghiamo
		+ Lista di archi: $O(nm)$
		+ Liste d'adiacenza: $O(n + m)$
		+ Matrice di adiacenza: $O(n^2)$ 

### Visita in Profondità (DFS) Ricorsiva
#### Algoritmo
```C
DFS(G)  
	for each (u nodo in G) 
		marca u come bianco; parent[u]=null  
	for each (u nodo in G) 
		if (u bianco) DFS(G,u)  

DFS(G,u)  
	//inizio visita  
	visita u; 
	marca u come grigio  
	for each ((u,v) arco in G)  
		if (v bianco)  
			parent[v]=u  
			DFS(G,v)  
	//marca u come nero  
	//fine visita
```

## Cammino Minimo in un Grafo Pesato
+ In un grafo **pesato**, ad ogni arco è associato un peso o costo.
+ Il cammino minimo fra due nodi è il cammino con **distanza minima**
### Dijkstra (Johnson, 1977)
#### Problema 
+ Dati un grafo orientato **pesato** $G$ con **pesi non negativi** e un nodo di partenza $s$, trovare per ogni nodo $u$ del grafo il **cammino minimo** da $s$ a $u$.
#### Algoritmo
+ L'idea di base è di effettuare una visita in **ampiezza**, in cui ad ogni passo:
	+ Per i nodi già visitati si ha la distanza e l’albero T di cammini **minimi**  
	+ Per ogni nodo non ancora visitato si ha distanza provvisoria = lunghezza minima di un cammino in T più un arco  
	+ Si estrae dalla coda un nodo a distanza provvisoria minima (che risulta essere la distanza)  
	+ Si aggiornano le distanze provvisorie dei nodi adiacenti al nodo estratto tenendo conto del nuovo arco in T
+ Allo scopo di facilitare l'estrazione del nodo minimo, memorizzeremo i nodi in **code a priorità**, sviluppate come **heap binari**
	+ Quest'ultimo permette operazioni di modifica economiche, in $\theta(\log{n})$ 
```C
Djikstra(G,s)  
	for each (u nodo in G) 
		dist[u] = ∞ // tutti i nodi sono bianchi  
	parent[s] = null; 
	dist[s] = 0 // s diventa grigio  
	Q = heap vuoto  
	for each (u nodo in G) 
		Q.add(u,dist[u])  
	while (Q non vuota)
		//estraggo nodo a distanza provvisoria minima, 
		//u diventa nero  
		u = Q.getMin()   
		for each ((u,v) arco in G) //v diventa o resta grigio  
			if (dist[u] + c(u,v) < dist[v]) // se v nero falso
				parent[v] = u; 
				dist[v] = dist[u] + c(u,v)  
				Q.changePriority(v, dist[v]) //moveUp
```
#### Correttezza
+ Innanzitutto ci ricaviamo come `post`
	+ `Post:` $\forall u, dist[u] = d[u]$ 
		+ Tutti hanno costo minimo
+ L'**invariante** sarà composta da due condizioni:
	1. Per ogni nodo nero, $dist[u] = d[u]$ 
	2. Per ogni nodo rimanente, $dist[u] = d/Q[u]$ 
		+ Ciò vuol dire che ogni nodo nell'heap ha la migliore distanza rispetto ai nodi neri
+ La seconda condizione è solo un'**ausiliaria** per dimostrare la prima
+ Valutiamo quindi:
	1. $Pre \to Inv$ 
		+ Questa vale banalmente, in quanto:
			1. Non ci sono nodi neri (tutti i nodi sono in coda)
			2. La distanza è per tutti infinito, tranne che per $s$ per cui vale 0.
	2. $Inv \land \neg B \to Post$ 
		+ Valgono per costruzione
	3.  $Inv \land B \to C$ 
		1. Viene estratto dalla coda il nodo u con dist[u] minima, quindi, per l’invariante (2), tale che esiste un cammino π da s a u minimo tra quelli costituiti da tutti nodi neri tranne l’ultimo. Tale cammino è allora anche il **minimo in assoluto** fra tutti  i cammini da s a u. 
		+  Infatti, supponiamo per assurdo che esista un cammino da s a u di costo minore di quello di π. Questo cammino deve necessariamente contenere nodi non neri, altrimenti avrebbe costo maggiore o uguale a quello di π. Sia w il primo di tali nodi non neri. Il cammino quindi è della forma π1π2 con π1 cammino da s a w e π2 cammino da w a u. Ma il cammino π1, essendo formato solo da nodi neri tranne l’ultimo, ha costo maggiore o uguale a quello di π, e quindi a maggior ragione π1π2 ha costo maggiore o uguale a quello di π. 
		+ Quindi, aggiungendo il nodo u estratto dalla coda all’insieme dei nodi neri, l’invariante (1) vale ancora, ossia, è ancora vero che per tutti i nodi neri, compreso il nuovo nodo nero u, è stato trovato il cammino minimo.
		2.  Poiché l’insieme dei nodi neri risulta modificato per l’aggiunta di u, occorre però ripristinare l’invariante (2): per ogni  nodo v in Q, dist[v] deve essere la lunghezza del minimo fra i cammini da s a v i cui nodi sono tutti, eccetto v neri; ma  adesso fra i nodi neri c’è anche u, quindi bisogna controllare se per qualche nodo v adiacente a u il cammino da s a v  passante per u è più corto del cammino trovato precedentemente, e in tal caso aggiornare dist[v] e parent[v].
	4. Funzione di Terminazione $t$
		+ La funzione di terminazione è il numero di nodi nell'heap
		+ Il loro numero è **limitato** inferiormente a 0

#### Complessità
+ I costi necessari sono:
	+ **Inizializzazione** di tutti i nodi come bianchi: $O(n)$
	+ $n$ **estrazioni** dallo heap: $O(n \log n)$
	+ **Ciclo interno**: ogni arco viene percorso una volta, e per ogni nodo adiacente si ha eventuale moveUp nello heap, quindi $O(m \log n)$
+ La complessità finale è $\color{Apricot}\Theta ((m+n)\log{n})$.
	+ Se il grafo fosse particolarmente denso, la complessità diventerebbe $O(n^2 \log n)$, diventando peggiore della versione originale 
 ---
## Minimo Albero Ricoprente (MST)
+ Molto speso può risultare utile trovare un __albero minimo ricoprente__ di un grafo, ovvero un sotto-grafo connesso, aciclico e ricoprente, in cui la somma degli archi è **minima**
### Prim
#### Algoritmo
+ L'idea principale è molto __simile al Dijkstra__. Ad ogni ciclo salviamo le distanze minori del nodo che analizziamo, fino a svuotare l'heap.
+ Cerchiamo il nodo più vicino all'albero già costruito
```C
Prim(G,s)  
	for each (u nodo in G) 
		marca u come non visitato //necessario  
	for each (u nodo in G) 
		dist[u] = ∞  
	parent[s] = null; 
	dist[s] = 0  
	Q = heap vuoto  
	for each (u nodo in G) 
		Q.add(u, dist[u])  
	while(Q non vuota)  
		//estraggo nodo a minima distanza dai neri  
		u = Q.getMin() 
		marca u come visitato (nero)  
		for each ((u,v) arco in G)  
			if (v non visitato && c(u,v) < dist[v] )  
				parent[v] = u; 
				dist[v] = c(u,v)  
				Q.changePriority(v,dist[v]) //moveUp
```
#### Correttezza
+ L'**invariante** è ancora una volta composta da due parti:
	1. $T ⊆ MST$ per qualche $MST$ minimo albero ricoprente di $G$
		+ $T$ è l'albero costruito dall'algoritmo
	2. per ogni nodo $u \neq s$ in $Q$,  $dist[u] =$ costo minimo di un arco che collega u a un nodo nero
+ Valgono quindi 
	1. $Pre \to Inv$ 
		1. Vale banalmente perché T è vuoto (non ci sono nodi neri)
		2. Vale banalmente perché non ci sono nodi neri e la distanza è per tutti infinito, tranne che per s.
	3. $Inv \land B \to C$ 
		+ *nelle note*
	4. Funzione di Terminazione $t$
		+ La funzione di terminazione è il numero di nodi nell'heap
		+ Il loro numero è **limitato** inferiormente a 0
#### Complessità
+ Essa è calcolabile in modo analogo a Dijkstra
 ---
### Kruskal
#### Algoritmo
+ A differenza dell'algoritmo di Prim, **Kruskal** costruisce il MST unendo più **sotto-alberi** fra loro ad ogni turno
+ La sequenza utilizzata ha l'unico requisito di essere ordinata, quindi si può usare un semplice **array** per realizzarla
```C
Kruskal(G)  
	s = sequenza archi di G in ordine di costo crescente  
	T = foresta formata dai nodi di G e nessun arco  
	while (s non vuota)  
		estrai da s il primo elemento (u,v)  
		if (u,v non connessi in T) 
			T = T + (u,v)  
	return T
```
#### Correttezza
+ Similmente a Prim, l'**invariante** è
	+ `Inv:` $T ⊆ MST$ per qualche $MST$ minimo albero ricoprente di $G$
+ Valgono quindi 
	1. $Pre \to Inv$ 
		+ Vale banalmente, in quanto non ci sono archi in T
	 3. $Inv \land B \to C$ 
		+ *nelle note*
	4. Funzione di Terminazione $t$
		+ La funzione di terminazione è il numero di nodi in $s$
		+ Il loro numero è **limitato** inferiormente a 0
#### Complessità
+ I costi necessari sono:
	+ Creare $s$: $O(m \log m)$ 
+ Il problema è: quanto costa **controllare se due nodi sono già connessi**?
+ Questo dipende dall'**implementazione** 
+ Utilizzando una struttura **Union-Find Quick-Union**, debitamente ottimizzata, la complessità diviene:
	+ $\color{Apricot}O(m \log m)$ 
 ---
## Ordinamento Topologico
+ L'Ordinamento Topologico consiste nell'__ordinare__ i __nodi__ di un __grafo aciclico orientato__ (DAG) a partire dal nodo sorgente, sulla base dell'__ordine degli archi__
* Esiste sempre almeno un ordine topologico
### Primo Algoritmo (TPSort)
#### Algoritmo
+  Si basa sulla seguente idea:
	* A ogni giro, __prendiamo__ un nodo __sorgente__, e lo mettiamo in una __lista__
	* __Abbassiamo__ di uno il numero di __nodi entranti__ in tutti i suoi nodi "figli"
	* Al ciclo successivo, dovrebbe esserci almeno un __nuovo__ nodo __sorgente__, e ripartiamo da lì
```C
topologicalsort(G)  
	S = insieme vuoto // nodi sorgente
	Ord = sequenza vuota // nodi ordinati
	for each (u nodo in G) 
		indegree[u] = indegree di u //m passi  
	for each (u nodo in G) 
		if (indegree[u] = 0) 
			S.add(u) //n passi  
	while (S non vuoto) // in tutto m passi  
		u = S.remove()  
		Ord.add(u) //aggiunge in fondo  
		for each ((u,v) arco in G)  
			indegree[v]--  
			if (indegree[v]=0) 
				S.add(v)  
	return Ord
```
#### Complessità
+ Ha la complessità di una comune visita, $\color{Apricot}O(m + n)$
 ---
### Secondo Algoritmo (TSDFS)
#### Algoritmo
+ Esso consiste in una **visita in profondità con timestamp**
	+ Effettuo una visita __DFS__, ma su ogni nodo che visito lascio un __numero__, che indica il momento in cui l'ho visitato
	* Quando finisco di visitare i figli del nodo, aggiungo un __secondo timestamp__ su di esso
	* Aggiungendo i nodi nella __lista__ secondo l'__ordine dei timestamp__ dovrebbe fornirci una lista ordinata dei nodi
```C
DFS(G)  
	for each (u nodo in G) 
		marca u come bianco; 
		parent[u]=null 
	time = 0  
	for each (u nodo in G) 
		if (u bianco) 
			DFS(G,u) 

DFS(G,u,T)  
	time++; 
	start[u] = time //inizio visita  
	visita u; 
	marca u come grigio  
	for each ((u,v) arco in G)  
		if (v bianco)  
			parent[v]=u  
			DFS(G,v)  
	time++; 
	end[u] = time //marca u come nero  
	//fine visita
```
#### Correttezza
+ **Nelle note**, in generale, qualunque sia il modo in cui raggiungo due nodi con arco $(u, v)$, sarà sempre vero che $end[v] < end[u]$ 
#### Complessità 
+ Ha la complessità di una comune visita, $\color{Apricot}O(m + n)$

 ---
## Componenti Fortemente Connesse (CFC)
+ Dato un grafo G orientato, come facciamo a trovare le __componenti fortemente connesse__ (CFC) ?
	* Una CFC è un sotto-grafo formato da nodi mutualmente raggiungibili
* Calcolati i CFC, è possibile calcolare il **grafo quoziente**, un grafo in cui i nodi sono le CFC del grafo, e gli archi i collegamenti fra essi
### SCC
#### Algoritmo
+ Possiamo considerarlo una __generalizzazione__ dell'__ordinamento topologico__
	* Inizialmente ottengo un ordinamento topologico del grafo tramite __DFS__ con Timestamp
	* Ottengo una __copia trasposta__ del grafo (Con gli archi in ordine opposto), e comincio una __DFS__ del grafo a partire dal nodo con timestamp maggiore fino ad arrivare al nodo di partenza, Questo __cammino__ sarà una CFC e, una volta salvata, rimuoveremo questi nodi dal grafo
	* Ripetiamo fino all'__esaurimento__ dei nodi
```C
SCC(G)  
	DFS(G,Ord) //aggiunge i nodo visitati a Ord in ordine di fine visita  
	//si noti che non occorre calcolare i tempi di fine visita  
	GT = grafo trasposto di G  
	Ord↔ = sequenza vuota //ordine topologico delle c.f.c.  
	while (Ord non vuota)  
		u = ultimo nodo non visitato in Ord //si trova in una c.f.c. sorgente  
		C = insieme di nodi vuoto  
		DFS(GT ,u,C) //aggiunge nodi visitati in C  
		Ord↔.add(C) //aggiunge in fondo  
	return Ord↔
```
#### Complessità
+ Ha la complessità di una comune visita, $\color{Apricot}O(m + n)$

## Programmazione Dinamica
+ La programmazione dinamica è un __paradigma__ di programmazione, come il divide-et-impera
* Essa si basa sul partire da problemi __piccoli__ e, risolvendoli, arrivare a risolvere problemi più __grandi__ (__bottom-up__). Nel mentre le soluzioni ritrovate possono venire __memorizzate__, in modo da poter essere __riutilizzate__ in seguito
### Longest Common Subsequence (LCS)
![[lcs.jpg]]
#### Problema
+ Dobbiamo cercare la più **lunga sotto-sequenza comune** a due stringhe
#### Algoritmo
+ È possibile utilizzare più algoritmi per risolvere il problema
+ Quello che vediamo utilizza la **Programmazione Dinamica**
+ L'idea è:
	+ Costruiamo una matrice LCS con m+1 righe ed n+1 colonne.
	+ La prima riga e la prima colonna vanno riempite con la **sequenza vuota**, di lunghezza 0.
	+ In ogni casella non occorre memorizzare tutta la LCS ma basta mettere: 
		+ Se si ha lo **stesso carattere** sulla riga e sulla colonna, una “**freccia diagonale”**, **aumentando di 1** la lunghezza rispetto alla casella puntata dalla freccia
		+ Se sulla riga e sulla colonna ci sono **due caratteri diversi**, una **freccia** verso la **cella** di lunghezza **maggiore** fra la contigua sopra e la contigua a sinistra (se hanno uguale lunghezza si sceglie per esempio quella sopra). La **lunghezza** è la **stessa** di quella della **cella** puntata dalla freccia
	+ La LCS corrispondente a ciascuna casella si ottiene, dall’**ultimo elemento** al primo, **seguendo** le **frecce** a partire dalla casella
+ Ecco un esempio:
![[lcs2.png]]
+ Sono evidenziati i percorsi per ritrovare le sequenze ACAB e ACBA
+ L'algoritmo avrà quindi forma:
```C
for (i = 0; i <= m; i++) 
	L[i,0] = 0  
for (j = 0; j <= n; j++) 
	L[0,j] = 0  
	
for (i = 1; i <= m; i++)  
	for (j = 1; j <= n; j++)  
		if (X[i] = Y[j])  
			L[i,j] = L[i-1,j-1] + 1; 
			R[i,j] = ↖  
		else if (L[i,j-1] > L[i-1,j])  
			L[i,j] = L[i,j-1];
			R[i,j] = ←  
		else 
			L[i,j] = L[i-1,j];
			R[i,j] = ↑
```
#### Complessità
+ La complessità corrisponde al tempo necessario a costruire la matrice, ovvero $\Theta(mn) \approx \color{Apricot}\Theta(n^2)$ 
+ Nonostante possa sembrare alto, è sempre **meglio** del tempo dell'algoritmo divide-et-impera, esponenziale
+ La complessità **spaziale** è **uguale**. È possibile ottimizzare la matrice in modo tale da arrivare ad avere complessità spaziale **lineare**
 ---
### Floyd-Warshall
#### Problema
+ Dato un grafo orientato pesato, troviamo la **distanza** (lunghezza del cammino minimo) fra tutte le coppie di nodi nel grafo
#### Algoritmo
+ È facile capire come convenga utilizzare la Programmazione Dinamica per questo problema
+ L'idea alla base è **dividere** in **sotto-problemi** scritti come "qual'è il peso minimo di un cammino da X a Y che usa come nodi quelli da 1 a K?" (Cammini K-Vincolati)
* **Definizione** Induttiva
	* Caso **Base**
		* In questo caso, K=0
		* Se X=Y, il cammino è 0
		* Se X $\neq$ Y il cammino è lungo quanto il cammino fra X e Y. Se non esiste, è $\infty$ 
	* Passo **Induttivo**
		* Usiamo K = K +1
		* Se il cammino non usa K, allora è uguale a $d^K(X,Y)$ 
		* Altrimenti è $d^K(X,K+1) + d^K(K+1,Y)$ 
```C
FloydWarshall(G)  
	for each (x,y : nodi in G)  
		D0[x,y] = 0 se x=y, 
			      c(x,y) se x != y ed esiste arco (x,y), 
			      ∞ altrimenti  
	for (k=1; k <= n; k++)  
		for each (x,y : nodi in G) 
			Dk[x,y] = Dk−1[x,y]  
			if (Dk−1[x,k] + Dk−1[k,y] < Dk[x,y]) 
				Dk[x,y] = Dk−1[x,k] + Dk−1[k,y]  
	return Dn
```
#### Complessità
+ La complessità temporale coincide con quella spaziale, ed è ovviamente **cubica** ($\color{Apricot}\Theta (n^3)$ ) (Dobbiamo costruire $n$ matrici $n \times n$)
+ È possibile arrivare ad una complessità **quadratica**, utilizzando un unica matrice
---
+ È possibile modificare l'algoritmo in modo da ottenere anche **l'albero dei cammini minimi** 
+ Dovremo includere una matrice ulteriore, la **matrice dei predecessori**, in cui vengono memorizzati i predecessori di un valore $y$ nel cammino minimo $(x, y)$
```C
FloydWarshall(G)  
	for each (x,y : nodi in G)  
		D[x,y] = 0 se x=y, 
				 cx,y se x != y ed esiste arco (x,y), 
				 ∞ altrimenti  
		Π[x,y] = x se x != y ed esiste arco (x,y), 
				 NULL altrimenti  
	for (k=1; k <= n; k++)  
		for each (x,y : nodi in G)  
			if (D[x,k] + D[k,y] < D[x,y])  
				D[x,y] = D[x,k] + D[k,y]  
				Π[x,y] = Π[k,y]  
	return D,Π
```
+ Questa matrice indica il sotto-grafo dei cammini minimi
+ È possibile ottenere questi cammini minimi tramite l'algoritmo
```C
shortest_path(Π,x,y)  
	if (x=y) 
		return x  
	else if (Π[x,y] = null) 
		return ... [non esiste cammino]  
	else 
		return shortest_path(Π,x,Π[x,y]) · y
```
 ---
# 4 - Algoritmi Randomizzati
## Ordinamento
### Il Guardarobiere Distratto
+ Un classico problema è quello del **guardarobiere distratto**:
	* **n** persone vanno ad una festa, tutti con un cappello differente, e lo consegnano all'ingresso al guardarobiere. All'uscita, ne ricevano uno casuale. 
	* **Quante persone ricevono il proprio cappello?**
* Si risolve facilmente tramite le proprietà delle **VA**
	* Consideriamo ogni persona come una VA indicatrice di Bernoulli. La possibilità che valga 1, ovvero che abbia il suo cappello, è $\frac{1}{n}$, e corrisponde al suo valore atteso
	* Possiamo calcolare il **valore atteso della somma di VA**, ovvero di tutte le persone, come la **somma dei loro valori attesi**. 
	* Questa corrisponderà a $n \cdot \frac{1}{n}$, ovvero **1** 
	* Ci aspettiamo che **una** sola persona torni a casa col proprio cappello
 ---
### Las Vegas QuickSort
+ Il LVQuickSort è una variante del QuickSort, in cui ad ogni giro scegliamo un pivot differente, a caso
```C
LVQuickSort(S)
	if |S| ≤ 1
		then return S
	else
		1. campiona s da S con probabilità uniforme
		2. forma S< e S≥ confrontando ogni numero di S \ {s} con s
		3. LVQuickSort(S≥)
		4. LVQuickSort(S<)
		5. return la concatenazione di S<, s e S≥
```
* Come fa a essere **più efficiente** di quello normale?
* Per capirlo, prendiamo una VA indicatrice $I(i, j)$. Questa variabile ha valore 1 se gli elementi in posizione i e j vengono confrontati nel corso dell'algoritmo
* Questo accade solo se uno dei due viene scelto come **pivot**, per cui
	* $P(I(i, j) = 1) = \cfrac{2}{j - i +1}$ 
* Pensiamo ora ad una seconda VA indicatrice, $X$, la quale indica il numero di **confronti totali** eseguiti in un esecuzione dell'algoritmo. Qual'è il suo valore medio?
	* $\mathbb{E}[X] = \sum_i \sum_j \mathbb{E}[I(i, j)] = \sum_i \sum_j \cfrac{2}{j - i +1}$ 
* Questo valore è una **sommatoria** molto particolare, la quale non converge a 0 abbastanza velocemente da poter essere calcolata normalmente
* Possiamo **approssimarne** il valore tramite il seguente **integrale**
	* $\int^{n}_{i + 1} \cfrac{2}{t - i + 1} dt \approx 2 \ln(n - i + 1)$ 
* Questo valore rimane molto basso. Osservando dati empirici, noteremo che i tempi di esecuzione medi si avvicineranno molto spesso a questo valore, cementando l'algoritmo in $\color{Apricot}O(n \log n)$
* È quindi **sempre preferibile** alla versione **iterativa**

## Programmazione Lineare
![[Pasted image 20230614110010.png]]
+ I problemi di Programmazione Lineare sono problemi di **ottimizzazione**, in cui abbiamo fissato dei **vincoli** (limiti) ed una **funzione**, di cui vogliamo ottimizzare i valori, che sia massimizzarli o minimizzarli, all'interno di questi vincoli
+ Esistono **più algoritmi** per risolvere questi problemi
### Metodo del Simplesso
+ L'idea è semplice: È ovvio che la soluzione non si troverà mai su di un punto interno all'area, ma al massimo su uno dei vertici
+ Esso quindi
	+ Sceglie un **vertice**
	+ Si sposta su un vertice adiacente per cui il valore viene **maggiormente ottimizzato**
	+ Questo continua, fino a che non accade una di queste due cose:
		+ L'algoritmo **diverge**, perché la funzione cresce illimitatamente in una direzione
		+ L'algoritmo si **arresta**, poiché non si trovano ulteriori vertici dal valore migliore
			+ In questo caso, l'ultimo vertice risulta essere il massimo
+ Quest'algoritmo è **spesso efficiente**, **ma** nel caso di problemi con molte dimensioni, il costo cresce in modo **esponenziale** con la dimensione dei vertici
 ---
### LVIncrementalLP
+ Questo è un algoritmo randomizzato **Las Vegas**, che permette di allontanarsi dal caso peggiore nel caso di input piccoli
```C
LVIncrementalLP(V)
	1. if n = 1 or m = 1  
		determina x∗  
		return x∗  
	2. campiona un vincolo v uniformemente in V  
	3. LVIncrementalLP(V \ {v})  
	4. if x∗ non viola v  
		   return x∗  
	   else  
		   proietta i vincoli in V \ {v} su v ottenendo V ′  
	       LVIncrementalLP(V ′)
```

#### Complessità 
+ Se $T (m, n)$ è il valore atteso del tempo di esecuzione dell’algoritmo per $m$ vincoli in $n$ dimensioni:
	+ $\color{Apricot}T (m, n) \color{White}≤ \color{WildStrawberry}T (m − 1, n) \color{White}+ \color{Aquamarine}O(n) \color{White}+ \color{LimeGreen}\cfrac{n}{m}\color{White} \cdot\Bigl(\color{Lavender}O(nm) \color{White}+ \color{GreenYellow}T (m − 1, n − 1)\color{White}\Bigl)$
+ Dove:
	+ $\color{WildStrawberry}T (m − 1, n)$ è il costo della ricorsione su $V \backslash \{v\}$
	+ $\color{Aquamarine}O(n)$ è il costo del controllo della violazione di $x^*$ 
	+ $\color{LimeGreen}\cfrac{n}{m}$ è la probabilità che $v$ sia un estremo
	+ $\color{Lavender}O(nm)$ è il costo delle proiezioni di vincoli in $V \backslash \{v\}$ su $v$
	+ $\color{GreenYellow}T (m − 1, n − 1)$ è il costo della ricorsione su un problema con un vincolo ed una dimensione in meno
+ Tramite il metodo della sostituzione, si arriva a dire che, per $b$ abbastanza grande, vale:
	+ $\color{Apricot}T(m, n) \leq bmn!$ 

## Teoria dei Giochi
+ Introduciamo ora dei concetti della teoria dei giochi, utili per valutare le prestazioni degli algoritmi Las Vegas
---
+ Dato un gioco a somma 0, descritto da una matrice, il teorema di **Von Neumann** dice è sempre possibile avere due strategie miste per il quale il gioco ha valore $V$
	+ $\max_p \min_q p^TMq = \min_q \max_p p^TMq = p^TMq = V$
---
+ Immaginiamo ora di star giocando ad un gioco in cui la posizione $i, j$ della matrice rappresenta il **tempo** impiegato da un algoritmo $j$ su un input $i$ di un problema
+ Possiamo ritrovare la **complessità inferiore** del problema con il valore seguente:
	+ $V_C = \min_{A∈A} \max_{I∈I} T(I, A)$ 
		+ Questo è il tempo impiegato dall'**algoritmo migliore** sull'**input peggiore**
+ Vediamo che, nell'uso di strategie miste, si ottengono risultati molto interessanti:
+ **Principio di Yao**:
	+ Per ogni distribuzione $p$ e $q$
		+ $\color{Apricot}\min_{A \in \mathbb{A}} \; \mathbb{E}[T(I_p, A)] \; \leq \;  \max_{I \in \mathbb{I}}\; \mathbb{E}[T(I, A_q)]$ 
		+ Il tempo impiegato dall'algoritmo **migliore** sull'input **medio** è sempre **minore** od uguale al tempo impiegato dall'algoritmo **medio** sull'input **peggiore**
+ Ciò ci dice che, per trovare il **tempo migliore di un algoritmo randomizzato**, possiamo **studiare** il comportamento dell'**algoritmo deterministico ottimo** su una distribuzione di **input** che ci **conviene** 
## Valutazione di un Albero di un Gioco
+ Studiamo un **gioco** dalle seguenti regole:
	+ Ci sono due giocatori
	+ Ogni giocatore può scegliere una fra $d$ mosse ad ogni turno
	+ Ogni giocatore cerca di vincere
+ Costruiamo un albero del gioco $T_{d, k}$ atto a rappresentare le strategie attuabili, con le seguenti caratteristiche:
	+ $T_{d,k}$ ha $d^{2k}$ foglie che si trovano a distanza $2k$ dalla radice
		+ Nel caso binario $2^{2k} = 4^k$
	+ I **nodi** interni possono essere di tipo:
		+ Se la distanza dalla radice è **pari**, **MIN**
		+ Se la distanza dalla radice è **dispari**, **MAX**
	+ Il **valore del gioco** è un numero associato ad ogni nodo
+ Il **Problema della Valutazione del Gioco** consiste nel determinare il **valore della radice** tenendo conto che:
	+ Ogni **foglia** restituisce il proprio **valore**
	+ Ogni **nodo** restituisce il valore **massimo** o **minimo** dei suoi $d$ figli, sulla base del tipo del nodo
		+ Nel caso utilizzassimo come valori 1 o 0, potremmo sostituire **MAX** e **MIN** con **OR** e **AND** 
	+ Uno dei giocatori vorrà **massimizzare** il valore del gioco, l'altro **minimizzarlo**
![[giocotree.png]]
+ Risulta ovvio che, per valutare il valore di questi alberi, partendo dalle radici, ci troveremo spesso a dover controllare i valori di **tutte** le foglie!
	+ Non molto conveniente...
+ Ma se utilizzassimo un'algoritmo **randomizzato**?
+ È dimostrabile che, nel caso binario:
	+ Il costo atteso per valutare una qualsiasi realizzazione $T_{2,k}$ è al più $\color{Apricot}3^k$.
+ **Caso base** ($k$ = 1):
![[tree-base.png]]
+ Valutiamo l'albero a **sinistra**
	+ Nella metà dei casi, ci basterà leggere **una sola foglia** per valutare l'OR, beccando l'1, altrimenti dovremmo leggerne due. Questo vale per entrambe i nodi OR
		+ Il costo è quindi $\cfrac{1}{2}(1 + 2) + \cfrac{1}{2}(1 + 2) = 3$
+ Valutiamo l'albero a **destra**
	+ Se campioniamo l'OR che ritorna 0, ci basta vedere le sue due foglie per valutare l'intero albero. Altrimenti, è possibile che si leggano tutte e quattro le foglie
		+ Il costo è quindi $\cfrac{1}{2}(2) + \cfrac{1}{2}(2 + 2) = 3$
 + **Passo Induttivo**:
+ Arrivati al nodo $k$, avremo impiegato massimo $3^{k-1}$ per calcolare i valori dei figli
	+ Se questo nodo è un **OR**, se valutiamo il primo figlio ed è un **1**, finiamo qui, altrimenti guardiamo entrambi
		+ Il costo è quindi $\cfrac{1}{2}(3^{k-1}) + \cfrac{1}{2}(2\cdot 3^{k-1}) = \cfrac{3^k}{2} < 3^{k}$
	+ Similmente, se questo nodo è un **AND**, se valutiamo il primo figlio ed è uno **0**, finiamo qui, altrimenti guardiamo entrambi
		+ Il costo è quindi $\cfrac{1}{2}(3^{k-1}) + \cfrac{1}{2}(2\cdot 3^{k-1}) = \cfrac{3^k}{2} < 3^{k}$
---
+ Questo algoritmo ha un costo sub-lineare, in quanto $3^k = n^{\log_4 3} = n^{0.793} < n$ 
+ Quindi il suo **costo** nel caso peggiore è **inferiore** a quello di un algoritmo **deterministico**
---
+ Possiamo invece trovare un limite **inferiore** all'algoritmo sfruttando il **Principio di Yao**
+ Esiste un algoritmo **deterministico** capace di risolvere il problema in modo **molto efficace**
+ Questo è il **Depth First Pruning** (DFP)
+ Esso **riscrive** in modo equivalente gli **alberi**, utilizzando per ogni nodo l'operatore **NOR**
+ Supponiamo che le probabilità dei valori delle foglie, **indipendenti dagli altri valori**,  siano:
	+ $P(1) = p = \cfrac{3 - \sqrt{5}}{2}$ 
	+ $P(0) = 1 - p = \cfrac{\sqrt{5} - 1}{2}$ 
+ Facendo i calcoli, osserviamo che la **probabilità** che un nodo **NOR** valga 1 **coincide** con $p$
+ Ora, calcoliamo il tempo impiegato a valutare un albero alto $h$
	+ $W_T (h) = W_T (h − 1) + (1 − p)W_T (h − 1) = (2 − p)W_T (h − 1) \to (2 − p)^h$
+ Sostituendo $h$ con $\log_2 n$ otteniamo che:
	+ $W_T(\log_2 n) = (2 - p)^{\log_2 n} \to \color{Apricot} n^{0.694} < n^{0.793}$ 
+ Questo sembrerebbe **suggerirci** che **esiste** un **algoritmo randomizzato migliore** di quello che abbiamo visto
+ È vero? **No**!
+ Questo perché abbiamo considerato i valori dei nodi **indipendenti** fra loro, ma questo **non è vero** nella realtà
 ---
## Taglio Minimo
+ Dato un grafo, questo algoritmo determina il **numero minimo** di **archi** da "**tagliare**" per ottenere due **sotto-grafi**
```C
MCMinCut(G)
	for i = n to 2  
		1. campiona un arco m in G con probabilità uniforme e 
		   identifica i suoi vertici, u e v, in un nuovo vertice uv 
		2. rimuovi tutti gli archi che univano i vertici u e v, incluso 
		   quello campionato, e mantieni tutti gli archi che 
		   incidono sul nuovo vertice uv  
		3. i ← i − 1  
	C `e costituito dagli archi che uniscono gli ultimi due vertici rimasti di G
```
+ Questo è un algoritmo di tipo **Montecarlo**: 
	+ Ciò vuol dire che il risultato **non sempre** è quello **corretto**, **ma** c'è un **alta probabilità** che lo sia, per cui **basta eseguirlo** un determinato **numero di volte** e osservare i risultati per ottenere il risultato voluto
---
#### Correttezza
+ Come facciamo a dimostrare che questa probabilità è **alta**?
+ Beh, possiamo notare che l'algoritmo fallisce nel caso in cui sceglie un arco appartenente al taglio minimo in uno dei campionamenti
+ Sappiamo che se $k$ è il risultato del taglio minimo, vale che il numero minimo di archi $m$ vale:
	+ $m = \cfrac{kn}{2}$ 
	+ Altrimenti esisterebbe almeno un vertice di grado minore di $k$ i cui archi costituiscono un taglio minimo di dimensione strettamente minore di $k$
+ Quindi, ogni volta che campioniamo un arco, la probabilità che io peschi un arco nel taglio minimo è:
	+ $P(E) \leq \cfrac{k}{\frac{kn}{2}} = \cfrac{2}{n}$ 
+ Quindi la probabilità opposta è
	+ $P(F) \geq 1 - \cfrac{2}{n}$ 
+ Ora, valutiamo la probabilità che ad ogni campionamento, non peschiamo alcun nodo del taglio minimo:
	+ $P(F1, F2, \cdots, Fn) \; \geq \; \prod^{n-2}_{i = 1}\Bigl(1 - \cfrac{2}{n - i + 1}\Bigl)  \; \to \; \cfrac{2}{n(n-1)} \; \approx \; \color{Apricot}\cfrac{2}{n^2}$ 
+ Se eseguiamo l'algoritmo $m$ volte, la probabilità di **non ottenere** almeno un taglio minimo è:
	+ $\color{Apricot}\mathbb{P}(m) < \Bigl(1 - \frac{2}{n^2}\Bigl)^{m-1}$ 
+ Quindi, al salire di $m$, la probabilità è altamente bassa
+ Dato che il taglio minimo è sempre **minimo**, è **facile da identificare** fra i risultati sbagliati. Quindi, anche con un piccolo numero di esecuzioni, è **altamente probabile** ritrovare il valore del taglio minimo con questo algoritmo
## Accordo Bizantino
+ Un classico problema:
	+ Durante una battaglia l’esercito bizantino è diviso in tre accampamenti al comando dei generali $genU$ , $genV$ ed $genZ$.
	+ Uno tra $genU$ , $genV$ e $genZ$ è un **traditore** ma la sua identità è ignota ai due generali leali.
	+ Ogni sera, i generali possono comunicare tra loro spedendosi un messaggio in cui manifestano la loro intenzione di attaccare, $Attack$, o di ritirarsi, $Withdraw$. 
	+ I generali **leali** spediscono un messaggio **consistente** (lo stesso messaggio agli altri due generali), mentre il generale **traditore** può spedire messaggi **diversi** al fine di infliggere il massimo danno.
	+ Se le armate dei generali leali attaccano o si ritirano assieme la maggior parte dei soldati tornerà a casa. Se, invece, prendono una decisione diversa entrambe le armate andranno incontro a una pesante disfatta.
	+ **Esiste un protocollo di comunicazione capace di garantire il raggiungimento del consenso tra i due generali leali in un numero finito di round?**
+ Comprendiamo come questo problema possa essere importante, specie in sistemi informatici, in cui ci si può ritrovare a comunicare con processi mal-funzionanti, "traditori"
---
+ Per studiare dei metodi di risoluzione, proviamo ad immaginare $n$ processi, di cui $f$ difettosi, che cercano di accordarsi sul valore di un bit.
	+ Essi si spediscono dei messaggi in modo sincrono, ovvero ricevono sempre $n$ messaggi ad ogni round
+ I generali leali devono accordarsi su un **protocollo**, capace di determinare una decisione finale sul valore del bit, che rispetti le proprietà di:
	+ **Consenso**:
		+ I bit dei processi affidabili assumono tutti lo stesso valore, ovvero, dopo un certo numero di round, se $p_j$ è un qualunque processo affidabile allora $b(j) = v$;
	+ **Validità**:
		+ Se il valore iniziale di tutti i processi affidabili è lo stesso, ovvero $b_0(j) = v^∗$ per ogni processo affidabile $p_j$, allora $v = v^∗$. Il raggiungimento del consenso, pertanto, non può essere basato su un valore concordato di $default$.
+ Si può dimostrare che il **consenso** è **raggiungibile** solo se
	+ $n ≥ 3f + 1$
---
+ Un primo algoritmo deterministico per risolvere il problema è basato sull'EIG (**Exponential Information Gathering**)
+ Esso consiste nella creazione da parte di ogni generale leale di un albero contenente le informazioni ricevute dagli altri generali sui valori dei bit ricevuti da tutti
---
+ Esiste anche un protocollo **Montecarlo** capace di risolvere il problema
+ Esso si basa sull'utilizzo di una moneta globale, un risultato ottenuto randomicamente da una moneta onesta, calcolato ad ogni round e comunicato a tutti i processi
```C
MCByzantineGeneral
	while (TRUE)  
		1. trasmetti b(j) agli altri n − 1 processi  
		2. ricevi i valori spediti dagli altri n − 1 processi  
		3. maj(j) ← valore maggioritario tra i ricevuti (incluso il proprio)  
		4. tally(j) ← numero dei valori uguali a maj(j)  
		5. if tally(j) ≥ T  
			   then b(j) ← maj(j)  
		   else if testa  
			   then b(j) ← 1  
		   else b(j) ← 0
```
#### Correttezza
+ Questo algoritmo funziona in tutti i casi:
	+ I $2f + 1$ processi affidabili sono **unanimemente d’accordo**: 
		+ Il consenso è raggiunto poiché al passo 5, per un qualunque processo affidabile $j$, risulta che $tally(j) ≥ T$ . Questo è vero sia se $b(j) = v_0$ al primo round, sia se $b(j) = v$ in qualche round successivo.
	+ **Non** tutti i processi affidabili **concordano**: 
		+ Dobbiamo considerare due ulteriori casi. 
			+ Nel primo non esiste alcun processo affidabile$j$ per cui $tally(j) ≥ T$ : 
				+ il consenso è quindi raggiunto nel primo round e coincide con l’esito del lancio della moneta. 
			+ Nel secondo, per qualche processo  $j^∗$ avremo $tally(j^∗) ≥ T$ . 
				+ Poiché i processi faulty sono al più $f$ e per almeno $f + 1$ processi affidabili il bit spedito è $maj(j^∗)$, non può esserci alcun processo affidabile $k^∗$ per il quale 
					+ $tally(k^∗) ≥ T$ con $maj(k^∗) \neq maj(j^∗)$.
			+ Pertanto, con probabilità $\frac{1}{2}$, dopo l’esito del lancio della moneta, tutti i processi affidabili convergeranno su $maj(j∗)$. 
+ Affinché funzioni, i processi affidabili devono essere almeno $2f + 1$, così che nessun processo possa ricevere una maggioranza di bit dal valore erroneo 
## Test di Primalità
+ È possibile implementare un **test di primalità** randomizzato Montecarlo basato sul **numero di testimoni** che un numero sia **composto**
```C
MCPrimalityTest(n)   
	1. s = 0  
	2. q = n − 1  
	3. while (q pari)  
		s ← s + 1  
		q ← q/2  
	4. campiona a uniformemente a caso in {2, 3, . . . , n − 2}  
	5. calcola x ≡ aq (mod n)  
	6. if x ≡ ±1  
		return n "probabilmente primo"  
	7. while s − 1 ≥ 0  
		x ≡ x2 (mod n)  
		if x ≡ −1 (mod n)  
			return n "probabilmente primo"  
		s ← s − 1  
	8. return n "composto"
```
+ *da approfondire*
## Verifica di Uguaglianza Matriciale
+ L'algoritmo di moltiplicazione fra due matrici è molto **inefficiente**, essendo in $O(n^3)$, a causa del numero di moltiplicazioni necessarie
	+ Nel caso di matrici $2\times2$ è possibile ottenere lo stesso risultato con 7 moltiplicazioni $O(7)$
+ Esiste però un algoritmo randomizzato Montecarlo che permette di risolvere in un tempo **lievemente minore**, con un concetto molto semplice:
	+ Invece di verificare $AB = C$ verifichiamo $ABr = Cr$ dove $r$ è un vettore formato da $\{0, 1\}$, campionati randomicamente, con $p = \frac{1}{2}$ 
	+ Le moltiplicazioni con i **vettori** sono in $\color{Apricot}O(n^2)$ 
```C
MCMatrixMultiplicationVerifyer(A, B, C)
	1. campiona r uniformemente a caso in {0, 1}n  
	2. s ← Br // P (rj = 0) = P (rj = 1) = 1/2 per j = 1, . . . , n  
	3. t ← As // t = A(Br)  
	4. u ← Cr  
	5. if t = u  
		   return "probabilmente AB = C"  
	   else  
		   return "AB 6 = C"
```
---
#### Correttezza
+ Riflettiamo:
	+ Se $AB \neq C$, allora esiste $D = AB - C$, il quale possiede **almeno** un elemento della sua matrice **non nullo**
	+ In questo caso $A(Br) = Cr$ avviene solamente se nel moltiplicare $D$ con $r$ viene ad **annullarsi** proprio **quell'elemento** non nullo
	+ Ovvero se:
		+ $∑_k d_{ik}r_k = 0$
	+ Chiamando $y = ∑_{k \neq j} d_{ik}r_k$ otteniamo
		+ $∑_k d_{ik}r_k \; = \; d_{ij}r_j + y$ 
	+ Possiamo quindi riscrivere la probabilità d'errore come la probabilità che questa somma valga $0$. 
	+ Siccome $y$ può valere o non valere $0$, possiamo riscriverlo tramite le formule della probabilità totale:
		+ $P (d_{ij} r_j + y = 0) = P (d_{ij} r_j + y = 0|y = 0)P (y = 0) + P (d_{ij} r_j + y = 0|y \neq 0)P (y \neq 0)$
	+ E dato che possiamo intuire:
		+ $P (d_{ij} r_j + y = 0|y = 0) = P (d_{ij} r_j = 0) = P (r_j = 0) = \cfrac{1}{2}$
		+ $P (d_{ij} r_j + y = 0|y \neq 0) = P (r_j = 1 ∩ d_{ij} = −y) ≤ P (rj = 1) = \cfrac{1}{2}$
	+ Otteniamo infine:
		+ $P (A(Br) = Cr) = P (d_{ij} r_j + y = 0) ≤ \cfrac{1}{2} P (y = 0) + \cfrac{1}{2} P (y \neq 0) = \cfrac{1}{2}$ 
+ La probabilità di sbagliare è quindi inferiore ad $\cfrac{1}{2}$ !
+ Eseguendo l'algoritmo $k$ volte, **la probabilità di sbagliare diminuirà in modo geometrico**, divenendo $\color{Apricot}\cfrac{1}{2^k}$ 
## Uguaglianza Tramite Fingerprinting
+ Immaginiamo di avere due amici, Alice e Bob, i quali vogliono verificare che un file, di cui entrambi posseggono una copia, sia effettivamente lo stesso file
+ Devono verificarne l'uguaglianza in modo efficiente, senza doversi inviare l'intero file, magari molto pesante
+ Presentiamo un metodo Montecarlo che si basa sui seguenti concetti:
---
+ **Teorema fondamentale della Teoria dei Numeri**
	+ $\lim_{x \to \infty} \cfrac{\pi(x)}{\frac{x}{\ln(x)}} = 1$
		+ $\pi(x)$ è il numero di primi minori o uguali ad $x$
	+ Ciò ci dice che, al crescere di $x$, il rapporto fra il numero ed il suo logaritmo naturale è una buona stima del numero di primi **inferiori** ad esso
+ **Maggiorazione del numero di Fattori Primi**
	+ I fattori primi di un numero $n < 2^l$ sono al massimo $l$
		+ Del resto, se fossero di più, essendo quasi tutti i fattori maggiori di 2, $n$ sarebbe certamente un numero maggiore di $2^l$ 
+ **Impronta digitale**
	+ Sia $p$ un numero primo compreso fra $2$ e $l^2$ e $n$ un numero naturale minore di $2^l$.
	+ L'impronta digitale $f(n)$ di $n$ è definita come:
		+ $f(n) := n \mod p$
---
+ L'idea del nostro algoritmo consiste nel valutare i nostri due **file**, leggendoli **come numeri binari**.
	+ Se è il file è lungo $l$ bit, risulta ovvio che il numero ottenuto dovrà essere minore di $2^l$
	+ Questo numero verrà passato in una funzione di fingerprinting, usando come $p$ un numero primo minore di $l^2$
		+ $f(a)$ dovrà essere memorizzato in al massimo $2 \ln(l)$ bit
	+ Inviamo quindi $f(a)$ al destinatario, il quale lo confronterà con $f(b)$, verificando la possibile uguaglianza
```C
MCStringEqualityVerifyer(a, b)
	1. campiona p, primo, uniformemente a caso in {2, . . . , l^2}  
	2. f (a) ← a (mod p)  
	3. f (b) ← b (mod p)  
	4. if |f (a) − f (b)| ≡ 0 (mod p)  
		   return "input probabilmente uguali"  
	   else  
		   return "input diversi"
```
---
#### Correttezza
+ Riflettiamo:
	+ Se $a \neq b$ allora $1 < |a − b| ≤ 2^l$
	+ Ciò vuol dire che $|a - b|$ ha al più $l$ fattori primi
	+ Otteniamo quindi la probabilità d'errore come:
		+ $\color{Apricot}\mathbb{P} \color{White}= \cfrac{l}{\frac{l^2}{2 \ln(l)}} = \color{Apricot}\cfrac{2 \ln(l)}{l}$ 
+ Del resto, il falso positivo può avvenire solo se il numero primo scelto è in comune a $f(a), f(b)$ di due file differenti
	+ Questo è molto improbabile