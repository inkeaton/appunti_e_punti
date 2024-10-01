* Si può notare che è abbastanza stupido avere un __singolo__ server __root__, in quanto questi può __sovraccaricarsi__ facilmente
* A tal scopo furono inizialmente definiti __13__ server root, a cui furono associati 13 diversi indirizzi IP
* Oggi giorno, esistono __migliaia__ di diversi server root, i quali sono sempre associati a questi 13. tramite il sistema __Anycast__, la __rete__ individua il server root più __vicino__ al client ed invia la sua richiesta ad esso
* I server root vengono __gestiti__ dai __Service Provider__, società come ad esempio Fastweb.
* L'instradamento di queste query DNS utilizza un sistema diverso da quello IP
* Anche i server __TLD__ utilizzano questo __sistema__. A livello __autoritativo__, __decide l'azienda__ privata, in base a fattori come numero di accessi o origine geografica dei client
---
* I server DNS locali possiedono una __cache__ in cui conervare indirizzi precedentemente tradotti. A questi viene associato un __timeout__ di validità, così da evitare la consegna di indirizzi obsoleti ai client
* La risposta in cache viene sempre inviata come risposta __non autoritativa__. Insieme ad essa inviamo una seconda __risposta autoritativa__, ovvero l'indirizzo del __server autoritativo__ superiore
* In questo modo, il client può controllare la validità dell'indirizzo ricevuto chiedendolo a questo secondo indirizzo
---
* Le comunicazioni UDP non sono molto sicure. Una tecnica molto semplice che sfrutta le falle di queste sistema è l'__IP Spoofing__: questi consiste nell'inviare messaggi con un falso indirizzo IP del mittente, fingendosi qualcos'altro
* Potrei usare questo sistema per inviare al server DNS locale indirizzi tradotti falsi (__Cache Poisoning__)
* Si usano due metodi per __combattere__ questi attacchi:
	* Il primo consiste nel assegnare alla richiesta DNS un __ID__ di 16 bit. La risposta dovrà avre lo stesso ID, e sarà complicato per l'hacker indovinare il numero giusto
	* Il secondo consiste nel comunicare sulla stessa __porta__ randomizzata, aggiungendo degli ipotetici 16 bit in più