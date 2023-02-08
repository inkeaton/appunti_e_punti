#### Teoria
* I tipi vengono dedotti automaticamente dall'interprete in base al modo in cui vengono usati
* `int` è un tipo built-in semplice, `int -> int` è un tipo built-in composto
	* `->` è un costruttore di tipi, i tipi formati con esso sono solitamente i tipi delle funzioni
	* è associativo a destra
	```ocaml
	int->int->int = int->(int->int)
	```
---
* Le funzioni hanno precedenza superiore alle operazioni
* Le funzioni anonime hanno precedenza inferiore

---
#### Variabili
* Tutte le variabili sono in realtà "costanti", non mutabili. 
* Possono essere modificate facendo una nuova dichiarazione, la quale sovrascrive la precedente
* Sono globali, perchè sono definite al livello superiore. Si possono creare variabili locali, definendole dentro delle funzioni
```ocaml
# let x=2;; 
val x : int = 2 

# let y=x+40;; 
val y : int = 42 

# x+y;; 
- : int = 44
```

---
#### Funzioni
* Dichiarare una funzione
```ocaml
let inc = fun x -> x+1 (* the increment function *) 
let inc2 x = x+1 (* a more compact syntax *)
```

* Funzioni __anonime__ (non sono propriamente definite, ma usate sul momento)
```ocaml
fun x -> x+1 (* the increment function *)
```

* Usare una funzione 
```ocaml
inc 3 (* syntax inc(3) optional, evaluation returns 4 *) 
inc2 3 (* syntax inc2(3) optional, evaluation returns 4 *)
(fun x -> x+1) 3 (* evaluation returns 4 *)
```

* Le funzioni che prendono più argomenti possono essere scritte nei seguenti modi
```ocaml 
# fun x -> fun y -> x+y 
- : int -> int -> int = <fun>

# fun x y -> x+y                 (* a more compact syntax *)
- : int -> int -> int = <fun>
```

* Le funzioni possono prendere come argomenti anche altre funzioni
```ocaml
# let apply_f_to_0_and_inc = fun f -> 1+f 0;;
val apply_f_to_0_and_inc : (int -> int) -> int = <fun>
```

---
* Le funzioni possono essere __curried__ o __uncurried__
	* Nel primo caso, vengono passati n argomenti
	* Nel secondo, una sola tupla contenente n elementi
```ocaml
# fun x y->x+y;; (* curried version *)
- : int -> int -> int = <fun>
# fun (x,y)->x+y;; (* uncurried version *)
- : int * int -> int = <fun>
```
* Le funzioni curried permettono __l'applicazione parziale__, ovvero il passare un elemento alla volta. Questo permette di definire nuove funzioni, e facilitare il riutilizzo del codice
---
* Non è possibile confrontare due funzioni con `=`
---
* Dichiarando una funzione utilizzando una valore di una variabile statica, essa continuerà ad usare quel valore, anche se esso viene sovrascritto
---
#### Ricorsione
* Possiamo usare la parola `rec` nel dichiarare una funzione per renderla ricorsiva
```ocaml
let rec sumsquare n = 
	if n<0 then 0 else n*n+sumsquare(n-1);;
```

---
#### Variabili Locali
* Possono essere definite tramite la parola `and` all'interno di una funzione
* Nelle dichiarazioni innestate, si possono sovrascrivere i valori di variabili di livello superiore
```ocaml
# let f x=x+1 and v=41 in f v;; (* f and v can only be used here *) 
- : int = 42

# let x=1 in let x=x*2 in x*x (* nested declarations *) 
- : int = 4
```

#### Tuple
* Usa `,` come operatore, `*` come costruttore di tipo
	* `,` ha precedenza minore di tutti gli operatori tranne la funzione anonima
	* `*` ha precedenza superiore di `->`
 ```ocaml
 # () 
 - : unit = () (* this is the void value *) 
 
 # print_int;;  (* predefined, prints an integer on stdout *) 
 - : int -> unit = <fun>
 
 # 1,2,3 
 - : int * int * int = (1, 2, 3) 
 
 # (1,2),3 
 - : (int * int) * int = ((1, 2), 3) 
 
 # 1,(2,3) 
 - : int * (int * int) = (1, (2, 3))
 ```
 
 * Possono esserci funzioni con Tuple come argomenti
```ocaml
# let add(x,y) = x+y;; (* let add = fun(x,y) -> x+y *) 
val add : int * int -> int = <fun>

# add (3,4);; 
- : int = 7
```

---
#### Booleani
* Definiti con l'espressione `false|true` 
* Possiedono gli operatori `not`, `||` e `&&`
	* `||` e `&&` sono valuatati a __Short Circuit__: non sempre vengono valutati entrambi gli operandi
	

#### Espressioni Condizionali
* Si usano `if`, `then`, e `else` 
* Le condizioni in `then` e `else` devono avere lo stesso tipo

---
#### Liste 
* Le liste sono tipi built-in, implementati come liste singolarmente collegate
* Le liste create devono essere liste di __qualcosa__ (es, `int list`)
* `[ ]` rappresenta la lista vuota
	* `[]` ha tipo `'a list` 
		* `'a` è un tipo __variabile__, può corrispondere ad ogni tipo 
* `::` permette di attaccare un elemento ad una lista già esistente
	* Ha associatività destra
* `@` permette di concatenare due liste. 
	* A differenza del precedente, non permette di decomporre unicamente la lista, e ha associatività sinistra
	* Ha complessità temporale molto superiore
* `list` è il type constructor corrispondente
---
* Una scrittura più semplice è `[e1;e2;. . .;en]`, equivalente di `e1::e2::. . .::en::[]`
```ocaml
[1] = 1::[] 
[1;2;3] = 1::2::3::[] 
[1,true] = (1,true)::[] 
1,[true] = 1,true::[]
```

---
* __Differenze__ fra liste e tuple:
	* Le liste devono avere tipi omogenei, le tuple no
	* Le liste possono avere lunghezza differente ed essere dello stesso tipo, le tuple no (`int*int` $\neq$ `int*int*int` )

#### Operatori come Funzioni Curried
* usando le parentesi tonde possiamo usare numerosi operatori come funzioni curried
```ocaml
# (+);; 
- : int -> int -> int = <fun>

# ( * );; 
- : int -> int -> int = <fun>

# (-);; 
- : int -> int -> int = <fun>

# (/);; 
- : int -> int -> int = <fun>

# (&&);; 
- : bool -> bool -> bool = <fun>
- 
# (||);; 
- : bool -> bool -> bool = <fun>

# (<);; 
- : ’a -> ’a -> bool = <fun>

# (=);; 
- : ’a -> ’a -> bool = <fun>

# (@) 
- : ’a list -> ’a list -> ’a list = <fun>
```

---
#### Pattern Matching
* 