* I socket di tipo __stream__ sono basati sul protocollo __TCP__
* Per comunicare, bisogna creare un __canale__ di connessione fra due socket, uno di tipo __client__, uno di tipo __server__
* Questi vengono creati dalla syscall __socket__(), con le dovute flag
* __Client__:
	* Esso ha il ruolo __attivo__ nella comunicazione.
	* Questa comincia quando esso invia una richiesta di inizio comunicazione, tramite la syscall __connect__().
	* Questa prende come argomenti l'__fd__ che identifica il socket del client, e l'__indirizzo__ del destinatario
		* L'indirizzo si ottiene tramite la syscall __getaddrinfo__(), che traduce gli indirizzi nel formato corretto. Traduce anche gli URL, usando il sistema dei DNS
	* Dopo aver inviato la richiesta, ed aver avviato la connessione, la comunicazione avviene tramite le syscall __send__() e __recv__()
* __Server__:
	* Esso ha il ruolo __passivo__ nella comunicazione
	* Dopo esser stato creato, il socket usa __bind__() per associarsi ad una porta, unica per ogni socket. Dopo di che chiama __listen__(), per rimanere in attesa di una richiesta di comunicazione su quella porta
	* Ricevuta la richiesta, esso usa __accept__() per accettarla, ottenendo un nuovo __fd__.
	* Il server userà questo socket per __comunicare__ con quel client, usando send() e recv().
	* Questo sistema permette ad un server di __comunicare con più client contemporaneamente__, usando i diversi fd
---
* È possibile usare __connect__() __anche__ in un socket di tipo __DGRAM__, per mandare un gran numero di messaggi allo stesso destinatario.
* La lunghezza dei messaggi in __DGRAM__ è __limitata__ a 2^16 byte, a causa dell'utilizzo di datagrammi. __STREAM__ __non ha queste limitazioni__
* __STREAM__ è sempre __più sicuro__ di DGRAM. In particolare, STREAM è molto sicuro sulle __lunghe distanze__ e sulle reti geografiche, rendendo l'IP spoofing quasi impossibile. Questa sicurezza __non c'è a livello locale__, in cui si usano indirizzi MAC
---
* Possiamo paragonare la velocità tramite un __ping__
* L'applicazione ping manda un messaggio all'app pong, la quale risponde
* Usando dei diagrammi di questi test, paragonando la velocità alla quantità di messaggi inviati notiamo che:
	* Quando inviamo messaggi __brevi__, __UDP__ è superiore a TCP
	* Nei __lunghi__, __TCP__ supera UDP grazie al controllo di flusso. Inoltre, UDP non può superare i 2^16 byte per messaggio, rallentandolo