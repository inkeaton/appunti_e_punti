# Codici Numerici
---
## Numeri Positivi: Rappresentazione in Base 2
* Ogni cifra indica una potenza di 2, da destra verso sinistra
	* 00001011 = $2^0$ + $2^1$ + $2^3$ = 11

## Numeri Negativi 
### Rappresentazione a Modulo e Segno
* Il segno è rappresentato dal primo bit a sinistra, 0 indica un numero positivo, 1 un numero negativo
* è una rappresentazione molto efficace, ma non rende possibili semplici algoritmi di calcolo
	* ES: __1__ 001 = -1
			  __0__ 001 = 1 
### Rappresentazione Complemento a 1
* Il numero negativo è l'inverso del numero positivo
* Non funzionano ancora gli algoritmi
	* ES: 1011 = -4
### Rappresentazione Complemento a 2
* Il numero negativo è l'inverso del numero positivo, a cui viene poi sommato 1
* Questa bizzarra rappresentazione permette gli algoritmi di somma e sottrazione
* Inoltre, esiste una sola versione del numero 0
	* ES: 7 + (-8) 
		* 00000111 + 
		- 11111000   =  
		- 11111111      == -1 
### Rappresentazione in Eccesso $2^{n-1}$ 
* In una rappresentazione fissa ad $n$ bit, viene sommato ad ogni numero il valore $2^{n-1}$ 
* Il valore 0 sarà sempre unico, ma non si potranno applicare gli algoritmi citati in precedenza
* Si potranno rappresentare quindi i numeri compresi fra  $[-2^{n-1}, 2^{n-1}-1]$  

## Numeri Razionali
### Rappresentazione Fixed Point
* Semplicemente si "allarga" la rappresentazione in base 2, considerendo anche le potenze negative
* l'unico problema è che si deve decidere il punto in cui mettere la virgola, rendendo impossibile rappresentare tutti i numeri con un unica convenzione
### Rappresentazione Floating point 
* Il numero si ottiene attraverso il seguente calcolo:
	* $V = -1^s * 2^e * m$ 
* Vediamo la versione codificata su 32 bit, in cui:
	* $s$ indica il __Segno__ del numero
	* $e$ indica l'__Esponente__, un numero codificato in rappresentazione in eccesso 128, in cui però -127 e 128 indicano cose differenti, e non vengono usati:
		* 128 indica che si tratta di una __forma non normalizzata__, e quindi il numero viene letto in modo differente, con la mantissa letta come un numero in Fixed Point, con la virgola posizionata a 127 posizioni precedenti
			* Un numero non noramlizzato è lo 0, rappresentato come una sequenza di trentadue zeri
		* -127 indica  che il risultato __non è un numero__, per cui il valore potrebbe essere risultato di 0/0, -n/0, n/0	
		* $m$ è la __Mantissa__, la parte frazionaria del numero, codificata su 23 bit,  ma considerando un 1 davanti, diventando in realtà codifica su 24 bit
		
## Codice ad Espansione
* Si possono codificare numeri in modo da espandere il numero di cifre su cui essere codificati solo quando necessario
* Ad esempio, posso rappresentare 00, 01 e 10 su 2 bit, ma 11 non rappresenterà 3, ma che il numero è ora codificato su 5 bit. Arrivati a 11111 si ripeterà lo stesso
* Questi metodi vengono usati nella codifica del codice macchina

## Ridondanza 
* R = n° combinazioni totali / n° combinazioni usate
* Un codice __minimale__ ha un R compresa fra 1 e 2, se è maggiore di 2 è __ridondante__

## Entropia
* L'Entropia è un valore che indica il contenuto informativo di una comunicazione, calcolato con la seguente formula:
	* $E(x)=−∑[Pr(x1)∗log2(Pr(x1))]$
* Se il valore è uguale al numero di bit dell'informazione, il contenuto informativo è massimo. Ma se sappiamo già qualche probabilità, il valore diminuirà
* Cerchiamo di avere un Entropia bassa, ma non azzerata, poichè in tal caso la comunicazione sarebbe inutile 
## Errori e Distanza di Hamming
* Si possono usare codici ridondanti per poter determinare errori nel codice
* Infatti, se uso un codice con un bit in più rispetto a quello richiesto, avrò il doppio delle combinazioni, con metà non utilizzate. Basta che decido che quelle utilizzate sono quelle con una specifica __distanza di Hamming__ (differenza bit a bit fra combinazioni)
* Se incappo in una combinazione non usata, so che c'è stato un errore. Per poter riconoscere più tipi di errore, bisogna aumentare ancora la ridondanza, o usare altri metodi
* Nel caso di D.H. alta, è anche possibile intuire quale sia la stringa originaria, e correggere l'errore

