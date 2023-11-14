## Iniettività, Suriettività, Biettività
---
* $f : A \to \mathbb{R}$ è **iniettiva** se $\forall x, y \in A \quad f(x) \neq f(y)$
* $f : A \to \mathbb{R}$ è **suriettiva** se $\forall y \in \mathbb{R} \quad \exists x \in A \;|\; f(x) = y$
* $f : A \to \mathbb{R}$ è **biettiva** se $\forall y \in \mathbb{R} \quad \exists! x \in A \;|\; f(x) = y$
* Come si traduce ciò graficamente?
	* $f : A \to \mathbb{R}$  è **iniettiva** se dato un $x \in A$, il punto $(x, f(x))$ è l'unico a quella altezza
	* $f : A \to \mathbb{R}$ è **suriettiva** se il suo grafico interseca ogni linea orizzontale
	* $f : A \to \mathbb{R}$ è **biettiva** se valgono entrambe le precedenti

## Operazioni fra Funzioni 
---
* Date $f , g: A \to \mathbb{R}$ *(si possono considerare anche domini discordanti, ma il dominio della funzione risultante sarà l'intersezione delle due)* :
	* $(f+g)(x) = f(x) + g(x)$
	* $(f-g)(x) = f(x) - g(x)$
	* $(f\cdot g)(x) = f(x) \cdot g(x)$
	* $(\frac{f}{g})(x) = \frac{f(x)}{g(x)}, \quad g(x) \neq 0$
	* $(\lambda f)(x) = \lambda \cdot f(x), \quad \lambda \in \mathbb{R}$
* Queste funzioni che abbiamo ottenuto non hanno niente a che fare con le funzioni originali
* Infatti queste non fanno altro che fare operazioni fra i risulati delle due
* Diverso è il caso della prossima operazione: la **COMPOSIZIONE**
	* $f\circ g (x) = f(g(x))$
* Qual'è il dominio di $f \circ g$?
	* $dom(f \circ g) = \{x \in dom(g) \;|\; g(x) \in dom(f)\}$
## Funzione Inversa
---
* Prendendo una funzione $f : A \to \mathbb{R}$ iniettiva possiamo costruirci l'INVERSA
	* Data $y \in Im(f)$ definiamo l'inversa come la funzione $g(y) = x$, unica soluzione di $y = f(x)$
	* Essa viene indicata come $f^{-1}$
* Vale che:
	* $dom(f^{-1}) = Im(f)$
	* $Im(f^{-1}) = dom(f)$ 
	* $f(f^{-1}(y)) = y$
	* $f^{-1}(f(x)) = x$
* Il grafico della funzione inversa è simmerticamente invertito rispetto alla bisettrice del 1° e 3° quadrante