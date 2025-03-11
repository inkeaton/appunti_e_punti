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