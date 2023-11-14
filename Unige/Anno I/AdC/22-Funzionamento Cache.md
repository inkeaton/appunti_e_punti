* All'Accensione della macchina la CPU cerca nella CACHE i dati necessari. Non li trova, e segnala un MISS
* Il dispositivo ad esso predisposto accede alla RAM e copia una linea di dati in CACHE.
* Allora la CPU comincia a lavorare, segnalando un HIT
* Nel caso la CACHE fosse piena, decidiamo che linea sostituire attraverso lo stesso metodo del working ste, usando un bit di LRU
---
* Come facciamo nle caso in cui dovessimo scrivere in RAM, (e quindi scrivere in CACHE)?
* Abbiamo due approcci:
	* **WRITE-THROUGH:** Scriviamo sia in CACHE che in RAM, in due cicli di CLOCK, così da mantenere la consistenza fra le due e semplificare il processo
	* **WRITE-BACK:** Scriviamo in RAM solo quando la linea viene sostituita, così da ridurre il numero di scritture in RAM e permettendo di tenere buone prestazioni. Dovremo implementare un bit indicatore di un'avvenuta modifica in una linea, e dare la precedenza a linee non usate da tanto e non scritte nella sostituzione
* Per quanto possa sembrare che il primo algoritmo sia molto più lento, in realtà si è osservato che in media un computer esegue un 75% di letture in confronto ad un 25% di scritture. Quindi anche con questo algoritmo il computer lavora ad una velocità 4 volte superiore ad un computer non dotato di CACHE
---
## CACHE a CORRISPONDENZA DIRETTA
* A differenza della cache organizzata in modo totalmente associativo, questa cache è una RAM STATICA
* Il campo TAG viene ridotto, includendo un ulteriore spazio che indica il numero di linea in CACHE
* Il campo TAG viene usato per indicare una specifica linea, e capire se è già stata copiata in dalla RAM
* In questo modo la struttura è anche + economica: usiamo una RAM statica con una struttura associativa
* Sarà inoltre un unico circuito comparatore per confrontare i TAG
* L'unico inghippo sta nell'HIT or MISS, poichè all'avvenire del MISS; il processore potrà per forza copiare il valore i n quella specifica cella, al di là della sua utilità
## CACHE ASSOCIATIVA ad INSIEMI
* Questa è una via di mezzo fra le due precedenti
* Le linee vengono suddivise in più insiemi. Nel campo TAG verranno usati dei bit per indirizzare alla linea nell'insieme giusto
* SImilmente alle pagine, ogni insieme avrà indirizzi relativi ad esso. Nel caso dovessi accedere ad un dato in una specifica posizione, guardo nelle celle in quella posizione in ogni insieme, usando un comparatore per insieme. Se l'informazione si trova in una di essi, ritorno HIT, se no ritorno MISS, e scelgo in quale insieme salvare l'informazione, ridandomi la possibilità di scelta persa nella CORRISPONDENZA DIRETTA
---
* Nei sistemi moderni, vengono utilizzati più "livelli" di CACHE, ovvero più CACHE separate, le quali aumentano di dimensioni all'allontanarsi dalla CPU
* In questo modo aumenterebbe la velocità di lettura della CPU, avendo a disposizione una prima CACHE molto più piccola, senza aver bisogno di copiare continuamente le informazioni dalla molto più grande RAM
* Ha senso utilizzare in WRITE-THROUGH nella prima CACHE, il WRITE-BACK nelle altre