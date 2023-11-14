+ Gli automi **$\varepsilon$-NFA** sono una variante degli NFA, i quali permettono di effettuare transizioni dette **silenti**, nelle quali si passa ad un altro stato senza la lettura di alcun simbolo
	+ Queste transizioni vengono denominate con il simbolo $\varepsilon$. Bisogna stare attento a non confonderlo con la stringa vuota $\varepsilon$ 
---
+ Automa
	+ $\mathcal{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Cyan}{F}, \textcolor{Mulberry}{\delta})$ 
+ Funzione di Transizione
	+ $\textcolor{Mulberry}{\delta} : Q \times \Sigma \cup \{\varepsilon\} \to \mathcal{P}(Q)$
+ Configurazioni
	+ $<q, u>$
+ Configurazioni Ferme
	+ $<q, \varepsilon> \wedge \; \delta(q, \varepsilon) = \emptyset$
	+ $<q, \sigma u> \wedge \; \delta(q, \sigma) = \emptyset \; \wedge \; \delta(q, \varepsilon) = \emptyset$
 + Passi
	 + $<q, \sigma u> \;\to \; <q^{'}, u> \; \leftrightarrow \; q^{'} \in \delta(q, \sigma)$    (Caso di **lettura**)
	 + $<q, u> \;\to \; <q^{'}, u> \; \leftrightarrow \; q^{'} \in \delta(q, \varepsilon)$       (Caso **silente**)
+ Riduzione
	+ È non deterministica e **non terminante** (È possibile ritrovarsi in cicli infiniti di transizioni silenti)
+ Chiusura $\hat{\delta}$ 
	+ Viene ridefinita tramite il seguente nuovo concetto
		+ $\textcolor{Apricot}{\varepsilon\text{-closure}} : \quad Q \to \mathcal{P}(Q)$ 
		+ Dato uno stato, vengono restituiti tutti gli stati raggiungibili solo con transizioni **silenti**
	+ $\delta^{*} : Q \times \Sigma^* \to \mathcal{P}(Q)$
		+ $\hat{\delta}(q, \varepsilon) = \varepsilon\text{-closure}(q)$ 
		+ $\hat{\delta}(q, u\sigma) = \bigcup_{q^{'}\in \hat{\delta}(q,u)}\varepsilon\text{-closure}(\hat{\delta}(q^{'}, \sigma))$ 
+ Linguaggio Accettato
	+ $L(\mathcal{M}) = \{u \; | <q_0, u> \; \xrightarrow{*} \; <q_f, \varepsilon>, \; q_f \in F\}$ 
	+ $L(\mathcal{M}) = \{u \; | \; \hat{\delta}(q_0, u) \cap F \neq \emptyset\}$
---
+ È possibile convertire un automa $\mathcal{M}_{\varepsilon}$ in un equivalente $\mathcal{M}_{\varepsilon}$ 
	+ $\mathcal{M}_{\varepsilon} = (Q_N, \Sigma, q_0, \delta_{\varepsilon}, F_{\varepsilon})$ 
	+ $\mathcal{M}_N = (Q_N, \Sigma, q_0, \delta_N, F_N)$ 
		+ $F_N = F_{\varepsilon}\;[ \cup {q_0} \leftrightarrow q_0 \xrightarrow{\varepsilon^{*}}q_f \in F ]$ 
		+ $\delta_N = \begin{dcases}\text{transizioni non silenti in } \delta_{\varepsilon} \\ q \xrightarrow{\sigma N} q^{'} \leftrightarrow q \xrightarrow{\varepsilon^{*} \sigma \varepsilon^{*}} q^{'}\end{dcases}$
+ In linguaggio naturale:
	1. Manteniamo $F_\varepsilon \to F_N$, aggiungendo $q_0$ se e solo se possiede percorsi in $q_f \in F_N$ tramite transizioni silenti
	2. Tutte le transizioni non silenti vengono mantenute
	3. Le transizioni silenti vengono aggiunte se e solo se esiste un percorso che le contiene, oltre a transizioni non silenti
	4. Alla fine dello schema, si potrebbero rimuovere gli eventuali stati superflui (non raggiungibili)