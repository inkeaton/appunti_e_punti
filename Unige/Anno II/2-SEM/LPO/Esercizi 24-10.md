* let rec genprod f n = if n<=0 then 1 else f n * genprod f (n-1);;
* let fact = genprod (fun x->x);;
* let ten_power = genprod(fun x->10);;