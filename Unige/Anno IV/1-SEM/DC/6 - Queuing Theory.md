+ We will try to find a way to optimize queues
+ We will strat by describing the problem using the **M/M/1** model
+ In it, we have two key values:
	+ $\lambda$ which is the rate at which jobs **join** the queue
	+ $\mu$ which is the rate at which jobs **leave** the queue
+ The **number of nodes** in the queue is seen as a **state** of the model
+ Jobs are served in FIFO order
---
+ Now, let's see how this model behaves on the long run
+ Our objective is to be an **equilibrium**
+ To reach that, we need that:
	+ $\lambda < \mu$, otherwise the number of elements in the queue will keep growing
	+ The probability of moving from the state $p_i$ to the state $P_{i+1}$ is the same as the opposite, namely:
		+ $\lambda p_i dt = \mu pi_{i+1} dt$
		+ $p_{i+1} = \frac{\lambda}{\mu}p_i$
+ Now, to simplify our computations, let's assume that $\mu=1$
+ Then, $p_{i+1} = \lambda p_i$
+ by continuing with substitutions, we get that:
	+ $p_i = \lambda^i p_0$
+ Since this is a probability distribution, its sum must be one. We can then solve and find the value of $p_0$:
	+ $p_0 = 1 - \lambda$
+ We can then compute the **average queue length**:
	+ $L = \frac{\lambda}{1-\lambda}$
+ We can use **Little's Law** to find the **average time spent** in the system $W$
	+ $L = \lambda W$
	+ $W = \frac{L}{\lambda} = \frac{1}{1-\lambda}$
---
+ Now, let's imagine that we've got **multiple servers** each owning a queue
+ We want to assign loads in the most efficient way possible
+ One idea is to assign each job to the least loaded server!
+ But we'd need to find the specific server each time
+ A simple solution is to choose the least loaded server in a smaller subset of $d$ servers (**Supermarket Queuing**)
+ Doing this, the fraction of queues with at least $I$ jobs drops from $\lambda^{I}$ to $\lambda^{\cfrac{d^i -1}{d-1}}$
---
+ An improvement in **scheduling** comes from **preemptive policies**, the idea of choosing which job to execute, not using FIFO
+ **Round-Robin** plans to give turns to each job, and pausing them when the turn ends. 
+ **Size-Based Scheduling** gives priority to smaller, quicker jobs. A good implementation is Shortest Remaining Processing Time
	+ There is always a small risk of starvation for bigger jobs
	+ You have to pay attention on how you measure size! 
	+ (*more details in slides*)