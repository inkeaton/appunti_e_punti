Circuiti Numerici
lunedì 1 novembre 2021
11:46

- Implementiamo la somma a livello hardware
- Ci servirà un dispositivo a due vie ed una uscita.
- Proviamo a crearlo con ingressi ad 1 bit

|     |     |     |     |
| --- | --- | --- | --- |
|     | B   | 0   | 1   |
| A   |     |     |     |
| 0   |     | 00  | 01  |
| 1   |     | 01  | 10  |

- U0 = A XOR B (1 nella seconda cifra)
- U1 = A AND B (1 nella prima cifra)

- Quindi

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](c61c70fa402a4e08b54fffb7f20b793a.png)

    - Questo dispositivo viene detto HALF ADDER, o semi sommatore
    - Viene detto semi perché non può avere come risultato valori superiori a 2, come 3
    - Per farlo, proviamo ad inserire un terzo valore C, facendo quindi A+B+C
    - Per estendere U0, basta collegare C allo XOR
    - Per estendere U1 invece, bisogna considerare che U1 è 1 se più ingressi sono entrambi 1, ovvero A e B, A e C, B e C.
    - Creiamo quindi 3 AND e li colleghiamo ad un OR

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Questo è un FULL ADDER, capace di produrre 3 come risultato massimo Esso risolve il problema su calcoli ad 1 bit. Per calcoli superiori, basta collegare fra loro più FA e HA Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](39b6c0fc28c64e31bf8a607c38fb502b.png)

- Si parte da un Half Adder, e poi si usa un Full Adder per ogni bit. Si può notare però che, all'aumentare dei bit, aumenta il possibile ritardo dovuto al variare degli ingressi. Questo perché ogni FA dipende dal resto del precedente
- Dunque, per quanto questo sia accettabile su un piccolo numero di bit, su un numero di bit superiore dovremo usare un altro metodo

- Questo consiste nell'utilizzo dei CARRY LOOKAHEAD o previsori del riporto.
- ES.
    - Riporto bit 3 = a1*b1 + a1*a0*b0 + b1*b0*a0
- Questi dispositivi a due livelli sono in grado di calcolare il resto per un FA
- Se fosse messo a metà di un circuito, dimezzerebbe il tempo necessario.

- Però, se ne usassimo molti, per quanto la velocità aumenterebbe molto, si dovrebbero usare molti dispositivi in più, oltre all'aumento del consumo elettrico.
- Bisogna quindi vedere quale sistema usare, a seconda delle necessità specifiche

- Questo circuito supporta anche le addizioni fra numeri col segno (In complemento a 2)
- Quindi, è possibile usarlo per fare sottrazioni
- ES.

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](6ec3661b1c7e49ea8478de7512283b49.png)

![Quindi, basterebbe invertire con dei NOT tutti i bit del numero, e poi sommare 1, per ottenere la rappresentazione in complemento a 1 Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Ma è eccessivamente complesso Riprendendo il procedimento precedente, basterebbe sostituire il HA iniziale con un FA, sommando anche 1 o 0, a seconda che si voglia sommare o sottrarre Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](1d3b6c1ca6c547cb94016138c001db02.png)

![](a4b093dd3a1c42d0b5ea97a01b4640b5.png)

    - Si potrebbero implementare anche altre funzioni, per esempio il cambio di segno, aumentando i bit di controllo

![Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Si potrebbero implementare anche Moltiplicazione e Divisione Per quanto normalmente siano complesse da realizzare, è molto facile realizzarle con potenze di 2 In questo caso, le due operazioni vengono dette operazioni di SCORRIMENTO, in particolare la moltiplicazione è di scorrimento a sinistra, la divisione è di scorrimento verso sinistra ES. Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna Disegni a penna](b2533a5174874f1691c7733ce25abbfb.png)

    - Per implementarlo, nella moltiplicazione, basta collegare ogni bit ad un multiplexer, controllato dalla potenza di 2 a cui si moltiplica
    - La divisione è un trattino più complessa. Infatti, nello spostarsi a destra, i bit "liberi" che si ritrovano a sinistra devono essere coerenti con il segno del risultato
    - Questo sarà risolvibile con un ulteriore multiplexer, che agisce sul primo bit, controllato dal bit di segno del numero per cui si moltiplica

Creato con OneNote.