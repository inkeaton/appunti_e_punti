+ Un **filtro** è una funzione che lascia passare alcune componenti del segnale e ne elimina altre 
+ Il concetto di filtro risulta molto chiaro nel dominio delle **frequenze**, qui possiamo parlare di 
	+ Filtri **passa basso**: lasciano passare immodificate le basse frequenze, eliminano le alte frequenze 
	+ Filtri **passa alto**: lasciano passare le alte frequenze 
	+ Filtri **passa banda**: lasciano passare le frequenze comprese tra due valor
+ Una funzione che annulla perfettamente gli intervalli voluti sono detti **filtri ideali**
+ Un esempio è il filtro passa basso ideale:
	+ $H(\omega) = \begin{dcases}A \quad |\omega| < \omega_c \\ 0 \quad \text{altrimenti}\end{dcases}$ 
+ Esso si applica moltiplicandolo con la trasformata del segnale che vogliamo modificare
+ Purtroppo però, si può notare che si tratta di una funzione $\text{rect}$. La sua trasformata è la funzione $\text{sinc}$, particolarmente scomoda da utilizzare. 
+ Per tal motivo, i **filtri ideali** risultano essere **inutilizzabili**
+ Si preferiscono quindi utilizzare altri filtri, come la funzione **gaussiana** e il filtro di **Butterworth**, i quali hanno trasformate più semplici
+ In Butterworth:
	+ $N$, l'ordine, determina l'accuratezza del taglio, ma anche la difficoltà d'approssimazione
	+ $\omega_c$, il cutoff o frequenza di taglio, il punto in cui vogliamo tagliare
![[Butterworth.png]]
---
+ Nel dominio del **tempo**, il filtraggio avviene tramite la convoluzione. Nel caso di funzioni discrete, useremo la **convoluzione discreta**:
	+ $g[n] = \sum_{k=o}^{N-1} h[k]\cdot f[n-k]$ 
+ E i **filtri** come variano?
+ Diventano quindi **array**, anche di dimensioni differenti dalla nostra funzione. Funzionano come **finestre**
---
+ In generale, i filtri possono essere utilizzati per:
	+ Evidenziare specifici **pattern**
	+ Ridurre il **rumore** di un segnale