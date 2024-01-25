+ In questo file, cercheremo di riassumere i concetti principali del corso di **Teoria degli Automi e Calcolabilità.**
![Image](TAC.png =300x200)

---
# 1 - Automi
+ Un **Alfabeto** è un **insieme** $\Sigma$ non vuoto, finito, di simboli
+ Una **Stringa** è una **sequenza** finita di simboli
+ Un **Linguaggio** è un alfabeto di stringhe $L \in \Sigma^*$ 
## 1.1 - Linguaggi Regolari
### Note Generali
+ Un **automa** è un algoritmo, una macchina estratta
	+ Possiamo rappresentare gli automi come grafi, o matrici
+ Ogni singolo momento in cui si trova l'automa è una **configurazione** $<q_n, u>$ 
	+ Una sequenza di specifiche configurazioni viene chiamata **computazione**
+ Alcune particolarità sono:
	+ Configurazioni **d'arresto**, da cui non si può passare ad alcun'altro stato
	+ Configurazioni **deterministiche**, in cui si può andare ad un unico stato
	+ Configurazioni **non deterministiche**, in cui si può andare a più di uno stato
+ Una relazione di riduzione viene detta **terminante**, se **non** permette **computazioni infinite**
---
+ La **chiusura riflessiva e transitiva** $\to^*$ indica che i due stati possono essere raggiunti in un numero finito di passi
	+ È facilmente dimostrabile per induzione (*dettagli nel cartaceo*)
+ Il **linguaggio accettato** è l'insieme delle stringhe riconoscibili da un'automa
	+  Può essere definito induttivamente (*dettagli nel cartaceo*)
+ Le **direttive d'esecuzione** indicano quando un passo viene completato
+ Le **direttive I/O** indicano il modo in cui viene fornito l'input e l'output
### DFA e mDFA
+ Gli **automi a stati finiti deterministici** (DFA) sono un tipo di automa riconoscitore molto semplice. 
+ Data una stringa, dicono se essa appartiene o no ad un linguaggio
+ Essi vengono definiti tramite una tupla:
	+ $\mathbb{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Cyan}{F}, \textcolor{Mulberry}{\delta})$ 
		+ $\textcolor{Apricot}{Q}$ è un insieme di **stati**, situazioni, in cui si può trovare la macchina
		+ $\textcolor{LimeGreen}{\Sigma}$ è l'**alfabeto** usato dalla macchina
		+ $\textcolor{WildStrawberry}{q_0}$ è lo **stato iniziale** della macchina
		+ $\textcolor{Cyan}{F}$ è l'insieme degli **stati finali** della macchina
		+ $\textcolor{Mulberry}{\delta}$ è la **funzione di transizione**, il funzionamento ad ogni passo, dell'automa
	+ Configurazioni
		+  $<q, u> \quad q \in Q, u \in \Sigma^*$
	+ Configurazioni Ferme
		+ $<q, \varepsilon>$
	+ Relazione di Riduzione
		+ $<q, \sigma u> \;\to \; <q^{'}, u> \; \leftrightarrow \; q^{'} \in \delta(q, \sigma)$
	+ Linguaggio Accettato
		+  $L(M) = \{u \; | <q_0, u> \; \to^* \; <q_f, \varepsilon>, \; q_f \in F\}$ 
	+ Direttiva I/O
		+ Stringhe in ingresso, segnale binario in uscita
+ I DFA riconoscono **linguaggi regolari**. Ogni linguaggio riconosciuto da un DFA è regolare
---
+ Un DFA può essere trasformato in un **mDFA**, un automa deterministico minimizzato
	+ $DFA \to \textcolor{Apricot}{mDFA} \quad | \quad L(\mathcal{M}) = L(\mathcal{M^m}) \wedge \nexists \mathcal{M'} | L(\mathcal{M'}) = L(\mathcal{M}) \wedge |Q'| < |Q^m|$  
+ Questo automa rimuove passaggi complessi o non necessari dal DFA originario
+ L'**algoritmo** è il seguente:
	1. Innanzitutto rimuoviamo gli stati non raggiungibili da $q_0$ 
	2. Partiamo dividendoli in stati finali e non finali
	3. Suddividiamo gli stati rimanenti in classi d'equivalenza, fatte in modo che, per ogni stringa, gli elementi di quella classe vanno tutti nella stessa classe (non per forza la loro)
	4. Osserviamo in che classi si muovono e, passaggio per passaggio, li dividiamo in sotto-classi
	5. Alla fine, otterremo un determinato numero di sotto-classi. Ognuna di esse sarà uno stato del nostro nuovo automa
### NFA
+ Un **automa a stati finiti non deterministico** è una variante di un DFA, con la differenza che sta nella sua funzione di transizione, la quale può ritornare **più stati**
	+ $\mathbb{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Cyan}{F}, \textcolor{Mulberry}{\delta})$ 
	+ $\textcolor{Mulberry}{\delta} : Q \times \Sigma \to \underbrace{\mathcal{P}(Q)}_{\text{insieme delle parti}}$
+ Se la computazione di un DFA poteva essere vista come una sequenza finita di stati, quella di un NFA può essere vista come un **albero finito**
	+ Esso può fermarsi anche prima di aver finito di leggere la stringa
---
+ Configurazioni **ferme**
	+ $< q, \varepsilon>$
	+ $< q, \sigma u>, \quad \delta(q, \sigma) = \emptyset$  
+ Ridefinizione di $\delta^*$
	+ $\delta^{*} : Q \times \Sigma^* \to \mathcal{P}(Q)$
	+ $\delta^{*}(q, \varepsilon) = \{q\}$ 
	+ $\delta^{*}(q, u \sigma) = \bigcup_{q' \in \delta^{*}(q, u)} \delta^* (q', \sigma)$  
+ Linguaggio Riconosciuto
	+  $L(\mathcal{M}) = \{u \; | <q_0, u> \; \xrightarrow{*} \; <q_f, \varepsilon>, \; q_f \in F\}$ 
		+ *È virtualmente uguale ad un DFA, ma adesso indica "se esiste una computazione accettabile"*
	+  $L(\mathcal{M}) = \{u \; | \; \left(\delta^{*}(q_0, u) \cap F \right) \neq \emptyset\}$ 
