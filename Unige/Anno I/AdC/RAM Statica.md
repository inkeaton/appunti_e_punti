RAM Statica
mercoledì 17 novembre 2021
15:17

- Un insieme di registri di tipo D
- Questi vengono messi insieme e fatti lavorare uno alla volta
- Ognuno di essi è etichettato con un numero, il suo indirizzo.
- Per ciò, la RAM può essere immaginata come un vettore, il cui indice è l'indirizzo della cella di memoria

- Su queste celle effettuiamo due operazioni principali: READ and WRITE
- Per scrivere, dobbiamo collegare la RAM al dispositivo di INPUT.
- Inoltre ci serve l'indirizzo della cella di memoria in cui scriviamo. L'indirizzo viene scritto in codice binario, quindi, per ottimizzare spazio, viene scelto un numero di celle 2^n
- Naturalmente, bisognerà anche definire il numero di bit memorizzabili da ogni registro

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](15e7734c9ca54af4b22aca954cb72f1e.png)

- Il controllo è codificato su due bit. Il primo è il CHIPS e NET (C/S) e determina se fare qualcosa o no. Se C/S = 1, controlla il secondo bit R/nW che se è 0 scrive, se è 1 legge
- Per leggere, ci servirà l'indirizzo in cui leggere ed il dato da passare. Per scrivere, ci servirà l'indirizzo in cui scrivere, ed il dato da scrivere. In tutti i casi, serve il controllo per determinare cosa fare.

- Si può notare però, che il numero di cavi da utilizzare sarebbe velocemente alto.
- ES.
    - Usiamo un processore a 64 bit con 16 GiB di RAM
    - Serviranno 64 cavi per i file da scrivere, 64 cavi per i file da leggere.
    - Ogni cella conterrà 8 byte = 64 bit d'informazione. Ci saranno quindi 2^31 celle, e serviranno 31 cavi per gli indirizzi, più i due del controllo
    - Quindi in totale, 161 cavi!
- Un modo per ridurre il numero di fili è aumentare il numero di indirizzi
- ES.
    - Usando un organizzazione a 32 bit, useremmo 32 + 32 + 32 + 2 = 98 fili
    - Con una ad 8 bit, 52

- Come fare la lettura? Usiamo un MPX, che sceglie una delle celle da connettere all'uscita
- Con 2^k ingressi ed una uscita, avrà come segnale di controllo gli indirizzi di indirizzamento
- Similmente, per la scrittura, la cella in cui scrivere viene determinata tramite un decoder o Demultiplexer a 2^k uscite, con i fili d'indirizzamento come controller

ARCHITETTURA DI VON NEUMANN

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](fe363c8e33a941baa524001beb9852fd.png)

- Riceve informazioni in INPUT, per poi elaborarle nella CPU, e stamparle in OUTPUT. Inoltre, può memorizzare queste stesse informazioni nella RAM
- La RAM interagisce con la CPU in modo scelti dal processore, in un rapporto MASTER/SLAVE
- La CPU da gli ordini tramite i fili d'indirizzamento e di controllo

- Per risparmiare, potremmo pensare di utilizzare un solo set di fili per comunicare informazioni in scrittura ed in lettura. Ma abbiamo il problema di dover gestire un flusso in direzioni diverse
- Per gestirlo introduciamo i dispositivi TRISTATE o a TRE STATI

![](45a5a3cd1c5f4b9ba80a34c94586613c.png)

![Disegni a penna Disegni a penna Disegni a penna](0e4444b2a5724b2189503db7e383fca8.png)

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna](b416477625b04375896021857ade6757.png)

|     |     |
| --- | --- |
| C   | U   |
| 0   | Non Collegato |
| ![](0b606b7415ab4da389ee1c81c748fd5e.png) | I   |

![](3804b91cf3004254a8939d9b92e82bff.png)

- Questo ci permette di "staccare" la CPU o la RAM quando necessario, per permettere all'altra di usufruire dei cavi
- Vengono messi due di questi dispositivi dall'uscita della RAM e della CPU. Questi vengono controllati tramite il bit R/nW del controllo, collegato ad entrambi. Infatti, quando è 1, la RAM è in lettura, e deve usare il cavo. Quindi la RAM si collega, e la CPU si scollega. Quando è 0, la RAM è in scrittura, quindi si scollega la RAM e si attacca la CPU

- L'unico problema che rimane è la dispendiosità di questi circuiti. Servono all'incirca 50 dispositivi NOR per realizzare un bit di memoria.
- CI serve un sistema che ne utilizza meno. Oltre al prezzo, più dispositivi si adoperano, maggiore è la possibilità di errori

RAM DINAMICHE

- Questo nuovo sistema viene implementato, poiché utilizza un solo dispositivo per bit di memoria
- Il problema insorge nel fatto che è in grado di memorizzare solo per brevissimo tempo.
- Per ovviare a tale problema si attua regolarmente la procedura di REFRESH: ogni singolo bit viene letto e ricopiato uguale, per "resettare" il timer
- Questo però influisce la velocità di calcolo. Infatti, il circuito non può leggere o scrivere mentre è in corso la procedura di REFRESH, ed essa è improrogabile

MEMORIA ASSOCIATIVA

- È un sistema ben più complesso della RAM, costruito in modo tale da velocizzare e standardizzare la velocità della ricerca
- Una singola cella di memoria ha la seguente struttura:

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](d4fe4eaedb8d4aacaf6a699f201fb11d.png)

- Essa è quindi formata da:
    - Due registri di tipo D, chiamati DATA (Che contiene l'informazione contenuta nella cella) e TAG. Quest'ultimo funge da "etichetta" per la cella. Inoltre, il primo bit di TAG indica se è piena o vuota (Servirà sempre un numero di bit per il TAG di almeno uno superiore al numero di celle)
    - Un CIRCUITO COMPARATORE

- La ricerca funziona nel seguente modo:
    - Ogni volta, la CPU invierà una copia del TAG, il "tipo" di dato che stiamo cercando.
    - Simultaneamente l'uno con l'altro, ogni circuito comparatore controllerà che il TAG della cella a cui è associato corrisponda a quello richiesto.
- In questo modo, la ricerca avviene molto più velocemente, non essendo sequenziale come nella RAM
- Per scrivere in questa memoria, bisognerà assegnare sia TAG che DATA, oltre che segnare nel primo bit del TAG che la cella è ora piena

- È un tipo di memoria STATICO

CONFRONTO CON RAM STATICA

- A parità di bit a disposizione, essa potrà contenere meno informazioni, dato che parte dei registri dovrà contenere i TAG
- Però, abbiamo la possibilità di scegliere le dimensioni dei TAG, mentre il numero di indirizzi della RAM sarà sempre uguale al numero di celle

Creato con OneNote.