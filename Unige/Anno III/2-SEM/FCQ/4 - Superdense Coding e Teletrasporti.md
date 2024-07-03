+ **Perché** un computer **quantistico** è più **vantaggioso** di uno **classico**?
+ Perché esso è **intrinsecamente parallelo**:
	+ Usando **Hadamard**, possiamo riscrivere un insieme di bit come la **sovrapposizione di tutti i loro possibili stati**
	+ Se **applichiamo** una generica **trasformazione** su questo stato, stiamo **contemporaneamente agendo su tutti** questi stati, allo stesso tempo
---
+ È possibile inviare **più di un bit** d'informazione usando un **singolo qubit**. Questo viene chiamato "**superdense coding**"
+ Facciamo un esempio:
	+ Alice e Bob possiedono ciascuno un qubit, e lo stato entangled ottenuto dai due:
		+ $| \Phi \rangle = \cfrac{|00 \rangle + |11 \rangle}{\sqrt{2}}$
	+ Alice vuole inviare due bit d'informazione a Bob (una delle sequenze 00, 01, 10, 11)
	+ Essa può applicare sul solo qubit che possiede le seguenti trasformazioni di Pauli:
		+ $00 \quad \to \quad \text{applica } \mathbb{1} \quad \to \quad \cfrac{|00 \rangle + |11 \rangle}{\sqrt{2}}$
		+ $01 \quad \to \quad \text{applica } X \quad \to \quad \cfrac{|10 \rangle + |01 \rangle}{\sqrt{2}}$
		+ $10 \quad \to \quad \text{applica } Z \quad \to \quad \cfrac{|00 \rangle - |11 \rangle}{\sqrt{2}}$
		+ $11 \quad \to \quad \text{applica } Y \quad \to \quad \cfrac{|01 \rangle - |10 \rangle}{\sqrt{2}}$
	+ Invia il qubit a Bob
	+ Bob applica ai qubit prima una porta **CNOT**, e poi una porta di **Hadamar**:
		+ $00 \quad \to \quad \text{applica CNOT} \quad \to \quad \cfrac{|00 \rangle + |10 \rangle}{\sqrt{2}} \quad \to \quad \text{applica H} \quad \to \quad |00 \rangle$
		+ $01 \quad \to \quad \text{applica CNOT} \quad \to \quad \cfrac{|11 \rangle + |01 \rangle}{\sqrt{2}} \quad \to \quad \text{applica H} \quad \to \quad |01 \rangle$
		+ $10 \quad \to \quad \text{applica CNOT} \quad \to \quad \cfrac{|00 \rangle - |10 \rangle}{\sqrt{2}} \quad \to \quad \text{applica H} \quad \to \quad |10 \rangle$
		+ $11 \quad \to \quad \text{applica CNOT} \quad \to \quad \cfrac{|00 \rangle - |01 \rangle}{\sqrt{2}} \quad \to \quad \text{applica H} \quad \to \quad |11 \rangle$
