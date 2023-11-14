Formule
venerdì 12 novembre 2021
15:31

- Anche le formule del primo ordine vengono costruite tramite albero sintattico
- La Radice è la formula considerata
- ![](58204a99998b4a919e0416a9a0966736.png)
    - ![](f3ef3a5faa814019a8a841f14b8fdece.png)
    - ![](138aaee3035e437281e5ed152498b1fd.png)
    - ![](166791afe4f44210a3acc9c27767f8b8.png)

- Per rendere le formule più leggibili, si rimuovono le parentesi non necessarie. I connettivi seguiranno la gerarchia:
    - ![](084b618c635c4fa3b5b04627a8c3aa61.png)
    - ![](fd91a083ae5c4e9d93aa2596835b2e01.png)
    - ![](131b832e8dcf403c90236bd9343b6290.png)
    - ![](47f270bc94044a85b3c8cef7ea2e1420.png)
- Inoltre, i simboli funzionali binari verranno messi in mezzo ai loro argomenti

- Ogni volta che una variabile compare in una formula, quella viene detta un OCCORRENZA.
- Ma queste occorrenze sono diverse fra loro. Osserviamo l'esempio
- ES.
    - ![](0257ac0cbe914dde8cea259ec0a55716.png)
    - Le prime due z sono variabili VINCOLATE. Potrebbero aver qualunque simbolo, e la formula non cambierebbe. Invece, la terza z è LIBERA. Il suo valore è fondamentale per l'interpretazione della formula, e deve essere deciso

- In generale, un occorrenza è VINCOLATA se si trova nell'argomento di una quantificazione (Compresa l'occorrenza immediatamente dopo il quantificatore)
- ![](f2b62a3a65764589a018c34fa46ff181.png)
- ![](7cac220b93d44429b675360e5e19cfd2.png)
- ![](57e7c92b642b4b0aa97dd21c67996d82.png)

- ![](821770faedd945ad80471fc733f231fa.png)
    - Se x è il simbolo subito dopo il quantificatore, è vincolata
    - Se no, è in una sotto formula. Si risale l'albero, fino a trovare un istanza del quantificatore. In tal caos è vincolata. Se non si trovano quantificatori, è libera.

- Una formula dice qualcosa sulle variabili libere, e dipende dal loro valore.
- Una formula senza variabili libere dipende solo dal conteso

Creato con OneNote.