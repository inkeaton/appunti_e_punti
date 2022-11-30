Circuiti Logici
mercoledì 20 ottobre 2021
17:43

- I circuiti combinatori possono essere rappresentati come scatole nere in cui avvengono trasformazioni di dati in entrata
- Partiamo da fili che possono essere o 0 o 1.
- Immaginiamo inizialmente una scatola in cui abbiamo una entrata ed una uscita
- Possono avvenire quattro possibili trasformazioni

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| I   | U1  | U2  | U3  | U4  |
| 0   | 0   | 0   | 1   | 1   |
| 1   | 0   | 1   | 0   | 1   |
|     | Costante<br>Inutile | Id(x)<br>Inutile | Funzione<br>di negazione | Costante<br>Inutile |

- DI queste, solo la funzione negazione è interessante da analizzare
- Prendiamo ora una scatola con due entrate ed una uscita
- Ci sono 2^4 possibilità

|     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| I1  | I2  | U1  | U2  | U3  | U4  | U5  | U6  | U7  | U8  | U9  | U10 | U11 | U12 | U13 | U14 | U15 | U16 |
| 0   | 0   | 0   | 1   | 0   | 1   | 0   | 1   | 1   | 0   | 1   | 0   | 1   | 0   | 1   | 0   | 1   | 0   |
| 0   | 1   | 0   | 0   | 1   | 1   | 0   | 0   | 1   | 0   | 0   | 1   | 1   | 0   | 0   | 1   | 1   | 1   |
| 1   | 0   | 0   | 0   | 0   | 0   | 1   | 1   | 1   | 0   | 0   | 0   | 0   | 1   | 1   | 1   | 1   | 1   |
| 1   | 1   | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 1   | 1   | 1   | 1   | 1   | 1   | 1   | 1   | 0   |
|     |     | Cost<br>Inutile | NOR |     | NOT I1<br>Inutile |     | NOT I2<br>Inutile | NAND | AND | XNOR | Id(x)2<br>Inutile |     | Id(x)1<br>Inutile |     | OR  | Cost<br>Inutile | XOR |

- Di tutte queste possibilità, ci interessano solo le funzioni AND, OR e XOR, ed i loro contrari
- Interessante notare che i contrari non sono altro che una funzione formata dalla funzione affermativa e la funzione negazione in tandem
- Andando avanti arriveremmo a vedere molte altre funzioni, ma sarebbero fin troppe, non ci soffermeremo.
- Considereremo solo queste 7.
- Diamo dei simboli ad ogni funzione:

![](0fcae7919f834d6f95cdd7aadb1daecb.gif)

- Queste funzioni possono essere allargati a casi a più ingressi, usandone più di una, e la proprietà associativa
- AND a tre ingressi è definita l'estensione commutativa ed associativa di AND

Creato con OneNote.