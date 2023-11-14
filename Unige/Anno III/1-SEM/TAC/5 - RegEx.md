+ Le **Espressioni Regolari** (RegEx) sono stringhe, che rappresentano un linguaggio su $\Sigma$, con alfabeto $\Sigma \cup \{\emptyset, \varepsilon, |, *, (, ) \}$ 
+ Essi rappresentano alcuni costrutti equivalenti:
	+ $r \quad \to \quad L(r)$ 
	+ $\emptyset \quad \to \quad \emptyset$ 
	+ $\varepsilon \quad \to \quad \{\varepsilon\}$ 
	+ $\sigma (\in \Sigma) \quad \to \quad \{\sigma\}$ 
	+ $r_1 | r_2 \quad \to \quad L(r_1) \cup L(r_2)$ 
	+ $r_1r_2 \quad \to \quad L(r_1) \cdot L(r_2)$ 
	+ $r^* \quad \to \quad L(r)^*$
+ Valgono le seguenti proprietà:
	+ $r|s = s|r$
	+ $r|(s|t) = (r|s)|t$
	+ $r(st) = (rs)t$
	+ $\emptyset^* = \varepsilon$ 
	+ $r^*(r|s)^* = (r|s)^*$ 
---
+ Esse possono essere trasformate in $\varepsilon$-NFA che riconoscono stringhe appartenenti al loro linguaggio
+ Ogni elemento viene tradotto in un modo specifico
	+ $r \quad \to \quad \boxed{\mathcal{M}(r)}$
	+ $\emptyset \quad \to \quad$ una macchina che rifiuta tutto
	+ $\varepsilon \quad \to \quad$una macchina che accetta solo la stringa vuota
	+ $\sigma \quad \to \quad$ una macchina che accetta solo il simbolo $\sigma$
	+ $r_1|r_2 \quad \to \quad$ una macchina che sceglie se usare $\mathcal{M}(r_1)$ o $\mathcal{M}(r_2)$ 
	+ $r_1r_2 \quad \to \quad$ una macchina che passa prima per  $\mathcal{M}(r_1)$, poi per $\mathcal{M}(r_2)$ 
	+ $r^* \quad \to \quad$ Una macchina che passa più volte in $\mathcal{M} (r)$   
		+ *disegni e dettagli nel cartaceo*