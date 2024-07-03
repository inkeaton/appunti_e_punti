+ In questo foglio cercheremo di riassumere i contenuti del corso di **Programmazione Concorrente e Algoritmi Distribuiti**
+ Questo foglio è principalmente pensato per prepararsi all'esame. A tal scopo, potrebbero non essere elencate tutte le parti del corso effettuate, ma solo quelle necessarie al compimento dell'esame
---
# 1 - Teoria
---
## Interleaving e Mutua Esclusione
+ Dati due processi paralleli, eseguiti in interleaving, possiamo richiedere tre proprietà dalla loro esecuzione:
	+ **Mutua Esclusione**: i due processi non accederanno mai allo stesso tempo alle risorse condivise, la cosiddetta "sezione critica"
	+ **Assenza di Deadlock**: i due processi non rimarranno mai in stallo, incapaci di proseguire l'esecuzione
	+ **Assenza di Starvation**: Nessuno dei due processi monopolizzerà il tempo d'esecuzione
+ Per verificare queste proprietà sugli algoritmi, useremo dei diagrammi di stato. In essi:
	+ Uno stato è una tupla contenente:
		+ Un puntatore all'istruzione per ogni processo coinvolto
		+ Un valore per ogni variabile condivisa
	+ Un cambio di stato è presente se si può passare allo stato successivo tramite l'istruzione puntata
+ Un modo per verificare le proprietà è usare un **invariante**, una proprietà che è sempre verificata. CI può essere utile nel verificare le proprietà discusse
+ Dei consigli:
	+ Considerare più cicli consecutivi
	+ Controllare che le variabili vengano resettate ad ogni ciclo
### Algoritmo di Dekker
![[dekker_alg.png]]
Verifica:
+ Mutua Esclusione? **SI**
+ Assenza di Deadlock? **SI**
+ Assenza di Starvation? **SI** se:
	+ I processi sono equi nell'esecuzione
	+ La sezione critica termina sempre con l'esecuzione del post-protocollo
### Algoritmo di Peterson
![[peterson_alg.png]]
Verifica:
+ Mutua Esclusione? **SI**
+ Assenza di Deadlock? **SI**
+ Assenza di Starvation? **SI** se:
	+ I processi sono equi nell'esecuzione
	+ La sezione critica termina sempre con l'esecuzione del post-protocollo
+ Esso può essere espanso in versioni a più processi:
#### Algoritmo Filter Lock-Peterson
+ Generalizzazione dell'algoritmo di Peterson per $n > 2$ processi
+ L'idea è fermare in un livello almeno un processo per volta. Quello che passa tutti i livelli accede alla sezione critica
![[filter_lock_alg.png]]
Verifica:
+ Mutua Esclusione? **SI**
+ Assenza di Deadlock? **BOH**
+ Assenza di Starvation? **SI** se:
	+ I processi sono equi nell'esecuzione
	+ La sezione critica termina sempre con l'esecuzione del post-protocollo
#### Algoritmo del Torneo-Peterson
+ Generalizzazione dell'algoritmo di Peterson per $n > 2$ processi
+ L'idea è fare Peterson a "turno" con ogni coppia di processi, chi vince continua, finché non ne abbiamo uno solo
![[tournament_alg.png]]
Verifica:
+ Mutua Esclusione? **SI**
+ Assenza di Deadlock? **BOH**
+ Assenza di Starvation? **SI** se:
	+ I processi sono equi nell'esecuzione
	+ La sezione critica termina sempre con l'esecuzione del post-protocollo
### Algoritmo del Fornaio
+ L'idea è che ogni processo che deve accedere alla sezione critica si "mette in coda", prendendo un "biglietto" numerato
+ Il processo col biglietto col numero minore verrà servito prima
![[baker_alg.png]]
Verifica:
+ Mutua Esclusione? **SI**
+ Assenza di Deadlock? **SI**
+ Assenza di Starvation? **SI** se:
	+ I processi sono equi nell'esecuzione
	+ La sezione critica termina sempre con l'esecuzione del post-protocollo

---
### Metodi Utili
#### Test and Set
![[test_and_set_alg.png]]
#### Semafori
---
## Message Passing
### Algoritmo di Lamport
+ Algoritmo per la sincronizzazione nei sistemi distribuiti
+ L'idea è che per richiedere l'accesso alla sezione critica, devo inviare un messaggio di richiesta ad ognuno degli altri sistemi, con timestamp, ed aspettare la risposta
+ Sarà autorizzato colui che ha il timestamp più vecchio fra tutte le richieste
![[lamport_alg_1.png]]
![[lamport_alg_2.png]]
Verifica:
+ Mutua Esclusione? **SI**
+ Assenza di Deadlock? **SI**
+ Assenza di Starvation? **SI**
### Algoritmo di Ricart-Agrawala
+ Usa un idea simile al precedente, ma cerca di limitare il numero di messaggi inviati
+ Dopo aver ricevuto una richiesta, rispondo solo se non devo accedere alla sezione critica, o se ho fatto richiesta dopo di essa
+ Accedo alla sezione critica solo se ricevo la risposta da tutti
![[ricart_agrawala_alg_1.png]]
![[ricart_agrawala_alg_2.png]]
Verifica:
+ Mutua Esclusione? **SI**
+ Assenza di Deadlock? **SI**
+ Assenza di Starvation? **SI**
---
## Verifica di Sistemi
### Strutture di Kripke
+ Una struttura di Kripke è un grafo orientato semplice dove:
	+ I vertici rappresentano gli **stati** di un sistema
	+ Ogni stato è etichettato con le sue **proposte atomiche,** proprietà vere all'interno di esso
	+ Gli archi rappresentano le **transizioni** fra stati
