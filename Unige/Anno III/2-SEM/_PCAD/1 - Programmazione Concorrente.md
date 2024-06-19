+ Fin dai primi anni 2000, si è cominciato a sviluppare la programmazione concorrente, allo scopo di superare i limiti della legge di Moore
+ È nato quindi lo studio della **programmazione concorrente**, l'esecuzione in contemporanea di processi che condividono specifiche risorse.
+ Questo è un processo **complicato**, in quanto l'**ordine** d'esecuzione delle istruzioni atomiche dei processi viene deciso, apparentemente in modo **casuale**, dal processore della macchina
+ Questo rende impossibile prevedere l'accesso alle componenti condivise, e **causa problemi di sincronizzazione** fra i due processi
+ Numerosi sono quindi i metodi utilizzati per risolvere queste complicazioni e sfruttare al massimo le possibilità del calcolo parallelo
---
+ Un **programma concorrente** è un **insieme di processi** eseguiti **in parallelo**, su uno o più processori, in grado di **comunicare** fra loro, tramite un sistema di messaggistica o risorse condivise
+ Ognuno dei processi può esser visto come un **insieme di istruzioni atomiche**, ed un puntatore che punta alla prossima istruzione da eseguire