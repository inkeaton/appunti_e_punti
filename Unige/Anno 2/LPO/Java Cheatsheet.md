let rec dup x :
  [] -> [];;
| h:t -> h:h:(dup x);;#### Programmazione ad oggetti
* Java è un linguaggio di __programmazione ad oggetti__![[Pasted image 20230214122903.png]]
* Esso è strutturato tramite l'astrazione degli oggetti e dei metodi:
	* Un __oggetto__ è una struttura dati, accessibile tramite dei __metodi__, delle "funzioni" specifiche a quell' oggetto
	* Un __istanza__ è, appunto, un'istanza di quell'oggetto, ovvero una "variabile" unica, creata sulla base quell'oggetto. Una __classe__ è una blueprint, le istanze sono gli oggetti creati con quelle blueprint
* Esistono più tipi di metodi. Un esempio sono i metodi __query__, che ritornano valori all'interno dell'istanza, senza modificarla, e __modification__, che modificano le variabili interne
* I dati di un oggetto sono contenuti in __campi__, "variabili", solitamente modificabili
---
* Gli oggetti vengono creati dinamicamente ed allocati sull'heap, Ni linguaggi basati sulle classi
* esempio di una classe che rappresenta un timer
```java
public class TimerClass { // private field of the object = hidden internal state 

	private int time; // in seconds, invariant: 0 <= time <= 3600 

	// public instance methods = interface of visible operations public 

	boolean isRunning() { // ’this’ is the target of the method 
		return this.getTime() > 0; 
	} 

	public int getTime() { // ’this’ is the target of the method 
		return this.time; 
	} 

	public void tick() { // ’this’ is the target of the method 
		if (this.isRunning()) 
			this.time--; 
	} 

	public int reset(int minutes) { // ’this’ is the target of the method 
		if (minutes < 0 || minutes > 60) // Java exceptions are special objects 
			throw new IllegalArgumentException(); 
		int prevTime = this.getTime(); 
		this.time = minutes * 60; 
		return prevTime; 
	} 
}
```

---
* Istanze create dalla stessa classe condividono i metodi, ma hanno campi unici. 
* Le istanze vengono __deallocate__ __automaticamente__ in Java
---
* All'interno della classe, si usa `this` per riferirsi all'__oggetto stesso__
* Si possono anche usare metodi di oggetti differenti, passati come argomenti di un metodo
---
* Per __creare una nuova istanza__ di una classe si usa la parola `new`. Ritorna l'indirizzo alla memoria allocata all'oggetto. Possono essere passati __argomenti__ per inizializzare i campi
---
* Gli oggetti creati da una classe C hanno tipo dinamico C. In java si possono creare anche variabili statiche di tipo C

#### Campi
* Vengono usate come variabili, sona accessibili usando il punto
```java
public int getTime() {
	return this.time; // field ’time’ of ’this’ is read
}
```

* Si possono usare diverse __parole__ nella definizione per definire l'accessibilità di un campo:
	* `private` indica che è __accessibile__ solo all'__interno della classe__
	* `public` che è accessibile __anche al di fuori__

#### Eccezioni
* Le eccezioni sono __oggetti speciali__, generati tramite `throw`
* Sono gestite tramite i `try-catch`
```java 
try{
	readFile(fname);
}

catch(IOException e){
	readFile(defaultFile);
}

catch (Throwable e) {
	e.printStackTrace();
	error("Unexpected error.");
}
```

* Alcuni tipi d'eccezione predefiniti sono `Throwable`, `IOException`, `NullPointerException`.
* Si possono definire __nuovi tipi di eccezioni__ creando nuove classi speciali
---
#### Assert
* Utili metodi utilizzati per __debuggare__ il codice, attivabili tramite l'opzione `-ea`
* Ad esse vengono passate espressioni booleane. In caso di risultato negativo, escono dal programma con errore
```java
TimerClass t1 = new TimerClass(); 
t1.reset(1); // t1 reset to 1 minute 
int seconds = 0; 
while (t1.isRunning()) { 
	t1.tick(); // one second per tick seconds++; 
} 

assert seconds == 60; // expected to hold 
assert !t1.isRunning(); // expected to hold
```

