* È un protocollo atto a __trasferire__ dati.
* Possiede numerose versioni. Le più importanti, che vedremo, sono:
	* __1.0__ del 1996, RFC 1945
	* __1.1__ del 1997
	* __2.0__ del 2015
	* __3.0__ del 2022
* È un __protocollo__ con struttura client/server, che __comunica__ sulla porta __TCP/80__. Ricorda in parte FTP e SMTP
* Come essi il client, una volta instaurata la connessione, __comunica__ con dei __comandi__ codificati su ASCII 7 bit
---
* Anche questo protocollo prevede degli __header__
* Questi saranno formati da numerosi __campi__, formati da __nomi__ seguiti da __due punti__ ed un __valore__. Se ne possono includere quanti se ne vogliono.
* Facciamo un esempio:
	* Vogliamo __richiedere__ il file `prova`. Useremo il comando __`GET`__ nel seguente modo:
		* `GET risorsa http/1.0\r\n`  (1.0 si riferisce alla versione del protocollo)
	* L'__header__ del messaggio potrà contenere i seguenti __nomi__:
		* `Host: indserver \r\n` -> Indica l'__indirizzo__ del server con cui comunichiamo
		* `Useragent: ` -> Indica con quale __browser__ comunichiamo col server
		* `Accept-language: `-> Indica il __linguaggio__ che vogliamo usare
		* `Connection:` -> indica se __chiudere__ la __connessione__ dopo la comunicazione
			* Nella versione __1.0__, la comunicazione era __effimera__, e terminava dopo ogni singolo messaggio. Questo è stato __cambiato__ a partire dalla __1.1__
		* Nell'ultimo campo inseriremo la __lunghezza__ del __body__ del messaggio 
_nel cartaceo c'è la risposta del server durante la fase di connessione_
---
* Richieste e risposte hanno una struttura simile
* Metodi definiti in questo protocollo:
	* __GET__: serve a __richiedere__ il __download__ di un file (es: `GET risorsa http/1.0\r\n`) dovrà contenere il __campo__ `host`. Questo servirà al __server__, per __comunicare__ con __più host__ contemporaneamente, usando questi protocolli. La richiesta non contiene niente nel body
	* __HEAD__: Usato dal __server__ per __rispondere__, avrà una struttura simile a get, con l'omissione del body del messaggio. La risposta positiva è 200. Nell'header potrebbero essere presenti tutti i __metadati__ del file. La richiesta non contiene niente nel body
		* In entrambi i comandi, viene restituita poi la parte header come risposta. Nel caso di HEAD, il client non reinvia il body _chiedere a ciccio_
	* __POST__: __aggiunge__ o scrive nel body dati di __variabili__ che ho precedentemente modificato nella form
* Un server http/1.0 deve possedere questi tre protocolli per essere definito tale
---
* Ci sono anche dei __metodi aggiuntivi__ che __non__ sono stati __implementati__: PUT, DELETE, LINK e UNLINK
* Non sono stati implementati in quanto il server __HTTP__ __non è autenticato__, e questi comandi __non avrebbero senso__, dando troppi poteri ad utenti non verificabili. 
* Per questo motivo, __HTTP__ viene usato solo per il __download__, non l'upload, dei file
---
* Data la connessione effimera della versione 1.0, per il server ogni richiesta è la prima
* Le __richieste__ sono __IDEMPOTENTI__, in quanto il numero di volte che vengono inviate non varia la risposta
* Il __server__ __non__ __memorizza__ le __informazioni__ inviate al client, ma per __velocizzare__ le procedeure di connessione ripetuta con il client, viene adottata delle tecniche di __caching__, sul client, dotate di data di scadenza, per consistenza
---
* Si possono costruire dei __GET__ __condizionali__, aggiungendo agli header una sezione __last modified__, che contiene la data dell'ultima modifica. 
* GET richiederà quindi un file che possiede una data di modifica __successiva__ a quella contenuta nell'header
* Se il file sul server ha data uguale o precedente a quella richiesta, il server rispondera con 30, body vuoto. In caso contrario, viene inviato il file richiesto
---
* __Cookies__ (definiti nell'RFC 6265)
* Questi servono a __memorizzare__ i dati non salvati dal server
* Il client invierà una richiesta al server che contiene il campo __setcookie__ ed un campo nome=valore
* Quest'ultimo indica al server di __associare__ al __nome__ un particolare __valore__
* Questo sistema può essere utilizzato per permettere al __server__ di __ricordarsi__ il client, nel caso di una successiva comunicazione