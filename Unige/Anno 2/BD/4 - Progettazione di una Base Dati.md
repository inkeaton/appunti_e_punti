 * La progettazione di una base dati segue i seguenti passi:
1. __Requisiti__
	* Inizialmente __analizziamo__ i __dati__ che devono essere organizzati, sia essi di per sè, che le descrizioni date dai clienti
2. __Progettazione Concettuale__
	* __Strutturiamo__ i dati in un __modello concettuale__. Il nostro obbiettivo è comprendere perfettamente __cosa__ sono i dati che organizziamo
3. __Progettazione Logica__ 
	* In questo passo dobbiamo capire __come__ organizzare i dati. Dobbiamo considerare due componenti principali
		* Il __modello effettivo__ in cui dovremo organizzare il database (Nel nostro caso, il modello relazionale)
		* Il __carico di lavoro__, ovvero i dati e le operazioni eseguite su essi
			* Vale la regola __80-20__: l'ottanta per cento delle operazioni effettuate sono solo il venti per cento delle operazioni possibili. Conviene quindi __ottimizzare__ questo venti per cento
	* I mezzi principali per comprendere la trasformazione della base di dati sono due:
		1. __Ristrutturazione__
			* Consiste nel __rimuovere o modificare__ certi elementi che sono intraducibili nel modello effettivamente usato
			* Effettuata tramite:
				* __Eliminazione__: Rimozione di elementi intraducibili (esempio, attributi multivalore, composti o gerarchie)
				* __Analisi delle ridondanze__: Comprensione di informazioni ripetute o facilemente ricavabili
				* __Partizionamenti e accorpamenti__: Suddivisione o unione di entità sulla base di attributi (verticale) o sottoinsiemi di istanze (orizzontale)
		2. __Traduzione__
			* Dobbiamo ora effettivamente trasformare il modello __concettuale__ in un modello logico. 
			* Nel caso del modello relazionale, __tradurremo__ le componenti nel seguente modo:
				* __Entità__ --> Relazioni
				* __Attributi__ delle Entità --> Attributi delle relazioni
				* __Identificatori__?
					* Interni --> Chiavi candidate
					* Esterni o Misti --> Chiave esterna
				* __Associazioni__?
					* Grado __2__
						* Possono essere trasformate in __chiavi esterne__ o in __tabelle__, relazioni speciali contenenti puntatori alle relazioni a cui si riferisce l'associazione, e gli attributi della relazione
					* Grado __3 o Superiore__
						* Direttamente tradotte in __tabelle__