+ Dato $PA$, insieme di proposte atomiche, esso ha $2^{PA}$ sottoinsiemi, e quindi possibili stati
+ Data una struttura $KS$, $Exec(KS)$ è l'insieme delle possibili **esecuzioni** su essa
+ In particolare, una traccia $Trace(KS)$ è una sequenza infinita di sottoinsiemi di $PA$
+ Un **proprietà temporale lineare** $P$ su $PA$ è un sotto-insieme di $(2^{PA})^\omega$, un insieme di tracce infinite 
	+ Diremo che $KS$ soddisfa $P$ se e solo se tutte le sue tracce sono in $P$
+ Esistono alcune proprietà temporali lineari particolari:
#### Safety
+ Sono un insieme di proprietà che verificano la seguente proposta:
	+ Se una traccia non è nella proprietà allora esiste un prefisso finito tale che ogni traccia con lo stesso prefisso non è nella proprietà
		+ "Non puoi ripararla"
#### Liveness
+ Sono un insieme di proprietà che verificano la seguente proposta:
	+ Per ogni sequenza finita, esiste un postfisso infinito capace di rendere l'unione delle due appartenente alla proprietà
		+ "Puoi sempre ripararla"

### Automi di Büchi
+ Un buon modo per descrivere una proprietà lineare temporale è quella di usare un automa
+ Un automa di Büchi (BA) è un tupla del tipo:
	+ $BA : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Cyan}{F}, \textcolor{Mulberry}{\delta})$ 
		+ $\textcolor{Apricot}{Q}$ è un insieme finito di **stati**
		+ $\textcolor{LimeGreen}{\Sigma}$ è l'**alfabeto** usato dalla macchina
		+ $\textcolor{WildStrawberry}{q_0}$ è l'insieme degli **stati iniziali** della macchina
		+ $\textcolor{Cyan}{F}$ è l'insieme degli **stati accettanti** della macchina
		+ $\textcolor{Mulberry}{\delta}$ è la **funzione di transizione**, il funzionamento ad ogni passo, dell'automa
+ Un esecuzione di un automa su una sequenza infinita è a sua volta una sequenza infinita di stati
+ L'esecuzione viene detta accettante se esiste un numero infinito tale che $q_{\infty} \in F$. Viene indicato come $L_{\omega}(A)$ l'insieme delle esecuzioni accettanti, il **linguaggio** dell'automa
+ Una PLT viene detta **regolare** se esiste un automa A tale che $P = L_{\omega}(A)$
+ Possiamo controllare se le tracce di una struttura di Kripke soddisfano una proprietà regolare P usando questi automi
	+ Prendiamo $\bar{P} = (2^{PA})^\omega \backslash P$, anch'essa regolare
	+ Abbiamo che $Trace(KS)$ soddisfa $P$ se e solo se $Trace(KS) \cap \bar{P} = \emptyset$
	+ Siccome $\bar{P}$ è regolare, possiamo costruire il suo automa $\bar{A}$
	+ Controlleremo dunque se l'intersezione fra $Trace(KS)$ ed il linguaggio $L_{\omega}(\bar{A})$ è vuota
		+ Ovvero, se esiste un ciclo infinito contenente lo stato finale
+ Per farlo costruiremo un nuovo grafo $KS \otimes \bar{A}$
### Sintassi LTL
+ La logica temporale lineare (LTL) permette di descrivere delle proprietà sulle tracce di un sistema (un sottoinsieme di $(2^{PA})^\omega$)
+ Abbiamo i seguenti simboli:
	+ $X \phi$ vuol dire "nel prossimo stato vale $\phi$"
	+ $\phi \cup \psi$ vuol dire "fino a che non ho uno stato con $\psi$ avrò stati con  $\phi$"
	+  $F \phi$ vuol dire "in uno stato futuro vale $\phi$"
	+  $G \phi$ vuol dire "per ogni stato vale $\phi$"
		+ $GF \phi$ vuol dire "$\phi$ vale infinitamente spesso"
		+ $FG \phi$ vuol dire "a partire da uno stato futuro varrà sempre $\phi$"
![[model_checking.png]]
# 2 - Codice
---
## C
### Creare Processi
### Thread e Locks
### Variabili Condizionali
### Barriere
### Semafori
## Java
### Thread e Runnable
### Locks
### Comunicazione in Rete