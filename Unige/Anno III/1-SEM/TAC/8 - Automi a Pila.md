+ Un automa a pila (**Push Down Automata**) (PDA) può essere visto come un $\varepsilon$-NFA dotato di una **memoria**, ovvero una **pila** 
+ Automa
	+ $\mathcal{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{Yellow}{\Gamma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Mulberry}{\delta}, \textcolor{Aquamarine}{Z} , \textcolor{Cyan}{F})$ 
		+ $\textcolor{Apricot}{Q}$ è un insieme di **stati**
		+ $\textcolor{LimeGreen}{\Sigma}$ è l'alfabeto di **input**
		+ $\textcolor{Yellow}{\Gamma}$ è l'alfabeto dei simboli della **pila**
		+ $\textcolor{WildStrawberry}{q_0}$ è lo **stato iniziale** della macchina
		+ $\textcolor{Mulberry}{\delta}$ è la **funzione di transizione**
		+ $\textcolor{Aquamarine}{Z}$ è un simbolo di $\textcolor{Yellow}{\Gamma}$, usato come "**placeholder**" nella pila
		+ $\textcolor{Cyan}{F}$ è l'insieme degli **stati finali** della macchina, **facoltativi**
+ Funzione di Transizione
	+ $\textcolor{Mulberry}{\delta} : Q \times (\Sigma \cup \{\varepsilon\}) \times \Gamma \to \mathcal{P}(Q\times \Gamma^*)$
		+ A ogni passo, l'automa osserva il simbolo, lo stato ed il simbolo in cima alla pila, per poi muoversi ad un nuovo stato, e modificare il simbolo della pila
+ Configurazioni
	+ $<q, u, \alpha>$
		+ $q \in Q$ stato corrente
		+ $u \in \Sigma^*$ stringa in lettura
		+ $\alpha \in \Gamma^*$ top della pila
+ Configurazioni Ferme
	+ $<q, a, \varepsilon>$ 
		+ La pila è vuota
	+ $<q, \varepsilon, x\alpha>\wedge \; \delta(q, \varepsilon,x) = \emptyset$ 
		+ La stringa è vuota, e non abbiamo altre transizioni silenti
	+ $<q, \sigma u, x\alpha> \wedge \; \delta(q, \sigma, x) = \emptyset \; \wedge \; \delta(q, \varepsilon, x) = \emptyset$ 
		+ Ci sono ancora simboli da leggere, ma non ci sono transizioni adatte
 + Passi
	 + $<q, \sigma u, x\alpha> \;\to \; <q^{'}, u, \beta \alpha> \; \leftrightarrow \; q^{'} \in \delta(q, \sigma, \beta)$    (Passo di **lettura**)
	 + $<q, u, x\alpha> \;\to \; <q^{'}, u, \beta \alpha> \; \leftrightarrow \; q^{'} \in \delta(q, \varepsilon, \beta)$       (Passo **silente**)
+ Riduzione
	+ È non deterministica e **non terminante** (È possibile ritrovarsi in cicli infiniti)
+ Linguaggio Accettato
	+ $L^{ES}(\mathcal{M}) = \{u \in \Sigma^* \; | <q_0, u, z> \; \xrightarrow{*} \; <\_, \varepsilon, \varepsilon>\}$ 
		+ Riconoscimento per **pila vuota**
	+ $L^{FS}(\mathcal{M}) = \{u \in \Sigma^* \; | <q_0, u, z> \; \xrightarrow{*} \; <q_f \in F, \varepsilon, \_>\}$
		+ Riconoscimento per **stati finali**
---
+ Per quanto in generale questi automi non sono deterministici, esiste una sotto-categoria detta **DPDA**, formata da **automi a pila deterministici**
+ È possibile capire se posso creare un automa deterministico per un determinato linguaggio?
+ Sì, una delle proprietà che ce lo mostra è la **proprietà del prefisso**
	+ Se $L$ contiene due stringhe, di cui una è prefisso dell'altra, allora non esiste un DPDA in grado di riconoscerle
		+ Questo implica che nessun automa in grado di riconoscere la stringa vuota può essere deterministico, in quanto questa è comparabile ad un prefisso
+ Un automa è deterministico se:
	+ $\forall <q, \sigma, x>$ 
		+ Esiste al più un passo di lettura
		+ Esiste al più un passo silente
		+ Esiste o un passo di lettura o uno silente