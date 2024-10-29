+ A **Linear Time Invariant System** is defined by a black-box function $L$ defined as follows:
	+ $L(f_i(t)) = f_o(t)$
+ The function can be described by using $L(\delta(t)) = h(t)$, the **impulse-response**.
	+ In fact, $H(t)$ describes how the transformation works on all the different frequencies (derives from $\Delta(\omega) =1$)
+ As such, we can also compute the function $L$ as a **convolution**:
	+ $f_o(t) = \int^{+\infty}_{-\infty} h(t-s) f_i(s) ds$
+ And as such, it derives the following in **Fourier** space:
	+ $F_o(\omega) = H(\omega)F_i(\omega)$
---
+ The function has the following properties:
	+ **Linearity**
		+ $L(a\cdot f_i(t) + b\cdot g_i(t)) = a\cdot f_o(t) + b\cdot g_o(t)$
	+ **Time Invariance**
		+ $L(f_i(t + s)) = f_o(t + s)$
			+ The output inherits the delay
	+ **Stability**
		+ Let's assume $|f_i(t)| \leq M$
		+ Then, $|f_o(t)| \leq MI$, where $I = \int^{+\infty}_{-\infty} |h(t)| dt$
			+ A banded input has a banded output
	+ **Causality**
		+ Causality is the property for which the output is produced only depending on the input received (we can't predict the future)
		+ A **function** is said to be **causal** if $f(t) = 0 \qquad \forall t<0$
		+ A **LTI** system is said to be **causal** if $f_i(t) = 0 \qquad \forall t<t_0 \to f_o(t) = 0 \qquad \forall t<t_0$
		+ A **LTI** system is said to be **causal** also if the function $h(t)$ is **causal**
---
+ One last property is that **sinusoids** are **eigenfunctions** of LTI systems. Their output is always a sinusoid with possibly a different phase and band
	+ $L(e^{i \omega_0 t}) \to f_0(0) e^{i \omega_0 t} = H(\omega_0) e^{i \omega_0 t}$
+ The complex constant $f_0(0)$ is equal to $H(\omega_0)$, which is equal to how the frequency $\omega_0$ is modified by the transformation
+ In the notes (*23/10/24*), the professor shows an **example** of a LTI system: An **electric circuit**!
+ It is also a first example of a **filter**