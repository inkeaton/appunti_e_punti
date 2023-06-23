* Un classico problema è quello del **guardarobiere distratto**:
	* **N** persone vanno ad una festa, tutti con un cappello differente, e lo consegnano all'ingresso al guardarobiere. All'uscita, ne ricevano uno casuale. 
	* **Quante persone ricevono il proprio cappello?**
* Si risolve facilmente tramite le proprietà delle **VA**
	* Consideriamo ogni persona come una VA indicatrice di Bernoulli. La possibilità che valga 1, ovvero che abbia il suo cappello, è $\frac{1}{N}$, e corrisponde al suo valore atteso
	* Possiamo calcolare il **valore atteso della somma di VA**, ovvero di tutte le persone, come la **somma dei loro valori attesi**. 
	* Questa corrisponderà a $n \cdot \frac{1}{n}$, ovvero **1** 
	* Ci aspettiamo che **una** sola persona torni a casa col proprio cappello
---
* Il LVQuickSort è una variante del QuickSort, in cui ad ogni giro scegliamo un pivot differente, a caso
* Come fa a essere **più efficiente** di quello normale?
* Per capirlo, prendiamo una VA indicatrice $I(i, j)$. Questa variabile ha valore 1 se gli elementi in posizione i e j vengono confrontati nel corso dell'algoritmo
* Questo accade solo se uno dei due viene scelto come **pivot**, per cui
	* $P(I(i, j) = 1) = \cfrac{2}{j - i +1}$ 
* Pensiamo ora ad una seconda VA indicatrice, $X$, la quale indica il numero di **confronti totali** eseguiti in un esecuzione dell'algoritmo. Qual'è il suo valor medio?
	* $\mathbb{E}[X] = \sum_i \sum_j \mathbb{E}[I(i, j)] = \sum_i \sum_j \cfrac{2}{j - i +1}$ 
* Questo valore è una **sommatoria** molto particolare, la quale non converge a 0 abbastanza velocemente da poter essere calcolata normalmente
* Possiamo **approssimarne** il valore tramite il seguente **integrale**
	* $\int^{n}_{i + 1} \cfrac{2}{t - i + 1} dt \approx 2 \ln(n - i + 1)$ 
* Questo valore rimane molto basso. Osservando dati empirici, noteremo che i tempi di esecuzione medi si avvicineranno molto spesso a questo valore, cementando l'algoritmo in $O(n \log n$ )
* È quindi **sempre preferibile** alla versione **iterativa**