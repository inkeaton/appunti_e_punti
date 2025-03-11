*5/3/25*
+ We'll now see the process of **acquisition** and **reconstruction** of a real object
+ The process itself is divided in multiple sections
	+ **Scanning**: Acquire multiple *range images* of the object
	+ **Registration**: Bring those images in the same 3D space
	+ **Stitching**: Integrate all of the images in a single mesh
	+ **Post-processing**: Repair and edit the final mesh as needed
---
+ There exist **numerous** **methods** for **acquisition**, the choice of one highly depends on the situation:
	+ **Touch Probes**: Used for smaller objects, quite a tedious process
		+ Precise and versatile, but limited
	+ **Optical Scanning**: Infer the geometry from light reflectance
		+ Less invasive and quite fast, but have difficulties with transparent objects
	+ **Time-of-Flight Lasers**: Uses GPS like logic for computation
		+ Useful for bigger objects, but only usable for still scenes
	+ **Triangulation Laser**: Uses a camera and a laser
		+ Very precise, but works only at small distances
	+ **Structured Light**: Computes information from the distortion of a pattern
		+ Very fast, but complex to implement, and prone to noise
	+ **Passive Stereo**: Uses two cameras, simulating the human visual system
*10/03/25*
+ *About rotation and translation, various computations...*