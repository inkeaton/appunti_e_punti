+ La **teoria della calcolabilità** è una materia **primordiale** dell'informatica, nata con l'obbiettivo principale di rispondere alla eseguenti domande:
	1. **È possibile fare tutto con un calcolatore?**
	2. **Se non è possibile, cosa non si può fare?**
	3. **Tutti i formalismi utilizzabili per scrivere un problema sono equivalenti?**
+ Queste domande saranno rianalizzate in modo più formale
---
+ Analizziamo l'insieme delle funzioni:
	+ $f : \mathbb{N}^k \to \mathbb{N}$ 
+ Tutte queste funzioni sono calcolabili con un algoritmo?
+ Innanzitutto, quante sono?
+ Se considerassimo solo le funzioni di scelta, $f' : \mathbb{N} \to \{1, 0\}$, vedremmo che il numero è già $2^n > \aleph_0 = |\mathbb{N}|$ 
	+ È quindi un numero infinito non numerabile
+ Tra queste esistono funzioni non calcolabili?
---
+ Presentiamo un mini-linguaggio, quello delle **Primitive-Ricorsive (PR)**, per vedere la situazione
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