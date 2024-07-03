+ In questo foglio cercheremo di riassumere i contenuti del corso di **Fondamenti di Computazione Quantistica**
---
# 1 - Basi
## A - Apparato Matematico
+ Per spiegare molti dei concetti fisici che introdurremo, abbiamo bisogno di vari concetti matematici
---
### Numeri Complessi
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
### Spazi Vettoriali
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
### Basi
+ Fissata una base ortonormale, ogni vettore può essere indicato come una **somma di componenti della base**, associati ad un coefficiente. Essi rappresentano la proiezione del vettore sugli assi dello spazio
	+ $w = \alpha u_0 + \beta v_0$
+ Possiamo vedere che:
	+ $< u_0, w > = <u_0, \alpha u_0 + \beta v_0 > = \alpha <u_0, u_0 > + \beta < u_0, v_0> = \alpha$ 
	+ $< v_0, w > = <v_0, \alpha u_0 + \beta v_0 > = \alpha <v_0, u_0 > + \beta < v_0, v_0> = \beta$ 
+ Le basi possono anche essere indicate nella **forma matriciale**
	+ $u_0 = \begin{bmatrix}   1 \\  0   \end{bmatrix}$
	+ $v_0 = \begin{bmatrix}   0 \\  1   \end{bmatrix}$
	+ Vediamo infatti che:
		+ $< u_0, v_0 > = (u_0^T)^* v_0 = u_0 = \begin{bmatrix}   1 &  0   \end{bmatrix} \cdot \begin{bmatrix}   0 \\  1   \end{bmatrix} = 0$
+ Possiamo indicare i vettori in modo simile:
	+ $w = \alpha u_0 + \beta v_0 = \alpha \begin{bmatrix}   1 \\  0   \end{bmatrix} + \beta \begin{bmatrix}   0 \\  1   \end{bmatrix} = \begin{bmatrix}   \alpha \\  \beta   \end{bmatrix}$
### Ket e Bra
+ Una notazione per i vettori spesso usata è quella di bra e ket
	+ **Ket** è il vettore
		+ $| v \rangle = v$
	+ **Bra** è il vettore **trasposto coniugato**
		+ $\langle v | = (v^T)^*$
+ Questa notazione **facilita** la **scrittura** di **prodotti vettoriali**
### Operazioni su Spazi Vettoriali
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
### Prodotto Tensore
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
+ Il prodotto dei prodotti scalari su $V$ e $W$
---
+ Consideriamo due vettori indicati tramite le loro basi ortonormali:
	+ $| v \rangle = a | \alpha_1 \rangle + b | \alpha_2 \rangle$
	+ $| w \rangle = c | \beta_1 \rangle + d | \beta_2 \rangle$
+ Il loro prodotto tensore è uguale a:
	+ $|v\rangle \oplus | w \rangle \quad = \quad ac |\alpha_1 \rangle \oplus | \beta_1 \rangle + ad |\alpha_1 \rangle \oplus | \beta_2 \rangle + bc |\alpha_2 \rangle \oplus | \beta_1 \rangle + bd |\alpha_2 \rangle \oplus | \beta_2 \rangle$
+ Abbiamo quindi ottenuto un nuovo vettore, che vive nello spazio vettoriale $V \otimes W$, con basi $C = \{|\alpha_1 \beta_1\rangle + |\alpha_1 \beta_2\rangle + |\alpha_2 \beta_1\rangle + |\alpha_2 \beta_2\rangle\}$
### Operatori
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
### Operatori Hermitiani
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
## B - Teoria della Misura e Qubit
### Esperimento della Fenditura
### Esperimento del Polarizzatore
---
>[!Teorema]
> ### Teoria della Misura
> + Immaginiamo di voler misurare una proprietà fisica di un sistema
> + La rappresentiamo come un **osservabile** $\Phi$, associato ad un **operatore hermitiano**
> + Immaginiamo un vettore $| \psi \rangle$ che rappresenta lo **stato** del sistema
> + Riscritto nella base di $\Phi$ sarà della forma:
> 	+ $| \psi \rangle = \sum_{i} a_i | \phi_i \rangle$
> + Nel momento in cui misuriamo $\Phi$ otteniamo come **valore uno degli autostati** $\phi$ con **probabilità** $|a_i|^2$
> + In seguito alla misura, il sistema **collassa nell'autostato** corrispondente

---
+ Un **fase** è un numero complesso scrivibile come l'esponenziale di un'unità immaginaria:
	+ $e^{i\lambda}$
+ In fisica quantistica, due stati che si distinguono di una **fase globale** sono **indistinguibili**
	+ $| u \rangle = e^{i\lambda} | u \rangle$
+ Quelli distinti da una fase detta **relativa** sono invece **distinguibili**
	+ $| v \rangle \neq e^{i\lambda} | v \rangle$
+ Questo vuole dire che, presi due stati, essi saranno **distinguibili solo in determinate basi**
---
+ Prendiamo due stati, che chiameremo **qubit**
+ Se effettuiamo il prodotto tensore fra loro, otteniamo un nuovo stato che rappresenta entrambi
+ A seconda della sua forma, lo stato si dice:
	+ **Fattorizzabile**, se è possibile lavorare sui singoli qubit senza influenzare gli altri
	+ **Entangled**, se è impossibile separare fra loro i due qubit e lavorare su di essi separatamente
+ Ad esempio, esistono quattro stati **entangled**, ortonormali, detti **stati di Bell**:
	+ $\cfrac{|00\rangle + |11 \rangle}{\sqrt{2}}$
	+ $\cfrac{|00\rangle - |11 \rangle}{\sqrt{2}}$
	+ $\cfrac{|01\rangle + |10 \rangle}{\sqrt{2}}$
	+ $\cfrac{|01\rangle - |10 \rangle}{\sqrt{2}}$
---
+ Gli stati possono rimanere entangled anche a grandi distanze. Possono quindi essere utilizzati per risolvere problemi di sincronizzazione
## C - Operatori
+ Tutte le trasformazioni quantistiche si effettuano tramite trasformazioni **unitarie**, le quali sono:
	+ **Lineari**
		+ $U | \psi \rangle = \alpha U | 0 \rangle + \beta U | 1 \rangle$ 
	+ **Reversibili**
		+ $\exists U^{-1} \to U^{-1}U = \mathbb{1}$
