  L'Algebra Binaria
venerdì 22 ottobre 2021
15:45

- Usando AND, OR e NOT, possiamo creare un sistema dalle proprietà simili a quelle algebriche
- Proprietà dell'algebra binaria:

    1. A + 0 = A

        - Il + rappresenta OR

    2. A * 1 = A

        - Il * rappresenta AND

    3. A + 1 = 1
    4. A * 0 = 0
    5. A + B = B + A
    6. A * B = B * A
    7. (A+B) + C = A + (B + C)
    8. (A*B)*C = A*(B*C)
    9. A*(B+C) = A*B + A*C
    10. ![](43539610c2a84675b9c37455da8beef4.png)
    11. ![](ba3829f382a945f18330ff3d1a68320a.png)
    12. A + A = A
    13. A * A = A
    14. ![](d50421c346fc4ccfb5270b3faf793fe6.png)

- Queste convenzioni vengono utilizzate nella Rappresentazione Disgiuntiva, un metodo alternativo alle tavole di verità utilizzato per rappresentare le proposizioni
- Tramite essa, queste vengono mostrate come:
    - ![](5d45596d0f814e0981dc486c0a353808.png)
    - ![](7dc4735edab84df4b783917212af4fa8.png)
- ES.
    - Rappresentiamo la funzione XOR con la somma di prodotti

|     |     |     |
| --- | --- | --- |
| A   | B   | XOR |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 0   | 0   |

- Per ogni riga, osservare il valore specificato per l'uscita: se é

0, allora passare alla riga seguente senza far nulla; se invece
il valore specificato é 1, allora scrivere un termine da
aggiungere ai termini già scritti in precedenza composto dal
prodotto di tutte le variabili di ingresso che assumono il
valore 1 e della negazione di tutte le variabili di ingresso che
assumono il valore 0.

- Dunque
    - ![](61f8bcf13d034ec2b60ad8312d136b9c.png)
- Queste forme non sono minimali, ma possono essere ridotte ancora usando proprietà dell'Algebra Binaria
- Nella rappresentazione come Prodotto di Somma si lavora similmente, ma osservando le righe con valore 0
- Un altro metodo, molto interessante, sono le mappe di Karnaugh, tabelle bidimensionali

|     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- |
|     |     | C   | 0   | 0   | 1   | 1   |
|     |     | D   | 0   | 1   | 1   | 0   |
| A   | B   |     |     |     |     |     |
| 0   | 0   |     |     |     |     |     |
| 0   | 1   |     |     |     |     |     |
| 1   | 1   |     |     |     |     |     |
| 1   | 0   |     |     |     |     |     |

- In queste tabelle, si utilizza l'ordine del Codice Gray, in cui 11 viene prima di 10. Questo per ottenere una D.H di 1 fra ogni possibile coppia
- Proviamo a tradurre una di queste mappe in una formula normale disgiuntiva
- ES.

|     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- |
|     |     | C   | 0   | 0   | 1   | 1   |
|     |     | D   | 0   | 1   | 1   | 0   |
| A   | B   |     |     |     |     |     |
| 0   | 0   |     | 1   | 0   | 0   | 1   |
| 0   | 1   |     | 1   | 1   | 1   | 0   |
| 1   | 1   |     | 1   | 0   | 0   | 0   |
| 1   | 0   |     | 1   | 0   | 0   | 1   |

- Controlliamo le caselle con 1. Vediamo se ci sono gruppi di caselle adiacenti di valore potenza di 2
- Per esempio, la prima colonna è formata da 4 = 2^2 1
- Possiamo creare una formula ben più minimale per essa, rispetto a con le tavole di verità
- ![](49f877c01f1f45f680dbf95327973c1c.png)
- Questa rappresentazione è infinitamente più corta di quella derivante dalle tavole di verità
- Anche le caselle in alto ed in basso a destra possono essere considerate adiacenti, avendo D.H. = 1
- ![](7905dcfbc60f49399326934f80432208.png)
- Inoltre, anche la prima e l'ultima colonna sono vicine, formando coppie nella prima ed ultima riga
- Inoltre, sono da considerare anche la coppia nella seconda riga
- Il risultato finale è:
    - ![](0165520ce5f34362bca9201c5b0367e1.png)

- Si può tradurre in un circuito con rappresentazione ordinata, divisibile in tre parti (i NOT, i AND ed i OR)
- Viene detta rappresentazione a 3 livelli. Essa ha il vantaggio che, al variare dei valori d'entrata, il possibile ritardo massimo del valore d'uscita è per forza 3 volte quello di una singola funzione. Inoltre è un applicazione maggiormente vicina alla realtà pratica.

Creato con OneNote.