+ Gli **UseCases**, proposti per la prima volta da Ivar Jacobson nel 1992, sono una **tecnica** utilizzata per **esprimere requisiti funzionali** di un sistema (anche non informatico!)
+ È una tecnica non visuale, che usa **solo testo**, ma esistono alcune sue rappresentazioni grafiche
+ In essi, il sistema vine visto come una black-box, e vengono descritte le iterazioni fra le entità partecipanti ed esso
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
		+ È il goal dello use case “breve frase verbale attiva”
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