+ Come detto in precedenza, una funzione può venire campionata attraverso il **treno d'impulsi**
+ Che aspetto la **trasformata** di una funzione campionata in tal modo?
+ Dato che $f_s(t) = f(t)\delta_t(t)$, possiamo applicare il teorema della convoluzione, ed ottenere
	+ $F_s(\omega) = \cfrac{1}{\tau} \sum^{+\infty}_{n = -\infty} F(\omega-\cfrac{\omega}{\tau})$
	+ E’ una **sequenza infinita e periodica** di copie di $F(\omega)$ con ampiezza del periodo $\cfrac{1}{\tau}$ 
---
+ Una funzione $f(t)$ viene detta a **banda limitata**  se la sua trasformata di Fourier è nulla al di fuori dell’intervallo $[ -\omega_{MAX}, \omega_{MAX}]$ 
---
+ Vediamo quindi il **teorema del campionamento**:
	+ Consideriamo una funzione continua $f(t)$ a banda limitata. 
	+ Una ricostruzione perfetta del segnale è garantita se la frequenza di campionamento è almeno il **doppio** della frequenza massima del segnale
		+ $\cfrac{1}{\tau} > 2\omega_{MAX}$ 
	+ Nel caso sia inferiore, avviene il cosiddetto effetto di **aliasing**, in cui le sezioni periodiche si intersecano e rovinano il segnale
	+ Tramite un operazione di filtraggio, usando un'altra funzione, è possibile poi recuperare $F(\omega)$ da $F_s(\omega)$, e quindi $f(t)$
---
