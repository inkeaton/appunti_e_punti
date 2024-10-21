+ As we saw, $KNN$ is an algorithm which works **locally**: assumes that near inputs behave similarly, and adjust the new ones based on that
+ It works extremely well in cases in which we have numerous inputs, and as such we can use a big $k$ and average more
+ But what should we so if we have fewer points? We need a more fitting function than the one $KNN$ can give us
+ The solution is to **look globally**
---
+ Given a set of points, what is the immediate function which comes to mind?
+ Simple, a **line** $wx + b$
+ In particular, the one which has an average lesser error, namely:
	+ $\hat{L}(w) = \frac{1}{n} \sum^{n}_{i=1} [(wx + b) - y_i]^2$
		+ **Least Square Minimization**
+ This is the **empirical loss function**
+ How do we find the one with the lesser value?
---
+  Let's start by finding $w$
+ We can find the minimal value by computing the **derivative**, and putting it equal to 0:
	+ $\begin{align}\frac{d \hat{L}(w)}{dw} = \frac{2}{n} \sum^{n}_{i=1} x_i(wx_i + b) - y_i &= 0 \\ [\sum^{n}_{i=1} x_i^2] \hat{w} &= \sum^{n}_{i=1} x_i y_i\end{align}$
+ To find $w$, we just **divide** the two numbers
+ In a **multidimensional** space, we'll need to do a **gradient** (*more computation details in notes*):
	+ $\begin{align} \triangledown \hat{L}(w) = \frac{2}{n} \sum^{n}_{i=1} x_i(w^T x_i - y_i) &= 0 \\ \sum^{n}_{i = 1} (x_i x_i^T)\hat{w} &= \sum^{n}_{i=1} x_i y_i \\ \hat{C} \hat{w} &= \hat{h}\end{align}$
+ Here the **vectors** used **complicate** a bit the situation: We need to solve a **linear system**. To do so, $\hat{C}$ must be invertible