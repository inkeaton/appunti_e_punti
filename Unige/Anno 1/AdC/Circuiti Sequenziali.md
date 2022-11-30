Circuiti Sequenziali
sabato 6 novembre 2021
11:09

![Un dispositivo la cui uscita non dipende solo dagli ingressi attuali, ma anche dalle uscite precedenti Il più semplice costruibile è il seguente Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](201c6e52916649d0ad48c783098c54f8.png)

    - Si notano all'interno dei cicli chiusi
    - Attraverso essi, possiamo usare questi circuiti per memorizzare dati al loro interno
    - La tavola di verità è la seguente

|     |     |     |
| --- | --- | --- |
| S   | R   | Q   |
|     |     |     |
| o   | 0   | Q*  |
| o   | 1   | 0   |
| 1   | 0   | 1   |
| 1   | 1   | null |

    - Particolarmente interessante è il caso 0,0.
    - Osservando il circuito, si noterà che il valore dei NOR dipende dal valore precedente di Q. Dato il ritardo nella ricezione dei nuovi valori 0 e 0, l'uscita manterrà il valore di Q precedente, Q*.
    - In tal modo, immettendo 0,0, memorizziamo il valore Q* precedente nel circuito
    - ES.

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](74279a9fd53040afa9f57650140a0038.png)

    - ![](../../_resources/ef358ef44a61448995ee57ead7136fee.png)
    - Questo dispositivo viene chiamato FLIP-FLOP tipo SET RESET
    - Viene rappresentato come

|     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- |
|     |     |     |     |     |     |
|     | ![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](74458f15dd164b579082d6789fb5dced.png) |     |     |     |     |
|     |     |     |     |     - Vietata (1,1)<br>    - (0,0) Memorizza la configurazione<br>immediatamente precedente |
|     |     | ![](1585dd8d2fe34bc990d5a4d70f99052e.png) |     |
|     |     |     |     |
|     |     |     |     |     |

    - Questo circuito può essere migliorato, allo scopo di evitare il problema della combinazione (1, 1), aggiungendo un segmento iniziale

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](f7f5cb3f500c45a0a9463577045c0e3e.png)

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](3776a4fc6db0484f92904c81f5f44c38.png)

- STROBE controlla il circuito. Quando è 0, S ed R diventano 0, memorizzando Q*. Quando è 1, il circuito funziona normalmente, con l'impossibilità di un ingresso 1,1.
- Questo dispositivo viene chiamato FLIP FLOP tipo D
- Riproduce in uscita il valore D, oppure lo memorizza

- Per poter memorizzare D in un preciso attimo di tempo, si costruisce un dispositivo, il cui principio ricorda quello dell'otturatore della macchina fotografica, il MASTER SLAVE

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](54ab28751ab04c69a4b09da46b1cdb53.png)

- Il funzionamento è il seguente:
    - Se CLOCK è a 0, il MASTER memorizza il valore precedente. Anche se D varia, l'uscita del MASTER non varia.
    - Per via della negazione, lo SLAVE è in modalità di calcolo, quindi Q avrà valore 1 o 0, a seconda del valore memorizzato in MASTER
    - Appena CLOCK varia in 1, il MASTER riproduce in uscita il valore di D. SLAVE memorizza il valore precedente di Q, Q*, che non varierà nel tempo.
    - Per far variare di nuovo Q, basterà variare di nuovo CLOCK.
- In questo modo, il valore Q memorizzato corrisponde esattamente a quello di D al momento in cui CLOCK varia da 1 a 0

- I circuiti sequenziali sono suddivisi in:
    - Asincroni
    - Sincroni (Con CLOCK)

- Il simbolo dei circuiti MASTER-SLAVE è

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Il triangolino vuol dire che è EDGE-TRIGGERED, l'uscita varia solo alla variazione 1→ 0 del CLOCK I circuiti Sincroni ci permettono di ovviare a molti problemi dei circuiti asincroni, dovuti al ritardo del calcolo dei dispositivi. Ad esempio, un multiplexer potrebbe produrre, per alcuni istanti dopo aver cambiato ingresso, una non voluta configurazione (0, 0) non voluta, memorizzando, in un f-f asincrono, un dato quando non voluto Questo problema viene chiamato ALEA DI COMMUTAZIONE Tramite i circuiti sincroni, questo problema viene risolto, dato che l'uscita varia solo quando voluto. Basterà aspettare un determinato tempo, sufficiente per avere i dati corretti. ALTRI CIRCUITI SINCRONI F-F TIPO T Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](fc7678c474f24a03838f66cba6cf6637.png)

|     |     |     |
| --- | --- | --- |
| T   | CK  | Q   |
|     |     |     |
| o   | ![](d71ff2c53adc4bc9830d4a5feea9611e.png) | Q*  |
| 1   | ![](d71ff2c53adc4bc9830d4a5feea9611e.png) | ![](b81a520e720d45f59a9afa372d986b90.png) |

|     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- |
|     |     |     |     |     |     |     |     |
|     |     |     - F-F TIPO JK |     |     |     |     |     |
|     |     |     |     | ![Disegni a penna Disegni a penna](683076fc89d243e7b7436f642084c0cd.png) |     |
|     |     |     |     |     |     |
|     | ![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](f89207b05bff43b688710081055f52c3.png) |     |     |
|     |     |     |     |     |
|     |     |     | ![Disegni a penna Disegni a penna Disegni a penna](43d80dec93ee41f6b8e59e6fcb9f0e31.png) |
|     |     |     |     |     |

|     |     |     |
| --- | --- | --- |
| J   | K   | Q   |
|     |     |     |
| o   | 0   | Q*  |
| o   | 1   | 0   |
| 1   | 0   | 1   |
| 1   | 1   | ![](b81a520e720d45f59a9afa372d986b90.png) |

    - Si può notare che questo dispositivo svolge le stesse mansioni di un F-F tipo set reset, con l'eccezione di poter usare l'ingresso 1,1

    - Questi dispositivi possono essere usati insieme ai circuiti combinatori, in modo da evitare possibili alee. I principi di costruzione sono i seguenti:
        - Costruire dispositivi combinatori con il minor ritardo possibile.
        - Regolare la frequenza di variazione di CLOCK in modo che sia coordinata con il ritardo del circuito combinatorio che lo precede, così da evitare alee

Creato con OneNote.