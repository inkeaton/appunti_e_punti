* I problemi possono essere classificati in diverse classi in base alle loro complessità: 
	* Un problema di classe __P__ è risolvibile e verificabile in tempo polinomiale
	* Un problema di classe __NP__ è verificabile in tempo polinomiale
		* Risulta che $P \subset NP$ 
* Tra i problemi NP esiste una sottoclasse, detta __NP-C__, contenente problemi NP-Completi. Questi hanno la caratteristica di essere di difficoltà superiore od equivalente a tutti gli altri problemi presenti in NP
	* Un problema è più difficile di un altro se, risolvendolo, posso risolvere anche il secondo
	* Questa nozione ha proprietà riflessiva e transitiva
* Per dimostrare che un problema è NP-Completo basta trovare un problema che sappiamo già essere NP-Completo e dimostrare che il primo problema è riducibile al secondo
* Conoscere queste proprietà di un problema ci permette di capire quando ha senso cercare determinati algoritmi, o quale complessità aspettaresi da essi
---
* Un esempio di problema NP-Completo è il problema __SAT__, ovvero la soddisfacibilità di formule logiche in forma congiuntiva-disgiuntiva (Ad esempio, $(A\vee B)\wedge(\neg B\vee C))$ 
	* Esso ha un ovvio algoritmo di risoluzione esponenziale
	* Ma ogni singola soluzione è verificabile in tempo polinomiale
---
* Gli algoritmi di verifica sono algoritmi di __decisione__. 
* Hanno la particolarità di essere funzioni, cui, posta un istanza del problema ed un __certificato__, ovvero una soluzione, ritornano vero se il certificato è soluzione per l'istanza
---
* Un problema può essere ridotto ad un secondo problema tramite una funzione di __riduzione__.
* Questa è una funzione con complessità __polinomiale__ che converte l'input di un problema nell'input di un secondo. Essa __mantiene__ la __correttezza__ dell'input nella trasformazione
---
* Tramite l'utilizzo di algoritmi non deterministici, è possibile dire che $P \subseteq NP$, ma si può dire che $P = NP$ ?
* Beh non si può sapere:
	* Per dire che $P \neq NP$ devo trovare un $p \in NP$ per cui non è possibile trovare un algoritmo polinomiale di soluzione
	* Per dire che $P = NP$  devo trovare un $p \in NP-C$ per cui esiste un algoritmo di risoluzione polinomiale. Per definizione, tutti gli altri saranno risolvibili in tempo comparabile
* Nessuna di queste due cose è stata dimostrata
---
* Problemi NP-Completi che abbiamo visto sono:
	* __3SAT__ - Variante di SAT in cui le formule disgiuntive hanno al massimo dimensione 3
	* __CLIQUE__ - Ritrovare un insieme di nodi tutti collegati fra loro in un grafo
	* __INSIEME INDIPENDENTE__ - Contrario di CLIQUE, ritrovare un insieme di nodi scollegati fra loro
	* __PROBLEMA DEL COMMESSO VIAGGIATORE__ - Dato un grafo pesato e orientato, ritrovare il minmo ciclo hamiltoniano
	* __PROBLEMA DELLO ZAINO__ - Dato uno zaino che può portare n chili e un insieme di oggetti, ognuno dotato di peso e valore, trovare il valore massimo trasportabile nello zaino
	* __COPERTURA DI VERTICI__ - Dato un garfo, ritrovare l'insieme di vertici che è collegato a tutti gli archi della figura
---
* Controllare gli appunti __cartacei__ per maggiori dettagli...