---
* In Java, gli oggetti sono __reference__, indirizzi alla memoria in cui sono salvati. Perciò, le operazioni che lo riguardano avvengono per reference
```java
TimerClass t1 = new TimerClass();
TimerClass t2 = t1; // t2 and t1 refer to the same object
TimerClass t3 = null; // t3 refers to no object
assert t1 == t2 && t1 != t3;
assert t3.isRunning(); // NullPointerException!
```

* Un oggetto di classe C è di tipo __reference type__ di classe C

---
* Java utilizza una __semantica statica__ con una regola: Il tipo statico di un oggetto deve essere compatibile con il tipo della sua dichiarazione
* Per controllare i tipi dinamici si può usare `instanceof` insieme ad `assert`
```java
TimerClass t1 = new TimerClass(); 
AnotherTimerClass t2 = new AnotherTimerClass(); 

assert t1 instanceof TimerClass; 
assert t2 instanceof AnotherTimerClass; 
assert !(null instanceof TimerClass); // null does not refer to any object 
assert !(null instanceof AnotherTimerClass); // null does not refer to any object
```

---
* Nell'__ideare una classe__, dobbiamo assicurare 3 condizioni:
	* La classe è stata __definita__ correttamente
	* I metodi __funzionano__ come intesi
	* Lo stato di un'istanza deve essere sempre __valido__, a seguito della chiamata di qualunque metodo
* Per assicurare quest'ultimo, possiamo usare più metodi
	* Usare information hiding e fare si che i campi possano essere variati solo tramite metodi della classe
	* Inizializzare i campi tramite __costruttori__

#### Costruttori
* I costruttori possono essere definiti come i metodi all'interno della classe
* Qesuti avranno forma `nomedellaclasse(arg1, arg2, ... , argn)` e saranno differenziati in base al numero ed al tipo degli argomenti
* Questo permette di inizializzare i campi di un'istanza in modo differente in base alle necessità, fin dalla sua dichiarazione
* I campi possono acnhe essere inizializzati con valori predefiniti nella loro definizione. Se non viene passato un valore, ne viene assegnato uno di default
```java
public class TimerClass {
		private int time = 60; // ’time’ in seconds, default is 1 minute
		public TimerClass() { // initializes ’time’ with the default value 60
	}
	public TimerClass(int minutes) {
		if (minutes < 0 || minutes > 60)
			throw new IllegalArgumentException();
		this.time = minutes * 60;
	}
	public TimerClass(TimerClass otherTimer) { // copy constructor
		this.time = otherTimer.getTime();
	}
...
}
```

* I costruttori possono essere a sua volta chiamati nella definizione di un altro costruttore, come `this(args)`, solo sulla prima riga della definizione
* Questo facilita il riutilizzo di codice
---
* Non si possono aggiungere campi ad un oggetto dopo la sua creazione
* Nel caso di campi opzionali di tipo reference, si assegna solitamente il valore `null`. Per gli altri tipi primitivi, non esiste una convenzione sul valore
---
#### Stringhe
* Predefinite nella classe `String`
* Sono oggetti __immutabili__, con sintassi standard
* Un oggetto immutabile non può essere cambiato dopo l'inizializzazione, uno __mutabile__ possiede dei campi variabili


#### Campi di classe
* Sono variabili comuni a tutte le istanze della classe
* definite con `static`, vengono salvate in memoria insieme ai metodi, nella definizione della classe
```java
public class Item { 
	private static long nextSN; // class field for the next serial 
	number private int price; // object field (value is in cents) 
	private long serialNumber; // object field /* invariant price>=0 && serialNumber>=0 && \forall Item o,o’; o.serialNumber==o’.serialNumber ==> o==o’; */ 

	public Item(int price) { 
		if (price < 0) 
			throw new IllegalArgumentException(); 
		this.price = price; 
		this.serialNumber = Item.nextSN++; 
	} 
	public int getPrice() { 
		return this.price; 
	} 
	
	public long getSerialNumber() { 
		return this.serialNumber;
	} 
}
```

