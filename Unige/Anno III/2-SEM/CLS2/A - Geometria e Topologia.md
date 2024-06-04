+ Uno **spazio vettoriale euclideo** è un insieme definito come:
	+ $\mathbb{R}^n = \{(x_1, \cdots, x_n) | x_j \in \mathbb{R}\}$
+ Con la particolarità di possedere un **prodotto scalare** fra i vettori in esso contenuto
+ Analizzando lo spazio $\mathbb{R}^2$, possiamo vedere che i vettori in esso contenuto possiedono le seguenti operazioni e proprietà:
	+ **Somma**
		+ $v1 + v2$
	+ **Moltiplicazione scalare**
		+ $\lambda v \qquad \forall \lambda \in \mathbb{R}$
	+ **Norma**
		+ $|| v || = \sqrt{x^2 + y^2}$
		+ Può esser vista come la lunghezza del vettore
		+ $||v|| > 0$
		+ $||v|| = 0 \leftrightarrow v = (0, 0)$
		+ $||\lambda v|| = |\lambda | ||v||$
		+ $| ||v|| - ||w|| | \leq ||v + w|| \leq ||w|| + ||w ||$ (Disuguaglianza Triangolare)
		+ $|x|, \; |y| \leq ||v||$
	+ **Prodotto Scalare**
		+ $v_1 \cdot w_2 = x_1x_2 + y_1y_2$
		+ Può esser visto come la proiezione reciproca dei vettori fra loro
		+ Possiede le proprietà:
			+ Transitiva
			+ Associativa con la somma
			+ Associativa con la moltiplicazione
			+ Disuguaglianza di Schwartz $|v \cdot w| \leq ||v || ||w||$
+ Uno spazio dotato sia di **norma** che di **prodotto scalare** viene detto **spazio normato**
+ Il **versore** di un vettore è la sua versione normalizzata:
	+ $\hat{w} = \cfrac{w}{||w||}$
+ Un vettore è **scomponibile** in componenti ortogonali (*dettagli nel cartaceo*)
---
+ Cominciamo a parlare di **topologia**

>[!Definizione]
> ### Palla Aperta
> + Sia $P_0 \in \mathbb{R}^n$ e $R > 0$
> + La palla aperta di centro $P_0$ e raggio $R$ è:
> 	+ $B_R(P_0) = \{ P \in \mathbb{R}^n : d(P, P_0) < R \}$
> + Dove $d(P, P_0) = || P -P_0||$, la distanza fra gli elementi
> + È quindi un insieme di punti sferico, con bordo escluso

+ La distanza utilizzata possiede le seguenti proprietà:

>[!Osservazione]
> ### Distanza
> + $d(P, P_0) = || P -P_0||$ rispetta le seguenti proprietà:
> 	+ $d(P, P_0) \geq 0$
> 	+ $d(P, P_0) = 0 \leftrightarrow P=P_0$
> 	+ $d(P, P_0) = d(P_0, P)$
> 	+ $d(P, Q) = d(P, S) + d(S, Q)$

+ Uno spazio in cui vengono rispettate queste proprietà viene detto **metrico**
+ Il valore stesso della distanza può venir calcolato in maniera diversa in base al metodo utilizzato. 
+ Normalmente intendiamo la **distanza euclidea** $d_2(P, P_0) = || P - P_0||$. 
+ Possiamo generare diversi tipi di distanze sostituendo $p \geq 1$ nella seguente formula:
	+ $d_p(P_1, P_2) = (|x_1 - x_2|^p+|y_1 - y_2|^p)^{- \frac{1}{p}}$

---

>[!Definizione]
> ### Punti negli insiemi
> + Sia $A \subseteq \mathbb{R}^n, P_0 \in \mathbb{R}^n$
> + Il punto $P_0$ viene detto:
> 	+ **Interno** ad $A$ se esiste $\delta > 0 | B_{\delta} P_0 \subset A$
> 		+ L'insieme dei punti interni si chiama **Interno** di $A$, $A°$
> 		+ È l'insieme dei punti all'interno della figura
> 	+ **Aderente** ad $A$ se  $\forall \delta > 0 | B_{\delta} P_0 \cap A \neq \emptyset$
> 		+ L'insieme dei punti aderenti si chiama **Chiusura** di $A$, $\overline{A}$
> 		+ È l'insieme dei punti della figura e del bordo
> 	+ **di Frontiera** $\forall \delta > 0 | B_{\delta} P_0 \cap A \neq \emptyset  \wedge B_{\delta} P_0 \cap A^C \neq \emptyset$
> 		+ L'insieme dei punti di frontiera si chiama **Frontiera** di $A$, $\partial A$
> 		+ È l'insieme dei punti del bordo

+ Valgono le seguenti proprietà:

>[!Proposizione]
> ### Proprietà parti dell'insieme
> + Sia $A \subseteq \mathbb{R}^n$
> + Valgono le seguenti proprietà:
> 	+ $A° \subseteq A \subseteq \overline{A}$
> 	+ $\overline{A} = A° \cup \partial A$
> 	+ $A° = A \setminus \partial A$

>[!Definizione]
> ### Tipi di Insiemi
> + Sia $A \subseteq \mathbb{R}^n$
> + Diciamo che:
> 	+ $A$ è **aperto** se $A = A°$
> 		+ $A \text{ aperto } \leftrightarrow A \cap \partial A = \emptyset$ 
> 	+ $A$ è **chiuso** se $A = \overline{A}$
> 		+ $A \text{ chiuso } \leftrightarrow \partial A \subseteq A$ 
> 	+ $A$ è **limitato** se $\exists P_0, \; R > 0 | A \subseteq B_R P_0$
> 		+ $A \text{ limitato } \leftrightarrow \sup_{p \in A} ||p|| < \infty$ 

+ Esistono due soli insiemi sia aperti che chiusi: $\emptyset$ e $\mathbb{R}$
