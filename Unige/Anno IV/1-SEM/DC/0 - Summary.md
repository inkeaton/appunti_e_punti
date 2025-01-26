+ In this note, i will try to summarize the most important concepts of the **Distributed Computing** class.
+ The section about the usage of PySpark by professor Delzanno will be avoided, as it is mostly practical
---
# 1 - General Concepts
+  A Distributed System is a collection of autonomous computing elements (nodes) that appear to its users as a single coherent system
+ They're used everywhere, mostly for their properties:
	+ **Availability**: if one computer (or 10) break down, my website/DB will still work 
	+ **Performance**: a single-machine implementation won’t be able to handle the load/won’t be fast enough
	+ **Decentralization**: I don’t want my system to be controlled by a single entity
+ We need them to be **coherent**:
	+ We need **synchronization** (there is no global clock) 
	+ We need to **manage** group membership & **authorizations** 
	+ We need to **deal** with node **failures**
## ACID Properties
+ A classic set of properties to implement transactions:
	+ **Atomicity**: each transaction is treated as a single unit, that is it either succeeds or fails completely
	+ **Consistency** (Correctness): the system remains in a valid state
	+ **Isolation**: even if transactions may be run concurrently, the system behaves as if they’ve been running sequentially
	+ **Durability**: Even in case of a system failure, the result of the transaction is not lost
## CAP Theorem
+ In a system (that allows transactions), you cannot have all of consistency, availability and partition tolerance
	+ **Consistency**: every read receives the most recent write or an error
	+ **Availability**: every request receives a non-error response
	+ **Partition Tolerance**: the system keeps working even if an arbitrary number of messages between the nodes of our distributed system is dropped
	
![CAP Proof|500](CAP_Proof.png)
# 2 - CP Systems
+ How do we build a **distributed system** capable of operating like a single machine, and **respecting the ACID properties?**
+ We'll imagine we are working in a **fail-stop scenario**:
	+ One-to-one messages only 
	+ They can take arbitrary time 
	+ They can be lost
	+ Computers can stop for an arbitrary time 
	+ But they don’t lose data
+ There is a worse failure model than fail-stop, **Byzantine Consensus**, in which broken nodes may send any message, maybe even acting maliciously
## Deterministic State Machines
+ One pattern is the **State Machine Replication**:
	+ Each machine is a deterministic state machine
	+ Each receives commands
		+ If it's a "write" command, it shares it in a common log with all others machines
		+ if it's a "read" command, it executes it locally
	+ This is **optimized** for **Read-Intensive Workloads**
+ This way, all machines remain synchronized in the same state 
+ **How do we implement this shared log?**
## Paxos
+ A solution is given by the notoriously complicated **Paxos Algorithm**:
	1. One machine sends a message to start a consensus (**Prepare**)
	2. The others answer, preparing to receive a proposal (**Promise**)
	3. If most of the machines answered, the first machine sends a proposal (**Accept**)
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
## RAFT
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
+ #### **TBD: LOOK AT THIS**
	+ How the log is managed
	+ It is important to manage the **growth** in size of the **log**, and its eventual **compaction** 
---
+ Generally, consensus is expensive:
	+ Difficult to implement
	+ Risks being a bottleneck
	+ In organizing machines you have a trade-off between reliability and latency
# 3 - Coordination
## Apache Zookeeper
+ Apache Zookeeper is a **coordination service**, used for multiple purposes
+ It is designed in such a way that:
	+ It's general, reliable and easy to use
	+ Tailor made for **read-intensive workloads**
+ It is **built** on top of another consensus algorithm (Similar to **RAFT**)
+ It has a **wait-free architecture** (no server will be stopped). This means that locks are not present, even if they can be implemented
+ Writes are **linearizable** (executed in the order they are performed), reads are **serializable** (you might be reading stale data)
	+ All operations on the same client will be serialized in FIFO order
