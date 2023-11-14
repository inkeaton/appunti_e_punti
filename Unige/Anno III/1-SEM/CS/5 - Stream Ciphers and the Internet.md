+ In stream ciphers, each byte is encrypted individually
+ They derive from **Vernam Ciphers** (One-Time Pads), but modern iterations use a **pseudo-random key generator**
+ This way, the **key** itself becomes the generator **seed**, eliminating the key size problem
+ One example of stream cipher is **RC4**. Created in 1987 by Rivest, and secret until 1993, it is very simple and effective
+ In general, with a properly designed pseudo-random number generator, a **stream** cipher can be **as secure** as a **block** cipher of comparable key length
+ Still, we can't reuse keys
---
+ Considering the internet stack, where should encryption be placed?
	+ In levels 1-2 we use **Link Encryption**
	+ In superior levels, we use **End-To-End Encryption**
+ The first one is less secure, and protects only during transmission, while the second makes the message secure and protected from its creation in the app to the receiving program
+ The first one needs multiple keys, one for each transmission, while the second uses only one
+ Still, the first one is implementable at the hardware level
	+ *More details in paper and slides*