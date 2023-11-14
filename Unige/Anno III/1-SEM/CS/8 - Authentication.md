+ Message authentication is concerned with:
	+ Protecting the integrity of a message
	+ Validating identity of originator
	+ Non-repudiation of origin (dispute resolution)
+ It is based on using an **authenticator**, a value used to authenticate a message
+ We'll consider three methods:
	+ **Message encryption**: Encrypting the whole message
	+ **Message Authentication Code**: A value obtained with a function of the message and secret code
	+ **Cryptographic Hash function**: similar to before, but which uses a hash function
---
+ In the **message encryption** method, we may use a public key encryption scheme, to ensure the identity of the sender
+ To prevent message tampering, we may also add a checksum
+ While surely effective, the message is **not really efficient**, especially if we don't care about the confidentiality of the communication, and the message itself is really big
	+ In some legacy systems, confidentiality could even result being a problem!
---
+ In the **Message Authentication Code** method, we use a MAC function $C$, which accepts a variable-size message $M$ and a secret key $K$ as input and produces a fixed-size output $C(M, K )$
	+ The pair itself is called MAC
+ If needed, other layers of encryption may be applied to ensure confidentiality. Still, the authentication of the message remains undisputed
+ A famous MACs is the **Data Authentication Algorithm**, based on **DES**. Today, it is not secure
---
+ In the  **Cryptographic Hash function** method, we use a hash function $H$, without a key, to compute a fixed-size output, $H(M)$ which will be our authenticator.
	+ $H(M)$ is also called message digest or hash code
+ We have the advantage of **not having a key to share**
	+ Since a hash is technically not unique, we can also combine this technique with MACs to ensure authentication
+ Also, hash function have the **avalanche** effect, which is really useful
+ To be considered useful, a Hash function needs the following properties:
![[hashProperties.png]]
+ **One-way** property is really useful in message authentication involving the use of **secret values**
+ **WCR** helps in preventing forgery in the cases of using encrypted hashes, and also in **password** encryption
	+ It can be improved by the usage of **salt**, to prevent **dictionary** attacks
+  Also, both WCR and SCR prevent **birthday attacks**, which are based on the birthday paradox. *(mathematical details in slides)*
	+ If unsure, always double the hash bits to prevent it
---
+ In the **S/Key** system, we use a one-time password, generated on the spot, to authenticate
	+ *More details in slides*
---
+ *We also briefly mentioned GPG*
+ There exists a **method** to **create hash functions**, proposed by **Merkle**. *Some details in slides*