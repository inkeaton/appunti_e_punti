+ In questo foglio cercheremo di riassumere i contenuti del corso di **Introduzione alla Data Science**
---
# 1 - Preparazione del Dato
+ La preparazione dei dati consiste nel pulire e trasformare i dati per facilitarne l'analisi
+ I dati possono contenere errori di vario tipo:
	+ Typo
	+ Valori errati
	+ Valori nulli
	+ Formati differenti
	+ Inconsistenze
	+ Violazione di vincoli
	+ Duplicati
+ Questo perché essi possono essere incompleti, rumorosi, inconsistenti, a causa del modo in cui sono stati raccolti
+ Le **proprietà principali** che dobbiamo verificare sono le seguenti:
	+ **Consistenza**
		+ Rispetto di regole semantiche
	+ **Precisione**
		+ Massima vicinanza fra valori registrati e valori dell'entità reale
	+ **Completezza**
		+ Evitare la presenza di valori nulli
	+ **Timeliness**
		+ Fare in modo che i dati siano tutti relativi allo stesso periodo
+  Come lo risolviamo?
	+ Si possono correggere o con i valori mancanti (o corretti) o con valori medi
	+ Possiamo buttare via le righe o colonne difettate
# 2 - Esplorazione e Visualizzazione
## Statistiche
+ Un buon metodo per visualizzare i nostri dati è utilizzare i seguenti valori statistici, ognuno indicatore di aspetti differenti:
	+ **Frequenza**
		+ Dato un possibile valore $v_i$ di un attributo di $m$ dati:
		+ $\text{frequenza}(v_i) = \cfrac{\text{n di dati con valore }v_i}{m}$
	+ **Moda**
		+ Dato un attributo, il valore con frequenza maggiore
	+ **Percentili**
		+ Dato un insieme di dati, il percentile $x_p$ è il valore sotto il quale abbiamo il $p\%$ dei dati. 
		+ Si chiamano il primo, secondo e terzo percentile $x_{25\%}, x_{50\%}, x_{75\%}$
	+ **Media**
		+ *Solita roba...*
		+ La media è maggiormente influenzata dagli outliers rispetto alla mediana
	+ **Mediana**
		+ Il secondo percentile $x_{50\%}$
	+ **Indici di dispersione**
		+ Ci dicono quanto i dati siano sparpagliati fra minimo e massimo
		+ **Intervallo**
			+ $\text{range}(x) = \max(x) - \min(x)$
		+ **Varianza**
			+ $\text{var}(x) = \frac{1}{m-1} \sum^{m}_{i=1} (x_i - \underbracket{\bar{x}}_{media})^2$
			+ Influenzata anch'essa dagli outliers (usa la media)
		+ **Deviazione Standard**
			+ $s_x = \sqrt{\text{var}(x)}$
		+ **Intervallo Interquartile**
			+ $\text{IQR}(x) = x_{75\%} - x_{25\%}$
+ Ci sono alcune statistiche anche su insiemi di variabili:
	+ **Covarianza**
		+ $\text{cov}(x_i, x_j) = \frac{1}{m-1} \sum^{m}_{k=1} (x_{ki} - \bar{x}_{i})(x_{kj} - \bar{x}_{j})$
	+ **Correlazione**
		+ $\text{corr}(x_i, x_j) = \cfrac{\text{cov}(x_i, x_j)}{s_is_j}$
		+ Fra $-1$ e $1$
## Grafici
+ I grafici dovrebbero possedere un insieme di proprietà dette **ACCENT**:
	+ **A**pprehension: 
		+ Capacità di percepire correttamente le relazioni tra variabili
	+ **C**larity: 
		+ Capacità di distinguere visivamente tutti gli elementi di un grafico
	+ **C**onsistency: 
		+ Capacità di interpretare un grafico per confronto (similarità) con grafici precedenti
	+ **E**fficiency: 
		+ Capacità di rappresentare una relazione anche complessa in modo semplice
	+ **N**ecessity: 
		+ La necessità che si ha di usare il grafico (ci sono modi migliori per rappresentare la stessa informazione?)
	+ **T**ruthfulness: 
		+ Capacità di determinare il valore rappresentato da ogni elemento del grafico osservando la sua magnitude relativamente ad una scala implicita o esplicita
