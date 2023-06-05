* Al livello 5, abbiamo bisogno di un protocollo in grado di tradurre nomi astratti in indirizzi ip
* Questi è il protocollo __DNS__ (RFC 1034, 1035). Consiste in domande ad un insieme di server, che rispondono con l'indirizzo richiesto
* Domande e risposte sono scritte nel seguente modo:
	* __16__ bit di __ID__ del messaggio, __16__ bit di __flag__
	* __16__ bit di # di __domande__ fatte e __16__ bit di # di __risposte__ ricevute
	* __16__ bit di risposte __autoritative__ e __16__ bit di risposte __addizionali__ 
	* Sezioni di lunghezza variabile contenenti __domande__, __risposte__, __autoritative__, __addizionali__
---
* La comunicazione fra host e server avviene sulla porta UDP/53, usando il protocollo UDP
* I server DNS sono organizzati in strutture ad albero, gerarchiche. 
	* Esiste un nodo __Root__, punto di partenza
	* I nodi ad esso figli sono i __Top Level Domain__. Questa sezione è gestita a livello __pubblico__
	* Subito sotto si trovano i livelli __Autoritativi__, gestiti __privatamente__
* Questa organizzazione permette di accedere facilamente all'intera rete, poichè nonostante la usa enormità, essa è suddivisa in varie sezioni, ed ogni server lavora solo su una sezione
	* ES www.dibris.unige.it 
		* .it è il TLD (dovrebbe essere .it., ma nessuno lo scrive così)
		* .unige e .dibris sono livelli autoritativi
		* www. indica la generica struttura interna di un server, usato per indicare la volontà di volersi connettere ad un host della rete, senza doverlo specificare ulteriormente
---
* Vengono usati due __algoritmi__ diversi per ritrovare i server richiesti:
	* __Ricorsivo__: il client invia la domanda alla root. La root identifica il TLD, ed invia la richiesta al nodo relativo. Questo nodo fa lo stesso con il livello autoritativo, e così via fino all'ultimo nodo. Questi invierà l'IP necessario al client
	* __Iterativo__: Simile al precedente, ma con la differenza che ogni nodo invia l'ip del nodo successivo al client, il quale invierà nuovamente la richeista al nuovo nodo
* Il __primo__ è più __veloce__, ma __grava sui server__, mentre il __secondo__ è più __lento__, ma fa in modo che __parte del carico sia presa dal client__
* È la rete DNS a scegliere che algoritmo usare
---
* È possibile utilizzare dei __server DNS locali__: semplicemente prendono il ruolo dei client nel rapportarsi con la rete, __unendo in qualche modo i due algoritmi__. Essi possiedono inoltre una cache in cui memorizzano indirizzi precedentemente tradotti, così da premettere in alcuni casi traduzioni immediate