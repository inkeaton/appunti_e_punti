+ Google engineers have several **sharded** (partial databases) and **replicated** datacenters distributed across the world
+ They need **linearization** (external consistency) along all the transactions
+ Sadly we **can't use** Paxos/RAFT on all the nodes: The cost would be enormous on such a scale
+ So, they came out with an idea: Use locally Paxos, and then **sync** periodically
+ Each data is tagged with a timestamp, to know in which order it was sent
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
+ So, how do we ensure **linearizability**?
+ The idea is that transactions will follow the timestamp order
+ Data is kept in a key-value format
+ Writes will receive their timestamp when they acquire the **lock**
+ As such, transactions that work on the same data will be by default happening in separated time intervals (because of the locks)
+ In the cases in which the system is uncertain of its time, it will simply wait and slow down, to avoid conflicting with other transactions
	+ In general, the uncertainty should never go above the length of a transaction