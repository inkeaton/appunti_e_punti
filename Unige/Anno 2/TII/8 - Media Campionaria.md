* La __media campionaria__ è un valore che indica il valore medio di una variabile aleatoria, __calcolata__ sulla base dei valori __ottenuti__ in più esperimenti
* Su $n$ tiri, il valore medio della VA $X$  vale
	* $\mu_n = \cfrac{1}{n} \cdot \sum^{n}_{i = 1} X_i$ 
* Questo valore __non__ corrisponde a $\mathbb{E}[X]$. È vero però che, calcolando più volte la media, $\mathbb{E}[\mu_n] \approxeq \mathbb{E}[X]$ 
* L'__attendibilità__ di questa "media di medie" __dipende__ dalla __varianza__ di $X$
	* $Var(\mu_n) = \cfrac{Var(X)^2}{n}$ 
	* All'aumentare dei __lanci__, aumenta la __precisione__
* Inoltre, se $n \to \infty$, $\mu_n \to \mathbb{E}[X]$ 