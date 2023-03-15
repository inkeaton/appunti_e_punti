* Nel __tradurre__ i concetti __logici__ di relazione e schema, sfrutteremo la già esistente struttura __fisica__ dei record e dei tracciati record. 
* Ogni __tupla__ sarà rappresentata da un __record__ nel file, e il relativo __tracciato__ indicherà lo __schema__ presente
* A seconda dei tipi di dati, le tuple possono occupare una quantità __differente__ di __spazio__, nonostante l'equivalente schema e struttura. Inoltre, potremmo pensare di conservare __più__ tuple all'interno dello __stesso file__ (Questo viene normalmente fatto in database di grandi dimensioni)
---
* Ogni volta che eseguiamo un __comando__, questi viene:
	* __Controllato__ ed approvato dal Query Manager, venendo tradotto in un programma specifico
	* Quest'ultimo __accede__ ad i dati del database, tramite il File Manager ed il Buffer Manager
		* Il DBMS utilizza un proprio file manager così da migliorare la portabilità e l'efficenza
* Essendo questi ultimi conservati in file, dobbiamo pensare al modo più efficente per accedere ad essi, considerando le __limitazioni__ degli hard-drive
---
* Possiamo suddividere il tempo necessario in tre sezioni:
	* Tempo di __latenza__: Tempo di spostamento del braccio laser sul disco ($\approx 10 ms$)
	* Tempo di __trasferimento__: ($\approx 1 ms$ per blocco)
	* Tempo di __accesso__: ($\approx1$ milionesimo di secondo)
* Possiamo __migliorare__ il tempo di __latenza__ organizzando in modo ottimale i dati su disco!
* Possiamo organizzarli in tre modi:
	* Allocazione __contigua__: Tutti i blocchi relativi ad un file si trovano vicini
		* Diminuisce il tempo richiesto, ma è difficile espandere i file
	* Allocazione __concatenata__: I blocchi sono sparsi, ed ognuno punta al successivo
		* Facile espandere, ma aumenta il tempo richiesto
	* Allocazione __???__: I blocchi si trovano su tracce diverse, sullo stesso "cilindro", ma alla stessa distanza dal centro. 
		* In questo modo, le braccia si devono muovere comunque una sola volta, ma abbiamo lo spazio per espandere il file. Organizzazione ottimale
* Considerando invece la struttura __interna__ di un file, conviene fare in modo che in un blocco si trovino solo record fra loro __collegati__, così da __ridurre__ il numero di letture richieste
* Un modo ottimale è __ordinare__ i record per un qualche criterio