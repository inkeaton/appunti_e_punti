Elementi di un sistema di calcolo
martedì 5 ottobre 2021
10:58

- Questo modello è stato ideato da John Von Neumann negli anni 40, nella cosiddetta macchina di Neumann, e viene seguito dalla maggior parte dei computer moderni
- Esso è strutturato nel seguente modo:

- ![Control Unit (CUI)  Instruction Register (IR)  Program Counter (PC)  Arithmetic Logic Unit (ALO)  Memoria principale (RAM)  Memoria Secondaria  Central  Processing  Unit  CPU  Disp. input  Disp. Output](4ca18ac59a6e4645a9434fea3210ab37.png)

RAM

- Random Access Memory, memoria ad accesso arbitrario mediante indirizzo
- Memorizza dati temporanei, attraverso la memorizzazione di un vettore di numeri interi
- È da immaginarsi come un numero predeterminato di celle, ognuna denominata da un indirizzo, capaci di immagazzinare dati e codici in linguaggio base
- I dati potrebbero essere input o valori intermedi dei calcoli

CPU

- La Control Unit (CU) realizza il funzionamento interno della macchina, effettuando i calcoli
- Essa contiene tre registri
    - L'Accumulatore (ACC) e l'Instruction Register (IR) che immagazzinano dati interni
    - Il Program Counter (PC) che immagazzina gli indirizzi delle celle della RAM

Esecuzione di un PROGRAMMA

- Un programma ha il seguente ciclo di vita:

- ![editor  compilatore  libreria  linker  loader  ececuzone](Compilazione%20di%20un%20file.png)

EDITOR

- Dopo aver ideato l'algoritmo di un programma, questo viene scritto in codice di alto livello, nel caso di questo corso, C++
- Questo viene scritto in programmi, chiamati editor, i quali salvano il programma in un file di testo, dall'apposita estensione (nel caso del C++, .cpp)

COMPILATORE

- Allo scopo di essere eseguiti, questi programmi hanno bisogno di essere tradotti in linguaggi di livello inferiore
- Qui interviene il compilatore, il quale dopo aver controllato che il codice sia corretto, lo traduce in codice oggetto

LINKER

- In seguito il linker unisce il codice sorgente del programma ad altri pezzi di codice pre-compilato. In questo modo, il programmatore può evitare di riscrivere ogni volta parti di codice fondamentali

LOADER

- Esso carica nella RAM il programma tradotto in codice eseguibile

ESECUZIONE

- Il programma viene eseguito dalla CPU

Creato con OneNote.