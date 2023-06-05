+ In questo foglio, proveremo a riassumere i concetti chiave studiati nel corso di Teoria dell'Informazione ed Inferenza
# 1 - Probabilità

## A - Basi
* Concetti chiave della probabilità sono i seguenti:
	* __Principio Base__:
		* Se abbiamo due esperimenti, il primo con $N$ risultati, il secondo con $M$, allora i due hanno $N \cdot M$ risultati
	* __Permutazioni__:
		* Il numero di modi possibili in cui poter **ordinare** $N$ elementi. Ricavabile come $N!$ 
	* __Disposizioni__:
		* Il numero di modi possibili in cui **ordinare** un __sottoinsieme__ di $i$ elementi a partire da $N$ elementi. Ricavabile come $\frac{N!}{(N-i)!}$ 
	* __Combinazioni__:
		* Il numero di modi in __scegliere__ $i$ elementi di un insieme di $N$ elementi. Ricavabile come $\frac{N!}{i! \cdot (N - i)!}$. Corrisponde al __coefficiente binomiale__ 
---
## B - Assiomi
* Definiamo tre __assiomi__ da cui costruire un sistema:
	1. $P(S) = 1$ 
	2. $\forall E \subset S \; \; 0 \leq P(E) < 1$ 
	3. $E_1,E_2 \subset S, \; E_1E_2 = \emptyset \; \to \; P(E_1 \cup E_2) = P(E_1) + P(E_2)$ 
* Da essi possiamo ricavare le seguenti __proprietà__: 
	* $P(\emptyset) = 0$ 
	* $P(E^C) = 1 - P(E)$ 
	* $E \subseteq F \to P(E) \leq P(F)$ 
	* $EF \neq \emptyset \to P(E \cup F) = P(E) + P(F) - P(EF)$ 
