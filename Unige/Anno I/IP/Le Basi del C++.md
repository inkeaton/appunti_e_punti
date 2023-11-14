Le Basi del C++
mercoledì 29 settembre 2021
15:58

- Programmazione imperativa in C++
- Il programma più corto in C++:
- Int main()

{

}

- La struttura di un programma
- Int main() <-- int indica che il programma restituisce un int

{
Prima istruzione; <-- graffa dopo ogni istruzione
…
Ultima istruzione;

return 0; <-- indica che dopo aver fatto quello che doveva, il programma restituisce un valore

}

- Il programma vero e proprio va all'interno delle graffe
- Ogni programma contiene il blocco main principale
- Il linguaggio è suddiviso in
    - Regole di sintassi, che decretano quali istruzioni siano valide
    - Regole di semantica, che danno un significato alle istruzioni
- Elementi di un programma
    - Importanti sono i commenti, che esplicano parti del programma
    - Le indentazioni

- I programmi hanno il compito di elaborare dati. A basso livello, ogni dato è in codice binario
- Ad alto livello, si codificano espressioni specifiche per certe istruzioni, legate al linguaggio
- I dati si classificano in tipi:
    - Un tipo caratterizza un dominio di valori e lo spazio necessario per codificare questi valori (in bit)
- Esempi
    - Numeri Interi con e senza segno
    - Numeri razionali
    - Booleani
    - Caratteri
    - Puntatori (indirizzi di altri dati)
    - Stringhe
    - Tipi strutturati (array, stream, record..)

- Tipi di dati in C++
    - Semplici
        - Interi
        - Floating
    - Strutturati
    - Indirizzo
- Interi
    - Char, short, int, long ed i loro corrispettivi unsigned (senza segno)
        - Ognuno ha peso e dominio di valori diverso
    - Booleani (True or False), peso 1 byte
    - Esempi di int
        - -69420, 0, 78, +567
    - Esempi di char
        - Oltre ai numeri interi piccoli, char può rappresentare lettere singole, "t"
        - Si usano più gruppi, ASCII, EBCDIC. Noi useremo ASCII
        - Ogni valore rappresenta una carattere (non tutti stampabili). 65 = "A"
        - Caratteri non stampabili sono:
            - \n, newline
            - \t, tab
            - \0, null
- Floating
    - Sono usati per rappresentare numeri reali. Hanno una parte intera, ed una frazionaria
    - Esistono tre tipi float, double, long double (range e peso diverso)
- Operatori aritmetici
    - +, -, *, /. Si possono usare con ogni tipo
    - % (modulo o resto) si applica solo agli interi
        - 35%5 = 4 (35 diviso 5 ha come resto 4)
    - Le parentesi hanno priorità massima, seguite da * e /
- Espressioni
    - Le espressioni intere hanno operandi interi, ed i risultati sono numeri interi
    - Le espressioni a virgola mobile hanno tutti operandi a v. mobile, e risultato
    - Le espressioni miste hanno come risultato a virgola mobile

Esercizi

- 2+3*5
- 12.8*17.1-30.0
- 6/(4+3)
- 4*3 +

Creato con OneNote.