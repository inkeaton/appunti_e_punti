### ENTITÀ
#### Attributi
#### Associazioni
#### Gerarchie
#### Identificatori
#### Vincoli/Note
---
### TO-DO
* Da finire RILEVATORE e RILEVAZIONE, Pensare a GRUPPO
* Trovare identificatore per SPECIE 
* Riguardare tutto in generale
---
### TO-THINK-ABOUT
* Ha senso memorizzare i partecipanti al progetto? E se no, come memorizzare i responsabili delle rilevazioni?
* Come dovremmo organizzare i gruppi? Bisogna avere anche gruppi di fitobotanica? Dovrebbero rispettare le stesse regole?
* Come memorizzare i tipi di sensore presente in un orto?
* Possiamo organizzare in un modo migliore le informazioni di una rilevazione?
* USARE EAN O UPC CODES PER IDENTIFICARE SENSORI
---
### SCUOLA
#### Attributi
* Nome Istituto
* Codice Meccanografico
* Provincia
* Ciclo D'Istruzione
* Tipo di Finanziamento (0, 1)
#### Associazioni
* Con (1, N) PERSONE di riferimento
	* Associazione con attributo Partecipante
* Possiede (1, N) CLASSI che partecipano al progetto
* Possiede (1, N) ORTI
* Studia (3, 3) SPECIE
#### Gerarchie
#### Identificatori
* Codice Meccanografico
#### Vincoli/Note
* Tipo di Finanziamento è presente solo se la scuola beneficia di un finanziamento
* Partecipante è un attributo di tipo Booleano che indica se il referente è anche partecipante
* Deve possedere almeno una classe che partecipa al progetto, altrimenti non sarebbe in questo schema
---
### PERSONA
#### Attributi
* Nome 
* Cognome
* Indirizzo Email
* Numero Telefonico (0, 1)
* Ruolo
#### Associazioni
* È referente di (0, N) SCUOLE
	* Associazione con attributo Partecipante 
#### Gerarchie
* Ha come sottoinsieme __DOCENTE__, formato da persone con ruolo uguale a docente
	* ##### Associazioni
	* Ogni docente può essere referente di (0, N) CLASSI
#### Identificatori
* Nome, Cognome, Indirizzo Email
#### Vincoli/Note
* Partecipante è un attributo di tipo Booleano che indica se il referente è anche partecipante
---
### CLASSE
#### Attributi
* Nome (Classe)
* Ordine o Tipo
#### Associazioni
* Ha come referente (1, 1) DOCENTI, in PERSONA
* Appartiene a (1, 1) SCUOLA
* Ha piantato (0, N) REPLICHE
#### Gerarchie
#### Identificatori
* Il Nome e la SCUOLA a cui appartiene
#### Vincoli/Note
* Può aver piantato 0 REPLICHE se è appena entrata nel progetto
---
### ORTO
#### Attributi
* Nome
* Tipo di Coltivazione
* Coordinate GPS
* Superfice
* Condizioni Ambientali
#### Associazioni
* Posseduto da (1, 1) SCUOLA
* Contiene (0, N) REPLICHE
* Contiene (0, N) RILEVATORI
#### Identificatori
* Nome con la SCUOLA a cui appartiene
#### Vincoli/Note
---
### SPECIE
#### Attributi
* Nome Comune
* Nome Scientifico
* Esposizione
* Scopo
* Tipo di Coltivazione
#### Associazioni
* Viene studiata da (0, N) SCUOLE
* Vi appartengono (0, N) REPLICHE
#### Gerarchie
#### Identificatori
* DA TROVARE IDENTIFICATORE
#### Vincoli/Note
----
### REPLICA
#### Attributi
* N° Replica
* Esposizione Specifica
* Data di Messa a Dimora
#### Associazioni
* Viene piantata da (1, 1) CLASSI
* Appartiene a (1, 1) SPECIE
* Appartiene a (1, 1) GRUPPI
* È piantata in (1, 1) ORTI
* È monitorata da (0, N) RILEVATORI
#### Gerarchie
#### Identificatori
* N° Replica e la SPECIE a cui appartiene
#### Vincoli/Note
* Il N° Replica viene pensato come il numero di replica di una specifica specie, e quindi unico per le repliche di una specie
---
### GRUPPO
#### Attributi
* Id
* Scopo
* Tipo (0, N)
#### Associazioni
* È composto da (20, 20) REPLICHE
#### Gerarchie
* Suddiviso in FITOBONIFICA e BIOMONITORAGGIO
	* I gruppi di Biomonitoraggio sono Associati ad un secondo gruppo di biomonitoraggio di tipo differente
#### Identificatori
* Id e Scopo
#### Vincoli/Note
---
### RILEVAZIONE
#### Attributi
* Data Rilevazione
* Ora Rilevazione
* Data Inserimento
* Ora Inserimento
* Scopo
* Informazioni
	* Tipologia di Substrato
	* Tipo di Coltivazione
	* Cosa sto Monitorando (0, 1)
	* Larghezza Chioma/Foglie
	* Lunghezza Chioma/Foglie
	* Peso Fresco Chioma/Foglie (0, 1)
	* Peso Secco Chioma/Foglie
	* Altezza Pianta
	* Lunghezza Radice
	* Peso Fresco Radici
	* Peso Secco Radici
	* N° Fiori
	* N° Frutti
	* N° Foglie Danneggiate
	* % di Superfice Danneggiata per Foglia
	* pH
	* Umidità
	* Temperatura
#### Associazioni
* Effettua misurazioni su (1, N) REPLICHE
* Possiede (1, 1) RESPONSABILE di Rilevazione
* Possiede (0, 1) RESPONSABILE di Inserimento
* Utilizza (1, N) RILEVATORI
	* Con Attributo Modalità di Trasmissione
#### Gerarchie
#### Identificatori
* DA TROVARE IDENTIFICATORE
#### Vincoli/Note
* Il nome Istituto Scolastico può essere dedotto dall'affiliazione del responsabile della rilevazione
* La SPECIE monitorata può essere dedotta dalla SPECIE delle REPLICHE studiate
* Cosa Sto Monitorando viene indicato solo per RILEVAZIONI con Scopo di Fitobonifica
---
### RILEVATORE
#### Attributi
#### Associazioni
* Si trova in (1, 1) ORTO
* Monitora (0, N) REPLICHE
* Utilizzato in (0, N) RILEVAZIONI
* 
#### Gerarchie
#### Identificatori
#### Vincoli/Note