+ Esse inoltre **conservano il prodotto scalare**:
	+ $\langle a' | b' \rangle = (\langle a | U^{-1})(U | b \rangle) = \langle a | b \rangle$
### Pauli
+ Operatori classici sono le trasformazioni di Pauli:
	+ $\mathbb{1}$ (L'**identità**)
		+ $\mathbb{1} | 0 \rangle = | 0 \rangle$
		+ $\mathbb{1} | 1 \rangle = | 1 \rangle$
		+ $\mathbb{1} = \begin{bmatrix} 1 & 0 \\ 0 & 1\end{bmatrix}$
	+ $X$
		+ $X | 0 \rangle = | 1 \rangle$
		+ $X | 1 \rangle = | 0 \rangle$
		+ $X = \begin{bmatrix} 0 & 1 \\ 1 & 0\end{bmatrix}$
	+ $Z$
		+ $Z | 0 \rangle = | 0 \rangle$
		+ $Z | 1 \rangle = -| 1 \rangle$
		+ $Z = \begin{bmatrix} 1 & 0 \\ 0 & -1\end{bmatrix}$
	+ $Y$
		+ $Y | 0 \rangle = -i| 1 \rangle$
		+ $Y | 1 \rangle = | 0 \rangle$
		+ $Y = \begin{bmatrix} 0 & -i \\ i & 0\end{bmatrix}$
+ Di queste, **solo $X$ e $Z$ sono veramente necessarie**, in quanto l'identità è banale, e possiamo ottenere $Y = -i X Z$
+ Possiamo usarle per scrivere tutte le operazioni a singolo qubit necessarie
### Hadamard
+ Un altro operatore utile è la **porta di Hadamard** 
	+ $H$
		+ $H | 0 \rangle = | + \rangle$
		+ $H | 1 \rangle = | - \rangle$
		+ $H = \cfrac{1}{\sqrt{2}}\begin{bmatrix} 1 & 1 \\ -1 & 1\end{bmatrix}$
	+ Genericamente:
		+ $H|k\rangle = \cfrac{1}{\sqrt{2}} \sum^{1}_{z = 0} (-1)^{kz} |z \rangle$
+ Permette di passare dalla base canonica a quella $\pm$ 
+ Anch'essa può esser scritta con $X$ e $Z$
### CNOT
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
### Inizializzazione Bit
+ Come facciamo ad **inizializzare** la memoria di un computer con i **qubit** tutti inizialmente inizializzati a $|0 \rangle$?
+ Si usa Hadamard, assieme al **Phase Gate**, definito come:
	+ $U_{ph} (\gamma) = \begin{cases} |0 \rangle \to |0 \rangle \\ |1 \rangle \to e^{i \gamma} | 1 \rangle \end{cases}$
+ La procedura è:
	+ $\begin{align}|0 \rangle \overbrace{\to}^H &\cfrac{1}{\sqrt{2}}(|0 \rangle + |1\rangle)\\ \overbrace{\to}^{U_{ph} ( -2 \alpha)} &\cfrac{1}{\sqrt{2}}(|0 \rangle + e^{-2i\alpha}|1\rangle) \\ \overbrace{\to}^{H} &\cfrac{1}{2}(|0 \rangle + |1 \rangle+ e^{-2i\alpha}(|0 \rangle - |1\rangle)) = \\ = &\cfrac{1}{2}((1 + e^{-2i\alpha}) | 0 \rangle + (1 - e^{-2i\alpha}) | 1 \rangle) = \\ = &\underbrace{\cfrac{e^{-i\alpha}}{2}}_{\text{fase globale}} (\underbrace{(e^{i\alpha} + e^{-i\alpha})}_{2\cos \alpha} | 0 \rangle + \underbrace{(e^{i\alpha} - e^{-i\alpha})}_{2 i \sin \alpha} | 1 \rangle) = \\ = &e^{-i\alpha} (\cos \alpha |0 \rangle + i \sin \alpha | 1 \rangle) = \\ \overbrace{\to}^{U_{ph} ( -i \frac{\pi}{2})} &\cos \alpha |0 \rangle + \sin \alpha | 1 \rangle = \\ \overbrace{\to}^{U_{ph} ( \gamma)} &\cos \alpha |0 \rangle + e^{i\gamma} \sin \alpha | 1 \rangle \end{align}$
+ Questo ci permette quindi di **inizializzare qubit** a valori voluti
### No-Cloning e No-Deleting

# 2 - Applicazioni
## A - Vantaggi Quantistici
+ **Perché** un computer **quantistico** è più **vantaggioso** di uno **classico**?
+ Perché esso è **intrinsecamente parallelo**:
	+ Usando **Hadamard**, possiamo riscrivere un insieme di bit come la **sovrapposizione di tutti i loro possibili stati**
	+ Se **applichiamo** una generica **trasformazione** su questo stato, stiamo **contemporaneamente agendo su tutti** questi stati, allo stesso tempo
### Super-Dense Coding
+ È possibile inviare **più di un bit** d'informazione usando un **singolo qubit**. Questo viene chiamato "**superdense coding**"
+ Facciamo un esempio:
	+ Alice e Bob possiedono ciascuno un qubit, e lo stato entangled ottenuto dai due:
		+ $| \Phi \rangle = \cfrac{|0_A0_B \rangle + |1_A1_B \rangle}{\sqrt{2}}$
	+ Alice vuole inviare due bit d'informazione a Bob (una delle sequenze 00, 01, 10, 11)
	+ Essa può applicare sul solo qubit che possiede le seguenti trasformazioni di Pauli:
		+ $00 \xrightarrow{\mathbb{1}} \cfrac{|0_A0_B \rangle + |1_A1_B \rangle}{\sqrt{2}}$
		+ $01\xrightarrow{X} \cfrac{|1_A0_B \rangle + |0_A1_B \rangle}{\sqrt{2}}$
		+ $10 \xrightarrow{Z} \cfrac{|0_A0_B \rangle - |1_A1_B \rangle}{\sqrt{2}}$
		+ $11 \xrightarrow{iY} \cfrac{|0_A1_B \rangle - |1_A0_B \rangle}{\sqrt{2}}$
		+ Questi sono i quattro stati ortogonali di Bell, distinguibili tramite misura
	+ Invia il qubit a Bob
	+ Bob applica ai qubit prima una porta **CNOT**, e poi una porta di **Hadamar**:
		+ $\begin{align}00 \xrightarrow{C_ANOT_B} &\cfrac{|0_A\rangle + |1_A \rangle}{\sqrt{2}} |0_B \rangle \xrightarrow{H_A} |0_A0_B \rangle\end{align}$
		+ $\begin{align}01 \xrightarrow{C_ANOT_B} &\cfrac{|1_A\rangle + |0_A \rangle}{\sqrt{2}} |1_B \rangle \xrightarrow{H_A} |0_A1_B \rangle\end{align}$
		+ $\begin{align}10 \xrightarrow{C_ANOT_B} &\cfrac{|0_A\rangle - |1_A \rangle}{\sqrt{2}} |0_B \rangle \xrightarrow{H_A} |1_A0_B \rangle\end{align}$
		+ $\begin{align}11 \xrightarrow{C_ANOT_B} &\cfrac{|0_A\rangle - |1_A \rangle}{\sqrt{2}} |1_B \rangle \xrightarrow{H_A} |1_A1_B \rangle\end{align}$
+ Quindi, inviando solo un qubit, Alice ha condiviso 2 bit d'informazione
+ Abbiamo inoltre a disposizione 4 porte unitarie, invece delle 2 classiche ($\mathbb{1}$, NOT)
### Teletrasporto Quantistico
+ Un altra operazione unica dei computer quantici è il **teletrasporto quantistico**
+ Al contrario del superdense coding, esso non necessita scambio d'informazione
+ Facciamo un esempio:
	+ Alice e Bob possiedono ciascuno un qubit, $I$ di $A$ e $III$ di $B$, e lo stato entangled ottenuto dai due. Alice possiede un secondo qubit $II$,
		+ $| \Phi \rangle = \overbrace{| \psi_A \rangle}^{II} \cfrac{|\overbrace{0}^{I}\overbrace{0}^{III} \rangle + |\overbrace{1}^{I}\overbrace{1}^{III} \rangle}{\sqrt{2}}$
		+ $| \psi_A \rangle = \alpha |0 \rangle + \beta | 1 \rangle$
	+ Alice vuole comunicare a Bob lo stato di $II$, e al contrario di prima, essi non possiedono un canale di comunicazione
	+ Essa dunque applica una porta **CNOT** sui **suoi due qubit** ($I$ e $II$) (Il formato è stato riscritto in una forma più semplice, moltiplicando $| \psi_A \rangle$)
		+ $|\Phi \rangle \xrightarrow{C_I NOT_{II}} \frac{1}{\sqrt{2}} [ \alpha | 0 \rangle (|00 \rangle + | 11 \rangle) + \beta |1 \rangle (|10 \rangle + | 01 \rangle)]$
	+ Dopodiché Alice applica una porta di **Hadamar** su $I$
		+ $\xrightarrow{H_I} \frac{1}{2} [ \alpha (| 0 \rangle + | 1 \rangle) (|00 \rangle + | 11 \rangle) + \beta (| 0 \rangle - | 1 \rangle) (|10 \rangle + | 01 \rangle)]$
	+ **Fattorizziamo**:
		+ $\frac{1}{2} [ |00 \rangle (\alpha| 0 \rangle + \beta| 1 \rangle) + | 01 \rangle(\alpha| 1 \rangle + \beta| 0 \rangle) + |10 \rangle (\alpha| 0 \rangle - \beta| 1 \rangle) + | 11 \rangle(\alpha| 1 \rangle - \beta| 0 \rangle)]$
			+ Ora è il qubit di Bob ad avere le informazioni da trasferire, senza scambio di materia
	+ Alice infine **effettua una misura** su $I$ e $II$, collassando il sistema. I possibili risultati sono:
		+ $\text{Probabilità } \frac{1}{4} \qquad \overbrace{| 00 \rangle}^{A} \qquad \overbrace{(\alpha| 0 \rangle + \beta| 1 \rangle)}^{B}$
		+ $\text{Probabilità } \frac{1}{4} \qquad | 01 \rangle \qquad (\alpha| 1 \rangle + \beta| 0 \rangle)$
		+ $\text{Probabilità } \frac{1}{4} \qquad | 10 \rangle \qquad (\alpha| 0 \rangle + \beta| 1 \rangle)$
		+ $\text{Probabilità } \frac{1}{4} \qquad | 11 \rangle \qquad (\alpha| 1 \rangle - \beta| 0 \rangle)$
		+ Lo stato che Bob possiede al momento ricorda quello che Alice voleva trasferire. 
	+ Ora, effettuando una comunicazione successiva, su un nuovo canale tradizionale, Alice comunica a Bob cosa ha misurato. Sulla base di esso, Bob effettua:
		+ $(\alpha| 0 \rangle + \beta| 1 \rangle) \qquad \overbrace{\to}^{\mathbb{1}} \qquad |\psi \rangle$
		+ $(\alpha| 1 \rangle + \beta| 0 \rangle) \qquad \overbrace{\to}^{X} \qquad |\psi \rangle$
		+ $(\alpha| 0 \rangle - \beta| 1 \rangle) \qquad \overbrace{\to}^{\mathbb{Z}} \qquad |\psi \rangle$
		+ $(\alpha| 1 \rangle - \beta| 0 \rangle) \qquad \overbrace{\to}^{\mathbb{Y}} \qquad |\psi \rangle$
	+ Bob riesce quindi a recuperare lo stato iniziale di $II$
+ Se associamo un significato a $\alpha$ e $\beta$, due reali, possiamo **trasferire $2 \mathbb{R}$ di informazione in una sola comunicazione**. Impressionante!
## B - Algoritmi
### Deutsch
#### Obbiettivo
+ Data una funzione $f : \{0, 1\} \to \{0, 1\}$, determinare se essa è **costante** o **bilanciata**
#### Preparativi
+ Nel procedimento è necessario applicare la funzione $f$, riscritta come un operatore quantistico $U_f$. Esso si comporta nel seguente modo:
	+ $|x, y \rangle  \xrightarrow{U_f} |x, y \oplus f(x) \rangle$
+ Applicandolo a $|x\rangle |-\rangle$, l’applicazione dell’operatore $U_f$ lascia invariato sia il primo qubit che il secondo ma lo stato acquista una fase $(-1)^{f(x)}$ che dipende dal valore della funzione $f$ calcolata per $x$
	+ *Possiamo dire che lo stato $|x\rangle |-\rangle$è un autovettore dell’operatore $U_f$ con autovalore $(-1)^{f(x)}$*
+ Esso viene chiamata l'**operatore oracolo**
#### Procedimento
![Deutsch Algorithm|400](deutsch.png)
+ Partiamo da uno stato composto da due bit:
	+ $| \psi_0 \rangle = |\underbrace{0_l}_{\text{bit logico }} \underbrace{0_a}_{\text{ bit ancella}}\rangle$
+ Applichiamo una porta $NOT_2$:
	+ $\xrightarrow{X_2} \quad |0_l 1_a \rangle$
+ Applichiamo una porta di **Hadamard** ad entrambi i bit:
	+ $\xrightarrow{H_l \otimes H_a }  \quad  | \psi_1 \rangle = |+_l -_a \rangle = \cfrac{1}{2} (|0_l \rangle + | 1_l \rangle)(|0_a \rangle - |1_a \rangle)$
+ Applichiamo quindi $U_f$ a $|\psi_1 \rangle$
	+ $\begin{equation}\begin{split} \xrightarrow{U_f}\quad |\psi_2 \rangle =& U_f|+_l -_a \rangle = \\ =& U_f \cfrac{1}{\sqrt{2}} (|0_l \rangle + | 1_l \rangle)|-_a \rangle = \\ =& \cfrac{1}{\sqrt{2}} ((-1)^{f(0)}|0_l \rangle + (-1)^{f(1)}| 1_l \rangle)|-_a \rangle \end{split}\end{equation}$
+ Applichiamo una porta di **Hadamard** al primo bit logico:
	+ $\begin{equation}\begin{split} \xrightarrow{H_l} \quad |\psi_3 \rangle =& \cfrac{1}{2} \left[((-1)^{f(0)}(|0_l \rangle + |1_l \rangle)) + ((-1)^{f(1)}(| 0_l \rangle - |1_l \rangle)\right]|-_a \rangle = \\ =& \cfrac{1}{2} \left[ \left( \left( (-1)^{f(0)} + (-1)^{f(1)} \right)|0_l \rangle \right) + \left( \left( (-1)^{f(0)} - (-1)^{f(1)} \right) |1_l \rangle \right) \right]|-_a \rangle \end{split} \end{equation}$
+ Infine, effettuiamo una **misura** sul bit logico:
	+ $\begin{cases} f \text{  costante } \xrightarrow{\text{misura}} \underbrace{\pm}_{\text{fase globale}} | 0  \rangle = | 0 \rangle  \quad \text{probabilità } = 1 \\ f \text{ bilanciata } \xrightarrow{\text{misura}} \underbrace{\pm}_{\text{fase globale}} | 1  \rangle = | 1 \rangle \quad \text{probabilità } = 1 \end{cases}$
+ Questo ci permette dunque di distinguere fra i due casi
#### Vantaggio
+ Classicamente, è necessario chiamare $f$ $2$ volte. Con Deutsch-Jozsa, esso viene chiamata solo una volta
### Deutsch-Jozsa
#### Obbiettivo
+ Data una funzione $f : \{0, 1\}^n \to \{0, 1\}$, determinare se essa è **costante** o **bilanciata** (metà input in $0$, metà input in $1$)
#### Procedimento
![Deutsch-Jozsa Algorithm|400](deutsch-jozsa.png =200x100)
+ Partiamo da uno stato composto da $n + 1$ bit:
	+ $| \psi_0 \rangle = |\underbrace{0_l^{n}}_{\text{bit logici }} \underbrace{0_a}_{\text{ bit ancella}}\rangle$
+ Applichiamo una porta $NOT_{n+1}$:
	+ $\xrightarrow{X_{n + 1}} \quad |0_l^n 1_a \rangle$
+ Applichiamo una porta di **Hadamard** a tutti i bit:
	+ $\xrightarrow{H^{\otimes n} \otimes H}\quad  | \psi_1 \rangle = \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0}| x_l \rangle |-_a \rangle$
+ Applichiamo quindi $U_f$ a $|\psi_1 \rangle$
	+ $\begin{equation}\begin{split}\xrightarrow{U_f}\quad |\psi_2 \rangle =& \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0} (-1)^{f(x)} | x_l \rangle |-_a \rangle\end{split}\end{equation}$
