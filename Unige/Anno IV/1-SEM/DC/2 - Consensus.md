+ How do we build a **distributed system** capable of operating like a single machine, and **respecting the ACID properties?**
+ One pattern is the **State Machine Replication**:
	+ Each machine is a deterministic state machine
	+ Each receives commands
		+ If it's a "write" command, it shares it in a common log with all others machines
		+ if it's a "read" command, it executes it
+ This way, all machines remain synchronized in the same state 
+ **How do we implement this shared log?**
+ We'll imagine we are working in a **fail-stop scenario**:
	+ One-to-one messages only 
	+ They can take arbitrary time 
	+ They can be lost
	+ Computers can stop for an arbitrary time 
	+ But they don’t lose data
### Paxos
+ A solution is given by the notoriously complicated **Paxos Algorithm**:
	1. One machine sends a message to start a consensus (**Propose**)
	2. The others answer, preparing to receive a propose (**Promise**)
	3. If most of the machines answered, the first machine sends a propose (**Accept**)
	4. The others receive the propose and send an acceptation (**Accepted**)
		+ *This step is very cost intensive, since we send messages between all nodes*
	5. If most of the machines answered, the consensus is reached
		+ *(while usually one uses multi-paxos to solve the consensus problem, we'll only see basic paxos, since it is way more simple)*
+ Each message uses a **round counter**, to ensure the freshness of the messages
+ The important thing here is reaching a consensus, not really what the consensus is 
+ If we use $2n + 1$ machines, the protocol can **tolerate** $n$ **failures**:
	+ If you have just one proposer 
		+ **One** or **more** **receptors** fail: Still works as long as the majority is up 
		+ A **proposer fails** in the “**prepare**” phase : Nothing happens, another proposer should eventually show up and start the algorithm 
		+ A **proposer fails** in the “**accept**” phase: Either another proposer overwrites the decision or it gets notified of what’s been done until now, and finishes the job
	+ **Two** or more **proposers** 
		+ The algorithm will never result in a wrong output 
		+ But (in theory) it can result in a **livelock**, an infinite loop of messages
---
+ Still, there are things to be considered when used which are not defined:
	+ **Leader election**:
		+ We can choose a fixed proposer, chosen with Paxos itself
	+ **Cluster Management**:
		+ How do we manage adding and removing nodes?
### RAFT
+ RAFT is a **simpler alternative** to Paxos for finding consensus
+ It is based on three roles:
	+ The **Leader**: The node which proposes the decisions
	+ The **Candidate**: A node proposing to become leader
	+ The **Follower**: A node which follows the leader instructions
+ The system works as follows:
	+ Initially we have all followers
	+ One of the followers becomes a candidate, and proposes as leader to the other nodes
	+ Each node will receive and vote. They can vote only once for round
	+ When it receives the majority of positive answers, it becomes the leader.
	+ The leader sends regularly **heartbeats**, messages which signal that it is still alive
	+ If the nodes do not receive heartbeats before a timeout, a new leader is elected
	+ When a longer timeout expires (term), a new leader is elected
+ The system is able to manage multiple **edge cases**
	+ In case of **split votes**, each one of the tied leaders will receive a randomized timeout to start the voting process again. One will be elected before the other
	+ In case of a **network partition** it is possible to have multiple leaders. In this case, when the partition is solved, the older leader will renounce its role and its uncommitted changes
---
+ It is important to manage the **growth** in size of the **log**, and its eventual **compaction** (*to be studied*)
---
+ Generally, consensus is expensive:
	+ Difficult to implement
	+ Risks being a bottleneck
	+ In organizing machines you have a trade-off between reliability and latency
