* __Teorema di Cramer__:
	* Se $m=n$, $AX=B$ ammette un __unica__ soluzione, __se e solo se__, $|A| \ne 0$ 
	* $X=A^{-1}B = \frac{1}{\det(A)}A^*B$ 
* Ogni soluzione avrà __forma__ $x_i = \frac{|A_{C^A_i \leftrightarrow B}|}{\det(A)}$ , in cui cambiamo la colonna $i$ di $A$ con $B$ 
* E se $\det(A) = 0$? $\to$ Teorema di __Rouchè-Capelli__
	* Il sistema __ammette__ soluzioni se e solo se $rk(A) =rk(A|B)$ 
	* Nel caso ci siano soluzioni, queste __saranno__ $\infty^{n-rk(A)}$ 