+ Vediamo ora le applicazione di Fourier nel discreto
+ Se prendiamo una funzione, e la "periodizziamo", la sua trasformata di Fourier è discreta
+ Invece, se facciamo la trasformata di una funzione discreta, otterremo una funzione periodica, ma continua.
+ Quindi, per ottenere un risultato comodo, possiamo "periodizzare" la nostra funzione discreta. La trasformata che si otterrà sarà **discreta**, e **periodica**
+ Otteniamo quindi la definizione di **Trasformata Discreta di Fourier** (DFT)
![[DFT.png]]
---
+ Similmente, l'inversa corrisponde a:
![[DFT-1.png]]
---
+ La DFT di un segnale **discreto a valori reali** ha una simmetria speciale: 
	+  La parte **reale** è **simmetrica pari** 
	+  La parte **immaginaria** è **simmetrica dispari**
+ In particolare:
	+ Se $f$ è reale e pari, $F$ è reale e pari
	+ Se $f$ è reale e dispari, $F$ è immaginaria e dispari
+ Inoltre
	+ Se $f$ è reale, $F[0]$ è reale
---
+ Bisogna stare attenti a non perdere i punti di riferimento della funzione nella **periodizzazione**, ovvero: **Da dove iniziava**?
	+ Questo porta il **problema dello shift**
	+ Un modo per evitarlo è memorizzare in un array separato i **tempi** relativi ad ogni punto
+ Bisogna in particolare stare attenti ai **cambi di fase**:
![[CambiDIFase.png]]