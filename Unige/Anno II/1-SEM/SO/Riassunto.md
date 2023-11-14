## 1. Intro
* In un sistema operativo, il __Kernel__ si occupa di gestire e virtualizzare le risorse del Computer (CPU, Memoria)
* Ogni processo viene virtualizzato, ed identificato da un numero, un __PID__
* Il sistema operativo esporta dei comandi speciali di questa VM, le _system call_
* Un buon sistema operativo dovrebbe:
	* Virtualizzare le risorse __evitando l'overhead__, dando ad ogni programma solo le risorse di cui ha bisogno
	* __Isolare__ e __proteggere__ i vari programmi
	* Essere robusto ed __affidabile__, privo di bug
---
* I primi OS non erano altro che librerie per l'esecuzione in batch di più programmi
* Col tempo, questi si sono evoluti in modo tale che potessere eseguire più programmi contemporaneamente
---
## 2. Shell e Terminali
* La Shell è un programma capace di tradurre comandi in istruzioni del Kernel
* La più famosa, e che useremo, è Bash
* Per usare una shell si dovranno usare dei Terminali Virtuali, discendenti delle telescriventi
* `/dev/tty` è il file/terminale associato ad un processo
* Le __Virtual Console__ sono terminali virtuali che condividono tastiera e schermo, usate per eseguire i programmi
	* In Ubuntu, `tty1` è il Login Manager, `tty2` è l'ambiente grafico
* Spesso in questi ambienti si usano __Emulatori di Terminali__, che emulano terminali testuali
* Questi funzionano grazie agli __Pseudoterminali__ `pty`, che collegano i terminali virtuali ai processi in una struttura Master-Slave
	* Un emulatore di terminale crea un nuovo terminale aprendo `/dev/ptmx` ottenendo un file descriptor (Master) ed il programma che vuole interagire con esso apre il `/dev/pts/...` relativo (Slave)
	* In questo modo, un processo che si aspetta di essere collegato ad un terminale può interagire con un programma normale, come un emulatore di terminale
---
* Directory principali in Unix
	* `/` Radice
	* `/bin` e `/sbin`: Comandi essenziali e d'amministrazione 
	* `/boot`: File per l'avvio del sistema
	* `/dev`: File che corrispondo a dispositivi
	* `/etc`: File di configurazione del sistema
	* `/home` e `/root`: Home degli utenti e di root
	* `/lib*`: Librerie
	* `/media` e `/mnt`: mount point per media rimovibili
	* `/proc` e `/sys`: File system virtuali, usati per interagire con i processi
	* `/tmp`: File temporanei
	* `/usr`: gerarchia secondaria condivisibile fra più host
---
* Nei pseudoterminali si usa la __Disciplina di Linea__, un insieme di regole nel modo in cui vengono interpretati i comandi dati a terminale, permettendo correzioni e comandi "speciali" (ctrl+C, etc).
* Questa può essere cambiata (es, Vi)
* Ciò vuol dire che i nostri comandi non vengono inviati alla shell finchè non premiamo invio
---
* Si possono usare le __Sequenze d'escape__ per colorare l'output
---
* __Cosa fa una shell?__:
	* Stampa un prompt ed aspetta l'input
	* Legge l'input, spezzandolo in parole ed operatori
	* Espande gli alias e suddivide i comandi in semplici e complessi
	* Esegue le espansioni
	* Esegue le redirezioni I/O
	* Esegue il comando (solitamente un eseguibile, ma ce ne sono di built-in)
	* Di solito, ne aspetta la terminazione
	* Ricomincia
