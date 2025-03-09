*5/3/25*
+ **How do we store a shape**? and most importantly, **what** do we want to **store** in this shape?
	+ Geometry?
	+ Connectivity?
	+ Attributes?
+ What **operations** should be **supported**?
	+ Rendering?
	+ Geometry queries?
	+ Modifications?
+ How do we **determine** its **quality**?
	+ Time/Space complexity
	+ Redundancy
---
+ The first method we see **Triangle List**, used in the **STL** format. It's used in CAD applications
+ It's very **simple**:
	+ We have a 3-column table, in which we memorize for each row a triangle
+ It's extremely simple, and as such it is **not too useful** for more **complex** operations
	+ We have to compute connectivity information
	+ There's an incredible amount of vertex redundancy
+ Another method is the **Indexed Face Set**, used in **OBJ**, **OFF**, **WRL**
+ **Reduces redundancy**:
	+ We have two tables, one of vertices, and one of faces, which refers to the first
+ Still, we have **no neighbourhood information**
	+ Also, editing is more complex
+ The **Half-Edge** structure introduces orientation into the data. Edges are oriented
+ The information stored becomes as follows:
	+ Vertex:
		+ Position
		+ 1 outgoing half-edge (index)
	+ Half-edge
		+ 1 origin vertex index 
		+ 1 incident face index 
		+ 3 next, prev, twin half-edge indices
	+ Face
		+ 1 incident half-edge index
+ This makes it very easy to move in the structure, keeping also connectivity information
+ This structure is really **good** for geometry **queries**, **but** it has an **high space complexity**, and it **needs** to be **converted** for **rendering**, making it less preferable for real time rendering
+ In our class we will not use any of the previous structure, but a evolution of the second one, **Indexed Face Set *with Adjacencies***, used in the igl library
	+ Same basis of the indexed structure, plus each face points to its adjacent faces and each vertex points to one of its incident faces 
	+ While some information is not explicitly stored, it can be **computed** and **stored** on **request** (a lazy approach)