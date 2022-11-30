Codici Numerici
mercoledì 29 settembre 2021
15:58
Codici per la rappresentazione dei numeri A LUNGHEZZA VARIABILE

- Allo scopo di rappresentare grandezze numeriche, è necessario utilizzare un codice
- Il più comune è la rappresentazione posizionale in base 10
    - 27 = 2*10^1 + 7*10^0
- Un altro è il sistema numerico romano
    - 2021 = MMXXI
- Questi sistemi condividono il fatto di essere a lunghezza variabile, ovvero il fatto che ogni numero viene rappresentato da un numero di caratteri diverso.
- Necessario in questi sistemi è l'utilizzo dello spazio vuoto, che permette di comprendere inizio e fine dei numeri

- Di un sistema numerico, due sono le caratteristiche principali da considerare:
    - Sinteticità: il numero di caratteri necessario per scrivere i numeri
    - Semplicità degli algoritmi: Facilità nell'effettuare calcoli
- Interessante è provare ad utilizzare sistemi con differente base da 10
- ES.
    - BASE 16 (1,2,3,4,5,6,7,8,9,A,B,C,D,E,F), 10 = A
    - BASE 8 (1,2,3,4,5,6,7), 10 = 12

BASE 2

- In particolare, è molto interessante utilizzare la BASE 2 (0,1)
- Essa infatti, per quanto sia molto meno sintetica rispetto alle precedenti (ES. 10 = 1010), permette di effettuare calcoli in modo molto più veloce e semplice.
- ES.
    - Per effettuare moltiplicazioni, è necessario conoscere solo conoscere due tabelline

0*x = 0
1*x = x

- Inoltre, è utile in un computer, per il fatto che utilizza solo due simboli, assimilabili a spento-acceso
- Essa può essere anche facilmente convertita in BASE 16 ed 8
- ES.
    - Per la base 16, bisogna considerare il numero preso a gruppi di 4

1|0001 = 11

- Per la BASE 8, a gruppi di 3

10|101|110|010 = 2562

- Spesso questo genere di conversione viene utilizzato per convertire le cifre in un formato più sintetico e comprensibile dall'utente

Rappresentazione a LUNGHEZZA FISSA

- Molto vantaggioso può essere l'utilizzare un sistema a lunghezza fissa, ovvero uno in cui ogni numero ha la stessa lunghezza
- Questo ha il vantaggio di rendere superfluo lo spazio vuoto, dato che sappiamo sicuramente dove inizia e finisce il numero, oltre a semplificare ulteriormente gli algoritmi di calcolo ma ha lo svantaggio di avere un tetto massimo di numeri rappresentabili
- ES.
    - Codice in BASE 2, 8 BIT

0 < x < 255

- Questa rappresentazione viene utilizzata nel codificare suoni
- Nei computer odierni si utilizzano rappresentazioni a 32 (massimo 2^32 valori) o 64 (2^64) bit, numeri capaci di soddisfare largamente le necessità dei moderni calcolatori
    - Talvolta vengono utilizzati sistemi a 128 bit, solitamente nel generare codici univoci ed irripetibili

Creato con OneNote.