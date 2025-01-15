+ Let's imagine that we want to solve a **binary classification problem**.
+ We can use the same techniques we saw for RLS, but we need to change the loss function in something different
+ Using -1 and 1 as labels, we can exploit the sign of the product to determine the correctness of the prediction
+ We will use the **Logistic/Cross Entropy Loss**: $$l(f(x), y) = \log{(1 + e^{-y f(x)})}$$
+ As before, we'd like to minimize its value, computing the gradient
+ The gradient is as follows: $$\bigtriangledown (\hat{\varepsilon}(w) + \lambda ||w||^2) = \frac{1}{n} \sum^n_{i=1} - \cfrac{y_i x_i}{1 + e^{y_i w^T x_i}} + 2 \lambda w$$
+ This gradient is not linear in $w$, this means we can't solve and find $w$ with an equation!
+ We'll have to use the **Gradient Descent** method: $$w_0 = 0, \qquad w_{t+1} = w_t - \gamma_t \bigtriangledown (\hat{\varepsilon}(w_t) + \lambda ||w_t||^2)$$
+ This is an **iterative method**, with each iteration we get closer and closer to the optimal solution
---
+ The gradient descent method can be costly
+ Another solution is the **Stochastic Gradient Descent** method:
	+ As before, but we compute the gradient only on $b$ samples
	+ This way we reduce the computation costs. The convergence will be noisier, but comparatively quicker 
+ *6/11/24 for details, search fro Support Vector Machines*
+ 