* Simboli speciali sono `$`, `\`, e `"`
* Il `$` serve ad espandere le __variabili d'ambiente__
* `$$` è il PID della Bash
* I file `/dev/null` e `/dev/zero` sono file contenenti `0` e `\0`
* `yes` stampa una stringa fino a che non viene ucciso il programma
---
* Ogni programma restituisce un __exit status__, recuperabile da `$?`
* L'exit status di un programma terminato da un segnale `s` è `s + 128`
* In Bash, `0` è `true`, `1` è `false`
* Si possono fare degli "__assert__" con `test` e le parentesi quadre
---
* Si possono anche creare funzioni vere e proprie, con `if, else, for, while`, etc
---
* __Job Control__
* È un meccanismo che permette di gestire più "lavori" da un unico terminale
* Ogni terminale può avere oltre al job in Foreground, (Quello che stiamo guardando) molti altri in background
* Per mettere un job in background, usiamo `fg`, per riprenderlo, usiamo `bg [n]`, ove `n` è il numero visibile con `jobs`
---
* Quando __apriamo__ l’emulatore di terminale, lui 
	* crea un `pty` e gestisce la parte master 
	* crea un nuovo processo `p`, che crea una nuova sessione; `p` diventa session-leader 
	* apre lo slave, che diventa il terminale di controllo della sessione; `p` è detto anche controlling process 
	* esegue la shell
* Quando __chiudiamo__ la finestra corrispondente, viene “disconnesso” 
	* il kernel manda il segnale SIGHUP al session-leader, la shell 
	* la shell, a sua volta, lo manda a tutti i job che gestisce 
	* di default, SIGHUP termina i processi
---
## 3. File e Processi
* Una chiamata di sistema o _system call_ è una richiesta controllata al kernel
* Sono scritte in assembly, ma esistono molte __funzioni wrapper__ in C, per poterle usare anche nei programmi di più alto livello
* Queste __funzioni__
	* Preparano gli argomenti, inserendoli negli appositi registri
	* Eseguono una trap (`SYSCALL`)
	* Il Kernel esegue la richiesta, e salva il risultato negli appositi registri
	* Ritornano alla normalità tramite l'istruzione `IRET
	* La funzione wrapper controlla il risultato e a seconda di esso falliscono o lo restituiscono
* Queste funzioni sono più "__impegnative__"
* Controllare sempre il valore di ritorno e di `errno`
---
* Le varie informazioni vengono memorizzate in variabili che variano a seconda del sistema operativo
* Meglio usare degli __alias__ come `pid_t` o castare ad un valore sicuramente maggiore
---
* L'I/O avviene attraverso i __File Descriptors__
	* Numeri che identificano un file, ma anche dispositivi o connessioni
	* Ogni programma ha i suoi
* I primi tre sono per convenzione `STDIN`, `STDOUT`, `STDERR`
* La syscall __`open`__ apre un file (in modalità specificate tramite `flags`) e restituisce un fd relativo ad esso, il più piccolo disponibile
	* Può anche creare il file specificato, in modalità specificate da `mode`
---
* Per modificare i permessi su di un file si possono usare __`chmod`__ e __`chown`__, usando codici in ottale
---
* __`read`__ e __`write`__ leggono e scrivono su di un file, restituendo quanti byte sono stati letti
	* Modificano l'offset del file (nel caso sia un file vero e proprio)
	* Modificabile con __`lseek`__
* __`close`__ chiude un file descriptor
---
* Le system call __`stat`, `lstat`, e `fstat`__ restituiscono i metadati di un file
* Ogni file system ha dei limiti e delle regole per i file al suo interno
* Queste sono leggibili tramite __`getconf`__, __`fpathconf`__ e __`pathconf`__ 
* Alcune costanti che finiscono con `MAX` indicano i valori minimi
---
* Programmi come gcc e clang __pilotano__ il processo di __compilazione__:
	* Compilatori e assemblatori producono i file `.o` a partire dai sorgente
	* `ld` il link editor, mette insieme librerie e file oggetto, eseguendo rilocazione e risoluzione dei simboli, ottenendo i `.out`
* Il __linking__ di per sè può essere __statico__ o __dinamico__
	* Nel primo caso i pezzi di libreria necessari vengono "copiati" nell'eseguibile, rendendo il programma funzionante su tutte le macchine con lo stesso SO
	* Nel secondo caso, le librerie necessarie vengono solo "annotate" nel file, fra cui il programma `ld.so` che si occuperà di leggerle e "unirle" a tempo d'esecuzione
		* Questo rende il programma più facile d'aggiornare , ma più difficle da portare su altre macchine
