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