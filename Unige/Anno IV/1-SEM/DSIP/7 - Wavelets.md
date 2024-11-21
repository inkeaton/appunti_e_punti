+ The **Wavelet Transform** is an alternative transform of a signal, commonly used in the **image** world, which has some local properties
+ The base algorithm is simple:
	+ Let's take a signal of $2^N$ samples
	+ Let's compute the average of couples of numbers. We get a new signal of $2^{n-1}$ samples
	+ Let's compute the difference between the average and its original values. We get another vector, $2^{N-1}$ long, called the **details** vector
	+ We can repeat this until we remain with one value and $N$ details vectors
	+ Using the details, we can return to the original signal, without any loss
---
+ There is another way of viewing the same process
+ We take the following functions: $$ \underbracket{\phi(x) = 
\begin{cases}
1 \quad 0 \leq x < 1 \\ 0 \quad\text{otherwise} \end{cases}}_{\text{father wavelet}} \qquad \underbracket{\psi(x) = \begin{cases}1 \qquad 0 \leq x < \frac{1}{2} \\ -1 \quad \frac{1}{2} \leq x < 1 \\ 0 \qquad \text{otherwise}
\end{cases}}_{\text{mother wavelet}}$$
+ From them, we define: $$\hat{\phi}_i^j = 2^{\frac{j}{2}} \phi(2^jx-i) \qquad \hat{\psi}_i^j = 2^{\frac{j}{2}} \psi(2^jx-i) $$
+ These functions are all **orthogonal** and **normal**. Groups of them can be used as a base to project the signals onto (*Pitagora proof in the notes*)
+ Now, let's consider: $$\phi^j = \left[ \phi^j_0, \phi^j_1, \cdots, \phi^j_{2^j -1}\right] \qquad \psi^j = \left[ \psi^j_0, \psi^j_1, \cdots, \psi^j_{2^{j-1} -1}\right]$$
	+ They're **row** vectors
+ We define $P^j$ and $Q^j$ such that: $$\phi^{j-1} = \phi^j P^J \qquad \psi^{j-1} = \phi^j Q^J$$
+ Now we consider
	+ $C^J$ the vector containing the **averages** at the $J^{th}$ scale
	+ $D^J$ the vector containing the **details** at the $J^{th}$ scale
+ We obtain: $$C^j = P^J C^{J-1} + Q^J D^{J-1}$$
+ This is our formula for **reconstructing** our signal! (synthesis filter)
	+ We can also write it as: $$C^J = \begin{bmatrix}P^J | Q^J\end{bmatrix} \begin{bmatrix}C^{J-1} \\ D^{J-1}\end{bmatrix} $$
+ For **compressing** (analysis filter), we do instead:$$\begin{align} C^{j-1} = A^J C^J\\ D^{j-1} = B^J C^J\end{align}$$
+ Where: $$A^J = \frac{1}{2}(P^J)^T \qquad B^J = \frac{1}{2}(Q^J)^T$$
	+ As before, we can write: $$\begin{bmatrix}A^J \\ B^J\end{bmatrix} = \begin{bmatrix}P^J | Q^J\end{bmatrix}^T$$
	+ The final result of the Wavelet transform is the following: **We can decompose a signal in the sum of some orthogonal components**