+ Applichiamo nuovamente una porta di **Hadamard** a tutti i primi N bit:
	+ $\begin{equation}\begin{split}\xrightarrow{H^{\otimes n}} \quad |\psi_3 \rangle =& \cfrac{1}{N} \sum^{N-1}_{x=0} \sum^{N-1}_{z=0} (-1)^{xz + f(x)}|z_l \rangle|-_a \rangle \end{split} \end{equation}$
+ Infine, effettuiamo una **misura** sul bit logico:
	+ Se Alice misura sempre e solo la stringa vuota, la funzione è costante. Altrimenti, la funzione è bilanciata
	+ *più dettagli nelle note, (chap 4, pag 15)*
+ Questo ci permette dunque di distinguere fra i due casi
#### Vantaggio
+ Classicamente, è necessario chiamare $f$ $N$ volte. Con Deutsch-Jozsa, esso viene chiamata solo una volta

### Bernstein-Vazirani
#### Obbiettivo
+ Consideriamo una funzione $f_a(x) : \{0, 1\}^{N} \to \{0, 1\}$, definita come $f_a(x) = ax$
+ Cerchiamo di determinare il valore di $a$
#### Preparativi
+ Similmente a prima, tradurremo $f_a$ in $U_{f_a}$
	+ *non sicuro...*
