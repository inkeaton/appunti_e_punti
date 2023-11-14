Codici ad Espansione
venerdì 15 ottobre 2021
16:53

- In un codice di questo tipo, alcune codifiche utilizzano un numero diverso dal normale di bit, in modo da risparmiare complessivamente numero di bit.
- ES.
    - Partiamo da una codifica a 2 bit. Abbiamo 4 possibili combinazioni 00, 01, 10, 11
    - Mettiamo che 11 indica una lunghezza maggiore di bit, 5 per la precisione.
    - Avremo quindi 11000, 11001, 11010, 11011, 11100, 11101, 11110, 11111
    - Potremmo continuare, usando 11111 come indicatore di una lunghezza di 11 bit, per esempio
- Un secondo metodo consiste nel "numerare" le lunghezze di codice necessarie
- ES.
    - 0 - 00|00
    - 1 - 01|000000
    - 2 - 10|0000000000
    - 3 - 11|000000000000
    - Ogni numero iniziale indica una lunghezza di bit differente
- Questo tipo di codice viene usato nella codifica delle istruzioni del processore, il codice macchina

ENTROPIA

- Definita da Shannon
    - ![](46238aee84284d51a0c7f417d94b559a.png)
- Immaginiamo di avere due persone, Alice e Bob. Bob chiede ad Alice se vuole andare al mare. Lei gli risponderà attraverso un messaggio a 1 bit. Egli si aspetta due possibili tipi di risposta, o sì o no.
- Non avendo altre informazioni disponibili, egli da 1/2 di probabilità a sì, ed 1/2 è no
- Calcoliamo l'entropia
    - ![](029a511864f8425f9b31b8dc8b702cec.png)
- Essa è uguale ad 1 (dato che il messaggio è su 1 bit). Ciò vuol dire che il contenuto informativo del messaggio è massimo.
- Ma questo valore dipende dalle aspettative del ricevente. Questo perché se Bob sapesse che la probabilità di sì è superiore, mettiamo 3/4, il calcolo darebbe 0,84. Questo perché parte dell'informazione comunicata era ridondante, essendo già intuita da Bob
- Anche se l'informazione venisse scomposta in più messaggi, il contenuto informativo rimarrebbe di valore uguale
- Idealmente cerchiamo di avere un entropia bassa, ma non azzerata, perché in tale contesto il messaggio sarebbe completamente inutile

Creato con OneNote.