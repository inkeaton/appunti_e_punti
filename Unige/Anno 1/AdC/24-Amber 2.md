* Studieremo la struttura del processore opensource Amber 2, basato sulla tecnologia ARM V2a
* Esistono 2 varianti:
	* v23. CPU Pipeline a 3 stati (Fetch, Decode, Execute), dotata di una singola Cache Write-Through
	* v25. CPU Pipeline a 5 stati (Fetch, Decode, Execute, Memory, Write Back), dotata di due Cache, una per scrivere i dati, l'altra per leggerli. Quest'ultima utilizza un protocollo WT
* Il Bus è comune ed è organizzato a 32 bit, come la RAM.
*  La Cache è organizzata in linee di quattro parole, ovvero 16 B, con organizzazione ASSOCIATIVA AD INSIEMI. Vi possono esser 2, 3, 4, o 8 insiemi, ognuno di 4kB
*  Nel caso vi sia un MISS in Cache, è implementato un sistema capace di "fermare" la pipeline e riempire la Cache prima di proseguire
## Esecuzione di un'istruzione in v23
![Screenshot-20220331145747-581x886.png](Screenshot-20220331145747-581x886.png)
* Immaginiamo di dover eseguire un'istruzione
* Innanzitutto inviamo in input all'unità di FETCH l'indirizzo dell'istruzione
* Esso controllerà in CACHE la presenza dell'istruzione. In caso di MISS, ferma la pipeline e inserisce in CACHE la linea necessaria. In caso di HIT, fetcha le istruzioni e le passa nel registro READ INSTRUCTION/DATA
* Questi dati verrano decodificati dall'unità di decodificazione. Nel caso l'istruzione richieda più cicli per essere compiuta, le istruzioni relative ad essi verranno salvate nel registro DECODE STATE, ed usate successivamente
* Infine, questa verrà eseguita dall'unità EXEC, ed i risultati saranno mandati nei registri del DATA PATH
	* Nel caso questa fosse un istruzione che richiede più cicli, come scrittura o lettura, o che deve scrivere in CACHE, sarà pausata la pipeline e verranno eseguite le istruzioni memorizzate in DECODE STATE
	* Ad esempio, per eseguire una lettura, dovremo pausare la pipeline per 2 cicli di CLOCK (fetchando ed eseguendo il dato richiesto)

## Esecuzione di un'istruzione in v25
* Il procedimento è in realtà molto simile a quello di v23, con la differenza di adoperare due CACHE, una di lettura, ed una di scrittura, con WT
* Questo permette di eseguire in contemporanea istruzioni di LOAD o STORE in contemporanea a quella di FETCH, evitando gli stalli necessari in v23, e velocizzando il processore
* Negli esempi successivi sarà presa come riferimento la versione v23

## Registri
* I registri sono sono 16, contenente ognuno 32 bit
	* I registri 0-7 sono di uso GENERALE, e vengono usate dalle istruzioni della CPU, ad esempio di STORE e di LOAD
	* I registri 8-15 sono speciali ed usati dal sistema
		* r13 è lo STACK POINTER, che indica l'inizio dei programmi nello STACK
		* r14 è il LINK POINTER, usato per salvare il valore di r15 alla chiamata di una funzione. Nel caso sia chiamata un'ulteriore funzione, i valori verranno salvati come normale nello STACK
		* r15 è il PROGRAM COUNTER
* Per via dell'organizzazione della CACHE, gli ultimi 2 bit del PC vengono inutilizzati: vengono dunque riciclati per implementare 4 diversi stati del processore
	* USR: User, modalità in cui girano i programmi normali
	* SUC: Supervisor, modalità riservata all'OS
	* IRQ: Interrupt, usata dall'INTERRUPT HANDLER
	* FIRQ: Fast Interrupt, usata per una gestione più veloce delle Interruzioni
* Alcune di queste modalità hanno delle copie di registri a loro dedicate, allo scopo di aumentare la velocità d'esecuzione. In particolare, FIRQ possiede una copia a se riservata dei registri 8-14, così da essere più veloce rispetto a IRQ. r15 è ovviamente comune a tutti, com r0-r7


![Screenshot-20220331153256-509x491.png](Screenshot-20220331153256-509x491.png)