## Errori e Bit di Parità
* In pratica, useremo dei bit in più, quelli con posizione potenza di 2, per indicare i valori contenuti negli altri bit di informazione
* Questi bit di parità conterranno un valore che indica __la somma dei valori contenuti nei bit che hanno bisogno di quella potenza per ottenere il rispettivo valore posizionale in somma di potenze di due__
	* ES: 12 = 8 + 4, quindi dovrò aggiungere sommare ai bit di parità 8 e 4 il valore contenuto in 12 

## Cancellazioni
* Oltre a possibili errori, sono possibili anche cancellazioni. Un modo per prevenirle è __dividere le informazioni in più trance__, a cui associamo dei bit di parità
* è infatti più improbabile che si cancellino entrambe, e tramite i bit di parità potremmo risalire al valore originale


---
# Circuiti Logici e Sequenziali
## Circuiti Combinatori
* I principali circuiti sono:
	* NOT
	* AND
	* OR
	* XOR 
* E le loro negazioni
* ![[Circuiti.gif]]
* Queste funzioni a 2 ingressi possono essere allargate tramite la __proprietà associativa__
## Algebra Binaria e Rappresentazioni Pratiche
* Possiamo utilizzare l'AND come un $\cdot$ e l'OR come un $+$ per implementare una sorta di __Algebra__
* Questo ci permetterà di rappresentare circuiti più complessi come somme di prodotti o prodotti di somme
* Tutti i circuiti possono essere rappresentati usando solo OR, AND e NOT, oppure usando solo NAND
* Un problema che ci rimane è come arrivare alla __forma minimale__, ovvero l'espressione minima in grado di rappresentare la funzione. Questo ci permetterà di semplificare la struttura reale del circuito
* Una rappresentazione utile a comprendere la rappresentazione minima sono le __Mappe di Karnaugh__
* ![[Schermata del 2022-06-18 11-53-53.png]]
* In essa, i diversi casi dei due ingressi sono separati nelle due righe, e vengono scritti usando il __Codice Gray__, variante del codice binario, utilizzata allo scopo di avere distanza di Hamming uguale ad uno fra ogni cifra
* Per dedurre la rappresentazione minimale, bisogna prendere a gruppi di potenze di 2 i valori 1, considerando che le celle "wrappano" intorno
* Il metodo più semplice per rappresentare una funzione più complessa è utilizzare circuiti, usando i simboli delle funzioni elementari, collegate con dei cavi
* Un altro è il __BDD, Albero di Decisione__, una struttura ad albero in cui ad ogni nodo si sceglie fra 0 ed 1. è necessario un ordine stabilito fra gli ingressi, e a seconda di cosa si sceglie sarà più difficile giungere ad una forma minimale
## Circuiti Logici
### Multiplexer
* ![[Schermata del 2022-06-18 12-02-06.png]]
* Questo circuito è in grado di scegliere quale valore mandare in uscita fra i due ingressi, sulla base del valore del terzo ingresso, denominato di Controllo
* Questa circuito può essere allargato a più ingressi, ma avrebbe bisogno di tanti bit di controllo quanti bit d'informazione necessari in ingresso
* Esso viene rappresentato con il simbolo __MPX__
### Demultiplexer
* ![[Pasted image 20220618120752.png]]
* Il circuito opposto al Multiplexer, sceglie un uscita su cui far uscire l'input
* Simbolo __DMPX__
* Osservando la struttura del DMPX, possiamo notare una parte che rimane in comune al MPX, ovvero il __DECODER__
* ![[Pasted image 20220618121023.png]]
## Circuiti Numerici
* Per la somma si possono implementare due tipi di Circuiti:
* ![[Pasted image 20220618162552.png]]
* l'__Half-Adder__ o semi sommatore è in grado di calcolare valori che arrivano a 2
* Per valori superiori serve il __Full-Adder__
* ![[Pasted image 20220618162729.png]]
* Questo risolve i calcoli su 1 bit. Per calcoli superiori, serve combinare più Full ed Half Adder
* Un circuito simile sarebbe anche in grado di compiere sottrazioni e cambi di segno
* __Moltiplicazione__ e __divisione__ si ottengono shiftando rispettivamente a sinistra ed a destra i valori del numero, nel caso di moltiplicazioni per potenze di 2
* Nel caso della divisione, sarà necessario un circuito in grado di dedurre il nuovo valore del bit di segno a sinistra
* Questi circuiti sarnno poi contenuti nell'__ALU__, un circuito capace di tutte le operazioni logiche ed aritmetiche della macchina
## Circuiti Sequenziali
* Questi sono circuiti dotati della particolarità di avere il valore d'uscita che varia anche in base ai valori precedenti
### Flip Flop Set Reset
![[Pasted image 20220619160546.png]]
### Flip Flop Tipo D
![[Pasted image 20220619160629.png]]
* Per poter memorizzare il valore precedente in un momento preciso si usano i circuiti __Master-Slave__
* Questi circuiti cambiano il valore in uscita solo al momento dello scattare del calore di CLOCK
* ES ![[Pasted image 20220619160800.png]]
### Flip Flop Tipo T
![[Pasted image 20220619160837.png]]
### Flip Flop Tipo JK
![[Pasted image 20220619160906.png]]
## Registri
* Sono circuiti costituiti dall'unione di più circuiti sequenziali
### Registro Tipo D
![[Pasted image 20220619161144.png]]
* Costituito da flip flop tipo D, è in grado di memorizzare valori
### Registro tipo T
![[Pasted image 20220619161310.png]]
* Questo circuito è formato da flip flop tipo T, ed è in grado di memorizzare una combinazione ed aumentarla di 1 ad ogni ciclo di CLOCK
* A questa struttura si può aggiungere una funzione di RESET, per poter contare da 0
### Registro a Scorrimento
![[Pasted image 20220619161452.png]]
* Questo circuito è in grado di compiere la moltiplicazione per 2, shiftando i valori del numero verso l'alto
* Può essere anche usato per trasmettere informazioni
---
# Architettura Von Neumann
---
## RAM
* Una memoria RAM di tipo __statico__ è formata dall'unione di molti registri di tipo D
* Ognuno di questi verrà considerato una cella, sulla quale possiamo leggere o scrivere, identificata da un indirizzo
* Essa riceve in input dato da scrivere ed indirizzo a cui accedere, oltre ad un controllo codificato su 2 bit
	* C/S indica se lavorare sulla RAM
	* R/nW indica, nel caso C/S sia 1, se leggere o scrivere