+ Clients can subscribe to receive notifications of changes, before seeing the result of the change (**Change Events**)
---
+ The system is implemented as a **distributed file system**, where every operation is a transaction, and we can have change notifications
	+ Each piece of information is a **znode**, which can have other nodes as children (**Hierarchical namespace**)
	![Zookeeper API|500](API.png)
+ In the API, we can pass various flags:
	+ **Watch**: receive change notifications from the file
	+ **ExpectedVersion**: Work on that specific version of the file
	+ **Ephemeral**: When the client is disconnected, the file will be deleted
	+ **Sequence**: Append a counter to the file name
---
+ Using this structure, it is possible to implement all the required features:
	+ **Shared Configuration**: The workers subscribe to the conf file, the admin modifies it. When they get notified, they reload it
	+ **Group membership**: A worker creates an ephemeral file to represent itself. When it disconnects, the file will be removed
	+ **Leader Election**: If the file leader is missing, a worker will create it with its name, in ephemeral form. It will become the leader. When it disconnects, the file will disappear and a new election will be done
	+ **Locks**: Use sequence numbered files as "tickets" to know when is your turn. When the person before me is no longer present, it is my turn
---
+ The machines themselves work using a consensus protocol that’s similar to Raft
+ Update is committed when a majority of servers saved the change
+ **Reads are way quicker than writes**. As the **number of machines increases**, Writes become more expensive, and **reads more cheap** *(see slides for graph)*
## Google Cloud Spanner
+ Google engineers have several **sharded** (partial databases) and **replicated** datacenters distributed across the world
+ They need **linearization** (external consistency) along all the transactions
+ Sadly we **can't use** Paxos/RAFT on all the nodes: The cost would be enormous on such a scale
+ So, they came out with an idea: Use locally Paxos, and then **sync** periodically
+ Each data is tagged with a **timestamp**, to know in which order it was sent
---
+ To do this, we need **very precise clocks**. Since they are very expansive, we can't have them on every node.
+ So, we establish a **time master**, a node which owns a very precise clock (in the case of google, even atomic clocks!) which the other nodes contact to know the exact time
+ The machine use a system called **TrueTime** to query
+ While it is secret, we can assume that the communication happens using something similar to the **NTP** protocol (*see in slides or older SETI notes*)
+ The output of the time master is an interval $[\text{earliest}, \text{latest}]$. Our time is inside of that interval
+ For increased precision, we contact multiple time masters, and combine the results using the **Intersection Algorithm**
	+ We measure a score for intersection between intervals depending on how many intervals are in that intersection 
+ After synchronization, it doesn't take much time for the internal clock to drift again (Google even measured some statistics)
+ The precision itself of the TrueTime depends on the condition of the traffic (congestions, maintenance)
---
+ #### **TBD: LOOK AT THIS**
+ So, how do we ensure **linearizability**?
+ The idea is that transactions will follow the timestamp order
+ Data is kept in a key-value format
+ Writes will receive their timestamp when they acquire the **lock**
+ As such, transactions that work on the same data will be by default happening in separated time intervals (because of the locks)
+ In the cases in which the system is uncertain of its time, it will simply wait and slow down, to avoid conflicting with other transactions
	+ In general, the uncertainty should never go above the length of a transaction
# 4 - Availability
## Erasure Coding
+ Let's assume we want to save our data on $N$ servers and being able to withstand the failure of $M$ servers
+ The easiest idea is to **replicate** the data. I put $N=M+1$, and copy my data non alla $N$ servers. But the **space complexity is very high**, and as such it is not very scalable as a method. We need to reduce the redundancy
---
+ If we consider $M=1$, a simple improvement is using **parity blocks**. We split our data in $K=N-1$ blocks, and we compute another block applying $XOR$ to all blocks.
+ This way, any single block we lose can be recomputed from all the remaining blocks, and we only need one ulterior $\frac{N}{K}$ block of additional space
+ But this solution **cannot go beyond one server failure**...
---
+ #### **TBD: LOOK AT THIS**
+ A more complex solution comes from **Erasure Coding**
+ The idea is encoding my data in $N$ blocks, each of size $\frac{1}{K}$th of the original data, where $K=N-M$
+ We will need only any $K$ blocks to recover the missing data
+ How does it work?
	+ The idea is to describe our data as the **coefficients** of a polynomial curve
	+ We memorize it as several points belonging to the curve
	+ Given a sufficient amount of **points** $K$, it is possible to resolve a linear system and **compute the original data**
