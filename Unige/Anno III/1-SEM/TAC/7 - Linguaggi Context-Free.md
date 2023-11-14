+ I linguaggi context-free sono una categoria di linguaggi non regolari, che vengono identificati da una grammatica **BNF**
+ Per la precisione, una **grammatica context-free** è una tupla dalla forma:
	+  $\mathcal{G} : ( \textcolor{Apricot}{T}, \textcolor{LimeGreen}{N}, \textcolor{WildStrawberry}{\mathcal{S}}, \textcolor{Cyan}{\mathcal{P}})$ 
		+ $\textcolor{Apricot}{T}$ è l'alfabeto dei terminali, i **simboli** utilizzati nel linguaggio
		+ $\textcolor{LimeGreen}{N}$ è l'alfabeto dei non-terminali, i **meta-simboli** ottenuti per costruzione
		+ $\textcolor{WildStrawberry}{\mathcal{S}} \in \textcolor{LimeGreen}{N}$ è il simbolo iniziale, o **assioma**
		+ $\textcolor{Cyan}{\mathcal{P}}$ è un insieme di coppie $(A \in \textcolor{LimeGreen}{N}, \alpha \in ( \textcolor{Apricot}{T} \cup \textcolor{LimeGreen}{N}))^*$, che descrivono le possibili **derivazioni** 
+ Tramite le derivazioni, la grammatica è in grado di **generare un linguaggio**
	+ $\mathcal{S} \xrightarrow{*} n \in T^*$ 
+ A ogni passaggio, una determinata $\alpha$ viene riscritta in una certa $ \beta$ seguendo le trasformazioni descritte dalle coppie in $\mathcal{P}$ 
+ Quindi
	+ $L(\mathcal{G}) = \{u \; | \; \mathcal{S} \xrightarrow{*} u\}$
+ *La derivazione può essere anche fatta tramite uno schema ad albero*
---
+ Come facciamo a **dimostrare** che una grammatica $\mathcal{G}$ è stata definita in modo **corretto**?
+ Dobbiamo dimostrare due proprietà:
	1. Se la stringa viene riconosciuta, appartiene al linguaggio (**Soundness**)
	2. Se la stringa appartiene al linguaggio, viene riconosciuta
+ La **prima** proprietà è **facilmente dimostrabile**, ridefinendo l'automa in maniera induttiva, e sfruttando quindi il principio d'**induzione**
+ Per la **seconda** è necessario un **ragionamento ad hoc**, a seconda della grammatica analizzata
---
+ ***MANCA LA DIMOSTRAZIONE CHE UN LINGUAGGIO CONTEXT-FREE È IN GRADO DI GENERARE TUTTE LE STRINGHE CHE SI VOGLIONO***