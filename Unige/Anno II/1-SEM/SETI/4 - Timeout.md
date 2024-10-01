* Dato che ad ogni messaggio è richiesto un ACK, spesso si inviano informazioni dentro ad un ACK che sarebbe normalmente vuoto (__Piggy Bagging__)
* Anche il protocollo TCP usa il __Timeout__, codificato nel RFC 6298. Esso lo calcola in base a due valori:
	* La __media del tempo necessario ad inviare un messaggio__ e ricevere un ACK. Questa è mobile, tiene maggiormente conto del valore nuovo della media, e viene aggiornata ad ogni invio. $\alpha$ ha valore $\frac{1}{8}$ 
		* $Nuova stima = ( 1 - \alpha) \cdot stima precedente + \alpha \cdot nuovo valore$  
	* La __deviazione__ dei valori dal valore medio. $\beta$ è $\frac{1}{4}$ 
		* $dev = (1 - \beta) \cdot devprecedente + \beta \cdot |stima - nuovo valore|$ 
* Il __timeout__ avrà alla fine valore:
	* $timeout = stima + 4 \cdot dev$
* Questo valore viene calcolato ad ogni ACK.
* In caso un timeout __scada__, si __raddoppia__ il valore di timeout, mantenendo il calcolo di stima e dev con i precedenti valori
---
* In caso un mittente voglia inviare un numero molto grande di dati, egli dovrà farlo inviando un gran numero di datagrammi separati. In questi casi è stupido pensare di inviare ACK per ognuno di questi: possiamo pensare di __inviare ack solo ogni tot pacchetti__. 
* Nel caso i pacchetti siano in disordine, possiamo __aspettare__ l'arrivo dei giusti pacchetti prima di inviare un ACK. È anche possibile comunicare la __mancata ricezione__ tramite il __rinvio__ di ACK precedentemente inviati, arrivando spesso prima di un timeout e velocizzando il rinvio di pacchetti