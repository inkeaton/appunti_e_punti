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