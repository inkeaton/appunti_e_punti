+ We begin talking about **unsupervised learning** and **generative models**
	+ The objective is to take as input unlabeled training samples from some distribution and learn a model that represents that distribution
+ We begin by talking about a pretty simple approach: **Autoencoders**
	+ Unsupervised approach for **learning** a **lower dimensional feature** representation of an input **from unlabeled training data**
	+ Traditionally used for dimensionality reduction and feature learning, now they are also used for generative models
+ It is composed of two sections:
	+ An **encoder** function, $h = f(x)$: it describes the lower dimensional code to represent the input
	+ A **decoder** function, r = g(h), that produces the approximate reconstruction
+ Our real **objective** is the **code**, which is codified in the **latent space**: the **reconstruction** is used only **for training**
+ The **size** of the **latent space** is related to the **quality** of the feature extraction
	+ If too big, the network will simply try to "copy" the data
	+ If instead it is relatively small, it will be forced to detect and store the most important features (**under-complete autoencoder**)
	+ It's like we were filtering the data
+ If we do not use non-linear activations and use a loss function based on MSE, the system becomes quite similar to **PCA**, with the **difference** of the latent dimensions which will **not** be necessarily **orthogonal** and will have (more or less) the same variance
+ We can also create **probabilistic autoencoders** (*look more on these*)
+ Autoencoders can also be used for **transfer learning**:
	+ We learn a representation of lots of data with an encoder
	+ We then use this representation as the starting point of a classification network 
+ *Missing part on regularized auto-encoders*
+ An evolution of the concept is the **Variational Auto-encoder** (VAE)
	+ Instead of encoding an input into a point in the latent space, a VAE encodes it as a **distribution** over the latent space.
	+ The p distributions are chosen to be normal: the encoder can learn mean and the covariance matrix
	+ This enforces a pattern into the generated data, which ensures that good properties are kept
+ The loss is evaluated with the addition of a **parameter** which describes the quality of the distributions themselves. Its impact can be controlled by adding a parameter $\beta$ and using it as a **regularizer**
---
+ An **example usage** of AEs is learning **Disentangled Representations**:
	+ Learn a representation h that separates the distinct and informative **Factors of Variations** (FoVs) in the data, so that “A change in a single underlying factor of variation leads to a change in a single factor in the learned representation”
+ This can be achieved by using $\beta$-VAEs where $\beta > 1$ 
---
+ We now take a look at **Generative Adversarial Networks** (GANs)
+ Those are networks created with the goal of **generating new data**
+ They are composed of two sections:
	+ A **generator network**, which directly produces samples
	+ Its adversary, the **discriminator network**, which attempts to distinguish between samples drawn from the training data and samples drawn from the generator, assigning likelihoods of being real
		+ It is pretty similar to an AE's Decoder
+ As the network is **trained**:
	+ The discriminator learns to become **better at** **distinguishing** real from generated images
	+ The generator learns to **generate better images** to fool the discriminator
+ **Convergence** is reached when the discriminator's accuracy starts sitting around 50%, as it **becomes unable to distinguish the two results**
+ Mathematically, the situation is **annoying**, as we have in our hands a **min-max problem** (*formula in slides*)
	+ The **Discriminator** wants D(x) = 1 and D(G(z))=0 (Wants to **maximize**)
	+ The **Generator** wants D(G(z))=1 (Wants to **minimize**)
+ We can solve it using an **alternating gradient descent method**, which is quite **slow** unfortunately 