+ Esistono diversi tipi di grafici molto utili:
	+ **Scatter Plot**
		+ Notare relazioni e correlazioni fra variabili
		+ Per variabili quantitative
	+ **Line Plot**
		+ Per notare variazioni col passare col passare del tempo
		+ Per variabili quantitative
	+ **Bar Plot**
	+ **Istogramma**
		+ Servono per rappresentare e visualizzare la distribuzione di frequenza di una variabile quantitativa
		+ Per variabili qualitative
	+ **Box-Plot**
		+ Vengono utilizzati per mostrare una distribuzione di valori e mettono in evidenza cinque diverse quantità:
			+ Valore minimo
			+ Primo quartile
			+ Secondo quartile (mediana)
			+ Terzo quartile
			+ Valore massimo
		+ *DA CONTINUARE*
	+ **Pie-Chart**
		+ Possono essere usati in alternativa ai grafici a barre quando il numero di categorie è limitato
	+ **Matrici**
		+ Covarianza
		+ Correlazione
		+ Similarità
+ Uno molto figo, per variare la dimensionalità dei dati, è l'**OLAP**, un array multidimensionale, basato su attributi quantizzati o quantizzabili
+ Si possono fare alcune operazioni:
	+ Slicing
	+ Dicing
	+ Roll-Up
	+ Drill-Down
# 3 - Statistica$^+$
+ Ricordiamo il teorema di **Bayes**
	+ $P(F|E) = \cfrac{P(E|F)P(F)}{P(E)}$ 
+ Utile per capire se una nostra ipotesi ha un'alta probabilità di essere verificata (*DA RIVEDERE*)
#### Stime dei punti (DA VEDERE)
#### Intervallo di confidenza
## T-Test per un campione
+ Il t-test per un campione è un test statistico per determinare se un campione di dati numerici (quantitativi) differisce in modo significativo da un altro (come la popolazione o un altro campione)
+ Procedimento:
	1. Specificare le ipotesi
		+ Nulla: le due popolazioni sono statisticamente uguali
		+ Alternativa: Le due sono diverse, o una è minore dell'altra
	2. Controllare le dimensioni del campione
		+ Data la dimensione $N$ del campione e $M$ della popolazione devono valere
			+ $N > 30$
			+ $10N < M$
	3.  Scegliamo un livello di significatività
		+ Solitamente allo $0.05$
	4. Raccogliamo i dati
	5. Effettuiamo il test
		+ Otterremo due valori:
			+ T-test: la deviazione dei valori del campione rispetto all'ipotesi nulla
			+ P-value: la frequenza con cui il risultato ottenuto si otterrebbe per caso
		+ Il risultato è quindi:
			+ Se p-value > livello di significatività 
				+ Non possiamo rigettare ipotesi nulla
			+ Se p-value < livello di significatività 
				+ Rigettiamo ipotesi nulla
			+ Se p-value << livello di significatività 
				+ Rigettiamo ipotesi nulla in favore di quella alternativa
## Chi-Quadro
### Correttezza
+ Si usa quando vogliamo analizzare una variabile categorica da una popolazione o vogliamo determinare se una variabile segue una certa distribuzione, specificata oppure attesa
+ "Confrontiamo quanto osservato con quanto previsto"
+ Procedimento:
	1. Specificare le ipotesi
		+ Nulla: la distribuzione osservata è come quella prevista
		+ Alternativa: Le due distribuzioni sono diverse
	2. Controllare le dimensioni del campione
		+ Data la dimensione $N$ del campione, $M$ della popolazione e $P$ numero dei conteggi devono valere
			+ $P > 5$
			+ $10N < M$ 
	3. Scegliamo un livello di significatività e calcoliamo i gradi di libertà
		+ Solitamente allo $0.05$ 
		+ I gradi sono ($\text{numero di classi} -1$)
	4. Raccogliamo i dati
	5. Effettuiamo il test
		+ $\chi = \sum \cfrac{(\text{Osservato - Atteso})^2}{\text{Atteso}}$
	6. Confrontiamo il risultato con la distribuzione chi-quadrato 
		+ Usiamo gradi di liberà ed intervallo di confidenza per ritrovare il dato necessario
		+ Il risultato è quindi:
			+ La statistica di test è inferiore al valore del chi-quadrato
				+ Non possiamo rifiutare ipotesi nulla
			+ La statistica di test è superiore al valore del chi-quadrato 
				+ Rifiutiamo ipotesi nulla
