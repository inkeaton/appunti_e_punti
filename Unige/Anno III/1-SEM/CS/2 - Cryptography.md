+ Imagine communicating on an untrustworthy channel. 
+ How do we make sure that we are communicating without being overheard?
+ Three properties must be respected:
	+ **Confidentiality**
	+ **Integrity**
	+ **Authentication**
+ Here we must make us of the techniques of **cryptology**, the study of secret writing
+ We have:
	+ **Stenography**: Hiding messages in another messages
		+ An example might be hiding a message in the bits of the pixels of an image
	+ **Cryptography**: The science of secret writing

---
+ A generic cryptographic schema is the following:
	+ **INSERT SCHEMA**
+ Where:
	+ **Plain Text** is the message we want to send
	+ **Cipher Text** is the hidden message
	+ **Key 1** and **Key 2** are the means by which the message is ciphered/deciphered
		+ $E_{k_1}(P) = C, \quad D_{k_2}(C) = P$ 

+ The **security** of such a system **depends** not so much on the encryption algorithm itself, but on the **secrecy** of the **keys**
	+ Here lies the **Key Exchange Dilemma**: The key must be shared in a secure channel, but we usually use encryption exactly because of the lack of one

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
+ General approaches are:
	+ **Brute-Force attack**: always possible, has heavy costs, and assumes that the plain text is recognizable
	+ **Crypt-analytic attack**:
---
+ There are various kinds of attacks:
	+ **Ciphertext Attacks**
		+ Given $C_{1\dots n}$ find $M_{1\dots n}$ or a decryption algorithm
	+ **Known plaintext**
		+ Given $C_{1\dots n}$ and $M_1$, find the key or decipher $M_{2}$ 
   + **Chosen plaintext** 
		+ Same as above but cryptanalyst may choose $M_{1\dots n}$
	+ **Adaptive chosen plaintext** 
		+ Cryptanalyst can not only choose plaintext, but he can modify the plaintext based on encryption results.
	+ **Chosen ciphertext** 
		+ Cryptanalyst can chose different ciphertexts to be decrypted and gets access to the decrypted plaintext
---
+ A **definition** of **security** can be given as follows:
	1. Specify an oracle (a type of attack).
	2. Define what the adversary needs to do to win the game, i.e., a condition on his output.
	3. The system is secure under the definition, if any **efficient** adversary wins the game with only **negligible** probability.