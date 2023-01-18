## Intro
* In questo corso abbiamo studiato vari tipi di protocolli, ognuno classificabile in una sezione del cosiddetto Internet Stack
* Li riassumeremo in questo file, andando di grado in grado
---
## 2. Data Link

### Ethernet
* Protocollo ideato per collegare più computer, via cavo
* __Standard__: IEEE 802.3
* __Frame__: 
	![[Ethernet Frame.png]]
	* Il __Preambolo__ segnala ad un host l'arrivo del messaggio, e serve a sincronizzare il suo clock per l'invio di messaggi
	* __CRC__ è un checksum calcolato tramite CRC-32
---
* La trasmissione avviene un bit alla volta, lungo il filo, in modo sincrono, tramite un clock
	* Nella versione del 1983, il clock ha una frequenza di 10 MHz, con una velocità di 10^6 bit al secondo
* I dati arrivano a tutti gli host collegati alla rete. Essi controllano se i dati sono inviati a loro stessi, in tal caso leggono il messaggio
---
* Un problema di questo meccanismo sono le __interferenze__. Se due messaggi passano allo stesso tempo, possono confondersi a vicenda
* Per evitarle si usa l'algoritmo __CSMA-CD__ (Carrier Sensor Multiple Access - Collision Detection)
	* Appena un dispositivo fra quelli connessi alla rete rileva una connessione, questi "urla" a tutti gli altri dell'avvenuto (Jamming)
	* I due dispositivi che trasmettevano interrompono la comunicazione.
	* Ognuno dei due riprendee dop un tempo, scelto casualmente, multiplo di T, un tempo maggiore di quello necessario perchè un messaggio si propaghi su tutto il filo. Nel caso scelgano lo stesso, si ripete l'interferenza, e si sceglie fra un numero maggiore di multipli
* Il tempo necessario per la propagazione è l'__intervallo di vulnerabilità__. Dopo questo tempo, ogni host riceve la trasmissione di chi comunica sul cavo
---
* Esistono varie versioni del protocollo
	* __10 Base 5__
		* Utilizza un cavo coassiale, ma si può usare anche al livello 1 per comunicare con i dispositivi dell'host
	* __10 Base 2__ (1985)
		* Si usa un connettore a t
	* __10 Base T__ (1990)
		* Ci si collega tramite il __doppino telefonico__: più economico, lunghezza massima limitata a 100 metri, velocità massima 250 Mhz/s
		* Viene introdotto l'__Hub__, un dispositivo ripetitore a cui collegare tutti gli host tramite i cavi. In questo modo, non si deve usare tutti lo stesso cavo, e si ovvia alle limitazioni di lunghezza massima
	* __100 Base T__ (1995)
		* La frequenza passa a 100 Mhz, __aumentando__ la velocità di trasmissione
	* __100 Base FX__
		* Utilizza per la connessione la __fibra__ ottica
	* __1000 Base TX___ (1998)
		* Oltre ad aumentare la frequenza, si passa ad usare i cavi RJ45, formati da quattro doppini telefonici
		* L'Hub si evolve in uno __Switch__:
			* La connessione avviene tramite due cavi, ottenendo due sensi di marcia per i dati (sistema FULL DUPLEX)
			* Lo switch diventa un computer dotato di RAM. Nell'inviare un messaggio, lo copia in essa e lo trasmette solo all'host destinatario, evitando completamente le collisioni
			* L'unico svantaggio è la perdita di tempo nel fare Store & Forward (Alta Banda, Alta Latenza).
			* Inoltre, switch inizialmente non conosce gli indirizzi dei dispositivi collegati, deve fare una richiesta broadcast a tutti
---
* Il protocollo Ethernet utilizza gli indirizzi __MAC__ per identificare gli host
* Ogni indirizzo è composto da 6 byte, ed è unico per ogni dispositivo. 
	* I primi 24 bit indicano il costruttore, i rimanenti il dispositivo

---
### 802.11 (WIFI)
* Evoluzione di Ethernet che prevede l'utilizzo di __frequenze radio__ al posto di cavi
---
* Ogni dispositivo sarà dotato di un' antenna, e comunicherà sulle frequenze 2.4GHz o 5GHz, a bassa potenza
* Ci sono due modalità di comunicazione
	* __Peer to Peer__: I due dispositivi comunicano __direttamente__ fra loro
	* __Infrastructure__: I due dispositivi comunicano utilizzando un __Access Point__ come __intermediario__
* La __prima__ modalità viene utilizzata molto __raramente__, in quanto Infrastructure ha il vantaggio di permettere l'aumento dell'area coperta dalla rete
* Rispetto ad Ethernet, la __velocità__ è molto più __bassa__, si comunica all'incirca a 20 Mb al secondo
---
* Esistono più versioni del protocollo:
	* __`a`__: Utilizzato in America, lavora sui 5 GHz
	* __`b`__: Utilizzato in Europa, lavora sui 2.4 GHz
	* __`g`__: Standard capace di raggiungere una banda di 54Mb/s