---
+ Questi automi ci permettono di riconoscere linguaggi più complessi di quelli deterministici? **NO**
+ Ci permettono però di programmare in modo più semplice. Infatti, gli NFA sono traducibili in DFA; con un semplice algoritmo.
#### Teorema di Rabin-Scott
+ Dato $\mathcal{M}_N = (Q_N, \Sigma, q_0, \delta_N, F_N)$ 
+ $\exists \mathcal{M}_D \; | \; L(\mathcal{M}_D) = L(\mathcal{M}_N)$ 
	+  $\mathcal{M}_D = (\mathcal{P}(Q_N), \Sigma, \{q_0\}, \delta_D, F_D)$
	+ $q_D \in F_D \leftrightarrow q_D \cap F_N \neq \emptyset$ 
	+ $\delta_D \; : \; \mathcal{P}(Q_N) \times \Sigma \to \mathcal{P}(Q_N)$ 
	+ $\delta_D(q_D, \sigma) \; = \; \bigcup_{q_N \in q_D} \delta_N(q_N, \sigma)$  

+ *Negli appunti cartacei, dimostrazione che $L(\mathcal{M}_N) = L(\mathcal{M}_D)$* 
+ *Vedere esercizi su questo*
### $\varepsilon$-NFA
+ Gli automi **$\varepsilon$-NFA** sono una variante degli NFA, i quali permettono di effettuare transizioni dette **silenti**, nelle quali si passa ad un altro stato senza la lettura di alcun simbolo
+ Automa
	+ $\mathcal{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Cyan}{F}, \textcolor{Mulberry}{\delta})$ 
+ Funzione di Transizione
	+ $\textcolor{Mulberry}{\delta} : Q \times \Sigma \cup \{\varepsilon\} \to \mathcal{P}(Q)$
+ Configurazioni
	+ $<q, u>$
+ Configurazioni Ferme
	+ $<q, \varepsilon> \wedge \; \delta(q, \varepsilon) = \emptyset$
	+ $<q, \sigma u> \wedge \; \delta(q, \sigma) = \emptyset \; \wedge \; \delta(q, \varepsilon) = \emptyset$
 + Passi
	 + $<q, \sigma u> \;\to \; <q^{'}, u> \; \leftrightarrow \; q^{'} \in \delta(q, \sigma)$    (Caso di **lettura**)
	 + $<q, u> \;\to \; <q^{'}, u> \; \leftrightarrow \; q^{'} \in \delta(q, \varepsilon)$       (Caso **silente**)
+ Riduzione
	+ È non deterministica e **non terminante** (È possibile ritrovarsi in cicli infiniti di transizioni silenti)
+ Chiusura $\hat{\delta}$ 
	+ Viene ridefinita tramite il seguente nuovo concetto
		+ $\textcolor{Apricot}{\varepsilon\text{-closure}} : \quad Q \to \mathcal{P}(Q)$ 
		+ Dato uno stato, vengono restituiti tutti gli stati raggiungibili solo con transizioni **silenti**
	+ $\hat{\delta} : Q \times \Sigma^* \to \mathcal{P}(Q)$
		+ $\hat{\delta}(q, \varepsilon) = \varepsilon\text{-closure}(q)$ 
		+ $\hat{\delta}(q, u\sigma) = \bigcup_{q^{'}\in \hat{\delta}(q,u)}\varepsilon\text{-closure}(\hat{\delta}(q^{'}, \sigma))$ 
+ Linguaggio Accettato
	+ $L(\mathcal{M}) = \{u \; | <q_0, u> \; \xrightarrow{*} \; <q_f, \varepsilon>, \; q_f \in F\}$ 
	+ $L(\mathcal{M}) = \{u \; | \; \hat{\delta}(q_0, u) \cap F \neq \emptyset\}$
---
+ È possibile convertire un automa $\mathcal{M}_{\varepsilon}$ in un equivalente $\mathcal{M}_{N}$ 
	+ $\mathcal{M}_{\varepsilon} = (Q_N, \Sigma, q_0, \delta_{\varepsilon}, F_{\varepsilon})$ 
	+ $\mathcal{M}_N = (Q_N, \Sigma, q_0, \delta_N, F_N)$ 
		+ $F_N = F_{\varepsilon}\;[ \cup {q_0} \leftrightarrow q_0 \xrightarrow{\varepsilon^{*}}q_f \in F ]$ 
		+ $\delta_N = \begin{dcases}\text{transizioni non silenti in } \delta_{\varepsilon} \\ q \xrightarrow{\sigma N} q^{'} \leftrightarrow q \xrightarrow{\varepsilon^{*} \sigma \varepsilon^{*}} q^{'}\end{dcases}$
+ In linguaggio naturale:
	1. Manteniamo $F_\varepsilon \to F_N$, aggiungendo $q_0$ se e solo se possiede percorsi in $q_f \in F_N$ tramite transizioni silenti
	2. Tutte le transizioni non silenti vengono mantenute
	3. Le transizioni silenti vengono aggiunte se e solo se esiste un percorso che le contiene, oltre a transizioni non silenti
	4. Alla fine dello schema, si potrebbero rimuovere gli eventuali stati superflui (non raggiungibili)
### RegEx
+  Le **Espressioni Regolari** (RegEx) sono stringhe, che rappresentano un linguaggio su $\Sigma$, con alfabeto $\Sigma \cup \{\emptyset, \varepsilon, |, *, (, ) \}$ 
+ Essi rappresentano alcuni costrutti equivalenti:
	+ $r \quad \to \quad L(r)$ 
	+ $\emptyset \quad \to \quad \emptyset$ 
	+ $\varepsilon \quad \to \quad \{\varepsilon\}$ 
	+ $\sigma (\in \Sigma) \quad \to \quad \{\sigma\}$ 
	+ $r_1 | r_2 \quad \to \quad L(r_1) \cup L(r_2)$ 
	+ $r_1r_2 \quad \to \quad L(r_1) \cdot L(r_2)$ 
	+ $r^* \quad \to \quad L(r)^*$
+ Valgono le seguenti proprietà:
	+ $r|s = s|r$
	+ $r|(s|t) = (r|s)|t$
	+ $r(st) = (rs)t$
	+ $\emptyset^* = \varepsilon$ 
	+ $r^*(r|s)^* = (r|s)^*$ 