#### Procedimento
![Bernstein-Vazirani Algorithm|400](bernstein-vazirani.png =200x100)
+ La struttura dell'algoritmo è simile a quella di Deutsch-Jozsa
+ Partiamo da $| 0 \rangle^{\oplus N}$
+ Applichiamo i passaggi di Deutsch-Jozsa:
	+ $\begin{equation}\begin{split} \xrightarrow{H^{\otimes n}, U_{f_a}, H^{\otimes n}}\quad |\psi_3 \rangle =& \cfrac{1}{N} \sum^{N-1}_{x=0} \sum^{N-1}_{z=0} (-1)^{xz + f_a(x)}|z \rangle\end{split} \end{equation}$
+ Fattorizziamo la $x$:
	+ $= \quad \cfrac{1}{N} \sum^{N-1}_{z} \underbrace{\left(\sum^{N-1}_{x} (-1)^{x(a \oplus z)}\right)}_{\chi} |z\rangle$
+ Dobbiamo ora comprendere il valore del coefficiente $\chi$:
	+ Se $a=z$, vale che $a_i \oplus z_i = 0 \quad\forall i$ 
	+ Dunque, $x (a \oplus z ) = 0$, e $\chi_{z=a} = \cfrac{1}{N} \sum^{N-1}_{x} 1 = 1$
	+ Siccome i coefficienti sono normalizzati, $\forall z \neq a \quad \chi_{z\neq a} = 0$
