* Viene utilizzato il valore speciale `null` per indicare la __mancanza__ di valore in un campo. Ogni tipo di dato può assumere questo valore. 
	* Possiamo __specificare__ invece quali campi possono essere `null` tramite alcune __keyword__ del linguaggio
---
* Una __chiave__ è un attributo __unico__ di un elemento della relazione, capace di __identificarlo__.
* Formalmente, possiede le seguenti __proprietà__:
	* $\forall r \in \mathbb{R} \; \;\exists k \subseteq {A_1, \cdots ,A_n } \; | \; se k_{r_1} = k_{r_2} \to r_1[k] = r_2[k]$  (__proprietà d'univocità__)
	* Non esistono sottinsiemi propri di k che sono a loro volta chiavi
* Una chiave che non rispetta la seconda proprietà viene detta __superchiave__. I suoi sottoinsiemi possono essere a loro volta chiavi o superchiavi, più minimali
* L'insieme di tutti gli attributi di un elemento è sempre superchiave
* A noi interessa trovare chiavi __minimali__, ovvero l'insieme di attributi univoci di cardinalità minore
---
* Possiamo anche avere più chiavi utilizzabili. L'insieme di esse viene detto chiavi __candidate__.
* Fra esse sceglieremo una chiave __primaria__, un insieme di attributi che non possono essere nulli, e che useremo come chiave. 
* Le rimanenti verranno chiamate chiavi __alternative__
---
* Esitono anche le cosiddette chiavi __esterne__. Esse __non__ sono vere e proprie __chiavi__, ma un insieme di attributi appartenenti ad una seconda relazione (referente) i quali avranno lo stesso valore di alcuni attributi della relazione riferita. 
* Questo permette di creare un __associazione__ fra diversi elementi di diverse relazioni