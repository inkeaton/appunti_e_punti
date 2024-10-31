+ Let's imagine we want to measure something of value $s$
+ We measure and obtain $m_1 = s + r_1$. This won't be a perfect measurement
+ We could measure $t$ times and compute the average. Assuming that the noise in the values is unbiased ($\mathbb{E}[r_i] = 0$, $\mathbb{E}[r_i^2] = R$ finite ), the perturbed values will be distributed along a gaussian centered on the correct value, and as such we will compute a value $\hat{s}_t$ which as $t$ increases should get closer and closer to $s$
+ This works, but we need a simpler implementation to update easily our estimations on the increasing of $t$
+ This is the base of the **Kalman Filter**
---
+ Let's consider the following:$$\hat{s_t} = \underbracket{\hat{s}_t^-}_{\text{previous estimate}} + \underbracket{k_t}_{\text{Kalman Gain}} \cdot \underbracket{(m_t - \hat{s}_t^-)}_{\text{novelty}}$$
+ This explains how to update the value of $\hat{s}_t$ knowing the new measure and old average
+ We need to know the value of $k_t$
+ We can find it by searching the value that minimizes the MSE: $$\arg_{k_t} \min \mathbb{E}[(s - \hat{s}_t)^2] = \arg_{k_t} \min P_t$$
+ By doing some computations, we obtain the following: $$k_t = \cfrac{P_t^-}{P_t^- + R} = \frac{1}{t}$$
+ From this we obtain:$$P_t = (1 - k_t) P_t^- = \frac{R}{t}$$
+ Those make sense:
	+ As the number of measurements increases, the gain decreases (and so the new values affects less and less the state) and so does the variance of the error (the sigma of the gaussian which represents it decreases quadratically)
+ As such, we have obtained **rules** to **update** the following as $t$ grows:
	+ **State** $\hat{s}_t$
	+ **Gain** $k_t$
	+ **Variance** $P_t$
+ If we do not have any new measurements, the values remain the same. We do not really predict, we just keep the same value as before
---
+ Let's consider an analogous, more complex situation
+ We consider a ball, moving at **constant velocity** on a pool table
+ It's state is represented as the vector: $$s_t = \begin{bmatrix}x_t \\ u_t \\ y_t \\ v_t\end{bmatrix}$$ Where:
	+ $(x_t, y_t)$ is the **position** of the ball in the moment $t$
	+ $(u_t, v_t)$ is the **speed** of the ball along the two axis in the moment $t$
+ Since the velocity is constant, $(u_t, v_t)$ does not change, while $(x_t, y_t)$ changes as follows:$$\begin{align}x_{t+1} &= x_t + \Delta t \;u_t \\ y_{t+1} &= y_t + \Delta t \;v_t\end{align}$$
+ If we consider them as matrices, we can write the **process model** $\Phi$, the updating rule of the state: $$s_{t+1} = \begin{bmatrix}x_{t+1} \\ u_{t+1} \\ y_{t+1} \\ v_{t+1}\end{bmatrix} = \underbracket{\begin{bmatrix}1 & \Delta t & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & \Delta t \\ 0 & 0 & 0 & 1\end{bmatrix}}_{\Phi} \cdot\begin{bmatrix}x_t \\ u_t \\ y_t \\ v_t\end{bmatrix}$$
+ Still, this model only works for a system where velocity is constant. But this isn't usually true, there can be a change in acceleration or direction
+ We'll consider such changes as **noise**, as follows: $$s_{t+1} = \Phi s_t + q_t$$
+ Similar to before, we have that $\mathbb{E}[q_t] = 0$, and we get $\mathbb{E}[q_t q_t^T] = Q$, the **covariance** matrix
+ Since velocity is considered constant, we do not measure it
+ As such, a measurement is defined as the following:$$m_t = \underbracket{\begin{bmatrix}1 & 0 & 0& 0 \\ 0 & 0 & 1 & 0\end{bmatrix}}_H \cdot s_t + \underbracket{\begin{bmatrix}r_{x, t} \\ r_{y, t}\end{bmatrix}}_{r_t}$$
+ We have that $\mathbb{E}[r_t] = 0$, and we get $\mathbb{E}[r_t r_t^T] = R$, the **covariance** matrix of the singular error
+ Now, we get the following formula to get the optimal estimate of $s_t$ after $t$ measurements: $$\hat{s}_t = \hat{s}_t^- + k_t(m_t - H s
+\hat{S}_t^-)$$
+ We come back to the age old question: How do we compute $k_t$?
+ As last time! We want to minimize the error's variance: $$\begin{align}e_t &= s_t - \hat{s}_t \\ \arg_{k_t} &\min \mathbb{E}[e_te_t^T]\end{align}$$
+ In particular, we need to minimize its **trace**, the sum of the elements on the diagonal (The variances)
+ Computing the complex gradient, we arrive to the following: $$k_t = p_t^-H^T(Hp_t^-H^T + R)^{-1}$$
+ If we were to compare, we'll observe which it is completely analogous to the simpler case