* Questa sarà poi collegata alla CPU tramite il bus di sistema
* Il problema di questo dispositivo è però che è molto costoso e complesso, con quindi grandi possibilità di errori
* Questo ci spinge ad utilizzare una RAM di tipo __dinamico__
* Questa salva solo temporaneamente i dati, e quindi deve spesso compiere l'operazione di REFRESH, ricopiando i suoi dati su se stessa, però è molto più semplice ed economica
* Esiste un organizzazione in grado di ottimizzare gli accessi alla RAM
* Questa è la __memoria associativa__, in cui invece di riconoscere indirizzi, ogni cella è identificata da un campo tag, il quale viene controllato quasi immediatamente tramite un circuito comparatore, e confrontato con quello richiesto dalla CPU
* Questo velocizza di un sacco le operazioni
* Solitamente viene implementata come memoria statica
## CPU ed Esecuzione Istruzioni
* La CPU è l'unità principale del computer, che svolge le istruzioni richieste
* Oltre a contenere l'ALU, essa contiene anche dei registri in cui salvare dati a cui poter accedere molto velocemente 
* La CPU esegue le istruzioni in RAM tramite 3 fasi:
	* Fetch: Uso il valore salvato nel registro PC come indirizzo per la cella in RAM in cui si trova l'sitruzione
	* Decode: Decodifico l'istruzione appena letta
	* Execute: Viene eseguita l'istruzione vera e propria