* Sono disponibili 11 canali di comunicazione differenti, ma a causa delle sovrapposizioni, se ne possono usare solo 3 alla volta
---
* Al contrario di Ethernet, non abbiamo bisogno di usare CSMA/CD, useremo il cosiddetto CSMA/CA, __Collision Avoidance__
	* Potremmo usare un sistema di __ACK__ e __timeout__. Dopo aver inviato un messaggio, attenderemo un tempo t l'arrivo dell'ACK. Nel caso non arrivi, ipotizzeremo una collisione, ed attenderemo un secondo tempo s prima di reinviare. Nel caso si ripeta, ripeteremo la procedura, raddoppiando il tempo d'attesa
	* Questo sistema non è però utilizzabile in reti caotiche
* Introduciamo un __secondo__ sistema
	* Quando vogliamo comunicare sulla rete, inviamo un messaggio __RTS__ (Request to Send) all'access point
	* Questo riceve le richieste, ed invia un __CST__ (Clear to Send) a chi deve comunicare
	* In questo modo, si parla uno alla volta. La rete si __rallenta__ un poco, ma è più __affidabile__
---
* Gli access point possono essere collegati a __reti locali__, permettendo la comunicazione anche con dispositivi collegati via filo
* Sarà lui ad occuparsi della __traduzione__ dei messaggi
---
* L'header di 802.11 è uguale a quello di 802.3, con la differenza di contenere anche l'indirizzo MAC dell'access point 
* Inoltre in messaggi si dividono in messaggi di tipo __Controllo__, che contengono RTS o CTS, e messaggi di tipo __Dati__, contenenti informazioni
---
* La rete risulta molto __meno sicura__ rispetto a quella __Ethernet__, in quanto è molto più facile collegarsi
* Per questo sono stati introdotti vari metodi di cifratura. Uno è il __WEP__, terribilmente insicuro
* Prima di connetterci alla rete, dovremo trasmettere le __chiavi__ di cifratura, purtroppo passate in chiaro
* Inoltre, solo i Frame di tipo Dati vengono cifrati, permettendo senza problemi attacchi che utilizzano i messaggi di tipo Controllo, come __Denial of Service__, o interferenze
---
## 3. Network

### Indirizzi
* Sono numeri che identificano una specifica macchina
* Composti da 4 byte, contiene quattro numeri
  Questi byte vengono divisi in due sezioni:
	* L'__Indirizzo di Rete__ o Gateway, che identifica la __rete locale__ a cui è connesso l'host
	* L'__Indirizzo di Host__, che identifica l'__host__ nella rete
* Il numero di byte per sezione non è fisso: Si aggiunge all'indirizzo una __Netmask__ da 4 byte
* L'indirizzo __privato__ `127.0.0.0` identifica la nostra macchina
* Gli indirizzi __Broadcast__ idenficano una sottorete, hanno la sezione Host tutta uguale a 1
---

### IPv4
* Si occupa di trasmettere i __datagrammi__ fra i vari router
* __RFC__: 791
* __Header__: 5 righe da 32 bit, più opzioni
	![[IPv4 Header.png]]
	* __Prima__ riga:
		* __4__ bit che indicano la __versione__ del protocollo
		* __4__ bit che indicano quanto è __lungo__ in totale l'__header__
		* __8__ bit indicano il __Service Type__, una feature mai utilizzata che indicava il tipo di servizio del pacchetto
		* __16__ bit che indicano la __lunghezza totale__ del datagramma
	* __Seconda__ riga: (SCRIVILA DOPO)
	* __Terza__ riga:
		* __8__ bit chiamati __Time to Live__ (TTL), il quale è un numero diminuito ad ogni passaggio fra router. Se raggiunge 0, il datagramma viene eliminato. Questo serve ad __evitare loop__ in cui il datagramma gira all'infinito fra router
		* __8__ bit chiamati __Next Level Protocol__ (NLP), i quali indicano il metodo di __codifica__ del __payload__ a livello L4
		* __16__ bit chiamati __Checksum__, i quali sono __bit di parità__ ottenuti dalla somma dei bit delle linee a gruppi di 16. Servono a capire se si sono verificati errori
	* __Quarta__ riga: __indirizzo__ IP del __mittente__
	* __Quinta__ riga: __indirizzo__ del __destinatario__
		* Possono essere presenti __ulteriori linee__ contenenti __opzioni__ aggiuntive, ma vengono __raramente utilizzate__
---
* I messaggi vengono trasmessi da router a router in modalità __Best Effort__
---

### IPv6
* __Miglioramento__ di __IPv4__, tramite l'aumento dei bit d'indirizzo e standardizzazione dell'header
* __Header__: Lungo 40 byte
	 ![[IPv6.jpg]]
	* TTL viene rinominato in Hop Limit
	* __Traffic Class__ e __Flow Label__ non vengono ancora usati
	* Viene rimossa la __frammentazione__, in quanto inefficiente
	* Viene rimosso il __CHECKSUM__, in quanto superfluo
