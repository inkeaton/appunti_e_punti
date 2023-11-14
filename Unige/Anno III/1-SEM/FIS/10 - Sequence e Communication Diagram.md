+ *Non essendo presente a lezione, è più confusa del solito. Da rivedere*
+ I tipi di diagrammi che vedremo oggi appartengono alla sotto-categoria di diagrammi di modellazione dinamica, come gli UseCase diagram
---
+ I diagrammi di **iterazione** descrivono la collaborazione di un gruppo d'oggetti, ovvero come essi **comunicano** fra loro
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
---
+ I diagrammi di **comunicazione** sono **simili** ai sequence diagram, in quanto come essi hanno l'obbiettivo di descrivere la comunicazione fra due o più oggetti, ma quest'ultimi si **concentrano** maggiormente sulla **comunicazione stessa**, invece che alla sequenza temporale dello scambio di messaggi