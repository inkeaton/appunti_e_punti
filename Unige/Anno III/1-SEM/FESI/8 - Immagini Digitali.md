+ Nel mondo digitale, le immagini vengono rappresentate come **matrici bidimensionali** di pixel
+ Il significato del valore del pixel dipende dal tipo di immagine
	+ Intensità luminosa, colore, calore, etc...
+ Com'era nel mondo mono-dimensionale, si può effettuare la trasformata di Fourier anche a questo genere di segnale.
	+ Al posto di sinusoidi, si ottiene una somma di **onde planari**
+ Bisogna solo stare attenti alla nuova dimensione introdotta, e come questa complichi le cose
+ Oltre a effettuare le solite somme, si compiono anche degli **shift** e delle **normalizzazioni**, per aiutare a comprendere cosa stia succedendo visivamente
+ Tecnicamente:
	+ Calcoliamo la trasformata di Fourier
	+ Shiftiamo il risultato ottenuto
	+ Applichiamo il modulo
	+ Normalizziamo tramite il $\log_{10}$ 
+ Come in 1D, possiamo applicare filtri
+ Si possono anche applicare le **derivate doppie**, unendo due derivate parziali
	+ Quella sulla x mostrerà le variazioni in orizzontale, quella sulla y in verticale. Unendole, otteniamo la derivata vera e propria
+ Questa derivata mette in evidenza gli **edge**, o contorni, ovvero cambiamenti significativi e locali all'interno di un immagine
+ Possono ricordare i contorni di un oggetto, ma non sono collegati a questo