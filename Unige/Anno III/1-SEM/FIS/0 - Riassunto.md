+ In questo file, cercheremo di riassumere i concetti principali del corso di **Fondamenti di Ingegneria del Software**
---
# 1 - Introduzione e Modelli di Sviluppo
### Intro
+ Alla base sta il concetto che, come in altre industrie, la qualità del prodotto finale dipenda dalla qualità del processo produttivo
+ Vengono quindi definiti dei **processi**, serie di **fasi** da seguire nella produzione del software
+ Come in una catena di montaggio, ogni fase produce un **deliverable**, il quale verrà rielaborato nella fase successiva

+ Esistono tre macro modelli:
	+ **Agili**: Più **libertà** data ai programmatori, i quali devono necessariamente essere molto abili
	+ **Plan-driven**: Data maggiore importanza al progetto ed al **design** iniziale
	+ **Formali**: **Teoria** al centro, basata su dimostrazioni matematiche
### Modelli di Sviluppo
Un **modello di sviluppo** è una modellazione astratta del processo di sviluppo del software
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
+ Questo metodo viene chiamato Code N' Fix, e **non** è un **metodo di processo**
#### Waterfall
+ Questo è uno dei **metodi** di sviluppo **più famosi** ed **utilizzati**
+ Fu cominciato da utilizzare negli anni 50 a livello militare, fu definito a livello scientifico negli anni 70, e si è diffuso negli anni 70-80
+ Strutturato in 5 fasi:
	0. **Studio di Fattibilità**
		+ Fase **facoltativa**
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
+ Questa idea è stata riscoperta recentemente, e trasformata nei **MMD**
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
# 2 - Ingegneria dei Requisiti
+ Un requisito software è **un qualcosa che il sistema deve fare**
	+ Una funzionalità, un vincolo, etc
+ La maggior parte dei progetti che falliscono lo devono al fatto di non aver compreso pienamente i requisiti  
+ Inoltre, il costo relativo della rimozione dei difetti di un software è al suo minimo durante la fase di design. Quindi questi errori **vanno riconosciuti il prima possibile**
---
+ Esistono più modi di descrivere i requisiti:
	+ Linguaggi **Formali**
		+ Linguaggio Z
	+ Notazioni **Visuali**
		+ UML
	+ Testo **Strutturato**
		+ Form o template
	+ Linguaggio **naturale**
	+ **UseCases**
	+ **User Stories**
		+ Usati nei metodi agili
---
+ I requisiti si differenziano in:
	+ Requisiti **Utente**:
		+ Scritti in linguaggio naturale e pensati per il **cliente**
			+ Spesso usati nella stesura del contratto
		+ Spesso imprecisi
		+ Descrivono i **bisogni** del cliente
	+ Requisiti di **Sistema**:
		+ Scritti con linguaggi specifici e pensati per lo **sviluppatore**
		+ Sono dettagliati e precisi
		+ Descrivono **cosa deve fare** il sistema
+ Non sempre vengono usati entrambi i gruppi, ma nel caso di sì, essi devono essere tenuti allineati fra loro
---
+ Si dividono anche in:
	+ Requisiti **Funzionali**
		+ Rappresentano i **servizi** e le funzionalità richieste dal cliente
	+ Requisiti **Non-Funzionali**
		+ Sono **vincoli** sul sistema, legati alle modalità gestionali
		+ Ne esistono varie sottocategorie (Requisiti etici, etc)
---
+ Il **Requirements Engineering** è il termine che descrive l'insieme delle fasi di raccolta e documentazione dei requisiti del progetto
+ Il suo scopo principale è la creazione del **Requirement Document** (RD), un documento che descrive le funzionalità ed i servizi offerti dal sistema, e la sua **manutenzione**
	+ Esistono numerosi **tool** che assistono la produzione del documento
+ È un processo iterativo, formato da due fasi principali:
	+ Requirements **Development**
		+ La fase di **produzione** dell'RD, divisa in
			+ Requirements **Elicitation**
				+ Vengono raccolti i requisiti, spesso tramite interviste con gli stakeholders, ed analisi degli elementi del dominio dell'applicazione
			+ Requirements **Analysis**
				+ Viene analizzati i requisiti raccolti e si valuta la loro chiarezza, fattibilità e completezza
				+ Viene anche stabilità una **gerarchia di priorità**, così da capire quali siano più necessari
					+ Si usano scale numeriche, o altre come la MosCOW
			+ Requirements **Specification**
				+ Vengono specificati i requisiti rilevati nell'RD, dividendo fra la **Definizione** (Requisiti Utente) e la **Specifica** (Requisiti di Sistema)
			+ Requirements **Validation**
				+ Terze parti valutano la qualità e chiarezza del documento
				+ Altri metodi consistono in piccole fasi di testing, o lo sviluppo di un prototipo
	+ Requirements **Management**
		+ Viene tenuto aggiornato il documento, valutando possibili proposte di modifica
			+ Sono fattibili? Che impatto hanno?
![[R-Eng.png]]
---
+ Le proprietà che dovrebbero essere possedute da ogni requisito sono:
	+ **Correttezza**
	+ **Consistenza**
	+ **Completezza**
		+ Praticamente impossibile...
	+ **Realismo**
	+ **Inequivocabilità**
	+ **Verificabilità**
		+ Sono testabili?
	+  **Tracciabilità**
		+ A che richiesta del cliente corrispondono?
		+ Spesso si usa una **matrice di tracciabilità** se mantenere il rapporto
---
+ Spesso gli RD sono organizzati secondo vari standard, uno dei più famosi è l'**IEEE Std 830-1998** (*dettagli nelle slide*)
---
+ Spesso questi lavori sono effettuati da uno specialista, l'**Analista Software**
---
+ *Nelle slide sono presenti consigli su come effettuare le interviste, ed i tipici difetti di un RD*
# 3 - Design
### General
+ È il processo che trasforma un problema in una soluzione
	+ Il problema sono i requisiti software
	+ La soluzione è una struttura per l'implementazione software
+ Anche il design si divide in più parti
	+ **High Level Design**
		+ I componenti del sistema vengono definiti ad alto livello, come black-box, legati ai requisiti
	+ **Low Level Design**
		+ Ognuno dei sotto-componenti viene descritto in modo più dettagliato
+ Lo stesso design può essere sviluppato in modo:
	+ **Platform Independent**
		+ Astratto ed universale, facilmente riutilizzabile
	+ **Platform Dependent**
		+ Legato ad una specifica implementazione, e più facile da implementare
---
+ Questa fase non è propriamente creativa, in quanto si **sfruttano** spesso **concetti già esistenti**
+ Questo si fa in quattro modi diversi:
	+ **Clonazione**
		+ Si riutilizza interamente design/codice, con piccoli aggiustamenti
	+ **Design Pattern**
		+ Una buona soluzione ad un problema ricorrente
	+ **Stili Architetturali**
		+ Una architettura generica che suggerisce come decomporre il Sistema
	+ **Software Frameworks**
		+ Un insieme di classi e interfacce cooperanti che realizzano un design per uno specifico dominio applicativo o tipologia di app
