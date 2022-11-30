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
		* `GET prova http/1.0\r\n`  (1.0 si riferisce alla versione del protocollo)
	* L'__header__ del messaggio potrà contenere i seguenti __nomi__:
		* `Host: indserver \r\n` -> Indica l'__indirizzo__ del server con cui comunichiamo
		* `Useragent: ` -> Indica con quale __browser__ comunichiamo col server
		* `Accept-language: `-> Indica il __linguaggio__ che vogliamo usare
		* `Connection:` -> indica se __chiudere__ la __connessione__ dopo la comunicazione
			* Nella versione __1.0__, la comunicazione era __effimera__, e terminava dopo ogni singolo messaggio. Questo è stato __cambiato__ a partire dalla __1.1__
		* Nell'ultimo campo inseriremo la __lunghezza__ del __body__ del messaggio 
_nel cartaceo c'è la risposta del server durante la fase di connessione_