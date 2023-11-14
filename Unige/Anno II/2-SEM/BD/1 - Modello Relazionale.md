* Un __dato__ è un fatto, un valore grezzo. Inserito in un contesto, diviene un' __informazione__
* Conserveremo le __istanze__ di dati in __schemi__, capcaci di comunicarci il contesto necessario. Ma come?
* Utilizzeremo la struttura descritta nel __modello relazionale__ (definito da Edgard Codd nel 1970), il cui principio chiave è l'__astrazione__ dell'accesso ai dati per l'utente finale
---
* Cominciamo con delle definizioni:
* Un __dominio__ $D$ è un insieme potenzialmente infinito di valori
* Il __prodotto cartesiano__ fra più domini è l'insieme delle n-uple formate con gli elementi dei domini
* Una __relazione__ è un sottinsieme del prodotto cartesiano fra più domini
	* Il __grado__ della relazione è il numero di domini coinvolti, corrisponde al numero di "colonne"
	* La __cardinalità__ è il numero di elementi presenti nella relazione, corrisponde al numero di "righe"
	* Le tuple presenti nella relazione possono essere viste come funzioni. Questa è la notazione __posizionale__, che permette di accedere ai valori delle tuple
* Tramite questi costrutti, i dati dei domini vengono organizzati tramite lo __schema__ delle relazioni, capaci di dare il __contesto__ necessario
* CI occuperemo di sistemi __schema-first__, in cui viene prima pensato lo schema da usare, poi vengono inseriti i dati
---
* A tutto ciò possiamo aggiungere la notazione con __nome__: ogni dominio viene chiamato con un nome. In questo modo, quando accediamo alla tupla, accediamo ad un tipo di dato "__etichettato__"