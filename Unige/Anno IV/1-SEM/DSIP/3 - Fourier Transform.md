+ Let's remember the components of the Fourier Series:
	+ $\psi_n (t) = \frac{1}{\sqrt{2}} e^{int}$
	+ $c_n = \frac{1}{2\pi} \int^{\pi}_{-\pi} f(t) e^{-int} dt$
	+ $f(t) = \sum^{\infty}_{-\infty} c_n e^{int}$
+ This works in a finite interval $[a, b]$. We can expand this definition in a infinite space $\mathbb{R}$,k with real valued functions
+ This is represented by $F(\omega)$, a function derived from $f(t)$, which represents the coefficient of the $\omega$ harmonic in $f$
+ We derive the following:
	+ $F(\omega) = \int^{\infty}_{-\infty} f(t) e^{-i \omega t} dt$
	+ $f(t) = \frac{1}{2\pi} \int^{\infty}_{-\infty} f(t) e^{i \omega t} dt$
+ It's important to remember that $F$ does not have to be real. It depends on the contents of odd harmonics in the function
---
+ Let's see some **properties**!
	+ Every function $f$ has a transform $F$. $(f, F)$ is called a **pair**
		+ An example is $(P_T, 2\;\text{sinc})$
	+ It's **linear**: $a_1 f_1(t) + a_2 f_2(t) \leftrightarrow a_1 F_1(\omega) + a_2 F_2(\omega)$
	+ In case of a shift, the transform varies of a **phase**: $f(t-t_0) \leftrightarrow e^{-i \omega t_0}F(\omega)$
	+ In case of a **conjugate**: $f^*(t) \leftrightarrow F^*(-\omega)$ 
---
+ The Fourier Transform can be seen as a rotation. That means that angles and norm remain the same.
+ In particular (**Blancharell's Theorem**)
	+ $\int^{\infty}_{-\infty} f(t) g^*(t) dt = \frac{1}{2 \pi} \int^{\infty}_{-\infty} F(\omega) G^*(\omega) d \omega$ 
	+ $||f||^2 = ||F||^2$