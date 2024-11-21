  + Of the three representation we've seen, all of them are:
	  + **Orthogonal**
	  + **Complete** (We are able to return to the original signal without losses)
+ While this properties are cool and all, they bring some cons, orthogonality in particular:
	+ We are unable to separate a signal form the noise contained in it
	+ If we lose the value of a considerable projection, we are screwed
+ As such, we present a new representation, more sparse and redundant
---
+ A frame in $\mathbb{R}^n$ is a sequence of n-dimensional vectors $f_i$ ($i \in (1, \cdots m)$) with $m \geq n$, such that: $$\exists B\geq A > 0 \; | \quad \forall v \in \mathbb{R}^n \qquad A||v||^2 \leq \sum \langle f_i, v \rangle^2 \leq B||v||^2$$
+ If $A=B$, the frame is said to be **tight**.
+ If all the $f_i$s are unit norm, we call it a **unit norm frame**
+ An important property is that every frame is a **spanning sequence** of $\mathbb{R}^n$, and viceversa
	+ This ensures that the $f_i$ are not all null
+ We define the following filters:
	+ The **Analysis Filter** is a linear map $F: \mathbb{R}^n \to \mathbb{R}^m$ defined as: $$F(v) = \begin{bmatrix} \langle f_1, v \rangle & \langle f_2, v \rangle & \cdots & \langle f_m, v \rangle\end{bmatrix}^T$$
		+ It can be written as the matrix:$$F = \begin{bmatrix}f_1^T \\ f_2^T \\ \vdots \\ f_m^T\end{bmatrix}_{m \times n}$$
	+ The **Synthesis Filter** is a linear map $F^*: \mathbb{R}^m \to \mathbb{R}^n$ defined as: $$F^*(c) = \sum^m_{i=1} c_i f_i$$
		+ The operator simply is: $$F^* = F^T$$
+ This two filters have **three** main **properties**:
	1. $F$ is **injective**
	2. Given $e_i$ the standard basis in $\mathbb{R}^n$, the following is true:$$F^Te_i = f_i$$
	3. $F^*$ is **surjective**
---
+ Let's now see how to use a frame
+ The **Frame Operator** $S$ is the linear map $\mathbb{R}^n \to \mathbb{R}^n$ defined as: $$S(v) = F^TFv = \sum^M \langle v_i f_i\rangle f_i$$
	+ It's symmetric, invertible and positive definite
+ This formula may remind us of the projection on orthonormal basis, but it is not complete ($S(v) \neq v$)
+ We need to introduce the concept of **dual frame**, $S^{-1}f_i$ 
+ So, it is true the following: $$v = SS^{-1} v = \sum^m \langle v, S^-1f_i \rangle f_i = \sum^m \langle v, f_i \rangle S^-1f_i$$
	+ We can choose on which one project and which one reconstruct