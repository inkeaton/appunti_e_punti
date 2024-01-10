+  In this file, we'll try to summarize the main concepts of the **Computer Security** course
---
# 1 - Introduction
+ The main objective of a cyber-security expert is **risk assessment**: One must be able to recognize the main attacks possible on a computer system, and asses the specific risks
+ It is usually calculated with the following formula:
	+ $risk = f(P_E, I_E)$ 
		+ $P_E$ is the **probability** of the event occurring
		+ $I_E$ is the **impact** of the event, the entity of the damage
		+ $f$ is a simple function, usually the **product**
+ While the **impact** may be usually **simple** to fathom, the **probability** may **not** be
---
+ Five are the main **properties** of Security:
	+ **Confidentiality** : Information is not learned by unauthorized agents
		+ Related are **privacy** and **secrecy**, respectively confidentiality for **privates** and **companies** , and **anonymity**, to keep one's identity secret
	+ **Integrity**: Data has not been maliciously altered
	+ **Authentication**: Agents or data origin can be traced
	+ **Availability**: Services can be accessed when needed
		+ May be attacked via Dos and DDos attacks
	+ **Accountability**: Actions can be traced back the the responsible
		+ Logs may be used, but cannot always be reliable
		+ Another way is **non-repudiation**, the impossibility of the agent to deny its actions
# 2 - Cryptography
## Introduction
+ Imagine communicating on an untrustworthy channel. 
+ How do we make sure that we are communicating without being overheard?
+ Three properties must be respected:
	+ **Confidentiality**
	+ **Integrity**
	+ **Authentication**
+ We can use Cryptography!
---
+ **Plain Text** is the message we want to send
+ **Cipher Text** is the hidden message
+ **Key 1** and **Key 2** are the means by which the message is ciphered/deciphered
	+ $E_{k_1}(P) = C, \quad D_{k_2}(C) = P$ 

+ The **security** of such a system **depends** not so much on the encryption algorithm itself, but on the **secrecy** of the **keys**
	+ Here lies the **Key Exchange Dilemma**: The key must be shared in a secure channel, but we usually use encryption exactly because of the lack of one...
---
+ Some definitions
+ The used **algorithms** can be divided in:
	+ **Symmetric** : $k_1$ is **related** to $k_2$ 
	+ **Asymmetric**: $k_1$ is **unrelated** to $k_2$ 
		+ **Public key**: there exists a public key, which can be **securely shared**

+ The **security** of a **cryptographic system** can be defined as:
	+ **Unconditional**: no matter the computing power, the encryption cannot be broken. 
		+ Measured via **information** theory
	+ **Conditional**: It is theoretically possible to break the encryption, but it is very difficult, or highly unlikely
		+ Measured via **complexity** theory

+ **Cryptanalysis** is the science of recovering encrypted messages, and also their keys

+ There are various kinds of **attacks**:
	+ **Ciphertext Attacks**
		+ Given $C_{1\dots n}$ find $M_{1\dots n}$ or a decryption algorithm
	+ **Known plaintext**
		+ Given $C_{1\dots n}$ and $M_1$, find the key or decipher $M_{2}$ 
	+  **Chosen plaintext** 
		+ Same as above but cryptanalyst may choose $M_{1\dots n}$
		+ **Adaptive chosen plaintext** 
			+ Cryptanalyst can not only choose plaintext, but he can modify the plaintext based on encryption results.
		+ **Chosen ciphertext** 
			+ Cryptanalyst can choose different ciphertexts to be decrypted and gets access to the decrypted plaintext

+ A **definition** of **security** can be given as follows:
	1. Specify an oracle (a type of attack).
	2. Define what the adversary needs to do to win the game, i.e., a condition on his output.
	3. The system is secure under the definition, if any **efficient** adversary wins the game with only **negligible** probability.
---
+ Let's give some formal definitions:
	+ $\mathcal{A}$ is an **alphabet**, a set of symbols
	+ $\mathcal{M} \in \mathcal{A}$ is the **message space**. 
	+ $m \in \mathcal{M}$ is a **message**
	+ $\mathcal{C}$ is the **ciphertext space** (which may be using a different alphabet) 
	+ $\mathcal{K} \in \mathcal{C}$ is the **key space**
	+ $e, d \in \mathcal{K}$ are the encryption and decryption **keys**
---
+ An **Encryption Scheme** is formed by two sets of **functions**:
	+ $E_e : e \in \mathcal{K}$ 
	+ $D_d : d \in \mathcal{K}$ 
+ Such that:
	+ $\forall e \in \mathcal{K} \quad \exists d \in \mathcal{K} \; |\; D_d = E_e^{-1} \leftrightarrow D_d(E_e(m)) = m \qquad \forall m \in \mathcal{M}$ 