### Indipendenza
+ Ci aiuta a determinare se due variabili categoriche sono indipendenti fra loro
+  Procedimento:
	1. Specificare le ipotesi
		+ Nulla: le due variabili sono indipendenti
		+ Alternativa: le due variabili non sono indipendenti
	2. Controllare le dimensioni del campione
		+ Data la dimensione $N$ del campione, $M$ della popolazione e $P$ numero dei conteggi devono valere
			+ $P > 5$
			+ $10N < M$ 
	3. Scegliamo un livello di significatività e calcoliamo i gradi di libertà
		+ Solitamente allo $0.05$ 
	4. Raccogliamo i dati
	5. Effettuiamo il test
		+ Per farlo dobbiamo creare la cosiddetta matrice di contingenza, creando quelli osservati, e quelli se fossero indipendenti 
		+ $\chi = \sum \cfrac{(\text{Osservato - Atteso})^2}{\text{Atteso}}$
	7. Confrontiamo il risultato con la distribuzione chi-quadrato 
		+ Usiamo gradi di liberà ed intervallo di confidenza per ritrovare il dato necessario
		+ Il risultato è quindi:
			+ La statistica di test è inferiore al valore del chi-quadrato
				+ Non possiamo rifiutare ipotesi nulla
			+ La statistica di test è superiore al valore del chi-quadrato 
				+ Rifiutiamo ipotesi nulla
# 4 - Machine Learning
## Supervisionato
+ Lo scopo del machine learning supervisionato è stimare una funzione capace di predire e simulare il comportamento dei nostri dati
+ La funzione che cerchiamo deve avere due importanti proprietà: 
	+ Capacità di rappresentare i dati di training (**fitting**) 
	- La capacità di generalizzare ai dati che avremo a disposizione in futuro (**stability** / **generalization**)
### Regressione Lineare
+ Cerchiamo di stimare una retta che simuli il comportamento dei nostri dati
+ Possiamo stimare la sua qualità tramite il calcolo dei residui:
	+ $R = \sum^{n}_{k=1}(\bar{y_k} - y_k)^2$
+ Per trovare la funzione migliore, dobbiamo fare in modo di minimizzare il valore di $R$
+ Altre statistiche utili sono:
	+ $MSE = \frac{1}{n}\sum^{n}_{k=1}(\bar{y_k} - y_k)^2$
	+ $RMSE = \sqrt{\frac{1}{n}\sum^{n}_{k=1}(\bar{y_k} - y_k)^2}$
### Regressione Logistica
+ Si tratta di una generalizzazione del modello di regressione lineare ai problemi di classificazione
+ Con la regressione logistica prevediamo la probabilità che il dato appartenga ad una certa classe
+ Un altro modo per effettuare la classificazione è usare la **classificazione bayesiana naïve**, basata sul teorema di Bayes
## Non Supervisionato
+ In questi metodi, possediamo solo una parte dei dati, e proviamo a dedurne altri valori
### Clustering
+ L’obiettivo degli algoritmi di clustering è di individuare strutture (gruppi di dati «coerenti» rispetto ad una qualche misura) all'interno dei dati
+ Un metodo utile è l'**algoritmo K-means**
	+ L'idea è scegliere un numero $n$ di punti a caso nei dati
	+ Chiameremo essi centroidi. 
	+ Adesso cicleremo, facendo ogni volta:
		+ Assegniamo ad ogni punto il centroide a cui è più vicino
		+ Aggiorniamo la posizione del centroide, rendendolo più centrale
	+ Continuiamo fino a quando i centroidi non si muovono più
+ La scelta del numero di cluster è fondamentale in questo caso. Come facciamo a capire quale è migliore?
+ Possiamo usare il **coefficiente di silhouette**
	+ $SC = \cfrac{\text{distanza media fra cluster} - \text{distanza media fra i punti del cluster}}{\max{(\text{distanza media fra cluster}, \text{distanza media fra i punti del cluster}})}$
+ Quello con $SC$ massimo è il numero di cluster migliore!
### Riduzione Dimensionalità Dati
+ Quando i dati vengono rappresentati con un numero di caratteristiche troppo alto rispetto al numero di dati potremmo incontrare la cosiddetta **curse of dimensionality**
+ Maggiore è il numero di caratteristiche usate per la rappresentazione di un dato, più i dati stessi risultano essere distanti gli uni dagli altri
+ Quando le caratteristiche sono troppe rispetto alle reali necessità rischiamo di non migliorare la capacità descrittiva della rappresentazione, e anzi peggiorare i risultati
+ Una soluzione può essere quella di **riscrivere** i dati in una **base più significativa**