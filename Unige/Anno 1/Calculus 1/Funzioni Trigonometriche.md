## Radianti
* Le funzioni che andremo a studiare si basano sugli angoli di un cerchio
* Per misurare tali angoli non useremo i gradi, ma i RADIANTI
	* Essi possono essere definiti come l'arco di cerchio misurato dall'angolo indicato, riferendosi alla misura di un cerchio di raggio 1. Per esempio, $360° = 2 \pi$
		* In generale $angolo\;in\;radianti = \frac{angolo\;in\;gradi}{360} \cdot 2\pi$
## Funzioni
* $cos(x)$ e $sin(x)$ indicano rispettivamente la posizione sull'asse x e y del punto formatosi dall'incrocio fra l'asse dell'angolo x e della circonferenza relativa. Per il teorema di Pitagora, $sin^2(x) + cos^2(x) = 1$
* $tan(x)$ indica la posizione sull'asse y del punto formatosi dall'incrocio fra l'asse dell'angolo x e della retta $r : x = 1$. Può essere calcolata come $tan(x) = \frac{sin(x)}{cos(x)}$. Per proprietà geometriche, $sin(x) \leq x \leq tan(x)$
* $cotan(x)$ indica la posizione sull'asse x del punto formatosi dall'incrocio fra l'asse dell'angolo x e della retta $r : y = 1$. Può essere calcolata come $cotan(x) = \frac{cos(x)}{sin(x)}$

### Sin(x)
* E' una funzione PERIODICA, ovvero, i suoi valori si ripetono periodicamente per tutto il suo dominio, $\mathbb{R}$. $cod(sin(x)) = (-1, 1)$
* A ripetersi è la sezione compresa in $(0, 2\pi)$. Essa alterna intervalli di decrescenza(Es. $(-\frac{\pi}{2}, \frac{\pi}{2})$) ad intervalli di crescenza ($(\frac{\pi}{2}, \frac{3}{2}\pi)$)
* E' una funzione DISPARI, ovvero simmetrica rispetto all'origine
### Cos(x)
* Anch'essa funzione periodica, condivide dominio e codominio con $sin(x)$, ma si trova visivamente traslata verso sinistra di $\frac{\pi}{2}$.
* Da ciò otteniamo la fomula algebrica $sin(x) = cos(x - \frac{\pi}{2})$
* Decresce in  $(0, \pi)$, cresce in $(\pi, 2\pi)$
* E' una funzione PARI, ovvero simmetrica rispetto all'asse y
### Tan(x)
* Anch'essa è una funzione periodica, con $dom(tan(x)) = \{ x \in \mathbb{R} \; | \; x \neq \frac{\pi}{2} + k \pi, \; k \in \mathbb{N}\}$, e $cod(tan(x)) = \mathbb{R}$
* Essa è crescente per ogni intervallo del suo dominio
* è DISPARI
### Cotan(x)
* Essa appare come una versione traslata di $\frac{\pi}{2}$ e specchiata di $tan(x)$
* $dom(cotan(x)) = \{ x \in \mathbb{R} \; | \; x \neq \pi + k \pi, \; k \in \mathbb{N}\}$, e $cod(cotan(x)) = \mathbb{R}$
* Essa è decrescente in ogni parte del suo dominio

## Proprietà Algebriche
* $cos(x + y) = cos(x) \cdot cos(y) -sin(x)\cdot sin(y)$
* $cos(x - y) = cos(x) \cdot cos(y) +sin(x)\cdot sin(y)$
* $sin(x + y) = cos(y) \cdot sin(x)  + cos(x)\cdot sin(y)$
* $sin(x - y) = cos(y) \cdot sin(x)  - cos(x)\cdot sin(y)$

* $tan(x+y) = \frac{tan(x) + tan(y)}{1 - tan(x) \cdot tan(y)}$
* $tan(x-y) = \frac{tan(x) - tan(y)}{1 + tan(x) \cdot tan(y)}$

* $cos(2x) = 2cos^2(x) -1 = 1 - 2sin^2(x)$
* $sin(2x) = 2sin(x)cos(x)$
* $sin(3x) =3sin(x) - 4sin^3(x)$

* $sin^2(x) = \frac{1 - cos(2x)}{2}$
* $sin(x) = \sqrt{\frac{1 - cos(2x)}{2}} \quad 0 \leq x \leq \pi$
* $sin(\frac{x}{2}) = \sqrt{\frac{1 - cos(x)}{2}} \quad 0 \leq x \leq 2\pi$