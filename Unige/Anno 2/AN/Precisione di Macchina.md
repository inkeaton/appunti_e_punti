## Floating Point
* Nei computer, sono presenti numerosi __errori inerenti__, dovuti al modo in cui i numeri vengono memorizzati nel computer
* Il metodo più diffuso è il _floating point_, usato per descrivere un ampio range di numeri, anche decimali
	* $x =\pm B^p \cdot f$ 
	* $B$ è la __Base__ del sistema
	* $p$ viene chiamato __Caratteristica__, ed è un valore compreso fra due estremi
	* $f$ è la __Mantissa__, e descrive la parte decimale del numero, di $t$ cifre.   $B^{-1} \leq f \leq 1$ 
* Dovrò decidere quanto spazio riservare ad ognuna delle componenti del sistema. In base a questa decisione si formerà un insieme denominato __numeri di macchina__, il quale rappresenta l'insieme dei numeri rappresentabili.
	* Un esempio è quello dei numeri __double__ in C++ ovvero $F(2, 52, 1024, 1023)$ 
	* 2 è la base, __52__ i bit riservati alla mantissa, e la caratteristica è compresa fra -1024 e +1023, ovvero è codificata in __11__ bit, ed il segno sarà codificato in __1__ bit (64 bit totali)
---
* Nonostante il grande range a nostra disposizione, è sempre __impossibile__ rappresentare tutti i valori esistenti, senza incorrere in qualche __errore inerente__
* I calcolatori si trovano spesso a __convertire__ il numero reale in modo da poterlo conservare
* Due sono i metodi principalmente usati:
	* __Troncamento__: Consiste nel considerare nella mantissa errata $\tilde{f}$ solo i primi $t$ valori, troncando la mantissa reale
	* __Arrotondamento__: Metodo principalmente usato, consiste nel agire in modo diverso in base al valore della cifra $d_{t+1}$ :
		* $d_{t+1} < \frac{B}{2} \to \tilde{x} := trn(x)$ 
		* $d_{t+1} \geq \frac{B}{2} \to \tilde{f} := trn(f) + B^{-t}$  
* Quanto può essere __grande__ l'__errore commesso nell'arrotondare__?
	* __Errore assoluto__:
		* $|\delta| = |\tilde{x} - x | \leq B^p \cdot \frac{1}{2}B^{-t}$ 
	* __Errore relativo__:
		* $|\epsilon| = \frac{|\tilde{x} - x |}{|x|} \leq\frac{1}{2}B^{-t +1} = \mu$ 
* Quest'ultimo valore viene chiamato __precisione di macchina__, $\mu$ 
	* Nei __double__ in c++, $\mu \approx 210^{-16}$ 
	* __errore inerente__ $\approx c_f \cdot errinput \approx c_f \cdot \mu$ 
---
 ## Errori algoritmici
* Questo errore inerente crea __errori__ nel __calcolo__ con __valori minori__ della __precisione di macchina__
* Proviamo ora a calcolare l'__errore__ __algoritmico__ creatosi dalle operazioni fra numeri memorizzati in un calcolatore:
	* __Somma__ o __Sottrazione__
		* $\epsilon_{a\pm b} \circeq \frac{a}{a\pm b} \epsilon_a \pm \frac{b}{a\pm b} \epsilon_b + \epsilon$ 
		* Possiamo notare la presenza di __coefficenti di amplificazione__ vicino agli errori relativi degli addendi
		* Questi coefficenti tendono ad un valore elevato nel caso delle operazioni di __cancellazione__, ovvero quando facciamo $a+b$, $a \approx -b$  (oppure $a-b$ , $a \approx b$ )
		* Quindi, un errore anche __piccolo__, verrà __amplificato enormemente__ in queste situazioni
	* __Moltiplicazione__ 
		* $\epsilon_{a\cdot b} \circeq \epsilon_a + \epsilon_b + \epsilon$ 
		* Possiamo notare l'assenza di coefficenti di amplificazione, rendendo l'operazione __sicura__
	* __Divisione__ 
		* $\epsilon_{\frac{a}{b}} \circeq \epsilon_a - \epsilon_b + \epsilon$
		* Similmente a prima, __non sono presenti situazioni sospette__