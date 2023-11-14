Macchina di Von Neumann
venerdì 19 novembre 2021
14:49

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](e390b0e3955b4fb7931da1bc303fa308.png)

- Questa struttura è la prima architettura moderna di un calcolatore
- La struttura funziona come un unico circuito sequenziale sincrono
- La differenza principale con i colleghi precedenti è l'utilizzo di un unico supporto di memoria (la RAM) per contenere sia DATI che ISTRUZIONI
- Inoltre, essa è in grado di eseguire PROGRAMMI SEQUENZIALI, ovvero dare la possibilità di inserire istruzioni in modo ordinato, tramite gli indici delle celle della RAM

- All'Interno della C.U. si trovano due registri, il PROGRAM COUNTER e l'INSTRUCTION REGISTER
- Essi verranno utilizzati nell'esecuzione di un programma

ESECUZIONE DI UN PROGRAMMA
1. RESET - PC viene portato a 0

2. FETCH - Leggo la prima istruzione, usando il PC come indirizzo. Riporto il dato in esso memorizzato in IR. Contemporaneamente, PC viene aumentato di 1, tutto in un singolo scatto del CLOCK

3. DECODE - l'istruzione in IR viene decodificata

4. EXECUTE - l'istruzione viene eseguita. Dopo di che si ritorna alla fase di FETCH

- In questo modo, vengono eseguite in sequenza le istruzioni contenute nella RAM
- Ma questo ordine può essere modificato tramite le ISTRUZIONI DI SALTO, istruzioni che modificano PC, permettendo quindi di "saltare" a determinate istruzioni
- Questo permette di implementare sistemi di controllo, o cicli utilizzando poche celle di memoria
- Si potrebbero anche implementare valori di PC che vengono calcolati dalla macchina stessa, in base all'input. Queste vengono definite ISTRUZIONI AUTOMODIFICANTI

- Questa macchina è capace di fare tutti i calcoli di cui abbiamo bisogno, ma le istruzioni vanno codificate in modo molto complesso, cosa che rende facile il commettere errori.
- Del resto, è questo il motivo per cui esistono i linguaggi di programmazione di alto livello, codici che vengono poi codificati nelle istruzioni a più basso livello dai COMPILER  e LINKER

Creato con OneNote.