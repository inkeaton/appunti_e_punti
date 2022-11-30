* La derivazione normale viene rappresentata con $\to$ , quella multipla con $\to ^+$ 
* Un linguaggio generato da una grammatica è l'insieme delle stringhe terminali generate in più passaggi dalla grammatica
---
* Dobbiamo realizzare un parser che rispetti la grammatica che abbiamo scelto
* Nella derivazione, i non terminali vengono studiati contemporaneamente
* Non viene più prodotta una lista, ma un albero
* Bisogna stare attenti ad evitare ambiguità nella precedenza delle operazioni, per far modo che gli alberi si "snodino" in ordine corretto
* Una soluzione è usare gli operatori come prefissi o postfissi, invece che infissi
* Od usare una notazione simile a quella delle funzioni
* La soluzione più semplice però è aggiungere altre regole, per mantenere la notazione infissa
*  