---
+ Il **design architetturale** (High Level Design) è la fase iniziale del processo, in cui si identifica:
	+ Le **(macro) componenti** di un sistema
	+ Come avviene il **controllo** e la **comunicazione** tra componenti
+ Produce una descrizione dell'**architettura software**
+ Fra componenti si può dividere fra:
	+ **Sotto-sistemi**: Sistemi a se stanti, utilizzati dal nostro sistema
	+ **Moduli**: unità dipendenti che offrono servizi ad altre unità
+ Spesso queste architetture vengono descritte tramite **schemi a blocchi**, in cui i blocchi corrispondono ai componenti, ed i collegamenti alle loro relazioni
+ La scelta di un'architettura è fondamentale, in quanto impatta su:
	+ **Performance**
	+ **Security**
	+ **Safety**
	+ **Availability**
	+ **Maintainability**
+ Ma ovviamente, **non si può avere tutto**
	+ Scegliere componenti large-grain riduce le comunicazioni, migliorando le prestazioni, ma peggiorando la manutenibilità
	+ Componenti ridondanti migliorano l'availability, ma peggiorano Safety
	+ Usare un’architettura a livelli migliora Security ma aumenta comunicazioni e così degrada Performance…	
+ Comunque la **scelta** di un'**architettura aiuta**, dato che:
	+ Guida lo sviluppo ed aiuta nella comprensione del sistema
	+ Documenta il sistema
	+ Aiuta a ragionare sull'evoluzione del sistema
	+ Supporta decisioni manageriali
	+ Facilita l’analisi di alcune proprietà
	+ Permette il riuso (Large-scale)
---
+ L'architettura può conformarsi ad uno **stile architetturale**, assimilabile allo stile di una casa
+ Ognuno di essi è definito da
	+ Un insieme di tipologie di **componenti**
	+ Un insieme di tipologie di **connettori**
+ Ci sono numerosi stili
	+ Layered
	+ Repository
	+ Client/Server (Two Tier o Three Tier)
	+ Pipe and Filter
	+ Microservice
+ Sono suddivisibili in 
	+ **Strutturali**: Danno solo un idea di come **organizzare** il sistema
	+ **Di Controllo**: Danno anche idee su come **controllare** il sistema
---
#### Layered
+ Organizza il sistema in un **insieme di livelli** ognuno dei quali fornisce un **insieme di servizi**
+ Un livello "si appoggia" solo sul livello inferiore 
	+ Cioè usa solo i servizi del livello inferiore
+ Es. Android, GNU/Linux OS
---
#### Repository
+ I dati condivisi fra componenti sono tutti mantenuti in un **unico database centrale** (blackboard)
+ I componenti **comunicano** solo **attraverso** questo **database**
	+ Utile per applicazioni in cui i dati sono prodotti da un sottosistema e utilizzati da un altro
+ Es. Case Tool come Visual Paradigm
---
#### Client/Server
+ Modello di **sistema distribuito** che mostra come i dati e la computazione possono essere distribuiti su: 
	+ Insieme di **server** che **forniscono** servizi specifici 
		+ Es. servizi di stampa, servizi di gestione file
	+ Insieme di **client** che **utilizzano** tali servizi 
+ Esiste una **rete** che permette ai client di accedere ai server
+ Es, Web app
---
+ Solitamente un programma è composto da **tre** componenti
	+ **Presentation** Logic: L'interfaccia utente
	+ **Business** Logic: La gestione dei processi e logica
	+ **Data** Logic: La gestione del database
+ In una struttura del genere, come vanno divisi?
+ Ci sono due approcci:
	+ **Thin** Client: PL su client, BL e DL su server
	+ **Fat** Client: PL e BL su client, DL su server
+ Oppure esistono strutture dette **three tier**, che rispetto alle precedenti two tier possiedono un terzo server a cui dare BL
---
#### Pipe and Filter
+ I **filtri** effettuano **trasformazioni** che elaborano i loro input per produrre output 
+ Le **pipe** sono **connettori** che trasmettono i dati tra filtro e filtro
	+ Simile a ciò che si ottiene con `|` in un terminale
---
#### Microservice
+ È uno stile moderno, nato in contrapposizione alle architetture monolite e multi-tier
	+ Evoluzione delle architetture SOA (service oriented programming)
+ L'idea di base è di organizzare l'applicazione come un **insieme di servizi indipendenti**, che comunicano fra loro
	+ Questo permette di **evolvere** l'applicazione in modo molto **veloce**
+ Ogni microservizio:
	+ Realizza una funzionalità
	+ È autonomo
	+ Possiede un proprio DB
	+ Comunica e si coordina con gli altri
+ L'utente comunica con il sistema tramite un **gateway**, un API che fa da interfaccia
	+ *REST è una struttura famosa che vedremo a SAW*
+ Questo stile ha però dei **difetti**:
	+ Stabilire la dimensione dei microservizi
	+ Sviluppare la comunicazione fra essi
	+ Esposizione ai disservizi della rete
	+ Difficoltà di testing
	+ Maggior consumo di risorse
---
+ Tutti questi si trattano di **stili** architetturali **puri**, ma **nella realtà** si utilizzano stili **eterogenei**, che mischiano questi precedenti
+ Ciò si può ottenere in due modi:
	+ Modo **Gerarchico**: Alcune componenti interne sono organizzate tramite un altro stile
	+ **Mix di Architetture**: Si mischiano selvaggiamente gli stili
		+ Un esempio è un **compilatore**
---
+ 
### Design by Contract
+ Oggi vedremo il **Design by Contract**:
	+ È un metodo di design che punta a migliorare la qualità del software prodotto
	+ Prescrive che il progettista debba definire specifiche precise delle interfacce dei classi/componenti software, basandosi sulla metafora di un **contratto legale**
	+ Un “contratto”, viene creato per ogni componente del sistema prima che sia codificato
		+ L’idea centrale è che una componente software ha degli **obblighi** nei confronti delle altre componenti
+ I contratti sono composti da tre condizioni:
	+ **Pre**-condizione
		+ Rappresentano i requisiti sugli altri componenti prima dell'esecuzione del metodo
	+ **Post**-condizione
		+ Rappresenta i requisiti sugli altri componenti dopo l'esecuzione del metodo
	+ **Invariante** di Classe
		+ Una condizione che deve essere sempre verificata, a meno che l'interfaccia non sia nel mezzo di una transizione
	+ *Esse possono essere scritte in Object Constraint Language (OCL)*
