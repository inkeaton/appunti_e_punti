+ How do we build a **distributed system** capable of operating like a single machine, and **respecting the ACID properties?**
+ One pattern is the **State Machine Replication**:
	+ Each machine is a deterministic state machine
	+ Each receives commands
		+ If it's a "write" command, it shares it in a common log with all others machines
		+ if it's a "read" command, it executes it
+ This way, all machines remain synchronized in the same state 
+ **How do we implement this shared log?**
---
+ Let's imagine we are working in a **fail-stop scenario**:
	+ One-to-one messages only 
	+ They can take arbitrary time 
	+ They can be lost
	+ Computers can stop for an arbitrary time 
	+ But they don’t lose data
+ A solution is given by the notoriously complicated **Paxos Algorithm**:
	1. One machine sends a message to start a consensus (**Propose**)
	2. The others answer, preparing to receive a propose (**Promise**)
	3. If most of the machines answered, the first machine sends a propose (**Accept**)
	4. The others receive the propose and send an acceptation (**Accepted**)
	5. If most of the machines answered, the consensus is reached
		+ *(while usually one uses multi-paxos to solve the consensus problem, we'll only see basic paxos, since it is way more simple)*
+ If we use $2n + 1$ machines, the protocol can **tolerate** $n$ **failures**.
+ Each message uses a **round counter**, to ensure the freshness of the messages
+ The important thing here is reaching a consensus, not really what the consensus is