---
* Next Level indica il protocollo contenuto nel payload, che potrebbe essere anche IPv4 o IPv6
* Infatti questa tecnica, denominata __Tunnelling__, permette sia di estendere il payload IPv6, sia di comunicare con reti che supportano solo IPv4 
---
* Instradamento a livello IP. Come implementarlo?
* Abbiamo due metodi:
	* __Link-State__: Ogni router, appena inizializzato, invia a tutti i vicini il suo indirizzo, ed ognuno li memorizza in tabelle. Attraverso questi dati, si può creare un __grafo__. Attraverso l'agoritmo __Dijkstra__, saremo poi in grado di trovare il cammino minore fra due nodi. Un problema di questo metodo è nell'__eccessiva dimensione__ del grafo, nel caso di grandi reti
	* __Distance-Vector-Routing__: Ogni router possiede un distance-vector che indica la sua distanza da ogni altro router nella rete. Egli lo invia periodicamente ai suoi vicini. In questo modo, ogni router sarà in grado di calcolarsi le relative distanze fra ogni router, e determinare il minor cammino. Non conviene però su reti molto grandi
---
### ICMP 
* Si occupa di trasmettere i __messaggi d'errore__ delle comunicazioni IP
* __RFC__: 793

---
### ARP (Address Resolution Protocol)
* Si occupa di __tradurre__ indirizzi __IP__ in indirizzi __MAC__
---
* È un protocollo __Distribuito__, che funziona tramite la collaborazione fra tutti gli host della rete
* Inviamo un messaggio in modalità Broadcast, contenente un datagramma IP dentro un frame Ethernet
	* Il payload conterrà il necessario per una richiesta ARP
	* L'header IP conterrà l'IP del destinatario, chi stiamo cercando
* L'host ci risponderà con un messaggio analogo
	* I campi IP saranno uguali ma scambiati
	* I campi MAC conterrano, nel mittente, l'indirizzo da noi cercato
	* Il payload conterrà cio che serve a specificare che si tratta di una risposta ARP
---
* Molte richieste potrebbero intasare la rete, ma per questo gli host terranno una __cache__ in cui si salveranno gli indirizzi tradotti
	* Nei sistemi UNIX, Gli indirizzi __MAC__ possono essere salvati assieme agli indirizzi IP in `/etc/hosts`
* Questa cache è soggetta a __cache poisoning__. Una soluzione potrebbe essere introdurre elementi randomici, ma chiunque può vedere le richieste, quindi...
## 4. Transport

### Porte L4
* Numeri a 16 bit, assimilabili a frequenze su cui comunicare
* Suddivise in 
	* __Wellknown__: sono porte __statiche__, __associate all'applicazione__. Gli indirizzi da __0 a 1023__ sono __riservate all'amministratore__ ed alle applicazioni di sistema, le restanti utilizzabili dall'utente
	* __Ephemeral__: Sono porte effimere, generate dal sistema e __associate temporaneamente all'applicazione__, cambiate ad ogni comunicazione

### UDP (User Datagram Protocol)
* Protocollo per __smistare pacchetti__ fra le __applicazioni__, comunicando sulle porte L4
* __RFC__: 768
* __Header__: 2 righe da 32 bit
	![[UDP Header.png]]
	* __Prima__ riga:
		* __16__ bit contenenti la __porta sorgente__ 
		* __16__ bit contenenti la __porta di destinazione__
	* __Seconda__ riga:
		* __16__ bit che indicano la __lunghezza del messaggio__ e 
		* __16__ bit che contengono un __Checksum__
---
* La comunicazione avviene __senza connessione__: I messaggi vengono inviati senza nessun controllo del corretto ricevimento degli stessi.
* Il protocollo è perciò altamente __inaffidabile__
---

### TCP (Transmission Control Protocol)
* Svolge le stesse funzioni di UDP, creando un __canale di comunicazione__, __stabile__, __bidirezionale__ e __molto affidabile__, fatto in modo da poter inviare __multipli messaggi__
---
* __RFC__: 792
* __Header__: 5 righe da 32 bit, più opzioni
	![[TCP Header.png]]
	* __Prima__ Riga:
		* __16__ bit contenenti la __porta sorgente__ 
		* __16__ bit contenenti la __porta di destinazione__
	* __Seconda__ Riga: 
		* __32__ bit contenenti il __Sequence Number__, un numero che indica il numero di byte inviati durante la sessione.
	* __Terza__ Riga:
		*  __32__ bit contenenti l'__Acknowledgment Number__, simile al sequence number, utilizzato dal ricevente, ha lo stesso valore di SEQ # più uno
	* __Quarta__ Riga:
		* __4__ bit contenenti la __lunghezza__ dell'header
		* __3__ bit dell'RSV, un campo __inutilizzato__
		* __9__ bit contenenti delle __Flags__ che identificano il tipo di messaggio. 
		* __16__ bit contenenti la __Receive Window__, dimensione del buffer del ricevente
	* __Quinta__ Riga:
		* __16__ bit contenenti un __Checksum__, 
		* __16__ bit riservati all'Urgent pointer, __inutilizzati__
	* Infine, spazio per delle __opzioni__