+ La verifica della **prima** è responsabilità del **richiedente**, la verifica delle **ultime due** è responsabilità del **fornitore**
![[VantDesContr.png]]
---
### Design Algoritmi
+ Questa attività è solitamente responsabilità degli sviluppatori, e viene eseguita tramite i seguenti passaggi:
	1. Si analizza la descrizione di design della classe “target”
	2. Se esistono una o più operazioni che necessitano di un algoritmo
		1. Se è possibile selezionare un algoritmo conosciuto, si seleziona
		2. Se invece occorre definire un algoritmo si sceglie una **notazione**
		3. Utilizzando la nozione di “**stepwise refinement**” si sviluppa l’algoritmo nella notazione scelta
			+ Lo stepwise refinement è il processo attraverso il quale il codice viene sviluppato attraverso vari passi di raffinazione, in cui si riduce sempre di più l'astrazione della notazione
		4. *(facoltativo) Si usano i metodi formali per provare la correttezza dell’algoritmo proposto*
+ Quali sono queste notazioni? Ne esistono multiple, divisibili in 
	+ Visuali
	+ Testuali
+ Un esempio è lo **pseudo-codice** (PDL), in cui si mischia linguaggio naturale (narrativa) con linguaggio di programmazione
### Principi di Buon Design
+ Vediamo i vari principi di **buon design**. Sono numerosi per cui ne vederemo solo una parte
	+ In essi useremo il concetto di **modulo**, un entità software capace di fornire servizi, e contenere altri moduli a sua volta
1. **Astrazione**
	+ L'astrazione permette di concentrarsi su un problema senza doversi preoccupare dei dettagli più minuti, così da ragionare meglio
	+ Esistono tre tipi di astrazione
		+ Funzionale
			+ Definizione di una funzionalità indipendentemente dall'algoritmo che la implementa
		+ di Dati
			+ Definizione di un tipo di dato in base alle operazioni che su di esso possono essere fatte, senza definirne una struttura concreta
		+ di Controllo
			+ Definizione di un meccanismo di controllo senza indicarne i dettagli interni
2. **Decomposizione**
	+ Conviene scomporre un problema complesso in più sotto-problemi più semplici, per risolverlo meglio
	+ Bisogna però stare attenti a non esagerare, in quanto c'è comunque un costo nello sforzo necessario per riunire i sotto-problemi
3. **Modularità**
	+ Conseguenza del principio precedente, ci dice che dovremmo separare il sistema in moduli, seguendo il principio di **separation of concerns**
		+ I moduli ottenuti dovrebbero essere accomunati da obbiettivi e funzionalità offerte (massimizzare la coesione, minimizzare l’accoppiamento)
	+ Per **coesione**, si intende che un modulo dovrebbe svolgere un solo compito astratto
	+ Esistono diversi tipi di coesione, ma noi consideriamo quella funzionale
	+ È importante gestire anche l'**accoppiamento**, ovvero come i moduli interagiscono fra loro. In generale, si deve evitare che un modulo possa modificare parti di altri, e ridurre al massimo i collegamenti fra essi
4. **Information Hiding**
	+ Proprio per evitare l'accoppiamento cattivo, l'information hiding fa in modo di nascondere i dati di un modulo agli altri, evitando l'accesso diretto
5. **Alto Fan-in, Basso Fan-out**
	+ Costruendo il grafo delle dipendenze din un programma, si deve fare in modo che ci siano poche dipendenze (fan-out) e tanti utilizzi (fan-in) di ogni modulo
6. **Generalità**
	+ Ogni modulo deve essere strutturato in modo da essere generale e riutilizzabile
7. **In Generale:**
	+ Il design deve essere il più semplice possibile (**KISS**)
# 4 - UML
## 4.0 - Intro
+ UML (**Unified Modeling Language**) è uno standard OMG, il quale contiene una **famiglia di notazioni grafiche** utilizzabili durante la produzione di un software
+ Nato negli anni '90, creato dai "tre amigos"
+ *È importante studiarlo, in quanto standard dell'industria, ma non lo vederemo approfonditamente, in quanto complesso*
---
+ Esso **NON** è:
	+ Un metodo di sviluppo
	+ Un linguaggio di programmazione
	+ Legato a UP
+ Si può usare in tre modi:
	+ **Sketch**
		+ Disegno semplice espressivo
		+ Noi useremo principalmente questo
	+ **Blueprint**
		+ Descrizione dettagliata e completa
	+ **Linguaggio di programmazione**
		+ Modello astratto ma eseguibile
+ Nell'utilizzo di UML, è sempre importante specificare la **prospettiva** utilizzata
	+ Prospettiva **Software**
		+ Punto di vista dello sviluppatore, lo schema rappresenta il sistema vero proprio, componenti e tutto
	+ Prospettiva **Concettuale**
		+ Punto di vista del cliente, lo schema rappresenta le funzioni astratte del sistema
		+ Rappresenta i **Modelli di Dominio** (*dettagli in slide*)
---
+ UML fornisce:
	+ Una famiglia di **notazioni** (sintassi)
	+ Un **meta-modello** (semantica)
		+ *Non lo vedremo nel dettaglio...*
+ Un sistema viene descritto attraverso:
	+ Più **viste**, aspetti del sistema visti attraverso uno dei ruoli coinvolti
		+ *Esse possono essere incomplete, o sovrapposte fra loro*
	+ Più **diagrammi**, ognuno dei quali descrive una di queste viste
+ Un **modello** è un insieme di diagrammi che descrive uno stesso aspetto del sistema
---
+ UML comprende **14** tipi di diagrammi, noi ne vedremo circa **6**
+ Essi sono suddivisibili in
	+ **Strutturali**
	+ **Comportamentali**
+ UML viene usato in quasi tutte le fasi del processo:
	1. **Specifica Requisiti**
		+ Gli **UseCase** Diagram descrivono i requisiti
		+ Il **Class** Diagram descrive il glossario del dominio
		+ Gli **Activity** Diagram possono descrivere gli UseCase singoli
	 2. **High Level Design**
		 + L'architettura può essere descritta da un **Component** Diagram
		 + Un **Deployment** Diagram può descrivere la relazione fra componenti logici e non logici
	3. **Low Level Design**
		+ Il **Class** Diagram può rappresentare le classi software e le loro relazioni
		+ L'**Object** Diagram descrive gli oggetti del Class Diagram e aiuta a comprenderli
		+ I **Sequence** e **Communication** Diagrams mostrano il trasporto dei messaggi fra classi
		+ Il **Package** Diagram riassume il Class Diagram
		+ L'**Activity** Diagram definisce le operazioni di una classe
		+ Lo **State Machine** descrive oggetti a stati finiti complessi
---
+ UML non è perfetto, ed è possibile **migliorarlo** in due modi:
	+ Estendendo UML con **profili** predefiniti
	+ Usando diagrammi non-UML (Es, Storyboard)
		+ *È ovvio però che perdiamo l'universalità di UML...*
