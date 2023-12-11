+ Consideriamo insiemi numerici $X \subseteq \mathbb{N}$ 
+ Ognuno di questi numeri può essere considerato **l'indice di un programma**
+ Possiamo dire che:
	+ $X$ è **ricorsivo** se esiste un macchina che dice se un elemento $x$ è on non è in $X$, **terminando sempre**
		+ Possiamo vedere queste funzioni come **problemi decidibili**
	+ $X$ è **ricorsivamente numerabile** se esiste un macchina che dice se un elemento $x$ è on non è in $X$, **potendo non terminare**
		+ Gli insiemi $H$ e $K$, analoghi alle funzioni dell'**halting problem**, appartengono a questo insieme. La risposta positiva è sempre ottenibile
		+ Possiamo vedere queste funzioni come **problemi semi-decidibili**
			+ *(esistono anche problemi non-decidibili, come il problema della terminazione)*
+ Un altro modo per vedere se un insieme è ricorsivo è se la **funzione caratteristica** $\chi$ è ricorsiva
	+ $\chi_X(x) = \begin{dcases} 1 \quad x \in X \\ 0 \quad x \notin X\end{dcases}$ 
+ Analogamente, per vedere se un insieme è ricorsivamente enumerabile, bisogna vedere se la **funzione caratteristica** $\psi$ è ricorsiva
	+ $\psi_X(x) = \begin{dcases} 1 \quad x \in X \\ 0 \vee \uparrow \quad x \notin X\end{dcases}$
+ In questo casi, $X$ viene chiamato il **dominio di definizione** della funzione caratteristica
+ Tutte queste definizioni sono **collegate** fra loro
---
+ Vediamo il **Teorema di Post**
	+ L'insieme $X \subseteq \mathbb{N}$ è **ricorsivo** se e solo se $\overline{X}$ è **ricorsivo** e se e solo se sono **entrambi ricorsivamente enumerabili**
+ Tramite l'**inter-leaning**, è possibile dimostrare il teorema (*nel cartaceo*)
+ Tramite esso è possibile dare un esempio di insieme **non ricorsivamente enumerabile**
	+ Riprendiamo $K$ ed $H$, gli insiemi analoghi alle funzioni $f_k$ ed $f_h$ viste in precedenza
	+ $H$ e $K$ sono ricorsivamente enumerabili, ma non ricorsivi. Per ciò, $\overline{H}$ ed $\overline{K}$ sono **necessariamente non ricorsivamente enumerabili**
		+ *Questo è comprensibile, in quanto determinare se un programma non termina è un problema di natura ben più complessa di se termini*
----
+ Proprietà di **Chiusura**
+ $X, Y$ **ricorsivi**
+ Sono i seguenti ricorsivi?
	+ $\overline{X} \quad$ SI, per Post
	+ $X \cup Y\quad$ SI, si può realizzare una macchina specifica tramite quelle di $X$ ed $Y$ 
	+ $X \cap Y \quad$ SI, in modo simile a prima
	+ $X \cdot Y \quad$ SI, basta provare tutte le possibili decomposizioni
	+ $X^* \quad$ SI, basta fare come sopra
+  $X, Y$ **ricorsivamente enumerabili**
+ Sono i seguenti ricorsivamente enumerabili?
	+ $\overline{X} \quad$ NO, già visto con $\overline{K}$
	+ $X \cup Y\quad$ SI, si può realizzare una macchina specifica tramite quelle di $X$ ed $Y$ ed inter-leaning
	+ $X \cap Y \quad$ SI, in modo simile a prima con un and, o tramite un algoritmo sequenziale
	+ $X \cdot Y \quad$ SI, basta fare inter-leaning su tutte le possibili decomposizioni
	+ $X^* \quad$ SI, basta fare come sopra