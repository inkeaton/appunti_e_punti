+ Let's give some definitions:
	+ $\mathcal{A}$ is an **alphabet**, a set of symbols
	+ $\mathcal{M} \in \mathcal{A}$ is the **message space**. 
	+ $m \in \mathcal{M}$ is a **message**
	+ $\mathcal{C}$ is the **ciphertext space** (which may be using a different alphabet) 
	+ $\mathcal{K}$ is the **key space**
	+ $e, d \in \mathcal{K}$ are the encryption and decryption **keys**
+ An **Encryption Scheme** is formed by two sets of **functions**:
	+ $E_e : e \in \mathcal{K}$ 
	+ $D_d : d \in \mathcal{K}$ 
+ Such that:
	+ $\forall e \in \mathcal{K} \quad \exists d \in \mathcal{K} \; |\; D_d = E_e^{-1} \leftrightarrow D_d(E_e(m)) = m \qquad \forall m \in \mathcal{M}$ 
+ $d$ and $e$ form a **key pair** 
+ To construct an encryption scheme, we need:
	+ A message space $\mathcal{M}$
	+ A ciphertext space $\mathcal{C}$ 
	+ A key space $\mathcal{K}$ 
	+ An encryption transformation $E_e : e \in \mathcal{K}$ 
	+ An decryption transformation  $D_d : d \in \mathcal{K}$ 
---
+ A **Symmetric Key Encryption Scheme** uses e and d which are equal, or related to one another
+ Until the '70, it was the only type used
+ Types of those schemes are
	+ **Block ciphers**, in which the message is divided in blocks of symbols, and those are encrypted individually
	+ **Stream Ciphers**, in which the block length is 1
	+ **Codes**, in which the length is variable
		+ Code **translations** are kept in **code-books**
---
+ In **Simple Substitution Ciphers**, the letters are substituted with some other symbols from the alphabet
+ Some notable ones are
	+ **Caesar** Cipher
		+  Each letter is replaced by the character three to the right modulo 26
	+ **ROT** Cipher
		+ Each letter is replaced by the character 13 to the right modulo 26
	+ **Alphanumeric** Cipher
		+ Substitute numbers for letters.
+ Are they secure? Not too much, they are susceptible to **brute-force attacks**
+ We can **improve** by allowing an **arbitrary substitution**
---
+ Another way is the **Affine Cipher**, in which the symbols are substituted with the following rule:
	+ $e(m) = (a \cdot m + b) \mod{|\mathcal{A}|}$ 
+ $a$ and $b$ are two integers, and they're the key
+ To be invertible, $a$ and $|\mathcal{A}|$ must be **relatively prime**
--- 
+ Still, the **structure of the language**, with its repetitions and quirks **can help the cryptanalyst** find the key...
+ To counter this we introduce **Homophonic Substitution Cipher**, in which each of the plaintext symbols is coded into more than one cipher text symbol. 
+ This way, frequency analysis becomes more difficult, but also the size of data and decryption times
---
+ An idea by Leon Battista Alberti is the **Polyalphabetic Substitution Cipher**, a block cipher where the keys are a sequence of permutations over $\mathcal{A}$ (*search more details online*)
+ Still, the keys were very big
+ **Vigenère** proposed using affine transformations, to reduce the load of the keys
---
+ **One Time Pads** (or Vernam Cipher) work on binary data
	+ The key is a binary sequence, which is XOR'd to the plaintext.
+ If the **key** is **never reused**, it is **unconditionally secure**
+ The only problem is exchanging very big keys
---
+ A cryptographic function $E(k, m)$ is said **malleable** if:
	+ $\exists F(x), G(x) \; | \; F(E(k, m)) = E(k, G(m)) \qquad \forall m, k$ 
+ XOR is malleable
---
+ Another class of ciphers are **Transposition Ciphers**, in which the symbols are rearranged
	+ One famous example is the Lacedemonic Scytale
+ They're not more secure than substitution-based ones...
---
+ One evolution are **Composite Ciphers**, which mix both substitution and transposition techniques
+ Such codes get so complex, that cipher machines were invented, such as ENIGMA