+ Con le nostre nuovo conoscenze sulle serie, possiamo ridefinire il polinomio di Taylor come serie:

>[!Definizione]
> ### Serie di Taylor
> + Sia $I \in \mathbb{R}$ un intervallo aperto, e sia $f$ definita su $I$ e derivabile infinite volte in esso
> + Prendiamo un punto in $I$. Fissato $x \in I$, la serie di potenze:
> 	+ $\sum^{+\infty}_{0} \cfrac{f^{(n)} x_0}{n!}(x - x_0)^n$
> + Viene chiamata la Serie di Taylor di $f$ centrata in $x_0$
> + $f$ viene detta **sviluppabile** in Serie di Taylor se:
> 	+ $f(x) = \sum^{+\infty}_{0} \cfrac{f^{(n)} x_0}{n!}(x - x_0)^n \qquad \forall x \in I$

+ Ricordiamo che, per via dell'**univocità di Taylor,** se una funzione è sviluppabile in una serie di potenze $f(x) = \sum^{+\infty}_{0} a_n(x - x_0)^n$, questa serie è la serie di Taylor

>[!Teorema]
> ### Sviluppabilità
> + Sia $I \in \mathbb{R}$ un intervallo aperto, e sia $f$ definita su $I$ e derivabile infinite volte in esso
> + Se esistono $M, L > 0$ tali che:
> 	+ $|f^{(n)} (x)| \leq ML^n \qquad \forall x \in I, \forall n \in \mathbb{N}$
> + Allora $f$ è sviluppabile in Serie di Taylor  in $I$ $\forall x_0 \in I$
