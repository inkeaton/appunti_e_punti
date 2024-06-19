+ Vediamo la definizione di funzione continua:

>[!Definizione]
> ### Funzione Continua
> + Una funzione $F : A \subseteq \mathbb{R}^n \to \mathbb{R}^m$ viene detta continua in $P_0 \in A$ se:
> 	+ $\forall \varepsilon > 0 \; \exists \delta : || F(P) - F(P_0) || < \varepsilon \quad \text{se } P \in A \; \wedge \; || P - P_0  || < \delta$
> 	+ I punti sufficientemente vicini a $P_0$ vanno a finire nei punti vicini a $F(P_0)$
> + Se $f$ è continua $\forall p \in A$, diremo che è **continua** in $A$ 
>+ **Si indica** come $f \in C^0(A)$ 

+ Ci sono più modi per **determinare** se una funzione è **continua** o no
+ I seguenti concetti possono aiutarci a comprendere la natura della continuità della funzione che stiamo studiando:

>[!Lemma]
> ### Continuità di Vettoriale
> + Una funzione vettoriale $F : A \subseteq \mathbb{R}^n \to \mathbb{R}^m$ è continua in $P_0 \in A$ se e solo se sono continue tutte le funzioni scalari $f : A \subseteq \mathbb{R}^n \to \mathbb{R}$ che la compongono

>[!Teorema]
> ### Composizione di Continue
> + Siano $F : A \subseteq \mathbb{R}^n \to \mathbb{R}^m$ e $G : B \subseteq \mathbb{R}^m \to \mathbb{R}^l$
> + Se $F(A) \subseteq B$ e $F, G$ sono **continue**, allora la composizione $G \circ F : A \to \mathbb{R}^l$ è **continua**

>[!Teorema]
> ### Operazioni fra Continue
> + Siano $f, g : A \subseteq \mathbb{R}^n \to \mathbb{R}^m$ continue
> + Allora sono continue anche:
> 	+ $f + g$
> 	+ $fg$
> 	+ $\cfrac{f}{g}, \quad \text{se } g \neq 0$

---

+ Un concetto utile è quello di **infinitesimo**: 

>[!Definizione]
> ### Funzioni Infinitesime
> + Una funzione $\varepsilon : A \subseteq \mathbb{R}^n \to \mathbb{R}^m$ è detta **infinitesima nell'origine** se vale:
> 	+ $0 \in A$
> 	+ $\varepsilon(0) = 0 \in \mathbb{R}^m$
> 	+ $\varepsilon$ è continua in $0 \in \mathbb{R}^n$

 + **Traslando** queste funzioni, possiamo ottenere funzioni infinitesime in specifici punti
 + Il concetto di infinitesimo viene utilizzato in modo **simile** a quello di **infinito** nel calcolo dei limiti. Valgono dunque i seguenti:
	 + $\lambda \varepsilon (v) + \mu \varepsilon (v) = \varepsilon (v)$
	 + $\varepsilon(\varepsilon(v)) = \varepsilon(v)$
	 + $||\varepsilon(v)|| = \varepsilon(v)$
	 + Se $f : A \subseteq \mathbb{R}^n \to \mathbb{R}$ è localmente limitata e $0 \in A$, allora $f(v)\varepsilon(v) = \varepsilon(v)$
+ Possiamo fare la seguente osservazione:

>[!Osservazione]
> ### Piccole Distanze
> + $F \text{ continua in }  P_0 \quad \leftrightarrow \quad F(P) = F(P_0) + \varepsilon (P-P_0)$ 
> + Posti vicini fra loro hanno piccola distanza

 ---

+ Vediamo ora più nel dettaglio le **proprietà** delle funzioni continue
+ Vale il seguente:

>[!Proposizione]
> ### Controimmagini di insiemi
> + Sia $f : A \subseteq \mathbb{R}^n \to \mathbb{R}^m$ continua
> + Allora:
> 	+ Se $I$ è un intervallo aperto/chiuso in $\mathbb{R}$, allora $f^{-1}(I) : \{P \in A : f(P) \in I\}$ è aperto/chiuso
> 	+ **Non** vale il **contrario**

>[!Proposizione]
> ### Insiemi limitati
> + Sia $f : A \subseteq \mathbb{R}^2 \to \mathbb{R}^m$ continua, e $c \in \mathbb{R}$
> + Allora:
> 	+ $\{(x, y) \in \mathbb{R}^2 : f(x,y < c) \}$ è aperto $(I = (- \infty, c))$
> 	+ $\{(x, y) \in \mathbb{R}^2 : f(x,y \leq c) \}$ è chiuso $(I = (- \infty, c])$
> 	+ $\{(x, y) \in \mathbb{R}^2 : f(x,y = c) \}$ è chiuso $(I = (- \infty, c] \cap [c, + \infty))$

+ Ora che possediamo questi concetti, arriviamo ad enunciare il seguente teorema:

>[!Teorema]
> ### Teorema di Weierstrass
> + Sia $f : A \subseteq \mathbb{R}^2 \to \mathbb{R}^m$ continua, e $K$ chiuso e limitato
> + Allora esistono $p_1, p_2 \in K$ tali che $f(p_1) \leq f(p) \leq f(p_2) \quad \forall p \in K$
> + Vengono quindi denominati:
> 	+ $p_1$ **Punto di minimo**
> 	+ $p_2$ **Punto di massimo**
> 	+ $f(p_1)$ **Minimo assoluto**
> 	+ $f(p_2)$ **Massimo assoluto**
> + In casi multidimensionali, è possibile che esistano **più punti** di minimo e di massimo, **ma** **minimi** e **massimi** saranno sempre **unici**
