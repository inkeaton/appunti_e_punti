* Un __Vettore__ in $K^n$ è semplicemente una matrice colonna (o riga) in $M_{n1}(K)$ 
* Un vettore possiede:
	* __Lunghezza__: $\overline{OP} = \sqrt{x^2+y^2} = ||v||$  
	* __Direzione__: Parte per cui passa
	* __Verso__: da dove verso dove
---	
* La __Somma__ fra due vettori corrisponde alla __somma matriciale__. Graficamente, si usa la __regola del parallelogramma__
	* Dati due vettori, $||v + w|| \le ||v|| + ||w||$ 
* La __Moltiplicazione__ per un $t \in \mathbb{R}$ è anch'essa simile a quella matriciale. Graficamente, corrisponde ad una contrazione, o dilatazione
---
* Il __Prodotto Scalare__ corrisponde a $v \cdot w = x_vx_w + y_vy_w$ e corrisponde al prodotto riga per colonna $v^T \cdot w$. Viene rappresentato anche come $\langle v, w \rangle$ 
	* Per comprenderlo __geometricamente__, dobbiamo riscrivere i vettori in funzione di $\theta$, l'angolo che ognuno di essi forma con il piano: $v = \begin{pmatrix} ||v|| \cos \theta \\ ||v|| \sin \theta \end{pmatrix}$ 
	* $v \cdot w = ||v|| ||w|| \cos( \theta_w - \theta_v)$ 
* L'__angolo__ formatosi __fra__ i due __vettori__ verrà denominato $\widehat{vw}$ 
	* $v · w = 0 \leftrightarrow v ⊥ w$
	* $v · w > 0 \leftrightarrow θ < \frac{\pi}{2}$ 
	* $v · w < 0 \leftrightarrow θ > \frac{\pi}{2}$ 
---
* La __Proiezione Ortogonale__ di un vettore $v$ su uno $w$ corrisponde a: $p = \frac{v\cdot w}{||w||} \frac{w}{||w||}$ e consiste in una __contrazione__ del vettore $w$
---
* Tutto quello che abbiamo detto può essere __esteso__ a $K^n$, od in altri termini, __vettori__ con __più dimensioni__
* Questi sono __Spazi Vettoriali__, definiti come insiemi $V$ con due operazioni ( + e $\cdot$ ), in cui:
	* (V, +) è un gruppo commutativo.
	* $λ · (v + w) = λ · v + λ · w$ per ogni $λ ∈ K, v,w ∈ V.$
	* $(γ + λ) · v = γ · v + λ · v$ per ogni $γ, λ ∈ K, v ∈ V$.
	* $1 · v = v$ per ogni $v ∈ V$.
	* $(γλ) · v = γ · (λ · v)$ per ogni $γ, λ ∈ K, v ∈ V$.
* Le __operazioni__ diventano:
	* Somma: $v + w = \begin{pmatrix} x_1 + y_1 \\ \vdots \\ x_n + y_n \end{pmatrix}$ 
	* Moltiplicazione: $\lambda v = \begin{pmatrix} \lambda x_1 \\ \vdots \\ \lambda x_n \end{pmatrix}$ 
	* Lunghezza: $||v|| = \sqrt{x_1^2 + \cdots + x_n^2}$ 
	* Prodotto Scalare: $v \cdot w = x_1y_1 + x_2y_2 + \cdots + x_ny_n$ 
	* Proiezione Ortogonale: $p = \frac{v\cdot w}{||w||^2}w$ 
---
* Considerando $K^3$, possiamo calcolare il __Prodotto Vettoriale__, da non confondere con quello scalare, il quale si scrive come: $v \wedge w = \begin{pmatrix} \begin{vmatrix} x_2 && y_2 \\ x_3 && y_3 \end{vmatrix} \\ - \begin{vmatrix} x_1&& y_1 \\ x_3 && y_3 \end{vmatrix} \\ \begin{vmatrix} x_1 && y_1 \\ x_2 && y_2 \end{vmatrix} \end{pmatrix}$ 
* Dati due vettori, si ha che $v \perp (v \wedge w) \quad w \perp (v \wedge w)$ 
* Si può provare che $||v ∧ w|| = ||v|| ||w|| \sin \widehat{vw}$ 
	* Questo può essere usato per calcolare l'__area__ di un triangolo in 2 dimensioni, con la formula $A = \frac{||v \wedge w ||}{2}$ 
---
* La __Combinazione Lineare__ di $r$ vettori in $K^n$ a coefficienti $\lambda_1, \cdots, \lambda_r$ è uguale a $\lambda_1v_1 + \lambda_2v_2 + \cdots + \lambda_rv_r$ 
* L'insieme delle possibili combinazioni lineari di più vettori viene chiamato __Spazio Vettoriale__, e scritto come $\langle v_1, \cdots, v_r \rangle$ 
* Diciamo che dei vettori sono __Linearmente Dipendenti__, se esistono $\lambda_1, \cdots, \lambda_r$ non tutti nulli tali che la loro __combinazione__ lineare è __uguale a 0__. Se ciò __non__ avviene, essi sono __Linearmente Indipendenti__
	* Per trovare questi valori, posso impostare un sistema lineare in funzione delle lambda, e risolvere
---
* Diciamo che $v_1, \cdots, v_r$ sono una __Base__ di $\langle v_1, \cdots, v_r \rangle$ se sono linearmente __indipendenti__
* Le __Basi Canoniche__ sono insiemi di vettori che sono basi di vari spazi vettoriali
* Si può notare che __due__ vettori sono linearmente __dipendenti__ solo se __proporzionali__
* In generale, Sono __indipendenti__ se la __matrice__ formata dai __vettori__ ha rango $r$ 
* Se il rango è superiore a __n__ , sono __dipendenti__
* Se il __determinante__ è diverso da 0, sono __indipendenti__
* $w ∈ \langle v_1, \cdots , v_r \rangle$ se e solo se $rk(A) = rk(A | B)$ sarebbe moltiplicare per un coeciente una riga della matrice e sommarla o