* Vediamo come effettuare diversi tipi di interrogazioni in SQL e Algebra Relazionale
---
##### Ridenominazione
* Quest'operazione riporta gli attributi richiesti nel formato indicato
	* $\rho_{b_1,\cdots,b_k \; \leftarrow \; c_1, \cdots, c_k} R$ 
* Su può usare in SQL come:
```SQL
SELECT Anno AS Uscita
FROM Film
```

##### Proiezione
* Riporta solo alcune colonne della relazione, eliminando i duplicati
	* $\Pi_{b_1, \cdots, b_k} R$ 
* Il grado sarà uguale all'originale, la cardinalità minore o uguale
* Si può usare in SQL in due modi:
```SQL
SELECT Anno, Regista    
FROM Film;

SELECT DISTINCT Anno, Regista /* Elimina i duplicati */
FROM Film;
```

##### Selezione
* Questa operazione estrae alcune righe da una relazione sulla base di una formula logica
	* $\sigma_{F} R$ 
* La formula sarà composta da $\wedge, \vee, \neg$ e formule atomiche di forma $A_i \theta A_j$ dove $\theta \in \{=, \neq, \leq, <, \geq, > \}$ e $A_i, A_j$ sono attributi della relazione o valori degli attributi
* In SQL si scrive nel seguente modo
```SQL
SELECT *
FROM Film
WHERE Regista = "Tim Burton"
```
---
* Un problema non presente in algebra relazionale ma importante in SQL è la presenza di __attributi__ __nulli__. Nel valutare questi valori nelle formule logiche, si aggiunge ai valori logici un terzo valore, __unknown__, il quale non è ne vero o falso, e non influenza direttamente i valori delle formule
* Viene inoltre aggiunto un predicato per cercare valori nulli, ovvero `IS NULL`

##### Prodotto Cartesiano
* Questa famosa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \times S$ 
* Dato $U_R \bigcap U_S$ ,  $U_{R \times S} = U_R \bigcup U_S$ 
* grado($R \times S$) = grado($R$) + grado($S$)
* cardinalità($R \times S$) = cardinalità($R$) $\cdot$ cardinalità($S$)
* In SQL viene scritta come
```SQL
SELECT *
FROM Film, Cinema
```
---
* Possiamo gestire la presenza di attributi omonimi tramite l'utilizzo di una denominazione. Questa accortezza non è necessaria in SQL, in quanto il sistema etichetta automaticamente gli attributi con la relazione a cui sono associati

##### Unione
* Anche questa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \bigcup S$ 
* __grado__($R \bigcup S$) = grado($R$) = grado($S$)
* max(cardinalità($R$), cardinalità($S$)) $\leq$ __cardinalità__($R \bigcup S$) $\leq$  cardinalità($R$) + cardinalità($S$)
* Essa può essere utilizzata solo se le relazioni possiedono uno stesso schema, $U_R = U_S$, ed in SQL solo se i due schemi sono equivalenti, caratterizzati da tipi comuni 
*  In SQL viene scritta come
```SQL
SELECT *
FROM Film
UNION
SELECT *
FROM Documentario
```

##### Sottrazione Insiemistica
* Anche questa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \setminus S$ 
* $U_R = U_S = R_{R \setminus S}$ 
* cardinalità($R \setminus S$) $\leq$  cardinalità($R$)
*  In SQL viene scritta come
```SQL
SELECT *
FROM Film
EXCEPT/MINUS  // Uno di questi due
SELECT *
FROM Documentario
```

---
* Oltre a queste operazioni, è possibile ottenerne alcune, dette derivate, combinando quelle esistenti
---
##### Intersezione
*  Anche questa operazione binaria viene definita in modo equivalente alla corrispettiva insiemistica, e scritta come:
	* $R \bigcap S$ = $R \setminus (R \setminus S)$ 
* $U_R = U_S = R_{R \bigcap S}$ 
* 0 $\leq$ cardinalità($R \bigcap S$) $\leq$ min(cardinalità($R$), cardinalità($S$))
*  In SQL viene scritta come
```SQL
SELECT *
FROM Film
INTERSECT
SELECT *
FROM Documentario
```

##### Theta-Join
* Esso rappresenta un prodotto cartesiano seguito da una selezione, e ci permette di prendere elementi di relazioni che rispettano una formula atomica
* Viene scritta come:
	* $R \bowtie_{A\theta B} S$ 
* 0 $\leq$ cardinalità($R \bowtie_{A\theta B} S$) $\leq$ min(cardinalità($R$), cardinalità($S$))
* In SQL viene scritto come
```SQL
SELECT DISTINCT Titolo, Regista
FROM Noleggio JOIN Video
ON Noleggio.Colloc = Video.Colloc
```

##### Natural-Join
* Questa è una variante del Join, in cui vengono unite le righe sulla base di attributi comuni. Questo viene solitamente utilizzato per navigare chiavi esterne
* Bisogna fare attenzione perchè unisce TUTTI gli attributi comuni, sono solo quelli che vogliamo, ed è quindi utile utilizzarlo in comune ad una Ridenominazione