+ $d$ and $e$ form a **key pair** 
---
+ A cryptographic function $E(k, m)$ is said **malleable** if:
	+ $\exists F(x), G(x) \; | \; F(E(k, m)) = E(k, G(m)) \qquad \forall m, k$ 
---
+ To construct an encryption scheme, we need:
	+ A message space $\mathcal{M}$
	+ A ciphertext space $\mathcal{C}$ 
	+ A key space $\mathcal{K}$ 
	+ An encryption transformation $E_e : e \in \mathcal{K}$ 
	+ An decryption transformation  $D_d : d \in \mathcal{K}$ 
---
## Symmetric Key Encryption Schemes
+ A **Symmetric Key Encryption Scheme** uses $e$ and $d$ which are **equal,** or related to one another
### Simple Substitution and Transposition Ciphers
 In **Simple Substitution Ciphers**, the letters are substituted with some other symbols from the alphabet
+ Some notable ones are
	+ ***Caesar*** Cipher
		+  Each letter is replaced by the character three to the right modulo 26
	+ ***ROT*** Cipher
		+ Each letter is replaced by the character 13 to the right modulo 26
	+ ***Alphanumeric*** Cipher
		+ Substitute numbers for letters.
+ Are they secure? Not too much, they are susceptible to **brute-force attacks**
+ We can **improve** by allowing an **arbitrary substitution**
---
+ Another way is the ***Affine Cipher***, in which the symbols are substituted with the following rule:
	+ $e(m) = (a \cdot m + b) \mod{|\mathcal{A}|}$ 
+ $a$ and $b$ are two integers, and they're the key
+ To be invertible, $a$ and $|\mathcal{A}|$ must be **relatively prime**
---
 + Still, the **structure of the language**, with its repetitions and quirks **can help the cryptanalyst** find the key...
+ To counter this we introduce ***Homophonic Substitution Cipher***, in which each of the plaintext symbols is coded into **more than one** cipher text symbol. 
+ This way, frequency analysis becomes more difficult, but also the size of data and decryption times
---
+ An idea by Leon Battista Alberti is the ***Polyalphabetic Substitution Cipher***, a **block** cipher where the keys are a sequence of permutations over $\mathcal{A}$ 
	+ For each symbol, you encrypt with a specific key, in modulo
+ Still, the keys were very big
+ ***Vigenère*** proposed using affine transformations, to reduce the load of the keys
---
+ ***One Time Pads*** (or Vernam Cipher) work on **binary data**
	+ The key is a binary sequence, which is XOR'd to the plaintext.
+ It is a **stream** cipher
+ If the **key** is **never reused**, it is **unconditionally secure**
	+ Else, the **malleability** of the XOR makes it so that you can recover the messages
+ The only problem is **exchanging very big keys**
---
+ + Another class of ciphers are **Transposition Ciphers**, in which the symbols are rearranged
	+ One famous example is the ***Lacedemonic Scytale***
+ They're not more secure than substitution-based ones...
---
+ One evolution are **Composite Ciphers**, which mix both substitution and transposition techniques
+ Such codes get so complex, that cipher machines were invented, such as ENIGMA
### Block Ciphers
+ In **Block Ciphers**, the message is **divided** in multiple blocks, which are encrypted individually
	+ These blocks are usually **64 bits** or more
+ An **ideal block cipher** is incredibly **secure**
	+ Given a 64 bits block, you have $2^{64}$ possible different inputs, and $2^{64}!$ possible outputs
	+ Sadly though, the key itself (the code table) would be enormous, $n \cdot 2^{64}$ 
+ While secure, it is very **impractical** 
---
+ The solution consists in **Product Ciphers**, in which we use multiple different ciphers to obtain a more powerful encryption. This way, the **key is way smaller**
	+ Most symmetrical block ciphers follow this idea
---
+ In 1949 Claude Shannon proposed the ***Substitution-Permutation Cipher*** (S-P), which followed this format
+ ![[S-P.png]]
	+ The input is split in four blocks
	+ Each block is ciphered with a S-box (**Substitution** cipher)
		+ **Confusion** makes relationship between ciphertext and key as complex as possible
	+ The blocks are reunited and are ciphered with a P-box (**Transposition** cipher)
		+ **Diffusion** dissipates statistical structure of plaintext over bulk of ciphertext
	+ The cycle is iterated multiple times
---
+ It was implemented first by Horst Feistel in the ***Feistel Cipher***:
+ ![[Feistel.png]]
	+ The input is split in two blocks
	+ The **right** one is ciphered with a **rounding function** (Can be a S-P network) and a **key**
	+ The **left** one is **XOR**'d with the new right one.
	+ The two halves are swapped
	+ The cycle is iterated multiple times
