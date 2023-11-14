+ Un **modello di sviluppo** è una modellazione astratta del processo di sviluppo del software
+ L'utilizzo di uno di essi permette di dare **ordine**, **controllo** e **ripetibilità** al processo di sviluppo, così da migliorare la produttività, e la **qualità** finale del prodotto
+ Studiarli è **fondamentale**, in quanto dalla scelta di uno di essi può dipendere la buona riuscita del progetto
---
+ Essi sono classificabili in uno spettro, i cui opposti sono:
	+ **Prescrittivi**, rigidi e dipendenti da un piano
		+ Il più prescrittivo è il **RUP**, con 120 regole
	+ **Adattivi**, flessibili e basati sui programmatori
		+ Il più adattivo è il **Kanban**, con 3 regole
---
#### Code N' Fix
+ Agli albori dello sviluppo del software, negli anni 40, non si seguiva alcun metodo di processo
+ Solitamente i programmi erano utilizzati dai loro creatori, e si creavano "per tentativi", codificando e sistemando i bug che si creavano lungo la strada
+ Questo metodo viene chiamato Code N' Fix, e ***non*** è un **metodo di processo**
#### Waterfall
+ Questo è uno dei **metodi** di sviluppo **più famosi** ed **utilizzati**
+ Fu cominciato da utilizzare negli anni 50 a livello militare, fu definito a livello scientifico negli anni 70, e si è diffuso negli anni 70-80
+ Strutturato in 5 fasi:
	0. **Studio di Fattibilità**
		+ Fase aggiuntiva
		+ Prevede un'analisi della fattibilità del progetto, tenendo conto del budget e del tempo necessario
	1. **Raccolta, analisi e specifica requisiti**
		+ Si chiede al cliente quali siano le specifiche funzionalità richieste
		+ Il deliverable consente nella definizione o specifica dei requisiti
	2. **Design**
		+ Viene definita l'architettura software (high level design) e la struttura interna delle sue componenti (low level design)
		+ È preferibile un design astratto, sconnesso dall'implementazione pratica
		+ Il deliverable consiste nella specifica del design, scritto in UML
	3. **Implementazione o Codifica**
		+ Viene implementato il design descritto
		+ A seconda del modello, può essere una fase molto noiosa, o creativa
		+ Il deliverable è il codice del sistema
			+ In alcuni casi, questo passaggio viene saltato, ed il codice viene automaticamente generato dal modello tramite alcuni tool (MMD)
	4. **Testing**
		+ Il codice viene testato, e vengono riportati gli eventuali bug
		+ Il deliverable sono il test plan (cosa è stato testato) ed il test report (cosa si è scoperto)
			+ Le aziende tendono a spendere il 40-50% delle risorse di sviluppo su questa fase
	5.  **Consegna e Manutenzione**
		+ Il codice viene infine consegnato al cliente, con le dovute documentazioni e guide
		+ In seguito, si mantiene il codice, sviluppando patch, fixes, aggiornamenti, etc.
			+ Anche questa fase è tenuta molto in considerazione
---
+ **Vantaggi**:
	+ Introduce le fasi di analisi e design
	+ Pospone la fase d'implementazione, permetto di ragionare ad un livello maggiormente astratto
	+ Introduce ordine e disciplina nello sviluppo
+ **Svantaggi**
	+ È lineare e rigido, con l'impossibilità di far uso del feedback
	+ La consegna al cliente arriva dopo molto tempo, con la possibilità che siano cambiati i requisti
	+ Errori in fase iniziale possono avere gravi conseguenze sulle fasi finali
---
##### Varianti
+ Waterfall con **prototipazione**
	+ Prima dello sviluppo vero e proprio, viene creato un piccolo prototipo usa-e-getta, così da dare agli utenti un idea del risultato finale
+ Waterfall con **feedback**
	+ Alla fine di ogni fase, si raccoglie del feedback sull'andamento del progetto, e se necessario si ritorna alla fase precedente
+ **V-Model**
	+ Viene data maggior enfasi al testing, e in caso di fallimento su una fase, si riparte dalla fase ad essa relativa
![[V-model.png]]
---
#### Modelli Evolutivi
+ L'idea alla base di questi modelli è di poter reagire ai cambiamenti in requisiti con facilità
+ Essi si basano sul concetto di effettuare **multiple release**, e raccogliere il feedback su ognuna di esse per migliorare la successiva
+ Ci sono tre sottocategorie di questo modello
##### Modello a Prototyping
+ L'idea centrale si basa sulla realizzazione di un prototipo usa-e-getta, dal design veloce, utilizzato per validare le specifiche implementate
+ Esso è solitamente realizzato in un linguaggio ad altissimo livello, così da velocizzare la sua creazione, e possiede prestazioni o feature inferiori rispetto al prodotto finito![[Prototyping.png]]
+ **Vantaggi**
	+ Permette di raffinare requisiti definiti in termini di obiettivi generali e troppo vaghi 
	+ Rilevazione precoce di errori di interpretazione
+ **Svantaggi**
	+ Il prototipo è meccanismo per identificare i requisiti, spesso da “buttare” 
		+ Problema economico e psicologico 
		+ Il rischio è di non farlo e così scelte non ideali diventano parte integrante del sistema
##### Modello Incrementale
+ Vengono sviluppate numerose release, ognuna delle quali è focalizzata sull'implementazione di una delle feature richieste dal cliente
+ Una volta realizzata, essa viene mandata al cliente, il quale la valuta e in caso positivo, si comincia a creare la release seguente, implementando un'altra feature in più
+ In questo genere di modelli è fondamentale la **pianificazione**
	+ Quali feature per prime?
