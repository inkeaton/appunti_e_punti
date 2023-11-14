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