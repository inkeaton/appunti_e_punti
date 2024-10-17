+ We'll start talking about **sampling**
+ We start by defining the **train of impulses**
	+ $i(t) = \sum^{+\infty}_{n = -\infty} \delta(t -nt_s)$
+ It'a a periodic distribution, of period $t_s$
+ As such, we could compute it's **Fourier series**:
	+ $\omega_s = \cfrac{2 \pi}{t_s}$
	+ $i(t) = \sum^{+\infty}_{n = -\infty} c_n e^{int\omega_s}$
	+ $c_n = \frac{1}{t_s} \int^{+\frac{t_s}{2}}_{- \frac{t_s}{2}} \delta(t) e^{-int\omega_s} dt= \cfrac{1}{t_s}$
+ So:
	+ $i(t) = \frac{1}{t_s}\sum^{+\infty}_{n = -\infty}e^{int\omega_s}$
+ Now, we compute the **Fourier transform**:
	+ $I(\omega) = \frac{1}{t_s} \int^{+\infty}_{- \infty} i(t) e^{-i\omega t} dt$
+ By plugging the previous result, we get:
	+ $I(\omega) = \frac{2 \pi}{t_s} \sum^{+\infty}_{n = -\infty} \delta(\omega - n \omega_s)$
+ It is another train of impulses! It's an **eigenfunction**
+ It is just stretched/shrinked
---
+ Now, we can sample
+ Given the signal $s(t)$, we can compute:
	+ $s_{samp}(t) = i(t) s(t) = \begin{cases} s(t) \quad \text{if } t = t_n \\ 0 \quad \text{else} \end{cases}$
	+ $t_n = t-nt_s$
+ Its Fourier transform is very interesting:
	+ $S_{samp} = \frac{1}{2\pi}(S*I)(\omega) = \frac{\omega_s}{2 \pi} \sum^{+\infty}_{n = -\infty} s(\omega - n\omega_s)$
+ The transform consists in a **superposition of copies** of the original transform, each translated of $n \omega$ and of period $\frac{1}{t_s}$
+ This generates a problem: if the copies of the transform overlap, they would sum. So, we'd increase the coefficients of unneeded frequencies. This generates the problem known as **aliasing**
+ This can be solved by **limiting** the number of **frequencies** considered and using as sampling **interval** a value equal or inferior to $t_s = \frac{2\pi}{\omega_s} = \frac{\pi}{\omega_b}$
+ If done like that, it is possible to reconstruct exactly the same function (**Nyquist–Shannon sampling theorem**)
	+ (*The specific formula is listed in the notes (16/10/24), but it is rarely used*)