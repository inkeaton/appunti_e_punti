* Iniziamo definendo lo __spazio campionario__ $S$ come il "mondo" in cui possono avvenire degli __eventi__ $E$. Possiamo immaginare entrambi come __insiemi__, con $E \subset S$ 
* Chiamiamo $P(E)$ la __probabilità__ dell'evento $E$
* Definiamo tre __assiomi__ da cui costruire un sistema:
	1. $P(S) = 1$ 
	2. $\forall E \subset S \; \; 0 \leq P(E) < 1$ 
	3. $E_1,E_2 \subset S, \; E_1E_2 = \emptyset \; \to \; P(E_1 \cup E_2) = P(E_1) + P(E_2)$ 
* Da essi possiamo ricavare le seguenti __proprietà__: 
	* $P(\emptyset) = 0$ 
	* $P(E^C) = 1 - P(E)$ 
	* $E \subseteq F \to P(E) \leq P(F)$ 
	* $EF \neq \emptyset \to P(E \cup F) = P(E) + P(F) - P(EF)$ 
---
* Dato uno spazio campionario, si dice che gli eventi che lo compongono sono __equiprobabili__ nel caso in cui tutti essi abbiano la __stessa__ probabilità di avvenire. In tal caso il __calcolo__ della probabilità può essere __semplificato__ alla formula $P(E) = \frac{\#E}{\#S}$ 