---
* La connessione viene inizializzata tramite la  __3-Way-Handshake__:
	1. Inizialmente, il __primo host__ invia un messaggio con payload vuoto, contenente il __SEQ#__, generato randomicamente, e con la flag __SYN attiva__. Questo messaggio viene chiamato __SYN__, per Syncronize, e consiste nella __richiesta di connessione__
	2. Ricevuto il messaggio, nel caso in cui il __ricevente__ accetti la connessione, questi risponde con un secondo messaggio vuoto, contenente il suo __SEQ#__ ed il nuovamente generato __ACK#__, con le flag __SYN ed ACK attive__. Il messaggio viene chiamato __SYN/ACK__ e consiste in un'__accettazione della connessione__
	3. Infine, ricevuto il messaggio, il primo host invia un ultimo messaggio vuoto con solo la flag __ACK attiva__, chiamato __ACK__, per Acknowledgment. Questo consiste in una __conferma della ricezione del messaggio__
---
* All'invio di ogni messaggio, viene __aggiornato__ il SEQ# e l'ACK#. Quando il destinatario lo riceve, esso invia un messaggio vuoto con la flag ACK#, garantendo il corretto ricevimento dell'informazione
* Nel caso il __mittente non riceva__ una conferma entro un tempo limite (timeout), questi __reinvierà__ il pacchetto
* Gli host dovranno comunicare tenendo conto della __Receive Window__, e spezzare le informazioni in più pacchetti se necessario
* Nel caso un host impieghi troppo tempo a svuotare il suo buffer, questi può inviare pacchetti __Keep Alive__, vuoti, inviati solo per impedire il timeout
* Dato che ad ogni messaggio è richiesto un ACK, spesso si inviano informazioni dentro ad un ACK che sarebbe normalmente vuoto (__Piggy Bagging__)
*  In caso un mittente voglia inviare un numero molto grande di dati, egli dovrà farlo inviando un gran numero di datagrammi separati. In questi casi è stupido pensare di inviare ACK per ognuno di questi: possiamo pensare di __inviare ack solo ogni tot pacchetti__. 
* Nel caso i pacchetti siano in disordine, possiamo __aspettare__ l'arrivo dei giusti pacchetti prima di inviare un ACK. È anche possibile comunicare la __mancata ricezione__ tramite il __rinvio__ di ACK precedentemente inviati, arrivando spesso prima di un timeout e velocizzando il rinvio di pacchetti
---
*  La __connessione__ può essere __conclusa__ in due modi:
	* Attraverso l'invio di un messaggio con flag __RST__ attiva: Questa chiude __immediatamente__ il canale, senza bisogno di conferme, ed è utilizzata in casi d'errore od'emergenza
	* Attraverso l'invio di un messaggio con flag __FIN__ attiva: il ricevente __finirà__ di __inviare__ tutti i pacchetti ed in seguito invierà un messaggio con flag FIN/ACK attive. Infine il primo host conferma con un messaggio con ACK attiva, chiudendo la connessione
		* Quest'ultimo metodo conferma la ricezione corretta di tutti i pacchetti condivisi

#### Timeout
* __RFC__: 6298
* Viene calcolato in base a:
	* La __media del tempo necessario ad inviare un messaggio__ e ricevere un ACK. $\alpha$ ha valore $\frac{1}{8}$ in TCP
		* $Nuova stima = ( 1 - \alpha) \cdot stima precedente + \alpha \cdot nuovo valore$  
	*  La __deviazione__ dei valori dal valore medio. $\beta$ è $\frac{1}{4}$ in TCP
		* $dev = (1 - \beta) \cdot devprecedente + \beta \cdot |stima - nuovo valore|$ 
*  Il __timeout__ avrà alla fine valore:
	* $timeout = stima + 4 \cdot dev$
* Questo valore viene calcolato ad ogni ACK.
* In caso un timeout __scada__, si __raddoppia__ il valore di timeout, mantenendo il calcolo di stima e dev con i precedenti valori

## 5. Applications

### DNS
* Si occupa di tradurre i nomi __simbolici__ in indirizzi __IP__
---
* __RFC__: 1034, 1035
* __Comunicazione__: porta UDP/35
* __Domande e RIsposte__:
		![[DNS.jpg]]
	* __Prima__ Riga: 
		* __16__ bit di __ID__ del messaggio
		* __16__ bit di __flag__
	* __Seconda__ Riga:
		* __16__ bit di # di __domande__ fatte 
		* __16__ bit di # di __risposte__ ricevute
	* __Terza__ Riga:
		* __16__ bit di risposte __autoritative__ 
		* __16__ bit di risposte __addizionali__ 
	* Sezioni di lunghezza variabile contenenti __domande__, __risposte__, __autoritative__, __addizionali__
---
* I server sono organizzati in una struttura ad albero
	* Esiste un nodo __Root__, punto di partenza
	* I nodi ad esso figli sono i __Top Level Domain__. Questa sezione è gestita a livello __pubblico__
	* Subito sotto si trovano i livelli __Autoritativi__, gestiti __privatamente__
* Oggigiorno esistono migliaia di server __root__, associati ai 13 server root originali. Tramite il sistema __Anycast__ viene identificato il più vicino a noi.
* I server vengono gestiti dai __Service Provider__
* Anche i __TLD__ possono essere organizzati in questo modo, mentre a livello autoritativo, decidono i privati
---
*  Vengono usati due __algoritmi__ diversi per ritrovare i server richiesti:
	* __Ricorsivo__: il client invia la domanda alla root. La root identifica il TLD, ed invia la richiesta al nodo relativo. Questo nodo fa lo stesso con il livello autoritativo, e così via fino all'ultimo nodo. Questi invierà l'IP necessario al client
	* __Iterativo__: Simile al precedente, ma con la differenza che ogni nodo invia l'ip del nodo successivo al client, il quale invierà nuovamente la richeista al nuovo nodo
