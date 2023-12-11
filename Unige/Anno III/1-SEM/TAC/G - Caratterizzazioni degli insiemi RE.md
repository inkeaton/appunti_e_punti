+ Dato un insieme $A$ **ricorsivamente enumerabile** possiamo dare le tre seguenti definizioni, le quali sono equivalenti:
	1. $A$ possiede una macchina di **semi-decisione**
	2. $A$ è l'**immagine** di una **funzione ricorsiva**
	3. $A = \emptyset$ oppure è l'immagine di una **funzione ricorsiva totale**
+ È possibile dimostrare i collegamenti fra esse (*vedere nel cartaceo, tecnica a zig-zag*) 
+ Queste funzioni ricorsive sono quindi macchine in grado di generare (e quindi enumerare) tutte le funzioni presenti nell'insieme $A$ (con possibili ripetizioni)
	+ Da questo deriva il nome di "ricorsivamente enumerabile", in quanto possiamo dare un algoritmo per farlo
+ Quindi dire che un insieme è ricorsivamente numerabile vuol dire:
	+ Esiste un algoritmo di semi-decisione per decidere se un elemento ne fa parte
	+ Esso può essere generato algoritmicamente
---
+ Un altro esempio di insieme di funzioni non ricorsivamente enumerabile è l'insieme $\mathbb{T}$ delle funzioni che terminano sempre