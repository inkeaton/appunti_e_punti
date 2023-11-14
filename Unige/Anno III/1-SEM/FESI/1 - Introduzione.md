+ In questo corso, ci dedicheremo allo studio di segnali **1D** e **2D**
	+ Esempi dei primi sono **suoni**, voci, musica, ma anche concetti come il **meteo**, che evolvono nel tempo
	+ Esempi dei secondi sono principalmente **immagini**, in scale di grigio ed a colori
---
+ Formalmente, un **segnale** descrive una **grandezza fisica** che **varia** rispetto ad una variabile indipendente
+ Questi vengono descritti come **funzioni**, ad una o più variabili
	+ $\textcolor{Apricot}{g} = \textcolor{LimeGreen}{f}(\textcolor{WildStrawberry}{t})$ 
		+ $\textcolor{Apricot}{g}$ : Variabile dipendente
		+ $\textcolor{WildStrawberry}{t}$ : Variabile indipendente
		+ $\textcolor{LimeGreen}{f}$ : Relazione funzionale fra le due 

+ I segnali possono essere suddivisi in più **categorie**:
	+ Si può separare fra segnali a tempo **continuo**, in cui $\textcolor{WildStrawberry}{t}$ assume tutti i valori **reali**, e a tempo **discreto**, in cui $\textcolor{WildStrawberry}{t}$ assume sono i valori di un sottoinsieme **discreto**, ottenuto tramite **campionamento**
		+ Il campionamento trasforma la funzione $f(t) \to f(n\tau)$ 
		+ La qualità e dimensione del campionamento dipende dalla frequenza di campionamento $v_s = \frac{1}{\tau}$ 
	+ Oppure si può dividere fra segnali a **valori continui**, in cui $\textcolor{Apricot}{g}$ assume valori **reali**, e a **valori discreti**, in cui $\textcolor{Apricot}{g}$ assume i valori di un **sottoinsieme** discreto ottenuto mediante **quantizzazione**
		+ *Si noti che l'utilizzo di sistemi "discreti" è semplicemente dovuto alle limitazioni mnemoniche dei sistemi informatici, oltre ad eventuali necessità di presentazione dei dati*

+ Da queste due derivano due **famiglie** molto **famose** di segnali:
	+ **Analogici**, a tempi e valori **continui**
	+ **Digitali**, a tempi e valori **discreti**
