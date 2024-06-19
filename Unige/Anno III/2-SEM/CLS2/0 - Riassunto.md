+ In questo foglio cercheremo di riassumere i contenuti del corso di **Calculus 2**
+ Maggiori dettagli sono negli appunti associati e nelle note vicine
---
# 1 - Serie
## Polinomio di Taylor?
Esistono numerosi modi per **approssimare** il **valore** di una funzione
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

## Serie Numeriche e Criteri
+ Le serie numeriche sono **sommatorie infinite di numeri**
+ Vogliamo essere in grado di capire se questi valori esistono, non esistono, o sono infiniti

> [!Definizione]
>  ### Comportamento delle Successioni Numeriche
>   + Data la successione  $(a_n)$, con $n \geq 1$, si dice che la serie $\sum^{\infty}_{n = 1} a_n$:
> 	  + **Converge** al numero $\delta \in \mathbb{R}$ se esiste il limite finito $\lim_{N \to \infty} (a_1 + a_2 + \cdots + a_N) = \delta$. In questo caso, $\delta$ viene chiamata la **somma della serie**
> 	  + **Diverge** se $\lim_{N \to \infty} (a_1 + a_2 + \cdots + a_N) = \pm \infty$
> 	  + **È indeterminato** se $\nexists \lim_{N \to \infty} (a_1 + a_2 + \cdots + a_N)$

 + $a_n$ viene chiamato **termine generale della serie**.
 + $\delta_n = \sum^{n}_{k = 1} a_k$ viene chiamata **somma parziale n-esima**
 
>[!Concetto]
> ### Indipendenza del Carattere
> + Il carattere della serie $\sum^{\infty}_{n = n_0} a_n$ non dipende da $n_0$

---
+ Vedremo alcuni **criteri** che ci **aiuteranno** ad analizzare il comportamento delle serie che incontreremo
+  Un primo criterio, utile a dimostrare i successivi, è il seguente:

> [!Teorema]
> ### Criterio di Couchy
> + Se la serie $\sum^{\infty}_{n = 1} a_n$ converge, allora vale che $\lim_{n \to +\infty} a_n = 0$

+ Vediamo ora alcuni criteri specifici:
### Serie Positive
+ Esse sono serie in cui i valori che vengono sommati sono **solo positivi**
+ Vale per esse la seguente proposizione:

> [!Proposizione]
> ### Comportamento Serie Positive
> + Data una serie positiva $\sum^{\infty}_{n=0} a_n$, essa può comportarsi in solo due modi:
> 	+ **Converge** ad un numero finito positivo
> 	+ **Diverge** a $+ \infty$

+ Criteri utili sono:

> [!Proposizione]
> ### Criterio del Confronto
> + Prendiamo due successioni positive $a_n$ e $b_n$ tali che:
> 	+ $0 \leq a_n \leq b_n$
> + Allora vale che:
> 	+ Se $\sum^{\infty}_{n=0} b_n < + \infty$, allora $\sum^{\infty}_{n=0} a_n < + \infty$
> 	+ Se $\sum^{\infty}_{n=0} a_n = + \infty$, allora $\sum^{\infty}_{n=0} b_n = + \infty$

> [!Proposizione]
> ### Criterio del Confronto Asintotico
> + Prendiamo due successioni positive $a_n$ e $b_n$ tali che:
> 	+ $a_n = b_n \cdot c_n$
> + Vale che:
> 	+ Se $\lim_{n \to +\infty} c_n = c > 0$, allora  $\sum^{\infty}_{n=0} b_n$ e $\sum^{\infty}_{n=0} a_n$ possiedono lo **stesso carattere**
> 	+ Se $\lim_{n \to +\infty} c_n = 0$, e  $\sum^{\infty}_{n=0} b_n$ converge, anche $\sum^{\infty}_{n=0} a_n$ **converge**
> 	+ Se $\lim_{n \to +\infty} c_n = + \infty$, e  $\sum^{\infty}_{n=0} b_n$ diverge, anche $\sum^{\infty}_{n=0} a_n$ **diverge**

> [!Osservazione]
> ### Sul Confronto Asintotico
>  + Nei seguenti casi:
> 	+ $\lim_{n \to + \infty} \cfrac{a_n}{b_n} \to 0$ e $\sum b_n = + \infty$
> 	+ $\lim_{n \to + \infty} \cfrac{a_n}{b_n} \to + \infty$ e $\sum b_n < + \infty$
> + Non si può concludere niente sul carattere di $\sum a_n$

