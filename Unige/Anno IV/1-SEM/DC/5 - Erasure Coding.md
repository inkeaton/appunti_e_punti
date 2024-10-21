+ We'll see a method to ensure the **availability** of data.
+ Let's assume we want to save our data on $N$ servers and being able to withstand the failure of $M$ servers
+ The easiest idea is to **replicate** the data. I put $N=M+1$, and copy my data non alla $N$ servers. But the **space complexity is very high**, and as such it is not very scalable as a method. We need to reduce the redundancy
---
+ If we consider $M=1$, a simple improvement is using **parity blocks**. We split our data in $K=N-1$ blocks, and we compute another block applying $XOR$ to all blocks.
+ This way, any single block we lose can be recomputed from all the remaining blocks, and we only need one ulterior $\frac{N}{K}$ block of additional space
+ But this solution **cannot go beyond one server failure**...
---
+ A more complex solution comes from **Erasure Coding**
+ The idea is encoding my data in $N$ blocks, each of size $\frac{1}{K}$th of the original data, where $K=N-M$
+ We will need only any $K$ blocks to recover the missing data
+ How does it work?
	+ The idea is to describe our data as the **coefficients** of a polynomial curve
	+ We memorize it as several points belonging to the curve
	+ Given a sufficient amount of **points** $K$, it is possible to resolve a linear system and **compute the original data**
+ There's a catch tho: If the value of the points grows too much, it is possible that they become more expansive to store than the original data
+ A solution comes from using **finite fields** as values. An example are the **Integers Modulo** A Prime Number 