---
Esse possono essere trasformate in $\varepsilon$-NFA che riconoscono stringhe appartenenti al loro linguaggio
+ Ogni elemento viene tradotto in un modo specifico
	+ $r \quad \to \quad \boxed{\mathcal{M}(r)}$
	+ $\emptyset \quad \to \quad$ una macchina che rifiuta tutto
	+ $\varepsilon \quad \to \quad$una macchina che accetta solo la stringa vuota
	+ $\sigma \quad \to \quad$ una macchina che accetta solo il simbolo $\sigma$
	+ $r_1|r_2 \quad \to \quad$ una macchina che sceglie se usare $\mathcal{M}(r_1)$ o $\mathcal{M}(r_2)$ 
	+ $r_1r_2 \quad \to \quad$ una macchina che passa prima per  $\mathcal{M}(r_1)$, poi per $\mathcal{M}(r_2)$ 
	+ $r^* \quad \to \quad$ Una macchina che passa più volte in $\mathcal{M} (r)$   
+ Siamo arrivati quindi al punto di essere in grado di trasformare espressioni regolari direttamente in mDFA
	+ $RegEX \to \varepsilon - NFA \to NFA \to DFA \to mDFA$ 
---
### Chiusura Regolari
+ È possibile dimostrare che, **componendo linguaggi regolari**, si **ottengono** sempre **linguaggi regolari**
	+ $L_1 \cup L_2 \quad \to \quad$ regolare, in quanto ognuno dei due avrà un espressione regolare, e la loro unione è un espressione regolare, che rappresenta un linguaggio regolare
	+ $L_1 \cdot L_2 \quad \to \quad$ regolare, dimostrabile come nel precedente
	+ $L^* \quad \to \quad$ regolare, dimostrabile come nel precedente
	+ $\bar{L} \quad \to \quad$ regolare, basta invertire gli stati finali e non finali
	+ $L_1 \cap L_2 \quad \to \quad$ regolare, in quanto equivalente a $\bar{\bar{L_1} \cup \bar{L_2}}$ 
### Pumping Lemma
+ Come facciamo a **dimostrare** che un linguaggio generico è **regolare**?
	+ Basta dimostrare che esiste un DFA in grado di riconoscerlo
+ E per dimostrare il **contrario**?
	+ Questo è ben più complesso, avremo bisogno di usare un determinato **lemma**
+ L'idea è la seguente
	+ Se un DFA ha $s$ stati, è sicuramente in grado di riconoscere stringhe lunghe $s$
	+ Se una stringa $z$ ha $|z| > s$, affinché debba essere riconosciuta, ci deve essere una qual sorta di loop all'interno dell'automa, ed almeno uno stato sarà ripetuto
+ Questo ci porta alla definizione del **Pumping Lemma**:
	+ $L \text{ Regolare} \to \exists n \geq 0 | \forall z \in L, \; |z| \geq n, \; \exists \text{decomp.} \; z = uvw | \quad |uv| \leq n \quad |v| > 0 \quad \forall i \geq 0 \quad uv^iw \in L$
	+ A parole, ciò vuol dire che se abbiamo l'automa $\mathcal{M}$ com $n$ stati, se una stringa $z$ è con $|z| \geq n$, la stringa è divisibile in tre parti, $uvw$, in cui $v$ non è vuota, ed è composta da una ripetizione di simboli del linguaggio. Se ciò è vero, $L(\mathcal{M})$ è un linguaggio regolare
+ Possiamo usare questo lemma per dimostrare che un linguaggio non è regolare: basta che non lo rispetti
	+ Un esempio è il linguaggio $L = \{a^nb^n | n \geq 0\}$ 
+ Dobbiamo quindi dimostrare il **contrario**:
	+ $L \text{ non Regolare} \to \forall n \geq 0 | \exists z \in L, \; |z| \geq n, \; \forall \text{decomp.} \; z = uvw | \quad |uv| \leq n \quad |v| > 0 \quad \exists i \geq 0 \quad uv^iw \notin L$
---
	
## 1.2 - Linguaggi Context-Free
### Grammatiche
+ I linguaggi context-free sono una categoria di linguaggi non regolari, che vengono identificati da una grammatica **BNF**
+ Per la precisione, una **grammatica context-free** è una tupla dalla forma:
	+  $\mathcal{G} : ( \textcolor{Apricot}{T}, \textcolor{LimeGreen}{N}, \textcolor{WildStrawberry}{\mathcal{S}}, \textcolor{Cyan}{\mathcal{P}})$ 
		+ $\textcolor{Apricot}{T}$ è l'alfabeto dei terminali, i **simboli** utilizzati nel linguaggio
		+ $\textcolor{LimeGreen}{N}$ è l'alfabeto dei non-terminali, i **meta-simboli** ottenuti per costruzione
		+ $\textcolor{WildStrawberry}{\mathcal{S}} \in \textcolor{LimeGreen}{N}$ è il simbolo iniziale, o **assioma**
		+ $\textcolor{Cyan}{\mathcal{P}}$ è un insieme di coppie $(A \in \textcolor{LimeGreen}{N}, \alpha \in ( \textcolor{Apricot}{T} \cup \textcolor{LimeGreen}{N}))^*$, che descrivono le possibili **derivazioni** 
+ Tramite le derivazioni, la grammatica è in grado di **generare un linguaggio**
	+ $\mathcal{S} \xrightarrow{*} n \in T^*$ 
+ A ogni passaggio, una determinata $\alpha$ viene riscritta in una certa $\beta$ seguendo le trasformazioni descritte dalle coppie in $\mathcal{P}$ 
+ Quindi
	+ $L(\mathcal{G}) = \{u \; | \; \mathcal{S} \xrightarrow{*} u\}$
---
+ Come facciamo a **dimostrare** che una grammatica $\mathcal{G}$ è stata definita in modo **corretto**?
+ Dobbiamo dimostrare due proprietà:
	1. Se la stringa viene riconosciuta, appartiene al linguaggio (**Soundness**)
	2. Se la stringa appartiene al linguaggio, viene riconosciuta
+ La **prima** proprietà è **facilmente dimostrabile**, ridefinendo l'automa in maniera induttiva, e sfruttando quindi il principio d'**induzione**
+ Per la **seconda** è necessario un **ragionamento ad hoc**, a seconda della grammatica analizzata
### PDA e DPDA
+ Un automa a pila (**Push Down Automata**) (PDA) può essere visto come un $\varepsilon$-NFA dotato di una **memoria**, ovvero una **pila** 
+ Automa
	+ $\mathcal{M} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{Yellow}{\Gamma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Mulberry}{\delta}, \textcolor{Aquamarine}{Z} , \textcolor{Cyan}{F})$ 
		+ $\textcolor{Apricot}{Q}$ è un insieme di **stati**
		+ $\textcolor{LimeGreen}{\Sigma}$ è l'alfabeto di **input**
		+ $\textcolor{Yellow}{\Gamma}$ è l'alfabeto dei simboli della **pila**
		+ $\textcolor{WildStrawberry}{q_0}$ è lo **stato iniziale** della macchina
		+ $\textcolor{Mulberry}{\delta}$ è la **funzione di transizione**
		+ $\textcolor{Aquamarine}{Z}$ è un simbolo di $\textcolor{Yellow}{\Gamma}$, usato come "**placeholder**" nella pila
		+ $\textcolor{Cyan}{F}$ è l'insieme degli **stati finali** della macchina, **facoltativi**
