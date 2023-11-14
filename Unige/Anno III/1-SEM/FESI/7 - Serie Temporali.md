+ Una serie temporale è una **sequenza** di **dati** acquisiti ad intervalli di tempo regolari
+ Solitamente, vogliamo **rilevare** da essi:
	+ Anomalie
	+ Periodicità
	+ Previsioni
	+ Trend
+ Per far ciò, i dati vanno **ripuliti** da errori e rumori. Ci concentreremo su questo
---
+ La **differenza finita**, o derivata discreta, vine calcolata nel seguente modo:
	+ $f'(x) = \cfrac{f(x+h) -f(x)}{h}$ 
+ È un equivalente discreto della derivata nel continuo, e come essa ci permette di descrivere le **variazioni** della funzione studiata
	+ Queste variazioni possono essere classificate in **scalini**, cambi repentini facilmente identificabili, e **rampe**, ben più subdole
	+ Possono inoltre permetterci di rilevare **picchi** e **valli** del segnale
+ Possiamo anche studiare la derivata **seconda**, così da riconoscere **crescite** e **decrescite**
	+ In particolare, nel caso di determinate "spike", avvengono i cosiddetti **zero-crossing**, molto interessanti
+ Queste derivate possono essere implementate attraverso la **convoluzione** discreta, scegliendo dei determinati **filtri**
+ Ne esistono due in particolare
	+ $[1, -1]\quad$ **Forward** Difference
	+ $[-0.5, 0, -0.5] \quad$ **Central** Difference
		+ A differenza del precedente, questo è di dimensione dispari, e si concentra maggiormente sullo studio dei valori nei momenti subito precedenti e seguenti il momento
+ Sono entrambi filtri di **enhancement**, di tipo passa-alto
---
+ Un problema di questi filtri è che mettono in rilievo le variazioni del segnale, e con esso anche il **rumore**
+ È quindi preferibile applicare prima un filtro **passa-basso**, rimuovi rumore
	+ Esistono anche filtri "tuttofare", come la derivata della gaussiana
+ Esiste però del rumore non facilmente rimovibile, detto sale e pepe, che si può togliere solo attraverso il **filtro mediano**