* Nel caso in cui gli eventi sono **equiprobabili**, il calcolo della **probabilità** di un evento si riduce a:
	* $\cfrac{\# casi favorevoli}{\# casi totali}$ 
* La probabilità **soggettiva** è quella basata su intuizioni, e non calcoli
---
## C - Tipi di Probabilità

#### Probabilità Condizionata
+ La **probabilità** di un evento una volta che si venga a conoscenza della realizzazione di un altro evento casuale.
	+ $P(E|F) = \cfrac{P(EF)}{P(F)}$ 
		+ Questo è un valore relativo a $E$
+ Da essa possiamo ricavare la **regola della moltiplicazione**
	+ $P(EF) = P(E|F)P(F)$ 
+ Essa può essere usata anche su multipli eventi, nel seguente modo:
	* $P(EFG) = P(G|EF)P(F|E)P(E)$ 

#### Probabilità Totale
+ L'unione della probabilità di **tutti i casi** in cui avviene l'evento $E$
	* $P(E) = P(E|F)P(F) + P(E|F^C)P(F^C)$ 

#### Teorema di Bayes
+ Possiamo dedurre dalle formule precedenti:
	+ $P(F|E) = \cfrac{P(E|F)P(F)}{P(E)}$ 
+ Inoltre, riscrivendo tramite la probabilità totale, otteniamo:
	+ $P(F|E) = \cfrac{P(E|F)P(F)}{P(E|F)P(F) + P(E|F^C)P(F^C)}$ 
+ Questo teorema facilita il calcolo di probabilità a **priori** e a **posteriori**
#### Indipendenza degli Eventi
+ Due eventi si dicono **indipendenti** se vale che:
	+ $P(EF) = P(E) \cdot P(F)$ 
---
## D - Variabili Aleatorie Discrete
+ Una __variabile aleatoria__ è una __funzione__ che, partendo dallo __spazio campionario__, ci ritorna un __valore numerico__
+ Le cosiddette __variabili aleatorie discrete__ posseggono un numero __finito__ di risultati
---
+ Ogni __possibile valore__ di una variabile aleatoria possiede una __probabilità associata__
* Queste possono essere __rappresentate__ tramite delle __distribuzioni di probabilità__:
	* La __funzione probabilità di massa__ ($pmf$), la quale associa ad ogni valore la sua probabilità
	* La __funzione probabilità cumulata__ ($CDF$), la quale associa ad ogni valore la sua probabilità sommata alle probabilità dei casi precedenti. 
		* Assume la forma di una __funzione a gradini__, non decrescente
---
* Esistono inoltre due valori che vengono utilizzati per descrivere l'andamento delle funzioni:
	* Il **valore atteso**, una media pesata dei valori assunti dalla VA
		* $\mathbb{E}[X] = \sum^{N}_{i=1}  n_i \cdot P(n_i)$
		* Valgono le seguenti proprietà:
			* $\mathbb{E}[aX-b] = a \cdot \mathbb{E}[X] -b$ 
	* La **varianza**, la distanza media dei valori dal valore atteso:
		* $Var(X) = \sum^{N}_{i=1} (n_i - \mathbb{E}[X])^2 \cdot P(n_i) =  \mathbb{E}[(X - \mathbb{E}[X])^2]$ 
		+ Valgono le seguenti proprietà:
			*  $Var(aX -b) = a^2 \cdot Var(X)$ 
			*  $Var(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2$ 
	* La radice della varianza, la **deviazione standard**
		* $SD(X) = \sqrt{Var(X)}$ 

---
## E - Distribuzioni Discrete di Probabilità
#### Bernoulli
* La VA di Bernoulli ha solo due valori:
	* $P(X=0) = 1-p$ 
	* $P(X=1) = p$ 
* Si ricava che:
	* $\mathbb{E}[X] = p$
	* $Var[X] = p\cdot(1-p)$ 

#### Binomiale
* Questa VA conta i **successi** in una sequenza di $n$ realizzazioni **indipendenti** di una VA di Bernoulli
	* $pmf : \; p(X = i) = \dbinom{n}{i} \cdot p^i \cdot (1-p)^{n-i}$ 
	* $\mathbb{E}[X] = np$
	* $Var[X] = np\cdot(1-p)$ 
+ Questa distribuzione viene meglio descritta, nel caso di una VA continua, dalla distribuzione **Normale**, o Gaussiana

#### Geometrica
* Questa VA vale $n$ se si ottiene un **successo dopo** $n−1$ **fallimenti** in una sequenza di $n$ realizzazioni **indipendenti** di una VA di Bernoulli
	* $pmf : \; p(X = n) = (1-p)^{n-1}\cdot p$ 
	* $\mathbb{E}[X] = \cfrac{1}{p}$
	* $Var[X] = \cfrac{1 - p}{p^2}$ 
* Questa distribuzione mostra la veloce discesa della probabilità in relazione al numero di tentativi, che scende **esponenzialmente**

#### Poisson
+ Questa distribuzione descrive casi come la probabilità di **trovare** $i$ errori in una pagina di un libro, sapendo che in **media** ce ne sono $\mu$
	+ $pmf : \; p(X = i) = \cfrac{\mu^i}{i!}\cdot e^{-\mu}$ 
	* $\mathbb{E}[X] = Var[X] = \mu$ 
+ Per $n$ grandi e $p$ piccoli, la **Binomiale** tende ad **assomigliare** ad una **Poissoniana**

---
## F - Variabili Aleatorie Continue
+ Quando parliamo di valori continui, le $pmf$ e $CDF$ vengono **sostituite** da:
	+ La $pdf$ o **densità di probabilità** (corrispondente alla $pmf$) è una funzione $f$ per cui vale
		+ $P(X \in B) = \int_B f(x) \,dx \; \; B \in \mathbb{R}$ 
	+ La $CDF$ viene ridefinita tramite l'**integrale**, analogo della sommatoria, come:
		+ $F(x) = \int^{x}_{-\infty} f(t) \, dt$ 
+ Si deduce che:
	+ $\cfrac{dF}{dx}(x) = f(x)$ 
		+ Questo **lega** fra loro le due funzioni fondamentali
---
+ Vengono similmente ridefiniti **valore atteso** e **varianza** come:
	+ $\mathbb{E}[X] =  \int^{+\infty}_{-\infty} x \cdot f(x) \, dx$
	* $Var[X] = \int^{+\infty}_{-\infty} (x - \mathbb{E})^2\cdot f(x) \, dx$ 
* Queste vengono modificate **linearmente** in modo coerente alle controparti discrete

---
## G - Distribuzioni Continue di Probabilità 
#### Normale o Gaussiana
* Questa distribuzione si basa sulla VA $X = \mathbb{N}(\mu, \sigma^2)$, VA Gaussiana o Normale. Viene descritta dalla funzione:
	+ $pdf : \; f(x) = \cfrac{1}{ \sqrt{2 \pi}\cdot \sigma} \cdot e^{\cfrac{-(x-\mu)^2}{2\sigma^2}}$ 
	+ $\mathbb{E}[X] = \mu$
	+ $Var[X] = \sigma^2$
+ Questa funzione scala linearmente. Si può notare che è **inversamente proporzionale** al valore di $\sigma$

#### Esponenziale
* Questa distribuzione è usata in casi simili a quella di __Poisson__
	* $pdf : \; f(x) = \begin{cases} \lambda \cdot e^{-\lambda\cdot x} \quad x > 0 \\ 0 \qquad \qquad altrimenti\end{cases}$ 
	* $CDF : \; F_x(c) = 1 - e^{-\lambda \cdot c}$ 
	* $\mathbb{E}[X] = \cfrac{1}{\lambda}$ 
	* $Var(X) = \cfrac{2}{\lambda^2}$ 

---
## H - Variabili Aleatorie Multiple
+ Consideriamo insieme due **VA discrete**
+ La loro $pmf$ __congiunta__ è:
	* $P(x_i, y_j)$ = La probabilità che avvenga sia $x_i$ che $y_j$
	* $P(x_i, y_j) \neq P_x(x_i)\cdot P_y(y_j)$, a meno che non siano **indipendenti**
+ Possiamo calcolare le probabilità delle singole VA, a partire dai valori della pmf congiunta
* Queste sono le __marginalità__
	* $P_X(x_i) = \sum^{m}_{k=1} P(x_i, y_k)$ 
* La __CDF congiunta__ ha forma:
	* $F_{(X, Y)}(a, b) = \sum_{X_i<a}\sum_{Y_j<b} P(i, j)$ 
* Si può anche calcolare la __CDF della marginale__
	* $F_{X}(a) = \sum_{X_i<a}\sum^{m}_{j=1} P_X(i, j)$ 
---
+ Questi discorsi sono attuabili anche sulle VA **continue**, tramite la "traduzione" in integrali, ma sono discorsi particolarmente complessi, e quindi li **tralasciamo**

---
## I - Somme di Variabili Aleatorie
+ Sappiamo che vale
	* $\mathbb{E}[X + Y] = \mathbb{E}[X] + \mathbb{E}[Y]$ 
	* $\mathbb{E}[X \cdot Y] = \mathbb{E}[X] \cdot \mathbb{E}[Y]$        <-- Solo se le due __VA__ sono __indipendenti__ 
* Da quest'ultima proprietà possiamo ottenere due numeri capaci di __quantificare la dipendenza__ di due VA:
	* La __Covarianza__
		* $Cov(X, Y) = \mathbb{E}[X \cdot Y] - \mathbb{E}[X] \cdot \mathbb{E}[Y]$ 
			* Vale che $Cov(a\cdot X, b \cdot Y) = a \cdot b \cdot Cov (X, Y)$ 
	* La __Correlazione__ (Versione __normalizzata__ della Covarianza)
		* $\rho(X, Y) = \cfrac{Cov(X, Y)}{\sqrt{Var(X)} \cdot \sqrt{Var(Y)}}$ 
		* È sempre vero che $-1 \leq \rho(X, Y) \leq 1$ 
---
* __Varianza__ di una __somma__ di VA
	* $Var(X + Y) = Var(X) + Var(Y) + 2 \cdot Cov(X, Y)$ 
	* Si nota che, se le variabili sono indipendenti, $Cov(X, Y) = 0$ 
* Lo stesso discorso vale all'aumentare delle variabili sommate
* __Varianza__ di una __somma__ di VA __indipendenti__
	* $Var(\sum^{N}_{i=1} X_i) = \sum^{N}_{i=1} Var(X_i)$ 

---
## J - Media e Legge dei Grandi Numeri
+ Definiamo la **media** campionaria come:
	+ $\mu_n = \cfrac{1}{n} \cdot \sum^{n}_{i = 1} X_i$ 
+ Dove $n$ è il numero di esperimenti effettuati
+ Questa è una **stima** del valore atteso. Vale che:
	+ $\mathbb{E}[\mu_n] \approxeq \mathbb{E}[X]$ 
	+ $Var(\mu_n) = \cfrac{Var(X)}{n}$ 
		* All'aumentare degli esperimenti, aumenta la __precisione__
---
+ Introduciamo due concetti:
	+ Disuguaglianza di **Markov**:
		+ $P(X \geq a) \leq \cfrac{\mathbb{E}[X]}{a}$ 
			+ La probabilità che un valore di $X$ sia maggiore di un valore $a$ è sempre minore del rapporto fra il valore atteso ed $a$
	+ Disuguaglianza di **Chebyshev**:
		+ $P(|X - \mu| \geq e) \leq \cfrac{\sigma^2}{e^2}$ 
			+ La probabilità che la differenza fra un valore ed il suo valore atteso sia maggiore di $e$ è sempre minore del rapporto fra la varianza ed $e^2$
			+ _controllare es 2.11.1 note_
+ Questi valori sono pensati per aderire a tutte le distribuzioni di probabilità, e sono quindi molto "**larghi**" e generici
---
+ Applicando le precedenti leggi alla media campionaria, otteniamo che:
	+ $\forall \epsilon > 0 \quad\lim_{n \to \infty} P (|\mu_n - \mu| \geq \epsilon) = 0$ 
		+ Al crescere di n, la **probabilità** che $\mu_n$ **differisca** da $\mu$ **tende a 0**
+ Questa è la **legge dei grandi numeri**
+ Applicando Chebyshev, otteniamo che:
	+ $P (|\mu_n - \mu| \geq \epsilon) \leq \cfrac{\sigma^2}{n\epsilon^2}$ 
		+ Questo ci mostra come, al crescere di n, il valore destro tende a 0
---
+ Infine, per il **teorema del limite centrale**:
	+ Le stime di un valore atteso di una qualunque distribuzione tendono a distribuirsi come una normale standard, centrata sul valore atteso.

---
# 2 - Informazione e Codifiche

## A - Teoria dell'Informazione
+ Dato un certo evento E con probabilità di accadere P, definiamo l'**informazione di Shannon** come:
	* $S(p) = \log_2 (\frac{1}{p})$ 
* Da questa definizione intuiamo che:
	* È sempre **positiva**
	* Se la **probabilità** di un evento è **minore**, la sua **informazione** è **maggiore**
	* L'informazione ottenuta da due eventi indipendenti avvenuti è uguale alla somma della informazione singola dei due
+ Essa viene misurata in **bit**, il numero necessario per memorizzarla 
+ _formule utili nel teorema 3.14.4_
---
+ L'**entropia di Shannon** rappresenta invece quanto il valore di una VA è **incerto**, e viene calcolata nel seguente modo:
	* $H[X] = \sum_i p_i S(p_i)$ 
* Corrisponde al **valore atteso** dell'**informazione**
* Essa è **massima** quando i casi sono **equiprobabili**
* In quel caso, su N casi possibili:
	* $H[X] = \log_2 N$ 

---
## B - Entropia Congiunta e Condizionata 
+ Avendo due VA discrete, calcoliamo:
	+ **Entropia Congiunta**
		+ $H(X, Y) = \sum^{N}_{i = 1} \sum^{M}_{j = 1} p(X_i, y_j) \cdot \log_2 \cfrac{1}{p(x_i, y_j)}$
	+ **Entropia Condizionata**
		+ $H(X | Y = y_j) = \sum^{N}_{i = 1} p(x_i | x_j) \cdot \log_2 \cfrac{1}{p(x_i |y_j)}$ 
		+ Da cui otteniamo
		+ $H(X|Y) = \sum^{M}_{j = 1} p_y(y_j) \cdot H(X | Y = y_j)$
+ Possiamo notare che i prodotti utilizzati nei calcoli delle probabilità sono stati trasformati in somme dall'utilizzo del logaritmo
---
+ Ritroviamo che:
	+ $H(x, y) = H(x) + H(y|x) = H(y) + H(x|y)$ 
+ Inoltre
	+ $H(X | Y) \leq H(X)$ 
	+ Questo ha senso: Sapere qualcosa in più non mi farà mai dubitare di più di un risultato
---
+ La **mutua informazione** corrisponde all'informazione ottenibile da una VA dopo averne osservata un'altra
	+ $I(X;Y) \quad = \quad H(X) - H(X | Y) \quad = \quad H(Y) - H(Y|X)$ 

## C - Teoria dei Codici
+ Una **codifica binaria** può essere vista come una funzione $C(x)$  da un insieme di simboli X ad una stringa binaria
+ La **lunghezza** di questa stringa viene chiamata $L_C(x)$ 
+ Le codifiche più efficienti possiedono le seguenti proprietà:
	+ **Univocamente decifrabili**: Se per ogni insieme di simboli $x$ e $y$, le loro codifiche sono differenti 
		+ Questo fa in modo di non aver bisogno di uno spazio nella codifica
	+ **Istantanee**: Se la codifica di ogni simbolo $x$ non è prefisso di nessun'altra codifica
		+ Questo permette di non dover aspettare il simbolo successivo per tradurre la codifica
		+ È possibile controllar ciò se è possibile creare un albero binario della codifica, in cui ogni stringa è una foglia.
		+ Implica **univocità**
---
+ Una codifica deve anche tendere a **comprimere** il più possibile i simboli, in modo da risparmiare spazio
+ Possiamo misurare il successo in questo campo tramite la **lunghezza attesa** di un codice
	+ $L(C, X) = \sum_{x \in X} p(x)L_C(x)$ 
+ Arriviamo quindi al **Teorema di Kraft-McMillian**:
	+ Se una codifica $C$ è **univocamente decifrabile**, allora vale:
		+ $\sum_i 2^{-L_i} \leq 1$ 
+ Da ciò nasce il **Teorema Inverso di Kraft-McMillian**:
	+ Se un insieme di $L_i$ rispetta il teorema precedente, è sempre possibile creare una codifica **istantanea** $C$ in cui $L_C(x_i) = L_i$ 

---
## D - Compressione
+ L'**Informazione grezza** è il numero di bit minimi necessari per rappresentare un informazione.
	+ $H_0 = \log_2 N$ 
+ Essa è il limite inferiore della lunghezza di una codifica. 
+ Più in generale:
	+ La **lunghezza attesa** di una codifica univocamente decifrabile **non** può essere **minore** dell'**entropia** dell'insieme
+ Per la **codifica di Shannon**
	+ **Esiste** sempre una codifica **istantanea** $C$ per i valori assunti da una VA $X$ nell'insieme $S$ per la quale
		+ $H(X) \leq L(C, S) \leq H(X) + 1$ 

#### Codifica di Huffman
+ È un algoritmo di compressione molto semplice. Esso calcola la miglior codifica per **simbolo** possibile
+ Esso funziona nel seguente modo:
	+ Ordina i simboli per probabilità, dal maggiore al minore
	+ A ogni giro, prende i due simboli in coda, con probabilità minore. Essi vengono messi come foglie di un nodo di un albero.
	+ Questo nuovo "nodo" viene riaggiunto alla coda, con probabilità pari alla somma delle sue foglie
	+ Il processo viene ripetuto fino all'unione di tutti i simboli in un unico nodo
	+ L'albero binario ottenuto infine rappresenterà la codifica
+ Questa codifica fa in modo di dare ai simboli meno probabili codifiche più lunghe, e viceversa
+ La codifica ottenuta è **istantanea** per definizione

#### Codifica Aritmetica
+ È un algoritmo di compressione che lavora su un **flusso di dati**, superando alcuni dei limiti di Huffman
+ Esso funziona nel seguente modo:
	+ Viene preso l'intervallo $[0, 1)$
	+ Viene suddiviso in zone, sulla base della probabilità di ciascun simbolo
	+ A ogni simbolo della stringa codificata
		+ Viene scelto l'intervallo corrispondente al simbolo
		+ Questo sotto intervallo viene proporzionalmente suddiviso come nel modo precedente, e viene ripetuta l'operazione col simbolo seguente sul nuovo intervallo
	+ Finita la suddivisione, verrà scelto un valore numerico all'interno dell'intervallo rilevato: questo  valore sarà la codifica della stringa, un numero compreso fra 0 ed 1
+ Per la legge dei grandi numeri, al **crescere di N** lunghezza della stringa, la lunghezza della codifica si **avvicinerà** al **limite** dell'entropia
+ È possibile anche implementare una versione del codice che calcola le probabilità nel mentre della codifica

#### Codifica Convoluzionale
+ Questa codifica viene usata in casi in cui ci sia del rumore nel canale di comunicazione
+ Questa funziona nel seguente modo:
	+ Prendiamo la sequenza di $N$ bit che dobbiamo codificare
	+ A ogni giro
		+ Prendiamo un bit, e calcoliamo $P$ bit di parità, calcolati sulla base di $K$ bit, compreso il bit stesso che stiamo guardando
	+ Alla fine invieremo questi  $P \cdot N$ bit di parità
+ È possibile implementare una macchina a stati finiti per effettuare la codifica
+ Risulta invece maggiormente complessa la **decodifica**. Come abbiamo detto, il messaggio verrà trasmesso in un canale con rumore, quindi potrebbe arrivare alterato. Come faremo a capire qual'era la stringa originale?
+ In generale, assumeremo che fosse quella più **somigliante** a quella ricevuta
+ Usiamo un algoritmo, di **Viterbi**, di programmazione dinamica. Esso calcolerà la stringa più simile a quella ricevuta

# 3 - Inferenza

## A - Inferenza Frequentista
+ Questo tipo di inferenza si basa sul **principio di massima verosimiglianza**:
	+ Misurando dei dati, questi saranno generati dalla distribuzione di probabilità che massimizza la probabilità di vederli
+ Possiamo quantificare questa probabilità tramite la **verosimiglianza**:
	+ $L(X | \theta) = \prod^{n}_{i=1} f_\theta(x_i)$ 
	+ Questa è la probabilità che il valore x sia stato generato dalla distribuzione dipendente dal valore $\theta$ 
+ Quindi, la nostra **stima** di $\theta$ corrisponderà a:
	+ $\theta_0 = \arg \max_{\theta \in \Theta} \prod^{n}_{i = 1} f_\theta (x_i)$ 
+ Solitamente applichiamo il **logaritmo** a questo conto poiché, essendo funzione monotona, non cambia il massimo ricercato, e facilita il calcolo, trasformando la produttoria in una sommatoria
+ Utilizzando queste proprietà, è possibile crearsi degli **stimatori**, funzioni capaci di calcolare i parametri di una distribuzione sulla base dei valori campionati
	+ Nel caso di **Bernoulli** e **Normale**, abbiamo come stimatori:
		+ $p_0 = \cfrac{1}{n} \sum^{n}_{i= 1} x_i$ 
		+ $\mu_0 = \cfrac{1}{n} \sum^{n}_{i= 1} x_i$
		+ $\sigma_0^2 = \cfrac{1}{n} \sum^{n}_{i= 1} (x_i - \mu_0)^2$
			+ Quest'ultimo stimatore è in parte incorretto. Quindi si preferisce dividere per $n - 1$
+ Uno stimatore viene detto **distorto** se non considera tutti i casi possibili, altrimenti viene detto **corretto**

---
## B - Inferenza Bayesiana
+ Un altro metodo di inferenza si basa sull'applicazione del Teorema di **Bayes**, e l'applicazione del **principio di massimo a posteriori** (MAP)
+ Il sistema si basa sul calcolare le probabilità a posteriori di determinati eventi, basati sulle loro verosimiglianze, e sceglierne il maggiore. All'aumentare dei campionamenti, il valore scelto si avvicinerà sempre di più a quello scelto con inferenza frequentista
+ La differenza col frequentista ha al cuore il fatto di avere **conoscenze a priori**, le quali aiutano a velocizzare l'avvicinamento al valore da stimare, a parità di valori campionati

---
## C - Metodi Monte Carlo
* Non c'è molto da dire, che non sia già stato esplorato in **APA**

---
## D - Catene di Markov
* Immaginiamo di studiare un sistema $S$, capace di assumere $N$ stati in un tempo $t$ 
* Un **processo di Markov** è una coppia $(S, P)$ , dove P è una matrice di transizione (TM) $N\times N$. In essa:
	* $P_{i,j} = Pr(S_{t+1} = S_j | S_{t} = S_i)$ 
* Questo è un processo **senza memoria**: Non serve studiare i casi precedenti per calcolare i successivi
* Per l'equazione di Chapman-Kolmogorov:
	* $Pr(s_j|s_i t, in \; t \; passi) = (P^t)_{i,j}$ 
* Si può dire che una TM è
	* **Irriducibile** se, per ogni stato, esiste un tempo $t$ che permette di raggiungere tutti gli altri
		* Le TM che possiedono stati **assorbenti**, in cui le probabilità sono tutte concentrate in un punto, non possono essere irriducibili
	* **Regolare** se il $t$ precedente è uguale per tutti gli stati $s_i$
		* In senso matematico, se $P^t$ non possiede 0
---
* Una **distribuzione stazionaria** o vettore stocastico $q$ è un vettore $(1, N)$, per un sistema S se vale che:
	* $q^TP =q^T$ 
	* È una distribuzione di probabilità (quindi i suoi valori sommano a 1), oltre ad essere un autovettore, con autovalore 1.
* Se una TM è regolare, essa ammette un **unica** distribuzione stazionaria
* Una **distribuzione limite** è un vettore $\lambda$, tale che 
	* $P^t \to_{t \to +\infty} \begin{pmatrix}\lambda_1 & \lambda_2 & \cdots  & \lambda_n \\ \vdots \\ \lambda_1 & \lambda_2 & \cdots  & \lambda_n \end{pmatrix}$
* Una TM regolare ha un unica distribuzione limite, corrispondente alla distribuzione standard