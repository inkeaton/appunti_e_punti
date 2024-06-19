+ Nelle funzioni ad una variabile, ci sono due concetti dalla natura molto simile:

>[!Definizione]
> ### Derivata
> + La derivata di una funzione $f$ viene descritta come il seguente limite:
> 	+ $\exists \lim_{h \to 0} f(x_0 + h) - f(x_0) = f'(x_0)$

>[!Definizione]
> ### Linearizzabilità
> + Una funzione si dice linearizzabile se esistono $a, b \in \mathbb{R}$ tali che valga:
> 	+ $\lim_{x \to x_0} \cfrac{f(x) - \overbrace{(ax + b)}^{\text{polinomio di linearizzazione}}}{x - x_0} = 0$
> 		+ La differenza fra la tangente e la funzione va a 0 più velocemente della differenza fra le loro proiezioni

+ Si può provare che **i due concetti sono equivalenti in una dimensione**
+ Ma questo **non vale in più dimensioni!**
+ Diremo che una funzione è:
	+ **Derivabile** se può essere derivata in tutte le direzioni
	+ **Differenziabile** se esiste il piano tangente (implica derivabilità)
---
+ Esistono due **direzioni "privilegiate"** nel calcolo delle derivate:
	+ Parallelo all'**asse x**
	+ Parallelo all'**asse y**
+ Queste specifiche derivate vengono chiamate **derivate parziali**

>[!Definizione]
> ### Derivate parziali
> + $f$ è derivabile in $p_0 = (x_0, y_0)$ se:
> 	1. La funzione $x \to f(x, y_0)$ è derivabile in $x_0$
> 	2. La funzione $y \to f(x_0, y)$ è derivabile in $y_0$
> + In tal caso, si chiamano **derivate parziali** le seguenti:
> 	+ $\cfrac{d}{dx} f(x, y_0)|_{x = x_0} = \cfrac{\partial f}{\partial x} (x_0, y_0)$
> 	+ $\cfrac{d}{dy} f(x_0, y)|_{y = y_0} = \cfrac{\partial f}{\partial y} (x_0, y_0)$

+ Se $f$ è derivabile in $p_0$, allora
	+ $\cfrac{\partial f}{\partial x}(p_0)$ è la derivata parziale di $f$ rispetto ad $x$ in $p_0$
	+ $\cfrac{\partial f}{\partial y}(p_0)$ è la derivata parziale di $f$ rispetto ad $y$ in $p_0$
+ Esse si mettono insieme nel **gradiente**, il seguente vettore riga:
	+ $\triangledown f(p_0) = \left(\cfrac{\partial f}{\partial x}(p_0), \cfrac{\partial f}{\partial y}(p_0)\right)$ 
+ Possiamo vedere derivate parziali come solite derivate, in cui l'aumento è eseguito solo su una delle due componenti.
+ Possono essere quindi **calcolate** calcolando **una classica derivata**, trattando l'**altra** componente come una **costante**
---
+ $\cfrac{\partial f}{\partial x}(p_0)$ può essere visto come il **coefficiente angolare** della retta tangente alla curva ottenuta intersecando il grafico di $f$ con il piano $y = y_0$. 
+ Questa retta giace sul piano precedente e passa per $(x_0, y_0, f(p_0))$, e ha vettore direzionale $v = (1, 0, \cfrac{\partial f}{\partial x}(p_0))$
+ Analogamente, abbiamo il vettore $v = (0, 1, \cfrac{\partial f}{\partial y}(p_0))$
+ Questi due vettori sono linearmente indipendenti,ed individuano dunque un piano, descritto dalla seguente definizione **parametrica**:
	+ $Q = p_0 + tv + sw$
+ anche scrivibile come:
	+ $x = x_0 + t$
	+ $y = y_0 + s$
	+ $z = f(p_0) + \cfrac{\partial f}{\partial x}(p_0) + \cfrac{\partial f}{\partial y}(p_0)$
+ Questo piano è sicuramente collegato al piano tangente alla funzione in $p_0$, ma non è sicuramente il piano tangente, in quanto esso dipende solo dalle due direzioni delle derivate parziali, non tutte
+ Proviamo a ridefinire il piano attraverso il suo **vettore normale**:
	+ $N = \underbrace{v \wedge w}_{\text{prodotto vettore}} = \left( - \cfrac{\partial f}{\partial x}(p_0), -\cfrac{\partial f}{\partial y}(p_0), 1\right)$
+ Il piano viene quindi ridefinito come l'unione dei punti ortogonali al vettore $N$ (definizione **cartesiana**)
+ Possiamo riscriverlo come:
	+ $Q : \quad z = f(p_0) + \triangledown f(p_0) \cdot (p - p_0)$
---
+ Se esistono le derivate parziali di una funzione, valgono le seguenti equazioni:
	+ $f(x, y_0) = f(p_0) + \cfrac{\partial f}{\partial x}(p_0)(x - x_0) + |x - x_0| \cdot \varepsilon_1(x - x_0)$
	+ $f(x_0, y) = f(p_0) + \cfrac{\partial f}{\partial y}(p_0)(y - y_0) + |y - y_0| \cdot \varepsilon_2(y - y_0)$
+ Queste sono le **linearizzazioni** della funzione lungo gli assi x e y. Se sono vere, si dice che $f$ è **derivabile** in $p_0$ *(da riscrivere come definizione)*
---

>[!Definizione]
> ### Differenziabilità
> + Sia data la funzione $f : A \subseteq \mathbb{R}^2 \to \mathbb{R}$, derivabile su $A$ aperto
> + Essa si dice **differenziabile** in $p_0 = (x_0, y_0) \in A$ se vale la seguente equazione:
> 	+ $f(x, y) = f(p_0) + \triangledown f(p_0) \cdot (p - p_0) + \underbrace{d(p, p_0)}_{\text{distanza}} \cdot \varepsilon(p - p_0)$
> + Diremo inoltre che il **grafico** di $f$ possiede un piano tangente in $(x_0, y_0, f(p_0)$ di equazione:
> 	+ $Q : \quad z = f(p_0) + \triangledown f(p_0) \cdot (p - p_0)$

+ Esiste un **teorema molto più semplice**, per comprendere la differenziabilità di una funzione:

>[!Teorema]
> ### Differenziabilità semplificata
> + Sia data la funzione $f : A \subseteq \mathbb{R}^2 \to \mathbb{R}$
> + Se:
> 	+ $f$ è **derivabile** in $A$
> 	+ Le **derivate** parziali di $f$ sono **continue** in $A$
> 		+ Ovvero, se $f \in C^1(A)$
> + Allora $f$ è **differenziabile** in A

+ Questo è un teorema molto utile