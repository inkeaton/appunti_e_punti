+ Le serie di potenze non sono altro che la versione analitica dei polinomi, dove calcoliamo il limite del grado del polinomio ad infinito

>[!Definizione]
> ### Serie di Potenze
> + Dati  $(a_n)_{n \geq 0}$, $a_n \in \mathbb{R}$
> 	+ $\sum^{+\infty}_{\infty} a_n x^n$ è una serie di potenze centrata in 0
> 	+ $\sum^{+\infty}_{\infty} a_n (x - x_0)^n$ è una serie di potenze centrata in $x_0$

+ Le serie di potenze sono localmente eccellenti, ovvero sono molto efficaci in uno specifico intervallo. Il seguente teorema esplica questa proprietà:

>[!Teorema]
> ### "Sbarre Rosse"
> + Data la serie di potenze $\sum^{+\infty}_{\infty} a_n x^n$ esiste un $\rho \in [0, + \infty) \cup \{ \infty \}$ detto **raggio di convergenza**, tale che:
> 	1. Se $\rho = 0$, la serie converge solo in 0
> 	2. Se $0 < \rho < + \infty$, la serie converge **assolutamente** in  $(-\rho, \rho)$ e **totalmente** in $[-R, R]$ per ogni $R \in (0, \rho)$ e non converge in $(- \infty, - \rho) \cup (\rho, +\infty)$
> 	3. Se $\rho = + \infty$, la serie converge assolutamente in $\mathbb{R}$ e totalmente in ogni $[-R, R]$

+ Notiamo che non sappiamo come la funzione si comporti in $\pm \rho$
+ Questo teorema deriva dal seguente lemma:

>[!Lemma]
> + Se la serie di potenze $\sum^{+\infty}_{\infty} a_n x^n$ converge in $y \in \mathbb{R} \setminus \{ 0 \}$, allora c'è convergenza **totale** in $[-R, R] \quad \forall R \in (0, |y|)$ 

+ Questo comportamento delle serie di potenze può essere fatto risalire a quello della serie **geometrica**
---
+ Questa teorema ci aiuta notevolmente nel comprendere dove la serie converga, ma dobbiamo sapere quale sia il valore di $\rho$
+ I seguenti corollari ci danno dei modi per trovarlo:

>[!Corollario]
> ### $\rho$ tramite il Criterio del Rapporto
> + Supponiamo che $a_n \neq 0 \quad \forall n \in \mathbb{R}$
> + Se $\exists \lim_{x \to \infty} \frac{|a_{n+1}|}{|a_n|} = l \in [0, +\infty) \cup \{ + \infty\}$ vale:
> 	+ $\rho = \begin{cases} + \infty & l=0 \\ \frac{1}{l} & 0 < l < + \infty \\ 0 & l = + \infty   \end{cases}$

>[!Corollario]
> ### $\rho$ tramite il Criterio della Radice
> + Se $\exists \lim_{x \to \infty} \sqrt{|a_n|} = l \in [0, +\infty) \cup \{ + \infty\}$ vale:
> 	+ $\rho = \begin{cases} + \infty & l=0 \\ \frac{1}{l} & 0 < l < + \infty \\ 0 & l = + \infty   \end{cases}$

+ Questi criteri sono utili, ma **non sempre attuabili.** In quei casi, bisogna ricordarsi che il valore di $\rho$ può esser ricavato **anche** tramite **metodi meno ortodossi**, come scambi di variabili o simili
---
+ Sulle serie di potenze possiamo dire di più sulle loro integrazioni e derivazioni:

>[!Preposizione]
> ### Derivazione e Integrazione di Serie di Potenze
> + Supponiamo che la serie $\sum^{\infty}_{0} a_n x^n$ abbia $\rho$ e $I$, e sia $f: I \to \mathbb{R}$ la funzione somma della serie
> + Allora:
> 	1. $f$ è continua su $I$
> 	2. $f$ ammette primitiva su $I$, uguale a :
> 		$\int f(x) dx = \sum^{\infty}_{0} a_n \frac{1}{n+1} x^{n+1} + c$
> 	dove la serie integrata ha raggio di convergenza $\rho$
> 	3.   $f$ è derivabile su $(-\rho, \rho)$, dove:
> 		$f'(x) = \sum^{\infty}_{0} n a_n x^{n-1} + c$
> 	dove la serie derivata ha raggio di convergenza $\rho$

+ Notiamo che **non possiamo sapere** se la funzione è **derivabile** sui **bordi** dell'intervallo
+ Dalla precedente proposizione deriviamo il seguente teorema:

>[!Teorema]
> ### Derivazione di Serie di Potenze
> + Prendiamo una serie di potenze $\sum^{\infty}_{0} a_n x^n$ con $\rho > 0$
> + La funzione somma $f$ è derivabile infinite volte in $(- \rho, \rho)$. Per ogni $k \in \mathbb{N}$:
> 	+ $f^k(x) = \sum^{\infty}_{n = k} a_n \frac{n!}{(n-k)!}x^{n-k}$
> + In particolare:
> 	+ $f^{n}(0) = n! \cdot a_n$

---

>[!Corollario]
> ### Principio d'Identità delle Serie
> + Siano $\sum^{\infty}_{0} a_n x^n$ e $\sum^{\infty}_{0} b_n x^n$ con $\rho_a, \rho_b > 0$
> + Se esiste $\delta$ tale che $0 < \delta < \min \{\rho_a, \rho_b \}$ e 
> 	+ $\sum^{\infty}_{0} a_n x^n = \sum^{\infty}_{0} b_n x^n \qquad \forall x \in (- \delta, \delta)$
> + Allora $a_n = b_n \quad \forall n$ 

+ Questa proprietà **deriva** dal principio d'identità dei **polinomi**: Se due polinomi coincidono in parte, allora essi sono lo stesso polinomio