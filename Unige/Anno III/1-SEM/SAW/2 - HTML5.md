+ HTML (**H**yper**T**ext **M**arkup **L**anguage) è un linguaggio di **markup** che, come LaTeX e Markdown, viene utilizzato per comunicare al browser **l'organizzazione di un documento di testo**
+ I browser odierni non sono altro che interpreti di HTML
+ Il linguaggio funziona tramite **tag**, istruzioni che esplicitano la funzione od organizzazione del contenuto
+ Ai tag possono essere passati degli **attributi**
---
+ I **commenti** vengono inseriti con `<! ... >`
+ Ogni documento HTML inizia con la **dichiarazione del DOCTYPE**
+ In seguito, viene aperto il tag `<html>`, a cui si passa l'attributo `lang`, il quale indica la **lingua** della pagina, necessario al browser vocale
+ In seguito, si aprono **due sezioni**:
	+ `head`, che contiene i **metadati** della pagina
	+ `body`, che contiene il **contenuto** vero e proprio
```html
<!DOCTYPE html> 
<html lang="en"> 
	<head> 
		<title>My first document</title> 
	</head> 
	<body> 
		<h1>My First Heading</h1> 
		<p>My first paragraph.</p> 
	</body> 
</html>
```
---
+ I colori possono essere rappresentati tramite RGB, RGBA, HEX, ma recentemente si preferisce occuparsi della personalizzazione della pagina nei fogli di stile **CSS**
	+ *Per realizzare la scala dei grigi in RGB, basta usare i colori con quantità di colore pari*
	+ *È necessario che testo e sfondo abbiamo un buon contrasto, almeno 5:1, affinché siano facilmente leggibili da persona con difficoltà visive*
---
+ Per creare **titoli** si usano i tag `<h1> ... <h6>`, in ordine di grandezza decrescente
+ Per i **paragrafi** `<p>`
	+ Si può passare l'attributo `align` per l'allineamento
+ Per i **formati** possiamo usare
	+ `<b>` o `<strong>` per il **grassetto**
	+ `<i>` o `<em` per il **corsivo**
+ Per le **liste**
	+ `<ul>` per una lista **puntata**
	+ `<ol>` per una lista **numerata**
	+ `<li>` per l'**elemento** di una lista
+ Le **tabelle** venivano una volta usate per organizzare il testo, sono state soppiantate da div, span e tag semantici
---
+ Per le **immagini** usiamo il tag `<img>`
	+ l'attributo `src` indica il **path** dell'immagine, preferibilmente relativo
	+ l'attributo `alt`, la **descrizione** dell'immagine, per il browser locale
```html
<img src=”images/boccadasse.png” 
	 alt=”Landscape of Boccadasse”>
```
+ Per gli **audio** usiamo `<audio controls>`
	+ il tag `controls` da al browser la possibilità di **controllare** il flusso
	+ L'attributo `autoplay` fa partire **automaticamente** l'audio
	+ `loop` lo fa **ripetere**
	+ Al suo interno elenchiamo le sorgenti audio con `<source>`
		+ L'attributo `src` indica il **path** all'audio
		+ L'attributo `type`, il **formato**
			+ I formati supportati sono MP3, WAV e Ogg
	+ Con `<p>` possiamo indicare un **messaggio d'errore**, in caso non sia supportato il tipo di audio
```html
<audio controls> 
	<source src="audio.ogg" type="audio/ogg"> 
	<source src="audio.mp3" type="audio/mpeg"> 
	<p>Il tuo browser non supporta il tag audio</p> 
</audio>
```
+ Per i **video** usiamo  `<video controls>`
	+ Gli attributi `width` e `height` indicano rispettivamente **larghezza** ed **altezza** del video
	+ L'attributo `autoplay` fa partire **automaticamente** l'audio
	+ il tag `<track>` permette di associare **sottotitoli**
	+ Al suo interno elenchiamo le sorgenti video con `<source>`
		+ L'attributo `src` indica il **path** all'video
		+ L'attributo `type`, il **formato**
			+ I formati supportati sono MP4, WebM e Ogg
	+ Con `<p>` possiamo indicare un **messaggio d'errore**, in caso non sia supportato il tipo di video
