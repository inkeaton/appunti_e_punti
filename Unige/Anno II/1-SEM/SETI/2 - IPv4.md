* A partire dall'invenzione del telefono, i dati venivano trasferiti direttamente, tramite la cosiddetta __commutazione a circuito__, collegando i cavi fra gli intrelocutori quando necessario
* Oggigiorno si usa la __commutazione a pacchetti__
* Questa consiste nell'inviare informazioni in unità finite di bit, chiamate __pacchetti__ in L2 o __datagrammi__ in L3
* Questi vengono passati fra router e router tramite la tecnica __Store & Forward__, in cui ogni router riceve un pacchetto, lo analizza, e lo invia al successivo, uno per volta
---
* Il protocollo di comunicazione più usato è l'__IPv4__ (RFC 792), il quale lavora insieme all'__ICMP__ (RFC 793)
* Quest'ultimo si occupa di trasmettere i __messaggi d'errore__ di un eventuale comunicazione
* In caso d'errore, il pacchetto verrà eliminato. I router lavorano in modalità __Best Effort__, in cui tentano di recapitare ogni pacchetto inviato
* Ogni __protocollo__ organizza i suoi __datagrammi__ in modo __diverso__. Vediamo ora l'organizzazione dell'__IPv4__
* Questi datagrammi sono organizzati in due sezioni:
	* L'__Header__ o intestazione è una parte che contiene informazioni sul messaggio
	* Il __Payload__ contiene le informazioni che vengono trasmesse
---
* L'__Header__ è organizzato in linee da 32 bit, nel seguente modo:
	* Nella __prima__ riga ci sono:
		* __4__ bit che indicano la __versione__ del protocollo
		* __4__ bit che indicano quanto è __lungo__ in totale l'__header__
		* __8__ bit indicano il __Service Type__, una feature mai utilizzata che indicava il tipo di servizio del pacchetto
		* __16__ bit che indicano la __lunghezza totale__ del datagramma
	* Non vederemo l'organizzazione della __seconda__, complessa per ora
	* Nella __terza__ ci sono:
		* __8__ bit chiamati __Time to Live__ (TTL), il quale è un numero diminuito ad ogni passaggio fra router. Se raggiunge 0, il datagramma viene eliminato. Questo serve ad __evitare loop__ in cui il datagramma gira all'infinito fra router
		* __8__ bit chiamati __Next Level Protocol__ (NLP), i quali indicano il metodo di __codifica__ del __payload__ a livello L4
		* __16__ bit chiamati __Checksum__, i quali sono __bit di parità__ ottenuti dalla somma dei bit delle linee a gruppi di 16. Servono a capire se si sono verificati errori
	* Nella __quarta__ riga è presente l'__indirizzo__ IP del __mittente__
	* Nella __quinta__ riga, l'__indirizzo__ del __destinatario__
	* Infine, possono essere presenti __ulteriori linee__ contenenti __opzioni__ aggiuntive, ma vengono __raramente utilizzate__
	
## Indirizzi IP
* Gli indirizzi IP sono i corrispettivi del numero di telefono, numeri che identificano una macchina
* Questi sono composti da 4 byte, contenenti 4 numeri
* Questi byte vengono divisi in due sezioni:
	* L'__Indirizzo di Rete__ o Gateway, che identifica la __rete locale__ a cui è connesso l'host
	* L'__Indirizzo di Host__, che identifica l'__host__ nella rete
* Il __numero di bit__ riservato ad ognuno __non è fisso__: una volta esistevano tre standard:
	* __A__: __1__ byte per la rete, __3__ per l'host
	* __B__: __2__ byte per la rete, __2__ per l'host
	* __C__: __3__ byte per la rete, __1__ per l'host 
* Questo metodo però __limitava__ il numero di host ed indirizzi utilizzabili
* Perciò oggigiorno si utilizza il metodo della __Netmask__: insieme all'indirizzo viene comunicata anche un ulteriore linea da 4 byte, in cui il numero di bit uguale ad __1__ indica quanti __bit sono riservati alla rete__, i rimanenti __0__ quanti sono __riservati all'host__
---
* Oltre agli indirizzi IP pubblici, esistono anche gli indirizzi IP __privati__
* Questi vengono __utilizzati__ in reti LAN, __scollegate__ da altre reti, e __non vengono instradati__ dai router
* Questi __non__ devono essere __unici__. Solitamente iniziano con 192.168....
* L'indirizzo 127.0.0.0 identifica l'host su cui si sta operando
* Esistono anche indirizzi chiamati __Broadcast__, i quali identificano una __sottorete__, e permettono di comunicare con tutti gli host connessi ad essa. Essi possiedono la sezione host dell'indirizzo composta da tutti 1