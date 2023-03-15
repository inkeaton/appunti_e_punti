* I DBMS sono organizzati in __servizi__, moduli software, ognuno devoto ad uno specifico compito
* Essi si suddividono in __esterni__, richiesti esplicitamente dagli utenti, ed __interni__, utilizzati dal sistema per adempiere alle richieste
* Possiamo raggrupparli inoltre in tre componenti:
	* __Gestore delle strutture di memorizzazione__: L'insieme dei servizi che si occupano di gestire e memorizzare i dati
	* __Query manager__: L'insieme dei servizi che gestiscono ed eseguono i comandi DML
	* __Transaction manager__: L'insieme dei servizi che si occupano di gestire richieste complesse, e garantire l'integrità dei dati
---
* Oltre ai dati stessi, vengono memorizzati anche i cosiddetti __metadati__, informazioni come i permessi d'accesso, utenti, etc.
* Questi vengono memorizzati nei __cataloghi__ di sistema. Questi memorizzano anche le informazioni sui metadati stessi
---
* I classici utenti di DBMS sono i seguenti:
	* Progettisti di database
	* Programmatori Applicativi
	* Amministratori di Database (DBA)
	* Progettisti di DBMS
---
* Esistono diversi modi in cui organizzare i DBMS:
	* __Centralizzata__: Sia gli utenti che i sistemi si trovano sulla stessa macchina
	* __Client-Server__: I sistemi sono memorizzati su di una macchina, gli utenti effettuano richieste da altri host
	* __Distribuite__: I dati e le applicazioni sono distribuiti su più macchine.