```html
<video width="320" height="240" controls> 
	<source src="movie.mp4" type="video/mp4"> 
	<source src="movie.ogv" type="video/ogv"> 
	<p>Il tuo browser non supporta il tag video</p> 
</video>
```
+ È possibile fare l'**embedding** di video di YouTube
+ I **link** possono essere inseriti con `<a>`
	+ L'attributo `href` indica l'**indirizzo** vero e proprio, locale o remoto
```HTML
<a href=”https://unige.it/”>
	visit unige website
</a>
```
---
+ I **moduli** o form sono oggetti usati per ricevere **informazioni dagli utenti**
+ Si creano con il tag `<form>`. Attributi fondamentali sono:
	+ `action` che indica l'**azione** da eseguire nell'invio, di solito un programma apposito
	+ `method`, che indica il **metodo HTTP** usato per inviate i dati
		+ **GET** è meno sicuro, e usato per la creazione di stringhe di query
		+ **POST** viene usato per informazioni sensibili
+ All'interno del modulo, si possono inserire diversi **campi input**, ognuno con diverse funzionalità specifiche in base al valore dell'attributo `type`
```html
<input type=”text”> 
<input type=”radio”> 
<input type=”checkbox”> 
<input type=”password”> 
<input type=”submit”> 
<input type=”reset”> 
<input type=”hidden”> 
<input type=”file”>
```
+ Per funzionare correttamente, ognuno di questi campi deve essere **etichettato** tramite l'attributo `name`
+ I dati inviati possono essere **preimpostati** (come nel caso di test a crocette) con l'attributo `value`
+ Recentemente, sono stati introdotti **nuovi valori** di `type`, con **nuove funzionalità**, ma che possono apparire **differenti** fra browser e browser
```html
<input type=”color”> 
<input type=”date”> 
<input type=”datetime”> 
<input type=”email”> 
<input type=”url”> 
<input type=”month”> 
<input type=”number”> 
<input type=”range”>
<input type=”search”>
<input type=”tel”>
<input type=”time”>
<input type=”week”>
```
+ Questi potrebbero offrire anche **funzionalità di filtraggio**, ma bisogna ricordarsi che queste avvengono solo **a livello client**, e che è necessario effettuare tali controlli anche a livello server
---
+ Si possono implementare **menu a tendina** tramite `<select>` e `<option>`
	+ `<select>` accetta l'attributo `size`, che indica quanti elementi mostrare in ogni momento, di default 1
+ Si possono implementare **caselle di testo** mediante `<textarea>`, ma ne esistono alcune con maggiori funzionalità di terze parti
	+ `cols` e `row` specificano le **dimensioni**
---
+ Ognuno degli elementi elencati ha una specifica visualizzazione standard
	+ Gli elementi **block** sono visualizzati sempre su una nuova riga
	+ Gli elementi **inline** occupano solo lo spazio necessario
+ Esistono due elementi, `<div>` e `<span>`, appartenenti alle rispettive due categorie, che vengono usati solo come scatole, per occupare spazio, e **gestire la posizione degli altri elementi**
+ Questi venivano spesso utilizzati per implementare **tableless layouts**, organizzazione delle pagine ottenute senza tabelle 
+ Oggigiorno si **preferisce** utilizzare **tag semantici** appropriati, così da agevolare l'utilizzo dei browser vocali
---
+ Un documento HTML viene organizzato in una struttura a **blocchi**

![[2023-09-28_16-21-43.png]]

+ Il browser gestisce questa struttura come fosse un albero, detto **DOM**. Ne genera **due**, uno per la pagina **grafica**, ed uno per la pagina d'**accessibilità**, per i browser vocali
