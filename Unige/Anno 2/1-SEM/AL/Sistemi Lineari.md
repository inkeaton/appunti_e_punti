* Un __sistema lineare__ può essere riscritto con __tre matrici__:
	* A contenente i __coefficenti__ delle variabili
	* X contenenti le __variabili__
	* B contenente i __termini noti__
* Riscritto come $AX = B$ , può essere risolto nel caso $A$ sia __quadrata__ ed __invertibile__ ($X = A^{-1}B)$. Questa soluzione è unica
* La soluzione non cambia se effettuiamo operazioni con le matrici elementari, e possiamo quindi __ridurre__ le matrici A e B per facilitare i calcoli
* Una volta ridotto sappiamo che:
	* Il sistema __ha__ soluzione se __non__ ci sono __pivot__ nell'__ultima colonna__
	* Se il numero di __pivot__ è __uguale__ al numero di __incognite__, abbiamo un __unica__ soluzione, se è __minore__, esistono $\infty^{n-p}$ soluzioni