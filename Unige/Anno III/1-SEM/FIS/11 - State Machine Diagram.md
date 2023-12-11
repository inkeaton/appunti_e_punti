+ Diagramma di Modellazione **Dinamica**
+ Le **state machine** vengono usate per descrivere il **comportamento** di una **entità** come variazione del suo stato interno quando è sottoposta a sollecitazioni dal mondo esterno
	+ Un entità può essere un sistema software, sistema hardware, classe OO, entità del mondo reale, etc.
+ Queste entità possono reagire in maniera differente all'input in base al proprio **stato interno** 
+ È **differente** da un diagramma di **iterazione**, in quanto esso descrive un insieme di oggetti che si scambiano messaggi per raggiungere un dato obiettivo, mentre questo descrive la **sequenza di stati** in cui si trova un oggetto durante il suo ciclo di vita e in risposta a eventi
+ Uno **stato** rappresenta una **situazione** (nella vita di un oggetto) durante la quale delle **condizioni** vengono **soddisfatte** e delle **attività** possono essere **eseguite**
	+ Può anche intendere, a livello più basso, una combinazione dei valori dei campi di un oggetto
+ Usiamo questo genere di diagramma per descrivere entità che hanno una logica interna interessante e complessa 
---
+ Le State machine sono rappresentate da **grafi**, in cui
	+ nodo: stato
	+ arco: transizione (evento + guardia + attività)
+ La macchina è associata ad un entità, e riceve gli eventi in una coda
+ Ogni evento viene estratto solo in seguito all'esecuzione del precedente
+ Se più di una transizione è eseguibile in un momento, solo una viene eseguita, non deterministicamente
+ Esistono nodi **iniziali** (unici) e **finali** (multipli), che rappresentano l'inizio e la fine dell'esecuzione. Sono rappresentati da puntini neri
+ Le **transizioni** rappresentano come si passa da un evento all'altro. Possiedono tre componenti **facoltativi**:
	+ **Evento**: un ‘trigger’ che attiva il passaggio di stato. Ne esistono di multipli tipi (messaggi, temporali, di cambiamento, etc)
		+ Se manca l’evento vuol dire che la transizione avviene immediatamente
	+ **Guardia**: una condizione che, se vera, permette il passaggio di stato
		+ La mancanza della guardia indica che la transizione è intrapresa ogni volta che si verifica l’evento
	+ **Attività**: una o più azioni che sono compiute prima di cambiare stato. Esprimibili in modo informale, o in pseudo-linguaggio
		+ Se manca l’attività significa che durante la transizione si cambia stato ma non si fa altro
+ Le **attività interne** sono attività compiute senza bisogno di un evento scatenante
	+ Si può segnare entry o exit per specificare che vengono eseguite all'entrata/uscita dallo stato, o do, per indicare che vengono eseguite continuamente, finché si è nello stato
+ Esistono anche le **self-transition**, le quali attivano entry ed exit, ma non il resto
![[StateMachine.png]]
---
+ Uno stato può essere **composto** da più stati semplici, così da aiutare a suddividere la **complessità** del modello, o modellare la **concorrenza**
	+ Essi possiedono entry ed exit point multipli, per rappresentare i vari punti da cui può entrare od uscire l'input
---
+ Come possiamo implementare una macchina simile?
	+ In linguaggi che non le supportano come:
		+ **Switch case**
		+ **Design Pattern State**
			+ Si rappresenta ogni stato con una classe e si usa il polimorfismo per variare il comportamento
		+ **Tabelle di Stato**
			+ Creabili con **SMC** (*da rivedere*)