+ Vediamo inizialmente il concetto di periodicità

>[!Concetto]
> ### Periodicità
> + La funzione $f : \mathbb{R} \to \mathbb{R}$ viene detta $T$-**periodica** se vale:
> 	+ $f(x + T) = f(x) \qquad \forall x \in \mathbb{R}, \; T >0$
> + Essa viene detta **nota** se è nota in $[a, a+T] \; \forall a \in \mathbb{R}$

+ Esempi sono le funzioni trigonometriche, o le funzioni costanti
+ Queste funzioni possono essere riscritte in modo da **variare il periodo**, nel seguente modo:

>[!Osservazione]
> ### Cambio di Periodo
> + Data la funzione $f : \mathbb{R} \to \mathbb{R}$  $T$-**periodica**, esiste la funzione $g : \mathbb{R} \to \mathbb{R}$  $2\pi$-**periodica**, definita come:
> 	+ $g(x) = f\left(\cfrac{T}{2\pi} x\right)$

---
+ Immaginiamo una funzione periodica come un **vettore** in un piano
+ Questo piano è composto da una serie **infinita** di **basi**, anch'esse periodiche
+ Essendo un vettore, esso può essere riscritto come il **prodotto scalare** delle sue **proiezioni** su queste basi, ovvero la somma delle sue proiezioni
+ Essendo lo spazio composto da basi infinite, questo si traduce in un **integrale**
+ Questa è l'idea alla base della **serie di Fourier** :
>[!Definizione]
> ### Serie di Fourier
> + Data la funzione $f : \mathbb{R} \to \mathbb{R}$  $T$-periodica, i suoi **coefficienti di Fourier** sono della forma:
> 	+ $\hat{f_k} = \cfrac{1}{T} \cdot \int^{\frac{T}{2}}_{ - \frac{T}{2}} f(x) \cdot e^{-i \frac{2\pi}{T} k x} dx \quad k \in \mathbb{Z}$
> + Purchè l'integrale esista
> + La seguente serie viene chiamata la **serie di Fourier** di $f$:
> 	+ $\sum^{+\infty}_{k = - \infty} \hat{f_k} \cdot e^{i \frac{2\pi}{T} k x}$

