# Principio d'Induzione

- Sia **P** una proprietà sui numeri interi e **C** un intero:
    - Se P è vera per C **(Passo Base)** e, per ogni numero N > C, se P è vera per N - 1, vale anche per N **(Passo Induttivo)** allora P è valida per ogni N $\ge$ C
- Questo principio appartiene alla Logica del secondo ordine: proprietà che parlano di proprietà
- Il principio ricorda quello della **ricorsione**

### Esempio: Sommatoria dei Primi n numeri

- $S_n = \sum_{k=0}^n k = \frac{n(n+1)}{2}$
- Essa può essere dimostrata grazie al Principio d'Induzione
- BASE
    - $n = 0$
    - $\sum_{k=0}^0 k = \frac{0(0+1)}{2}$
    - $0 = \frac{0}{2}$
    - VERO, BASE VERIFICATA
- PASSO INDUTTIVO
    - Assumiamo $\sum_{k=0}^n k = \frac{n(n + 1)}{2}$
    - Proviamo $\sum_{j=0}^{n+1} j = \frac{(n+1)(n + 2)}{2}$
    - $\sum_{j=0}^{n+1} j = \left( \sum_{k=0}^{n} k \right) + (n + 1)$
    - $\sum_{j=0}^{n+1} j = \frac{n(n+1)}{2} + (n-1) = (n+1) * (\frac{n}{2} + 1) = (n+1) * (\frac{n + 2}{2} ) = \frac{(n+1)(n + 2)}{2}$
- DIMOSTRATO PER INDUZIONE

# Logaritmi
- $y = \log_bx \rightarrow b^y = x$
- b viene detta BASE e deve essere maggiore di 0 e diversa da 1
- x deve essere maggiore di 0

### Proprietà Logaritmi

- $log_b1 = 0$
- $log_bb = 1$
- $log_bb^z = z$
- $b^{log_bx} = x$
- $log_b(x * y) = log_bx + log_by$
- $log_bx = \frac{log_ax}{log_ab}, \forall a > 1$

### Funzione Logaritmo

## AGGIUNGERE GRAFICI

- La funzione tende a $+ \infty$, ma molto lentamente, rispetto a altre funzioni, per esempio quelle esponenziali
- Questo perchè una funzione esponenziale cresce sempre più velocemente di una polinomiale
- Questa particolarità ci aiuta nella sceltà degli algoritmi, in base all'efficienza. Infatti, **un algoritmo logaritmico è preferibile ad uno esponenziale**, questo perchè, su grandi numeri, il numero di operazioni per elemento cresce a velocità minore