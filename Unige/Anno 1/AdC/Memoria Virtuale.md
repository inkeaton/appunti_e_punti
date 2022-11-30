Memoria Virtuale
domenica 5 dicembre 2021
15:43

- Allo scopo di organizzare in modo più efficiente l'utilizzo della memoria, la RAM viene suddivisa in più sezioni, come lo STACK, attraverso il metodo della SEGMENTAZIONE.
- In particolare, in un sistema POSIX, esistono quattro principali sezioni:
    - CODICE: Contiene istruzioni
    - DATI STATICI: Contiene variabili globali e costanti
    - STACK: già spiegato in precedenza
    - HEAP: esso è un'altra sezione dinamica della memoria, similmente allo stack. La differenza sta nel fatto che esso viene gestito dal programmatore, sia nel creare che liberare spazio di memoria
- Ora che abbiamo queste diverse sezioni, dobbiamo trovare un modo per poter indirizzare la CPU solamente nelle sezioni di memoria ad essa utili (Es, durante la fase di FETCH, dovrà controllare solo la sezione CODICE)
- Per questo motivo introduciamo un nuovo dispositivo, la MMU (Memory Management Unit), situata fra CPU e BUS, la quale tradurrà gli indirizzi normali della RAM con degli indirizzi specifici alla sezione in cui la cella è situata
- Questi ultimi vengono chiamati INDIRIZZI VIRTUALI

- Essi si possono implementare in due modi:

1. Implicito
2. Esplicito

- I nostri indirizzi virtuali saranno formati da due sezioni:
    - Una da 2 bit che indica il numero della sezione in cui cercare
    - Una da, nel caso del pdp11, 16 bit, che indica l'indirizzo virtuale della cella di memoria
- L'indirizzo virtuale deve essere tradotto nell'indirizzo fisico. Questo deve essere fatto conoscendo la cella d'inizio della sezione e, la DIMENSIONE della sezione o la cella di fine.
- Questi dati verranno memorizzati in un registro dentro la MMU

- Quando inizia una traduzione, la MMU controllerà prima se l'indirizzo si trova OUT OF BOUNDS, utilizzando o la dimensione o l'indirizzo dell'ultima cella, e se il riscontro è negativo, calcolerà l'indirizzo fisico della cella sommando la prima cella della sezione all'indirizzo virtuale.

- La MMU conterrà quindi un circuito COMPARATORE ed uno SOMMATORE
- Inoltre essa contiene un sistema simile a quello delle interruzioni denominato TRAP. A differenza delle prima, i segnali di TRAP hanno priorità assoluta, e bloccano definitivamente lo svolgimento del programma
- Questo perché, al contrario delle interruzioni, un segnale di TRAP ha provenienza interna, ed indica quindi per forza un errore nella scrittura del programma, irrisolvibile.

- Nel caso la TRAP sia avviata su di un segmento dinamico (STACK o HEAP), il gestore delle interruzioni provvede ad incrementare la dimensione del segmento, modificando Ind. Min., Dimensione, e (nel caso dello STACK) SP.
- Questo ovviamente finché c'è spazio fra il segmento e quello ad esso adiacente. In tal caso, il gestore segnala errore.
- Il problema però è che potrebbe esserci ancora dello spazio libero nella RAM fra altri segmenti.
- Questo fenomeno viene chiamato FRAMMENTAZIONE
- L'unica soluzione sta nello spostare i segmenti, spostando anche i valori in essi contenuti (RILOCAZIONE)
- La RILOCAZIONE viene eseguita dalla CPU, ed è un processo che, a seconda della dimensione della RAM, prende molto tempo
- Per questo, essa viene eseguita in tandem con un ulteriore processo

- Un altro metodo utilizzabile è quello della PAGINAZIONE
- Il vantaggio di questo metodo è il poter sempre avere un indirizzo desiderato alla pagina, indipendentemente dalla sua posizione, così evitando la frammentazione della segmentazione
- Questa funziona in modo simile alla segmentazione. La RAM viene suddivisa in molte parti, di grandezza uniforme e predefinita, chiamate PAGINE. La dimensione di ognuna dev'essere 2^n
- L'Indirizzo virtuale sarà composto da due parti:
    - PAGE #: Indica il numero di pagina
    - OFFSET: Indica la distanza fra l'indirizzo iniziale della pagina e l'indirizzo indicato
- Per tradurre l'indirizzo nel corrispondente indirizzo fisico, OFFSET viene copiato (Passando attraverso Id(x)), mentre PAGE # deve essere sostituito con l'indirizzo iniziale della pagina indicata.
- L'indirizzo finale verrà dato dalla somma di OFFSET e dell'indirizzo della prima cella della pagina

