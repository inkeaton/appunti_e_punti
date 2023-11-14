+ Il processo di design ha numerose fasi
+ Durante l'**High Level Design** noi:
	+ Progettiamo l'architettura del sistema
	+ Specifichiamo le componenti interne
	+ Definiamo le interfacce, i metodi offerti dalle classi
+ Durante il **Low Level Design** noi:
	+ Progettiamo l'organizzazione del codice
	+ Progettiamo le strutture dati utilizzate
	+ Progettiamo gli algoritmi implementati
![[Dsign.png]]
---
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
+ Vediamo ora la **codifica degli algoritmi**
+ Questa attività è solitamente responsabilità degli sviluppatori, e viene eseguita tramite i seguenti passaggi:
	1. Si analizza la descrizione di design della classe “target”
	2. Se esistono una o più operazioni che necessitano di un algoritmo
		1.  Se è possibile selezionare un algoritmo conosciuto, si seleziona
		2. Se invece occorre definire un algoritmo si sceglie una **notazione**
		3. Utilizzando la nozione di “**stepwise refinement**” si sviluppa l’algoritmo nella notazione scelta
			+ Lo stepwise refinement è il processo attraverso il quale il codice viene sviluppato attraverso vari passi di raffinazione, in cui si riduce sempre di più l'astrazione della notazione
		4. *(facoltativo) Si usano i metodi formali per provare la correttezza dell’algoritmo proposto*
+ Quali sono queste notazioni? Ne esistono multiple, divisibili in 
	+ Visuali
	+ Testuali
+ Un esempio è lo **pseudo-codice** (PDL), in cui si mischia linguaggio naturale (narrativa) con linguaggio di programmazione
---
+ Vediamo i vari principi di **buon design**. Sono numerosi per cui ne vederemo solo una parte
	+ In essi useremo il concetto di **modulo**, un entità software capace di fornire servizi, e contenere altri moduli a sua volta
1. **Astrazione**
	+ L'astrazione permette di concentrarsi su un problema senza doversi preoccupare dei dettagli più minuti, così da ragionare meglio
	+ Esistono tre tipi di astrazione
		+ Funzionale
		+ di Dati
		+ di Controllo
2. **Decomposizione**
	+ Conviene scomporre un problema complesso in più sotto-problemi più semplici, per risolverlo meglio
	+ Bisogna però stare attenti a non esagerare, in quanto c'è comunque un costo nello sforzo necessario per riunire i sotto-problemi
3. **Modularità**
	+ Conseguenza del principio precedente, ci dice che dovremmo separare il sistema in moduli, seguendo il principio di **separation of concerns**
		+ I moduli ottenuti dovrebbero essere accomunati da obbiettivi e funzionalità offerte (massimizzare la coesione, minimizzare l’accoppiamento)
	+ Per **coesione**, si intende che un modulo dovrebbe svolgere un solo compito astratto
	+ Esistono diversi tipi di coesione, ma noi consideriamo quella funzionale
	+ È importante gestire anche l'**accoppiamento**, ovvero come i moduli interagiscono fra loro. In generale, si deve evitare che un modulo possa modificare parti di altri
4. **Information Hiding**
	+ Proprio per evitare l'accoppiamento cattivo, l'information hiding fa in modo di nascondere i dati di un modulo agli altri, evitando l'accesso diretto
5. **Alto Fan-in, Basso Fan-out**
	+ Costruendo il grafo delle dipendenze din un programma, si deve fare in modo che ci siano poche dipendenze (fan-out) e tanti utilizzi (fan-in) di ogni modulo
6. **Generalità**
	+ Ogni modulo deve essere strutturato in modo da essere generale e riutilizzabile
7. **In Generale:**
	+ Il design deve essere il più semplice possibile (**KISS**)