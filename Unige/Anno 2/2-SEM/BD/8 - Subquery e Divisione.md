* È possibile eseguire delle **sottointerrogazioni**, ovvero query interne ad altre query. 
* **Solitamente** queste vengono utilizzate per recuperare **informazioni** per **WHERE** e **HAVING**
* Queste dovrebbero riportare un unico valore, oppure si possono usare le seguenti keyword:
	* **ANY**: l'operazione deve valere per almeno una tupla del risultato
	* **ALL**: l'operazione deve valere per tutte le tuple del risultato
* Le subquery **correlate** sono sottoquery ricalcolate per ogni tupla che viene analizzata. 
* A causa di ciò, sono molto **inefficenti**
---
* Introduciamo infine un'ultima operazione dell'algebra relazionale, la **divisione**.
* Corrisponde a cercare **elementi** di una relazione **abbinati** a tutti gli elementi di un'altra relazione
* Viene chiamata divisione in quanto corrispondente all'**inverso** del **prodotto** cartesiano
* In SQL non esiste un'operatore apposito, ma è possibile ricrearla tramite la keyword **EXISTS**