##### Modello Iterativo
+ Si organizza in modo simile al primo, con la differenza che in ogni release sono presenti tutte le feature necessarie, semplicemente in qualità inferiore alla release finale
+ Nel corso dello sviluppo, le varie funzionalità verranno migliorate, sulla base del feedback degli utenti
+ **Vantaggi**
	+ I requisiti vengono raffinati ad altissimo livello
	+ Si ha una risposta più veloce al mercato
---
#### Modello a Spirale
+ Sviluppato nel 1988 da Barry Bohem
+ Si tratta di un **meta-modello**, in cui tutte le scelte vengono effettuate sulla base delle **valutazioni dei rischi** effettuate
+ Il modello ha quattro fasi:
	1. **Planning**
		+ Vengono identificati gli obbiettivi da raggiungere
		+ Vengono determinate le possibili alternative da seguire
		+ Vengono identificati i vincoli necessari ad alcune di queste alternative
	2. **Risk Analysis**
		+ Vengono identificati e valutati i rischi presenti
		+ In caso negativo, viene cancellato il progetto
	 3. **Engineering**
		 + Viene sviluppato il programma vero e proprio, seguendo un modello adeguato
	4. **Customer Evaluation**
		+ Vengono rivisti i passi precedenti assieme al cliente
---
+ **Vantaggi**
	+ Adatto a progetti molto complessi o critici	
+ **Svantaggi**
	+ la valutazione del rischio è un processo altamente complesso, e ciò non ci assicura protezione dall'**errore umano**
---
#### Unified Process (UP)
+ Introdotto nel 1996, dall'unificazione delle proposte di Booch, Rumbaugh e Jacobson
+ È pensato per l'OOP, ed è il primo ad utilizzazre la notazione UML
+ È molto **ispirato** dal modello a **spirale**, con l'aggiunta degli **UseCase**, linee guida da usare nelle scelte e specifici **tool** utilizzati per facilitare ed automatizzare alcune fasi
---
+ Il modello prevede più iterazioni, ognuna composta da 4 fasi
	1. **Inception**
		+ Studio di fattibilità, Requisiti essenziali del sistema, Risk analysis 
	2. **Elaboration**
		+ Sviluppa: 
			- La comprensione del dominio e del problema 
			- Gli UseCase della release da rilasciare 
			- L’architettura del sistema 
	3. **Construction**
		+ Design, codifica e testing del sistema
	4. **Transition**
		+ Messa in esercizio della release nel suo ambiente (deploy), training e testing da parte di utenti fidati
+ Ogni fase è a sua volta composta da diverse attività
	+ Requisiti, Analisi, Design, Codifica e Testing
+ Alla fine di ogni **fase**, viene rilasciata una **milestone**, simile al deliverable
+ Alla fine di ogni **iterazione**, viene rilasciata una **release**
+ Infine, il prodotto dovrà passare l'Acceptance Testing, il controllo effettuato dal cliente finale
---
#### Component Based
+ L'idea dello sviluppo con componenti è di basarsi sull'utilizzo di componenti di terze parti per l'implementazione di alcune funzionalità
+ È un modello che va nella direzione del **riutilizzo del software** 
	+ Spesso esiste uno ‘**Store**’ o ‘**Marketplace**’ dei componenti
---
+ **Vantaggi**
	+ Riduce la quantità di software da scrivere 
	+ Riduce i costi totali di sviluppo e i rischi 
	+ Consegne più veloci
+ **Svantaggi**
	+ Sono necessari dei compromessi 
		+ Requisiti iniziali potrebbero differire da quelli che si possono soddisfare con le componenti trovate/esistenti 
			+ Soluzione: si modificano i requisiti … 
			+ Bisogna però convincere il cliente!!!! 
	+ Integrazione non sempre facile 
	+ Spesso i componenti usati sono fatti evolvere dalla ditta produttrice senza controllo di chi li usa
----
#### Modelli Trasformazionali
+ Deriva dai metodi **formali**, e vede lo sviluppo del codice come l'implementazione di un modello matematico iniziale
+ Attraverso vari cicli, si passa dalle specifiche formali a livelli più in basso, fino ad arrivare al codice vero e proprio
+ Questa idea è stata riscoperta recentemente, e trasformata nei **MMD#**
---
#### Metodi Agili
+ Nei primi anni '90 nascono i modelli agili, i quali si basano su una visione differente dello sviluppo del codice
	+ Esso non è un prodotto industriale, ma un'opera d'arte. Perciò, l'enfasi va messa più sugli artisti, gli sviluppatori, che sui piani
+ I concetti principali, esposti nel manifesto del 2001 (The Agile Manifesto), sono i seguenti:
	+ Sono più importanti le **iterazioni fra gli individui** che il processo da seguire
	+ Si deve preferire un **software funzionante** ad una documentazione ferrea
	+ È meglio **collaborare con il cliente**, rispetto ad un contratto iniziale
	+ Meglio **adattarsi ai cambiamenti** che seguire il piano iniziale
---
+ I metodi agili possiedono effettivamente numerosi vantaggi rispetto ai modelli plan-driven, ma sono eccessivamente dipendenti dai programmatori coinvolti
+ Essi sono quindi preferibili in progetti semplici, con programmatori esperti, requisiti mutevoli e consegne rapide
---
#### DevOps
+ Questo è il metodo che viene usato dalla maggior parte delle aziende moderne
+ Prevede la collaborazione fra gli sviluppatori e i **sistemisti**
+ *Maggiori dettagli nelle slide*