+ Funzione di Transizione
	+ $\textcolor{Mulberry}{\delta} : Q \times (\Sigma \cup \{\varepsilon\}) \times \Gamma \to \mathcal{P}(Q\times \Gamma^*)$
		+ A ogni passo, l'automa osserva il simbolo, lo stato ed il simbolo in cima alla pila, per poi muoversi ad un nuovo stato, e modificare il simbolo della pila
+ Configurazioni
	+ $<q, u, \alpha>$
		+ $q \in Q$ stato corrente
		+ $u \in \Sigma^*$ stringa in lettura
		+ $\alpha \in \Gamma^*$ top della pila
+ Configurazioni Ferme
	+ $<q, a, \varepsilon>$ 
		+ La pila è vuota
	+ $<q, \varepsilon, x\alpha>\wedge \; \delta(q, \varepsilon,x) = \emptyset$ 
		+ La stringa è vuota, e non abbiamo altre transizioni silenti
	+ $<q, \sigma u, x\alpha> \wedge \; \delta(q, \sigma, x) = \emptyset \; \wedge \; \delta(q, \varepsilon, x) = \emptyset$ 
		+ Ci sono ancora simboli da leggere, ma non ci sono transizioni adatte
 + Passi
	 + $<q, \sigma u, x\alpha> \;\to \; <q^{'}, u, \beta \alpha> \; \leftrightarrow \; q^{'} \in \delta(q, \sigma, \beta)$    (Passo di **lettura**)
	 + $<q, u, x\alpha> \;\to \; <q^{'}, u, \beta \alpha> \; \leftrightarrow \; q^{'} \in \delta(q, \varepsilon, \beta)$       (Passo **silente**)
+ Riduzione
	+ È non deterministica e **non terminante** (È possibile ritrovarsi in cicli infiniti)
+ Linguaggio Accettato
	+ $L^{ES}(\mathcal{M}) = \{u \in \Sigma^* \; | <q_0, u, z> \; \xrightarrow{*} \; <\_, \varepsilon, \varepsilon>\}$ 
		+ Riconoscimento per **pila vuota**
	+ $L^{FS}(\mathcal{M}) = \{u \in \Sigma^* \; | <q_0, u, z> \; \xrightarrow{*} \; <q_f \in F, \varepsilon, \_>\}$
		+ Riconoscimento per **stati finali**
---
+ Per quanto in generale questi automi non sono deterministici, esiste una sotto-categoria detta **DPDA**, formata da **automi a pila deterministici**
+ È possibile capire se posso creare un automa deterministico per un determinato linguaggio?
+ Sì, una delle proprietà che ce lo mostra è la **proprietà del prefisso**
	+ Se $L$ contiene due stringhe, di cui una è prefisso dell'altra, allora non esiste un DPDA in grado di riconoscerle
		+ Questo implica che nessun automa in grado di riconoscere la stringa vuota può essere deterministico, in quanto questa è comparabile ad un prefisso
+ Un automa è deterministico se:
	+ $\forall <q, \sigma, x>$ 
		+ Esiste al più un passo di lettura
		+ Esiste al più un passo silente
		+ Esiste o un passo di lettura o uno silente
### Corrispondenze CF e PDA
+ Sappiamo che nei linguaggi regolari esiste una correlazione diretta fra RegEx e DFA
+ Esiste qualcosa di simile fra **Grammatiche CF e PDA**?
	+ Si!
---
+ Dato $L = L(G) \leftrightarrow L = L(\mathcal{M})$ 
+ Dimostriamo:
	1. $L = L(\mathcal{M}) \to$ Possiamo costruire $G$ Grammatica Context-Free tale che $L = L(G)$
		+ Dobbiamo ridurre $\mathcal{M}$ in un automa ad **uno stato**
		+ Esso diventerà
			+ $\mathcal{M} : (\{q\}, \Sigma, \Gamma, Z, \delta)$ 
		+ Dovremo costruire $G$ fatto come:
			+ $G : (\Sigma, \Gamma, Z, \mathcal{P})$ 
		+ In esso, $P$ sarà formato da coppie del genere
			+ $<q, \alpha> \in \delta(q, \sigma, X) \qquad X ::= \sigma \alpha$ 
			+ $<q, \alpha> \in \delta(q, \varepsilon, X) \qquad X ::= X \alpha$
	2. $L = L(G) \to$ Possiamo costruire $\mathcal{M}$ PDA tale che $L = L(\mathcal{M})$ 
		+ Riduciamo la grammatica alla forma normale di **Greibach**
		+ Essa sarà
			+ $G : (\Sigma, \Gamma, Z, \mathcal{P})$ 
		+ In cui tutte le trasformazioni saranno della forma
			+ $X ::= \sigma B_1 \cdots B_n$
		+ Dovremo quindi costruire $\mathcal{M}$ fatto come:
			+ $\mathcal{M} : (\{q\}, \Sigma, \Gamma, Z, \delta)$
		+ In cui, se c'è una produzione $X ::= \sigma B_1 \cdots B_n$ $\in \mathcal{P}$ vale che
			+ $\delta(q, \sigma, X) = (q_1, B_1 \cdots B_n)$ 
+ Possiamo in particolare notare le corrispondenze:
	+ Non terminali $\leftrightarrow$ Simboli pila
	+ Assioma $\leftrightarrow$ Simbolo iniziale pila
	+ Produzioni $\leftrightarrow$ Istruzioni Pila 
---
### Pumping Lemma
+ Esiste una versione del **Pumping Lemma** anche per i linguaggi Context Free
	+ Infatti, esistono vari tipi di linguaggi che **non** sono context free, ad esempio i **linguaggi di programmazione**
