+ Presentiamo un mini-linguaggio, quello delle **Primitive-Ricorsive (PR)**
+ Esso è un linguaggio di programmazione funzionale, reminescente di OCAML
+ In esso, un programma è un insieme di dichiarazione di funzioni del tipo:
	+ $f(x_1, \cdots, x_n) = e$
	+ $e ::= x \; | \; f(e_1, \cdots, e_n) \; | \; z \; | \; S(e)$ 
		+ $x$ è un valore numerico
		+ $z$ è lo zero
		+ $S(e)$ è l'incremento di 1
+ Le funzioni possono essere non ricorsive o ricorsive. Ma queste ultime implementano un tipo di ricorsione molto semplice, detta **primitiva** (non mutua ricorsione)
+ Queste vengono definite tramite due clausole di tipo:
	+ $f(x_1, \cdots, x_n, z) = e$ 
	+ $f(x_1, \cdots, x_n, S(y)) = e'$ 
+ Queste definiscono una funzione nel senso che, dato un programma, esso può essere ridotto, applicando le clausole necessarie, fino ad un singolo valore
---
+ Paragonando questo linguaggio alle macchine viste in precedenza, abbiamo che
	+ Configurazioni ferme $\quad \to \quad$ i valori numerici del tipo $S(\cdots S(Z)\cdots)$ 
	+ Riduzione 
		+ Essa è terminante e non deterministica, in quanto in alcuni casi è possibile applicare più di una riduzione allo stesso punto
		+ Nonostante ciò, i risultati ottenuti sono sempre gli stessi, per via della proprietà di terminazione
---
+ L'insieme delle funzioni descritte in PR può essere definito in maniera **induttiva**
+ Passo **Base**:
	+ $z(x_1, x_n) = 0 \; \forall n \geq 0 \quad$ (tutte le funzioni costanti zero) 
	+ $S(x) = x + 1 \quad$ (la funzione successore) 
	+ $\Pi_n(x_1, \cdots, x_n) = x_i\quad$ (proiezione)
+ Passo **Induttivo**
	+ Date $h, g : \mathbb{N^k} \to \mathbb{N}  \quad \forall i \in [1, \cdots, k]\quad$ si ha che
		+ $f(x_1, \cdots, x_k) = h(g_1(x_1,\cdots, x_k), \cdots, g_k(x_1,\cdots, x_k))$ 
		+ Questa è la **composizione generalizzata**, caso generale della composizione classica
	+ Date $h : \mathbb{N}^{n+1} \to \mathbb{N}, \quad g : \mathbb{N}^{n-1} \to \mathbb{N}$ si ha che
		+ $f(x_1, \cdots, x_{n-1}, 0) = g(x_1, \cdots, x_{n-1})$ 
		+ $f(x_1, \cdots, x_{n-1}, y+1) = h(x_1, \cdots, x_{n-1}, y, f(x_1, \cdots, x_{n-1}, y)$
		+ Questa è la **ricorsione primitiva**
---
+ Dire che sappiamo che una funzione è in PR è ben diverso dal dire che conosciamo un programma in grado di calcolarlo
---
+ Possiamo intuire che questo formalismo non è adatto a descrivere tutte le funzioni, in quanto **non** è in grado di descrivere funzioni **parziali**
+ Una dimostrazione è la **numerazione effettiva** di tutti i programmi PR
	+ Ogni programma PR è descrivibile da una stringa. Ciò vuol dire che è possibile ordinare queste stringhe, per lunghezza ed alfabeticamente. 
	+ Essi sono infiniti, ma siccome essi sono numerabili, ciò vuol dire che sono anche numerabili. Siccome sono numerabili, esso è un infinito $\in \aleph_0$, inferiore al numero di funzioni esistenti
	+ Questo ci conferma che il formalismo non è in grado di descrivere tutte le funzioni
+ Siccome la numerazioni è **effettiva**, ciò vuol dire che esistono i seguenti algoritmi
	+ dato n $\to$ programma n-esimo
	+ dato programma n-esimo $\to$ n
+ Negli appunti (10/11/23-14/11/23) viene mostrata una funzione che sfrutta questi algoritmi, e viene dimostrato che essa non appartiene a PR, confermando infine il fatto che **PR non è Turing-Completo**
	+ Essa viene chiamata **dimostrazione per diagonalizzazione**. Funziona per qualunque formalismo tale che:
		1. I programmi/algoritmi descritti sono numerabili
		2. Le funzioni descritte sono totali
	+ Un esempio di funzione totale non in PR è la funzione di Ackermann:
	```FORTRAN
	f(n, m): 
		if (m = 0)
			then n + 1
		else
			if (n = 0)
				then f(m-1, 1)
			else
				f(m-1, f(m, n-1))
	```
	+ È una funzione che cresce troppo velocemente per PR