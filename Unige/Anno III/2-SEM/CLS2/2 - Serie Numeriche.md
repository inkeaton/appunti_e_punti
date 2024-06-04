+ Similmente alle approssimazioni di funzioni, anche le serie numeriche sono **sommatorie di numeri infiniti**
+ Vogliamo essere in grado di capire se questi valori esistono, non esistono, o sono infiniti

> [!Definizione]
>  ### Comportamento delle Successioni Numeriche
>   + Data la successione  $(a_n)$, con $n \geq 1$, si dice che la serie $\sum^{\infty}_{n = 1} a_n$:
> 	  + **Converge** al numero $\delta \in \mathbb{R}$ se esiste il limite finito $\lim_{N \to \infty} (a_1 + a_2 + \cdots + a_N) = \delta$. In questo caso, $\delta$ viene chiamata la **somma della serie**
> 	  + **Diverge** se $\lim_{N \to \infty} (a_1 + a_2 + \cdots + a_N) = \pm \infty$
> 	  + **È indeterminato** se $\nexists \lim_{N \to \infty} (a_1 + a_2 + \cdots + a_N)$

 + $a_n$ viene chiamato **termine generale della serie**.
 + $\delta_n = \sum^{n}_{k = 1} a_k$ viene chiamata **somma parziale n-esima**
---
+ Vediamo alcune serie, ed il loro comportamento:
#### Serie Geometrica
+ La serie geometrica di ragione $q \in \mathbb{R}$ viene indicata come:
	+ $\sum^{+ \infty}_{n = 1} q^n$
+ Essa:
	+ **Converge** per $|q| < 1$
	+ **Diverge** a $+ \infty$ per $q \geq 1$ 
	+ **È indeterminata** per $q \leq -1$ 
+ Infatti, tramite un semplice prodotto, troviamo che:
	+ $\sum^{+ \infty}_{n = 1} q^n = \cfrac{q - q^{n+1}}{1 - q}$
+ Si può quindi anche calcolare:
	+ Dato $|q| < 1$
	+ $\sum^{+ \infty}_{n = 0} q^n = 1 + \cfrac{q}{1 - q} = \cfrac{1}{1-q}$
		+ Questo è uno dei risultati più importanti del mondo della matematica
#### Serie Armonica Generalizzata 
+ La serie armonica viene indicata come:
	+ $\sum^{+ \infty}_{n = 1} \cfrac{1}{n^\alpha} \quad \alpha > 0$
+ Essa:
	+ **Converge** per $\alpha > 1$
	+ **Diverge**  per $\alpha \leq 1$ 
+ Provare la convergenza e divergenza di questa funzione è un poco più complesso, lo vedremo in seguito

>[!Concetto]
> ### Indipendenza del Carattere
> + Il carattere della serie $\sum^{\infty}_{n = n_0} a_n$ non dipende da $n_0$


