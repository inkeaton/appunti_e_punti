+ Let's focus on an improper class of functions, the **Singular Functions**
+ This class is composed **not** of **functions**, **but** of **distributions**, which we consider like functions since it helps with some computations.
+ We'll see two functions:
	+ $\delta(t) = \begin{cases} 0 \quad &t \neq 0 \\ 1 \quad &t = 0\end{cases}$        **Unit Pulse** (Dirac's delta)
		+ Works kinda like Kronecker's in the continuum
	+ $U(t) = \begin{cases} 0 \quad &t < 0 \\ 1 \quad &t \geq 0\end{cases}$       **Unit Step**
+ If we compute the product of them with a generic $\phi(t)$ we see:
	+ $\int^{+ \infty}_{ - \infty} \delta(t) \phi(t-t_0) dt = \phi(t_0)$
		+ We can use this as a function of functions $N_\delta(\phi)$ to **sample** $\phi$ in $t_0$ 
	+ $\int^{+ \infty}_{ - \infty} U(t) \phi(t) dt = \int^{+ \infty}_{0} \phi(t) dt$
		+ Associates $\phi$ to its integral in the positive reals
+ Those functions are **linear**:
	+ $\int^{+ \infty}_{ - \infty} \delta(t) \cdot (a\phi_2(t) + b\phi_2(t)) dt = a\phi_2(0) + b\phi_2(0)$
+ Also, they can be freely shifted
+ Also, the two are **related** as follows:
	+ $\cfrac{d U(t)}{dt} = \delta(t)$
---
+ Those improper functions are obtained using models
+ We'll see three models:
### Rectangle
+ Let's take the following function:
	+ $P_T(t) = \begin{cases} 1 \quad &-T \leq t \leq T \\ 0 \quad &\text{otherwise}\end{cases}$    
+ This function creates a **rectangle**, of area $2T$
+ Let's now consider:
	+ $r_T(t) = \cfrac{P_T(t)}{2T}$
+ This function creates a rectangle of **area $1$**
+ The base and height of the rectangle vary in order to maintain the area.
+ As such, as $T$, the base, decreases, the height increases.
+ So, we get the following:
	+ $\lim_{T\to 0} r_T(t) = \delta(t)$
	+ The rectangle in $\delta$ has a "height" of infinite magnitude, and no base
+ We found a first way to model $\delta$ !
### Gaussian
+ Let's consider the **unit norm** Gaussian:
	+ $g_{\sigma}(t) = \cfrac{1}{\sqrt{2 \pi} \sigma} e^{-\frac{t^2}{2\sigma^2}}$
+ The function has **area equal to 1**
+ Similarly to before,  the shape varies following $\sigma$, and:
	+ $\lim_{\sigma\to 0} g_\sigma(t) = \delta(t)$
+ We found a second way to model $\delta$ !
### Sinc
+ Let's consider the following variant of the **Sinc** function:
	+ $\frac{1}{\pi} \text{sinc} \; t = \cfrac{\sin{t}}{\pi t}$
+ It is a **normalized** version
+ Let's build form it the following:
	+ $h_{\omega}(t) = \cfrac{\sin{\omega t}}{\pi t}$
+ Similarly to before, it's shape varies on the factor $\omega$
+ So, we get:
	+ $\lim_{\omega\to + \infty} h_\omega(t) = \delta(t)$
+ We found a third way to model $\delta$ !
### Illegal Integral
+ Let's consider the following integral:
	+ $\frac{1}{2 \pi}\int^{+ \infty}_{-\infty} \cos{\omega t} \;d    \omega$
+ Because of how the cosine function works, it is normally impossible to compute
+ But let's write it in a weird but useful way:
	+ $\begin{align} \frac{1}{2 \pi} \lim_{\Omega \to + \infty} \int^{+ \Omega}_{-\Omega} \cos{\omega t} \;d \omega &= \frac{1}{2 \pi} \lim_{\Omega \to + \infty} \cfrac{\sin{\omega t}}{t} |_{- \Omega}^{+ \Omega} = \\ &= \lim_{\Omega \to + \infty} \cfrac{2\sin{\Omega t}}{2 \pi t} = \\ &= \lim_{\Omega \to + \infty} \cfrac{\sin{\Omega t}}{t} = \delta(t)\end{align}$
+ We manage to compute it and model, once again, $\delta$ !