* Possono essere inizializzati in modo simile ai campi di un'oggetto. Possiamo anche usare dei cicli
```java
public class Test {
	private static int val = 5; // class field initializers
	private static int fact = 1;
	static { // initializes Test.fact with the factorial of Test.val
		for (int i = 1; i <= Test.val; i++)
			Test.fact *= i;
	}
	
	public static void main(String[] args) {
		assert Test.val==5 && Test.fact==120;
	}
}
```

#### Metodi di classe
* Analoghi ai campi di classe. Agiscono su un'intera classe. Nelle loro definizioni, `this` non è definito
* Questi possono essere utilizzati per il riutilizzo del codice e per permettere l'accesso ai campi di classe

#### Subtyping
* La Classe `Object` è una classe speciale predefinita, ogni tipo reference è __sottotipo__ di esso
* I tipi, sia primitivi che reference, si trovano in una struttura ad albero, in cui alcuni tipi derivano dai tipi superiori. 
* Si tratta di un __ordine parziale__ (Non totale: esistono tipi reference non comparabili fra loro, ed i tipi reference non sono comparabili con i tipi primitivi)
* Questa struttura facilita il type-checking: Se è richiesto un tipo T, possiamo passare qualunque sottotipo di T (oltre a T stesso, ovviamente)

#### Uguaglianze
* `person1 == person2` implica che le due variabili indicano lo stesso indirizzo in memoria, e hanno quindi i valori dei campi equivalenti
	* Mai usare `==` e `!=` con oggetti immutabili
* `person1.equals(person2)` implica che i due oggetti hanno gli stessi valori nei campi, ma non implica che sono lo stesso oggetto

#### Copie profonde e superficiali
* Una copia __superficiale__ consiste nel copiare l'indirizzo di memoria di un oggetto. Le due variabili si riferiscono allo stesso oggetto
* Una copia __profonda__ consiste nel creare un nuovo oggetto, uguale a quello di partenza. Si può fare tramite specifici costruttori e la parola `new`

#### Campi `final`
* Sono campi di sola lettura, costanti
* Se sono puntatori ad un oggetto, l'oggetto è modificabile. Semplicemente punterà sempre a quell'oggetto
* Questo permette di rendere alcune variabili `public`, senza paura di creare problemi nell'information hiding
* __Un campo può essere pubblico solo se__
	* è `final`
	* contiene un valore primitivo o un oggetto immutabile
	* L'informazione contenuta può essere condivisa
* Un oggetto è immutabile se
	* Tutti i suoi campi sono `final`
	* Tutti i campi contengono valori primitivi, o oggetti immutabili a sua volta

#### Interfacce
* L'interfaccia di un oggetto è l'insieme di metodi visibili dall'esterno (__Non__ comprende i __costruttori__)
* Possiamo definirla separatamente dalla definizione della classe. Conterrà solo i metodi visibili
```java
public interface Timer { // Timer is a type but not a class
	// all these methods are abstract and public
	boolean isRunning();
	int getTime();
	void tick();
	int reset(int minutes);
}
```

* Potremo poi implementare l'interfaccia in una classe usando la parola `implements`
```java
public class TimerClass implements Timer { // TimerClass ≤ Timer 
	private int time = 60; 
	... 
	// all methods of Timer must be defined in the class 
	public TimerClass(Timer other) { 
		this.time = other.getTime(); 
	} 
	... 
}
```

* Possiamo anche definirla più volte in classi differenti. Questo permette di ottenere classi fra esse compatibili, in quanto sottotipi della stessa interfaccia
---
* Nei casi di sottotipi compatibili, i metodi ononimi chiamati corrispondono a quelli del tipo dinamico dell'oggetto su cui è chiamato, `this`

