* SQL è uno standard per linguaggi adoperati per gestire DBMS. Mentre esistono numerosi "dialetti", come il PostGress, studieremo lo standard
---
* Esso è composto da più componenti. Cominciamo vedendo il DDL (Data Definition Language), utilizzato per gestire lo schema del modello
---
* Esempi di comandi:
	* CREATE - Permette di creare nuovi oggetti
	* ALTER - Permette di modificare 
	* DROP - Permette di cancellare
---
* Possiamo creare una nuova tabella, implementazioen delle relazioni, tramite il comando CREATE TABLE. Queste tabelle accetteranno duplicati di default, in quanto maggiormente efficente, ma è possibile specificare il contrario
* Nel creare la tabella vengono passati nomi e domini (tipi) degli attributi della tabella
* Esempi di tipi in SQL sono:
	* DECIMAL(n) - numero di n cifre
	* NUMERIC(n.p) - numero di n cifre intere e p cifre decimali
	* CHAR(n) - stringa di n caratteri
	* BOOLEAN - lapalissiano
	* VARCHAR(n) - stringa di massimo n caratteri
	* DATE, TIMESTAMP, DATETIME - misurazioni di tempo differenti
---
* Nel definire gli attributi, possiamo specificare alcune proprietà per essi:
	* NON NULL - Non può essere nullo
	* DEFAULT - Valore di default
	* PRIMARY KEY - Fa parte della chiave primaria, non può esser nullo
	* UNIQUE - Fa parte di una chiave secondaria, non può esser nullo
	* CHECKVALUES - COntrolla che i valori siano in uno specifica sottodominio
	* FOREIGN KEY n REFERENCES p - L'attributo n è chiave esterna per la tabella p
	* ON n CASCADE - Specifica di aggiornare anche ulteriori tabelle collegate durante specifiche operazioni