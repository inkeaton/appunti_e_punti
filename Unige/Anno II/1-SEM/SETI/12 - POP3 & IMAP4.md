* L'Header di SMTP è formato da 72 caratteri.
* Sono presento tre sezioni:
	* __From__: il mittente
	* __To__: il destinatario
	* __Subject__: l'argomento del messaggio
* Ogni sezione __termina__ con i caratteri __`\r\n`.__
* L'intestazione __finisce__ alla prima __riga vuota__
* Subito sotto si trova il __messaggio__ vero e proprio. Esso __termina__ con i caratteri __`.\r\n`.__
---
* Per __leggere__ i messaggi, il __ricevente__ deve accedere alla __Mail Box__ presente sul __server__ SMTP
* Per __trasferire__ i messaggi, si usano due diversi protocolli:
* __POP__ (V3)
	* Definito nell'RFC 1939, di tipo applicativo, __comunica__ sulla porta __TCP/110__
	* Il client comunica inviando __comandi__ codificati su __ASCII__ 7 bit.
	* __`list`__ richiede la lista dei messaggi presenti sulla MBOX
	* __`retr`__ richiede un messaggio specifico da ricevere
		* Si possono fare anche __`retr`__ __parziali__, richiedendo solo l'header per vedere se il messaggio è importante, e valga la pena scaricarlo. I metodi utilizzati non sono standardizzati
	* __`dele`__ richiede di cancellare un messaggio dalla MBOX
	* Ha senso scaricare le email in locale, così da tenere quelle importanti anche offline, e avere un backup sul server
* __IMAP__ (V4)
	* Definito nell'RFC 3501
	* A differenza del protocollo precedente, i __messaggi__ vengono __conservati__ solo sul __server__. Quando il __client__ richiede una __copia__, questa verrà salvata su una __cache__ temporanea locale
	* __Inizialmente__ si scarica l'__header__, __poi__ il __body__, solo se necessario
---
* Un __alternativa__ a questi protocolli è il sistema di __Webmail__
* Si accede al server tramite __browser__, autenticandosi per accedere alla propria MBOX, ed i dati vengono trasmessi tramite __HTTP__
* Questo __facilita__ ulteriormente la __condivisione__ della casella fra più dispositivi