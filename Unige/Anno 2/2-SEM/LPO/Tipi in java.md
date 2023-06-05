* I tipi primitivi sono:
	* byte
	* short
	* char
	* int
	* long
	* float
	* double
* Ognuno dipende da tipi precedenti
	* int <= long <= float <= double
	* byte <= short <= int
	* char <= int

* Esistono due tipi di trasformazioni, widening e narrowing.
* I primi possono passare a sottotipi superiori
* Le seconde corrispondono al passare a tipi inferiori, perdendo dati

* Ogni tipo ha una wrapper class, che contiene metodi utili per il tipo
* Bisogna evitare di usare `==` e `!=`  con gli oggetti immutabili 