* Il __primo__ è più __veloce__, ma __grava sui server__, mentre il __secondo__ è più __lento__, ma fa in modo che __parte del carico sia presa dal client__
---
* Possiamo usare dei __server DNS locali__, che si occupano delle mansioni del client nell'algoritmo iterativo, dotati di __cache__, con timeout di __validità__
* Le risposte in cache vengono sempre inviate come __non autoritative__, con assieme la risposta autoritativa contenente il livello superiore. In questo modo, il ricevente può controllarne la validità, a quel livello
* Tramite __IP Spoofing__ è facile "avvelenare" queste cache. I metodi utilizzati per combattere questi attacchi consistono in:
	*  Assegnare alla richiesta DNS un __ID__ di 16 bit. La risposta dovrà avre lo stesso ID, e sarà complicato per l'hacker indovinare il numero giusto
	* Comunicare sulla stessa __porta__ randomizzata, aggiungendo degli ipotetici 16 bit in più
----
### Socket
* Un __socket__ è il __punto terminale__ di una connessione a doppio senso fra due macchine
* Esistono più modi di utilizzo di un socket:
	* __DGRAM__: Comunicazione assimilabile all'UDP
	* __STREAM__: Comunicazione assimilabile al TCP
	* __RAW__: Comunicazione al livello più basso
	
#### DGRAM
* Per iniziare una comunicazione di tipo socket, dobbiamo chiamare __`socket()`__ per crearne uno
	* La system call prende tre argomenti:
		* La __famiglia__ d'indirizzamento: indica il tipo di protocollo che useremo, ad esempio AF_INET per le comunicazioni su IPv4
		* Il __tipo__ di socket: in questo caso SOCK_DGRAM
		* Il __protocollo__ di trasporto: indica il protocollo specifico. Quello di default è IPPROTO_UDP 
---
* Per inviare un messaggio, useremo la system call __`sendto()`__
	* Prende come argomenti:
		* L'__fd__ del socket
		* Il puntatore al __buffer__ che contiene il __messaggio__
		* La __lunghezza__ del __buffer__
		* Un intero che indica delle __flag__
		* L'__indirizzo__ del __destinatario__
		* La __lunghezza__ dell'__indirizzo__ precedente

---
* Per __ricevere__ il messaggio, il destinatario dovrà avere un __socket__ dello stesso __tipo__ con lo stesso __indirizzo__
* Per __assegnare__ un __indirizzo__ ad un socket appena creato, usiamo la system call __`bind()`__
	* Ma come facciamo a sapere l'indirizzo del destinatario? Dobbiamo comunicare con esso tramite delle comunicazioni OOB (__Out of Bounds__)
---
* Per ricevere, usiamo la system call __`recvfrom()`__
	* Prende come argomenti:
		*  L'__fd__ del socket
		* Il puntatore al __buffer__ su cui scrivere il __messaggio__
		* La __lunghezza__ del __buffer__
		* Un intero che indica delle __flag__
		* L'__indirizzo__ del __mittente__
		* La __lunghezza__ dell'__indirizzo__ precedente
* Restituisce il numero di dati ricevuti
	* Se il buffer è troppo __piccolo__ rispetto ai dati ricevuti, solo una __parte__ dei dati viene __trascritta__
	* In questi casi è molto utilie la flag __`MSG_PEEK`__. Questa fa in modo che vengano __conservati__ i dati ricevuti, senza scriverli nel __buffer__. Se la `recvfrom()` viene richiamata, gli stessi dati vengono riportati
	* In questo modo, potremmo utilizzare la flag nelle comunicazioni, ed in caso il buffer sia __troppo piccolo__ rispetto ad i dati, __raddoppieremo__ lo __spazio__ dedicato al buffer
* Nel caso non riceva dati, questi si __blocca__ fino a quando non riceve informazioni
	* Si può evitare scrivendo la flag __`MSG_DONT_WAIT`__

#### STREAM
* I socket di tipo __stream__ sono basati sul protocollo __TCP__
* Per comunicare, bisogna creare un __canale__ di connessione fra due socket, uno di tipo __client__, uno di tipo __server__
* Questi vengono creati dalla syscall __`socket()`__, con le dovute flag
* __Client__:
	* Esso ha il ruolo __attivo__ nella comunicazione.
	* Questa comincia quando esso invia una richiesta di inizio comunicazione, tramite la syscall __`connect()`__.
	* Questa prende come argomenti l'__fd__ che identifica il socket del client, e l'__indirizzo__ del destinatario
		* L'indirizzo si ottiene tramite la syscall __`getaddrinfo()`__, che traduce gli indirizzi nel formato corretto. Traduce anche gli URL, usando il sistema dei DNS
	* Dopo aver inviato la richiesta, ed aver avviato la connessione, la comunicazione avviene tramite le syscall __send__() e __recv__()
