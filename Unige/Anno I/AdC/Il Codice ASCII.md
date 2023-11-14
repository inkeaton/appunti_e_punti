Il Codice  ASCII
martedì 12 ottobre 2021
10:23

- Codice a 7 bit utilizzato per rappresentare caratteri, sia stampabili che di controllo (es, \n "newline")
- Caratteri stampabili
    - 48 --> 57 = 0, 1, 2.. 9
    - 65 --> 90 = A,B… Z
    - 97 --> 122 = a,b… z
    - (Sono presenti anche simboli come \, ., ?, etc)
- Esempi di caratteri non stampabili (in totale, 32 circa)
    - 0 = "null" (terminatore di stringa, spazio vuoto)
    - 8 = "backspace" (sposta il cursore indietro di uno, o cancella un carattere)
    - 12 = "form feed" (Veniva usato nelle tele scriventi per passare al foglio successivo)
    - 27 = "escape" (può terminare un'applicazione)
- Questo codice può essere utilizzato per rappresentare anche altre cose
- ES.
    - Una targa è formata da quattro lettere e 3 numeri
    - Utilizzando il codice, possiamo rappresentarla in 49 bit, usando 7 caratteri ASCII

RIDONDANZA

- La ridondanza consiste nello spreco di spazio codificato
- Essa può essere calcolata attraverso il coefficiente di ridondanza R
    - R = n° combinazioni totali / n° combinazioni usate
- Ad esempio, proviamo a calcolare R per il codice ASCII, considerando solo i caratteri stampabili come usati
    - R = 2^7 / 2^7 - 32 = 1,3 (periodico)
- R è sempre >= 1
- Nel caso dell' ASCII, 1,3 è uno spreco molto lieve ed inevitabile. Infatti, ogni qualvolta si vuole rappresentare un numero di informazioni non in base 2, si avrà uno spreco
- Lo spreco viene considerato elevato quando R >= 2
- Proviamo a calcolare R per l'esempio delle targhe di prima
    - R = 2^49 / 26^4 * 10^3 = 10^6 (circa)
- Si può notare uno spreco enorme. Si potrebbero rimuovere dal codice circa 20 bit (log2R) rendendo il codice minimale (contrario di ridondante) ovvero 1< R < 2
- Un modo per calcolare le combinazioni necessarie è valutare il numero di valori possibili per cifra, vedere quale potenza di 2 è necessaria per rappresentarli tutti, e sommare gli esponenti di queste potenze, oppure fare log2(n° combinazioni usate)

ERRORI E DISTANZA DI HAMMING

- Un codice con R>2 può essere talvolta utile.
- In particolare, esso ci permette di rilevare un predeterminato numero di errori, numero dipendente da un nuovo concetto, la distanza di Hamming
- Essa si può descrivere come un valore che indica il numero di bit differenti l'uno dall'altro fra due combinazioni binarie
- ES.
    - 1010101010
    - 1011001010    D.H. = 2
- Prendiamo ad esempio un codice a 10 bit. Se fosse un codice minimale, ogni combinazione avrebbe un senso, ed il calcolatore non sarebbe in grado di comprendere eventuali errori di battitura, semplicemente penserebbe che gli sia stata comunicata un'altra combinazione, valida, dal significato differente.
- Invece, in un codice ridondante, è possibile incappare in combinazioni non utilizzate, le quali verranno sicuramente riconosciute come un errore
- A tal scopo, spesso si aggiunge un bit in più del necessario al codice utilizzato, in modo da avere un R > 2
- Un metodo per comprendere le combinazioni valide è il cosiddetto controllo di parità
- Si considerano valide solo le combinazioni con n° di 1 pari.
- Ma se può notare, che il controllo funzionerebbe solo in caso di un n° di errori (e D.H) dispari. Infatti, con due errori, il n° di 1 sarebbe nuovamente corretto, ed il calcolatore interpreterebbe in modo differente la stringa.
- È necessario un metodo ben più sofisticato

Creato con OneNote.