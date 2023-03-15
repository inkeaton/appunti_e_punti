* La probabilità __condizionata__ è il calcolo della probabilità di un evento $E$ __in seguito__ ad un evento $F$
* Essa viene definita come:
	* $P(E|F) = \frac{P(EF)}{P(F)}$ 
* Da essa ricaviamo la cosiddetta __regola della moltiplicazione__
	* $P(EF) = P(E|F)P(F)$ 
* Essa può essere usata anche su multipli eventi, nel seguente modo:
	* $P(EFG) = P(G|EF)P(F|E)P(E)$ 
---
* La probabilità __totale__ di un evento $E$ può essere calcolata come:
	* $P(E) = P(E|F)P(F) + P(E|F^C)P(F^C)$ 
* Possiamo descriverla come l'unione della probabilità di tutti i casi in cui avviene l'evento $E$
---
* Un teorema fondamentale della probabilità è il teorema di __Bayes__:
	* $P(F|E) = \frac{P(E|F)P(F)}{P(E)}$ 
* In esso, $P(F|E)$ è la cosiddetta probabilità a __posteriori__, $P(F)$ è la probabilità a __priori__ 
* Questo teorema ci permette di sfruttare tutte le informazioni che possiamo ottenere
* Potremmo usarlo per risolvere, ad esempio, il problema delle tre carte, o di __Monty Hall__