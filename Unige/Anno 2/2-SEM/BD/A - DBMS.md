* In questa sezione impareremo ad utilizzare i sistemi di gestione di basi di dati
---
* I DBMS vengono creati allo scopo di superare alcune __limitazioni__ imposte dalla struttura tradizionale di un __OS__ e di un file system
* oltre a permettere una migliore gestione dei dati, superando problemi di accesso multiplo e di sicurezza, permettono anche di utilizzare specifici linguaggi di tipo __dichiarativo__, i quali permettono di interagire con le informazioni, in modo molto astratto
* Il sistema adempirà alla richiesta attraverso i metodi che preferisce. Gli algoritmi utilizzati sono solitamente scritti in linguaggi __operazionali__, come l'Algebra Relazionale
---
* Il __database__ può essere visto attraverso tre livelli:
	* Livello __fisico__: I dati vengono visti come sono conservati sul dispositivo fisico. A noi non ci serve molto
	* Livello __logico__: I dati vengono visti come descritti dalle strutture e dagli schemi del modello relazionale
	* Livello __esterno__: Presente solo in database di grandi dimensioni, permette di visionare solo alcune parti dei dati, tramite alcune __viste__, definite dall'amministratore, accessibili solo ad un gruppo di applicazioni
* Su di essi valgono due proprietà:
	* Indipendenza __fisica__: Cambiando la struttura del livello fisico, la struttura del livello logico __non__ cambia
	* Indipendenza __logica__: Cambiando la struttura del livello logico, alcune viste del livello esterno __potrebbero__ cambiare
* Inoltre, ogni livello viene utilizzato e modificato tramite dei linguaggi dichiarativi specifici:
	* SDL: Permette di modificare lo schema dei dati, lavora sul livello esterno e logico
	* __DML__: Permette di modificare l'istanza dei dati, lavora principalmente sul livello logico
	* DDL: Permette di modificare lo schema fisico dei dati, lavora sul livello fisico
* A noi interesserà il livello __logico__
---
* Studieremo database di tipo __integration__ DD, in cui i dati vengono strutturati sulla base della loro __rappresentazione ideale__, e non in base a come devono essere usati