---
* Gli __eseguibili__ possono contenere:
	* __Codice macchina__: (sezione `.text`)
	* __Dati__ sia modificabili che di sola lettura: (sezione `.data` e `.rodata`)
	* __Metadati__: (Architettura, punto in cui iniziare, spazio riservato alle variabili, etc)
* Queste sezioni saranno mappate all'interno dello spazio d'indirizzamento del programma (da vedere ELF)
* Le librerie dinamiche verranno mappate con indirizzi diversi in ogni programma, venendo condiviso con altri programma
---
* __`getpid`__ e __`getppid`__ ritornano rispettivamente il pid di un programma e del suo genitore
* I processi sono organizzati in un albero, con radice il processo __`init`__
* Possono essere visti tramite il finto file system __`/proc`__
* Ogni processo possiede poi un directory __root__ che si usa per gli indirizzi assoluti e una directory di __lavoro__, usata per i percorsi relativi
	* `getcwd` la restituisce
	* `chdir` la cambia
---
* Le syscall usate per gestire i processi sono:
	* __`fork`__: Crea un nuovo processo, con il corrente come padre
	* __`_exit`__: Termina il processo
	* __`wait`__: Aspetta la terminazione di un processo figlio (più dettagli in seguito)
	* __`exec*`__: Esegue un nuovo processo, "trasformando" il corrente, ed il suo spazio d'indirizzamento
---
* __Fork__ 
	* __Clona__ il processo creando un __figlio__. Copia spazio d'indirizzamento e fd, cambiano invece `pid` e `ppid`
	* In caso di __successo__, ritorna il PID del figlio al padre, 0 al figlio
* __Exit__ e \_exit 
	* La prima è una __funzione__ del C che chiama le funzioni `atexit` e `on_exit`, svuota i buffer ed elimina i file temporanei
	* Dopo di che chiama la __system call__ `_exit` la quale rilascia le risorse, e termina il processo
	* Eventuali __figli orfani__ vengono adottati da `init` o da un processo subreaper designato
* __Wait__
	* __Attende__ un cambio di stato in un __figlio__, che sia una terminazione o uno stop
	* Per aspettare un figlio specifico, esiste `waitpid`
	* Se va a buon fine, salva l'exit status od il segnale del figlio in `wstatus`
	* Un processo terminato, __non__ aspettato dal padre è un processo __zombie__
	* Anche se termina, viene conservato PID ed exit status
	* Quando un processo __termina__, invia al padre il segnale `SIGCHLD` che va catturato per "aspettare" i figli
* __Exec*__
	* Queste funzioni __avviano__ un programma all'interno di quello chiamante, sostituendo lo spazio d'indirizzamento, a meno del PID e degli fd (A meno che non metta la flag `FD_CLOEXEC`)
	* Queste funzioni __non__ devono __ritornare__, ritornano solo in caso d'errore
	* A seconda della lettera presente nel comando, funzionano differentemente:
		* `v` indica che gli argomenti sono in un __array__
		* `l` indica che gli argomenti sono in una __lista__
		* `p` indica di cercare l'__eseguibile__ nel `PATH`
	* Nell'__eseguire__ un programma, il sistema prepara:
		* __Codice__ (r-x)
		* __Dati__ in sola lettura (r--)
		* __Dati__ (rw-)
		* __Stack__ (rw-) in cui si trovano le variabili d'ambiente, gli argomenti passati nel comando, etc
		* Il __Kernel__
		* Le __librerie__
---
* __`dup`__ duplica un fd, restituendo un nuovo valore, che indica allo stesso file
* __`dup2`__ duplica secondo uno specifico valore passato alla funzione
---
* Più fd possono puntare allo stesso file, ma possono avere offset differenti, puntando allo stesso inode, ma ad una differente spazio della Open file table
* Dipende se l'fd è stato duplicato, o se è stato ottenuto con una seconda open sullo stesso file
---
* __Pipe__
	* Permettono di creare un canale di comunicazione fra due processi, creando un buffer nel kernel su cui poter comunicare
	* Restituisce i due fd su cui scrivere e leggere
