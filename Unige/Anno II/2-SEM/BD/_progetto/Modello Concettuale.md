#### Scuola
+ Nome
+ Codice Meccanografico
+ Provincia
+ Ciclo d'istruzione
+ Referenti -> PERSONA
+ Specie -> SPECIE

#### Finanziamento
+ Tipo
+ Partecipante?
+ Referente -> PERSONA
+ Scuola -> SCUOLA

#### Persona
+ Codice Fiscale
+ Nome
+ Cognome
+ Email
+ Telefono **(O)**
+ Ruolo

#### Classe 
+ Nome (classe)
+ Ordine o Tipo
+ Docente di riferimento -> PERSONA

#### Orto
+ Scuola -> SCUOLA
+ Nome
+ Pieno campo o Vaso
+ Coordinate
+ Superficie
+ Utilizzabile da altri istituti

#### Specie
+ Nome Comune
+ Nome Scientifico

#### Utilizzo Specie
+ Specie -> SPECIE
+ Scopo
+ Esposizione
+ Tipo di Coltivazione

#### Repliche
+ Specie -> UTILIZZO SPECIE
+ N° Replica
+ Gruppo -> GRUPPO
+ Orto -> ORTO
+ Esposizione Specifica
+ Data di Messa a Dimora
+ Classe --> CLASSE

#### Rilevazioni
+ 

#### Gruppo
+ Codice Gruppo
+ Tipo
+ 