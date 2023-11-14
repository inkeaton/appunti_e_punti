## Funzioni Tipo Potenza

* $f(x) = x^n \quad n \in \mathbb{N}$

|  $n>0$   | $n<0$    |
| --- | --- |
| $dom(f) = \mathbb{R}$ | $dom(f) = \mathbb{R}$ |
| $Im(f) = (0, +\infty )$ | $Im(f) = \mathbb{R}$| 
| Crescente in $[0, + \infty)$ | Strettamente crescente, e Iniettiva |
| Decrescente in $(- \infty, 0]$ | |
| $f(-x) = f(x)$: Pari | $f(-x) = -f(x)$: dispari|

* Consideriamo la funzione al crescere di $n$, ovvero con $m \in \mathbb{N}, \; m > n$
	* $x^m \geq x^n \quad 0 \leq x \leq 1$
	* $x^m \leq x^n \quad x \geq 1$

## Funzioni Tipo Potenza Negativa
* $f(x) = x^{-n} = \frac{1}{x^n} \quad n \in \mathbb{N}$

|  $n>0$   | $n<0$    |
| --- | --- |
| $dom(f) = \mathbb{R} \backslash \{0\}$ | $dom(f) = \mathbb{R} \backslash \{0\}$ |
| $Im(f) = (0, +\infty )$ | $Im(f) = \mathbb{R} \backslash \{0\}$| 
| Non Monotona | Non Monotona |
| Crescente in $(- \infty, 0]$ | Crescente in $[0, + \infty)$|
| Decrescente in $[0, + \infty)$ | Decrescente in $(- \infty, 0]$|
| $f(-x) = f(x)$: Pari | $f(-x) = -f(x)$: dispari|

* Consideriamo la funzione al crescere di $n$, ovvero con $m \in \mathbb{N}, \; m > n$
	* $x^{-m} \geq x^{-n} \quad 0 \leq x \leq 1$
	* $x^{-m} \leq x^{-n} \quad x \geq 1$

## Funzioni Tipo Radice
* $f(x) = x^{\frac{1}{n}} = \sqrt[n]{x}$

|  $n>0$   | $n<0$    |
| --- | --- |
| $dom(f) = [0, + \infty)$ | $dom(f) = \mathbb{R}$ |
| $Im(f) = [0, + \infty)$ | $Im(f) = \mathbb{R}$| 
| Strettamente Crescente, quindi Iniettiva | Strettamente Crescente, Quindi Iniettiva |
| Non si può dire che è Pari | $f(-x) = -f(x)$: dispari|

* Consideriamo la funzione al crescere di $n$, ovvero con $m \in \mathbb{N}, \; m > n$
	* $x^{\frac{1}{m}} \geq x^{\frac{1}{n}} \quad 0 \leq x \leq 1$
	* $x^{\frac{1}{m}} \leq x^{\frac{1}{n}} \quad x \geq 1$

## Funzioni Esponente Razionale
* $f(x) = x^r = x^{\frac{p}{q}} = \sqrt[q]{x^p}$

| $r>0$ | $r<0$ |
| --- | --- |
| $dom(f) = [0, + \infty)$ | $dom(f) = (0, + \infty)$ |
| $Im(f) = [0, + \infty)$ | $Im(f) = (0, + \infty)$| 
| Strettamente Crescente, quindi Iniettiva | Strettamente Decrescente, Quindi Iniettiva |

* Consideriamo la funzione al crescere di $r$, ovvero con $o \in \mathbb{Q}, \; o > r$
	* $x^r \leq x^o \quad 0 \leq x \leq 1$
	* $x^r \geq x^o \quad x \geq 1$
* Questo vale in generale per $r, o \in \mathbb{R}$

## Funzioni Esponente Reale
* $f(x) = x^k \quad k \in \mathbb{R}$
* Stesse proprietà di $k \in \mathbb{Q}$

## Funzioni Esponenziali
* $f(x) = a^x$

| $a > 1$ | $0 < a < 1$ |
| --- | --- |
| $dom(f) = \mathbb{R}$ | $dom(f) = \mathbb{R}$ |
| $Im(f) = (0, + \infty)$ | $Im(f) = (0, + \infty)$| 
| Strettamente Crescente, quindi Iniettiva | Strettamente Decrescente, Quindi Iniettiva |
* Se $a = 1, \quad f(x) = 1^x = 1$
* Consideriamo la funzione al crescere di $a$, ovvero con $b \in \mathbb{R}, \; b > a$
	* $b^x \geq a^x \quad x \geq 0$
	* $b^x \leq a^x \quad x \leq 0$
* La sua inversa è:
## Funzioni Logaritmo
* $f(x) = \log_a{x}$
* $a$ deve sempre essere maggiore di 0

| $a > 1$ | $0 < a < 1$ |
| --- | --- |
| $dom(f) = (0, + \infty)$ | $dom(f) = (0, + \infty)$ |
| $Im(f) = \mathbb{R}$ | $Im(f) = \mathbb{R}$| 
| Strettamente Crescente, quindi Iniettiva | Strettamente Decrescente, Quindi Iniettiva |

## Funzioni Polinomiali
* $f(x) = a_nx^n + a_{n-1}x^{n-1} + ... + a_1x + a_0$
* Se sono presenti solo termini di grado dispari, la funzione è DISPARI, viceversa, se sono presenti solo termini di grado pari, la funzione è PARI

|  PARI   | DISPARI |
| --- | --- |
| $dom(f) = \mathbb{R}$ | $dom(f) = \mathbb{R}$ |
| $Im(f) = \mathbb{R}$ | $Im(f) \neq \mathbb{R}$| 

## Proprietà Logaritmo ed Esponenziale

| $a^{x + y} = a^x \cdot a^y$ | $\log_a{xy} =log_a{x} + log_a{y}$ |
| --- | --- |
| $a^{x \cdot b} = {a^x}^b$ | $\log_a{x^b} = b \cdot \log_a{x}$ |
| $a^{-x} = {a^x}^{-1} = \frac{1}{a^x}$ | $\log_a{\frac{1}{x}} = \log_a{x^{-1}} = -\log_a{x}$ |
| $a^0 = 1$ | $\log_a{1} = 0$ |
| $a^1 = a$ | $\log_a{a} = 1$ |
|  | $\log_a{x} = \log_b{x} \cdot \log_a{b}$ |
|  | $a^{\log_a{x}} = x$ |
|  | $\log_a{a^x} = x$ |

* Un tipo di logaritmo particolare è il cosiddetto LOGARITMO NATURALE, in base $e$, il cosidetto numero di Nepero.
* Questo logaritmo viene rappresentato come $\ln{x}$