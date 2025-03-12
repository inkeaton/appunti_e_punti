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
**(MISSING FINAL PART)**