+ Quindi, inviando solo un qubit, Alice ha condiviso 2 bit d'informazione
+ Abbiamo inoltre a disposizione 4 porte unitarie, invece delle 2 classiche ($\mathbb{1}$, NOT)
---
+ Un altra operazione unica dei computer quantici è il **teletrasporto quantistico**
+ Al contrario del superdense coding, esso non necessita scambio d'informazione
+ Facciamo un esempio:
	+ Alice e Bob possiedono ciascuno un qubit, $I$ di $A$ e $III$ di $B$, e lo stato entangled ottenuto dai due. Alice possiede un secondo qubit $II$, in uno stato generico.
		+ $| \Phi \rangle = \overbrace{| \psi_A \rangle}^{II} \cfrac{|\overbrace{0}^{I}\overbrace{0}^{III} \rangle + |\overbrace{1}^{I}\overbrace{1}^{III} \rangle}{\sqrt{2}}$
		+ $| \psi_A \rangle = \alpha |0 \rangle + \beta | 1 \rangle$
	+ Alice vuole comunicare a Bob lo stato di $II$, e al contrario di prima, essi non possiedono un canale di comunicazione
	+ Essa dunque applica una porta **CNOT** sui **suoi due qubit** ($I$ e $II$) (Il formato è stato riscritto in una forma più semplice)
		+ $|\Phi \rangle \quad \overbrace{\to}^{\text{CNOT}_{I,II}} \frac{1}{\sqrt{2}} [ \alpha | 0 \rangle (|00 \rangle + | 11 \rangle) + \beta |1 \rangle (|10 \rangle + | 01 \rangle)]$
	+ Dopodiché Alice applica una porta di **Hadamar** su $I$
		+ $\overbrace{\to}^{\text{H}_{I}} \frac{1}{2} [ \alpha (| 0 \rangle + | 1 \rangle) (|00 \rangle + | 11 \rangle) + \beta (| 0 \rangle - | 1 \rangle) (|10 \rangle + | 01 \rangle)]$
	+ **Fattorizziamo**:
		+ $\frac{1}{2} [ |00 \rangle (\alpha| 0 \rangle + \beta| 1 \rangle) + | 01 \rangle(\alpha| 1 \rangle + \beta| 0 \rangle) + |10 \rangle (\alpha| 0 \rangle - \beta| 1 \rangle) + | 11 \rangle + | 11 \rangle(\alpha| 1 \rangle - \beta| 0 \rangle)]$
			+ Ora è il qubit di Bob ad avere le informazioni da trasferire, senza scambio di materia
	+ Alice infine **effettua una misura** su $I$ e $II$, collassando il sistema. I possibili risultati sono:
		+ $\text{Probabilità } \frac{1}{4} \qquad \overbrace{| 00 \rangle}^{A} \qquad \overbrace{|00 \rangle (\alpha| 0 \rangle + \beta| 1 \rangle)}^{B}$
		+ $\text{Probabilità } \frac{1}{4} \qquad | 01 \rangle \qquad |01 \rangle (\alpha| 1 \rangle + \beta| 0 \rangle)$
		+ $\text{Probabilità } \frac{1}{4} \qquad | 10 \rangle \qquad |10 \rangle (\alpha| 0 \rangle + \beta| 1 \rangle)$
		+ $\text{Probabilità } \frac{1}{4} \qquad | 11 \rangle \qquad |11 \rangle (\alpha| 1 \rangle - \beta| 0 \rangle)$
		+ Lo stato che Bob possiede al momento ricorda quello che Alice voleva trasferire. 
	+ Ora, effettuando una comunicazione successiva, su un nuovo canale tradizionale, Alice comunica a Bob cosa ha misurato. Sulla base di esso, Bob effettua:
		+ $| 00 \rangle (\alpha| 0 \rangle + \beta| 1 \rangle) \qquad \overbrace{\to}^{\mathbb{1}} \qquad |\psi \rangle$
		+ $| 01 \rangle (\alpha| 1 \rangle + \beta| 0 \rangle) \qquad \overbrace{\to}^{X} \qquad |\psi \rangle$
		+ $| 10 \rangle (\alpha| 0 \rangle - \beta| 1 \rangle) \qquad \overbrace{\to}^{\mathbb{Z}} \qquad |\psi \rangle$
		+ $| 11 \rangle (\alpha| 1 \rangle - \beta| 0 \rangle) \qquad \overbrace{\to}^{\mathbb{Y}} \qquad |\psi \rangle$
	+ Bob riesce quindi a recuperare lo stato iniziale di $II$
+ Se associamo un significato a $\alpha$ e $\beta$, due reali, possiamo **trasferire $2 \mathbb{R}$ di informazione in una sola comunicazione**. Impressionante!
---
+ Uno svantaggio è invece la **non esistenza** di un operatore di **copiatura universale**
+ È possibile crearne solo per specifici stati. Essi devono inoltre essere paralleli (e quindi uguali) o ortogonali
	+ In questo senso, CNOT può essere visto come un operatore di copiatura per $| 0 \rangle$ e $| 1 \rangle$
---
+ Come facciamo ad **inizializzare** la memoria di un computer con i **qubit** tutti inizialmente inizializzati a $|0 \rangle$?
+ Si usa Hadamard, assieme al **Phase gate**, definito come:
		+ $U_{ph} (\gamma) = \begin{cases} |0 \rangle \to |0 \rangle \\ |1 \rangle \to e^{i \gamma} | 1 \rangle \end{cases}$
+ La procedura è:
	+ $|0 \rangle \overbrace{\to}^H \cfrac{1}{\sqrt{2}}(|0 \rangle + |1\rangle) \to$ 
	+ $\overbrace{\to}^{U_{ph} ( -2 \alpha)} \cfrac{1}{\sqrt{2}}(|0 \rangle + e^{-2i\alpha}|1\rangle) \to$
	+ $\overbrace{\to}^{H} \cfrac{1}{2}(|0 \rangle + |1 \rangle+ e^{-2i\alpha}(|0 \rangle - |1\rangle)) = \cfrac{1}{2}((1 + e^{-2i\alpha}) | 0 \rangle + (1 - e^{-2i\alpha}) | 1 \rangle)=$
	+ $= \underbrace{\cfrac{e^{-i\alpha}}{2}}_{\text{fase globale}} (\underbrace{(e^{i\alpha} + e^{-i\alpha})}_{2\cos \alpha} | 0 \rangle + \underbrace{(e^{i\alpha} - e^{-i\alpha})}_{2 i \sin \alpha} | 1 \rangle) =$
	+ $= \cos \alpha |0 \rangle + i \sin \alpha | 1 \rangle \to$
	+ $\overbrace{\to}^{U_{ph} ( \gamma)} \cos \alpha |0 \rangle + \sin \alpha e^{i\gamma} | 1 \rangle$
+ Questo ci permette quindi di **inizializzare qubit** a valori voluti