+ The good thing is that encryption and decryption are **structurally identical**, though the sub-keys used during encryption at each round are taken in reverse order during decryption.
---
+ The ***Data Encryption Standard*** (DES) (1993), now deprecated, was an encryption standard proposed by IBM, already used since 1977
	+ It's a block cipher, which uses 64 bit blocks
	+ The key is 56 bit, the eight remaining bits are parity check bits
+ It uses a **Feistel-Cipher** with a key scheduler, which computes new keys from the original one
	+ There are two additional permutations, one in the beginning, one in the end
	+ The keys and blocks use specific round functions and algorithms
![[DES.png]]
+ It has the advantage of having the **Avalanche Effect**:
	+ When changing **one** bit from the input or from the key, **more then half** of the output bits are changed
+ Still, it has been proven since 1999 that it is possible to **brute force** it in less than a day
+ One small solutions are **Double, Triple, and Three-Key Triple DES**, in which the encryption is repeated multiple times, using multiple keys
	+ Still, they can be victims of **meet-in-the-middle attacks**
---
+ The modern standard is the ***Advanced Encryption Standard*** (AES) (2001)
	+ It is based on a **Rijndael** Cipher, a family of ciphers which use S-P networks, and different sizes of blocks and keys
		+ AES has a **fixed block** size of 128 bits, and a key size of 128, 192, or 256 bits
		+ The key size used for an AES cipher specifies the number of repetitions of transformation rounds that convert the plaintext into ciphertext: 
			+ 10 cycles of repetition for 128-bit keys. 
			+ 12 cycles of repetition for 192-bit keys. 
			+ 14 cycles of repetition for 256-bit keys.
	+ It is very fast, both hardware and software side
---
#### Block Ciphers Limitations
 + What can we do if a message is longer than a block? 
+ We can use the ***Electronic Code-book*** method:
	+ We split the message in more blocks, each encrypted individually
+ It has its limitations though
	+ **Information leak**: identical ciphertext blocks map to identical plaintext blocks 
	+ **Limited integrity**: decryption doesn’t indicate if ciphertext blocks have been changed, deleted, or duplicated.
---
+ Another solution is the ***Cipher Block Chaining*** (CBC)
	+ The blocks are encrypted after being XOR'd with the precedent block
	+ The first block uses a placeholder block (IV)
+ This is much more secure:
	+ Identical plaintext blocks mapped to different ciphertext 
	+ **Chaining dependencies**: $C_j$ depends on all preceding plaintext. 
	+ **Self-synchronizing**: if an error occurs (changed bits, dropped blocks) in $C_j$ but not $C_{j+1}$, then $C_{j+2}$ is correctly decrypted.

### Stream Ciphers
+ In stream ciphers, each byte is encrypted **individually**
+ They derive from **Vernam Ciphers** (One-Time Pads), but modern iterations use a **pseudo-random key generator**
+ This way, the **key** itself becomes the generator **seed**, eliminating the key size problem
+ In general, with a properly designed pseudo-random number generator, a **stream** cipher can be **as secure** as a **block** cipher of comparable key length
+ Still, **we can't reuse keys**
---
+ One example of stream cipher is ***RC4***. Created in 1987 by Rivest, and secret until 1993, it is very simple and effective
---
## Public Key Encryption
+  Public Key Encryption was invented in 1975, to solve two problems
	+ The Key **Exchange** Problem
	+ The **Signature** Problem (How to sign a document in the online space)
+ It is defined by the following
	+ Consider $E_e$ and $D_e$ from an encryption schema
	+ Consider them designed such in a way that knowing $E_e$ and the ciphertext $c$ makes it impossible to compute $m$ 
	+ $E_e$ is defined as a **trap-door one-way function**
		+ $y = f_k(x) \qquad$    Easy to compute
		+ $x = f^{-1}_k(y)\qquad$ Difficult, if k is not known 
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
+ ![[pub-alg.png]]
---
+ The ***RSA*** algorithm is one of the most popular public encryption algorithm. 
+ It exploits the complexity of computing the **factorization** of large **prime** numbers
+ It works like this:
	1. Let $n$ be a number known by sender and receiver
	2. We split the plain-text in $\log_2(n)$ bits. As such, each block represents a number $M < n$
	3. Encryption and decryption are as follows:
		+ $C = M^e \mod{n}$ 
		+ $M=C^d \mod{n} = (M^e)^d \mod{n} = M^{ed} \mod{n}$ 
			+ As such, $e$ and $d$ must be chosen in a way such that they'll be multiplicative inverses $\mod{\phi(n)}$ 
