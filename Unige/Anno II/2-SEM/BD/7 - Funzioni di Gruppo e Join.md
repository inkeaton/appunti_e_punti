* Normalmente l'operazione di JOIN contiene nel risultato solo i valori che sono stati abbinati. 
* Oltre a questo JOIN, chiamato INNER, esiste una seconda versione, l'OUTER JOIN, che permette di ricevere anche tuple non abbinate. Si possono controllare tramite le keyword:
	* FULL: Tutte le tuple
	* LEFT: Le tuple della relazione sinistra
	* RIGHT: Le tuple della relazione destra
* I valori mancanti verranno riempiti con NULL
---
* È possibile eseguire operazioni sugli attributi risultanti di un SELECT
---
* Molto interessanti sono le funzioni di gruppo:
	* MIN
	* MAX
	* AVG
	* SUM
	* COUNT
* Queste possono essere usate nel SELECT per calcolare valori sull'insieme degli attributi riportati
* Però, come facciamo se volessimo eseguire operazioni solo su un sottoinsieme di tuple?
* Possiamo usare la keyword GROUP BY per raggruppare insiemi sulla base di un attributo
```SQL
SELECT Regista, AVG(Valutazione), MAX(Valutazione), MIN(Valutazione), COUNT(*)     
FROM Film;
GROUP BY Regista
```
* Ma nel far ciò, potremo estrarre solo attributi comuni ai gruppi, oppure funzioni di gruppo.
* Si possono inoltre filtrare i gruppi tramite la clausola HAVING (similmente al WHERE). Questa calcola condizioni sul gruppo, non sulle singole tuple