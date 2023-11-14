* RFC 7540, nel 2015
* Nel caso un client richiedesse molti file __piccoli__, ed uno _grande_, il __server__ impiegherebbe __molto tempo__ ad inviare quello grande
* Il __Client__ __non__ sa le __dimensioni__ del file, al contrario del server, ma è il primo a decidere l'__ordine__ con cui richiedere i dati
* Come fare?
* __Client__ apre più __connessioni__ con il server, così da ottimizzare le richieste
* I pacchetti utilizzati avranno una struttura simile:
	* _3_ byte per indicare la __lunghezza__ del pacchetto
	* _1_ byte per indicare il __tipo__, insieme a delle flag
	* _4_ byte per codificare un __identificatore__ (3 bit in realtà, quello più significativo è sempre a 0)
	* _chiedere a ciccio i dettagli_
	* Il resto consiste nel __payload__
* I datagrammi utilizzati sono quindi di __dimensione ridotta__ ($2^{24}$ bit), così da ridurre la dimesione dei buffer di ricevimento dei datagrammi
---
* Le __richieste__ e le __risposte__ saranno riconosciute dai bit di __identificatore__, __uguali__ fra di loro
* Se i __file__ inviati sono di __dimensione superiore__ alla massima consentita, questi saranno __segmentati__, ed inviati in __più trance__
* Per l'invio, viene usata una tecnica di __processor-sharing__, in cui inviamo piano piano pacchetti di ogni file che vogliamo inviare, così da non rallentare l'invio complessivo dei file
---
* (Con una struttura simile, avrebbe più senso utilizzare come protocollo UDP)
---
* Spesso si rischia di __perdere__ __dati__ durante il trasporto nell'internet, per via dei __buffer__ dei __router__ che non riescono a tenere i messaggi, e li eliminano
* Per questo, si prova a __ritrasmettere__ -> flow-control
* Si invia il messaggio, e se il router non ha spazio per tenerlo, si richiede il rinvio, fino a quando non si può inviare
* Questo può causare un __blocco__ della rete!
* Quindi si è decisi di mettere il controllo di rete non a livello 3, ma a 4
* Sarà il __client__ che, quando si accorge di poter causare una congestione, riduce il suo traffico
* Attraverso il __timeout__, client e server verificano che non si siano persi datagrammi
---
* Successivamente al 3 way handshake, la comunicazione avviene nel seguente modo
	* __SLOW START__: Invio __pochi datagrammi__ per controllare che la rete funzioni. L'aumento è in modo __esponenziale__, e continuo finchè non mi arriva più l'ACK
	* __RECOVERY__: memorizzo l'ultima grandezza inviata e ricomincio da capo, finchè non ricevo un ACK. A questo punto, riprendo ad __aumentare__ la dimensione fino a che non arrivo alla __metà__ della quantità che ha causato la __congestione__
	* __AUMENTO LINEARE__: Continuo ad __aumentare__ la dimensione __linearmente__, fino ad arrivare ad un errore di __congestione__