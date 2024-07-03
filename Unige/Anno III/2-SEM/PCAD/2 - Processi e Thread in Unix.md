+ In C, possiamo creare un **nuovo processo** grazie alla funzione `fork()`
```C
pid_t fork(void);    // create new process

pid_t getpid(void);  // get my pid
pid_t getppid(void); // get my father pid
```
+ Essa crea un processo **figlio**, **copia** di quello **padre**. Tramite il `pid` ritornato, il codice potrà gestire il diverso comportamento fra padre e figlio
+ Le **variabili non sono condivise** fra padre e figlio, ma sono una copia di quelle del padre
---
+ Se invece volessimo far **eseguire un comando** preciso potremmo utilizzare `exevp()`
```C
int execvp(const char *file, char *const argv[]);
```
+ Questo però **non crea un nuovo processo**, ma **sostituisce** quello chiamante
---
+ Per **comunicare** fra processi possiamo usare delle **pipe**, canali unidirezionali, utilizzabili come file descriptor
```C
int pipe(int fds[2]) // Scrivi in 1, leggi in 0
```
+ Queste potrebbero essere utilizzate **fra padre e figlio**: essendo indirizzi, essi sono condivisi fra i due. Devono ricordarsi di chiudere le rispettive parti non utilizzate
---
+ Questi metodi sono utili, ma **nessuno** di loro permette di **condividere variabili**
+ Utilizziamo quindi i **thread**
+ Essi sono multipli fili d'esecuzione all'interno di un processo. 
+ Ognuno possiede un **puntatore d'esecuzione** ed uno **stack** in cui memorizzare variabili a se uniche
+ Esiste una libreria specifica in C, `pthread.h`
+ Per creare un thread, si usa :
```C
int pthread_create { 
	pthread_t *thread, //Per ricordare i dati del nuovo thread 
	const pthread_attr_t *attr, // Attributi dello thread 
	void *(*start_routine) (void *), // Funzione da eseguire 
	void *arg; // Argomenti della funzione
}
```
+ Certe volte è necessario attendere il termine dell'esecuzione di uno di questi thread
+ Si può fare tramite la seguente funzione
```C
int pthread_join(pthread_t thread, void **value_ptr);
```
---
+ Come facciamo a proteggere i dati condivisi fra thread?
+ Ci sono più metodi. Uno molto utilizzato è quello dei **mutex lock**
+ Per poter accedere ad un dato, uno deve richiedere un lock, e poi rilasciarlo quando non deve più usarlo
+ Questo lock sono condivisi fra thread
+ Essi sono del tipo:
```C
pthread_mutex_t lock;

lock=PTHREAD_MUTEX_INITIALIZER; // inizializzazione

// prenderlo
int pthread_mutex_lock(pthread_mutex_t *lock);
// rilasciarlo
int pthread_mutex_unlock(pthread_mutex_t *lock);
```
+ *Nelle slide ci sono i thread in Java*
