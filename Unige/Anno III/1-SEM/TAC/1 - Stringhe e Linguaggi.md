+ Nel corso di **T**eoria degli **A**utomi e **C**alcolabilità, parleremo sia della definizione di automi, e lo studio del loro funzionamento, sia dei limiti dei calcolatori
---
+ Iniziamo riprendendo alcune definizioni
+ Un **Alfabeto** è un **insieme** $\Sigma$ non vuoto, finito, di simboli
+ Una **Stringa** è una **sequenza** finita di simboli
	+ Essa viene anche definita come una funzione:
		+ $a : [1, ... ,n] \to \Sigma \qquad n = |a|$ 
	+ $\color{Apricot}\epsilon$ rappresenta la **stringa vuota**
	+ $\color{Apricot}\Sigma^*$ rappresenta tutte le possibili stringhe sull'alfabeto $\Sigma$ 
+ Un operazione tipica è la **concatenazione** ( $\cdot$ ):
	+ Prese le stringhe $u$ e $v$, con $|u| = n$, $|v| = m$  
	+ $(u \cdot v) (k) = \begin{dcases} u(k) \qquad 1 \leq k \leq n \\ v(k-n) \qquad n+1 \leq k \leq m+n\end{dcases}$
+ È un operazione associativa, e forma un **monoide** ($\epsilon$ ne è l'elemento neutro)

+ Un **Linguaggio** è un alfabeto di stringhe $L \in \Sigma^*$ 
	+ Può essere finito o infinito
	+ Supporta le operazioni insiemistiche e la **concatenazione**
		+ $L_1 \cdot L_2 = \{ u \cdot v \; | \; u \in L_1 \wedge V \in L_2\}$ 
	+ Attenti a distinguere:
		+ $L \cdot \emptyset = \emptyset$ 
		+ $L \cdot \{\epsilon\} = L$ 
+ Definiamo con la chiusura di Kleene:
	+ $L^* = \bigcup_{n \geq 0} L^n$ 
	+ $L^+ = L^* \setminus {\epsilon}$ 