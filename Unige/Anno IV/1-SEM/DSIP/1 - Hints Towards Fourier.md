+ Let's begin by talking about **linear spaces**:

> [! Definition ] 
>  ### Linear Spaces
>  + A set $V$ is called **linear space** if the following properties are true:
> 	 + $\exists + : V \times V \to V$ defined as $u + v = w$
> 	 + $\forall v, u \in V \quad u + v = v + u$
> 	 + $\forall v, u, w \in V \quad (u + v) + w = v + (u + w)$
> 	 + $\exists 0 : \; 0 + v = v$
> 	 + $\forall v \exists -v : \; v + (-v) = 0$
> 	 + $\forall \alpha \in \mathbb{R}, \quad \alpha(u + v) = \alpha u + \alpha v$
> 	 + $\forall \alpha, \beta \in \mathbb{R}, \quad (\alpha + \beta)v = \alpha v + \beta v$

+ A linear space can be defined as **Euclidean** if it implements the following operation:

> [! Definition ] 
>  ### Scalar Product
>  + A scalar product is a map $\langle \dots  , \dots \rangle : V \times V \to \mathbb{R}$ such that:
> 	 + $\forall u, v \in V \quad \langle u, v \rangle = \langle v, u \rangle$
> 	 + $\forall u \in V \quad \langle u, u \rangle \geq 0, \quad \langle u, u \rangle = 0 \leftrightarrow u = 0, \sqrt{\langle u, u \rangle} = ||u||$
> 	 + $\forall u, v, w \in V \quad \langle \alpha u + \beta v, w \rangle = \alpha \langle u, w \rangle + \beta \langle v, w \rangle$

---

+ A linear space can be defined by a set of linearly independent vectors.
	+ We usually use the set called the **standard basis** $e_1, e_2, \cdots, e_n$
+ In such a space, a vector can be defined as such:
	+ $v = \sum^{N}_{n = 1} v_n e_n$
+ The elements $v_1, v_2, \cdots, v_n$ are called **components** of the vector
	+ A component $v_n$ is obtained as: $v_n = v \cdot e_n$
+ The **scalar product** is defined as:
	+ $\langle v, u \rangle = v^T u = \sum^{N}_{n=1} v_n u_n$
	+ *If you work with complex numbers, you use the complex conjugate of the second, to maintain the result a real number*
+ Given two vectors, one can **orthogonalize** them by subtracting the projection of one from the other
	+ For example, given $v_1$ and $v_2$ we get the following vectors:
		+ $u_1=v_1$
		+ $u_2 = v_2 - \cfrac{\langle v_2, v_1 \rangle}{\langle v_1, v_1 \rangle} v_1$
---
+ Let's consider a **linear space of piece-wise functions**
+ Its dimensions must be infinite
+ In it, the scalar product is defined as follows:
	+ $\begin{align}\langle f, g \rangle &= \int^{b}_{a} f(t) g(t) dt = \\ &= \frac{b - a}{N} \sum^{N}_{n=1} f_n g_n\end{align}$
+ We can see the similarity with the previous scalar product. When $N \to \infty$, it becomes equal
+ Similarly, we can orthogonalize functions as before:
	+  $g_1=f_1$
	 + $g_2 = f_2 - \cfrac{\langle f_2, f_1 \rangle}{\langle f_1, f_1 \rangle} f_1$
+ This confirms the idea that **functions can be seen just as vectors**, in this space
---
+ Let's introduce and **idea**.
+ Considering the $[-\pi, \pi]$ interval, we describe the following infinite sets of functions:
	+ $\begin{align}\phi_0 (t) &= \cfrac{1}{\sqrt{2\pi}} \\ \phi_{2n-1} (t) &= \cfrac{\sin{nt}}{\sqrt{\pi}}  \qquad n \in \mathbb{N}\\ \phi_{2n} (t) &= \cfrac{\cos{nt}}{\sqrt{\pi}}\end{align}$
+ Those functions are:
	+ **Normalized** (thanks to the denominators)
	+ **Mutually Orthogonal**
+ $n$ can be seen as the number of cycles of the functions
+ Another set is the following:
	+ $\psi_n (t) = \cfrac{e^{int}}{\sqrt{2 \pi}} \qquad n \in \mathbb{Z}$
+ This too has the same properties of the previous
+ Thus, we extend the property of linear independence:

> [! Extension ] 
>  ### Linear Independence
>  + An infinite set $V$ is called **linearly independent** if  if a finite subset of vectors is linearly independent

+ As such, we could use one of this sets as a **basis** for our space of functions
+ Then, we would get the components of a function with the following operation:
	+ $f_n = \langle f, \psi_n \rangle$
+ To get our function, we would need to compute the following sum:
	+ $f = \sum^{+ \infty}_{n = - \infty} f_n \psi_n$
+ Does this sum **converge**? **Yes**, to the actual function
+ But we can't sum to infinity, a computer as only so much space...
+ If we call $f_N$ the function obtained summing the first $N$ elements, how much is it different from $f$?

> [! Property ] 
>  ### Best Approximation Property
>  + Given a function $f$ and a arbitrary set of $N$ numbers $d_n$, the following is true:
> 	 + $||f_N - f|| \leq ||d_n - f ||$
> 		 + *More details in the notebook...*

+ To compare $f_N$ and $f$, we just need to **compare the norms** of the two functions
+ When $N \to \infty$, $||f_N - f|| \to 0$