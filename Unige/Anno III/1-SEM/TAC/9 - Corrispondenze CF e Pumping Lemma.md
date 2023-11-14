+ Sappiamo che nei linguaggi regolari esiste una correlazione diretta fra RegEx e DFA
+ Esiste qualcosa di simile fra **Grammatiche CF e PDA**?
	+ Si!
---
+ Dato $L = L(G) \leftrightarrow L = L(\mathcal{M})$ 
+ Dimostriamo:
	1. $L = L(\mathcal{M}) \to$ Possiamo costruire $G$ Grammatica Context-Free tale che $L = L(G)$
		+ Dobbiamo ridurre $\mathcal{M}$ in un automa ad **uno stato**
		+ Esso diventerà
			+ $\mathcal{M} : (\{q\}, \Sigma, \Gamma, Z, \delta)$ 
		+ Dovremo costruire $G$ fatto come:
			+ $G : (\Sigma, \Gamma, Z, \mathcal{P})$ 
		+ In esso, $P$ sarà formato da coppie del genere
			+ $<q, \alpha> \in \delta(q, \sigma, X) \qquad X ::= \sigma \alpha$ 
			+ $<q, \alpha> \in \delta(q, \varepsilon, X) \qquad X ::= X \alpha$
	2. $L = L(G) \to$ Possiamo costruire $\mathcal{M}$ PDA tale che $L = L(\mathcal{M})$ 
		+ Riduciamo la grammatica alla forma normale di **Greibach**
		+ Essa sarà
			+ $G : (\Sigma, \Gamma, Z, \mathcal{P})$ 
		+ In cui tutte le trasformazioni saranno della forma
			+ $X ::= \sigma B_1 \cdots B_n$
		+ Dovremo quindi costruire $\mathcal{M}$ fatto come:
			+ $\mathcal{M} : (\{q\}, \Sigma, \Gamma, Z, \delta)$
		+ In cui, se c'è una produzione $X ::= \sigma B_1 \cdots B_n$ $\in \mathcal{P}$ vale che
			+ $\delta(q, \sigma, X) = (q_1, B_1 \cdots B_n)$ 
+ Possiamo in particolare notare le corrispondenze:
	+ Non terminali $\leftrightarrow$ Simboli pila
	+ Assioma $\leftrightarrow$ Simbolo iniziale pila
	+ Produzioni $\leftrightarrow$ Istruzioni Pila 
---
+ Esiste una versione del **Pumping Lemma** anche per i linguaggi Context Free
	+ Infatti, esistono vari tipi di linguaggi che **non** sono context free, ad esempio i **linguaggi di programmazione**
+ La definizione è la seguente:
	+ $L \text{ CF} \to \exists n \in \mathbb{N} | \forall z \in L, \; |z| \geq n, \; \exists \text{decomp.} \; z = uvwxy | \quad |vwx| \leq n \quad |vx| > 0 \quad \forall i \geq 0 \quad uv^iwx^iy \in L$
	+ A parole, ciò vuol dire che se abbiamo l'automa $\mathcal{M}$ com $n$ stati, se una stringa $z$ è con $|z| \geq n$, la stringa è divisibile in cinque parti, $uvwxy$, in cui $vx$ non è vuota, ed è composta da una ripetizione di simboli del linguaggio. Se ciò è vero, $L(\mathcal{M})$ è un linguaggio context free
		+ È simile a quello usato nei linguaggi regolari. L'idea è sempre che ci deve essere una sezione che si ripete
+ Come la versione regolare, lo usiamo **al contrario**, per dimostrare che un linguaggio non è context free
	+ $L \text{ non CF} \to \forall n \in \mathbb{N} | \exists z \in L, \; |z| \geq n, \; \forall \text{decomp.} \; z = uvwxy | \quad |vwx| \leq n \quad |vx| > 0 \quad \exists i \geq 0 \quad uv^iwx^iy \notin L$
	