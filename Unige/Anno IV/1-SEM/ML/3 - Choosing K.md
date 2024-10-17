+ Returning on the KNN algorithm, how do we find the ideal value of $k$?
+ A simple idea is the **Hold Out Cross Validation**:
	+ We split the given set in two, training and **validation** set. The function will be constructed using the first, and tested for accuracy on the second. Th value of $k$ will be chosen on whatever one is more accurate to the actual values
+ How should we choose the values?
	+ We should take them **randomly**, to avoid problems derived from the vicinity of sequential points
+ Which ratio should we use for splitting?
	+ The percentage $\pi$ of training set should be always superior to 50%. The exact value depends on the quantity of data that we have
	+ On smaller datasets, often is useful to put almost alla data in the training set (**Leave-One-Out**)
		+ This method is the most precise, but the most expansive and less scalable
+ An idea is to repeat the sampling **multiple $q$ times** on different training subsets
+ We will get various values of $k$. How do we combine them?
	+ We choose the $k$ with the **best performance on every subset**:
		+ $\hat{k} = \arg_k \min (\text{avg}_{n = 1, \cdots, q} (\varepsilon_{v, n}(k)))$
+ How do we find the optimal number of repetition?
	+ We continue to cycle until the value of $k$ stabilizes
---
+ To avoid to choose random values for every split, we could just take another section of the same randomly sorted array (**Q-fold**)
---
+ Is there a way to scale the value of $k$ as new values are added to the training set?
---
+ Let's now consider how good can the optimal $k$ be
+ Such $k$ would be:
	+ $k^* = \arg \min_{k = 1, \cdots, n} \varepsilon(\hat{f}_k)$
	+ $x_i \approx P_x$
	+ $y_i = f^* (x_i) + \delta_i$
		+ $\delta_i \approx N(0, \sigma^2)$
+ The values obtained are noisy, perturbed from a Gaussian of variance $\sigma^2$ 
+ Let's now assume a case in which the noise is 0. The values obtained are:
	+ $f_k(x) = \frac{1}{k} \sum_{i \in I_{x, k}} f^*(x_i)$
+ Let's compare it to the perfect function:
	+ $|f_k(x) - f^*(x)|^2 = L^* (\cfrac{k}{n})^{\frac{1}{q}} \qquad \text{(algorithm bias)}$
		+ In which $L^*$ is the biggest difference between points (biggest derivative)
+ This means that:
	+ As we **average more** and k grows, the **error grows**.
	+ As the **data size increases**, the **error decreases**
		+ A good ratio between $k$ and $n$ would be useful
	+ As the **repetitions increase**, the **error decreases**
	+ Still, if our function is too complex, we can't do much
+ Similarly, let's consider the difference with the noisy version
	+ $\hat{f_k}(x) = \frac{1}{k} \sum_{i \in I_{x, k}} y_i$
	+ $\mathbb{E} |\hat{f_k}(x) - f_k(x)|^2 \leq \cfrac{\sigma^2}{k}$
+ So, in the case in which **there is noise**, we want a **bigger $k$**
+ We want to find the point in which the ideal value of $k$ fo the previous errors converges
+ So, we want to put them as equal (derives from using derivatives)
+ We get:
	+ $k^* = (\cfrac{\sigma^2}{L^*}n^{\frac{1}{q}})^{\frac{d}{d+1}}$
+ We see that also the **dimensionality** of the data matters!
	+ (*more details on computations on notes - 16/10/24*)