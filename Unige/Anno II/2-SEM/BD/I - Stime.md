* Come già detto, nello scegliere un PQP, si considera anche il costo d'esecuzione
* Come viene calcolato questo? Si utilizza un approccio bottom-up, e partendo dalle radici dei piani, si contano i costi parziali, sia di tempo che di spazio.
* Questi costi sono statistiche, stime ottenute tramite i dati contenuti nei cataloghi di sistema
* Idealmente, questi costi andrebbero ricalcolati ad ogni modifica della base di dati. Essendo un'operazione costosa, nella realtà questo avviene periodicamente, o quando richiesto tramite il comando ANALYZE
---
* Nello stimare il costo di una selezione si usa una probabilità, detta fattore di selettività.
* Questo indica quanto è probabile che una tupla nella relazione soddisfi la selezione
	* Se una selezione restituisce molte tuple, viene detta poco selettiva
* Anch'esso viene calcolato, come le altre statistiche
---
* Similmente all'ottimizzazione logica, anche i piani fisici vengono scelti in base ad alcune euristiche. 
* Queste permettono di effettuare una prima scrematura fra i possibili piani da scegliere. Verrà poi scelto un ultimo piano, quello più economico, fra i rimanenti
* Per i JOIN
	* Si preferiscono in piani Left-Deep, in quanto permettono di usare il pipelining
	* Non vengono considerate permutazioni di JOIN che implicano dei prodotti cartesiani
---
* Rimane infine l'attività di Progettazione Fisica

28/04/23