+ Siamo arrivati quindi al punto di essere in grado di trasformare espressioni regolari direttamente in DFA
	+ $RegEX \to \varepsilon - NFA \to NFA \to DFA$ 
+ Tutti questi tipi di automi sono quindi in grado di riconoscere linguaggi **regolari**
+ Esiste un ulteriore trasformazione però: Quella in **automa deterministico minimizzato**
	+ $DFA \to \textcolor{Apricot}{mDFA} \quad | \quad L(\mathcal{M}) = L(\mathcal{M^m} \wedge \nexists \mathcal{M'} | L(\mathcal{M'}) = L(\mathcal{M}) \wedge |Q'| < |Q^m|$  
+ Questo automa rimuove passaggi complessi o non necessari dal DFA originario
+ L'algoritmo è il seguente:
	1. Innanzitutto rimuoviamo gli stati non raggiungibili da $q_0$ 
	2. Suddividiamo gli stati rimanenti in classi d'equivalenza, fatte in modo che, per ogni stringa, gli elementi di quella classe vanno tutti nella stessa classe
	3. Partiamo dividendoli in stati finali e non finali
	4. Osserviamo in che classi si muovono e, passaggio per passaggio, li dividiamo in sotto-classi
	5. Alla fine, otterremo un determinato numero di sotto-classi. Ognuna di esse sarà uno stato del nostro nuovo automa
		+ *pseudo-codice in cartaceo*
---
+ È possibile dimostrare che, **componendo linguaggi regolari**, si **ottengono** sempre **linguaggi regolari**
	+ $L_1 \cup L_2 \quad \to \quad$ regolare, in quanto ognuno dei due avrà un espressione regolare, e la loro unione è un espressione regolare, che rappresenta un linguaggio regolare
	+ $L_1 \cdot L_2 \quad \to \quad$ regolare, dimostrabile come nel precedente
	+ $L^* \quad \to \quad$ regolare, dimostrabile come nel precedente
	+ $\bar{L} \quad \to \quad$ regolare, basta invertire gli stati finali e non finali
	+ $L_1 \cap L_2 \quad \to \quad$ regolare, in quanto equivalente a $\bar{\bar{L_1} \cup \bar{L_2}}$ 
+ Ma in generale, come facciamo a **dimostrare** che un linguaggio generico è **regolare**?
	+ Basta dimostrare che esiste un DFA in grado di riconoscerlo
+ E per dimostrare il **contrario**?
	+ Questo è ben più complesso, avremo bisogno di usare un determinato **lemma**
+ L'idea è la seguente
	+ Se un DFA ha $s$ stati, è sicuramente in grado di riconoscere stringhe lunghe $s$
	+ Se una stringa $z$ ha $|z| > s$, affinché debba essere riconosciuta, ci deve essere una qual sorta di loop all'interno dell'automa, ed almeno uno stato sarà ripetuto
+ Questo ci porta alla definizione del **Pumping Lemma**:
	+ $L \text{ Regolare} \to \exists n \geq 0 | \forall z \in L, \; |z| \geq n, \; \exists \text{decomp.} \; z = uvw | \quad |uv| \leq n \quad |v| > 0 \quad \forall i \geq 0 \quad uv^iw \in L$
	+ A parole, ciò vuol dire che se abbiamo l'automa $\mathcal{M}$ com $n$ stati, se una stringa $z$ è con $|z| \geq n$, la stringa è divisibile in tre parti, $uvw$, in cui $v$ non è vuota, ed è composta da una ripetizione di simboli del linguaggio. Se ciò è vero, $L(\mathcal{M})$ è un linguaggio regolare
+ Possiamo usare questo lemma per dimostrare che un linguaggio non è regolare: basta che non lo rispetti
	+ Un esempio è il linguaggio $L = \{a^nb^n | n \geq 0\}$ 
+ Dobbiamo quindi dimostrare il **contrario**:
	+ $L \text{ non Regolare} \to \forall n \geq 0 | \exists z \in L, \; |z| \geq n, \; \forall \text{decomp.} \; z = uvw | \quad |uv| \leq n \quad |v| > 0 \quad \exists i \geq 0 \quad uv^iw \notin L$