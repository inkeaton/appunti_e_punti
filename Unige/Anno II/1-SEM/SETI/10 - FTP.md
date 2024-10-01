* l'__FTP__ (File Transfer Protocol) è un protocollo di trasmissione destinato al __trasferimento di file__
* Viene descritto nell'RFC 959, con alcuni aggiornamenti aggiunti in RFC successivi
---
* Il processo consiste nell'instaurare una __connessione__ di tipo __TCP__ fra due dispositivi, in modo tale che un __client__ sia in grado di __accedere__ al __file system__ del __server__
* Vengono utilizzate __due porte__ in questo processo: __21/TCP__ destinata al __controllo__, e __20/TCP__ destinata alla __connessione__ dei dati
* La prima servirà quindi per l'invio di comandi, e verrà usata principalmente dal client, la seconda per la trasmissione dei dati, usata principalmente dal server
* Aperta la connessione sulla porta __21__, il __client__ comincia ad inviare comandi codificati in ASCII, di lunghezza 3-4 caratteri
* Il server __risponderà__ con un __numero__ decimale su tre cifre. 
* In base al __valore__ della prima cifra, __cambia il significato__
	* __1__ vuol dire ok __parziale__ (dimmi di più)
	* __2__ significa ok __completo__
	* __3__ è un ok totale
	* __4__ indica il __rifiuto temporaneo__ dell'azione
	* __5__ il __rifiuto totale__
* Anche il __valore__ della __seconda__ cifra __cambia__ il significato: 
	* __0__ Indica aspetti sintattici
	* 1 indica informazioni
	* 2 connessioni
	* 3 autenticazione
	* 4 non viene usato
	* 5 file system
* Il Server agisce poi al contrario, come un client, lavorando dalla porta 20, inviando ad una porta effimera aperta sul client, nella modalità connessione dati
---
* I __comandi__ che possono essere inviati sono ad esempio: 
	* __USER__, che serve per __autenticarsi__ nel server, passando lo username: Il server dorebbe rispondere 100, aspettandosi la password
	* __PASS__, che serve a passare la __password__ dell'utente. Il server dovrebbe rispondere 200
	* __PORT__ serve ad inviare il valore della porta effimera del client. Il server risponderà con 100, aspettando la richiesta di un file
	* __RETR__ serve a richiedere un file; dopo aver ricevuto questo comando il server comincia a trasmettere sulla porta 20, per poi chiudere la connessione a trasferimento terminato. A fine trasferimento, esso invia 200
	* __LIST__ funziona come un ls
	* __NOOP__ non fa niente, ma serve a mantenere la connessione sempre attiva, ed evitare che si chiuda per timeout
	* __PWD__ stampa la directory corrente
	* __CWD__ cambia la directory corrente
---
* I messaggi TCP sono passati in __chiaro__, quindi __possono essere facilmente "sniffati"__ ed intercettati
* Sono stati __creati__ quindi dei __metodi__ per __crittografare__ i dati condivisi
	* FTPS
	* __SFTP__: Quest'ultima è quella più usata, anche in SSH, cifra entrambi i canali di comunicazione
---
* Si può anche __accedere__ in modo __anonimo__ al server, usando lo username "__anonymous__" (non sarà necessaria alcuna password specifica, si può usare quella che si vuole)
* In questo modo si può __accedere__ ai __dati pubblici__ del server, non a quelli privati degli utenti
* Si può accedere sia in __modalità__ sola __lettura__ che sola __scrittura__. Nel caso di quest'ultima il client può scrivere sui file e caricarne altri, ma non può scaricare dati
---
* Nella modalità __attiva__, ci può essere la __complicazione__ della presenza di un firewall intorno al client. Questo restringe le possibilità del server nell'inviare dati
* Useremo quindi la __modalità Passiva__.
	* Invece di essere il client a creare una porta su cui comunica il server, è quest'ultimo a creare una porta effimera a cui il client si connetterà
* Per attivarla, usiamo il comando __PASV__ invece di PORT
---
* Oggigiorno, l'__HTTP__ ha __sostituito__ l'FTP, ma __non implementa__ tutte le sue funzionalità
---
* Per __usare__ il __protocollo__ FTP, esiste una __applicazione omonima__, FTP, appunto, che traduce i comandi che le passiamo
* Si può se no usare l'__applicazione Telnet__, che si occupa di connessioni TCP, due volte, una per canale. Essa permette di collegare stdin e stdout dell'utente con la connessione verso il server