* __Server__:
	* Esso ha il ruolo __passivo__ nella comunicazione
	* Dopo esser stato creato, il socket usa __`bind()`__ per associarsi ad una porta, unica per ogni socket. Dopo di che chiama __`listen()`__, per rimanere in attesa di una richiesta di comunicazione su quella porta
	* Ricevuta la richiesta, esso usa __`accept()`__ per accettarla, ottenendo un nuovo __fd__.
	* Il server userà questo socket per __comunicare__ con quel client, usando send() e recv().
	* Questo sistema permette ad un server di __comunicare con più client contemporaneamente__, usando i diversi fd
---
* La lunghezza dei messaggi in __DGRAM__ è __limitata__ a 2^16 byte, a causa dell'utilizzo di datagrammi. __STREAM__ __non ha queste limitazioni__
* __STREAM__ è sempre __più sicuro__ di DGRAM. In particolare, STREAM è molto sicuro sulle __lunghe distanze__ e sulle reti geografiche, rendendo l'IP spoofing quasi impossibile. Questa sicurezza __non c'è a livello locale__, in cui si usano indirizzi MAC
* __DGRAM__ è più __veloce__ di __STREAM__ sui messaggi __brevi__, ma soffre del __collo di bottiglia__ dovuto alla dimensione massima dei datagrammi. Inoltre __STREAM__ guadagna grazie al __controllo di flusso__
---

### NTPv4
* Viene usato per __sincronizzare__ gli __orologi__ di due macchine
---
* __RFC__: 958, 5905
* __Comunicazione__: porta UDP/123
---
* Allo scopo di __sincronizzare__ l'orologio,viene creata una rete di server a livelli, al cui livello 0 abbiamo un __orologio atomico__. Più si scende di livello, più ci si allontana dall'orologio
* Bisogna ora calcolare il tempo necessario per inviare e ricevere i messaggi, così da dedurre l'ora esatta nel momento in cui ci arriva il messaggio
* Potremmo calcolare l'RTT e sottrarre il tempo medio necessario per ricevere il messaggio, ma non converrebbe nel caso di connessioni instabili
* Un metodo migliore è contattare più volte tutti i server NTP a noi disponibili, e verificare quali sono quelli che hanno l'RTT più costante ad ogni comunicazione. In questo modo, potremo essere sicuri che la connessione col server è il più stabile possibile
---
* Una volta confermata l'ora, bisogna __correggere__ il Virtual Clock correttamente
* Infatti, se cambiassimo l'ora improvvisamente, potremmo causare errori in alcune applicazioni
* Conviene quindi accelerare o rallentare l'orologio, fino a raggiungere l'ora voluta
---
* È un protocollo non sicuro, a causa dell'utilizzo di certificati con data di scadenza

---
### FTP
* Viene usato per __trasferire dati__
---
* __RFC__: 959
* __Comunicazione__: porte TCP/20 e TCP/21
---
* La porta 21 viene usata per inviare comandi, la 20 per trasferire i dati
* Il client invia comnadi sulla porta 21. ad esempio:
	* __USER__, che serve per __autenticarsi__ nel server, passando lo username: Il server dorebbe rispondere 100, aspettandosi la password
	* __PASS__, che serve a passare la __password__ dell'utente. Il server dovrebbe rispondere 200
	* __PORT__ serve ad inviare il valore della porta effimera del client (Modalità __attiva__). Il server risponderà con 100, aspettando la richiesta di un file
	* __PASV__ serve ad attivare la modalità __passiva__, in cui sarà il serve a creare una porta effimera su cui il client si connetterà. Utile in caso di firewall attorno al client
	* __RETR__ serve a richiedere un file; dopo aver ricevuto questo comando il server comincia a trasmettere sulla porta 20, per poi chiudere la connessione a trasferimento terminato. A fine trasferimento, esso invia 200
	* __LIST__ funziona come un ls
	* __NOOP__ non fa niente, ma serve a mantenere la connessione sempre attiva, ed evitare che si chiuda per timeout
	* __PWD__ stampa la directory corrente
	* __CWD__ cambia la directory corrente
---
* Si può accedere al server in modalità anonima con lo username "anonymous". Permette di accedere ai dati pubblici del server, ma non permette il download dei file
---
* __SFTP__ è un metodo di crittografia dei dati inviati

---
### SMTP & ESMTP
* Viene usato per inviare email, messaggi inviati asincronamente
---
* __RFC__: 5321
* __Comunicazione__: porta TCP/25
* __Header__:
	* Formato da 72 caratteri.
	* Sono presento tre sezioni:
		* __From__: il mittente
		* __To__: il destinatario
		* __Subject__: l'argomento del messaggio
	* Ogni sezione __termina__ con i caratteri __`\r\n`.__
	* L'intestazione __finisce__ alla prima __riga vuota__
	* Subito sotto si trova il __messaggio__ vero e proprio. Esso __termina__ con i caratteri __`.\r\n`.__
