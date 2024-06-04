+ Il concetto di serie numerica è facilmente estendibile a quello di serie di funzioni:

>[!Definizione]
>### Serie di Funzioni
> + Sia dato un insieme di funzioni $f_n : I \to \mathbb{R}, \quad n \geq 1, \quad I \subseteq \mathbb{R}$.
> + Diremo che la serie $\sum^{\infty}_{n = 1} f_n$:
> 	+ **Converge puntualmente** sull'intervallo $J \subseteq I$ se essa converge $\forall x \in J$ . In tal caso, la funzione $f : J \to \mathbb{R}$ definita come $f(x) = \sum^{\infty}_{n = 1} f_n(x)$ viene chiamata **somma della serie**
> 	+ **Converge assolutamente** sull'intervallo $J \subseteq I$ se $\sum^{\infty}_{n = 1} |f_n(x)|$ converge $\forall x \in J$ 

+ Uno dei primi teoremi utili per comprendere il comportamento di queste serie è il seguente:

>[!Proposizione]
>### Criterio di Weierstrass
> + Se la serie a **termini positivi** $\sum a_n$, dove $a_n = \sup_{x \in I} |f_n(x)|$, converge, ossia se $\sum^{\infty}_{n=1} (\sup_{x \in I} |f_n(x)|) < + \infty$, allora la serie $\sum^{\infty}_{n=1} f_n$ di $f_n : I \to \mathbb{R}$ converge **assolutamente** su $I$

+ Valgono le seguenti osservazioni:

>[!Osservazione]
>### Su Weierstrass
> 1. Se vale la convergenza di Weierstrass, si dice che la serie converge **totalmente**
> 2. Per dimostrare che la convergenza esiste, basta dimostrare che $|f_n(x)| < c_n, \quad \forall x \in I$, dove $c_n$ è una successione positiva convergente

+ Quest'ultimo è un ragionamento intuitivo, che potrebbe ricordarci del criterio del confronto delle serie numeriche
+ Possiamo inoltre trarre i seguenti corollari:

>[!Corollario]
> ### Continuità della Somma
> + Siano $f_n : I \to \mathbb{R}$. Se valgono i seguenti:
> 	1. Tutte le $f_n$ sono continue su $I$
> 	2. La serie $\sum^{\infty}_{n=1} f_n$ converge **totalmente** a $f$
> +  Allora $f$ è **continua** su $I$

+ La continuità è una proprietà detta **puntuale**. Somme di oggetti che l'hanno, l'avranno

>[!Corollario]
> ### Integrazione Termine a Termine
> + Siano $f_n : I \to \mathbb{R}$. Se valgono i seguenti:
> 	1. Tutte le $f_n$ sono continue su $[a, b]$
> 	2. La serie $\sum^{\infty}_{n=1} f_n$ converge **totalmente** in $[a,b]$a $f$
> +  Allora $f$ è **integrabile** su $[a, b]$, ed esiste $\int^{b}_{a} f(x) dx = \sum^{\infty}_{n=1} \int^{b}_{a} f_n(x) dx$ 
> + L'integrale della somma è uguale alla somma degli integrali

>[!Corollario]
> ### Derivazione Termine a Termine
> + Siano $f_n : I \to \mathbb{R}$. Se valgono i seguenti:
> 	1. Tutte le $f_n$sono derivabili in $I$, e tutte le derivate $f'_n$ sono continue su $I$
> 	2. La serie $\sum^{\infty}_{n=1} f_n$ converge **puntualmente** a $f$ su $I$
> 	3. La serie $\sum^{\infty}_{n=1} f'_n$ converge **totalmente** su $I$
> +  Allora $f$ è **derivabile** su $I$ e si ha. $f'(x) = \sum^{\infty}_{n=1} f'_n(x)$
> + La derivata della somma è uguale alla somma delle derivate

+ Un osservazione simile esiste anche per i **limiti**
---
>[!Osservazione]
> + Se $f$ converge totalmente su $[a, b]$, allora $f$ è continua su $\mathbb{R}$

+ Un altro tipo di convergenza che non vedremo è la convergenza **uniforme**. Essa viene implicata dalla totale, ed implica l'assoluta
	+ Totale $\to$ Uniforme $\to$ Assoluta $\to$ Puntuale

>[!Corollario]
> + Siano $f_n : [a, b] \to \mathbb{R}$ continue. Supponiamo che $\sum f_n$ converga totalmente su $(a, b)$. Allora la somma converge anche in $[a, b]$, e la somma è continua in $[a, b]$