#### Cicli for
```java
// standard ’for’ syntax
for (int i = 0; i < a.length; i++)
	a[i] = i + 1;
	
// ’enhanced for’ with more compact syntax 
for (int el : a) 
	sum += el; 
```

#### Array in Java
* Sono oggetti speciali, creati dinamicamente
* La lunghezza è un campo `final`, non modificabile
* I componenti dell'array vengono inizializzati con valori di default
* Possono essere inizializzati sia a creation che a declaration time
* Si possono creare array __multidimensionali__
---
* Posso assegnare ad elementi di un array di tipo reference oggetti che siano sottotipi del tipo di array. Questo non avviene con gli array di tipi primitivi
* I controlli sulle assegnazioni avvengono a __runtime__

#### Main
* Un programma Java parte sempre dal metodo main, definito come segue:
```java
public static void main(String[] args){...}
```
* In arg sono contenunti gli argomenti passati dal terminale

#### Stdout
* `System.out` è lo standard output. È un campo `final` della classe predefinita `System`. È di tipo `PrintStream`. Quest'ultimo possiede i metodi `print` e `println` per stampare
```java
public class PrintArguments {
	public static void main(String[] args) {
		for (String s : args)
			System.out.println(s); // prints with new line
			System.out.print(s); // prints
	}
}
```

#### Tipi Primitivi
* I tipi primitivi sono:
	* `boolean`
	* Tipi Interi:
		* `byte` (1 byte)
		* `short` (2 bytes)
		* `char` (2 bytes, unsigned)
		* `int` (4 bytes)
		* `long` (8 bytes)
	* Tipi Floating Point
		* `float` (4 bytes)
		* `double` (8 bytes)
* Sia interi che floating point possono essere scritti come __literal__
* I tipi sono nella seguente relazione:
![[Tipi Primitivi.png]]

* Al contrario dei tipi reference, una variabile di tipo primitivo può contenere solo valori di quel tipo. Nell'assegnazione di valori di tipi diversi, vengono effettuate delle __conversioni__
* Queste sono di due tipi:
	* __Allargamento__: Passiamo da un tipo inferiore ad un tipo superiore. Possono avvenire in modo __implicito__, non si perdono informazioni con l'eccezione di alcuni casi
	* __Riduzione__:  Passiamo da un tipo superiore ad un tipo inferiore. C'è perdita di dati, e a causa della pericolosità deve avvenire __esplicitamente__, tramite casting o `Math.round`. 
		* Il cast è più efficente ma meno preciso rispetto al rounding

#### Classi Wrapper
* Per ogni tipo primitivo esiste una classe wrapper predefinita, __immutabile__,  che contiene numerosi metodi utili ai calcoli 
```java
int i = 42;
Integer o = Integer.valueOf(i); 
```

* Al contrario dei tipi primitivi, essi __non sono sottotipi__ fra loro:
![[Gerarchia Classi Wrapper.png]]

* Inoltre, essendo tipi di categoria diversa, I tipi primitivi __non sono compatibili__ con le relative classi wrapper(`int` $\nleq$ `Integer`, `int` $\ngeq$ `Integer`)
* Nel passare dati fra di esse, vengono eseguite delle conversioni implicite, definite __boxing__ ed __unboxing__
```java
Integer o = 42; // boxing, same as ’Integer o=Integer.valueOf(42)’ 
int i = o; // unboxing, same as ’int i=o.intValue()’
```

#### Promozione Numerica
* Durante alcune operazioni logiche o numeriche, possono avvenire degli unboxing o allargamenti implicitamente
```java
assert 5 / 2 == 2; // no conversion
assert 5 / 2. == 2.5; // widening int -> double
Integer i = 5; // boxing int -> Integer
assert i == 5; // unboxing Integer -> int
assert i > 2; // unboxing Integer -> int
assert i * 2 == 10; // unboxing Integer -> int
assert i * i == 25; // unboxing Integer -> int
assert i / 2. == 2.5; // unboxing and widening Integer -> int -> double
```