+ Si può notare che $e^{-i \frac{2\pi}{T} k x}$ è un **numero complesso**. La differenza di segno su $i$ nelle due parti della formula deriva dal **complesso coniugato**
+ Inoltre, $\hat{f}_k(x)$ è un **numero**. La serie di Fourier è una serie di funzioni
---
+ I coefficienti di Fourier sono "simmetrici", essi si ripetono intorno all'origine
+ Proviamo a sommarli:
	+ $\hat{f_k} + \hat{f_{-k}} = \frac{2}{T} \int^{\frac{T}{2}}_{-\frac{T}{2}} f(x) \cos(\frac{2 \pi}{T} kx) dx = a_k$
	+ $i(\hat{f_k} - \hat{f_{-k}} = \frac{2}{T} \int^{\frac{T}{2}}_{-\frac{T}{2}} f(x) \sin(\frac{2 \pi}{T} kx) dx = b_k$
+ Possiamo usare questi due valori per **riscrivere la somma di Fourier**:
	+ $S_N(y) = \frac{a_0}{2} + \sum^{N}_{k=1} (a_k \cos(\frac{2 \pi}{T} kx) + b_k \sin(\frac{2 \pi}{T} kx))$
+  Possiamo anche scrivere che:
	+ $\hat{f_k} = \frac{1}{2} (a_k - i b_k)$
	+ $\hat{f_{-k}} = \frac{1}{2} (a_k + i b_k)$
+ Possiamo capire che:
	+ Se una funzione è **pari**, è composta solo da parti di **coseno**, e quindi non contiene $b_k$
	+ Se una funzione è **dispari**, è composta solo da parti di **seno**, e quindi non contiene $a_k$
+ Una cosa importante è, che **più** una funzione è **regolare**, **più velocemente** i suoi **coefficienti** tendono a **0**:
	+ $0 = \lim_{k \to \pm \infty} |\hat{f^n_k}| \underbrace{=}_{T = 2 \pi} \lim_{k \to \pm \infty} |k^n \hat{f_k}| = 0$
---

>[!Teorema]
> ### Somme di Periodiche
> + Date le funzioni $f, g : \mathbb{R} \to \mathbb{C}$  $T$-**periodiche** ed i valori $\alpha, \beta \in \mathbb{C}$, valgono le seguenti proprietà:
> 	+ $\widehat{(\alpha f + \beta g)_k} = \alpha \hat{f_k} + \beta \hat{g_k} \qquad \forall k \in \mathbb{Z}$
> 	+ $f(x) = f(-x) \leftrightarrows \hat{f_k} = \hat{f_{-k}} \leftrightarrows b_k = 0$
> 	+ $f(-x) = -f(-x) \leftrightarrows \hat{f_k} = \hat{f_{-k}} \leftrightarrows a_k = 0$
> 	+ $\overline{f(x)} = f(x) \leftrightarrows \hat{f_-{k}} = \overline{\hat{f_{k}}} \leftrightarrows a_k, b_k \in \mathbb{R}$
> 	+ Se $x_0 \in \mathbb{R}$, $g(x) = f(x -x_0)$:
> 		+ $\hat{g_k} = e^{-i \frac{2 \pi}{T} x_0 k} \hat{f_k}$
> 	+ Se $f \in C^n(\mathbb{R})$ (continua in $\mathbb{R}$):
> 		+ $\hat{f^{(n)}}_k = (i \frac{2 \pi}{T} k)^n \hat{f_k}$

+ Questo è un teorema **lungo** e **pieno di significati**. Possiamo già dire che è un primo esempio di **trasformata di Fourier**
+ L'**energia** di un onda viene indicata come:
	+ $L^2 = \int^{\frac{T}{2}}_{- \frac{T}{2}} |f(x)|^2$
		+ $L$ è la norma dell'onda
+ Si può dimostrare che:
	+ $L^2 = \sum^{+\infty}_{n = -\infty} |\hat{f_n}|^2$
+ Questo mostra che la **trasformata conserva l'energia** dell'onda, non in modo dissimile da come funziona il **Teorema di Pitagora** 

>[!Teorema]
> ### Formula di Parseval
> + Data la funzione $f : \mathbb{R} \to \mathbb{C}$  $T$-**periodica** e Riemann-integrabile nell'intervallo $[-\frac{T}{2}, \frac{T}{2}]$, vale che:
> 	+ $\frac{1}{T} \int^{\frac{T}{2}}_{- \frac{T}{2}} |f(x)|^2 = \frac{|a_0|^2}{4} \frac{1}{2} \sum^{\infty}_{k=1} (|a_k|^2 + |b_k|^2) = \sum^{+\infty}_{k = -\infty} |\hat{f_k}|^2$
> + Se $f$ è reale, si può riscrivere come:
> 	+ $\frac{2}{T} \int^{\frac{T}{2}}_{- \frac{T}{2}} f(x)^2 = \frac{a_0^2}{2} \sum^{\infty}_{k=1} (a_k^2 + b_k^2)$

---

>[!Teorema]
> ### Teorema di Dirichlet
> + Prendiamo la funzione $f : \mathbb{R} \to \mathbb{C}$  $T$-**periodica** (regolare a tratti)
> + Supponiamo che esistano un numero finiti di punti $\{x_1, \cdots, x_n\}$, a distanze differenti, contenuti in $[-\frac{T}{2}, \frac{T}{2}]$, tali che:
> 	+ In ciascun intervallo $(x_{i-j}, x_i)$, $f$ è **derivabile**
> 	+ $\forall i = 0, \cdots , n$ esistono i seguenti limiti, finiti:
> 		+ $\lim_{x \to x_i^-} f(x) = f(x_i^-)$
> 		+ $\lim_{x \to x_i^+} f(x) = f(x_i^+)$
> 		+ $\lim_{x \to x_i^-} f'(x) = f'(x_i^-)$
> 		+ $\lim_{x \to x_i^+} f'(x) = f'(x_i^+)$
> + Allora vale che:
> 	+ $\forall x \notin \{x_0, \cdots, x_n\}$
> 		+ $f(x) = \frac{a_0}{2} + \sum^{N}_{k=1} (a_k \cos(\frac{2 \pi}{T} kx) + b_k \sin(\frac{2 \pi}{T} kx)) = S_N(y)$
> 		+ Quindi, converge
> 	+ $\forall i \in \{0, \cdots, n\}$
> 		+ $S_N(y) = \cfrac{f(x_i^-) + f(x_i^+)}{2}$
> 		+ Quindi converge alla media fra i valori dei lati dei salti
> 	+ Se $f$ è **continua**, allora la serie di Fourier converge totalmente su $\mathbb{R}$

+ Come vediamo, essere una funzione **continua non basta** per capire se ne **esiste la serie**, sono necessarie anche condizione sulla sua derivabilità