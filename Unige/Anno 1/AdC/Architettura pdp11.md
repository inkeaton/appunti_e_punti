Architettura pdp11
mercoledì 24 novembre 2021
15:12

- La pdp11 è un'architettura a 16 bit creata dalla Digital Co. nel 1970, venduta fino alla fine degli anni ottanta.
- Per quanto sia oggi giorno obsoleta (lenta, consuma molto energia) essa viene ancora utilizzata a livello industriale e aerospaziale, per la sua affidabilità e resistenza alle interferenze elettromagnetici
- Essa è molto simile alla Von Neumann
- Per quanto sia a 16 bit, essa ha la particolarità di essere in grado di lavorare a soli 8 bit, come verrà spiegato più avanti

STRUTTURA GENERALE

- I dispositivi sono connessi tramite un insieme di cavi, chiamato BUS

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](6b6d3500ddd94cc4b9276429860ab3d3.png)

- Oltre a connettere i dispositivi, questa controlla velocità, clock, etc.
- Questa struttura permette di modificare il calcolatore, aggiungendo o togliendo dispositivi, senza dover modificare i dispositivi già presenti

STRUTTURA RAM

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](0483dc78e3b64acc9a7426430e2c8faa.png)

- La RAM contiene un massimo di 2^16 celle di memoria
- Ognuna di essa è da 16 bit, ma è suddivisa in due celle da 8 l'una.
- Questo permette al calcolatore di lavorare ad 8 bit: Per selezionare entrambe le celle, usa l'indirizzo pari della cella con i bit più significativi, per lavorare solo su 8 bit, i meno significativi, usa l'indirizzo dispari della seconda sezione.
- Inoltre, la RAM possiede una sezione dalla dimensione variabile, denominata STACK. Essa si forma nelle ultime celle della memoria, 2^16 in su.
- Il suo funzionamento ed utilizzo verrà spiegato meglio nelle istruzioni JUMP

STRUTTURA CPU

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](db474518a85d4d0d91178567075846ff.png)

    - La CPU contiene all'interno, oltre all'ALU, 9 registri.
        - I primi 8 sono chiamati da 0 a 7 R1, R2 etc. I primi 6 sono uguali e memorizzano valori. R7 è il PC, che ad ogni FETCH viene aumentato di 2.
        - Il nono è il registro di STATO, che memorizza informazioni secondarie
    - Le istruzioni vengono codificate su 16 bit, con un codice ad espansione, in due modi:

|     |     |     |     |
| --- | --- | --- | --- |
|     |     |     |     |
|     | ![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](6850f7b80cd641889eb8f62bd4ef4268.png) |     |     |
|     |     |     - Istruzione BINARIA |
|     |     |     |

|     |     |     |     |
| --- | --- | --- | --- |
|     |     |     |     |
|     | ![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](7955aa0eee0a4f94af5110519980bcf9.png) |     |     |
|     |     |     - Istruzione UNARIA |
|     |     |     |

- Le istruzioni quindi sono suddivise in:
    - OPCODE: L'istruzione che deve essere compiuta
    - SOURCE: Una degli operandi dell'Istruzione, che viene solo letto
    - DESTINATION: l'altro operando, il quale oltre ad essere letto, sarà la cella in cui verrà scritto il risultato

- Gli operandi sono a loro volta codificati nel seguente modo:

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](cda9571686024ef68c31fe6ff949d697.png)

![MODO: Indica il modo in cui l'operando viene passato. Esistono 4 modalità: REGISTRO (00): L'Operando è il contenuto del registro indicato nella sezione REGISTRO del SOURCE/DESTINATION. I registri indicati sono R0…R5 della CPU. AUTOINCREMENTO (01): l'Operando è il contenuto della cella di memoria RAM indicata dall'indirizzo presente in REGISTRO. Dopo l'operazione, il REGISTRO viene incrementato di 2, per lavorare alla cella seguente AUTODECREMENTO (10): Uguale al precedente, con la differenza che REGISTRO viene decrementato di 2, per lavorare alla cella precedente INDICIZZATO: L'Operando corrisponde al contenuto della cella di RAM indicata dall'indirizzo ottenuto dalla somma fra l'indirizzo contenuto nel REGISTRO, ed un valore costante, solitamente salvato nella cella di memoria seguente INDIREZIONE è un valore che, se ad 1, indica che ciò che normalmente sarebbe l'operando è in realtà l'indirizzo della cella in cui si trova l'operando REGISTRO: Contiene l'indirizzo di un registro, sia della CPU che della RAM ISTRUZIONI Le istruzioni codificabili in OPCODE sono numerose, ne vedremo alcune È interessante notare che per molte di queste istruzioni esiste un corrispettivo che funziona su 8 bit, scritto con una B alla fine (es, CLR -> 16 bit, CLRB -> 8 bit) PRINCIPALI CLR Clear Destination Assegna 0 ad un operando COM Complemento ad 1 Nega l'operando (rendendolo il suo opposto in complemento ad 1) INC Incremento Aumenta di 1 l'operando DEC Decremento Diminuisce di 1 l'operando NEG Complemento a 2 Nega l'operando (rendendolo il suo opposto in complemento a 2) TST Test Memorizza nel registro di STATO i risultati ausiliari della ALU SHIFT ASR Shift right Sposta i bit a destra (Divisione per potenze di 2) ASL Shift left Sposta i bit a sinistra (Moltiplicazione per potenze di 2) ROR Rotate right Ruota i bit verso destra ROL Rotate left Ruota i bit verso sinistra ADC Add carry Somma tenendo conto di un eventuale resto di un operazione precedente, potenzialmente salvato nel registro di STATO SWAB Swap byte Scambia i valori dei byte ad 8 bit di un byte a 16 bit SWAB in particolare è fondamentale per poter effettuare operazioni sugli 8 bit più significativi. Questi dovranno essere scambiati prima e dopo l'operazione che si vuole compiere su 8 bit BRANCH BR Branch Sostituisce PC con un altro valore BNE Branch not equal Sostituisce PC con un altro valore se nel registro di STATO l'operazione appena compiuta è diversa da 0](0ff14153a7d148338cc1752c367a5d7f.png)

