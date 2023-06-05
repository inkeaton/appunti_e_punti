* Nelle espressioni regolari:
	* $\emptyset \to$ insieme vuoto
	* $\epsilon \to$ stringa vuota
	* $\sigma \to \{" \sigma "\} \forall \sigma \in A$  
	* $e_1|e_2 \to$ Unione del significato di $e_1$ ed $e_2$ 
	* $e_1 \cdot e_2 \to$ Unione del significato di $e_1$ ed $e_2$ 
	* $e^* \to$ Concatenazione di $e$ per tutte le lettere del suo linguaggio
	* $e \to (e)$ Il significato di e
* Ordine delle operazioni:
	* La stella di Kleene ha precedenza su concatenazione ed unione
	* La concatenazione ha la precedenza sulla unione
	* La concatenazione e l'unione hanno associatività sinistra
* Sintassi pratica dei linguaggi di programmazione:
	* $e+$ vuol dire più volte $e$
	* $e?$ vuol dire che $e$ è opzionale
	* $[...]$ vuol dire l'unione delle stringhe fra parentesi
	* $[... - ...]$ vuol dire l'unione delle stringhe nel range fra le lettere fra parentesi
	* [ ^... ] vuol dire ogni stringa di lunghezza 1 tranne quelle fra parentesi
	* . Vuol dire qualunque stringa di lunghezza 1
	* \ è l'"escape character", ovvero da significato speciale alle lettere normali, e viceversa
* Le espressioni regolari vengono usate in molti ambiti, ma a noi interessano ora per l'analisi lessicale
* L'analisi lessicale consiste nella suddivisione dellle stringhe in lessemi, ovvero unità lessicali
---
* Un token è una astrazione di un lessema
* Consiste in un tipo ed delle informazioni semantiche o sintattiche
* esempio, un identificatore