---
* Il client viene chiamato __MUA__ (Mail User Agent), il server __MTA__ (Mail Transfer Agent)
* Per la comunicazione, viene usata una tecnica di __Store & Forward__, reminesciente delle cassette postali: 
	* Il __messaggio__ del MUA viene inviato ad un __secondo__ MTA, il quale si occuperà di __reinstradare__ il messaggio al destinatario. Questi dovrà poi accedere alla __mailbox__ presente sull'MTP per __ricevere__ il messaggio
	* Questo viene fatto così che il destinatario possa ricevere il messaggio anche se la sua macchina fosse spenta
---
* Ecco un esempio di comunicazione con il server per l'invio di una lettera
	*  __MUA__ apre una connessione di tipo __STREAM__ sulla porta __25__, per comunicare con il MTA. Venivano scambiati file di testo, passando i singoli caratteri __ASCII__ su 7 bit
	* Invia il messaggio __CONNECT__ 25, richiedendo la __connessione__ sulla porta 25. 
		* MTA risponde con __220__ (OK)
	* MUA risponde con __HELO__ seguito dal suo __indirizzo__, in forma numerica e simbolica
		* MTA risponde come __250__ (OK, ho capito chi sei)
	* MUA risponde con __MAIL FROM__, seguito dall'indirizzo del __mittente__, ovvero dell'utente, che invia io messaggio
		* MTA risponde nuovamente con 250
	* MUA risponde con __RCPT TO__, seguito dall'indirizzo del __destinatario__
		* MTA risponde nuovamente con 250
	* MUA risponde con __DATA__, seguito dal __contenuto__ della lettera
		* MTA risponde con __354__ (OK, dimmi il messaggio che vuoi inviare)
	* MUA risponde con tutto quello che vuole (?)
		* MTA risponde per l'ultima volta con 250: L'MTA ha __preso in carico__ il messaggio, e si occuperà di __portarlo a destinazione__.
	* MTA __chiude__ la connessione
---
* Si può inviare quello che si vuole, finchè sia in ASCII 7 bit
* Il servizio è __Best-Effort__
---
* La mancata autenticazione causa problemi di sicurezza, e vulnerabilità ad attacchi di tipo __SPAM__. Per questo viene introdotto l'__ESMTP__, che comunica con connessioni cifrate
* Si comunica sulla porta __587__
* Il messaggio iniziale diventa __EHCO__ (invece che HELO), il quale permette di accedere ad una fase di autenticazione (usando __USR__ e __PWD__)
---
* Nell'inviare dati che non sono file di testo, questi vengono codificati con __UUENCODE__, la quale usa il codice __RADIX64__.
* Questo tipo di comunicazione non è molto efficiente però, e per questo convine usare __FTP__ per dati molto grandi
---
* __MIME__, estensione di UEECODE, gestisce la codifica/decodifica. Vengono definiti anche i __MIME TYPE__, classificazione di tutti i tipi di dati codificabili
---
* Per poter __leggere__ dalla casella postale si usano due protocolli diversi:
#### POP3
* __RFC__: 1939
* __Comunicazione__: porta __TCP/110__, TCP/995 per la comunicazione sicura
---
* Il client comunica inviando __comandi__ codificati su __ASCII__ 7 bit.
	* __`list`__ richiede la lista dei messaggi presenti sulla MBOX
	* __`retr`__ richiede un messaggio specifico da ricevere
		* Si possono fare anche __`retr`__ __parziali__, richiedendo solo l'header per vedere se il messaggio è importante, e valga la pena scaricarlo. I metodi utilizzati non sono standardizzati
	* __`dele`__ richiede di cancellare un messaggio dalla MBOX
	* Ha senso scaricare le email in locale, così da tenere quelle importanti anche offline, e avere un backup sul server
#### IMAP4
* __RFC__: 3501
* __Comunicazione__: porta __TCP/143__
---
* A differenza del protocollo precedente, i __messaggi__ vengono __conservati__ solo sul __server__. Quando il __client__ richiede una __copia__, questa verrà salvata su una __cache__ temporanea locale
	* __Inizialmente__ si scarica l'__header__, __poi__ il __body__, solo se necessario
#### Webmail
 * Si accede al server tramite __browser__, autenticandosi per accedere alla propria MBOX, ed i dati vengono trasmessi tramite __HTTP__
* Questo __facilita__ ulteriormente la __condivisione__ della casella fra più dispositivi
---
### HTTP
* Usato per __trasferire dati__
* Possiede numerose versioni
	* __1.0__ del 1996, __RFC__ 1945
	* __1.1__ del 1997
	* __2.0__ del 2015, __RFC__ 7540
	* __3.0__ del 2022
---
* __Comunicazione__: TCP/80
* __Header__: Di lunghezza indefinita, contiene numerosi campi separati dal carattere `\r\n`. L'ultimo campo conterrà la __lunghezza__ totale dell'header. Alcuni esempi sono:
	* `Host:` -> Indica l'__indirizzo__ del server con cui comunichiamo
	* `Useragent:` -> Indica con quale __browser__ comunichiamo col server
	* `Accept-language: `-> Indica il __linguaggio__ che vogliamo usare
	* `Connection:` -> indica se __chiudere__ la __connessione__ dopo la comunicazione
			* Nella versione __1.0__, la comunicazione era __effimera__, e terminava dopo ogni singolo messaggio. Questo è stato __cambiato__ a partire dalla __1.1__
