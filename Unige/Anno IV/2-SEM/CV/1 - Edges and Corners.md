+ A **useful kernel** for convolution is the following: $$\begin{bmatrix}
1 & -1
\end{bmatrix}$$
+ It enables us to compute a discrete **approximation** of the **derivative** of an image in the horizontal direction
	+ If we were to transpose it, we could do the same in the vertical direction
+ So these two make it possible to compute the **gradient** of the image in the various points
+ The gradient and its computable components (magnitude, orientation) are the basis for **edge detection algorithms**
+ There is a problem to be taken care of though: **Noise**
+ The presence of noise in a signal can be of great impact in this problem. The **solution** is in applying a **smoothing filter** to the image, usually a gaussian filter
+ Thanks to the properties of convolution, it is possible to **switch the order of derivation** and simply apply the **derivative of the gaussian** to the function to obtain the wanted result, removing the need to recompute each time the derivative of the signal
+ Other useful filters are Sobel's and Robert's. The first one does both smoothing and edge detection, being a combination of two filters of such kind: $$\begin{bmatrix} 1 & 0 & -1 \\ 2 & 0 & -2 \\ 1 & 0 & 1
\end{bmatrix} = \begin{bmatrix} 1 \\ 2 \\ 1
\end{bmatrix} \cdot \begin{bmatrix} 1 & 0 & -1
\end{bmatrix}$$
---
+ Another useful feature to detect are **corners**
+ Their definition is a bit different from the standard English one: they're points in which the **variation** of the signal happens in **multiple directions.** 
	+ e.g. a point is a corner
+ How do we detect them?
+ We need to consider the concept of the **Sum of Squared Distances** (SSDs)
	+ Given a point $p$ we consider their neighbourhood, the image patch $N_p$ centered in the point
	+ We can compute the **auto-correlation**(?): $$E_p(d) = \sum_{p_i \in N_p}(I(p_I) - I(p_i +d))^2$$ This tells us how much is $p$ similar to its neighbours
	+ Using Taylor's Series (and ignoring higher value derivatives, too noise-sensible) we can rewrite: $$E_p(d) \approx \sum_{p_i \in N_p} (\triangledown I(p_i) \cdot d)^2 = d^T A_c d$$ where $A_c$ is the **auto-correlation matrix**: $$\begin{bmatrix} \sum_{p_i \in N_p} I_x(p_i)^2 & \sum_{p_i \in N_p} I_x(p_i)I_y(p_i)  \\ \sum_{p_i \in N_p} I_x(p_i) I_y(p_i)  & \sum_{p_i \in N_p} I_y(p_i)^2 \end{bmatrix}$$
	+ When $A_c$ is **diagonalized**, only a corner will have **both eigenvalues not-null**. **We found a way to detect corners**!
+ This is the **Shi-Tumasi** method, and it is quite used