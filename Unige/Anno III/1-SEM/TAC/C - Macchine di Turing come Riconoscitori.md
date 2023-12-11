+ La **Macchina di Turing** è un formalismo molto speciale, in grado di **descrivere** **tutte** le **funzioni calcolabili**
+ È immaginabile come un **nastro infinito**, ricoperto di **simboli** vari, sul quale scorre una **testina** in grado di scrivere e leggere i simboli
+ Esistono **più definizioni** specifiche, **cominceremo** vedendo la definizione della macchina come **automa riconoscitore**
---
+ La Macchina di Turing è una **macchina a stati deterministica**
+ L'automa è descritto dalla seguente tupla:
	+ $\mathcal{MdT} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Mulberry}{\delta}, \textcolor{Cyan}{F})$ 
		+ $\textcolor{Apricot}{Q}$ è un insieme di **stati**
		+ $\textcolor{LimeGreen}{\Sigma}$ è l'alfabeto di **input**, dei simboli sul nastro
		+ $\textcolor{WildStrawberry}{q_0}$ è lo **stato iniziale** della macchina
		+ $\textcolor{Mulberry}{\delta}$ è la **funzione di transizione**
		+ $\textcolor{Cyan}{F}$ è l'insieme degli **stati finali** della macchina
+ Funzione di Transizione
	+ $\textcolor{Mulberry}{\delta} : Q \times \Gamma \to Q \times \Gamma \times \{L, R, N\}$
		+ L, R e N indicano **come muoversi** sul nastro (sinistra, destra, fermo)
			+ Spesso N è realizzato muovendosi a vuoto due volte, destra e sinistra
+ Configurazioni
	+ $<\alpha, q, \beta>$
		+ $\alpha \in \Sigma^*$ stringa a sinistra della testina
		+ $q$           stato attuale della macchina
		+ $\beta \in \Sigma^*$ stringa a destra della testina
+ Configurazioni Ferme
	+ $<\alpha, q, x\beta>\wedge \; \delta(q, x)\uparrow$ 
	+ $<\alpha, q, \varepsilon> \wedge \; \delta(q, \varepsilon)\uparrow$ 
+ Computazioni
	+ Computazione **accettante**  
		+ $c_0 \to c_1 \to \cdots \to c_n : <\_, q \in F, \_>$ 
		+ Non ci importa di cosa è rimasto sul nastro, siamo giunti in uno stato finale
		+ Per fare in modo di fermarci sugli stati finali, si fa in modo che se $q_n \in F$, $\delta(q, x)\uparrow$ 
	+ Computazione **non accettante**
		1. $c_0 \to c_1 \to \cdots \to c_n : <\alpha, q \notin F, \beta>$ 
			+ Con casi possibili
				+ $<\alpha, q \notin F, x\beta> \quad \delta(q, x)\uparrow$ 
				+ $<\alpha, q \notin F, \varepsilon> \quad \; \delta(q, \varepsilon)\uparrow$ 
		2. $c_0 \to c_1 \to \cdots \to c_{\infty}$
			+ La macchina **non termina**
			+ La stringa non è accettata, ma non lo sapremo mai
	+ È possibile riscrivere il macchina in modo da avere solo due casi: termina e non termina
		+ Basta creare uno stato che indica non accettato, e ritornare sempre li in caso di non accettazione
+ Linguaggio
	+ Linguaggio **Accettato**:
		+ $L^{A}(\mathcal{M}) = \{u \in \Sigma^* \; | <\varepsilon, q_0, u> \; \xrightarrow{*} \; <\_, q \in F, \_>\}$
			+ Potrebbe non terminare
	+ Linguaggio **Riconosciuto**:
		+ Se $L^R(\mathcal{M})$ è accettato e se $\forall u \notin L^R \quad <\varepsilon, q_0, u> \; \xrightarrow{*} \; <\_, q \notin F, \_>$ 
			+ Termina sempre
--- 
+ Diciamo che un linguaggio è **ricorsivamente enumerabile** (RE) se il linguaggio è il linguaggio di una qualche macchina di Turing
+ Diciamo che un linguaggio è **ricorsivo** (R) se il linguaggio è il linguaggio di una qualche macchina di Turing che **termina sempre**
	+ Se un linguaggio è R, è anche RE
+ Esiste quindi sempre un algoritmo che riconosce sempre le stringhe per i linguaggi R. È più difficile dirlo per i linguaggi RE
---
+ Lo **stile di programmazione** per queste macchine un **passo in avanti** rispetto agli automi visti in passato, **ma** è comunque **complesso**
	+ Bassissimo livello
	+ Presente l'idea di una memoria estendibile
	+ Si può sia leggere che scrivere
	+ Ci si può spostare liberamente
+ Rispetto a linguaggi più moderni, **manca** solo il concetto di **accesso diretto alla memoria** 