---
* Il client __comunica__ con dei __comandi__ codificati su ASCII 7 bit:
	* __GET__: serve a __richiedere__ il __download__ di un file (es: `GET risorsa http/1.0\r\n`) 
		* Dovrà contenere il __campo__ `host`. Questo servirà al __server__, per __comunicare__ con __più host__ contemporaneamente, usando questi protocolli. La richiesta non contiene niente nel body
	* __HEAD__: Usato dal __server__ per __rispondere__, avrà una struttura simile a get, con l'omissione del body del messaggio. La risposta positiva è 200. Nell'header potrebbero essere presenti tutti i __metadati__ del file. La richiesta non contiene niente nel body
		* In entrambi i comandi, viene restituita poi la parte header come risposta. Nel caso di HEAD, il client non reinvia il body _chiedere a ciccio_
	* __POST__: __aggiunge__ o scrive nel body dati di __variabili__ che ho precedentemente modificato nella form
	* Ci sono anche dei __metodi aggiuntivi__ che __non__ sono stati __implementati__: __PUT__, __DELETE__, __LINK__ e __UNLINK__
		* Non sono stati implementati in quanto il server __HTTP__ __non è autenticato__, e questi comandi __non avrebbero senso__, dando troppi poteri ad utenti non verificabili. 
			* Per questo motivo, __HTTP__ viene usato solo per il __download__, non l'upload, dei file
---
* Si possono costruire dei __GET__ __condizionali__, aggiungendo agli header una sezione __last modified__, che contiene la data dell'ultima modifica. 
* GET richiederà quindi un file che possiede una data di modifica __successiva__ a quella contenuta nell'header
* Se il file sul server ha data uguale o precedente a quella richiesta, il server rispondera con 304, body vuoto. In caso contrario, viene inviato il file richiesto
---
* __Cookies__ (definiti nell'__RFC__ 6265)
* Questi servono a __memorizzare__ i dati non salvati dal server
* Il client invierà una richiesta al server che contiene il campo __setcookie__ ed un campo nome=valore
* Quest'ultimo indica al server di __associare__ al __nome__ un particolare __valore__
* Questo sistema può essere utilizzato per permettere al __server__ di __ricordarsi__ il client, nel caso di una successiva comunicazione
---
* Nella versione __2.0__, si aprono più connessioni, allo scopo di ottimizzare le richieste col client
* Un problema di questo sistema è la possibilità di perdere dati durante la trasmissione, a causa della struttura dei router
* Per questo, si prova a __ritrasmettere__ -> flow-control
* Si invia il messaggio, e se il router non ha spazio per tenerlo, si richiede il rinvio, fino a quando non si può inviare
* Questo può causare un __blocco__ della rete!
* Per evitarlo, il client deve gestire il __numero__ di richieste che fa
* Successivamente al 3 way handshake, la comunicazione avviene nel seguente modo
	* __SLOW START__: Invio __pochi datagrammi__ per controllare che la rete funzioni. L'aumento è in modo __esponenziale__, e continuo finchè non mi arriva più l'ACK
	* __RECOVERY__: memorizzo l'ultima grandezza inviata e ricomincio da capo, finchè non ricevo un ACK. A questo punto, riprendo ad __aumentare__ la dimensione fino a che non arrivo alla __metà__ della quantità che ha causato la __congestione__
	* __AUMENTO LINEARE__: Continuo ad __aumentare__ la dimensione __linearmente__, fino ad arrivare ad un errore di __congestione__

---
### DHCP (Dynamic Host Configuration Protocol)
* Si occupa di gestire la __configurazione__ __IP__ dei dispositivi in una rete, specie nei casi in cui si rimuovono ed aggiungono spesso dispositivi
---
* __Comunicazione__: UDP/68 per il client, UDP/67 per il server
---
* Le __richieste__ avranno:
	* Nel Frame, il MAC dell'host come mittente e Broadcast come destinatario
	* Nell' Header IP,  0 nel mittente, Broadcast nel destinatario
* Le __risposte__ avranno
	* Nel Frame, MAC del server DHCP che risponde come mittente, MAC dell'host come destinatario
	* Nell'Header IP, I campi scambiati rispetto alla risposta
	* Nel Payload, l'indirizzo IP proposto dal server
* Il Client sceglierà una fra le varie proposte di server suggerite, ed invierà un rltimo messaggio, sempre usando l'indirizzo 0, con il nuovo indirizzo nel payload, così che gli altri possano sapere l'__indirizzo definitivo__.
* È possibile __programmare__ il router in modo tale che assegni ad uno stesso indirizzo MAC lo __stesso indirizzo IP__, utile specie se il dispositivo deve essere un server
---
* Oltre all'indirizzo IP, il client riceverà anche:
	* __Default Gateway__: l'indirizzo a cui connettersi per fare il primo hop, coincide con quello del router
	* __DNS Local__: L'indirizzo del server DNS locale, condiviso sulla rete
	* __NTP__: indirizzo del server NTP
	* __Netmask__: Una maschera di bit da sommare ad un indirizzo IP. Nel caso il risultato sia uguale al mio, quell'indirizzo appartiene alla mia rete