* Possono venire definite anche le __complessità__ di un __problema__, nel seguente modo
	* La $O(f(n))$ di un problema viene definita come la $O(f(n))$ __minima__ fra quelle degli algoritmi che risolvono il problema
	* La $\Omega(f(n))$ di un problema viene definita come la $\Omega(f(n))$, __comune__ a tutti gli algoritmi risolutori del problema
* I problemi vengono quindi __classificati__ in base alle loro complessità e presenza di algoritmi di risoluzione:
	* __Trattabili chiusi__: Risolvibili con algoritmi efficenti, non si possono migliorare
	* Trattabili __con gap algoritmico__: Risolvibili con algoritmi efficenti, se ne possono teoricamente creare di più efficenti
	* __Presumibilmente intrattabili__: Risolvibili con algoritmi esponenziali, se ne possono teoricamente creare di più efficenti
	* __Dimostrabilmente__ intrattabili: Risolvibili con algoritmi esponenziali, non si possono migliorare
	* Dimostrabilmente __insolubili__: Irrisolvibili tramite algoritmo
---
* Come possiamo verificare la __correttezza__ degli algoritmi? Nel caso di quelli __ricorsivi__, possiamo sfruttare le loro definizioni, in quanto __induttive__
* Infatti, avendo definito un insieme in modo induttivo, è possibile definire una proprietà come valida sulla totalità dell'insieme attraverso il __principio d'induzione__
* __Induzione aritmetica__:
	* $P(0), \; se \; P(n) \to P(n+1) \; \; \rightarrow  \; \; P(n) \forall n \in \mathbb{N}$ 
* __Induzione aritmetica completa__:
	* $P(0), \; se \; P(n) \to P(m) \; (m > n) \; \; \rightarrow  \; \; P(n) \forall n \in \mathbb{N}$ 
		* Quest'ultima è utile nel caso di algoritmi di tipo _divide-et-impera_
---
* __Serie Geometrica__:
	* $\sum^{n}_{i=0} q^i = \frac{q^{n+1} - 1 }{q - 1}$ 