+ Quindi ci basta misurare i bit, e otterremmo con certezza assoluta il valore di $a$
#### Vantaggio
+ Classicamente, è necessario chiamare $f_a$ $N$ volte sugli $N$ vettori normalizzati. Con Bernstein-Vazirani, esso viene chiamata solo una volta
### Simon
#### Obbiettivo
+ Consideriamo una funzione $f_s(x) : \{0, 1\}^{N} \to \{0, 1\}^n$
	+ $\forall x \quad \exists y! : f(x) = f(y), \; y = x \oplus a$
+ Cerchiamo di trovare $a$
	+ Si può vedere come ritrovare un periodo di una funzione
#### Preparativi
+ Similmente a prima, tradurremo $f_s$ in $U_{f_s}$
	+ *non sicuro...*
#### Procedimento
![Simon Algorithm|400](simon.png =200x100)
+ Partiamo da uno stato composto da $2N$ bit:
	+ $| \psi_0 \rangle = |\underbrace{0_l^{\otimes N}}_{\text{bit logici }} \underbrace{0_a^{\otimes N}}_{\text{ bit ancella}}\rangle$
+ Applichiamo una porta di **Hadamard** ai bit logici:
	+ $\overbrace{\to}^{H^{\otimes N}} \quad |\psi_1 \rangle = \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0} |x_l \rangle |0_a \rangle^{\otimes N}$
+ Applichiamo $U_{f_s}$:
	+ $\overbrace{\to}^{U_{f_s}} \quad |\psi_2 \rangle = \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0} |x_l \rangle \underbrace{|f(x_a) \rangle}_{|\overline{0_a} \oplus f(x) \rangle}$
+ **Fattorizziamo** i valori simili:
	+ $= \quad \cfrac{1}{\sqrt{\frac{N}{2}}} \sum^{N-1}_{x=0} \left( |x_l \rangle + |x_l \oplus a \rangle \right) |f(x_a) \rangle$
+ Effettuiamo una misura sugli ultimi $n$ bit ancilla
+ Applichiamo nuovamente una porta di **Hadamar** ai bit logici:
	+ $\begin{equation}\begin{split}\overbrace{\to}^{H^{\otimes N}} \quad |\psi_3 \rangle =& \cfrac{1}{\sqrt{2N}} \sum^{N-1}_{z=0} \left[ (-1)^{x_0z} + (-1)^{((x_0 \oplus a)z)}\right]|z \rangle = \\ =& \cfrac{1}{\sqrt{2N}} \sum^{N-1}_{z=0} \left[ (-1)^{x_0z} + (-1)^{(x_0z + az)}\right]|z \rangle\end{split}\end{equation}$
+ **Fattorizziamo** il coefficiente:
	+ $= \quad \cfrac{1}{\sqrt{2N}} \sum^{N-1}_{z=0} \underbrace{(-1)^{x_0z}\left[1 + (-1)^{(az)}\right]}_{\chi} |z \rangle$
+ Cosa succede se:
	+ $az = 0 \quad \to \quad \chi_z \neq 0$
	+ $az = 1 \quad \to \quad \chi_z = 0$
+ La somma precedente può essere riscritta come:
	+ $= \quad \sum_{az=0} \chi_z |z \rangle$
+ Effettuiamo una misura, e memorizziamo uno degli $z : az = 0$
+ Rieseguendo più volte l'algoritmo, otterremo più $z$, in modo da comporre il seguente sistema:
	+ $\begin{cases}a_1z_1 + a_2 z_2 + a_3 z_3 + \cdots \\ a_1 z'_1 + a_2z'_2 + a_3z'_3 + \cdots \\ a_1 z''_1 + a_2z''_2 + a_3z''_3 + \cdots \\ \vdots \end{cases}$
+ Risolvendolo, otterremo $a$
#### Vantaggio
+ L'algoritmo scala linearmente, $\theta (N)$
### Grover
#### Obbiettivo
+  Consideriamo una funzione $f_g(x) : \{0, 1\}^{N} \to \{0, 1\}$
	+ $f(x) = \begin{cases}1 \qquad x\text{ è soluzione} \\0 \qquad x\text{ non è soluzione}  \end{cases}$
+ Cerchiamo di trovare di trovare l'insieme soluzione $S : \{ \forall x \in S  f(x) = 1\}$
	+ Si può vedere come una **ricerca in un database**
#### Preparativi
+ Useremo la funzione oracolo $U_f$ chiamata $O$
	+ $|x \rangle \overbrace{\to}^{O} (-1)^{f(x)} |x \rangle$
+ Useremo inoltre l'operatore di **diffusione** di Grover, $g$
	+ $\begin{equation}\begin{split} g =& \quad H^{\otimes N} (2 |0 \times 0 | - \mathbb{1}) H^{\otimes N} = \\ =& \quad 2 |\psi \times \psi | - \mathbb{1} \qquad \qquad \qquad \qquad |\psi \rangle = H^{\otimes N} |0 \rangle \end{split}\end{equation}$
+ L'operatore di Grover è quindi:
	+ $G = g O$
#### Procedimento
![Grover Algorithm|400](grover.png =200x100)
+ Partiamo da uno stato composto da $N$ bit:
	+ $| \psi_0 \rangle = |0^{\otimes N}\rangle$
+ Applichiamo una porta di **Hadamard** ai bit:
	+ $\overbrace{\to}^{H^{\otimes N}} \quad |\psi \rangle = \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0} |x \rangle$
