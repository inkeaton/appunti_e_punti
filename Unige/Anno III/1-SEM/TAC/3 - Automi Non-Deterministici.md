+ Una automa a stati finiti **non deterministico** (NFA) è in parte simile alla sua controparte deterministica
	+ $\mathbb{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Cyan}{F}, \textcolor{Mulberry}{\delta})$ 
	+ $\textcolor{Mulberry}{\delta} : Q \times \Sigma \to \underbrace{\mathcal{P}(Q)}_{\text{insieme delle parti}}$
+ La differenza sta nella sua funzione di transizione, la quale può ritornare **più stati**
+ Se la computazione di un DFA poteva essere vista come una sequenza finita di stati, quella di un NFA può essere vista come un **albero finito**
+ Esso può fermarsi anche prima di aver finito di leggere la stringa
---
+ Le configurazioni **ferme** sono del tipo:
	+ $< q, \varepsilon>$
	+ $< q, \sigma u>, \quad \delta(q, \sigma) = \emptyset$  
+ Il **linguaggio riconosciuto**:
	+ $L(M) = \{u \; | <q_0, u> \; \xrightarrow{*} \; <q_f, \varepsilon>, \; q_f \in F\}$ 
		+ *È virtualmente uguale ad un DFA, ma adesso indica "se esiste una computazione accettabile"*
+ Viene anche ridefinita $\delta^*$ 
	+ $\delta^{*} : Q \times \Sigma^* \to \mathcal{P}(Q)$
	+ $\delta^{*}(q, \varepsilon) = \{q\}$ 
	+ $\delta^{*}(q, u \sigma) = \bigcup_{q' \in \delta^{*}(q, u)} \delta^* (q, \sigma)$ 
+ Ridefiniamo il linguaggio come:
	+ $L(\mathcal{M}) = \{u \; | \; \delta^{*}(q_0, u) \cap F \neq \emptyset\}$ 
---
+ Questi automi ci permettono di riconoscere linguaggi più complessi di quelli deterministici? **NO**
+ Ci permettono però di programmare in modo più semplice. Infatti, gli NFA sono traducibili in DFA; con un semplice algoritmo.
#### Teorema di Robin-Scott
+ Dato $\mathcal{M}_N = (Q_N, \Sigma, q_0, \delta_N, F_N)$ 
+ $\exists \mathcal{M}_D \; | \; L(\mathcal{M}_D) = L(\mathcal{M}_N)$ 
	+  $\mathcal{M}_D = (\mathcal{P}(Q_N), \Sigma, \{q_0\}, \delta_D, F_D)$
	+ $q_D \in F_D \leftrightarrow q_D \cap F_N \neq \emptyset$ 
	+ $\delta_D \; : \; \mathcal{P}(Q_N) \times \Sigma \to \mathcal{P}(Q_N)$ 
	+ $\delta_D(q_D, \sigma) \; = \; \bigcup_{q_N \in q_D} \delta_N(q_N, \sigma)$  

+ *Negli appunti cartacei, dimostrazione che $L(\mathcal{M}_N) = L(\mathcal{M}_D)$* 