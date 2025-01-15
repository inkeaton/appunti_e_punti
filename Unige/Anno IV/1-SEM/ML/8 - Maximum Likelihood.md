 #25/11/24 #27/11/24
 
+ Let's change for a bit our point of view
+ We've always assumed a **Frequentist** point of view on our probabilities, as "random", unknowable values
+ We switch to the **Probabilistic** (Bayesian) approach.
	+ We assume our data to be generated from a parameterized Probability $P_{\theta}$
	+ We what to find the best possible values for $\theta$, computing its **Maximum Likelihood Estimation** (MLE)
+ *In the notes, we show how to do so for KNN, RLS, LR, and we see that we come up to similar solutions to the original approach (27/11/24)*
---
+ Can we implement **regularization** in this system?
+ Yes!
	+ Let's assume our parameter $\theta$ is generated from another distribution, that we call **Prior** $\Pi$, which is centered on the true $\theta$
	+ The variance $\sigma$ of $\Pi$ will determine how often we get the true value of $\theta$
	+ $\Pi$ is an hyper-parameter
+ *Missing stuff on using Bayes to define Maximum At Posteriori (MAP), Somayeh sent you notes*