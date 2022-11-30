* Nel corso di __Sistemi di Elaborazione e Trasmissione Dati__ studieremo sia la struttura dei sistemi operativi che il funzionamento della trasmissione di dati fra calcolatori
---
* Ricordando dal precedente corso di AdC, possiamo descrivere un calcolatore con una struttura a livelli, ognuno dei quali caratterizzato da una diversa quantità di astrazione:
	1. L'__Hardware__: l'insieme dei circuiti fisici che compongono la macchina
	2. Il __Firmware__: l'insieme dei programmi di base impiantati nel dispositivo 
	3. Il __Sistema Operativo__: il programma principale del dispositivo, il quale grazie alle trap ed interrupt handler riesce a far girare altri programmi
		* A questo livello si arriva ad avere una cosiddetta __macchina virtuale__
	4. Le __Librerie__: frammenti di codice già scritto e riutilizzabile, utilizzati dalle applicazioni
	5. Le __Applicazioni__, programmi creati dall'utente
*  In ogni livello, si opera in modi simili, passando dai circuiti logici dell'hardware al codice delle applicazioni
---
* Dobbiamo immaginare in modo simile il cosiddetto __Internet Stack__, ovvero la struttura che descrive l'organizzazione dei __protocolli di comunicazione__
	1. L'__Hardware:
		* In questo livello sono presenti i dispositivi che vogliamo collegare fra di loro, gli __host__ con le loro __schede d'interconnessione__, ed il __modem__
	2. Il __Data Link__:
		* Nel livello data link consideriamo il software presente nei modem e negli host. Questi, collegati tramite cavi o connessioni wireless, permettono di trasmettere dati fra di essi, formando una rete locale, o __LAN__
	3. Il __Network__
		* In questo livello viene introdotto un nuovo dispositivo, il __router__
		* Questi viene integrato nella LAN, ed ha l'obbiettivo di connettersi ad altri router, così da __connettere fra di loro più LAN__, formando una __WAN__
		* Questi router potranno essere parti di ulteriori reti LAN od essere __nodi intermedi__, punti di passaggio per arrivare all'host richiesto
		* Questo è l'_inter-net_, la connessione _fra reti_
	4. Il __Transport__
		* Ora che gli host sono connessi fra di loro, dobbiamo fare in modo che singole __applicazioni__ di diversi computer siano in grado di interagire fra di loro
		* Viene quindi introdotto il concetto di __porta__. Va immaginato come __un posto in cui scambiarsi informazioni__. Allo scopo di interagire fra di loro, due applicazioni comunicheranno sulla stessa porta
		* Nell'__HTTP__ viene usata la porta __80__, nel __SMTP__ la porta __25__
		* Esiste anche il _port binding_, un metodo in cui un applicazione utilizza sempre una determinata porta, che il computer riserva ad essa
	5. __Applications__
		* In questo livello vengono implementate ulteriori funzionalità, come la trasmissione di file contenenti metadati
		* Verrà approfondita in seguito
---
* In una relazione __Client-Server__, il client è un host capace di inoltrare una richiesta dati ad un server, il quale invierà i dati richiesti. Il server non è in grado di effettuare richieste al client