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
+ Another is **Left-Right consistency** (*look for it in slides...*)
### 3D Reconstruction
+ When we are building our reconstruction, it is important to consider two sets of hyper-parameters, which are fundamental:
	+ **Intrinsic** Parameters: Describe the translation of a point from camera to pixels
		+ $f$ Focal Length 
		+ $(s_x, s_y)$ size of a pixel in $mm$
		+ $p = (x_0, y_0)$ central point
			+ Those parameters can be know a priori or estimated by camera **calibration** procedures
			+ Using those we can compute the **unit measure translation** $$\begin{align}x_{mm} &= -(x_{pix} - x_0)s_x \\ y_{mm} &= -(y_{pix} - y_0)s_y\end{align}$$
	+ **Extrinsic** Parameters: Describe the relationship between the two cameras
		+ $R$ rotation
		+ $T$ translation
		+ Those parameters can be obtained starting from **point correspondences**
			+ Using those we can compute: $$P_r = R(P_l - T)$$
---
+ To complete our explanation, we need to explain some geometric concepts
+ **Homogeneous coordinates** are a system to represent points, vectors and planes which supports also to infinity (*More details in slides...*)
+ All elements are in equivalences classes: $$(kx, ky, k) \equiv (x, y, 1)$$
+ This system **enables** us to write some **operations** as **linear**
+ The **perspective model** becomes as follows: $$\underbracket{\begin{pmatrix} x_{2D} \\ y_{2D} \\ 1 \end{pmatrix}}_{\text{2D point}} \equiv \begin{pmatrix} fX_{3D} \\ fY_{3D} \\ Z_{3D} \end{pmatrix} = \underbracket{\begin{bmatrix}f & 0 & 0 & 0 \\ 0 & f & 0 & 0 \\ 0 & 0 & 1 & 0 \end{bmatrix}}_{\text{projection matrix M}} \underbracket{\begin{pmatrix} X_{3D} \\ Y_{3D} \\ Z_{3D} \\ 1\end{pmatrix}}_{\text{3D point}}$$
+ We can factorize $M$ in two sections, which helps us separate **intrinsic** and **extrinsic** parameters: $$ M = \text{diag}(f, f, 1) [I_{3\times3}| \overrightarrow{0}]$$
+ The same can be done for **unit measure translation**, using the operator $K$ $$\begin{align}K &= \begin{bmatrix}
-\frac{f}{s_x} & 0 & x_0 \\ 0 & -\frac{f}{s_y} & y_0 \\ 0 & 0 & 1 \end{bmatrix} [I_{3 \times 3} | \overrightarrow{T}] \\ p_{pix} &= KMP_{3D}\end{align}$$ (*This part does not coincide with the slides, to be understood...*)
### Epipolar Geometry
+ Given two observation points $O_L, O_R$, stable, and a point $P$ in the real world, we can imagine a plane, called the **epipolar plane** , which goes trough them, and as such also through $p_L, p_R$, $P$'s projections on the camera planes
+ The intersections between the camera planes and the epipolar plane are two lines called **epipolar lines**. On this lines live the **epipoles**, the intersections between the baseline and the camera planes
+ The baseline is stable, as $O_L, O_R$ do not move, while the point $P$ may move. As such, the epipolar plane is **constrained** to the baseline, and the epipoles will always be on it, and the projections $p_L, p_R$ will always be on the epilines (**Epipolar Constraint**)
+ Now, epipolar **geometry** can be **estimated**, using the fact that the vectors $L_L = \overline{O_LP}, \; L_R = L_L - T = \overline{O_RP}, \; T = \overline{O_LO_R}$ are **coplanar**, and as such $$(L_L - T)^T T \times L_L = 0$$
+ From this, we can rewrite $$\begin{align} T \times L_L &= S L_L \quad \text{where} \quad S = \begin{bmatrix} 0 & -T_3 & T_2 \\ T_3 & 0 & -T_1 \\ -T_2 & T_1 & 0 \end{bmatrix} \\ (R^TL_R)^TSL_L &= 0 \\ L_R^T\underbracket{RS}_{
\substack{\text{essential} \\ \text{matrix }E}}L_L &= 0\end{align}$$
+ Now, we can write the following $$(p_R)^TEp_L =0$$
+ This means that, **knowing** only the points (in mm), we could **compute** the **essential** matrix. And it could give us an understanding of the external parameters
+ Also, we can rewrite: $$\begin{align}(K_R^{-1} p_R^{PIX})^TE (K_Lp_L^{PIX}) &=0 \\ (p_R^{PIX})^T \underbracket{K_R^{-T}E K_L^{-1}}_{\substack{\text{fundamental} \\ \text{matrix }F}} (p_L^{PIX}) &= 0\end{align}$$
+ Using $F$, we can start directly from the points in **pixel form**
+ It is also a map between points and their epipolar lines $$l' = Fp^{PIX}$$
	+ Using $F$, we can estimate the epipoles, and the position of the cameras
+ Sadly, there's **no** way to **factorize** $F$ to find $E$
+ Still, we can compute it starting from the points we have, using the **eight points algorithm**:
	+ Given at least 8 point couples, we can write a linear system, in which each equation is composed of pieces of the points ($A$), and the unknowns are the nine elements which compose the $F$ matrix
	+ This can be solved as any conventional system (with SVD)
+ If the points are more than 8, the system is **over-determined**. 
	+ This is often a good thing, as we must consider that we may have **noisy** correspondences. 
	+ So, we may try to approximate the problem, by **minimizing** $AF$
+ A correct $F$ matrix should have rank 2. Most probably, this matrix won't have rank 2, most likely 3
	+ To correct this, we should compute the SVD of $F$, suppress one eigenvalue out of $\Sigma$ and recompose. The obtained matrix $F'$ will have the correct rank