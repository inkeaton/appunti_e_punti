+ Esistono numerosi modi per **approssimare** il **valore** di una funzione
+ Cominceremo vedendo le approssimazioni locali, limitate ad una sezione della funzione
+ Il primo tipo di approssimazione che vedremo ha la sua **origine** nel teorema di **Rolle**, corollario di di La Grange:

> [! Teorema ] 
>  ### La Grange
>  + Prendiamo $f: [a, b] \to \mathbb{R}$ continua nel suo intervallo, e derivabile in $(a, b)$
>  + Se consideriamo la retta secante $\overline{ab}$, essa è parallela ad almeno una delle rette tangenti alla funzione
>  + Dunque, esiste $c \in (a, b)$ tale che: 
> 	 + $f(b) - f(a) = f'(c) \cdot (b -a)$
>  + Riscrivibile come:
> 	 + $\cfrac{f(b) - f(a)}{(b -a)} = f'(c)$
> 		+ $c$ è esattamente il coefficente angolare della retta $\overline{ab}$

+ Esso può dimostrare il seguente teorema:

> [! Teorema ] 
> ### Formula di Taylor con resto di La Grange
> + Prendiamo $f: [a, b] \to \mathbb{R}$ continua e derivabile nel suo intervallo.
> + Per ogni $n \in \mathbb{N}$, esiste $c_n \in (a, b)$ tale che:
> 	+ $f(b) = \underbrace{f(a) + f' (a) \cdot (b - a) + \cdots + \cfrac{1}{n!} \cdot f^{(n)}(a)\cdot (b-a)^n}_{\text{Polinomio di Taylor di ordine n di f, centrato in a}} + \underbrace{\cfrac{f^{(n+1)}(c_n)}{(n+1)!} \cdot (b-a)^{n+1}}_{\text{Resto di La Grange}}$

+ Cosa vuol dire ciò?
	+ Supponiamo inizialmente che la funzione sia molto regolare. Dunque, per studiare il suo comportamento, la studiamo solo in $a$, derivando innumerevoli volte
	+ Il risultato di ciò è il **Polinomio di Taylor** ($T_n(x)$) . Questa è pur sempre un approssimazione, errata per sua natura. Per ciò correggiamo il risultato finale sommando il **resto di La Grange** ($R_n(x)$)
+ Il difetto principale di questa formula è il valore $c_n$ , **sconosciuto**. Stiamo dunque incapaci di calcolare l'errore dell'approssimazione ottenuta con Taylor. 
+ **Ma questo è veramente un problema?** 
	+ Osserviamo meglio $R_n(x)$
		+ $R_n(x) =\cfrac{f^{(n+1)}(c_n)}{(n+1)!} \cdot (b-a)^{n+1}$
	+ Notiamo che la dimensione del valore dipende da due valori:
		+ La differenza fra $a$ e $b$ 
		+ La dimensione di $n$
	+ Al diminuire della prima, e crescere del secondo, il valore del resto diminuisce velocemente, con unico fattore contrastante il valore della derivata n-esima, $M$
	+ Dunque:
		+ $|R_n(b)| \leq \cfrac{|(b-a)^{n+1}|}{(n+1)!} \cdot M$
+  *Dimostrazione nelle note cartacee*
---
+ Esiste un altro modo per scrivere questo tipo di approssimazione, utile per alcuni casi:

> [! Teorema ] 
> ### Formula di Taylor con resto di Peano
> + Prendiamo $f: [a, b] \to \mathbb{R}$ continua e derivabile nel suo intervallo.
> + Per ogni $n \in \mathbb{N}$,  vale che:
> 	+ $f(b) = \underbrace{f(a) + f' (a) \cdot (b - a) + \cdots + \cfrac{1}{n!} \cdot f^{(n)}(a)\cdot (b-a)^n}_{\text{Polinomio di Taylor di ordine n di f, centrato in a}} + \underbrace{(b-a)^{n} \cdot \varepsilon(x-x_0)}_{\text{Resto in forma di Peano}}$
> + In esso, $\varepsilon$ è una generica funzione che tende a $0$ per $x \to x_o$ 

+ Questa formula può essere usata assieme al seguente teorema, per provare che determinate funzioni, nonostante la loro complessità, sono approssimabili solo attraverso Taylor

> [! Teorema ] 
> ###  Univocità della Formula di Taylor
> + Sia $I$ un intervallo, e sia $f : I \to R$,derivabile infinite volte nel suo intervallo
> + Per ogni $n \geq 0$ e supponiamo che si abbia il seguente polinomio:
> 	+ $f(x) = a_0 + a_1 \cdot (x - x_0) + \cdots + a_n \cdots (x -x_0)^n + (x-x_0)^{n} \cdot \varepsilon(x-x_0)$
> + Allora quel polinomio è il polinomio di Taylor
+  *Dimostrazione nelle note cartacee*
---
+ ### Approssimazioni Utili
	+ $\cfrac{1}{1 + x} = \left( \sum^{N}_{n=0}  (-1)^n \cdot x^n \right) + x^N \cdot \varepsilon (x)$
	+ $e^x = \left( \sum^{N}_{n=0} \cfrac{x^n}{n!} \right) + x^N \cdot \varepsilon (x)$
	+ $\log(1 + x) = \left( \sum^{N}_{n=0} \cfrac{(-1)^{n+1}}{n} \cdot x^n \right) + x^N \cdot \varepsilon (x)$
	+ $\sin x = \left( \sum^{N}_{n=0} \cfrac{(-1)^n \cdot x^{2n + 1}}{(2n + 1)!} \right) + x^{2N + 1} \cdot \varepsilon (x)$
	+ $\cos x = \left( \sum^{N}_{n=0} \cfrac{(-1)^n \cdot x^{2n}}{(2n)!} \right) + x^{2N} \cdot \varepsilon (x)$
	+ $\arctan x = \left( \sum^{N}_{n=0} \cfrac{(-1)^n \cdot x^{2n + 1}}{2n + 1} \right) + x^{2N + 1} \cdot \varepsilon (x)$
	+ $(1 + x)^{\alpha} = \left( \sum^{N}_{n=0} \cfrac{\prod^{n+1}_{k=0} \alpha - k}{n!} \cdot x^n \right) + x^{N} \cdot \varepsilon (x)$
	+ $(1 + x)^{-k} = \left( \sum^{N}_{n=0} \dbinom{n + k - 1}{k - 1} \cdot x^n \right) + x^{N} \cdot \varepsilon (x)$
		+ dove $k \in \mathbb{N} \setminus \{0\}$