* Questo implica che ogni istruzione viene tecnicamente eseguita in 3 cicli di CLOCK
## Input, Output e Interruzioni
* I dispositivi di Input ed Output funzionano in modo simile alla RAM, direttamente collegati alla CPU, e contenendo dei registri "memory mapped" all'interno
* Per poter interagire coi programmi, viene implementato il sistema delle __interruzioni__ 
	* Ogni dispositivo è collegato alla CPU tramite il BUS con un filo
	* Quando devono intergire, mandano un bit sul filo. La CPU controlla se viene segnalata un interruzione prima di ogni fase di FETCH, ed in caso positivo, causa una BRANCH ad un programma detto __interrupt handler__, il quale ha lo scopo di gestire l'interruzione. Si può stabilire una gerarchia di priorità di interruzioni
	* Una volta gestita l'interruzione, il programma riparte da dove era stato interrotto
## Virtualizzazione della Memoria
* In un sistema POSIX, la RAM viene organizzata in 4 sezioni:
	* Codice: contiene le istruzioni che la CPU deve compiere
	* Dati: i dati su cui il computer lavora
	* Stack: Contiene dati temporanei predisposti dal sistema
	* Heap: spazio che i programmi possono richiedere
* Per velocizzare il sistema, ed impedire eventuali errori, dobbiamo trovare un modo per cui la CPU possa accedere solo alle sezioni di RAM necessarie al momento
* Useremo degli __indirizzi virtuali__, i quali saranno tradotti in quelli fisici da un nuovo dispositivo l'__MMU__
* Allo scopo di gestire indirizzi errati o rischieste di aumento di spazio (per heap e stack) implementiamo le __trap__, simili alle interruzioni, con la differenza che queste indicano solitamente un errore nel programma, spesso non risolvibile
* Per gestire la memoria, suddivideremo la memoria dispnibile in segmenti denominati __pagine__
* -   Gli indirizzi avranno tre campi: 
    -   N° SEGMENTO: indica il segmento in cui siamo 
    -   PAGE #: Indica il numero di pagina dentro al segmento (quindi relativo al segmento) 
    -   OFFSET: indirizzo relativo all'inizio della pagina
-   La traduzione avverrà su due livelli: 
    -   Prima, l'MMU controllerà la tabella dei segmenti, la quale conterrà l'informazione della posizione della tabella delle pagine di quel segmento 
    -   Esisterà una tabella delle pagine per segmento, che conterrà l'indirizzo fisico della pagina 
    -   Nel caso PAGE # sia troppo grande rispetto al n° di pagine all'interno del segmento, verrà segnalata una TRAP 
    -   La TLB funzionerà allo stesso modo, con la differenza di contenere oltre al PAGE # il N° SEGMENTO nel TAG. La __TLB__ conterrà gli indirizzi fisici delle pagine, per velocizzare l'accesso a pagine a cui si ha già fatto accesso
## Istruzioni Privilegiate
* Il sistema possiede normalmente due stati in cui lavorare, USER e SUPERVISOR, il secondo consente di compiere istruzioni __privilegiate__, più pericolose, e sono spesso riservate all'OS
* In caso di bisogno, i programmi applicaztivi possono segnalare con una TRAP il bisogno di passare alla modalità SUPERVISOR. In questo caso le TRAP vengono chiamate SYSTEM CALL
## Virtualizzazione della CPU
* Possiamo fare in modo che i programmi vedano solo parte della memoria, così che la CPU possa eseguirne più di uno alla volta
* Questo sistema può essere usato anche per installare più OS su di una macchina, i quali verranno gestiti da un programma denominato __hypervisor__ 
## Unità Disco e SWAP
* Le unità disco sono dispositivi di memoria statici, strutturati a blocchi, spesso di dimensioni pari ad una pagina di RAM
* Essi possono essere utilizzati per memorizzare dati, ed implementare __ibernazione__ e __paginazione a richiesta__
	* La prima consiste nel salvare in una zona denominata __SWAP__ i dati della RAM, così da poter memorizzare per molto più tempo quei dati senza dover eseguire il refresh
	* La seconda consiste nel conservare le pagine in SWAP, e caricarle in RAM solo quando esplicitamente richiesto 
	* Questo sembrerebbe rallentare il programma, ma tramite tecniche timesharing si attenua questo problema, e si ottiene addirittura una velocizzazione, nel caso di una SWAP >> RAM, dato che è come se avessimo una RAM di dimensione superiore