+ As such, the procedure becomes as follows:
	1. Generate two (large) distinct primes $p$ and $q$
	2. Compute $n = pq$ and $\phi = (p − 1)(q − 1)$
	3. Select an $e, 1 < e < \phi$, relatively prime to $\phi$.
	4. Compute $d$ such that $ed \mod{\phi} = 1$
	5. Publish $(e, n)$, keep $(d, n)$ private, discard $p$ and $q$
+ Encryption and decryption work as previously described 
+ $d$ could be computed using the **Extended Euclidean Algorithm**

+ RSA is **not 100% secure**
	+ While prime factorization is really complex, it is still possible
	+ As such, advancements in the field could break the system
	+ More over, RSA is **malleable**. As such, some other padding methods are used for support
---
+ Public Key Cryptography is really cool, but still, if the private key was known, all the past messages would be broken
+ There's another method which instead avoids this problem (it has **Perfect Forward Secrecy** (PFS))
+ It is the ***Diffie-Hellman*** Key Exchange Algorithm
+ It works like this:
	1. Principals share prime $q$ and primitive root $\alpha$ of $q$. Both may be public
	2. $A$ and $B$ generate random numbers $X_A$ and $X_B$ (resp.) both less than $q$.
	3. $A$ computes $Y_A = \alpha^{X_A} \mod q$ , $B$ computes  $Y_B = \alpha^{X_B} \mod q$
	4.  $A$ and $B$ exchange results.
	5.  $A$ computes $K_A = Y_B^{X_A} \mod q$ , $B$ computes  $K_B = Y_A^{X_B} \mod q$.
	6. The keys obtained are **equal** ($K_B = K_A$)
+ The system exploits the **difficulty** in computing **discrete logs**
![[Diffie-Hellman.png]]
+ Other than PFS, the good thing is that the actual **key** is **never shared**
+ The problem though is that the system is **unauthenticated**, and as such, the system may be **vulnerable** to **man-in-the-middle attacks**
	+ The only solution is signing the exponents, but this requires another set of shared keys...
# 3 - Authentication
+ Message Authentication is concerned with:
	+ Protecting the integrity of a message
	+ Validating identity of originator
	+ Non-repudiation of origin (dispute resolution)
+  It is based on using an **authenticator**, a value used to authenticate a message, generated by a function
+ We'll consider three methods:
	+ **Message Encryption**: Encrypting the whole message
	+ **Message Authentication Code**: A value obtained with a function of the message and secret code
	+ **Cryptographic Hash function**: similar to before, but which uses a hash function
## Message Encryption
+ In the **message encryption** method, we may use a **public** key encryption scheme, to ensure the identity of the sender
+ To prevent message tampering, we may also add a checksum
+ While surely effective, the message is **not really efficient**, especially if we don't care about the confidentiality of the communication, and the message itself is really big
	+ In some legacy, less powerful, systems, confidentiality could even result being a problem!
## Message Authentication Code
+ In the **Message Authentication Code** method, we use a MAC function $C$, which accepts a variable-size message $M$ and a secret key $K$ as input and produces a fixed-size output $C(M, K )$
	+ The pair itself is called MAC
+ If needed, other layers of encryption may be applied to ensure confidentiality. Still, the authentication of the message remains undisputed
+ A famous MACs is the **Data Authentication Algorithm**, based on **DES**. Today, it is not secure
## Cryptographic Hash
+ In the  **Cryptographic Hash function** method, we use a hash function $H$, without a key, to compute a fixed-size output, $H(M)$ which will be our authenticator.
	+ $H(M)$ is also called message digest or hash code
+ This code is the fingerprint of the message, and ensures its **integrity**
+ We have the advantage of **not having a key to share**
	+ Since a hash is technically not unique, we can also combine this technique with MACs to ensure **authentication**
+ Also, hash function have the **avalanche** effect, which is really useful
+ To be considered useful, a Hash function needs the following properties:
+ ![[hashProperties.png]]
+ **One-way** property is really useful in message authentication involving the use of **secret values**
+ **Weak Collision Resistance** helps in preventing forgery in the cases of using encrypted hashes, and also in **password** encryption
	+ It can be improved by the usage of **salt**, to prevent **dictionary** attacks
+  Also, both WCR and SCR prevent **birthday attacks**, which are based on the **birthday** paradox. 
	+  Let $H$ have $2^m$ possible outputs. $H$ must be applied to $2^\cfrac{m}{2}$ inputs so that the probability of a collision is greater than $0.5$
	+ ***RIVEDERE BENE IL PERCHÉ***
