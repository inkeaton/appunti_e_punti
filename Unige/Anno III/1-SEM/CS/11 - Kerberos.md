+ **Kerberos** is a protocol for authentication/access control for client/server applications.
+ Was developed as part of Project Athena (MIT, 1980’s). 
	+ Version V (1993) now standard. 
	+ Widely used, e.g., Microsoft Windows and Microsoft Active Directory.
+ Its name derives from the fact that, originally it was intended to implement **three** components (like Kerberos' Heads) to guard a network's gate:
	+ **Authentication**
	+ **Accounting**
	+ **Audit**
+ Sadly, only the first one was ever implemented
---
+ It's **rules** are numerous:
	+ The user’s password must never travel over the network
	+ The user’s password must never be stored in any form on the client machine: it must be immediately discarded after being used
	+ The user’s password should never be stored in an unencrypted form even in the authentication server database
	+ **Single Sign-On**: The user is asked to enter a password only once per work session. Therefore users can transparently access all the services they are authorized for without having to re-enter the password during this session
	+ **Authentication information resides on the authentication server only**. The application servers must not contain the authentication information for their users. This is essential for obtaining the following results:
		+ The administrator can disable the account of any user by acting in a single location without having to act on the several application servers
		+ When a user changes its password, it is changed for all services at the same time
		+ There is no redundancy of authentication information which would otherwise have to be safeguarded in various places
	+ **Mutual Authentication**: not only do the users have to demonstrate that they are who they say, but, when requested, the application servers must prove their authenticity to the client as well
	+ Following the completion of authentication and authorization, the client and server must be able to establish an encrypted connection
+ Following those rules, the following **requirements** will be met:
	+ **Secure**: An eavesdropper should not be able to obtain information to impersonate a user
	+ **Reliable**: As many services depend on Kerberos for access control, it must be highly reliable and support a distributed architecture, where one system can back up another
	+ **Transparent**: Each user should enter a single password to obtain network services; otherwise he should be unaware of underlying protocols
	+ **Scalable**: The system should scale to support large numbers of users and servers; this suggests a modular, distributed architecture
---
+ The **system architecture** seems peculiar. It is formed by three main components
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
---
+ A Kerberos server defines a **realm**, a section of sort
+ The protocol supports **inter-realm communications**, very useful in case of company merging
+ Sadly, the numbers of extra steps needed increase very rapidly with the number of parties involved, so it's not always feasible
---
+ Its **limitations** mainly derive from its high reliability on **synchronized clocks**