+ Applichiamo l'oracolo $O$:
+ Applichiamo nuovamente **Hadamard**:
+ Applichiamo l'operatore $(2 |0 \times 0 | - \mathbb{1})$, il quale cambia la fase dei bit diversi da $|0 \rangle$:
+ Applichiamo un ultima volta **Hadamard** :
+ Effettuiamo una misura
---
+ Per comprendere il funzionamento dell'algoritmo, vediamolo dal punto di vista **geometrico**:
	+ Immaginiamo di avere un database composto da $N$ elementi, contenente $M$ soluzioni
	+ Definiamo uno stato $| \alpha \rangle$ come la somma di tutte le **non-soluzioni** $x$
		+ $|\alpha \rangle = \quad \cfrac{1}{\sqrt{N - M}} \sum^{N}_{\text{x non soluzione}} | x \rangle$
	+ Analogamente, $| \beta \rangle$ sarà la somma di tutte le **soluzioni** $x$
		+ $|\beta \rangle = \quad \cfrac{1}{\sqrt{M}} \sum^{N}_{\text{x soluzione}} | x \rangle$
	+ Lo stato iniziale $| \psi \rangle$ viene quindi riscritto come:
		+ $| \psi \rangle = \quad \sqrt{\cfrac{N - M}{N}} | \alpha \rangle + \sqrt{\cfrac{M}{N}} | \beta \rangle$
	+ Questo è quindi lo **stato iniziale** riscritto nella **base** $\alpha \beta$
	+ Ora dobbiamo riscrivere gli **operatori**
		+ Oracolo $O$
			+ Cambia il segno se $x$ è la soluzione
			+ $O = \quad | \alpha \times \alpha | - | \beta \times \beta |$
			+ $O = \quad \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$
		+ Operatore $U$
			+ Cambia la fase a tutti gli stati tranne $|0^{\otimes n}\rangle$
			+ $U = 2|0^{\otimes n} \times 0^{\otimes n} | - \mathbb{1}$ 
		+ Operatore di Diffusione $g$
			+ $g = H^{\otimes n} U H^{\otimes n} = 2 | \psi \times \psi | - \mathbb{1}$
		+ Operatore di Grover $G$
			+ $G = gO$
	+ Riscriviamo ora lo stato iniziale in modo geometrico, come:
		+ $| \psi \rangle = \cos{\frac{\theta}{2}} | \alpha \rangle + \sin{\frac{\theta}{2}} | \beta \rangle$
	+ Abbiamo che:
		+ $(2 | \psi \times \psi | - \mathbb{1}) | \alpha \rangle = \cos{\theta} |\alpha \rangle+ \sin{\theta} | \beta \rangle$
		+ $(2 | \psi \times \psi | - \mathbb{1}) | \beta \rangle = \sin{\theta} |\alpha \rangle - \cos{\theta} | \beta \rangle$
	+ Da questo riscriviamo $g$ come:
		+ $g = \quad \begin{bmatrix} \cos{\theta} & \sin{\theta} \\ \sin{\theta} & -\cos{\theta} \end{bmatrix}$
	+ E di conseguenza:
		+ $G = gO = \quad \begin{bmatrix} \cos{\theta} & -\sin{\theta} \\ \sin{\theta} & \cos{\theta} \end{bmatrix}$
	+ Questo operatore ruota l'input di un angolo $\theta$, spostando il vettore $| \psi \rangle$ verso la soluzione $| \beta \rangle$
	+ Applicando più volte l'operatore, avremo la certezza di essere molto vicini alla soluzione
	![[rotazione_grover.png]]
#### Vantaggio
## C - Crittografia
+ Segnare particolarità crittografia quantistica
### BB84
+ L'idea alla base del protocollo è il fatto che la certezza di una misura di uno stato si basa sulla base utilizzata. +
	+ Quindi, possiamo sempre scegliere una base in cui la misura è deterministica e non probabilistica
+ Useremo **due basi** per il nostro algoritmo $_{1}^{0}$ e $\pm$, descritte in precedenza
+ Il protocollo è dunque il seguente:
	1. Alice intende inviare $n$ bit a Bob. Essa **estrae due sequenze** randomiche di $n$ bit
		+ La **prima** rappresenta una **stringa logica** da associare al messaggio
		+ La **seconda** rappresenta una **stringa delle basi**, che indica in che base misurare il bit logico corrispondente
	2. Sulla base delle sue stringhe Alice crea una sequenza di qubit, codificando in ognuno il valore del bit logico nella base corrispondente.
	3. Alice invia la sequenza di qubit a Bob
	4. Bob riceve i qubit ed estrae una sequenza randomica di $n$ bit. Essa sarà la sua **stringa delle basi**
	5. Egli effettua una misura sui qubit di sulla base delle basi indicate dalla stringa estratta.
		+ Se la base sul bit coincide con quella originale di Alice, il risultato della misura sarà deterministico, altrimenti questi sarà probabilistico, con ognuno dei casi con probabilità $\frac{1}{2}$
	6. In seguito, sia Alice che Bob pubblicano le stringhe delle basi utilizzate. In questo modo, essi posso riconoscere i bit coincidenti, e questi valori saranno utilizzati come chiave  
+ Questo processo può essere reso più sicuro, **proteggendolo** dall'intervento di un ipotetica **Eve**
	+ Essa potrebbe effettuare un attacco man-in-the-middle. Siccome essa non è a conoscenza della stringa delle basi di Alice, essa perturberà, in media, il 50% dei qubit inviati.
+ Una soluzione semplice è aggiungere un passaggio:
	7. Alice e Bob pubblicano una parte dei bit **correlati** calcolati. Essi dovrebbero essere completamente correlati. 
		+ In caso in cui la quantità di perturbazione supera una soglia predeterminata, si annulla il protocollo e si ripete in un ambiente più sicuro. 
		+ Se invece il controllo va a buon fine, si usa come chiave la parte di bit non condivisa
### EPR91
+ Il protocollo intende superare due proprietà di BB84:
	+ BB84 è un protocollo asimmetrico: la chiave viene generata da Alice
	+ Inoltre è presente uno scambio di qubit
+ Il protocollo è quindi come segue:
	1. Alice e Bob condividono $n$ qubit entangled del tipo:
		+ $|\Phi^+ \rangle = \cfrac{|00 \rangle + |11 \rangle}{\sqrt{2}}$
	2. Alice genera un bit randomico classico ed usa il suo valore per decidere la base in cui misurare il suo qubit, ottenendo il valore $a$. Bob si comporta in modo analogo, ottenendo $b$
	3. Siccome i bit sono correlati, $a$ e $b$ saranno sempre correlati fra loro.
	4. Quindi, useremo le misure in cui i bit randomici di Alice e Bob coincidono come chiave crittografica
	5. **DA FINIRE**
