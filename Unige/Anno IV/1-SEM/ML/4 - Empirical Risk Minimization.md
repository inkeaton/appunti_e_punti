+ As we saw, $KNN$ is an algorithm which works **locally**: assumes that near inputs behave similarly, and adjust the new ones based on that
+ It works extremely well in cases in which we have numerous inputs, and as such we can use a big $k$ and average more
+ But what should we so if we have fewer points? We need a more fitting function than the one $KNN$ can give us
+ The solution is to **look globally**
---
+ Given a set of points, what is the immediate function which comes to mind?
+ Simple, a **line** $wx + b$
+ In particular, the one which has an average lesser error, namely: $$\hat{L}(w) = \frac{1}{n} \sum^{n}_{i=1} [(wx + b) - y_i]^2$$
	+ **Least Square Minimization**
+ This is the **empirical loss function**
+ How do we find the one with the lesser value?
---
+  Let's start by finding $w$
+ We can find the minimal value by computing the **derivative**, and putting it equal to 0:$$\begin{align}\frac{d \hat{L}(w)}{dw} = \frac{2}{n} \sum^{n}_{i=1} x_i(wx_i + b) - y_i &= 0 \\ [\sum^{n}_{i=1} x_i^2] \hat{w} &= \sum^{n}_{i=1} x_i y_i\end{align}$$
+ To find $w$, we just **divide** the two numbers
+ In a **multidimensional** space, we'll need to do a **gradient** (*more computation details in notes*):$$\begin{align} \triangledown \hat{L}(w) = \frac{2}{n} \sum^{n}_{i=1} x_i(w^T x_i - y_i) &= 0 \\ \sum^{n}_{i = 1} (x_i x_i^T)\hat{w} &= \sum^{n}_{i=1} x_i y_i \\ \hat{C} \hat{w} &= \hat{h}\end{align}$$
+ Here the **vectors** used **complicate** a bit the situation: We need to solve a **linear system**. 
+ To do so, $\hat{C}$ must be invertible
+ Is it, tho?
---
+ If we remember: $$\begin{align}\hat{L}(w) &= \frac{1}{n} \sum^{n}_{i=1} [(wx + b) - y_i]^2 = \\ &= \frac{1}{n} || \hat{X}w - \hat{Y} ||^2\end{align}$$
+ So, let's consider the analogue, simpler system: $$\hat{X}w = \hat{Y}$$
---
+ Consider the input $X$, which is $n \times d$ 
	+ If $n > d$, the solution is impossible to find. We have **too many constraints.**
		+ In this case we have an **over-determined** or **under-parameterized** model
	+ If $n < d$, the  space of the solution is superior to the constraints. as such, we have **multiple solutions**
		+ In this case we have an **under-determined** or **over-parameterized** model
+ This last case can seem interesting, but it is in fact a problem
+ If we consider $\hat{C} = \hat{X}^T\hat{X}$, its rank varies depending on the previous value
	+ If $n > d$, the rank is $d$. 
		+ Good, $\hat{C}$ is invertible
	+ If $n < d$, the rank is $n$. 
		+ Bad, $\hat{C}$ is not invertible, and as such we can't solve the previous system
---
+ The solution comes from **changing the problem**: $$\hat{L}_\lambda(w) = \frac{1}{n} \sum^{n}_{i=1} [(wx + b) - y_i]^2 + \lambda ||w||^2$$
+ $\lambda$ is a **free** parameter
+ So, we compute the gradient and obtain the following: $$(\hat{C} + \lambda I) w = \hat{h}$$
+ To find $\hat{w}$, we need to compute: $$\hat{w} = (\hat{C} + \lambda I)^{-1}\hat{h}$$
+ What did we **gain** from this?
	1. We can imagine $\hat{L}(w)$ as a **flat parabola**, with multiple minimizer points. $\lambda||w||^2$ is a sharp parabola, depending on the value of $\lambda$. By summing it to $\hat{L}(w)$, we **reduce the number of solutions**!
	2. By choosing the right $\lambda$, we can make the matrix **invertible**, and as such solvable: $$\begin{align}
			\hat{C}^{-1} &\to (\hat{C} + \lambda I)^{-1} \\
				\begin{bmatrix}
					\frac{1}{\sigma_1} & \cdots & 0 \\
					\vdots & \ddots & \vdots \\
					0 & \cdots & \frac{1}{\sigma_d}
				\end{bmatrix}
				&\to
				\begin{bmatrix}
					\frac{1}{\sigma_1 + \lambda} & \cdots & 0 \\
					\vdots & \ddots & \vdots \\
					0 & \cdots & \frac{1}{\sigma_d + \lambda}
				\end{bmatrix}
		   \end{align}$$ We can choose $\lambda$ depending on the **eigenvalues**, to correct them.
+ To do this last part, we need to have a diagonal matrix. While this is not always true, the matrices we work with are always **diagonalizable** (We could use $SVD$)
+ How do we choose $\lambda$? same as we chose $k$: **cross-validation**!