+ There's a catch tho: If the value of the **points** grows too much, it is possible that they become **more expansive to store** than the original data
+ A solution comes from using **finite fields** as values. An example are the **Integers Modulo** A Prime Number 
## Queuing Theory
+ #### **TBD: LOOK AT THIS**
+ We will try to find a way to optimize queues
+ We will strat by describing the problem using the **M/M/1** model
+ In it, we have two key values:
	+ $\lambda$ which is the rate at which jobs **join** the queue
	+ $\mu$ which is the rate at which jobs **leave** the queue
+ The **number of nodes** in the queue is seen as a **state** of the model
+ Jobs are served in FIFO order
---
+ Now, let's see how this model behaves on the long run
+ Our objective is to be at **equilibrium**
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
## Discrete Event Simulations
+ *It was a lab for SSE students, not a lot to look at...*
# 5 - Distributed Systems
## Tor
+ **The Onion Router** is a protocol intended to ensure the privacy of communications online.
+ To make it work, we **assume**:
	+ An attacker can't control all nodes of a Tor Network
	+ Attackers can’t see your traffic from both guard and exit nodes
+ The idea is quite simple:
	+ Instead of sending my message directly to the destination, it passes through **three different nodes**
	+ Each node only knows the previous and following node, and as such it can't track the route of the message
	+ The message is encrypted in various **layers**, as much as the nodes
+ The nodes are called
	+ **Guard** Node: Receives the message from the sender
	+ **Relay** Node: Passes it to the exit
	+ **Exit** Node: Sends the message to the destination
		+ This last node can be considered responsible for the communication, and as such it is not a desired role
+ On each communication, the nodes used change.
---
+ The nodes communicate using a SOCKS Proxy, TCP-based
+ Now, Tor nodes are publicly known, and as such some countries block access to known nodes
+ **Bridges** exist to allow people to use Tor anyway
	+ Basically, secret on-demand nodes
---
+ Another useful feature is the usage of **Onion Services**
+ Basically, servers accessed via a request to a decentralized DB (DHT) using the Tor Protocol
	+ The idea is to "schedule a meeting" with the server in a specified Tor node
---
+ Now, Tor is not perfect, and as such, there are multiple kinds of attacks which the network can suffer
	+ **Bridges** can be **discovered** and manually censored. The solution resides in **obfuscation**
	+ **Websites** can be **fingerprinted**. Tor uses **standard message** sizes to avoid it, but if we have a known list of websites in which to search, it is still possible to enact the attack
	+ The **Sybil Attack** consists in creating and **controlling** a **large amount** of Tor **nodes**, obtaining control over the system. The solution is to fingerprint the nodes to detect similarities
## Searches in P2P Systems
+ **P2P systems** are really **convenient**:
	+ Self-organized and adaptive
	+ Distributed and decentralized, hence fault-tolerant
	+ Censorship-resistant (as we’ve seen with Tor)
	+ Uses resources that would be wasted otherwise