---
## 4. Scheduling
* Per virtualizzare la CPU usiamo il sistema di _time sharing_
* Il meccanismo per cambiare processo in esecuzione si chiama __context-switch__
* La parte di kernel che si occupa di decidere cosa eseguire si chiama __scheduler__
* Ma come facciamo ad implementarlo __efficacemente__?
* Innanzitutto esitono due approcci per decidere se tenere un processo:
	* __Cooperativo__: finchè un processo esegue syscall, rimane ad eseguire
	* __Non Cooperativo__: un processo rimane in esecuzione fino allo scadere di un timer
---
* La sostituzione avviene salvando i registri del programma nell'apposito Kernel Stack
* Le cache non vengono salvate, causando un relativo rallentamento in seguito alla sostituzione
---
* Un processo può essere in più stati:
	* __Init__: è stato appena creato
	* __Running__: in esecuzione, ha accesso alla CPU
	* __Ready__: in esecuzione, attende di avere accesso alla CPU
	* __Blocked__: sta aspettando dei dati (tipicamente I/O) prima di continuare l'esecuzione
---
* Algoritmi per lo scheduling
* __FIFO__:
	* I programmi vengono eseguiti in ordine di arrivo, e conclusi prima di passare ad un altro
	* Problematico nel caso di programmi molto __lunghi__ (effetto convoglio)
*  __Shortest-Job First__ (SJF):
	* Vengono conclusi prima i programmi più corti, fino alla fine
	* Nel caso arrivi un programma più __corto__ poco dopo?
* __Shortest Time-To-Completion First__ (STCF): 
	* Si cerca di completare il programma che ci mette meno a terminare. Nel caso ne arrivi uno nuovo più breve, switchiamo
	* Ma se consideriamo il _response time_?
* __Round-Robin__ (RR):
	* Ogni processo ha un fettina di tempo d'esecuzione, scaduto quel tempo passa ad un altro, in ordine
	* In questo modo ottmizziamo il tempo di risposta (Tutti hanno circa la stessa durata) ma peggioriamo il Turnaround Time, dato che i programmi brevi vengono terribilmente penalizzati
	* E se un programma fa __I/O__?
* __Multi-level Feedback Queue__ (MLFQ):
	* Suddividiamo i processi, in base alla priorità, in più code
	* La priorità viene decisa in base a come si è comportato in precedenza.
	* Inizialmente un processo entra con priorità massima. Se sfrutta tutto il quanto di tempo (relativo alla sua priorità) ad esso riservato, cala di priorità
	* Ogni tot, ridiamo a tutti la priorità massima, per favorire i processi più "vecchi"
	* Se dobbiamo scegliere fra due processi
		* Se p(A) > p(B) gira A
		* Se p(A) = p(B) usiamo il __RR__ 
* __Completely Fair Scheduler__ (CFS):
	* Assegna ad ogni processo un `vruntime`, una variabile che indica quanto tempo hanno passato in esecuzione.
	* In base ad esso, decide di mandare in esecuzione il programma con `vruntime` più piccolo, per un tempo `sched_latency/n`, dove `n` è il numero di processi al momento
	* Una volta eseguito, il suo `vruntime` viene aggiornato, in base al tempo passato ed in base al numero di processi in corso
		* I processi vengono conservati in BST rossi e neri, così da ritrovare facilmente il processo con `vruntime` minore
	* In caso un processo faccia molto I/O? il suo `vruntime` rimarrebbe ingiustamente basso...
	* Quanto torna in esecuzione lo ricalcoliamo come il minimo degli altri
		* Questo algoritmo __non__ è molto __conveniente__ per i programmi che fanno molto __I/O__

---
## 5. Multi-Threading
* Un thread è un flusso di esecuzione
	* Come se fosse un secondo processo che condivide lo spazio d'esecuzione
	* Possiede un errno ed uno stack propri
	* Sono soggetti ai Context-Switch
