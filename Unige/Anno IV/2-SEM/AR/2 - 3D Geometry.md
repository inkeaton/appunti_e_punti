+ To describe the geometry of real and virtual worlds, we must define a 3D Euclidean space, with **Cartesian coordinates**.
	+ The space can be **right** or **left** handed (varying the sign of the z axis), it changes from product to product (Unity3D is left handed)
+ Each point P in this space will be described by its Cartesian coordinates
+ We can define shapes by  a list of its vertices
---
+ Given a shape, we can perform two types of operations on it:
	+ **Translation**: the change of the origin of the object
	+ **Linear Transformations**: straight and parallel lines are preserved and there is no translation
+ A translation can be described as a **vector**, which is summed to the vertices of the objects, changing their position
+ Transformations are instead described as linear operators, **matrices**
+ Examples of transformations are:
	+ **Scaling**, which can be uniform or not uniform. An example is: $$\begin{bmatrix} k_x & 0 & 0 \\ 0 & k_y & 0 \\ 0 & 0 & k_z
\end{bmatrix}$$
	+ **Rotations** 
		+ The Euler theorem tells us that we need at least three numbers to represent an arbitrary rotation in the 3D space
		+ In order to avoid distortion, the rotation must respect the following properties:
			1. No stretching of axes
			2. No shearing
			3. No mirror images
		+  In the 2D case, these are satisfied if:
			+ The columns of M must have unit length
			+ The coordinate axes remain perpendicular 
			+ The determinant of M is positive
		+ The easiest way to describe **3D rotation** is as a **set of 2D** ones (yaw, pitch roll)
		+ It is possible to **combine rotation and translation** in a single operation, as: $$\begin{bmatrix}& R& & T \\ 0 & 0 & 0 & 1\end{bmatrix}$$
		+ In order to do this, we need to add a dimension to the coordinates, which are now called **Homogeneous Coordinates**
		+ A **Gimbal Lock** is the loss of one degree of freedom in a three dimensional space. This may happen when two of the three axis are put in parallel positions. We want to **avoid** that
		+ Another way to describe rotations is through **Quaternions**. In those we describe a rotation around a specific axis $(X, Y, Z$)