+ But they've got a simple problem: **How do we search** for something inside of them?
+ After all, each node is independent, and so the information about the position of specific files is known only by the node itself
+ Various systems have tried to solve the problem:
	+ **Centralized P2P**: The Napster network had a **index server**, in which users submitted the location of their files
		+ Very simple idea, but it creates a **point of failure**, and bottleneck
	+ **Flooding**: Used in the first versions of Gnutella, messages would be sent with a TTL to all nodes, and forwarded to nearby nodes, until the file was found, or the message died
		+ While the system worked, it was slow and very expensive, it could even overload weaker systems
	+ **Ultrapeers**: Adopted by newer versions of Gnutella, the nodes were classified in leaf nodes and ultrapeers. 
		+ This latter category included the most performant machines, which were connected to other ultrapeers. 
		+ Each of leafs would send to the router a query routing table (QRT),  a representation of the set of files they have using a **Bloom Filter**, to its peer
		+ Ultrapeers aggregate their QRTs and those of all their leaves, and sends the results to all their neighbours
		+ Queries get sent to a peer only if they have a hope of having the requested file
			+ This modifications greatly **improved scalability**
---
+ For QRTs we needed an efficient representation of the words we wanted to search
### Bloom Filters
+ An idea is using **Bloom Filters**, a data structure representing a set, which has only two methods:
	+ $\text{add(x)}$: add an element to the set
	+ $\text{test(x)}$: tell me if x is in the set 
		+ There’s a possibility for **false positives**
+ There is **no** way of **retrieving** the elements inside of the set, but it is a **very compact** notation!
+ It is implemented as a list of $m$ bits, with $k$ hash functions mapping elements to values in the list
	+ **Add** applies the $k$ hash functions to the new element, setting $k$ bits to 1
	+ **Test** verifies that the $k$ bits are all set to 1
+ While the performance can be worse than, let's say, a hash table, its compactness is a great advantage
	+ In databases: keeping a “cache” in RAM before accessing a disk 
		+ If we know an item isn’t on disk, we spare a disk access 
	+ Web caches: avoid storing data requested only once 
		+ Only cache things at the second time they’re asked
---
+ How **probable** is a **false positive**?
+ Let's assume we have $m$ bits, $k$ hashing functions and $n$ elements in the filter
+ The probability that a bit is not set to 1 by a single hash function for a single element is: $$1 - \frac{1}{m}$$
+ For the $k$ hashing functions, assuming they’re independent the probability that a bit is not set to 1 for each of them is$$\left(1 - \frac{1}{m}\right)^k$$
+ After inserting $n$ elements, a bit is still set to 0 with probability $$\left(1 - \frac{1}{m}\right)^{kn}$$
+ We get a false positive when $k$ random bits are set to 1, hence with probability $$p_{err} = \left(1 - \left(1 - \frac{1}{m}\right)^{kn}\right)^k$$
+ For large values of $m$, this can be approximated to $$p_{err} \approx (1-e^{-\cfrac{kn}{m}})^k$$
+ To **minimize** $p_{err}$, the optimal value of $k$ is $$k^* = \cfrac{m}{n}\ln{2}$$
+ *Continue, more in slides...*
### Cuckoo Filters
+ *No notes on them, see if curious...*
## Distributed Hash Tables
+ DHTs are a decentralized system for searching in P2P systems, an evolution over Ultrapeers
+ The key idea is using a structured P2P overlay, which let's us decide who gets to connect with who
+ Each of the peers handles a **portion of the hash table** $h(x)$ (actually more than one, for redundancy)
+ The **hashing** is **consistent**, adding or removing peers has a small impact on resource allocation
+ Item $x$ will be stored on node corresponding to address $h(x)$
### Chord Rings
+ To reach the needed nodes, we use a structure known as **Chord Ring**:
	+ Nodes take random identifiers, and get in the ring with a link to predecessor and followers
	+ Item x get inserted at the first peer with hash greater than h(x) (and a few more, for redundancy)
+ How do you get your item?
	+ You can get to the node responsible for a given key by **following successor link** until you get to the destination
		+ Very **slow**, and breaks if any node in the middle disappears, complexity is O(n)
	+ Each node can memorize "shortcuts" to node exponentially away from them, memorizing them in **finger tables**. (Accelerated Lookup)
		+ If at each step we follow the finger closest—but before—the destination, our lookup is much faster, complexity is O(log n)
