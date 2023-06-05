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

* Possiedono un modulo, `List`, contenente una serie di funzioni built-in da usare sulle liste
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
* I pattern sono delle sequenze costruite tramite costruttori (__non__ operatori) usate per identificare valori tramite la decomposizione
```ocaml
let add (x,y) = x+y;;
add (3,5);; (* does (3,5) match with pattern (x,y)? *)
```

* Possiamo usare in queste definizioni la wild card `_` , usata per indicare un dato di cui non ci importa il valore
```ocaml
let hd (h::t) = h;; (* returns the head of the list *)

let hd (h::_) = h;; (* head of the list, with wildcard ’_’ *)
```

* Possiamo usare questi pattern per creare degli "switch-case", creando funzioni capaci di variare a seconda del tipo di pattern, e sfruttare la decomposizione 
* Usiamo le parole `match` e `with`. `|` divide i casi
* Si può anche usare `as` per riferirsi alla variabile che viene scomposta nei casi 
```ocaml
let swap l = match l with
	[] -> []
	| [x] -> [x] (* x is a local variable for this case *)
	| x::y::t -> y::x::t;; (* x, y and t are local variables for this case *)

let mynot = function (* simplified syntax *)
	false -> true 
	| _ -> false;;

let ord_swap = function (* ls shorter than x::y::tl *)
	x::y::tl as ls -> if x>y then y::x::tl else ls
	| other -> other;;
```

#### Stringhe
* Hanno il tipo primitivo `string`, e si cotruiscono tramite `"`
* `""` è la stringa vuota.
* Esiste la concatenazione `^`, anche essa può essere usata in modo curried
* Le stringhe possiedono un __modulo__, `String`, il quale contiene varie funzioni predefinite da usare su di esse

---
#### Accumulatori
* Nella ricorsione possiamo usare degli __accumulatori__, variabili che contengono valori intermedi e vengono passati ad ogni ricorsione 
* Questo permette di implementare, per esempio, la tail recursion, nella quale l'ultima operazione eseguita è sempre la chiamata ricorsiva. Questo permette anche di ottimizzare il tempo d'esecuzione di queste funzioni
* Per far ciò serviranno delle funzioni ausiliarie (locali)
```ocaml
# let rec reverse = function 
	hd::tl -> reverse tl @ [hd] (* inductive case *) 
	| _ -> [];; (* base case [] *) 

# let acc_rev ls = (* parameter ls needed to get a polymorphic function *)
	let rec aux acc = function
		hd::tl -> aux (hd::acc) tl
		| _ -> acc
		in aux [] ls;;
```

---
#### Funzioni Polimorfiche
* Sono funzioni capaci di accettare argomenti differenti. Ad esempio, la `acc_rev` precedente può accettare `int list`, `bool list`, etc

---
#### Eccezioni
* Le eccezioni sono di tipo `exn`, e vengono generate con `raise`
* Sono dichiarate come `exception`
* La gestione avviene tramite `try` e `with`
```ocaml
exception Fault;; (* constant constructor *)
exception Fault1 of string;; (* a unary constructor *)
exception Fault2 of string*exn;; (* a binary constructor *)

let exc=Fault;;
let exc1=Fault1 "error message";;
let exc2=Fault2 ("msg",exc);;
```

* Esiste la funzione predefinita `failwith` che prende un argomento stringa e fa `raise` con essa

---
#### Float
* I float usano come operatori i "soliti", ma con il punto dopo. Per le tuple si usa `**`
* float e int __non__ sono compatibili
* Esiste un modulo, `Float`, con alcune funzioni

---
#### Tipi Varianti
* Usando `type`, possiamo definire __nuovi tipi__
	* L'identificatore di tipo deve iniziare con una lettera minuscola
	* I costruttori devono iniziare con una lettera maiuscola
	```ocaml
	type color = Red | Green | Blue;; (* just constant constructors *)
	
	let to_string = function (* to_string : color -> string *)
	  Red -> "red"
    | Green -> "green"
    | Blue -> "blue";;

	List.map to_string [Red; Blue; Green; Blue];;
	- : string list = ["red"; "blue"; "green"; "blue"]
	```

* Le dichiarazioni di tipi varianti possono essere __ricorsive__. Solitamente usato per creare strutture ad albero, come degli AST
* Un tipo variante built-in è `option`, composto da `None` e `Some of 'a`
	* Nel modulo `Option` sono definite alcune funzioni da usare con essi
* Potremmo implementare dei BST!