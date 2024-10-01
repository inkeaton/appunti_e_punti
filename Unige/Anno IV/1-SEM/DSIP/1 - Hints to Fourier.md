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

+ A linear space can be defined as Euclidean if it implements the following operation:

> [! Definition ] 
>  ### Scalar Product
>  + A scalar product is a map $\langle \dots  , \dots \rangle : V \times V \to \mathbb{R}$ such that:
> 	 + $\forall u, v \in V \quad \langle u, v \rangle = \langle v, u \rangle$
> 	 + $\forall u \in V \quad \langle u, u \rangle \geq 0, \quad \langle u, u \rangle = 0 \leftrightarrow u = 0$
> 	 + $\forall u, v, w \in V \quad \langle \alpha u + \beta v, w \rangle = \alpha \langle u, w \rangle + \beta \langle v, w \rangle$

---

+ A linear space can be defined by a set of linearly independent vectors.
	+ We usually use the set called the **standard basis** $e_1, e_2, \cdots, e_n$
+ In such a space, a vector can be defined as such:
	+ $v = \sum^{N}_{n = 1} v_n e_n$
+ The elements $v_1, v_2, \cdots, v_n$ are called **components** of the vector
	+ A component $v_n$ is obtained as: $v_n = v \cdot e_n$
+ The scalar product is defined as:
	+ $v^T u = \sum^{N}_{n=1} v_n u_n$
---
+ Let's consider a **linear space of piece-wise functions**
+ Its dimensions must be infinite
+ In it, the scalar product is defined as follows:
	+ $\begin{align}\langle f, g \rangle &= \int^{b}_{a} f(t) g(t) dt = \\ &= \frac{b - a}{N} \sum^{N}_{n=1} f_n g_n\end{align}$
+ We can see the similarity with the previous scalar product. When $N \to \infty$, it becomes equal