+ **Adding nodes** is quite **easy**, you just need to get your number and the position of the next two successors
+ To **avoid faults** when nodes get disconnected, a periodic **stabilization** is executed, updating successor lists and finger tables every once in a while
+ Chord rings **scale incredibly well**
### Kademlia
+ Kademlia is an **implementation** of **DHTs**
+ Has a **similar** idea to the **chords rings**, logarithmic number of steps to get to destination
+ Added value: links are **symmetrical**, so you can exploit information about them when they reach you
## Bittorrent
+ Bittorrent is a **file distribution system**, which **does not implement search**
+ At its core we have the **torrent** files, containing **metadata** about our file
+ **Trackers** are machines which help discover other nodes of the network. The usage of DHTs has made them **unnecessary**
+ **Seeds** are nodes which have a full copy of the file, they are just sharing it
+ **Downloaders** are nodes which have not finished downloading the file. When they finish, they become seeds
+ Each file is cut in small pieces of 256KB. Torrent files contain hashes of each piece
+ Nodes connect with each other, asking pieces of the file
	+ Which piece to **ask first**? Always the **rarest**, so it will be preserved
---
+ In order to promote cooperation, Bittorrent implements a method called **tit-for-tat**, inspired from the results of **game theory**:
	+ Among all the uploads open, most are **choked**, uploaders don’t send data through them
	+ Every 30s, give an upload slot to a random node which is uploading
	+ Result: to get **fast downloads**, you need to **upload fast**
+ This entices nodes to continue sharing files, even when they have already downloaded them
+ Tit-for-Tat is a bare-bone version of the concept of **reputation**: if you have a good reputation, I’ll be more friendly to you
# 6 - Eventually Consistent Systems
+ Let's remember the CAP Theorem
+ The first systems we have seen were **CP** systems 
	+ If Paxos/Raft are partitioned, the minority will stop working
+ We'll now take a look at **AP** systems, when we will be sacrificing consistency
## Eventual Consistency
+ The two main ideas for data management historically were:
	+ **SQL** Databases: Efficient but Monolithic
	+ **Unix** style Filesystems: Flexible but Complex
+ In the 90's, there started some first approaches to **unite** the **two philosophies**
+ **Brewer** was one of the first, coining the BASE acronym in opposition to ACID
+ After the discovery of the CAP theorem in the mid 00's, its **eventually consistent systems** started to get traction
---
+ Our idea is to let the system work even when partitioned, maybe in a restricted "**partition mode**"
+ But problems arise
	+ How do we detect we have been partitioned?
	+ What can the system do and do not when partitioned?
	+ How do we return to a consistent state afterwards?
	+ How do we detect errors?
+ A good example of eventually consistent systems are **ATM's**
## Amazon Dynamo
+ Dynamo is a system designed for **handling shopping carts** at Amazon
+ **Cassandra** is a very similar system by Apache (*small differences, look in slides*)
+ Its objective is to be **as available as possible**
+ Its requirements are as follows:
	+ Must be always writable, even in partition mode
	+ Must appear consistent to the user
	+ Guaranteed latency measured at percentile 99.9
	+ Highly scalable
	+ Configurable
+ Its key idea is using **chord rings** inside of datacenters
	+ As such, it is **completely decentralized**
+ **Unlike Chord**, every **node** knows the **full partition table**
	+ Routing table updated via a **gossiping** algorithm: every node periodically exchanges information with a random set of other nodes. This is used also for failure detection
+ Also, it uses a **faster** method for **partitioning**, one which **reduces scalability**
+ When machines are disconnected, they are considered transient, they will return
+ In the meantime their writes and reads spill to the next machine in the ring
+ When the machine comes back, they are updated (can create some rare inconsistencies)
---
+ The **API** has two methods:
	+ **get**(key) [value], version_info
	+ **put**(key, value, version_info)