+ Un profilo viene definito da
	+ **Stereotipi**, l'insieme degli elementi aggiuntivi ottenuti modificando quelli già esistenti
	+ **Vincoli aggiuntivi**, oltre a quelli già presenti
	+ **Informazioni semantiche** aggiuntive
+ In generale, bisogna pensare che per quanto esista lo standard, tutti utilizzano versioni lievemente diverse di UML. Perciò, è fondamentale riuscire ad adattarsi
+ *Consigli nelle slide su come usare UML*
## 4.1 - UseCases e UseCase Diagram
+ Gli **UseCases**, proposti per la prima volta da Ivar Jacobson nel 1992, sono una **tecnica** utilizzata per **esprimere requisiti funzionali** di un sistema (anche non informatico!)
+ È una tecnica non visuale, che usa **solo testo**, ma esistono alcune sue rappresentazioni grafiche
+ In essi, il sistema viene visto come una black-box, e vengono descritte le iterazioni fra le entità partecipanti ed esso
	+ Ovvio l'utilizzo del **punto di vista dell'utente**
---
+ La definizione di uno UseCase si basa su quattro categorie di oggetti:
	+ **Attori** : Ruoli assunti dalle entità che partecipano
	+ **UseCase** : Ciò che gli attori possono fare col sistema
	+ **Relazioni** : Rapporti fra Attori e UseCase
	+ **Confini del Sistema** : Indicazioni dei limiti del sistema
---
+ La prima cosa da fare è definire i **limiti** del sistema
	+ In questo modo sapremo cosa dovremo sviluppare, e cosa sarà eseguito sulla base di codice già esistente o servizi di terze parti
+ Gli **attori** rappresentano **chi o cosa interagisce con il sistema**, un **ruolo** ricoperto da un'entità
+ Sono divisibili in:
	+ **Primari**: Chi usa il sistema (utenti)
	+ **Secondari**: Chi viene usato dal sistema (servizi esterni)
+ Si possono definire **gerarchie** fra essi
+ Uno **scenario** è una sequenza ordinata di iterazioni fra un sistema e gli attori
	+ Rappresenta quindi un **istanza** del sistema, una particolare esecuzione di uno UseCase
+ Uno **UseCase** viene quindi ridefinito come un **insieme di scenari** che hanno in comune lo **scopo finale dell'utente**
---
+ Gli UseCase sono solitamente descritti tramite **template**, in linguaggio naturale
	+ Devono essere semplici, e comprensibili per il cliente
+ In essi, descriveremo uno Scenario **Principale** (Il normale comportamento del sistema) ed i vari Scenari **Secondari** (i possibili scenari alternativi)
+ Il template che useremo contiene i seguenti campi:
	+ **Nome dello use case**: 
		+ È il goal dello use case, una “breve frase verbale attiva”
		+ Scritto in UpperCamelCase
	+ **Identificatore**: 
		+ Di solito numerico progressivo 
	+ **Breve descrizione**: 
		+ Un paragrafo che fissa l’obbiettivo dello use case 
	+ **Attori primari**: 
		+ L’attore/gli attori primari dello use case 
	+ **Attori secondari**: 
		+ Gli attori che “servono” per svolgere lo use case 
	+ **Precondizioni**: 
		+ Vincoli sullo stato corrente del sistema 
	+ **Scenario principale**: 
		+ I passi che costituiscono lo use case 
	+ **Post-condizioni**: 
		+ Condizioni che devono essere vere quando lo use case termina con successo l’esecuzione 
	+ **Scenari alternativi**: 
		+ Un elenco di alternative allo scenario principale
---
+ Ogni scenario sarà composto da un insieme di **passi**, concisi, numerati, ed ordinati temporalmente
	+ Dalla forma `<numero> Il <qualcosa/qualcuno> <qualche azione><qualche azione>`
+ Possono verificarsi **deviazioni**
	+ **Semplici**: usiamo “se” ed "altrimenti" nella sequenza principale
	+ **Complesse**: scriviamo sequenze degli eventi alternative
		+ Essi vengono documentati a parte, per semplicità
		+ Il loro id è relativo al caso "padre"
		+ In essi va specificato quando possono iniziare, o se possono iniziare in qualunque momento
+ Possiamo anche indicare **loop** (while e for) tramite "per" e "fintantoché"
---
+ Esistono multipli tipi di relazioni fra UseCases:
	+ **Inclusione**
		+ Usata per decomporre uno UseCase complesso in più "sotto-funzioni", altri UseCases già definiti
		+ Rappresentato con la parola `include`
	+ **Estensione**
		+ Definiscono comportamenti opzionali, legando uno UseCase completo ad uno incompleto, creato ad hoc
		+ Rappresentato con la parola `extend` 
	+ **Generalizzazione**
		+ Vengono definite gerarchie fra UseCases. I figli ereditano i passi dei genitori, e possono modificarli
		+ Stare attenti a come vengono indicata, spesso non è molto comprensibile
---
+ Spesso insieme agli UseCases si aggiungono degli **screen mock-up**, per mostrare l'aspetto dell'ipotetica GUI
+ Esistono tool che aiutano a produrli
+ *Consigli sulllo sviluppo degli UseCases nelle slide*
## 4.2 - Class Diagram
+ Un **Class** Diagram definisce:
	+ Le classi
	+ Le loro feature
		+ Attributi
		+ Operazioni (metodi della classe)
	+ Le relazioni fra più classi
		+ Associazioni
		+ Aggregazioni/Composizioni
		+ Specializzazioni/Generalizzazioni
		+ Dipendenze
+ Ovvero la struttura **statica** di ciò che vogliamo modellare
+ Esso viene usato sia nella fase di raccolta **requisiti** che nella fase di **design**
+ Il **significato** stesso del diagramma dipende dalla **prospettiva** adottata:
	+ **Concettuale**
		+ Descrive gli **elementi** del pezzo di mondo che stiamo modellando
			+ Classe -> concetto del dominio
			+ Operazione -> azione o responsabilità
	+ **Software**
		+ Descrive i **dettagli** del **design** del software che stiamo sviluppando
			+ Classe -> Classe OO
			+ Operazione -> Metodo
---
+ In UML, il concetto di **classe** è lo stesso dei linguaggi di programmazione ad oggetti
+ Un **oggetto** invece è un istanza di una classe
+ Una **classe** viene rappresentata da un rettangolo con il nome della classe all'interno
	+ Se si vuole si possono anche scrivere attributi, operazioni, etc
	+ Bisogna stare attenti al fatto che non scrivere gli attributi non vuol dire che essi non ci siano. Se si vuole specificare ciò, si devono disegnare le rispettive sezioni come vuote
---
+ Gli **attributi** vengono scritti nel seguente modo:
	+ `visibilità nome: tipo [molteplicità] = default {proprietà}`
