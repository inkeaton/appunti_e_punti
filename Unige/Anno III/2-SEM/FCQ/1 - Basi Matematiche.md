+ Per spiegare molti dei concetti fisici che introdurremo, abbiamo bisogno di vari concetti matematici
---
#### Numeri Complessi
+ I **numeri complessi** vengono scritti come:
	+ $a + b \cdot i$
		+ $a, b \in \mathbb{R}$
		+ $i = \sqrt{-1}$
+ Dati due numeri $z = a + b \cdot i$ e $w = c + d \cdot i$ abbiamo che:
	+ $z + w = (a + i \cdot b) + (c + i \cdot d) = (a + c) + i \cdot (b + d)$
	+ $z · w = (a + i \cdot b) · (c + i \cdot d) = (ac - bd) + i \cdot (ad + bc)$
+ Il **complesso coniugato** di $z$ viene indicato come:
	+ $z^* = a - b \cdot i$
+ Vale che:
	+ $z \cdot z^* = a^2 + b^2$
+ Il **modulo** di un numero complesso viene calcolato come:
	+ $|z| = \sqrt{a^2 +b^2}$
---
+ Ogni numero complesso può esser visto come un **punto** su un asse. Dunque, possiamo indicarlo attraverso il **vettore** associato al punto
	+ $z = |z|(\cos{\theta}  + i \sin{\theta}) = |z|e^{i \theta}$
		+ Dove $\theta$ è l'angolo del vettore con il piano
#### Spazi Vettoriali
+ Un **vettore** possiede tre proprietà:
	+ **Modulo**
		+ Lunghezza
	+ **Direzione**
		+ Retta su cui si trova
	+ **Verso**
		+ Direzione in cui punta
+ Più vettori possono essere **sommati** tramite la **regola del parallelogramma**. Se i vettori sommati appartenevano allo stesso spazio vettoriale, allora anche il vettore risultante vi apparterrà
+ La **moltiplicazione per scalare** viene definita come:
	+ $\alpha \cdot v$
+ Se $\alpha < -1$, otteniamo $-v$, il **vettore opposto** a $v$. Possiede ugual modulo e direzione, ma verso opposto.
	+ La loro somma è uguale a 0
+ Uno spazio vettoriale è **chiuso** rispetto a somma e moltiplicazione scalare
---
+ Il **prodotto scalare** viene definito come:
	+ $< u, v > \to \mathbb{C}$ 
+ Esso rispetta le seguenti proprietà:
	+ $\forall u \in V \quad <u, u> = n \in \mathbb{R}, \quad n > 0$
		+ $n = 0 \to u = 0$
	+ $\forall u, v \in V \quad < u, v > = <v, u>$
	+ $\forall u, v, w \in V, \; \forall \alpha, \beta \in \mathbb{C} \quad <w, \alpha u + \beta v > = \alpha <w, u > + \beta < w, v >$
+ Due vettori sono **ortogonali** se vale $< v, u > = 0$
+ La **norma** di un vettore vale $\sqrt{< u, u>}$
+ Un vettore è **normalizzato** se vale $< u, u > = 1$
+ Due vettori normali ortogonali vengono detti **ortonormali**
---
#### Basi
+ Fissata una base ortonormale, ogni vettore può essere indicato come una **somma di componenti della base**, associati ad un coefficiente. Essi rappresentano la proiezione del vettore sugli assi dello spazio
	+ $w = \alpha u_0 + \beta v_0$
+ Possiamo vedere che:
	+ $< u_0, w > = <u_0, \alpha u_0 + \beta v_0 > = \alpha <u_0, u_0 > + \beta < u_0, v_0> = \alpha$ 
	+ $< v_0, w > = <v_0, \alpha u_0 + \beta v_0 > = \alpha <v_0, u_0 > + \beta < v_0, v_0> = \beta$ 
+ Le basi possono anche essere indicate nella **forma matriciale**
	+ $u_0 = \begin{pmatrix}   1 \\  0   \end{pmatrix}$
	+ $v_0 = \begin{pmatrix}   0 \\  1   \end{pmatrix}$
	+ Vediamo infatti che:
		+ $< u_0, v_0 > = (u_0^T)^* v_0 = u_0 = \begin{pmatrix}   1 &  0   \end{pmatrix} \cdot \begin{pmatrix}   0 \\  1   \end{pmatrix} = 0$
+ Possiamo indicare i vettori in modo simile:
	+ $w = \alpha u_0 + \beta v_0 = \alpha \begin{pmatrix}   1 \\  0   \end{pmatrix} + \beta \begin{pmatrix}   0 \\  1   \end{pmatrix} = \begin{pmatrix}   \alpha \\  \beta   \end{pmatrix}$
#### Ket e Bra
+ Una notazione per i vettori spesso usata è quella di bra e ket
	+ **Ket** è il vettore **normale**
		+ $| v > = v$
	+ **Bra** è il vettore **trasposto coniugato**
		+ $< v | = (v^T)^*$
+ Questa notazione **facilita** la **scrittura** di **prodotti vettoriali**
#### Operazioni su Spazi Vettoriali
+ Presi due spazi vettoriali $V$ e $W$, ognuno definito dalle rispettive basi $A$ e $B$, definiamo la **somma diretta** come:
	+ $V \oplus W := \{(|v > , |w>) \quad \text{tali che} \quad |v> \in V \wedge |w> \in W\}$
		+ *(si comporta come uno XOR, somma modulo 2)*
