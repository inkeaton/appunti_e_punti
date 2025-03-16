+ In the **rendering** process, we obtain a 2D image from a 3D object
+ During this process, we consider lots and lots of different **reference frames** for our information
+ The **visualization pipeline** is the chain of transformations that link all of those frames
+ We consider:
	+ **Modeling Transform**
		+ We move all local objects in a shared global world, with global coordinates, using a $4 \times 4$ roto-translation
	+ **Viewing Transform**
		+ All the objects are described in the eye (camera) reference frame, using another $4 \times 4$ roto-translation
		+ The union of this and the previous transform is often called **Model-View** Transform
	+ **Projection Transform**
		+ All of the objects get described in a limited portion of space, the one in the FOV of the viewer
		+ The projection can either be **orthographic** ("straight") or **perspective** (as in the human eye). We'll use the latter
		+ It has the shape of a **Frustum** (a clipped pyramid), as an approximation of the human cone of view
		+ It follows the **pinhole camera model**
		+ The Frustum is defined by
			+ Aspect Ratio
			+ FOV Vertical Angle
			+ Near and Far clipping planes
		+ The transformation happens via a $4 \times 4$ operation: $$A = \begin{bmatrix}\frac{f}{\text{aspect ratio}} & 0 & 0 & 0 \\ 0 & f & 0 & 0 \\ 0 & 0 & \frac{\text{far} + \text{near}}{\text{near} - \text{far}} & \frac{2 \cdot \text{far} \cdot \text{near}}{\text{near} - \text{far}}\\ 0 & 0 & -1 & 0\end{bmatrix} \qquad f = \cot\left(\frac{\text{FOVy}}{2}\right)$$
	+ **Viewport Transform**
		+ The 3D space is transformed in a 2D image, defined by a viewport, a window
+ *10/03/25*
	+ *Missing some part on accommodation vergence conflict and other stuff, te be recovered*