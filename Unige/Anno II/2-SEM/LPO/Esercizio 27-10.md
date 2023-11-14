* let rec interval = fun x y -> if x > y then [] else x::interval (x+1) y;;
* let interval min max=
	* let rec aux x = if x > max then [] else x::aux (x+1) in aux min
* --- definiamo una variabile (funzione) locale che è aux 
