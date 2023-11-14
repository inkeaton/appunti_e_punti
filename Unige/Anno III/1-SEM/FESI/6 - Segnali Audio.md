+ Il suono che percepiamo è un fenomeno complesso, derivato dalla variazione della **pressione** dell'aria
	+ Variazioni **ampie** rappresentano suoni **forti**
	+ Variazioni **rapide** rappresentano toni **acuti**
+ Essi possono essere rappresentati come variazioni delle pressione rispetto alla pressione media, o rispetto alla pressione stessa
	+ Esiste anche una rappresentazione bidimensionale, lo **spettrogramma**, in cui abbiamo il tempo sulle x, le frequenza sulle y, ed il colore per indicare l'intensità
+ In questo caso, la **frequenza** rappresenta il **numero** di **vibrazioni** al secondo, e viene misurata in **Hertz**
	+ Essa è legata al **tono** del suono
	+ Vengono definiti suoni le frequenze comprese fra 20 Hz e 20 KHz
+ L'**intensità** è legata all'**ampiezza** della vibrazione, e viene misurata in **decibel**
	+ Essa è legata al "**volume**" del suono
+ Il rapporto fra le due misure viene misurato in **phon**
---
+ I suoni stessi sono composti a loro volta da altri suoni
+ Possiamo quindi applicare la **DFT** anche ad essi, ma il problema è che la trasformata **non** è in grado di **memorizzare** l'**ordine** degli eventi, fondamentale nel caso del suono
	+ Suoni diversi, ma composti dalla stessa "percentuale" di suoni hanno la stessa trasformata
+ Per ovviare a questo problema, si utilizza la **Short Time Fourier Transform** (STFT), in cui applichiamo la trasformata solo su sezioni della funzione alla volta, ottenendo multiple trasformate