+ Possiamo vedere la Macchina di Turing come un **calcolatore**, ovvero una macchina che realizza una **funzione** input $\to$ output **parziale** (può non terminare)
+ Essa è definita dalla tupla seguente
	+ $\mathcal{MdT} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Mulberry}{\delta}, \textcolor{Yellow}{B})$ 
	+ Non abbiamo più bisogno di stati finali
---
+ Per poter calcolare le funzioni dobbiamo essere in grado di **codificare** input ed output
+ Avremo bisogno delle due funzioni seguenti, **iniettive** ma non surgettive
	+ $C_{in}: \text{Input} \to \Sigma^*$ 
	+ $C_{out}: \text{Output} \to \Sigma^*$ 
+ La macchina calcola il risultato nel seguente modo:
	+ Prima converte l'input in linguaggio macchina
	+ Esegue le computazione 
	+ Ci sono tre casi possibili ora
		1. Arriva ad una configurazione ferma, legge l'output e vede che corrisponde ad un valore. Questo è il **risultato** della computazione
		2. Arriva ad una configurazione ferma, legge l'output e vede che non corrisponde a nessun valore. La funzione **non è definita** su questo input
		3. La computazione non termina mai. La funzione **non è definita** su questo input
+ In generale queste funzioni sono **parziali**
---
+ Diciamo che una funzione è **Turing-Calcolabile** se esiste una $MdT$ in grado di calcolarla. Questo concetto può essere esteso a quello di calcolabilità