* Nel caso in cui avessimo tutte le pagine caricate in RAM e dovessimo caricarne ancora una, dobbiamo decidere quale togliere
* Per farlo si usa spesso l'__algoritmo LRU__, il quale permette di comprendere quale pagina non viene usata da più tempo, e quindi decide di sostituire quella. Lo farà utilizzando un bit di uso, il quale viene portato a 1 quando la pagina viene usata, e periodicamente riportato a 0
---
# Architettura Pipeline
---
## Località e Cache
* Osservando l'esecuzione dei programmi, si possono notare le seguenti proprietà:
	* LOCALITA' nel TEMPO:
		* Se il processore richiede l'indirizzo i, è molto probabile che questo venga nuovamente richiesto in futuro
	* LOCALITA' nello SPAZIO
		* Se il processore richiede l'indirizzo j, è molto probabile che richieda in futuro l'indirizzo j +1, j + 2, etc.
* Queste possono essere sfruttate per velocizzare l'esecuzione dei programmi, tramite l'introduzione di una memoria __CACHE__
* Questa sarà una memoria statica associativa, con lo scopo di velocizzare l'accesso alla RAM. In essa verrà copiata parte dei dati della RAM, i quali saranno conservati in "linee", così da sfruttare la proprietà di località nello spazio
* La cache sarà più piccola della RAM, possiamo permettercelo grazie alla proprietà di località nel tempo
* La CACHE può essere organizzata in più modi:
	*  **Completamente Associativa**
		* La sezione dati di ogni cella della CACHE conterrà più di un dato. Questo perchè per via della proprietà di località nello spazio, i dati successivi a quello richiesto saranno richiesti a breve. In questo modo li carichiamo già, in un singolo ciclo di CLOCK
		* Il numero di dati immagazzinati in una cella sarà $2^N$. Questo perchè in questo modo potremo segnare nella sezione tag solo i bit meno più significativi, in comune a tutte le celle. Inoltre nel tag saranno riservati bit per identificare il dato richiesto e per indicare la dimensione delle celle
	* __Corrispondenza Diretta
		*  A differenza della cache organizzata in modo totalmente associativo, questa cache è una RAM STATICA
		* Il campo TAG viene ridotto, includendo un ulteriore spazio che indica il numero di linea in CACHE
		* Il campo TAG viene usato per indicare una specifica linea, e capire se è già stata copiata in dalla RAM
		* In questo modo la struttura è anche + economica: usiamo una RAM statica con una struttura associativa
		* Sarà inoltre un unico circuito comparatore per confrontare i TAG
		* L'unico inghippo sta nell'HIT or MISS, poichè all'avvenire del MISS; il processore potrà per forza copiare il valore in quella specifica cella, al di là della sua utilità
	* __Associativa ad Insiemi__
		*  Questa è una via di mezzo fra le due precedenti
		* Le linee vengono suddivise in più insiemi. Nel campo TAG verranno usati dei bit per indirizzare alla linea nell'insieme giusto
		* SImilmente alle pagine, ogni insieme avrà indirizzi relativi ad esso. Nel caso dovessi accedere ad un dato in una specifica posizione, guardo nelle celle in quella posizione in ogni insieme, usando un comparatore per insieme. Se l'informazione si trova in una di essi, ritorno HIT, se no ritorno MISS, e scelgo in quale insieme salvare l'informazione, ridandomi la possibilità di scelta persa nella CORRISPONDENZA DIRETTA
* Cosa si deve fare nel caso si dovesse __scrivere__ in RAM?
* Abbiamo due approcci:
	* **WRITE-THROUGH:** Scriviamo sia in CACHE che in RAM, in due cicli di CLOCK, così da mantenere la consistenza fra le due e semplificare il processo
	* **WRITE-BACK:** Scriviamo in RAM solo quando la linea viene sostituita, così da ridurre il numero di scritture in RAM e permettendo di tenere buone prestazioni. Dovremo implementare un bit indicatore di un'avvenuta modifica in una linea, e dare la precedenza a linee non usate da tanto e non scritte nella sostituzione
* Nei sistemi più moderni si utilizzano più CACHE, che con l'avvicinarsi alla CPU diminuiscono di dimensioni
* In questo modo, la CPU deve guardare in meno celle di memoria, velocizzando ulteriormente la lettura 
## Pipeline
* 