* Bisogna stare attenti ad esse per l'efficenza del codice. Se possibile, __evitiamo__ di eseguire conversioni ed un/boxing quando non necessario

#### Modularizzazione
* Allo scopo di organizzare il codice, possiamo utilizzare la struttura dei __Moduli__ e __Pacchetti__. I primi organizzano e gestiscono i secondi, che organizzano e gestiscono classi
* Noi useremo i pacchetti
* Questi sono organizzati come una cartella, contenenti sottopacchetti (ulteriori cartelle) e unità di compilazione (file) contenenti definizioni di classi e interfacce
* Il nome di un pacchetto corrisponde al suo path (javax/swing/tree ==> `javax.swing.tree` )
---
* Le classi ed interfacce contenute hanno due nomi:
	* Un nome __semplice__, utilizzabile all'interno del pacchetto (`TreePath`)
	* Un nome __qualificato__, utilizzabile all'esterno del pacchetto (se sono pubbliche, ovviamente) (`javax.swing.tree.TreePath`)
---
* Possiamo indicare il pacchetto a cui appartiene un file con `package`
* __Solo__ una classe per file può essere __pubblica__, ed il __nome__ del file deve essere lo stesso della classe __pubblica__
---
* Aggiungiamo un __altro__ strato di __information hiding__: Package: rendiamo l'oggetto accessibile __solo__ nel pacchetto
* Questo è l'accesso di default, definito senza nessuna parola
```java
private void privateMeth(){...} // private method
void packageMeth(){...}         // package method
public void publicMeth(){...}   // public method
```

* __Non__ esiste visibilità fra pacchetti e sottopacchetti
---
* Useremo principalmente pacchetti del modulo `java.base`

#### Import
* Usando `import`, possiamo importare un pacchetto, od un singolo comando, nel file, così da poter utilizzare il nome semplice
* Usando uno `static import`, possiamo addirittura usare metodi statici senza usare nomi di classe

#### RegEx
* In Java, le espressioni regolari vengono valutate tramite due classi, `Matcher` e `Pattern`
	* La prima è un oggetto contenente informazioni su un singolo match, con relativi metodi per accedervi
		* Per operazioni molto semplici, è possibile utilizzare il metodo `matches` della classe `String`
	* la seconda è un oggetto contenente un pattern, una RegEx, utilizzabile insieme alla prima

##### Pattern
* Sono oggetti immutabili, creati da stringhe, rappresentanti espressioni regolari, tramite il metodo `compile`
* Possono creare `Matcher` tramite il metodo `matcher`

##### Matcher
* Un matcher è un oggetto mutabile, dotato di un pattern e di una __sequenza di input__
* Esso lavora su una sottosequenza dell'input, una __regione__, modificabile tramite il metodo `region(int start, int end)` (`start` incluso)
	* All'inizio, la regione corrisponde all'intera sequenza
* La sequenza di input è modificabile tramite `reset(CharSequence input)`
---
* Altri metodi sono:
	* `matches()` cerca di fare match di __tutta la regione__ con il pattern
	* `lookingAt()` cerca di fare match di una __sottosequenza__ della regione, a partire dall'__inizio__
	* `find()` cerca una __sottosequenza__ che corrisponda, che __non__ parta dall'__inizio__
```java
Pattern pt = Pattern.compile("[A-Z][a-z]+"); 
Matcher mt = pt.matcher("Java"); // region is the whole input 
assert mt.matches(); // the entire region matches 
mt.reset("Java language"); // region is the whole input 
assert !mt.matches(); // the entire region does not match 
assert mt.lookingAt(); // "Java" matches 
mt.reset("language Java"); // region is the whole input 
assert !mt.matches(); // the entire region does not match 
assert !mt.lookingAt(); // no subsequence matches from the beginning 
assert mt.find(); // "Java" matches
```

