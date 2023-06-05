* All'interno di un sistema, è fondamentale fare in modo che solo determinati utenti abbiano determinati privilegi su determinate relazioni
* Queste informazioni verranno memorizzate nei cataloghi di sistema, in terne principalmente composte da:
	* Soggetto: L'utente 
	* Oggetto: La relazione
	* Privilegio: Il privilegio posseduto dall'utente sulla relazione
* Questi privilegi vengono concessi dal creatore delle relazioni stesse, tramite due comandi:
	* GRANT
	* REVOKE
* È una politica discrezionale, a sistema chiuso
---
* Un esempio di operazione di GRANT è la seguente:
```sql
GRANT SELECT | ALL PRIVILEGES
ON Relazione
TO Utente | Public
{WITH GRANT OPTION}
```
+ La GRANT OPTION permette all'utente che riceve il privilegio di concederlo a sua volta ad altri utenti
---
Un esempio di operazione di REVOKE è la seguente:
```SQL
REVOKE {GRANT OPTION FOR} SELECT
ON Relazione
FROM Utente
```
* È possibile anche solo rimuovere la GRANT OPTION
---
* Le autorizzazioni presenti nei cataloghi possono essere viste come dei grafi. I nodi saranno gli utenti, gli archi le autorizzazioni concesse da un "nodo" all'altro.
* Ci sarà un grafo per ogni privilegio per ogni relazione
* Questi grafi saranno usati dal sistema per capire come eseguire GRANT e REVOKE
	* Per il GRANT, dovrà capire se permettere l'operazione all'utente, controllando se il suo nodo non ha archi entranti, o ha un arco entrante con GRANT OPTION
	* Per il REVOKE, dovrà controllare se è stato l'utente a concedere il permesso al soggetto del comando. Oltre a questo, dovra vedere come gestire eventuali dipendenze. Lo si può esplicare tramite le seguenti keyword:
		* RESTRICT: Se esistono nodi dipendenti, non eseguire
		* CASCADE: Se esistono nodi dipendenti, elimina anch'essi
	* È importante ricordare che gli utenti possono ricevere permessi da fonti indipendenti, possbilemente rendendo alcuni REVOKE effettivamente inutili
---
* Gestiti in maniera simile agli utenti, esistono i ruoli, gruppi di utenti
* Questi vengono gestiti tramite i comandi
	* CREATE
	* DROP
	* SET
* Gli utenti possono cambiare ruolo
* Si possono sanche usare GRANT e REVOKE per dare permessi a questi ruoli, oppure dare ad un utente il permesso di usare un ruolo, tramite ADMIN OPTION
* I ruoli possono anche essere definiti tramite inheritance, in modo simile ai linguaggi di programmazione ad oggetti
---
