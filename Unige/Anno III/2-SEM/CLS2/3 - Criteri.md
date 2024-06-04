+ Vedremo alcuni **criteri** che ci **aiuteranno** ad analizzare il comportamento di alcune serie
+ Un primo criterio, utile a dimostrare i successivi, è il seguente:

> [!Teorema]
> ### Criterio di Couchy
> + Se la serie $\sum^{\infty}_{n = 1} a_n$ converge, allora vale che $\lim_{n \to +\infty} a_n = 0$

#### Serie Positive
+ Esse sono serie in cui i valori che vengono sommati sono solo positivi
+ Vale per esse la seguente proposizione:

> [!Proposizione]
> ### Comportamento Serie Positive
> + Data una serie positiva $\sum^{\infty}_{n=0} a_n$, essa può comportarsi in solo due modi:
> 	+ **Converge** ad un numero finito positivo
> 	+ **Diverge** a $+ \infty$

+ Del resto, se ci pensiamo, una successione positiva è una **funzione monotona crescente**. 
+ Per queste serie positive, esistono numerosi criteri utili. Il primo è il criterio del confronto

> [!Proposizione]
> ### Criterio del Confronto
> + Prendiamo due successioni positive $a_n$ e $b_n$ tali che:
> 	+ $0 \leq a_n \leq b_n$
> + Allora vale che:
> 	+ Se $\sum^{\infty}_{n=0} b_n < + \infty$, allora $\sum^{\infty}_{n=0} a_n < + \infty$
> 	+ Se $\sum^{\infty}_{n=0} a_n = + \infty$, allora $\sum^{\infty}_{n=0} b_n = + \infty$

+ La dimostrazione è intuibile: se $b_n$ è finito, un valore minore di esso deve essere finito. A sua volta, se $a_n$ è infinito, un valore superiore ad $a_n$ deve essere infinito
+ Un criterio di natura simile è quello del confronto asintotico:

> [!Proposizione]
> ### Criterio del Confronto Asintotico
> + Prendiamo due successioni positive $a_n$ e $b_n$ tali che:
> 	+ $a_n = b_n \cdot c_n$
> + Vale che:
> 	+ Se $\lim_{n \to +\infty} c_n = c > 0$, allora  $\sum^{\infty}_{n=0} b_n$ e $\sum^{\infty}_{n=0} a_n$ possiedono lo **stesso carattere**
> 	+ Se $\lim_{n \to +\infty} c_n = 0$, e  $\sum^{\infty}_{n=0} b_n$ converge, anche $\sum^{\infty}_{n=0} a_n$ **converge**
> 	+ Se $\lim_{n \to +\infty} c_n = + \infty$, e  $\sum^{\infty}_{n=0} b_n$ diverge, anche $\sum^{\infty}_{n=0} a_n$ **diverge**

+ Si noti che rimangono dei casi **non coperti** da questo criterio:

> [!Osservazione]
> ### Sul Confronto Asintotico
>  + Nei seguenti casi:
> 	+ $\lim_{n \to + \infty} \cfrac{a_n}{b_n} \to 0$ e $\sum b_n = + \infty$
> 	+ $\lim_{n \to + \infty} \cfrac{a_n}{b_n} \to + \infty$ e $\sum b_n < + \infty$
> + Non si può concludere niente sul carattere di $\sum a_n$

+ Vediamo quindi altri tre criteri utilizzati per le serie positive. Il primo di questi è il criterio della radice:

> [!Proposizione]
> ### Criterio della Radice
> + Prendiamo una serie positiva $\sum a_n$ tale che esiste:
> 	+ $\lim_{n \to \infty} \sqrt{a_n}^n = \ell \in [0, + \infty) \cup \{ + \infty \}$
> + Valgono i seguenti:
> 	1. Se $\ell < 1$, allora  $\sum a_n < + \infty$ 
> 	2. Se $\ell > 1$, allora  $\sum a_n = + \infty$ 
> 	3. Se $\ell = 1$, allora  **non possiamo dire niente** su $\sum a_n$ 

