# Disk e SWAP

### Unità Disco (DSK)
* Le unità disco sono unità di memoria, non dissimili dalle RAM, ma strutturate in modo differente:
	* Le unità DSK sono solitamente non volatili, e conservano nel tempo i dati, al contrario delle unità RAM
	* La RAM è indirizzabile tramite delle "parole" (indirizzi), le DSK sono organizzate in **BLOCCHI**, insiemi di byte di grandi dimensioni
	* Per leggere da un DSK non si utilizzano i registri della CPU, ma si copiano i valori contenuti nel blocco richiesto nella RAM, da cui poi saranno a sua volta letti
* Allo scopo di semplificare quest'ultimo funzionamento, spesso si fanno corrispondere le dimensioni di un blocco con la dimensione di una pagina
---
### Ibernazione
* Potremmo anche fare il contrario, ovvero copiare l'intera RAM all'interno di un'unità DSK
* Questo ci permetterebbe di "salvare" lo stato della RAM all'interno del DSK, permettendo di conservare lo stato corrente del dispositivo, pur spegnendolo (**IBERNAZIONE**)
* L'area di memoria destinata a questa copia viene definita **SWAP**. In un sistema di calcolo POSIX, è necessaria una SWAP $\ge$ RAM per supportare l'Ibernazione, ma questo non è un problema, dato che solitamente SWAP >> RAM
---
### Paginazione a Richiesta
* Una SWAP >> RAM può essere utilizzata per eseguire più programmi contemporaneamente, "fingendo" di possedere una RAM di dimensioni maggiori
* Questa idea viene implementata attraverso la **PAGINAZIONE A RICHIESTA**, in cui i programmi non vengono caricati nella RAM ma nella SWAP
	* All'accensione del computer l'MMU controlla la RAM per istruzioni. La RAM è vuota, facendo quindi scattare una TRAP
	* l'OS interviene, cercando il programma richiesto nella SWAP, e caricandolo nella RAM, in una pagina libera. La PAGE TABLE viene modificata con l'indirizzo giusto.
	* Quando il programma giunge ad un altra pagina, il sistema si ripete
* L'idea generale consiste quindi nel caricare una pagina in RAM solo quando un programma la richiede
* Questo ovviamente rallenterebbe l'esecuzione del programma, dato che ad ogni pagina il sistema dovrebbe perdere tempo a richiederla
* Per ovviare a questo problema viene implementata la tattica TIMESHARING: mentre il sistema carica la pagina richiesta, viene eseguito un secondo programma
* Questo sistema è ovviamente solo utile nei calcolatori che possiedono una zona SWAP molto maggiore rispetto all RAM; e potrebbe persino velocizzare la velocità di calcolo
---
* Cosa succede quando tutte le pagine della RAM sono occupate?
* Bisognerebbe sostituire una pagina già in uso con quella richiesta, salvandola nella SWAP, e riprenderla quando servirà nuovamente...
* Ma è un grosso spreco di tempo!
* A tal scopo i programmi vengono divisi in due insiemei, WORKING SET e MEMORY SET
* Il WS è formato delle pagine che sono necessarie al momento. Questo insieme quindi cambia a seconda del momento dell'esecuzione del programma in cui siamo
* Le pagine contenute nel MS sono invece non necessarie, e possono essere sostituite
---
### LRU
* Esistono numerosi algoritmi capaci di ritrovare le pagine appartenenti al WS, am il più efficente è l'LRU (LIST RECIPE U)
	* Viene tenuto conto dell'ultima volta in cui è stata utilizzata una pagina
	* Quando deve essere sostituita una pagina, si sceglie quella che non viene utilizzata da più tempo
* Il timer che indica l'ultimo utilizzo di una pagina viene implementato con un solo bit
	* Quando la pagina viene caricata il bit è 0
	* Quando viene utilizzata, viene impostato a 1
	* Periodicamente, tutti i bit timer vengono riportati a 0
* In questo modo, capiamo che le pagine che possono essere sostituite sono quelle che hanno il bit timer ancora a 0
---
* L'informazione riguardo alla posizione della SWAP si trova nella SEG TABLE, indicando la sua posizione nel DSK
* Nella PAGE TABLE segneremo per ogni tavola anche:
	* Se è caricata in RAM (Le TRAP di pagina mancante useranno questo bit)
	* Il suo indirizzo
	* Se è stata modificata
	* Il bit timer necessario a LRU
---
* Il THRASHING è una situazione in cui il sistema si trova bloccato, continuando a scambiare pagine senza avanzare in nessun programma