* Il TLS (Thread Local Space) è uno spazio (logicamente) locale ad ogni thread. Organizzato come un dizionario, possiamo salvarci dei dati come `void *` 
---
* I thread vengono principalmente usati per compiere processi parallelamente, e sfruttare il downtime durante l'I/O
* Si possono creare con __`pthread_create`__
* Si può uscire da un thread con __`pthread_exit`__
* E attenderne la terminazione con __`pthread_join`__
* I valori di ritorno sono `void *`
---
* Un grosso problema dei thread sono gli accessi alle risorse condivise. le parti di codice che li compiono vengono definite sezioni critiche
* Si dice _race condition_ quando il risultato finale di alcune operazioni dipende dalla temporizzazione dei thread
* Per evitare questi problemi, bisogna __sincronizzare__ i thread nell'accedere ai dati condivisi
* Una prima soluzione sono i __Lock__
	* Implementati dai mutex in pthread, si dichiara con `pthread_mutex_t`
	* Viene acquisito da un thread per accedere ai dati, e va rilasciato il prima possibile
* Spinlock (DA VEDERE)
---
* Le cosiddette funzioni "__rientranti__" vengono considerate thread safe. Sono pensate per poter essere facilmente interrotte, e solitamente il loro funzionamento non include sezioni critiche, tramite l'utilizzo di lock o di TLS
---
* Ci sono numerosi bug che possono verificarsi a causa dell'utilizzo di più thread. Uno di questi è il __Deadlock__:
	* Una situzione in cui due thread attendono a vicenda un lock dall'altro
	* Per impedirlo, possiamo fare in modo che i programmi non conservino lcok quando non ne hanno più bisogno, o che li acquisiscano in un ordine preciso
---
## 6. Sicurezza
* La sicurezza di un SO si basa su tre fattori:
	* __Confidenzialità__
	* __Integrità__
	* __Disponibilità__
* In generale, condividere file, controllando con chi vengono condivisi
---
* Quando un programma cerca di eseguire una syscall, oltre a valutare la correttezza della chiamata, il sistema deve controllare che essa rispetti la __politica di sicurezza__ del sistema. Bisogna considerare il __contesto__
* Gestiremo le richieste tramite le 3 A:
	* __Autenticazione__
	* __Autorizzazione__
	* __Accounting__ (contabilità)
---
* In Unix, gli utenti vengono riconosciuti da un nome __utente__ e da una __password__. Le informazioni su di essi si trovano in `/etc/passwd` e `/etc/shadow`
* Il sistema identifica gli utenti ed i gruppi tramite due numeri, gli __UID__ e i GID
* UID = 0 corrisponde all'utente `root`, amministratore
* A sua volta, i processi si dividono in privilegiati e non-privilegiati, in base allo UID del "creatore"
---
* Come gestire chi fa cosa?
	* __Access Control List__
		* Ogni oggetto ha una lista in cui si indica cosa possa fare ogni utente
		* In unix esiste una versione ottimizzata
	* __Capabilities__
		* Ogni oggetto ha delle "chiavi" che ne permettono l'uso
* Chi decide chi può fare cosa?
	* __DAC__: Il proprietario
	* __MAC__: un autorità superiore
* Solitamente si usa DAC, ma comunque `root` puà leggere qualunque cosa di solito
---
* Principio del __minimo__ privilegio:
	* Nessun processo dovrebbe mai poter accedere a più risorse del minimo indispensabile per il suo corretto funzionamento.
---
* Ogni processo possiede tre UIDs
	* __Real__ UID: Il proprietario
	* __Effective__ UID: Usato per determinare i permessi di accesso
	* __Saved__ UID
* Al login sono tutti uguali
* Tramite `setuid` possiamo modificare EUID scambiandolo con uno degli altri due
* Se un file eseguibile ha il bit `set-userid` abilitato, EUID e SUID diventano uguali a RUID
---
* Il comando `chroot` permette di modificare la __root__ di un processo
* Questo permette di chiuderlo in una _chroot-jail_, evitando che acceda a risorse a lui non riservate sul FS
* Antenati dei __Container__
---
* Tipi di attacchi:
	* __Privilege Escalation__: Sfruttiamo debolezze per diventare root
	* __Injection__: Iniettiamo nostro codice in programmi già privilegiati