## D - Correzione Errori
### Errori
+ Allo scopo di moltiplicare l'informazione, codificheremo un bit logico con un blocco di tre qubit:
	+ $\begin{align} | 0_L \rangle = &|000\rangle \\ | 1_L \rangle = &|111\rangle \end{align}$
+  Il punto cruciale è di codificare gli stati logici in modo tale che siano autostati degli operatori che poi andiamo a misurare. 
+ In questo modo, la misura permette di estrarre l’informazione riguardante l’errore senza distruggere la sovrapposizione di stati.
#### Bit-Flip
+ Nel caso in cui avvenga un bit-flip, effettueremo due **misure** sui seguenti operatori:
	+ $Z_1 \otimes Z_2$
	+ $Z_1 \otimes Z_3$
+ Queste misure ci dicono se i bit coinvolti sono diversi fra loro, senza influenzare il valore dello stato, essendo autostati
	+ Se i bit su cui misuriamo sono diversi, otterremo $-1$ altrimenti $1$
+ Sulla base delle coppie di valori possiamo capire quale bit è stato modificato:
	+ $\begin{align}\{1, 1\} \rightarrow &\text{nessuno errore} \\ \{-1, 1\} \rightarrow &\text{errore sul secondo bit} \\ \{1, -1\} \rightarrow &\text{errore sul terzo bit} \\ \{-1, -1\} \rightarrow &\text{errore sul primo bit} \end{align}$
+ E possiamo poi usare un operatore $X$ sul bit coinvolto
#### Small Error
+ Per lo small error, possiamo usare lo stesso metodo, nonostante il fatto che il nostro stato non è più autostato degli operatori:
	+ La maggior parte delle volte il sistema collasserà nel valore corretto, autocorreggendosi
	+ Pochissime volte collasserà nel caso errato, ma ci darà come autovalore $-1$, segnalandoci la presenza dell'errore
#### Phase Flip
+ Possiamo pensare al phase-flip come ad un bit flip nella base $\pm$.
+ La nostra soluzione è quindi la seguente:
	+ Applicare $H^{\otimes 3}$ ai qubit
	+ Misurare $X_1 \otimes X_2$ e $X_1 \otimes X_3$ in maniera analoga al precedente
	+ Sulla base dei valori, correggere con $Z$
	+ Applicare nuovamente $H^{\otimes 3}$
### Shor1995
+ Questo primo protocollo di Shor si basa sulle idee viste in precedenza
+ In esso, un bit logico è composto da 9 qubit, organizzati come segue:
	+ $\begin{align} |\bar{0} \rangle &= \cfrac{|000 \rangle + |111 \rangle}{\sqrt{2}} \\ |\bar{1} \rangle &= \cfrac{|000 \rangle - |111 \rangle}{\sqrt{2}} \end{align}$
	+ $\begin{align} |0_L\rangle &= |\bar{0}\rangle |\bar{0}\rangle |\bar{0}\rangle \\ |1_L\rangle &= |\bar{1}\rangle |\bar{1}\rangle |\bar{1}\rangle \end{align}$
#### Bit-flip
+ Uguale al precedente
#### Phase-flip
+ Nella correzione del phase-flip, invece di confrontare i singoli bit, confrontiamo i blocchi, in quanto un bit-flip è equivalente al flip del valore del blocco
	+ Misuriamo $(X_1 \otimes X_2 \otimes X_3)( X_4 \otimes X_5 \otimes X_6)$ e $(X_1 \otimes X_2 \otimes X_3)( X_7 \otimes X_8 \otimes X_9)$ in modo analogo alle correzioni precedenti
	+ Sulla base del risultato, correggeremo con $Z$ sul blocco
		+ Il qubit specifico su cui applicarlo è indifferente, ci interessa solo il blocco
#### Small Error
+ Dobbiamo applicare sia il protocollo di bit-flip che quello di phase-flip *(dettagli nelle note)*
### Protocollo di Shor
+ *(dettagli nella relazione)*

## E - Quantum Games
### Spin-Flip
+ Picard e Q condividono un qubit $q$, inizializzato a $| 1 \rangle$
+ Essi agiscono nel seguente modo:
	1. Q applica $X$ o $\mathbb{1}$ a $q$
	2. Picard applica $X$ o $\mathbb{1}$ a $q$
	3. Q applica $X$ o $\mathbb{1}$ a $q$
+ Picard vince se $p = |0 \rangle$, altrimenti vince Q
	+ Nessuno dei due conosce le mosse degli altri
+ Nel caso classico, non esiste una strategia per vincere, sarà sempre casuale
---
+ Nel caso quantistico, supponiamo che Q possa applicare una porta quantistica qualsiasi, e che Picard applichi $X$ come probabilità $p$ e $\mathbb{1}$ con probabilità $1-p$
+ Ora Q ha una strategia per vincere sempre:
	1. Q applica una generica porta $U_1$, tale che:
		+ $| \psi \rangle =|1 \rangle \xrightarrow{U_1} a|1 \rangle + b | 0 \rangle$
	 2. Picard applicherà con le varie probabilità:
		 + $\begin{cases} a|0 \rangle + b |1 \rangle \qquad \text{con probabilità } p \text{ applica } X \\ a|1 \rangle + b |0 \rangle \qquad \text{con probabilità } 1 - p \text{ applica } \mathbb{1}\end{cases}$
	3. Q ora applica Hadamard:
	 + $\begin{cases} \frac{1}{\sqrt{2}}[(a-b)|1 \rangle + (a+b) |0 \rangle] \qquad \text{con probabilità } p \\ \frac{1}{\sqrt{2}} [(a+b)|0 \rangle + (-a + b) |1 \rangle] \qquad \text{con probabilità } 1 - p\end{cases}$
	 + Capiamo che, se applichiamo $H$ anche al primo passaggio, misureremo sempre $|1 \rangle$, e Q vincerà sempre!
		 + Questo è dovuto al fatto che $| - \rangle$ è autostato sia di $X$ che di $\mathbb{1}$
