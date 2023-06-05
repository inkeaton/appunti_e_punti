* Listiamo i diversi tipi di esercizi presenti nelle prove d'esame, e come risolverli

## Errori
* Data una funzione $f(x)$, determina il condizionamento del problema del calcolo di $f(x)$ per valori che tendono a $t$
	1. Calcoliamo $c_f = \frac{x \cdot f'(x)}{f(x)}$ 
		* Per facilitare i caloli, si possono usare diverse scritture di $f(x)$, come suggerite dagli algoritmi proposti
	2.  Calcoliamo il valore $c = \lim_{x \to t} c_f$. In base all'entità di $c$ determiniamo se il problema è ben o mal condizionato
* Studiare l'errore d'approssimazione nei seguenti algoritmi
	1. Creiamo il grafo, connettendo ogni passaggio dell'algoritmo come dovuto
	2. Etichettiamo i nodi con l'errore relativo a quella variabile, gli archi con il coefficente relativo a quell'errore
	3. Riscriviamo il calcolo dell'erroe finale, sommando gli errori di ogni step moltiplicati con i loro coefficenti
		* Il coefficiente di ogni errore è la somma dei prodotti dei coefficienti per ogni nodo attraversato dall'errore, cammino per cammino
	4. Per dimostrare che l'algoritmo sia stabile od instabile basta verificare che uno dei coefficienti tenda a $\pm \infty$ nel punto considerato

## Rotazioni di Givens
* Dato un vettore $\begin{pmatrix} a \\ b \\ \vdots \\ c \end{pmatrix}$ , viene richiesto una serie di rotazioni di Givens tali che il vettore divenga $\begin{pmatrix} q \\ 0 \\ \vdots \\ 0 \end{pmatrix}$ o simili, con $q \in \mathbb{R}$ 

## Approssimazione ai minimi quadrati
* Data una funzione contenente dei parametri ed una serie di punti, si richiede di ritrovare i valori dei parametri tali che la funzione approssimi ai minimi quadrati i dati forniti

## Diagonalizzazione e Metodo delle potenze Inverse
* Data una matrice, viene richiesto di diagonalizzarla, se possibile, e studiare il metodo delle potenze inverso con uno shift $p$
* 