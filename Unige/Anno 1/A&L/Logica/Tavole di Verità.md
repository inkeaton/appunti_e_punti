Tavole di Verità
lunedì 11 ottobre 2021
16:42

- Il significato dei connettivi logici può essere riassunto algoritmicamente dalle tavole di verità
- Avremo due valori
    - ![](b167f92a8e4340dbbbe0b11e0eac6aac.png)
    - Vero (T, V, 1)

NEGAZIONE

- ![](0e0ad088c36a449ba4ab04428b3a540e.png)

|     |     |
| --- | --- |
| P   | ![](0aaeb72bfb42488497e211c4e2870969.png) |
| 0   | 1   |
| 1   | 0   |

DISGIUNZIONE

- ![](63b580bfaa204e74904c334478f1002e.png)

|     |     |     |
| --- | --- | --- |
| P   | Q   | ![](088d632a54b14096874fd2f981458db1.png) |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 1   |

CONGIUNZIONE

- ![](bdc601e70e354ce0b1a3ea6eb3d94cd3.png)

|     |     |     |
| --- | --- | --- |
| P   | Q   | ![](a489c5123bc6408495880a43776d1078.png) |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

IMPLICAZIONE

- ![](0e3e2cb5d1c842e68f232e51ea715d73.png)

|     |     |     |
| --- | --- | --- |
| P   | Q   | ![](03ecc34583eb4be3b9001c8538546a16.png) |
| 0   | 0   | 1   |
| 0   | 1   | 1   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

BIIMPLICAZIONE

- ![](cddcf21417e543de80440cce43cefa91.png)

|     |     |     |
| --- | --- | --- |
| P   | Q   | ![](db7b4e5316f645cfbb08cb8564b22317.png) |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

Proposizioni ATOMICHE

- Creiamo una famiglia di asserzioni atomiche od elementari, proposizioni che possono essere o vere o false, non ulteriormente scomponibili
- Queste vengono rappresentate dalle lettere dell'alfabeto latino (A,B,C…)
- Utilizzando queste insieme ad i connettivi, possiamo formare asserzioni ben più complesse da sottoporre alle tavole di verità
- ES.
- ![](6976764b742645a7978c11cdfe61792c.png)
- La tavola di verità corrispondente è:

|     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- |
| A   | B   | C   | ![](ef25920e19064d7da8e7be66f45a44e0.png) | ![](e92e2afa49fa45f5adb1c1f3903dd5e6.png) | ![](e9e85ddcb6e345fb89e839cf8fd120e7.png) | P   |
| 0   | 0   | 0   | 1   | 0   | 1   | 1   |
| 0   | 0   | 1   | 1   | 1   | 0   | 0   |
| 0   | 1   | 0   | 0   | 1   | 0   | 0   |
| 0   | 1   | 1   | 0   | 1   | 0   | 0   |
| 1   | 0   | 0   | 1   | 0   | 0   | 0   |
| 1   | 0   | 1   | 1   | 1   | 1   | 1   |
| 1   | 1   | 0   | 1   | 1   | 1   | 1   |
| 1   | 1   | 1   | 1   | 1   | 1   | 1   |

Creato con OneNote.