+ There are multiple ways to create a shape on a computer:
	+ **Acquiring** it form a real world object, through discrete sampling
	+ **Modeling** it **manually**
	+ **Modeling** it **procedurally** via an algorithm
+ Either way, we need a representation to store those shapes
+ Its properties (Editability, Renderization, etc.) depend from what we want to do with it
+ The two main ways to represent an object are:
	+ Through the **space** it occupies
	+ Through its **surface**
+ Each approach has pros and cons
---
+ When we acquire real world object, we scan **points**, a set of 3d tuples, which usually **also** store **normal** and **curvature**
+ Those are quite annoying to work with, so often they are converted to meshes or other representations
+ This because **neighbourhood information is essential** , and an unordered set is not ideal 
---
+ **Parametric representations** are functions $f : \mathbb{R}^m \to \mathbb{R}^n$ where usually $m < n$
+ examples are:
	+ **Planar Curve** $\quad s(t) = (x(t), y(t))$
	+ **Space Curve** $\quad s(t) = (x(t), y(t), z(t))$
	+ **3D Surface** $\quad s(u, v) = (x(u, v), y(u, v), z(u, v))$
	+ **Explicit Circle** $\quad s(t) = r(\cos(t), \sin(t))$
	+ **Bezier Curves**
	+ **Splines**
+ **Pros**:
	+ Easy to generate points on the curve/surface
	+ Separates x/y/z components
+ **Cons**:
	+ Hard to tell inside/outside
	+ Hard to tell if a point is on the curve/surface
	+ Hard to join patches at boundaries that match exactly
---
+ Another method are **Implicit Curves and Surfaces**
+ Those are defined as the **kernel of an implicit function**, the locus of the points of the solution of an equation
+ They enable determining **inside** and **outside** of a shape
+ The normal direction to the surface (curve) is given by the gradient of the implicit function
+ This approach is limited sadly. We can't represent shapes too complicated.
+ An improvement is given by combining multiple shapes using **boolean operators** like union, intersection, difference, etc
+ The result can be smoothed using **smooth blending**, which "interpolates" between the two shapes
+ Writing the shapes in exponential format, we can use the previous operations to create meta-balls or **blobs** (*look more into this*)
	+  A rather old method, presented in 1982
+ **Pros**:
	+ Easy to determine inside/outside/boundary
+ **Cons**:
	+ Hard to generate points on the curve/surface
	+ Does not lend itself to (real-time) rendering