- Per effettuare la traduzione, l'MMU deve naturalmente sapere la cella iniziale corrispondente a quella pagina. Queste informazioni vengono salvate nella TABELLA DELLE PAGINE.
- Questa tabella avrà 2^n righe, con n il numero di bit del PAGE #.
- Si può notare che questa tabella può diventare molto, molto grande. Per questo verrà memorizzata nella RAM.
- Naturalmente però, la tabella non deve essere troppo grande, se no perderemmo spazio nella RAM (occupandolo con la tabella)
- Una soluzione è aumentare la dimensione delle pagine, ottenendo una tabella più corta. Questo però può causare una forma di frammentazione: infatti, se inseriamo in una pagina un programma di dimensioni minori, perdiamo lo spazio non occupato della pagina.
- Bisogna quindi trovare l'equilibrio fra grande e piccolo.

- Un problema si ritrova adesso nell'MMU. Essa infatti deve ogni volta controllare prima la tabella nella RAM, e poi la cella indicata. In questo modo, per eseguire una lettura, ne dobbiamo eseguire 2, duplicando il tempo necessario
- Per questo implementiamo un nuovo dispositivo, la TRANSLATION LOOKASIDE BUFFER (TLB).
- Questa è una MEMORIA ASSOCIATIVA
- Ogni volta che l'MMU esegue il FETCH, controlla prima la TLB. Nel caso non ci sia niente, esegue come al solito. Quando ha finito l'istruzione, salva nella TLB l'indirizzo fisico della PAGINA, mettendo nel TAG l'indirizzo virtuale PAGE #.
- Al secondo FETCH, è molto probabile che l'istruzione si trovi nella stessa pagina. Quindi, l'MMU controlla se nella TLB è salvato l'indirizzo richiesto, ed utilizza quello per trovare la cella richiesta
- In questo modo, l'MMU leggerà la tabella delle pagine solo quando dovrà cambiare pagina

- Ora, la soluzione finale è combinare queste due tecniche

- SEGM + PAG
- Gli indirizzi avranno tre campi:
    - N° SEGMENTO: indica il segmento in cui siamo
    - PAGE #: Indica il numero di pagina dentro al segmento (quindi relativo al segmento)
    - OFFSET: (come prima)
- La traduzione avverrà su due livelli:
    - Prima, l'MMU controllerà la tabella dei segmenti, la quale conterrà l'informazione della posizione della tabella delle pagine dei quel segmento
    - Esisterà una tabella delle pagine per segmento, che conterrà l'indirizzo fisico della pagina
    - Nel caso PAGE # sia troppo grande rispetto al n° di pagine all'interno del segmento, verrà segnalata una TRAP
    - La TLB funzionerà allo stesso modo, con la differenza di contenere oltre al PAGE # il N° SEGMENTO nel TAG

- Potremo inoltre inserire altre informazioni all'interno della tabella dei segmenti, come ad esempio delle "proprietà" dei segmenti stessi. Per esempio, potremmo segnare il segmento CODICE come eseguibile, ma non riscrivibile o leggibile. Nel caso una di queste due espressioni venga eseguita verrà segnalata una TRAP.

ISTRUZIONI PRIVILEGIATE

- Nel registro di STATO è presente un bit (o più di uno) detto bit di STATO che individua due modalità in cui il processore può lavorare
- Queste sono la modalità USER (0) e la modalità SYSTEM (1)
- La differenza fra le due è che nella seconda il sistema può eseguire istruzioni dette PRIVILEGIATE, le quali sono riservate a programmi affidabili, in particolare il SISTEMA OPERATIVO
- Nel caso un programma utente cerchi di eseguire istruzioni privilegiate, quando non gli è permesso, verrà segnalata una TRAP

- Un esempio è l'accensione del dispositivo.
- All'inizio la RAM è vuota, e con essa le tabelle dei segmenti e di paginazione ed il gestore delle TRAP/INTERRUPT
- Per consentire il funzionamento della memoria virtuale è necessario caricare questi dati. Il processore li reperisce utilizzando delle istruzioni privilegiate che gli permettono di lavorare utilizzando gli INDIRIZZI FISICI
- Alla fine di questa fase, detta BOOTSTRAP, il sistema passa in modalità USER, funzionando regolarmente

- Quindi in generale, la modalità SYSTEM è riservata ad istruzioni dell'OS, essendo esso un programma affidabile (non dovrebbe contenere errori)

Creato con OneNote.