### Deutsch
#### Obbiettivo
+ Data una funzione $f : \{0, 1\} \to \{0, 1\}$, determinare se essa è **costante** o **bilanciata**
#### Preparativi
+ Nel procedimento è necessario applicare la funzione $f$, riscritta come un operatore quantistico $U_f$. Esso si comporta nel seguente modo:
	+ $|x, y \rangle  \overbrace{\to}^{U_f} |x, y \oplus f(x) \rangle$
+ Applicandolo a $|x\rangle |-\rangle$, l’applicazione dell’operatore $U_f$ lascia invariato sia il primo qubit che il secondo ma lo stato acquista una fase $(-1)^{f(x)}$ che dipende dal valore della funzione $f$ calcolata per $x$
	+ *Possiamo dire che lo stato $|x\rangle |-\rangle$è un autovettore dell’operatore $U_f$ con autovalore $(-1)^{f(x)}$*
+ Esso viene chiamata l'**operatore oracolo**
#### Procedimento
![Deutsch Algorithm|400](deutsch.png)
+ Partiamo da uno stato composto da due bit:
	+ $| \psi_0 \rangle = |\underbrace{0_l}_{\text{bit logico }} \underbrace{0_a}_{\text{ bit ancella}}\rangle$
+ Applichiamo una porta $NOT_2$:
	+ $\overbrace{\to}^{NOT_2} \quad |0_l 1_a \rangle$
+ Applichiamo una porta di **Hadamard** ad entrambi i bit:
	+ $\overbrace{\to}^{H_1 \otimes H_2 } \quad  | \psi_1 \rangle = |+_l -_a \rangle = \cfrac{1}{2} (|0_l \rangle + | 1_l \rangle)(|0_a \rangle - |1_a \rangle)$
+ Applichiamo quindi $U_f$ a $|\psi_1 \rangle$
	+ $\begin{equation}\begin{split}\overbrace{\to}^{U_f } \quad |\psi_2 \rangle =& U_f|+_l -_a \rangle = \\ =& U_f \cfrac{1}{\sqrt{2}} (|0_l \rangle + | 1_l \rangle)|-_a \rangle = \\ =& \cfrac{1}{\sqrt{2}} ((-1)^{f(0)}|0_l \rangle + (-1)^{f(1)}| 1_l \rangle)|-_a \rangle \end{split}\end{equation}$
+ Applichiamo una porta di **Hadamard** al primo bit logico:
	+ $\begin{equation}\begin{split}\overbrace{\to}^{H_1} \quad |\psi_3 \rangle =& \cfrac{1}{2} \left[((-1)^{f(0)}(|0_l \rangle + |1_l \rangle)) + ((-1)^{f(1)}(| 0_l \rangle - |1_l \rangle)\right]|-_a \rangle = \\ =& \cfrac{1}{2} \left[ \left( \left( (-1)^{f(0)} + (-1)^{f(1)} \right)|0_l \rangle \right) + \left( \left( (-1)^{f(0)} - (-1)^{f(1)} \right) |1_l \rangle \right) \right]|-_a \rangle \end{split} \end{equation}$
+ Infine, effettuiamo una **misura** sul bit logico:
	+ $\begin{cases} f \text{  costante } \quad \overbrace{\to}^\text{misura} \quad \underbrace{\pm}_{\text{fase globale}} | 0  \rangle = | 0 \rangle  \quad \text{probabilità } = 1 \\ f \text{ bilanciata } \quad \overbrace{\to}^\text{misura} \quad \underbrace{\pm}_{\text{fase globale}} | 1  \rangle = | 1 \rangle \quad \text{probabilità } = 1 \end{cases}$
+ Questo ci permette dunque di distinguere fra i due casi
#### Vantaggio
+ Classicamente, è necessario chiamare $f$ due volte. Con Deutsch, esso viene chiamata solo una volta
### Deutsch-Jozsa 
#### Obbiettivo
+ Data una funzione $f : \{0, 1\}^n \to \{0, 1\}$, determinare se essa è **costante** o **bilanciata** (metà input in $0$, metà input in $1$)
#### Procedimento
![Deutsch-Jozsa Algorithm|400](deutsch-jozsa.png =200x100)
+ Partiamo da uno stato composto da $n + 1$ bit:
	+ $| \psi_0 \rangle = |\underbrace{0_l^{n}}_{\text{bit logici }} \underbrace{0_a}_{\text{ bit ancella}}\rangle$
+ Applichiamo una porta $NOT_{n+1}$:
	+ $\overbrace{\to}^{NOT_{n+1}} \quad |0_l^n 1_a \rangle$
+ Applichiamo una porta di **Hadamard** a tutti i bit:
	+ $\overbrace{\to}^{H^{\otimes n} \otimes H } \quad  | \psi_1 \rangle = \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0}| x_l \rangle |-_a \rangle$