+ La definizione è la seguente:
	+ $L \text{ CF} \to \exists n \in \mathbb{N} | \forall z \in L, \; |z| \geq n, \; \exists \text{decomp.} \; z = uvwxy | \quad |vwx| \leq n \quad |vx| > 0 \quad \forall i \geq 0 \quad uv^iwx^iy \in L$
	+ A parole, ciò vuol dire che se abbiamo l'automa $\mathcal{M}$ com $n$ stati, se una stringa $z$ è con $|z| \geq n$, la stringa è divisibile in cinque parti, $uvwxy$, in cui $vx$ non è vuota, ed è composta da una ripetizione di simboli del linguaggio. Se ciò è vero, $L(\mathcal{M})$ è un linguaggio context free
		+ È simile a quello usato nei linguaggi regolari. L'idea è sempre che ci deve essere una sezione che si ripete
+ Come la versione regolare, lo usiamo **al contrario**, per dimostrare che un linguaggio non è context free
	+ $L \text{ non CF} \to \forall n \in \mathbb{N} | \exists z \in L, \; |z| \geq n, \; \forall \text{decomp.} \; z = uvwxy | \quad |vwx| \leq n \quad |vx| > 0 \quad \exists i \geq 0 \quad uv^iwx^iy \notin L$
---

### Chiusura CF
+  Vediamo le proprietà di chiusura dei linguaggi Context Free:
	+ $L_1 \cup L_2 \quad \to \quad$ Context Free
	+ $L_1 \cdot L_2 \quad \to \quad$ Context Free
	+ $L^* \quad \to \quad$ Context Free
	+ $\bar{L} \quad \to \quad$ NON Context Free
	+ $L_1 \cap L_2 \quad \to \quad$ NON Context Free
		+ *dimostrazioni e altro nei fogli, 3/11/23*
---
+ Esistono degli algoritmi per ottenere automaticamente degli automi PDA da una grammatica context-free, una volta che questa è stata riscritta in forma normale di Greibach
+ Purtroppo essi sono in tempi cubici ($O(n^3)$)
+ Fortunatamente, nella pratica, i compilatori utilizzano algoritmi maggiormente efficienti, tramite l'utilizzo di assunzioni aggiuntive
# 2 - Calcolabilità
## 2.0 - Intro
+ La **teoria della calcolabilità** è una materia **primordiale** dell'informatica, nata con l'obbiettivo principale di rispondere alla eseguenti domande:
	1. **È possibile fare tutto con un calcolatore?**
	2. **Se non è possibile, cosa non si può fare?**
	3. **Tutti i formalismi utilizzabili per scrivere un problema sono equivalenti?**
+ Queste domande saranno rianalizzate in modo più formale
---
+ Analizziamo l'insieme delle funzioni:
	+ $f : \mathbb{N}^k \to \mathbb{N}$ 
+ Tutte queste funzioni sono calcolabili con un algoritmo?
+ Innanzitutto, quante sono?
+ Se considerassimo solo le funzioni di scelta, $f' : \mathbb{N} \to \{1, 0\}$, vedremmo che il numero è già $2^n > \aleph_0 = |\mathbb{N}|$ 
	+ È quindi un numero infinito non numerabile
+ Tra queste esistono funzioni non calcolabili?
---
## 2.1 - Primitive-Ricorsive
+ Presentiamo un mini-linguaggio, quello delle **Primitive-Ricorsive (PR)**
+ Esso è un linguaggio di programmazione funzionale, reminescente di OCAML
+ In esso, un programma è un insieme di dichiarazione di funzioni del tipo:
	+ $f(x_1, \cdots, x_n) = e$
	+ $e ::= x \; | \; f(e_1, \cdots, e_n) \; | \; z \; | \; S(e)$ 
		+ $x$ è un valore numerico
		+ $z$ è lo zero
		+ $S(e)$ è l'incremento di 1
+ Le funzioni possono essere non ricorsive o ricorsive. Ma queste ultime implementano un tipo di ricorsione molto semplice, detta **primitiva** (non mutua ricorsione)
+ Queste vengono definite tramite due clausole di tipo:
	+ $f(x_1, \cdots, x_n, z) = e$ 
	+ $f(x_1, \cdots, x_n, S(y)) = e'$ 
+ Queste definiscono una funzione nel senso che, dato un programma, esso può essere ridotto, applicando le clausole necessarie, fino ad un singolo valore
---
+ **Paragonando** questo linguaggio alle macchine viste in precedenza, abbiamo che
	+ Configurazioni ferme 
		+ I valori numerici del tipo $S(\cdots S(Z)\cdots)$ 
	+ Riduzione 
		+ Essa è terminante e non deterministica, in quanto in alcuni casi è possibile applicare più di una riduzione allo stesso punto
		+ Nonostante ciò, i risultati ottenuti sono sempre gli stessi, per via della proprietà di terminazione
---
+ L'insieme delle funzioni descritte in PR può essere definito in maniera **induttiva**
+ Passo **Base**:
	+ $z(x_1, \cdots, x_n) = 0 \; \forall n \geq 0 \quad$ (tutte le funzioni costanti zero) 
	+ $S(x) = x + 1 \quad$ (la funzione successore) 
	+ $\Pi_n(x_1, \cdots, x_n) = x_i\quad$ (proiezione)
