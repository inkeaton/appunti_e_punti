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
+ By doing some computations, we obtain the following: $$k_t = \cfrac{P_t^-}{P_t^- + R}$$
+ From this we obtain:$$P_t = (1 - k_t) P_t^-$$
+ As such, we have obtained **rules** to **update** the following as $t$ grows:
	+ **State** $\hat{s}_t$
	+ **Gain** $k_t$
	+ **Variance** $P_t$
+ If we do not have any new measurements, the values remain the same. We do not really predict, we just keep the same value as before
+ We'll now see the same in a more complex situation