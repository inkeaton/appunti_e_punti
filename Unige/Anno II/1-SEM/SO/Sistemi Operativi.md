* Nella sezione di SETI dedicata ai __Sistemi Operativi__, impareremo il funzionamento di un sistema standard, usando come base Linux
---
* Abbiamo studiato in precedenza il modo in cui il computer funziona: virtualizzazione della memoria, trap, interrupt, etc.
* Grazie alla virtualizzazione, il sistema è in grado di eseguire più programmi contemporaneamente: ognuno di essi crede di utilizzare una propria CPU ed una propria memoria. Ognuno di essi è identificato da un codice __PID__
* Il programma che si occupa di gestire e sincronizzare questi processi è il __Kernel__ o nucleo del sistema operativo. Questi è un programma molto semplice, e spesso si aggiungono ad essi numerosi altri programmi atti a semplificare i rapporti con esso. L'insieme di questi forma il __Sistema Operativo__
	* Per __accedere__ ai __dispositivi__ fisici si usano i __Device-Drivers__, per gestire la __memoria__ si usano astrazioni come il __File-System__
* L'__obbiettivo__ principale del __kernel__ è gestire in modo __efficente__ le risorse, mantenendo __protezione__ ed __isolamento__ fra i diversi processi concorrenti
---
* I primi sistemi operativi sono nati sui computer a _batch-processing_, i quali eseguivano un solo programma per volta, come __librerie__ atte ad astrarre l'uso delle applicazioni
* Con l'avvento dei minicomputer, si è cominciati ad eseguire più applicazioni contemporaneamente, richiedendo l'utilizzo di un programma che gestisse l'accesso al processore
* Il primo OS largamente diffuso fu __Unix__: semplice, potente ed economico, scritto in __C__
* Da esso sono stati creati degli standard per sistemi operativi, __Posix__ e __Single Unix Specification__
* Studieremo la struttura di sistemi operativi __Unix-like__, basati su di esso
---
* La __shell__ è un programma fondamentale dei sistemi unix-like: è un __interprete di comando__, che offre un interfaccia di __alto__ livello alle funzionalità del __kernel__
* Per usarlo, serve utilizzare un __terminale__: __linee di comando__, eredi delle telescriventi
* Ogni sistema è dotato di __terminali virtuali__ da cui poter accedere alla shell
* In Linux il terminale corrisponde ad un file, /dev/tty , come tutto in Unix
* I pty sono coppie di terminali che funzionano in coppia, con un master ed uno slave. Permettono l'emulazione di terminali
* Ogni processo usa tre file descriptor: stdin/cin, stdout/cout, stderr/cerr
* Una shell si relaziona con il terminale leggendo da stdin e scrivendo su stdout/stderr
* /proc è un file system virtuale, un modo che il kernel usa per ricevere le informazioni sui programmi che girano. in /proc/"pid"/fd sono presenti i file descriptor