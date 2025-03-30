+ Sometimes is very **difficult to label our data:**
	+ Doing it is time consuming
	+ Values change with time
	+ Bias is often a problem to be dealt with
+ A **solution** to deal with it is the class of **Self-Supervised Learning** approaches
+ They are part of the unsupervised approaches
+ The idea is the following:
	+ Given our data, we divide it in two different sections
	+ On the first one, we define a **pretext task**, (which is **supervised**) which forces the model to learn the most relevant features of our data. 
	+ After this training, we transfer what the model learn on one built for our **downstream task**, and train it as needed
+ This is **not that different from transfer learning**, simply we are somehow training ourselves the feature extractor
+ Examples of pretext tasks are:
	+ Autoencoders
	+ GANs
	+ Diffusion Generators
	+ Geometric Transformations
	+ Colorization
	+ Super Resolution
	+ In-painting
	+ Solving Puzzles
	+ etc.
---
+ A problem with our structure is that during the pretext task, the model learns only on **one** input object **at a time**
+ This creates the **risk of** the model **cheating**, learning less general features in order to complete the task
+ This is solved by **Self-Supervised Contrastive Learning**:
	+ Each input is an **anchor** $x$, let's say a "label"
	+ Every permutation of $x$ is a **positive** $x^+$
	+ Every other input is a **negative** $x^-$
	+ We want the **embedding** of the **anchor** to be **similar** to the one of the **positives**, and **different** from the one of the **negatives**
	+ We define a **score function** $s()$ such that: $$s(f(x), f(x^+)) >> s(f(x), f(x^-))$$
	+ And we use the **Contrastive Loss** (InfoNCE), which, given one positive and $N-1$ negative samples, can be written as: $$L = -\mathbb{E}_X \left[\log \frac{e^{(f(x), f(x^+))}}{\sum^{N}_{j = 1} e^{(f(x), f(x_j))}}\right]$$
		+ It closely **resembles** the **Soft-Max** activation function
		+ It is a lower bound on the **Mutual Information** between $f(x)$ and $f(x^+)$ $$MI(f(x), f(x^+) - \log(N) \geq -L$$
		+ From this we understand that we **want** a **lot** of **negative samples**
+ The learning itself can be implemented in multiple ways
### SimCLR
+ One is **SimCLR**:
	+ The score function is **Cosine Similarity** $$s(u, v) = \frac{u^T v}{||u||||v||}$$
	+ Once a input is embedded, it is moved in a **Projection Space** where the loss is computed, in **mini-batches**. 
	+ **Negatives** are **recycled** between batches
	+ Positive samples are generated using data-augmentation with geometric transformations
		+ During the **choice of transformation**, it is important to notice that **local** ones generate less differences between images than global, and as such are **more** **effective**
	+ During the **transfer**, the **projection** network is **discarded**, since the most relevant features are determined in the previous layer
### MoCo
+ A limitation of SimCLR is the high number of negatives and batches required
+ MoCo partly addresses these problems
	+ Given an input, we augment it
	+ The augmentation is seen as a key for a dictionary, which is composed by the original input batch and all previous batches
	+ The task is then to access the input using the augmentation as a key
+ The usage of older batches reduces the number of negatives required
+ While the augmentation is encoded normally, the dictionary is managed by a **Momentum Encoder**, which is slowly being updated in a similar manner to gradient descent by the **normal encoder**
	+ This helps with back-propagation, made more difficult by the increasing size of the dictionary
+ The main hypothesis is that good features can be learned by a large dictionary that covers a rich set of negative samples, while the encoder for the dictionary keys is kept as consistent as possible despite its evolution.
### Byol
+ This is **not** a **contrastive** method, but it is based on SimCLR and MoCo
+ Basically the input is augmented two times, and one of the augmentations becomes a label for the other one
	+ Does not use negative examples 
	+ More resilient to transformation and batch size than contrastive methods
+ BYOL achieves **higher performance** than state-of-the-art contrastive methods
---
+ It exists also a class of methods called **supervised contrastive loss**, where we know the labels, but still use a contrastive method