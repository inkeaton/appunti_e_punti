* Definito nell'RFC 5905 (nel 2010), è un protocollo usato per __sincronizzare__ gli __orologi__ di due macchine
* Esso risale al 1985, anno in cui veniva descritta la versione 0 nell'RFC 958
---
* Nelle macchine moderne, il tempo viene misurato tramite due orologi
	* l'__RTC__ (Real Time Clock), un orologio al litio, dotato di una batteria propria, il quale misura costantemente il tempo
	* L'__Orologio Virtuale__, un contatore conservato in memoria RAM, il quale salva il valore dell'RTC all'accensione, e continua ad accrescerlo tramite interrupt fino allo spegnimento
*  È __impossibile__ che questi valori siano perfetti, sarebbe necessario un __orologio__ ad altissima precisione, di tipo __atomico__
* Infatti, l'idea alla base dell'NTP sfrutta proprio questi orologi:
	* Avremo un __server__ collegato ad un __orologio atomico__. Egli avrà __l'ora esatta__. 
	* Collegeremo ad esso ulteriori server, fino a formare una __rete a livelli__. Al livello 0 avremo l'orologio, all'1 il primo server, al 2 i server collegati a quest'ultimo, e così via
* Otterremo così una struttura memore di quella DNS
---
* Immaginiamo ora un __client__, il quale desidera __sincronizzare__ l'ora con questa rete. Questi invierà un messaggio __DGRAM UDP__ sulla porta __123__
* Il server gli risponderà con un messaggio dello stesso tipo, sulla stessa porta, contenente l'__ora esatta__. Ma quale ora? Quella di __quando ha ricevuto il messaggio__
* A seconda della qualità della rete e della distanza, __potrebbe passare una quantità di tempo significativa__ fra la scrittura del messaggio e l'effettiva ricezione di esso da parte del client, inquinando il nostro valore
* L'unico modo per ovviare a questo problema è cercare di __prevedere e calcolare questo scarto__
---
* Possiamo innanzitutto calcolare il __Round Trip Time__, tramite la formula:
	* $(t_1 -t_0) + (t_3 -t_2)$ 
* Dove:
	* $t_0$: Tempo d'invio della richiesta
	* $t_1$: Tempo di ricezione della richiesta
	* $t_2$: Tempo d'invio della risposta
	* $t_3$: Tempo di ricezione della risposta
* Dividendolo per due, possiamo ricavare il valore medio di quello scarto, l'__offset__, non importa quanto grande, e __ricavarci l'ora attuale__
* Il __problema__ si trova quando la __comunicazione__ fra i due calcolatori è __instabile__: Nel caso la richiesta ci metta molto meno della risposta, la media sarebbe ingannevole
---
* La soluzione si trova nella __scelta__ del server con cui comunicare
* Prima di effettuare la misurazione vera e propria, effettueremo __una lunga serie di richieste__ a tutti i server NTP a noi disponibili
* __Col tempo__, potremo __notare__ quali hanno RTT costante, quali mi rispondono con costanza, e quelli che si trovano ai livelli più alti della struttura NTP
* In questo modo, __potremo__ __scegliere__ il server che ci da __minore possibilità di errore__
---
* Una volta ricevuto il nuovo valore dell'orologio, è importante __aggiornare correttamente__ il Virtual Clock
* Infatti, se __cambiassimo__ i valori __direttamente__, potremmo causare __errori__ nelle applicazioni che ne fanno uso, sopprattutto nel caso fossimo avanti
* La soluzione sta nel __rallentare__ o __accelerare__ la frequenza delle interrupt _tick_, che aggiornano il Clock, fino ad arrivare al valore desiderato
---
* La sicurezza di questo protocollo è molto bassa: questo è dovuto al fatto che fa uso di certificati di sicurezza dotati di data di scadenza, la cui validità può essere modificata proprio tramite gli attachi che tentano di prevenire...