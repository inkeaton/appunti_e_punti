Cancellazione e Numeri negativi
venerdì 15 ottobre 2021
15:51

- Oltre a possibili errori di trascrizione, sono da considerare possibili cancellazioni
- Per evitare ciò, si potrebbe aggiungere una copia della nostra informazione. In questo modo se si cancellasse una, avremmo l'altra. Ma avremmo bisogno del doppio dei bit d'informazione
- Un altro metodo è dividere la nostra informazione, codificata per esempio su 8 bit, in due trance da 4 bit l'una, su due dispositivi diversi, con quindi dimensione totale equivalente.
- Ad essi aggiungiamo un ulteriore sequenza in 4 bit, sulla quale si troveranno i bit di parità, nel seguente modo
    - Codifichiamo 10110001

|     |     |
| --- | --- |
| Primo blocco | 1011 |
| Secondo blocco | 0001 |
| Blocco di parità | 1010 |

- Questo metodo viene usato nel codice RAID5
- In questo modo si usano solo 4 bit in più, aggiungendo meno ridondanza.
- Questa idea si può allargare, spezzettando sempre di più, ma aumenta il rischio di cancellazione

NUMERI NEGATIVI

- ![](fe021b17a96f4c29b85fefe5c1f4b6f2.png)
- CI serve un codice a lunghezza fissa
- Un primo metodo è quello a Modulo e Segno
    - Rappresentiamo il segno come un bit: 0 = +
    - ES
        - -3 =  10000011
- Il problema di questa rappresentazione insorge nei calcoli, somma ed addizione
- Un modo migliore è già il Complemento a 1
    - Il numero negativo è l'inverso del positivo
    - ES
        - + 8 = 0000000000001000

 -8 = 111111111111111110111

- In ogni caso, non ci aiuta negli algoritmi
- Viene quindi introdotto il Complemento a 2
    - Il numero negativo è l'inverso del positivo, a cui viene sommato +1
    - ES
        - +8 = 0000000000001000

-8 =           1111111111110111 +
      1 =
                 1111111111111000

- Proviamo una somma
- 7 + (-8)
    - 00000111 +
    - 11111000 =
    - 11111111 == -1, corretto
- L'algoritmo di somma funziona!
- Un'altra caratteristica di questa rappresentazione è il fatto di avere uno zero unico
- Un'altra rappresentazione che utilizza un solo 0 è la rappresentazione in Eccesso 2^(n-1)
    - ES
        - Prendiamo una rappresentazione ad 8 bit. N = 8
        - 2^(8-1) = 128 = 1000000
        - Questo valore viene sommato ad ogni numero
            - 0 = 10000000 + 00000000 = 10000000
        - Il valore più alto è 127 = 11111111
        - Questo si può applicare anche ai numeri negativi.
        - Posso quindi rappresentare numeri compresi fra -128 < x < 127
- L'unica differenza con la rappresentazione precedente è la presenza di un numero negativo in più ed il fatto che gli algoritmi non sarebbero utilizzabili

NUMERI FRAZIONARI

- Un primo modo per rappresentarli è il Fixed Point, a virgola fissa
    - Similmente ai numeri binari naturali, si considerano determinate posizioni potenze negative di 2
    - Tutto sta nello scegliere la posizione della virgola, che rimane fissa
    - ES
        - 3,75 = 1 + 2 + 1/2 + 1/4

|     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 1   | 1   | ,   | 1   | 1   | 0   | 0   |
| 2^4 | 2^3 | 2^2 | 2^1 |     | 2^-1 | 2^-2 | 2^-3 | 2^-4 |

- Questo metodo viene usato nel calcolo delle probabilità, nell'utilizzare numeri compresi fra 1 e 0
- Il secondo, più complesso, ma utile, è il Floating Point, a virgola mobile
    - V = (-1)^s * 2^e * m
    - In questa rappresentazione, un numero può avere più rappresentazioni
    - Per questo si usano per la maggior parte dei numeri rappresentazioni normalizzate, ovvero nelle quali m (Mantissa) è compreso fra 1 e 2
    - Queste seguono lo standard IEEE754. La rappresentazione cambia a seconda dei bit.
    - Ora la vedremo su 32 bit, in cui 1 bit è usato per il segno, 8 per l'esponente e 23 per la mantissa
    - Alcuni numeri non possono essere scritti in questa forma, ma mostreremo più avanti che essi possono essere rappresentati comunque attraverso l'uso di e (Esponente) in forme non normalizzate ma uniche
    - Un esempio di numero è

    -

|     |     |     |     |
| --- | --- | --- | --- |
| 1 = | 0   | 01111111 | 00000000000000000000000 |
|     | Segno | Esponente | Mantissa |

    - La MANTISSA
        - Essa rappresenta la parte frazionaria del numero
        - Essendo sempre compresa fra 1 e 2, essa viene scritta senza riportare il primo 1. Quindi, anche se abbiamo 23 bit, possiamo codificare una mantissa fino a 24 bit
    - L'ESPONENTE
        - Questo è un numero con segno scritto in rappresentazione in eccesso 127, non 128.
        - Infatti, nonostante sia composto da 8 bit, alcuni dei suoi valori indicano cose differenti
        - In generale, essa può variare fra -126 <= x <= 127
        - Il valore -127 indica che si tratta di una forma non normalizzata. In questo caso, la decodifica del numero cambia. La mantissa viene letta come un numero in Fixed Point, con virgola a 127 posizioni precedenti.
        - Il valore 128 indica che il valore non è un numero. Potrebbero essere successe tre cose:
            - Se m != 0, il risultato non è un numero, e deriva da 0/0
            - ![](../../_resources/021eb8103daf4bf6a2bcebfda8f419b6.png)
            - ![](../../_resources/d05681d8e4c949a2b4777bc6c919d636.png)
    - Un esempio di numero non normalizzato è lo 0, il quale viene rappresentato come una sequenza di 32 zeri. Comodo.

Creato con OneNote.