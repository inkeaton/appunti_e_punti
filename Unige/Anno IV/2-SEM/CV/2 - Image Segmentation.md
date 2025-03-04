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