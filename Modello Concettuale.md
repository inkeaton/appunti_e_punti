# 1. Schema Entità-Relazione
## 1.1 Note per la comprensione dello schema
* 
# 2. Ristrutturazione Specifiche
# 3. Dizionario delle Entità
## SCUOLA
#### Descrizione
* Una SCUOLA è un istituto scolastico partecipante al progetto, il quale contiene classi, mette a disposizione orti per le iniziative collegate, e può ricevere finanziamenti per il progetto. 
#### Attributi
* Nome Istituto : Stringa
* Codice Meccanografico : Stringa 
* Provincia : Stringa
* Ciclo D'Istruzione : Stringa
* Tipo di Finanziamento (0, 1) : Stringa
#### Associazioni
* Possiede (1, N) PERSONE di riferimento
	* Associazione con attributo Partecipante : Booleano
* Possiede (1, N) CLASSI che partecipano al progetto
* Possiede (1, N) ORTI
* Studia (3, 3) SPECIE
#### Identificatori
* Le SCUOLE vengono identificate dall'attributo __Codice Meccanografico__
#### Vincoli/Note
* Tipo di Finanziamento è presente solo se la scuola beneficia di un finanziamento
* Partecipante è un attributo di tipo Booleano che indica se il referente è anche partecipante
* Deve possedere almeno una classe che partecipa al progetto, altrimenti non sarebbe in questo schema
## PERSONA
#### Descrizione 
* Una PERSONA è un individuo facente parte del progetto. Esso può venir memorizzato per i seguenti motivi:
	* È uno STUDENTE facente parte di una CLASSE partecipante al progetto
	* È REFERENTE per il finanziamento di una SCUOLA
	* È DOCENTE di riferimento di una CLASSE partecipante al progetto
#### Attributi
* Nome : Stringa
* Cognome : Stringa
* Indirizzo Email : Stringa
* Numero Telefonico (0, 1) : Intero
* Ruolo : Stringa
#### Associazioni
* È referente di (0, N) SCUOLE
	* Associazione con attributo Partecipante : Booleano
#### Gerarchie
* Possiede una gerarchia totale-esclusiva, che suddivide l'entità in STUDENTI e REFERENTI. A sua volta, REFERENTI possiede una gerarchia parziale-condivisa che crea il sottoinsieme DOCENTI. Questi sottoinsiemi possiedono le seguenti caratteristiche:
	* ##### STUDENTI
		* ###### Associazioni
		* Appartiene a (1, 1) CLASSI
	* ##### REFERENTI
		* ###### Associazioni
		* È persona di riferimento per (0, N) SCUOLE
			* Associazione con attributo Partecipante : Booleano
	* ##### DOCENTI
		* ###### Associazioni
		* È docente di riferimento di (0, 1) CLASSI
#### Identificatori
* Insieme , Il Nome, Cognome, ed Indirizzo Email
#### Vincoli/Note
* Partecipante è un attributo di tipo Booleano che indica se il referente è anche partecipante al progetto
---
## CLASSE
#### Descrizione
* Una CLASSE è, appunto, una delle classi di un'istituto scolastico partecipante al progetto
#### Attributi
* Nome (Classe) : Stringa
* Ordine o Tipo : Stringa
#### Associazioni
* Ha come referente (1, 1) DOCENTI, in PERSONA
* Appartiene a (1, 1) SCUOLA
* Ha piantato (0, N) REPLICHE
#### Identificatori
* Il Nome e la SCUOLA a cui appartiene
#### Vincoli/Note
* Può aver piantato 0 REPLICHE se è appena entrata nel progetto
---
## ORTO
#### Descrizione
* Un ORTO è uno spazio verde appartenente ad una SCUOLA, nel quale vengono piantate le REPLICHE studiate nel progetto. 
#### Attributi
* Nome : Stringa
* Tipo di Coltivazione : Stringa
* Coordinate GPS : Stringa
* Superfice : Intero
* Condizioni Ambientali : Booleano
#### Associazioni
* Posseduto da (1, 1) SCUOLA
* Contiene (0, N) REPLICHE
* Contiene (0, N) RILEVATORI
#### Identificatori
* Nome con la SCUOLA a cui appartiene
#### Vincoli/Note
---
## SPECIE
#### Descrizione 
* Una SPECIE è una classe di piante a cui appartengono più REPLICHE. Ogni SPECIE 
#### Attributi
* Nome Comune : Stringa
* Nome Scientifico : Stringa
* Esposizione : Stringa
* Scopo : Stringa
* Tipo di Coltivazione : Stringa
#### Associazioni
* Viene studiata da (0, N) SCUOLE
* Vi appartengono (0, N) REPLICHE
* Viene monitorata in (0, N) RILEVAZIONI
#### Identificatori
* DA TROVARE IDENTIFICATORE
#### Vincoli/Note
----
## REPLICA
#### Descrizione
* Una REPLICA è una pianta appartenente ad una SPECIE utilizzata per effettuare le misurazioni per il progetto
#### Attributi
* N° Replica : Intero
* Esposizione Specifica : Stringa
* Data di Messa a Dimora : Data
#### Associazioni
* Viene piantata da (1, 1) CLASSI
* Appartiene a (1, 1) SPECIE
* Appartiene a (1, 1) GRUPPI
* È piantata in (1, 1) ORTI
* È monitorata da ( ,  ) RILEVATORI
#### Identificatori
* N° Replica e la SPECIE a cui appartiene
#### Vincoli/Note
* Il N° Replica viene pensato come il numero di replica di una specifica specie, e quindi unico per le repliche di una specie
## GRUPPO
#### Descrizione
* Un GRUPPO è un insieme di REPLICHE caratterizzate dallo stesso scopo 
#### Attributi
* N° Gruppo : Intero
* Scopo : Stringa
* Pulito / Inquinato : Stringa
#### Associazioni
* È composto da (20, 20) REPLICHE
#### Gerarchie
* Suddiviso in FITOBONIFICA e BIOMONITORAGGIO
	* I gruppi di Biomonitoraggio sono Associati ad un secondo gruppo di biomonitoraggio di tipo differente
	* __DA FINIRE__
#### Identificatori
* Id e Scopo
#### Vincoli/Note
## RILEVAZIONE
#### Descrizione
* Una RILEVAZIONE è una raccolta di MISURAZIONI su repliche appartenenti ad una stessa SPECIE.
#### Attributi
* N° Rilevazione
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
## RILEVATORE
#### Descrizione
* Un RILEVATORE è un apparecchio elettronico capace di rilevare pH, temperatura ed umidità di una REPLICA, allo scopo di effettuare le RILEVAZIONI
#### Attributi
#### Associazioni
* Si trova in (1, 1) ORTO
* Monitora (0, N) REPLICHE
* Utilizzato in (0, N) RILEVAZIONI
* 
#### Gerarchie
#### Identificatori
#### Vincoli/Note
## RESPONSABILE
#### Descrizione
* Un RESPONSABILE rappresenta l'autore di una RILEVAZIONE o del suo inserimento, che esso sia una CLASSE o uno STUDENTE
#### Attributi
#### Associazioni
#### Gerarchie
#### Identificatori
#### Vincoli/Note
## MISURAZIONE
#### Descrizione
* Una MISURAZIONE rappresenta l'insieme di misure di un certo dato raccolte in una RILEVAZIONE, insieme alle eventuali note
#### Attributi
#### Associazioni
#### Gerarchie
#### Identificatori
#### Vincoli/Note
# 4. Note Aggiuntive