![BE Branch equal Sostituisce PC con un altro valore se nel registro di STATO l'operazione appena compiuta è uguale a 0 BRL Sostituisce PC con un altro valore se nel registro di STATO l'operazione appena compiuta ha risultato positivo BMI Sostituisce PC con un altro valore se nel registro di STATO l'operazione appena compiuta ha risultato negativo BVC Branch overflow Sostituisce PC con un altro valore se nel registro di STATO è avvenuto dell'OVERFLOW BVS Sostituisce PC con un altro valore se nel registro di STATO non è avvenuto OVERFLOW BCC Branch riporto Sostituisce PC con un altro valore se nel registro di STATO c'è del riporto BCS Sostituisce PC con un altro valore se nel registro di STATO non c'è del riporto Queste istruzioni modificano PC sommando ad esso un determinato valore, chiamato OFFSET Per questo motivo, le istruzioni BRANCH sono codificate in un modo ulteriormente diverso: Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](7f1824d036f1430aae7c475f6933c341.png)

![Per questo motivo, le istruzioni BRANCH possono saltare solo a posizioni relativamente vicine alla cella originale JUMP JMP Jump Sostituisce PC con un altro valore JSR Jump to subroutine (PUSH) Sostituisce PC con un altro valore, salvando il precedente valore di PC nello STACK RTS Return from subroutine (POP) Sostituisce PC con un valore salvato nello STACK Le istruzioni JUMP funzionano in modo simile alle BRANCH, con la differenza di sostituire direttamente PC con un valore Esse sono codificate nel seguente modo: Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](7083540a02164a7891822289a9b26e30.png)

- Mentre il funzionamento di JMP è abbastanza esplicito, JSR e RTS sono un poco più complesse.
- Per spiegarle, introduciamo il concetto di STACK

- Questo è una sezione della memoria RAM, che si forma negli indirizzi più grandi della memoria, la cui dimensione è variabile.
- All'accensione della macchina, questa non esiste. Appena vogliamo scrivere qualcosa nello STACK, esso viene formato, a partire dalla cella 2^16 in su (Se abbiamo due celle si STACK, queste saranno 2^16 e 2^16 -2)
- Per scrivere nello Stack viene utilizzato il registro R6 della CPU, lo STACK POINTER (SP) il quale indica l'ultima cella dello STACK riempita
- SP viene gestito similmente a PC, con modalità di autoincremento e autodecremento, con la differenza che sono utilizzati in modo "invertito", dato che si va a ritroso nella RAM (Per scrivere si usa la modalità di autodecremento, per leggere la modalità di autoincremento)

- Dunque, JSR funziona nel modo seguente:
    - Individua un registro (Rn), e ne copia il contenuto nello STACK, tramite un operazione PUSH, nella cella indicata dal SP dopo che questo ha subito la procedura di autodecremento
    - Il registro Rn viene poi sovrascritto con il valore DESTINATION
- Spesso si utilizza questa operazione con Rn = R7, ottenendo un effetto simile a JMP
- La differenza è che il vecchio valore di R7 viene salvato e memorizzato nello STACK
- Questo viene poi utilizzato dall'istruzione RTS, nel seguente modo:
    - Individua il valore salvato nella cella indicata da SP, e con un operazione di POP, lo sovrascrive nel registro Rn
    - Dopo di che, SP viene autoincrementato, per indicare la nuova fine dello STACK

- Queste operazioni sono RIENTRANTI, ovvero possono essere applicate più volte di fila, senza problemi
- Inoltre queste permettono di implementare l'ESTENSIONE PROCEDURALE
    - Con questo si intende la creazione di FUNZIONI, ovvero programmi, che permettono di aumentare le capacità del dispositivo, salvandole in una determinata parte della RAM a cui "saltare" quando bisogna usarle.

- Si può anche utilizzare R7 sia come Rn che come DESTINATION, con autoincremento.
- In questo modo, potrei salvare l'indirizzo della funzione nella cella immediatamente successiva alla cella con JSR

- Quello che rimane da chiedersi è come passare i parametri ed i risultati fra il programma principale e la funzione che li utilizza.
- Basta salvare anch'essi nello STACK, attraverso l'istruzione MOV
- La funzione accederà poi a questi dati attraverso la modalità indicizzata, utilizzando SP e la distanza costante a cui si trova il dato richiesto
- (P.S, bisogna ricordarsi di lasciare uno spazio vuoto nello STACK per il risultato di una funzione)

- Questa struttura dati viene denominata LIFO

Creato con OneNote.