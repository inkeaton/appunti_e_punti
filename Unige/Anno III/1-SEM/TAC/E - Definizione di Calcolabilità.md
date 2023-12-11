+ Secondo la Tesi di **Church-Turing** la nozione di **T-Calcolabile** è **equivalente** a quella di **calcolabile**
	+ Si dice anche che è **ricorsiva**, sinonimo di calcolabile
+ Questa idea è supportata da varie nozioni
	+ Tutti gli altri formalismi proposti ($\mu$-ricorsive, $\lambda$-calcolo, macchine a registri, linguaggi di programmazione) si sono rivelati equivalenti
	+ Tutte le funzioni intuitivamente calcolabili sono risultate T-Calcolabili
	+ Le prove delle equivalenze fra formalismi avvengono per modalità **costruttiva**, ovvero attraverso la creazione di algoritmi di "traduzione"
+ Come usiamo questo concetto?
	+ Per **dimostrare** che una funzione è **calcolabile**, basta dimostrare che **esiste** una **macchina** in grado di calcolarla, fornendo anche solo un algoritmo informale
---
+ **Quante sono** le $MdT$? sono infinite, numerabili (in quanto rappresentabili come stringhe) e superiori al numero di funzioni calcolabili (anch'esse infinite numerabili), in quanto esistono un numero infinito di macchine che possono rappresentare la stessa funzione
	+ Ovviamente, dire che $f$ è calcolabile è diverso dal dire che conosciamo una macchina di Turing per $f$
+ Il numero di $f$ ricorsive totali è sempre numerabile, anche se inferiore al numero di funzioni ricorsive totali 
---
+ Cos'è la **macchina di Turing universale**?
	+ È una macchina che prende in input la descrizione di una macchina ed un input, e restituisce l'output di quella macchina su quell'input
+ Sarebbe una vera e propria macchina **programmabile**, di cui possiamo decidere le istruzioni
+ Esiste? Certo, possiamo descriverla come:
	+ $f_u(x, y) = \begin{dcases}f_x(y) \quad \text{se  } f_x(y) \downarrow \\ \uparrow \quad \text{altrimenti}\end{dcases}$
+ Essa è una funzione ricorsiva in quanto possiamo dare un semplice algoritmo per calcolarla:
```
input x, y
trovo Mx
return Mx(y)
```
+ Questa macchina è un **interprete**, o calcolatore programmabile
---
+ Vediamo un esempio di funzione **non-calcolabile**, l'**Halting Problem
	+ $f_H(x, y) = \begin{dcases} 1 \quad \text{se  } f_x(y) \downarrow \\0 \quad \text{altrimenti}\end{dcases}$
+ Per essere calcolabile, deve necessariamente esistere un programma in grado di calcolarla
+ La prima idea consiste nell'eseguire $f_x(y)$ e controllare il risultato
	+ Ma un programma del genere non sarebbe in grado di terminare, nel caso in cui $f_x$ non terminasse
	+ Dobbiamo per forza andare ad analizzare il programma di $f_x$...
+ Proviamo prima ad analizzare la versione **diagonalizzata** di $f_H$
	+ $f_K(x) = \begin{dcases} 1 \quad \text{se  } f_x(x) \downarrow \\0 \quad \text{altrimenti}\end{dcases}$
+ Questa **non può** essere ricorsiva. Consideriamo la seguente funzione $g$
	+ $g(x) = \begin{dcases} \uparrow \quad \text{se  } \mathcal{M}_K(x) \text{ termina} \\1 \quad \text{altrimenti}\end{dcases}$
+ Se $f_K$ è calcolabile, dobbiamo essere in grado di capire se una macchina non termina. Se sappiamo farlo, anche $g$ è calcolabile (l'algoritmo è facilmente intuibile )
+ Ma se è calcolabile, esiste $z \; | \; f_z = g$ 
+ Quindi possiamo calcolare:
	+ $g(z) = \begin{dcases} \uparrow \quad \text{se  } g(z) \downarrow \\1 \quad \text{se  } g(z) \uparrow\end{dcases}$
+ Questo è ovviamente un paradosso
+ Quindi $g$ non è calcolabile, e quindi nemmeno $f_K$, e quindi nemmeno $f_H$ (per riduzione) 
---
