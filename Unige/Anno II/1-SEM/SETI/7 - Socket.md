* Un __socket__ è il __punto terminale__ di una connessione a doppio senso fra due macchine
* Esistono più modi di utilizzo di un socket:
	* __DGRAM__: Comunicazione assimilabile all'UDP
	* __STREAM__: Comunicazione assimilabile al TCP
	* __RAW__: Comunicazione al livello più basso
---
### DGRAM
* Per iniziare una comunicazione di tipo socket, dobbiamo chiamare la __system call socket()__ per crearne uno
* Questa restituisce un file descriptor che identificherà il socket, su cui scrivere e leggere peer comunicare
* La system call prende tre argomenti:
	* La __famiglia__ d'indirizzamento: indica il tipo di protocollo che useremo, ad esempio AF_INET per le comunicazioni su IPv4
	* Il __tipo__ di socket: in questo caso SOCK_DGRAM
	* Il __protocollo__ di trasporto: indica il protocollo specifico. Quello di default è IPPROTO_UDP
* Per inviare un messaggio, useremo la system call __sendto()__
* Prende come argomenti:
	* L'__fd__ del socket
	* Il puntatore al __buffer__ che contiene il __messaggio__
	* La __lunghezza__ del __buffer__
	* Un intero che indica delle __flag__
	* L'__indirizzo__ del __destinatario__
	* La __lunghezza__ dell'__indirizzo__ precedente
* Per __ricevere__ il messaggio, il destinatario dovrà avere un __socket__ dello stesso __tipo__ con lo stesso __indirizzo__
* Per __assegnare__ un __indirizzo__ ad un socket appena creato, usiamo la system call __bind()__
* Ma come facciamo a sapere l'indirizzo del destinatario? Dobbiamo comunicare con esso tramite delle comunicazioni OOB (__Out of Bounds__)
* Per ricevere, usiamo la system call __recvfrom()__
* Prende come argomenti:
	*  L'__fd__ del socket
	* Il puntatore al __buffer__ su cui scrivere il __messaggio__
	* La __lunghezza__ del __buffer__
	* Un intero che indica delle __flag__
	* L'__indirizzo__ del __mittente__
	* La __lunghezza__ dell'__indirizzo__ precedente
* Restituisce un size_t contenente il numero di dati ricevuti
* Se il buffer è troppo piccolo rispetto ai dati ricevuti, solo una parte dei dati viene trascritta
* In questi casi è molto utilie la flag MSG_PEEK. Questa fa in modo che vengano conservati i dati ricevuti, senza scriverli nel buffer. Se la recvfrom() viene richiamata, gli stessi dati vengono riportati
* In questo modo, potremmo utilizzare la flag nelle comunicazioni, ed in caso il buffer sia troppo piccolo rispetto ad i dati, raddoppieremo lo spazio dedicato al buffer e richiameremo recvfrom() senza la flag, salvando i dati in memoria
* Nel caso recvfrom() non riceva dati, questi si blocca fino a quando non riceve informazioni
* Si può evitare scrivendo la flag MSG_DONT_WAIT