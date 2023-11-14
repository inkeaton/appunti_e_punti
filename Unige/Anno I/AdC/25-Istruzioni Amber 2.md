* Tutte le istruzioni dell'Amber 2 sono parole di 32 bit
* Ogni istruzione è CONDIZIONALE, ovvero avviene in base ad una condizione, con una struttura *if-else*.
* Questa condizione è codificata nei primi 4 bit dell'istruzione
* Alcune condizioni dipendono dai bit di stato, modificati dall'istruzione precedente. 
* Esempi di valori di questi bit sono:
	* N - il risultato precedente è < 0
	* Z - il risultato precedente è uguale a qualcosa
	* C - Il risultato precedente ha un riporto
	* V - Il risultato precedente ha causato overflow
* Esempi di condizioni sono
	* al (14) - istruzione non condizionale
	* eq (0) - valore uguale a qualcosa

* Esistono più tipi di istruzioni, codificate in modi diversi:
![[istruzioniAmber2_codificaIstruzioni.png | 670]]

## REGOP
* i bit 26/27 00 indicano l'istruzione di tipo REGOP
* il 25 è il bit I, indica il metodo d'indirizzamento
* i bit da 24 a 21 sono l'OPCODE
* il bit 20 contiene il bit S, di modifica. Nel caso S = 0, il bit di stato non viene modificato, e l'struzione non ha effetti sulle condizioni della successiva
* 19-16 contengono il registro Rn, 15-12 il registro Rd. Questi sono i principali operandi
* I rimanenti 12 bit codificano lo SHIFTER OPERAND, il terzo ed ultimo operando delle operazioni

* Le REGOP lavorano su 3 operandi, nel seguente modo:
	* Rd = Rn + ShOp
* Le operazioni sono di tipo aritmetico-logico ![[istruzioniAmber2_RegopOpcode.png]]
* Lo ShOp è codificato in modo da poter essere modificato tramite scorrimento, ovvero MOLTIPLICAZIONI in base 2
* Queste operazioni sono di tipo algebrico/logico
* Questa modifica viene ottenuta tramite l'aggiunta di un circuito nel DATA PATH, il circuito shifter, che modifica lo ShOp come richiesto

* Quest'ultimo viene codificato nel seguente modo:![[istruzioniAmber2_RegopShifterCode.png]]
	* Nel caso I = 1, l'indirizzamento è immediato, e viene suddiviso il registro in due parti
		* I bit 7-0 indicano un valore fisso
		* I bit 11-8 indicano di quanto scorrere il valore ad 8 bit su una base di 32 bit
		* Lo scorrimento degli 8 bit verrà eseguito dallo shifter sulla base dei 4 bit
	* Nel caso I = 0, ShOp viene letto in modo differente
		* I bit 3-0 indicano un registro della CPU, Rm
		* i bit 6-5 indicano il tipo di scorrimento da eseguire:
			* LSL 00 - Scorrimento a sinistra senza segno
			* LSR 01 - Scorrimento a destra senza segno
			* ASR 10 - Scorrimento a destra, considerandolo un complemento a 2
			* ROR 11 - Rotazione
		* Il bit 4 indica come interpretare i 5 bit rimanenti:
			* b4 = 0: indicano di quanto scorrere
			* b4 = 1: b7 = 0, i restanti 4 indicano un registro della CPU Rs, che contiene di quanto scorrere Rm

## MULT
* Queste istruzioni compiono moltiplicazioni
## SWAP
* Queste istruzioni scambiano i valori contenuti in dei registri, utilizzando 3 operazioni di READ e WRITE
* è preferibile rispetto ad un implementazione scritta in codice poichè non interrompibile da una TRAP
## BRANCH
* L'istruzione è riconosciuta dai bit 27-25 (101)
* Il bit 24 è il bit L, di LINK, ed indica il tipo di salto
	* L = 0: l'istruzione è di salto relativo, OFFSET viene sommato a PC
	* L = 1: l'istruzione è di ritorno da funzione, il valore precedente di PC viene salvato in LP prima della somma
* è importante ricordare che i bit di offeset vengono fatti scorrere di due posizioni a sinitra prima della somma, dato che gli ultimi due valori di PC indicano lo stato della CPU
## TRANS
* Queste operazioni compiono letture e scritture in RAM, ovvero operazioni di LOAD e STORE
	* LOAD - Rd = RAM[IND]
	* STORE - RAM[IND] = Rd
* Il bit 23 U indica come ottenere l'indirizzo
	* U = 0 -> IND = Rn - OFFSET/Rm
	* U = 1 -> IND = Rn + OFFSET/Rm
* il bit 22 B indica su quanti bit lavorare
	* B = 0 -> 32 bit
	* B = 1 -> 8 bit
* il bit 20 L indica il tipo di operazione da compiere
	* L = 0 -> STORE
	* L =1 -> LOAD
* il bit 25 I indica se usiamo la modalità indicizzata
	* I = 0 -> IND = Rn +/- OFFSET
	* I = 1 -> IND = Rn +/- Rm
		* Rm è contenuto in OFFSET, e codificato come in REGOP
* i bit P e W indicano come interpretare l'offset nel caso I = 0
	* Indicizzato 10
	* Preincremento 11
	* Postincremento 00
	* Indicizzato Non Privilegiato
		* Quest'ultimo, nonostante il nome, viene usato in modalità privilegiata per accedere ai registri riservati alla modalità non privilegiata

* La velocità di queste operazioni non può essere minore di due cicli di CLOCK, dato che per scrivere o leggere nell'unica CACHE a nostra disposizione, dovremo interrompere per forza la PIPELINE
* Per tal motivo, nel programmare, conviene cercare di utilizzare il meno possibile dati in CACHE ed il più possibile dati già presenti nei registri
## MTRANS
* Simili alle precedenti, con la differenza di essere capaci di operare su più registri contemporaneamente
* La ragione più utile per usare questa funzione è utilizzare come Rn SP, così da salvare nello STACK il valore dei registri alla chiamata di una funzione
## SWI
* Sta per SoftWare Interrupt, ed è usata all'avvenire di una TRAP
* Essa segnala l'avvenire di una trap, e l'OS può utilizzare i 24 bit inutilizzati per localizzare il gestore delle interruzioni, oppure per identificare il tipo di TRAP, secondo convenzioni da esso istituite
* Nell'utilizzo di offset (quindi anche nelle istruzioni BRANCH) è importante notare che, a causa della pipeline, al momento dell'esecuzione il PC sarà due istruzioni (8 byte) in avanti rispetto al momento del fetch, e quindi l'offset dovrà essere minore
