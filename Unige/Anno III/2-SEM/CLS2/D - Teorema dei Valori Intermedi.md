+ Vediamo un ulteriore proprietà di alcuni insiemi continui:

>[!Definizione]
> ###  Connesso per archi
> + Un sotto-insieme $C \subseteq \mathbb{R}^n$ si dice connesso per archi se $\forall p_0, p_1 \in C$ esiste una **curva**, cioè una funzione continua $\gamma : [0, 1] \to C$ tale che $\gamma(0) = p_0, \; \gamma(1) = p_1$
> 	+  L'idea è che esiste una "linea" all'interno dell'insieme che collega i due punti
> 	+ Se $n=1$, $C$ è connesso se e solo se $C$ è un **intervallo**

+ Un insieme può essere:
	+ Connesso per archi
	+ Stellato
	+ Convesso
+ Sono in ordine di potenza (Il secondo implica il primo, ma non viceversa)

>[!Osservazione]
> ###  Tipi di archi connessi
> + Se $A$ è connesso per archi e $\gamma : A \to C$ è continua, allora $f(A)$ è di uno dei seguenti tipi:
> 	+ $[\inf f(A), \sup f(A)]$
> 	+ $(\inf f(A), \sup f(A)]$
> 	+ $[\inf f(A), \sup f(A))$
> 	+ $(\inf f(A), \sup f(A))$
> 	+ $(-\infty, \sup f(A)]$
> 	+ $(-\infty, \sup f(A))$
> 	+ $[\inf f(A), + \infty)$
> 	+ $(\inf f(A), + \infty)$
> 	+ $(- \infty, + \infty)$

---
+ Nelle funzioni ad **una** variabile, esiste il **teorema dei valori intermedi**, che dice che, una funzione continua in un intervallo $I$ assume tutti i valori all'interno di uno specifico intervallo di $y$
+ Nelle funzioni multidimensionali, viene ridefinito in questo modo:

>[!Teorema]
> ### Teorema di Valori Intermedi
> + Sia $A \in \mathbb{R}^n$ connesso per archi, e $f : A \to \mathbb{R}$ funzione continua
> + Allora, per ogni $C \in (\inf f(a), \sup f(a))$ esiste $P \in A | f(p) = C$
> 	+ Presi due punti fra $\inf$ e $\sup$, tutti i **valori intermedi** vengono assunti da $f$

+ ***riorganizzare l'ordine fra questa nota e quella precedente***