+ In esso:
	+ La **visibilità** è divisa in quattro livelli, reminescenti di Java
		+ Pubblico `+`
		+ Privato `-`
		+ Protetto `#`
		+ Package `~`
	+ Il **tipo** può essere un tipo primitivo, o un'altra classe
	+ Le **molteplicità** indicano il quantitativo degli attributo (ER style)
	+ **Default** è il valore di default dell'attributo
	+ Le **proprietà aggiuntive** sono proprietà specifiche (Es, readonly)
---
+ Le **operazioni** vengono scritte come:
	+ `visibilità nome (lista parametri) : tipo-ritornato {proprietà}`
+ In cui:
	+ **Lista parametri** contiene nome e tipo dei parametri, secondo la forma:
		+ `direzione nome: tipo = default`
			+ **direzione**: input (in), output (out) o entrambi (inout). Il valore di default è in
	+ **Tipo-ritornato** è il tipo del valore di ritorno
+ Esse sono classificabili in 
	+ Query: ottengono un valore, senza effettuare modifiche
	+ Modificatori: Modificano un valore
+ *Solitamente le operazioni set e get non si indicano, sono scontate*
---
+ Il **Datatype** è un concetto differente da quello di oggetto.
+ Sono elementi senza identità, identificati dal loro valore
+ Sono rappresentabili come classi con lo stereotipo `<<datatype>>`
---
+ Un **associazione** rappresenta una relazione fra classi
+ Viene rappresentata come una freccia che unisce le due
+ Su di essa si scrive il nome dell'associazione e la **direzione** (< o >)
+ Questo non va confuso con il **verso di navigazione**, ovvero la punta della freccia, che indica in che direzione è possibile reperire le informazioni
+ Le associazioni possiedono anche una **molteplicità**. 
	+ Bisogna stare attenti, in quanto l'ordine è invertito rispetto ai diagrammi ER!
+ *Solitamente si usano le associazioni per rappresentare campi tipati da classi, gli attributi per tipi primitivi e datatype*
+ Esistono alcune varianti di operazioni ed attributi:
	+ Quelli **statici** corrispondono ai metodi ed attributi static di Java
	+ Le associazioni **riflessive** sono con un oggetto della classe stessa
	+ Le associazioni **bidirezionali** sono navigabili in entrambe le direzioni. Sono complesse da implementare
	+ Le operazioni **astratte** vengono definite in sottoclassi. Sono scritte in corsivo
## 4.3 - Object Diagram
+ L'**Object** Diagram viene usato per chiarire class diagram complessi, dando **esempi** dell'utilizzo delle classi
+ In essi gli oggetti sono identificati dal nome sottolineato, e rappresentano **istanze** delle classi
---
+ Le **note** sono commenti, usati per specificare il comportamento di classi e feature
---
+ L'**aggregazione** è un tipo di associazione che rappresenta l'appartenenza ad un gruppo
	+ È un idea principalmente concettuale, viene poi tradotta in una semplice associazione a livello software
+ La **composizione** rappresenta l'idea di un oggetto composto da altri oggetti
	+ In esso le parti non esistono da sole, ogni componente appartiene ad un solo oggetto per volta
+ La **generalizzazione** è l'idea che un oggetto sia un figlio di un altro. L'**ereditarietà** è il modo attraverso il quale questo concetto viene applicato a livello di codice
+ La **dipendenza** è un tipo di associazione che indica che la modifica di uno può influire sull'altro.
	+ Viene solitamente indicato da una freccia tratteggiata
	+ Bisogna mettere solo quelle più importanti, per evitare di complicare troppo lo schema
---
+ In UML, un **metodo** è l'implementazione di un operazione, il quale specifica il comportamento di essa
	+ Possono esistere più metodi per una stessa operazione
--- 
+ In UML, l'**interfaccia** indica due cose
	+ È l’insieme delle operazioni visibili all'esterno degli oggetti che sono istanze di quella classe  
	+ È un entità “simile” ad una classe, ma è priva di implementazione (ha solo operazioni pubbliche)
+ Esse possono essere mostrate in UML come classi con lo stereotipo `<<interface>>`. 
+ Ad esse si possono collegare le classi che le implementano con delle **frecce tratteggiate**, oppure con la notazione a **lollipop**
+ In generale, esse sono utili per separare l'implementazione di un interfaccia dall'interfaccia vera e propria, diminuendo l'accoppiamento e allargando il supporto all'ereditarietà multipla
---
+ I **vincoli** possono essere definiti come regole che riducono il numero di combinazioni possibili negli object diagram
+ Questi sono solitamente definiti dalla struttura del diagramma stesso, ma non tutto può essere espresso da ciò
+ Per tal motivo si possono inserire delle **regole di vincolo**, all'interno di **commenti**, scritti o in linguaggio naturale o in OCL (Object Constraint Language), all'interno di parentesi graffe
	+ L'OCL è basato sulla **logica del prim'ordine**, ed utilizza i concetti di invariante e pre-post condizioni, reminescenti del design-by-contract
## 4.4 - Sequence Diagram
+  I diagrammi di **iterazione** descrivono la collaborazione di un gruppo d'oggetti, ovvero come essi **comunicano** fra loro
+ I messaggi inviati possono essere:
	+ Sincroni: il mittente si pone in attesa del risultato
	+ Asincroni: il mittente continua l'esecuzione
+ Essi sono composti da 
	+ Scatole, che rappresentano i partecipanti al dialogo
	+ Linee verticali che rappresentano la timeline della conversazione. La loro "pienezza" indica se il partecipante è in controllo
	+ Frecce che indicano i **messaggi** scambiati
+ I messaggi possono essere di vario tipo
	+ Un messaggio trovato ha il partecipante che l'ha generato omesso 
	+ Un messaggio sincrono è mostrato con una freccia piena
	+ Un messaggio self è inviato a se stesso
		+ La freccia ritorna a se stesso
+ I messaggi hanno la seguente sintassi:
	+ `returnValue = message(parameters):returnType`
+ I vari interlocutori possono venir creati nel corso della conversazione. Nel caso accada essi vengono disegnati all'altezza del messaggio generatore. 
	+ Nel caso vengano distrutti, ci si comporta analogamente
---
+ Per descrivere cicli e simili, si mettono le sezioni in essi contenute all'interno di scatole, dette **frame**, sulle quali si indica anche il tipo di loop, e la guardia del loop, se necessaria
+ I cicli vengono chiamati **loop**
+ Gli if/else **alt**
	+ In essi le guardie indicano le condizioni. I diversi casi vengono separati da linee tratteggiate
+ I frame possono essere **annidiati**
+ È possibile creare delle "funzioni", chiuse in frame, le quali possono essere riferite nel sequence diagram principale tramite la parola **ref**
+ **par** indica che due sezioni vengono eseguite parallelamente
![[SD-operators.png]]
---
+ I **sequence diagram** sono molto utili, ma la loro **efficacia** è **limitata** alla descrizione delle **iterazioni**, non della logica di controllo, ne alla descrizione dei dettagli di un algoritmo
	+ Per questo, è preferibile usare lo pseudo-codice
