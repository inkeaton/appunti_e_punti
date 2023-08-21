### SCUOLA
#### Attributi:
* Nome
* Codice Meccanografico
* Provincia
* Ciclo d'Istruzione
#### Associazioni:
* Riceve (0, N) FINANZIAMENTI
* Ha (1, N) REFERENTI
* Utilizza (0, N) ORTI
* Possiede (1, N) ORTI
* Formata da (0, N) CLASSI
* Segue (3, 3) SPECIE
#### Identificatori:
* L'attributo __Codice Meccanografico__
---
### FINANZIAMENTO
#### Attributi:
* Tipo
* Id
* Soldi
#### Associazioni:
* È ricevuto da (1, 1) SCUOLE
* Possiede un REFERENTE per il finanziamento
	* Con attributo Partecipante
#### Identificatori:
* l'attributo __Id__
---
### REFERENTI
#### Associazioni:
* È referente di (1, 1) SCUOLE
* È (1, 1) PERSONA
* È referente di un FINANZIAMENTO
#### Identificatori:
* Le associazioni con __SCUOLA e PERSONA__
---
### PERSONA
#### Attributi:
* Nome
* Cognome
* Email
* Cellulare (1, 0)
* Ruolo
#### Associazioni:
* È REFERENTE di (0, N) scuole
#### Gerarchie:
* Ha una gerarchia parziale-condivisa, __DOCENTI__
	* ##### Attributi:
		 * Insegnamento
	* ##### Associazioni:
		* È responsabile di (0, N) CLASSI
#### Identificatori:
* Insieme, gli attributi __Nome__, __Cognome__, __Email__
---
### CLASSE
#### Attributi:
* Sezione
* Classe
* Tipo
* Ordine
* Ruolo
#### Associazioni:
* Ha come responsabile (1, 1) DOCENTI
* Appartiene a (1, 1) SCUOLE
* Ha piantato (0, N) PIANTE
* È responsabile di (0, N) RILEVAZIONI
* È responsabile di (0, N) inserimenti di RILEVAZIONI
#### Identificatori:
* Insieme, gli attributi __Sezione__, __Classe__ e l'associazione con __SCUOLA__
---
### SPECIE
#### Attributi:
* Nome
* Nome Scientifico
* Esposizione
#### Associazioni:
* Viene seguita da (0, N) SCUOLE
* Ha (1, 1) SCOPI
* Ne esistono (0, N) REPLICHE
#### Identificatori:
* L'attributo __Nome Scientifico__
---
### ORTO
#### Attributi:
* Nome
* Condizioni
* Superfice
* Coordinate GPS
* Campo / Vaso
#### Associazioni:
* Appartiene a (1, 1) SCUOLE
* Viene utilizzato da (0, N) SCUOLE
* Appartiene a (1, 1) GRUPPO
* Contiene (0, N) SENSORI
#### Identificatori:
* Insieme, l'attributo __Nome__ e l'associazione con la __SCUOLA__ a cui __appartiene__ 
---
### PIANTA
#### Attributi:
* N° Replica
* Esposizione
* Data di Messa a Dimora
* Terriccio / Suolo
#### Associazioni:
* È replica di (1, 1) SPECIE
* È stata piantata da (1, 1) CLASSI
* Appartiene a (1, 1) GRUPPI
* Viene controllata da (0, N) SENSORI
* Viene testata da (0, N) RILEVAZIONI
* Viene confrontata in (0, N) RILEVAZIONI
#### Identificatori:
* Insieme, l'attributo __N° Replica__ e l'associazione con la __SPECIE__ a cui appartiene 
---
### SCOPO
#### Associazioni:
* È scopo di (0, N) SPECIE
#### Gerarchie
* Ha una gerarchia totale-esclusiva, che la divide in: 
* __BIOMONITORAGGIO__
	* ##### Associazioni:
		* È in relazione con (0, N) GRUPPI
		* Viene controllata in (0, N) RILEVAZIONI
* __FITOBONIFICA__
	* ##### Attributi:
		 * Suolo / Aria
	* ##### Associazioni:
		* Viene controllata in (0, N) RILEVAZIONI

---
### RILEVAZIONE
#### Attributi:
* Data Rilevazione
* Ora Rilevazione
* Data Inserimento
* Ora Inserimento
* BIOMASSA:
	* Lunghezza Foglie
	* Larghezza Foglia
	* Peso Fresco
	* Peso Secco
	* Altezza Pianta
	* Lunghezza Radice
* FIORI_FRUTTI
	* N° Frutti
	* N° Fiori
	* Peso Secco
	* Peso Fresco
* SUOLO
	* pH
	* Umidità
	* Temperatura
* DANNI
	* N° Foglie Danneggiate
	* Percentuale Danni nella Foglia
#### Associazioni
* Testa (1, 1) PIANTA
* Confronta (1, 1) PIANTA
* Si occupa di (0, 1) FITOBONIFICHE
* Si occupa di (0, 1) BIOMONITORAGGIO
* Ha come responsabile di rilevazione (1, 1) CLASSE
	* Con attributo Persona
* Ha come responsabile di inserimento (0, 1) CLASSE
	* Con attributo Persona
* Utilizza come strumento (1, 1) RILEVATORE
#### Identificatori
* L'associazione con la __PIANTA__ che __testa__
---
### RILEVATORE
#### Attributi:
* N° Serie
* Luce
* Fertilità
* Temperatura
* Umidità
* App
#### Associazioni:
* Strumento di (0, N) RILEVAZIONI
#### Gerarchie:
* Ha una gerarchia totale-esclusiva:
* __SENSORI__
	* ##### Attributi:
		 * N° Sensore Orto
		 * Tipo
	* ##### Associazioni:
		* Controlla (0, 1) PIANTA
		* È di proprietà di (1, 1) ORTO
* __ARDUINO__ 
	* ##### Attributi:
		* MicroSD
		* Nome
		* Peso
		* Voltaggio
#### Identificatori:
* L'attributo __N° Serie__
---
### GRUPPO
#### Attributi:
* Stress / Controllo
#### Associazioni:
* È contenuto in (1, N) ORTI
* Contiene (20, 20) PIANTE
* È in contatto con (0, 1) piante in un altro GRUPPO
* È in  rapporto con (1, 1) piante in un altro GRUPPO, per diversi SCOPI
#### Identificatori:
* È identificato dalla PIANTA che è contenuta in esso
---
