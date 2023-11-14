+ In questo corso, ci occuperemo di definire e discutere le basi della **Computer Security**
+ Il corso è in Inglese, e per ciò gli appunti saranno nello stesso linguaggio
---
+ The english terms **safety** and **security** have the same italian translation (sicurezza), but have two **different meanings** in english:
	+ Safety means to be protected by natural threats, or **accidents**
	+ Security means to be protected by external threats, perpetrated by individuals, **human agents**
+ As such, the **course** will be focused on studying the **vulnerabilities** of computer systems, and as such, the possible kinds of **attacks** which they may render possible
---
+ Nowadays, most of the world heavily relies on computer systems for critical infrastructures of society.
+ While **private companies** seek out the best experts for their security, **states** too have started to invest in the matter
+ **Italy** has created two entities:
	+ Il **Comando Per le Operazioni in Rete** (COR), which operates in military matters
	+ l'**Agenzia per la Cybersicurezza Nazionale** (ACN), which operates in civilian matters
+ Over than those two, exists the **Perimetro Nazionale di Cybersicurezza**, a secret set of national and private companies, which are required to only use **computer systems** certified by the state as **secure** 
---
+ The main objective of a cyber-security expert is **risk assessment**: One must be able to recognize the main attacks possible on a computer system, and asses the specific risks
+ It is usually calculated with the following formula:
	+ $risk = f(P_E, I_E)$ 
		+ $P_E$ is the **probability** of the event occurring
		+ $I_E$ is the **impact** of the event, the entity of the damage
		+ $f$ is a simple function, usually the **product**
+ While the **impact** may be usually **simple** to fathom, the **probability** may **not** be
---
+ Five are the main properties of Security:
	+ **Confidentiality** : Information is not learned by unauthorized agents
		+ Related are **privacy** and **secrecy**, respectively confidentiality for **privates** and **companies** , and **anonymity**, to keep one's identity secret
	+ **Integrity**: Data has not been maliciously altered
	+ **Authentication**: Agents or data origin can be traced
	+ **Availability**: Services can be accessed when needed
		+ May be attacked via Dos and DDos attacks
	+ **Accountability**: Actions can be traced back the the responsible
		+ Logs may be used, but cannot always be reliable
		+ Another way is **non-repudiation**, the impossibility of the agent to deny its actions
---
+ The best solution to implementing security is **security by design**: designing the system while already thinking about the possible security issues
+ Usually we follow the following steps:
	+ A **security analysis**, a survey on the various possible threats
	+ A **threat model**, a file documenting the threats revealed
	+ A **risk assessment**, an evaluation of the risks brought on by the threats
	+ A **security policy**, an adeguate set of countermeasures
	+ Finally, a **security solution**, which considers also the budgetary constraints which may be present