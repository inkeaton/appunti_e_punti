Termini
lunedì 8 novembre 2021
15:09

- Sono espressioni che indicano Individui, ovvero membri del dominio a cui siamo interessati
- Sono definiti discorsivamente come:
    - Ogni variabile è un termine
    - Ogni Costante è un termine
    - ![](614662cbfc1443a983ac47ebfb42367d.png)
- ![](f268b6e99a5846bead0e1cf4fcfa7d84.png)
    - ![](eaed60e5f6c54194a5ec5efe7d6e357e.png)
    - ![](ddfc607f4d67437e831eab9fb0107985.png)
- Ovvero
    - ![](c6d5bcfc08594d7d837b268d5c944934.png)

- I termini si costruiscono con strutture ad albero sintattico
    - La radice è il termine (o stringa) dato
    - Se un nodo ha una variabile o costante come etichetta, è un nodo
    - ![](3f43be009e3f4eb3a88cb74d14b0a276.png)

ALGORITMO ALBERO SINTATTICO TERMINI

- Dato un nodo con etichetta
    - Controlla se l'etichetta è una variabile o una costante. In questo caso, il nodo è una foglia
    - Altrimenti, controlla se comincia con un simbolo funzionale, in caso contrario, non si tratta di un termine.
    - ![](31dbfdbb7e7f425d872c96329478e529.png)
    - Passa al nodo seguente

- L'Albero può essere semplificato immettendo nei nodi non terminali solo il simbolo funzionale
- ![](b4c38e29811d49959d41a8037732f6b7.png)

POLINOMI

- ![](c502e20a4aba4a33a23f3c0ee0cb5013.png)
    - +, * Simboli Funzionali Binari
    - 1 Simbolo di Costante

- Sia t :
    - ![](ff520e93b0f640e288cabda754c20bde.png)
- Riscriviamolo con + e * messi fra i loro argomenti
    - ![](29b093edcc904a49a1f3878ba47d9621.png)
- Riscrivibile, secondo le convenzioni matematiche
    - ![](1c6c8c218c0d46d097d0c9c3e534c25e.png)

- Una volta riscritto in questo modo è impossibile ritornare alla forma originale. Questo perché la funzione che ci ha fatto arrivare a questa forma non è suriettiva

- Una volta stabiliti in termini, determiniamo come fare affermazioni su di essi
- Le affermazioni sono relazioni o quantificazioni

- Definiamo le formule atomiche
    - ![](d3b07c86ecfc4477af6a4c77539889c4.png)
    - Il n° di formule atomiche realizzabili dipende dalle relazioni presenti nel linguaggio. In ogni linguaggio è sempre presente la relazione di uguaglianza =

ALGORITMO FORMULE ATOMICHE

- Data una stringa, controlla che
    - Il primo ed ultimo simbolo siano parentesi
    - Il secondo sia un simbolo di relazione
    - Il terzo ed il penultimo siano parentesi
    - ![](b8ab08653c6745229814813255c566f7.png)
    - Che fra le virgole ci siano dei termini

- Dato L, Linguaggio di prim'ordine, l'insieme delle formule è definito, ricorsivamente, come:
    - Ogni formula atomica è una formula
    - ![](64aaf02984044606bfc8c6297e4686ef.png)
    - ![](219e731f9aa34246b0c75e39236c7e0a.png)
    - ![](0844e69453454d4190245e765cc22496.png)
- Definito per induzione
    - ![](d5e021697a4d43f6916653f8892482aa.png)
    - ![](4bc63bbae55841a39418040de75ae2e4.png)
- L'Insieme delle L-Formule è allora
    - ![](c0a110134ba746328adf463e17ca8e52.png)

COSTANTE LOGICA PRINCIPALE

- L'ultima costante logica applicata
- Ritrovabile col seguente algoritmo, derivato di uno simile presente nella logica proposizionale
    - Supponiamo quindi di avere una formula P non atomica
        - Il primo simbolo è una parentesi, la sua chiusura è l'ultimo simbolo
        - Il secondo può essere:
            - ![](4d60c33523ed4d7e999f14e26c2a572b.png)
            - Una parentesi. In questo caso, si trova la ) corrispettiva. Il connettivo subito dopo questa è il connettivo principale, Le sue sotto formule sono ciò che precede e segue il connettivo
            - Un quantificatore. In questo caso, il quantificatore è il connettivo principale. Ad esso segue una variabile, ed ad essa un termine, che è la sotto formula principale

Creato con OneNote.