+ Passo **Induttivo**
	+ Date $h, g : \mathbb{N^k} \to \mathbb{N}  \quad \forall i \in [1, \cdots, k]\quad$ si ha che
		+ $f(x_1, \cdots, x_k) = h(g_1(x_1,\cdots, x_k), \cdots, g_k(x_1,\cdots, x_k))$ 
		+ Questa è la **composizione generalizzata**, caso generale della composizione classica
	+ Date $h : \mathbb{N}^{n+1} \to \mathbb{N}, \quad g : \mathbb{N}^{n-1} \to \mathbb{N}$ si ha che
		+ $f(x_1, \cdots, x_{n-1}, 0) = g(x_1, \cdots, x_{n-1})$ 
		+ $f(x_1, \cdots, x_{n-1}, y+1) = h(x_1, \cdots, x_{n-1}, y, f(x_1, \cdots, x_{n-1}, y)$
		+ Questa è la **ricorsione primitiva**
---
+ Possiamo intuire che questo formalismo non è adatto a descrivere tutte le funzioni, in quanto **non** è in grado di descrivere funzioni **parziali**
+ Una dimostrazione è la **numerazione effettiva** di tutti i programmi PR
	+ Ogni programma PR è descrivibile da una stringa. Ciò vuol dire che è possibile ordinare queste stringhe, per lunghezza ed alfabeticamente. 
	+ Essi sono infiniti, ma siccome essi sono numerabili, ciò vuol dire che sono anche numerabili. Siccome sono numerabili, esso è un infinito $\in \aleph_0$, inferiore al numero di funzioni esistenti
	+ Questo ci conferma che il formalismo non è in grado di descrivere tutte le funzioni
+ Siccome la numerazioni è **effettiva**, ciò vuol dire che esistono i seguenti algoritmi
	+ dato n $\to$ programma n-esimo
	+ dato programma n-esimo $\to$ n
+ Negli appunti (10/11/23-14/11/23) viene mostrata una funzione che sfrutta questi algoritmi, e viene dimostrato che essa non appartiene a PR, confermando infine il fatto che **PR non è Turing-Completo**
	+ Essa viene chiamata **dimostrazione per diagonalizzazione**. Funziona per qualunque formalismo tale che:
		1. I programmi/algoritmi descritti sono numerabili
		2. Le funzioni descritte sono totali
	+ Un esempio di funzione totale non in PR è la funzione di Ackermann:
	```FORTRAN
	f(n, m): 
		if (m = 0)
			then n + 1
		else
			if (n = 0)
				then f(m-1, 1)
			else
				f(m-1, f(m, n-1))
	```
	+ È una funzione che cresce troppo velocemente per PR
---
## 2.2 - Macchine di Turing
+ La **Macchina di Turing** è un formalismo molto speciale, in grado di **descrivere** **tutte** le **funzioni calcolabili**
+ È immaginabile come un **nastro infinito**, ricoperto di **simboli** vari, sul quale scorre una **testina** in grado di scrivere e leggere i simboli
+ Esistono **più definizioni** specifiche, **cominceremo** vedendo la definizione della macchina come **automa riconoscitore**
### Riconoscitore
+ La Macchina di Turing è una **macchina a stati deterministica**
+ L'automa è descritto dalla seguente tupla:
	+ $\mathcal{MdT} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Mulberry}{\delta}, \textcolor{Cyan}{F})$ 
		+ $\textcolor{Apricot}{Q}$ è un insieme di **stati**
		+ $\textcolor{LimeGreen}{\Sigma}$ è l'alfabeto di **input**, dei simboli sul nastro
		+ $\textcolor{WildStrawberry}{q_0}$ è lo **stato iniziale** della macchina
		+ $\textcolor{Mulberry}{\delta}$ è la **funzione di transizione**
		+ $\textcolor{Cyan}{F}$ è l'insieme degli **stati finali** della macchina
+ Funzione di Transizione
	+ $\textcolor{Mulberry}{\delta} : Q \times \Gamma \to Q \times \Gamma \times \{L, R, N\}$
		+ L, R e N indicano **come muoversi** sul nastro (sinistra, destra, fermo)
			+ Spesso N è realizzato muovendosi a vuoto due volte, destra e sinistra
+ Configurazioni
	+ $<\alpha, q, \beta>$
		+ $\alpha \in \Sigma^*$ stringa a sinistra della testina
		+ $q$           stato attuale della macchina
		+ $\beta \in \Sigma^*$ stringa a destra della testina
+ Configurazioni Ferme
	+ $<\alpha, q, x\beta>\wedge \; \delta(q, x)\uparrow$ 
	+ $<\alpha, q, \varepsilon> \wedge \; \delta(q, \varepsilon)\uparrow$ 
+ Computazioni
	+ Computazione **accettante**  
		+ $c_0 \to c_1 \to \cdots \to c_n : <\_, q \in F, \_>$ 
		+ Non ci importa di cosa è rimasto sul nastro, siamo giunti in uno stato finale
		+ Per fare in modo di fermarci sugli stati finali, si fa in modo che se $q_n \in F$, $\delta(q, x)\uparrow$ 
	+ Computazione **non accettante**
		1. $c_0 \to c_1 \to \cdots \to c_n : <\alpha, q \notin F, \beta>$ 
			+ Con casi possibili
				+ $<\alpha, q \notin F, x\beta> \quad \delta(q, x)\uparrow$ 
				+ $<\alpha, q \notin F, \varepsilon> \quad \; \delta(q, \varepsilon)\uparrow$ 
		2. $c_0 \to c_1 \to \cdots \to c_{\infty}$
			+ La macchina **non termina**
			+ La stringa non è accettata, ma non lo sapremo mai
	+ È possibile riscrivere la macchina in modo da avere solo due casi: termina e non termina
		+ Basta creare uno stato che indica non accettato, e ritornare sempre li in caso di non accettazione
+ Linguaggio
	+ Linguaggio **Accettato**:
		+ $L^{A}(\mathcal{M}) = \{u \in \Sigma^* \; | <\varepsilon, q_0, u> \; \xrightarrow{*} \; <\_, q \in F, \_>\}$
			+ Potrebbe non terminare
	+ Linguaggio **Riconosciuto**:
		+ Se $L^R(\mathcal{M})$ è accettato e se $\forall u \notin L^R \quad <\varepsilon, q_0, u> \; \xrightarrow{*} \; <\_, q \notin F, \_>$
			+ Termina sempre
---
+ Lo **stile di programmazione** per queste macchine un **passo in avanti** rispetto agli automi visti in passato, **ma** è comunque **complesso**
	+ Bassissimo livello
	+ Presente l'idea di una memoria estendibile
	+ Si può sia leggere che scrivere
	+ Ci si può spostare liberamente
+ Rispetto a linguaggi più moderni, **manca** solo il concetto di **accesso diretto alla memoria** 
### Calcolatore
+ Possiamo vedere la Macchina di Turing come un **calcolatore**, ovvero una macchina che realizza una **funzione** input $\to$ output **parziale** (può non terminare)
+ Essa è definita dalla tupla seguente
	+ $\mathcal{MdT} : ( \textcolor{Apricot}{Q}, \textcolor{LimeGreen}{\Sigma}, \textcolor{WildStrawberry}{q_0}, \textcolor{Mulberry}{\delta}, \textcolor{Yellow}{B})$ 
	+ Non abbiamo più bisogno di stati finali
---
+ Per poter calcolare le funzioni dobbiamo essere in grado di **codificare** input ed output
+ Avremo bisogno delle due funzioni seguenti, **iniettive** ma non surgettive
	+ $C_{in}: \text{Input} \to \Sigma^*$ 
	+ $C_{out}: \text{Output} \to \Sigma^*$ 
