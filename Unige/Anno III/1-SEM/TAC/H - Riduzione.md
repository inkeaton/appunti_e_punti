+ Abbiamo visto che capire se un insieme è ricorsivo o R.E. è relativamente complesso 
+ Fortunatamente esistono vari metodi per dimostrarlo. Uno è quello della **riduzione**
+ Esso è simile a quello di riduzione polinomiale visto ad APA
	+ Dati $A, B \in \mathbb{N}$, si dice che $A \leq B$ se e solo se $\exists f : \mathbb{N} \to \mathbb{N}$ ricorsiva totale tale che $x \in A \leftrightarrow f(x) \in B$ 
+ Si dice che $A$ viene **ridotto** a $B$ 
+ Questo per noi è molto importante, in quanto i due insiemi sono collegati:
	+ $B$ ricorsivo $\to$ $A$ ricorsivo
	+ $A$ non ricorsivo $\to$ $B$ non ricorsivo
	+ $B$ ricorsivamente enumerabile $\to$ $A$ ricorsivamente enumerabile
	+ $A$ non ricorsivamente enumerabile $\to$ $B$ non ricorsivamente enumerabile
+ Possiamo quindi **sfruttare** l'idea per dimostrare la ricorsività o non ricorsività di un insieme
+ 5/12/23