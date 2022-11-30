* Il corso di __Algebra Lineare ed Analisi Numerica__ è improntato all'implementazione della teoria matematica nella programmazione
---
# Problemi
* Il nostro obbiettivo come programmatori e matematici è risolvere problemi
* Come programmatori, potremmo ristrovarci con problemi legati alla memoria o al tempo necessario
* Come matematici, analizzeremo i problemi reali, attraverso il seguente processo
	* Creeremo un __modello matematico continuo__, il quale è un modello basato su dati generici, capace di rappresentare il problema in termini matematici
	* Questo si evolverà in un __modello matematico reale o discreto__, il quale sarà basato su un numero di input ed output definito, e più vicino alla realtà del problema
	* Dallo studio di questo modello otterremo infine un __algoritmo__, una soluzione al nostro problema
* è però vero che non sempre è possibile risolvere i problemi
* Spesso può essere che il problema proposto possiede __errori__ nella sua struttura
---
# Errori
* Errori __analitici__: nascono nella formulazione del PROBLEMA, nella traduzione in MODELLO MATEMATICO o nella discretizzazione (MODELLO DISCRETO); 
* Errori __inerenti__: sono errori di misurazione ad esempio, sono sempre presenti (DATI); • 
* Errori __algoritmici__: riguardano le approssimazioni che si adottano nell'algoritmo (RISULTATI INTERMEDI).
* Gli errori di cui dobbiamo invece preoccuparci sono gli errori legati ai __valori__ del problema
* Indichiamo i valori in questo modo:
	* $x$  valore __esatto__
	* $\tilde{x}$  valore __perturbato__ (errato)
* Gli errori dei valori possono essere descritti in più modi:
	* L'errore __assoluto__ è calcolabile come $d_x = \tilde{x} -x$, e rappresenta lo scostamento fra il valore esatto e quello perturbato
		* Questo tipo di errore ha il problema di non rendere immediatamente evidente l'entità dell'errore, dipendente dal valore esatto iniziale
	* L'errore __relativo__ calcolabile come $r_x =\frac{\tilde{x} - x}{x}$ rappresenta invece l'__entità__ dell'errore, grazie al confronto col valore esatto
* È possibile calcolare il __condizionamento__, ovvero un valore che indica quanto un errore in $x$ influisce su $f(x)$ 
* Esso è uguale a ${cond}_x = \frac{r_{f(x)}}{r_x}$
	* Il minimo e miglior valore che possiamo avere è 1
* Utilizzando le definizioni dei valori presenti nella formula, possiamo riscriverla come:
	* ${cond}_x = \frac{f(\tilde{x}) - f(x)}{f(x)} \cdot \frac{x}{\tilde{x} - x}$ 
* Notando il rapporto incrementale, questo valore diventa noto come __coefficente di amplificazione__ e viene riscritto come segue:
	* $\lim_{\tilde{x} \to x} = \frac{x \cdot f'(x)}{f(x)}$ 
