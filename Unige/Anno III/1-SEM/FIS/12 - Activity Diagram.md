+ Diagramma di Modellazione **Dinamica**
+ Sono diagrammi **poliedrici**, che possiamo descrivere come una standardizzazione ed **evoluzione** dei classici **flowchart**, aggiungendo il supporto all'elaborazione concorrente/parallela 
+ Descrivono come viene svolta un’attività relativa ad una qualsiasi entità, ovvero quale è il flusso di azioni che devono accadere, ed in quale ordine
+ Vengono usati in vari modi lungo quasi tutte le fasi di sviluppo
+ Si usano diversi tipi di **nodi** e **flussi** per specificare il comportamento:
![[ADNodi.png]]
+ Nei nodi azione si possono specificare i dettagli, o invocare un altra attività tramite il simbolo **rake**
---
+ Durante lo svolgersi dell'attività, si generano e trasportano diversi **token**, specificati. Un nodo azione viene eseguito solo quando sono presenti tutti i token su tutti i suoi archi in entrata.
+ I nodi finali ed iniziali sono rappresentati da pallini neri. Il primo è unico, i secondi multipli e facoltativi
---
+ In un nodo decisione, se più di una guardia è vera, viene fatta una scelta non deterministica
+ Oltre ai nodi decisione, esistono i nodi **fusione**, in cui i flussi possono riunirsi
+ I nodi Fork e Join gestiscono il parallelismo
+ I nodi **finali di flusso** terminano solo un flusso, e non tutta l'attività
+ I nodi **oggetto** sono utilizzabili per modellare l'input ed output. Questi possono possedere stati, coerenti con quelli della macchina a stati ad esso associato
+ Il flusso può essere suddiviso in **swim-lanes**, sezioni che specificano chi è l'esecutore dell'attività
+ I nodi **ricezione** gestiscono gli eventi (*da rivedere*)
+ **Input ed output** sono rappresentati com nodi oggetto sui bordi dell'attività
+ Le **regioni interrompibili** specificano sezioni in cui si può forzare l'interruzione dell'attività sulla base di un evento