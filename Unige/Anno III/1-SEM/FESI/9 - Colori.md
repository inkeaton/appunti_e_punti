+ Il colore è una **proprietà** molto **complessa** da descrivere, in quanto **non oggettiva**, ma dipendente da numerosi fattori
	+ Illuminazione
	+ Memoria
	+ Emozioni
	+ Identità e proprietà dell'oggetto
+ A livello biologico, l'uomo vede attraverso due tipi di cellule
	+ I **bastoncelli**, che identificano le variazioni di **luminosità**
	+ I **coni**, i quali identificano i **dettagli** ed i colori di un oggetto. Ne esistono tre varianti
		+ S corti, identificano le lunghezze blu
		+ M medi, identificano le lunghezze verdi
		+ L lunghi, identificano le lunghezze rosse
+ I colori stessi sono ricavati da una sezione limitata delle lunghezze d'onda delle radiazioni elettromagnetiche
---
+ Detto tutto ciò, è possibili creare un **modello** di colore, in modo simile a quello che abbiamo descritto per i suoni e le immagini?
+ Beh sì, ma dobbiamo decidere la nostra **base**, ovvero il nostro sottoinsieme di elementi che ci permettono di formare i colori
	+ Negli esempi precedenti, le basi erano l'insieme dei sinusoidi e delle onde planari
+ Secondo la **teoria del tristimolo**, esistono solamente tre classi di fotorecettori sensibili al colore nel cervello, quindi ci basterà una base di tre valori
+ Esistono due modi principali per creare colori:
	+ **Sintesi Sottrattiva**
		+ Partendo dal bianco, si rimuovono piano a piano le onde non necessarie, per formare il colore voluto
		+ In questo modello, i colori primari, la nostra base, sono il **ciano**, il **magenta** ed il **giallo**
	+ **Sintesi Additiva**
		+ Partendo dal nero, si aggiungono le onde necessarie, per formare i colori voluti
		+ In questo modello, i colori primari, sono il **rosso**, il **verde**, ed il **blu**
+ Da queste due sintesi, otteniamo due modelli famosi
	+ **CMYK**
		+ Usato nelle stampanti, utilizza ciano, magenta, giallo e nero per creare i colori voluti
			+ Il nero viene utilizzato per produrre tinte scure nei casi di inchiostri di bassa qualità
	+ **RGB**
		+ Usato nelle immagini digitali, utilizza rosso, verde e blu
			+ È uno standard non-ufficiale online
			+ È capace di rappresentare "solo" 16,7 milioni di tinte
			+ Questo ed il precedente sono spazi di colore **cubici**
+ Il vero standard invece, capace di rappresentare tutti i colori esistenti, è il **CIE**, inventato nel 1931.
	+ Esso utilizza tre valori
		+ $x, z$ indicano la tinta
		+ $y$ indica la percezione della luminanza sulla retina
---
+ Nonostante la popolarità di RGB, esso risulta abbastanza complesso da usare nel caso in cui volessimo creare o trovare un colore
+ Esiste quindi un ulteriore standard, **HSV**, il quale permette una modellazione più facilmente comprensibile
	+ Utilizza tre valori
		+ $H$ è l'hue, o **tinta**. Rappresenta il "**colore**" vero e proprio
		+ $S$ è la **saturazione**. Rappresenta la **distanza** del colore dal **grigio**
		+ $V$ è il valore, o **intensità luminosa**. Rappresenta la **distanza** del colore dal **nero**
	+ Esso genera uno spazio di colore **conico**
---
+ Un problema complesso nel mondo digitale è la segmentazione, ovvero il riconoscimento di aree di colore uniforme
+ Per quanto a noi possa sembrare ovvio, aree di di colore uniforme possono apparire non omogenee, a causa di differente illuminazione
+ Risulta quindi complesso identificare le sezioni uniformi