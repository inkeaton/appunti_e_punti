    Allo scopo di permettere il funzionamento di più programmi simultaneamente, viene implementato un sistema detto VIRTUALIZZAZIONE della CPU 

    Viene fatto in modo che ogni programma "veda" solo una parte della memoria, ad esso riservata, simulando la presenza di più macchine virtuali sulla nostra macchina fisica, ognuna impegnata ad eseguire un programma 

 

    Questa tecnologia permette anche l'utilizzo di più OS 
    Per gestirli viene implementato un programma detto HYPERVISOR 

    Questo gestisce, ad esempio, la modalità privilegiata 

        Normalmente il sistema girerà in modalità USR. Quando un OS richiede un'istruzione privilegiata,  viene inviata una TRAP. 

        Il gestore "simulerà" il passaggio alla modalità SYS, riempendo i campi dei sistemi nel modo richiesto 

 

    Un "evoluzione" è l'EMULATORE 

    Grazie a questo programma, il computer è capace di eseguire istruzioni scritte per computer dotati di CPU e architetture diverse 

        Quando una di queste istruzioni viene eseguita, viene inviata una TRAP 

        Questa fa intervenire l'EMULATORE, il quale, in più cicli di CLOCK, riempie i registri nel modo richiesto, "traducendo" l'istruzione 

    Quindi, nonostante il tempo richiesto sia superiore, è possibile eseguire istruzioni scritte per sistemi diversi 

 

    Nella struttura del computer, le richieste privilegiate funzionano tramite le TRAP, chiamate ora SYSTEM CALL, le quali alzano il livello di privilegio quando necessario 

    Vengono quindi implementate le cosiddette TRAP ESPLICITE, segnali previsti dal programma, utilizzati solo per aumentare il livello di privilegio 

![Schermata da 2022-02-24 11-37-18.png](../../_resources/Schermata da 2022-02-24 11-37-18.png)

    Nel secondo e nel terzo vengono mostrati due tipi diversi di HYPERVISOR, detti TIPO 1 e TIPO 2 

    Il T2 userà delle SYSTEM CALL per virtualizzare per il secondo sistema 

    Sia l'OS kernel che l'HYPERVISOR virtualizzano per altre applicazioni, la differenza sta nell'interfaccia dei due, più elevata nel primo 

    Di solito un OS è dotato di un A.P.I., un interfaccia di programmazione, utilizzabile per scrivere ed eseguire programmi 