+ Solitamente si usano a livello dei **requisiti** e a livello di **design**
+ Nel primo caso, essi vengono chiamati **Sequence Diagram di Sistema** (SSD), e vengono usati per descrivere gli scenari di input/output di uno UseCase
	+ Essi sono utili nelle fase di testing e nella traduzione durante la fase di design
## 4.5 - Communication Diagram
+  I diagrammi di **comunicazione** sono **simili** ai sequence diagram, in quanto come essi hanno l'obbiettivo di descrivere la comunicazione fra due o più oggetti, ma quest'ultimi si **concentrano** maggiormente sulla **comunicazione stessa**, invece che alla sequenza temporale dello scambio di messaggi
	+ *Vedere di più*
## 4.6 - State Machine Diagram
+  Diagramma di Modellazione **Dinamica**
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
## 4.7 - Activity Diagram
+ Sono diagrammi **poliedrici**, che possiamo descrivere come una standardizzazione ed **evoluzione** dei classici **flowchart**, aggiungendo il supporto all'elaborazione concorrente/parallela 
+ Descrivono come viene svolta un’attività relativa ad una qualsiasi entità, ovvero quale è il flusso di azioni che devono accadere, ed in quale ordine
+ Vengono usati in vari modi lungo quasi tutte le fasi di sviluppo
+ Si usano diversi tipi di **nodi** e **flussi** per specificare il comportamento:
![[ADNodi.png]]
+ Nei nodi azione si possono specificare i dettagli, o invocare un altra attività tramite il simbolo **rake**
---
+ Durante lo svolgersi dell'attività, si generano e trasportano diversi **token**, specificati. Un nodo azione viene eseguito solo quando sono presenti tutti i token su tutti i suoi archi in entrata.
+ I nodi finali ed iniziali sono rappresentati da pallini neri. Il primo è unico, i secondi multipli e facoltativi
---
+ In un nodo decisione, se più di una guardia è vera, viene fatta una scelta non deterministica
+ Oltre ai nodi decisione, esistono i nodi **fusione**, in cui i flussi possono riunirsi
+ I nodi Fork e Join gestiscono il parallelismo
+ I nodi **finali di flusso** terminano solo un flusso, e non tutta l'attività
+ I nodi **oggetto** sono utilizzabili per modellare l'input ed output. Questi possono possedere stati, coerenti con quelli della macchina a stati ad esso associato
+ Il flusso può essere suddiviso in **swim-lanes**, sezioni che specificano chi è l'esecutore dell'attività
+ I nodi **ricezione** gestiscono gli eventi (*da rivedere*)
+ **Input ed output** sono rappresentati com nodi oggetto sui bordi dell'attività
+ Le **regioni interrompibili** specificano sezioni in cui si può forzare l'interruzione dell'attività sulla base di un evento
## 4.8 - Component Diagram
+  In UML, una componente è un **unità modulare rimpiazzabile**, astratto
+ Essi vengono implementati da **artefatti**, entità fisiche
+ Un sottosistema è invece un sistema che possiede una classe facade che espone l'interfaccia
---
+ I **Component Diagram** rappresentano quindi il **sistema** e le **dipendenze** fra gli elementi che lo compongono
+ Sono utilizzati principalmente ad **alto livello**, per poter descrivere a livello più alto gli elementi
+ Le componenti utilizzate sono divisibili in UI, Logiche e database.
---
+ Ogni componente è mostrato come un rettangolo dotato di 
	+ Una **Parola chiave** o icona, che ne descrive la tipologia
	+ Un **Nome**, che lo identifica
+ Le **interfacce** vengono descritte tramite la struttura a **lollipop**
	+ Una versione meno usata utilizza frecce e rettangoli