+ Applichiamo quindi $U_f$ a $|\psi_1 \rangle$
	+ $\begin{equation}\begin{split}\overbrace{\to}^{U_f } \quad |\psi_2 \rangle =& \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0} (-1)^{f(x)} | x_l \rangle |-_a \rangle\end{split}\end{equation}$
+ Applichiamo nuovamente una porta di **Hadamard** a tutti i primi N bit:
	+ $\begin{equation}\begin{split}\overbrace{\to}^{H^{\otimes n}} \quad |\psi_3 \rangle =& \cfrac{1}{N} \sum^{N-1}_{x=0} \sum^{N-1}_{z=0} (-1)^{xz + f(x)}|z_l \rangle|-_a \rangle \end{split} \end{equation}$
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
	+ $\begin{equation}\begin{split}\overbrace{\to}^{H^{\otimes n}, U_{f_a}, H^{\otimes n}} \quad |\psi_3 \rangle =& \cfrac{1}{N} \sum^{N-1}_{x=0} \sum^{N-1}_{z=0} (-1)^{xz + f_a(x)}|z \rangle\end{split} \end{equation}$
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
+ Cerchiamo di trovare di trovare $a$
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
	+ $= \quad \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0} \left( |x_l \rangle + |x_l \oplus a \rangle \right) |f(x_a) \rangle$
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
+ Cerchiamo di trovare di trovare l'insieme soluzione $S : \{ x : f(x) = 1\}$
	+ Si può vedere come una **ricerca in un database**
#### Preparativi
+ Useremo la funzione oracolo $U_f$ chiamata $O$
	+ $|x \rangle \overbrace{\to}^{O} (-1)^{f(x)} |x \rangle$
+ Useremo inoltre l'operatore di **diffusione** di Grover, $g$
	+ $\begin{equation}\begin{split} g =& \quad H^{\otimes N} (2 |0 \times 0 | - \mathbb{1}) H^{\otimes N} = \\ =& \quad 2 |\psi \times \psi | - \mathbb{1} \qquad \qquad \qquad \qquad |\psi \rangle = H^{\otimes N} |0 \rangle \end{split}\end{equation}$
+ L'operatore di **Grover** è:
	+ $G = \quad g \cdot O$
#### Procedimento
![Grover Algorithm|400](grover.png =200x100)
+ Partiamo da uno stato composto da $N$ bit:
	+ $| \psi_0 \rangle = |0^{\otimes N}\rangle$
+ Applichiamo una porta di **Hadamard** ai bit:
	+ $\overbrace{\to}^{H^{\otimes N}} \quad |\psi_1 \rangle = \cfrac{1}{\sqrt{N}} \sum^{N-1}_{x=0} |x \rangle$
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
		+ $| \psi \rangle = \quad \cfrac{1}{\sqrt{N - M}} \sum^{N - M}_{\text{x non soluzione}} | x \rangle + \cfrac{1}{\sqrt{M}} \sum^{M}_{\text{x soluzione}} | x \rangle$
	+ A partire dalle definizioni degli stati, si può riscrivere come:
		+ $| \psi \rangle = \quad \sqrt{\cfrac{N - M}{N}} | \alpha \rangle + \sqrt{\cfrac{M}{N}} | \beta \rangle = \cos{\frac{\theta}{2}} | \alpha \rangle + \sin{\frac{\theta}{2}} | \beta \rangle$
	+ Questo è quindi lo **stato iniziale** riscritto nella **base** $\alpha \beta$
	+ Ora dobbiamo riscrivere gli **operatori**
		+ $O = \quad | \alpha \times \alpha | - | \beta \times \beta |$
		+ $O = \quad \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}$
#### Vantaggio