+ La macchina calcola il risultato nel seguente modo:
	+ Prima converte l'input in linguaggio macchina
	+ Esegue le computazione 
	+ Ci sono tre casi possibili ora
		1. Arriva ad una configurazione ferma, legge l'output e vede che corrisponde ad un valore. Questo è il **risultato** della computazione
		2. Arriva ad una configurazione ferma, legge l'output e vede che non corrisponde a nessun valore. La funzione **non è definita** su questo input
		3. La computazione non termina mai. La funzione **non è definita** su questo input
+ In generale queste funzioni sono **parziali**
---
+ Diciamo che una funzione è **Turing-Calcolabile** se esiste una $MdT$ in grado di calcolarla. Questo concetto può essere esteso a quello di calcolabilità
### Calcolabilità
+ Secondo la Tesi di **Church-Turing** la nozione di **T-Calcolabile** è **equivalente** a quella di **calcolabile**
	+ Si dice anche che è **ricorsiva**, sinonimo di calcolabile
+ Questa idea è supportata da varie nozioni
	+ Tutti gli altri formalismi proposti ($\mu$-ricorsive, $\lambda$-calcolo, macchine a registri, linguaggi di programmazione) si sono rivelati equivalenti
	+ Tutte le funzioni intuitivamente calcolabili sono risultate T-Calcolabili
	+ Le prove delle equivalenze fra formalismi avvengono per modalità **costruttiva**, ovvero attraverso la creazione di algoritmi di "traduzione"
+ Come usiamo questo concetto?
	+ Per **dimostrare** che una funzione è **calcolabile**, basta dimostrare che **esiste** una **macchina** in grado di calcolarla, fornendo anche solo un algoritmo informale
