+ Let's remember the components of the Fourier Series:
	+ $\psi_n (t) = \frac{1}{\sqrt{2}} e^{int}$
	+ $c_n = \frac{1}{2\pi} \int^{\pi}_{-\pi} f(t) e^{-int} dt$
	+ $f(t) = \sum^{\infty}_{-\infty} c_n e^{int}$
+ This works in a finite interval $[a, b]$. We can expand this definition in a infinite space $\mathbb{R}$,k with real valued functions
+ This is represented by $F(\omega)$, a function derived from $f(t)$, which represents the coefficient of the $\omega$ harmonic in $f$
+ We derive the following:
	+ $F(\omega) = \int^{\infty}_{-\infty} f(t) e^{-i \omega t} dt$
	+ $f(t) = \frac{1}{2\pi} \int^{\infty}_{-\infty} f(t) e^{i \omega t} dt$
+ It's important to remember that $F$ **does not have to be real**. It depends on the contents of odd harmonics in the function
---
+ Let's see some **properties**!
	+ Every function $f$ has a transform $F$. $(f, F)$ is called a **pair**
		+ An example is $(P_T, 2\;\text{sinc})$
		+ On finite signals, you just need to add a lot of 0 before and after
	+ It's **linear**: $a_1 f_1(t) + a_2 f_2(t) \leftrightarrow a_1 F_1(\omega) + a_2 F_2(\omega)$
	+ In case of a time shift, the transform varies of a **phase**: $f(t-t_0) \leftrightarrow e^{-i \omega t_0}F(\omega)$
	+ In case of a **conjugate**: $f^*(t) \leftrightarrow F^*(-\omega)$ 
	+ In case of a **derivative**: $f'(t) \leftrightarrow i\omega F'(\omega)$ 
		+ As $\omega$ increases, the height does too: higher values of higher frequencies
		+ $F'(\omega)$ must go to zero quicker than $f(\omega)$ does already
	+ In case of a **integral**: $\int^{t}_{-\infty}f(t) \leftrightarrow \cfrac{F(\omega)}{i\omega }$ 
		+ The opposite as before
---
+ The Fourier Transform can be seen as a rotation. That means that angles and norm remain the same.
+ In particular (**Plancharel's Theorem**)
	+ $\int^{\infty}_{-\infty} f(t) g^*(t) dt = \frac{1}{2 \pi} \int^{\infty}_{-\infty} F(\omega) G^*(\omega) d \omega$ 
+ It becomes:
	+ $\int^{\infty}_{-\infty} f(t)^2 dt = \frac{1}{2 \pi} \int^{\infty}_{-\infty} |F(\omega)|^2 d \omega$ 
	+ The **norm** is conserved!
---
+ Let's now see the **convolution**, a particular operation:
	+ $h(t) = (f * g) (t) = \int^{+\infty}_{-\infty} f(x) g(t-x) dx$
	+ $f$ is computed with a flipped, shifted version of $g$
+ The operation is very **computationally expansive**: We have to do an infinite amount of integrals!
+ But there is an **easier** way:
	+ $h(t) = (f * g) (t) = F(\omega)G(\omega) = H(\omega)$
	+ We just need to do two transforms, one product, and one inverse transform!
+ This will be the basis for **filters** and **linear systems**
	+ Vale anche il contrario
		+ $f(t)  g (t) = \frac{1}{2\pi}(F*G)(\omega)$
---
+ Since the transform is a linear transform, does it have a **eigenfunction**? yes!
	+ If we transform a **Gaussian** of width $\sigma$ we will get another Gaussian of width $\frac{1}{\sigma}$
	+ (*more details in notes, 15/10/24*)