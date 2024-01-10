+ A **trapdoor one-way function** is a one-way function such that:
	+ $y = f_k(x) \qquad$ Easy to compute
	+ $x = f^{-1}_k(y)\qquad$ Difficult, if k is not known 
+ It is the kind of function used in public encryption
---
+ The **RSA** algorithm is one of the most popular public encryption algorithm. 
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
	+ *Mathematical details in slides*
---
+ RSA is **not 100% secure**
	+ While prime factorization is really complex, it is still possible
	+ As such, advancements in the field could break the system
	+ More over, RSA is **malleable**. As such, some other padding methods are used for support
---
+ Public key encryption is really secure, but not really efficient
+ As such, it is usually used as support for symmetrical encryption
+ An example, is securing the **key-exchange**!
	+ An example is in SSL/TLS, in which RSA is used
+ Still, if the private key was known, all the past messages would be broken
+ There's another method which instead avoids this problem (it has **Perfect Forward Secrecy** (PFS))
+ It is the **Diffie-Hellman** Key Exchange Algorithm
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
---
+ *In paper notes, there are some parts on secure elements, TPM and similar*