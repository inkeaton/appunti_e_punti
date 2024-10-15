+ Apache Zookeeper is a **coordination service**, used for multiple purposes
+ It is designed in such a way that:
	+ It's general, reliable and easy to use
	+ Tailor made for read-intensive workloads
+ It is built on top of another consensus algorithm (Similar to RAFT)
+ It has a wait-free architecture (no server will be stopped). This means that locks are not present, even if they can be implemented
+ Writes are **linearizable** (executed in the order they are performed), reads are **serializable** (you might be reading stale data)
	+ All operations on the same client will be serialized in FIFO order
+ Clients can subscribe to receive notifications of changes, before seeing the result of the change (**Change Events**)
---
+ The system is implemented as a **distributed file system**, where every operation is a transaction, and we can have change notifications
	+ Each piece of information is a **znode**, which can have other nodes as children
	![[API.png]]
+ In the API, we can pass various flags:
	+ **Watch**: receive change notifications from the file
	+ **ExpectedVersion**: Work on that specific version of the file
	+ **Ephemeral**: When the client is disconnected, the file will be deleted
	+ **Sequence**: Append a counter to the file name
---
+ Using this structure, it is possible to implement all the required features:
	+ **Shared Configuration**: The workers subscribe to the conf file, the admin modifies it. When they get notified, the reload it
	+ **Group membership**: A worker creates an ephemeral file to represent itself. When it disconnects, the file will be removed
	+ **Leader Election**: If the file leader is missing, a worker will create it with its name, in ephemeral form. It will become the leader. When it disconnects, the file will disappear and a new election will be done
	+ **Locks**: Use sequence numbered files as "tickets" to know when is your turn. When the person before me is no longer present, it is my turn
---
+ The machines themselves work using a consensus protocol that’s similar to Raft
+ Update is committed when a majority of servers saved the change
+ Reads are way quicker than writes. As the number of machines increases, Writes become more expensive, and reads more cheap *(see slides for graph)*