* Una matrice quadrata viene detta __nilpotente__ se esiste N $\in \mathbb{N}$ tale che $A^N =0$   
* Una matrice nilpotente __non__ è invertibile
* L'inversa della matrice identica è se stessa
* Se una matrice $A$ è invertibile allora $A^{-1}$ è invertibile
* $(AB)^{-1} = B^{-1} \cdot A^{-1}$ 
* $GL_n(K)$ è l'insieme delle __matrici invertibili__. $(GL_n(K), \cdot)$ è un __gruppo__
---
* Un importante gruppo di matrici invertibili sono le matrici __elementari__:
	* $I_n$, la matrice __identica__
	* $E_{ij}$, ottenuta dalla matrice identica __scambiando la riga i con la riga j__
	* $E_i(\lambda)$, ottenuta dalla matrice identica __moltiplicando per $\lambda$__ la riga $R_i$  della matrice identica
		* $E_i(\lambda)^{-1} = E_i(\lambda^{-1})$ 
	* $E_{ij}(\lambda)$, ottenuta dalla matrice identica __aggiungendo alla riga $R_i$ la riga $\lambda R_j$__
	* Moltiplicando una matrice elementare a sinistra con una matrice qualsiasi otteniamo lo stesso effetto della matrice elementare su quella normale
---
* Possiamo usare queste qualità per effettuare la __Riduzione di Gauss__, un algoritmo che riduce le matrici a __matrici a scalini__, ovvero in cui il primo elemento non nullo della riga i+1-esima è più a destra del primo elemento della riga i-esima	

![[Gauss.png]]

* Il numero di pivot sarà sempre minore od uguale al numero di righe della matrice
* È possibile rendere la matrice completamente ridotta, ovvero ridotta, con i pivot uguali a 0, e con gli elementi sopra le colonne dei pivot uguali a 0
* Tutte le matrici sono totalmente riducibili
* La totalmente ridotta di una quadrata è l'identica, o ha almeno l'ultima riga nulla
---
* Si può notare che partendo dall'identica, ed effettuando su di essa tutte le operazioni elementari effettuate su A per giungere alla sua totalmente ridotta, riducendo totalmente A otteniamo anche la sua inversa