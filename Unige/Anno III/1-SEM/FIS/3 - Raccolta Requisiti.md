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