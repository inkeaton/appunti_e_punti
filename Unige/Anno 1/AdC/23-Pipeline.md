* Per ora, abbiamo strutturato la nostra CPU sulla base della struttura dell'architettura VON NEUMANN
* Ma per via del funzionamento, strutturato in FETCH, DECODE, e EXECUTE, servono tre cicli di CLOCK per eseguire una singola istruzione.
* Possiamo fare in modo di velocizzare il nostro processore strutturandolo con un sistema a "catena di montaggio", PIPELINE
## PIPELINE
* Il sistema ha alla base il suddividere la CPU in tre dispositivi, ognuno dei quali predisposto ad una delle fasi del ciclo di esecuzione
* Avremo quindi
	* UNITA' di FETCH
	* UNITA' di DECODIFICAZIONE
	* UNITA' di ESECUZIONE
* Colleghiamo ognuna di esse al CLOCK, in modo ceh possano lavorare in contemporanea
* ES
	* Consideriamo di dover eseguire un programma sequenziale
	* Al primo ciclo di CLOCK, fetcheremo l'istruzione I0
	* Al secondo, decodificheremo I0, mentre fetchiamo I1
	* Al terzo, eseguiamo I0, decodifichiamo I1 e fetchiamo I2
	* E così via...
---
* Il problema insorge nel caso di programmi non sequenziali
* Infatti, quando eseguiremo un istruzione JUMP, avremo già decodificato e fetchato le due istruzioni successive, le quali non devono essere eseguite al momento. Questi dati già elaborati dovranno essere cancellati, perdendo tempo
* Ci sono più soluzioni al problema
	* Prima di tutto, controlleremo in DECODE se l'istruzione è una di JUMP, così da fetchare un'istruzione in meno
	* Nel caso delle condizionali, se la condizione non è verificata, non cancelleremo niente
	* Un'ulteriore soluzione sono i DELAY SLOT: Un istruzione JUMP viene eseguita solo dopo un numero predefinito di istruzioni che le segue. Questo implica una diverso ordine delle istruzioni in assembly, ma permette di non dover cancellare nessuna istruzione già elaborata
---
* E' possibile aggiungere più unità, in modo da velocizzare l'esecuzione. Solitamente si aggiungono unità di esecuzione, così da aiutare l'esecuzione di istruzioni che richiedono + cicli di CLOCK