+ If unsure, always double the hash bits to prevent it
---
+  In the ***S/Key*** system, we use a one-time password, generated on the spot, to authenticate
	+ Starting from an initial secret, a common hash function is applied, numerous times. Each time the user needs to enter, a new password is generated by passing the **latest password in the hash**. This makes the passwords **one-time** and **useless to sniffers**
---
There exists a **method** to **create hash functions**, proposed by **Merkle**. *Some details in slides*
# 4 - Security Protocols
+ A **protocol** is a set of rules used to coordinate a communication
	+ It can be seen as a **distributed algorithm**
+ Security protocols are:
	+ key to secure distributed systems 
	+ ubiquitous: they span virtually all application domains and the whole protocol stack 
	+ (deceptively) simple: use established protocols when available/possible, but be ready to design/develop/use a new one if necessary needed
+ A **Security** or **Cryptographic Protocol** can be used to achieve the various security objectives necessary
+ The messages may use various components and operations:
	+ Names
	+ Keys: $K$ and $K^{-1}$ 
	+ Symmetric Keys
	+ Encryption: Encrypting with public key
	+ Signing: Encrypting with private key
	+ Nonces: Fresh data used for answers
	+ Timestamps
	+ Message Concatenation
---
+ The **Protocol Notation** (Alice and Bob Notation) is used to describe the communication between principals in protocols
+ In it, the two communicating principals are usually called **Initiator** and **Responder** (or Alice and Bob)

+ In the following protocols, the following **assumptions** are considered true:
	+ Principals know their private keys and public keys of others
	+ Principals can generate/check nonces and timestamps, encrypt and decrypt with known keys
	+ Principals correctly implement the protocol (Honest) 
+ We will use the **Standard Attacker Model**, or **Dolev-Yao** Model, In which the attacker is active, and:
	+ He can intercept and read all messages.
	+ He can decompose messages into their parts. But cryptography is secure: decryption requires inverse keys
	+ He can build new messages with the different constructors.
	+ He can send messages at any time.
		+ Those are very **strong** assumptions, and this makes the obtained systems **very secure**
#### Key Distribution Scenario
+ An example of a protocol is the **Key Distribution Scenario
+ **Description**
	+ Alice (A) and Bob (B) need a shared key to communicate, generated by a Key Distribution Center (KDC)
+ **Goal**
	+ Share secretly a key
+ Here's how it works:
	1. A sends KDC a message containing the identifiers of A and B, with a nonce
	2. KDC answers with a message made by two sections:
		+ The first one is encrypted with A's public key, and contains the previous message sent by A, with the new session key
		+ The second is encrypted with B's public key, and contains the identifier of A, with the new session key
	3. A sends B the second section of the message
	4. B sends A a nonce, encrypted with the new session key
	5. A send B a function of the nonce, encrypted with the new session key
+ While not bad, this protocol is **not safe from replay attacks**. The usage of **timestamps** could **improve** its security 
#### NSPK
+ The **Needham-Schroeder Public Key Authentication Protocol** (NSPK) has the goal of **mutual authentication**
+ It works like this
	1. $A → B : \quad \{A, N_A\}_{K_B}$
	2. $B → A : \quad \{N_A, N_B\}_{K_A}$
	3. $A → B : \quad \{N_B\}_{K_B}$
