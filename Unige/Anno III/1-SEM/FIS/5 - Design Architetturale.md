+ Ora che abbiamo visto la parte di raccolta requisiti, passiamo a quella di **Software Design**
---
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
+ Comunque la scelta di un'**architettura aiuta**, dato che:
	+ Guida lo sviluppo ed aiuta nella comprensione del sistema
	+ Documenta il sistema
	+ Aiuta a ragionare sull'evoluzione del sistema
	+ Supporta decisioni manageriali
	+ Facilita l’analisi di alcune proprietà
	+  Permette il riuso (Large-scale)
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
	+ Insieme di **client** che **utilizzano** tali servizi 
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