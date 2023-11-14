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
---
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
+ In UML, un **metodo** è l'implementazione di un operazione, la quale specifica il comportamento di essa
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