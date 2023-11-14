+ In questo corso, studieremo l'ingegneria del software, un insieme di trucchi, consigli e strumenti, atti a rendere efficiente lo sviluppo di una applicazione
---
+ Alla base sta il concetto che, come in altre industrie, la qualità del prodotto finale dipenda dalla qualità del processo produttivo
+ Vengono quindi definiti dei **processi**, serie di **fasi** da seguire nella produzione del software
+ Come in una catena di montaggio, ogni fase produce un **deliverable**, il quale verrà rielaborato nella fase successiva

+ Esistono tre macro modelli:
	+ **Agili**: Più **libertà** data ai programmatori, i quali devono necessariamente essere molto abili
	+ **Plan-driven**: Data maggiore importanza al progetto ed al **design** iniziale
	+ **Formali**: **Teoria** al centro, basata su dimostrazioni matematiche

+ Uno dei modelli più famosi è il **Waterfall**, composto dalle seguenti fasi:
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