> [!Proposizione]
> ### Criterio della Radice
> + Prendiamo una serie positiva $\sum a_n$ tale che esiste:
> 	+ $\lim_{n \to \infty} \sqrt{a_n}^n = \ell \in [0, + \infty) \cup \{ + \infty \}$
> + Valgono i seguenti:
> 	1. Se $\ell < 1$, allora  $\sum a_n < + \infty$ 
> 	2. Se $\ell > 1$, allora  $\sum a_n = + \infty$ 
> 	3. Se $\ell = 1$, allora  **non possiamo dire niente** su $\sum a_n$ 

> [!Proposizione]
> ### Criterio del Rapporto
> + Prendiamo una serie positiva $\sum a_n$ tale che esiste:
> 	+ $\lim_{n \to \infty} \frac{a_n + 1}{a_n} = \ell \in [0, + \infty) \cup \{ + \infty \}$
> + Valgono i seguenti:
> 	1. Se $\ell < 1$, allora  $\sum a_n < + \infty$ 
> 	2. Se $\ell > 1$, allora  $\sum a_n = + \infty$ 
> 	3. Se $\ell = 1$, allora  **non possiamo dire niente** su $\sum a_n$ 

> [!Proposizione]
> ### Criterio dell'Integrale
> + Sia $f : [1, + \infty ) \to (0, + \infty)$ decrescente, e sia $a_n = f(n) \forall n$
> + Allora le seguenti cose sono sinonime:
> 	+ $\sum^{+ \infty}_{n = 1} a_n$**converge**
> 	+ $\int^{+ \infty}_{1} f(x) dx$ è **finito**
> + Questo è dovuto alla seguente uguaglianza:
> 	+ $\int^{+ \infty}_{1} f(x) dx \quad \leq \quad \sum^{+ \infty}_{n = 1} a_n \quad \leq \quad a_1 + \int^{+ \infty}_{1} f(x) dx$
#### Serie Geometrica
+ La serie geometrica di ragione $q \in \mathbb{R}$ viene indicata come:
	+ $\sum^{+ \infty}_{n = 1} q^n$
+ Essa:
	+ **Converge** per $|q| < 1$
	+ **Diverge** a $+ \infty$ per $q \geq 1$ 
	+ **È indeterminata** per $q \leq -1$ 
+ Infatti, tramite un semplice prodotto, troviamo che:
	+ $\sum^{+ \infty}_{n = 1} q^n = \cfrac{q - q^{n+1}}{1 - q}$
+ Si può quindi anche calcolare:
	+ Dato $|q| < 1$
	+ $\sum^{+ \infty}_{n = 0} q^n = 1 + \cfrac{q}{1 - q} = \cfrac{1}{1-q}$
		+ Questo è uno dei risultati più importanti del mondo della matematica
#### Serie Armonica Generalizzata 
+ La serie armonica viene indicata come:
	+ $\sum^{+ \infty}_{n = 1} \cfrac{1}{n^\alpha} \quad \alpha > 0$
+ Essa:
	+ **Converge** per $\alpha > 1$
	+ **Diverge**  per $\alpha \leq 1$ 
### Serie non Positive
+ I criteri visti in precedenza valgono solo per serie positive
+ Come ci comportiamo per **serie non positive**?
+ Possiamo usare il seguente criterio:

> [!Proposizione]
> ### Criterio di Convergenza Assoluta
> + Si dice che una serie $a_n$ **converge assolutamente** se converge la serie $\sum^{+ \infty}_{n = 1} | a_n |$

> [!Proposizione]
> ### Sulla Convergenza Assoluta
> + $\sum^{+ \infty}_{n = 1} | a_n | < + \infty \quad \to \quad \sum^{+ \infty}_{n = 1} a_n$ converge

+ Possiamo quindi usare la convergenza assoluta per capire se una successione converge, ma **non** per capire se non converge
---
+ Le **serie a segno alterno** sono una categoria di serie di forma:
	+ $\sum^{+ \infty}_{n = 1} (-1)^{n+1} a_n \quad a_n > 0$
+ Esse servono per comprendere il seguente criterio:

> [!Proposizione]
> ### Criterio di Leibniz
> + Sia $(a_n)_{n \geq 1}$ una successione tale che:
> 	1. $a_n \geq 0 \quad \forall n \geq 0 \quad$ **positiva**
> 	2. $\lim_{m \to \infty} a_n = 0 \quad$ **infinitesima**
> 	3. $a_{n + 1} < a_n \quad \forall n \geq \quad$ **decrescente**
>  + Allora la seguente serie a segno alterno:
> 	 + $\sum^{+ \infty}_{n = 1} (-1)^{n + 1} a_n$
> + **Converge**, e la somma $s$ della serie soddisfa la seguente uguaglianza:
> 	+ $| s - s_n| \leq a_{n + 1} \quad \forall n \geq 1$

