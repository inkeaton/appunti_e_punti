### Porte
* Arrivati all'L4, il sistema deve ora comunicare come __smistare i messaggi fra le applicazioni__
* Per fare ciò, il sistema utilizza l'astrazione delle __porte__, numeri a 16 bit
* Le porte vanno __pensate__ come __frequenze__ o canali __su cui comunicare__. Due applicazioni su due macchine diverse scelgono su quali porte riceveranno i loro messaggi
* Le porte si dividono in due categorie:
	* __Wellknown__: sono porte __statiche__, __associate all'applicazione__. Gli indirizzi da __0 a 1023__ sono __riservate all'amministratore__ ed alle applicazioni di sistema, le __restanti__ sono utilizzabili dagli __utenti__. Ad esempio il protocollo HTTP usa la porta 80, HTTPS usa la 470..., il servizio email la 25
	* __Ephemeral__: Sono porte effimere, generate dal sistema e __associate temporaneamente all'applicazione__, cambiate ad ogni comunicazione

### UDP
* Esistono due protocolli utilizzati a questo livello, il primo è l'__UDP__ (RFC 768)
* Il suo __header__ è strutturato nel seguente modo:

![[UDP Header.png]]

* __16__ bit contenente la __porta sorgente__ e __16__ contenente la __porta di destinazione__
	* __16__ bit che indicano la __lunghezza del messaggio__ e __16__ che contengono un __Checksum__
* Questi è presente insieme al messaggio nel payload del datagramma
---
* La comunicazione avviene __senza connessione__: Un dispositivo invierà un messaggio ad un altro dispositivo passivo. Questi, una volta ricevuto il messaggio, potrà rispondere con una seconda comunicazione UDP
* Questo sistema __soffre__ ancora della __inaffidabilità__ della trasmissione a datagrammi: se perdiamo un pacchetto, non potremo far altro che inviare una nuova comunicazione richiedendo un rinvio
 
### TCP
* Il secondo protocollo utilizzato è il __TCP__
* Il suo __header__ è strutturato nel seguente modo:

 ![[TCP Header.png]]
 
	* __16__ bit contenente la __porta sorgente__ e __16__ contenente la __porta di destinazione__
	* __32__ bit contenenti il __Sequence Number__, un numero che indica il numero di byte inviati durante la sessione. Esso inizia a contare da un numero scelto casualmente
	* __32__ bit contenenti l'__Acknowledgment Number__, simile al sequence number, utilizzato dal ricevente, ha lo stesso valore di SEQ # più uno
	* __4__ bit contenenti la __lunghezza__ dell'header, __3__ bit dell'RSV, un campo __inutilizzato__, __9__ bit contenenti delle __Flags__ che identificano il messaggio. 
		* Queste sono: __ACK, URG, SYN, RST, FIN, PSH__
	* __16__ bit contenenti la __Receive Window__, dimensione del buffer nella memoria del kernel del ricevente, necessari per comprendere quanti dati si possono inviare al momento
	* __16__ bit contenenti un __Checksum__, __16__ riservati all'Urgent pointer, __inutilizzati__
	* Infine, rimane lo spazio per le __opzioni__, spesso non utilizzate
* Anch'esso viene memorizzato assieme al payload
---
* L'__idea__ dietro al TCP è quella di creare un __canale di comunicazione__, __stabile__, __bidirezionale__ e __molto affidabile__, fatto in modo da poter inviare __multipli messaggi__
* Il sistema viene inizializzato attraverso il cosiddetto __3-Way-Handshake__
	1. Inizialmente, il __primo host__ invia un messaggio con payload vuoto, contenente il __SEQ#__, generato randomicamente, e con la flag __SYN attiva__. Questo messaggio viene chiamato __SYN__, per Syncronize, e consiste nella __richiesta di connessione__
	2. Ricevuto il messaggio, nel caso in cui il __ricevente__ accetti la connessione, questi risponde con un secondo messaggio vuoto, contenente SEQ# ed il nuovamente generato __ACK#__, con le flag __SYN ed ACK attive__. Il messaggio viene chiamato __SYN/ACK__ e consiste in un'__accettazione della connessione__
	3. Infine, ricevuto il messaggio, il primo host invia un ultimo messaggio vuoto con solo la flag __ACK attiva__, chiamato __ACK__, per Acknowledgment. Questo consiste in una __conferma della ricezione del messaggio__
* Alla fine di questi passaggi, la connessione è __stabilita__.
* Ogni volta che un messaggio viene inviato, vengono aggiornati SEQ# e ACK#, ed il __destinatario__ invia un secondo __messaggio__ con flag __ACK attiva__. Questo funge da __conferma della ricezione__ del messaggio
* Nel caso il __mittente non riceva__ una conferma entro un tempo limite, questi __reinvierà__ il pacchetto
* Questo __garantisce__ l'__affidabilità__ del sistema
* Gli host dovranno comunicare tenendo conto della Receive Window, e spezzare le informazioni in più pacchetti se necessario
* Nel caso un host impieghi troppo tempo a svuotare il suo buffer, questi può inviare pacchetti __Keep Alive__, vuoti, inviati solo per impedire il timeout
* La connessione può essere conclusa in due modi:
	* Attraverso l'invio di un messaggio con flag RST attiva: Questa chiude immediatamente il canale, senza bisogno di conferme, ed è utilizzata in casi d'errore od'emergenza
	* Attraverso l'invio di un messaggio con flag FIN attiva: il ricevente finirà di inviare tutti i pacchetti ed in seguito invierà un messaggio con flag FIN/ACK attive. Infine il primo host conferma con un messaggio con ACK attiva, chiudendo la connessione
		* Quest'ultimo metodo conferma la ricezione corretta di tutti i pacchetti condivisi