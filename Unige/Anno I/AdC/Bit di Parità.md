Bit di Parità
martedì 12 ottobre 2021
11:04

- In che modo possiamo rilevare un numero di errori pari, utilizzando il metodo del bit di parità?
- Aggiungiamo un ulteriore bit di parità!

- Proviamo a creare un codice con D.H >= 3, così da poter rilevare 1 o 2 errori
- Partiamo da un codice ad 1 bit. Saranno necessari due bit di parità, portando a due possibili codici
    - 000       (P1P2B)
    - 111
- La verifica della parità avviene ad un bit di parità per volta, ovvero: controllo prima se P1+B = pari, poi se P2+B = pari
- Volendo rappresentare più di un bit di informazione, dovremo aumentare i bit di parità. In particolare, per il seguente numero di bit di parità, l'informazione codificabile sarà:

|     |     |     |
| --- | --- | --- |
| P   | B   | Tot |
| 2   | 1   | 3   |
| 3   | 4   | 7   |
| 4   | 11  | 15  |
| 5   | 26  | 31  |
| 6   | 57  | 63  |

- Si può notare che il tot è sempre uguale a 2^P - 1

ALGORITMO DI VERIFICA

- Ora è necessario creare un algoritmo in grado di verificare correttamente i bit di parità
- A tal scopo, posizioneremo i bit di parità nelle posizioni del codice equivalenti alle potenze di 2
- ES.
    - Proviamo a codificare nel modo descritto la lettera B in ASCII
        - 1000010
    - Dovremo codificare 7 bit di informazione, quindi basteranno 4 P

    -

|     |     |     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  | 11  |
| 1   | 0   | 1   | 0   | 0   | 0   | 0   | 1   | 0   | 1   | 0   |
| P1  | P2  | B3  | P3  | B5  | B6  | B7  | P4  | B9  | B10 | B11 |

    - Adesso bisogna determinare il valore dei P
    - Per farlo, bisogna andare a verificare in quali B, osservando la posizione, sarà necessario il valore della posizione del P per arrivare a quel numero. Trovati questi B, si osserva quale valore (0 o 1) sarà necessario per renderlo pari
        - P1  è necessario in ogni B dispari , quindi 1, 3, 5, 7, 9, 11. La somma dei loro valori da 1, quindi P1=1
        - P2  è necessario in 3 (2 + 1) 6 (2 + 4), 7 (1 + 2 + 4), 10 (2 + 8) ed 11 (1 +2 + 8). La somma dei loro valori è 2, quindi P2= 0
        - P3  è necessario in 5, 6 e 7. La somma è 0, P3= 0
        - P4  è necessario in 9, 10, 11. La somma è 1, P4= 1

CORREGGERE GLI ERRORI

- Sapendo di avere una stringa errata, e conoscendo, per esempio, che è presente 1 errore, sarà ora possibile correggere questo errore.
- Infatti, basterà verificare la D.H con le stringhe corrette. Tutte hanno fra di loro D.H = 3, ma la stringa errata avrà, con una sola, D.H = 1. Questa sarà la stringa originariamente codificata.
- Il discorso rimane uguale nel caso di due errori, considerando D.H = 2
- Naturalmente, il nostro codice non sarà in grado di rilevare più di due errori, per motivi precedentemente spiegati. Per fare ciò, servirà ideare un codice con D.H superiore.

Creato con OneNote.