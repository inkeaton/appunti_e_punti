+ Tutte le trasformazioni quantistiche si effettuano tramite trasformazioni **unitarie**, le quali sono:
	+ **Lineari**
		+ $U | \psi \rangle = \alpha U | 0 \rangle + \beta U | 1 \rangle$ 
	+ **Reversibili**
		+ $\exists U^{-1} \to U^{-1}U = \mathbb{1}$
+ Esse inoltre **conservano il prodotto scalare**:
	+ $\langle a' | b' \rangle = (\langle a | U^{-1})(U | b \rangle) = \langle a | b \rangle$
---
+ Operatori classici sono le trasformazioni di Pauli:
	+ $\mathbb{1}$ (L'**identità**)
		+ $\mathbb{1} | 0 \rangle = | 0 \rangle$
		+ $\mathbb{1} | 1 \rangle = | 1 \rangle$
		+ $\mathbb{1} = \begin{pmatrix} 1 & 0 \\ 0 & 1\end{pmatrix}$
	+ $X$
		+ $X | 0 \rangle = | 1 \rangle$
		+ $X | 1 \rangle = | 0 \rangle$
		+ $X = \begin{pmatrix} 0 & 1 \\ 1 & 0\end{pmatrix}$
	+ $Z$
		+ $Z | 0 \rangle = | 0 \rangle$
		+ $Z | 1 \rangle = -| 1 \rangle$
		+ $Z = \begin{pmatrix} 1 & 0 \\ 0 & -1\end{pmatrix}$
	+ $Y$
		+ $Y | 0 \rangle = -i| 1 \rangle$
		+ $Y | 1 \rangle = | 0 \rangle$
		+ $Y = \begin{pmatrix} 0 & -i \\ i & 0\end{pmatrix}$
+ Di queste, **solo $X$ e $Z$ sono veramente necessarie**, in quanto l'identità è banale, e possiamo ottenere $Y = -i X Z$
+ Possiamo usarle per scrivere tutte le operazioni a singolo qubit necessarie
+ Un altro operatore utile è la **porta di Hadamard** 
	+ $H$
		+ $H | 0 \rangle = | + \rangle$
		+ $H | 1 \rangle = | - \rangle$
	+ Genericamente:
		+ $H|k\rangle = \cfrac{1}{\sqrt{2}} \sum^{1}_{z = 0} (-1)^{kz} |z \rangle$
+ Permette di passare dalla base canonica a quella $\pm$ 
+ Anch'essa può esser scritta con $X$ e $Z$
---
+ Esistono anche porte a **multipli qubit**. La più utile è la **Control-Not**
	+ $C_1NOT_2$
		+ $C_1NOT_2 | 00 \rangle = | 00 \rangle$
		+ $C_1NOT_2 | 01 \rangle = | 01 \rangle$
		+ $C_1NOT_2 | 10 \rangle = | 11 \rangle$
		+ $C_1NOT_2 | 11 \rangle = | 10 \rangle$
+ Essa **inverte il valore del secondo qubit** sulla base del **primo** bit di **controllo**
+ L'insieme formato da $X$, $Z$ e $C_1NOT_2$, è un **insieme di porte universali**, con cui è possibili effettuare tutte le operazioni necessarie su un insieme di qubit
---
+ Un metodo per **rappresentare** uno stato è la **sfera di Bloch**, che lo riduce ad un **punto**, sulla superficie di una **sfera** unitaria $x^2 + y^2 + z^2 = 1$
+ Esso viene riscritto come:
	+ $| \psi \rangle = \cos \frac{\theta}{2} | 1 \rangle + \sin \frac{\theta}{2} e^{i \phi}| 0 \rangle$ 
+ Le sue coordinate sugli assi si ottengono tramite le **operazioni di Pauli**:
	+ $x = \langle \psi | X | \psi \rangle = \sin \theta \cos \phi$
	+ $y = \langle \psi | Y | \psi \rangle = \sin \theta \sin \phi$
	+ $z = \langle \psi | Z | \psi \rangle = \cos \theta$
+ Gli angoli sono rispettivamente:
	+ $\theta$: Angolo fra il punto e l'asse $z$
	+ $\phi$: Angolo fra il punto e l'asse $x$
+ Possiamo immaginare le **operazioni unitarie** di Pauli come **rotazioni** intorno ai rispettivi assi