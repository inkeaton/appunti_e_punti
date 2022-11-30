* Le LISTE sono strutture dati formate da una sequela di struct denominate "celle". Qui riportiamo un esempio di una cella di lista semplice, per immagazzinare interi, ed un puntatore a cella:
```
struct {
	int information;
	cell* next;
}

cell * lista;
```

* Questo puntatore sarà la nostra vera e propria "lista", poichè punterà alla prima cella di questa "catena"
* Ogni cella punterà poi alla successiva, fino all'ultima che punterà a `nullptr`
* Una lista vuota verrà quindi riconosciuta da puntare a `nullptr`
* Gli elementi vengono solitamente aggiunti in testa
* Oltre a questo tipo di liste esistono le **liste circolari**, le quali hanno la differenza di avere l'ultima cella che punta alla prima cella, creando un circolo
* Infine ci sono le **liste circolari con sentinella**, le quali hanno la particolarità di possedere sempre una cella, la cosidetta "sentinella": una lista vuotà verrà riconosciuta dal possedere solo questa cella che punta a se stessa
* Per aggiungere elementi, questi verranno immessi subito dopo la sentinella, la quale sarà sempre la prima cella
* Questo permette di ridurre il numero di modifche del valore del puntatore iniziale