## Serie di Funzioni
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
---
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
> 	2. La serie $\sum^{\infty}_{n=1} f_n$ converge **totalmente** in $[a,b]$ a  $f$
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
## Serie di Fourier
+ Vediamo inizialmente il concetto di periodicità
>[!Concetto]
> ### Periodicità
> + La funzione $f : \mathbb{R} \to \mathbb{R}$ viene detta $T$-**periodica** se vale:
> 	+ $f(x + T) = f(x) \qquad \forall x \in \mathbb{R}, \; T >0$
> + Essa viene detta **nota** se è nota in $[a, a+T] \; \forall a \in \mathbb{R}$

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
	+ $i(\hat{f_k} - \hat{f_{-k}}) = \frac{2}{T} \int^{\frac{T}{2}}_{-\frac{T}{2}} f(x) \sin(\frac{2 \pi}{T} kx) dx = b_k$
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
## Serie di Potenze
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
> + Se $\exists \lim_{x \to \infty} \sqrt{|a_n|}^n = l \in [0, +\infty) \cup \{ + \infty\}$ vale:
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
## Serie di Taylor
+ Con le nostre nuovo conoscenze sulle serie, possiamo ridefinire il polinomio di Taylor come serie:

>[!Definizione]
> ### Serie di Taylor
> + Sia $I \in \mathbb{R}$ un intervallo aperto, e sia $f$ definita su $I$ e derivabile infinite volte in esso
> + Prendiamo un punto in $I$. Fissato $x \in I$, la serie di potenze:
> 	+ $\sum^{+\infty}_{0} \cfrac{f^{(n)} x_0}{n!}(x - x_0)^n$
> + Viene chiamata la Serie di Taylor di $f$ centrata in $x_0$
> + $f$ viene detta **sviluppabile** in Serie di Taylor se:
> 	+ $f(x) = \sum^{+\infty}_{0} \cfrac{f^{(n)} x_0}{n!}(x - x_0)^n \qquad \forall x \in I$

+ Ricordiamo che, per via dell'**univocità di Taylor,** se una funzione è sviluppabile in una serie di potenze $f(x) = \sum^{+\infty}_{0} a_n(x - x_0)^n$, questa serie è la serie di Taylor

>[!Teorema]
> ### Sviluppabilità
> + Sia $I \in \mathbb{R}$ un intervallo aperto, e sia $f$ definita su $I$ e derivabile infinite volte in esso
> + Se esistono $M, L > 0$ tali che:
> 	+ $|f^{(n)} (x)| \leq ML^n \qquad \forall x \in I, \forall n \in \mathbb{N}$
> + Allora $f$ è sviluppabile in Serie di Taylor  in $I$ $\forall x_0 \in I$

# 2 - Spazi Multidimensionali
## Cose utili che segno

> [!Corollario]
> + Sia $f : A \in \mathbb{R}^2 \to \mathbb{R}$ differenziabile
> + Allora:
> 	+ $\forall p_0 \in A$ e $\forall v = (v_1, v_2) \in \mathbb{R}^2$, $\exists$ finito:
> 		+ $\lim_{t \to 0} \cfrac{f(p_0 + tv) - f(p_0)}{t} = \triangledown f(p_0) \cdot v$
> 	+ Se il limite esiste viene chiamato **derivata direzionale** rispetto a $v$ in $p_0$, indicata come $\frac{df}{dv}(p_0)$
> + Possiamo calcolare la derivata direzionale tramite il gradiente. 
> + **Possiamo usarlo al contrario** per dimostrare che qualcosa non è differenziabile

---
+ Possiamo fare derivate seconde anche in più dimensioni
+ Esse vengono raccolte nella **matrice Hessiana**:
	+ $H = \begin{bmatrix}\frac{\partial^2 f}{\partial x^2} (x, y) & \frac{\partial^2 f}{\partial y \partial x} (x, y) \\ \frac{\partial^2 f}{\partial x \partial y} (x, y) & \frac{\partial^2 f}{\partial y^2} (x, y)\end{bmatrix}$
+  Se vale $f \in C^2 (A)$ (tutte le 4 derivate sono continue), allora le derivate "miste" sono uguali fra loro, per ogni $(x, y)$
---
+ Esiste una versione multidimensionale del teorema di La Grange
---
+ Del Dini
+ Estremi vincolati
+ Curve