+ Get returns **multiple values** in cases of **inconsistencies**. The client must manage that, using **version_info** to solve
	+ **Vector Clocks** can be used to automatically solve some inconsistencies, by using multiple counters for each machine that has worked on them
+ We can **configure** the system using three **parameters**:
	+ **N**: number of copies for each piece of data (often, 3)
	+ **R**: number of reads to get a successful read
	+ **W**: number of writes to get a successful write
		+ Default is N=3, R=2, W=2 (Consistent & durable)
+ We can toggle them as necessary to choose consistency, speed or durability
---
+ We can use structures like **Merkle Trees** to compare the hashes of data:
	+ We compute the hashes of our data
	+ Then we hash the couple of hashes
	+ We continue step by step until we have only one hash left
+ Merkle trees are used to **compare data** between nodes that store **replicas** of a partition 
	+ If the **root** is **different**, compare the **children** to find out which half is different, and so on recursively 
	+ Fast way to spot differences & reconcile them
---
+ Rarely, every **countermeasure fails**, and the client receives **more than one value**
+ What to do depends on the situation
+ But this case is very **rare**: Amazon reports 0.06% cases of more than 1 value returned
+ *Some other optimizations are possible, look in slides*

# 7 - Working with Big Data
+ Big data is characterized by the 3 Vs:
	+ **Volume**
	+ **Velocity**
	+ **Variety**
+ Often the quality of the work done on it depends form the data itself, and not the algorithms used
+ Working on such enormous amount of data is basically **impossible** using a **single machine**, we need to scale out and use distributed systems
## MapReduce
+ In many workloads, **disk I/O** is the **bottleneck**
+ In order to speed up, we want to read from several disks at the same time, **parallelize the reads**
+ We'll use a **Shared Nothing** architecture:
	+ Independent entities, with no common state
	+ Synchronization introduces latencies, and it is difficult to implement without bugs
	+ A goal is to minimize sharing, so that we synchronize only when we need to
+ In a system this big, **failures are normal.** We need to manage them
+ We also want to **avoid moving data** as much as possible, given their size
+ We can't even load them up all in RAM!
+ We need to work **sequentially** to reduce overhead. Each time we read and rewrite all. Even if it sounds stupid, it is way faster
+ As such, we want to **process** the data **close to the disks** where it resides
+ Distributed filesystems are necessary, and they need to enable **local processing**
+ Here comes **MapReduce**:
	+ Based on **Functional Programming**
	+ Used to **batch process** data present on a **distributed file system**
+ The model works in two steps:
	+ **Map**: Given a function $m$, it is applied to each of the elements of the dataset
	+ **Reduce**: Given a function $r$, an initial value and a list of inputs, the operation is applied recursively on a element and the initial value, then on the output and the next element, and so on. Can be seen as a **aggregation** operation 
+ In the machines itself, we have more phases:
	+ **Map Phase**: Happens on the machines containing the data. Unneeded data is filtered and then the functional map is applied, all in parallel. Produces **key pair values**
	+ **Shuffle Phase**: Data gets grouped by key, so that we get a sequences of all values mapped to the same key. Data gets moved on the network
	+ **Reduce Phase**: The aggregation operation is applied on the data, and its output is written on the DFS
