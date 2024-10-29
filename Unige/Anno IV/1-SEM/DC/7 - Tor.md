+ **The Onion Router** is a protocol intended to ensure the privacy of communications online.
+ To make it work, we **assume**:
	+ An attacker can't control all nodes of a Tor Network
	+ Attackers can’t see your traffic from both guard and exit nodes
+ The idea is quite simple:
	+ Instead of sending my message directly to the destination, it passes through **three different nodes**
	+ Each node only knows the previous and following node, and as such it can't track the route of the message
	+ The message is encrypted in various **layers**, as much as the nodes
+ The nodes are called
	+ **Guard** Node: Receives the message fro the sender
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
+ Basically, servers accessed via a request to a decentralized DB using the Tor Protocol
	+ The idea is to "schedule a meeting" with the server in a specified Tor node
---
+ Now, Tor is not perfect, and as such, there are multiple kinds of attacks which the network can suffer
	+ **Bridges** can be **discovered** and manually censored. The solution resides in **obfuscation**
	+ **Websites** can be **fingerprinted**. Tor uses **standard message** sizes to avoid it, but id we have a known list of websites in which to search, it is still possible to enact the attack
	+ The **Sybil Attack** consists in creating and **controlling** a **large amount** of Tor **nodes**, obtaining control over the system. The solution is to fingerprint the nodes to detect similarities