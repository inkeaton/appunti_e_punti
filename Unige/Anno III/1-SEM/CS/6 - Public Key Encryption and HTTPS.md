+ Public Key Encryption was invented in 1975, to solve two problems
	+ The Key **Exchange** Problem
	+ The **Signature** Problem (How to sign a document in the online space)
+ It is defined by the following
	+ Consider $E_e$ and $D_e$ from an encryption schema
	+ Consider them designed such in a way that knowing $E_e$ and the ciphertext $c$ makes it impossible to compute $m$ 
	+ $E_e$ is defined as a **trap-door one-way function**
		+ $f$ said to be a one-way function, if $f$ is “easy” to compute, but $f^{−1}$ is “hard” to compute
	+ As such, $e$ can be public information, without problems. It is the **public key**
	+ Instead, $d$ will be kept secret, the **private key**
---
+ The system can be used in two different ways
	+ We could encrypt the message with the public key of the intended receiver $A$. Only $A$ will be able to decipher it, with its private key
		+ This method ensures **confidentiality**
	![[pub-secr.png]]
	+ We could encrypt our message with our private key. While everyone will be able to decipher it, it will be certain that it was sent by us
		+ This method ensures **authentication**
	![[pub-aut.png]]
	+ It is possible to **combine the two**, using double encryption, and two sets of keys
	![[pub-both.png]]
---
+ Such a system needs various **requirements** to be met
	+ It is computationally easy for sender $B$ to generate a pair of keys
	+ It is computationally easy for sender $A$, knowing $PU_b$ and $M$, to generate $C$
	+ It is computationally easy for receiver $B$ to decrypt $C$ using $PR_b$ to recover $M$
	+ It is computationally infeasible for an adversary, knowing $PU_b$ to determine $PR_b$
	+  It is computationally infeasible for an adversary, knowing $PU_b$ and $C$ to recover $M$.
	+ The two keys can be applied in either order
+ As such, few are the **algorithms** which satisfy those:
![[pub-alg.png]]
---
+ Some kind of attacks are:
	+ **Brute-force**
		+ Countermeasure: Use large keys
	+ **Compute PubK from PriK**
	+ **Compute equal ciphertext**
		+ Resolvable using **salt**
---
+ In **HTTPS**, the security protocol used is **SSL/TLS**
+ It works with the following steps:
	1. The host sends a HTTPS request to the server
	2. The server sends back its **public** key
	3. The host generates a pseudo-random number generator **seed**, and sends it to the server, after encrypting it with its public key
	4. The server receives the seed and decrypts it with its **private** key
	5. Now that both the machines have the same key, they start communicating using a **Stream Cipher** (RC4 style)
+ The system is **very secure.** 
+ One of the possible attacks is a malevolent server impersonating the requested one, and sending its public key. 
	+ It could be solved with **digital certificates**