* Oltre alle istruzioni già descritte, ne troviamo alcune che si differenziano nella modalità di funzionamento: queste sono __CODTRANS, CODREGOP e CORTRANS__ 
* Queste istruzioni infatti sfruttano una particolarità dell'architettura ARM, ovvero l'utilizzo di __COPROCESSORI__
* Questi sono componenti aggiuntivi del processore (possono esserne aggiunti fino a 16) che possono implementare funzionalità facoltative o complesse, in modo da non rallentare la CPU 
* Esempi sono:
	* FPU: compie le operazioni con i Floating Point
	* MMU: precedentemente descritta, gestisce la virtualizzazione del processore
	* CACHE di 2° LIVELLO: Autodescrittiva
	* CRYPTO: Crittografa valori
	* RANDOM... MAGARI! Non esiste un dispositivo capace di vera randomicità
	* SYSTEM: Utilizzato dall'OS per gestire MMU e CACHE, possiamo usarlo anche per riconfigurare la paginazione della RAM
* Similmente alla CPU, ognuno di questi dispositivi conterrà 16 registri ad essi riservati
* Le istruzioni precedentemente descritte implementano:
	* COREGOP: Esegue un operazione specifica del coprocessore indicato in CP#, secondo CPOPCODE, passando se necssario i due registri del coprocessore CRn e CRd
	* CODTRANS: Trasferisce valori fra la RAM ed i registri di CP#
	* CORTRANS: Trasferisce valori fra i registri della CPU ed i registri di CP#