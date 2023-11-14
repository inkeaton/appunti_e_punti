* Fare un __Limite__ consiste nel controllare il comportamento della funzione vicino ad  $x_0$, punto di accumulazione per $Dom(f)$   
## DEF
* Sia $A \in \mathbb{R}$ , $x_0 \in \mathbb{R}$ è detto __punto di accumulazione__ di $A$ se $\forall \epsilon > 0 \quad \exists x \in A \backslash \{x_0\}$ tale che $x \in (x_0 - \epsilon, x_0 + \epsilon)$ 
## DEF 
* Un Intorno di $x_0$ è un intervallo della forma $(x_0 - \epsilon, x_0 + \epsilon)$ con $\epsilon > 0$ 
	* Un intorno bucato è  $(x_0 - \epsilon, x_0 + \epsilon) \backslash \{x_0\}$ 
	* Un intorno destro è  $[x_0, x_0 + \epsilon)$
	* Un intorno sinistro è  $(x_0 - \epsilon, x_0]$
## DEF 
* $A \in \mathbb{R}$. Si dice che:
	* $+\infty$ è punto d'accumulazione di $A$ se $\forall M > 0$, $\exists x \in A$ tale che $x \geq M$ 
	* $-\infty$ è punto d'accumulazione di $A$ se $\forall M > 0$, $\exists x \in A$ tale che $x \leq -M$ 

# Limiti
* Sia $f:A \to \mathbb{R}$ e sia $x_0$ un punto di accumulazione di $A$ 
* I possibili risultati di $\lim_{x \to x_0}f(x)$ sono:
	1. $l \in \mathbb{R}$
	2. $+\infty$
	3. $-\infty$ 
	4. $\nexists$ 
* Consideriamo ora i tre casi $x_0 \in \mathbb{R}$, $x_0 = + \infty$, $x_0 = -\infty$ con ognuno dei risultati possibili

### $x_0 = +\infty$ 
2. $\lim_{x \to +\infty}f(x) = + \infty$ 
	* Da un certo punto in poi, andando verso destra, il grafico rimarra sopra qualunque altitudine
3. $\lim_{x \to +\infty}f(x) = - \infty$ 
	* Il contrario del precedente, andrà verso il basso 
1. $\lim_{x \to +\infty}f(x) = l$ 
	* I valori verso infinito rimarranno inclusi in un intorno di $l$ 
4. $\nexists \lim_{x \to +\infty}f(x)$  
	* Probabilmente la funzione oscilla fra più valori. Un esempio è la funzione $\sin x$ 

### $x_0 = -\infty$ 
2. $\lim_{x \to -\infty}f(x) = + \infty$ 
	* Da un certo punto in poi, andando verso sinistra, il grafico rimarra sopra qualunque altitudine
3. $\lim_{x \to -\infty}f(x) = - \infty$ 
	* Il contrario del precedente, andrà verso il basso 
1. $\lim_{x \to -\infty}f(x) = l$ 
	* I valori verso meno infinito rimarranno inclusi in un intorno di $l$ 
4. $\nexists \lim_{x \to -\infty}f(x)$  
	* Probabilmente la funzione oscilla fra più valori. Un esempio è la funzione $\sin x$ 
	* In generale, vi si ricade se non si verificano i tre casi precedenti

### $x_0 \in \mathbb{R}$ 
2. $\lim_{x \to x_0}f(x) = + \infty$ 
	* I due "lembi" del grafico salgono verso l'alto in prossimità del punto
3. $\lim_{x \to x_0}f(x) = - \infty$ 
	* Il contrario del precedente, andrà verso il basso 
1. $\lim_{x \to x_0}f(x) = l$ 
	* I valori verso meno infinito rimarranno inclusi in un intorno di $l$, e si formerà un "buco" nel grafico
4. $\nexists \lim_{x \to x_0}f(x)$  
	* In questi casi, è possibile calcolare i limiti da destra e da sinistra, indicati con $x \to x_0^{+}$ e $x \to x_0^{+}$, i quali potrebbero esistere con valori differenti. Un esempio sono i limiti con $x \to 0$ di $f(x) = \frac{1}{x}$ 
* E' importante ricordare che il valore di un limite può essere discordante dal valore della funzione in quel punto
* Ma nel caso i due valori concordino, si dice che la funzione è __Continua__ in quel punto
## Proprietà dei Limiti
1. $\lim_{x \to x_0}(f(x)+g(x)) = \lim_{x \to x_0}f(x) + \lim_{x \to x_0}g(x)$
2. $\lim_{x \to x_0}f(x)\cdot g(x) = (\lim_{x \to x_0}f(x))\cdot (\lim_{x \to x_0}g(x))$
3. $\lim_{x \to x_0}\frac{f(x)}{g(x)} = \frac{\lim_{x \to x_0}f(x)}{\lim_{x \to x_0}g(x)}$
4. $\lim_{x \to x_0}f(x)^{g(x)} = (\lim_{x \to x_0}f(x))^{(\lim_{x \to x_0}g(x))}$
5. $\lim_{x \to x_0}f(x) = l_0, \quad \lim_{y \to l_0}g(x) = l_1$
   $\to$ $\lim_{x \to x_0}f(g(x)) =\lim_{y \to l_0}g(f(x)) = l_1$
## Forme Indeterminate
* Le forme indeterminate sono operazioni a cui è possibile arrivare nel calcolo dei limiti, le quali a sè sono irrisolvibili
	* $+ \infty - \infty$ 
	* $0 \cdot \infty$ 
	* $\frac{0}{0}$
	* $\frac{\infty}{\infty}$ 
	* $1^{\infty}$
	* $0^0$ 
	* $\infty^0$ 
* Esistono più modi per risolverli, com riscriverli tramite raccoglimento o, come vederemo più avanti, tramite i __limiti notevoli__, oppure si può sfruttare ad esempio la __gerarchia degli infiniti__ 
	* Le funzioni che vanno ad infinito non lo fanno allo stesso modo, alcune più velocemente di altre.
	* La scala semplificata è:
		* $e^x >> x^n >> \log_n{x}$
	* Questo ci permette di risolvere forme indeterminate $\frac{\infty}{\infty}$ considerando l'infinito inferiore come un numero intero, ottenendo quindi come risultato o $0$ o $\infty$   
* Un semplice metodo per risolvere alcune forme indeterminate $x \to \infty$ è raccogliere l'incognita di grado superiore