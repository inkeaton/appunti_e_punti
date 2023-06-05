* Il protocollo usato per i messaggi email è l'__SMTP__, uno dei più utilizzati in rete.
	* In precedenza veniva usato l'FTP
* SMTP __automatizza__ la trasmissione fra utente e destinatario
* Esso utilizza una modalità di connessione __asincrona__: Non è necessaria la presenza costante di mittente e destinatario, in quanto essi comunicano in attimi di tempo diversi
* Definito nell'RFC 5321. La prima versione moderna risale al 1985
---
* Il client viene chiamato __MUA__ (Mail User Agent), il server __MTA__ (Mail Transfer Agent)
* Per la comunicazione, viene usata una tecnica di __Store & Forward__, reminesciente delle cassette postali: 
	* Il __messaggio__ del MUA viene inviato ad un __secondo__ MTA, il quale si occuperà di __reinstradare__ il messaggio al destinatario. Questi dovrà poi accedere alla __mailbox__ presente sull'MTP per __ricevere__ il messaggio
	* Questo viene fatto così che il destinatario possa ricevere il messaggio anche se la sua macchina fosse spenta
* Esistono poi due protocolli, __POP__ e __IMAP__, definiti per accedere alla mailbox 
---
* Vediamo ora la versione iniziale del protocollo
	* __MUA__ apre una connessione di tipo __STREAM__ sulla porta __25__, per comunicare con il MTA. Venivano scambiati file di testo, passando i singoli caratteri __ASCII__ su 7 bit
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
* Il servizio è __Best-Effort__. Nel caso il messaggio __non__ sia __recapitato__ a causa di errori, uno degli MTA che si occupato di trasmetterlo __comunicherà__ all'__MUA__ dell'accaduto
---
* Una debolezza del sistema consiste nella __mancata autenticazione__ dell'indirizzo del mittente e dell'host. Questo permette di compiere diversi tipi di attacchi
* Uno è lo __SPAM__. Consiste nell'inviare un numero molto elevato di messaggi a chiunque, __intasando__ la rete ed il sistema di MTA
* Il mittente può benissimo usare un indirizzo __falso__ e "nascondersi"
* Per contestare lo spam è stato introdotto l'__open relay__ (Un MTA che accetta connessioni da chiunque)
---
* Un evoluzione si ha con il protocollo __ESMTP__, il quale permette di comunicare utilizzando connessioni __cifrate__
* Si comunica sulla porta __587__
* Il messaggio iniziale diventa __EHCO__ (invece che HELO), il quale permette di accedere ad una fase di autenticazione (usando __USR__ e __PWD__)
---
* Sono stati introdotti dei sistemi di __filtraggio__, capaci di __riconoscere__ le __email SPAM__ negli MTA, prima ancora di reinstradarle. Questo però non impedisce di inviare questi messaggi
---
* Per poter inviare cose che non sono file di testo si usa la codifica __UUENCODE__, la quale usa il codice __RADIX64__, codice che codifica i dati in __base 64__, usando un sottinsieme di 64 simboli __ASCII__ (0-9, a-z, A-Z)
* Nella comunicazione, invio i dati __bit__ per __bit__. I primi __6 bit__ vengono codificati come un singolo __carattere__ RADIX64
* Questi verranno poi tradotti a destinazione
	* Questo tipo di __comunicazione__ determina __ridondanza__. Nel caso di __dati molto grandi__, conviene usare il protocollo __FTP__
* Vengono messi __72__ caratteri per __riga__, fra le righe viene messo in automatico dall'UEECODE un \<LF\>
* __MIME__, estensione di UEECODE, gestisce la codifica/decodifica. Vengono definiti anche i __MIME TYPE__, classificazione di tutti i tipi di dati codificabili