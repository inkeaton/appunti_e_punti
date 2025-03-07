+ Image segmentation consiste in **dividing** the image in a set of multiple, connected and non-intersecting **sub-regions**, where their members are united by common predicates
+ A simple idea is using a **threshold** to divide in two classes the objects (usually foreground and background)
+ But how do we choose a good threshold?
+ A first simple method consiste in **Global Thresholding**:
	+ Select a numerical threshold $T$
	+ Separate in two regions value inferior and superior to $T$
	+ Compute mean values in the regions
	+ Use those values to compute a new threshold and repeat,m until the sub-regions stabilize
+ This enables the computation of a good threshold
+ Another thresholding approach is the **Otsu Algorithm**, whose objective is the minimization of intra-class variance:
	+ We choose a numerical threshold $k$
	+ We separate in two regions value inferior and superior to $k$
	+ We compute the mean values for both of the regions and globally
	+ The optimal threshold $k$ is the one that maximizes: $$\sigma^2_B = P_1(M_1 - M_G) + P_2(M_2 - M_G)$$
+ **Thresholding** is **not** a **versatile** method, it can be used only when there is an actual division between values (look at the image **histogram** to check)
---
+ Another class of methods is **Unsupervised Segmentation**, in which ML's unsupervised learning methods are used to enable the segmentation
+ First of all, we need to assign **descriptive values** to our pixels
+ The ones we may have in mind are **color** and **position**
+ We may obtain a description as follows: $$x_i = (r_i, g_i, b_i, x_i, y_i)$$
	+ It's important to remember to scale accordingly the values, especially the position, in order to avoid an over-representation of single values
+ Now, we see a first method which uses **K-Means.**
+ Our goal is to maximize the between class variance, similar to before
	+ Input: An image I, K classes
	+ We initialize the centroids $C_k$
	+ We assign a centroid to each of the points as follows: $$C(x_i) = {\arg \min}_{1 \leq k \leq K} ||x_i - c_k||$$
	+ We update the centroids position
	+ Repeat the two previous steps until we reach stability
---
+ A similar problem is the computation of **super-pixels**, small sections of the image containing similar, neighbouring pixels
+ We take a look at SLIC (**Simple Linear Iterative Clustering**) an algorithm for their computation
+ It uses a similar structure. For the color of the pixels, it uses the **Lab** color standard
+ For the algorithm, we need to know how to compute distances between pixels
+ We use the following formulas: $$\begin{align}
d_{\text{Lab}} (x_i, x_j) =& \sqrt{(L_i - L_j)^2 + (a_i - a_j)^2 + (b_i - b_j)^2}\\ D(x_i, x_j) =& d_{\text{Lab}} (x_i, x_j) + \frac{m}{s} d_{\text{xy}} (x_i, x_j)\end{align}$$Where $m$ is a scaling factor, to control the effect of the Cartesian distance, and $s$ controls the average size of a super-pixel
+ Now we can explain the **algorithm**:
	+ Input: Image $I$, Size $s$
	+ We divide the input image in a grid, in which each cell is $s \times s$
	+ On each of the cells, we put a centroid
	+ We move each centroid towards the lowest gradient position of its $n \times n$ neighbourhood, in order to avoid edges and other annoying positions
	+ We initialize a label list $l(i) = -1$ and a distance list $d(i) = \infty$ for each pixel
	+ For each cluster $c_k$:
		+ We consider the $2s \times 2s$ neighbourhood
		+ We compute $D(x_i, c_k)$ for each pixel in the neighbourhood
		+ If $D$ is smaller than $d(i)$, assign $d(i) = D, \quad l(i) = k$
	+ Update Cluster's positions
	+ Repeat the two previous steps until we reach stability