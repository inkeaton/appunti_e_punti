* In linguaggi con semantica __statica__, le variabili vengono __dichiarate__ ed usate in modo __coerente__ alla loro definizione
* In linguaggi con semantica __dinamica__, questo valore può __variare__, al massimo creando errori statici
* I primi sono più complessi, ma efficienti, i secondi più semplici ed espressivi
* È __difficile__ sviluppare __compilatori__ per i linguaggi __dinamici__, si usano degli __interpreti__
---
* Esistono tre possibili errori in un linguaggio:
	* __Sintassi__: è stato scritto in modo errato il codice
	* __Statico__: errori dovuti alla semantica statica di un linguaggio
	* __Dinamico__: un errore che viene segnalato a run-time
* La __sintassi__ è il __modo__ in cui qualcosa è scritto, la __semantica__ è il __significato__ che diamo a questo qualcosa
---
* Un __Alfabeto__ $A$ è un insieme non vuoto, finito, di simboli 
* Una __Stringa__, su un alfabeto $A$, è una sequenza $\color{Apricot} u : [1...n] \to A$ tale che:
	* $[1...n]$ è l'__intervallo__ di numeri naturali $i$ tale che $1 \leq i \leq n$ 
	* $u$ è una funzione __totale__
	* $n$ è la __lunghezza__ di $u$ 
* Un __Programma__ può essere definito come una stringa su di un alfabeto
---
* Una stringa __non__ __vuota__ può essere rappresentata come:
	* $u : [1, 2, 3, 4] \to A$ 
		* $u(1) = w$ 
		* $u(2) = o$ 
		* $u(3) = r$ 
		* $u(4) = d$ 
	* Questa è la stringa "__word__" 
---
* La __concatenzione__ è "l'unione" di stringhe. è associativa ma __non__ commutativa
* La stringa vuota $\color{Lavender}\emptyset$ o $\color{Lavender}\epsilon$, è l'elemento __neutro__ 
* È un __monoide__
* Vale l'__iterazione__ delle stringhe, dimostrata tramite induzione: $u^n$ è u __concatenata__ $n$ volte
---
* $A^n$ = l'insieme delle stringhe di lunghezza $n$ fatte con l'alfabeto $A$
* $A^+$ = l'insieme delle stringhe di lunghezza $>0$  fatte con l'alfabeto $A$
* $A^*$ = l'insieme delle stringhe fatte con l'alfabeto $A$
---
* Un __linguaggio__ fatto su $A$ è un sott'insieme di $A^*$ 
* Esiste un modo matematico per definire un linguaggio specifico?
* Certo, lo definiamo come la composizione di altri due linguaggi
* Questi possono essere composti tramite l'__unione__ e la __concatenazione__
* Il __Linguaggio__ è un __monoide__, tramite la __concatenazione__, che eredita dalla concatenazione delle stringhe le sue proprietà
* L'insieme vuoto è l'__identità__ della concatenazione
* Valgono simili concetti, come $L^n$, $L^0$, $L^+$ e $L^*$ 
* $L^+ = L \cdot L^*$ 
___
* __Espressioni regolari__
* Sono delle convenzioni usate per rappresentare insiemi di stringhe
* $a|b = a \cup b$ 