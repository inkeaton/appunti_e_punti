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
		+ This last category included the most performant machines, which were connected to other ultrapeers. 
		+ Each of leafs would send to the router a query routing table (QRT),  a representation of the set of files they have using a **Bloom Filter**, to its peer
		+ Ultrapeers aggregate their QRTs and those of all their leaves, and sends the results to all their neighbors
		+ Queries get sent to a peer only if they have a hope of having the requested file
			+ This modifications greatly **improved scalability**
---
+ *The slides here explain what is a bloom filter and its evolution, the cuckoo filter*
+ *4/11/24 (We continue talking about bloom filters and explain the chord ring)*