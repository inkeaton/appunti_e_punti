## Teorema del Confronto
* Siano $f$, $g$ ed $h$ tre funzioni, e $x_0$ un punto d'accumulazione per i domini delle tre funzioni
* Supponiamo che $\forall x$ "vicino" a $x_0$ vale che $g(x) \geq f(x) \geq h(x)$ e che $\lim_{x\to x_0}{g(x)} = \lim_{x\to x_0}{h(x)} = j \in \mathbb{R}$ 
* Questo vuol dire che $\lim_{x\to x_0}{f(x)} = j$ 
### Corollario
* Prendiamo $|f(x)| \leq M \quad \forall x$ (funzione limitata) e $\lim_{x\to x_0}{g(x)} = 0$ (infinitesimo)
* Allora $\lim_{x\to x_0}{f(x) \cdot g(x)} = 0$ 

## Teorema della Permanenza del Segno
* $\lim_{x \to x_0} f(x) = l \in \mathbb{R} \cup \{\pm \infty\}$ 
	1. Se $l > 0$ oppure $l  = + \infty$, allora esiste un intorno $I$ di $x_0$ tale che $f(x)> 0 \quad \forall x \in I \cap Dom(f), \; x \neq x_0$ 
	2. Se $f(x) \geq 0$ in un intorno $I$ di $x_0$, $x \neq x_0$ allora $l \geq 0$ oppure $l = + \infty$ 
### Corollario 
* $\exists$ intorno $I$ di $x_0$ , $\exists$ $M > 0 \; | \; |f(x)| \leq M \quad x \in I, \; x \neq x_0$. Inoltre, $\lim_{x\to x_0}{g(x)} = 0$ 
* Allora $\lim_{x \to x_0}{f(x) \cdot g(x)} = 0$ 