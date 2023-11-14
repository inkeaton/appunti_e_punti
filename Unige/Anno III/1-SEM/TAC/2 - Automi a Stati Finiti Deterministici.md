+ Un **automa** è un algoritmo, una macchina estratta
+ Inizieremo vedendo una sotto categoria, gli automi **riconoscitori**
+ In particolare, gli **automi a stati finiti deterministici** (DFA)
+ Essi vengono definiti tramite una tupla:
	+ $\mathbb{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Cyan}{F}, \textcolor{Mulberry}{\delta})$ 
		+ $\textcolor{Apricot}{Q}$ è un insieme di **stati**, situazioni, in cui si può trovare la macchina
		+ $\textcolor{LimeGreen}{\Sigma}$ è l'**alfabeto** usato dalla macchina
		+ $\textcolor{WildStrawberry}{q_0}$ è lo **stato iniziale** della macchina
		+ $\textcolor{Cyan}{F}$ è l'insieme degli **stati finali** della macchina
		+ $\textcolor{Mulberry}{\delta}$ è la **funzione di transizione**, il funzionamento ad ogni passo, dell'automa
+ L'automa funziona quindi nel seguente modo:
	1. L'automa si troverà inizialmente nello stato $q_0$ 
	2. Esso riceverà una stringa $\sigma u$. Egli si troverà quindi nella configurazione $<q_0, \sigma u>$ 
	3. Egli esegue quindi la funzione $\delta : Q \times \Sigma \to Q$, la quale, prendendo lo stato attuale ed il primo carattere della stringa $\sigma$, determina il prossimo stato $q_1$, passando alla configurazione $< q_1, u>$ 
	4. Egli ripeterà il passaggio *3*  fino a che non arriverà ad una configurazione $<q_n, \epsilon>$ 
	5. Quindi:
		+ Se $q_n \in F$ , la stringa è stata **riconosciuta**
		+ Altrimenti, viene **rifiutata**
+ Gli automi possono essere rappresentati come:
	+ Tramite la definizione di $\delta$
	+ Tramite una matrice
	+ Graficamente
---
+ Ogni singolo momento in cui si trova l'automa è una **configurazione** $<q_n, u>$ 
	+ *Una sequenza di specifiche configurazioni viene chiamata computazione*
+ Alcune particolarità sono:
	+ Configurazioni **d'arresto**, da cui non si può passare ad alcun'altro stato
	+ Configurazioni **deterministiche**, in cui si può andare ad un unico stato
+ Una relazione di riduzione viene detta **terminante**, se **non** permette **computazioni infinite**
---
+ La **chiusura riflessiva e transitiva** $\to^*$ indica che i due stati possono essere raggiunti in un numero finito di passi
	+ È facilmente dimostrabile per induzione (*dettagli nel cartaceo*)
+ Il **linguaggio accettato** è l'insieme delle stringhe riconoscibili da un'automa
	+ $L(M) = \{u \; | <q_0, u> \; \to^* \; <q_f, \epsilon>, \; q_f \in F\}$ 
		+ Può essere definita induttivamente (*dettagli nel cartaceo*)
+ Le **direttive d'esecuzione** indicano quando un passo viene completato
	+ Nel DFA, corrisponde all'esecuzione di $\delta$
+ Le **direttive I/O** indicano il modo in cui viene fornito l'input e l'output
	+ Nel DFA, l'input è una stringa, l'output un segnale binario
---
+ Come facciamo a provare che un automa riconosce il linguaggio voluto?
	1. Ogni stringa in $L$ viene accettata
	2. Tutte le stringhe restanti vengono rifiutate