+ We can reduce the amount of data needed to be sent across the network using **combiners**, mini-reducers which **aggregate locally** the mapped data before sending it
+ This idea is very cool, but we need to find ways to make it as efficient as possible
+ One is to use **multiple rounds** of MapReduce
---
+ *Look at Co-Occurrence Matrix, Pairs and Stripes approaches in Slides...*
## Hadoop
+ If you don’t work at Google, **Hadoop** is the software suite you’re likely to use if you have a large dataset
+ Hadoop uses **HDFS**, its own distributed file system. It is designed to **enable MapReduce**
+ It is intended to work on large datasets, stored between multiple machines, using a single distributed file system, tailored to **read-intensive workloads** 
---
+ Files are stored as **blocks**, big (128 MB) chunks of data, in order to speed up sequential reads
+ Blocks are **replicated** in different machines. **Erasure coding** is **not used**, in order to process data right away
+ There are different types of machines in the network:
	+ **NameNode**: keeps blocks metadata in RAM, about their position and data. Writes are written in an atomic and synchronous way on a **journal**, kept somewhere else on the network
	+ **Secondary NameNode**: Receives copies of the edit log from the NameNode. If the main NameNode goes down, one of those will take its place
	+ **DataNode**: store data, heartbeat to the NameNode with the list of their blocks
+   History of a **Read**:
	+ Client gets the block locations from the NameNode, sorted by proximity to the client
	+ Then asks the nodes for the data
+ History of a **Write**:
	+ Client asks the NameNode for k DataNodes (default k=3)
	+ Client writes on first node, then the node copies the data on the next one, and so on
		+ Default: first replica **off-rack**, second replica in the same rack of the first
	+ In the end, a chain of acks is sent, reaching the client
---
+ A MapReduce **job** is composed of **tasks** (single-machine, independent job):
	+ **Map**: by default, 1 HDFS block 1→ input split 1 task. Usually are executed quickly
	+ **Reduce**: Number of reduce tasks is **user-specified**, since it highly depends on the reduce operation itself. The duration time is variable as well
+ What **scheduler** should we use?
	+ **FIFO** penalizes small jobs
	+ **Fair** schedulers give priority to active jobs with **least running tasks**, similarly to round robin schedulers. You cannot prioritize jobs in the queue though
	+ **Capacity** schedulers create virtual clusters, in order to give access to the right amount of power to separate applications or organizations. In case a cluster is not being used, you can always share it with somebody else
	+ Weirdly, **Shortest Job First** is **not useful**, since it is **difficult to estimate** the **duration** of a job
+ **Failures** are fairly **common**, and as such they are managed:
	+ If a task fails, it’s retried a few times (e.g., 4)
	+ If a task hangs (no progress), it’s killed and retried
	+ If a worker machine fails, the scheduler notices the lack of heartbeats and removes it from the worker pool
	+ If the scheduler fails Zookeeper can be used to set up a backup and keep it updated
---
+ The **shuffle phase** happens in part during the Map phase, in part during the Reduce phase
	+ **Map** Task:
		+ The Map gets applied to the data and then is stored in a circular buffer
		+ When the buffer is filled, it’s partitioned (by destination reducer), sorted and spilled to disk
			+ Combiners are run right before spilling to disk
		+ At the end of a map phase, spills are merged and sent to reducers
	+ **Reduce** Task:
		+ Reducers fetch data from mappers and run a merge (like a distributed merge sort)
			+ Mappers don’t delete data right after it’s sent to reducers, so in case of errors they can send it again
		+ After the merge, the reduce is applied and output is saved (& replicated) on HDFS
## Spark
+ MapReduce is incredibly useful, but still has a big **flaw**: Each MapReduce job has to **read and write** from disk
	+ This is the **solution** to deal with **unreliability**: write everything on disk and replicate it
	+ However, this is **slow**
+ What if things could be kept in **RAM** without the need of touching the disk every time?
+ This is the goal of **Spark**!
+ It uses a particular data structure, **Resilient Distributed Datasets** (RDDs)
	+ Immutable, distributed in-memory data structures, partitioned among the machines in the cluster
	+ Only built through **coarse-grained operations** that process the whole RDD
	+ **Fault** recovery performed using **lineage**
		+ Lineage is s log of all the operations done to get there
		+ Recover lost partitions by recomputing what’s missing
+ **Databases** are useful for **small** modifications, **RDDs** for **large** operations
---
+ *Look at GraphX in slides...*