### I Valori di X ed Y
+ Supponiamo che Alice, Bob e Charlie sono stati imprigionati e separati. Per poter essere liberati, devono vincere ad un gioco
	1. Ognuno ha a disposizione due variabili $X$ ed $Y$. Separatamente gli viene chiesto di attribuire il valore $1$ o $-1$ ad ognuna delle variabili. Sanno che, o viene chiesto a tutti il valore di $X$, o viene chiesto ad uno di loro il valore di $X$, ed agli altri il valore di $Y$
		+ Ci sono quindi quattro casi possibili
			+ $\begin{align} &\{X_A, X_B, X_C\}\\ &\{X_A, Y_B, Y_C\} \\ &\{ Y_A, X_B, Y_C \}\\ &\{ Y_A, Y_B, X_C \}\end{align}$
	2. Essi devono scegliere i valori in modo che si ottengano i seguenti risultati:
		+ $\begin{align} X_A X_B X_C &= -1\\ X_A Y_B Y_C &= 1 \\ Y_A X_B Y_C &= 1 \\ Y_A Y_B X_C &= 1\end{align}$
		+ Ovviamente, $A, B$ e $C$ non sono a conoscenza delle rispettive risposte
+ Esiste una strategia vincente? Classicamente, no
---
+ Se $A, B, C$ condividessero uno stato quantistico entangled, sarebbe invece possibile!
+ Supponiamo che condividano lo stato:
	+ $|GHZ \rangle = \frac{1}{\sqrt{2}} (|0_A0_B0_C \rangle - |1_A 1_B 1_C \rangle)$
+ Essi si comporteranno nel seguente modo:
	+ Se gli viene chiesto di attribuire un valore ad $X$, essi applicheranno l'operatore $X$ di Pauli sul qubit
	+ Se gli viene chiesto di attribuire un valore ad $Y$, essi applicheranno l'operatore $Y$ di Pauli sul qubit
+ Per comprendere il loro funzionamento, riscriviamo lo stato $|GHZ \rangle$ nella base $\pm$, autostati di $X$ o in $\bar{\pm}$, autostati di $Y$
+ Nel caso applicassimo $X_A \otimes X_B \otimes X_C$ avremmo, nella base $\pm$:
	+ $\begin{align}|GHZ \rangle = &\cfrac{1}{4}\left[(|+ \rangle + | - \rangle)^{\otimes 3}-(|+ \rangle - |- \rangle)^{\otimes 3}\right]= \\ = & \cfrac{1}{2}\left[|++- \rangle + |+-+ \rangle + |-++ \rangle + |--- \rangle \right]\end{align}$
	+ Vediamo che, qualunque sia lo stato in cui collassa il sistema, si otterrà sempre $-1$ come risultato del prodotto delle misure
+ Nel caso in cui applicassimo $X_A \otimes Y_B \otimes Y_C$ avremmo, nella base $\bar{\pm}$:
	+ $\begin{align}|GHZ \rangle = &\cfrac{1}{4}\left[(|+ \rangle + | - \rangle)\otimes(|\bar{+}\rangle + | \bar{-} \rangle)^{\otimes 2}-(|+ \rangle - |- \rangle)\otimes (-i)^2(|\bar{+}\rangle + | \bar{-}\rangle)^{\otimes 2}\right]= \\ = & \cfrac{1}{2}\left[|+\bar{+}\bar{+} \rangle + |+\bar{-}\bar{-} \rangle + |-\bar{+}\bar{-} \rangle + |-\bar{-}\bar{+} \rangle \right]\end{align}$
	+  Vediamo che, qualunque sia lo stato in cui collassa il sistema, si otterrà sempre $1$ come risultato del prodotto delle misure
### CAPITOLO 8-V DA FARE
## F - Bomb Tester
+ Ci sono **situazioni** in meccanica quantistica si può **ottenere informazione** su un oggetto **senza misurarlo direttamente** (o meglio senza interagire con esso)
![[bomb_tester.png]]
+ Immaginiamo di inviare i fotoni in un canale. Rappresenteremo i fotoni verticali con $|1\rangle$ e quelli orizzontali con $|0\rangle$.
+ Essi saranno quindi inizialmente a $|0\rangle$. Incontreranno un beam-splitter, che ne manda la metà in verticale. Possiamo quindi immaginarla come una porta di Hadamard $H$.
+ In seguito essi incontreranno degli specchi, che invertiranno la direzione della parte coinvolta. Possiamo immaginarli come delle $X$.
+ Quindi, il percorso che eseguono nel circuito $(a)$ è il seguente:
	+ $\begin{align}|0 \rangle \xrightarrow{H} &\frac{1}{\sqrt{2}}(|0\rangle + |1 \rangle) \\ \xrightarrow{X} &\frac{1}{\sqrt{2}}(|0\rangle + |1 \rangle) \\ \xrightarrow{H}  &|0 \rangle \end{align}$
+ I fotoni verranno quindi tutti rilevati nel detector 1
+ Nel caso del circuito $(b)$ abbiamo invece un corpo assorbente (la bomba) che assorbe la parte di fotoni verticali, quindi il 50% dei fotoni
+ Della parte rimanente, essi verranno separati dall'ultimo beam-splitter, e quindi il 25% andrà nel detector 1, ed il 25% rimanente nel detector 2
+ Quindi, il detector 2 rileverà fotoni solo nel caso in cui è presente un oggetto assorbente in uno dei due percorsi
---
+ Usiamo questa struttura per creare un bomb-tester.
+ Supponiamo di avere un certo numero di bombe che vengono attivate da un detector di fotoni. Vogliamo sapere quali bombe sono attive senza farle esplodere.
+ Classicamente questo è impossibile: infatti se inviamo un fotone alla bomba attiva, essa esploderà
+ Quantisticamente, immaginiamo le due situazioni come i circuiti precedenti:
	+ Nel circuito $(a)$ è come se la bomba fosse inattiva: i fotoni la attraversano senza problemi, e li riceveremo solo sul detector 1
	+ Nel circuito $(b)$ la bomba è attiva, ed è il corpo assorbente. Quindi:
		+ Nel 50% dei casi, la bomba esploderà
		+ Nel 25% dei casi sarà misurato sul detector 1
		+ Nel 25% dei casi sarà misurato sul detector 2
+ Ciò vuol dire che se la bomba è attiva, riusciremo a rilevarla senza attivarla nel 25% dei casi. Incredibile!
	+ ![[optimized_bomb_tester.png]]
	+ Un modo per migliorare la percentuale di successo è sostituire $H$ con un generica rotazione di $\theta$ che mandi pochi fotoni in verticale e ripetere $N$ volte lo splitting. Per $\theta$ sufficientemente piccolo e $N$ sufficientemente grande, la probabilità si avvicina molto al 100%! 