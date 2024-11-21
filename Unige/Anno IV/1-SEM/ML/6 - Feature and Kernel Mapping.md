+ The models we have seen are useful, but they can only work with linear models
+ What if we wanted to predict a **non-linear** model?
+ In particular, we want to study models linear in parameters, non-linear in unknowns
---
+ Our objective is to avoid rewriting all of the code and ideas we implemented
+ A simple first idea is to use a **Feature Map** $\Phi$ able to translate our problems in another space $\in \mathbb{R}^p$ where the problem becomes linear
	+ An example is using polynomials, as linear combinations of monomials, sinusoids, gaussians, etc
	+ If our function resembled more of an union between these spaces, we could try using them in tandem
---
+ The problem though is that, as **dimensions grow**, the number $p$ grows as well, making computations more and **more complex**
+ We want a method able to remain efficient even as the number of dimensions grows to **infinity**
+ To achieve better performance, we change the way we compute our solutions
+ We can rewrite the following: $$w_\lambda = \sum^n \phi(x_i)c_i, \qquad c= \left[\Phi \Phi^T + \lambda n I\right]Y$$And the solution becomes:$$f_\lambda = \sum \phi(x_i)^T\phi(x_i)c_i$$
+ We can see that we do not need to compute $w$ to solve the problem, we just need a **Kernel Map** $K(x, \hat{x})$, a matrix such that: $$\left[K(x, \hat{x})\right]_{ij} = \sum^p_{k=1} \phi_k(x) \phi_k(\hat{x})$$
+ We see that as $p$ grows the sum seems infinite! But, depending on the specific $\Phi$, we can use some infinite series tricks to determine were it **does converge**, and as such, compute them
	+ *We saw examples for polynomials and gaussians*