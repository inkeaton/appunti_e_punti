+ Semplici **trasformazioni** sui segnali sono:
	+ **Traslazione** $\qquad \phi(t_0) = f(t - t_0)$ 
	+ **Scalatura** $\qquad \phi(t) = f(at)$ 
	+ **Inversione** $\qquad \phi(t) = f(-t)$ 
---
+ Alcuni segnali **famosi** sono:
	+ **Rettangolare**
		+ $\text{rect}(t) = \begin{dcases} A \quad |t| < \frac{W}{2} \\ 0 \qquad |t| > \frac{W}{2} \end{dcases}$
		+ $A$ e $W$ sono valori scelti arbitrariamente
	+ **Gradino**
		+ $u(t) = \begin{dcases} 1 \qquad t > 0 \\ 0 \qquad t < 0 \end{dcases}$
	+ **Impulso** (Delta di Dirac)
		+ $\delta(t) = \begin{dcases} \infty \qquad t = 0 \\ 0 \qquad t \neq 0 \end{dcases}$
	+ Impulso **Discreto**
		+ $\delta(x) = \begin{dcases} 1 \qquad x = 0 \\ 0 \qquad x \neq 0 \end{dcases}$
+ La Delta in particolare è molto utile
+ Una sua variante traslata, il **Treno d'Impulsi**, può essere usato come **campionatore**, moltiplicando la funzione che vogliamo campionare per esso
---
+ Tutte le funzioni continue e periodiche possono essere scritte come **somme pesate** di sinusoidi
+ Questo è possibile grazie alla cosiddetta **Serie di Fourier**
+ È possibile ottenere una scrittura simile per qualunque tipo di funzione. Questa viene chiamata **Trasformata di Fourier**
	+ Si tratta di un processo invertibile
+ Prendiamo quindi una funzione continua e periodica, di periodo $T$
+ Essa può quindi essere scritta come
	+ $f(t) = \sum^{+\infty}_{-\infty} C_n \cdot e^{j \cfrac{2 \pi n}{T} t}$ 
		+ I vari $C_n$ non sono altro che i pesi della somma per ognuna delle sinusoidi
		+ $e^{j \cfrac{2 \pi n}{T} t}$ è un numero complesso, $j$ è la componente immaginaria
+ La sua **Trasformata** di Fourier è quindi:
	+ $\mathcal{F}\{f (t)\} = \int^{+\infty}_{-\infty} f (t) e^{-j 2 \pi \omega t} dt = F (\omega)$ 
	+ La sua inversa è
		+  $f (t) = \int^{+\infty}_{-\infty} F (\omega) e^{j 2 \pi \omega t} d\omega$ 
+ Una proprietà importante è il **cambio di fase**:
	+ $F[f(t - \tau)] = F(\omega) \cdot e^{-j 2 \pi \omega \tau}$ 
---
+ Un esempio è la funzione $\text{rect}$, la cui trasformata è la funzione $\text{sinc}$
	+ $\textcolor{Apricot}{\text{sinc}}(\omega) = AW \cdot \cfrac{\sin(\pi\omega W)}{\pi \omega W}$  
+ La trasformata della funzione **impulso** è invece la costante **1**
+ Invece, quella dell'**impulso traslato** è:
	+ $F(\omega)= \cos(-2\pi j \omega t_0)- j \sin(-2\pi j \omega t_0)$ 
+ Possiamo notare come **piccoli cambiamenti** nello spazio reale, del tempo, portano a **grandi variazioni** nello spazio di Fourier, delle frequenze 
---
+ Un operazione comune fra segnali è la **convoluzione**
+ Viene definita come:
	+ $c(t) = f(t) * h(t) = \int^{+\infty}_{-\infty} f(\tau) \cdot h(t- \tau) d\tau$ 
+ Una proprietà molto importante è la seguente (**Teorema di Convoluzione**):
	+ $\mathcal{F}\{f(t) * h(t)\} = H(\omega) \cdot F(\omega)$ 
	+ $\mathcal{F}\{f(t) \cdot h(t)\} = H(\omega) * F(\omega)$ 
+ Calcolare la **convoluzione** su un computer è molto **complesso**, a causa del calcolo dell'integrale
+ Data la precedente proprietà, ci basta eseguire l'operazione **nello** spazio di **Fourier**, e viceversa, per **semplificare** l'operazione