Utilizzo Stack e Interruzioni
mercoledì 1 dicembre 2021
15:14

- Abbiamo quindi visto che lo stack viene usato per:
    - "saltare" da un istruzione ad un'altra, con possibilità di ritorno
    - Passare valori fra il programma e le sue subroutines
- Un ulteriore utilizzo è memorizzare variabili LOCALI o AUTOMATICHE, ovvero variabili create da una subroutine, le quali vengono poi cancellate al ritorno dalle subroutine

INPUT ed OUTPUT

- Questi vengono collegati alla CPU allo stesso modo della RAM, allo scopo di standardizzare i collegamenti
- Per via di ciò, questi vengono strutturati in un modo simile alla RAM stessa, contenendo registri tipo D, chiamati REGISTRI MAPPATI IN MEMORIA
- Questi vengono indicati da indirizzi, gli stessi della RAM. Per tale motivo, la RAM non è mai composta da 2^16 celle, ma sempre da meno. Questo per poter lasciare qualche indirizzo per INPUT ed OUTPUT

- L'iterazione fra programma e utilizzatore viene limitata: Se il programma non prevede l'utilizzo della tastiera o altri dispositivi d'input, l'utilizzatore non avrà in alcun modo controllo sul programma, non potendolo fermare od altro.
- Per questo vengono implementate le INTERRUZIONI

MECCANISMO INTERRUPT

- Diviso in più fasi:

1. SEGNALAZIONE

    - Viene aggiunto al BUS un filo d'interruzione, un circuito collegato ad ogni dispositivo, che trasmette 1 alla CPU quando uno dei dispositivi segnala un interruzione

2. RISPOSTA

    - Viene aggiunta un ulteriore fase al ciclo di esecuzione di un istruzione, appena prima del FETCH, che controlla se viene segnalata un'interruzione
    - In caso positivo, il PC viene sostituito con un indirizzo HANDLER, che indica il programma che gestirà l'interruzione
    - Per evitare che il programma venga interrotto ancora una volta, prima che l'interruzione stessa venga gestita, si collega con un AND al filo d'interruzione un bit del registro di STATO, il bit di MASCHERA, il quale diventa 0 quando il programma sta gestendo l'interruzione
    - Si possono utilizzare insieme più bit di maschera per implementare un sistema di priorità di interruzioni, in modo che interruzioni che non possono aspettare vengono gestite prima di altre, con HANDLER diversi

3. GESTIONE

    - Il programma in HANDLER agisce sull'interruzione. Questo verrà poi definito dall' OS più avanti

Creato con OneNote.