+ It may be  subject to **man-in-the-middle attacks**, used by attackers to fake their identity
+ A simple **solution** is to **specify** the identity of the **interlocutor** (**Lowe**'s Fix)
	2. $B → A : \{N_A, N_B, B\}_{K_A}$
#### Otway-Rees
+ The **Otway-Rees Protocol** (ORP) has the goal of providing **authenticated key distribution** (with key authentication and key freshness) but without entity authentication or key confirmation
+ It works like this
	1. $A → B : \quad I, A, B, \{N_A, I, A, B\}_{K_{AS}}$
	2. $B → S : \quad I, A, B, \{N_A, I, A, B\}_{K_{AS}}, \{N_B, I, A, B\}_{K_{BS}}$
	3. $S → B : \quad I, \{N_A, K_{AB}\}_{K_{AS}}, \{N_B, K_{AB}\}_{K_{BS}}$
	4. $B → A : \quad I, \{N_A, K_{AB}\}_{K_{AS}}$
+ This system can be victim of **type flaw attacks**
	+ If B sends back to A its initial message, A can be fooled into thinking that $K_{AB} = IAB$. Idem with S 
+ A **solution** is to use some few more bits to add some **type information** to the sub-messages
#### Andrew Secure RPC
+ The **Andrew Secure RPC Protocol** (AS) has the goal to exchange a **fresh**, authenticated, secret, **shared key**, between two principals sharing a symmetrical key.
	1. $A \to B: \quad A, \{N_A\}_{K_{AB}}$ 
	2. $B \to A: \quad \{N_A + 1, N_B\}_{K_{AB}}$
	3. $A \to B: \quad \{N_B+1\}_{K_{AB}}$
	4. $B \to A: \quad \{K'_{AB}, N'_B\}_{K_{AB}}$
+ Establishes the session key $K'_{AB}$ and the nonce $N'_B$ 
+ It still can be victim of **type flaw attacks**, but only authentication is violated, not secrecy
#### Denning and Sacco
+ The **CA (Denning & Sacco) Protocol** is used to share fresh session keys with CAs
	1. $A \to S: \quad A,B$
	2. $S \to A: \quad C_A, C_B$
	3. $A \to B: \quad C_A, C_B, \{\{T_A, K_{AB}\}_{K_A^{-1}}\}_{K_B}$
+ It may be  subject to **man-in-the-middle attacks**
+ The solution still is to specify the principals' identities in the messages
#### Principles of Protocols Designing
+ In slides
#### NSSKA
+ The **Needham-Schroeder Shared Key Authentication Protocol** (NSSK) has the goal to share a key in an authenticated matter:
	1. $A → KDC : \quad A, B, N_A$
	2. $KDC → A : \quad \{N_A, B, K_{AB},\{K_{AB}, A\}_{K_{BS}}\}_{K_{AS}}$
	3. $A → B : \quad \{K_{AB}, A\}_{K_{BS}}$
	4. $B → A : \quad \{N_B\}_{K_{AB}}$
	5. $A \to B : \quad \{N_B-1\}_{K_{AB}}$ 
+ This protocol is still subject to **replay** attacks, which can be solved by adding **timestamps** to the messages
#### Kerberos
+  **Kerberos** is a protocol for authentication/access control for client/server applications.
+  The **system architecture** seems peculiar. It is formed by three main components
	+  The **Kerberos Authentication Server** (KAS) which manages Authentication
	+ The **Ticket Granting Server** (TGS) which manages Authorization
	+ Various servers which check TGS' tickets, ensuring Access Control
+ The **protocol** is inspired by the NSSK protocol, with the difference of using timestamps instead of nonces, to ensure freshness
+ It is divided in three sections, each one composed by two messages
	+ **Authentication** (Once per user login session)
	+ **Authorization** (Once per type of service)
	+ **Service** (Once per service session)
---
 + Those sections work as follows:
	1. Authentication
		1. $A \to KAS : \quad A, TGS$ 
		2. $KAS \to A : \quad \{K_{A, TGS}, TGS, \mathcal{T}_1\}_{K_{AS}}, \{A, TGS, K_{A, TGS}, \mathcal{T}_1\}_{K_{KAS, TGS}}$
		+ The second section of the message works as an **authentication ticket**, usable by A to contact the TGS and request its services
	2. Authorization
		1. $A \to TGS : \quad \{A, TGS, K_{A, TGS}, \mathcal{T}_1\}_{K_{KAS, TGS}}, \{A, \mathcal{T}_2\}_{K_{A, TGS}}, B$
		2. $TGS \to A : \quad \{K_{AB}, B, \mathcal{T}_3\}_{K_{A, TGS}}, \{A, B, K_{AB}, \mathcal{T}_3\}_{K_{BS}}$ 
		+ A sends the AuthTicket with an authenticator, with a short lifespan
		+ A receives a new session key, with a short lifespan, and a ServTicket, to access the server services
	3. Access Control
		1. $A \to B : \quad \{A, B, K_{AB}, \mathcal{T}_3\}_{K_{BS}}, \{A, \mathcal{T}_4\}_{K_{A, TGS}}$
		2. $B \to A : \quad \{\mathcal{T}_4 + 1\}_{K_{AB}}$ 
		+ A sends the service ticket, with a new authenticator
		+ The server replies by authenticating the service
	+ *MORE DETAILS IN ITS FILE*

# 5 - Web Security
### Placement of Encryption (CHANGE POSITION)
+ Considering the internet stack, where should encryption be placed?
	+ In levels 1-2 we use **Link Encryption**
	+ In superior levels, we use **End-To-End Encryption**
+ The first one is less secure, and protects only during **transmission**, while the second makes the message secure and protected from its creation in the **app** to the receiving program
+ The first one needs multiple keys, one for each transmission, while the second uses only one
+ Still, the first one is implementable at the hardware level
### HTTPS
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
### Digital Certificates
+ In public key encryption systems, some man-in-the-middle attacks are possible, by faking the identity of the other party, and sharing a false public key.
+ These attacks can be thwarted by the introduction of **Digital Certificates**
+ Those objects are "**id** cards", which are used both for key distribution, and authentication
+ They contain all the information about a party, with also their **public key.** These information are encrypted with the private key of a **trusted issuers** (CA), organizations which have the role of issuing them
+ The receiver will decrypt the certificate with the issuer public key
+ Since the private key is technically secret, there **ain't no way it could be faked**, and as such, the receiver is sure of the identity of the other party
---
+ Now, how could the client have the public key of the issuer?
+ They usually have them stored locally in the **OS**, since it is trustworthy. 
+ The OS itself received the list of public keys form a **root CA**, a special issuer which creates certificates for issuers and monitors them
+ It also is needed to know when certificates are **revoked**. There are two methods:
	+ **CRL** distribution points
		+ Those are lists of revoked certificates
		+ They tend to grow very quickly, and as such, this method is becoming less popular
	+ **OCSP** responders
		+ This system, using a special protocol, is less heavy
---
+  The certificates cost **money**, and must be requested to the issuer. They also have an **expiration date**
+ There are two main **categories** of certificates:
	+ **Domain Validation** (DV)
		+ The most common kind. Only the ownership of the domain is verified
	+ **Organization Validation** (OV) and **Extended Validation** (EV)
		+ Also the real-life identity of the owner is verified

### IPSec
+ The **Internet** is very different from a small computer network
+ Security becomes much more complex to discuss
+ An important quirk of the internet is its **layered structure**: each communication is in reality composed of smaller messages
+ How can we **ensure security** in such an eco-system?
+ The simplest and most effective idea comes in securing the **applications** themselves, like in some past protocols, but there are alternatives
+ We could also secure the communication between the Application and Transport layer (with **SSL**, ensuring end-to-end encryption)
+ But we'll instead see **IPSec**, which is capable of ensuring security on the transport layer itself
---
+ IPSec makes it possible to create a secure channel for all applications, using IP addresses for authentication
+ It is a **IETF Standard**
![[IPSec.png]]
+ *DA RIVEDERE*

### General Web Security (IN SLIDES)
# 6 - Buffer Overflows
+ It’s possible to have a great, secure, design but an insecure implementation
+ Buffer overflows are a very common type of error, exploitable as an attack
+ It occurs when data is written past a buffer’s end
+ The resulting damage depends on
	+ Where the data spills over to
	+ How this memory region is used (e.g., flags for access control)
	+  What modifications are made
+ Can be avoided with:
	+ a canary, a random value checked for integrity
	+ avoiding unsafe functions
	+ Marking the stack as not executable

# 7 - Access Control
+ **Cryptography** is useful for ensuring confidentiality and integrity, but does **not help** when dealing with **availability**
+ We need to define a **Security Policy**, a set of rules which determine what is allowed
	+ A security **model** is a formal representation, a security **mechanism** a practical implementation
+ They can be grouped in three classes:
	+ **Discretionary (DAC)** (authorization-based) policies control access based on the identity of the requestor and on access rules stating what requestors are (or are not) allowed to do. 
	+ **Mandatory (MAC)** policies control access based on mandated regulations determined by a central authority. 
		+ The explicit authorization is required
		+ Useful when the data is not owned by the user
	+ **Role-based (RBAC)** policies control access depending on the roles that users have within the system and on rules stating what accesses are allowed to users in given roles.
---
+ Every request passes through a trusted component called **reference monitor** that must enjoy the following properties: 
	+ **tamper-proof**: it should not be possible to alter it (or at least it should not be possible for alterations to go undetected); 
	+ **non-bypassable**: it must mediate all accesses to the system and its resources; 
	+ **security kernel**: it must be confined in a limited part of the system; 
	+ **small**: it must be of limited size to be susceptible of rigorous verification methods
---
+ Formally, the protection of the system can be seen as a **protection state**, of a state machine, the system itself
+ The state is determined by the internal mechanisms of the policy
---
### DAC
+ Premise: **users own resources and control their access**. 
+ The owner of information or a resource is able to change its permission at his or her discretion. Owners can usually also transfer ownership of information to other users. 
+ **Flexible**, but **open to mistakes**, negligence, or abuse. 
	+ Requires that all system users understand and respect security policy and understand AC mechanisms. 
	+ Users and subjects (programs) are trated as the same, and this can be abused
	+ Abuse, e.g., by **Trojan horses**: programs that trick users into transferring rights
#### Access Control Matrixes
+ The privileges of a user in DAC is usually described as a **triple** {Subject, Object, Privilegs}
+ There are various ways of describing it, and one is a **matrix**
+ ![[AC-ControlMatrix.png]]
+ We can add/remove subjects, objects and privileges
####  Harrison-Ruzzo-Ullman
+ The Harrison-Ruzzo-Ullman model defines authorization systems **formalizing** **how to change access rights** or how to create and delete subjects and objects.
+ We use
	+ **States**, defined by the triple {Subjects, Objects, Matrix}
	+ **State Transition**, described by specific commands
```c
command c(x1, . . . , xk ) 
	if r1 in M(xs1 , xo1 ) and . . . rm in M(xsm , xom ) 
	then op1; . . . opn 
end
```
+ There are **six** primitive operations
	+ enter r in M(s, o) -> add privilege
	+ delete r in M(s, o) -> remove privilege
	+ create subject s -> add subject
	+ destroy subject s -> remove subject
	+ create object o -> add object
	+ destroy object o -> remove object
---
+ More examples in slides
#### Other Data Structures
+ Other than Matrixs, we can also use:
	+ **Access Control Lists**
		+ Each file has a list of users, with its privileges on the file
		+ Used in Linux
	+ **Capabilities Lists**
		+ Each user has a list of files, with its privileges on the file
		+ Less common
+ While they're **less efficient** to access, they occupy **way less space** than matrixes
### MAC
+ AC decisions formalized (controlled) by comparing **security labels** indicating sensitivity/criticality of objects, with **formal authorization**, i.e. security clearances, of subjects.
+ More **rigid** and **secure** than DAC, used in critical systems (ex, the military)
+ Usually, those labels and authorization are structured with a **partial order**. 
	+ A user can **read** objects with labels **lesser** than its authorization, and **write** on ones **greater** than it
	+ This way, data can only go up
	+ ![[MAC Example.png]]
+ Usual names are
	+ Top Secret
	+ Secret
	+ Confidential
	+ Unclassified
#### Bell-LaPadula 
+ Probably most famous and influential security model, has as main objective the **confidentiality** of data
+ It combines DAC and MAC aspects
	+ Access permissions are defined **both** through an **AC matrix** and through **security levels.**
	+ Multi-level security (MLS): mandatory policies prevent information flowing downwards from a high security level to a low one.
	+ BLP is a **static** model: security levels (labels) never change.
+ It uses the partial ordering, **no-read-up** and **no-write-down** properties
---
+ The system is very **secure**, but very **limited**
	+ It does **not specify** how to **change** access rights or how to create and delete subjects and objects
	+ It **contains covert channels**, i.e. information-flows that are not controlled by security mechanisms. (like transmitting via task manager!)
#### Biba 
+ The Biba Model uses **opposite properties** to BLP to **ensure integrity**, not confidentiality
	+ **No-read-down** and **No-write-up**
	+ Relax **no-read-down** (“subject low watermark property”): Allow a subject to read down, but first lower its integrity level to that of the object being read. 
	+ Relax **no-write-up** (“object low watermark property”): Lower object level to that of subject doing the write.
+ The **two** models can be **combined** to have **both** integrity and confidentiality
#### Chinese Wall (Brewer And Nash)
+ A commercial **confidentiality** model, inspired by BLP, which adds three levels of abstraction:
	+ Companies, subjects and objects
	+ All objects regarding the same company are in a **company dataset**
	+ All company datasets from competing companies are in the same **conflict of interest class**
+ The security label of an object is obtained from its dataset and class
+ The **permissions** are **dynamic**, and depend on which objects the user is currently accessing or has accessed
	+ In particular, it can't have accessed data from another competing company
	+ Indirect information-flow is still possible with this property
### Role-Based Access
+ An alternative to MAC and DAC policies, widely used in **commercial applications**
	+ For access control it is much more important to know what a user’s organizational responsibilities are, rather than who the user is.
+ Its structure is **similar** to **DAC**, but we **give permissions to roles**, not users. The users will then assume determinate roles in the system to access the permissions
	+ Roles can be in **hierarchies**
+ The users can change roles easily, if permitted. This simplifies the management of the addition of new users
+ The main **pros** are:
	+ Roles allow a user to sign on with the **least privilege** required for the particular task she needs to perform. Users authorized to powerful roles do not need to exercise them until those privileges are actually needed. This **minimizes** the **danger** of damage due to inadvertent errors or Trojan Horses.
	+ **Separation of duties** refer to the principle that no user should be given enough privileges to misuse the system on their own. For instance, the person authorizing a paycheck should not be the same person who can prepare them. Separation of duties can be enforced either statically or dynamically
	+ **Constraints enforcement.** Roles provide a basis for the specification and enforcement of further protection requirements. For instance, cardinality constraints, that restrict the number of users allowed to activate a role or the number of roles allowed to exercise a given privilege. The constraints can be dynamic, i.e. be imposed on roles activation rather than on their assignment
