+ *03/03/25*
+ Polygonal meshes are **boundary representations** of objects
+ They approximate smooth surfaces in a very efficient way, the error decreases very fast as the complexity increases
+ They can describe any **shape**, with **arbitrary topology**, and support **adaptive refinement**
+ Also, they render efficiently
+ The **polygons** we use are
	+ Closed
	+ Planar
	+ Simple (No edge intersections)
+ The **mesh** itself is defined as a **set** $M$ of closed simple polygons $Q_i$
	+ Each edge belongs to a polygon
	+ Each polygon describes a face of the mesh
+ Some definitions:
	+ The **valence** of a vertex is the number of entering edges
	+ The **boundary** is the set of all edges belonging to only one face
		+ If **empty**, the mesh is said to be **watertight**
	+ A surface is a **closed 2-manifold** if it is everywhere locally **homeomorphic** to a disk
		+ A variant is the **Manifold with boundary**: a vicinity of each boundary point is homeomorphic to a half-disk
		+ In a manifold mesh, there are at most 2 faces sharing an edge
		+ If closed and not intersecting, a manifold divides the space into **interior** and **exterior** (Jordan Theorem). The manifold itself is the **boundary** of the object that occupies the interior
		+ A closed manifold polygonal mesh is called a **polyhedron**
	+ Every **face** of a polygonal mesh is **orientable**
		+ Two neighbouring faces are **consistently orientated** if shared edges have opposite orientation
		+ A polygonal **mesh** is **orientable**, if the incident faces to every edge can be **consistently oriented**
	+ The **Genus** of a shape is one half of the maximum number of **independent closed paths** that do not disconnect the graph
		+ Informally, the number of **handles** (be wary of tricky spots)
		+ A Sphere has genus 0, a Thoroid has genus 1
---
+ An important result is the **Euler-Poincarè Formula** which states:
	+ The following **sum** is **constant** for a given surface topology, no matter which (manifold) mesh we choose to cover it: $$\chi(M) = v - e + f$$For **orientable meshes** is **also** true: $$\chi(M) = 2(c-g)-b$$where:
		+ $v$: number of vertices
		+ $e$: number of edges
		+ $f$: number of faces
		+ $c$: number of connected components
		+ $g$: genus
		+ $b$: number of boundary loops
+ This has important **implications** for mesh **storage**:
	+ In a triangle mesh, the ratio of edges to faces is: $$e = \frac{3}{2}f$$
	+ Ratio of vertices to faces is: $$f \approx 2v$$
	+ Ratio of edges to vertices is: $$e \approx 3v$$
	+ Average degree of a vertex is 6
+ *5/3/25*
+ A mesh is called **Regular** if all faces have the same number of edges and all vertex degrees are equal. It si called **Quasi-Regular** if most of the faces respect the previous properties
	+ To achieve regularity, an object must be a **thoroid**
	+ A **Semi-Regular** mesh is a type of quasi regular mesh obtained through sub-division
+ A **sliver** is a triangle with highly different angles. We want to avoid them, as they create problems in computations, and a method to determine them is using inscribe and "coscribe" circles
---
+ **Triangulations** are polygonal meshes which only use triangular faces
+ Those are very **useful** for **simplifying** algorithms and computations, **but** are **rarely used** for **modeling**, as quad or superior meshes have properties like **edge loops** which are helpful for editing
+ The **quality** of those shapes depends on **different** features:
	+ Triangle meshes
		+ Uniform Area
		+ Angles close to 60
	+ Quad meshes
		+ Number of irregular vertices
		+ Angles close to 90
		+ Good edge flow