+ Simile nel suo significato è il criterio del rapporto

> [!Proposizione]
> ### Criterio del Rapporto
> + Prendiamo una serie positiva $\sum a_n$ tale che esiste:
> 	+ $\lim_{n \to \infty} \frac{a_n + 1}{a_n} = \ell \in [0, + \infty) \cup \{ + \infty \}$
> + Valgono i seguenti:
> 	1. Se $\ell < 1$, allora  $\sum a_n < + \infty$ 
> 	2. Se $\ell > 1$, allora  $\sum a_n = + \infty$ 
> 	3. Se $\ell = 1$, allora  **non possiamo dire niente** su $\sum a_n$ 

+ Infatti, immaginiamo che $\ell < 1$. Ciò vuol dire che $\frac{a_n + 1}{a_n} \leq q < 1$, dove $q$ è un numero minore di 1
+ Dunque:
	+ $a_2 \leq q a_1$
	+ $a_3 \leq q a_2 \leq q^2 a_1$
	+ $\cdots$
	+ $a_n \leq q^n a_1$
	+ $\sum a_n \leq a_1 \sum q^n$
+ $\sum q^n$ non è che la serie geometrica. Abbiamo visto che essa converge per $q < 1$

+ L'ultimo di questi criteri è il **criterio integrale**.
+ Immaginiamo di avere una funzione $f$ positiva **decrescente**
+ Se prendiamo una successione $a_n = f(n)$, possiamo immaginare il valore della serie come formato da **blocchi** di altezza $a_n$ e lunghezza 1, in modo simile alla definizione d'integrale.
+ Ogni blocco avrà quindi area $a_n$ e l'area ottenuta dalla somma di questi blocchi sarà uguale al valore della sommatoria
+ Quest'area può essere spostata, e possiamo vederla sia come sotto la funzione $f$, che come sopra
+ Otteniamo quindi il seguente criterio:

> [!Proposizione]
> ### Criterio dell'Integrale
> + Sia $f : [1, + \infty ) \to (0, + \infty)$ decrescente, e sia $a_n = f(n) \forall n$
> + Allora le seguenti cose sono sinonime:
> 	+ $\sum^{+ \infty}_{n = 1} a_n$**converge**
> 	+ $\int^{+ \infty}_{1} f(x) dx$ è **finito**
> + Questo è dovuto alla seguente uguaglianza:
> 	+ $\int^{+ \infty}_{1} f(x) dx \quad \leq \quad \sum^{+ \infty}_{n = 1} a_n \quad \leq \quad a_1 + \int^{+ \infty}_{1} f(x) dx$

+ Questo **criterio** è molto **più forte**, in quanto ci fornisce anche una **stima** del valore della **successione**
+ Esso viene usato per dimostrare il comportamento della serie armonica generalizzata

#### Serie Generiche
+ I criteri visti in precedenza valgono solo per serie positive
+ Come ci comportiamo per **serie non positive**?
+ Possiamo usare il seguente criterio:

> [!Proposizione]
> ### Criterio di Convergenza Assoluta
> + Si dice che una serie $a_n$ **converge assolutamente** se converge la serie $\sum^{+ \infty}_{n = 1} | a_n |$

+ Se riflettiamo, la somma di valori assolutamente finiti, sarà sempre un valore finito
+ Deriviamo la seguente osservazione:

> [!Proposizione]
> ### Sulla Convergenza Assoluta
> + $\sum^{+ \infty}_{n = 1} | a_n | < + \infty \quad \to \quad \sum^{+ \infty}_{n = 1} a_n$ converge

+ Possiamo quindi usare la convergenza assoluta per capire se una successione converge, ma **non** per capire se non converge
#### Serie a Segno Alterno
+ Le serie a segno alterno sono una categoria di serie di forma:
	+ $\sum^{+ \infty}_{n = 1} (-1)^{n+1} a_n \quad a_n > 0$
+ Prendono il loro nome dal fatto che il segno di ogni elemento si alterna al variare di $n$
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

+ *Dimostrazione nelle note*