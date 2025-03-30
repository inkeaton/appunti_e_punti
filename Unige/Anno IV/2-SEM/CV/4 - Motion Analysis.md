+ What do we gain if we analyse **videos** instead than images?
+ We assume we are observing a scene with one camera acquiring a set of images “close in time”
+ The result is an **image sequence**, a **series** of N images, or **frames**, acquired at **small, discrete, time instants** $$t_k = t_0 + k \Delta t$$
	+ We'll assume constant illumination during the recording (**Brightness Constancy assumption**)
+ There are various types of problems we may want to tackle:
	+ **Correspondence**: which elements of a frame correspond to which elements of the next frame?
		+ "A simplified image matching problem"
	+ **Reconstruction**: what was the 3D position and 3D velocity of the observed elements?
	+ **Motion Segmentation**: what regions of the image plane correspond to different moving parts?
		+ In the case the camera is still, motion segmentation is called **Change Detection**
	+ **Tracking**: Estimate the (2D or even 3D) trajectories of points or objects from image sequences (Kalman style :)
## Motion Segmentation
### Change Detection
+ What's the **simplest idea** we can come up with?
	+ Given two consecutive images, we compute a **binary map** where each pixel has value 1 if the corresponding pixel in the two images is different
+ This idea, while already effective, does **not account** for **noise**. 
+ We can use a **threshold**, to determine "how different" must two pixels be to detect a change
+ Still, this method **does not account for moving patches**. This determines **artifacts** in the reconstruction
+ We could consider a reference image of the **background** to determine what changed between the frames
+ Still, it is possible for the **background** to **change** overtime, so we **need** to **update** it somehow
+ There are multiple ways to do so, but we'll see the **most versatile**, **Running Average**
	+ We compute the first reference image $B$ as an average of the first $N$ frames
	+ At each frame, we:
		+ **Detect** changes $$M_t(x, y) = \begin{cases}
1 & \text{if } |I_t(x, y) - B_{t-1}(x, y)| > \tau \\ 0 & \text{otherwise}
\end{cases}$$
		+ **Update** the background $$B_t(x, y) = \begin{cases}
B_{t-1}(x, y) & \text{if } |I_t(x, y) - B_{t-1}(x, y)| > \tau \\ (1-\alpha)B_{t-1}(x, y) + \alpha I_t(x, y) &\text{otherwise}
\end{cases}$$
+ We update each frame if there were no significant changes
+ $\alpha$ will determine how much does the update weigh
+ **Pros**
	+ It is quite robust to moving objects in the scene
	+ It incorporates smooth stable changes (at a speed which is proportional to $\alpha$)
	+ It is simple and computationally efficient
+ **Cons**
	+ It does not deal with repetitive (and uninteresting) motion
+ It can be **improved** by **considering multiple frames** in the update when determining changes 
### General Case
+ We now assume our **camera** to be **moving**
+ As such, every pixel will change between every frame
+ A first idea could be to use **image matching methods**, since we can imagine that the changed pixels will keep descriptors, and would simply be moved by a small amount
+ We'll **not consider** this method
+ Instead, we'll see a method which employs **derivatives**, both in space and time
+ Our objective will be to estimate the **apparent motion** of the pixels (**Optical Flow**)
+ Let's consider the the image brightness constancy equation: $$I(x, y, t) = I(x+u, y+v, t+1)$$
+ Using a **Taylor approximation**, we can transform it in: $$\frac{\partial I}{\partial x} u + \frac{\partial I}{\partial y} v + I_t = 0$$
+ This can be rewritten as: $$(\nabla I)^T \;\overset{\rightarrow}{u} + I_t = 0$$
+ This is a **linear equation**, which we could solve to find $u$ and $v$!
+ But this is **not enough**! We just have **one** constraint for two unknowns
+ We need to somehow add more constraints
+ One approach (**Lucas-Kanade Algorithm**) **assumes** $\overset{\rightarrow}{u}$ to be constant in a small **neighbourhood** of the point we're evaluating
+ So, if we were to consider all of the points of this neighbourhood at the same time, we'd obtain a system of equations with one equation for each point in the neighbourhood, more than enough to solve for $\overset{\rightarrow}{u}$! $$\begin{align} A \;\overset{\rightarrow}{u} &= b \\ \\\text{where } A = \begin{bmatrix} \nabla I(x_1, t)^T \\ \vdots \\ \nabla I(x_m, t)^T \end{bmatrix} & \text{and} \;  b = \begin{bmatrix} -I_t(x_1, t) \\ \vdots \\ -I_t(x_m, t) \end{bmatrix}  \end{align}$$
+ We can solve with the **pseudo-inverse**, but $AA^T$ will be full rank only on the **corners** of the image, points which are not subject to the aperture problem
+ Often the algorithm is just applied to those points
### Fast Movements
+ All of the **temporal-derivative** based algorithms are **not meant for fast movement** (Lucas-Kanade included)
+ A disingenuous solution would be to simply increase the size of the patches, but this would also increase ambiguity
+ A better solution is given by **Multi-Resolution Lucas-Kanade**:
	+ Given two frames, we build a pyramid for each of them, composed of smoothed and sub-sampled versions of the frames
	+ We start from the bottom and apply LK, getting the coarsest estimation possible
	+ We upsample the result to the next level
	+ We build a warped version of the first frame of that level (We move the pixels by the amount estimated from the previous gradient, with the help of some interpolation)
	+ We apply LK to the warp and the latter frame, obtaining a correction
	+ We update LK's estimation for this layer by adding the correction
	+ Repeat for each layer
+ It's like if we **searched** each time for the **right level** to detect the movement
## Reconstruction
+ When creating a **2D** image, we necessarily **lose information** about the **3D** space we are capturing, most importantly **depth**
+ This is a **perspective projection**
+ Also our brain encounters a similar problem. But in this case, we do not consider just a image, but two: the two slightly different perspectives captured by our eyes
+ This is called **stereopsis** or stereo vision, the problem of inferring 3D information (structure and distances) from two or more images taken from different viewpoints
+ In the special case of a fixation point at infinity, given two coplanar views, the **depth**  $Z$ of an object can be computed as: $$Z = \frac{fT}{x_r - x_l} = \frac{\overbracket{f}^{\text{focal length }}\overbracket{T}^{\text{baseline}}}{\underbracket{d}_{\text{disparity}}}$$
+ This case can be can be **generalized** quite easily
+ So, in stereopsis, we we work as follows:
	1. We find **corresponding elements** between images
	2. We **reconstruct** the environment using **triangulation**
### Correspondence Problem
+ The correspondence problem involves two decisions:
	+ Which image elements to match
	+ Which feature description + similarity measure to adopt
+ A method can be computing a **disparity map**, giving the relative displacement for each pixel.
+ The algorithm we'll see will require the two images to be **rectified**, namely that corresponding point are on the same line
	+ While not always true, there exist multiple methods to rectify images algorithmically, and as such it is an **acceptable requirement**
+ A **simple first algorithm** is the following:
	+ Given two images, we choose a size of neighbourhood
	+ For each pixel of the first image and each value of disparity $d$ we estimate the similarity between the pixel's neighbourhood and the corresponding neighbourhood moved by $d$ in the other image
	+ After computing all disparities, we choose the one with higher similarity as the best possible correspondence for that pixel
+ This **will not work well** in a **dense** scenario: correspondences are made more difficult by occlusions (points with no counterpart on the other image)
+ Some solutions can be working on corners on using some priors
+ Anothyer is **Left-Right consistency** (*look for it in slides...*)