* Inoltre
	* `start()` ritorna l'__indice__ del __primo__ carattere che corrisponde
	* `end()` ritorna l'__indice successivo__ all'ultimo carattere che corrisponde
	* `group()` ritorna la __stringa__ che ha corrisposto
---
* In seguito a `region` e `reset`, vengono persi i risultati dei precedenti match
* I risultati di un match possono essere salvati in un oggetto `Matchresult` (`java.util.regex.Matchresult`)
---
* Nello scrivere le RegEx da passare, possiamo usare le parentesi per, oltre che forzare la precedenza, per definire dei __gruppi__ di cattura
* Essi sono indicizzati, in ordine di scrittura
	* Il gruppo 0 corrisponde all'intera espressione
* Possiamo usare `group`, passandogli l'indice giusto, per richiedere la stringa che corrisponde al gruppo richiesto
```java
Pattern pt = Pattern.compile("(0|[1-9][0-9]*)([Ll]?)"); 
Matcher mt = pt.matcher("42L"); 
mt.lookingAt(); 
MatchResult res = mt.toMatchResult(); 
assert res.group(0).equals("42L"); // 0 is (0|[1-9][0-9]*)([Ll]?) 
assert res.group(1).equals("42"); // 1 is (0|[1-9][0-9]*) 
assert res.group(2).equals("L"); // 2 is ([Ll]?) 
mt.reset("42"); 
mt.lookingAt(); 
res = mt.toMatchResult(); 
assert res.group(0).equals("42"); 
assert res.group(1).equals("42"); 
assert res.group(2).equals("");
```

* Regole Generali sulle RegEx:
![[Java RegEx1.png]]
![[Java RegEx2.png]]
![[Java RegEx3.png]]

---
* Un problema degli operatori delle RegEx è che la concatenazione e `|` __non__ sono __avidi__, ovvero non prendono la stringa più grande che corrisponde. Questo crea problemi nel cercare di identificare certe __keywords__
```java
pt = Pattern.compile("(if|let)|([a-zA-Z]\\w*)"); // recall "\\w" is "[a-zA-Z_0-9]" 
mt = pt.matcher("ifvar"); 
assert mt.lookingAt(); 
assert mt.group(1).equals("if");
```

* Si può risolvere tramite il __word boundary__ `\\b`
```java
pt = Pattern.compile("((?:if|let)\\b)|([a-zA-Z]\\w*)"); 
mt = pt.matcher("ifvar"); 
assert mt.lookingAt(); 
assert mt.group(2).equals("ifvar"); // identifier 

mt.reset("if"); 
assert mt.lookingAt(); 
assert mt.group(1).equals("if"); // keyword
```

* `\\b` indica che ci deve essere un carattere non-lettera a fine stringa (non in `\\w`) come `\s`, per esempio

#### Ereditarietà
* L'ereditarietà consiste nella generazione di nuove classi sulla base di alcune già esistenti
* Questo permette di riutilizzare codice. Inoltre, permette compatibilità fra i due tipi
* Per farlo, usiamo la parola `extends`
```java
public class StoppableTimerClass extends TimerClass implements StoppableTimer { 
	private boolean stopped; 

	public boolean stopped() { return this.stopped; } 
	public void stop() { this.stopped = true; } 
	public void restart() { this.stopped = false; } 
	
	@Override public boolean isRunning() { // redefined 
		return super.isRunning() && !this.stopped(); 
	} 
	
	@Override public int reset(int minutes) { // redefined 
		this.restart(); 
		return super.reset(minutes); 
	} 
	
	public static void main(String[] args) { 
		StoppableTimerClass st = new StoppableTimerClass(); 
		assert st.isRunning() && st.getTime()==60; 
		st.stop(); 
		assert !st.isRunning() && st.getTime()==60; 
		st.tick(); 
		assert !st.isRunning() && st.getTime()==60; 
		st.restart(); 
		st.tick(); 
		assert st.isRunning() && st.getTime()==59; 
	} 
}
```