---
+ **Quante sono** le $MdT$? sono infinite, numerabili (in quanto rappresentabili come stringhe) e superiori al numero di funzioni calcolabili (anch'esse infinite numerabili), in quanto esistono un numero infinito di macchine che possono rappresentare la stessa funzione
	+ Ovviamente, dire che $f$ è calcolabile è diverso dal dire che conosciamo una macchina di Turing per $f$
+ Il numero di $f$ ricorsive totali è sempre numerabile, anche se inferiore al numero di funzioni ricorsive totali 
---
+ Cos'è la **macchina di Turing universale**?
	+ È una macchina che prende in input la descrizione di una macchina ed un input, e restituisce l'output di quella macchina su quell'input
+ Sarebbe una vera e propria macchina **programmabile**, di cui possiamo decidere le istruzioni
+ Esiste? Certo, possiamo descriverla come:
	+ $f_u(x, y) = \begin{dcases}f_x(y) \quad \text{se  } f_x(y) \downarrow \\ \uparrow \quad \text{altrimenti}\end{dcases}$
+ Essa è una funzione ricorsiva in quanto possiamo dare un semplice algoritmo per calcolarla:
```
input x, y
trovo Mx
return Mx(y)
```
+ Questa macchina è un **interprete**, o calcolatore programmabile
---
## 2.3 - Ricorsività
+ Diciamo che un linguaggio è **ricorsivamente enumerabile** (RE) se il linguaggio è il linguaggio di una qualche macchina di Turing
+ Diciamo che un linguaggio è **ricorsivo** (R) se il linguaggio è il linguaggio di una qualche macchina di Turing che **termina sempre**
	+ Se un linguaggio è R, è anche RE
+ Esiste quindi sempre un algoritmo che riconosce sempre le stringhe per i linguaggi R. È più difficile dirlo per i linguaggi RE
---
+ Vediamo un esempio di funzione **non-calcolabile**, l'**Halting Problem
	+ $f_H(x, y) = \begin{dcases} 1 \quad \text{se  } f_x(y) \downarrow \\0 \quad \text{altrimenti}\end{dcases}$
+ Per essere calcolabile, deve necessariamente esistere un programma in grado di calcolarla
+ La prima idea consiste nell'eseguire $f_x(y)$ e controllare il risultato
	+ Ma un programma del genere non sarebbe in grado di terminare, nel caso in cui $f_x$ non terminasse
	+ Dobbiamo per forza andare ad analizzare il programma di $f_x$...
+ Proviamo prima ad analizzare la versione **diagonalizzata** di $f_H$
	+ $f_K(x) = \begin{dcases} 1 \quad \text{se  } f_x(x) \downarrow \\0 \quad \text{altrimenti}\end{dcases}$
+ Questa **non può** essere ricorsiva. Consideriamo la seguente funzione $g$
	+ $g(x) = \begin{dcases} \uparrow \quad \text{se  } \mathcal{M}_K(x) \text{ termina} \\1 \quad \text{altrimenti}\end{dcases}$
+ Se $f_K$ è calcolabile, dobbiamo essere in grado di capire se una macchina non termina. Se sappiamo farlo, anche $g$ è calcolabile (l'algoritmo è facilmente intuibile )
+ Ma se è calcolabile, esiste $z \; | \; f_z = g$ 
+ Quindi possiamo calcolare:
	+ $g(z) = \begin{dcases} \uparrow \quad \text{se  } g(z) \downarrow \\1 \quad \text{se  } g(z) \uparrow\end{dcases}$
+ Questo è ovviamente un paradosso
+ Quindi $g$ non è calcolabile, e quindi nemmeno $f_K$, e quindi nemmeno $f_H$ (per riduzione) 
---
### Insiemi di Funzioni
+ Consideriamo insiemi numerici $X \subseteq \mathbb{N}$ 
+ Ognuno di questi numeri può essere considerato **l'indice di un programma**
+ Possiamo dire che:
	+ $X$ è **ricorsivo** se esiste un macchina che dice se un elemento $x$ è on non è in $X$, **terminando sempre**
		+ Possiamo vedere queste funzioni come **problemi decidibili**
	+ $X$ è **ricorsivamente numerabile** se esiste un macchina che dice se un elemento $x$ è on non è in $X$, **potendo non terminare**
		+ Gli insiemi $H$ e $K$, analoghi alle funzioni dell'**halting problem**, appartengono a questo insieme. La risposta positiva è sempre ottenibile
		+ Possiamo vedere queste funzioni come **problemi semi-decidibili**
			+ *(esistono anche problemi non-decidibili, come il problema della terminazione)*
			+ Un esempio di insieme di funzioni non ricorsivamente enumerabile è l'insieme $\mathbb{T}$ delle funzioni che terminano sempre
+ Un altro modo per vedere se un insieme è ricorsivo è se la **funzione caratteristica** $\chi$ è ricorsiva
	+ $\chi_X(x) = \begin{dcases} 1 \quad x \in X \\ 0 \quad x \notin X\end{dcases}$ 
+ Analogamente, per vedere se un insieme è ricorsivamente enumerabile, bisogna vedere se la **funzione semicaratteristica** $\psi$ è ricorsiva
	+ $\psi_X(x) = \begin{dcases} 1 \quad x \in X \\ 0 \vee \uparrow \quad x \notin X\end{dcases}$
+ In questo casi, $X$ viene chiamato il **dominio di definizione** della funzione caratteristica
+ Tutte queste definizioni sono **collegate** fra loro
---
#### Post
+ Vediamo il **Teorema di Post**
	+ L'insieme $X \subseteq \mathbb{N}$ è **ricorsivo** se e solo se $\overline{X}$ è **ricorsivo** e se e solo se sono **entrambi ricorsivamente enumerabili**
+ Tramite l'**inter-leaning**, è possibile dimostrare il teorema (*nel cartaceo*)
+ Tramite esso è possibile dare un esempio di insieme **non ricorsivamente enumerabile**
	+ Riprendiamo $K$ ed $H$, gli insiemi analoghi alle funzioni $f_k$ ed $f_h$ viste in precedenza
	+ $H$ e $K$ sono ricorsivamente enumerabili, ma non ricorsivi. Per ciò, $\overline{H}$ ed $\overline{K}$ sono **necessariamente non ricorsivamente enumerabili**
		+ *Questo è comprensibile, in quanto determinare se un programma non termina è un problema di natura ben più complessa di se termini*
### Chiusura Ricorsivi e RE
+ $X, Y$ **ricorsivi**
+ Sono i seguenti ricorsivi?
	+ $\overline{X} \quad$ **SI**, per Post
	+ $X \cup Y\quad$ **SI**, si può realizzare una macchina specifica tramite quelle di $X$ ed $Y$ 
	+ $X \cap Y \quad$ **SI**, in modo simile a prima
	+ $X \cdot Y \quad$ **SI**, basta provare tutte le possibili decomposizioni
	+ $X^* \quad$ **SI**, basta fare come sopra
+  $X, Y$ **ricorsivamente enumerabili**
+ Sono i seguenti ricorsivamente enumerabili?
	+ $\overline{X} \quad$ **NO**, già visto con $\overline{K}$
	+ $X \cup Y\quad$ **SI**, si può realizzare una macchina specifica tramite quelle di $X$ ed $Y$ ed inter-leaning
	+ $X \cap Y \quad$ **SI**, in modo simile a prima con un and, o tramite un algoritmo sequenziale
	+ $X \cdot Y \quad$ **SI**, basta fare inter-leaning su tutte le possibili decomposizioni
	+ $X^* \quad$ **SI**, basta fare come sopra
---
### Caratterizzazioni di RE
+ Dato un insieme $A$ **ricorsivamente enumerabile** possiamo dare le tre seguenti definizioni, le quali sono equivalenti:
	1. $A$ possiede una macchina di **semi-decisione**
	2. $A$ è l'**immagine** di una **funzione ricorsiva**
	3. $A = \emptyset$ oppure è l'immagine di una **funzione ricorsiva totale**
+ È possibile dimostrare i collegamenti fra esse (*vedere nel cartaceo, tecnica a zig-zag*) 
+ Queste funzioni ricorsive sono quindi macchine in grado di generare (e quindi enumerare) tutte le funzioni presenti nell'insieme $A$ (con possibili ripetizioni)
	+ Da questo deriva il nome di "ricorsivamente enumerabile", in quanto possiamo dare un algoritmo per farlo
+ Quindi dire che un insieme è ricorsivamente numerabile vuol dire:
	+ Esiste un algoritmo di semi-decisione per decidere se un elemento ne fa parte
	+ Esso può essere generato algoritmicamente
---
### Riduzione
+ Abbiamo visto che capire se un insieme è ricorsivo o R.E. è relativamente complesso 
+ Fortunatamente esistono vari metodi per dimostrarlo. Uno è quello della **riduzione**
+ Esso è simile a quello di riduzione polinomiale visto ad APA
	+ Dati $A, B \in \mathbb{N}$, si dice che $A \leq B$ se e solo se $\exists f : \mathbb{N} \to \mathbb{N}$ ricorsiva totale tale che $x \in A \leftrightarrow f(x) \in B$ 
+ Si dice che $A$ viene **ridotto** a $B$ 
	+ La riduzione è **riflessiva e transitiva**
+ Questo per noi è molto importante, in quanto i due insiemi sono collegati:
	+ $B$ ricorsivo $\to$ $A$ ricorsivo
	+ $A$ non ricorsivo $\to$ $B$ non ricorsivo
	+ $B$ ricorsivamente enumerabile $\to$ $A$ ricorsivamente enumerabile
	+ $A$ non ricorsivamente enumerabile $\to$ $B$ non ricorsivamente enumerabile
+ Possiamo quindi **sfruttare** l'idea per dimostrare la ricorsività o non ricorsività di un insieme
#### Teorema del Parametro (s-m-n)
+ Data $f: \mathbb{N} \times \mathbb{N} \to \mathbb{N}$ ricorsiva
+ $\exists \; g : \mathbb{N} \to \mathbb{N}$ ricorsiva totale tale che $\phi_{g(x)}(y) = f(x, y)$ 
	+ Fissato l'**argomento** $x$, posso sempre trovare una **funzione** in un solo parametro che calcola $f(x, y)$ 
+ Questo teorema può essere utile per dimostrare l'esistenza di $g$
---
### Rice
+ Le **proprietà semantiche** di una funzione, **non** sono **decidibili**
+ Queste sono le proprietà relative all'input/output della funzione, e vengono chiamate **estensionali**
	+ Possiamo arrivare a queste funzioni in più modi, l'importante è il risultato
	+ Per dimostrare hce una funzione non è estenzionale, basta mostrare che esistono due funzioni differenti, dal comportamento uguale, per cui la proprietà non vale
+ Esse sono decidibili solo se banali. Nel nostro caso, che il sottoinsieme ottenuto è $\emptyset$ o $\mathbb{N}$ 
+ Possiamo usare questa proprietà per dimostrare la non ricorsività di un insieme: Basta dimostrare che la proprietà è estensionale, ma non banale 
## 2.4 - Appendici
### $\mu$-Ricorsive
### MdT Non Deterministiche