+ Questo nuovo spazio ha dimensione uguale alla somma delle dimensioni di $V$ e $W$
+ Questo insieme è un nuovo spazio vettoriale rispetto alla **somma**, ridefinita come:
	+ $|u> + |u'> := (|v> + |v'>)\oplus (|w> + |w'>)$
		+ $|u> = |v> \oplus |w>$
		+ $|u'> = |v'> \oplus |w'>$
+ Vediamo quindi che la somma è ottenuta sommando separatamente i vettori nelle loro basi
+ Se il **prodotto** scalare è permesso nelle basi originali, esso può esistere anche in questa, in modo analogo:
	+ $\langle u | u' \rangle = ( \langle v | \oplus \langle w |) \cdot ( \langle v' | \oplus \langle w' |) := \langle v || v' \rangle + \langle w || w' \rangle$
	+ Il prodotto scalare di $V \oplus W$ si ottiene sommando i prodotti scalari di $V$ e $W$
#### Prodotto Tensore
+ Consideriamo due spazi vettoriali $V$ e $W$, ognuno definito dalle rispettive basi $A$ e $B$. $\dim{A} = n, \dim{B}=m$
+ Il **prodotto tensore** $\otimes$ è un nuovo spazio vettoriale con $\dim{(V \otimes W )} = nm$
+ La nuova base avrà come basi nuovi vettori ortonormali, tecnicamente ottenuti da quelli di partenza. I loro valori vengono scelti da noi
+ I suoi elementi sono della forma:
	+ $| \alpha_i \rangle_V \otimes | \beta_j \rangle_W$
		+ Scrivibile anche come $|\alpha_i \beta_j \rangle$
+ Esso soddisfa le seguenti proprietà:
	+ $\forall | v \rangle, |v' \rangle \in V, | w \rangle \in W \quad (| v \rangle + |v' \rangle) \otimes |w \rangle = | v \rangle \otimes | w \rangle + | v' \rangle \otimes | w \rangle$
	+ $\forall | v \rangle \in V, | w \rangle, |w' \rangle \in W \quad   |v \rangle \otimes (| w \rangle + |w' \rangle) = | v \rangle \otimes | w \rangle + | v \rangle \otimes | w' \rangle$
	+ $\forall | v \rangle \in V, | w \rangle \in W, \alpha \in \mathbb{C} \quad (\alpha |v \rangle) \otimes | w \rangle = |v \rangle \otimes (\alpha | w \rangle) = \alpha( | v \rangle \otimes | w \rangle)$
+ Se $V$ e $W$ ammettono prodotto scalare, $V \otimes W$ ammette il **prodotto scalare** definito come:
	+ $\langle u | u' \rangle = (\langle v | \otimes \langle w |) \cdot (|v' \rangle \otimes |w' \rangle) := \langle v | v' \rangle \cdot \langle w | w' \rangle$ 
+ La **norma** del vettore è quindi uguale al prodotto della **norma** dei vettori di partenza
---
+ Consideriamo due vettori indicati tramite le loro basi ortonormali:
	+ $| v \rangle = a | \alpha_1 \rangle + b | \alpha_2 \rangle$
	+ $| w \rangle = c | \beta_1 \rangle + d | \beta_2 \rangle$
+ Il loro prodotto tensore è uguale a:
	+ $|v\rangle \oplus | w \rangle \quad = \quad ac |\alpha_1 \rangle \oplus | \beta_1 \rangle + ad |\alpha_1 \rangle \oplus | \beta_2 \rangle + bc |\alpha_2 \rangle \oplus | \beta_1 \rangle + bd |\alpha_2 \rangle \oplus | \beta_2 \rangle$
+ Abbiamo quindi ottenuto un nuovo vettore, che vive nello spazio vettoriale $V \otimes W$, con basi $C = \{|\alpha_1 \beta_1\rangle + |\alpha_1 \beta_2\rangle + |\alpha_2 \beta_1\rangle + |\alpha_2 \beta_2\rangle\}$
#### Operatori
+ Lavorando con i vettori, le operazioni risulteranno essere **matrici**
+ Lavorando in un ipotetico spazio $A = \{|\alpha_1\rangle, \cdots, | \alpha_n \rangle\}$, ogni elemento della matrice $O_{n \times n}$ sarà della forma:
	+ $O_{ij} = \langle \alpha_i | o | \alpha_j \rangle$ 
		+ Dove $o$ è scelto da noi
+ Essi sono solitamente scritti con la forma **ket-bra**
	+ Dati due vettori $| v \rangle, | w \rangle$ e un operazione $O$, tali che:
		+ $O(| v \rangle) = | w \rangle$
	+ Definiamo l'operazione come:
		+ $O = |w \rangle \langle v |$
			+ Se pensiamo alle operazioni fra vettori ha senso, in quanto si ottiene una matrice
+ È come se stessimo indicando la nostra operazione dando un **esempio** di come funziona
+ Un esempio d'utilizzo è il seguente:
	+ $O(| v \rangle) = (|w \rangle \langle v |)| v \rangle = (\langle v | v \rangle) | w \rangle = | w \rangle$
#### Operatori Hermitiani
+ Essi sono una particolare categoria di operatori che rispettano la seguente proprietà:
	+ $O^{\dagger} = O$ 
+ Il **trasposto coniugato** dell'operatore **è se stesso**!
+ Dato un vettore $| v\rangle$, se vale:
	+ $O | v \rangle = \lambda | v \rangle \qquad \lambda \in \mathbb{C}$
+ Allora si dice che:
	+ $| v \rangle$ **autostato** di O
	+ $\lambda$ **autovalore** di O
+ In particolare, se O è **hermitiano**, allora $\lambda \in \mathbb{R}$
+ Vale inoltre il seguente **teorema**:
	+ Dati gli autostati di $O$ $|v \rangle, |w \rangle$ ed i loro autovalori $v, w$ 
	+ Se $v \neq w$, allora $\to$ $\langle v | w \rangle = 0$, ovvero i due vettori sono **ortogonali** 