---
## 7. File System
* I __dischi__ (dispositivi a blocchi) sono unità di memoria secondaria strutturate come una serie di __settori__ (di solito da 512 byte)
* Per accedere a questi usiamo degli indirizzi (Tipo RAM paginata)
* È molto __costoso__ accedere sul disco, quindi i sistemi UNIX hanno una __cache__ in cui salvare i dati letti. Le eventuali modifiche verranno eseguite su di essa, ed al momento di __espellere__ l'unità, copiate su disco
	* Possiamo forzare la scrittura con `sync`
---
* Per vari motivi, si può voler __partizionare__ un disco, dividendolo in più sezioni
* Gli standard più utilizzati sono:
	* __Master Boot Record__ (MBR)
		* Massimo 4 partizioni, estendibili
	* __GUID Partition Table__ (GPT)
		* Quante partizioni vuoi, identificate da un UUID
* In UNIX, file speciali corrispondono ai dispositivi di I/O (compresi i dischi) identificati da un __Major__ (Tipo di dispositivo) e __Minor__ (Il dispositivo stesso) number (Es, `/dev/sda`) 
---
* Per utilizzare un dispositivo a blocchi bisogna "__montarlo__", collegandolo al file system preesistente. Si può agganciare tramite il comando `mount`
* Oggi giorno i dispositivi vengono identificati tramite UUID. Quando vengono collegati o scollegati viene inviato un segnale dal kernel, il quale può essere facilmente intercettato dai sistemi che ne hanno bisogno
---
* Per accedere ai dati, esistono due astrazioni:
	* __File__: una sequenza di byte 
	* __Directory__: contenitori logici di file e directory (ricorsivamente)
* Per poterli creare al di sopra di un dispositivo a blocchi, c'è bisogno di implementare un _file-system_, una struttura dati che gestisce dati e metadati
* Formattare un disco vuol dire preparare questa struttura. Esistono molti formati differenti, noi studieremo il vsfs, il Very Simple File System
	* Ovviamente per accedere al disco, saranno necessarie anche le tabelle degli FD e dei file aperti
---
* Immaginiamo di avere un disco da 4kb
* Parte di esso dovrà essere riservato a conservare i __metadati__ dei dati conservati
* Ogni file avrà un __inode__, conservato in una tabella di lunghezza fissa (numero massimo di file fissato). Poi un __inode bitmap__, che indica quali di questi inode è utilizzato, una __data bitmap__, che indica quanti blocchi dato vengono usati
* Infine un __superblocco__, contenente tutte le info sul FS
---
* Ogni __inode__ contiene tutte le informazioni di un file, TRANNE il __nome__
* L'inode contiene inoltre __puntatori__ ai __dati__ del file. Ci saranno un numero piccolo di puntatori a dati veri, poi i restanti puntano ad ulteriori gruppi di puntatori, i quali potranno puntare anche ad altri blocchi, e così via
* Le __directory__ contengono associazioni fra __nomi__ e __inode__
* Queste associazioni sono i cosidetti __hard link__, nomi aggiunti ad un file
* Da non confondere con i __symbolic link__, file che contengono un percorso, possibilmente inesistente
	* Entrambi vengono creati con `ln`
---
* Se si devono aggiornare parti della struttura dati del FS, cosa succede se manca la corrente a metà?
* Possiamo __controllare__ l'integrità del disco con `fsck` , ma è molto lento...
* Meglio usare il metodo di __Journaling__: Ogni volta che monto un disco lo segno come "sporco" e scrivo separatamente le modifiche che eseguo. Quando lo smonto, lo segno come "pulito"
* Se crasha, il disco deve essere sporco, e quindi non è integro. Le modifiche segnate nel log verranno reapplicate