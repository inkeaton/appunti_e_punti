* Il **Query Processor** è un componente del gestore delle query, responsabile dell'**elaborazione** delle **interrogazioni** richieste
* Ha come obbiettivo principale la **determinazione** della modalità più **efficente** per eseguire una query
---
* Ogni query verrà tradotta in un **Piano di Esecuzione Logico** (LQP), una riscrittura in algebra relazionale dell'interrogazione. Questo potrà essere **rappresentato** da un **albero**.
* Esistono **multipli** LQP per una singola query. Il sistema dovrà determinare il più **efficace**.

* Una volta **fissato** un **LQP**, il sistema dovrà determinare un **Piano di Esecuzione Fisico** (PQP), ovvero l'insieme delle operazioni (**algoritmi**) utilizzati per eseguire l'interrogazione a livello fisico.
* Questo non **dipenderà** solo dal **LQP**, ma anche dallo **schema fisico** dei dati (Se sono presenti indici, se i record sono ordinati, etc.)
---
* Il Query Processor elabora le interrogazioni nel seguente modo, attraverso i suoi componenti:
	1. Query Compiler
		 1. **Parser**
			* Viene controllata la correttezza della query e trasformata in un parse tree
		2. **Translator**
			* Preso il parse tree, viene trasformato nella formula algebrica relazionale più **ovvia** (non la più ottimale)
	2. Query Optimizer 
		1. **Logic Optimizer**
			* Questa formula viene riscritta nella maniera più ottimale (LQP)
		2. **Physical Optimizer**
			* Fissato l'LQP e lo schema fisico, viene elaborato il piano fisico più efficente (PQP)
				* Come? Tramite statistiche di sistema, vedremo più avanti
	3. Query Engine 
		1. **Execution**
			* La query viene eseguita
---
* Vediamo nei dettagli il **Logic** Optimizer
* Come fa a determinare il piano migliore? Esso possiede due insiemi di concetti utili
	* **Equivalenze** Algebriche
	* Regole di **Riscrittura** (basate su **euristiche**)

* Quest'ultime sono regole basate sui seguenti principi:
	* **Anticipare** il più possibile le operazioni che permettono di **ridurre** la dimensione dei risultati intermedi  
		* **Selezione** e **Proiezione**  
	* Fattorizzare condizioni di selezione complesse e lunghe liste di attributi in proiezioni, per aumentare la possibilità di applicare regole di riscrittura
* Derivano le seguenti regole:
	* Eseguire le operazioni di **selezione** (σ) il più **presto** possibile
	* Eseguire le operazioni di **proiezione** (π) il più **presto** possibile
	* **Introdurre ulteriori proiezioni** nell’espressione, gli unici attributi da non eliminare sono quelli che appaiono nel risultato della query  o sono necessari in operazioni successive

* Alla fine l'ottimizzatore rstituirà un unico piano. Potrebbe restituirne di più equivalenti, ma aumenterebbe esponenzialmente il lavoro dell'ottimizzatore fisico