* Il nuovo oggetto avrà tutti i campi e i metodi (pubblici) del genitore. Può definirne di nuovi o __sovrascriverli__ tramite la parola `@Override`
* Se necessario, possiamo chiamare i metodi della superclasse su `this`, chiamandolo `super`
* Similmente ai costruttori, possiamo anche sovraccaricare i metodi, dando più definizioni del metodo nelle sottoclassi, con argomenti differenti
---
* Aggiungiamo la parola `protected` per l'information hiding. I campi di questo tipo saranno accessibili solo nello stesso pacchetto e nelle sottoclassi
---
* La classe che otteniamo sarà sottotipo reference della superclasse genitrice

#### Dynamic Dispatch of Object Methods
* Se chiamiamo il metodo `m.o()`, come facciamo a sapere quale versione del metodo viene chiamata?
	* Innanzitutto controlliamo se esiste una versione nella classe `C` di `o`
	* Se non la troviamo, guardiamo nelle superclassi di `C`
	* Continuiamo fino a che non la troviamo. Se non la troviamo, viene riportata l'eccezione `NoSuchMethodError`
* Nel caso in cui si chiami `super.o()`, __non__ avviene questo controllo, verrà sempre chiamato il metodo della prima superclasse
* Questo controllo non avviene neppure su metodi o campi di __classe__. Quest'ultimi inoltre non possono essere ridefiniti (ma vengono ereditati)
---
* I costruttori non possono venire ereditati: Per ovviare a ciò, questi devono essere di livello `protected`, e venire ridefiniti nella nuova classe (Possiamo sfruttare `super()`)
* Se non si usa `super()`, esso viene messo implicitamente nella prima riga. Dovremo comunque __inizializzare__ le variabili specifiche di questa classe

#### Classi Astratte
* Le classi astratte sono un ibrido fra interfacce e classi: Contengono implementazioni parziali. Questo ci permette di definire solo alcuni metodi, lasciando altri indefiniti, potendo essere definiti dalle sottoclassi. Questo permette una maggiore riutilizzazione del codice, condiviso in questo caso dalle sottoclassi
* I metodi che non vogliamo definire devono esssre definit con la parola `abstract`. Non è necessario definire i campi

#### Ereditarietà Multipla
* In Java, solo le interfacce possono farla
* Permette definizioni più flessibili, ma molto più complesse

#### Overloading Resolution
* Essa consiste nel determinare __quale versione__ del metodo o costruttore da utilizzare in una determinata chiamata
* Essa avviene in modo __statico__, durante la compilazione, e per ciò dipende dal tipo statico degli argomenti e del target
![[Overloading Resolution.png]]

* Dopo aver determinato la classe del metodo e i tipi (statici) degli argomenti, la ricerca avviene in vari passaggi:
	* Step __1__: Cerchiamo un versione del metodo che corrisponda al tipo dell'argomento o ai suoi sottotipi. Se esiste la versione relativa al suo tipo, preferiamo quella, o in generale una più specifica, in cui gli argomenti sono tipo superiore rispetto agli altri
		* Se non esiste un metodo più specifico degli altri, la risoluzione fallisce
	* Step __2__: Se non esistono versioni compatibili tramite sottotipi, controlliamo se è possibile effettuare una __conversione__, o un boxing od unboxing con allargamento
	* Step __3__: Se non esistono metodi con conversioni con arità statica disponibili, useremo dei metodi con arità variabile

#### Classi Predefinite Utili
* `Object` contiene numerosi metodi per gestire qualunque tipo di oggetto
* `Objects` contiene ulteriori funzioni, da non confondere con la prima
* `StringBuilder` è un tipo di stringa __mutabile__. Come `String` implementa `CharSequence`, e per ciò sono compatibili

#### Metodi Generici
* Usando come tipo `<T>` possiamo definire una variabile di __tipo tipo__
* Questo permette di creare metodi generici, applicabili ad una varietà di tipi differenti
```java
public static <T> T requireNonNull(T obj) { // correct
	if (obj == null)
		throw new NullPointerException();
	return obj;
}
```
