+ Le funzioni a più variabili $F : A \in \mathbb{R}^n \to \mathbb{R}^m$ possono essere divise in due categorie:
	+ **Scalari**, per $m = 1$
	+ **Vettoriali**, per $m > 1$
+ Vedremo più nel dettaglio le funzioni scalari, in quanto **ogni funzione vettoriale** $F$ può essere **riscritta** **con** l'utilizzo di un insieme di funzioni **scalari** $f_n$ (campo scalare) :
	+ $F(x_1, \cdots, x_n) = (f_1(x_1, \cdots, x_n), \cdots, f_n(x_1, \cdots, x_n))$
+ L'**immagine** di $F : A \in \mathbb{R}^n \to \mathbb{R}^m$ viene definita come:
	+ $F(A) = \{Q \in \mathbb{R}^m : Q = F(P), P \in A\}$
+ La **controimmagine** come:
	+ $F^{-1}(D) = \{P \in A : F(P) \in D\}$
---
+ Le funzioni in $\mathbb{R}^3$ possono essere rappresentate in più modi:
	+ Associando alla funzione una **superficie**, un "modello 3D" della funzione
	+ Associando alla funzione degli **insiemi di livello**, curve e punti accomunati dal valore della **controimmagine** in quel punto. 
		+ È un sistema affine alle **cartine topografiche**
		+ Aiuta a comprendere la **ripidità** della funzione
---
+ Una funzione si dice:
	+ **Lineare**, se passa per l'origine del piano
	+ **Affine**, se non passa per l'origine
+ Un importante classe di funzioni è quella delle **funzioni scalari affini**:
	+ $f(x, y) = z_0 + a(x - x_0) + b(y - y_0)$
+ Il **grafico** di una funzione simile è il piano di equazione cartesiana:
	+ $(a, b, -1) \cdot (x-x_0, y-y_0, z-z_0)$
+ è il piano **ortogonale** al vettore (detto **direzionale**) $(a, b, -1)$ che passa per il punto $(x-x_0, y-y_0, z-z_0)$
---
+ Le **Curve** sono un insieme di funzioni definite su un sotto-intervallo di $\mathbb{R}$ 
+ La sua immagine o **sostegno** è uguale all'oggetto tridimensionale che assoceremmo comunemente alla curva
+ Curve **diverse** possono condividere lo **stesso** sostegno:
	+ $f(t) = (\cos t, \cos t)$
	+ $g(t) = (\cos 2t, \cos 2t)$
		+ $f$ e $g$ possiedono lo stesso sostegno
---
+ Le **superfici** sono un argomento più complesso. Le definiremo come superfici **parametriche**
+ Esse sono funzioni della forma:
	+ $\sigma (u, v) = (x(u, v), \; y(u, v), \; z(u, v))$
+ *manca piccola parte sulle funzioni lineari*