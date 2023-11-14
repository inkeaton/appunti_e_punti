+ In **block ciphers**, the message is **divided** in multiple blocks, which are encrypted individually
	+ These blocks are usually **64 bits** or more
+ An **ideal block cipher** is incredibly **secure**
	+ Given a 64 bits block, you have $2^{64}$ possible different inputs, and $2^{64}!$ possible outputs
	+ Sadly though, the key itself (the code table) would be enormous, $n \cdot 2^{64}$ 
+ While secure, it is very **impractical** 
---
+ The solution consists in **Product Ciphers**, in which we use multiple different ciphers to obtain a more powerful encryption. This way, the **key is way smaller**
+ Most Symmetrical Block Ciphers follow this idea
+ In 1949 Claude Shannon proposed the **Substitution-Permutation Cipher** (S-P), which followed this format
	+ The input is split in four blocks
	+ Each block is ciphered with a S-box (**substitution** cipher)
		+ **Confusion** makes relationship between ciphertext and key as complex as possible
	+ The blocks are reunited and are ciphered with a T-box (**transposition** cipher)
		+ **Diffusion** dissipates statistical structure of plaintext over bulk of ciphertext
	+ The cycle is iterated multiple times
---
+ It was implemented first by Horst Feistel in the **Feistel Cipher**:
	+ The input is split in two blocks
	+ The **right** one is ciphered with a **rounding function** (Can be a S-P network)
	+ The **left** one is **XOR**'d with the new right one.
	+ The two halves are swapped
	+ The cycle is iterated multiple times
+ The good thing is that encryption and decryption are **structurally identical**, though the sub-keys used during encryption at each round are taken in reverse order during decryption.
	+ *In the slides it is shown how the properties of XOR affect the decryption*
---
+ The **Data Encryption Standard** (DES) (1993), now deprecated, was an encryption standard proposed by IBM, already used since 1977
	+ It's a block cipher, which uses 64 bit blocks
	+ The key is 56 bit, the eight remaining bits are parity check bits
+ It uses a Feistel-Cipher with a key scheduler, which computes new keys from the original one
	+ There are two additional permutations, one in the beginning, one in the end
	+ The keys and blocks use specific round functions and algorithms
![[DES.png]]
+ It has the advantage of having the **Avalanche Effect**:
	+ When changing **one** bit from the input or from the key, **more then half** of the output bits are changed
+ Still, it has been proven since 1999 that it is possible to **brute force** it in less than a day
+ One small solutions are **Double and Triple DES**, in which the encryption is repeated multiple times, using multiple keys
	+ Still, they can be victims of meet-in-the-middle attacks
---
+ The modern standard is the **Advanced Encryption Standard** (AES) (2001)
	+ It is based on a **Rijndael** Cipher, a family of ciphers which use S-P networks, and different sizes of blocks and keys
		+ AES has a **fixed block** size of 128 bits, and a key size of 128, 192, or 256 bits
		+ The key size used for an AES cipher specifies the number of repetitions of transformation rounds that convert the plaintext into ciphertext: 
			+ 10 cycles of repetition for 128-bit keys. 
			+ 12 cycles of repetition for 192-bit keys. 
			+ 14 cycles of repetition for 256-bit keys.
	+ It is very fast, both hardware and software side
---
+ What can we do if a message is longer than a block? 
+ We can use the **Electronic Code-book** method:
	+ We split the message in more blocks, each encrypted individually
+ It has its limitations tho
	+ **Information leak**: identical ciphertext blocks map to identical plaintext blocks 
	+ **Limited integrity**: decryption doesn’t indicate if ciphertext blocks have been changed, deleted, or duplicated.
+ Another solution is the **Cipher Block Chaining** (CBC)
	+ The blocks are encrypted after being XOR'd with the precedent block
	+ The first block uses a placeholder block (IV)
+ This is much more secure:
	+ Identical plaintext blocks mapped to different ciphertext 
	+ **Chaining dependencies**: $C_j$ depends on all preceding plaintext. 
	+ **Self-synchronizing**: if an error occurs (changed bits, dropped blocks) in $C_j$ but not $C_{j+1}$, then $C_{j+2}$ is correctly decrypted.
---
+ **Analytic Attacks** use the knowledge of the inner workings of the cryptography to get information
+ **Timing Attacks** use the analysis of the inner workings of the physical components to gather information