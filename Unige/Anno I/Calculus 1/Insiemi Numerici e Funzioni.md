# Insiemi Numerici
* In questo corso ci concentreremo sulle Funzioni Reali, definite come $f:\mathbb{R}\rightarrow\mathbb{R}$
* Questo perchè l'Analisi ci fornisce strumenti in grado di analizzare queste funzioni in particolare
## Cos'è $\mathbb{R}$?
* $\mathbb{R}$ è l'insieme dei numeri Reali. Esso è totalmente ordinato e viene rappresentato come una retta orientata, su cui sono segnati i punti 0 e 1
* $\mathbb{R}$ è quindi identificato da tutti i punti che appartengono a questa retta
* Sottoinsiemi di $\mathbb{R}$ sono:
	* $\mathbb{N}$: i Numeri Naturali $\{0, 1, 2, 3...\}$
	* $\mathbb{Z}$: i Numeri Interi $\{...-2, -1, 0, 1, 2...\}$
	* $\mathbb{Q}$: i Numeri Razionali $\{\frac{m}{n} \;|\; m \in \mathbb{Z}, n \in \mathbb{N} \}$
* Mentre i primi due insiemi possono essere facilmente rappresentati sulla retta, $\mathbb{Q}$ non può essere individuato su di essa, questo per via della sua **DENSITA'**
* ### LEMMA: DENSITA' DI $\mathbb{Q}$
	* $\forall x, y \in \mathbb{R} \;|\; x < y, \quad \exists q \in \mathbb{Q} \;|\; x < q < y$
---
* Altri sottinsiemi particolari di $\mathbb{R}$ sono gli **INTERVALLI**
	* Intervalli LIMITATI (geometricamente assimiliabili a segmenti)
		* $(a, b) = \{x \in \mathbb{R} \;|\; x > a, \; x < b\}$ INTERVALLO APERTO
		* $[a, b] = \{x \in \mathbb{R} \;|\; x \ge a, \; x \le b\}$ INTERVALLO CHIUSO
		* $[a, b) = \{x \in \mathbb{R} \;|\; x \ge a, \; x < b\}$ INTERVALLI SEMIAPERTI
		* $(a, b] = \{x \in \mathbb{R} \;|\; x > a, \; x \le b\}$
	* Intervalli ILLIMITATI (geometricamente assimilabili a semirette)
		* $(a, +\infty) = \{x \in \mathbb{R} \;|\; x > a\}$ SEMIRETTA APERTA
		* $[a, +\infty) = \{x \in \mathbb{R} \;|\; x \ge a\}$ SEMIRETTA CHIUSA
		* $(-\infty, a) = \{x \in \mathbb{R} \;|\; x < a\}$ SEMIRETTA APERTA
		* $(-\infty, a]  = \{x \in \mathbb{R} \;|\; x \le a\}$ SEMIRETTA CHIUSA

## Funzioni, Dominio e Codominio

* Come già specificato, in questo corso studieremo funzioni reali, con dominio $dom(f) \in \mathbb{R}$
* Per questo motivo, nell'indicare il DOMINIO di una funzione ci riferiremo al "più grande insieme di definizione", e non a $\mathbb{R}$
* ES
	* $f(x) = \frac{1}{x}$ è definita per $x \neq 0$
	* Dunque, $dom(f) = \mathbb{R}^* = (-\infty, 0) \cup (0, +\infty)$
* ### DEF: FUNZIONE
	* Una funzione $f : dom(x) \rightarrow \mathbb{R}$ è un' associazione biunivoca di un elemento del dominio di $f$ con uno di $\mathbb{R}$
	* In particolare: $\forall x \in dom(f) \, \,\exists !\, y \in \mathbb{R} \;|\; f(x) = y$
* Particolarità delle funzioni reali è lapossibilità di rappresentare il loro GRAFICO nel PIANO CARTESIANO
* Come una retta rappresenta $\mathbb{R}$, il piano rappresenta $\mathbb{R}^2 = \{(x, y) \;|\; x \in \mathbb{R}, y \in \mathbb{R}\}$ 
* Il grafico della funzione è invece $graph(f) = \{(x, f(x) \in \mathbb{R}^2 \;|\; x \in dom(f) \} \subseteq \mathbb{R}$
* Il grafico esiste solo all'interno del dominio
* ### DEF: IMMAGINE DI $f$
	* $Im(f) = \{y \in \mathbb{R} \;|\; \exists x \in dom(f) \;|\; f(x) = y\}$
	* Questa è il CODOMINIO