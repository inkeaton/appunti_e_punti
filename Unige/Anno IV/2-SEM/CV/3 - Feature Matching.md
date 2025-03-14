+ An important objective of Computer Vision is **Image Matching**, i.e. estimating the **similarity** between two images
+ This can be approached in two ways:
	+ **Global** Matching: Create a global descriptor and compare
	+ **Local** Matching: Extract local features (dense or sparse) and compare
+ We begin by considering **local matching**, namely matching consistent elements in different images
+ The pipeline works as follows:
	+ Feature **Detection**: Find interest points on each image
	+ Feature **Description**: Compute a vector description for each point 
	+ Feature **Matching**: Match the descriptions
+ Translations and rotations can be easy to approach, while changes of perspective and illumination are much harder
+ Our first approach will be:
	+ Detect **corners**
	+ Describe them with **patches**
+ This is simple, but not applicable in more difficult cases
+ We'll have to use **SIFT**s (Scale Invariant Feature Transforms, like blob-like features
---
+ An important tool for feature detection is **Multi-Scale Representation**:
	+ Related to the Image Pyramid, the basic idea is to work on a bunch of copies of our image, all of them **smoothed by a different amount**
	+ Each **feature** will be **more noticeable** on **one** of the levels
+ In the case of **blob-like features**, we can detect them using the **Image-Laplacian**, after smoothing the image
	+ Via the properties of convolution, we can **precompute** the **Laplacian of Gaussian** $\triangledown^2 G$(LoG) and directly use that
+ This function gives us a map where the extreme points correspond to blobs
+ This method was consider **not too efficient**
+ Using it as a basis, the **Difference of Gaussians** (DoG) method was created, on tthe basis of the following approximation:$$\triangledown^2G \approx G(., K \sigma) - G(., \sigma)$$
+ We build a multi scale representation of the image, where each of them is **smoothed** of a different amount. Then, we compute the difference of the pairs.
+ The final maps are approximations of the Laplacian applied to the image. To detect a **blob**, we need to look in both the specific map and the two adjacent (scale-space neighbourhood)
+ The amount of smoothing in which the feature is found is an encoding of the correct scale of the blob
+ This method is quite good also because it requires of us only the first derivative
---
+ After detecting those feature we need to know **how to describe them**
+ Assuming we have found a point $p_i$ an idea could be using **SIFT**
	+ We could consider the neighborhood of the point, 4x4 cells of size 4x4 pixels
	+ For each cell we build an orientation histogram, in which we memorize the gradient orientation of the pixels
	+ We concatenate the results in a single histogram
+ This result is quite robust, and it is able to **withstand rotation**
---
+ Now we need to **match** the **features** wee just described
+ We take a look at a brute-force approach:
	+ We decide a method to compute similarities (Euclidean Distance, SSDs, etc)
	+ We create an affinity matrix between the features of the two images, where each cell tells us the similarity between the two features
	+ Then we look for the maximum of each row, and we see if it is so, and if the matrix value is above a threshold, a match is detected that case, a match is detected