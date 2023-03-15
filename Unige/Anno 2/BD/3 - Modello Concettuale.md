* Per quanto il modello relazionale sia ottimale per costruire basi di dati, non è facilmente comprensibile
* Utilizziamo quindi un modello __concettuale__ per poter rappresentare in un modo più semplice i nostri dati, e comprendere più facilmente l'organizzazione
* Studieremo in particolare il modello __Entity-Relationship__ (ER), sviluppato da Peter Chen nel 1976
---
* Un __entità__ è un __insieme__ di oggetti, le __istanze__ dell'entità
	* Vengono rappresentate graficamente come __rettangoli__
* Una __associazione__ è un insieme di __legami__ fra due o più istanze. Queste possono appartenere a più entità, od ad una stessa, con i cosiddetti __ruoli__ ad indicare il significato di ognuna
	* Vengono rappresentate graficamente come __rombi__
* Queste vengono __classificate__ in base al __numero__ di oggetti nella associazione.
* Dobbiamo cercare di usare associazioni il più possibile __semplici__, ovvero con numero minore di istanze collegate
---
* Sia entità che associazioni possiedono degli __attributi__, ovvero __funzioni__ applicabili sulle istanze capaci di ritornare valori
	* Vengono rappresentati graficamente come __pallini__ __bianchi__
* Questi attributi possono avere dei __vincoli di cardinalità__, __limiti__ inferiori e superiori al __numero__ di __valori__ che l'attributo può possedere
	* Attributi con __vincolo__ inferiore __nullo__ vengono detti __opzionali__
	* Questi vincoli esistono anche per le associazioni, riguardo il numero di associazioni possibili con alcune istanze
* Esistono anche attributi composti, formati da più proprietà variabili
* Facilitano la scrittura di alcuni vincoli di cardinalità
	* Indicati come __grossi pallini__ bianchi
---
* Un __identificatore__ è un insieme di attributi o associazioni capaci di identificare univocamente un' istanza di un entità
	* Vengono idicati graficamente da __pallini neri__
* Si suddividono in:
	* __Interni__: basati sui valori degli __attributi__
	* __Esterni__: basati sui valori delle __associazioni__
		* Le entità che possiedono solo identificatori esterni vengono dette __deboli__
	* __Misti__: basati __sia__ su associazioni che attributi
* Inoltre si dicono:
	* __Semplici__: formati da una __sola__ proprietà
	* __Composti__: formati da __più__ proprietà
* Gli identificatori __misti__ sono tutti __composti__