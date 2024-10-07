+ We will call $S_n$ the **training set**, composed of $n$ tuples $(x_i, y_i)$, where:
	+ $x_i \in X \subseteq \mathbb{R}^d$ , l'**input**
	+ $y_i \in Y$ , l'**output**. La sua dimensione e forma varia a seconda del problema
+ Our objective is to find a function $f$ such that:
	+ $f(x_i) \approxeq y_i$ (**fitting** property)
	+ $f(x_{new}) \approxeq y_{new}$ (**generalization** property)
+ To find it, we must first assume the following statement:
	1. The set of $x_i$ has been sampled **independently and identically** by a probability distribution $P_x(x)$
	2. The pairs in $S_n$ have been sampled from a **joint probability** $P(x, y) = P_x(x) \cdot P(y | x)$
		+ Those probabilities are related to the components of a supervised learning system:
			+ **Generator**:  Generates $x_i$
			+ **Supervisor**: generates $y_i$ from $x_i$
			+ **Learning Machine**: given the pairs $(x_i, y_i)$ finds $f(x)$
+ To find $f$ we need to have a way to quantify its quality
+ That is the **loss function**, which tells how much we lose from an approximation
	+ $l(y_i, f(x_i)) \to [0, + \infty)$
	+ *Many variants are used, one popular one is the square loss*
+ Using it we can compute the **expected loss** given by a function:
	+ $\varepsilon(f) = \mathbb{E}(x) = \int_Y \int_{X} P(x, y) l(y_i, f(x_i)) dx dy$
+ As such, the **best function** $f$ is:
	+ $f^* = \arg \min_{f \in H} \varepsilon (f)$
---
+ Sadly, there are **two caveats**:
	+ We do not know the probabilities
	+ We do not have all the space for computing the integral
+ **Then**, we need to reason in **empirical terms**:
	+ $\widehat{\varepsilon(f)} = \cfrac{1}{n} \sum^{n}_{i=1} l(y_i, f(x_i))$
	+ $\hat{f} \arg \min_{f \in H} \widehat{\varepsilon (f)}$
---
+ It is important to choose wisely the size of the hypothesis space $H$ to ensure the quality of the solution:
	+ It should not be too small, causing **underfitting**
	+ It should not be too big, causing **overfitting** and instability