+ Si possono specificare **dipendenze** fra i componenti, se si vuole descrivere la relazione fra le interfacce in modo più astratto
## 4.9 - Deployment Diagram
+ Esso mostra la **relazione** tra **hardware** e **software** in un sistema
+ Possiamo considerarlo una implementazione del component diagram
+ Utilizza **nodi**, rappresentati da scatole tridimensionali, e **connessioni**, rappresentate da linee
	+ Ogni nodo è una periferica fisica, o un ambiente software di esecuzione di codice. In generale, qualcosa in grado di eseguire codice
		+ I nodi possono essere annidati (Es, ambiente di esecuzione all'interno di un sistema hardware)
	+ Le connessioni rappresentano quindi canali di connessione fra essi
+ Gli **artefatti**, sono **entità concrete** del mondo reale, come codice, che possono essere **dislocate** sui nodi. Essi possono avere dipendenze fra loro
+ Gli artefatti possono essere messi con la relazione **manifest** con component diagrams per mostrare che essi siano manifestazioni fisiche di essi
## 4.10 - Package Diagram
+ Un **package** in UML è un costrutto che permette di prendere un numero arbitrario di element (classi, use case, modelli, altri package, etc) e raggrupparli insieme
	+ Decidere la suddivisione in package dei propri elementi è qualcosa di complesso. Un consiglio è cercare di seguire i principi di buona progettazione
+ Ogni package definisce un **namespace**, una regione in cui i nomi devono essere univoci
+ In un package diagram, ogni pacchetto è rappresentato da una **cartella**, al cui interno vengono disegnati gli elementi contenuti nel package
	+ Vengono utilizzati i due gradi di visibilità public(+) e private(-)
+ Si possono indicare **dipendenze** fra i vari elementi tramite frecce
# 5 - Design Patterns
+ Un Design Pattern è una **soluzione elegante** (con un nome) di uno **specifico problema** di design/programmazione OO che costituisce un unità di **riuso** (non l'unica)
	+ Essi aiutano ad applicare i principi di buona progettazione OO e quindi creare buoni design. 
+ Un **framework** è un insieme di classi e interfacce cooperanti che **realizzano** un **design riusabile e personalizzabile** per uno specifico dominio applicativo o tipologia di app. Anch'essi sono unità di riuso
	+ A differenza di una libreria, usata per supplire a buchi nel sistema, il framework è un sistema bucato che viene riempito dallo sviluppatore, con le classi mancanti
	+ Rispetto ad un design pattern, essi sono più concreti e più specifici ad un dominio
### GRASP Patterns
+ Essi sono un insieme di patterns usati per l'assegnazione di responsabilità nel software. 
	+ Sono fondamentali per l'OOP
#### Controller
+ **Quale** è il primo **oggetto** oltre lo strato di UI che **riceve e coordina** un operazione di sistema?
+ La **soluzione** è dare la responsabilità ad una **classe apposita** o, nel caso di un sistema grande, una classe specifica al caso d'uso del momento
### Design Pattern Classici
+ Essi sono quelli originariamente esposti in GoF, sono 23
+ Sono suddivisi in tre categorie
	+ **Creazionali**: creazione degli oggetti (in modo controllato)
	+ **Strutturali**: composizione di classi ed oggetti (strutture tipiche) 
	+ **Comportamentali**: come classi (oggetti) interagiscono tra di loro e si distribuiscono le responsabilità
+ Ne vedremo solo una piccola selezione
#### Creazionali
+ Legati alla domanda "chi crea questo oggetto?"
+ Esiste un pattern GRASP, Creator, che spesso viene usato, am esistono varie alternative
##### Factory e Abstract Factory
+ Utile per nascondere la logica di creazione
+ L'idea principale è di avere un **tipo** di oggetto, factory, il qaule si **occupa di crearne altri**. Si può avere una specializzazione dell'oggetto per ogni tipo creati
+ **Abstract** factory è una versione di questo pattern che permette di creare classi di oggetti, in modo separato dalle classi concrete che lo implementano
	+ C'è però lo **svantaggio** di **complicare** l'**aggiunta** di nuovi elementi
#### Strutturali
##### Adapter
+ Si occupa di **tradurre un interfaccia** in un altro modo
	+ Questo permette a classi incompatibili di lavorare insieme
+ Questo pattern può essere implementato tramite un **oggetto**, che utilizza la **composizione**
##### Facade
+ Ci permette di utilizzare una classe **facciata** per poter utilizzare più classi come una sola
+ Questo riduce l'accoppiamento, nasconde la complessità al cliente, e non previene l'utilizzo singolo delle classi
#### Comportamentali
##### Template Method
+ L'idea consiste nello scrivere una parte invariante di un algoritmo una sola volta, e lasciare il resto da definire alle sotto-classi
+ Il pattern può essere implementato attraverso la definizione di una **classe astratta** 
+ Esso realizza anche la cosiddetta **inversione di controllo**, in cui è la sovraclasse a chiamare i metodi delle sottoclassi, e non il contrario
+ È una tecnica fondamentale per il riutilizzo del codice, si deve solo stare **attenti** nel **decidere** cosa viene tenuto **fisso** e cosa no
##### Observer
+ L'idea consiste nell'avere oggetti che osservano altri oggetti, monitorando i loro cambi di stato
	+ Esso può essere utilizzato per implementare **viste**
+ Essa è implementabile tramite un metodo **notify**, invocato dagli **oggetti** ogni qualvolta che **essi cambiano**, e comunicato agli osservatori, i quali si sono "iscritti" all'oggetto in precedenza
+ Si deve stare attenti a come il cambiamento dell'osservato possa interagire con gli osservatori
##### State
+ È un metodo per definire le **State Machine** in linguaggi che non lo supportano
+ Usiamo **classi esterne** ed il **polimorfismo** per definire i diversi stati 
+ Ha il difetto di aumentare il numero delle classi, ma semplifica molto l'implementazione
### Stili Architetturali
+ Oltre ai design pattern classici, esistono pure pattern architetturali, i quali sono un pattern più astratto, che descrive la struttura architetturale di un applicazione
#### MVC
+ L'idea è di dividere un'applicazione interattiva in tre tipologie di componenti
	+ Un **Modello**, che si occupa dell'elaborazione dei **dati**
	+ Delle **Viste**, che si occupano di gestire l'**input**
	+ Dei **Controller**, che si occupano di gestire l'**output**
+ Un interfaccia utente è formata da una vista ed un controller
# 6 - Refactoring e Testing
### Refactoring
+ Esso significa riorganizzare, **ristrutturare il codice**, in modo dal renderlo più semplice ed efficiente, senza modificare le sue funzionalità
+ **Non** vuol dire
	+ **Fixare** un bug
	+ Cambiare **linguaggio**
	+ Cambiare la **piattaforma**
	+ Cambiare completamente il **design**
+ Insieme ad altri metodi (Redocumentation, Reverse Engineering, Re-Engineering) è fondamentale per la sopravvivenza di **sistemi legacy**
+ Fare refactoring significa migliorare il codice in tutti i modi, oltre che supplire ad eventuali **debiti tecnici** (eccessiva complessità) dovuti a multipli aggiornamenti
	+ E soprattutto, rende il codice maggiormente mantenibile
+ Si deve fare raramente, in quanto impegnativo. In generale è  da fare:
	+ All'aggiunta di una nuova funzionalità di sistema
	+ In seguito alla correzione di un bug
	+ Quando viene rilevato un "**code smell**"
+ Un code smell è un **indicatore di cattiva salute** del codice
+ Non è una certezza, ma è un qualcosa che va controllato
+ Numerosi sono gli indicatori
	+ **Troppo codice** (Metodi lunghi, coidce duplicato, classi grandi...)
	+ **Troppo poco codice** (Classi piccole, Data Classes, catch vuoti...)
	+ **Troppi commenti**
+ Il refactoring viene eseguito in queste fasi quindi:
	+ Trova code smell
	+ Esegui una **piccola** semplificazione
	+ Ricompila il codice
	+ Riesegui i test, e controlla che tutto funzioni
+ La maggior parte dei refactoring è di basso livello (l**ow-level-refactoring**) ed essi sono i mattoncini che compongono i refactoring più complessi
+ Si possono utilizzare tool automatizzati per eseguire il refactoring, ma essi possono commettere errori a causa della loro semplicità. Sempre meglio ricontrollare
+ Esempi di **refactoring elementari** sono:
	+ Esplicitare le inner-class anonime
	+ Estrazione di metodi
	+ Estrazione di classi
	+ Trasferimento di metodi
	+ Sostituzione di variabili temporanee con query
	+ Sostituzione di parametri con chiamate di metodo
+ Alcuni **più complessi** sono
	+ Sostituzione di ereditarietà con delegazione
	+ Sostituzione di condizionalità con polimorfismo
	+ Separazione di presentation e business logic
### Testing
+ Il Software Testing è una procedura sistematica che prevede l’esecuzione di un sistema software con l’intento di trovare **failure** (e poi il **fault** associato)
+ Notiamo la differenza fra:
	+ **Errore**: commesso da uno sviluppatore
	+ **Fault**: Difetto vero e proprio nel codice
	+ **Failure**: Fallimento del sistema a causa di un fault
+ Il **debugging** è la ricerca di fault in seguito alla rilevazione di un failure durante il **testing**
+ Diviso in due fasi:
	+ Localizzazione del fault
	+ Rimozione del fault
---
+ Il testing è complesso, in quanto è **impossibile** fare una serie di **test esaustiva**
+ Si deve quindi selezionare una quantità di test limitata, i quali abbiano un'alta probabilità di ritrovare fault
+ Esistono due approcci:
	+ **Black** Box (Functional Testing)
		+ Universale, ed applicabile non appena i requisiti sono stati forniti
	+ **White** Box (Structural Testing)
		+ Molto utile, ma eccessivamente complesso, il suo utilizzo è limitato a piccole sezioni del sistema
+ La differenza fra i due è basata sul fatto che nel primo si creano test non basati sulla conoscenza del funzionamento interno del sistema
+ Un **caso di test** è un insieme di input e di output attesi. Una t**est suite** è un insieme di casi di test
---
+ Esistono diverse **tipologie** di testing
	+ Testing di **Unità**
		+ Test di una singola classe, solitamente white box
	+ Testing d'**Integrazione**
		+ Test di più moduli insieme, per verificare che funziono correttamente
	+  Testing di **Sistema**
		+ Test dell'intero sistema, controllando che soddisfi i requisiti. Solitamente black box
	+ Testing di **Regressione** 
		+ in seguito ad un aggiornamento, si effettuano nuovamente i test, per assicurarci che non ci siano effetti collaterali
+ Il testing può essere effettuato manualmente od in modo automatizzato
---
+ La qualità di una test suite può essere valutata in base al numero di righe di codice che vengono eseguite da essa (**coverage**)
+ Si può calcolare anche realizzando un grafo di flusso del codice
+ CI sono diversi "tier" di copertura:
	+ **Statement** coverage
		+ Tutti gli statement o nodi devono essere toccati
	+ **Branch** coverage
		+ Copertura di tutti i branch
		+ Condizione minima richiesta dallo standard IEEE
	+ **Multiple Condition** coverage
		+ Copertura di tutte le possibili condizioni dei nodi decisionali
	+ **All Paths** coverage
		+ Copertura di tutti i cammini (impossibile)
+ Solitamente si sceglie un tier ed una percentuale, e si realizza una suite che segua i due criteri
---
+ Nel black box testing, si parte **suddividendo** gli **input** in più classi
+ SI parte con input **legali** ed **illegali**, per poi suddividere ancor maggiormente
+ Si sceglieranno casi di test che utilizzano input sul **confine** di queste classi, in quanto sono quelli che hanno una probabilità maggiore di causare errori
# 7 - Persistenza Oggetti
+ Per memorizzare **dati** anche dopo la chiusura dell'applicazione dobbiamo essere in grado di **salvarli** e **recuperarli** alla prossima esecuzione
+ Questa è una richiesta nella maggior parte dei sistemi software. **Scegliere** in che **modo** implementarla è un **importante** scelta di **design**
+ Abbiamo due metodi principali:
	+ Tramite la memorizzazione su **file**
	+ Tramite l'utilizzo di un **DBMS**
+ Nel primo caso, i dati possono essere memorizzati in formato **binario**, o come un file **leggibile** (XML, JSON)
+ Nel caso dei DBMS, è importante scegliere il **tipo** di database
	+ RDBMS e modelli **relazionali**
		+ Molto popolare, utilizza SQL
	+ OODBMS (**Object** Data Model)
		+ Essi implementano la **persistenza ortogonale**, che permette di memorizzare perfettamente i dati, in modo 1:1
		+ Infatti, il sistema memorizza gli **oggetti** in memoria
	+ **Object-Relational** Model
		+ **Via di mezzo** fra i due precedenti. Permette di memorizzare gli oggetti in tabelle relazionali
		+ SQL moderno è basato su questo modello
		+ Non rispetta la prima forma normale, e permette di definire nuovi tipi e metodi
	+ **No SQL**
		+ Una famiglia eterogenea di sistemi accomunati dalla voglia di non usare SQL 
		+ Una ragione è l'**impedance mismatch**, la mancata corrispondenza diretta fra tabelle ed oggetti, dovuta all'**OR mapping**, il modo con cui si memorizzano gli oggetti in SQL
	+ Una volta scelto il database, dobbiamo decidere come interagire con esso dal codice, in quanto essi non sono direttamente collegati
	+ Ci sono più metodi
		+ **Brute-Force**
			+ Le classi del linguaggio possiedono metodi per interagire con il DB direttamente
			+ Soluzione più semplice, utile in piccoli progetti
			+ Genera però un forte accoppiamento, e riduce l'astrazione della memorizzazione dei dati
		+ **Persistence Layer** (DAO)
			+ Creiamo uno strato dell'applicazione che si occupa solamente di gestire la comunicazione fra l'applicazione ed il DB
			+ L'iterazione con il DB è quindi incapsulata dall'iterazione con queste classi apposite
			+ Questo facilita anche la futura modifica del codice, che riguarda solo le classi DAO
		+ **Persistance Framework**
			+ Evoluzione del precedente, consiste in un framework che si occupa di tradurre richieste in codice in codice SQL
			+ Il mapping è solitamente memorizzato in XML
			+ Questo implementa un incapsulamento completo. Il programmatore vede il SQL solamente quando programma il framework
			+ Queste query saranno auto-generate però, e quindi potrebbero non essere efficienti
+ Sistemi complessi come quelli dei grandi siti moderni possono anche scegliere di usare **diversi metodi** di memorizzazione nello stesso sito, a seconda del dato memorizzato
+ Si differenzia fra
	+ **Integration** DB
		+ Una base di dati per più applicazione, in SQL
	+ **Application** DB
		+ Più basi di dati, in JSON o XML. Disaccoppiamento fra il DB ed il modo in cui i dati vengono recuperati
# 8 - Extreme Programming
+ L'extreme programming è uno dei metodi di sviluppo **agili** citati in precedenza
+ È un metodo pensato per **piccoli gruppi** (4-20), che cerca di essere flessibile
+ **Non** viene usato **UML**, e si passa velocemente alla fase di codifica
+ I requisiti vengono raccolti tramite **user stories**, casi d'uso non regolamentati, spesso scritti dal cliente stesso
+ Il cliente è spesso contattato, e vengono eseguite **multiple release** (ogni 1-4 settimane), per dare un idea del lavoro eseguito al cliente
+ Il design viene prodotto tramite il metodo **CRC** (Class Responsibility Collaboration)
	+ Si usano foglietti adesivi su cui vengono scritti il nome della classe, le responsabilità e le collaborazioni con le altre classi
+ In generale, il design non viene esplicato in diagrammi e simili, ma può essere dedotto dal codice. È tutto nella testa degli sviluppatori
+ Per ciò il **codice deve** essere **ben scritto**, ed **espressivo**
---
+ **Non** si pianifica pensando al **riuso**, **ma** alla **semplicità**. Il codice è in comune, chiunque può modificarlo
+ Tutti i programmatori si mettono d'accordo su delle **convenzioni** sintattiche nel codificare
+ Spesso si esegue il **pair programming**: Una persona scrive, mentre l'altra osserva e commenta.
	+ Tecnica controversa
+ I casi di test vengono ideati prima di realizzare il codice, così da guidare lo sviluppo (**Test driven development** (TDD) approach)
+ Il refactoring viene effettuato molto spesso, non appena un'unità passa i casi di test
+ Sono previsti degli **acceptance tests**, effettuati ad ogni release. Non devono essere sempre tutti superati, ma il numero di test superati dovrebbe salire ad ogni release