Alberi sintattici
domenica 24 ottobre 2021
15:14

- ![](60d11e0a9e9a4423af2888473922e598.png)
- Gli elementi di T vengono denominati nodi. Il nodo minimo è la radice, i nodi senza successori sono foglie
- ![](688f564fb77540de8342a02f903bfefe.png)
- Un albero viene detto binario se ogni nodo ha al più 2 successori immediati
- Un nodo può essere confrontato solo con i suoi predecessori e successori
- Un ramo è un insieme totalmente ordinato di nodi
- Un albero si dice etichettato se ad ogni nodo è associato un elemento di un insieme prefissato

DEFINIZIONE

- L'albero sintattico di una formula P è l'albero binario etichettato finito tale che:

    1. La radice è etichettata con P
    2. Se un nodo è etichettato con una formula Q allora:

        - Se Q è una formula atomica, il nodo è una foglia
        - ![](036367b5113e42009539e0c5b3c2fd58.png)
        - Se Q è (R#S), dove # è un connettivo binario, allora Q ha due successori immediati, R ed S

- Usando questo algoritmo, potremmo creare un programma in grado di creare un albero sintattico automaticamente da una formula. Il programma che ne uscirebbe sarebbe ricorsivo e quindi potrebbe esserci il rischio che continui in infinito, ma siamo sicuri che non lo faccia, dato che esso dipende dalla lunghezza delle etichette dell'albero, le quali diminuiscono ogni volta.

OSS

- Sia P una formula e T il suo albero
    - I nodi di T sono le sotto formule di P
    - Le etichette delle foglie sono le atomiche di P

IL CONNETTIVO PRINCIPALE

- Esiste un algoritmo in grado di ritrovarlo, basato sulle parentesi
- Ogni volta che scriviamo (, dovremo poi scrivere ).
- Per trovare la ) associata alla ( che ci interessa, creiamo un contatore che, ogni volta che trova una parentesi (, aumenta di 1, e diminuisce di 1 quando incontra ). La parentesi ) sulla quale il contatore diventa 0 , è la parentesi relativa a (.

- Supponiamo quindi di avere una proposizione P non atomica
    - Il primo simbolo è una parentesi, la sua chiusura è l'ultimo simbolo
    - Il secondo può essere:
        - ![](30163e33cf384e12924b8e7865a47c31.png)
        - Una parentesi. In questo caso, si trova la ) corrispettiva. Il connettivo subito dopo questa è il connettivo principale, Le sue sotto formule sono ciò che precede e segue il connettivo
- Questo algoritmo può essere usato anche su stringhe che non sono formule, ma si incepperà prima o poi

CONVENZIONI SULLE PARENTESI

- Con le regole stabilite, servono un sacco di parentesi per scrivere le formule più complesse
- Quindi, allo scopo di facilitarne la lettura, stabiliamo delle convenzioni:
    - Eliminiamo le parentesi intorno alle atomiche
    - SI eliminano le parentesi attorno alle sotto formule quando coerenti, usando come indice la seguente gerarchia:
        - ![](c1646cdc2f3a461184caaca21aa5d0bf.png)
        - ![](7dd2a914bff749a7a962c4c96be162b6.png)
        - ![](7c9455b3d1ab4dac8863160a6cfb6a86.png)
    - ![](b02e413fba2d4d6eb06a764585e3db60.png)
- ES.
    - ![](613cc2a6801d4a7cb94d7771e7188a05.png)
    - ![](707b51875d6944a6ab1097fbfefd4c5a.png)
    - ![](dd8b71295bf840e3bf4226ac294cd7b4.png)
    - ![](de0a2ea0480c4f1ea650b8e23613a92e.png)
    - ![](150265e07e8143e5b1479370b9d6723b.png)
- Si possono scrivere anche gli alberi senza (). Il connettivo principale è quello di priorità più bassa, non contenuto fra parentesi

Creato con OneNote.